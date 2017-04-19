---
title: "ミラーリング パフォーマンス基準の警告しきい値および警告の使用 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データベース ミラーリングの監視 [SQL Server]"
  - "しきい値 [SQL Server]"
  - "データベース ミラーリング [SQL Server], SQL Server Management Studio での管理"
  - "警告 [SQL Server]、データベース ミラーリング"
  - "データベース ミラーリング [SQL Server] の監視"
  - "警告 [データベース ミラーリング]"
ms.assetid: 8cdd1515-0bd7-4f8c-a7fc-a33b575e20f6
caps.latest.revision: 40
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 40
---
# ミラーリング パフォーマンス基準の警告しきい値および警告の使用 (SQL Server)
  このトピックでは、データベース ミラーリング用に警告しきい値を構成および管理できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントについて説明します。 データベース ミラーリング モニター、または **sp_dbmmonitorchangealert**、**sp_dbmmonitorhelpalert**、および **sp_dbmmonitordropalert** の各ストアド プロシージャを使用できます。 また、データベース ミラーリング イベントの警告の構成についても説明します。  
  
 ミラー化されたデータベースに対する監視が確立された後、システム管理者は、複数の主要なパフォーマンス基準に警告しきい値を設定できます。 また、管理者は、これらの基準や他のデータベース ミラーリング イベントに基づいて警告を構成することもできます。  
  
 **このトピックの内容**  
  
-   [パフォーマンス基準と警告しきい値](#PerfMetricsAndWarningThresholds)  
  
-   [警告しきい値の設定と管理](#SetUpManageWarningThresholds)  
  
-   [ミラー化されたデータベースに対する警告の使用](#UseAlerts)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="PerfMetricsAndWarningThresholds"></a> パフォーマンス基準と警告しきい値  
 次の表では、警告を構成できるパフォーマンス基準、対応する警告しきい値、および対応するデータベース ミラーリング モニターのラベルについて説明します。  
  
|パフォーマンス基準|警告しきい値|データベース ミラーリング モデルのラベル|  
|------------------------|-----------------------|--------------------------------------|  
|未送信のログ|未送信のログのサイズ (KB) を指定します。このサイズを超えると、プリンシパル サーバー インスタンスで警告が生成されます。 この警告は、サイズの観点からデータ損失の可能性を測定するのに役立ち、特に、高パフォーマンス モードに関連しています。 パートナーとの通信が切断されたためにミラーリングが一時停止または中断している場合は、高安全モードにも関係します。|**[未送信のログがしきい値を超えた場合に警告する]**|  
|未復元のログ|未復元のログのサイズ (KB) を指定します。このサイズを超えると、ミラー サーバー インスタンスで警告が生成されます。 この警告を使用すると、フェールオーバー時間を判断できます。 *フェールオーバー時間* の大部分は、以前のミラー サーバーの再実行キューに残っているログをロールフォワードする場合に必要となる時間です。この時間にわずかな時間を加えます。<br /><br /> 注: 自動フェールオーバーの場合、システムがエラーを通知するまでの時間は、フェールオーバー時間に関係ありません。<br /><br /> 詳細については、「[役割の交代中に発生するサービスの中断時間の算出 &#40;データベース ミラーリング&#41;](../../database-engine/database-mirroring/estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)」を参照してください。|**[復元されていないログがしきい値を超えた場合に警告する]**|  
|最も古い未送信のトランザクション|送信キュー内にトランザクションを累積できる時間 (分単位) を指定します。この時間を経過すると、プリンシパル サーバー インスタンスで警告が生成されます。 この警告は、時間の観点からデータ損失の可能性を測定するのに役立ち、特に、高パフォーマンス モードに関連しています。 パートナーとの通信が切断されたためにミラーリングが一時停止または中断している場合は、高安全モードにも関係します。|**[最も古い未送信のトランザクションの経過期間がしきい値を超えた場合に警告する]**|  
|ミラー コミットのオーバーヘッド|許容可能な、トランザクションあたりの平均遅延時間 (ミリ秒単位) を指定します。この時間を経過すると、プリンシパル サーバーで警告が生成されます。 この遅延時間は、ミラー サーバー インスタンスによってトランザクションのログ レコードが再実行キューに書き込まれるのをプリンシパル サーバー インスタンスが待機している間、発生したオーバーヘッドの量になります。 この値は高安全モードにのみ関係します。|**[ミラー コミットのオーバーヘッドがしきい値を超えた場合に警告する]**|  
  
 これらのパフォーマンス基準のいずれでも、システム管理者は、ミラー化されたデータベースでしきい値を指定できます。 詳細については、このトピックの「 [警告しきい値の設定と管理](#SetUpManageWarningThresholds)」を参照してください。  
  
##  <a name="SetUpManageWarningThresholds"></a> 警告しきい値の設定と管理  
 システム管理者は、主要なミラーリング パフォーマンス基準に 1 つ以上の警告しきい値を設定できます。 両方のパートナーの特定の警告に対してしきい値を設定し、データベースがフェールオーバーする場合に警告が保持されるようにすることをお勧めします。 各パートナーで適切なしきい値は、そのパートナーのシステムのパフォーマンス機能によって異なります。  
  
 警告しきい値は、次のいずれかを使用して設定および管理できます。  
  
-   データベース ミラーリング モニター (Database Mirroring Monitor)  
  
     データベース ミラーリング モニターでは、管理者は、 **[警告]** タブ ページをクリックして、プリンシパル サーバー インスタンスとミラー サーバー インスタンスの両方で選択したデータベースの警告の現在の構成を同時に確認できます。 そのページから、 **[警告しきい値の設定]** ダイアログ ボックスを開き、1 つ以上の警告しきい値を有効にして設定できます。  
  
     データベース ミラーリング モニターのインターフェイスの概要については、「 [Database Mirroring Monitor Overview](../../database-engine/database-mirroring/database-mirroring-monitor-overview.md)」を参照してください。 データベース ミラーリング モニターの起動方法については、「[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)」を参照してください。  
  
-   システム ストアド プロシージャ  
  
     次のシステム ストアド プロシージャを使用すると、管理者は、一度に 1 つのパートナーのミラー化されたデータベースで警告しきい値を設定および管理できます。  
  
    |手順|説明|  
    |---------------|-----------------|  
    |[sp_dbmmonitorchangealert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)|指定したミラーリングのパフォーマンス基準に対する警告しきい値を追加または変更します。|  
    |[sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)|データベース ミラーリング監視の主要なパフォーマンス基準の 1 つまたはすべてについて、警告しきい値に関する情報を返します。|  
    |[sp_dbmmonitordropalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)|指定したパフォーマンス基準に対する警告を削除します。|  
  
## Windows イベント ログに送信されるパフォーマンスしきい値イベント  
 パフォーマンス基準に警告しきい値を定義する場合、状態テーブルを更新すると、最新の値がそのしきい値に対して評価されます。 しきい値に達している場合は、更新用のプロシージャ **sp_dbmmonitorupdate** によって、基準に対する情報イベント (*パフォーマンスしきい値イベント*) が生成され、そのイベントが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows イベント ログに書き込まれます。 次の表は、パフォーマンスしきい値イベントのイベント ID を示しています。  
  
|パフォーマンス基準|イベント ID|  
|------------------------|--------------|  
|未送信のログ|32042|  
|未復元のログ|32043|  
|最も古い未送信のトランザクション|32040|  
|ミラー コミットのオーバーヘッド|32044|  
  
> [!NOTE]  
>  管理者は、これらのイベントの 1 つ以上で警告を定義できます。 詳細については、このトピックの「 [ミラー化されたデータベースに対する警告の使用](#UseAlerts)」を参照してください。  
>   
>  トピック  
  
##  <a name="UseAlerts"></a> ミラー化されたデータベースに対する警告の使用  
 ミラー化されたデータベースを監視する際に重要なのは、重大なデータベース ミラーリング イベントに対して警告を構成することです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、次のようなデータベース ミラーリング イベントが生成されます。  
  
-   パフォーマンスしきい値イベント  
  
     詳細については、このトピックの「Windows イベント ログに送信されるパフォーマンスしきい値イベント」を参照してください。  
  
-   状態変更イベント  
  
     データベース ミラーリング セッションの内部状態に変更が生じたときに生成される Windows Management Instrumentation (WMI) イベントです。  
  
    > [!NOTE]  
    >  詳細については、「[WMI Provider for Server Events の概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)」を参照してください。  
  
 システム管理者は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントまたは他のアプリケーション ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Operations Manager など) を使用して、これらのイベントに対して警告を構成できます。  
  
 データベース ミラーリング イベントで警告を定義する場合は、両方のパートナー サーバー インスタンスで警告しきい値と警告を定義することをお勧めします。 個々のイベントはプリンシパル サーバーまたはミラー サーバーのいずれかで生成されますが、各パートナーは常にどちらの役割も実行できます。 フェールオーバー後に警告が動作を続行するには、両方のパートナーで警告を定義する必要があります。  
  
 詳細については、 [SQL Server Web サイト](http://go.microsoft.com/fwlink/?linkid=62373)にあるデータベース ミラーリング イベントの警告に関するホワイト ペーパーを参照してください。 このホワイト ペーパーには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用した警告の構成方法、データベース ミラーリングの WMI イベント、およびサンプル スクリプトに関する情報が記載されています。  
  
> [!IMPORTANT]  
>  すべてのミラーリング セッションでは、状態変更イベントに対する警告を送信するようにデータベースを構成することを強くお勧めします。 状態変更は手動による構成の変更結果として予測される場合を除いて、データを損傷する可能性があります。 データを保護するには、予測されていない状態変更の原因を特定して解決します。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **SQL Server Management Studio を使用して警告を作成するには**  
  
-   [エラー番号を使用して警告を作成する](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [WMI イベント警告の作成](../../ssms/agent/create-a-wmi-event-alert.md)  
  
 **データベース ミラーリングを監視するには**  
  
-   [データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
-   [sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql.md)  
  
-   [sp_dbmmonitorchangealert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)  
  
-   [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)  
  
-   [sp_dbmmonitordropalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)  
  
-   [sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)  
  
-   [sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)  
  
-   [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)  
  
-   [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
-   [sp_dbmmonitorupdate &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql.md)  
  
## 参照  
 [データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [データベース ミラーリングの監視 &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
  