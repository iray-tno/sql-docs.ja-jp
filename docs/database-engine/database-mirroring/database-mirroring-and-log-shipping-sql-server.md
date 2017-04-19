---
title: "データベース ミラーリングとログ配布 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データベース ミラーリング [SQL Server], 相互運用性"
  - "ログ配布 [SQL Server], データベース ミラーリング"
ms.assetid: 53e98134-e274-4dfd-8b72-0cc0fd5c800e
caps.latest.revision: 36
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 36
---
# データベース ミラーリングとログ配布 (SQL Server)
  特定のデータベースをミラーリングまたはログ配布することができます。また、ミラーリングとログ配布を同時に行うこともできます。 使用する方法を選択するには、次の点を検討します。  
  
-   必要な配布先サーバーは何台か。  
  
     配布先データベースが 1 つしか必要でない場合は、データベース ミラーリングをお勧めします。  
  
     配布先データベースが複数必要である場合、ログ配布を単独で使用するか、またはデータベース ミラーリングと併用する必要があります。 2 つの操作を組み合わせることで、データベース ミラーリングの利点を得られるだけでなく、ログ配布により複数配布先のサポートが可能になります。  
  
-   配布先データベースでのログ復元を (論理エラーに対する保護などの目的で) 遅延させる必要があるか。その場合は、ログ配布を単独またはデータベース ミラーリングと合わせて使用します。  
  
 ここでは、ログ配布とデータベース ミラーリングを組み合わせる場合の考慮事項について説明します。  
  
> [!NOTE]  
>  それぞれのテクノロジの概要については、「[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)」と「[ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。  
  
## ログ配布とデータベース ミラーリングの組み合わせ  
 ログ配布のバックアップ共有が損なわれていない場合、ミラーリング セッションのプリンシパル データベースをログ配布構成のプライマリ データベースとして使用することも (またはその逆を行うことも) できます。 データベース ミラーリングのセッションは、同期 (トランザクションの安全性の設定が FULL) と非同期 (トランザクションの安全性の設定が OFF) のいずれの操作モードでも実行できます。  
  
> [!NOTE]  
>  データベース ミラーリングを使用するには、常に完全復旧モデルが必要になります。  
  
 通常は、ログ配布とデータベース ミラーリングを組み合わせる場合、ログ配布の前にミラーリング セッションを確立します。ただしこの順序は必須ではありません。 次に、現在のプリンシパル データベースを、ログ配布のプライマリとして、1 つ以上のリモート セカンダリ データベースと共に構成します (*プリンシパル/プライマリ データベース*)。 また、ミラー データベースもログ配布のプライマリ (*ミラー/プライマリ データベース*) として構成する必要があります。 ログ配布のセカンダリ データベースは、プリンシパル/プライマリ サーバーおよびミラー/プライマリ サーバーのいずれとも異なるサーバー インスタンスに配置するようにします。  
  
> [!NOTE]  
>  ログ配布で使用するサーバーすべてについて、大文字と小文字の区別に関する設定を揃えてください。  
  
 ログ配布セッションでは、プライマリ データベースのバックアップ ジョブによりログ バックアップがバックアップ フォルダーに作成されます。 このフォルダーから、セカンダリ サーバーのコピー ジョブによりバックアップのコピーが行われます。 バックアップ ジョブおよびコピー ジョブが成功するには、ジョブからログ配布のバックアップ フォルダーに対するアクセスが必要です。 プライマリ サーバーの可用性を最大にするため、バックアップ フォルダーは独立したホスト コンピューターの共有のバックアップ場所に作成することをお勧めします。 この共有のバックアップ場所 (*バックアップ共有*といいます) は、ミラー/プライマリ サーバーを含めたすべてのログ配布サーバーからアクセスできるようにします。  
  
 データベース ミラーリングのフェールオーバー後もログ配布を続行するには、プリンシパル データベースをプライマリにしたときと同一の構成で、ミラー サーバーをプライマリ サーバーとして構成する必要があります。 ミラー データベースの復元中は、バックアップ ジョブを行ってミラー データベースにログをバックアップすることができません。 したがって、セカンダリ サーバーへのログ バックアップのコピーを進行中のプリンシパル/プライマリ データベースがミラー/プライマリ データベースによって妨害されることはありません。 誤った警告が報告されるのを防ぐため、ミラー/プライマリ データベースでのバックアップ ジョブの実行後、**log_shipping_monitor_history_detail** テーブルにメッセージ ログが書き込まれ、成功のステータスがエージェント ジョブから返されます。  
  
 ログ配布セッション中はミラー/プライマリ データベースがアクティブでなくなります。 ただし、ミラーリングがフェールオーバーした場合は以前のミラー データベースがプリンシパル データベースとしてオンラインになります。 同時に、そのデータベースはログ配布プライマリ データベースとしてアクティブになります。 そのデータベースにログを配布できなかったログ配布のバックアップ ジョブにより、ログ配布が開始されます。 逆に、フェールオーバーが発生すると、以前のプリンシパル/プライマリ データベースが新しいミラー/プライマリ データベースになって復元状態になります。そのデータベースに対するバックアップ ジョブはログのバックアップを停止します。  
  
> [!NOTE]  
>  自動フェールオーバーの場合は、以前のプリンシパル/プライマリ データベースがミラーリング セッションに再度参加したときに、ミラーの役割への交代が発生します。  
  
 自動フェールオーバーを伴う高い安全性モードを実行するには、*ミラーリング監視サーバー インスタンス*と呼ばれる追加のサーバー インスタンスを使用してミラーリング セッションを構成します。 データベースを同期した後で何かの理由によりプリンシパル データベースに障害が発生した場合、およびミラー サーバーとミラーリング監視サーバーが相互通信を続行できる場合は、自動フェールオーバーが発生します。 自動フェールオーバーが発生すると、プリンシパルの役割がミラー サーバーに引き継がれ、ミラーのデータベースがプリンシパル データベースとしてオンラインになります。 新しいプリンシパル/プライマリ サーバーからログ配布のバックアップ場所にアクセスできる場合、バックアップ ジョブはその場所へのログ バックアップの配布を開始します。 データベース ミラーリングを同期モードにすると、ログ チェーンがミラーリングのフェールオーバーの影響を受けず、有効なログのみが復元されます。 セカンダリ サーバーは、別のサーバー インスタンスがプライマリ サーバーになったことを認識することなくログ バックアップのコピーを継続します。  
  
 ローカル ログ配布モニターを使用している場合、このシナリオのために特別に考慮が必要な事項はありません。 このシナリオでリモート監視インスタンスを使用する際の詳細については、このトピックの「リモート監視インスタンスでのデータベース ミラーリングの影響」を参照してください。  
  
## プリンシパルからミラー データベースへのフェールオーバー  
 次の図に、自動フェールオーバーを伴う高い安全性モードでミラーリングを実行する際の、ログ配布とデータベース ミラーリングの連係動作を示します。 **Server_A** はミラーリング用のプリンシパル サーバーであり、ログ配布用のプライマリ サーバーでもあります。 **Server_B** はミラー サーバーであり、プライマリ サーバーとして構成されています。現在はアクティブになっていません。 **Server_C** および **Server_D** はログ配布のセカンダリ サーバーです。 ログ配布セッションの可用性を最大にするため、バックアップの場所は独立したホスト コンピューターの共有ディレクトリに作成します。  
  
 ![ログ配布とデータベース ミラーリング](../../database-engine/database-mirroring/media/logshipping-and-dbm-automatic-failover.gif "ログ配布とデータベース ミラーリング")  
  
 ミラーリング フェールオーバー後も、セカンダリ サーバーで定義されているプライマリ サーバーの名前は変わりません。 」を参照してください。  
  
## リモート監視インスタンスでのデータベース ミラーリングの影響  
 ログ配布をリモート監視インスタンスと共に使用しているときは、ログ配布セッションとデータベース ミラーリングを組み合わせることでモニター テーブルの情報に影響が及びます。 プライマリに関する情報は、プリンシパル/プライマリで構成されたモニターと各セカンダリで構成されたモニターの組み合わせです。  
  
 できる限り監視をシームレスにするため、リモート モニターを使用する場合は、セカンダリでプライマリを構成するときに元のプライマリの名前を指定することをお勧めします。 こうすることで、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントからのログ配布構成の変更も容易になります。 監視の詳細については、「[ログ配布の監視 &#40;Transact-SQL&#41;](../../database-engine/log-shipping/monitor-log-shipping-transact-sql.md)」を参照してください。  
  
## ミラーリングとログ配布を合わせた設定  
 データベース ミラーリングとログ配布を合わせて設定するには、次の手順を実行する必要があります。  
  
1.  NORECOVERY が設定されたプリンシパル/プライマリ データベースのバックアップを別のサーバー インスタンスに復元します。このバックアップは、後でデータベース ミラーリングのプリンシパル/プライマリ データベースに対するミラー データベースとして使用します。 詳細については、「[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)」を参照してください。  
  
2.  データベース ミラーリングをセットアップする。 詳細については、「[Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)」または「[データベース ミラーリングの設定 &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)」を参照してください。  
  
3.  プリンシパル/プライマリ データベースのバックアップを別のサーバー インスタンスに復元します。このバックアップは、後でログ配布のプライマリ データベースに対するセカンダリ データベースとして使用します。  
  
4.  1 つ以上のセカンダリ データベースのプライマリ データベースであるプリンシパル データベースにログ配布を設定します。  
  
     バックアップ ディレクトリ (バックアップ共有) として使用する共有を 1 つ設定します。 これにより、プリンシパル サーバーとミラー サーバーの間で役割を交代した後も、引き続き前と同一のディレクトリにバックアップ ジョブによる書き込みが行われます。 ベスト プラクティスは、この共有の場所をミラーリングとログ配布に関与しているデータベースをホストするサーバーとは異なる物理サーバー上にすることです。  
  
     詳細については、「[ログ配布の構成 &#40;SQL Server&#41;](../../database-engine/log-shipping/configure-log-shipping-sql-server.md)」を参照してください。  
  
5.  プリンシパルからミラーへ手動でフェールオーバーします。  
  
     手動フェールオーバーを実行するには、次の手順を実行します。  
  
    -   [データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
6.  プライマリ データベースである新しいプリンシパル (以前のミラー) にログ配布を設定します。  
  
    > [!IMPORTANT]  
    >  セカンダリからは設定を実行しないでください。  
  
     手順 4. で使用したものと同一のバックアップ共有を使用する必要があります。  
  
     [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[トランザクション ログの配布]** インターフェイスで、ログ配布構成ごとにサポートされるプライマリ データベースは 1 つのみです。 このため、新しいプリンシパルをプライマリとして設定するにはストアド プロシージャを使用する必要があります。  
  
7.  元のプリンシパルにフェールバックするには、別の手動フェールオーバーを実行します。  
  
  