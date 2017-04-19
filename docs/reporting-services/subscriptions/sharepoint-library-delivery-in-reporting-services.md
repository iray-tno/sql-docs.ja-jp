---
title: "Reporting Services での SharePoint ライブラリへの配信 | Microsoft Docs"
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
helpviewer_keywords: 
  - "SharePoint 統合 [Reporting Services], レポートの配信"
  - "レポートの送信 [Reporting Services]"
  - "サブスクリプション [Reporting Services], SharePoint ライブラリへの配信"
ms.assetid: cb4e4f71-f2d5-475a-9284-ea324c93c7de
caps.latest.revision: 15
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 15
---
# Reporting Services での SharePoint ライブラリへの配信
  SharePoint 統合用に構成されているレポート サーバーでは、レポートを SharePoint ライブラリに送信する配信拡張機能を使用できます。  
  
 SharePoint 配信拡張機能を使用するには、SharePoint サイトのアプリケーション ページからサブスクリプションを作成し、配信の種類を **[SharePoint ドキュメント ライブラリ]** に設定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] またはレポート マネージャーで作成したサブスクリプションに対して、SharePoint 配信拡張機能を使用することはできません。  
  
> [!NOTE]  
>  レポート サーバーがネイティブ モードで動作している場合、配信拡張機能では SharePoint サイトへのレポートの配信がサポートされません。 ネイティブ モードのレポート サーバーに対して、プログラムから配信拡張機能を呼び出そうとすると、サーバーは **rsDeliveryExtensionNotFound** エラーを返し、レポート サーバーのログ ファイルに **rsOperationNotSupportedSharePointMode** エラーが記録されます。  
  
## 必要条件  
 作成済みレポートをライブラリに配信するための要件を次に示します。  
  
-   レポート サーバーは SharePoint 統合モードに構成する必要があります。  
  
-   レポート サーバーに SharePoint 配信拡張機能をインストールして構成する必要があります。  
  
-   レポートはレポート定義 (.rdl) ファイルにする必要があります。 サブスクリプションを利用して、モデルやリソースなど、他の種類のレポート サーバー コンテンツを配信することはできません。 データ ソースとしてモデルが使用されているアドホック レポートをサブスクライブすることはできません。  
  
-   レポートでは保存されている資格情報を使用する必要があります。 これは、配信の種類に関係なく、レポートに対してどのようなサブスクリプションを作成する場合でも必須です。  
  
-   配信先は SharePoint ライブラリである必要があります。 対象ライブラリを選択する際には、同じ SharePoint サイト上のライブラリを選択する必要があります。 同じサイト コレクション内の別のサーバーや別のサイト上のライブラリにレポートを配信することはできません。  
  
 プロパティおよびメタデータは、レポートの配信に含まれません。 レポートが最初に配信されるときに、レポートが含まれているフォルダーまたはリストのセキュリティ設定がレポートに継承されます。 その後でセキュリティ設定を変更したり、レポート プロパティを設定したりしても、設定は維持されます。 サブスクリプションでは、指定された場所に格納されているレポートのみが更新されます。  
  
## SharePoint 権限  
 サブスクリプションを作成するには、レポートに対する "アイテムの表示" 権限が必要です。 レポートを配信するには、レポートの配信先のライブラリに対する "アイテムの追加" 権限が必要です。  
  
## サブスクリプションの作成、変更、および削除を行うには  
  
1.  レポートへのアクセス元となる SharePoint サイトに移動します。  
  
2.  レポートを選択し、レポートの横にある下向きの矢印をクリックして、**[サブスクリプションの管理]** をクリックします。  
  
3.  **[作成]**、**[編集]**、または **[削除]** をクリックします。  
  
 [サブスクリプションの管理] リストの状態メッセージに、サブスクリプションの現在の情報が表示されます。この情報には、サブスクリプションの状態や、サブスクリプションの最終実行日時などが含まれます。  
  
## 配信オプションの設定  
 レポートを SharePoint ライブラリに配信するサブスクリプションには、次の配信オプションを設定できます。  
  
 [出力形式のレンダリング]  
 レポートの配信に使用されるアプリケーション形式を指定します。 レポートはこの形式へのレンダリング後に配信されます。 選択した出力形式によって、既定のファイル拡張子が決まります。  
  
 選択できる出力形式は、レポート サーバーにインストールされている一連の表示拡張機能によって決まります。  
  
 内部での使用に限られる出力形式や、SharePoint 統合モードで実行中のレポート サーバーでサポートされない出力形式は指定できません。 指定できない形式は、Null、RGDI、および HTMLOWC などです。  
  
 ファイル名と拡張子  
 対象ライブラリでレポートが表示されるときのファイル名と拡張子を指定します。 ファイル拡張子を指定しなければ、レポートの出力形式に基づいてレポート サーバーで拡張子が作成されます。 この値は必須です。 ファイル名に使用できない文字は、: \ / * ? " \< > | # { } % です。 " \< > | # { } %  
  
 [タイトル]  
 対象ライブラリ内のレポートの **Title** プロパティ (オプション) を指定します。 これは、ライブラリに格納されているすべてのアイテムに対する標準プロパティです。 ユーザーは、SharePoint サイトでライブラリ コンテンツを表示するときに、このプロパティを表示するか非表示にするかを指定できます。  
  
 [パス]  
 SharePoint ライブラリへの完全修飾 URL (SharePoint Web アプリケーションおよびサイトを含む) を指定します。 たとえば、http://mySharePointWeb/MySite/MyDocLib の場合、"http://mySharePointWeb" は Web アプリケーションを表し、"MySite" は SharePoint サイト、"MyDocLib" はレポートが配信される SharePoint ライブラリです。  
  
 ページ、サイト、またはリストを指定することはできません。 対象コンテナーは、同じサイトまたはファームにあるライブラリであることが必要です。  
  
 [上書きのオプション]  
 同じファイル名と拡張子を持つファイルは、サブスクリプションの処理時に新しい方のバージョンに置き換えられます。 既存のファイルを新しいバージョンに置き換える場合、**[上書き]** を選択します。 サブスクリプションでファイルを置き換えない場合には、**[なし]** を選択します。 この場合、対象ファイルと名前と拡張子が同じであるファイルが存在すると、配信が実行されません。 ファイル名の末尾に数値を付加して、同じファイルの連続するバージョンを追加する場合は、**[自動増分]** を選択します。  
  
 [自動コピー]  
 [自動コピー] 機能を使用して、最新バージョンのファイルを複数の場所に自動コピーする場合、**[上書き]** が有効な場合にのみファイルがコピーされます。 **[自動増分]** または **[なし]** を指定した場合、配信が失敗し、**rsDeliveryError** エラーが発生します。  
  
## 参照  
 [Create and Manage Subscriptions for SharePoint Mode Report Servers](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)   
 [サブスクリプションと配信 &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [レポート データ ソースに関する資格情報と接続情報を指定する](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  