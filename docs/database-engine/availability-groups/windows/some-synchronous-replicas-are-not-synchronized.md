---
title: "いくつかの同期のレプリカが同期されていません | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.agp5synchronized.issues.f1"
helpviewer_keywords: 
  - "可用性グループ [SQL Server]、ポリシー"
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
caps.latest.revision: 11
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 11
---
# いくつかの同期のレプリカが同期されていません
    
## 概要  
  
|||  
|-|-|  
|**ポリシー名**|同期レプリカのデータの同期状態|  
|**問題点**|一部の同期レプリカが同期されていません。|  
|**カテゴリ**|**警告**|  
|**ファセット**|可用性グループ|  
  
## 説明  
 このポリシーは、すべての可用性レプリカのデータ同期状態をロール アップし、期待される状態とは異なる可用性レプリカがないかどうかを確認します。 非同期レプリカが SYNCHRONIZING 状態ではない場合、および同期レプリカが SYNCHRONIZED 状態ではない場合、ポリシーは異常な状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のこのリリース向けに、TechNet Wiki の「[Some synchronous replicas are not synchronized (一部の同期レプリカが同期されていない)](http://go.microsoft.com/fwlink/p/?LinkId=220853)」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## 考えられる原因  
 この可用性グループには、現在同期されていない同期レプリカが少なくとも 1 つ存在します。 レプリカの同期状態は、SYNCHONIZING と NOT SYNCHRONIZING のいずれかになります。  
  
## 考えられる解決方法  
 可用性レプリカのポリシーの状態を検索条件として、同期状態が不適切な可用性レプリカを探し、問題を解決してください。  
  
## 参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  