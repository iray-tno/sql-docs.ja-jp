---
title: "BULK INSERT または OPENROWSET(BULK...) を使用した一括データのインポート (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "07/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BULK INSERT ステートメント, リモート データ ファイルからのデータのインポート"
  - "一括インポート [SQL Server], 方法"
  - "一括エクスポート [SQL Server], 方法"
  - "OPENROWSET 関数, BULK INSERT"
  - "一括インポート [SQL Server], セキュリティ"
  - "一括行セット プロバイダー [SQL Server]"
  - "一括エクスポート [SQL Server]、BULK INSERT ステートメント"
  - "リモート データ アクセス [SQL Server], 一括インポート"
  - "一括インポート [SQL Server]、BULK INSERT ステートメント"
  - "Transact-SQL 一括エクスポートおよびインポート操作"
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
caps.latest.revision: 45
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 44
---
# BULK INSERT または OPENROWSET(BULK...) を使用した一括データのインポート (SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  このトピックでは、[!INCLUDE[tsql](../../includes/tsql-md.md)] の BULK INSERT ステートメントと INSERT...SELECT * FROM OPENROWSET(BULK...) ステートメントを使用して、データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルにデータを一括インポートする方法の概要を説明します。 また、BULK INSERT および OPENROWSET(BULK...) を使用する場合のセキュリティの注意点や、リモート データ ソースから一括インポートする方法についても説明します。  
  
> **注:** BULK INSERT または OPENROWSET(BULK...) を使用する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンで権限の借用がどのように処理されるかを理解しておくことが重要です。 詳細については、後の「セキュリティの注意点」を参照してください。  
  
## BULK INSERT ステートメント  
 BULK INSERT では、データ ファイルからテーブルにデータが読み込まれます。 この機能は、 **bcp** コマンドの **in** オプションと似ていますが、データ ファイルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスによって読み取られる点が異なります。 BULK INSERT の構文の説明については、「[BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。  
  
## BULK INSERT の例  
 
  
-   [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
-   [XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## OPENROWSET(BULK...) 関数  
 OPENROWSET 一括行セット プロバイダーには、BULK オプションを指定して OPENROWSET 関数を呼び出すことによってアクセスします。 OPENROWSET(BULK...) 関数では、OLE DB プロバイダー経由でデータ ファイルなどのリモート データ ソースに接続することで、リモート データにアクセスできます。  
  
 データを一括インポートするには、INSERT ステートメントの SELECT...FROM 句から OPENROWSET(BULK...) を呼び出します。 データの一括インポートの基本構文は次のとおりです。  
  
 INSERT ...SELECT * FROM OPENROWSET(BULK...)  
  
 OPENROWSET(BULK...) を INSERT ステートメント内で使用する場合は、テーブル ヒントがサポートされます。 BULK 句では、TABLOCK などの通常のテーブル ヒント以外に、特殊なテーブル ヒント IGNORE_CONSTRAINTS (CHECK 制約だけを無視)、IGNORE_TRIGGERS、KEEPDEFAULTS、KEEPIDENTITY を使用できます。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md)」を参照してください。  
  
 BULK オプションの上記以外の使い方の詳細については、「[OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)」を参照してください。  
  
## INSERT...SELECT * FROM OPENROWSET(BULK...) ステートメント - 例:
  
-   [XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## セキュリティに関する考慮事項  
 ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス アカウントのセキュリティ プロファイルが使用されます。 SQL Server 認証を使用したログインは、データベース エンジン以外では認証できません。 そのため、SQL Server 認証を使用したログインによって BULK INSERT コマンドが開始されると、SQL Server プロセス アカウント (SQL Server データベース エンジン サービスで使用されるアカウント) のセキュリティ コンテキストを使用してデータへの接続が行われます。 
 
 ソース データを正しく読み取るには、SQL Server データベース エンジンで使用されるアカウントに対して、ソース データへのアクセス権を付与する必要があります。 これに対して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーが Windows 認証を使用してログインした場合、そのユーザーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスのセキュリティ プロファイルに関係なく、そのユーザー アカウントでアクセス可能なファイルのみを読み取ることができます。  
  
 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに Windows 認証を使用してログインしたユーザーを考えます。 ユーザーが BULK INSERT または OPENROWSET を使用してデータ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータをインポートするには、アカウントにデータ ファイルの読み取りアクセス許可が与えられていなければなりません。 データ ファイルへのアクセスで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスにそのファイルへのアクセス許可がなくても、ユーザーはそのファイルからテーブルにデータをインポートできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスにファイル アクセス許可を与える必要はありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows では、認証されている Windows ユーザーの資格情報を転送することで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスから別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへ接続できるように構成することが可能です。 この設定を、" *権限借用* " または " *権限委譲*" といいます。 BULK INSERT または OPENROWSET を使用する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンによってユーザーの権限借用のセキュリティがどのように処理されるかを理解しておくことが重要です。 ユーザーの権限を借用することで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスまたはユーザーのいずれかが使用しているコンピューターとは異なるコンピューターにデータ ファイルを常駐させることができます。 たとえば、**Computer_A** 上のユーザーが **Computer_B** 上のデータ ファイルにアクセスでき、資格情報の委任が適切に設定されている場合、このユーザーは、**Computer_C** 上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続して、**Computer_B** 上のデータ ファイルにアクセスし、そのファイルから **Computer_C** 上のテーブルにデータを一括インポートできます。  
  
## リモート データ ファイルからの一括インポート  
 BULK INSERT または INSERT...SELECT \* FROM OPENROWSET(BULK...) を使用して別のコンピューターからデータを一括インポートするには、データ ファイルを 2 台のコンピューター間で共有している必要があります。 共有データ ファイルを指定するには、UNC (汎用名前付け規則) 名を使用します。UNC 名の一般的な形式は、**\\\\***Servername***\\***Sharename***\\***Path***\\***Filename* です。 また、データ ファイルへのアクセスに使用されるアカウントは、リモート ディスク上のファイルの読み取りに必要な権限を持っている必要があります。  
  
 たとえば、次の `BULK INSERT` ステートメントでは、 `SalesOrderDetail` というデータ ファイルから `AdventureWorks` データベースの `newdata.txt`テーブルにデータの一括インポートを行います。 このデータ ファイルは、`\dailyorders` というシステムの `salesforce` というネットワーク共有ディレクトリの `computer2` という共有フォルダーにあります。  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> **注:** クライアントが読み取るファイルは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とは無関係であるため、**bcp** にはこの制限は適用されません。  
  
## 参照  
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-clause-transact-sql.md)   
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
  