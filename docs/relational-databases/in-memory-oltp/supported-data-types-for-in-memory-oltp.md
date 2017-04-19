---
title: "インメモリ OLTP に対してサポートされるデータ型 | Microsoft Docs"
ms.custom: ""
ms.date: "05/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
caps.latest.revision: 26
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 26
---
# インメモリ OLTP に対してサポートされるデータ型
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  この記事では、次のインメモリ OLTP 機能でサポートされていないデータ型の一覧を示します。  
  
-   メモリ最適化テーブル  
  
-   ネイティブ コンパイル ストアド プロシージャ  
  
## サポートされていないデータ型  
 次のデータ型はサポートされません。  
  
||||  
|-|-|-|  
|[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)|[geography &#40;Transact-SQL&#41;](../Topic/geography%20\(Transact-SQL\).md)|[geometry &#40;Transact-SQL&#41;](../Topic/geometry%20\(Transact-SQL\).md)|  
|[hierarchyid &#40;Transact-SQL&#41;](../Topic/hierarchyid%20\(Transact-SQL\).md)|[rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)|[xml &#40;Transact-SQL&#41;](../../t-sql/xml/xml-transact-sql.md)|  
|[sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)|ユーザー定義型|」を参照してください。|  
  
## サポートされる重要なデータ型  
 インメモリ OLTP の機能では、ほとんどのデータ型がサポートされています。 次のデータ型は特に重要です。  
  
|文字列型とバイナリ型|詳細情報|  
|-----------------------------|--------------------------|  
|binary と varbinary*|[binary と varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|char と varchar*|[char および varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|nchar と nvarchar*|[nchar および nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
  
上記の文字列データ型とバイナリ データ型については、SQL Server 2016 以降は次のようになります。  
  
- 個々のメモリ最適化テーブルには、それらの長さが 8,060 バイトの物理行サイズを超えることがあっても、`nvarchar(4000)` などの複数の長い列が含まれている場合があります。  
  
- メモリ最適化テーブルには、`varchar(max)` などのデータ型の最大長の文字列やバイナリ列がある場合があります。  


### 行外の LOB 列およびその他の列の特定

次の Transact-SQL SELECT ステートメントにより、メモリ最適化テーブルの行外のすべての列のレポートが生成されます。  次の点に注意してください。

- インデックス キー列はすべて行内に格納されます。
  - メモリ最適化テーブルでは、一意ではないインデックス キーが、NULL 値を許容する列を含むことができるようになりました。
  - メモリ最適化テーブルでは、インデックスを UNIQUE として宣言できます。 
- すべての LOB 列は行外に格納されます。
- max_length の -1 は、ラージ オブジェクト (LOB) 列を表します。


```tsql
SELECT
        OBJECT_NAME(m.object_id) as [table],
        c.name                   as [column],
        c.max_length
    FROM
             sys.memory_optimized_tables_internal_attributes AS m
        JOIN sys.columns                                     AS c
                ON  m.object_id = c.object_id
                AND m.minor_id  = c.column_id
    WHERE
        m.type = 5;
```


#### ネイティブ コンパイル モジュールでの LOB のサポート


組み込み文字列関数をネイティブ  コンパイル モジュール (ネイティブ プロシージャなど) で使用すると、関数により LOB 型の文字列が受け入れられます。 たとえば、ネイティブ プロシージャで LTrim 関数を使用すると、nvarchar(max) 型や varbinary(max) 型のパラメーターを入力することができます。

これらの LOB は、ネイティブ コンパイル スカラー UDF (ユーザー定義関数) からの戻り値を指定することもできます。


### その他のデータ型


|その他の型|詳細情報|  
|-----------------|--------------------------|  
|テーブル型|[メモリ最適化テーブル変数](../Topic/Memory-Optimized%20Table%20Variables.md)|  
  
## 参照  
 [Transact-SQL によるインメモリ OLTP のサポート](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)   
 [メモリ最適化テーブルへの LOB 列の実装](http://msdn.microsoft.com/ja-jp/bd8df0a5-12b9-4f4c-887c-2fb78dd79f4e)   
 [メモリ最適化テーブルへの SQL_VARIANT の実装](../../relational-databases/in-memory-oltp/implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  