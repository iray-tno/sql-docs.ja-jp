---
title: "SAP NetWeaver BI の接続の種類 (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f985856b-31d5-4e56-844b-8a8ee38da67e
caps.latest.revision: 8
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# SAP NetWeaver BI の接続の種類 (SSRS)
  SAP NetWeaver® Business Intelligence の外部データ ソースのデータをレポートに含めるには、種類が [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] のデータ拡張機能に基づいています。  
  
 このデータ拡張機能を使用すると、[!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] の外部データ ソースで定義された InfoCube、MultiProvider (仮想 InfoCube)、および Web 対応クエリから多次元データを取得できます。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 手順については、「[データ接続またはデータ ソースの追加および確認 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」をご覧ください。  
  
##  <a name="Connection"></a> 接続文字列  
 データ ソースに接続するときに使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次の接続文字列では、8000 番ポートを使用してサーバー上の [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースを指定し、SOAP を使用してインターネット経由の XML for Analysis Services (XMLA) を指定しています。  
  
```  
DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla  
```  
  
 接続文字列の例について詳しくは、「[レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)」をご覧ください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳しくは、「[データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」または「[レポート ビルダーでの資格情報の指定](../Topic/Specify%20Credentials%20in%20Report%20Builder.md)」を参照してください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Query"></a> クエリ  
 グラフィカル クエリ デザイナーのデザイン モードまたはクエリ モードを使用すると、データ ソース上の基になるデータ構造を参照しながら、多次元式 (MDX) クエリを作成できます。 デザイン時には、クエリ デザイナーから対話的にクエリを実行して結果を確認することができます。 作成したクエリによって、データセットのフィールドが定義されます。 実行時には、データ ソースから実際のデータが返されます。 グラフィカル クエリ デザイナーでは、次の操作を実行できます。  
  
-   デザイン モードでは、ディメンション、メンバー、メンバーのプロパティ、主要データなどを、データ ソースからデータ ペインにドラッグして、多次元式 (MDX) クエリを作成できます。 計算されるメンバー ペインから、計算されるメンバーをデータ ペインにドラッグして、追加のデータセット フィールドを定義できます。  
  
-   クエリ モードでは、ディメンション、メンバー、メンバーのプロパティ、主要データなどをクエリ ペインにドラッグするか、MDX テキストを直接クエリ ペインに入力できます。 計算されるメンバー ペインから、計算されるメンバーをデータ ペインにドラッグして、追加のデータセット フィールドを定義できます。  
  
 クエリを作成すると、クエリ デザイナーは MDX クエリに既定のプロパティを自動的に追加します。 既定のプロパティ以外のプロパティを含めるには、MDX クエリを手動で変更する必要があります。  
  
 関連付けられているクエリ デザイナーについて詳しくは、「[SAP NetWeaver BI Query Designer のユーザー インターフェイス&#40;レポート ビルダー&#41;](../Topic/SAP%20NetWeaver%20BI%20Query%20Designer%20User%20Interface%20\(Report%20Builder\).md)」をご覧ください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Extended"></a> 拡張フィールド プロパティ  
 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースは、拡張フィールド プロパティをサポートしています。 拡張フィールド プロパティは、**Value** と **IsMissing** に追加する形で、データ処理拡張機能によってデータセットのフィールドに定義されるプロパティです。 拡張プロパティには、定義済みプロパティとカスタム プロパティがあります。 定義済みのプロパティは、複数のデータ ソースに共通のプロパティです。 カスタム プロパティは、各データ ソースの固有のプロパティです。  
  
### フィールド プロパティの操作  
 拡張フィールド プロパティは、レポート レイアウトにドラッグすることのできるアイテムとして [レポート データ] ウィンドウには表示されません。 その代わりに、このプロパティの親フィールドをレポートにドラッグすることによって、既定のプロパティである **Value** を必要なプロパティに変更することが可能です。 たとえば、MDX クエリ デザイナーで、メタデータ ペインからクエリ ペインにレベルをドロップすることによって **Calendar Year/Month Level 01** というフィールド名を作成した場合、カスタムの拡張プロパティ **Long Name** を式の中で参照するには、次の構文を使用します。  
  
 `=Fields!Calendar_Year_Month_Level_01("Long Name")`  
  
 メタデータ ペインでフィールドにカーソルを合わせると、拡張フィールド プロパティの名前がツールヒントに表示されます。 基になっているデータの調査に使用できるクエリ デザイナーについて詳しくは、「[SAP NetWeaver BI Query Designer のユーザー インターフェイス](../../reporting-services/report-data/sap-netweaver-bi-query-designer-user-interface.md)」をご覧ください。  
  
> [!NOTE]  
>  拡張フィールド プロパティに対応する値が存在するのは、レポートを実行して対応するデータセットのデータを取得する際に、データ ソースによって値が提供された場合のみです。 その場合、以下に示す構文を使用して、すべての式からこれらの **Field** プロパティ値を参照できます。 ただし、これらのフィールドはこのデータ プロバイダーに固有であり、レポート定義言語には含まれないため、これらの値に加えた変更はレポート定義には保存されません。  
  
 定義済みの拡張プロパティを式の中で参照するには、次のいずれかの構文を使用します。  
  
-   *Fields!FieldName.PropertyName*  
  
-   *Fields!FieldName("PropertyName")*  
  
 カスタム拡張プロパティを式の中で参照するには、次の構文を使用します。  
  
-   *Fields!FieldName("PropertyName")*  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
### 定義済みフィールド プロパティ  
 次の表に、[!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースで使用できる定義済みフィールド プロパティの一覧を示します。  
  
|**プロパティ**|**型**|**説明/有効値**|  
|------------------|--------------|---------------------------------------|  
|**値**|**オブジェクト**|フィールドのデータ値を指定します。|  
|**IsMissing**|**ブール値**|フィールドが結果データセットに存在するかどうかを示します。|  
|**FormattedValue**|**文字列**|主要データの書式設定した値を返します。|  
|**BackgroundColor**|**文字列**|データベースで定義されたフィールドの背景色を返します。|  
|**色**|**文字列**|データベースで定義されたアイテムの前景色を返します。|  
|**[キー]**|**オブジェクト**|レベルのキーを返します。|  
|**LevelNumber**|**Integer**|親子階層の場合は、レベル番号またはディメンション番号を返します。|  
|**ParentUniqueName**|**文字列**|親子階層の場合は、親レベルの完全修飾名を返します。|  
|**UniqueName**|**文字列**|レベルの完全修飾名を返します。 たとえば、従業員の **UniqueName** の値は *[0D_Company].[10D_Department].[11]* のようになります。|  
  
 フィールドおよびフィールド プロパティを式で使用する方法について詳しくは、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder-and-ssrs.md)」をご覧ください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Remarks"></a> 解説  
 このデータ プロバイダーでは使用できないレポート配信モードもあります。 このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。 詳しくは、「[サブスクライバー データに対して外部データ ソースを使用する &#40;データ ドリブン サブスクリプション&#41;](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」をご覧ください。  
  
 詳しくは、「[Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence (SAP NetWeaver Business Intelligence で SQL Server 2008 Reporting Services を使用する)](http://go.microsoft.com/fwlink/?LinkId=167352)」をご覧ください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="HowTo"></a> 操作方法に関するトピック  
 データ接続、データ ソース、およびデータセットを操作する手順について説明します。  
  
 [データ接続またはデータ ソースの追加および確認 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [共有データセットまたは埋め込みデータセットの作成 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [データセットへのフィルターの追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Related"></a> 関連項目  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義、カスタマイズ、および使用する手順が説明されています。  
  
 [レポート データセット &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 クエリによって生成されるデータセット フィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
## 参照  
 [レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  