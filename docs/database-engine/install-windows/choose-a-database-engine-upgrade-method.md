---
title: "データベース エンジンのアップグレード方法の選択 | Microsoft Docs"
ms.custom: ""
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e57a427-2e88-4ef6-b142-4ccad97bcecc
caps.latest.revision: 23
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 23
---
# データベース エンジンのアップグレード方法の選択
  SQL Server の以前のリリースから [!INCLUDE[ssDE](../../includes/ssde-md.md)] への [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のアップグレードを計画している場合、ダウンタイムとリスクを最小限に抑えるために、考慮すべきいくつかのアプローチがあります。 インプレース アップグレードの実行、新規インストールへの移行、またはローリング アップグレードの実行が可能です。 次の図は、これらのアプローチから選択する場合に役立ちます。 図の各アプローチについては、下でも説明しています。 図の意思決定ポイントに役立てるため、「 [Plan and Test the Database Engine Upgrade Plan](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md)」も参照してください。  
  
 ![Database Engine Upgrade Method Decision Tree](../../database-engine/install-windows/media/database-engine-upgrade-method-decision-tree.png "Database Engine Upgrade Method Decision Tree")  
  
 **ダウンロード**  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]をダウンロードするには、  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**にアクセスしてください。  
  
-   Azure アカウントをすでにお持ちですか?  すでにお持ちの場合は、 **[こちら](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016ctp2evaluationwindowsserver2012r2/?wt.mc_id=sqL16_vm)** にアクセスして、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] がインストール済みの仮想マシンをすぐにご利用いただけます。  
  
> [!NOTE]  
>  また、アップグレード計画の一環として、Azure SQL Database のアップグレードや SQL Server 環境の仮想化を考慮する場合もあります。 それらのトピックは、このトピックの範囲外ですが、次にいくつかリンクを示します。「[SQL Server 2016 ハイブリッド クラウドの概要](../Topic/Introduction%20to%20SQL%20Server%202016%20Hybrid%20Cloud.md)」、「[Azure Virtual Machine における SQL Server の概要](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/)」、「[Azure SQL Database](https://azure.microsoft.com/en-us/services/sql-database/)」、「[クラウド SQL Server オプションの選択：Azure SQL (PaaS) Database または Azure VM (IaaS) の SQL Server](https://azure.microsoft.com/documentation/articles/data-management-azure-sql-database-and-sql-server-iaas/)」。  
  
##  <a name="UpgradeInPlace"></a> インプレース アップグレード  
 このアプローチでは、SQL Server セットアップ プログラムは、既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ビットを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ビットで置き換えて、既存の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストールをアップグレードし、次に各システム データベースとユーザー データベースをアップグレードします。  インプレース アップグレード アプローチは最も簡単ですが、ある程度のダウンタイムを必要とし、フォールバックが必要な場合にフォールバックに時間がかかるため、すべてのシナリオでサポートされるわけではありません。 インプレース アップグレードがサポートされるシナリオとサポートされないシナリオの詳細については、「[サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」を参照してください。  
  
 このアプローチは、次のシナリオでよく使われます。  
  
-   高可用性 (HA) 構成のない開発環境。  
  
-   ダウンタイムを許容でき、最新のハードウェアとソフトウェアで実行されている非ミッション クリティカル運用環境。 ダウンタイムの長さは、データベースのサイズと、I/O サブシステムの速度によって異なります。 メモリ最適化テーブルを使用している場合、SQL Server 2014 をアップグレードすると、余分な時間がかかることがあります。 詳細については、「 [Plan and Test the Database Engine Upgrade Plan](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md)」を参照してください。  
  
> [!WARNING]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ プログラムの実行中に、アップグレード前チェックの実行の一部として、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが停止し、再起動します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアップグレードすると、以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは上書きされて、コンピューター上に存在しなくなります。 アップグレードする前に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースおよび以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関連するその他のオブジェクトをバックアップしてください。  
  
 次の図に、[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインプレース アップグレードに必要な手順の概要を示します。  
  
 ![Database Engine Upgrade Non-HA In-Place Upgrade](../../database-engine/install-windows/media/database-engine-upgrade-non-ha-in-place-upgrade.png "Database Engine Upgrade Non-HA In-Place Upgrade")  
  
 詳細の手順については、「[インストール ウィザードを使用した SQL Server 2016 へのアップグレード &#40;セットアップ&#41;](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)」を参照してください。  
  
##  <a name="NewInstallationUpgrade"></a> 新しいインストールへの移行  
 このアプローチでは、多くの場合に、新しいハードウェア上に、新しいバージョンのオペレーティング システムで新しい [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 環境をビルドしながら、現在の環境を維持します。 新しい環境に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールしたら、既存の環境から既存のユーザー データベースを新しい環境に移行し、ダウンタイムを最小限に抑えるように、新しい環境を準備するための多くの手順を実行します。 これらの手順では、以下の移行が含まれます。  
  
-   **システム オブジェクト:** 一部のアプリケーションでは、シングル ユーザー データベースのスコープ外の情報、エンティティ、オブジェクトに依存する場合があります。 通常、アプリケーションには、マスター データベースと msdb データベースへの依存関係があり、ユーザー データベースにも依存関係があります。 ユーザー データベースの外部に格納される (ユーザー データベースを正しく機能させるために必要な) すべてのデータは、対象のサーバー インスタンスで使用できるようにする必要があります。 たとえば、アプリケーションのログインが、マスター データベースにメタデータとして格納されているため、それらを移行先サーバーで再作成する必要があります。 アプリケーションまたはデータベースのメンテナンス プランが、メタデータが msdb データベースに格納されるエージェント ジョブに依存している場合、移行先サーバー インスタンスでこれらのジョブを再作成する必要があります。 同様に、サーバーレベルのトリガーのメタデータはマスターに格納されます。  
    アプリケーションのデータベースを別のサーバー インスタンスに移動するときは、移行先サーバー インスタンス上のマスターおよび msdb に、依存しているエンティティとオブジェクトのすべてのメタデータを再作成する必要があります。 たとえば、データベース アプリケーションでサーバーレベルのトリガーを使用している場合、そのデータベースを新しいシステムでアタッチまたは復元するだけでは不十分です。 このデータベースは、マスター データベース内にこれらのトリガーのメタデータを手動で再作成しない限り、正常に動作しません。 詳細については、「[データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage metadata when making a database available on another server.md)」を参照してください。  
  
-   **MSDB に格納されている Integration Services パッケージ:** MSDB にパッケージを格納する場合、 [dtutil Utility](../../integration-services/dtutil-utility.md) を使用して、それらのパッケージをスクリプトに記述するか、新しいサーバーに再配置する必要があります。 新しいサーバーでパッケージを使用する前に、パッケージを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードする必要があります。 詳細については、「 [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md)」を参照してください。  
  
-   **Reporting Services 暗号化キー:** レポート サーバー構成で重要なのは、機密情報の暗号化に使用される対称キーのバックアップ コピーの作成です。 キーのバックアップ コピーは多くのルーチン処理で必要とされ、キーのバックアップ コピーにより新しいインストールで既存のレポート サーバー データベースを再利用できます。 詳細については、「[Reporting Services の暗号化キーのバックアップと復元](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md)」および「[Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。  
  
 新しい   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 環境に既存の環境と同じシステム オブジェクトを設定したら、既存のシステムのダウンタイムを最小限に抑える方法で、ユーザー データベースを既存のシステムから、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスに移行します。 データベースの移行を実行するには、バックアップと復元を使用するか、SAN 環境内の場合は LUN を再指定します。 両方の方法の手順を下の図に示しています。  
  
> [!CAUTION]  
>  ダウンタイムの長さは、データベースのサイズと、I/O サブシステムの速度によって異なります。 メモリ最適化テーブルを使用している場合、SQL Server 2014 をアップグレードすると、余分な時間がかかることがあります。 詳細については、「 [Plan and Test the Database Engine Upgrade Plan](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md)」を参照してください。  
  
 ユーザー データベースの移行後、多様な方法 (サーバー名の変更、DNS エントリの使用、接続文字列の変更など) のいずれかを使用して、新しいユーザーを新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに指示します。  新規インストール アプローチは、インプレース アップグレードと比較して、リスクとダウンタイムを減らし、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレードと同時のハードウェアとオペレーティング システムのアップグレードを容易にします。  
  
> [!NOTE]  
>  既に高可用性 (HA) ソリューションを設置しているなど、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが複数ある環境の場合は、「[ローリング アップグレード](#RollingUpgrade)」に進みます。 高可用性ソリューションを設定していない場合は、[データベース ミラーリング](http://msdn.microsoft.com/library/ms190941.aspx)を一時的に構成して、ダウンタイムを最小にして、このアップグレードを容易にするか、またはこの機会を利用して、永続的な HA ソリューションとして、[Always On 可用性グループ](http://msdn.microsoft.com/library/hh510260.aspx)を構成することを考慮できます。  
  
 たとえば、このアプローチは、次をアップグレードする場合に使用できます。  
  
-   サポートされていないオペレーティング システムへの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は X86 インストールをサポートしていないため、SQL Server の x86 インストール。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 新しいハードウェアや新しいバージョンのオペレーティング システムへ。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] としての SQL Server 2005 では、SQLServer 2005 から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのインプレース アップグレードはサポートされていません。 詳細については、「 [Are you upgrading from SQL Server 2005?](../../database-engine/install-windows/are-you-upgrading-from-sql-server-2005.md)」を参照してください。  
  
 新規インストール アップグレードに必要な手順は、アタッチされたストレージを使用するか、または SAN ストレージを使用するかどうかによってやや異なります。  
  
-   **アタッチされたストレージ環境:** アタッチされたストレージを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境がある場合、次の図と図内のリンクで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の新規インストール アップグレードに必要な手順を示しています。  
  
     ![New installation upgrade method using backup and restore for attached storage](../../database-engine/install-windows/media/new-installation-upgrade-method-using-backup-and-restore-for-attached-storage.png "New installation upgrade method using backup and restore for attached storage")  
  
-   **SAN ストレージ環境:**  SAN ストレージを使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境がある場合、次の図と図内のリンクで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の新規インストール アップグレードに必要な手順を示しています。  
  
     ![New installation upgrade method using detach and attach for SAN storage](../../database-engine/install-windows/media/new-installation-upgrade-method-using-detach-and-attach-for-san-storage.png "New installation upgrade method using detach and attach for SAN storage")  
  
##  <a name="RollingUpgrade"></a> ローリング アップグレード  
 ローリング アップグレードは、特定の順序でアップグレードする必要がある複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを含む SQL Server ソリューション環境で、アップタイムを最大にし、リスクを最小にして、機能を維持するために必要です。 ローリング アップグレードは、基本的に特定の順序での複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのアップグレードであり、既存の各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対してインプレース アップグレードを実行するか、またはアップグレード プロジェクトの一環としてハードウェアやオペレーティング システムのアップグレードを容易にするために、新規インストール アップグレードを実行します。 ローリング アップグレード アプローチを使用する必要がある多くのシナリオがあります。 これらを以下の各トピックで説明します。  
  
-   Always-On 可用性グループ: この環境でローリング アップグレードを実行する詳細な手順については、「[Always-On 可用性グループ レプリカ インスタンスのアップグレード](../../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)」を参照してください。  
  
-   フェールオーバー クラスタリング インスタンス: この環境でローリング アップグレードを実行する詳細な手順については、「[SQL Server フェールオーバー クラスター インスタンスのアップグレード](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)」を参照してください。  
  
-   ミラー化インスタンス: この環境でローリング アップグレードを実行する詳細な手順については、「[ミラー化されたインスタンスのアップグレード](../../database-engine/database-mirroring/upgrading-mirrored-instances.md)」を参照してください。  
  
-   ログ配布インスタンス: この環境でローリング アップグレードを実行する詳細な手順については、「[SQL Server 2016 へのログ配布のアップグレード &#40;Transact-SQL&#41;](../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)」を参照してください。  
  
-   レプリケーション環境: この環境でローリング アップグレードを実行する詳細な手順については、「 [Upgrade Replicated Databases](../../database-engine/install-windows/upgrade-replicated-databases.md)」を参照してください。  
  
-   SQL Server Reporting Services スケールアウト環境: この環境でローリング アップグレードを実行する詳細な手順については、「[Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。  
  
## この記事は役に立ちましたか? フィードバックをお待ちしております。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。  [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Choose%20a%20Database%20Engine%20Upgrade%20Method%20page)にコメントをお送りください  
  
## 参照  
 [データベース エンジンのアップグレード計画の策定およびテスト](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md)   
 [データベース エンジンのアップグレードの完了](../../database-engine/install-windows/complete-the-database-engine-upgrade.md)  
  
  