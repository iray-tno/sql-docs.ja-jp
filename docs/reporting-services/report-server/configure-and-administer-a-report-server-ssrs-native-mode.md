---
title: "レポート サーバーを構成および管理する (SSRS ネイティブ モード) | Microsoft Docs"
ms.custom: ""
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Reporting Services, コンポーネント"
  - "[Reporting Services] の配置, コンポーネント オプション"
  - "レポート サーバー [Reporting Services], コンポーネント オプション"
  - "構成オプション [Reporting Services]"
  - "administering Reporting Services"
  - "コンポーネント [Reporting Services], 構成"
  - "サーバーの構成 [Reporting Services]"
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
caps.latest.revision: 51
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 51
---
# レポート サーバーを構成および管理する (SSRS ネイティブ モード)
  このトピックでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を構成するための方法について説明します。 また、特定のコンポーネント、機能、サーバー機能の構成方法について説明しているトピックへのリストも記載されています。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は次の方法で構成できます。  
  
-   Reporting Services 構成マネージャーを使用します。 このセクションの多くのトピックでは、このツールを使用して特定の機能を構成する方法について説明しています。  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して、サーバーのプロパティのカスタマイズ、個人用レポートの有効化、トレース ログの有効化、および、サイト全体に対する既定値の設定を行います。 サイト設定の詳細については、Management Studio の「[Reporting Services レポート サーバー &#40;ネイティブ モード&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)」を参照してください。 サーバーのプロパティをプログラムから設定するスクリプトを作成して実行できます。 詳細については、「[配置タスクおよび管理タスクのスクリプト作成](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)」および「[レポート サーバーのシステム プロパティ](../Topic/Report%20Server%20System%20Properties.md)」を参照してください。  
  
-   レポート マネージャー使用して、レポート サーバーにアクセスするための権限を与えます。 権限は、各ユーザーまたはグループ アカウントに対して定義したロールの割り当てを通じて付与されます。 詳細については、「[ロールと権限 &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md)」を参照してください。  
  
-   必要に応じて、構成ファイルを修正し、アプリケーションの設定を変更します。 各ファイルの詳細およびそれらの修正のガイドラインについては、「[Reporting Services 構成ファイル](../../reporting-services/report-server/reporting-services-configuration-files.md)」を参照してください。  
  
## このセクションの内容  
 [レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 レポート サーバーおよびレポート マネージャーへのアクセスに使用する URL の定義方法について説明します。  
  
 [レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 サービスのアカウントとパスワードを変更する方法の推奨事項と手順について説明します。  
  
 [レポート サーバー データベースの作成 &#40;SSRS構成マネージャー&#41;](../../reporting-services/install-windows/create-a-report-server-database-ssrs-configuration-manager.md)  
 サーバーのメタデータやオブジェクトの格納に必要なレポート サーバー データベースを作成する方法について説明します。  
  
 [レポート サーバー データベース接続の構成 &#40;SSRS構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 レポート サーバーからレポート サーバー データベースへの接続に使用する接続文字列を変更する方法について説明します。  
  
 [電子メール配信用にレポート サーバーを構成する (SSRS 構成マネージャー)](http://msdn.microsoft.com/ja-jp/b838f970-d11a-4239-b164-8d11f4581d83)  
 電子メールによるレポートの配信をサポートするようにレポート サーバーを構成する方法について説明します。  
  
 [自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 自動実行モードでレポートを処理するようにユーザー アカウントを構成する方法について説明します。  
  
## 参照  
 [レポート ビルダーへのアクセスの構成](../../reporting-services/report-server/configure-report-builder-access.md)   
 [Reporting Services 構成ファイル](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services のセキュリティと保護](../../reporting-services/security/reporting-services-security-and-protection.md)   
 [Reporting Services レポート サーバー &#40;ネイティブ モード&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)  
  
  