---
title: "データベース メール外部プログラム | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "外部プログラム [データベース メール]"
  - "DatabaseMail90.exe"
  - "データベース メール [SQL Server], 外部プログラム"
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
caps.latest.revision: 40
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 40
---
# データベース メール外部プログラム
  データベース メール外部実行可能ファイルは **DatabaseMail.exe** です。このファイルは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール環境の **MSSQL\Binn ディレクトリ**にあります。 データベース メールでは、処理する電子メール メッセージがあるときに、Service Broker のアクティブ化を使用して外部プログラムが起動されます。 次に、データベース メールによって外部プログラムの 1 つのインスタンスが開始されます。 外部プログラムは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサービス アカウントのセキュリティ コンテキストで実行されます。  
  
 **このトピックの内容**  
  
-   [データベース メール外部プログラムの概念](#ComponentsAndConcepts)  
  
-   [データベース メール外部プログラムの構成に関連するタスク](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> データベース メール外部プログラムの概念  
 外部プログラムが開始されるときに、プログラムによって Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続が行われ、電子メール メッセージの処理が開始されます。 指定されたタイムアウト期間内に送信するメッセージがなくなると、プログラムが終了します。 データベース メール構成ウィザードまたはデータベース メール ストアド プロシージャのいずれかを使用して、プログラムが終了するまでの時間を構成できます。 詳細については、「[sysmail_configure_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql.md)」を参照してください。  
  
 外部プログラムは、 **msdb** データベースのシステム テーブルに情報を保存します。 外部プログラムが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と通信できない場合は、プログラムによって、Microsoft Windows アプリケーション イベント ログにエラーが記録されます。 **データベース メール構成ウィザード** の **[システム パラメーターの構成]** ダイアログ ボックスでログのレベルを **[詳細]**に設定している場合、詳細なメッセージ ログが記録されます。  
  
 外部プログラムでは、効率を上げるために、アカウントやプロファイルに関する情報がキャッシュされることに注意してください。 そのため、アカウントやプロファイルの構成を変更しても、その変更が数分間、外部プログラムに反映されないことがあります。  
  
##  <a name="RelatedTasks"></a> データベース メール外部プログラムの構成に関連するタスク  
  
|構成タスク|トピック|  
|------------------------|----------------|  
|外部プログラムが終了するまでの時間を指定します。|[sysmail_configure_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql.md)|  
  
## 参照  
 [SQL Server Service Broker (SQL Server Service Broker)](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [データベース メールのログ記録と監査](../../relational-databases/database-mail/database-mail-log-and-audits.md)   
 [データベース メール](../../relational-databases/database-mail/database-mail.md)  
  
  