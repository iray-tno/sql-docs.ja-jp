---
title: "データ領域にデータがないことを示すメッセージの設定 (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# データ領域にデータがないことを示すメッセージの設定 (レポート ビルダーおよび SSRS)
  データのないデータ領域の代わりに表示レポートに表示するテキストを指定するときは、テーブル、マトリックス、または一覧データ領域に対して NoRowsMessage プロパティを、グラフ データ領域に対して NoDataMessage を、マップのカラー スケールに対して NoDataText を、それぞれ設定します。 実行時にレポート プロセッサによってレポートの各データセットに対しクエリが実行されますが、データセット クエリによって結果セットが生成されない場合があります。 空のデータセットにバインドされるデータ領域に対し、空のデータ領域を表示する代わりに表示するテキストを指定できます。 また、サブレポートのデータセットに実行時のデータがない場合、サブレポートに対し NoRowsMessage プロパティを設定することもできます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### テーブル、マトリックス、リストに NoRowsMessage プロパティを設定するには  
  
1.  [デザイン] ビューで、デザイン画面のテーブル、マトリックス、一覧データ領域、またはサブレポートをクリックして選択します。 選択したアイテムのプロパティがプロパティ ペインに表示されます。  
  
2.  プロパティ ペインの **[NoRowsMessage]** プロパティ フィールドに、メッセージとして表示するテキストを入力します。  
  
     または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。  
  
### グラフに NoDataMessage プロパティを設定するには  
  
1.  [デザイン] ビューで、デザイン画面のグラフをクリックして選択します。 選択したアイテムのプロパティがプロパティ ペインに表示されます。  
  
2.  プロパティ ペインで **[NoDataMessage]**ノードを展開します。  
  
3.  **[NoDataMessage]**プロパティ フィールドにメッセージとして表示するテキストを **[キャプション]** に入力します。  
  
     または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。  
  
### サブレポートに NoRowsMessage を設定するには  
  
1.  [デザイン] ビューで、デザイン画面のサブレポートをクリックして選択します。 選択したアイテムのプロパティがプロパティ ペインに表示されます。  
  
2.  プロパティ ペインの **[NoRowsMessage]** プロパティ フィールドに、メッセージとして表示するテキストを入力します。  
  
     または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。  
  
### マップのカラー スケールに NoDataText プロパティを設定するには  
  
1.  [デザイン] ビューで、マップのカラー スケールをクリックして選択します。 選択したアイテムのプロパティがプロパティ ペインに表示されます。  
  
2.  プロパティ ペインの **[NoDataText]**に、データ値を持たない色のラベルとして表示するテキストを入力します。  
  
     または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。  
  
## 参照  
 [サブレポート (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/subreports-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [グラフ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [マップ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [サブレポート (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/subreports-report-builder-and-ssrs.md)  
  
  