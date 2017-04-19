---
title: "Reporting Services のアンインストール | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
caps.latest.revision: 7
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "erikre"
caps.handback.revision: 7
---
# Reporting Services のアンインストール
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアンインストールすると、作成したコンテンツや変更した構成が削除されます。 ただし、アンインストールの完了後に必要なコンテンツがある場合は、アンインストール プロセスを開始する前に、コンテンツのコピーを作成することをお勧めします。  
  
## SharePoint モードのアンインストール  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードをアンインストールすると、次のものが削除されます。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  のサービスおよびサービス プロキシ。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストールに使用するファイル  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションは削除されません。 サービス アプリケーションが必要なくなった場合は、Windows PowerShell または SharePoint サーバーの全体管理を使用して削除してください。  
  
 レポート アイテムと関連するメタデータは削除されません。 この情報は、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションに関連するコンテンツ データベースと構成データベースに格納されます。 これらのデータベースは削除されません。SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の別のインストールにデータベースを手動で移行できます。 情報が必要なくなった場合は、データベースを削除してください。 詳細については、「 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。  
  
 削除されない 3 つの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データベースの名前の例を次に示します。  
  
-   **レポート サーバー データベース:** ReportingService_7f616e2d253040e8ab5653b3c09a065e  
  
-   **レポート サーバーの一時データベース:** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB  
  
-   **レポート サーバーの警告データベース:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting  
  
### SharePoint 製品用のアドインのアンインストール  
 コンピューターからアドインをアンインストールする場合は、ファイルのみをアンインストールするか、ファームから [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能も削除するかを選択できます。 SharePoint 製品の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインのアンインストール方法の詳細については、「[SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。  
  
## ネイティブ モードのアンインストール  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードをアンインストールすると、インストール後に**作成**または **変更**された内容がすべて残ります。 たとえば、データベース ファイル、ログ ファイル、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ファイル、コンテンツ アイテム (レポートやデータソース ファイルなど) がこれに含まれます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  はインスタンス機能であるため、Windows のコントロール パネルの [プログラムと機能] には表示されません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードをアンインストールするには  
  
1.  Windows のコントロール パネルで **[プログラムと機能]** をクリックします。  
  
2.  **[プログラムと機能]** で **[Microsoft SQL Server 2012]** を選択します。  
  
3.  アンインストール ウィザードで、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンス機能 **RS** を含むインスタンスを選択します。  
  
     ![rs_nativemode_uninstall_selectinstance](../../sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")  
  
4.  インスタンスを選択した後で、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能を選択します。  
  
     ![rs_nativemode_uninstall_selectfeatures](../../sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")  
  
5.  ウィザードを完了します。  
  
## 参照  
 [SQL Server の既存のインスタンスのアンインストール &#40;セットアップ&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)   
 [Power Pivot for SharePoint アドインのインストールまたはアンインストール &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)   
 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  