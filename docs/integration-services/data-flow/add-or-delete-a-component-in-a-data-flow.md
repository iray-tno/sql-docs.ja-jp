---
title: "データ フローでコンポーネントを追加または削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンポーネントの追加"
  - "コンポーネント [Integration Services], データ フロー"
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# データ フローでコンポーネントを追加または削除する
  データ フロー コンポーネントとは、データ フロー内の変換元、変換、および変換先のことです。 コンポーネントをデータ フローに追加するには、データ フロー タスクを事前にパッケージ制御フローに含める必要があります。  
  
 次の手順では、パッケージのデータ フローでコンポーネントを追加または削除する方法について説明します。  
  
### データ フローにコンポーネントを追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックし、コンポーネントを追加するデータ フローが含まれているデータ フロー タスクをダブルクリックします。  
  
4.  ツールボックスで、**[データ フローの変換元]**、**[データ フロー変換]**、または **[データ フローの変換先]** を展開し、次にデータ フロー アイテムを **[データ フロー]** タブのデザイン画面にドラッグします。  
  
5.  更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
### データ フローからコンポーネントを削除するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックし、コンポーネントを削除するデータ フローが含まれているデータ フロー タスクをダブルクリックします。  
  
4.  データ フロー コンポーネントを右クリックし、**[削除]** をクリックします。  
  
5.  削除操作を確認します。  
  
6.  更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## 参照  
 [データ フロー内でコンポーネントを連結する](../../integration-services/data-flow/connect-components-in-a-data-flow.md)   
 [データ フロー コンポーネントでエラー出力を構成する](../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md)   
 [データ フロー](../../integration-services/data-flow/data-flow.md)  
  
  