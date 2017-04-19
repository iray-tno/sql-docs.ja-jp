---
title: "リンク サーバー (データベース エンジン) | Microsoft Docs"
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
  - "OLE DB, リンク サーバー"
  - "OLE DB プロバイダー, リンク サーバー"
  - "サーバー管理 [SQL Server], リンク サーバー"
  - "リンク サーバー [SQL Server]"
  - "分散クエリ [SQL Server], リンク サーバー"
  - "サーバー [SQL Server], リンク"
  - "リモート サーバー [SQL Server], リンク サーバー"
  - "リンク サーバー [SQL Server], リンク サーバーについて"
ms.assetid: 6ef578bf-8da7-46e0-88b5-e310fc908bb0
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# リンク サーバー (データベース エンジン)
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスの外に存在する OLE DB データ ソースに対し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からコマンドを実行できるようにするには、リンク サーバーを構成します。 通常、リンク サーバーを構成する目的は、[!INCLUDE[ssDE](../../includes/ssde-md.md)] の別のインスタンスまたは別のデータベース製品 (Oracle など) のテーブルを含んだ [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]から実行できるようにすることです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] の Access や Excel など、さまざまな種類の OLE DB データ ソースをリンク サーバーとして構成できます。 リンク サーバーには次の利点があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の外部のデータにアクセスできる。  
  
-   企業内のさまざまなデータ ソースに対して分散クエリ、更新、コマンド、およびトランザクションを実行できる。  
  
-   さまざまなデータ ソースを同じように処理できる。  
  
 リンク サーバーの構成は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) ステートメントを使用して行うことができます。 各 OLE DB プロバイダーは、必要なパラメーターの数と型という点で大きく異なります。 たとえば、プロバイダーによっては、[sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md) を使用して、接続のセキュリティ コンテキストを指定する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から OLE DB ソース上のデータを更新できる OLE DB プロバイダーもあれば、 読み取り専用データ アクセスに特化したものも存在します。 各 OLE DB プロバイダーの詳細については、該当する OLE DB プロバイダーのドキュメントを参照してください。  
  
## リンク サーバーのコンポーネント  
 リンク サーバーの定義では、次のオブジェクトを指定します。  
  
-   OLE DB プロバイダー  
  
-   OLE DB データ ソース  
  
 *OLE DB プロバイダー*は、特定のデータ ソースを管理し、相互運用する DLL です。 *OLE DB データ ソース*は、OLE DB を使用してアクセスできる特定のデータベースを識別します。 リンク サーバーの定義を使用してクエリが行われるデータ ソースは通常はデータベースですが、さまざまなファイルやファイル形式用の OLE DB プロバイダーが存在します。 これには、テキスト ファイル、ワークシートのデータ、およびフルテキスト検索の結果が含まれます。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー (PROGID: SQLNCLI11) は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の公式の OLE DB プロバイダーです。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散クエリは、必要な OLE DB インターフェイスを実装しているすべての OLE DB プロバイダーで処理できるように設計されています。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーなど、特定のプロバイダーに対してのみテストが行われています。  
  
## リンク サーバーの詳細  
 次の図に、基本的なリンク サーバー構成を示します。  
  
 ![クライアント層、サーバー層、およびデータベース サーバー層](../../relational-databases/linked-servers/media/lsvr.gif "クライアント層、サーバー層、およびデータベース サーバー層")  
  
 リンク サーバーは、通常は分散クエリの処理に使用します。 クライアント アプリケーションからリンク サーバー経由で分散クエリが実行されるときは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でコマンドが解析され、OLE DB に要求が送信されます。 行セット要求は、プロバイダーに対するクエリの実行や、プロバイダーのベース テーブルを開くなどの形式をとります。  
  
 データ ソースがリンク サーバー経由でデータを返すには、そのデータ ソースの OLE DB プロバイダー (DLL) が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスと同じサーバー上に存在する必要があります。  
  
 サード パーティの OLE DB プロバイダーを使用しているときは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを実行しているアカウントに、プロバイダーがインストールされているディレクトリとそのすべてのサブディレクトリの読み取り権限と実行権限が必要です。  
  
## プロバイダーの管理  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が OLE DB プロバイダーを読み込んで使用する方法を制御する一連のオプションは、レジストリで指定されます。  
  
## リンク サーバー定義の管理  
 リンク サーバーをセットアップするときは、接続情報とデータ ソース情報を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録します。 登録後、1 つの論理名でデータ ソースを参照できます。  
  
 ストアド プロシージャとカタログ ビューを使用して、リンク サーバーの定義を管理できます。  
  
-   **sp_addlinkedserver** を実行して、リンク サーバーの定義を作成します。  
  
-   **sys.servers** システム カタログ ビューに対してクエリを実行して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスに定義されたリンク サーバーに関する情報を表示します。  
  
-   **sp_dropserver** を実行して、リンク サーバーの定義を削除します。 このストアド プロシージャを使用して、リモート サーバーを削除することもできます。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、リンク サーバーを定義することもできます。 オブジェクト エクスプローラーで **[サーバー オブジェクト]** を右クリックし、**[新規作成]** をポイントして、**[リンク サーバー]** をクリックします。 リンク サーバー名を右クリックして **[削除]** をクリックすると、リンク サーバーの定義を削除できます。  
  
 リンク サーバーに対して分散クエリを実行する場合は、クエリを実行するデータ ソースごとに 4 つの部分で構成される完全修飾テーブル名を指定します。 この 4 つの部分で構成される名前は、*linked_server_name.catalog***.***schema***.***object_name* という形式にする必要があります。  
  
> [!NOTE]  
>  リンク サーバーは、どのサーバーで定義されたかを示す (ループ バックする) ように定義することができます。 ループバック サーバーは、単一のサーバー ネットワークで分散クエリを使用するアプリケーションをテストする際に最も有効です。 ループバック リンク サーバーはテスト用であり、分散トランザクションなどの多くの操作ではサポートされていません。  
  
## 関連タスク  
 [リンク サーバーの作成 &#40;SQL Server データベース エンジン&#41;](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)  
  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)  
  
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)  
  
## 関連コンテンツ  
 [sys.servers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-servers-transact-sql.md)  
  
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)  
  
  