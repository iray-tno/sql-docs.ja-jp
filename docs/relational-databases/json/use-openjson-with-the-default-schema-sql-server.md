---
title: "既定のスキーマを使用する OPENJSON の使用 (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OPENJSON, 既定のスキーマ"
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# 既定のスキーマを使用する OPENJSON の使用 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  オブジェクトのプロパティごと、または配列内の要素ごとに 1 つの行が含まれたテーブルを返すには、既定のスキーマを使用して **OPENJSON** を使用します。  
  
 ここでは、既定のスキーマを使用して **OPENJSON** を使用する例をいくつか紹介します。 詳細とその他の例については、「[OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」を参照してください。  
  
## 例 - オブジェクトの各プロパティを返す  
 **Query**  
  
```tsql  
SELECT * FROM OPENJSON('{"name":"John","surname":"Doe","age":45}')  
```  
  
 **[結果]**  
  
|[キー]|値|  
|---------|-----------|  
|name|John|  
|姓|Doe|  
|有効期間|45|  
  
## 例 - 配列の各要素を返す  
 **Query**  
  
```tsql  
SELECT [key], value FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]')  
```  
  
 **[結果]**  
  
|[キー]|値|  
|---------|-----------|  
|0|en-GB|  
|1|en 英国|  
|2|de AT|  
|3|es AR|  
|4|sr という|  
  
## 例 - JSON を一時テーブルに変換する  
 次のクエリのすべてのプロパティを返します、 **情報** オブジェクトです。  
  
```tsql  
SET @json = N'{  
    "info":{    
      "type":1,  
      "address":{    
        "town":"Bristol",  
        "county":"Avon",  
        "country":"England"  
      },  
      "tags":["Sport", "Water polo"]  
   },  
   "type":"Basic"  
}'  
  
SELECT * FROM OPENJSON(@json, N'lax $.info')  
```  
  
 **[結果]**  
  
|[キー]|値|型|  
|---------|-----------|----------|  
|型|1|0|  
|address|{ "town":"Bristol", "county":"Avon", "country":"England" }|5|  
|タグ|[「スポーツ」、「Water ポーロ」]|4|  
  
## 例 - リレーショナル データと JSON データを結合する  
 次の例では、JSON 形式で SalesOrderReasons の配列を含む SalesReason テキスト列が、SalesOrderHeader テーブルにあります。 SalesOrderReasons オブジェクトには、"品質" と "製造元" のようなプロパティが含まれます。 この例では、販売理由が別個の子テーブルに含まれているかのように販売理由の JSON 配列を展開して、すべての販売注文行を関連する販売理由に結合するレポートを作成します。  
  
```tsql  
SELECT SalesOrderID, OrderDate, value AS Reason  
FROM Sales.SalesOrderHeader  
    CROSS APPLY OPENJSON (SalesReasons)  
  
```  
  
 この例では、OPENJSON から販売理由のテーブルが返されます。このテーブルでは、販売理由が値列として示されます。 CROSS APPLY 演算子は、OPENJSON テーブル値関数によって返される行に各販売注文の行を結合します。  
  
## 参照  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  