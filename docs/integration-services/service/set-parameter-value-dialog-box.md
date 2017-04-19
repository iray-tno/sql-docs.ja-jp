---
title: "[パラメーター値の設定] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# [パラメーター値の設定] ダイアログ ボックス
  プロジェクトとパッケージのパラメーターと接続マネージャーのプロパティの値を設定するには、**[パラメーター値の設定]** ダイアログ ボックスを使用します。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [[パラメーター値の設定] ダイアログ ボックスを開く](#open_dialog)  
  
-   [オプションの構成](#option)  
  
##  <a name="open_dialog"></a> [パラメーター値の設定] ダイアログ ボックスを開く  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。  
  
     SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。  
  
2.  オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。  
  
3.  **[SSISDB]** ノードを展開します。  
  
4.  パッケージまたはプロジェクトを右クリックして **[構成]** をクリックし、**[パラメーター]** タブまたは **[接続マネージャー]** タブの参照ボタンをクリックします。  
  
##  <a name="option"></a> オプションの構成  
 **パラメーター**  
 パラメーター名を一覧表示します。  
  
 **型**  
 パラメーター値のデータ型を一覧表示します。  
  
 **Description**  
 パラメーターのオプションの説明を表示します。  
  
 **値の編集**  
 パラメーター値を編集する場合に選択します。  
  
 **パッケージの既定値を使用する**  
 パッケージに保存されている既定のパラメーター値を使用する場合に選択します。  
  
 **環境変数を使用する**  
 環境に保存されている変数値を使用する場合に選択します。この変数値はプロジェクトまたはパッケージによって参照されます。 環境参照をプロジェクトまたはパッケージに追加するには、**[構成]** ダイアログ ボックスを使用します。 詳細については、「[[構成] ダイアログ ボックス](../Topic/Configure%20Dialog%20Box.md)」を参照してください。  
  
  