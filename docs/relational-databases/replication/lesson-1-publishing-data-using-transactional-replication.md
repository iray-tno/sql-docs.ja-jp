---
title: "レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "レプリケーション [SQL Server], チュートリアル"
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ
このレッスンでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してトランザクション パブリケーションを作成し、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの **Product** テーブルからフィルター選択したサブセットをパブリッシュします。 また、ディストリビューション エージェントにより使用される SQL Server ログインをパブリケーション アクセス リスト (PAL) に追加します。 このチュートリアルを行うには、前のチュートリアル「[レプリケーションに備えたサーバーの準備](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。  
  
### パブリケーションを作成し、アーティクルを定義するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、**[ローカル パブリケーション]** フォルダーを右クリックして、**[新しいパブリケーション]** をクリックします。  
  
    パブリケーションの新規作成ウィザードが起動します。  
  
3.  [パブリケーション データベース] ページで [[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] を選択し、**[次へ]** をクリックします。  
  
4.  [パブリケーションの種類] ページで **[トランザクション パブリケーション]** を選択し、**[次へ]** をクリックします。  
  
5.  [アーティクル] ページで、**[テーブル]** ノードを展開して **[Product]** チェック ボックスをオンにします。次に、**[Product]** を展開して、**[ListPrice]** チェック ボックスと **[StandardCost]** チェック ボックスをオフにします。 **[次へ]**をクリックします。  
  
6.  [テーブル行のフィルター選択] ページで、**[追加]** をクリックします。  
  
7.  **[フィルターの追加]** ダイアログ ボックスで **[SafetyStockLevel]** 列をクリックし、右矢印をクリックして、フィルター選択クエリの Filter ステートメントの WHERE 句にこの列を追加します。さらに、WHERE 句を次のように変更します。  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  **[OK]** をクリックし、**[次へ]** をクリックします。  
  
9. **[スナップショットをすぐに作成し、サブスクリプションを初期化できるようにそのスナップショットを保持する]** チェック ボックスをオンにして、**[次へ]** をクリックします。  
  
10. [エージェント セキュリティ] ページで、**[スナップショット エージェントのセキュリティ設定を使用する]** チェック ボックスをオフにします。  
  
11. スナップショット エージェントの **[セキュリティ設定]** をクリックして、**[プロセス アカウント]** ボックスに「\<*コンピューター名>***\repl_snapshot**」と入力し、このアカウントのパスワードを入力して **[OK]** をクリックします。  
  
12. 同様に、ログ リーダー エージェントのプロセス アカウントとして repl_logreader を設定し、**[完了]** をクリックします。  
  
13. [ウィザードの完了] ページで、**[パブリケーション名]** ボックスに「**AdvWorksProductTrans**」と入力し、**[完了]** をクリックします。  
  
14. パブリケーションが作成されたら、**[閉じる]** をクリックしてウィザードを閉じます。  
  
### スナップショット生成の状態を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でパブリッシャーに接続して、サーバー ノードを展開し、**[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、**[AdvWorksProductTrans]** を右クリックして、**[スナップショット エージェントの状態の表示]** をクリックします。  
  
3.  パブリケーションのスナップショット エージェントの現在の状態が表示されるので、 スナップショット ジョブが正常に終了していることを確認してから次のレッスンに進みます。  
  
### ディストリビューション エージェントのログインを PAL に追加するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でパブリッシャーに接続して、サーバー ノードを展開し、**[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、**[AdvWorksProductTrans]** パブリケーションを右クリックして、**[プロパティ]** をクリックします。  
  
    **[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **[パブリケーション アクセス リスト]** ページを選択して、**[追加]** をクリックします。  
  
4.  **[パブリケーション アクセスの追加]** ダイアログ ボックスで、*\<コンピューター名>***\repl_distribution** を選択して **[OK]** をクリックし、 **[OK]**をクリックします。  
  
## 次の手順  
ここでは、トランザクション パブリケーションを作成しました。 次は、このパブリケーションをサブスクライブします。 「[レッスン 2: トランザクション パブリケーションへのサブスクリプションの作成](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md)」を参照してください。  
  
## 参照  
[パブリッシュされたデータのフィルター選択](../../relational-databases/replication/publish/filter-published-data.md)  
[Define an Article](../../relational-databases/replication/publish/define-an-article.md)  
[スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-snapshot.md)  
  
  
  