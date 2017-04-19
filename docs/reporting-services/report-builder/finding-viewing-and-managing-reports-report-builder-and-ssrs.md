---
title: "レポートの検索、表示、管理 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5599300d-6bcd-4704-aba5-fa98e01c78a9
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 11
---
# レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)
  レポート ビルダーでは、レポート サーバーまたは SharePoint サイト上のフォルダーを参照して、レポート、共有データ ソース、モデル、その他の関連レポート アイテムを検索したり、自分のコンピューターを参照して、ローカル レポートを検索したりできます。 レポートを見つけやすくするため、レポート ビルダーでは最近使用されたサーバーとサイトの一覧を管理し、コンピューターのファイル システムの "デスクトップ"、"マイ ドキュメント"、および "マイ コンピューター" フォルダーに直接アクセスできるようにしています。  
  
 レポート デザイナーでも、自分のコンピューターを参照して、ローカル レポートを検索することができます。 レポート サーバーまたは SharePoint サイトにレポートを展開した後は、レポート マネージャーを使用してレポート サーバーを参照するか、SharePoint サイトを検索することによって、レポートを見つけることができます。 レポートとそれに関連するアイテムには、それらが展開された後もローカルからアクセスすることができます。  
  
> [!NOTE]  
>  レポート ビルダーはローカル モードで使用することも、レポート サーバーに接続して使用することもできます。 レポート サーバーとの接続がアクティブではない場合は、いくつかの制限事項が適用されます。  
  
 レポート ビルダーから、レポート サーバーまたは SharePoint サイト上のレポートを見つけるには、レポート サーバーまたは SharePoint サイトの URL を指定する必要があります。 レポート ビルダーを最初にインストールするときに、使用する URL を指定できます。 これが、レポートを保存したり開いたりするときにレポート ビルダーが既定で接続するサーバーまたはサイトになります。  
  
 レポートは、レポートの作成時や更新時にレポート ビルダーやレポート デザイナーでプレビューできます。レポートの表示と管理は、レポート マネージャーを使用してレポート サーバーで行うか、レポートをパブリッシュした後、Reporting Services に統合されている SharePoint サイトで SharePoint の組み込みツールや機能を使用して行うことができます。 詳細については、「[レポート ビルダーでのレポートのプレビュー](../../reporting-services/report-builder/previewing-reports-in-report-builder.md)」および「[レポートのプレビュー](../../reporting-services/reports/previewing-reports.md)」を参照してください。  
  
 レポート ビルダーやレポート デザイナーでレポートをプレビューするか、レポート マネージャーまたは SharePoint サイトでレポートを表示すると、データが更新され、レポートで使用しているデータ ソースから最新のデータがレポートに表示されます。 データを更新せずにレポートを表示する場合は、パブリッシュ済みレポートでレポート履歴とキャッシュされたデータを使用できます。 これらの機能は、レポート ビルダーやレポート デザイナーでレポートをプレビューするときには使用できません。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="FindingAndViewingReportsRB30"></a> レポート ビルダーを使用したレポートの検索と表示  
 作業するレポートを検索したり、レポートで使用する共有データ ソース、画像、サブレポートを選択したりするには、コンピューター、レポート サーバーのフォルダー、または Reporting Services に統合されている SharePoint サイトを参照します。  
  
 レポート サーバーでレポートを検索するには、レポート サーバーの URL を指定する必要があります。また、レポート アイテムの読み取りや保存ができるようにフォルダーに対する適切な権限が必要です。 適切な URL と権限については、レポート サーバーのシステム管理者に問い合わせてください。  
  
 レポート ビルダーでレポートを検索して開いた後、レポートのプレビューや変更を行うことができます。 レポートをプレビューすると、最新のデータが表示されます。 詳細については、「 [Previewing Reports in Report Builder](../../reporting-services/report-builder/previewing-reports-in-report-builder.md)」を参照してください。  
  
 レポート ビルダーは以下の作業に役立ちます。  
  
-   **レポートの検索**レポートの参照時に、レポート ビルダー用にカスタマイズされている使い慣れた Microsoft Office スタイルの **[ファイルを開く]** ダイアログ ボックスを使用できます。 [個人用レポート]、[サイトとサーバー]、[デスクトップ]、[マイ ドキュメント]、[マイ コンピューター] など、レポート サーバーまたはファイル システム上のフォルダーを参照できます。 [サイトとサーバー] は、最近使用したサーバーの一覧を提供します。  
  
-   **共有データ ソースの検索** 共有データ ソースの参照時に、最近使用した一覧から選択するか、レポートと同じレポート サーバー上の別のフォルダーを参照することができます。  
  
-   **レポートの表示** レポートの作成時や更新時にレポート ビルダーでレポートをプレビューします。 レポート ビルダーがレポート サーバーに接続しているときは、レポート サーバーがレポートを読み込んで処理します。接続していないときは、レポートがローカルで処理されます。 レポート ビルダーのレポート ビューアーに処理後のレポートが表示されます。  
  
 
##  <a name="ViewingAndManagingReportServer"></a> レポート サーバーでのレポートの表示と管理  
 レポート マネージャーは、レポート サーバーに保存されているレポートの表示および管理に使用されます。 サーバーのフォルダーを参照してレポートを見つけ、レポートを実行してブラウザーに表示し、管理作業を実行します。  
  
 レポート マネージャーは以下の管理作業に役立ちます。  
  
-   レポート、共有データ ソース、その他のレポート アイテムのプロパティの表示および更新  
  
-   レポートのアップロードとレポートの共有データ ソースの新規作成  
  
-   指定した日時および間隔でレポートを実行するスケジュールの作成  
  
-   レポートのサブスクリプションの作成、変更、削除  
  
-   レポート履歴の作成と、レポート履歴に保管するレポート スナップショット数の指定  
  
-   サーバーでレポートを整理するフォルダーの新規作成  
  
 これらの作業のいくつかはレポート サーバーの管理者が行う場合があります。 レポート サーバーで行う作業の詳細については、「[Reporting Services Report Server (Native Mode)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)」をご覧ください。  
  
 レポート マネージャーには通常、フォルダー、レポート、データ ソース、およびレポート モデルと、[個人用レポート] フォルダーが含まれています。 [個人用レポート] は、所有しているレポートを保存したり操作したりできる作業領域です。 他のレポート サーバー フォルダーはパブリック フォルダーであり、通常、フォルダーのコンテンツの追加や変更を行うには高度な権限が必要になります。 [個人用レポート] 内にフォルダーを作成して、レポートをさらに細かく分類できます。 詳細については、「[個人用レポートの使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/using-my-reports-report-builder-and-ssrs.md)」をご覧ください。  
  
 レポート マネージャーではレポートが Reporting Services HTML ビューアーに表示されます。 HTML ビューアーは、レポートを HTML で表示するためのフレームワークを提供し、レポートのツール バー、パラメーター セクション、資格情報セクション、ドキュメント マップなどが含まれています。 レポート ツール バーには、ページ ナビゲーション、拡大または縮小、更新、検索、エクスポート、印刷、データ フィードの機能があります。 URL を指定してレポートにアクセスした場合、[レポート] ツール バーはブラウザー ウィンドウのレポートの最上部に表示されます。 印刷機能はオプションで、管理者がオンにする必要があります。 この機能が使用可能なときは、プリンターのアイコンがレポート ツール バーに表示されます。 次の図は、[レポート マネージャー] ウィンドウのレポート ツール バーです。レポート ツール バーの機能が強調されています。  
  
 ![レポート マネージャーのレポート ツール バー](../../reporting-services/report-builder/media/hs-reportserver-blowout.png "レポート マネージャーのレポート ツール バー")  
[レポート マネージャー] ウィンドウ  
  
 ![レポート ツール バー](../../reporting-services/media/ssrs-htmlviewer-toolbar.gif "レポート ツール バー")  
レポート ツール バー  
  
 レポートを実行した後は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel や PDF など、レポートを別の形式にエクスポートできます。 また、コンマ区切り値 (CSV) 表示拡張機能などのデータ表示拡張機能を使用してレポートをエクスポートしてから、別のアプリケーションの入力として CSV データ ファイルを使用することもできます。 レポートのエクスポートの詳細については、「[レポートのエクスポート (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)」および「[別の種類のファイルとしてレポートをエクスポートする (レポート ビルダーおよび SSRS)](../Topic/Export%20a%20Report%20as%20Another%20File%20Type%20\(Report%20Builder%20and%20SSRS\).md)」をご覧ください。  
  
 レポートを選択して実行するには、レポート マネージャーを起動して、表示するレポートを検索または参照する方法が最も簡単です。 レポートを開く方法の手順を追った説明については、「[レポートを開閉する (レポート マネージャー)](../../reporting-services/reports/open-and-close-a-report-report-manager.md)」をご覧ください。  
  
 レポートを実行した後、そのレポートを更新すると新しいデータを表示できます。  
  
### レポートの更新  
 レポートのデータは頻繁に変わるので、レポートを更新して最新のデータを表示する必要があります。 レポートは 3 種類の方法で更新できます。  
  
|オプション|結果|  
|------------|------------|  
|ブラウザー ウィンドウの**[更新]** ボタン|セッションのキャッシュに保存されているレポートを表示します。 セッションのキャッシュは、ユーザーがレポートを開いた時点で作成されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、ブラウザー セッションを使用して、レポートが開いている間の表示状態の整合性を保ちます。|  
|![レポート ツール バーのブラウザー更新ボタン](../../reporting-services/media/htmlviewer-refresh.png "レポート ツール バーのブラウザー更新ボタン")|[レポート] ツール バーで **[更新]** ボタンをクリックすると、レポート サーバーは、クエリを再実行し、レポートが要求時に実行される場合はレポート データを更新します。 レポートがキャッシュされる場合、またはスナップショットである場合は、 **[更新]** をクリックすると、レポート サーバー データベースに保存されているレポートが表示されます。|  
|Ctrl&lt;/localizedText&gt; + &lt;localizedText&gt;F5&lt;/localizedText&gt; キー|[レポート] ツール バーで **[更新]** ボタンをクリックした場合と同じ結果になります。|  
  
  
##  <a name="ViewingAndManagingSharePointSite"></a> SharePoint サイトからのレポート サーバー アイテムの表示と管理  
 システム管理者がレポート サーバーを SharePoint 統合モードで実行するように構成している場合、SharePoint サイトからレポートや他のレポート サーバー アイテムを表示および管理できます。  
  
 SharePoint サイトには、データ ソース プロパティ、レポート履歴、レポート処理オプション、スケジュール、サブスクリプション、レポート パラメーターを設定するためのページや、共有スケジュールを作成するためのページがあります。 SharePoint サイトではレポート サーバー アイテムの管理を、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で他のツールを使って作成し管理するときと同じ方法で行うことができます。  
  
 アプリケーション ページにアクセスするには、SharePoint ライブラリに既に追加したレポートまたは他のレポート サーバー アイテムのドロップダウン メニューから、アイテム固有のアクションを選択します。 アイテムと権限に応じて、レポート ビルダーでレポートを作成したり、モデルを生成したり、モデル アイテムのセキュリティを設定することもできます。  
  
 Reporting Services および SharePoint テクノロジの詳細については、msdn.microsoft.com で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?LinkId=154888)の「[レポート サーバーの構成と管理 (Reporting Services SharePoint モード)](../../reporting-services/report-server-sharepoint/configuration and administration of a report server.md)」をご覧ください。  
  
### SharePoint サイトでのレポート サーバー アイテムの場所  
 プロパティを設定するには、まずアイテムを探し出せることが必要です。 レポート サーバー アイテムは、常にライブラリまたはライブラリ内のフォルダーに格納されています。  
  
 SharePoint サイトにアクセスすると、[参照] ページと [ライブラリ ツール] タブが表示されます。 [参照] ページには、ライブラリと、選択したライブラリのコンテンツが表示されます。 レポート、レポート モデル、およびライブラリ内のその他のアイテムの表示、フォルダーの探索、アイテムを格納するサイトの検索が可能です。  
  
 SharePoint サイト上のアイテムの中でレポート サーバー アイテムを見分けるには、見た目の異なるアイコンを使用するか、アイテムの種類の上にマウス ポインターを合わせ、表示されるファイル拡張子を確認します。 次の図は、 **レポート** ライブラリ内のフォルダー、レポート モデル、およびレポート定義を示しています。  
  
 ![レポート サーバー アイテムがある SharePoint ライブラリ](../../reporting-services/report-builder/media/rs-sharepointlibrary.gif "レポート サーバー アイテムがある SharePoint ライブラリ")  
  
### レポートの表示  
 SharePoint ライブラリにアップロードしたレポート定義 (.rdl ファイル) は、Reporting Services アドインによってインストールされたレポート ビューアー Web パーツから表示できます。 .rdl ファイルの関連付けは、アドインのインストール時に自動的に定義されます。 レポートを選択すると、レポートは自動的に Web パーツで開かれます。 レポートが開いたら、Web パーツにあるレポート ツール バーを使用して、ページ間の移動、レポートの検索、拡大または縮小、印刷を行うことができます。 ツール バーには、レポートを Atom データ フィードとしてエクスポートするデータ フィードのエクスポート オプションが含まれています。また、レポートの印刷、サブスクライブ、および PDF、Word、Excel などの異なる形式へのエクスポートを行う **[アクション]** メニューも含まれています。 **[アクション]** メニューからは、レポートをレポート ビルダーで開くこともできます。 次の図は、レポートと、 **[アクション]** メニューのエクスポート オプションを示しています。  
  
 ![rs_SharePointRunReport](../../reporting-services/report-builder/media/rs-sharepointrunreport.gif "rs_SharePointRunReport")  
  
### アクションによるアイテムの管理  
 管理タスクは、各アイテムのドロップダウン メニューからアクションを選択することで実行できます。 権限に応じて、各アイテムには共通アクションが割り当てられます。これらは SharePoint ライブラリに格納されているアイテムに標準のものです。 **[プロパティの表示]** や **[プロパティの編集]** は共通アクションの例です。 カスタム アクションでは、アイテム固有の管理機能が提供されます。 次の図は、レポート定義のアクションを示しています。 レポート定義のカスタム アクションの例としては、 **[サブスクリプションの管理]** や **[処理オプションの管理]**などがあります。  
  
 ![レポート サーバー アイテムのメニュー コマンド](../../reporting-services/report-builder/media/rs-ecbforrsitems.gif "レポート サーバー アイテムのメニュー コマンド")  
  
  
##  <a name="DeskTop"></a> デスクトップ アプリケーションでのレポートの表示  
 レポート ビューアーとしてブラウザーをまったく使用せず、代わりにデスクトップ アプリケーション ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel など) を使用することができます。 このためには、デスクトップ アプリケーションの形式および生成先の共有フォルダーを指定するサブスクリプションを定義します。 レポートは、アプリケーション ファイルとして生成され、ファイル名拡張子が付けられ、ハード ディスク上にファイルとして保存されます。 その後は、ブラウザーの代わりに [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel (または他のアプリケーション) を使用してレポートを表示できるようになります。  
  
  
##  <a name="AboutUserSessions"></a> ユーザー セッションについて  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、ブラウザー セッションを使用して、レポートの表示中の整合性を保ちます。 セッションは、認証されているユーザーではなく、ブラウザー接続に基づき確立されます。 ユーザーが新しいブラウザー ウィンドウでレポートを開くたびに、新しいセッションが作成されます。 ブラウザー セッションを確立すると、レポート サーバー上でレポートが変更されたとしても、ユーザーはセッション開始時に開いていたレポートに対して作業を継続して行います。 たとえば、ユーザーが午後 11 時にレポートを開き、レポートの作成者が同じレポートを午後 11 時 1 分に再びパブリッシュした場合でも、ユーザーのセッションが継続されている間はユーザーが開いたレポートがセッションに保持されます。  
  
 ブラウザーの **[更新]** ボタンを使用して同じセッション内のレポートを更新すると、元のセッションのバージョンのレポートが表示されます。 [レポート] ツール バーの **[更新]** ボタンを使用して要求時レポートを更新すると、レポートは再実行され、新しいデータがあれば、これが表示されます。  
  
 セッション情報は、レポート サーバーの一時データベースに格納されます。 レポート サーバーでは、 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] のセッション管理を使用しません。 サーバーを再起動したり、データベースの復旧操作を実行した場合、セッション状態は復元されません。 セッションの管理の詳細については、「[実行状態の識別](../../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)」をご覧ください。  
  
 
##  <a name="InThisSection"></a> このセクションの内容  
 以下のトピックでは、レポートの表示と管理について詳しく説明します。  
  
  [レポートの検索、表示、管理](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)
  
 [ブラウザーを使用したレポートの検索と表示 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs.md)  
 URL を使用してレポートを検索および表示する方法について説明します。  
  
 [レポートおよび他のアイテムの検索 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/searching-for-reports-and-other-items-report-builder-and-ssrs.md)  
 レポート マネージャーの検索機能を使用してレポート サーバーのアイテムを見つける方法について説明します。  
  
 [個人用レポートの使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/using-my-reports-report-builder-and-ssrs.md)  
 [個人用レポート] フォルダーを作業領域として使用し、所有しているレポートの保存や操作を行う方法について説明します。  
  
 [レポート ビルダーでのレポートのプレビュー](../../reporting-services/report-builder/previewing-reports-in-report-builder.md)  
 作成中または更新中のレポートをプレビューする方法について説明します。  
  
## 参照  
 [レポートの保存 (レポート ビルダー)](../../reporting-services/report-builder/saving-reports-report-builder.md)   
 [SQL Server 2016 のレポート ビルダー](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [レポート ビルダーのインストールとアンインストール](../Topic/Install%20and%20Uninstall%20Report%20Builder.md)  
  
  