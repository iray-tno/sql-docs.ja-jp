---
title: "参照リレーションシップと参照リレーションシップのプロパティの定義 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
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
  - "参照ディメンションのリレーションシップ"
  - "リレーションシップ [Analysis Services], 参照ディメンション"
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# 参照リレーションシップと参照リレーションシップのプロパティの定義
  参照ディメンションのリレーションシップは、キューブ デザイナーの **[ディメンションの使用法]** タブで定義します。 参照ディメンションのリレーションシップを定義するには、以下を指定します。  
  
-   結合先の中間ディメンション。 標準ディメンションまたは別の参照ディメンションを指定します。  
  
-   ディメンションがメジャー グループについての集計に使用できる最も低いレベルを定義する参照ディメンション属性。  
  
-   参照ディメンション属性に対応する中間ディメンションの (外部キー) 属性。  
  
 通常、参照ディメンションをファクト テーブルにリンクする列は参照ディメンションのキー属性ですが、この列を中間ディメンションの属性として定義する必要もあります。 参照ディメンションのチェーンを作成する場合は、まず、チェーンの最初のディメンションとメジャー グループ間に標準のリレーションシップを作成します。 次に、追加の各参照リレーションシップを順に作成します。 参照リレーションシップは、メジャー グループとのリレーションシップが既にあるディメンションに対してのみ作成できます。  
  
 参照ディメンションのリレーションシップを作成すると、ディメンション属性のリンクが既定で具体化されます。 ディメンション属性のリンクを具体化すると、各行のファクト テーブルおよび参照ディメンション間のリンクの値が具体化され、処理中にディメンションの MOLAP 構造に格納されます。 この操作を行うと、処理パフォーマンスやストレージの要件にわずかに影響しますが、クエリ パフォーマンスの向上を図ることができます。  
  
 参照ディメンションでは、参照ディメンションと参照ディメンションのメイン テーブルに対応するメジャー グループ間のリレーションシップを定義する属性を特定することにより、粒度が指定されます。 複数の参照ディメンションを連結すると、最も外側のディメンションからメジャー グループまでのリレーションシップが参照によって定義されます。  
  
  