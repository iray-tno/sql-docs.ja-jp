---
title: "アップグレード後のプラン ガイドの検証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プラン ガイド [SQL Server], アップグレード後の検証"
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# アップグレード後のプラン ガイドの検証
  アプリケーションを新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリリースにアップグレードした場合は、プラン ガイドの定義を再評価し、テストすることをお勧めします。 新しいリリースでは、パフォーマンス チューニングの要件とプラン ガイドの照合動作が異なる場合があります。 無効なプラン ガイドが原因でクエリが失敗することはありませんが、そのプラン ガイドは使用されずにプランがコンパイルされるので、最適な選択ではない場合があります。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にデータベースをアップグレードした後は、次の作業を実行することをお勧めします。  
  
-   既存のプラン ガイドを [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) 関数を使用して検証する。  
  
-   拡張イベントで、プラン ガイドによって不適切に生成されたプランがないか、[Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) イベントを使用して一定期間の間監視する。  
  
  