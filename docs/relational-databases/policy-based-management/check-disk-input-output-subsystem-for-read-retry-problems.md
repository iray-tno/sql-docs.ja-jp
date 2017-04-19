---
title: "ディスク I/O サブシステムの読み取り再試行の問題の確認 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ベスト プラクティス [データベース エンジン]"
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# ディスク I/O サブシステムの読み取り再試行の問題の確認
  このルールでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のイベント ログにエラー メッセージ 825 があるどうかを確認します。 このメッセージは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が最初の試行ではディスクからデータを読み取れなかったことを示します。 このメッセージは、ディスク I/O サブシステムに大きな問題があることを示しています。 このメッセージは、現時点では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の問題を示していませんが、 ディスクの問題を解決しないと、データの損失やデータベースの破損につながる可能性があります。  
  
## ベスト プラクティスと推奨事項  
 次の操作を行って、原因となっているハードウェアの問題を特定し、解決してください。  
  
-   このメッセージのエラー ログと変数テキストを確認し、問題の原因を明らかにする手掛かりを見つける。  
  
-   ディスク システムを確認する。 この問題は、ディスク、ディスク コントローラー、アレイ カード、またはディスク ドライバーに関連している可能性があります。  
  
-   ディスク システムの状態を調べる最新のユーティリティがあるかどうか、ディスクの製造元に問い合わせる。  
  
-   ドライバーの最新の更新があるかどうか、ディスクの製造元に問い合わせる。  
  
## 詳細情報  
 [MSSQLSERVER_825](../Topic/MSSQLSERVER_825.md)  
  
 [SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  