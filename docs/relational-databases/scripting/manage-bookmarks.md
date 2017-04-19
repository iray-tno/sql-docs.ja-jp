---
title: "ブックマークの管理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.BookmarkWindow"
helpviewer_keywords: 
  - "ブックマーク [SQL Server Management Studio]"
ms.assetid: 67cc3fd6-3238-4c58-a3ec-2d3b0438143a
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# ブックマークの管理
  コード エディターでの作業中に、**[ブックマーク]** ウィンドウで、ドキュメント内のコードの特定の行へのリンクを作成できます。 このウィンドウは、**[表示]** メニューから表示できます。  
  
 ブックマークの作成やブックマーク間の移動は、**[ブックマーク]** ウィンドウ上部の **[テキスト エディター]** ツール バーにあるボタンをクリックして実行します。 ブックマークの追加および削除や有効化および無効化を行ったり、ブックマークをフォルダーに構成したりできます。 また、**[ブックマーク]** ウィンドウ ショートカット メニューから、特定のコマンドも利用できます。 ブックマークを追加または削除するには、エディターで目的の行にカーソルを置き、**[ブックマークの設定/解除]** をクリックします。 ブックマークを有効化するには、**[ブックマーク]** ウィンドウで対象ブックマークのチェック ボックスをオンにします。ブックマークを無効化する (ただし、削除しない) 場合は、チェック ボックスをオフにします。  
  
## [テキスト エディター] ツール バー  
 エディターでテキスト ドキュメントを開いているときは、**[テキスト エディター]** ツール バーの次のボタンが有効になっています。 クエリ エディターで作業中に **[テキスト エディター]** ツール バーを表示するには、**[表示]** メニューで **[ツール バー]** をポイントし、**[テキスト エディター]** をクリックします。  
  
 **[現在行にブックマークを追加/削除します]**  
 アクティブなエディターで、ドキュメントの選択された行にブックマークを追加または削除します。 ブックマークが付けられたコードの行は変更しません。  
  
 **[カレットを前のブックマークへ移動します。]**  
 **[ブックマーク]** ウィンドウで有効になっている、前のブックマークを選択します。 最初のブックマークに到達すると、最後のブックマークにジャンプします。 必要に応じて、選択されたブックマークが存在するファイルをエディターで開きます。 そのドキュメントで、ブックマークが付けられた行までスクロールし、その位置にカーソルを置きます。  
  
 **[カレットを次のブックマークへ移動します。]**  
 **[ブックマーク]** ウィンドウで有効になっている、次のブックマークを選択します。 最後のブックマークに到達すると、最初のブックマークにジャンプします。 必要に応じて、選択されたブックマークが存在するファイルをエディターで開きます。 そのドキュメントで、ブックマークが付けられた行までスクロールし、その位置にカーソルを置きます。  
  
 **[ドキュメント内のブックマークをすべてクリア]**  
 確認メッセージを表示した後で、アクティブなドキュメントからすべてのブックマークを削除します。 ブックマークが付いたコードの行を削除するのではありません。  
  
> [!CAUTION]  
>  この処理を元に戻すことはできません。 元に戻すには、**[現在行にブックマークを追加/削除します]** を使用して新しいブックマークを作成する必要があります。 ブックマークを削除せずに無効化するには、**[ブックマーク]** ウィンドウで対象ブックマークのチェック ボックスをオフにします。  
  
## [ブックマーク] ウィンドウ  
 ブックマークを構成するには、**[ブックマーク]** ウィンドウでブックマーク フォルダーを作成します。 ブックマークをフォルダーにドラッグしてドロップします。 **[ブックマーク]** ウィンドウ上部にある次のボタンが利用可能です。  
  
 **[現在行にブックマークを追加/削除します。]**  
 アクティブなエディターで、ドキュメントの選択された行にブックマークを追加または削除します。 ブックマークが付けられたコードの行は変更しません。  
  
 **[新しいフォルダー]**  
 **[ブックマーク]** ウィンドウにフォルダーを追加します。  
  
> [!TIP]  
>  長いコード ファイルの場合は、ブックマークをタスク関連フォルダーに構成すると便利です。 フォルダーを選択すると、**[フォルダー内の前のブックマーク]** ボタンと **[フォルダー内の次のブックマーク]** ボタンが有効になります。  
  
 **[カレットを前のブックマークへ移動します。]**  
 **[ブックマーク]** ウィンドウで有効になっている、前のブックマークを選択します。 最初のブックマークに到達すると、最後のブックマークにジャンプします。 必要に応じて、選択されたブックマークが存在するファイルをエディターで開きます。 そのドキュメントで、ブックマークが付けられた行までスクロールし、その位置にカーソルを置きます。  
  
 **[カレットを次のブックマークへ移動します。]**  
 **[ブックマーク]** ウィンドウで有効になっている、次のブックマークを選択します。 最後のブックマークに到達すると、最初のブックマークにジャンプします。 必要に応じて、選択されたブックマークが存在するファイルをエディターで開きます。 そのドキュメントで、ブックマークが付けられた行までスクロールし、その位置にカーソルを置きます。  
  
 **[カレットを現在のフォルダー内の前のブックマークに移動します。]**  
 **[ブックマーク]** ウィンドウ内の同一フォルダー内で有効になっている、前のブックマークを選択します。 最初のブックマークに到達すると、そのフォルダーの最後のブックマークにジャンプします。 必要に応じて、選択されたブックマークが存在するファイルをエディターで開きます。 そのドキュメントで、ブックマークが付けられた行までスクロールし、その位置にカーソルを置きます。  
  
 **[カレットを現在のフォルダー内の次のブックマークに移動します。]**  
 **[ブックマーク]** ウィンドウ内の同一フォルダー内で有効になっている、次のブックマークを選択します。 最初のブックマークに到達すると、そのフォルダーの最初のブックマークにジャンプします。 必要に応じて、選択されたブックマークが存在するファイルをエディターで開きます。 そのドキュメントで、ブックマークが付けられた行までスクロールし、その位置にカーソルを置きます。  
  
 **[すべてのブックマークを有効/無効にします]**  
 **[ブックマーク]** ウィンドウ内のすべてのブックマークに対して、チェック ボックスをオフまたはオンにします。 ブックマークは削除されません。また、ブックマークが付けられたコードの行は変更されません。  
  
 **Del**  
 現在選択されているブックマークを **[ブックマーク]** ウィンドウ、およびブックマークが存在するドキュメントから削除します。 ブックマークが付いたコードの行を削除するのではありません。  
  
 ブックマークのチェック ボックス  
 各ブックマークには固有のチェック ボックスがあります。 既存のブックマークを有効化するには、**[ブックマーク]** ウィンドウで対象ブックマークのチェック ボックスをオンにします。 既存のブックマークを非表示にする (ただし削除しない) 場合は、**[ブックマーク]** ウィンドウで対象ブックマークのチェック ボックスをオフにします。  
  
## [ブックマーク] ウィンドウのショートカット メニュー  
 **[ブックマーク]** ウィンドウ内のエントリを右クリックし、ショートカット メニューから次のコマンドを利用できます。  
  
 **Del**  
 現在選択されているブックマークを **[ブックマーク]** ウィンドウ、およびブックマークが存在するドキュメントから削除します。 ブックマークが付いたコードの行を削除するのではありません。  
  
 **Rename**  
 ブックマークまたはフォルダーに新しい表示名を割り当てることができます。  
  
 **[ブックマークを有効/無効にする]**  
 **[ブックマーク]** ウィンドウ内で選択されたブックマークに対して、チェック ボックスをオフまたはオンにします。 ブックマークは削除されません。また、ブックマークが付けられたコードの行は変更されません。  
  
 **[すべてのブックマークを有効/無効にします]**  
 **[ブックマーク]** ウィンドウ内のすべてのブックマークに対して、チェック ボックスをオフまたはオンにします。 ブックマークは削除されません。また、ブックマークが付けられたコードの行は変更されません。  
  
## 参照  
 [SQL Server Management Studio のキーボード ショートカット](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)  
  
  