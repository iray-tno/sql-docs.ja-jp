---
title: スナップショット エージェント | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.snapshotagent.f1
helpviewer_keywords:
- Snapshot Agent dialog box
ms.assetid: b715e621-2cd5-4a15-8f58-a341aa8ef5e4
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6db035e4a53877b3088d9e724303dde0cfc72908
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32961507"
---
# <a name="snapshot-agent"></a>スナップショット エージェント
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[スナップショット エージェント]** ダイアログ ボックスには、状態、履歴、情報メッセージ、およびすべてのエラー メッセージを含む、スナップショット エージェントの詳細情報が表示されます。  
  
## <a name="options"></a>および  
 表示するスナップショット エージェントのセッションを **[表示]** メニューで選択した後、 **[スナップショット エージェントのセッション]** というラベルのグリッドで特定のセッションを選択します。 このセッションの詳細情報は、 **[選択されたセッションのアクション]** というラベルのグリッドに表示されます。 選択したセッションがエラーで終了した場合は、 **[選択されたセッションのエラーの詳細またはメッセージ]** というラベルのテキスト領域も表示されます。  
  
 **[表示]**  
 表示するスナップショット エージェント セッションを選択します。  
  
 **ステータス**  
 スナップショット エージェントの状態です。 表示される状態の種類を、次に示します。  
  
-   [エラー]  
  
-   [失敗したコマンドの再試行]  
  
-   [実行されていません]  
  
-   [完了]  
  
 **Start Time**  
 セッションの開始時刻です。  
  
 **[終了時刻]**  
 セッションの終了時刻です。 エージェントが停止していない場合は、このフィールドは空になっています。  
  
 **Duration**  
 このセッションでスナップショット エージェントが実行された時間の合計です。 この時間は、エージェントが現在実行中の場合の経過時間と、エージェント セッションが終了した場合のセッションの合計時間を表します。  
  
 **エラー メッセージ**  
 セッションがエラーで終了した場合、スナップショット エージェントによって記録された最新のエラー メッセージが表示されます。 セッションがエラーで終了しなかった場合は、このフィールドは空白です。  
  
 **[動作メッセージ]**  
 選択したセッション中にスナップショット エージェントによって記録された、すべての情報メッセージとエラー メッセージです。  
  
 **[動作時間]**  
 **[動作メッセージ]** 列で説明されたアクションが実行された時間です。  
  
 **[選択されたセッションのエラーの詳細またはメッセージ]**  
 選択したセッションの **[状態]** 列に **[エラー]** の値が表示されている場合にのみ表示されます。 このテキスト領域では、エラーの詳細情報とエラーの発生時に試行されたコマンドが表示されます。 エラーに関連する追加コンテンツへのリンクも含まれます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
