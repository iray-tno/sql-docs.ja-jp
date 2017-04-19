---
title: "lightweight pooling サーバー構成オプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "既定の簡易プーリング"
  - "オーバーヘッドの削減"
  - "lightweight pooling オプション"
  - "システム オーバーヘッド [SQL Server]"
  - "パフォーマンス [SQL Server], 簡易プーリング"
  - "コンテキスト切り替え [SQL Server], 簡易プーリング オプション"
  - "コンテキストの過度の切り替え [SQL Server]"
  - "オーバーヘッドの軽減"
  - "オーバーヘッド [SQL Server]"
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# lightweight pooling サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **lightweight pooling** オプションは、SMP (symmetric multiprocessing) 環境で発生するコンテキストの過度の切り替えによるシステムのオーバーヘッドを削減する手段を提供する場合に使用します。 コンテキストの過度の切り替えが発生した場合、簡易プーリングを使用してコンテキストの切り替えをインラインで行い、ユーザーまたはカーネルのリング遷移を削減することによって、スループットを向上できます。  
  
 ファイバー モードは、UMS ワーカーのコンテキスト切り替えがパフォーマンスの重大なボトルネックになる状況を対象としています。 この状況はまれであるため、一般的なシステムのパフォーマンスやスケーラビリティがファイバー モードで向上することはほとんどありません。 また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] ではコンテキストの切り替えが改良されているため、ファイバー モードの必要性はさらに少なくなっています。 ルーチン処理にファイバー モード スケジューリングを使用することはお勧めしません。 これは、コンテキストの切り替えがもたらす本来の利点が損なわれることでパフォーマンスが低下する場合があるためと、スレッド ローカル ストレージ (TLS) やスレッド所有オブジェクト (ミューテックス (Win32 カーネル オブジェクトの一種) など) を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部のコンポーネントがファイバー モードでは正常に機能しない場合があるためです。  
  
 **lightweight pooling** を 1 に設定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はファイバー モード スケジューリングに切り替わります。 このオプションの既定値は 0 です。  
  
 **lightweight pooling** オプションは拡張オプションです。 **sp_configure** システム ストアド プロシージャを使用して **lightweight pooling** の設定を変更するには、**show advanced options** を 1 に設定する必要があります。 この設定は、サーバーを再起動した後に有効になります。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 および [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP では、簡易プーリングはサポートされていません。 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] では、簡易プーリングが完全にサポートされています。  
  
> [!NOTE]  
>  簡易プーリングでは、共通言語ランタイム (CLR) の実行はサポートされていません。 "clr enabled" オプションまたは "lightweight pooling" オプションのいずれかを無効にしてください。 CLR に依存していてファイバー モードで正しく動作しない機能には、Hierarchy データ型、レプリケーション、およびポリシー ベースの管理があります。  
  
## 参照  
 [clr enabled サーバー構成オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [clr enabled サーバー構成オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)  
  
  