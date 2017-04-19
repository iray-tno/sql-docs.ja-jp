---
title: "変換を使用してデータを変換する | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ フロー [Integration Services]、変換"
  - "変換 [Integration Services]、変換について"
  - "データの変換 [Integration Services]"
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# 変換を使用してデータを変換する
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、変換元、変換、および変換先という 3 種類のデータ フロー コンポーネントが含まれています。  
  
 次の図は、1 つの変換元、2 つの変換、および 1 つの変換先を持つ、簡単なデータ フローを示しています。  
  
 ![データ フロー](../../../integration-services/data-flow/transformations/media/mw-dts-08.gif "データ フロー")  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の変換では、次の機能が用意されています。  
  
-   行セットを分割、コピー、およびマージしたり、参照操作を実行します。  
  
-   小文字を大文字に変更する変換などを適用することにより、列の値を更新して新しい列を作成します。  
  
-   データのクリーンアップ、テキストのマイニング、データ マイニング予測クエリの実行などのビジネス インテリジェンス操作を実行します。  
  
-   集計または並べ替えられた値、サンプル データ、またはピボットされたデータおよびピボット解除されたデータで構成される、新しい行セットを作成します。  
  
-   データのエクスポートおよびインポート、監査情報の提供、緩やかに変化するディメンションの処理などを行うタスクを実行します。  
  
 詳しくは、「[Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)」をご覧ください。  
  
 カスタムの変換を記述することもできます。 詳しくは、「[カスタム データ フロー コンポーネントの開発](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」と「[特定の種類のデータ フロー コンポーネントの開発](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)」をご覧ください。  
  
 変換をデータ フロー デザイナーに追加した後で、変換を構成する前に、データ フロー内の別の変換または変換元の出力をこの変換の入力に連結することにより、変換をデータ フローに連結します。 2 つのデータ フロー コンポーネント間のコネクタは、パスと呼ばれます。 コンポーネントの連結とパスを使用した作業の詳細については、「[パスを使用してコンポーネントを連結する](../Topic/Connect%20Components%20with%20Paths.md)」をご覧ください。  
  
### 変換をデータ フローに追加するには  
  
-   [データ フローでコンポーネントを追加または削除する](../../../integration-services/data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
### 変換をデータ フローに連結するには  
  
-   [データ フロー内でコンポーネントを連結する](../../../integration-services/data-flow/connect-components-in-a-data-flow.md)  
  
### 変換のプロパティを設定するには  
  
-   [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## 参照  
 [[データ フロー タスク]](../../../integration-services/control-flow/data-flow-task.md)   
 [データ フロー](../../../integration-services/data-flow/data-flow.md)   
 [パスを使用してコンポーネントを連結する](../Topic/Connect%20Components%20with%20Paths.md)   
 [データのエラー処理](../../../integration-services/data-flow/error-handling-in-data.md)   
 [データ フロー](../../../integration-services/data-flow/data-flow.md)  
  
  