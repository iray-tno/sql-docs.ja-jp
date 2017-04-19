---
title: "トランザクションの持続性の制御 | Microsoft Docs"
ms.custom: ""
ms.date: "09/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-transaction-log"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "遅延持続性"
  - "低速コミット"
ms.assetid: 3ac93b28-cac7-483e-a8ab-ac44e1cc1c76
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# トランザクションの持続性の制御
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] におけるトランザクションのコミットには、完全持続性、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定値、または遅延持続性 (低速コミットとも呼ばれます) が適用されます。    
    
 完全持続性トランザクションのコミットは同期的であり、トランザクションのログ レコードがディスクに書き込まれてからコミットが正常完了として報告され、制御がクライアントに返されます。 遅延持続性トランザクションのコミットは非同期的であり、トランザクションのログ レコードがディスクに書き込まれる前にコミットが正常完了として報告されます。 トランザクションを持続可能にするためには、トランザクション ログ エントリをディスクに書き込む必要があります。 遅延持続性トランザクションは、トランザクション ログ エントリがディスクにフラッシュされる時点で持続的になります。    
    
 このトピックでは、遅延持続性トランザクションについて詳しく説明します。    
    
## <a name="full-vs-delayed-transaction-durability"></a>トランザクションの完全持続性と遅延持続性    
 トランザクションの完全持続性と遅延持続性にはそれぞれ、長所と短所があります。 アプリケーションには、完全持続性トランザクションと遅延持続性トランザクションを混在させることができます。 ビジネス ニーズを慎重に考慮したうえで、それぞれのタイプのトランザクションの適合性を検討する必要があります。    
    
### <a name="full-transaction-durability"></a>トランザクションの完全持続性    
 完全持続性トランザクションは、クライアントに制御を返す前に、トランザクション ログをディスクに書き込みます。 次のような場合には、完全持続性トランザクションを使用する必要があります。    
    
-   システムで、データの損失が許容されない場合。     
    データの一部が失われるケースについては、「[データが失われるケース](../../relational-databases/logs/control-transaction-durability.md#bkmk_DataLoss)」のセクションを参照してください。    
    
-   ボトルネックの原因がトランザクション ログの書き込み待機時間ではない場合。    
    
 遅延持続性トランザクションは、トランザクション ログ レコードをメモリに保持してバッチ単位でトランザクション ログ レコードに書き込み、必要な I/O 操作を減らすことによって、ログの I/O による待機時間を短縮します。 遅延持続性トランザクションでは、ログ I/O の競合が減少し、システム内の待機時間を短縮できる可能性があります。    
    
 **トランザクションの完全持続性での保証**    
    
-   トランザクションのコミットが成功した場合、トランザクションによる変更は、システム内の他のトランザクションから認識できる状態になります。 トランザクション分離レベルの詳細については、「[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)」または「[メモリ最適化テーブルでのトランザクション](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)」を参照してください。    
    
-   持続性はコミット時に保証されます。 対応するログ レコードがディスクに保存されてからトランザクションのコミットが成功となり、制御がクライアントに返されます。    
    
### <a name="delayed-transaction-durability"></a>トランザクションの遅延持続性    
 トランザクションの遅延持続性は、ディスクへのログの非同期書き込みを使用して実現します。 トランザクション ログ レコードはバッファーに保持され、バッファーがいっぱいになった場合またはバッファーのフラッシュ イベントが発生した場合に、ディスクに書き込まれます。 トランザクションの遅延持続性では、次の理由によってシステム内の待機時間と競合の両方が軽減されます。    
    
-   トランザクション コミット処理では、ログ IO の完了を待たずに制御がクライアントに返されます。    
    
-   同時実行トランザクション間でログ IO の競合が発生する可能性は高くありません。ログ バッファーは大きな単位でディスクにフラッシュできるため、競合が軽減され、スループットを向上できます。    
    
    > [!NOTE]    
    >  ただしログ バッファーがフラッシュされる前にいっぱいになる場合など、同時実行性が高い場合は、ログ I/O の競合が生じることもあります。    
    
 #### <a name="when-to-use-delayed-transaction-durability"></a>トランザクションの遅延持続性の利用が適したケース    
    
 次のような場合は、トランザクションの遅延持続性の利用が適しています。    
    
 **ある程度のデータ損失を許容できる場合。**    
 ある程度のデータ損失を許容できる場合 (データの大部分を確保できていれば個々のレコードがそれほど重要ではない場合など) は、遅延持続性の使用を検討することができます。 一切のデータ損失を許容できない場合は、トランザクションの遅延持続性は使用しないでください。    
    
 **トランザクション ログの書き込みでボトルネックが発生している場合。**    
 パフォーマンスの問題がトランザクション ログの書き込みにおける待機時間によるものであれば、トランザクションの遅延持続性を使用することがアプリケーションにとってのメリットになる可能性があります。    
    
 **ワークロードの競合率が高い場合。**    
 競合レベルの高いワークロードがシステムに存在する場合、ロックの解放待ちに多くの時間が消費されます。 トランザクションの遅延持続性を使用すると、コミット時間を短縮できるため、早くロックを解放でき、結果として高いスループットにつながります。    
    
 ### <a name="delayed-transaction-durability-guarantees"></a>トランザクションの遅延持続性での保証   
    
-   トランザクションのコミットが成功した場合、トランザクションによる変更は、システム内の他のトランザクションから認識できる状態になります。    
    
-   トランザクションの持続性が保証されるのは、インメモリ トランザクション ログがディスクにフラッシュされた後のみです。 インメモリ トランザクション ログは、次の場合にディスクにフラッシュされます。    
    
    -   完全持続性トランザクションによって、同じデータベース内で変更が行われ、正常にコミットされた場合。   
    
    -   ユーザーがシステム ストアド プロシージャ `sp_flush_log` を正常に実行した場合。     
    
        完全持続性トランザクションまたは sp_flush_log によって正常コミットされた場合、それより前にコミットされた遅延持続性トランザクションはすべて、持続可能な状態になっていることを保証されます。
        
    - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、すべてのトランザクションが遅延持続性であっても、ログ生成とタイミングの両方に基づいて、ディスクへのログのフラッシュを試みます。 通常、IO デバイスが稼働状態を保っている場合、これは成功します。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では持続性トランザクションおよび sp_flush_log 以外にハード持続性は保証されません。      
    
  
    
## <a name="how-to-control-transaction-durability"></a>トランザクションの持続性を制御する方法    
    
###  <a name="a-namebkmkdbcontrola-database-level-control"></a><a name="bkmk_DbControl"></a> データベース レベルの制御    
 DBA は次のステートメントを使用して、トランザクションの遅延持続性をデータベースに対してユーザーが使用できるかどうかを制御できます。 遅延持続性の設定は ALTER DATABASE で設定する必要があります。    
    
```tsql    
ALTER DATABASE … SET DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }    
```    
    
 **DISABLED**    
 [既定値] この設定では、コミット レベルの設定 (DELAYED_DURABILITY=[ON | OFF]) に関係なく、データベースに対してコミットされたトランザクションにはすべて完全持続性が適用されます。 ストアド プロシージャの変更および再コンパイルの必要はありません。 この設定により、遅延持続性によるリスクを負うことなく、すべてのデータを持続可能にできます。    
    
 **ALLOWED**    
 この設定では、各トランザクションの持続性がトランザクション レベル (DELAYED_DURABILITY = { *OFF* | ON }) で決定されます。 詳細については、「[ATOMIC ブロック レベルの制御 – ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/logs/control-transaction-durability.md#CompiledProcControl)」と「[COMMIT レベルの制御 – Transact-SQL](../../relational-databases/logs/control-transaction-durability.md#bkmk_T-SQLControl)」を参照してください。    
    
 **FORCED**    
 この設定では、データベースにコミットされるすべてのトランザクションに遅延持続性が適用されます。 トランザクションで完全持続性 (DELAYED_DURABILITY = OFF) が指定された場合も、指定がまったく行われていない場合も、遅延持続性トランザクションになります。 データベースに対してトランザクションの遅延持続性が役立ち、アプリケーション コードの変更を行わない場合に、この設定を使用できます。    
    
###  <a name="a-namecompiledproccontrola-atomic-block-level-control-natively-compiled-stored-procedures"></a><a name="CompiledProcControl"></a> ATOMIC ブロック レベルの制御 – ネイティブ コンパイル ストアド プロシージャ    
 次のコードは、ATOMIC ブロック内で使用します。    
    
```tsql    
DELAYED_DURABILITY = { OFF | ON }    
```    
    
 **OFF**    
 [既定値] トランザクションに完全持続性が適用されます。ただし、データベース オプション DELAYED_DURABLITY = FORCED が有効であれば、コミットは非同期的であり、遅延持続性が適用されます。 詳細については、「[データベース レベルの制御](../../relational-databases/logs/control-transaction-durability.md#bkmk_DbControl)」を参照してください。    
    
 **ON**    
 トランザクションに遅延持続性が適用されます。ただし、データベース オプション DELAYED_DURABLITY = DISABLED が有効であれば、コミットは同期的であり、完全持続性が適用されます。  詳細については、「[データベース レベルの制御](../../relational-databases/logs/control-transaction-durability.md#bkmk_DbControl)」を参照してください。    
    
 **コード例:**    
    
```tsql    
CREATE PROCEDURE <procedureName> …    
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER    
AS BEGIN ATOMIC WITH     
(    
    DELAYED_DURABILITY = ON,    
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,    
    LANGUAGE = N'English'    
    …    
)    
END    
```    
    
### <a name="table-1-durability-in-atomic-blocks"></a>表 1: ATOMIC ブロックの持続性    
    
|ATOMIC ブロックの持続性オプション|既存のトランザクションが存在しない場合|処理中の (完全持続性または遅延持続性) トランザクションが存在する場合|    
|------------------------------------|-----------------------------|---------------------------------------------------------|    
|**DELAYED_DURABILITY = OFF**|ATOMIC ブロックで、新しい完全持続性トランザクションが開始されます。|ATOMIC ブロックで、既存のトランザクションにセーブポイントが作成され、新しいトランザクションが開始されます。|    
|**DELAYED_DURABILITY = ON**|ATOMIC ブロックで、新しい遅延持続性トランザクションが開始されます。|ATOMIC ブロックで、既存のトランザクションにセーブポイントが作成され、新しいトランザクションが開始されます。|    
    
###  <a name="a-namebkmkt-sqlcontrola-commit-level-control-includetsqltokentsqlmdmd"></a><a name="bkmk_T-SQLControl"></a> COMMIT レベルの制御 –[!INCLUDE[tsql](../../includes/tsql-md.md)]    
 COMMIT 構文は、トランザクションの遅延持続性を適用できるように拡張されています。 DELAYED_DURABILITY がデータベース レベルで DISABLED または FORCED に設定されている場合 (上記を参照)、この COMMIT オプションは無視されます。    
    
```tsql    
COMMIT [ { TRAN | TRANSACTION } ] [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]    
    
```    
    
 **OFF**    
 [既定値] トランザクションの COMMIT に完全持続性が適用されます。ただし、データベース オプション DELAYED_DURABLITY = FORCED が有効であれば、COMMIT は非同期的であり、遅延持続性が適用されます。 詳細については、「[データベース レベルの制御](../../relational-databases/logs/control-transaction-durability.md#bkmk_DbControl)」を参照してください。    
    
 **ON**    
 トランザクションの COMMIT に遅延持続性が適用されます。ただし、データベース オプション DELAYED_DURABLITY = DISABLED が有効であれば、COMMIT は同期的であり、完全持続性が適用されます。 詳細については、「[データベース レベルの制御](../../relational-databases/logs/control-transaction-durability.md#bkmk_DbControl)」を参照してください。    
    
### <a name="summary-of-options-and-their-interactions"></a>オプションとその作用の概要    
 このテーブルは、データベース レベルの遅延持続性設定とコミット レベルの設定の相互作用をまとめたものです。 データベース レベルの設定はコミット レベルの設定よりも常に優先されます。    
    
|COMMIT の設定/データベースの設定|DELAYED_DURABILITY = DISABLED|DELAYED_DURABILITY = ALLOWED|DELAYED_DURABILITY = FORCED|    
|--------------------------------------|-------------------------------------|------------------------------------|-----------------------------------|    
|**DELAYED_DURABILITY = OFF** データベース レベル トランザクション。|トランザクションに完全持続性が適用されます。|トランザクションに完全持続性が適用されます。|トランザクションに遅延持続性が適用されます。|    
|**DELAYED_DURABILITY = ON** データベース レベル トランザクション。|トランザクションに完全持続性が適用されます。|トランザクションに遅延持続性が適用されます。|トランザクションに遅延持続性が適用されます。|    
|**DELAYED_DURABILITY = OFF** 複数データベース間トランザクションまたは分散トランザクション。|トランザクションに完全持続性が適用されます。|トランザクションに完全持続性が適用されます。|トランザクションに完全持続性が適用されます。|    
|**DELAYED_DURABILITY = ON** 複数データベース間トランザクションまたは分散トランザクション。|トランザクションに完全持続性が適用されます。|トランザクションに完全持続性が適用されます。|トランザクションに完全持続性が適用されます。|    
    
## <a name="how-to-force-a-transaction-log-flush"></a>トランザクション ログのフラッシュを強制する方法    
 強制的にトランザクション ログをディスクにフラッシュするには、次の 2 つの方法があります。    
    
-   同じデータベースを変更する完全持続性トランザクションを実行する。 これにより、それまでにコミット済みの遅延持続性トランザクションのログ レコードがすべて強制的にディスクにフラッシュされます。    
    
-   システム ストアド プロシージャ `sp_flush_log` を実行する。 このプロシージャにより、それまでにコミット済みの遅延持続性トランザクションのログ レコードがすべて強制的にディスクにフラッシュされます。 詳細については、「[sys.sp_flush_log &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql.md)」を参照してください。    
    
##  <a name="a-namebkmkothersqlfeaturesa-delayed-durability-and-other-includessnoversiontokenssnoversionmdmd-features"></a><a name="bkmk_OtherSQLFeatures"></a> 遅延持続性とその他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能    
 **変更の追跡と変更データ キャプチャ**    
 変更の追跡を有効にしたすべてのトランザクションには、完全持続可能性が適用されます。 変更の追跡が有効なテーブルに対して書き込み操作を行うトランザクションには、変更追跡プロパティがあります。 変更データ キャプチャ (CDC) を使用するデータベースの場合、遅延持続は使用できません。    
    
 **クラッシュ後の復旧**    
 一貫性は保証されますが、コミット済みの遅延持続性トランザクションから変更内容が失われる場合があります。    
    
 **複数データベース間と DTC**    
 複数データベース間トランザクションまたは分散トランザクションの場合、データベースまたはトランザクションのコミット設定に関係なく、トランザクションには完全持続性が適用されます。    
    
 **AlwaysOn 可用性グループとミラーリング**    
 遅延持続性トランザクションでは、プライマリまたはいずれかのセカンダリに関する持続性は保証されません。 また、セカンダリでのトランザクションに関するナレッジは保証されません。 コミット後、同期セカンダリからの受信確認を受信する前に、制御がクライアントに返されます。 プライマリ上のディスクへのフラッシュ時に、セカンダリ レプリカへのレプリケーションが継続的に発生します。   
    
 **フェールオーバー クラスタリング**    
 遅延持続性トランザクションによる書き込みの一部が失われる場合があります。    
    
 **トランザクション レプリケーション**    
 遅延持続性トランザクションは、トランザクション レプリケーションではサポートされていません。    
    
 **ログ配布**    
 配信されるログに含まれるのは、持続可能な状態になったトランザクションのみです。    
    
 **ログ バックアップ**    
 バックアップに含まれるのは、持続可能な状態になったトランザクションのみです。    
    
##  <a name="a-namebkmkdatalossa-when-can-i-lose-data"></a><a name="bkmk_DataLoss"></a> データが失われるケース    
 遅延持続性をテーブルに実装する場合、状況によってはデータが失われる可能性があることを理解する必要があります。 一切のデータ損失を許容できない場合は、テーブルに対して遅延持続性は使用しないでください。    
    
### <a name="catastrophic-events"></a>重大なイベント    
 サーバー クラッシュなどの重大なイベントが発生すると、ディスクに保存されていないすべてのコミット済みトランザクションのデータが失われます。 遅延持続性トランザクションは、データベース内のいずれかのテーブル (持続性のあるメモリ最適化テーブルまたはディスク ベース テーブル) に対して完全持続性トランザクションが実行されるか、`sp_flush_log` が呼び出されるたびに、ディスクに保存されます。 遅延持続性トランザクションを使用している場合、定期的に更新するか定期的に `sp_flush_log` を呼び出すことができる小さいテーブルをデータベース内に作成して、未処理のコミット済みトランザクションすべてを保存できます。 トランザクション ログもいっぱいになるたびにフラッシュされますが、それを予測するのは難しく、制御は不可能です。    
    
### <a name="includessnoversiontokenssnoversionmdmd-shutdown-and-restart"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシャットダウンと再起動    
 遅延持続性の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の予期しないシャットダウンと予期されたシャットダウン/再起動に違いはありません。 重大なイベントと同様に、データ損失に対する計画を立てる必要があります。 計画されたシャットダウン/再起動では、ディスクに書き込まれていない一部のトランザクションが最初にディスクに保存される場合がありますが、それを予期することはできません。 計画されているかどうかに関係なく、シャットダウン/再起動によって重大なイベントと同様にデータが失われるものとして計画してください。    
    
## <a name="see-also"></a>参照    
 [メモリ最適化テーブルでのトランザクション](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)    
    
  