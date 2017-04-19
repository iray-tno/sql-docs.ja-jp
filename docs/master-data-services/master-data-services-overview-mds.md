---
title: "マスター データ サービスの概要 (MDS) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "マスター データとは"
helpviewer_keywords: 
  - "マスター データ サービス、概要"
  - "マスター データ サービス"
ms.assetid: 8a4c28b1-6061-4850-80b6-132438b8c156
caps.latest.revision: 28
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 27
---
# マスター データ サービスの概要 (MDS)
  このトピックでは、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のデータ編成と管理機能について説明します。 
  
 >  [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] アーキテクチャの説明については、simple-talk.com の記事「[Master Data Services -- The Basics](https://www.simple-talk.com/sql/database-delivery/master-data-services-basics)」 (マスター データ サービス -- 基本) を参照してください。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の新機能については、「[マスター データ サービス (MDS) の新機能](../master-data-services/what-s-new-in-master-data-services-mds.md)」を参照してください。  
   **[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のインストール、データベースと Web サイトのセットアップ、サンプル モデルの展開の手順については、**「[マスター データ サービスのイントールと構成](../master-data-services/master-data-services-installation-and-configuration.md)」を参照してください。  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、モデルはマスター データ構造の最上位のコンテナーです。 モデルを作成すると、類似したデータのグループを管理できます。たとえば、オンラインの製品データを管理するなどです。 モデルには 1 つ以上のエンティティが含まれています。エンティティにはメンバーが含まれており、これはデータ レコードです。 エンティティはテーブルに似ています。  
  
 たとえば、オンラインの製品モデルには、Product、Color、Style などのエンティティが含まれていることがあります。 Color エンティティには、赤、シルバー、黒の色のメンバーを含めることができます。  
  
 ![Color entity](../master-data-services/media/mds-productmodel-colorentity-composite.png "Color entity")  
  
 またモデルには、エンティティ内で定義されている属性も含まれます。 属性には、エンティティ メンバーを記述するのに役立つ値が含まれています。 自由形式属性とドメインベースの属性があります。  ドメインベースの属性には、あるエンティティのメンバーによって設定され、その他のエンティティの属性値として使用できる値が含まれます。  
  
 たとえば、Product エンティティには、Cost と Weight の自由形式属性を含めることができます。 また、Color エンティティ メンバーによって設定された値を含む、色 ![Number 1](../master-data-services/media/mds-number1.png "Number 1") を表すドメインベースの属性もあります。 この色のマスター リストは、Product エンティティ ![Number 2](../master-data-services/media/mds-number2.png "Number 2") の属性値として使用できます。  
  
 ![Domain-based attribute for color](../master-data-services/media/mds-productentity-color-domainattribute.png "Domain-based attribute for color")  
  
 派生階層は、モデル内のエンティティ間のリレーションシップから取得されます。 これらは、ドメインベースの属性リレーションシップです。 たとえば、Product モデルは、Color ![Number 2](../master-data-services/media/mds-number2.png "Number 2") エンティティと Product ![Number 3](../master-data-services/media/mds-number3.png "Number 3") エンティティ間のリレーションシップから取得される色の派生階層 ![Number 1](../master-data-services/media/mds-number1.png "Number 1") を持つ場合があります。  
  
 ![Color derived hierarchy](../master-data-services/media/mds-derivedhierarchy.png "Color derived hierarchy")  
  
 データの基本的な構造を定義したら、インポート機能を使用してデータ レコード (メンバー) の追加を開始できます。 ステージング テーブルにデータを読み込み、ビジネス ルールを使用してデータを検証して、MDS テーブルにデータを読み込みます。  また、属性の値を設定するのにビジネス ルールを使用することもできます。  
  
 次の表に主要な [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] タスクの概要を示します。 特に指定がない限り、次のすべての手順を実行するにはモデル管理者であることが必要です。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
> [!NOTE]  
>  テスト環境で次のタスクを実行し、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のインストール時に提供されたサンプル データを使用できます。 詳細については、「[モデルの配置 (マスター データ サービス)](../master-data-services/deploying-models-master-data-services.md)」を参照してください。  
  
|操作|詳細|関連項目|  
|------------|-------------|--------------------|  
|モデルを作成する|モデルを作成すると、そのモデルが VERSION_1 と見なされます。|[モデル (マスター データ サービス)](../master-data-services/models-master-data-services.md)<br /><br /> [モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)|  
|エンティティを作成する|メンバーを含めるためにエンティティを必要な数だけ作成します。|[エンティティ (マスター データ サービス)](../master-data-services/entities-master-data-services.md)<br /><br /> [エンティティを作成する (マスター データ サービス)](../master-data-services/create-an-entity-master-data-services.md)|  
|ドメイン ベースの属性として使用するエンティティを作成する|ドメイン ベースの属性を作成するには、まず属性値の一覧を設定するエンティティを作成します。|[ドメインベースの属性 (マスター データ サービス)](../master-data-services/domain-based-attributes-master-data-services.md)<br /><br /> [ドメイン ベースの属性を作成する (マスター データ サービス)](../master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|エンティティの属性を作成する|メンバーを表す属性を作成します。 各エンティティには Name 属性と Code 属性が自動的に含まれます。これらの属性は削除できません。 テキスト、日付、数値、またはファイルを含む他の自由形式の属性を作成できます。|[属性 (マスター データ サービス)](../master-data-services/attributes-master-data-services.md)<br /><br /> [テキスト属性を作成する (マスター データ サービス)](../master-data-services/create-a-text-attribute-master-data-services.md)<br /><br /> [数値属性を作成する (マスター データ サービス)](../master-data-services/create-a-numeric-attribute-master-data-services.md)<br /><br /> [日付属性を作成する (マスター データ サービス)](../master-data-services/create-a-date-attribute-master-data-services.md)<br /><br /> [リンク属性を作成する (マスター データ サービス)](../master-data-services/create-a-link-attribute-master-data-services.md)<br /><br /> [ファイル属性を作成する (マスター データ サービス)](../master-data-services/create-a-file-attribute-master-data-services.md)|  
|属性グループを作成する|エンティティに 4 つまたは 5 つ以上の属性がある場合は、属性グループを作成できます。 これらのグループは、 **[エクスプローラー]** のグリッド上に表示されるタブに対応します。各タブに属性をグループ化することにより、移動が容易になります。|[属性グループ (マスター データ サービス)](../master-data-services/attribute-groups-master-data-services.md)<br /><br /> [属性グループを作成する (マスター データ サービス)](../master-data-services/create-an-attribute-group-master-data-services.md)|  
|サポート エンティティのメンバーをインポートする|ステージング処理を使用して、サポート エンティティのデータをインポートします。 Product モデルの場合は、色やサイズをインポートすることを意味します。 手動でメンバーを作成することもできます。<br /><br /> <br /><br /> 注: ユーザーに最低でもエンティティのリーフ モデル オブジェクトに対する [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 更新 **権限があり、** [エクスプローラー] **機能領域にアクセスできる場合は、** でメンバーを作成できます。|[概要: テーブルからデータをインポートする (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)<br /><br /> [リーフ メンバーを作成する (マスター データ サービス)](../master-data-services/create-a-leaf-member-master-data-services.md)|  
|データ品質を保証するビジネス ルールの作成および適用|データの精度を保証するためにビジネス ルールを作成してパブリッシュします。 ビジネス ルールを使用すると、次のことが可能になります。<br /><br /> 既定の属性値を設定する。<br /><br /> 属性値を変更する。<br /><br /> データがビジネス ルール検証に合格しなかったときに、電子メール通知を送信する。|[ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)<br /><br /> [ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)<br /><br /> [ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)<br /><br /> [電子メール通知を構成する (マスター データ サービス)](../master-data-services/configure-email-notifications-master-data-services.md)<br /><br /> [通知を送信するようにビジネス ルールを構成する (マスター データ サービス)](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|プライマリ エンティティのメンバーをインポートし、ビジネス ルールを適用する|ステージング処理を使用してプライマリ エンティティのメンバーをインポートします。 インポートが完了したら、バージョンを検証することにより、モデル バージョン内のすべてのメンバーにビジネス ルールが適用されます。<br /><br /> 次に、ビジネス ルール検証に問題があれば修正します。|[検証 (マスター データ サービス)](../master-data-services/validation-master-data-services.md)<br /><br /> [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)<br /><br /> [検証ストアド プロシージャ (マスター データ サービス)](../master-data-services/validation-stored-procedure-master-data-services.md)|  
|派生階層を作成する|派生階層は、ビジネス ニーズの変化に応じて更新でき、すべてのメンバーを適切なレベルで記述するようにします。|[派生階層 (マスター データ サービス)](../master-data-services/derived-hierarchies-master-data-services.md)<br /><br /> [派生階層を作成する (マスター データ サービス)](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|必要に応じて、明示的階層を作成する|レベル ベースではなく、単一のエンティティのメンバーを含む階層を作成する場合に、明示的階層を作成できます。|[明示的階層 (マスター データ サービス)](../master-data-services/explicit-hierarchies-master-data-services.md)<br /><br /> [明示的階層を作成する (マスター データ サービス)](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|必要に応じて、コレクションを作成します。|レポートまたは分析のためにメンバーのさまざまなグループを表示する場合で、完全な階層を必要としないときは、コレクションを作成します。<br /><br /> <br /><br /> 注: ユーザーに最低でもコレクション モデル オブジェクトに対する [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 更新 **権限があり、** [エクスプローラー] **機能領域にアクセスできる場合は、** でコレクションを作成できます。|[コレクション (マスター データ サービス)](../master-data-services/collections-master-data-services.md)<br /><br /> [コレクションを作成する (マスター データ サービス)](../master-data-services/create-a-collection-master-data-services.md)|  
|ユーザー定義メタデータを作成する|モデル オブジェクトを記述するには、モデルにユーザー定義メタデータを追加します。 メタデータには、オブジェクトの所有者やデータ ソースを含めることができます。|[メタデータ (マスター データ サービス)](../Topic/Metadata%20\(Master%20Data%20Services\).md)|  
|モデルのバージョンをロックし、バージョン フラグを割り当てる|モデルのバージョンをロックして、管理者以外のユーザーがメンバーに対する変更を実行できないようにします。 ビジネス ルールに対するバージョンのデータ検証が正常に完了したら、バージョンをコミットできます。これにより、すべてのユーザーがメンバーに対する変更を実行できなくなります。<br /><br /> バージョン フラグを作成してモデルに割り当てます。 フラグによって、ユーザーおよびサブスクライブ システムは使用するモデルのバージョンを識別できます。|[バージョン (マスター データ サービス)](../master-data-services/versions-master-data-services.md)<br /><br /> [バージョンをロックする (マスター データ サービス)](../master-data-services/lock-a-version-master-data-services.md)<br /><br /> [バージョン フラグを作成する (マスター データ サービス)](../master-data-services/create-a-version-flag-master-data-services.md)|  
|サブスクリプション ビューを作成する|サブスクライブ システムでマスター データを使用するために、サブスクリプション ビューを作成します。これにより、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに標準ビューが作成されます。|[概要: データのエクスポート (マスター データ サービス)](../master-data-services/overview-exporting-data-master-data-services.md)<br /><br /> [サブスクリプション ビューを作成してデータをエクスポートする (マスター データ サービス)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|ユーザー権限とグループ権限を構成する|ユーザー権限とグループ権限は、テスト環境から運用環境にコピーできません。 ただし、運用環境で最終的に使用するセキュリティを決定するために、テスト環境を使用できます。|[セキュリティ (マスター データ サービス)](../master-data-services/security-master-data-services.md)<br /><br /> [グループを追加する (マスター データ サービス)](../master-data-services/add-a-group-master-data-services.md)<br /><br /> [ユーザーを追加する (マスター データ サービス)](../master-data-services/add-a-user-master-data-services.md)|  
  
 準備ができたら、データの有無に関係なく、運用環境にモデルを配置できます。 詳細については、「[モデルの配置 (マスター データ サービス)](../master-data-services/deploying-models-master-data-services.md)」を参照してください。  
  
  