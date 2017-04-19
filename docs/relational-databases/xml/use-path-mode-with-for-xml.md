---
title: "FOR XML での PATH モードの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PATH FOR XML モード"
  - "文字 [SQL Server], XML"
  - "別名 [SQL Server], XML"
  - "FOR XML 句, PATH モード"
  - "FOR XML PATH モード"
  - "列名 [SQL Server]"
  - "XPath クエリ [SQL Server]"
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# FOR XML での PATH モードの使用
  「[FOR XML を使用した XML の構築](../../relational-databases/xml/for-xml-sql-server.md)」で説明したように、PATH モードを使用すると、要素と属性の組み合わせが容易になります。 入れ子構造を使用することで、複雑なプロパティも容易に表現できるようになります。 FOR XML EXPLICIT モードのクエリを使用してこのような XML を行セットから作成することもできますが、煩雑になりかねない EXPLICIT モードのクエリに比べて PATH モードでは同じことを簡潔に行うことができます。 PATH モードに、入れ子の FOR XML クエリと、**xml** 型のインスタンスを返す TYPE ディレクティブを組み合わせることで、簡潔なクエリを記述できます。  
  
 PATH モードでは、列名または列の別名が XPath 式として処理されます。 XPath 式は XML に値がどのようにマップされているかを示します。 各 XPath 式は、行要素に対して相対的に生成されるノードの種類 (属性、要素、スカラー値など) および名前と階層を提供する相対 XPath です。  
  
 ここでは、さまざまな条件における行セットでの列のマッピングについて説明し、例を示します。  
  
## このセクションの内容  
  
-   [名前のない列](../../relational-databases/xml/columns-without-a-name.md)  
  
-   [名前のある列](../../relational-databases/xml/columns-with-a-name.md)  
  
-   [名前をワイルドカード文字で指定した列](../../relational-databases/xml/columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [XPath ノード テストの名前が付いた列](../../relational-databases/xml/columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [パスを data&#40;&#41; として指定した列の名前](../../relational-databases/xml/column-names-with-the-path-specified-as-data.md)  
  
-   [NULL 値が含まれる列の既定動作](../../relational-databases/xml/columns-that-contain-a-null-value-by-default.md)  
  
-   [PATH モードでの名前空間のサポート](../../relational-databases/xml/namespace-support-in-path-mode.md)  
  
-   [例 : PATH モードの使用](../../relational-databases/xml/examples-using-path-mode.md)  
  
## 参照  
 [WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML &#40;SQL Server&#41;](../../relational-databases/xml/for-xml-sql-server.md)  
  
  