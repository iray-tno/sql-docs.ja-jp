---
title: "Analysis Services データベースに対する拡張フィールド プロパティ (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d7d87e2-bf0d-4ebb-a287-80b5a967a3f2
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# Analysis Services データベースに対する拡張フィールド プロパティ (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ処理拡張機能では、拡張フィールド プロパティがサポートされています。 拡張フィールド プロパティとは、データ ソースにありデータ処理拡張機能でサポートされるフィールド プロパティ **Value** および **IsMissing** に加えて使用するプロパティです。 拡張プロパティは、レポート データセットのフィールド コレクションの一部としてレポート データ ペインには表示されません。 拡張フィールド プロパティ値をレポートに含めるには、組み込み **Fields** コレクションを使用して名前で拡張フィールド プロパティ値を指定する式を記述します。  
  
 拡張プロパティには、定義済みプロパティとカスタム プロパティがあります。 定義済みプロパティとは、特定のフィールド プロパティ名にマップされ、組み込み **Fields** コレクションを介して名前でアクセスできる、複数のデータ ソースに共通のプロパティです。 カスタム プロパティは、各データ プロバイダーに固有であり、拡張プロパティ名を文字列として扱う構文のみを使用して、組み込み **Fields** コレクションを介してアクセスできます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX クエリ デザイナーをグラフィカル モードで使用してクエリを定義する場合、定義済みの一連のセル プロパティおよびディメンション プロパティが自動的に MDX クエリに追加されます。 レポート内では、MDX クエリに明記されている拡張プロパティのみを使用できます。 レポートによっては、既定の MDX コマンド テキストを変更して、キューブに定義されている他のディメンションまたはカスタム プロパティを含めることができます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースで使用できる拡張フィールドの詳細については、「[プロパティ値の作成および使用 (MDX)](../Topic/Creating%20and%20Using%20Property%20Values%20\(MDX\).md)」を参照してください。  
  
## レポートのフィールド プロパティの操作  
 拡張フィールド プロパティには、定義済みプロパティとデータ プロバイダー固有のプロパティがあります。 フィールド プロパティは、データセット用に作成されたクエリに存在しますが、**レポート データ** ペインのフィールド一覧に表示されません。したがって、フィールド プロパティをレポートのデザイン画面にドラッグすることはできません。 その代わり、フィールドをレポートにドラッグし、フィールドの **Value** プロパティを、使用するプロパティに変更します。 たとえば、キューブからのセル データが既に書式設定されている場合は、`=Fields!FieldName.FormattedValue` の式を使用することで、FormattedValue フィールド プロパティを使用できます。  
  
 事前に定義されていない拡張プロパティを参照するには、式で次の構文を使用します。  
  
-   *Fields!FieldName("PropertyName")*  
  
## 定義済みフィールド プロパティ  
 ほとんどの場合、定義済みフィールド プロパティはメジャー、レベル、またはディメンションに適用されます。 定義済みフィールド プロパティは、対応する値が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースに格納されている必要があります。 値が存在しない場合、または、レベルにメジャーのみのフィールド プロパティを指定する場合、プロパティは NULL 値を返します。  
  
 次の構文のいずれかを使用して、式から定義済みプロパティを参照できます。  
  
-   *Fields!FieldName.PropertyName*  
  
-   *Fields!FieldName("PropertyName")*  
  
 次の表に、使用できる定義済みフィールド プロパティの一覧を示します。  
  
|**プロパティ**|**型**|**説明/有効値**|  
|------------------|--------------|---------------------------------------|  
|**値**|**オブジェクト**|フィールドのデータ値を指定します。|  
|**IsMissing**|**ブール値**|フィールドが結果データセットに存在するかどうかを示します。|  
|**UniqueName**|**文字列**|レベルの完全修飾名を返します。 たとえば、従業員の **UniqueName** 値は *[Employee].[Employee Department].[Department].&[Sales].&[North American Sales Manager].&[272]* のようになります。|  
|**BackgroundColor**|**文字列**|データベースで定義されたフィールドの背景色を返します。|  
|**色**|**文字列**|データベースで定義されたアイテムの前景色を返します。|  
|**FontFamily**|**文字列**|データベースで定義されたアイテムのフォント名を返します。|  
|**フォントサイズ**|**文字列**|データベースで定義されたアイテムのフォントのポイント サイズを返します。|  
|**フォント太さ**|**文字列**|データベースで定義されたアイテムのフォントの太さを返します。|  
|**FontStyle**|**文字列**|データベースで定義されたアイテムのフォントのスタイルを返します。|  
|**TextDecoration**|**文字列**|データベースで定義されたアイテムの特殊なテキストの書式設定を返します。|  
|**FormattedValue**|**文字列**|メジャーまたは主要データに対して書式設定した値を返します。 たとえば、**Sales Amount Quota** の **FormattedValue** プロパティは、$1,124,400.00 などの通貨形式を返します。|  
|**[キー]**|**オブジェクト**|レベルのキーを返します。|  
|**LevelNumber**|**Integer**|親子階層の場合は、レベル番号またはディメンション番号を返します。|  
|**ParentUniqueName**|**文字列**|親子階層の場合は、親レベルの完全修飾名を返します。|  
  
> [!NOTE]  
>  レポートが実行されてそのデータセットのデータを取得する際にデータ ソース ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] キューブなど) によってこれらの値が提供される場合にのみ、これらの拡張フィールド プロパティに対応する値が存在します。 その場合、次のセクションに示す構文を使用して、すべての式からこれらのフィールド プロパティ値を参照できます。 ただし、これらのフィールドはこのデータ プロバイダーに固有であるため、これらの値に加えた変更はレポート定義には保存されません。  
  
### 拡張プロパティの例  
 拡張プロパティの例として、次の MDX クエリおよび結果セットには、キューブに対して定義されているディメンション属性で使用できるいくつかのメンバー プロパティが含まれています。 含まれているメンバー プロパティは、MEMBER_CAPTION、UNIQUENAME、Properties("Day Name")、MEMBER_VALUE、PARENT_UNIQUE_NAME、および MEMBER_KEY です。  
  
 この MDX クエリは、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベースに付属している [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW データベース内の [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] キューブに対して実行されます。  
  
```  
WITH MEMBER [Measures].[DateCaption]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_CAPTION'   
   MEMBER [Measures].[DateUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.UNIQUENAME'   
   MEMBER [Measures].[DateDayName]   
      AS '[Date].[Date].Properties("Day Name")'   
   MEMBER [Measures].[DateValueinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_VALUE'   
   MEMBER [Measures].[DateParentUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.PARENT_UNIQUE_NAME'   
   MEMBER [Measures].[DateMemberKeyinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_KEY'   
SELECT {  
   [Measures].[DateCaption],   
   [Measures].[DateUniqueName],   
   [Measures].[DateDayName],   
   [Measures].[DateValueinOriginalDatatype],  
   [Measures].[DateParentUniqueName],  
   [Measures].[DateMemberKeyinOriginalDatatype]  
   } ON COLUMNS , [Date].[Date].ALLMEMBERS ON ROWS   
FROM [Adventure Works]  
  
```  
  
 このクエリを MDX クエリ ペインで実行すると、1,158 行の結果セットが返されます。 最初の 4 行を次の表に示します。  
  
|DateCaption|DateUniqueName|DateDayName|DateValueinOriginalDatatype|DateParentUniqueName|DateMemberKeyinOriginalDatatype|  
|-----------------|--------------------|-----------------|---------------------------------|--------------------------|-------------------------------------|  
|All Periods|[Date].[Date].[All Periods]|(null)|(null)|(null)|0|  
|1-Jul-01|[Date].[Date].&[1]|日曜日|7/1/2001|[Date].[Date].[All Periods]|1|  
|2-Jul-01|[Date].[Date].&[2]|月曜日|7/2/2001|[Date].[Date].[All Periods]|2|  
|3-Jul-01|[Date].[Date].&[3]|火曜日|7/3/2001|[Date].[Date].[All Periods]|3|  
  
 MDX クエリ デザイナーのグラフィカル モードを使用して作成される既定の MDX クエリに、ディメンション プロパティとして含まれるのは MEMBER_CAPTION と UNIQUENAME のみです。 既定では、これらの値は常に **String** データ型です。  
  
 メンバー プロパティの元のデータ型を保持する必要がある場合は、テキスト ベースのクエリ デザイナーで既定の MDX ステートメントを変更することによって、追加のプロパティ MEMBER_VALUE を含めることができます。 次の単純な MDX ステートメントでは、取得するディメンション プロパティのリストに MEMBER_VALUE が追加されています。  
  
```  
SELECT NON EMPTY {[Measures].[Order Count]} ON COLUMNS,   
NON EMPTY { ([Date].[Month of Year].[Month of Year] ) }   
DIMENSION PROPERTIES   
   MEMBER_CAPTION, MEMBER_UNIQUE_NAME, MEMBER_VALUE ON ROWS   
FROM [Adventure Works]  
CELL PROPERTIES   
   VALUE, BACK_COLOR, FORE_COLOR,   
   FORMATTED_VALUE, FORMAT_STRING,   
   FONT_NAME, FONT_SIZE, FONT_FLAGS  
```  
  
 MDX 結果ペインに表示された結果の最初の 4 行を次の表に示します。  
  
|Month of Year|Order Count|  
|-------------------|-----------------|  
|January|2,481|  
|February|2,684|  
|March|2,749|  
|April|2,739|  
  
 プロパティは MDX の SELECT ステートメントに含まれていますが、結果セット列には表示されません。 そこで、拡張プロパティ機能を使用すると、データをレポートに使用することができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の MDX クエリ結果ペインで、セルをダブルクリックすると、セルのプロパティ値が表示されます (キューブ内で設定されている場合)。 1,379 という値が格納されている最初の Order Count セルをダブルクリックすると、ポップアップ ウィンドウに次のセル プロパティが表示されます。  
  
|プロパティ|値|  
|--------------|-----------|  
|CellOrdinal|0|  
|VALUE|2481|  
|BACK_COLOR|(null)|  
|FORE_COLOR|(null)|  
|FORMATTED_VALUE|2,481|  
|FORMAT_STRING|#,#|  
|FONT_NAME|(null)|  
|FONT_SIZE|(null)|  
|FONT_FLAGS|(null)|  
  
 このクエリを使用してレポート データセットを作成し、データセットをテーブルにバインドすると、フィールドの既定の VALUE プロパティが表示されます (たとえば `=Fields!Month_of_Year!Value`)。 Value フィールドでは **String** データ型が使用されるので、この式をテーブルの並べ替え式として設定した場合、テーブルは月のアルファベット順に並べ替えられます。 月がカレンダー順に並ぶ (つまり、January が先頭に来て December が最後に来る) ようにテーブルを並べ替えるには、次の式を使用します。  
  
```  
=Fields!Month_of_Year("MEMBER_VALUE")  
```  
  
 これにより、データ ソースの元の整数データ型に基づいてフィールドの値が並べ替えられます。  
  
## 参照  
 [式 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [式で使用される組み込みコレクション (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder-and-ssrs.md)   
 [データセット フィールド コレクション (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  