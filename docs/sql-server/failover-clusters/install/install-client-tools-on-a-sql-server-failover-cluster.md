---
title: "SQL Server フェールオーバー クラスターへのクライアント ツールのインストール | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c82d510-9798-46be-bebb-cac9bef56936
caps.latest.revision: 9
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 9
---
# SQL Server フェールオーバー クラスターへのクライアント ツールのインストール
  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] などのクライアント ツールは同じマシン上のすべてのインスタンスに共有される共通の機能です。 これらのツールは、サイド バイ サイド インストールが可能な、サポートされている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の旧バージョンと互換性があります。 1 つのノードに同時に存在することのできるライアント ツールのバージョンは 1 つだけです。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のクライアント ツールがセットアップ時に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クラスターの最初のノードにインストールされた場合、後で [ノードの追加] を使って [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにノードが追加された場合、自動的にそのノードにもクライアント ツールが追加されます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックは、[ノードの追加] を使って [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クラスターに追加されたノードに自動的に追加されません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックのローカル コピーが必要なノードには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックを手動でインストールできます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クラスターを初めてインストールしたときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント ツールをインストールしなかった場合、次の手順に従って後でインストールできます。  
  
## インストール手順  
  
#### セットアップのユーザー インターフェイスを使った [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント ツールのインストール  
  
1.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストール メディアを挿入します。 インストールのルート フォルダーにある Setup.exe をダブルクリックします。 ネットワーク共有からインストールするには、ネットワーク共有上のルート フォルダーに移動し、Setup.exe をダブルクリックします。  
  
2.  **[インストール]** ページで、**[[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** をクリックします。 **[[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターの新規インストール]** はクリックしないでください。  
  
3.  セットアップを続行する前に、システム構成チェッカーによってコンピューターのシステム状態が確認されます。  
  
4.  **[インストールの種類]** ページで、**[[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の新規インストールを実行する]** をクリックします。  
  
5.  **[機能の選択]** ページで、インストールするツールを選択して、セットアップ プロセスの残りの手順を進めます。  
  
#### コマンド プロンプトを使った [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント ツールのインストール  
  
1.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント ツールと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックをインストールするには、Setup.exe/q/Action=Install /Features=Tools コマンドを実行します。  
  
2.  基本的な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理ツールだけをインストールするには、Setup.exe/q/Action=Install Features=SSMS コマンドを実行します。 これにより、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]、[!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]、qlcmd ユーティリティ、および [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] Powershell プロバイダーに対する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サポートがインストールされます。  
  
3.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理ツールの完全インストールには、Setup.exe/q/Action=Install /Features=ADV_SSMS コマンドを実行します。 機能のパラメーター値に関する詳細については、「[コマンド プロンプトからの SQL Server 2016 のインストール](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。  
  
### [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント ツールのアンインストール  
 クライアント ツールは、コントロール パネルの [プログラムの追加と削除] に **[[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]]** と表示されるので、そこで削除できます。 [ノードの削除] を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスをフェールオーバー クラスターからアンインストールする場合、クライアント コンポーネントは一緒にアンインストールされません。  
  
## 参照  
 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  