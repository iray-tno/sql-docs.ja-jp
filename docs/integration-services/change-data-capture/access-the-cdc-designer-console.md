---
title: CDC デザイナー コンソールへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: change-data-capture
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- accMsDes
ms.assetid: b168c64e-c1b5-42d4-a92a-84de1dd0324e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: af7ed11a4e927a45764cc726287bf7cff949c45b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="access-the-cdc-designer-console"></a>CDC デザイナー コンソールへのアクセス
  CDC デザイナー コンソールには、コンソールをインストールしたコンピューターからアクセスすることができます。 インストールの詳細については、インストールを参照してください。  
  
 CDC デザイナー コンソールを開くと、[SQL Server への接続] ダイアログ ボックスが表示されます。  
  
 CDC デザイナーにアクセスする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインには、MSXDBCDC データベースに対する UPDATE 権限が必要です。 また、新しい Oracle CDC インスタンスを作成するには、ログインが `dbcreator` 固定サーバー ロールを持っている必要もあります。 また、使用する CDC データベースへの SELECT アクセス権がログインに含まれていることも推奨されます。このアクセス権が含まれていない場合、ユーザーはそれらのデータベースの状態を表示できません。  
  
 [SQL Server への接続] ダイアログ ボックスに次の情報を入力します。  
  
### <a name="server-name"></a>[サーバー名]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。  
  
### <a name="authentication"></a>[認証]  
 次のいずれかを選択します。  
  
-   **[Windows 認証]**  
  
-   **[SQL Server 認証]**: このオプションを選択する場合、接続先の **のユーザーの** [ログイン] **と** [パスワード] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を入力する必要があります。  
  
 ログインには、MSXCDCDB データベースへのアクセスを許可するデータベース ロールが必要です。 また、使用する追加のデータベースへのアクセスがログインに含まれていることも推奨されます。このアクセスが含まれていない場合、ユーザーはそれらのデータベース内のデータを表示できません。  
  
### <a name="options"></a>および  
 矢印をクリックして、構成するオプションを表示します。 これらのオプションを既定値のままにすることもできます。 使用可能なオプションは次のとおりです。  
  
 **[接続タイムアウト]**  
 CDC Service for Oracle が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は **15**です。  
  
 **[実行タイムアウト]**  
 Oracle CDC Windows Service がコマンドの実行を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は、 **30**です。  
  
 **[暗号化接続]**  
 Oracle CDC Service とターゲットの **インスタンスの間の暗号化された接続を使用した通信に対しては、** [暗号化接続] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択します。**[詳細設定]**: 必要に応じて、 **[詳細設定]** をクリックし、[高度な接続プロパティ] ダイアログ ボックスに追加の接続プロパティを入力します。  
  
 **詳細設定**  
 必要に応じて、 **[詳細設定]** をクリックし、[高度な接続プロパティ] ダイアログ ボックスに追加の接続プロパティを入力します。  
  
 [高度な接続プロパティ] ダイアログ ボックスの詳細については、「 [高度な接続プロパティ](../../integration-services/change-data-capture/advanced-connection-properties.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CDC デザイナーで使用する SQL Server 接続に必要な権限](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
