---
title: "DTAXML 要素 (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "DTAXML 要素"
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# DTAXML 要素 (DTA)
  データベース エンジン チューニング アドバイザーの XML 入力ファイルと出力ファイルにおけるルート要素 **DTAXML** には、データベース エンジン チューニング アドバイザーが生成するチューニング入力とチューニング出力を記述したすべての要素が含まれます。  
  
## 構文  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## 要素の属性  
  
|属性|説明|  
|---------------|-----------------|  
|**xmlns:xsi**|必須。 XML Schema Instance 名前空間を識別します。 この名前空間の属性を使用して、データベース エンジン チューニング アドバイザーの XML ファイルの検証に使用するスキーマを参照します。<br /><br /> 必須値 : [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|必須。 データベース エンジン チューニング アドバイザーの名前空間を識別します。<br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の XML エディターを使用してデータベース エンジン チューニング アドバイザーの XML ファイルを編集する場合、F1 ヘルプとダイナミック ヘルプでは、この値を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの参照トピックを検索します。<br /><br /> 必須値 :<br /><br /> [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?LinkId=43100) の名前空間|  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|DTA の XML ファイルにつき 1 回の出現が必要です。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|なし|  
|**子要素**|[DTAInput 要素 &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)<br /><br /> **DTAOutput** 要素 (詳細については、「[データベース エンジン チューニング アドバイザーの XML スキーマ](http://schemas.microsoft.com/sqlserver/)」を参照してください)|  
  
## 解説  
 XML 名前空間の詳細については、 [MSDN Library の「](http://go.microsoft.com/fwlink/?LinkId=7341) XML ドキュメントにおける名前空間 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 」を参照してください。  
  
## 例  
 一般的な **DTAXML** 要素の例については、「[XML 入力ファイル サンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  