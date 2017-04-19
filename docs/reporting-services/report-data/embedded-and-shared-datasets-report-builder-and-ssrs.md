---
title: "埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adc95cc0-d15a-413d-bc5a-302eab37a069
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# 埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)
  レポートにおけるデータセットとは、外部データ ソースに対してクエリを実行することによって返されるレポート データをいいます。 外部データ ソースに関する情報はデータ接続に含まれており、データセットは、そのデータ接続によって異なります。 レポート定義にデータそのものは含まれていません。 データセットには、クエリ コマンド、フィールド コレクション、パラメーター、フィルター、および大文字と小文字の区別と照合順序を含むデータ オプションがあります。 データセットには次の 2 種類があります。  
  
-   **共有データセット:** 共有データセットはレポート サーバー上でパブリッシュされ、複数のレポートで使用できます。 共有データセットは共有データ ソースに基づく必要があります。 キャッシュ更新計画を作成することによって、共有データセットをキャッシュおよびスケジュールできます。  
  
-   **埋め込みデータセット:** 埋め込みデータセットは 1 つのレポートで定義および使用されます。  
  
 これらの 2 つのデータセットでは、作成、格納、管理の方法が異なります。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 共有データセット  
 共有データセットは、複数のレポートで使用できるクエリを作成するために使用します。 共有データセットはレポート サーバー上に格納され、レポートまたは共有データ ソースとは別に管理されます。 たとえば、レポート サーバー管理者は、パフォーマンスの高いインデックス作成や他のクエリのパフォーマンスの最適化を実施するために、クエリを更新することができます。  
  
 可能な限り共有データセットを使用することをお勧めします。 クエリを最適化するか、クエリ結果をキャッシュすると、レポートのパフォーマンスを向上できます。 データへのアクセスが管理しやすくなり、レポートやレポートからアクセスするデータセットの安全性とパフォーマンスを高めることができます。  
  
 レポート デザイナーでは、レポート プロジェクトの一部として共有データセットを作成し、レポート サーバーに配置するかどうかを制御できます。 レポート サーバー上の保存先を参照して共有データセットを選択し、レポートに追加することはできません。  
  
 レポート ビルダーでは、次の操作を実行できます。  
  
1.  共有データセットを作成するには、共有データセットのデザイン ビューを使用します。 それをレポート サーバーまたは SharePoint サイトに保存することによって、他のレポートと共有することができます。 レポート サーバー上の保存先を参照して既存のデータセットを選択し、編集することもできます。 このビューでは、クエリを作成してすべてのデータセット オプションを設定できます。 詳細については、「[共有データセット デザイン ビュー &#40;レポート ビルダー&#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)」を参照してください。  
  
2.  レポートに共有データセットを追加するには、レポート デザイン ビューでレポート ビルダーを開きます。 ウィザードかレポート データ ペインから、レポート サーバーを参照し、共有データセットを選択してレポートに追加します。 このビューでは、フィールドを追加する以外に、クエリは変更できません。 他のデータ オプションを上書きし、フィルターを追加することはできます。 フィルターは削除できません。  
  
3.  次の表には、レポート サーバー上の共有データセットの定義とレポート定義内の共有データセットのインスタンスで構成できるプロパティを比較しています。  
  
    |プロパティ|定義の構成に関する注意事項|インスタンスの構成に関する注意事項|  
    |--------------|--------------------------------------------|------------------------------------------|  
    |クエリ テキスト|クエリを構成する (クエリを式として定義するなど)|クエリの変更は不可|  
    |クエリ パラメーター|レポート パラメーターの参照は不可<br /><br /> 既定値を含む<br /><br /> 読み取り専用フラグを含む|定義で読み取り専用とマークされていないパラメーターを構成する|  
    |フィルター|フィルターの定義|定義の一部を構成するデータセット フィルターの表示または変更は不可<br /><br /> 追加フィルターの作成は可能|  
    |[データ ソース]|共有データ ソースである必要がある|データ ソースの変更は不可|  
    |フィールド|クエリ コマンドのフィールド<br /><br /> データセット定義の一部を構成しない計算フィールド|フィールドの表示 (変更は不可)<br /><br /> フィールド コレクションは静的で、共有データセットをレポートに追加したときのクエリに基づきます。 更新するには、 **[データセットのプロパティ]** ダイアログ ボックスの **[フィールドの更新]** をクリックします。 定義内の現在のクエリから返されるコレクションが、実際のフィールド コレクションです。<br /><br /> 計算フィールドの追加|  
    |データセット|大文字と小文字の区別などのデータ オプション|インスタンスのデータ オプションの上書き|  
  
## 埋め込みデータセット  
 埋め込みデータセットは、1 つのレポートのみに使用するデータを外部データ ソースから取得する場合に使用します。 埋め込みデータセットは、その他の依存関係がなく、複数のレポートに使用する必要のないクエリを作成する場合に役立ちます。  
  
 埋め込みデータセットを作成または編集するには、[レポート データ] ペインを使用します。 データセットを作成した後は、**[データセットのプロパティ]** ダイアログ ボックスでプロパティを構成できます。  
  
## 参照  
 [埋め込みおよび共有のデータ接続またはデータ ソース &#40;レポート ビルダーおよび SSRS&#41;](../Topic/Embedded%20and%20Shared%20Data%20Connections%20or%20Data%20Sources%20\(Report%20Builder%20and%20SSRS\).md)   
 [共有データセットまたは埋め込みデータセットの作成 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [レポート データセット &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)   
 [データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  