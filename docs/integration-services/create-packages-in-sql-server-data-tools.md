---
title: "SQL Server データ ツールでのパッケージの作成 | Microsoft Docs"
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
  - "SSIS パッケージ, 作成"
  - "Integration Services パッケージ, 作成"
  - "パッケージ [Integration Services], 作成"
  - "SQL Server Integration Services パッケージ, 作成"
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
caps.latest.revision: 51
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 51
---
# SQL Server データ ツールでのパッケージの作成
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で新しいパッケージを作成するには、次のいずれかの方法を使用します。  
  
-   [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に含まれるパッケージ テンプレートを使用する。  
  
-   カスタム テンプレートを使用する。  
  
     新しいパッケージを作成するためのテンプレートとしてカスタム パッケージを使用する操作は簡単で、カスタム パッケージを DataTransformationItems フォルダーにコピーするだけです。 既定では、このフォルダーは、C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject にあります。  
  
-   既存のパッケージをコピーする。  
  
     再利用できる機能が既存のパッケージにある場合、既存のパッケージのオブジェクトをコピーして貼り付けることにより、新しいパッケージの制御フローとデータ フローをより短時間で構築できます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトでコピーと貼り付けを使用する方法の詳細については、「[パッケージ オブジェクトの再利用](../integration-services/reuse-of-package-objects.md)」を参照してください。  
  
     新しいパッケージを作成する場合に、既存のパッケージをコピーするか、カスタム パッケージをテンプレートとして使用すると、既存のパッケージの名前と GUID もコピーされます。 新しいパッケージの名前と GUID は、コピー元のパッケージと区別できるように更新する必要があります。 たとえば、複数のパッケージに同じ GUID が使用されると、ログ データが所属するパッケージを特定することが難しくなります。 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のプロパティ ウィンドウを使用することにより、**ID** プロパティの GUID を再生成して、**Name** プロパティの値を更新できます。 詳細については、「[パッケージのプロパティを設定する](../integration-services/set-package-properties.md)」と「[dtutil ユーティリティ](../integration-services/dtutil-utility.md)」を参照してください。  
  
-   テンプレートとして指定したカスタム パッケージを使用する。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを実行します。  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、簡単なインポートまたはエクスポートに使用できる完成したパッケージを作成します。 このウィザードでは、インポートまたはエクスポートをすぐに実行できるように、接続、変換元、および変換先が構成され、必要なすべてのデータ変換が追加されます。 パッケージを後で再び実行したり [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] でパッケージを改良、強化するために、パッケージを保存することもできます。 ただし、パッケージを保存する場合は、パッケージを変更したり、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でパッケージを実行したりする前に、既存の [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] プロジェクトにパッケージを追加しておく必要があります。  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] デザイナーを使用して [!INCLUDE[ssIS](../includes/ssis-md.md)] で作成したパッケージは、ファイル システムに保存されます。 パッケージを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] またはパッケージ ストアに保存するには、パッケージのコピーを保存する必要があります。 詳細については、「[パッケージのコピーを保存する](../Topic/Save%20a%20Copy%20of%20a%20Package.md)」を参照してください。  

 既定のパッケージ テンプレートを使用して基本的なパッケージを作成する方法のデモ ビデオについては、「[基本パッケージの作成 (SQL Server ビデオ)](http://go.microsoft.com/fwlink/?LinkId=131023)」を参照してください。  

## SQL Server Data Tools を取得する
SQL Server Data Tools (SSDT) をインストールするには、「[SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。

## パッケージ テンプレートを使用して SQL Server データ ツールでパッケージを作成する  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージを作成する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、**[SSIS パッケージ]** フォルダーを右クリックし、**[新しい SSIS パッケージ]** をクリックします。  
  
3.  必要に応じて、制御フロー、データ フロー タスク、およびイベント ハンドラーをパッケージに追加します。 詳細については、「[制御フロー](../integration-services/control-flow/control-flow.md)」、「[データ フロー](../integration-services/data-flow/data-flow.md)」、および「[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../integration-services/integration-services-ssis-event-handlers.md)」を参照してください。  
  
4.  **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックし、新しいパッケージを保存します。  
  
    > [!NOTE]  
    >  空のパッケージも保存できます。  
  
## プロジェクトとそのパッケージのターゲット バージョンを選択する  
  
1.  ソリューション エクスプローラーで Integration Services プロジェクトを右クリックし、**[プロパティ]** を選択すると、そのプロジェクトのプロパティ ページが開きます。  
  
2.  **[構成プロパティ]** の **[全般]**タブで、 **[TargetServerVersion]** プロパティを選択した後、[SQL Server 2016]、[SQL Server 2014]、または [SQL Server 2012] を選択します。  
  
     ![TargetServerVersion property in project properties dialog box](../integration-services/media/targetserverversion2.png "TargetServerVersion property in project properties dialog box")  
  
 SQL Server 2016、SQL Server 2014 または SQL Server 2012 を対象とするパッケージを実行、作成、および管理できます。  
  
  