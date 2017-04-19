---
title: "URL アクセスを使用してレポートをエクスポートする | Microsoft Docs"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "形式 [Reporting Services], URL レンダリング"
  - "URL アクセス [Reporting Services], レンダリング形式"
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# URL アクセスを使用してレポートをエクスポートする
  *rs:Format* URL パラメーターを使用すると、レポートを表示する形式を必要に応じて指定できます。  HTML4.0 および HTM5 (表示拡張機能) の場合は、ブラウザーにレンダリングされます。他の形式の場合は、レポート出力をローカル ファイルに保存するよう促すメッセージが表示されます。  
  
 たとえば、ネイティブ モードのレポート サーバーから直接レポートの PDF コピーを取得するには、次の URL を使用します。  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 また、SharePoint 統合モードのレポート サーバーから取得するには、次の URL を使用します。  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 たとえば、ブラウザーで次の URL コマンドを実行すると、レポート サーバーの名前付きインスタンスから PPTX レポートがエクスポートされます。  
  
```  
http://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 このパラメーターの有効値は、アクセス先レポート サーバーにインストールされているレポート表示拡張機能によって異なります。 一般的な拡張機能は HTML4.0、MHTML、IMAGE、EXCELOPENXML (xlsx)、WORDOPENXML (docx)、CSV、PDF、XML、および NULL です。 指定した表示拡張機能がレポート サーバーにインストールされていない場合は、レポートが表示されず、エラーが生成されてブラウザーに表示されます。  
  
 *Format* パラメーターを URL の一部として含めない場合は、レポート サーバーがブラウザーを検出し、適切な HTML 形式でレポートを表示します。  
  
## 参照  
 [URL アクセス (SSRS)](../reporting-services/url-access-ssrs.md)   
 [URL アクセス パラメーター リファレンス](../reporting-services/url-access-parameter-reference.md)  
  
  