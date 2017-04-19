---
title: "[ユーザー ロールのプロパティ] (Management Studio) | Microsoft Docs"
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
f1_keywords: 
  - "sql13.swb.reportserver.userroleproperties.f1"
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
caps.latest.revision: 27
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 27
---
# [ユーザー ロールのプロパティ] (Management Studio)
  このページを使用すると、アイテムレベルのロールの定義に含まれるタスクを表示できます。 また、このページを使用して、タスク一覧を変更したりロールの説明を変更したりすることもできます。  
  
 アイテムレベルのロールの定義は、ユーザーが特定のアイテム (フォルダー、レポート、リソース、または共有データ ソース) に対して実行する名前付きの一連のタスクです。 ロールの定義は、レポート マネージャーでロールの割り当てを作成するためにユーザーまたはグループに割り当てられます。 ユーザーまたはグループが実行できる内容は、ロールの定義に含まれているタスクによって記述されます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  には、作業に使用できる事前定義されたアイテムレベルのロールの定義が多く含まれています。 定義ごとのタスク一覧を変更することで、ロールの定義を変更できます。 ロールの定義を編集すると、そのロールの定義を含むすべてのロールの割り当てに反映されます。  
  
> [!NOTE]  
>  ユーザー ロールの割り当ては、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。 レポート サーバーが SharePoint 統合モード用に構成されている場合、このページには、SharePoint サイトで定義されているロールと権限レベルに関する読み取り専用の情報が表示されます。  
  
## オプション  
 **名前**  
 ロールの定義名を指定します。  
  
 **Description**  
 ロール定義の説明が表示されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、この説明はこのページにのみ表示されます。 この説明は、レポート マネージャーでロールの割り当てを行う際にそのロールを使用するかどうかを判断するのに役立ちます。  
  
 **タスク**  
 このロール定義で選択できるアイテムレベルのタスクがすべて一覧表示されます。 定義済みタスクの一覧にアイテムを追加または一覧から削除することで、ユーザーがこのロールを使用して特定のアイテムにアクセスする方法を定義できます。 新しいタスクを作成したり、既存のタスクを変更したりすることはできません。 ロールの定義のタスク一覧は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でのみ表示されます。  
  
 **タスクの説明**  
 各タスクに関する情報が表示されます。 タスクの説明を変更することはできません。  
  
## 参照  
 [アイテムレベルのタスク](../../reporting-services/security/item-level-tasks.md)   
 [ロールの定義](../../reporting-services/security/role-definitions.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [タスクと権限](../../reporting-services/security/tasks-and-permissions.md)   
 [Predefined Roles](../../reporting-services/security/predefined-roles.md)  
  
  