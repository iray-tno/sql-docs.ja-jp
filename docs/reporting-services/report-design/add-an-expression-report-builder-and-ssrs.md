---
title: "式の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# 式の追加 (レポート ビルダーおよび SSRS)
  レポート アイテムのプロパティ、フィルター、グループ、並べ替え順、接続文字列、パラメーター値などを定義するために、レポートには随所に式が使用されます。 式は等号 (=) で始まり、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] に書き込まれます。 式は、評価結果とレポート レイアウト要素を組み合わせるレポート プロセッサによって実行時に評価されます。  
  
 式には単純式と複合式があります。 単純式は、組み込みコレクションの 1 つのアイテムを指します。 複合式には、定数、演算子、グローバル コレクションのアイテム、および関数呼び出しを含めることができます。 詳細については、「[式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### テキスト ボックスに式を追加するには  
  
-   **[デザイン]** ビューで、式を追加するデザイン画面のテキスト ボックスをクリックします。  
  
    -   単純式の場合、テキスト ボックスに式の表示テキストを入力します。 たとえば、Sales データセット フィールドには、`[Sales]` を入力します。  
  
    -   複合式の場合、テキスト ボックスを右クリックし、**[式]** をクリックします。 **[式]** ダイアログ ボックスが表示されます。 式ペインの '=' の後に式を入力するか、対話形式で式を作成し、[OK] をクリックします。  
  
         式がデザイン画面に `<<Expr>>`として表示されます。  
  
## 参照  
 [テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [テキスト ボックス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [レポートでの式の使用 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [グループ式の例 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [[式] ダイアログ ボックス &#40;レポート ビルダー&#41;](../Topic/Expression%20Dialog%20Box%20\(Report%20Builder\).md)   
 [式の例 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [レポートにコードを追加する &#40;SSRS&#41;](../../reporting-services/report-design/add-code-to-a-report-ssrs.md)  
  
  