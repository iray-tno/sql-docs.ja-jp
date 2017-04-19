---
title: "データベースのサイズを大きくする | Microsoft Docs"
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
  - "サイズのデータベース [SQL Server]"
  - "データベース サイズの拡大"
  - "データベース サイズ [SQL Server], 拡大"
  - "サイズ [SQL Server], データベース"
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# データベースのサイズを大きくする
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースのサイズを大きくする方法について説明します。 既存のデータ ファイルまたはログ ファイルのサイズを大きくするか、データベースに新しいファイルを追加することで、データベースを拡張します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してデータベースのサイズを大きくするには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   BACKUP ステートメントの実行中にファイルを追加したり削除したりすることはできません。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 データベースに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### データベースのサイズを大きくするには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  [**データベース**] を展開し、サイズを大きくするデータベースを右クリックして、[**プロパティ**] をクリックします。  
  
3.  **[データベースのプロパティ]**ダイアログ ボックスで、 **[ファイル]** ページをクリックします。  
  
4.  既存のファイルのサイズを大きくするには、目的のファイルの [**初期サイズ (MB)**] 列の値を大きくします。 データベースのサイズは、少なくとも 1 MB ずつ大きくする必要があります。  
  
5.  新しいファイルを追加してデータベースのサイズを大きくするには、 **[追加]** をクリックして、新しいファイルの値を入力します。 詳細については、「 [Add Data or Log Files to a Database](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)」をご覧ください。  
  
6.  クリックして **OK**です。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### データベースのサイズを大きくするには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、`test1dat3` ファイルのサイズを拡張します。  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../relational-databases/databases/codesnippet/tsql/increase-the-size-of-a-d_1.sql)]  
  
 その他の例については、「[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md)」をご覧ください。  
  
## 参照  
 [データベースに対するデータ ファイルまたはログ ファイルの追加](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)   
 [データベースの圧縮](../../relational-databases/databases/shrink-a-database.md)  
  
  