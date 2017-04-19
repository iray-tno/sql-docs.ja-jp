---
title: "[SQL 変換先エディター] ([詳細設定] ページ) | Microsoft Docs"
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
  - "sql13.dts.designer.sqlserverdestadapter.advanced.f1"
helpviewer_keywords: 
  - "SQL Server 変換先エディター"
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# [SQL 変換先エディター] ([詳細設定] ページ)
  **[SQL 変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、詳細な一括挿入オプションを指定できます。  
  
 SQL Server 変換先の詳細については、「 [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md)」を参照してください。  
  
## オプション  
 **[ID を保持する]**  
 タスクが値を ID 列に挿入するかどうかを指定します。 このプロパティの既定値は **False**です。  
  
 **[NULL を保持する]**  
 タスクが NULL 値を保持するかどうかを指定します。 このプロパティの既定値は **False**です。  
  
 **[テーブル ロック]**  
 データが読み込まれるときにテーブルをロックするかどうかを指定します。 このプロパティの既定値は **True**です。  
  
 **CHECK 制約**  
 タスクが制約をチェックするかどうかを指定します。 このプロパティの既定値は **True**です。  
  
 **[トリガーを起動する]**  
 テーブルにおける一括挿入でトリガーを起動するかどうかを指定します。 このプロパティの既定値は **False**です。  
  
 **[先頭行]**  
 先頭行が挿入されるように指定します。 このプロパティの既定値は、**-1** です。これは、値が割り当てられていないことを示します。  
  
> [!NOTE]  
>  このプロパティに値を割り当てない場合、**[SQL 変換先エディター]** のテキスト ボックスをクリアします。 **[プロパティ]** ウィンドウ、**[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。  
  
 **[最終行]**  
 最終行が挿入されるように指定します。 このプロパティの既定値は、**-1** です。これは、値が割り当てられていないことを示します。  
  
> [!NOTE]  
>  このプロパティに値を割り当てない場合、**[SQL 変換先エディター]** のテキスト ボックスをクリアします。 **[プロパティ]** ウィンドウ、**[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。  
  
 **[エラーの最大数]**  
 一括挿入を停止する前に許容するエラー数を指定します。 このプロパティの既定値は、**-1** です。これは、値が割り当てられていないことを示します。  
  
> [!NOTE]  
>  このプロパティに値を割り当てない場合、**[SQL 変換先エディター]** のテキスト ボックスをクリアします。 **[プロパティ]** ウィンドウ、**[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。  
  
 **Timeout**  
 タイムアウトで一括挿入が停止されるまでの待機時間を秒数で指定します。  
  
 **[列の順序]**  
 キー列の名前を入力します。 各列は、昇順または降順で並べ替えることができます。 複数のキー列を使用する場合は、リストをコンマで区切ります。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[SQL 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../Topic/SQL%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)   
 [[SQL 変換先エディター] &#40;[マッピング] ページ&#41;](../Topic/SQL%20Destination%20Editor%20\(Mappings%20Page\).md)   
 [SQL Server 変換先を使用してデータの一括読み込みを行う](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  