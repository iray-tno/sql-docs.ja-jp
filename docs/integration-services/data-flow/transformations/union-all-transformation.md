---
title: "全体結合変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.unionalltrans.f1"
helpviewer_keywords: 
  - "データセットのマージ [Integration Services]"
  - "データセットの結合"
  - "全体結合変換"
  - "データセット [Integration Services], マージ"
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# 全体結合変換
  全体結合変換は、複数の入力を 1 つの出力に結合します。 たとえば、5 つの異なるフラット ファイル ソースからの出力を全体結合変換への入力とし、1 つの出力に結合できます。  
  
## 入力および出力  
 変換入力は、変換出力に 1 つずつ追加されます。行の並べ替えは発生しません。 パッケージで並べ替え出力が必要な場合は、全体結合変換ではなくマージ変換を使用する必要があります。  
  
 全体結合変換に連結した最初の入力が変換出力のソースとなり、これから変換出力が作成されます。 全体結合変換に次に連結した入力の列は、変換出力の列にマップされます。  
  
 入力をマージするには、入力の列を出力の列にマップします。 最低 1 つの入力の列を、各出力列にマップする必要があります。 2 つの列の間のマッピングでは、列のメタデータが一致する必要があります。 たとえば、マップされた列は同じデータ型である必要があります。  
  
 マップされた列に文字列データが含まれ、出力列の長さが入力列の長さよりも短い場合、入力列を含めることができるように、出力列の長さが自動的に調整されます。 出力列にマップされない入力列は、出力列の値が NULL に設定されます。  
  
 この変換は、複数の入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
## 全体結合変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[全体結合変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「[全体結合変換エディター](../../../integration-services/data-flow/transformations/union-all-transformation-editor.md)」を参照してください。  
  
 プログラムによって設定できるプロパティの詳細については、「[共通プロパティ](../Topic/Common%20Properties.md)」を参照してください。  
  
 プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。  
  
-   [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## 関連タスク  
 [全体結合変換を使用してデータをマージする](../../../integration-services/data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)  
  
  