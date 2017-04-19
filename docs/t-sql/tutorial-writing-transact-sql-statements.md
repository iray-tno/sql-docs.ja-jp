---
title: "チュートリアル : Transact-SQL ステートメントの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "08/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "Transact-SQL ステートメント, チュートリアル"
  - "Transact-SQL のチュートリアル"
  - "チュートリアル [Transact-SQL]"
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# チュートリアル : Transact-SQL ステートメントの作成
[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの作成チュートリアルへようこそ。 このチュートリアルは、SQL ステートメントを初めて作成するユーザーを対象としています。 ここでは初心者のユーザーを対象に、テーブルを作成し、データを挿入するための基本的なステートメントを紹介します。 このチュートリアルでは、[!INCLUDE[tsql](../includes/tsql-md.md)] 製品に実装されている SQL 規格の [!INCLUDE[msCoName](../includes/msconame-md.md)] を使用します。 このチュートリアルは、[!INCLUDE[tsql](../includes/tsql-md.md)] 言語を簡単に紹介することを目的としています。[!INCLUDE[tsql](../includes/tsql-md.md)] クラスの代わりとなるものではありません。 このチュートリアルで使用するステートメントは意図的に簡潔化されており、通常の実稼働データベースに見られる複雑性を表すものではありません。  
  
>**注:** 初心者の方には、[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを記述するのでなく、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の使用をお勧めします。  
  
## 詳細情報  
特定のステートメントの詳細については、SQL Server オンライン ブックで名前を指定してステートメントを検索するか、[コンテンツ] を使用して、[Transact-SQL リファレンス (データベース エンジン)](../t-sql/transact-sql-reference-database-engine.md) の下にアルファベット順に列挙されている 1,800 の言語要素を参照してください。 情報を検索する別の方法として、興味のある内容に関連するキーワードを検索する方法があります。 たとえば、日付の一部 (月など) を返す方法を求めるには、**日付 [SQL Server]** のインデックスを検索し、**日付要素**を選択します。 これにより、トピック [「DATEPART (Transact-SQL)」](../t-sql/functions/datepart-transact-sql.md) が表示されます。 別の例として、文字列の操作方法を求めるには、**文字列関数**を検索します。 これにより、トピック [「文字列関数 (Transact-SQL)」](../t-sql/functions/string-functions-transact-sql.md) が表示されます。  
  
## 学習する内容  
このチュートリアルでは、データベースの作成、データベースのテーブルの作成、テーブルへのデータの挿入、データの更新、読み取り、削除、およびテーブルの削除の方法を示します。 ユーザーは、ビューやストアド プロシージャを作成し、データベースとデータのユーザーを構成します。  
  
このチュートリアルは、次の 3 つのレッスンで構成されています。  
  
[レッスン 1: データベース オブジェクトの作成](../t-sql/lesson-1-creating-database-objects.md)  
このレッスンでは、データベースを作成し、データベースにテーブルを作成し、データをテーブルに挿入します。さらに、データを更新し、読み取ります。  
  
[レッスン 2: データベース オブジェクトに対する権限の構成](../t-sql/lesson-2-configuring-permissions-on-database-objects.md)  
このレッスンでは、ログインとユーザーを作成します。 また、ビューとストアド プロシージャも作成し、ストアド プロシージャにユーザー権限を与えます。  
  
[レッスン 3: データベース オブジェクトの削除](../t-sql/lesson-3-deleting-database-objects.md)  
このレッスンでは、データへのアクセス権を削除し、データをテーブルから削除し、テーブル、次にデータベースを削除します。  
  
## 必要条件  
このチュートリアルを完了するにあたって SQL 言語に関する知識は必要ありませんが、テーブルなどの基本的なデータベース概念は理解している必要があります。 このチュートリアルでは、データベースと Windows ユーザーを作成します。 これらのタスクには高レベルのアクセス許可が必要なので、コンピューターには管理者としてログインしてください。  
  
システムには次のコンポーネントがインストールされている必要があります。  
  
-   任意のエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-  [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)  
  

 
  
  
  