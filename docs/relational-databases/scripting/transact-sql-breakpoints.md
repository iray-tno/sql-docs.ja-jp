---
title: "Transact-SQL ブレークポイント | Microsoft Docs"
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
  - "Transact-SQL デバッガー, ブレークポイント"
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Transact-SQL ブレークポイント
  ブレークポイントは、特定の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーの実行の一時停止を指定し、その時点のコード要素の状態を確認できます。  
  
## ブレークポイント  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーの実行時に、特定のステートメントでブレークポイントを切り替えることができます。 ブレークポイントが含まれているステートメントに到達すると、デバッガーの実行は一時停止され、変数やパラメーターに存在する値などの情報を表示できます。  
  
 ブレークポイントの管理は、個別にエディター ウィンドウで、またはまとめて **[ブレークポイント]** ウィンドウで行うことができます。 ブレークポイントを編集することにより、実行を一時停止する条件や、ブレークポイント実行時の動作を指定できます。  
  
## ブレークポイントのタスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|デバッガーを一時停止する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを指定する方法について説明します。|[ブレークポイントの切り替え](../../relational-databases/scripting/toggle-a-breakpoint.md)|  
|ブレークポイントを一時的に非アクティブ化し、後で再アクティブ化する方法について説明します。 ブレークポイントを削除する方法についても説明します。|[ブレークポイントの有効化、無効化、および削除](../../relational-databases/scripting/enable-disable-and-delete-breakpoints.md)|  
|指定した Transact-SQL 式の評価に基づいてブレークポイントがブレークするかどうかを決定する条件を指定する方法について説明します。|[ブレークポイント条件の指定](../../relational-databases/scripting/specify-a-breakpoint-condition.md)|  
|ブレークポイントを含むステートメントが指定の回数実行されたときにのみ、ブレークポイントがブレークするように、ヒット カウントを指定する方法について説明します。|[ヒット カウントの指定](../../relational-databases/scripting/specify-a-hit-count.md)|  
|指定されたプロセスまたはスレッドでのみブレークポイントがブレークするように、フィルターを指定する方法について説明します。|[ブレークポイント フィルターの指定](../../relational-databases/scripting/specify-a-breakpoint-filter.md)|  
|ブレークポイント ステートメントが実行されるときに行われるカスタム操作である、**ヒット時**アクションを指定する方法について説明します。 例としては、メッセージの出力などが考えられます。|[ブレークポイント アクションの指定](../../relational-databases/scripting/specify-a-breakpoint-action.md)|  
|ブレークポイントの場所を編集する方法について説明します。|[ブレークポイントの位置の編集](../../relational-databases/scripting/edit-a-breakpoint-location.md)|  
  
## 参照  
 [Transact-SQL デバッガー情報](../../relational-databases/scripting/transact-sql-debugger-information.md)  
  
  