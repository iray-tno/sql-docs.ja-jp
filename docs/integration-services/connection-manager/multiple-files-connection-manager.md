---
title: "複数ファイル接続マネージャー | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フォルダー [Integration Services], 接続"
  - "ファイル [Integration Services], 接続"
  - "複数ファイル接続マネージャー"
  - "接続マネージャー [Integration Services], 複数のファイル"
  - "接続 [Integration Services], ファイル"
  - "複数ファイル接続"
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 36
---
# 複数ファイル接続マネージャー
  複数ファイル接続マネージャーを使用すると、パッケージで既存のファイルやフォルダーを参照したり、実行時にファイルやフォルダーを作成したりできます。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の組み込みタスクとデータ フロー コンポーネントは、複数ファイル接続マネージャーを使用しません。 ただし、スクリプト タスクまたはスクリプト コンポーネントでは、この接続マネージャーを使用できます。 スクリプト タスクで接続マネージャーを使用する方法については、「[スクリプト タスクでのデータ ソースへの接続](../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)」を参照してください。 スクリプト コンポーネントで接続マネージャーを使用する方法については、「[スクリプト コンポーネントでのデータ ソースへの接続](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)」を参照してください。  
  
## 複数ファイル接続マネージャーの使用方法の種類  
 複数ファイル接続マネージャーの **FileUsageType** プロパティでは、接続の使用方法を指定します。 複数ファイル接続マネージャーでは、ファイルの作成、フォルダーの作成、既存のファイルの使用、および既存のフォルダーの使用を行うことができます。  
  
 次の表に **FileUsageType** の値を示します。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|複数ファイル接続マネージャーは、既存のファイルを使用します。|  
|**1**|複数ファイル接続マネージャーは、ファイルを作成します。|  
|**2**|複数ファイル接続マネージャーは、既存のフォルダーを使用します。|  
|**3**|複数ファイル接続マネージャーは、フォルダーを作成します。|  
  
## 複数ファイル接続マネージャーの構成  
 複数ファイル接続マネージャーをパッケージに追加するときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時に複数ファイルの接続を解決する接続マネージャーを作成し、複数ファイルの接続プロパティを設定して、複数ファイルの接続をパッケージの **Connections** コレクションに追加します。  
  
 接続マネージャーの **ConnectionManagerType** プロパティは、**MULTIFILE** に設定されます。  
  
 複数ファイル接続マネージャーは、次の方法で構成できます。  
  
-   ファイルとフォルダーの、使用法の種類を指定します。  
  
-   ファイルとフォルダーを指定します。  
  
-   複数のファイルまたはフォルダーを使用する場合、ファイルとフォルダーのアクセス順序を指定します。  
  
 複数ファイル接続マネージャーが複数のファイルとフォルダーを参照する場合、そのファイルとフォルダーのパスは、パイプ (|) 文字で区切ります。 この接続マネージャーの **ConnectionString** プロパティの形式は、次のとおりです。  
  
 \<*パス*>|\<*パス*>  
  
 複数のファイルまたはフォルダーを指定する場合、ワイルドカード文字を使用することもできます。 たとえば、C ドライブ内のすべてのテキスト ファイルを参照するには、**ConnectionString** プロパティの値を「C:\\*.txt」に設定します。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「[[ファイル接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](../Topic/Add%20File%20Connection%20Manager%20Dialog%20Box%20UI%20Reference.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成の詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>」および「[プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)」を参照してください。  
  
  