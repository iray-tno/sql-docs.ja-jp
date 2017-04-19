---
title: "Web アプリケーションの要件 (マスター データ サービス) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "マスター データ サービス"
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
caps.latest.revision: 40
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 38
---
# Web アプリケーションの要件 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] は、インターネット インフォメーション サービス (IIS) によってホストされる Web アプリケーションです。 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] は Internet Explorer (IE) 9 以降でのみ動作します。 IE 8 以前のバージョン、Microsoft Edge、Chrome はサポートされていません。  
  
 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] Web アプリケーションを作成および構成するには、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] を使用します。 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] は、ローカル コンピューター上の IIS を構成するので、最初に Web 構成タスクを行う場合に最適です。 たとえば、1 つの[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを使用して [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  環境を構成したり、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のスケールアウト配置の最初の Web アプリケーションを構成したりします。 スケールアウト配置の複数の Web サーバーの構成など、より複雑なタスクを実行する場合は、IIS ツールを使用します。  
  
> [!NOTE]  
>  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のコンポーネントをインストールするコンピューターはすべてライセンス供与を受けている必要があります。 詳細については、使用許諾契約書 (EULA) を参照してください。  
  
## 必要条件  
  
### オペレーティング システム  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] をインストールする前に、次の要件を確認してください。    
    
-   [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)    
  
### Microsoft Silverlight  
 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションで作業するには、Silverlight 5 をクライアント コンピューターにインストールする必要があります。 Silverlight の必要なバージョンがない場合、Web アプリケーションで Silverlight を使用する部分に移動したときに、Silverlight をインストールするよう要求されます。 Silverlight 5 は [ここ](http://go.microsoft.com/fwlink/?LinkId=243096)からインストールできます。  
  
### ロールとロール サービス  
 Windows Server 2012 または Windows Server 2012 R2 では、Microsoft 管理コンソール (MMC) にある**サーバー マネージャー**を使用して、**Web サーバー (IIS)** ロールと必要なロール サービスをインストールできます。  
 
 
> [!IMPORTANT]  
>**動的なコンテンツ圧縮**は既定で有効になっています。 CPU 使用率は増加しますが、XML 応答サイズを大幅に縮小し、ネットワーク I/O を節約できます。  詳細については、「[マスター データ サービス &#40;MDS&#41; の新機能](../../master-data-services/what-s-new-in-master-data-services-mds.md)」の「**[CTP 2.0] パフォーマンスの向上**」を参照してください。   
  
||  
|-|  
|[インターネット インフォメーション サービス]<br /><br /> Web 管理ツール<br /><br /> IIS 管理コンソール<br /><br /> World Wide Web サービス<br /><br /> アプリケーション開発<br /><br /> .NET Extensibility 3.5<br /><br /> .NET Extensibility 4.5<br /><br /> ASP.NET 3.5<br /><br /> ASP.NET 4.5<br /><br /> ISAPI 拡張<br /><br /> ISAPI フィルター<br /><br /> HTTP 基本機能<br /><br /> 既定のドキュメント<br /><br /> ディレクトリの参照<br /><br /> HTTP エラー<br /><br /> 静的なコンテンツ<br /><br /> [注: WebDAV 発行はインストールしないでください]<br /><br /> 状態と診断<br /><br /> HTTP ログ<br /><br /> 要求の監視<br /><br /> パフォーマンス<br /><br /> 静的なコンテンツの圧縮<br /><br /> セキュリティ<br /><br /> 要求フィルター<br /><br /> [Windows 認証]|  
  
### 機能 
 Windows Server 2012 および Windows Server 2012 R2 では、**サーバー マネージャー**を使用して、次に示す必要な機能をインストールできます。  
  
||  
|-|  
|.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)<br /><br /> .NET Framework 4.5 Advanced Services<br /><br /> ASP.NET 4.5<br /><br /> WCF サービス<br /><br /> HTTP アクティブ化 [注: これは必須です。]<br /><br /> TCP ポート共有<br /><br /> Windows プロセス アクティブ化サービス<br /><br /> プロセス モデル<br /><br /> .NET 環境<br /><br /> 構成 API|  
  
 前提条件となるサーバーの役割と機能を追加する PowerShell スクリプトのサンプルを次に示します。 前提条件となるサーバーの役割と機能は、環境によって異なります。  
  
```powershell  
Install-WindowsFeature Web-Mgmt-Console, AS-NET-Framework, Web-Asp-Net, Web-Asp-Net45, Web-Default-Doc, Web-Dir-Browsing, Web-Http-Errors, Web-Static-Content, Web-Http-Logging, Web-Request-Monitor, Web-Stat-Compression, Web-Filtering, Web-Windows-Auth, NET-Framework-Core, WAS-Process-Model, WAS-NET-Environment, WAS-Config-APIs  
  
Install-WindowsFeature Web-App-Dev, NET-Framework-45-Features -IncludeAllSubFeature –Restart  
```  
  
 PowerShell コマンドの詳細については、「[Install-WindowsFeature](https://technet.microsoft.com/library/jj205467)」を参照してください。  
  
### アカウントと権限  
  
|型|説明|  
|----------|-----------------|  
|Windows アカウント|Windows のロール、ロール サービス、および機能を構成し、ローカル コンピューター上の IIS にあるアプリケーション プール、Web サイト、および Web アプリケーションを作成して管理する権限がある Windows アカウントを使用して Web サーバー コンピューターにログオンする必要があります。|  
|サービス アカウント|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] で [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]Web アプリケーションを作成するときは、アプリケーションが実行されるアプリケーション プールの ID を指定する必要があります。 このアカウントは、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースの作成時に指定したサービス アカウントと異なっていてもかまいません。<br /><br /> この ID はドメイン ユーザー アカウントである必要があり、データベースにアクセスするために [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースの mds_exec データベース ロールに追加されます。 詳細については、「[データベース ログイン、ユーザー、およびロール &#40;マスター データ サービス&#41;](../../master-data-services/database-logins-users-and-roles-master-data-services.md)」を参照してください。 また、このアカウントは、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Windows グループ **MDS_ServiceAccounts** にも追加されます。このグループには、ファイル システムの一時コンパイル ディレクトリ **MDSTempDir** に対する権限が与えられています。 詳細については、「[フォルダーとファイルの権限 &#40;マスター データ サービス&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md)」を参照してください。|  
  
## 参照  
 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md)   
 [マスター データ サービスのイントール、および IIS のロールと機能の構成](../../sql-server/media/master-data-services.png)       
 [マスター データ マネージャー Web アプリケーションの作成 &#40;マスター データ サービス&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [[Web の構成] ページ &#40;マスター データ サービス構成マネージャー&#41;](../Topic/Web%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)  
  
  