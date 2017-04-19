---
title: "シーケンス コンテナー | Microsoft Docs"
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
  - "sql13.dts.designer.sequencecontainer.f1"
helpviewer_keywords: 
  - "シーケンス コンテナー"
  - "制御フローのグループ化"
  - "コンテナー [Integration Services], シーケンス"
  - "制御フローのサブセット [Integration Services]"
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 48
---
# シーケンス コンテナー
  シーケンス コンテナーは、パッケージ制御フローのサブセットである制御フローを定義します。 シーケンス コンテナーは、パッケージを複数の個別の制御フローにグループ化します。各制御フローには、パッケージ制御フロー全体の中で実行される、1 つ以上のタスクおよびコンテナーが含まれます。  
  
 シーケンス コンテナーには、他のコンテナーの他に、複数のタスクを含めることができます。 シーケンス コンテナーにタスクとコンテナーを追加する手順は、タスクとコンテナーをドラッグする先がパッケージ コンテナーではなくシーケンス コンテナーであること以外は、パッケージに追加する手順と同様です。 シーケンス コンテナーに複数のタスクまたはコンテナーが含まれる場合、パッケージの場合と同様に、優先順位制約を使用してそれらを連結できます。 優先順位制約の詳細については、「[優先順位制約](../../integration-services/control-flow/precedence-constraints.md)」を参照してください。  
  
 シーケンス コンテナーを使用すると、次のような多くの利点があります。  
  
-   タスクのグループを無効にして、パッケージ制御フローの 1 つのサブセットに集中してパッケージをデバッグできるようにします。  
  
-   個別のタスクではなくシーケンス コンテナー上でプロパティを設定することにより、複数タスクのプロパティを 1 か所で管理します。  
  
     たとえば、シーケンス コンテナーの **Disable** プロパティを **True** に設定すると、シーケンス コンテナーのすべてのタスクとコンテナーを無効にできます。  
  
-   関連タスクおよびコンテナーのグループが使用する、変数の範囲を指定します。  
  
-   多数のタスクをグループ化すると、シーケンス コンテナーの折りたたみおよび展開によってタスクを簡単に管理できるようになります。  
  
     また、タスク グループを作成すると、**[グループ]** ボックスで展開および折りたたみを行うことができます。 ただし、**[グループ]** ボックスはデザイン時の機能であり、プロパティがなく、実行時には動作しません。 詳細については、「[コンポーネントのグループ化とグループの解除](../../integration-services/group-or-ungroup-components.md)」を参照してください。  
  
-   シーケンス コンテナー上でトランザクションの属性を設定し、パッケージ制御フローのサブセットのトランザクションを定義します。 この方法により、より細かなレベルでトランザクションを管理できます。  
  
     たとえば、シーケンス コンテナーに 2 つの関連タスクが含まれ、1 つはテーブル内のデータを削除するタスクで、もう 1 つはテーブルにデータを挿入するタスクの場合、挿入アクションが失敗した場合に削除アクションをロールバックするようにトランザクションを構成できます。 詳細については、「[Integration Services のトランザクション](../../integration-services/integration-services-transactions.md)」を参照してください。  
  
## シーケンス コンテナーの構成  
 シーケンス コンテナーにはカスタム ユーザー インターフェイスはなく、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の **[プロパティ]** ウィンドウ、またはプログラムによってのみ構成できます。  
  
 プログラムによってこれらのプロパティを設定する方法の詳細については、開発者ガイドの **T:Microsoft.SqlServer.Dts.Runtime.Sequence** クラスのドキュメントを参照してください。  
  
## 関連タスク  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でコンポーネントのプロパティを設定する方法については、「[タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)」を参照してください。  
  
## 参照  
 [制御フローのタスクまたはコンテナーを追加または削除する](../../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [既定の優先順位制約を使用してタスクとコンテナーを連結する](../Topic/Connect%20Tasks%20and%20Containers%20by%20Using%20a%20Default%20Precedence%20Constraint.md)   
 [Integration Services コンテナー](../../integration-services/control-flow/integration-services-containers.md)  
  
  