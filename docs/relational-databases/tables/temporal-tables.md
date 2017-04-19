---
title: "テンポラル テーブル | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/11/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e442303d-4de1-494e-94e4-4f66c29b5fb9
caps.latest.revision: 47
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 47
---
# テンポラル テーブル
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 現時点の正しいデータのみではなく、テーブルに保存されていた任意の時点のデータ情報を提供することを組み込みでサポートするデータベース機能として、システム バージョン管理されたテンポラル テーブルが導入されました。 テンポラルは、ANSI SQL 2011 で導入され、現在は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でサポートされているデータベース機能です。  
  
 **クイック スタート**  
  
-   **はじめに:**  
  
    -   [システム バージョン管理されたテンポラル テーブルの概要](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)  
  
    -   [メモリ最適化テーブルでのシステム バージョン管理されたテンポラル テーブル](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)  
  
    -   [テンポラル テーブルの使用シナリオ](../../relational-databases/tables/temporal-table-usage-scenarios.md)  
  
    -   [Azure SQL Database のテンポラル テーブルの概要](https://azure.microsoft.com/documentation/articles/sql-database-temporal-tables/)  
  
-   **例 :**  
  
    -   [システム バージョン管理されたテンポラル テーブルの作成](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)  
  
    -   [メモリ最適化およびシステム バージョン管理されたテンポラル テーブルの使用](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)  
  
    -   [システム バージョン管理のテンポラル テーブルのデータの変更](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)  
  
    -   [システム バージョン管理されたテンポラル テーブルのデータのクエリ](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)  
  
    -   **Adventure Works サンプル データベースをダウンロードする:** テンポラル テーブルの使用を開始するには、「 [SQL Server 2016 CTP3 用の AdventureWorks データベース](https://www.microsoft.com/download/details.aspx?id=49502) 」をサンプルのスクリプトと共にダウンロードし、‘Temporal’ フォルダー内の指示に従ってください。  
  
-   **構文 :**  
  
    -   [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
  
    -   [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
    -   [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)  
  
-   **ビデオ:** 「 [SQL Server 2016 でのテンポラル](http://channel9.msdn.com/Shows/Data-Exposed/Temporal-in-SQL-Server-2016)」でテンポラルに関する 20 分間の説明を参照してください。  
  
## システム バージョン管理されたテンポラル テーブルとは  
 システム バージョン管理されたテンポラル テーブルは、データ変更の履歴を完全に保持し、特定の時点の分析を簡単に実行できるよう設計された [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の新しい種類のユーザー テーブルです。 各行の有効期間はシステム (つまりデータベース エンジン) によって管理されているため、この種類のテンポラル テーブルは、システム バージョン管理されたテンポラル テーブルと呼ばれています。  
  
 すべてのテンポラル テーブルには、それぞれに **datetime2** データ型が明示的に定義されている 2 つの列があります。 これらの列は、期間列と呼ばれます。 これら期間列は、行が変更されるたびに各行の有効期間を記録するためにシステムのみに使用されます。  
  
 テンポラル テーブルには、これらの期間列に加え、ミラー化されたスキーマを使用する別のテーブルへの参照も含まれています。 システムでは、このテーブルを使用して、テンポラル テーブルの行が更新または削除されるたびに、行の以前のバージョンを自動的に保存します。 現在 (実際) の行バージョンを保存するメインのテーブルが現行テーブルまたはテンポラル テーブルと簡単に呼ばれているのに対し、この追加のテーブルは、履歴テーブルと呼ばれています。 テンポラル テーブルの作成時、ユーザーは既存の履歴テーブルを指定するか (スキーマ準拠である必要があります)、システムに既定の履歴テーブルを作成させます。  
  
## テンポラルである理由  
 データの実際のソースは動的で、ビジネスの意思決定はアナリストがデータの進化から得ることができる洞察に通常依存しています。 テンポラル テーブルの使用例は次のとおりです。  
  
-   すべてのデータ変更の監査と、必要に応じてのデータの科学捜査の実行  
  
-   過去の任意の時点でのデータの状態の再構築  
  
-   長期の傾向の計算  
  
-   意思決定支援アプリケーションのための緩やかに変化するディメンションの維持  
  
-   偶発的なデータ変更やアプリケーション エラーからの復旧  
  
## テンポラルのしくみ  
 テーブルのシステム バージョン管理は、現行テーブルと履歴テーブルの 1 組のテーブルとして実装されます。 これらの各テーブル内には、次の 2 つの追加の **datetime2** 列で、各行の有効期間が定義されています。  
  
-   期間開始列: システムにより、この行の開始時間が、通常は **SysStartTime** 列である列に書き込まれます。  
  
-   期間終了列: システムにより、この行の終了時間が、通常は **SysEndTime** 列である列に書き込まれます。  
  
 現行テーブルには、各行の現在の値が含まれています。 履歴テーブルには、存在する場合、各行のそれぞれの以前の値と、それが有効であった期間の開始時間と終了時間が含まれています。  
  
 ![Temporal-HowWorks](../../relational-databases/tables/media/temporal-howworks.PNG "Temporal-HowWorks")  
  
 次に、Employee 情報が仮定の HR データベースにあるシナリオの簡単な例を示します。  
  
```  
CREATE TABLE dbo.Employee   
(    
  [EmployeeID] int NOT NULL PRIMARY KEY CLUSTERED   
  , [Name] nvarchar(100) NOT NULL  
  , [Position] varchar(100) NOT NULL   
  , [Department] varchar(100) NOT NULL  
  , [Address] nvarchar(1024) NOT NULL  
  , [AnnualSalary] decimal (10,2) NOT NULL  
  , [ValidFrom] datetime2 (2) GENERATED ALWAYS AS ROW START  
  , [ValidTo] datetime2 (2) GENERATED ALWAYS AS ROW END  
  , PERIOD FOR SYSTEM_TIME (ValidFrom, ValidTo)  
 )    
 WITH (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.EmployeeHistory));  
```  
  
 **INSERTS:** システムにより、**INSERT** では、**SysStartTime** 列には、システム クロックに基づく現在のトランザクションの開始時間 (UTC タイム ゾーン) の値が設定され、**SysEndTime** 列には、最大値の 9999-12-31 の値が割り当てられます。 これは行をオープンとマークします。  
  
 **UPDATES:** システムにより、**UPDATE** では、行の前の値が履歴テーブルに保存され、**SysEndTime** 列には、システム クロックに基づく現在のトランザクションの開始時間 (UTC タイム ゾーン) の値が設定されます。 これは行をクローズドとマークし、行が有効であった期間が記録されます。 現行テーブルでは、行は新しい値で更新され、システムにより **SysStartTime** 列には、システム クロックに基づくトランザクションの開始時間 (UTC タイム ゾーン) の値が設定されます。 現行テーブル内の **SysEndTime** 列の更新された行の値は、最大値の 9999-12-31 のままです。  
  
 **DELETES:** システムにより、**DELETE** では、行の前の値が履歴テーブルに保存され、**SysEndTime** 列には、システム クロックに基づく現在のトランザクションの開始時間 (UTC タイム ゾーン) の値が設定されます。 これは行をクローズドとマークし、前の行が有効であった期間が記録されます。 現行テーブルでは、その行は削除されます。 現行テーブルに対するクエリでは、この行は返されません。 履歴データを処理するクエリのみで、クローズドの行のデータが返されます。  
  
 **MERGE:** **MERGE** では、**MERGE** ステートメントでアクションとして何が指定されているかによって、まさに最大 3 つのステートメント (**INSERT**、**UPDATE**、または **DELETE**、あるいはこれらすべて) が実行されたかのような動作になります。  
  
> [!IMPORTANT]  
>  システム datetime2 列に記録されている時間は、トランザクション自体の開始時間に基づいています。 たとえば、1 つのトランザクションで挿入されたすべての行の、**SYSTEM_TIME** 期間の開始に対応する列の UTC 時間は同じになります。  
  
## テンポラル データのクエリ方法  
 **SELECT** ステートメントの **FROM***\<table>* 句には、現行および履歴テーブルのデータをクエリする新しい **FOR SYSTEM_TIME** 句が導入されました。これには、テンポラル専用のサブ句が 5 つあります。 この新しい **SELECT** ステートメントの構文は、1 つのテーブルで直接サポートされており、複数の結合を介して、また複数のテンポラル テーブル上のビューを介して反映されます。  
  
 ![Temporal-Querying](../../relational-databases/tables/media/temporal-querying.PNG "Temporal-Querying")  
  
 次のクエリでは、少なくとも 2014 年の 1 月 1 日から 2015 年 1 月 1 日 (上限の境界を含む) の間にアクティブであった、EmployeeID が 1000 の従業員行の行バージョンが検索されます。  
  
```  
SELECT * FROM Employee   
    FOR SYSTEM_TIME    
        BETWEEN '2014-01-01 00:00:00.0000000' AND '2015-01-01 00:00:00.0000000'   
            WHERE EmployeeID = 1000 ORDER BY ValidFrom;  
```  
  
> [!NOTE]  
>  **FOR SYSTEM_TIME** では、有効時間がゼロの行は除外されます (**SysStartTime** = **SysEndTime**)。  
> それらの行は、同じトランザクションで同じ主キーに対して複数の更新を実行すると生成されます。  
> その場合は、テンポラル クエリでは、トランザクション前と、トランザクション後に現行となったの行番号のみを示します。  
> それらの行を分析に含める必要がある場合は、履歴テーブルを直接クエリします。  
  
 次の表の該当行列の SysStartTime は、クエリ対象のテーブルの **SysStartTime** 列の値で、**SysEndTime** はクエリ対象のテーブルの **SysEndTime** 列の値です。 完全な構文と例については、「[FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)」、および「[システム バージョン管理されたテンポラル テーブルのデータのクエリ](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)」を参照してください。  
  
|式|該当行|説明|  
|----------------|---------------------|-----------------|  
|**AS OF**<date_time>|SysStartTime \<= date_time AND SysEndTime > date_time|過去の指定時点の実際 (現行) の値を含む行のあるテーブルを返します。 内部的には、テンポラル テーブルとその履歴テーブルの結合が行われ、結果がフィルター処理されて、*<date_time>* パラメーターで指定された特定の時点で有効だった行の値が返されます。 *system_start_time_column_name* 値が *<date_time>* パラメーター値と等しいかそれよりも小さく、*system_end_time_column_name* 値が *<date_time>* パラメーター値より大きい場合に、行の値は有効と見なされます。|  
|**FROM**<start_date_time>**TO**<end_date_time>|SysStartTime \< end_date_time AND SysEndTime > start_date_time|指定した時間範囲内でアクティブだったすべての行バージョンの値を含むテーブルを返します。FROM 引数の *<start_date_time>* パラメーター値の前にアクティブになったか、TO 引数の *<end_date_time>* パラメーター値の後にアクティブでなくなったかに無関係です。 内部的には、共用体が一時的なテーブルとその履歴テーブルの間実行され、結果をフィルター処理すると、指定した時間範囲の中にいつでもにアクティブだったすべての行のバージョンの値を返します。 FROM エンドポイントによって定義されている下限の境界で正確にアクティブになった行は含まれ、TO エンドポイントによって定義された境界の上限で正確にアクティブになったレコードは含まれません。|  
|**BETWEEN**<start_date_time>**AND**<end_date_time>|SysStartTime \<= end_date_time AND SysEndTime > start_date_time|返される行のテーブルには <end_date_time> エンドポイントで定義された上限の境界でアクティブになった行が含まれることを除き、**FOR SYSTEM_TIME FROM** <start_date_time>**TO** <end_date_time> の説明と同じです。|  
|**CONTAINED IN** (<start_date_time> , <end_date_time>)|SysStartTime >= start_date_time AND SysEndTime \<= end_date_time|CONTAINED IN 引数の 2 つの datetime 値で定義された指定時間範囲内に開かれて閉じられたすべての行バージョンの値を含むテーブルを返します。 行が下位の境界に正確に有効になったまたは上限の境界上だけでアクティブにされているが中断されることでは、含まれています。|  
|**ALL**|すべての行|現行および履歴テーブルに属する行の和を返します。|  
  
> [!NOTE]  
>  必要に応じて、これらの期間列を明示的に参照しないクエリがこれらの列を返さないよう、これらの期間列を隠すこともできます (**SELECT \* FROM***\<table>* シナリオ)。 非表示の列を返すには、クエリで非表示の列を単純に明示的に参照してください。 同様に、**INSERT** および **BULK INSERT** ステートメントでも、これらの新しい期間列が存在しないかのように続行されます (そして列値は自動入力されます)。 **HIDDEN** 句の使用方法の詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)」および「[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
## この記事は役に立ちましたか? フィードバックをお待ちしております。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。  [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Tables%20page)にコメントをお送りください  
  
## 参照  
 [システム バージョン管理されたテンポラル テーブルの概要](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [メモリ最適化テーブルでのシステム バージョン管理されたテンポラル テーブル](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [テンポラル テーブルの使用シナリオ](../../relational-databases/tables/temporal-table-usage-scenarios.md)   
 [テンポラル テーブルの考慮事項と制約](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [テンポラル テーブルでのパーティション分割](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [テンポラル テーブルのシステム一貫性のチェック](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [テンポラル テーブル セキュリティ](../../relational-databases/tables/temporal-table-security.md)   
 [テンポラル テーブル メタデータのビューおよび関数](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  