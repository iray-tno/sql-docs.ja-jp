---
title: "検証 (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 12
---
# 検証 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、データを検証してその精度を保証します。 一部の検証は自動的に行われますが、それ以外の検証は管理者が作成するビジネス ルールに基づきます。  
  
## データ検証の実行タイミング  
 検証は異なるタイミングで行われ、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web アプリケーションに別々に表示されます。  
  
|検証の種類|決定基準|実行タイミング|マスター データ マネージャー Web UI での表示|Excel 用アドインでの表示|MDS リポジトリにデータが保存されるかどうか|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|ビジネス ルールの検証|MDS 管理者|ユーザーがデータを追加または編集するときは、自動<br /><br /> ユーザーがビジネス ルールを適用するときは、手動<br /><br /> **Web アプリケーションの** [バージョン管理] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 機能領域の管理者がビジネス ルールに対してバージョンを検証するときは、手動|検証エラー|ValidationStatus|可|  
|データ型およびコンテンツの検証|モデル オブジェクトの (属性の長さやデータ型など) を作成するときは、MDS 管理者|ユーザーがデータを追加または編集するときは、自動|入力エラー|InputStatus|いいえ|  
|データ型およびコンテンツの検証|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] または [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|ユーザーがデータを追加または編集するときは、自動|入力エラー|InputStatus|いいえ|  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|データを検証するために、ビジネス ルールを作成してパブリッシュする。|[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|ビジネス ルールに対してデータのバージョンを検証する (管理者のみ)。|[ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|ビジネス ルールに対してデータの特定のサブセットを検証する ( **[エクスプローラー]** 機能領域への権限があるすべてのユーザー)。|[ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|ビジネス ルールに対してデータの特定のサブセットを検証する ( **[エクスプローラー]** 機能領域への権限があり、 [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]を使用するすべてのユーザー)。|[ビジネス ルールの適用 (Excel 用 MDS アドイン)](../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## 参照  
 [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)  
  
  