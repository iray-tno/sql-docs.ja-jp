---
title: "テーブル値パラメーターの使用 (データベース エンジン) | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テーブル値パラメーター"
  - "テーブル値パラメーター、テーブル値パラメーターについて"
  - "パラメーター [SQL Server]、テーブル値"
  - "TVP 「テーブル値パラメーター」を参照"
ms.assetid: 5e95a382-1e01-4c74-81f5-055612c2ad99
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# テーブル値パラメーターの使用 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  テーブル値パラメーターは、ユーザー定義テーブル型を使用して宣言されます。 テーブル値パラメーターを使用すると、一時テーブルまたは多数のパラメーターを作成せずに、ストアド プロシージャや関数などの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはルーチンに複数行のデータを送信できます。  
  
 テーブル値パラメーターは OLE DB や ODBC のパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。 テーブル値パラメーターには、セットベースの操作に使用できるという利点もあります。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] では、入力データのコピーが作成されないようにするために、テーブル値パラメーターがルーチンに参照渡しされます。 テーブル値パラメーターを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] ルーチンを作成して実行し、[!INCLUDE[tsql](../../includes/tsql-md.md)] コード、および任意のマネージ言語のマネージ クライアントとネイティブ クライアントから呼び出すことができます。  
  
 **このトピックの内容**  
  
 [利点](#Benefits)  
  
 [制限](#Restrictions)  
  
 [テーブル値パラメーターと BULK INSERT 操作](#BulkInsert)  
  
 [例](#Example)  
  
##  <a name="Benefits"></a> 利点  
 テーブル値パラメーターの対象範囲はストアド プロシージャ、関数、または動的な [!INCLUDE[tsql](../../includes/tsql-md.md)] テキストで、他のパラメーターと同じです。 同様に、テーブル型の変数の対象範囲も、DECLARE ステートメントを使用して作成される他のローカル変数と同じです。 テーブル値変数は、動的な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内で宣言でき、テーブル値パラメーターとしてストアド プロシージャおよび関数に渡すことができます。  
  
 テーブル値パラメーターは柔軟性が高く、一時テーブルやその他の方法でパラメーターの一覧を渡す場合よりもパフォーマンスが向上することもあります。 テーブル値パラメーターには、次の利点があります。  
  
-   クライアントからのデータを最初に設定する際にロックを取得しません。  
  
-   単純なプログラミング モデルを提供します。  
  
-   複雑なビジネス ロジックを 1 つのルーチンに含めることができます。  
  
-   サーバーへのラウンド トリップが減少します。  
  
-   基数が異なるテーブル構造を含めることができます。  
  
-   厳密に型指定されます。  
  
-   クライアントで並べ替え順序と一意キーを指定できます。  
  
-   ストアド プロシージャで使用すると、一時テーブルのようにキャッシュされます。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、テーブル値パラメーターはパラメーター化クエリ用にもキャッシュされます。  
  
##  <a name="Restrictions"></a> 制限  
 テーブル値パラメーターには、次の制限があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でテーブル値パラメーターの列の統計が保持されません。  
  
-   テーブル値パラメーターは、READONLY 入力パラメーターとして [!INCLUDE[tsql](../../includes/tsql-md.md)] ルーチンに渡す必要があります。 ルーチン本体でテーブル値パラメーターに対して UPDATE、DELETE、INSERT などの DML 操作を実行することはできません。  
  
-   SELECT INTO または INSERT EXEC ステートメントの対象としてテーブル値パラメーターを使用することはできません。 テーブル値パラメーターは、SELECT INTO の FROM 句か、INSERT EXEC 文字列またはストアド プロシージャに含めることができます。  
  
##  <a name="BulkInsert"></a> テーブル値パラメーターと BULK INSERT 操作  
 テーブル値パラメーターの使用はセットベースの変数を使用するその他の方法に似ていますが、多くの場合、大規模なデータセットを処理するときは、テーブル値パラメーターを使用する方が短時間で済みます。 テーブル値パラメーターよりもスタートアップ コストがかかる一括操作と比較すると、1,000 行未満の行を挿入する場合は、テーブル値パラメーターの方がパフォーマンスが高くなります。  
  
 再利用されるテーブル値パラメーターの場合、一時テーブル キャッシュを使用するとメリットがあります。 このテーブル キャッシュを使用すると、同等の BULK INSERT 操作よりもスケーラビリティが向上します。 少数の行の挿入操作では、BULK INSERT 操作またはテーブル値パラメーターではなく、パラメーター一覧またはバッチにまとめられたステートメントを使用すると、パフォーマンス上の利点が多少得られる場合があります。 ただし、これらの方法はプログラミングが容易ではなく、行が増えるとすぐにパフォーマンスが低下します。  
  
 テーブル値パラメーターは、同等のパラメーター配列の実装と同様またはそれ以上のパフォーマンスを実現します。  
  
##  <a name="Example"></a> 例  
 次の例では、[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、テーブル値パラメーターの型を作成してその型を参照する変数を宣言し、パラメーター一覧を入力して値をストアド プロシージャに渡す方法を示します。  
  
```  
USE AdventureWorks2012;  
GO  
  
/* Create a table type. */  
CREATE TYPE LocationTableType AS TABLE   
( LocationName VARCHAR(50)  
, CostRate INT );  
GO  
  
/* Create a procedure to receive data for the table-valued parameter. */  
CREATE PROCEDURE dbo. usp_InsertProductionLocation  
    @TVP LocationTableType READONLY  
    AS   
    SET NOCOUNT ON  
    INSERT INTO AdventureWorks2012.Production.Location  
           (Name  
           ,CostRate  
           ,Availability  
           ,ModifiedDate)  
        SELECT *, 0, GETDATE()  
        FROM  @TVP;  
        GO  
  
/* Declare a variable that references the type. */  
DECLARE @LocationTVP AS LocationTableType;  
  
/* Add data to the table variable. */  
INSERT INTO @LocationTVP (LocationName, CostRate)  
    SELECT Name, 0.00  
    FROM AdventureWorks2012.Person.StateProvince;  
  
/* Pass the table variable data to a stored procedure. */  
EXEC usp_InsertProductionLocation @LocationTVP;  
GO  
```  
  
## 参照  
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [sys.parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)   
 [sys.parameter_type_usages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)  
  
  