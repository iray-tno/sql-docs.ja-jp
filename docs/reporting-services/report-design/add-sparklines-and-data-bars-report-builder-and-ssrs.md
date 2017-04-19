---
title: "スパークラインとデータ バーの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# スパークラインとデータ バーの追加 (レポート ビルダーおよび SSRS)
  スパークラインとデータ バーは小さく簡潔なグラフであり、余分な情報を最小限に抑えて多くの情報を伝えます。 詳細については、「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。  
  
 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートで、通常、スパークラインとデータ バーは、テーブルまたはマトリックス内のセルに置かれます。 スパークラインには、それぞれ 1 つの系列のみが表示されます。 データ バーには、1 つまたは複数のデータ ポイントを含めることができます。 スパークラインとデータ バーでは、テーブルまたはマトリックスで各行の系列情報を繰り返す場合にその効果が得られます。  
  
## テーブルまたはマトリックスにスパークラインまたはデータ バーを追加するには  
  
1.  表示するデータを含む[テーブル](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)または[マトリックス](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)を作成していない場合は、それらを作成します。  
  
2.  テーブルまたはマトリックスに列を挿入します。 詳細については、「[列の挿入または削除 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。  
  
3.  **[挿入]** タブで、**[スパークライン]** または **[データ バー]** をクリックし、新しい列のセル内をクリックします。  
  
    > [!NOTE]  
    >  スパークラインをテーブル内の詳細グループに置くことはできません。 グループに関連付けられているセルにのみ置くことができます。  
  
4.  **[スパークラインの種類の変更] または [データ バーの種類の変更]** ダイアログ ボックスで、目的のスパークラインまたはデータ バーの種類をクリックし、**[OK]** をクリックします。  
  
5.  スパークラインまたはデータ バーをクリックします。  
  
     **グラフ データ** ペインが開きます。  
  
6.  **[値]** 領域で、**[フィールドの追加]** のプラス記号 (**+**) をクリックし、グラフ化する値のあるフィールドをクリックします。  
  
7.  **[カテゴリ グループ]** 領域で、**[フィールドの追加]** のプラス記号 (**+**) をクリックし、グループ化に使用する値のフィールドをクリックします。  
  
     通常、各行に 1 つの系列を使用するので、スパークラインまたはデータ バーでは **[系列グループ]** 領域にフィールドを追加しません。  
  
## 参照  
 [グラフ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [テーブル内のグラフまたはマトリックスでのデータの整列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  