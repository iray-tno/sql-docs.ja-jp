---
title: CLR データベース オブジェクトのデータにアクセス |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
caps.latest.revision: 41
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 85229a6a5475e2b3e1b033cd070a13a008825951
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32921767"
---
# <a name="data-access-from-clr-database-objects"></a>CLR データベース オブジェクトからのデータ アクセス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  共通言語ランタイム (CLR) のルーチンは、のインスタンスに格納されたデータに簡単にアクセスが[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]でこれを実行する、リモート インスタンスに格納されているデータだけでなくです。 ルーチンからどのデータにアクセスできるかは、コードが実行されているユーザー コンテキストによって決まります。 .NET Framework Data Provider for を使用して CLR データベース オブジェクト内からデータにアクセス[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]も呼ばれるとして**SqlClient**です。 これは、開発者がマネージ クライアント アプリケーションや中間層アプリケーションから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データにアクセスする際に使用するプロバイダーと同じです。 このため、ADO.NET の知識を活用することができ、 **SqlClient**クライアントや中間層アプリケーションでします。  
  
> [!NOTE]  
>  ユーザー定義型メソッドとユーザー定義関数では、既定ではデータ アクセスの実行が許可されていません。 設定する必要があります、 **DataAccess**プロパティ**SqlMethodAttribute**または**SqlFunctionAttribute**に**DataAccessKind.Read**を有効にするにはユーザー定義型 (UDT) のメソッドやユーザー定義関数からの読み取り専用データ アクセスします。 UDT またはユーザー定義関数によるデータ変更操作は許可されません。この操作を実行しようとすると、実行時に例外がスローされます。  
  
 ここでは、CLR データベース オブジェクト内からデータにアクセスする際の機能や動作の具体的な違いについて説明します。 ADO.NET の機能の詳細については、.NET Framework SDK に付属の ADO.NET のドキュメントを参照してください。  
  
 次の表は、このセクションのトピックを一覧表示します。  
  
 [コンテキスト接続](../../../relational-databases/clr-integration/data-access/context-connection.md)  
 SQL Server へのコンテキスト接続について説明します。  
  
 [接続の権限借用と資格情報](../../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
 接続の権限借用および接続の資格情報について説明します。  
  
 [ADO.NET に対する SQL Server インプロセス固有の拡張機能](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 プロセス内の固有の説明**SqlPipe**、 **SqlContext**、 **SqlTriggerContext**、および**SqlDataRecord**オブジェクト。  
  
 [CLR 統合とトランザクション](../../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
 System.Transactions 名前空間で提供される新しいトランザクション フレームワークを ADO.NET および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 統合と統合する方法について説明します。  
  
 [CLR データベース オブジェクトからの XML シリアル化](http://msdn.microsoft.com/library/ac84339b-9384-4710-bebc-01607864a344)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部で CLR データベース オブジェクトの XML シリアル化のシナリオを有効にする方法について説明します。  
  
  
