---
title: "SQL Server のローカル言語版 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20b99363-0490-4aa3-9a3d-262f827d81e8
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# SQL Server のローカル言語版
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Windows オペレーティング システムでサポートされているすべての言語がサポートされています。  
  
## 言語間サポート  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の英語版は、オペレーティング システムのすべてのローカライズ版で実行できます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ版は、対応する言語にローカライズされたオペレーティング システム、または Windows Multilingual User Interface Pack (MUI) 設定を使用することにより、サポートされているオペレーティング システムの英語版でも実行できます。 詳しくは、「 [Configure Operating System to Support Localized Versions](../../sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS)」をご覧ください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ版は、同じ言語のローカライズ版にのみアップグレードでき、英語版にはアップグレードできません。  
  
-   また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ版は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の英語インスタンスとサイド バイ サイドでインストールできます。  
  
##  <a name="BK_ConfigureOS"></a> ローカライズ バージョンのサポートのためのオペレーティング システムの構成  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各言語のバージョンは、Windows Multilingual User Interface Pack (MUI) 設定を使用することにより、サポートされているオペレーティング システムの英語バージョン上でサポートされます。  
  
 ただし、英語以外の MUI 設定を持つ英語オペレーティング システムを実行しているサーバーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ バージョンをインストールする場合は、事前にオペレーティング システムのいくつかの設定を確認する必要があります。 以下のオペレーティング システム設定が、インストールする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ローカライズ バージョンの言語に一致していることを確認する必要があります。  
  
-   オペレーティング システムのユーザー インターフェイス設定  
  
-   オペレーティング システムのユーザー ロケール設定  
  
-   システム ロケール設定  
  
 この設定と、インストールする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ローカライズ バージョンの言語が一致しない場合は、以下の手順に従ってオペレーティング システムの設定を正しく指定してください。  
  
> [!CAUTION]  
>  異なる言語バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを、同じコンピューターにインストールすることはサポートされていません。  
  
#### オペレーティング システムのユーザー インターフェイス設定を変更するには  
  
1.  ローカライズ バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に一致するオペレーティング システム MUI がインストールされていない場合は、インストールします。  
  
2.  コントロール パネルで **[地域と言語のオプション]**を開きます。  
  
3.  **[言語]** タブで、 **[メニューとダイアログで使われる言語]**ボックスの一覧から言語を選択します。  
  
     この設定は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のユーザー インターフェイス言語に影響を及ぼします。したがって、ローカライズ バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と一致している必要があります。  
  
4.  **[適用]** をクリックして変更を確認し、 **[OK]** をクリックしてウィンドウを閉じます。  
  
#### オペレーティング システムのユーザー ロケール設定を変更するには  
  
1.  ローカライズ バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に一致するオペレーティング システム MUI がインストールされていない場合は、インストールします。  
  
2.  コントロール パネルで **[地域と言語のオプション]**を開きます。  
  
3.  **[地域オプション]** タブの **[使う言語を選び、必要に応じてカスタマイズをクリックして希望する形式を選択してください:]**ボックスで、一覧から言語を選択します。  
  
     この設定は、カルチャに特有なデータの書式に影響を及ぼします。  
  
4.  **[適用]** をクリックして変更を確認し、 **[OK]** をクリックしてウィンドウを閉じます。  
  
#### システムのロケール設定を変更するには  
  
1.  ローカライズ バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に一致するオペレーティング システム MUI がインストールされていない場合は、インストールします。  
  
2.  コントロール パネルで **[地域と言語のオプション]**を開きます。  
  
3.  **[詳細設定]** タブの **[使う Unicode 対応でないプログラムの言語バージョンに一致する言語を選んでください]** で、一覧から言語を選択します。  
  
     この設定により、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールに最適な既定照合順序を選択できるようになります。  
  
4.  **[適用]** をクリックして変更を確認し、 **[OK]** をクリックしてウィンドウを閉じます。  
  
## 参照  
 [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016.md)  
  
  