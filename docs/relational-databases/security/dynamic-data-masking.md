---
title: "動的なデータ マスキング | Microsoft Docs"
ms.custom: ""
ms.date: "09/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a62f4ff9-2953-42ca-b7d8-1f8f527c4d66
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# 動的なデータ マスキング
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

![動的なデータ マスキング](../../relational-databases/security/media/dynamic-data-masking.png)

動的データ マスク (DDM) は、特権のないユーザーに対してデリケートなデータをマスクし、データの公開を制限します。 DDM を使用すると、アプリケーションのセキュリティの設計とコーディングを大幅に簡略化することができます。  

動的データ マスクでは、公開するデリケートなデータの量を指定することで、そのようなデータに対する未承認のアクセスを防ぎ、アプリケーション レイヤーへの影響が最小限に抑えられます。 DDM は、指定されたデータベース フィールドで、データベースのクエリの結果セットに含まれる機密データを隠蔽し、データベースのデータを変更しないように構成できます。 動的データ マスクは、クエリの結果にマスク ルールが適用されるため、既存のアプリケーションで簡単に使用できます。 多くのアプリケーションは、既存のクエリを変更せずに、デリケートなデータをマスクすることができます。

*  中央のデータ マスク ポリシーは、データベースの機密フィールドに対して直接動作します。
*  機密データに対するアクセス権を持つ特権のあるユーザーまたはロールを指定します。
*  DDM には、フル マスク関数、部分マスク関数だけでなく、数値データ用のランダム マスクがあります。
*  単純な [!INCLUDE[tsql_md](../../includes/tsql-md.md)] コマンドで、マスクを定義し、管理します。

たとえば、コール センターのサポート担当者は、社会保障番号やクレジット カード番号などの数桁から顧客を識別することがありますが、これらのデータ項目をサポート担当者にすべて公開するべきではありません。 クエリの結果セットの社会保障番号やクレジット カード番号の末尾 4 桁を除くすべての番号をマスクするマスク ルールを設定することができます。 また、別の例として、適切なデータ マスクを使用して、個人を特定できる情報 (PII) データを保護すると、開発者は法令遵守規定に違反せずに、トラブルシューティングを行うために運用環境に対してクエリを実行することができます。

 動的データ マスクの目的は、アクセスすべきではないユーザーがデータを閲覧することを防ぎ、デリケートなデータの公開を制限することにあります。 動的データ マスクは、ユーザーが直接データベースに接続し、徹底的なクエリを実行して、デリケートなデータの漏えいを防ぐことを目的としてはいません。 動的データ マスクは、その他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ機能 (監査、暗号化、行レベルのセキュリティなど) を補完します。 データベース内のデリケートなデータの保護をより強化するために、セキュリティ機能と連携して動的データ マスクを使用することをお勧めします。  
  
 動的データ マスクは [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] と [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] で使用できます。[!INCLUDE[tsql](../../includes/tsql-md.md)] をコマンドを使用して構成します。 Azure ポータルで動的データ マスクを構成する方法の詳細については、「[SQL Database 動的データ マスクの使用 (Azure ポータル)](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)」を参照してください。  
  
## 動的データ マスクを定義する  
 マスク ルールは、列のデータを難読化するために、テーブル内の列で定義することがあります。 4 種類のマスクを利用できます。  
  
|関数|説明|使用例|  
|--------------|-----------------|--------------|  
|既定値|指定のフィールドのデータ型に応じたフル マスク。<br /><br /> 文字列データ型 (**char**、**nchar**、**varchar**、**nvarchar**、**text**、**ntext**) のフィールドのサイズが 4 文字未満の場合は、XXXX またはそれ未満の数の X を使用します。  <br /><br /> 数値データ型 (**bigint**、**bit**、**decimal**、**int**、**money**、**numeric**、**smallint**、**smallmoney**、**tinyint**、**float**、**real**) の場合は値 0 を使用します。<br /><br /> 日付/時刻のデータ型 (**date**、**datetime2**、**datetime**、**datetimeoffset**、**smalldatetime**、**time**) の場合は、01.01.1900 00:00:00.0000000 を使用します。<br /><br />バイナリ データ型 (**binary**、**varbinary**、**image**) の場合は、ASCII 値 0 のシングル バイトを使用します。|列定義の構文例: `Phone# varchar(12) MASKED WITH (FUNCTION = 'default()') NULL`<br /><br /> ALTER 構文例: `ALTER COLUMN Gender ADD MASKED WITH (FUNCTION = 'default()')`|  
|Email|メール アドレスの最初の 1 文字と定数サフィックスの ".com" をメール アドレスのフォームで公開するマスク方法。 」を参照してください。 `aXXX@XXXX.com`」を参照してください。|定義の構文例: `Email varchar(100) MASKED WITH (FUNCTION = 'email()') NULL`<br /><br /> ALTER 構文例: `ALTER COLUMN Email ADD MASKED WITH (FUNCTION = 'email()'`|  
|ランダム|ランダム マスク関数は任意の数字型に使用でき、指定した範囲内で生成したランダムな値でオリジナルの値をマスクします。|定義の構文例: `Account_Number bigint MASKED WITH (FUNCTION = 'random([start range], [end range])')`<br /><br /> ALTER 構文例: `ALTER COLUMN [Month] ADD MASKED WITH (FUNCTION = 'random(1, 12)')`|  
|カスタム文字列|間にカスタム埋め込み文字列を追加し、最初と最後の文字を公開するマスク方法。 `prefix,[padding],suffix`<br /><br /> 注: 元の文字列が全体をマスクするには短すぎる場合、プレフィックスまたはサフィックスの一部は公開されません。|定義の構文例: `FirstName varchar(100) MASKED WITH (FUNCTION = 'partial(prefix,[padding],suffix)') NULL`<br /><br /> ALTER 構文例: `ALTER COLUMN [Phone Number] ADD MASKED WITH (FUNCTION = 'partial(1,"XXXXXXX",0)')`<br /><br /> その他の例:<br /><br /> `ALTER COLUMN [Phone Number] ADD MASKED WITH (FUNCTION = 'partial(5,"XXXXXXX",0)')`<br /><br /> `ALTER COLUMN [Social Security Number] ADD MASKED WITH (FUNCTION = 'partial(0,"XXX-XX-",4)')`|  
  
## Permissions  
 動的データ マスクでテーブルを作成するのに特別なアクセス許可は要りません。スキーマ アクセス許可に対する **CREATE TABLE** と **ALTER** のみ必要です。  
  
 列のマスクを追加、置換、削除するには、 **ALTER ANY MASK** アクセス許可と、テーブルに対する **ALTER** アクセス許可が必要です。 セキュリティの責任者には、 **ALTER ANY MASK** の付与が適切です。  
  
 テーブルに対して **SELECT** アクセス許可を持つユーザーは、テーブル データを閲覧できます。 マスク済みとして定義されている列には、マスクされたデータが表示されます。 **UNMASK** アクセス許可を付与されたユーザーは、マスクが定義された列から、マスクを解除したデータを取得できます。  
  
 データベースに対する **CONTROL** アクセス許可には、 **ALTER ANY MASK** と **UNMASK** の両方のアクセス許可が含まれます。  
  
## ベスト プラクティスと一般的なユース ケース  
  
-   列にマスクを作成しても、その列に対する更新を妨げることはありません。 マスクされた列にクエリを実行すると、ユーザーはマスクされたデータを受け取りますが、書き込みアクセス許可があるユーザーは、データを更新できます。 更新する許可を制限するために、適切なアクセス制御ポリシーを使用する必要があります。  
  
-   	`SELECT INTO` または `INSERT INTO` を使用して、マスクされた列を別のテーブルにコピーすると、対象のテーブルにマスクされたデータが表示されます。  
  
-   動的データ マスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートとエクスポートを実行すると適用されます。 マスクされた列を含むデータベースは、マスクされたデータを含むバックアップ ファイルを生成し (**UNMASK** 特権がないユーザーがエクスポートしたことを前提とします)、インポートされたデータベースは、マスクされたデータを静的に格納します。  
  
## マスクされた列に対してクエリを実行する  
 **sys.masked_columns** ビューを使用して、マスク関数が適用されたテーブルの列に対してクエリを実行します。 このビューが継承、 **sys.columns** ビューです。 **sys.columns** ビューのすべての列と、**is_masked** 列および **masking_function** 列を返して、マスクされた列かどうかを示し、マスクされた列の場合は、どのようなマスキング関数が定義されているかを示します。 これは、列があるマスキング関数が適用されるは表示のみを表示します。  
  
```  
SELECT c.name, tbl.name as table_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.[object_id] = tbl.[object_id]  
WHERE is_masked = 1;  
```  
  
## 制限事項と制約事項  
 次の列の型には、マスク ルールを定義することはできません。  
  
-   暗号化された列 (常に暗号化されます)  
  
-   FILESTREAM  
  
-   COLUMN_SET、または列セットの一部であるスパース列  
  
-   マスクは計算列に構築できません。ただし、計算列が MASK を所有する列に依存する場合は、計算列がマスクされたデータを返します。  
  
-   データ マスクを持つ列を FULLTEXT インデックスのキーにすることはできません。  
  
 **UNMASK** アクセス許可のないユーザーの場合、使用されていない **READTEXT**、 **UPDATETEXT**、および **WRITETEXT** ステートメントは、動的データ マスク用に構成された列で適切に動作しません。 
 
 動的データ マスクの追加は基になっているテーブルでのスキーマ変更として実装されるため、依存関係を持つ列では実行できません。 この制限を回避するには、最初に依存関係を削除してから、動的データ マスクを追加した後、依存関係を再作成します。 たとえば、依存関係がその列に依存するインデックスによるものである場合は、インデックスを削除し、マスクを追加してから、依存するインデックスを再作成します。
 

## セキュリティに関する注意: 推論またはブルートフォース手法を使用してマスクをバイパスする

動的データ マスクは、アプリケーションに使用される事前定義されたクエリ セットのデータ公開を制限することで、アプリケーション開発を単純化するために設計されています。 動的データ マスクは、実稼働データベースに直接アクセスするときに機密データが誤って公開されることを防ぐためにも有効ですが、アドホック クエリ アクセス許可を持つ特権のないユーザーが、実際のデータに対するアクセス権を得る手法を適用する可能性にも注意する必要があります。 このようなアドホック アクセス権を付与する必要がある場合、すべてのデータベース操作を監視し、このシナリオを軽減するために監査を使用することをお勧めします。
 
たとえば、データベースに対してアドホック クエリを実行する十分な特権を持つデータベース プリンシパルがいて、基になるデータを ’推測’ し、最終的には実際の値を推測しようと試みているとします。 管理者は `[Employee].[Salary]` 列に対してマスクを定義しましたが、このユーザーはデータベースに直接接続し、値の推測を開始し、最終的には従業員セットの `[Salary]` 値を推測します。
 

```
SELECT ID, Name, Salary FROM Employees
WHERE Salary > 99999 and Salary < 100001;
```

>    |  Id | 名前| Salary |   
>    | ----- | ---------- | ------ | 
>    |  62543 | Jane Doe | 0 | 
>    |  91245 | John Smith | 0 |  

この例は、データベースに対してアドホック クエリを実行するユーザーから、機密データをセキュリティで完全に保護する唯一の手段として動的データ マスクを使用すべきではないことを示しています。 動的データ マスクは偶発的な機密データの公開を防ぐ場合に適していますが、基になるデータを推測する悪意のある攻撃を防ぐためのものではありません。
 
データベースのアクセス許可を適切に管理し、必要最小限のアクセス許可の原則に常に従うことが重要です。 また、データベースに対して実行されるすべてのアクティビティを追跡するために、必ず監査を有効にしてください。

  
## 使用例  
  
### 動的データ マスクを作成する  
 次の例では、3 種類の動的データ マスクでテーブルを作成します。 この例ではテーブルを作成し、結果を表示するように選びます。  
  
```  
CREATE TABLE Membership  
  (MemberID int IDENTITY PRIMARY KEY,  
   FirstName varchar(100) MASKED WITH (FUNCTION = 'partial(1,"XXXXXXX",0)') NULL,  
   LastName varchar(100) NOT NULL,  
   Phone# varchar(12) MASKED WITH (FUNCTION = 'default()') NULL,  
   Email varchar(100) MASKED WITH (FUNCTION = 'email()') NULL);  
  
INSERT Membership (FirstName, LastName, Phone#, Email) VALUES   
('Roberto', 'Tamburello', '555.123.4567', 'RTamburello@contoso.com'),  
('Janice', 'Galvin', '555.123.4568', 'JGalvin@contoso.com.co'),  
('Zheng', 'Mu', '555.123.4569', 'ZMu@contoso.net');  
SELECT * FROM Membership;  
```  
  
 新しいユーザーが作成され、テーブルに対する **SELECT** アクセス許可が付与されました。 `TestUser` ビューのマスクされたデータとして、クエリが実行されます。  
  
```  
CREATE USER TestUser WITHOUT LOGIN;  
GRANT SELECT ON Membership TO TestUser;  
  
EXECUTE AS USER = 'TestUser';  
SELECT * FROM Membership;  
REVERT;  
```  
  
 データが変更されたことで、結果はマスクを次のように表示します。  
  
 `1    Roberto     Tamburello    555.123.4567    RTamburello@contoso.com`  
  
 into  
  
 `1    RXXXXXXX    Tamburello    xxxx            RXXX@XXXX.com`  
  
### 既存の列のマスクを追加または編集する  
 **ALTER TABLE** ステートメントを使用して、テーブル内の既存の列にマスクを追加したり、その列のマスクを編集したりします。  
次の例では、マスク関数を `LastName` 列に追加します。  
  
```  
ALTER TABLE Membership  
ALTER COLUMN LastName ADD MASKED WITH (FUNCTION = 'partial(2,"XXX",0)');  
```  
  
 次の例では、 `LastName` 列のマスク関数を変更します。  
  
```  
ALTER TABLE Membership  
ALTER COLUMN LastName varchar(100) MASKED WITH (FUNCTION = 'default()');  
```  
  
### アクセス許可を付与して、マスクが解除されたデータを表示する  
 **UNMASK** アクセス許可が付与されると、 `TestUser` は、マスクが解除されたデータを閲覧できるようになります。  
  
```  
GRANT UNMASK TO TestUser;  
EXECUTE AS USER = 'TestUser';  
SELECT * FROM Membership;  
REVERT;   
  
-- Removing the UNMASK permission  
REVOKE UNMASK TO TestUser;  
```  
  
### 動的データ マスクをドロップする  
 次のステートメントは、先ほどの例で作成された `LastName` 列のマスクをドロップします。  
  
```  
ALTER TABLE Membership   
ALTER COLUMN LastName DROP MASKED;  
```  
  
## 参照  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [column_definition &#40;Transact-SQL&#41;](../Topic/column_definition%20\(Transact-SQL\).md)   
 [sys.masked_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-masked-columns-transact-sql.md)   
 [SQL Database 動的データ マスクの使用 (Azure ポータル)](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
  