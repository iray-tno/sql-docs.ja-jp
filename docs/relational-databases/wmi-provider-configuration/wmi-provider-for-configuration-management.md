---
title: WMI Provider for Configuration Management Concepts |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management
- SQL Server WMI Provider
- configuration management [WMI]
- WMI Provider for Configuration Management, about WMI Provider for Configuration Management
ms.assetid: 7e41db24-b915-4eb8-a1d6-e6948ee915b7
caps.latest.revision: 24
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5336850afaa1ac5073d0efbd81b4746b2acd5043
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33011089"
---
# <a name="wmi-provider-for-configuration-management"></a>WMI Provider for Configuration Management
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  WMI プロバイダーは、パブリッシュされたレイヤーで使用される、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager のスナップインで[!INCLUDE[msCoName](../../includes/msconame-md.md)]管理コンソール (MMC) および[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager です。 これにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーから要求されたレジストリ操作を処理する API 呼び出しは、統一されたインターフェイスで操作できます。また、選択された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスに対して高度な制御および操作を行えます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップによって自動的にコンパイルされる DLL ファイルおよび MOF ファイルです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダーには、コントロールに使用するオブジェクトのクラスのセットが含まれています、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスの次のメソッドを使用します。  
  
-   WQL (Windows Query Language) を埋め込むことができる VBScript、[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)]、Perl などのスクリプト言語。  
  
-   SMO マネージ コード プログラム内の <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクト。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダー スナップインを持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは MMC。  
  
## <a name="using-a-script-language"></a>スクリプト言語の使用  
 スクリプト言語の使用には、次のような利点があります。  
  
-   開発環境が不要。  
  
-   スクリプト言語をサポートするファイルが幅広く利用可能。  
  
 スクリプトは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダーに加えて、その他の WMI プロバイダーでも機能することができます。 ドメイン管理者は、スクリプトを使用して、ネットワーク上の複数のコンピューターのサービスの設定、ネットワーク設定、および別名設定を行うことができます。  
  
 このセクションでは、スクリプトから構成管理用の WMI プロバイダーにアクセスする方法についてより詳細に説明します。  
  
## <a name="using-the-smo-managedcomputer-object"></a>SMO ManagedComputer オブジェクトの使用  
 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクトは、構成管理用 WMI プロバイダーへのアクセスを提供する SMO マネージ オブジェクトです。 SMO プログラムを使用すると、<xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクトを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク設定、別名設定の表示と修正を行うことができます。 詳細については、次を参照してください。 [Services の管理とネットワークの設定を使用して WMI プロバイダーによって](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)です。  
  
## <a name="using-the-microsoft-management-console-or-sql-server-configuration-manager"></a>Microsoft 管理コンソールまたは SQL Server 構成マネージャーの使用  
 Microsoft 管理コンソール (MMC) は、スクリプティング言語またはマネージド コード プログラムではなく、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを管理するインターフェイスを提供します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理 MMC スナップインを使用して、サービスの停止や開始、およびサービス アカウントの変更を行うことができます。  
  
 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、クライアント プロトコルとサーバー プロトコル、およびサーバー別名を管理することができます。  
  
## <a name="see-also"></a>参照  
 [WMI Provider for Configuration Management の理解](../../relational-databases/wmi-provider-configuration/understanding-the-wmi-provider-for-configuration-management.md)   
 [WMI Provider for Configuration Management の使用](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [WQL を使用して、スクリプティング言語での WMI Provider for Configuration Management](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
