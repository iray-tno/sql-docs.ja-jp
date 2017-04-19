---
title: "Reorganize and Rebuild Indexes | Microsoft Docs"
ms.custom: ""
ms.date: "04/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.index.rebuild.f1"
  - "sql13.swb.indexproperties.fragmentation.f1"
  - "sql13.swb.index.reorg.f1"
helpviewer_keywords: 
  - "ラージ オブジェクトのデフラグ"
  - "インデックス [SQL Server], 再構成"
  - "インデックスの再構成 [SQL Server]"
  - "再構成、インデックス"
  - "ラージ オブジェクト データ型のデフラグ"
  - "インデックスの断片化 [SQL Server]"
  - "インデックスの再構築 [SQL Server]"
  - "再構築、インデックス"
  - "インデックス [SQL Server], 再構築"
  - "インデックスの断片化解消"
  - "非クラスター化インデックス [SQL Server], 断片化解消"
  - "断片化 [SQL Server]"
  - "インデックスの断片化解消 [SQL Server]"
  - "LOB データ [SQL Server], 断片化解消"
  - "クラスター化インデックス, 断片化解消"
ms.assetid: a28c684a-c4e9-4b24-a7ae-e248808b31e9
caps.latest.revision: 70
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 70
---
# Reorganize and Rebuild Indexes
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、断片化したインデックスを再構成または再構築する方法について説明します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]では、基になるデータに対して挿入、更新、または削除の各操作が行われるたびに、インデックスが自動的にメンテナンスされます。 このような変更が長期にわたると、インデックス内の情報がデータベース内に散在 (断片化) することになります。 インデックスに、キー値に基づく論理順序とデータ ファイル内の物理順序が一致しないページが存在すると、断片化が発生します。 インデックスが大量に断片化されると、クエリのパフォーマンスが低下し、アプリケーションの応答が遅くなる場合があります。  
  
 インデックスを再構成するか、インデックスを再構築することにより、インデックスの断片化を解消できます。 パーティション構成に基づいて構築されたパーティション インデックスでは、完全なインデックスまたはインデックスの 1 つのパーティションで、再構成または再構築のいずれかを実行できます。 インデックスの再構築では、インデックスを削除し再作成します。 この操作では、断片化をなくし、指定されているか既に存在する FILL FACTOR 設定に基づいてページを圧縮することによりディスク領域を取り戻した後、連続するページにインデックス行を再び並べ替えます。 ALL を指定した場合、テーブル上のすべてのインデックスが、1 回のトランザクションで削除され再構築されます。 インデックスの再構成では、最小のシステム リソースが使用されます。 この操作では、リーフ レベル ページをリーフ ノードの論理順序 (左から右) に合わせて物理的に並べ替えることにより、テーブルやビュー上にあるクラスター化および非クラスター化インデックスのリーフ レベルをデフラグします。 再構成でも、インデックス ページは圧縮されます。 圧縮は既存の FILL FACTOR 値に基づいて行われます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [断片化の検出](#Fragmentation)  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **インデックスの断片化を確認するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedureFrag)  
  
     [Transact-SQL](#TsqlProcedureFrag)  
  
-   **インデックスを再構成または再構築するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedureReorg)  
  
     [Transact-SQL](#TsqlProcedureReorg)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Fragmentation"></a> 断片化の検出  
 断片化を解消する方法を決める最初の手順は、断片化の程度を判断するためにインデックスを分析することです。 システム関数 [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) を使用して、特定のインデックス、テーブルやインデックス付きビュー上のすべてのインデックス、データベース内のすべてのインデックス、またはすべてのデータベース内のすべてのインデックスの断片化を検出できます。 パーティション インデックスの場合は、**sys.dm_db_index_physical_stats** でもパーティションごとの断片化情報が提供されます。  
  
 **sys.dm_db_index_physical_stats** 関数から返される結果セットに含まれる列を次に示します。  
  
|列|説明|  
|------------|-----------------|  
|**avg_fragmentation_in_percent**|論理的な断片化 (インデックス内で順序が乱れたページ) の割合。|  
|**fragment_count**|インデックス内の断片化 (物理的に連続したリーフ ページ) の数。|  
|**avg_fragment_size_in_pages**|インデックス内の 1 つの断片化内の平均ページ数。|  
  
 断片化の程度がわかったら、次の表を使用して、断片化を解消するための最適な方法を決定します。  
  
|**avg_fragmentation_in_percent** 値|断片化解消ステートメント|  
|-----------------------------------------------|--------------------------|  
|5 ～ 30%|ALTER INDEX REORGANIZE|  
|> 30%|ALTER INDEX REBUILD WITH (ONLINE = ON)*|  
  
 \* インデックスの再構築はオンラインでもオフラインでも実行できます。 インデックスの再構成は、常にオンラインで実行されます。 再編成オプションと同様の可用性を実現するには、インデックスをオンラインで再構築してください。  
  
 これらの値は、ALTER INDEX REORGANIZE と ALTER INDEX REBUILD の使い分けの大まかな目安となります。 ただし、実際の値は状況によって変わります。 それぞれの環境で実際に試して最適なしきい値を特定することが重要です。 断片化のレベルが非常に低い場合 (5% 未満) は、これらのコマンドのいずれも使用しないでください。インデックスの再構成や再構築には、ほとんどの場合、そのようなわずかな断片化を解消するには見合わないコストがかかります。  
  
> [!NOTE]
>  一般に、小さなインデックスの断片化は制御不能である場合がほとんどです。 小さなインデックスのページは、混合エクステントに格納される場合もあります。 混合エクステントは最大 8 つのオブジェクトで共有されるため、インデックスを再構成または再構築しても、小さなインデックスの断片化は解消されない場合があります。
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   128 エクステントを超えるインデックスは、論理フェーズと物理フェーズの 2 つの独立したフェーズで再構築されます。 論理フェーズでは、インデックスによって使用されている既存のアロケーション ユニットが、割り当て解除に設定されます。その後、データ行がコピーされ、並べ替えられてから、再構築されたインデックスを格納するために作成された新しいアロケーション ユニットに移動されます。 物理フェーズでは、バックグラウンドで行われる短いトランザクションで、以前に割り当て解除に設定されたアロケーション ユニットが物理的に削除され、ロックの必要はあまり多くありません。  
  
-   インデックスを再編成するときは、インデックス オプションを指定できません。  
  
-   この操作では、ファイル グループ内の他のファイルではなく、同じファイル上に一時的な作業ページを割り当てなければならないため、`ALTER INDEX REORGANIZE` ステートメントには、使用可能な領域があるインデックスを含むデータ ファイルが必要です。  ファイル グループに使用可能な空きページがある場合でも、エラー 1105「データベース \<database name> にオブジェクト \<index name>.\<table name> の領域を割り当てられませんでした。'PRIMARY' ファイル グループがいっぱいです。」が発生する可能性があります。
  
-   固定されていないインデックスをパーティションが 1, 000 個以上あるテーブルに作成または再構築することは可能ですが、サポートされていません。 このような操作を行うと、操作中にパフォーマンスが低下したりメモリが過度に消費される可能性があります。
  
> [!NOTE]
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、パーティション インデックスが作成または再構築された場合、テーブル内のすべての行をスキャンして統計を作成することはできません。 代わりに、クエリ オプティマイザーが既定のサンプリング アルゴリズムを使用して統計を生成します。 テーブル内のすべての行をスキャンしてパーティション インデックスの統計を作成するには、FULLSCAN 句で CREATE STATISTICS または UPDATE STATISTICS を使用します。
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 テーブルまたはビューに対する ALTER 権限が必要です。 実行するには、**sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
##  <a name="SSMSProcedureFrag"></a> SQL Server Management Studio の使用  
  
#### インデックスの断片化を確認するには  
  
1.  オブジェクト エクスプローラーで、インデックスの断片化を確認するテーブルが格納されているデータベースを展開します。  
  
2.  **[テーブル]** フォルダーを展開します。  
  
3.  インデックスの断片化を確認するテーブルを展開します。  
  
4.  **[インデックス]** フォルダーを展開します。  
  
5.  断片化を確認するインデックスを右クリックし、**[プロパティ]** を選択します。  
  
6.  **[ページの選択]**の **[断片化]**を選択します。  
  
     **[断片化]** ページでは、次の情報を取得できます。  
  
     **[ページのゆとり]**  
     インデックス ページのゆとりの平均をパーセントで示します。 100% は、インデックス ページが完全にいっぱいであることを示します。 50% は、平均して各インデックス ページが半分埋まっていることを示します。  
  
     **[全体の断片化]**  
     論理的な断片化の割合です。 この値は、順番に格納されないインデックス内のページ数を示します。  
  
     **[行の平均サイズ]**  
     リーフ レベルの行の平均サイズです。  
  
     **[奥行]**  
     インデックス内のレベルの数 (リーフ レベルを含む) です。  
  
     **[転送されたレコード]**  
     別のデータの場所への転送ポインターを持つ、ヒープ内の転送されたレコード数です  (この状態は、更新中に、新しい行を格納できる十分なスペースが元の場所にない場合に発生します)。  
  
     **[非実体行]**  
     削除のマークが付けられている行の中で、まだ削除されていない行の数です。 これらの行は、サーバーが使用中でないときにクリーンアップ スレッドによって削除されます。 この値には、スナップショット分離トランザクションが未完了であるために保持される行は含まれません。  
  
     **インデックスの種類**  
     インデックスの種類です。 指定できる値は、 **[クラスター化]**、 **[非クラスター化]**、および **[プライマリ XML]**です。 テーブルは、ヒープ (インデックスなし) としても格納できますが、その場合は、この [インデックスのプロパティ] ページは開きません。  
  
     **[リーフレベルの行]**  
     リール レベルの行の数です。  
  
     **[行の最大サイズ]**  
     リーフ レベルの最大行サイズです。  
  
     **[行の最小サイズ]**  
     リーフ レベルの最小行サイズです。  
  
     **[ページ]**  
     データ ページ数の合計です。  
  
     **Partition ID**  
     インデックスを含む B ツリーのパーティション ID です。  
  
     **[バージョンの非実体行]**  
     未処理のスナップショット分離トランザクションが原因で保持されているゴースト レコードの数。  
  
##  <a name="TsqlProcedureFrag"></a> Transact-SQL の使用  
  
#### インデックスの断片化を確認するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find the average fragmentation percentage of all indexes  
    -- in the HumanResources.Employee table.   
    SELECT a.index_id, name, avg_fragmentation_in_percent  
    FROM sys.dm_db_index_physical_stats (DB_ID(N'AdventureWorks2012'), OBJECT_ID(N'HumanResources.Employee'), NULL, NULL, NULL) AS a  
        JOIN sys.indexes AS b ON a.object_id = b.object_id AND a.index_id = b.index_id;   
    GO  
    ```  
  
     上のステートメントでは、次のような結果セットが返されます。  
  
    ```  
    index_id    name                                                  avg_fragmentation_in_percent  
    ----------- ----------------------------------------------------- ----------------------------  
    1           PK_Employee_BusinessEntityID                          0  
    2           IX_Employee_OrganizationalNode                        0  
    3           IX_Employee_OrganizationalLevel_OrganizationalNode    0  
    5           AK_Employee_LoginID                                   66.6666666666667  
    6           AK_Employee_NationalIDNumber                          50  
    7           AK_Employee_rowguid                                   0  
  
    (6 row(s) affected)  
    ```  
  
 詳細については、「[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)」を参照してください。  
  
##  <a name="SSMSProcedureReorg"></a> SQL Server Management Studio の使用  
  
#### インデックスを再構成または再構築するには  
  
1.  オブジェクト エクスプローラーで、インデックスを再構成するテーブルが格納されているデータベースを展開します。  
  
2.  **[テーブル]** フォルダーを展開します。  
  
3.  インデックスを再構成するテーブルを展開します。  
  
4.  **[インデックス]** フォルダーを展開します。  
  
5.  再構成するインデックスを右クリックし、**[再構成]** を選択します。  
  
6.  **[インデックスの再構成]** ダイアログ ボックスで、 **[再構成するインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]**をクリックします。  
  
7.  **[ラージ オブジェクトの列データを圧縮する]** チェック ボックスをオンにして、ラージ オブジェクト (LOB) データを含むページもすべて圧縮することを指定します。  
  
8.  クリックして **OK.**  
  
#### テーブルのすべてのインデックスを再構成するには  
  
1.  オブジェクト エクスプローラーで、インデックスを再構成するテーブルが格納されているデータベースを展開します。  
  
2.  **[テーブル]** フォルダーを展開します。  
  
3.  インデックスを再構成するテーブルを展開します。  
  
4.  **[インデックス]** フォルダーを右クリックし、**[すべて再構成]** を選択します。  
  
5.  **[インデックスの再構成]** ダイアログ ボックスで、 **[再構成するインデックス]**に目的のインデックスが表示されていることを確認します。 **[再構成するインデックス]** グリッドからインデックスを削除するには、インデックスを選択し、Del キーを押します。  
  
6.  **[ラージ オブジェクトの列データを圧縮する]** チェック ボックスをオンにして、ラージ オブジェクト (LOB) データを含むページもすべて圧縮することを指定します。  
  
7.  クリックして **OK.**  
  
#### インデックスを再構築するには  
  
1.  オブジェクト エクスプローラーで、インデックスを再構成するテーブルが格納されているデータベースを展開します。  
  
2.  **[テーブル]** フォルダーを展開します。  
  
3.  インデックスを再構成するテーブルを展開します。  
  
4.  **[インデックス]** フォルダーを展開します。  
  
5.  再構成するインデックスを右クリックし、**[再構成]** を選択します。  
  
6.  **[インデックスの再構築]** ダイアログ ボックスで、 **[再構築するインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]**をクリックします。  
  
7.  **[ラージ オブジェクトの列データを圧縮する]** チェック ボックスをオンにして、ラージ オブジェクト (LOB) データを含むページもすべて圧縮することを指定します。  
  
8.  クリックして **OK.**  
  
##  <a name="TsqlProcedureReorg"></a> Transact-SQL の使用  
  
#### デフラグされたインデックスを再構成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize the IX_Employee_OrganizationalLevel_OrganizationalNode index on the HumanResources.Employee table.   
  
    ALTER INDEX IX_Employee_OrganizationalLevel_OrganizationalNode ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### テーブルのすべてのインデックスを再構成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### デフラグされたインデックスを再構築するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 次の例では、 `Employee` テーブルで単一のインデックスを再構築します。  
  
     [!code-sql[IndexDDL#AlterIndex1](../../relational-databases/indexes/codesnippet/tsql/reorganize-and-rebuild-i_1.sql)]  
  
#### テーブルのすべてのインデックスを再構築するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付けます。この例では、キーワード `ALL`を指定しています。 この場合、テーブルに関連付けられているすべてのインデックスが再構築されます。 3 つのオプションが指定されます。  
  
     [!code-sql[IndexDDL#AlterIndex2](../../relational-databases/indexes/codesnippet/tsql/reorganize-and-rebuild-i_2.sql)]  
  
 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)」を参照してください。  
  
## 参照  
 [SQL Server 2000 インデックスの最適化に関するベスト プラクティス](http://technet.microsoft.com/library/cc966523.aspx)  
  
  