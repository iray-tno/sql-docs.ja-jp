---
title: "極座標グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9402d8f-202a-4cdf-949e-50f5b1d2b885
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# 極座標グラフ (レポート ビルダーおよび SSRS)
  極座標グラフでは、カテゴリ別にグループ化されたポイントのセットとして、360°の円上に系列が表示されます。 値は、円の中心からポイントまでの距離で表されます。 ポイントが中心から遠いほど、その値は大きくなります。 カテゴリのラベルは、グラフの周囲に表示されます。 極座標グラフにデータを追加する方法の詳細については、「[グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## バリエーション  
  
-   **レーダー チャート**: レーダー チャートでは、系列が円形の線または領域で表示されます。 極座標グラフとは異なり、レーダー チャートでは、極座標の観点ではデータが表示されません。  
  
## 極座標グラフのデータに関する注意点  
  
-   レーダー チャートは、複数の系列のカテゴリ データを比較する場合に役立ちます。  
  
-   極座標グラフは、極データをグラフ化する際に最もよく使用されます。ここでは、各データ ポイントが角度や距離によって決まります。  
  
-   極座標グラフは、同じグラフ領域内で他の種類のグラフと組み合わせることはできません。  
  
## 例  
 次の例では、レーダー チャートの使用方法を示します。 次の表は、チャートのサンプル データを示しています。  
  
|名前|売上|  
|----------|-----------|  
|低木|61|  
|種|78|  
|球根|60|  
|木|38|  
|花|81|  
  
 この例では、名前フィールドがカテゴリ グループ領域に配置されます。 売上フィールドは値領域に配置されます。 売上フィールドをドロップすると、グラフの売上フィールドが自動的に計算されます。 レーダー チャートでは、売上フィールド内の値の数に基づいて、ラベルを配置する場所が計算されます。ここでは、5 つの値が含まれているため、円周上で等間隔に設定された 5 つの点にラベルが配置されます。 売上フィールドに 3 つの値が含まれている場合、円周上で等間隔に設定された 3 つの点にラベルが配置されます。  
  
 次の図は、提示されたデータに基づくレーダー チャートの例を示しています。  
  
 ![レーダー チャート](../../reporting-services/report-design/media/rs-radarchart.gif "レーダー チャート")  
  
## 参照  
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [グラフの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [折れ線グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/line-charts-report-builder-and-ssrs.md)   
 [グラフ内の空のデータ ポイントおよび NULL データ ポイント &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  