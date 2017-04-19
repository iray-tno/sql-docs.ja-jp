---
title: "ODBC SQL Server のドライバーのバージョンを確認する方法 (Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "11/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドライバー バージョン番号 [ODBC]"
  - "ODBC ドライバー, バージョン番号"
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# ODBC SQL Server のドライバーのバージョンを確認する方法 (Windows)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  コンピューターによっては、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] や他社製のさまざまな ODBC ドライバーが組み込まれています。 このトピックでは、Windows の **ODBC データ ソース アドミニストレーター** を使用して、インストールされている ODBC ドライバーのバージョンを確認する方法について説明します。  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32bit-odbc"></a>ODBC SQL Server のドライバーのバージョンを確認するには (32 ビット ODBC)  
  
-   **ODBC データ ソース アドミニストレーター**で **[ドライバー]** タブをクリックします。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [バージョン] **列に、Microsoft** エントリの情報が表示されます。  


> [!NOTE]  
>  SQL Database の Azure Active Directory 認証への接続には、[ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) などの最新ドライバーをインストールします。   

  
## <a name="see-also"></a>参照  
 [ODBC データ ソース アドミニストレーターの起動](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  