---
title: "ポリシー ベースの管理のストレージ | Microsoft Docs"
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
  - "ポリシー ベースの管理, ストレージ"
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# ポリシー ベースの管理のストレージ
  ポリシーは msdb データベースに格納されます。 ポリシーまたは条件を変更した後、msdb をバックアップする必要があります。 詳細については、「[システム データベースのバックアップと復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)」を参照してください。  
  
## ポリシーの保存  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの監視に使用できるポリシーが用意されています。 これらのポリシーは、[!INCLUDE[ssDE](../../includes/ssde-md.md)] に既定でインストールされませんが、既定のインストール場所である C:\Program Files\Microsoft SQL Server\130\Tools\Policies\DatabaseEngine\1033 からインポートできます。  
  
 ポリシーを直接作成するには、**[ファイル] メニューの [新規作成]** を使用して、ポリシーをファイルに保存します。 これにより、[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスに接続していないときにポリシーを作成できます。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の現在のインスタンスで評価されたポリシーのポリシー履歴は、msdb システム テーブルに格納されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のその他のインスタンスに適用されたポリシーまたは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] や [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に適用されたポリシーのポリシー履歴は保持されません。  
  
  