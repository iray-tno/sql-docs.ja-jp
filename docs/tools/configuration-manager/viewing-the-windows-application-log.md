---
title: "Windows アプリケーション ログの表示 | Microsoft Docs"
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
  - "アプリケーション ログ [SQL Server]"
  - "Windows アプリケーション ログ [SQL Server]"
  - "Windows アプリケーション ログの確認"
  - "エラー [SQL Server], ログ"
  - "システム ログ [SQL Server]"
  - "セキュリティ ログ [SQL Server]"
  - "Windows アプリケーション ログの表示"
  - "ログ [SQL Server], Windows アプリケーション ログ"
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Windows アプリケーション ログの表示
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が Microsoft Windows アプリケーション ログを使用するように構成されている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各セッションでは新しいイベントが書き込まれます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログとは異なり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを開始するたびに新しいアプリケーション ログが作成されることはありません。  
  
 Windows イベント ビューアーまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のログ ビューアーを使用して、Windows アプリケーション ログを表示および管理します。  
  
 イベント ビューアーでは、次の 3 つのログを表示できます。  
  
|Windows ログの種類|Description|  
|----------------------|-----------------|  
|システム ログ|Windows オペレーティング システムのコンポーネントによってログに記録されるイベントを記録します。 たとえば、起動時にドライバーや他のシステム コンポーネントの読み込みが失敗した場合には、システム ログに記録されます。|  
|Security log|失敗したログイン試行などのセキュリティ イベントを記録します。 これは、セキュリティ システムへの変更を監視し、セキュリティ侵害のおそれのある箇所を特定するために役立ちます。 たとえば、システムへのログオン試行は、User Manager の監査設定によってセキュリティ ログに記録できます。<br /><br /> **sysadmin** 固定サーバー ロールのメンバーだけが、セキュリティ ログを表示できます。|  
|アプリケーション ログ|アプリケーションによってログに記録されるイベントを記録します。 たとえば、データベース アプリケーションは、アプリケーション ログにファイル エラーを記録することがあります。|  
  
 イベント ビューアーの使用方法、アプリケーション ログの管理方法、および表示される情報の解釈方法の詳細については、Windows のマニュアルを参照してください。  
  
 **Windows アプリケーション ログを表示するには**  
  
 [Windows アプリケーション ログの表示 &#40;Windows&#41;](../../relational-databases/performance/view-the-windows-application-log-windows.md)  
  
  