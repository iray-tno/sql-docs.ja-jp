---
title: "混合型と単純コンテンツ | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "混合型 [SQL Server]"
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# 混合型と単純コンテンツ
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、混合型を単純コンテンツに制限することはできません。  
  
## 例  
 次の XML スキーマ コレクションでは、 `myComplexTypeA` は空にできる複合型です。 つまり、その要素はどちらも、 `minOccurs` が 0 に設定されています。 この複合型を、 `myComplexTypeB` の宣言で行った方法で単純コンテンツに制限することはできません。 したがって、次の XML スキーマ コレクションの作成は失敗します。  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## 参照  
 [サーバー上の XML スキーマ コレクションの要件と制限](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  