---
title: "SharePoint ユーザー用のデータ警告マネージャー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "管理, 警告"
  - "管理, データ警告"
ms.assetid: 7b9281c8-2f8b-48f7-85d8-7a7a596e3c82
caps.latest.revision: 16
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 15
---
# SharePoint ユーザー用のデータ警告マネージャー
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のデータ警告マネージャーを使用して、SharePoint インフォメーション ワーカーはデータ警告を管理することができます。 具体的には、自分が作成した警告に関する情報を表示したり、警告を削除することができるほか、警告の定義を開いて編集したり、警告をオンデマンドで実行することができます。 1 つのレポートに対する警告のみを表示するか、すべてのレポートに対する警告を表示するかを選択することもできます。 次の図に、SharePoint インフォメーション ワーカーがデータ警告マネージャー内で使用できる機能を示します。  
  
 ![SharePoint ユーザー用の警告マネージャー機能](../reporting-services/media/rs-alertmanageriw.gif "SharePoint ユーザー用の警告マネージャー機能")  
  
 SharePoint サイトのデータ警告機能を有効にすると、MyDataAlerts.aspx と SiteDataAlerts.aspx という 2 つの SharePoint ページが作成されて、SharePoint サイトに追加されます。 MyDataAlerts.aspx は、SharePoint インフォメーション ワーカー用のデータ警告マネージャーです。 インフォメーション ワーカーは、警告を作成したレポートの右クリック メニューからデータ警告マネージャーを開くことができます。  
  
 URL を使用して直接データ警告マネージャーを開くこともできます。 URL の構文を次に示します。  
  
 `http://<site name>/_layouts/ReportServer/MyDataAlerts.aspx`  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の警告機能を使用するには、管理者から権限を割り当ててもらう必要があります。 必要な権限の詳細については、「[Reporting Services のデータ警告](../reporting-services/reporting-services-data-alerts.md)」を参照してください。  
  
##  <a name="ViewingAlerts"></a> データ警告情報の表示  
 データ警告デザイナーでは、自分が作成したデータ警告の一覧を表示できます。 データ警告マネージャーを開くには、SharePoint ライブラリにパブリッシュされたレポートを右クリックします。 次の図は、レポートの右クリック メニューに表示される **[データ警告の管理]** オプションを示しています。  
  
 ![レポート コンテキスト メニューから警告マネージャーを開く](../reporting-services/media/rs-openalertmanager.gif "レポート コンテキスト メニューから警告マネージャーを開く")  
  
 データ警告マネージャーには、警告名、レポート名、警告定義の作成者としての自分の名前、警告メッセージが送られた数、警告が最後に実行された時刻、警告の定義が最後に変更された時刻、および最新の警告メッセージの状態を一覧にしたテーブルが組み込まれています。 警告メッセージの生成や送信ができない場合は、エラーに関する情報が状態列に含まれているので、これを利用して警告のトラブルシューティングを行います。 詳細については、「[データ警告マネージャーでのデータ警告の管理](../reporting-services/manage-my-data-alerts-in-data-alert-manager.md)」を参照してください。  
  
 次の表は、データ警告マネージャー内のテーブルから取得されたサンプル データを示しています。 エラーが発生した場合は、エラー メッセージとログ内のエントリの識別子 (GUID) がテーブル内の **[状態]** フィールドに含められます。  
  
|警告名|[レポート名]|[作成者]|送信済みの警告|[最終実行]|更新日時|[状態]|  
|----------------|-----------------|----------------|-----------------|--------------|-------------------|------------|  
|SalesQTR|SalesByTerritoryAndQTR|Lauren Johnson|4|6/12/2011|6/1/2011|前回の警告が成功し、警告が送信されました。|  
|UnitsSold|ProductsSalesByQTR|Lauren Johnson|2|7/1/2011|6/28/2011|前回の警告は成功しましたが、データが変更されなかったため、警告は送信されませんでした。|  
|TopPromotion|PromotionTracking|Lauren Johnson|0||5/23/2011|警告が作成されました。|  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="DeleteAlerts"></a> データ警告の削除  
 警告の定義は、データ警告マネージャーから削除します。 インフォメーション ワーカーは、自分が作成した警告定義を削除できます。 他のユーザーによって作成された警告定義を削除することはできません。 詳細については、「[データ警告マネージャーでのデータ警告の管理](../reporting-services/manage-my-data-alerts-in-data-alert-manager.md)」を参照してください。  
  
 削除を行うと、その警告定義は完全に削除されます。 警告メッセージを一時停止したいだけの場合は、警告定義内で、定期実行パターンか、開始/終了日を変更してください。 詳細については、「[警告デザイナーでのデータ警告の編集](../reporting-services/edit-a-data-alert-in-alert-designer.md)」を参照してください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="EditAlerts"></a> データ警告の編集  
 インフォメーション ワーカーとして、データ警告マネージャーから警告定義を開きます。 自分が作成した警告定義は編集できますが、他のユーザーが作成した警告定義は編集できません。 警告定義を右クリックして **[編集]** をクリックすると、データ警告デザイナーが開き、警告定義が表示されます。 詳細については、「[データ警告デザイナー](../reporting-services/data-alert-designer.md)」および「[警告デザイナーでのデータ警告の編集](../reporting-services/edit-a-data-alert-in-alert-designer.md)」を参照してください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="RunAlerts"></a> データ警告の実行  
 データ警告マネージャーには、警告サービスがデータ警告定義を最後に処理した時刻と、データ警告メッセージが送信された回数に関する情報が含まれます。 必要な場合には、スケジュールによって指定された時刻を待たず、直ちに警告メッセージを実行および送信することもできます。 データ警告マネージャーから警告を実行すると、警告スケジュールが上書きされ、1 ～ 5 分以内に警告定義の処理が開始されます。これにかかる時間は、レポートの実行に必要な時間と、警告を実行するように選択した時点でのレポート サーバーのビジー状況によって左右されます。 ただし、結果が変更された場合にのみメッセージが送信されるように指定した場合、結果が変更されなければ、メッセージは作成も送信もされません。 詳細については、「[データ警告マネージャーでのデータ警告の管理](../reporting-services/manage-my-data-alerts-in-data-alert-manager.md)」を参照してください。  
  
> [!NOTE]  
>  **[実行]** オプションをクリックした後、**[状態]** 列の値が更新され、警告が処理中であることが示されるまでには数秒かかります。 **[実行]** オプションを複数回クリックすると、警告は複数回処理されます。 これを行うと、レポート サーバー上のリソースが不必要に消費され、レポート サーバーのパフォーマンスが低下することがあります。 警告に関する更新後の情報を参照するには、Web ブラウザーの更新ボタンをクリックして、状態の更新と、警告に関するその他の情報をチェックしてください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="HowTo"></a> 関連タスク  
 警告を管理し、警告の定義を編集する際の手順を紹介しているトピックの一覧を次に示します。  
  
-   [データ警告マネージャーでのデータ警告の管理](../reporting-services/manage-my-data-alerts-in-data-alert-manager.md)  
  
-   [警告デザイナーでのデータ警告の編集](../reporting-services/edit-a-data-alert-in-alert-designer.md)  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
## 参照  
 [データ警告デザイナー](../reporting-services/data-alert-designer.md)   
 [データ警告デザイナーでのデータ警告の作成](../reporting-services/create-a-data-alert-in-data-alert-designer.md)   
 [Reporting Services Data Alerts](../reporting-services/reporting-services-data-alerts.md)  
  
  