---
title: "Access データベースに接続する | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アクセス [Integration Services]"
  - "データベースへのアクセス [Integration Services]"
ms.assetid: 229fbd46-ef6a-4609-a4cc-d80d52c33cf1
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Access データベースに接続する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを Microsoft Office Access データ ソースに接続するには、OLE DB 接続マネージャーとデータ プロパイダが必要です。 使用するデータ プロパイダは、データ ソースを作成した Access のバージョンによって異なります。  
  
-   Access 2003 以前のバージョンの場合、パッケージには [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider が必要です。  
  
-   Access 2007 の場合、パッケージには、Microsoft Office 12.0 Access データベース エンジン用の OLE DB プロバイダーが必要です。  
  
 OLE DB 接続マネージャーを作成し、対応するデータ プロパイダを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [接続マネージャー] 領域または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードから選択することができます。  
  
> [!NOTE]  
>  64 ビット コンピューターでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Access データ ソースに接続するパッケージを 32 ビット モードで実行する必要があります。 32 ビット バージョンで使用できるのは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider と Microsoft Office 12.0 Access 用の OLE DB プロバイダーだけです。  
  
## Access 2003 以前の形式のデータ ソースへの接続  
  
#### [接続マネージャー] 領域から Access 接続マネージャーを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、パッケージを開きます。  
  
2.  **[接続マネージャー]** 領域内を右クリックし、**[新しい OLE DB 接続]** を選択します。  
  
3.  **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスで、**[新規作成]** をクリックします。  
  
     詳細については、「[OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
4.  **[接続マネージャー]** ダイアログ ボックスの **[プロバイダー]** で **[Microsoft Jet 4.0 OLE DB Provider]** を選択し、接続マネージャーを適切に構成します。  
  
#### SQL Server インポートおよびエクスポート ウィザードから Access 接続を作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを起動します。  
  
2.  **[データ ソースの選択]** ページの **[データ ソース]** で **[Microsoft Access]** を選択して、Access 接続を構成します。  
  
     **[データ ソース]** で **[Microsoft Access]** を選択すると、適切なデータ プロバイダーを使用して必要な OLE DB 接続マネージャーが自動的に作成されます。 詳細については、「[OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
## Access 2007 形式のデータ ソースへの接続  
 Access 2007 データ ソースにアクセスする場合、OLE DB 接続マネージャーでは Microsoft Office 12.0 Access データベース エンジン用の OLE DB プロバイダーが必要です。 このプロバイダーは、2007 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office system と共に自動的にインストールされます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を実行しているコンピューターに 2007 Office system がインストールされていない場合は、プロバイダーを別途インストールする必要があります。 Microsoft Office 12.0 Access データベース エンジン用の OLE DB プロバイダーをインストールするには、「[2007 Office System ドライバー : データ接続コンポーネント](http://go.microsoft.com/fwlink/?LinkId=98155)」でコンポーネントをダウンロードしてインストールしてください。  
  
#### [接続マネージャー] 領域から OLE DB 接続マネージャーを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、パッケージを開きます。  
  
2.  **[接続マネージャー]** 領域内を右クリックし、**[新しい OLE DB 接続]** を選択します。  
  
3.  **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスで、**[新規作成]** をクリックします。  
  
     詳細については、「[OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
4.  **[接続マネージャー]** ダイアログ ボックスの **[プロバイダー]** で **[Microsoft Office 12.0 Access Database Engine OLE DB]** を選択し、接続マネージャーを適切に構成します。  
  
    > [!NOTE]  
    >  Access 2007 を使用するデータ ソースに接続する場合は、**[データ ソース]** で **[Microsoft Jet 4.0 OLE DB Provider]** を選択することはできません。  
  
#### SQL Server インポートおよびエクスポート ウィザードから OLE DB 接続を作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを起動します。  
  
2.  **[データ ソースの選択]** ページの **[データ ソース]** で **[Microsoft Office 12.0 Access Database Engine OLE DB Provider]** を選択し、接続マネージャーを適切に構成します。  
  
    > [!NOTE]  
    >  Access 2007 を使用するデータ ソースに接続する場合は、**[データ ソース]** で **[Microsoft Jet 4.0 OLE DB Provider]** を選択することはできません。  
  
     **[データ ソース]** で **[Microsoft Office 12.0 Access Database Engine OLE DB Provider]** を選択すると、適切なデータ プロバイダーを使用して必要な OLE DB 接続マネージャーが自動的に作成されます。 詳細については、「[OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
## 参照  
 [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  