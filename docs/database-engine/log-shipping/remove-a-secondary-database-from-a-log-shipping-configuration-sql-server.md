---
title: "ログ配布構成からのセカンダリ データベースの削除 (SQL Server) | Microsoft Docs"
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
  - "削除、セカンダリ データベース"
  - "セカンダリ データベース [SQL Server], ログ配布"
  - "セカンダリ データベースの消去"
  - "セカンダリ データ ファイル [SQL Server], 削除"
  - "ログ配布 [SQL Server], セカンダリ データベース"
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
caps.latest.revision: 19
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 19
---
# ログ配布構成からのセカンダリ データベースの削除 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ログ配布セカンダリ データベースを削除する方法を説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してログ配布セカンダリ データベースを削除するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> 権限  
 ログ配布ストアド プロシージャには、**sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### ログ配布セカンダリ データベースを削除するには  
  
1.  現在のログ配布プライマリ サーバーである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を展開し、ログ配布プライマリ データベースを右クリックして **[プロパティ]** をクリックします。  
  
3.  **[ページの選択]**の **[トランザクション ログの配布]**をクリックします。  
  
4.  **[セカンダリ サーバー インスタンスとデータベース]**で、削除するデータベースをクリックします。  
  
5.  **[削除]**をクリックします。  
  
6.  **[OK]** をクリックすると構成が更新されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### セカンダリ データベースを削除するには  
  
1.  プライマリ サーバーで [sp_delete_log_shipping_primary_secondary](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql.md) を実行して、セカンダリ データベースに関する情報をプライマリ サーバーから削除します。  
  
2.  セカンダリ サーバーで [sp_delete_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md) を実行して、セカンダリ データベースを削除します。  
  
    > [!NOTE]  
    >  同じセカンダリ ID を持つセカンダリ データベースが他にない場合は、**sp_delete_log_shipping_secondary_primary** が **sp_delete_log_shipping_secondary_database** により呼び出され、セカンダリ ID のエントリ、およびコピー ジョブと復元ジョブが削除されます。  
  
3.  セカンダリ サーバーでコピー ジョブと復元ジョブを無効にします。 詳細については、「 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)」をご覧ください。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [SQL Server 2016 へのログ配布のアップグレード &#40;Transact-SQL&#41;](../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [ログ配布の構成 &#40;SQL Server&#41;](../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
-   [ログ配布構成へのセカンダリ データベースの追加 &#40;SQL Server&#41;](../../database-engine/log-shipping/add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [ログ配布の削除 &#40;SQL Server&#41;](../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   [ログ配布レポートの表示 &#40;SQL Server Management Studio&#41;](../../database-engine/log-shipping/view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [ログ配布の監視 &#40;Transact-SQL&#41;](../../database-engine/log-shipping/monitor-log-shipping-transact-sql.md)  
  
-   [ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;](../../database-engine/log-shipping/fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## 参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [ログ配布テーブルとストアド プロシージャ](../../database-engine/log-shipping/log-shipping-tables-and-stored-procedures.md)  
  
  