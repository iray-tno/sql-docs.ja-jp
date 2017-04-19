---
title: "SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 463c570e-9f75-4653-b3b8-4d61753b0013
caps.latest.revision: 16
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 16
---
# SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールは、1 つ以上の別個のインスタンスで構成されます。 既定のインスタンスか名前付きインスタンスかにかかわらず、各インスタンスには、それぞれ専用のプログラム ファイルとデータ ファイルが用意されます。さらに、コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのインスタンスが使用する共有ファイル セットもあります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]が含まれている場合は、これらの各コンポーネントで使用するデータと実行ファイルのセット、およびすべてのコンポーネントが使用する共有ファイルが用意されます。  
  
 コンポーネントごとにインストール場所を分けるため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の各コンポーネントについて一意のインスタンス ID が生成されます。  
  
> [!IMPORTANT]  
>  リムーバブル ディスク ドライブ、圧縮を使用するファイル システム、システム ファイルが存在するディレクトリ、およびフェールオーバー クラスター インスタンス上の共有ドライブには、プログラム ファイルとデータ ファイルをインストールすることができません。  
>  
>  SQL Server のフォルダーおよびファイルの種類を除外するように、ウイルス対策アプリケーションやスパイウェア対策アプリケーションなどのスキャン ソフトウェアを構成することが必要な場合があります。 詳細については、[SQL Server を実行するコンピューターでのウイルス対策ソフトウェア](https://support.microsoft.com/kb/309422)に関するこちらのサポート記事をご覧ください。
> 
>  システム データベース (master、model、MSDB、および tempdb) と[!INCLUDE[ssDE](../../includes/ssde-md.md)]のユーザー データベースは、ストレージ オプションとしてサーバー メッセージ ブロック (SMB) ファイル サーバーを指定してインストールできます。 これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スタンドアロン インストールと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インストール (FCI) の両方に当てはまります。 詳細については、「 [Install SQL Server with SMB Fileshare as a Storage Option](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md)」を参照してください。  
>   
>  Binn、Data、Ftdata、HTML、1033 の各ディレクトリとその内容は削除しないでください。 他のディレクトリは必要に応じて削除できますが、削除した機能やデータを元に戻すには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をいったんアンインストールしてからインストールし直す必要があります。 HTML ディレクトリ内のすべての .htm ファイルは、削除も修正もしないでください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のツールを正常に機能させるには、これらのファイルが必要です。  
  
## のすべてのインスタンスで共有されるファイル [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 同じコンピューター上のすべてのインスタンスが使用する共通ファイルは、[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)] フォルダーにインストールされます (\<*ドライブ*> は、コンポーネントがインストールされているドライブ名です)。 既定値は、通常はドライブ C です。  
  
## ファイルの場所とレジストリのマッピング  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップの実行時には、サーバー コンポーネントごとにインスタンス ID が生成されます。 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リリースのサーバー コンポーネントは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。  
  
 既定のインスタンス ID は、次の形式を使用して作成されます。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]を表す "MSSQL" に、メジャー バージョン番号、アンダースコアおよびマイナー番号 (該当する場合)、ピリオド、およびインスタンス名を連結した形式  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を表す "MSAS" に、メジャー バージョン番号、アンダースコアおよびマイナー番号 (該当する場合)、ピリオド、およびインスタンス名を連結した形式  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を表す "MSRS" に、メジャー バージョン番号、アンダースコアおよびマイナー番号 (該当する場合)、ピリオド、およびインスタンス名を連結した形式  
  
 このリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における既定のインスタンス ID の例を次に示します。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の既定のインスタンスの場合: MSSQL13.MSSQLSERVER。  
  
-   [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]の既定のインスタンスの場合: MSAS13.MSSQLSERVER。  
  
-   "MyInstance" という名前の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスの場合: MSSQL13.MyInstance。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]および [!INCLUDE[ssDE](../../includes/ssde-md.md)] を含み、名前が "MyInstance" で、インストール先が既定のディレクトリである [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の名前付きインスタンスの場合、ディレクトリ構造は次のようになります。  
  
-   C:\Program Files\Microsoft SQL Server\MSSQL13.MyInstance\  
  
-   C:\Program Files\Microsoft SQL Server\MSAS13.MyInstance\  
  
 インスタンス ID には任意の値を指定できますが、特殊文字や予約されたキーワードは使用しないでください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ時に、既定以外のインスタンス ID を指定できます。 ユーザーが既定のインストール ディレクトリを変更した場合は、\<Program Files>\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の代わりに \<カスタム パス>\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用されます。 アンダースコア (_) で始まるインスタンス ID、またはシャープ記号 (#) かドル記号 ($) を含むインスタンス ID はサポートされていないことに注意してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] とクライアント コンポーネントはインスタンス対応でないため、インスタンス ID は割り当てられません。 既定では、インスタンス対応でないコンポーネントが単一のディレクトリ [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)] にインストールされます。 1 つの共有コンポーネントのインストール パスを変更すると、他の共有コンポーネントのパスも変更されます。 後続のインストールでは、最初のインストールと同じディレクトリに、インスタンス対応でないコンポーネントがインストールされます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、インストール後にインスタンスの名前を変更できる、唯一の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントです。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの名前を変更しても、インスタンス ID は変更されません。 インスタンスの名前変更が完了した後も、ディレクトリとレジストリ キーは、インストール時に作成されたインスタンス ID を引き続き使用します。  
  
 インスタンス対応のコンポーネントの場合は、HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*Instance_ID*> の下にレジストリ ハイブが作成されます。 例を次に示します。  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.MyInstance  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.MyInstance  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.MyInstance  
  
 このレジストリは、インスタンス ID とインスタンス名のマッピングも管理します。 インスタンス ID とインスタンス名のマッピングは次のようになります。  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instance Names\SQL] "InstanceName"="MSSQL13"  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instance Names\OLAP] "InstanceName"="MSAS13"  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instance Names\RS] "InstanceName"="MSRS13"  
  
## ファイル パスの指定  
 セットアップ中、次の機能のインストール パスを変更できます。  
  
 セットアップでインストール パスが表示されるのは、ユーザーがインストール先フォルダーを構成できる機能のみです。  
  
|コンポーネント|既定のパス|構成可能/固定パス|  
|---------------|------------------|--------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] サーバー コンポーネント|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceID>\|構成可能|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] データ ファイル|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceID>\|構成可能|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー (server)|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.\<InstanceID>\|構成可能|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ファイル|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.\<InstanceID>\|構成可能|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー (report server)|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.\<InstanceID>\Reporting Services\ReportServer\Bin\|構成可能|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート マネージャー|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.\<InstanceID>\Reporting Services\ReportManager\|固定パス|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|\<インストール ディレクトリ>\130\DTS\|構成可能*|  
|クライアント コンポーネント (bcp.exe および sqlcmd.exe を除く)|\<インストール ディレクトリ>\130\Tools\|構成可能*|  
|クライアント コンポーネント (bcp.exe および sqlcmd.exe)|\<インストール ディレクトリ>\Client SDK\ODBC\110\Tools\Binn|固定パス|  
|レプリケーションおよびサーバー側 COM オブジェクト|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM (COM)\\**|固定パス|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネント DLL (データ変換ランタイム エンジン、データ変換パイプライン エンジン、および **dtexec** コマンド プロンプト ユーティリティ用)|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Binn|固定パス|  
|DLL。次のマネージ接続をサポート:  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Connections|固定パス|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がサポートする列挙子の型ごとの DLL|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\ForEachEnumerators|固定パス|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service、WMI プロバイダー|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Shared\|固定パス|  
|次のすべてのインスタンス間で共有されるコンポーネント: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Shared\|固定パス|  
  
 **\*\* セキュリティに関する注意 \*\*** \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\ フォルダーが権限の制限により保護されていることを確認してください。  
  
 ファイルの場所の既定のドライブは *systemdrive*で、通常は C ドライブです。子機能のインストール パスは、親機能のインストール パスと同じになります。  
  
 * 1 つのインストール パスが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] とクライアント コンポーネントの間で共有されます。 1 つのコンポーネントのインストール パスを変更すると、他のコンポーネントのパスも変更されます。 後続のインストールでは、最初のインストールと同じ場所にコンポーネントがインストールされます。  
  
 ** このディレクトリは、コンピューター上のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで使用されます。 コンピューター上のいずれかのインスタンスに更新を適用すると、このフォルダー内のファイルに対する変更内容が、コンピューター上のすべてのインスタンスに反映されます。 既存のインストールに機能を追加する場合、前にインストールした機能の場所は変更できません。また、新しい機能のインストール場所を指定することもできません。 セットアップで以前に設定したディレクトリに追加機能をインストールするか、製品をいったんアンインストールしてインストールし直す必要があります。  
  
> [!NOTE]  
>  クラスター化された構成では、クラスターのすべてのノードで使用できるローカル ドライブを選択する必要があります。  
  
 セットアップ時にサーバー コンポーネントまたはデータ ファイルのインストール パスを指定する場合、プログラム ファイルとデータ ファイルについては、指定した場所に加えてインスタンス ID も使用されます。 ツールおよびその他の共有ファイルについては、インスタンス ID は使用されません。 また、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プログラム ファイルとデータ ファイルについてもインスタンス ID は使用されませんが、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] リポジトリについてはインスタンス ID が使用されます。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]機能のインストール パスを設定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップではそのパスがルート ディレクトリとして使用されます。このルート ディレクトリは、SQL データ ファイルを含め、そのインストールで使用するすべてのインスタンス固有フォルダーに適用されます。 この場合、ルートを "C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceName>\MSSQL\\" に設定すると、このパスの末尾にインスタンス固有のディレクトリが追加されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザード (セットアップ UI モード) で USESYSDB アップグレード機能の使用を選択すると、製品が再帰的フォルダー階層にインストールされることがよくあります。 たとえば、\<*SQLProgramFiles*>\MSSQL13\MSSQL\MSSQL10_50\MSSQL\Data\\ です。 USESYSDB 機能を使用する場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]機能ではなく、SQL データ ファイル機能のインストール パスを設定してください。  
  
> [!NOTE]  
>  データ ファイルは、常に、Data という名前の子ディレクトリに格納されているものと見なされます。 たとえば、アップグレード時に、システム データベースのデータ ディレクトリのルート パスとして C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceName>\ を指定すると、データ ファイルは C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceName>\MSSQL\Data に見つかります。  
  
## 参照  
 [データベース エンジンの構成 - データ ディレクトリ](../Topic/Database%20Engine%20Configuration%20-%20Data%20Directories.md)   
 [Analysis Services の構成 - データ ディレクトリ](../Topic/Analysis%20Services%20Configuration%20-%20Data%20Directories.md)  
  
  