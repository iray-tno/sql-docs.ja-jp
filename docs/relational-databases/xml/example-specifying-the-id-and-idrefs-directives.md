---
title: "例 : ID ディレクティブと IDREFS ディレクティブの指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDREFS ディレクティブ"
  - "ID ディレクティブ"
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# 例 : ID ディレクティブと IDREFS ディレクティブの指定
  要素の属性は、 **ID** 型の属性として指定することができます。さらに、この属性を参照する **IDREFS** 属性を使用できます。 これにより、ドキュメント内のリンク作成が可能になります。これは、リレーショナル データベースにおける主キーと外部キーのリレーションシップに似ています。  
  
 この例では、 **ID** ディレクティブと **IDREFS** ディレクティブを使用して、 **ID** 型と **IDREFS** 型の属性を作成する方法を示します。 ID は整数値にできないので、この例では ID 値を変換します。 つまり、型キャストを行っています。 ID 値にはプレフィックスを使用します。  
  
 次のような XML を生成するとします。  
  
```  
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >  
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
 < `SalesOrderIDList` > 要素の `Customer` 属性は、複数の値を指定できる属性であり、< `SalesOrderID` > 要素の `SalesOrder` 属性を参照しています。 このリンクを確立するには、`SalesOrderID` 属性を `ID` 型として宣言し、< `SalesOrderIDList`> 要素の `Customer` 属性を `IDREFS` 型として宣言する必要があります。 各顧客が複数の注文を発注することが考えられるので、`IDREFS` 型を使用しています。  
  
 **IDREFS** 型の要素も、複数の値を保持できます。 このため、別の SELECT 句を使用して、同じタグ、親、およびキー列の情報を再利用する必要があります。 さらに、**IDREFS** 値を構成する一連の行が、それぞれの親要素の直後にグループ化された状態で表示されるように、`ORDER BY` 句を指定します。  
  
 求める XML を生成するクエリを次に示します。 このクエリでは、`ID` ディレクティブと `IDREFS` ディレクティブを使用して、指定した列名の型を上書きしています (`SalesOrder!2!SalesOrderID!ID`、`Customer!1!SalesOrderIDList!IDREFS`)。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID       [Customer!1!CustomerID],  
        NULL               [Customer!1!SalesOrderIDList!IDREFS],  
        NULL               [SalesOrder!2!SalesOrderID!ID],  
        NULL               [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   
UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerIDORDER BY [Customer!1!CustomerID] ,  
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## 参照  
 [FOR XML での EXPLICIT モードの使用](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  