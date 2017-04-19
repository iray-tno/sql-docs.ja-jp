---
title: "Power Pivot データ更新 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動データ更新 [Analysis Services と SharePoint]"
  - "定期データ更新 [Analysis Services と SharePoint]"
  - "データ更新 [Analysis Services と SharePoint]"
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
caps.latest.revision: 24
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 24
---
# Power Pivot データ更新
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含むブックを作成したら、最初にブックを作成するときに使用したソースから更新情報を取得するクエリまたはコマンドを再実行して、定期的にデータを更新することができます。 このプロセスは**データ更新**と呼ばれます。データ更新は、[!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] で要求時に実行したり、SharePoint ファーム内のアプリケーション サーバーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロセスとして実行される定期的な操作として実行したりすることができます。 詳細については、以下をご覧ください。  
  
-   [SharePoint 2010 での PowerPivot データの更新](http://msdn.microsoft.com/ja-jp/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Power Pivot 自動データ更新アカウントの構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/ja-jp/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [詳細については、「Power Pivot データ更新用の保存された資格情報の構成 (Power Pivot for SharePoint)」を参照してください。](http://msdn.microsoft.com/ja-jp/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [データ更新のスケジュール (Power Pivot for SharePoint)](http://msdn.microsoft.com/ja-jp/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [データ更新履歴の表示 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および SharePoint Server 2013 の Excel Services では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ モデルのデータ更新に新しいアーキテクチャを使用しています。 SharePoint 2013 でサポートされているアーキテクチャでは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ モデルを読み込むための主要なコンポーネントとして Excel Services が使用されます。 以前に使用されていたデータ更新のアーキテクチャでは、データ モデルを読み込むために、SharePoint モードで [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスおよび [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を実行しているサーバーが使用されていました。 詳細については、以下を参照してください。  
>   
>  -   [SharePoint 2013 での PowerPivot データ更新](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  