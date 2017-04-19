---
title: "マージ レプリケーションの競合検出および解決の詳細 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マージ レプリケーションの競合回避 [SQL Server レプリケーション], 競合回避について"
  - "既定の競合回避モジュール"
  - "列レベルの競合追跡"
  - "行レベルの競合追跡"
  - "マージ レプリケーションの競合の表示"
  - "マージ レプリケーションの競合解決"
  - "論理レコード レベルの競合追跡 [SQL Server レプリケーション]"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
ms.assetid: 063d3d9c-ccb5-4fab-9d0c-c675997428b4
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# マージ レプリケーションの競合検出および解決の詳細
  パブリッシャーとサブスクライバーが接続され、同期が発生すると、マージ エージェントによって競合の検出が行われます。 競合が検出された場合、マージ エージェントは競合回避モジュール (アーティクルをパブリケーションに追加するときに指定) を使用して、他のサイトに反映する許容データを決定します。  
  
> [!NOTE]  
>  サブスクライバーとパブリッシャーの同期が取られていても、異なるサブスクライバーで行われた更新の間に競合が発生する場合があります。これに比べ、サブスクライバーとパブリッシャーにおける更新では、競合はあまり発生しません。  
  
 競合検出および解決の動作は、次のオプションによって異なります。これらのオプションについては、このトピックで解説します。  
  
-   列レベルの追跡、行レベルの追跡、または論理レコードレベルの追跡のいずれかを指定しているかどうか。  
  
-   優先度に基づく解決メカニズムを指定しているかどうか、またはアーティクル競合回避モジュールを指定しているかどうか。 アーティクル競合回避モジュールは次のいずれかになります。  
  
    -   A *ビジネス ロジック ハンドラー* マネージ コードで記述します。  
  
    -   COM ベース *カスタム競合回避モジュール*します。  
  
    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] によって提供される COM ベースの競合回避モジュール  
  
     既定の解決メカニズムを使用する場合、クライアントまたはサーバーのどちらのサブスクリプションが使用されるかによっても動作が異なります。  
  
## 競合検出  
 データの変更が競合と見なされるかどうかは、アーティクルに対して設定した競合の追跡の種類によって異なります。  
  
-   列レベルの追跡を選択している場合、複数のレプリケーション ノードで行われた同一行の同一列に対する変更が競合と見なされます。  
  
-   行レベルの追跡を選択している場合、複数のレプリケーション ノードで行われた同一行の任意の列に対する変更が競合と見なされます (該当する行で影響を受ける列が同一である必要はありません)。  
  
-   論理レコードレベルの追跡を選択している場合、複数のレプリケーション ノードで行われた同一論理レコードの任意の行に対する変更が競合と見なされます (該当する行で影響を受ける列が同一である必要はありません)。  
  
 詳しくは、「 [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md)」をご覧ください。  
  
 アーティクルに対して競合の追跡と競合解決のレベルを指定するには、「 [Specify the Conflict Tracking and Resolution Level for Merge Articles](../../../relational-databases/replication/publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)」を参照してください。  
  
## 競合解決  
 競合が検出されると、選択した競合回避モジュールがマージ エージェントによって起動され、この競合回避モジュールを使用して、競合で優先するデータを決定します。 競合で優先された行がパブリッシャーおよびサブスクライバーで適用され、優先されなかった行のデータは競合テーブルに書き込まれます。 対話型操作による競合解決を選択しなかった場合、競合はモジュールの実行直後に解決されます。  
  
### 競合回避モジュールの種類  
 マージ レプリケーションでは、アーティクル レベルで競合解決が行われます。 複数のアーティクルで構成されているパブリケーションの場合、複数の競合回避モジュールで各アーティクルに対応するか、1 つの競合回避モジュールで 1 つのアーティクル、複数のアーティクル、またはパブリケーションを構成するすべてのアーティクルに対応できます。  
  
 既定の優先度に基づく競合回避モジュールを使用する場合、アーティクルに対して競合回避モジュール プロパティを設定する必要はありません。 既定の競合回避モジュールではなくアーティクル競合回避モジュールを使用する場合、パブリッシャーで使用できる競合回避モジュールを選択し、アーティクルに対して競合回避モジュールのプロパティを設定する必要があります。 競合回避モジュールに渡す必要がある特定の情報を、競合回避モジュール情報のプロパティに指定することもできます。  
  
 マージ レプリケーションでは、次に示す 4 つの競合回避モジュールを使用できます。  
  
-   既定の優先度に基づく競合回避モジュール  
  
     既定の解決メカニズムの動作は、クライアント サブスクリプションまたはサーバー サブスクリプションのどちらが使用されているかによって異なります。 サーバー サブスクリプションを使用する個々のサブスクライバーに優先度値を割り当てると、最も優先度の高いノードで行われた変更が競合で最優先されます。 クライアント サブスクリプションの場合は、パブリッシャーに書き込まれた最初の変更が優先されます。  
  
     サブスクリプションの作成後にその種類を変更することはできません。  
  
-   ビジネス ロジック ハンドラー  
  
     ビジネス ロジック ハンドラー フレームワークを使用すると、マネージ コードのアセンブリを記述して、マージ同期処理中に呼び出すことができます。 このアセンブリには、競合など同期中に発生するさまざまな状況に対処するためのビジネス ロジックを記述できます。 詳細については、次を参照してください。 [マージ同期中にビジネス ロジックを実行](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)します。  
  
-   COM ベースのカスタム競合回避モジュール  
  
     マージ レプリケーションなどの言語で COM オブジェクトとしての競合回避モジュールを記述するための API では [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]します。 詳細については、次を参照してください。 [COM ベース カスタム競合回避モジュール](../../../relational-databases/replication/merge/com-based-custom-resolvers.md)します。  
  
-   COM ベース競合回避モジュールによって提供されます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]  
  
     [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] COM ベース競合回避モジュールの数が含まれます。 詳細については、次を参照してください。 [Microsoft COM ベース競合回避モジュール](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md)します。  
  
 競合回避モジュールの該当する種類を選択する方法については、次を参照してください。 [競合回避モジュールを選択して](../../../relational-databases/replication/merge/choose-a-resolver.md)します。  
  
> [!NOTE]  
>  アーティクル競合回避モジュールの中には、特定の操作が行われた場合のみ競合を処理するように作成されているものもあります。 たとえば、更新については処理するが、挿入や削除については処理しない競合回避モジュールがあります。 既定の優先度に基づく競合回避モジュールでは、アーティクル競合回避モジュールで処理されない競合が処理されます。  
  
 マージ サブスクリプションの種類と競合解決の優先度を指定するには、「  
  
-   [!含める [ssManStudioFull] (../Token/ssManStudioFull_md.md)]: [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md)  
  
-   レプリケーション [!INCLUDE[tsql](../../../includes/tsql-md.md)] プログラミングおよびレプリケーション管理オブジェクト (RMO) プログラミング: [プル サブスクリプションを作成する](../../../relational-databases/replication/create-a-pull-subscription.md) と [プッシュ サブスクリプションを作成します。](../../../relational-databases/replication/create-a-push-subscription.md)  
  
### インタラクティブ競合回避モジュール  
 レプリケーションにはインタラクティブ競合回避モジュールのユーザー インターフェイスが用意されており、既定の優先度に基づく競合回避モジュールやアーティクル競合回避モジュールと併用できます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同期マネージャーを使用して要求時同期を実行すると、インタラクティブ競合回避モジュールに実行時の競合データが表示され、競合の解決方法を選択できます。 対話的な解決を有効にして、インタラクティブ競合回避モジュールを起動する方法の詳細については、次を参照してください。 [インタラクティブな競合解決](../../../relational-databases/replication/merge/interactive-conflict-resolution.md)します。  
  
## 競合の表示  
 競合を表示する最も簡単な方法はレプリケーション競合表示モジュールを使用することです。このモジュールは [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] から使用できます ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、競合テーブルに対してクエリを実行するためのストアド プロシージャも用意されています)。 競合表示モジュールはインタラクティブ競合回避モジュールに似たツールです。ただし、インタラクティブ競合回避モジュールが同期実行時の競合の解決に使用されるのに対し、競合表示モジュールは解決後の競合の表示を目的として設計されています。 競合メタデータがシステム テーブルでまだ利用可能な場合 (競合メタデータの既定の保持期間は 14 日間)、競合表示モジュールを使用して競合の解決結果を上書きできます。ただし、直接的な介入が定期的に必要となる場合は、インタラクティブ競合回避モジュールの使用を検討してください。  
  
> [!NOTE]  
>  論理レコードに関連する競合は、競合表示モジュールに表示されません。 これらの競合に関する情報を表示するには、レプリケーション ストアド プロシージャを使用します。 詳細については、次を参照してください [#40; (&)、マージ パブリケーションの競合情報の表示。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/view conflict information for merge publications.md)します。  
  
 競合表示モジュールには、次に示す 3 つのシステム テーブルの情報が表示されます。  
  
-   レプリケーションでは、テーブルごとに競合テーブルを作成、フォームの名前を持つ、マージ アーティクルで **msmerge_conflict _ \< PublicationName>_ \< ArticleName>**します。  
  
     競合テーブルには、基になるテーブルと同じ構造があります。 これらのテーブルの行は競合で優先されなかった行で構成されています (競合で優先された行は実際のユーザー テーブルにあります)。  
  
-    **MSmerge_conflicts_info** テーブルは、競合の種類など、個々 の競合に関する情報を提供します。  
  
-    **Sysmergearticles** テーブルを識別するユーザー テーブルの競合があるテーブルし、の競合テーブルに関する情報を提供します。  
  
 競合情報の既定の保存先は次のとおりです。  
  
-   パブリケーションの互換性レベルが 90 RTM 以上の場合は、パブリッシャーおよびサブスクライバーに保存されます。  
  
-   パブリケーションの互換性レベルが 80 RTM 未満の場合は、パブリッシャーに保存されます。  
  
-   サブスクライバーが [!INCLUDE[ssEW](../../../includes/ssew-md.md)] を実行している場合は、パブリッシャーに保存されます。 競合データは保管できません [!INCLUDE[ssEW](../../../includes/ssew-md.md)] サブスクライバーです。  
  
 **競合を表示するには**  
  
-   [!含める [ssManStudioFull] (../Token/ssManStudioFull_md.md)]: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   レプリケーション [!INCLUDE[tsql](../../../includes/tsql-md.md)] プログラミング: [#40; (&)、マージ パブリケーションの競合情報を表示レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/view conflict information for merge publications.md)  
  
## 参照  
 [データの同期](../../../relational-databases/replication/synchronize-data.md)  
  
  