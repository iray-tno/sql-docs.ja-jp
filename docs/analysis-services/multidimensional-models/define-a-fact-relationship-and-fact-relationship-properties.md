---
title: "ファクト リレーションシップとファクト リレーションシップのプロパティの定義 | Microsoft Docs"
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
  - "ファクト ディメンション [Analysis Services]"
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# ファクト リレーションシップとファクト リレーションシップのプロパティの定義
  新しいキューブ ディメンションまたは新しいメジャー グループが定義されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ファクト ディメンションのリレーションシップが存在するかどうかを検出し、ディメンションの使用法を **[ファクト]** に設定しようと試みます。 ファクト ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。 ディメンションとメジャー グループ間のファクト リレーションシップには次の制約があります。  
  
-   1 つのキューブ ディメンションには、特定のメジャー グループに対してファクト リレーションシップを 1 つだけ設定できます。  
  
-   1 つのキューブ ディメンションには、複数のメジャー グループに対して個別のファクト リレーションシップを設定できます。  
  
-   リレーションシップの粒度属性は、ディメンションのキー属性 (取引番号など) である必要があります。 これにより、ディメンションとファクト テーブル内のファクトとの間に一対一リレーションシップが作成されます。  
  
  