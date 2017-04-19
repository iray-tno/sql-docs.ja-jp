---
title: "[FTP タスク エディター] ([ファイル転送] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ftptask.filetransfer.f1"
helpviewer_keywords: 
  - "ファイル転送プロトコル タスク エディター"
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# [FTP タスク エディター] ([ファイル転送] ページ)
  **[FTP タスク エディター]** ダイアログ ボックスの **[ファイル転送]** ページを使用すると、タスクで実行される FTP 操作を構成できます。  
  
 このタスクの詳細については、「[FTP タスク](../../integration-services/control-flow/ftp-task.md)」を参照してください。  
  
## オプション  
 **[IsRemotePathVariable]**  
 リモート パスが変数に格納されているかどうかを表します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**True**|対象になるパスは変数に格納されます。 この値を選択すると、動的オプションの **[RemoteVariable]** が表示されます。|  
|**False**|対象になるパスは、ファイル接続マネージャーで指定されます。 この値を選択すると、動的オプションの **[RemotePath]** が表示されます。|  
  
 **[OverwriteFileAtDestination]**  
 転送先でファイルを上書きできるかどうかを指定します。  
  
 **[IsLocalPathVariable]**  
 ローカル パスが変数に格納されているかどうかを表します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**True**|対象になるパスは変数に格納されます。 この値を選択すると、動的オプションの **[LocalVariable]** が表示されます。|  
|**False**|対象になるパスは、ファイル接続マネージャーで指定されます。 この値を選択すると、動的オプションの **[LocalPath]** が表示されます。|  
  
 **操作**  
 実行する FTP 操作を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**ファイルの送信**|ファイルを送信します。 この値を選択すると、動的オプションの **[LocalVariable]**、**[LocalPathRemoteVariable]**、**[RemotePath]** が表示されます。|  
|**ファイルの受信**|ファイルを受信します。 この値を選択すると、動的オプションの **[LocalVariable]**、**[LocalPathRemoteVariable]**、**[RemotePath]** が表示されます。|  
|**ローカル ディレクトリの作成**|ローカル ディレクトリを作成します。 この値を選択すると、動的オプションの **[LocalVariable]** および **[LocalPath]** が表示されます。|  
|**リモート ディレクトリの作成**|リモート ディレクトリを作成します。 この値を選択すると、動的オプションの **[RemoteVariable]** および **[RemotePath]** が表示されます。|  
|**ローカル ディレクトリの削除**|ローカル ディレクトリを削除します。 この値を選択すると、動的オプションの **[LocalVariable]** および **[LocalPath]** が表示されます。|  
|**リモート ディレクトリの削除**|リモート ディレクトリを削除します。 この値を選択すると、動的オプションの **[RemoteVariable]** および **[RemotePath]** が表示されます。|  
|**ローカル ファイルの削除**|ローカル ファイルを削除します。 この値を選択すると、動的オプションの **[LocalVariable]** および **[LocalPath]** が表示されます。|  
|**リモート ファイルの削除**|リモート ファイルを削除します。 この値を選択すると、動的オプションの **[RemoteVariable]** および **[RemotePath]** が表示されます。|  
  
 **[IsTransferASCII]**  
 リモート FTP サーバーへ転送されるファイル、およびリモート FTP サーバーから転送されるファイルを ASCII モードで転送するかどうかを指定します。  
  
## [IsRemotePathVariable] の動的オプション  
  
### [IsRemotePathVariable] = [True]  
 **[RemoteVariable]**  
 既存のユーザー定義変数を選択するか、**[\<新しい接続>]** をクリックしてユーザー定義変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) の変数](../../integration-services/integration-services-ssis-variables.md)、変数の追加  
  
### [IsRemotePathVariable] = [False]  
 **RemotePath**  
 既存の FTP 接続マネージャーを選択するか、**[\<新しい接続>]** をクリックして接続マネージャーを作成します。  
  
 **関連トピック**: [FTP 接続マネージャー](../../integration-services/connection-manager/ftp-connection-manager.md)、[FTP 接続マネージャー エディター](../../integration-services/connection-manager/ftp-connection-manager-editor.md)  
  
## [IsLocalPathVariable] の動的オプション  
  
### [IsLocalPathVariable] = [True]  
 **[LocalVariable]**  
 既存のユーザー定義変数を選択するか、**[\<新しい変数>]** をクリックして変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) の変数](../../integration-services/integration-services-ssis-variables.md)、変数の追加  
  
### [IsLocalPathVariable] = [False]  
 **LocalPath**  
 既存のファイル接続マネージャーを選択するか、**[\<新しい接続>]** をクリックして、接続マネージャーを作成します。  
  
 **関連トピック:** [フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[FTP タスク エディター] ([全般] ページ)](../Topic/FTP%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)  
  
  