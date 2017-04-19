---
title: "[参照変換エディター] ([接続] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.lookuptransformation.referencetable.f1"
helpviewer_keywords: 
  - "参照変換エディター"
ms.assetid: e90d6b69-5a26-43c5-8433-5c3c9588e08c
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# [参照変換エディター] ([接続] ページ)
  **[参照変換エディター]** ダイアログ ボックスの **[接続]** ページを使用して、接続マネージャーを選択します。 OLE DB 接続マネージャーを選択する場合は、参照データセットを生成するためのクエリ、テーブル、またはビューも選択します。  
  
 参照変換の詳細については、「 [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
## オプション  
 **[参照変換エディター]** ダイアログ ボックスの [全般] ページで **[フル キャッシュ]** および **[キャッシュ接続マネージャー]** を選択すると、次のオプションを使用できます。  
  
 **キャッシュ接続マネージャー**  
 既存のキャッシュ接続マネージャーを一覧から選択するか、**[新規作成]** をクリックして新しい接続を作成します。  
  
 **新規**  
 新しい接続を作成するには、**[キャッシュ接続マネージャー エディター]** ダイアログ ボックスを使用します。  
  
 **[参照変換エディター]** ダイアログ ボックスの [全般] ページで **[フル キャッシュ]**、**[部分キャッシュ]**、**[キャッシュなし]**、および **[OLE DB 接続マネージャー]** を選択すると、次のオプションを使用できます。  
  
 **OLE DB 接続マネージャー**  
 一覧から既存の OLE DB 接続マネージャーを選択するか、**[新規作成]** をクリックして新しい接続を作成します。  
  
 **新規**  
 **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
 **[テーブルまたはビューを使用する]**  
 既存のテーブルまたはビューを一覧から選択するか、**[新規作成]** をクリックして新しいテーブルを作成します。  
  
> [!NOTE]  
>  **[参照変換エディター]** の **[詳細設定]** ページで SQL ステートメントを指定する場合、ここで選択したテーブル名はその SQL ステートメントで上書きおよび置換されます。 詳細については、「[[参照変換エディター] &#40;[詳細設定] ページ&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Advanced%20Page\).md)」を参照してください。  
  
 **新規**  
 **[テーブルの作成]** ダイアログ ボックスを使用して新しいテーブルを作成します。  
  
 **[SQL クエリの結果を使用する]**  
 既存のクエリの参照、新しいクエリの構築、クエリ構文のチェック、およびクエリ結果のプレビューを行うには、このオプションを選択します。  
  
 **[クエリの作成]**  
 **[クエリ ビルダー]** を使用して、実行する Transact-SQL ステートメントを作成します。これは、データを参照することによってクエリを作成するグラフィカルなツールです。  
  
 **参照**  
 ファイルとして保存されている既存のクエリを参照します。  
  
 **[クエリの解析]**  
 クエリ構文をチェックします。  
  
 **プレビュー**  
 **[クエリ結果のプレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 結果は 200 行まで表示されます。  
  
## 外部リソース  
 blogs.msdn.com のブログ「 [キャッシュ モードの参照](http://go.microsoft.com/fwlink/?LinkId=219518) 」  
  
## 参照  
 [[参照変換エディター] &#40;[全般] ページ&#41;](../Topic/Lookup%20Transformation%20Editor%20\(General%20Page\).md)   
 [[参照変換エディター] &#40;[列] ページ&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Columns%20Page\).md)   
 [[参照変換エディター] &#40;[詳細設定] ページ&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Advanced%20Page\).md)   
 [[参照変換エディター] &#40;[エラー出力] ページ&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Error%20Output%20Page\).md)   
 [あいまい参照変換](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  