---
title: "コマンド プロンプトからの SQL Server 2016 のインストール | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server のインストール, コマンド プロンプト"
  - "インストール スクリプト [SQL Server]"
  - "メンテナンス スクリプト [SQL Server]"
  - "REMOVENODE プロパティ"
  - "コンポーネント [SQL Server], 削除"
  - "コマンド プロンプト [SQL Server], SQL Server のインストール"
  - "ASACCOUNT パラメーター"
  - "フェールオーバー クラスタリング [SQL Server], インストール"
  - "master データベース [SQL Server], 再構築"
  - "SQLCOLLATION パラメーター"
  - "クラスター [SQL Server], インストール"
  - "自動インストール [SQL Server]"
  - "照合順序の変更"
  - "AGTPASSWORD パラメーター"
  - "USESYSDB パラメーター"
  - "RSPASSWORD パラメーター"
  - "AUTOSTART パラメーター"
  - "ASPASSWORD パラメーター"
  - "スタンドアロン インストール [SQL Server]"
  - "SAMPLEDATABASESERVER パラメーター"
  - "コンポーネントの追加"
  - "SAPWD パラメーター"
  - "スクリプト [SQL Server], アンインストール"
  - "リモート インストール [SQL Server]"
  - "コンポーネント [SQL Server], インストール"
  - "TARGETCOMPUTER パラメーター"
  - "REMOVENODE パラメーター"
  - "REINSTALLMODE パラメーター"
  - "スクリプト [SQL Server], メンテナンス"
  - "レジストリの再構築"
  - "SQLPASSWORD パラメーター"
  - "データベースの再構築"
  - "IP プロパティ"
  - "PIDKEY パラメーター"
  - "RSCONFIGURATION パラメーター"
  - "ADDLOCAL パラメーター"
  - "セットアップ [SQL Server], コマンド プロンプト"
  - "REBUILDDATABASE パラメーター"
  - "SECURITYMODE パラメーター"
  - "REMOVE プロパティ"
  - "DISABLENETWORKPROTOCOLS パラメーター"
  - "INSTALLDATADIR パラメーター"
  - "REMOVE パラメーター"
  - "コンポーネントの削除"
  - "SQLACCOUNT パラメーター"
  - "パラメーター [SQL Server], SQL Server のインストール"
  - "UPGRADE パラメーター"
  - "ショートカット [SQL Server]"
  - "コンポーネントの更新"
  - "SQL Server の削除"
  - "SQL Server のクラスター化されたインスタンス"
  - "INSTALLSQLDATADIR パラメーター"
  - "RSACCOUNT パラメーター"
  - "ADMINPASSWORD パラメーター"
  - "GROUP プロパティ"
  - "ERRORREPORTING プロパティ"
  - "アンインストール スクリプト [SQL Server]"
  - "AGTACCOUNT パラメーター"
  - "SAVESYSDB パラメーター"
  - "INSTALLVS パラメーター"
  - "INSTANCENAME パラメーター"
  - "スクリプト [SQL Server], インストール"
  - "データベースの再構築, master"
  - "SQL Server のアンインストール"
  - "ASCOLLATION パラメーター"
  - ".ini ファイル"
  - "ADDNODE パラメーター"
  - "コマンド ラインからのインストール [SQL Server]"
  - "VS パラメーター"
  - "INSTALLASDATADIR パラメーター"
  - "INSTALLSQLDIR パラメーター"
  - "ノード [フェールオーバー クラスタリング], コマンド プロンプト"
  - "INSTALLSQLSHAREDDIR パラメーター"
ms.assetid: df40c888-691c-4962-a420-78a57852364d
caps.latest.revision: 255
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 254
---
# コマンド プロンプトからの SQL Server 2016 のインストール
  SQL Server のセットアップを実行する前に、「[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)」を参照してください。  
  
 SQL Server の新しいインスタンスをコマンド プロンプトでインストールすると、インストールする機能とその機能の構成を指定できます。 また、セットアップのユーザー インターフェイスに、サイレント モード、基本的な対話方式、または完全な対話方式を指定できます。  
  
> **注:** コマンド プロンプトを使用してインストールする場合、SQL Server では、/Q パラメーターを使用した非表示モード、または /QS パラメーターを使用した簡易非表示モードがサポートされます。 /QS スイッチでは、進捗状況のみが表示され、入力はできません。また、該当する場合でもエラー メッセージは表示されません。 /QS パラメーターは、/Action=install を指定した場合にのみサポートされます。  
  
 どのインストール方法を使用するかにかかわらず、個人として、または組織を代表して、ソフトウェア ライセンス条項に同意するかどうかを確認する必要があります。ただし、ソフトウェアの使用に別の契約 (マイクロソフト ボリューム ライセンス契約や、ISV または OEM とのサード パーティ契約など) が適用される場合を除きます。  
  
 ライセンス条項は、セットアップのユーザー インターフェイスで確認し、同意することができます。 /Q または /QS パラメーターを使用した自動インストールでは、/IACCEPTSQLSERVERLICENSETERMS パラメーターを指定する必要があります。 ライセンス条項は、「 [マイクロソフト ソフトウェア ライセンス条項](http://go.microsoft.com/fwlink/?LinkId=148209)」で別途確認できます。  
  
> **注:** ソフトウェアの入手方法 (マイクロソフトのボリューム ライセンスを通じて入手した場合など) によっては、ソフトウェアの使用に追加の条件が課されることがあります。  
  
 コマンド プロンプトによるインストールは、次のシナリオで使用されます。  
  
-   コマンド プロンプトから構文とパラメーターを指定して、ローカル コンピューター上で SQL Server のインスタンスと共有コンポーネントのインストール、アップグレード、または削除を行う場合。  
  
-   フェールオーバー クラスター インスタンスのインストール、アップグレード、または削除を行う場合。  
  
-   ある SQL Server エディションから別の SQL Server エディションにアップグレードする場合。  
  
-   構成ファイルに指定された構文とパラメーターを使用して、ローカル コンピューターに SQL Server のインスタンスをインストールする場合。 この方法を使用すると、インストール構成を複数のコンピューターにコピーしたり、フェールオーバー クラスターのインストールで複数のノードをインストールしたりすることができます。  
  
 コマンド プロンプトから SQL Server をインストールする場合は、インストールのセットアップ パラメーターを、インストール構文の一部としてコマンド プロンプトで指定します。  
  
> **注:** ローカルでのインストールの場合、セットアップを管理者として実行する必要があります。 SQL Server をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。 フェールオーバー クラスターのインストールの場合は、サービスとしてログインする権限、およびすべてのフェールオーバー クラスター ノード上のオペレーティング システムの一部として動作する権限を持つローカル管理者である必要があります。  
  
##  <a name="a-nameproperusea-proper-use-of-setup-parameters"></a><a name="ProperUse"></a> セットアップ パラメーターの適切な使用法  
 正しい構文でインストール コマンドを作成するには、次のガイドラインに従ってください。  
  
-   /PARAMETER  
  
-   /PARAMETER=真/偽  
  
-   /PARAMETER=1/0 (Boolean 型用)  
  
-   /PARAMETER="値" (すべての単一値パラメーター用)。 値にスペースを挿入する場合は、二重引用符が必要です。そうでない場合も、二重引用符の使用をお勧めします。  
  
-   /PARAMETER="値 1" "値 2" "値 3" (すべての複数値パラメーター用)。 値にスペースを挿入する場合は、二重引用符が必要です。そうでない場合も、二重引用符の使用をお勧めします。  
  
 **例外:**  
  
-   /FEATURES は複数値パラメーターです。書式は /FEATURES=AS,RS,IS で、スペースのないコンマ区切りの形式です。  
  
 **使用例:**  
  
-   /INSTANCEDIR=c:\Path はサポートされています。  
  
-   /INSTANCEDIR="c:\Path" はサポートされています。  
  
> [!NOTE]  
>  -   SQL Server をインストールするときに、INSTANCEDIR と SQLUSERDBDIR と同じディレクトリ パスを指定した場合、SQL Server エージェントとフルテキスト検索は、アクセス許可がないために開始されません。  
>   
>      リレーショナル サーバーの値では、1 つまたは 2 つの円記号を追加して終了する形式のパスがサポートされています。  
> -   このパラメーターの値である /PID を二重引用符で囲む必要があります。  
  
## <a name="sql-server-parameters"></a>SQL Server パラメーター  
 次の各セクションでは、インストール、更新、および修復の各シナリオのためのコマンド ライン インストール スクリプトを作成するパラメーターについて説明します。  
  
 SQL Server コンポーネント用として挙げられているパラメーターは、そのコンポーネント専用です。 SQL Server エージェント パラメーターおよび SQL Server ブラウザー パラメーターは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] をインストールする場合に適用されます。  
  
-   [インストール パラメーター](#Install)  
  
-   [SysPrep パラメーター](#SysPrep)  
  
-   [アップグレード パラメーター](#Upgrade)  
  
-   [修復パラメーター](#Repair)  
  
-   [再構築システム データベース パラメーター](#Rebuild)  
  
-   [アンインストール パラメーター](#Uninstall)  
  
-   [フェールオーバー クラスター パラメーター](#ClusterInstall)  
  
-   [サービス アカウント パラメーター](#Accounts)  
  
-   [機能パラメーター](#Feature)  
  
-   [ロール パラメーター](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md#RoleParameters)  
  
-   [/FAILOVERCLUSTERROLLOWNERSHIP パラメーターを使用したフェールオーバーの動作の制御](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md#RollOwnership)  
  
-   [インスタンス ID (InstanceID) の構成](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md#InstanceID) 
  
##  <a name="a-nameinstalla-installation-parameters"></a><a name="Install"></a> インストール パラメーター  
 次の表に示すパラメーターは、インストール用のコマンド ライン スクリプトを作成する場合に使用します。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|インストール ワークフローを示すために必要です。<br /><br /> サポートされる値: **Install**|  
|SQL Server セットアップ コントロール|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。|  
|SQL Server セットアップ コントロール|/IACCEPTROPENLICENSETERMS <br /><br /> **R Services (In-Database) または Microsoft R Server のいずれかを含む自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。| 
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/UpdateEnabled<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、SQL Server セットアップには検出された更新プログラムが含まれます。|  
|SQL Server セットアップ コントロール|/UpdateSource<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを取得する場所を指定します。 有効値は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update を検索する "MU"、有効なフォルダー パス、相対パス (.\MyUpdates など)、または UNC 共有です。 既定では、SQL Server セットアップは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update または Windows Server Update Services を介して Windows Update Service を検索します。|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/ERRORREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/> エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server のエラー報告が指定されます。<br /><br /> 詳細については、「 [Microsoft エラー報告サービスのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkID=72173)」を参照してください。<br /><br /> サポートされる値: <br /><br /> 0 = 無効<br /><br /> 1 = 有効|  
|SQL Server セットアップ コントロール|/FEATURES<br /><br /> - または -<br /><br /> /ROLE<br /><br /> **必須**|インストールするコンポーネントを指定します。<br /><br /> インストールする SQL Server コンポーネントを個別に指定するには、**/FEATURES** を選びます。 詳細については、「 [機能パラメーター](#Feature) 」を参照してください。<br /><br /> セットアップ ロールを指定するには、**/ROLE** を選びます。 セットアップ ロールは、事前に定義された構成で SQL Server をインストールします。|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|インストール パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTALLSHAREDDIR<br /><br /> **省略可**|共有コンポーネント (64 ビット) の既定以外のインストール ディレクトリを指定します。<br /><br /> 既定値は、%Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server です<br /><br /> %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server には設定できません|  
|SQL Server セットアップ コントロール|/INSTALLSHAREDWOWDIR<br /><br /> **省略可**|共有コンポーネント (32 ビット) の既定以外のインストール ディレクトリを指定します。 64 ビット システムのみでサポートされます。<br /><br /> 既定値は、%Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server です<br /><br /> %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server には設定できません|  
|SQL Server セットアップ コントロール|/INSTANCEDIR<br /><br /> **省略可**|インスタンス専用のコンポーネントについて既定以外のインストール ディレクトリを指定します。|  
|SQL Server セットアップ コントロール|/INSTANCEID<br /><br /> **省略可**|[InstanceID](#InstanceID)の既定値以外の値を指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **省略可**|エンジン サービスのアカウントを指定します。 既定値は、**NT Authority\NETWORK SERVICE** です。|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **省略可**|エンジン サービス アカウントのパスワードを指定します。|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **省略可**|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|/PBPORTRANGE<br /><br /> **省略可**|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **省略可**|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 サポートされる値: **True**、 **False**|  
|SQL Server セットアップ コントロール|/PID<br /><br /> **省略可**|SQL Server のエディション用のプロダクト キーを指定します。 このパラメーターが指定されていない場合、Evaluation が使用されます。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/QS<br /><br /> **省略可**|セットアップが UI を使用して実行され、UI を使用して進捗状況が表示されるように指定します。さらに、セットアップで入力ができないように、またはエラー メッセージが表示されないように指定します。|  
|SQL Server セットアップ コントロール|/UIMODE<br /><br /> **省略可**|セットアップ時に表示するダイアログ ボックスの数を最小限に抑えるかどうかを指定します。<br /><br /> **/UIMode** は、**/ACTION=INSTALL** および **UPGRADE** の各パラメーターと共に使用する必要があります。 サポートされる値: <br /><br /> **/UIMODE=Normal** は、Express 以外のエディションの既定値で、選ばれた機能のセットアップ ダイアログ ボックスをすべて表示します。<br /><br /> **/UIMODE=AutoAdvance** は、Express エディションの既定値で、重要でないダイアログ ボックスをスキップします。<br /><br /> <br /><br /> **UIMODE** は、他のパラメーターと組み合わせて使用するとオーバーライドされます。 たとえば、**/UIMODE=AutoAdvance** と **/ADDCURRENTUSERASSQLADMIN=FALSE** の両方を指定した場合、準備ダイアログ ボックスには現在のユーザーの情報が自動入力されません。<br /><br /> **UIMode** 設定を **/Q** または **/QS** の各パラメーターと共に使用することはできません。|  
|SQL Server セットアップ コントロール|/SQMREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server の機能の使用状況レポートが指定されます。<br /><br />サポートされる値: <br /><br /> 0 = 無効<br /><br /> 1 = 有効|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server エージェント|/AGTSVCACCOUNT<br /><br /> **必須**|SQL Server エージェント サービスのアカウントを指定します。|  
|SQL Server エージェント|/AGTSVCPASSWORD<br /><br /> [必須](#Accounts)|SQL Server エージェント サービス アカウントのパスワードを指定します。|  
|SQL Server エージェント|/AGTSVCSTARTUPTYPE<br /><br /> **省略可**|SQL Server エージェント サービスの[スタートアップ](#Accounts) モードを指定します。<br /><br /> サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASBACKUPDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] バックアップ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCOLLATION<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の照合順序の設定を指定します。<br /><br /> 既定値: **Latin1_General_CI_AS**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCONFIGDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 構成ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASDATADIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASLOGDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Log。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Log。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSERVERMODE<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー モードを指定します。 有効な値は、MULTIDIMENSIONAL、POWERPIVOT、または TABULAR です。 **ASSERVERMODE** では、大文字と小文字が区別されます。 値はすべて大文字で指定する必要があります。 有効な値の詳細については、「[Analysis Services のインストール](../../analysis-services/instances/install-windows/install-analysis-services.md)」をご覧ください。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのアカウントを指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのパスワードを指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCSTARTUPTYPE<br /><br /> **省略可**|[サービスの](#Accounts) スタートアップ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] モードを指定します。 サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSYSADMINACCOUNTS<br /><br /> **必須**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の管理者資格情報を指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASTEMPDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 一時ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server \\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Temp。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Temp。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASPROVIDERMSOLAP<br /><br /> **省略可**|MSOLAP プロバイダーをインプロセスで実行できるかどうかを指定します。<br /><br /> 既定値: 1 = 有効|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/FARMACCOUNT<br /><br /> **SPI_AS_NewFarm の場合に必須**|SharePoint の全体管理サービスとその他の重要なサービスをファームで実行するためのドメイン ユーザー アカウントを指定します。<br /><br /> このパラメーターは、/ROLE = SPI_AS_NEWFARM でインストールされた [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスにのみ使用されます。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/FARMPASSWORD<br /><br /> **SPI_AS_NewFarm の場合に必須**|ファーム アカウントのパスワードを指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/PASSPHRASE<br /><br /> **SPI_AS_NewFarm の場合に必須**|アプリケーション サーバーまたは Web フロント エンド サーバーを SharePoint ファームに追加するために使用されるパスフレーズを指定します。<br /><br /> このパラメーターは、/ROLE = SPI_AS_NEWFARM でインストールされた [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスにのみ使用されます。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/FARMADMINIPORT<br /><br /> **SPI_AS_NewFarm の場合に必須**|SharePoint の全体管理 Web アプリケーションに接続するために使用されるポートを指定します。<br /><br /> このパラメーターは、/ROLE = SPI_AS_NEWFARM でインストールされた [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスにのみ使用されます。|  
|SQL Server Browser|/BROWSERSVCSTARTUPTYPE<br /><br /> **省略可**|SQL Server Browser サービスの[スタートアップ](#Accounts) モードを指定します。 サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/ENABLERANU<br /><br /> **省略可**|[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のインストールの実行アカウント資格情報を有効にします。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/INSTALLSQLDATADIR<br /><br /> **省略可**|SQL Server データ ファイルのデータ ディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **/SECURITYMODE=SQL の場合に必須**|SQL Server sa アカウントのパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SECURITYMODE<br /><br /> **省略可**|SQL Server のセキュリティ モードを指定します。<br /><br /> このパラメーターを指定しない場合、Windows 限定の認証モードがサポートされます。<br /><br /> サポートされる値: **SQL**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLBACKUPDIR<br /><br /> **省略可**|バックアップ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Backup|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **省略可**|SQL Server の照合順序の設定を指定します。<br /><br /> 既定値は、Windows オペレーティング システムのロケールに基づいています。 詳細については、「 [セットアップでの照合順序の設定](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx)」を参照してください。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/ADDCURRENTUSERASSQLADMIN<br /><br /> **省略可**|現在のユーザーを SQL Server **sysadmin** 固定サーバー ロールに追加します。 /ADDCURRENTUSERASSQLADMIN パラメーターは、Express エディションをインストールする場合、または /Role=ALLFeatures_WithDefaults が指定されている場合に使用できます。 詳細については、後述の /ROLE をご覧ください。<br /><br /> /ADDCURRENTUSERASSQLADMIN の使用はオプションですが、/ADDCURRENTUSERASSQLADMIN または /SQLSYSADMINACCOUNTS のどちらかを指定する必要があります。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のエディション: **True**<br /><br /> 他のすべてのエディション: **False**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **必須**|SQL Server サービスの開始アカウントを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [必須](#Accounts)|SQLSVCACCOUNT のパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCSTARTUPTYPE<br /><br /> **省略可**|SQL Server サービスの[スタートアップ](#Accounts) アカウントを指定します。 サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **必須**|sysadmin ロールのメンバーになるためにログインを準備するには、このパラメーターを使用します。<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 以外の SQL Server のエディションの場合、/SQLSYSADMINACCOUNTS は必須です。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のエディションの場合、/SQLSYSADMINACCOUNTS の使用はオプションですが、/SQLSYSADMINACCOUNTS または /ADDCURRENTUSERASSQLADMIN のどちらかを指定する必要があります。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **省略可**|tempdb のデータ ファイルのディレクトリを指定します。 複数のディレクトリを指定する場合、各ディレクトリを空白で区切ります。 複数のディレクトリが指定されている場合、tempdb データ ファイルはラウンド ロビン形式ですべてのディレクトリにまたがるようになります。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **省略可**|tempdb のログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **省略可**|セットアップで追加する tempdb データ ファイルの数を指定します。 この値はコアの数まで増やすことができます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 1<br /><br /> 他のすべてのエディション: 8 またはコアの数のうち、小さい方の値<br /><br /> **\*\* 重要 \*\*** tempdb のプライマリ データベース ファイルは引き続き tempdb.mdf になります。 その他の tempdb ファイルには、tempdb_mssql_#.ndf という名前が付けられます。# は、セットアップ中に作成されたその他の各 tempdb データベース ファイルの一意の番号を表します。 この名前付け規則は、各データベース ファイルを一意にすることを目的としています。 SQL Server のインスタンスをアンインストールすると、tempdb_mssql_#.ndf 名前付け規則を使用するファイルが削除されます。 ユーザー データベース ファイルには tempdb_mssql_*.ndf 名前付け規則を使用しないでください。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **省略可**|各 tempdb データ ファイルの初期サイズを MB 単位で指定します。 最大 1024 MB まで指定できます。 既定値 = 8<br /><br /> 許容範囲: 最小値 = 8、最大値 = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 1024 MB まで指定できます。<br /><br /> 既定値：64  許容範囲: 最小値 = 0、最大値 = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **省略可**|tempdb ログ ファイルの初期サイズを MB 単位で指定します。 最大 1024 MB まで指定できます。 <br />既定値: 8<br /><br /> 許容範囲: 最小値 = 8、最大値 = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 1024 MB まで指定できます。<br /><br /> 既定値：64  許容範囲: 最小値 = 0、最大値 = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBDIR<br /><br /> **省略可**|ユーザー データベースのデータ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCINSTANTFILEINIT<br /><br /> **省略可**|SQL Server サービス アカウントのファイルの瞬時初期化を有効にします。 セキュリティとパフォーマンスに関する考慮事項については、「[データベースのファイルの瞬時初期化](../../relational-databases/databases/database-instant-file-initialization.md)」をご覧ください。<br /><br /> 既定値: False<br /><br /> 省略可能な値: True|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBLOGDIR<br /><br /> **省略可**|ユーザー データベースのログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|FILESTREAM|/FILESTREAMLEVEL<br /><br /> **省略可**|FILESTREAM 機能のアクセス レベルを指定します。 サポートされる値: <br /><br /> 0 = [このインスタンスに対する FILESTREAM サポートを無効にする]  (既定値)<br /><br /> 1 = [[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にする]<br /><br /> 2 = [[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスおよびファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]  (クラスター シナリオに対しては無効です) <br /><br /> 3 = [リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]|  
|FILESTREAM|/FILESTREAMSHARENAME<br /><br /> **省略可**<br /><br /> **FILESTREAMLEVEL が 1 より大きい場合は必須。**|FILESTREAM データを格納する Windows 共有の名前を指定します。|  
|SQL Server フルテキスト|/FTSVCACCOUNT<br /><br /> **省略可**|フルテキスト フィルター ランチャー サービスのアカウントを指定します。<br /><br /> このパラメーターは、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] では無視されます。 ServiceSID は、SQL Server と Full-text Filter Daemon 間の通信を確立するのに使用されます。 この値を指定しない場合、フルテキスト フィルター ランチャー サービスが無効になります。 サービス アカウントを変更し、フルテキスト機能を有効にするには、SQL Server コントロール マネージャーを使用する必要があります。<br /><br /> 既定値: ローカル サービス アカウント|  
|SQL Server フルテキスト|/FTSVCPASSWORD<br /><br /> **省略可**|フルテキスト フィルター ランチャー サービスのパスワードを指定します。<br /><br /> このパラメーターは、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] では無視されます。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のアカウントを指定します。<br /><br /> 既定値: NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパスワードを指定します。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **省略可**|[サービスの](#Accounts) スタートアップ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] モードを指定します。|  
|SQL Server のネットワーク構成|/NPENABLED<br /><br /> **省略可**|SQL Server サービスの名前付きパイプ プロトコルの状態を指定します。 サポートされる値: <br /><br /> 0 = [名前付きパイプ プロトコルを無効にする]<br /><br /> 1 = [名前付きパイプ プロトコルを有効にする]|  
|SQL Server のネットワーク構成|/TCPENABLED<br /><br /> **省略可**|SQL Server サービスの TCP プロトコルの状態を指定します。 サポートされる値: <br /><br /> 0 = [TCP プロトコルを無効にする]<br /><br /> 1 = [TCP プロトコルを有効にする]|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **省略可**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール モードを指定します。 サポートされる値: <br /><br /> **SharePointFilesOnlyMode**<br /><br /> **DefaultNativeMode**<br /><br /> **FilesOnlyMode**<br /><br /> <br /><br /> 注: インストールに SQL Server[!INCLUDE[ssDE](../../includes/ssde-md.md)] が含まれている場合、既定の RSINSTALLMODE は DefaultNativeMode になります。<br /><br /> インストールに SQL Server[!INCLUDE[ssDE](../../includes/ssde-md.md)] が含まれていない場合、既定の RSINSTALLMODE は FilesOnlyMode になります。<br /><br /> DefaultNativeMode を選択しても、インストールに SQL Server[!INCLUDE[ssDE](../../includes/ssde-md.md)] が含まれていない場合、RSINSTALLMODE は自動的に FilesOnlyMode に変更されます。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の開始アカウントを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスの開始アカウントのパスワードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCStartupType<br /><br /> **省略可**|[の](#Accounts) スタートアップ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]モードを指定します。|  
|R Services (In-Database)|MRCACHEDIRECTORY|このパラメーターを使用して、[このセクション](https://msdn.microsoft.com/library/mt695942.aspx)で説明されている Microsoft R Open コンポーネントと Microsoft R Server コンポーネント用のキャッシュ ディレクトリを指定します。 通常、この設定を使用するのは、インターネット アクセスを使用していないコンピューターでコマンド ラインから SQL Server R Services をインストールする場合です。|  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、レプリケーション、フルテキスト検索の各コンポーネントが配置された新しいスタンドアロン インスタンスをインストールし、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のファイルの瞬時初期化を有効にするには、次の構文を使用します。  
  
```  
  
Setup.exe /q /ACTION=Install /FEATURES=SQL /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /SQLSVCINSTANTFILEINIT="True" /IACCEPTSQLSERVERLICENSETERMS  
  
```  
  
##  <a name="a-namesysprepa-sysprep-parameters"></a><a name="SysPrep"></a> SysPrep パラメーター  
 SQL Server SysPrep の詳細については、  
  
 「[SysPrep を使用した SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-using-sysprep.md)」をご覧ください。  
  
#### <a name="prepare-image-parameters"></a>イメージの準備パラメーター  
 次の表に示すパラメーターは、SQL Server のインスタンスを準備する (構成は行わない) ためのコマンド ライン スクリプトを作成する場合に使用します。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|インストール ワークフローを示すために必要です。<br /><br /> サポートされる値: **PrepareImage**|  
|SQL Server セットアップ コントロール|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/UpdateEnabled<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、SQL Server セットアップには検出された更新プログラムが含まれます。|  
|SQL Server セットアップ コントロール|/UpdateSource<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを取得する場所を指定します。 有効値は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update を検索する "MU"、有効なフォルダー パス、相対パス (.\MyUpdates など)、または UNC 共有です。 既定では、SQL Server セットアップは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update または Windows Server Update Services を介して Windows Update Service を検索します。|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/FEATURES<br /><br /> **必須**|インストールする [コンポーネント](#Feature) を指定します。<br /><br /> サポートされる値: SQLEngine、Replication、FullText、DQ、AS、AS_SPI、RS、RS_SHP、RS_SHPWFE、DQC、Conn、IS、BC、SDK、DREPLAY_CTLR、DREPLAY_CLT、SNAC_SDK、SQLODBC、SQLODBC_SDK、LocalDB、MDS、POLYBASE|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|インストール パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTALLSHAREDDIR<br /><br /> **省略可**|共有コンポーネント (64 ビット) の既定以外のインストール ディレクトリを指定します。<br /><br /> 既定値は、%Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server です<br /><br /> %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server には設定できません|  
|SQL Server セットアップ コントロール|/INSTANCEDIR<br /><br /> **省略可**|インスタンス専用のコンポーネントについて既定以外のインストール ディレクトリを指定します。|  
|SQL Server セットアップ コントロール|/INSTANCEID<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 2 (2013 年 1 月) より前: **必須**<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 2 以降 **必須** (インスタンス機能用)|準備中のインスタンスのインスタンス ID を指定します。|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **省略可**|エンジン サービスのアカウントを指定します。 既定値は、**NT Authority\NETWORK SERVICE** です。|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **省略可**|エンジン サービス アカウントのパスワードを指定します。|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **省略可**|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|/PBPORTRANGE<br /><br /> **省略可**|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **省略可**|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 サポートされる値: **True**、 **False**|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/QS<br /><br /> **省略可**|セットアップが UI を使用して実行され、UI を使用して進捗状況が表示されるように指定します。さらに、セットアップで入力ができないように、またはエラー メッセージが表示されないように指定します。|  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、レプリケーション、フルテキスト検索の各コンポーネントおよび [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] が配置された新しいスタンドアロン インスタンスを準備するには  
  
```  
Setup.exe /q /ACTION=PrepareImage /FEATURES=SQL,RS /InstanceID =<MYINST> /IACCEPTSQLSERVERLICENSETERMS  
```  
  
#### <a name="complete-image-parameters"></a>イメージの完了パラメーター  
 次の表に示すパラメーターは、準備された SQL Server のインスタンスを完了および構成するためのコマンド ライン スクリプトを作成する場合に使用します。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|インストール ワークフローを示すために必要です。<br /><br /> サポートされる値: **CompleteImage**|  
|SQL Server セットアップ コントロール|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/ERRORREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server のエラー報告が指定されます。<br /><br /> 詳細については、「 [Microsoft エラー報告サービスのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkID=72173)」を参照してください。 サポートされる値: <br /><br /> 1 = 有効<br /><br /> 0 = 無効|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|インストール パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTANCEID<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 2 (2013 年 1 月) より前: **必須**<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 2 以降: **省略可**|イメージの準備手順で指定されたインスタンス ID を使用します。<br /><br /> サポートされる値: 準備されたインスタンスのインスタンス ID。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 2 (2013 年 1 月) より前: **必須**<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 2 以降: **省略可**|完了させるインスタンスの SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **省略可**|エンジン サービスのアカウントを指定します。 既定値は、**NT Authority\NETWORK SERVICE** です。|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **省略可**|エンジン サービス アカウントのパスワードを指定します。|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **省略可**|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|/PBPORTRANGE<br /><br /> **省略可**|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **省略可**|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 サポートされる値: **True**、 **False**|  
|SQL Server セットアップ コントロール|/PID<br /><br /> **省略可**|SQL Server のエディション用のプロダクト キーを指定します。 このパラメーターが指定されていない場合、Evaluation が使用されます。<br /><br /> 注: SQL Server Express、SQL Server Express with Tools、または SQL Server Express with Advanced Services をインストールする場合、PID は事前に定義されます。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/QS<br /><br /> **省略可**|セットアップが UI を使用して実行され、UI を使用して進捗状況が表示されるように指定します。さらに、セットアップで入力ができないように、またはエラー メッセージが表示されないように指定します。|  
|SQL Server セットアップ コントロール|/SQMREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server の機能の使用状況レポートが指定されます。<br /><br />サポートされる値: <br /><br /> 0 = 無効<br /><br /> 1 = 有効|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server エージェント|/AGTSVCACCOUNT<br /><br /> **必須**|SQL Server エージェント サービスのアカウントを指定します。|  
|SQL Server エージェント|/AGTSVCPASSWORD<br /><br /> [必須](#Accounts)|SQL Server エージェント サービス アカウントのパスワードを指定します。|  
|SQL Server エージェント|/AGTSVCSTARTUPTYPE<br /><br /> **省略可**|SQL Server エージェント サービスの[スタートアップ](#Accounts) モードを指定します。 サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|SQL Server Browser|/BROWSERSVCSTARTUPTYPE<br /><br /> **省略可**|SQL Server Browser サービスの[スタートアップ](#Accounts) モードを指定します。 サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/ENABLERANU<br /><br /> **省略可**|SQL Server Express インストールの実行アカウント資格情報を有効にします。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/INSTALLSQLDATADIR<br /><br /> **省略可**|SQL Server データ ファイルのデータ ディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **/SECURITYMODE=SQL の場合に必須**|SQL Server sa アカウントのパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SECURITYMODE<br /><br /> **省略可**|SQL Server のセキュリティ モードを指定します。<br /><br /> このパラメーターを指定しない場合、Windows 限定の認証モードがサポートされます。<br /><br /> サポートされる値: **SQL**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLBACKUPDIR<br /><br /> **省略可**|バックアップ ファイルのディレクトリを指定します。<br /><br /> 既定値:<br /><br /> \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Backup|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **省略可**|SQL Server の照合順序の設定を指定します。<br /><br /> 既定値は、Windows オペレーティング システムのロケールに基づいています。 詳細については、「 [セットアップでの照合順序の設定](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx)」を参照してください。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **必須**|SQL Server サービスの開始アカウントを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [必須](#Accounts)|SQLSVCACCOUNT のパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCSTARTUPTYPE<br /><br /> **省略可**|SQL Server サービスの[スタートアップ](#Accounts) アカウントを指定します。 サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **必須**|sysadmin ロールのメンバーになるためにログインを準備するには、このパラメーターを使用します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **省略可**|tempdb のデータ ファイルのディレクトリを指定します。 複数のディレクトリを指定する場合、各ディレクトリを空白で区切ります。 複数のディレクトリが指定されている場合、tempdb データ ファイルはラウンド ロビン形式ですべてのディレクトリにまたがるようになります。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **省略可**|tempdb のログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **省略可**|各 tempdb データ ファイルの初期サイズを MB 単位で指定します。 最大 256 MB まで指定できます。<br /><br /> 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 4<br /><br /> 他のすべてのエディション: 8<br /><br /> 許容範囲: 最小値 = 既定値 (4 または 8)、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 256 MB まで指定できます。<br /><br /> 既定値：64<br /><br /> 許容範囲: 最小値 = 0、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **省略可**|tempdb ログ ファイルの初期サイズを MB 単位で指定します。 最大 256 MB まで指定できます。<br /><br /> 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 4<br /><br /> 他のすべてのエディション: 8<br /><br /> 許容範囲: 最小値 = 既定値 (4 または 8)、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 256 MB まで指定できます。<br /><br /> 既定値：64<br /><br /> 許容範囲: 最小値 = 0、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **省略可**|セットアップで追加する tempdb データ ファイルの数を指定します。 この値はコアの数まで増やすことができます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 1<br /><br /> 他のすべてのエディション: 8 またはコアの数のうち、小さい方の値<br /><br /> **\*\* 重要 \*\*** tempdb のプライマリ データベース ファイルは引き続き tempdb.mdf になります。 その他の tempdb ファイルには、tempdb_mssql_#.ndf という名前が付けられます。# は、セットアップ中に作成されたその他の各 tempdb データベース ファイルの一意の番号を表します。 この名前付け規則は、各データベース ファイルを一意にすることを目的としています。 SQL Server のインスタンスをアンインストールすると、tempdb_mssql_#.ndf 名前付け規則を使用するファイルが削除されます。 ユーザー データベース ファイルには tempdb_mssql_\*.ndf 名前付け規則を使用しないでください。<br /><br /> **\*\* 警告 \*\*** このパラメーターの構成では [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] はサポートされていません。 セットアップでインストールされる tempdb データ ファイルは 1 つだけです。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBDIR<br /><br /> **省略可**|ユーザー データベースのデータ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBLOGDIR<br /><br /> **省略可**|ユーザー データベースのログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|FILESTREAM|/FILESTREAMLEVEL<br /><br /> **省略可**|FILESTREAM 機能のアクセス レベルを指定します。 サポートされる値: <br /><br /> 0 = [このインスタンスに対する FILESTREAM サポートを無効にする]  (既定値)<br /><br /> 1 = [[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にする]<br /><br /> 2 = [[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスおよびファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]  (クラスター シナリオに対しては無効です) <br /><br /> 3 = [リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]|  
|FILESTREAM|/FILESTREAMSHARENAME<br /><br /> **省略可**<br /><br /> **FILESTREAMLEVEL が 1 より大きい場合は必須。**|FILESTREAM データを格納する Windows 共有の名前を指定します。|  
|SQL Server フルテキスト|/FTSVCACCOUNT<br /><br /> **省略可**|フルテキスト フィルター ランチャー サービスのアカウントを指定します。<br /><br /> このパラメーターは、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] では無視されます。 ServiceSID は、SQL Server と Full-text Filter Daemon 間の通信を確立するのに使用されます。 この値を指定しない場合、フルテキスト フィルター ランチャー サービスが無効になります。 サービス アカウントを変更し、フルテキスト機能を有効にするには、SQL Server コントロール マネージャーを使用する必要があります。<br /><br /> 既定値: ローカル サービス アカウント|  
|SQL Server フルテキスト|/FTSVCPASSWORD<br /><br /> **省略可**|フルテキスト フィルター ランチャー サービスのパスワードを指定します。<br /><br /> このパラメーターは、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] では無視されます。|  
|SQL Server のネットワーク構成|/NPENABLED<br /><br /> **省略可**|SQL Server サービスの名前付きパイプ プロトコルの状態を指定します。 サポートされる値: <br /><br /> 0 = [名前付きパイプ プロトコルを無効にする]<br /><br /> 1 = [名前付きパイプ プロトコルを有効にする]|  
|SQL Server のネットワーク構成|/TCPENABLED<br /><br /> **省略可**|SQL Server サービスの TCP プロトコルの状態を指定します。 サポートされる値: <br /><br /> 0 = [TCP プロトコルを無効にする]<br /><br /> 1 = [TCP プロトコルを有効にする]|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **省略可**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール モードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の開始アカウントを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスの開始アカウントのパスワードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCStartupType<br /><br /> **省略可**|[の](#Accounts) スタートアップ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]モードを指定します。|  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、レプリケーション、フルテキスト検索の各コンポーネントが配置された、準備済みのスタンドアロン インスタンスを完了するには  
  
```  
  
setup.exe /q /ACTION=CompleteImage /INSTANCENAME=MYNEWINST /INSTANCEID=<MYINST> /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /IACCEPTSQLSERVERLICENSETERMS  
  
```  
  
##  <a name="a-nameupgradea-upgrade-parameters"></a><a name="Upgrade"></a> アップグレード パラメーター  
 次の表に示すパラメーターは、アップグレード用のコマンド ライン スクリプトを作成する場合に使用します。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|インストール ワークフローを示すために必要です。 サポートされる値: <br /><br /> **アップグレード**<br /><br /> **EditionUpgrade**<br /><br /> <br /><br /> 値 **EditionUpgrade** は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の既存のエディションを別のエディションにアップグレードするときに使用します。 サポートされるバージョンとエディションのアップグレードについては、「 [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/*UpdateEnabled*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、SQL Server セットアップには検出された更新プログラムが含まれます。|  
|SQL Server セットアップ コントロール|/*UpdateSource*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを取得する場所を指定します。 有効値は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update を検索する "MU"、有効なフォルダー パス、相対パス (.\MyUpdates など)、または UNC 共有です。 既定では、SQL Server セットアップは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update または Windows Server Update Services を介して Windows Update Service を検索します。|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/ERRORREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server のエラー報告が指定されます。<br /><br /> 詳細については、「 [Microsoft エラー報告サービスのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkID=72173)」を参照してください。 サポートされる値: <br /><br /> 1 = 有効<br /><br /> 0 = 無効|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/ INSTANCEDIR<br /><br /> **省略可**|共有コンポーネントの既定以外のインストール ディレクトリを指定します。|  
|SQL Server セットアップ コントロール|/INSTANCEID<br /><br /> **[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降からアップグレードする場合は必須**です。<br /><br /> **次をアップグレードする場合はオプション: [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]**|[InstanceID](#InstanceID)の既定値以外の値を指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/PID<br /><br /> **省略可**|SQL Server のエディション用のプロダクト キーを指定します。 このパラメーターが指定されていない場合、Evaluation が使用されます。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/UIMODE<br /><br /> **省略可**|セットアップ時に表示するダイアログ ボックスの数を最小限に抑えるかどうかを指定します。 <br />                **/UIMode** は、**/ACTION=INSTALL** および **UPGRADE** の各パラメーターと共に使用する必要があります。 サポートされる値: <br /><br /> **/UIMODE=Normal** は、Express 以外のエディションの既定値で、選ばれた機能のセットアップ ダイアログ ボックスをすべて表示します。<br /><br /> **/UIMODE=AutoAdvance** は、Express エディションの既定値で、重要でないダイアログ ボックスをスキップします。<br /><br /> **UIMode** 設定は、**/Q** パラメーターまたは **/QS** パラメーターと共に使用することはできません。|  
|SQL Server セットアップ コントロール|/SQMREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server の機能の使用状況レポートが指定されます。<br /><br />サポートされる値: <br /><br /> 1 = 有効<br /><br /> 0 = 無効|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server Browser サービス|/BROWSERSVCSTARTUPTYPE<br /><br /> **省略可**|SQL Server Browser サービスの[スタートアップ](#Accounts) モードを指定します。 サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|SQL Server フルテキスト|/FTUPGRADEOPTION<br /><br /> **省略可**|フルテキスト カタログのアップグレード オプションを指定します。 サポートされる値: <br /><br /> **REBUILD**<br /><br /> **RESET**<br /><br /> **IMPORT**|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のアカウントを指定します。<br /><br /> 既定値: NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパスワードを指定します。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **省略可**|[サービスの](#Accounts) スタートアップ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] モードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSUPGRADEDATABASEACCOUNT<br /><br /> **省略可**|プロパティは、2008 R2 以前のバージョンの SharePoint モードのレポート サーバーをアップグレードする場合にのみ使用されます。 SQL Server 2012 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]で変更された古い SharePoint モード アーキテクチャを使用するレポート サーバーに対しては、追加のアップグレード操作が実行されます。 このオプションがコマンド ライン インストールに含まれていない場合、古いレポート サーバー インスタンスの既定のサービス アカウントが使用されます。 このプロパティが使用されている場合は、**/RSUPGRADEPASSWORD** プロパティを使用してアカウントのパスワードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSUPGRADEPASSWORD<br /><br /> **省略可**|既存のレポート サーバー サービス アカウントのパスワード。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/ALLOWUPGRADEFORSSRSSHAREPOINTMODE|SharePoint 共有サービス アーキテクチャに基づく SharePoint モードのインストールをアップグレードする場合、このスイッチが必要です。 スイッチは、非共有サービス バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードする場合には必要ありません。|  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 既存のインスタンスまたはフェールオーバー クラスター ノードを SQL Server の以前のバージョンからアップグレードするためのサンプル構文は次のとおりです。  
  
```  
Setup.exe /q /ACTION=upgrade /INSTANCEID = <INSTANCEID>/INSTANCENAME=MSSQLSERVER /RSUPGRADEDATABASEACCOUNT="<Provide a SQL Server logon account that can connect to the report server during upgrade>" /RSUPGRADEPASSWORD="<Provide a password for the report server upgrade account>" /ISSVCAccount="NT Authority\Network Service" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
##  <a name="a-namerepaira-repair-parameters"></a><a name="Repair"></a> 修復パラメーター  
 次の表に示すパラメーターは、修復用のコマンド ライン スクリプトを作成する場合に使用します。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|修復ワークフローを示すために必要です。<br /><br /> サポートされる値: **Repair**|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/FEATURES<br /><br /> **必須**|修復する [コンポーネント](#Feature) を指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **省略可**|エンジン サービスのアカウントを指定します。 既定値は、**NT Authority\NETWORK SERVICE** です。|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **省略可**|エンジン サービス アカウントのパスワードを指定します。|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **省略可**|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|/PBPORTRANGE<br /><br /> **省略可**|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **省略可**|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 サポートされる値: **True**、 **False**|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 インスタンスと共有コンポーネントを修復します。  
  
```  
Setup.exe /q /ACTION=Repair /INSTANCENAME=<instancename>  
```  
  
##  <a name="a-namerebuilda-rebuild-system-database-parameters"></a><a name="Rebuild"></a> 再構築システム データベース パラメーター  
 次の表に示すパラメーターは、master、model、msdb、および tempdb の各システム データベースを再構築するコマンド ライン スクリプトを作成する場合に使用します。 詳細については、「[システム データベースの再構築](../../relational-databases/databases/rebuild-system-databases.md)」を参照してください。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|データベースの再構築に関するワークフローを示すのに必要です。<br /><br /> サポートされる値: **Rebuilddatabase**|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **省略可**|新しいサーバー レベルの照合順序を指定します。<br /><br /> 既定値は、Windows オペレーティング システムのロケールに基づいています。 詳細については、「 [セットアップでの照合順序の設定](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx)」を参照してください。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **インスタンスのインストール中に /SECURITYMODE=SQL が指定された場合に必須。**|SQL SA アカウントのパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **必須**|sysadmin ロールのメンバーになるためにログインを準備するには、このパラメーターを使用します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **省略可**|tempdb のデータ ファイルのディレクトリを指定します。 複数のディレクトリを指定する場合、各ディレクトリを空白で区切ります。 複数のディレクトリが指定されている場合、tempdb データ ファイルはラウンド ロビン形式ですべてのディレクトリにまたがるようになります。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **省略可**|tempdb のログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **省略可**|セットアップで追加する tempdb データ ファイルの数を指定します。 この値はコアの数まで増やすことができます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 1<br /><br /> 他のすべてのエディション: 8 またはコアの数のうち、小さい方の値<br /><br /> **\*\* 重要 \*\*** tempdb のプライマリ データベース ファイルは引き続き tempdb.mdf になります。 その他の tempdb ファイルには、tempdb_mssql_#.ndf という名前が付けられます。# は、セットアップ中に作成されたその他の各 tempdb データベース ファイルの一意の番号を表します。 この名前付け規則は、各データベース ファイルを一意にすることを目的としています。 SQL Server のインスタンスをアンインストールすると、tempdb_mssql_#.ndf 名前付け規則を使用するファイルが削除されます。 ユーザー データベース ファイルには tempdb_mssql_\*.ndf 名前付け規則を使用しないでください。<br /><br /> **\*\* 警告 \*\*** このパラメーターの構成では [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] はサポートされていません。 セットアップでインストールされる tempdb データ ファイルは 1 つだけです。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **省略可**|各 tempdb データ ファイルの初期サイズを MB 単位で指定します。 最大 256 MB まで指定できます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 4<br /><br /> 他のすべてのエディション: 8<br /><br /> 許容範囲: 最小値 = 既定値 (4 または 8)、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 256 MB まで指定できます。<br /><br /> 既定値：64<br /><br /> 許容範囲: 最小値 = 0、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **省略可**|tempdb ログ ファイルの初期サイズを MB 単位で指定します。 最大 256 MB まで指定できます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 4<br /><br /> 他のすべてのエディション: 8<br /><br /> 許容範囲: 最小値 = 既定値 (4 または 8)、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 256 MB まで指定できます。<br /><br /> 既定値：64<br /><br /> 許容範囲: 最小値 = 0、最大値 = 256|  
  
##  <a name="a-nameuninstalla-uninstall-parameters"></a><a name="Uninstall"></a> アンインストール パラメーター  
 次の表に示すパラメーターは、アンインストール用のコマンド ライン スクリプトを作成する場合に使用します。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|アンインストール ワークフローを示すために必要です。<br /><br /> サポートされる値: **Uninstall**|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/FEATURES<br /><br /> **必須**|アンインストールする [コンポーネント](#Feature) を指定します。|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 SQL Server の既存のインスタンスをアンインストールする場合。  
  
```  
Setup.exe /Action=Uninstall /FEATURES=SQL,AS,RS,IS,Tools /INSTANCENAME=MSSQLSERVER  
```  
  
 名前付きインスタンスを削除する場合は、このトピックで前に述べた例の "MSSQLSERVER" の代わりにインスタンス名を指定します。  
  
##  <a name="a-nameclusterinstalla-failover-cluster-parameters"></a><a name="ClusterInstall"></a> フェールオーバー クラスター パラメーター  
 SQL Server フェールオーバー クラスター インスタンスをインストールする前に、次のトピックを確認してください。  
  
-   [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)  
  
-   [[SQL Server インストールにおけるセキュリティの考慮事項](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)]
  
-   [フェールオーバー クラスタリングをインストールする前に](../../sql-server/failover-clusters/install/before-installing-failover-clustering.md)  
  
-   [Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
    > [!IMPORTANT]  
    >  フェールオーバー クラスターのすべてのインストール コマンドには、基になる Windows クラスターが必要です。 SQL Server フェールオーバー クラスターに含まれるすべてのノードは、同じ Windows クラスターに含まれている必要があります。  
  
 次のフェールオーバー クラスターのインストール スクリプトをテストし、必要に応じて変更してください。  
  
#### <a name="integrated-install-failover-cluster-parameters"></a>フェールオーバー クラスターの統合インストール パラメーター  
 次の表に示すパラメーターは、フェールオーバー クラスターのインストール用コマンド ライン スクリプトを作成する場合に使用します。  
  
 統合インストールの詳細については、「[Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」をご覧ください。  
  
> **注:** インストール後にノードを追加するには、[ノードの追加](#AddNode)操作を使用します。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|詳細|  
|-----------------------------------------|---------------|-------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|フェールオーバー クラスター インストール ワークフローを示すために必要です。<br /><br /> サポートされる値: **InstallFailoverCluster**|  
|SQL Server セットアップ コントロール|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERGROUP<br /><br /> **省略可**|SQL Server フェールオーバー クラスターに使用されるリソース グループの名前を指定します。 名前は、既存のクラスター グループの名前か新規のリソース グループの名前のどちらかになります。<br /><br /> 既定値:<br /><br /> SQL Server (\<InstanceName>)|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **省略可**|エンジン サービスのアカウントを指定します。 既定値は、**NT Authority\NETWORK SERVICE** です。|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **省略可**|エンジン サービス アカウントのパスワードを指定します。|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **省略可**|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|/PBPORTRANGE<br /><br /> **省略可**|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **省略可**|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 サポートされる値: **True**、 **False**|  
|SQL Server セットアップ コントロール|/*UpdateEnabled*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、SQL Server セットアップには検出された更新プログラムが含まれます。|  
|SQL Server セットアップ コントロール|/*UpdateSource*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを取得する場所を指定します。 有効値は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update を検索する "MU"、有効なフォルダー パス、相対パス (.\MyUpdates など)、または UNC 共有です。 既定では、SQL Server セットアップは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update または Windows Server Update Services を介して Windows Update Service を検索します。|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/ERRORREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server のエラー報告が指定されます。<br /><br /> 詳細については、「 [Microsoft エラー報告サービスのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkID=72173)」を参照してください。 サポートされる値: <br /><br /> 1 = 有効<br /><br /> 0 = 無効|  
|SQL Server セットアップ コントロール|/FEATURES<br /><br /> **必須**|インストールする [コンポーネント](#Feature) を指定します。|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTALLSHAREDDIR<br /><br /> **省略可**|共有コンポーネント (64 ビット) の既定以外のインストール ディレクトリを指定します。<br /><br /> 既定値は、%Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server です<br /><br /> %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server には設定できません|  
|SQL Server セットアップ コントロール|/INSTALLSHAREDWOWDIR<br /><br /> **省略可**|共有コンポーネント (32 ビット) の既定以外のインストール ディレクトリを指定します。 64 ビット システムのみでサポートされます。<br /><br /> 既定値は、%Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server です<br /><br /> %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server には設定できません|  
|SQL Server セットアップ コントロール|/INSTANCEDIR<br /><br /> **省略可**|インスタンス専用のコンポーネントについて既定以外のインストール ディレクトリを指定します。|  
|SQL Server セットアップ コントロール|/INSTANCEID<br /><br /> **省略可**|[InstanceID](#InstanceID)の既定値以外の値を指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/PID<br /><br /> **省略可**|SQL Server のエディション用のプロダクト キーを指定します。 このパラメーターが指定されていない場合、Evaluation が使用されます。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/QS<br /><br /> **省略可**|セットアップが UI を使用して実行され、UI を使用して進捗状況が表示されるように指定します。さらに、セットアップで入力ができないように、またはエラー メッセージが表示されないように指定します。|  
|SQL Server セットアップ コントロール|/SQMREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server の機能の使用状況レポートが指定されます。<br /><br />サポートされる値: <br /><br /> 1 = 有効<br /><br /> 0 = 無効|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERDISKS<br /><br /> **省略可**|SQL Server フェールオーバー クラスター リソース グループに含まれる共有ディスクの一覧を指定します。<br /><br /> 既定値: 最初のドライブが、すべてのデータベースの既定のドライブとして使用されます。|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERIPADDRESSES<br /><br /> **必須**|エンコードされた IP アドレスを指定します。 エンコードはセミコロン (;) で区切り、\<IP の種類>;\<アドレス>;\<ネットワーク名>;\<サブネット マスク> という形式に従います。 サポートされている IP の種類には、DHCP、IPv4、および IPv6 があります。<br />フェールオーバー クラスターの IP アドレスを複数指定するには、間にスペースを入れます。 次の例を参照してください。<br /><br /> FAILOVERCLUSTERIPADDRESSES=DEFAULT<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;172.16.0.0;ClusterNetwork1;172.31.255.255<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;2001:db8:23:1002:20f:1fff:feff:b3a3;ClusterNetwork1|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERNETWORKNAME<br /><br /> **必須**|新しい SQL Server フェールオーバー クラスターのネットワーク名を指定します。 このネットワーク名は、ネットワーク上で新しい SQL Server フェールオーバー クラスター インスタンスを識別するために使用されます。|  
|SQL Server エージェント|/AGTSVCACCOUNT<br /><br /> **必須**|SQL Server エージェント サービスのアカウントを指定します。|  
|SQL Server エージェント|/AGTSVCPASSWORD<br /><br /> [必須](#Accounts)|SQL Server エージェント サービス アカウントのパスワードを指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASBACKUPDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] バックアップ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCOLLATION<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の照合順序の設定を指定します。<br /><br /> 既定値: **Latin1_General_CI_AS**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCONFIGDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 構成ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASDATADIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASLOGDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Log。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Log。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSYSADMINACCOUNTS<br /><br /> **必須**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の管理者資格情報を指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASTEMPDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 一時ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Temp。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Temp。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASPROVIDERMSOLAP<br /><br /> **省略可**|MSOLAP プロバイダーをインプロセスで実行できるかどうかを指定します。<br /><br /> 既定値: 1 = 有効|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSERVERMODE<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー モードを指定します。 クラスターのシナリオで有効な値は、MULTIDIMENSIONAL または TABULAR です。 **ASSERVERMODE** では、大文字と小文字が区別されます。 値はすべて大文字で指定する必要があります。 有効な値の詳細については、「表形式モードでの Analysis Services のインストール」を参照してください。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/INSTALLSQLDATADIR<br /><br /> **必須**|SQL Server データ ファイルのデータ ディレクトリを指定します。<br /><br /> データ ディレクトリは、共有クラスター ディスク上に指定する必要があります。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **/SECURITYMODE=SQL の場合に必須**|SQL Server sa アカウントのパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SECURITYMODE<br /><br /> **省略可**|SQL Server のセキュリティ モードを指定します。<br /><br /> このパラメーターを指定しない場合、Windows 限定の認証モードがサポートされます。<br /><br /> サポートされる値: **SQL**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLBACKUPDIR<br /><br /> **省略可**|バックアップ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Backup|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **省略可**|SQL Server の照合順序の設定を指定します。<br /><br /> 既定値は、Windows オペレーティング システムのロケールに基づいています。 詳細については、「 [セットアップでの照合順序の設定](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx)」を参照してください。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **必須**|SQL Server サービスの開始アカウントを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [必須](#Accounts)|SQLSVCACCOUNT のパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **必須**|sysadmin ロールのメンバーになるためにログインを準備するには、このパラメーターを使用します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBDIR<br /><br /> **省略可**|ユーザー データベースのデータ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **省略可**|tempdb のデータ ファイルのディレクトリを指定します。 複数のディレクトリを指定する場合、各ディレクトリを空白で区切ります。 複数のディレクトリが指定されている場合、tempdb データ ファイルはラウンド ロビン形式ですべてのディレクトリにまたがるようになります。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **省略可**|tempdb のログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **省略可**|セットアップで追加する tempdb データ ファイルの数を指定します。 この値はコアの数まで増やすことができます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 1<br /><br /> 他のすべてのエディション: 8 またはコアの数のうち、小さい方の値<br /><br /> **\*\* 重要 \*\*** tempdb のプライマリ データベース ファイルは引き続き tempdb.mdf になります。 その他の tempdb ファイルには、tempdb_mssql_#.ndf という名前が付けられます。# は、セットアップ中に作成されたその他の各 tempdb データベース ファイルの一意の番号を表します。 この名前付け規則は、各データベース ファイルを一意にすることを目的としています。 SQL Server のインスタンスをアンインストールすると、tempdb_mssql_#.ndf 名前付け規則を使用するファイルが削除されます。 ユーザー データベース ファイルには tempdb_mssql_\*.ndf 名前付け規則を使用しないでください。<br /><br /> **\*\* 警告 \*\*** このパラメーターの構成では [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] はサポートされていません。 セットアップでインストールされる tempdb データ ファイルは 1 つだけです。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **省略可**|各 tempdb データ ファイルの初期サイズを MB 単位で指定します。 最大 256 MB まで指定できます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 4<br /><br /> 他のすべてのエディション: 8<br /><br /> 許容範囲: 最小値 = 既定値 (4 または 8)、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 256 MB まで指定できます。<br /><br /> 既定値：64<br /><br /> 許容範囲: 最小値 = 0、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **省略可**|tempdb ログ ファイルの初期サイズを MB 単位で指定します。 最大 256 MB まで指定できます。 <br /> 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 4<br /><br /> 他のすべてのエディション: 8<br /><br /> 許容範囲: 最小値 = 既定値 (4 または 8)、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 256 MB まで指定できます。<br /><br /> 既定値：64<br /><br /> 許容範囲: 最小値 = 0、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBLOGDIR<br /><br /> **省略可**|ユーザー データベースのログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|FILESTREAM|/FILESTREAMLEVEL<br /><br /> **省略可**|FILESTREAM 機能のアクセス レベルを指定します。 サポートされる値: <br /><br /> 0 = [このインスタンスに対する FILESTREAM サポートを無効にする]  (既定値)<br /><br /> 1 = [[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にする]<br /><br /> 2 = [[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスおよびファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]  (クラスター シナリオに対しては無効です) <br /><br /> 3 = [リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]|  
|FILESTREAM|/FILESTREAMSHARENAME<br /><br /> **省略可**<br /><br /> **FILESTREAMLEVEL が 1 より大きい場合は必須。**|FILESTREAM データを格納する Windows 共有の名前を指定します。|  
|SQL Server フルテキスト|/FTSVCACCOUNT<br /><br /> **省略可**|フルテキスト フィルター ランチャー サービスのアカウントを指定します。<br /><br /> このパラメーターは、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] では無視されます。 ServiceSID は、SQL Server と Full-text Filter Daemon 間の通信を確立するのに使用されます。<br /><br /> この値を指定しない場合、フルテキスト フィルター ランチャー サービスが無効になります。 サービス アカウントを変更し、フルテキスト機能を有効にするには、SQL Server コントロール マネージャーを使用する必要があります。<br /><br /> 既定値: ローカル サービス アカウント|  
|SQL Server フルテキスト|/FTSVCPASSWORD<br /><br /> **省略可**|フルテキスト フィルター ランチャー サービスのパスワードを指定します。<br /><br /> このパラメーターは、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] では無視されます。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のアカウントを指定します。<br /><br /> 既定値: NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパスワードを指定します。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **省略可**|[サービスの](#Accounts) スタートアップ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] モードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **省略可**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール モードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の開始アカウントを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスの開始アカウントのパスワードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCStartupType<br /><br /> **省略可**|[の](#Accounts) スタートアップ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]モードを指定します。|  
  
 ドメイン グループの代わりに、サービス SID を使用することをお勧めします。  
  
##### <a name="additional-notes"></a>追加情報:   
 クラスター対応のコンポーネントは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] だけです。 他の機能はクラスターに対応していないので、フェールオーバーに対する可用性があまり高くありません。  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が配置された単一ノードの SQL Server フェールオーバー クラスター インスタンスを既定のインスタンスとしてインストールするには、次のコマンドを使用します。  
  
```  
setup.exe /q /ACTION=InstallFailoverCluster /InstanceName=MSSQLSERVER /INDICATEPROGRESS /ASSYSADMINACCOUNTS="<DomainName\UserName>" /ASDATADIR=<Drive>:\OLAP\Data /ASLOGDIR=<Drive>:\OLAP\Log /ASBACKUPDIR=<Drive>:\OLAP\Backup /ASCONFIGDIR=<Drive>:\OLAP\Config /ASTEMPDIR=<Drive>:\OLAP\Temp /FAILOVERCLUSTERDISKS="<Cluster Disk Resource Name - for example, 'Disk S:'" /FAILOVERCLUSTERNETWORKNAME="<Insert Network Name>" /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;Cluster Network;xxx.xxx.xxx.x" /FAILOVERCLUSTERGROUP="MSSQLSERVER" /Features=AS,SQL /ASSVCACCOUNT="<DomainName\UserName>" /ASSVCPASSWORD="xxxxxxxxxxx" /AGTSVCACCOUNT="<DomainName\UserName>" /AGTSVCPASSWORD="xxxxxxxxxxx" /INSTALLSQLDATADIR="<Drive>:\<Path>\MSSQLSERVER" /SQLCOLLATION="SQL_Latin1_General_CP1_CS_AS" /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="xxxxxxxxxxx" /SQLSYSADMINACCOUNTS="<DomainName\UserName> /IACCEPTSQLSERVERLICENSETERMS  
```  
  
#### <a name="prepare-failover-cluster-parameters"></a>フェールオーバー クラスターの準備パラメーター  
 次の表に示すパラメーターは、フェールオーバー クラスターを準備するコマンド ライン スクリプトを作成する場合に使用します。 ここでは、フェールオーバー クラスターのすべてのノードにフェールオーバー クラスター インスタンスを準備するのに必要な、クラスターの高度なインストールの最初の手順がわかります。 詳細については、「[Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|フェールオーバー クラスターの準備に関するワークフローを示すために必要です。<br /><br /> サポートされる値: **PrepareFailoverCluster**|  
|SQL Server セットアップ コントロール|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/*UpdateEnabled*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、SQL Server セットアップには検出された更新プログラムが含まれます。|  
|SQL Server セットアップ コントロール|/*UpdateSource*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを取得する場所を指定します。 有効値は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update を検索する "MU"、有効なフォルダー パス、相対パス (.\MyUpdates など)、または UNC 共有です。 既定では、SQL Server セットアップは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update または Windows Server Update Services を介して Windows Update Service を検索します。|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/ERRORREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server のエラー報告が指定されます。<br /><br /> 詳細については、「 [Microsoft エラー報告サービスのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkID=72173)」を参照してください。 サポートされる値: <br /><br /> 0 = 無効<br /><br /> 1 = 有効|  
|SQL Server セットアップ コントロール|/FEATURES<br /><br /> **必須**|インストールする [コンポーネント](#Feature) を指定します。|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTALLSHAREDDIR<br /><br /> **省略可**|共有コンポーネント (64 ビット) の既定以外のインストール ディレクトリを指定します。<br /><br /> 既定値は、%Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server です<br /><br /> %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server には設定できません|  
|SQL Server セットアップ コントロール|/INSTALLSHAREDWOWDIR<br /><br /> **省略可**|共有コンポーネント (32 ビット) の既定以外のインストール ディレクトリを指定します。 64 ビット システムのみでサポートされます。<br /><br /> 既定値は、%Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server です<br /><br /> %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server には設定できません|  
|SQL Server セットアップ コントロール|/INSTANCEDIR<br /><br /> **省略可**|インスタンス専用のコンポーネントについて既定以外のインストール ディレクトリを指定します。|  
|SQL Server セットアップ コントロール|/INSTANCEID<br /><br /> **省略可**|[InstanceID](#InstanceID)の既定値以外の値を指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **省略可**|エンジン サービスのアカウントを指定します。 既定値は、**NT Authority\NETWORK SERVICE** です。|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **省略可**|エンジン サービス アカウントのパスワードを指定します。|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **省略可**|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|/PBPORTRANGE<br /><br /> **省略可**|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **省略可**|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 サポートされる値: **True**、 **False**|  
|SQL Server セットアップ コントロール|/PID<br /><br /> **省略可**|SQL Server のエディション用のプロダクト キーを指定します。 このパラメーターが指定されていない場合、<br /><br /> Evaluation が使用されます。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/QS<br /><br /> **省略可**|セットアップが UI を使用して実行され、UI を使用して進捗状況が表示されるように指定します。さらに、セットアップで入力ができないように、またはエラー メッセージが表示されないように指定します。|  
|SQL Server セットアップ コントロール|/SQMREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server の機能の使用状況レポートが指定されます。<br /><br />サポートされる値: <br /><br /> 0 = 無効<br /><br /> 1 = 有効|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server エージェント|/AGTSVCACCOUNT<br /><br /> **必須**|SQL Server エージェント サービスのアカウントを指定します。|  
|SQL Server エージェント|/AGTSVCPASSWORD<br /><br /> [必須](#Accounts)|SQL Server エージェント サービス アカウントのパスワードを指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのアカウントを指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **必須**|SQL Server サービスの開始アカウントを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [必須](#Accounts)|SQLSVCACCOUNT のパスワードを指定します。|  
|FILESTREAM|/FILESTREAMLEVEL<br /><br /> **省略可**|FILESTREAM 機能のアクセス レベルを指定します。 サポートされる値: <br /><br /> 0 = [このインスタンスに対する FILESTREAM サポートを無効にする]  (既定値)<br /><br /> 1 = [[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にする]<br /><br /> 2 = [[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスおよびファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]  (クラスター シナリオに対しては無効です) <br /><br /> 3 = [リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]|  
|FILESTREAM|/FILESTREAMSHARENAME<br /><br /> **省略可**<br /><br /> FILESTREAMLEVEL が 1 より大きい場合は**必須** 。|FILESTREAM データを格納する Windows 共有の名前を指定します。|  
|SQL Server フルテキスト|/FTSVCACCOUNT<br /><br /> **省略可**|フルテキスト フィルター ランチャー サービスのアカウントを指定します。<br /><br /> このパラメーターは、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] では無視されます。 ServiceSID は、SQL Server と Full-text Filter Daemon 間の通信を確立するのに使用されます。<br /><br /> この値を指定しない場合、フルテキスト フィルター ランチャー サービスが無効になります。 サービス アカウントを変更し、フルテキスト機能を有効にするには、SQL Server コントロール マネージャーを使用する必要があります。<br /><br /> 既定値: ローカル サービス アカウント|  
|SQL Server フルテキスト|/FTSVCPASSWORD<br /><br /> **省略可**|フルテキスト フィルター ランチャー サービスのパスワードを指定します。<br /><br /> このパラメーターは、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] では無視されます。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のアカウントを指定します。<br /><br /> 既定値: NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパスワードを指定します。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **省略可**|[サービスの](#Accounts) スタートアップ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] モードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **ファイル専用モードのみで使用可**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール モードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の開始アカウントを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスの開始アカウントのパスワードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCStartupType<br /><br /> **省略可**|[の](#Accounts) スタートアップ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]モードを指定します。|  
  
 ドメイン グループの代わりに、サービス SID を使用することをお勧めします。  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]用のフェールオーバー クラスターの高度なインストール シナリオで "準備" 手順を実行するには  
  
 既定のインスタンスを準備するには、コマンド プロンプトで次のコマンドを実行します。  
  
```  
setup.exe /q /ACTION=PrepareFailoverCluster /InstanceName=MSSQLSERVER /Features=AS,SQL /INDICATEPROGRESS /ASSVCACCOUNT="<DomainName\UserName>" /ASSVCPASSWORD="xxxxxxxxxxx" /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="xxxxxxxxxxx" /AGTSVCACCOUNT="<DomainName\UserName>" /AGTSVCPASSWORD="xxxxxxxxxxx" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
 名前付きインスタンスを準備するには、コマンド プロンプトで次のコマンドを実行します。  
  
```  
setup.exe /q /ACTION=PrepareFailoverCluster /InstanceName="<Insert Instance name>" /Features=AS,SQL /INDICATEPROGRESS /ASSVCACCOUNT="<DomainName\UserName>" /ASSVCPASSWORD="xxxxxxxxxxx" /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="xxxxxxxxxxx" /AGTSVCACCOUNT="<DomainName\UserName>" /AGTSVCPASSWORD="xxxxxxxxxxx" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
#### <a name="complete-failover-cluster-parameters"></a>フェールオーバー クラスターの完了パラメーター  
 次の表に示すパラメーターは、フェールオーバー クラスターを完了するコマンド ライン スクリプトを作成する場合に使用します。 ここでは、フェールオーバー クラスターの高度なインストール オプションについて、2 番目の手順がわかります。 すべてのフェールオーバー クラスター ノードで準備を実行した後、共有ディスクを所有するノードでこのコマンドを実行します。 詳細については、「[Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|フェールオーバー クラスターの完了に関するワークフローを示すために必要です。<br /><br /> サポートされる値: **CompleteFailoverCluster**|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERGROUP<br /><br /> **省略可**|SQL Server フェールオーバー クラスターに使用されるリソース グループの名前を指定します。 名前は、既存のクラスター グループの名前か新規のリソース グループの名前のどちらかになります。<br /><br /> 既定値:<br /><br /> SQL Server (\<InstanceName>)|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/ERRORREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server のエラー報告が指定されます。<br /><br /> 詳細については、「 [Microsoft エラー報告サービスのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkID=72173)」を参照してください。 サポートされる値: <br /><br /> 1 = 有効<br /><br /> 0 = 無効|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/PID<br /><br /> **省略可**|SQL Server のエディション用のプロダクト キーを指定します。 このパラメーターが指定されていない場合、Evaluation が使用されます。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/QS<br /><br /> **省略可**|セットアップが UI を使用して実行され、UI を使用して進捗状況が表示されるように指定します。さらに、セットアップで入力ができないように、またはエラー メッセージが表示されないように指定します。|  
|SQL Server セットアップ コントロール|/SQMREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server の機能の使用状況レポートが指定されます。<br /><br />サポートされる値: <br /><br /> 1 = 有効<br /><br /> 0 = 無効|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERDISKS<br /><br /> **省略可**|SQL Server フェールオーバー クラスター リソース グループに含まれる共有ディスクの一覧を指定します。<br /><br /> 既定値:<br /><br /> 最初のドライブは、すべてのデータベースに対して既定のドライブとして使用されます。|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERIPADDRESSES<br /><br /> **必須**|エンコードされた IP アドレスを指定します。 エンコードはセミコロン (;) で区切り、\<IP の種類>;\<アドレス>;\<ネットワーク名>;\<サブネット マスク> という形式に従います。 サポートされている IP の種類には、DHCP、IPv4、および IPv6 があります。<br />フェールオーバー クラスターの IP アドレスを複数指定するには、間にスペースを入れます。 次の例を参照してください。<br /><br /> FAILOVERCLUSTERIPADDRESSES=DEFAULT<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;172.16.0.0;ClusterNetwork1;172.31.255.255<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;2001:db8:23:1002:20f:1fff:feff:b3a3;ClusterNetwork1|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERNETWORKNAME<br /><br /> **必須**|新しい SQL Server フェールオーバー クラスターのネットワーク名を指定します。 このネットワーク名は、ネットワーク上で新しい SQL Server フェールオーバー クラスター インスタンスを識別するために使用されます。|  
|SQL Server セットアップ コントロール|/CONFIRMIPDEPENDENCYCHANGE|マルチサブネット フェールオーバー クラスターについて、IP アドレス リソースの依存関係を OR に設定することを示します。 詳細については、「[新しい SQL Server フェールオーバー クラスターの作成 &#40;セットアップ&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)」をご覧ください。 サポートされる値: <br /><br /> 0 = False (既定値)<br /><br /> 1 = True|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASBACKUPDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] バックアップ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCOLLATION<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の照合順序の設定を指定します。<br /><br /> 既定値: **Latin1_General_CI_AS**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCONFIGDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 構成ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASDATADIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASLOGDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログ ファイルのディレクトリを指定します。 既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\ \<INSTANCEDIR>\\<ASInstanceID\>\OLAP\Log。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\ \<INSTANCEDIR>\\<ASInstanceID\>\OLAP\Log。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSERVERMODE<br /><br /> **省略可**|Analysis Services インスタンスのサーバー モードを指定します。 クラスターのシナリオで有効な値は、MULTIDIMENSIONAL または TABULAR です。 **ASSERVERMODE** では、大文字と小文字が区別されます。 値はすべて大文字で指定する必要があります。 有効な値の詳細については、「表形式モードでの Analysis Services のインストール」を参照してください。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSYSADMINACCOUNTS<br /><br /> **必須**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の管理者資格情報を指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASTEMPDIR<br /><br /> **省略可**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 一時ファイルのディレクトリを指定します。既定値:<br /><br /> WOW モード (64 ビット) 用: %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\ \<INSTANCEDIR>\\<ASInstanceID\>\OLAP\Temp。<br /><br /> 他のすべてのインストール用: %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\ \<INSTANCEDIR>\\<ASInstanceID\>\OLAP\Temp。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASPROVIDERMSOLAP<br /><br /> **省略可**|MSOLAP プロバイダーをインプロセスで実行できるかどうかを指定します。<br /><br /> 既定値: 1 = 有効|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/INSTALLSQLDATADIR<br /><br /> **必須**|SQL Server データ ファイルのデータ ディレクトリを指定します。<br /><br /> データ ディレクトリは、共有クラスター ディスク上に指定する必要があります。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **/SECURITYMODE=SQL の場合に必須**|SQL Server sa アカウントのパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SECURITYMODE<br /><br /> **省略可**|SQL Server のセキュリティ モードを指定します。<br /><br /> このパラメーターを指定しない場合、Windows 限定の認証モードがサポートされます。<br /><br /> サポートされる値: **SQL**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLBACKUPDIR<br /><br /> **省略可**|バックアップ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Backup|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **省略可**|SQL Server の照合順序の設定を指定します。<br /><br /> 既定値は、Windows オペレーティング システムのロケールに基づいています。 詳細については、「 [セットアップでの照合順序の設定](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx)」を参照してください。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **必須**|sysadmin ロールのメンバーになるためにログインを準備するには、このパラメーターを使用します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBDIR<br /><br /> **省略可**|ユーザー データベースのデータ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBLOGDIR<br /><br /> **省略可**|ユーザー データベースのログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **ファイル専用モードのみで使用可**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール モードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **省略可**|tempdb のデータ ファイルのディレクトリを指定します。 複数のディレクトリを指定する場合、各ディレクトリを空白で区切ります。 複数のディレクトリが指定されている場合、tempdb データ ファイルはラウンド ロビン形式ですべてのディレクトリにまたがるようになります。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **省略可**|tempdb のログ ファイルのディレクトリを指定します。<br /><br /> 既定値: \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> 注: このパラメーターは、RebuildDatabase シナリオにも追加されます。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **省略可**|セットアップで追加する tempdb データ ファイルの数を指定します。 この値はコアの数まで増やすことができます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 1<br /><br /> 他のすべてのエディション: 8 またはコアの数のうち、小さい方の値<br /><br /> **\*\* 重要 \*\*** tempdb のプライマリ データベース ファイルは引き続き tempdb.mdf になります。 その他の tempdb ファイルには、tempdb_mssql_#.ndf という名前が付けられます。# は、セットアップ中に作成されたその他の各 tempdb データベース ファイルの一意の番号を表します。 この名前付け規則は、各データベース ファイルを一意にすることを目的としています。 SQL Server のインスタンスをアンインストールすると、tempdb_mssql_#.ndf 名前付け規則を使用するファイルが削除されます。 ユーザー データベース ファイルには tempdb_mssql_\*.ndf 名前付け規則を使用しないでください。<br /><br /> **\*\* 警告 \*\*** このパラメーターの構成では [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] はサポートされていません。 セットアップでインストールされる tempdb データ ファイルは 1 つだけです。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **省略可**|各 tempdb データ ファイルの初期サイズを MB 単位で指定します。 最大 256 MB まで指定できます。 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 4<br /><br /> 他のすべてのエディション: 8<br /><br /> 許容範囲: 最小値 = 既定値 (4 または 8)、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 256 MB まで指定できます。<br /><br /> 既定値：64<br /><br /> 許容範囲: 最小値 = 0、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **省略可**|tempdb ログ ファイルの初期サイズを MB 単位で指定します。 最大 256 MB まで指定できます。 <br /> 既定値:<br /><br /> [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]: 4<br /><br /> 他のすべてのエディション: 8<br /><br /> 許容範囲: 最小値 = 既定値 (4 または 8)、最大値 = 256|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **省略可**|各 tempdb データ ファイルのファイル拡張増分値を MB 単位で指定します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 最大 256 MB まで指定できます。<br /><br /> 既定値：64<br /><br /> 許容範囲: 最小値 = 0、最大値 = 256|  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]用のフェールオーバー クラスターの高度なインストール シナリオで "完了" 手順を実行するには、 フェールオーバー クラスター内のアクティブなノードにするコンピューター上で次のコマンドを実行して、ノードを使用できるようにします。 また、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] フェールオーバー クラスター内の共有ディスクを所有するノードで "CompleteFailoverCluster" アクションを実行する必要があります。  
  
 既定のインスタンスについてフェールオーバー クラスターのインストールを完了するには、コマンド プロンプトで次のコマンドを実行します。  
  
```  
setup.exe /q /ACTION=CompleteFailoverCluster /InstanceName=MSSQLSERVER /INDICATEPROGRESS /ASSYSADMINACCOUNTS="<DomainName\Username>" /ASDATADIR=<Drive>:\OLAP\Data /ASLOGDIR=<Drive>:\OLAP\Log /ASBACKUPDIR=<Drive>:\OLAP\Backup /ASCONFIGDIR=<Drive>:\OLAP\Config /ASTEMPDIR=<Drive>:\OLAP\Temp /FAILOVERCLUSTERDISKS="<Cluster Disk Resource Name - for example, 'Disk S:'>:" /FAILOVERCLUSTERNETWORKNAME="<Insert FOI Network Name>" /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;Cluster Network;xxx.xxx.xxx.x" /FAILOVERCLUSTERGROUP="MSSQLSERVER" /INSTALLSQLDATADIR="<Drive>:\<Path>\MSSQLSERVER" /SQLCOLLATION="SQL_Latin1_General_CP1_CS_AS" /SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
```  
  
 名前付きインスタンスに対してフェールオーバー クラスターのインストールを完了するには、コマンド プロンプトで次のコマンドを実行します。  
  
```  
setup.exe /q /ACTION=CompleteFailoverCluster /InstanceName="<Insert Instance Name>" /INDICATEPROGRESS /ASSYSADMINACCOUNTS="<DomainName\UserName>" /ASDATADIR=<Drive>:\KATMAI\Data /ASLOGDIR=<drive>:\KATMAI\Log /ASBACKUPDIR=<Drive>:\KATMAI\Backup /ASCONFIGDIR=<Drive>:\KATMAI\Config /ASTEMPDIR=<Drive>:\KATMAI\Temp /FAILOVERCLUSTERDISKS="<Cluster Disk Resource Name - for example, 'Disk S:'>" /FAILOVERCLUSTERNETWORKNAME="CompNamedFOI" /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;ClusterNetwork1;xxx.xxx.xxx.x" /FAILOVERCLUSTERGROUP="<Insert New Group Name>" /INSTALLSQLDATADIR="<Drive>:\<Path>\MSSQLSERVER_KATMAI" /SQLCOLLATION="SQL_Latin1_General_CP1_CS_AS" /SQLSYSADMINACCOUNTS="<DomainName\Username>"  
```  
  
#### <a name="upgrade-failover-cluster-parameters"></a>フェールオーバー クラスターのアップグレード パラメーター  
 次の表に示すパラメーターは、フェールオーバー クラスターのアップグレード用コマンド ライン スクリプトを作成する場合に使用します。 詳細については、「[SQL Server フェールオーバー クラスター インスタンスのアップグレード &#40;セットアップ&#41;](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)」および「[Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」をご覧ください。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|インストール ワークフローを示すために必要です。<br /><br /> サポートされる値: **Upgrade**|  
|SQL Server セットアップ コントロール|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/*UpdateEnabled*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、SQL Server セットアップには検出された更新プログラムが含まれます。|  
|SQL Server セットアップ コントロール|/*UpdateSource*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを取得する場所を指定します。 有効値は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update を検索する "MU"、有効なフォルダー パス、相対パス (.\MyUpdates など)、または UNC 共有です。 既定では、SQL Server セットアップは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update または Windows Server Update Services を介して Windows Update Service を検索します。|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/ERRORREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 <br/><br/>エラーのフィードバックを Microsoft に送信する方法を管理するには、「[How to configure SQL Server 2016 to send feedback to Microsoft (SQL Server 2016 を構成し、フィードバックを Microsoft に送信する方法)](http://support.microsoft.com/kb/3153756)」を参照してください。 <br/><br/>以前のバージョンでは、これにより SQL Server のエラー報告が指定されます。<br /><br /> 詳細については、「 [Microsoft エラー報告サービスのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkID=72173)」を参照してください。 サポートされる値: <br /><br /> 0 = 無効<br /><br /> 1 = 有効|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/ INSTANCEDIR<br /><br /> **省略可**|共有コンポーネントの既定以外のインストール ディレクトリを指定します。|  
|SQL Server セットアップ コントロール|/INSTANCEID<br /><br /> **[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降からアップグレードする場合に必須**<br /><br /> **次をアップグレードする場合はオプション: [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]**|[InstanceID](#InstanceID)の既定値以外の値を指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/PID<br /><br /> **省略可**|SQL Server のエディション用のプロダクト キーを指定します。 このパラメーターが指定されていない場合、Evaluation が使用されます。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/SQMREPORTING<br /><br /> **省略可**|SQL Server 2016 には影響しません。 以前のバージョンでは、これにより SQL Server の機能の使用状況レポートが指定されます。<br /><br />サポートされる値: <br /><br /> 0 = 無効<br /><br /> 1 = 有効|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERROLLOWNERSHIP|アップデート中の [フェールオーバーの動作](#RollOwnership) を指定します。|  
|SQL Server Browser サービス|/BROWSERSVCSTARTUPTYPE<br /><br /> **省略可**|SQL Server Browser サービスの[スタートアップ](#Accounts) モードを指定します。 サポートされる値: <br /><br /> **自動**<br /><br /> **無効**<br /><br /> **手動**|  
|SQL Server フルテキスト|/FTUPGRADEOPTION<br /><br /> **省略可**|フルテキスト カタログのアップグレード オプションを指定します。 サポートされる値: <br /><br /> **REBUILD**<br /><br /> **RESET**<br /><br /> **IMPORT**|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のアカウントを指定します。<br /><br /> 既定値: NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパスワードを指定します。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **省略可**|[サービスの](#Accounts) スタートアップ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] モードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSUPGRADEDATABASEACCOUNT<br /><br /> **省略可**|プロパティは、2008 R2 以前のバージョンの SharePoint モードのレポート サーバーをアップグレードする場合にのみ使用されます。 SQL Server 2012 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]で変更された古い SharePoint モード アーキテクチャを使用するレポート サーバーに対しては、追加のアップグレード操作が実行されます。 このオプションがコマンド ライン インストールに含まれていない場合、古いレポート サーバー インスタンスの既定のサービス アカウントが使用されます。 このプロパティが使用されている場合は、**/RSUPGRADEPASSWORD** プロパティを使用してアカウントのパスワードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSUPGRADEPASSWORD<br /><br /> **省略可**|既存のレポート サーバー サービス アカウントのパスワード。|  
  
####  <a name="a-nameaddnodea-add-node-parameters"></a><a name="AddNode"></a> ノード追加パラメーター  
 次の表に示すパラメーターは、ノード追加用のコマンド ライン スクリプトを作成する場合に使用します。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|AddNode ワークフローを示すために必要です。<br /><br /> サポートされる値: **AddNode**|  
|SQL Server セットアップ コントロール|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。**|ライセンス条項への同意を確認するために必要です。|  
|SQL Server セットアップ コントロール|/ENU<br /><br /> **省略可**|ローカライズされたオペレーティング システムに SQL Server の英語版をインストールする場合に、オペレーティング システムに対応する言語と英語の両方の言語パックがインストール メディアに含まれているときは、このパラメーターを使用します。|  
|SQL Server セットアップ コントロール|/*UpdateEnabled*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、SQL Server セットアップには検出された更新プログラムが含まれます。|  
|SQL Server セットアップ コントロール|/*UpdateSource*<br /><br /> **省略可**|SQL Server セットアップが製品の更新プログラムを取得する場所を指定します。 有効値は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update を検索する "MU"、有効なフォルダー パス、相対パス (.\MyUpdates など)、または UNC 共有です。 既定では、SQL Server セットアップは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update または Windows Server Update Services を介して Windows Update Service を検索します。|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **省略可**|エンジン サービスのアカウントを指定します。 既定値は、**NT Authority\NETWORK SERVICE** です。|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **省略可**|エンジン サービス アカウントのパスワードを指定します。|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **省略可**|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|/PBPORTRANGE<br /><br /> **省略可**|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **省略可**|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 サポートされる値: **True**、 **False**|  
|SQL Server セットアップ コントロール|/PID<br /><br /> **省略可**|SQL Server のエディション用のプロダクト キーを指定します。 このパラメーターが指定されていない場合、Evaluation が使用されます。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/QS<br /><br /> **省略可**|セットアップが UI を使用して実行され、UI を使用して進捗状況が表示されるように指定します。さらに、セットアップで入力ができないように、またはエラー メッセージが表示されないように指定します。|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server セットアップ コントロール|/FAILOVERCLUSTERIPADDRESSES<br /><br /> **必須**|エンコードされた IP アドレスを指定します。 エンコードはセミコロン (;) で区切り、\<IP の種類>;\<アドレス>;\<ネットワーク名>;\<サブネット マスク> という形式に従います。 サポートされている IP の種類には、DHCP、IPv4、および IPv6 があります。<br />フェールオーバー クラスターの IP アドレスを複数指定するには、間にスペースを入れます。 次の例を参照してください。<br /><br /> FAILOVERCLUSTERIPADDRESSES=DEFAULT<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;172.16.0.0;ClusterNetwork1;172.31.255.255<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;2001:db8:23:1002:20f:1fff:feff:b3a3;ClusterNetwork1<br /><br /> <br /><br /> 詳細については、「[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;Setup&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/CONFIRMIPDEPENDENCYCHANGE<br /><br /> **必須**|マルチサブネット フェールオーバー クラスターについて、IP アドレス リソースの依存関係を OR に設定することを示します。 詳細については、「[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;セットアップ&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)」をご覧ください。 サポートされる値: <br /><br /> 0 = False (既定値)<br /><br /> 1 = True|  
|SQL Server エージェント|/AGTSVCACCOUNT<br /><br /> **必須**|SQL Server エージェント サービスのアカウントを指定します。|  
|SQL Server エージェント|/AGTSVCPASSWORD<br /><br /> [必須](#Accounts)|SQL Server エージェント サービス アカウントのパスワードを指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCACCOUNT<br /><br /> **必須**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのアカウントを指定します。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのパスワードを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **必須**|SQL Server サービスの開始アカウントを指定します。|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [必須](#Accounts)|SQLSVCACCOUNT のパスワードを指定します。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパスワードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **ファイル専用モードのみで使用可**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール モードを指定します。|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [必須](#Accounts)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスの開始アカウントのパスワードを指定します。|  
  
##### <a name="additional-notes"></a>追加情報:   
 クラスター対応のコンポーネントは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] だけです。 他の機能はクラスターに対応していないので、フェールオーバーに対する可用性があまり高くありません。  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]が配置された既存のフェールオーバー クラスター インスタンスにノードを追加するには  
  
```  
setup.exe /q /ACTION=AddNode /INSTANCENAME="<Insert Instance Name>" /SQLSVCACCOUNT="<SQL account that is used on other nodes>" /SQLSVCPASSWORD="<password for SQL account>" /AGTSVCACCOUNT="<SQL Server Agent account that is used on other nodes>", /AGTSVCPASSWORD="<SQL Server Agent account password>" /ASSVCACCOUNT="<AS account that is used on other nodes>" /ASSVCPASSWORD=”<password for AS account>” /INDICATEPROGRESS /IACCEPTSQLSERVERLICENSETERMS /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;ClusterNetwork1;xxx.xxx.xxx.x" /CONFIRMIPDEPENDENCYCHANGE=0  
```  
  
#### <a name="remove-node-parameters"></a>ノード削除パラメーター  
 次の表に示すパラメーターは、ノード削除用のコマンド ライン スクリプトを作成する場合に使用します。 フェールオーバー クラスターをアンインストールするには、各フェールオーバー クラスター ノードで RemoveNode を実行する必要があります。 詳細については、「[Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーター|Description|  
|-----------------------------------------|---------------|-----------------|  
|SQL Server セットアップ コントロール|/ACTION<br /><br /> **必須**|RemoveNode ワークフローを示すために必要です。<br /><br /> サポートされる値: **RemoveNode**|  
|SQL Server セットアップ コントロール|/CONFIGURATIONFILE<br /><br /> **省略可**|使用する [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) を指定します。|  
|SQL Server セットアップ コントロール|/HELP、/H、/?<br /><br /> **省略可**|パラメーターの使用方法を表示します。|  
|SQL Server セットアップ コントロール|/INDICATEPROGRESS<br /><br /> **省略可**|詳細なセットアップ ログ ファイルがコンソールにパイプされるように指定します。|  
|SQL Server セットアップ コントロール|/INSTANCENAME<br /><br /> **必須**|SQL Server インスタンス名を指定します。<br /><br /> 詳細については、「 [Instance Configuration](../Topic/Instance%20Configuration.md)」を参照してください。|  
|SQL Server セットアップ コントロール|/Q<br /><br /> **省略可**|セットアップが、ユーザー インターフェイスなしで、非表示モードで実行されるように指定します。 このパラメーターは、自動インストールに使用されます。|  
|SQL Server セットアップ コントロール|/QS<br /><br /> **省略可**|セットアップが UI を使用して実行され、UI を使用して進捗状況が表示されるように指定します。さらに、セットアップで入力ができないように、またはエラー メッセージが表示されないように指定します。|  
|SQL Server セットアップ コントロール|/HIDECONSOLE<br /><br /> **省略可**|コンソール ウィンドウを非表示にするか閉じる場合に指定します。|  
|SQL Server セットアップ コントロール|/CONFIRMIPDEPENDENCYCHANGE<br /><br /> **必須**|マルチサブネット フェールオーバー クラスターについて、IP アドレス リソースの依存関係を OR から AND に設定することを示します。 詳細については、「[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;セットアップ&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)」をご覧ください。 サポートされる値: <br /><br /> 0 = False (既定値)<br /><br /> 1 = True|  
  
###### <a name="sample-syntax"></a>サンプル構文:   
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]が配置された既存のフェールオーバー クラスター インスタンスからノードを削除するには  
  
```  
setup.exe /q /ACTION=RemoveNode /INSTANCENAME="<Insert Instance Name>" [/INDICATEPROGRESS] /CONFIRMIPDEPENDENCYCHANGE=0  
```  
  
##  <a name="a-nameaccountsa-service-account-parameters"></a><a name="Accounts"></a> サービス アカウント パラメーター  
 ビルトイン アカウント、ローカル アカウント、またはドメイン アカウントを使用して、SQL Server サービスを構成できます。  
  
> **注:** 管理されたサービス アカウント、仮想アカウント、またはビルトイン アカウントを使用する場合、対応するパスワード パラメーターを指定しないでください。 これらのサービス アカウントの詳細については、「[Windows サービス アカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」の「**[!INCLUDE[win7](../../includes/win7-md.md)] と [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] で利用可能な新しいアカウントの種類**」セクションをご覧ください。  
  
 サービス アカウント構成の詳細については、「[Windows サービス アカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」をご覧ください。  
  
|SQL Server のコンポーネント (SQL Server component)|アカウント パラメーター|パスワード パラメーター|スタートアップの種類|  
|-----------------------------------------|-----------------------|------------------------|------------------|  
|SQL Server エージェント|/AGTSVCACCOUNT|/AGTSVCPASSWORD|/AGTSVCSTARTUPTYPE|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCACCOUNT|/ASSVCPASSWORD|/ASSVCSTARTUPTYPE|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT|/SQLSVCPASSWORD|/SQLSVCSTARTUPTYPE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT|/ISSVCPASSWORD|/ISSVCSTARTUPTYPE|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT|/RSSVCPASSWORD|/RSSVCSTARTUPTYPE|  
  
##  <a name="a-namefeaturea-feature-parameters"></a><a name="Feature"></a> 機能パラメーター  
 特定の機能をインストールするには、/FEATURES パラメーターを使用して、以下の表の親機能の値または機能の値を指定します。 SQL Server の各エディションでサポートされる機能の一覧については、「[SQL Server 2016 の各エディションがサポートする機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)」を参照してください。  
  
|親機能パラメーター|機能パラメーター|説明|  
|:---|:---|:---|  
|SQL||[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、レプリケーション、フルテキスト、および [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]をインストールします。|  
||SQLEngine|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のみをインストールします。|  
||レプリケーション|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]と共にレプリケーション コンポーネントをインストールします。|  
||FullText|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]と共にフルテキスト コンポーネントをインストールします。|  
||DQ|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のインストールを完了するために必要なファイルをコピーします。 SQL Server のインストールが完了したら、DQSInstaller.exe ファイルを実行して、[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]のインストールを完了させる必要があります。 詳細については、「[Data Quality Server のインストールを完了するための DQSInstaller.exe の実行](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)」をご覧ください。 このパラメーターでは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]もインストールされます。|  
||PolyBase|PolyBase コンポーネントをインストールします。|  
||AdvancedAnalytics|R Services (In-Database) をインストールします。|  
|AS||すべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントをインストールします。|  
|RS||すべての [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントをインストールします。|  
|DQC||[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]をインストールします。|  
|IS||すべての [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントをインストールします。|  
|MDS||[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]をインストールします。|  
|SQL_SHARED_MR||Microsoft R Server をインストールします。|  
|Tools*||クライアント ツールおよび SQL Server オンライン ブック コンポーネントをインストールします。|  
||BC|旧バージョンとの互換性コンポーネントをインストールします。|  
||BOL|ヘルプ コンテンツを表示および管理するための SQL Server オンライン ブック コンポーネントをインストールします。|
||Conn|接続コンポーネントをインストールします。|
||DREPLAY_CTLR|分散再生コントローラーをインストールします。|  
||DREPLAY_CLT|分散再生クライアントをインストールします。|  
||SNAC_SDK|[!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server Native Client 用 SDK をインストールします。|  
||SDK|ソフトウェア開発キットをインストールします。|  
||LocalDB**|LocalDB (プログラムの開発者を対象とした [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] の実行モード) をインストールします。|  

*SQL Server 管理ツール (SSMS) は、現在、SQL Server のインストーラーとは別のスタンドアロン インストーラー内にあります。 詳細については、「[コマンド ラインからの SQL Server Management Studio のインストール](https://msdn.microsoft.com/library/bb500441.aspx#Anchor_1)」をご覧ください。

 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express の SKU をインストールするときに、**LocalDB を選択できます。 詳細については、「[SQL Server 2016 Express LocalDB](../../database-engine/configure-windows/sql-server-2016-express-localdb.md)」をご覧ください。  
  
### <a name="feature-parameter-examples"></a>機能パラメーターの例:  
  
|パラメーターおよび値|説明|  
|--------------------------|-----------------|  
|/FEATURES=SQLEngine|レプリケーションおよびフルテキストなしの[!INCLUDE[ssDE](../../includes/ssde-md.md)]をインストールします。|  
|/FEATURES=SQLEngine, FullText|[!INCLUDE[ssDE](../../includes/ssde-md.md)]とフルテキストをインストールします。|  
|/FEATURES=SQL, Tools|完全な[!INCLUDE[ssDE](../../includes/ssde-md.md)]およびすべてのツールをインストールします。|  
|/FEATURES=BOL|ヘルプ コンテンツを表示および管理するための SQL Server オンライン ブック コンポーネントをインストールします。|  
|/FEATURES=SQLEngine, PolBase|PolyBase エンジンをインストールします。|  
  
##  <a name="a-nameroleparametersa-role-parameters"></a><a name="RoleParameters"></a> ロール パラメーター  
 セットアップ ロール パラメーター (/Role パラメーター) は、あらかじめ構成された機能の選択内容をインストールするために使用されます。 [!INCLUDE[ssAS_md](../../includes/ssas-md.md)] のロールでは、既存の SharePoint ファームまたは新規の未構成ファームのどちらかに [!INCLUDE[ssAS_md](../../includes/ssas-md.md)] インスタンスがインストールされます。 これらのシナリオをサポートするために、2 つのセットアップ ロールが用意されています。 インストールするために選択できるセットアップ ロールは一度に 1 つだけです。 セットアップ ロールを選択すると、そのロールに所属する機能とコンポーネントがセットアップによってインストールされます。 ロールに指定されている機能とコンポーネントは変更できません。 機能ロール パラメーターの使用方法の詳細については、「[コマンド プロンプトからの Power Pivot のインストール](http://msdn.microsoft.com/ja-jp/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328)」をご覧ください。  
  
 AllFeatures_WithDefaults ロールは、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のエディションの既定の動作であり、このロールを指定した場合は、ユーザーに対して表示されるダイアログ ボックスの数が減少します。 このロールは、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 以外の SQL Server エディションをインストールするときに、コマンド ラインから指定できます。  
  
|ロール|説明|インストールされる機能|  
|----------|-----------------|---------------|  
|SPI_AS_ExistingFarm|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 名前付きインスタンスとして、既存の [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] ファームまたはスタンドアロン サーバーにインストールします。|メモリ内のデータの格納と処理用にあらかじめ構成された、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 計算エンジン。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ソリューション パッケージ<br /><br /> [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] のインストーラー プログラム<br /><br /> SQL Server オンライン ブック|  
|SPI_AS_NewFarm|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] および[!INCLUDE[ssDE](../../includes/ssde-md.md)]を [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 名前付きインスタンスとして、新しい未構成の Office [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] ファームまたはスタンドアロン サーバーにインストールします。 SQL Server セットアップは、機能ロールのインストール時にファームを構成します。|メモリ内のデータの格納と処理用にあらかじめ構成された、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 計算エンジン。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ソリューション パッケージ<br /><br /> SQL Server オンライン ブック<br /><br /> [!INCLUDE[ssDE](../../includes/ssde-md.md)]<br /><br /> 構成ツール (Configuration Tools)<br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|AllFeatures_WithDefaults|現在のエディションで使用できるすべての機能をインストールします。<br /><br /> 現在のユーザーを SQL Server **sysadmin** 固定サーバー ロールに追加します。<br /><br /> [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] 以降を使用していて、そのオペレーティング システムがドメイン コントローラーでない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は既定で NTAUTHORITY\NETWORK SERVICE アカウントを使用し、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は既定で NTAUTHORITY\NETWORK SERVICE アカウントを使用します。<br /><br /> このロールは、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のエディションで、既定で有効になっています。 その他のエディションの場合、このロールは有効になっていませんが、UI またはコマンド ライン パラメーターを使用して指定できます。|[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]のエディションの場合は、そのエディションで使用できる機能のみがインストールされます。 その他のエディションの場合は、SQL Server のすべての機能がインストールされます。<br /><br /> **AllFeatures_WithDefaults** パラメーターは、**AllFeatures_WithDefaults** パラメーターの設定をオーバーライドする他のパラメーターと組み合わせて使用できます。 たとえば、**AllFeatures_WithDefaults** パラメーターと **/Features=RS** パラメーターを組み合わせて使用すると、すべての機能をインストールするコマンドがオーバーライドされ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のみがインストールされますが、**AllFeatures_WithDefaults** パラメーターを適用することで、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して既定のサービス アカウントが使用されます。<br /><br /> **AllFeatures_WithDefaults** パラメーターを **/ADDCURRENTUSERASSQLADMIN=FALSE** と共に使用すると、準備ダイアログには現在のユーザーに関する情報が自動入力されません。 SQL Server エージェントのサービス アカウントとパスワードを指定するには、**/AGTSVCACCOUNT** と **/AGTSVCPASSWORD** を追加します。|  
  
##  <a name="a-namerollownershipa-controlling-failover-behavior-using-the-failoverclusterrollownership-parameter"></a><a name="RollOwnership"></a> /FAILOVERCLUSTERROLLOWNERSHIP パラメーターを使用したフェールオーバーの動作の制御  
 SQL Server フェールオーバー クラスターを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードするには、フェールオーバー クラスター ノードのパッシブ ノードから開始して、1 ノードごとにセットアップを実行する必要があります。 フェールオーバー クラスター インスタンスのノード総数と、アップグレード済みのノードの数との違いに応じて、セットアップがアップグレード済みのノードにフェールオーバーする時期が決まります。 ノード総数の半数以上がアップグレード済みの場合、既定のセットアップにより、アップグレード済みのノードにフェールオーバーが発生します。  
  
 アップグレード プロセス中にクラスター ノードのフェールオーバーの動作を制御するには、コマンド プロンプトでアップグレード操作を実行して /FAILOVERCLUSTERROLLOWNERSHIP パラメーターを使用し、アップグレード操作によってノードがオフラインになる前にフェールオーバーの動作を制御します。 このパラメーターの使用方法は次のとおりです。  
  
-   /FAILOVERCLUSTERROLLOWNERSHIP=0 を指定すると、クラスターの所有権 (グループの移動) がアップグレード済みのノードに移動しないため、このノードはアップグレード終了時に SQL Server クラスターの実行可能な所有者の一覧に追加されません。  
  
-   /FAILOVERCLUSTERROLLOWNERSHIP=1 を指定すると、クラスターの所有権 (グループの移動) がアップグレードされたノードに移動するため、このノードはアップグレード終了時に SQL Server クラスターの実行可能な所有者の一覧に追加されます。  
  
-   /FAILOVERCLUSTERROLLOWNERSHIP=2 は既定の設定です。 これは、このパラメーターが指定されていない場合に使用されます。 この設定は、SQL Server セットアップによってクラスターの所有権 (グループの移動) が必要に応じて管理されることを示しています。  
  
##  <a name="a-nameinstanceida-instance-id-or-instanceid-configuration"></a><a name="InstanceID"></a> インスタンス ID (InstanceID) の構成  
 インスタンス ID (/InstanceID) パラメーターは、インスタンス コンポーネントのインストール先と、インスタンスのレジストリ パスを指定するために使用されます。 "INSTANCEID" の値は文字列で、一意である必要があります。  
  
-   SQL インスタンス ID:MSSQL13.\<INSTANCEID>  
  
-   AS インスタンス ID:MSAS13.\<INSTANCEID>  
  
-   RS インスタンス ID:MSRS13.\<INSTANCEID>  
  
 インスタンス対応のコンポーネントは次の場所に格納されます。  
  
 %Program Files%\\Microsoft SQL Server\\<SQLInstanceID\>  
  
 %Program Files%\\Microsoft SQL Server\\<ASInstanceID\>  
  
 %Program Files Microsoft SQL Server\\<RSInstanceID\>  
  
> **注:** INSTANCEID をコマンド ラインで指定しない場合、既定のセットアップでは、\<INSTANCEID> の代わりに \<INSTANCENAME> が使用されます。  
  
## <a name="see-also"></a>参照  
 [インストール ウィザードからの SQL Server 2016 のインストール ](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)   
 [SQL Server フェールオーバー クラスターのインストール](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)   
 [[SQL Server 2016 のビジネス インテリジェンス機能のインストール](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)]  
  