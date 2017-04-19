---
title: "トランザクションの注釈を設定する (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "注釈 [マスター データ サービス]、トランザクション用"
ms.assetid: f5a6b2ca-56de-4e42-9da8-fba0ac3e8d92
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# トランザクションの注釈を設定する (Master Data Services)
  履歴を参照する目的でトランザクションの詳細をサポートする場合、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] でトランザクションの注釈を設定します。  
  
> [!NOTE]  
>  注釈は削除できません。  
  
## 前提条件  
  
-   作成したトランザクションの注釈を設定するためには、**[エクスプローラー]** 機能領域へのアクセス権限と、注釈を設定するモデル オブジェクトに対する**更新**権限が最低限必要です。  
  
-   すべてのユーザーのトランザクションの注釈を設定するためには、**[バージョン管理]** 機能領域へのアクセス権限を持っているモデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### [エクスプローラー] でトランザクションの注釈を設定するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
2.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
3.  **[エクスプローラー]**をクリックします。  
  
4.  メニュー バーの **[エンティティ]** をポイントして、注釈を設定するトランザクションを持つメンバーを含むエンティティの名前をクリックします。  
  
5.  グリッドで、メンバーの行をクリックします。  
  
6.  **[トランザクションの表示]** をクリックします。  
  
7.  **[トランザクションの表示]** ダイアログ ボックスで、注釈を設定するトランザクションをクリックします。  
  
8.  ダイアログ ボックスの下部にあるボックスに、注釈を入力します。  
  
9. **[注釈の追加]** をクリックします。 **[注釈]** ペインに注釈が表示されます。  
  
### [バージョン管理] でトランザクションに注釈を設定する (管理者のみ)  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ホーム ページで、**[バージョン管理]** をクリックします。  
  
2.  メニュー バーの **[トランザクション]** をクリックします。  
  
3.  **[トランザクション]** ペインで、注釈を設定するトランザクションのグリッド内の行をクリックします。  
  
4.  **[トランザクションの注釈]** ペインの **[注釈]** ボックスに注釈を入力します。  
  
5.  **[OK]**をクリックします。  
  
## 参照  
 [注釈 (マスター データ サービス)](../master-data-services/annotations-master-data-services.md)   
 [トランザクション (マスター データ サービス)](../master-data-services/transactions-master-data-services.md)  
  
  