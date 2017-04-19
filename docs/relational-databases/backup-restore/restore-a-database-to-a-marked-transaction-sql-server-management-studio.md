---
title: "マークされたトランザクションへのデータベースの復元 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.restoretlog.markedtransaction.f1"
helpviewer_keywords: 
  - "データベース復元 [SQL Server], マークされたトランザクション"
  - "データベースの復元 [SQL Server], マークされたトランザクション"
  - "マークされたトランザクション [SQL Server], 復元"
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# マークされたトランザクションへのデータベースの復元 (SQL Server Management Studio)
  データベースが復元中の状態である場合、**[トランザクション ログの復元]** ダイアログ ボックスを使用して、使用可能なログ バックアップのマークされたトランザクションにデータベースを復元できます。  
  
> [!NOTE]  
>  詳細については、「[マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル#41;](../../relational-databases/backup-restore/use marked transactions to recover related databases consistently.md)」および「[マークされたトランザクションを含む関連データベースの復旧](../../relational-databases/backup-restore/recovery-of-related-databases-that-contain-marked-transaction.md)」を参照してください。  
  
### マークされたトランザクションを復元するには  
  
1.  オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。  
  
2.  **[データベース]**を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。  
  
3.  データベースを右クリックして **[タスク]** をポイントし、**[復元]** をクリックします。  
  
4.  **[トランザクション ログ]** をクリックして **[トランザクション ログの復元]** ダイアログ ボックスを開きます。  
  
5.  **[全般]** ページの **[復元先]** で、**[マークされたトランザクション]** をクリックします。**[マークされたトランザクションの選択]** ダイアログ ボックスが開きます。 このダイアログ ボックスには、選択したトランザクション ログ バックアップで使用できるマークされたトランザクションを一覧表示するグリッドが表示されます。  
  
     既定では、マークされたトランザクションの前まで復元され、マークされたトランザクションは復元されません。 マークされたトランザクションも復元するには、 **[マークされたトランザクションを含める]**チェック ボックスをオンにします。  
  
     次の表は、グリッドの列ヘッダーとその値を示しています。  
  
    |[ヘッダー]|値|  
    |------------|-----------|  
    |\<blank>|マークを選択するためのチェック ボックスを表示します。|  
    |**トランザクション マーク**|トランザクションがコミットされたときにユーザーによって指定された、マークされたトランザクションの名前。|  
    |**日付**|トランザクションがコミットされた日時。 トランザクションの日付と時刻は、クライアント コンピューターの日付と時刻ではなく、**msdbgmarkhistory** テーブルに記録されたとおりに表示されます。|  
    |**説明**|トランザクションがコミットされたときにユーザーが指定したマークされたトランザクションの説明 (該当する場合)。|  
    |**LSN (LSN)**|マークされたトランザクションのログ シーケンス番号。|  
    |**データベース**|マークされたトランザクションがコミットされたデータベースの名前。|  
    |**[ユーザー名]**|マークされたトランザクションをコミットしたデータベース ユーザーの名前。|  
  
## 参照  
 [SSMS を使用してデータベース バックアップを復元する](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
  