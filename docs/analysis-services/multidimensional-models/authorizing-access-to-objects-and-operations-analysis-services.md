---
title: "オブジェクトと操作へのアクセスの承認 (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.roledesignerdialog.general.f1"
  - "sql13.asvs.roledesignerdialog.membership.f1"
helpviewer_keywords: 
  - "アクセス権 [Analysis Services], ユーザー"
  - "権限 [Analysis Services], ユーザー"
  - "セキュリティ [Analysis Services], ユーザー アクセス"
  - "ユーザー アクセス権 [Analysis Services]"
  - "権限の付与 [Analysis Services], ユーザー"
ms.assetid: af28524e-5eca-4dce-a050-da4f406ee1c7
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 35
---
# オブジェクトと操作へのアクセスの承認 (Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内のキューブ、ディメンション、マイニング モデルへの管理者以外のユーザー アクセスは、1 つ以上のデータベース ロールのメンバーシップにより許可されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理者は、これらのデータベース ロールを作成し、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトに対する読み取り権限または読み取り/書き込み権限を与え、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のユーザーとグループを各ロールに割り当てます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、ユーザーまたはグループが属している各データベース ロールに関連付けられている権限を組み合わせて、特定の Windows ユーザーまたはグループに有効な権限を判断します。 その結果、1 つのデータベース ロールでディメンション、メジャー、または属性を表示するためのユーザーまたはグループ権限を付与していなくても、別のデータベース ロールでそのユーザーまたはグループ権限を付与している場合、そのユーザーまたはグループにはオブジェクトを表示する権限が与えられます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー管理者ロールのメンバーと、フル コントロール (管理者) 権限を持つデータベース ロールのメンバーは、データベースのデータとメタデータすべてにアクセスでき、特定のオブジェクトを表示するのにその他の権限を必要としません。 さらに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー ロールのメンバーに対してデータベースのオブジェクトへのアクセスを拒否することはできず、データベース内でフル コントロール (管理者) 権限を持つ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース ロールのメンバーに対してそのデータベース内のオブジェクトへのアクセスを拒否することもできません。 処理などの特殊な管理操作は、より権限の少ない別のロールを通じて承認されます。 詳細については、「[処理権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)」を参照してください。  
  
## データベースに対して定義されたロールの一覧表示  
 管理者は、SQL Server Management Studio から簡単な DMV クエリを実行することにより、サーバー上で定義されたすべてのロールの一覧を取得できます。  
  
1.  SSMS でデータベースを右クリックし、**[新しいクエリ]**、**[MDX]** の順に選択します。  
  
2.  次のクエリを入力し、F5 キーを押して実行します。  
  
    ```  
    Select * from $SYSTEM.DBSCHEMA_CATALOGS  
    ```  
  
     結果には、データベース名、説明、ロール名、最終更新日が含まれます。 この情報を開始位置として使用することにより、個々のデータベースに進んで特定のロールのメンバーシップと権限を確認できます。  
  
## Analysis Services の承認に関するトップダウンの概要  
 ここでは、権限の構成に関する基本的なワークフローについて説明します。  
  
 **手順 1: サーバーの管理**  
  
 最初の手順として、サーバー レベルで管理者権限を持つユーザーを決定します。 SQL Server をインストールするローカル管理者は、インストール時に、Analysis Services サーバー管理者として Windows アカウントを 1 つ以上指定するよう求められます。 サーバー管理者には、サーバー上の可能な権限がすべて付与されています。これには、サーバー上の任意のオブジェクトを表示、変更、削除したり、関連付けられているデータを表示したりする権限が含まれます。 インストールが完了したら、サーバー管理者は、アカウントを追加または削除してこのロールのメンバーシップを変更できます。 この権限レベルの詳細については、「[Analysis Services インスタンスにサーバー管理者権限を付与する](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)」を参照してください。  
  
 **手順 2: データベースの管理**  
  
 次に、テーブルまたは多次元ソリューションが作成されたら、データベースとしてサーバーに配置されます。 サーバー管理者は、問題のあるデータベースに対してフル コントロール権限を持つロールを定義することにより、データベース管理タスクを委任できます。 このロールのメンバーは、データベース内のオブジェクトを処理または照会したり、キューブ、ディメンション、およびデータベース自体にある他のオブジェクトにアクセスするために追加のロールを作成したりできます。 詳細については、「[データベース権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)」を参照してください。  
  
 **手順 3: クエリと処理のワークロードへのキューブ アクセスまたはモデル アクセスの有効化**  
  
 既定では、キューブまたはテーブル モデルにアクセスできるのは、サーバー管理者とデータベース管理者だけです。 組織内の他のユーザーがこれらのデータ構造を使用できるようにするには、**読み取り**特権を指定する権限と共に、Windows ユーザーおよびグループ アカウントを、キューブまたはモデルにマップするための追加のロール割り当てが必要です。 詳細については、「[キューブ権限またはモデル権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)」を参照してください。  
  
 処理タスクを他の管理機能と分離することにより、サーバー管理者およびデータベース管理者がこのタスクを他のユーザーに委任したり、スケジュール ソフトウェアを実行するサービス アカウントを指定することによって自動処理を構成したりできるようになります。 詳細については、「[処理権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)」を参照してください。  
  
> [!NOTE]  
>  ユーザーは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータ読み込み元である、基になるリレーショナル データベースのリレーショナル テーブルへの権限は必要とせず、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを実行しているコンピューターでのファイル レベルの権限も必要としません。  
  
 **手順 4 (省略可): 内部キューブ オブジェクトへのアクセスの許可または拒否**  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、データ モデル内のディメンション メンバーおよびセルを含む、個別のオブジェクトの設定権限のセキュリティ設定を提供します。 詳細については、「[ディメンション データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)」および「[セル データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)」を参照してください。  
  
 権限は、ユーザー ID によって異なります。 これは動的なセキュリティと呼ばれ、[UserName &#40;MDX&#41;](../../mdx/username-mdx.md) 関数を使用して実装されます。  
  
## ベスト プラクティス  
 権限のより優れた管理のために、次のような方法が推奨されます。  
  
1.  ロールを保守するユーザーが、ロールの機能を一目でわかるように、関数ごと (dbadmin、cubedeveloper、processadmin など) にロールを作成します。 他の場所でも示されているように、モデル定義でロールを定義できるため、後のソリューションの配置よりそれらのロールを保持することが優先されます。  
  
2.  対応する Windows セキュリティ グループを Active Directory に作成し、そのセキュリティ グループを Active Directory に保持することにより、適切な個々のアカウントが確実に含まれるようにします。 これにより、組織内のアカウント メンテナンスに使用されるツールおよび処理を既に使いこなしているセキュリティ スペシャリストが、セキュリティ グループ メンバーシップの責任を負うことになります。  
  
3.  モデルがそのソース ファイルからサーバーに再配置された場合にはすばやくロールの割り当てをレプリケートできるように、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にスクリプトを生成します。 スクリプトをすばやく生成する方法の詳細については、「[キューブ権限またはモデル権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)」を参照してください。  
  
4.  ロールのスコープとメンバーシップを反映する名前付け規則を採用します。 ロール名は、デザイン ツールおよび管理ツールにのみ表示されるため、キューブ セキュリティ スペシャリストにとって理解しやすい名前付け規則を使用してください。 たとえば、**processadmin-windowsgroup1** は、個々の Windows ユーザー アカウントが **windowsgroup1** セキュリティ グループのメンバーである組織内のユーザーに対して、読み取りアクセスおよび処理権限を示します。  
  
     アカウント情報を含めることは、多数のロールで使用されているアカウントを追跡するのに役立ちます。 ロールは追加式のため、**windowsgroup1** に関連付けられている結合されたロールは、そのセキュリティ グループに所属するユーザーにとって有効な権限セットを構成します。  
  
5.  開発中、キューブ開発者はモデルおよびデータベースのフル コントロール権限を必要としますが、一度データベースが実稼働サーバーにロールアウトされると、必要とされるのは読み込み権限のみです。 開発、テスト、および運用環境の配置を含むすべてのシナリオに対してロールの定義と割り当てを開発してください。  
  
 このような方法を使用すると、モデル内のロールの定義とメンバーシップへの動きを最小限にし、ロールの割り当てに可視性が加わるため、キューブ権限の実装および保持が簡単になります。  
  
## 参照  
 [Analysis Services インスタンスにサーバー管理者権限を付与する](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [ロールと権限 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)   
 [Analysis Services でサポートされる認証方法](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)  
  
  