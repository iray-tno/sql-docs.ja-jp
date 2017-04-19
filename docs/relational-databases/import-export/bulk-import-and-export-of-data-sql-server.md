---
title: "データの一括インポートと一括エクスポート (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "09/28/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データのエクスポート"
  - "一括インポート [SQL Server], 一括インポートについて"
  - "データ [SQL Server], 一括エクスポートと一括インポート"
  - "データの転送"
  - "データのインポート, (「一括インポート [SQL Server]」も参照)"
  - "データのコピー [SQL Server]"
  - "一括エクスポート [SQL Server]"
  - "データをインポートするには、一括インポート"
  - "データのコピー [SQL Server], 一括エクスポートと一括インポート"
  - "データのエクスポート, (「一括エクスポート [SQL Server]」も参照)"
  - "一括エクスポート [SQL Server], 一括エクスポートについて"
  - "一括インポート [SQL Server]"
  - "インポート、データ"
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
caps.latest.revision: 61
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 61
---
# データの一括インポートと一括エクスポート (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルからのデータの一括エクスポート (*一括データのエクスポート*)、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはパーティション分割されていないビューへの一括データのインポートがサポートされています。 
  
 *一括エクスポート* とは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルから特定のデータ ファイルにデータをコピーすることです。 
 *一括インポート* は、データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータを読み込むことを指します。 たとえば、データを [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel アプリケーションから特定のデータ ファイルにエクスポートした後、そのデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに一括インポートできます。  
 
##  <a name="MethodsForBuliIE"></a> データの一括インポートと一括エクスポートの方法  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルからのデータの一括エクスポート、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはパーティション分割されていないビューへのデータの一括インポートがサポートされています。 使用できる基本的な方法を次に示します。  
 
  
|方法|説明|データのインポート|データのエクスポート|  
|------------|-----------------|------------------|------------------|  
|[bcp ユーティリティ](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|データの一括エクスポートと一括インポート、およびフォーマット ファイルの生成を行うコマンド ライン ユーティリティ (Bcp.exe)。|可|はい|  
|[BULK INSERT ステートメント](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|データ ファイルのデータをデータベース テーブルまたはパーティション分割されていないビューに直接インポートする [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント。|はい|いいえ|  
|[INSERT ...SELECT * FROM OPENROWSET(BULK...) ステートメント](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|INSERT ステートメントでデータを選択するために OPENROWSET(BULK...) 関数を指定することによって、OPENROWSET 一括行セット プロバイダーを使用してデータを [!INCLUDE[tsql](../../includes/tsql-md.md)] テーブルに一括インポートする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメント。|はい|いいえ| 
|[SQL Server インポートおよびエクスポート ウィザード](https://msdn.microsoft.com/library/ms141209.aspx)|このウィザードでは、データセット、スプレッドシート、テキスト ファイルなど、さまざまな一般的なデータ形式の間でデータをインポートまたはエクスポートする簡単なパッケージが作成されます。|可|可|  
  
> [!IMPORTANT]
> SQL Server の一括インポート操作では、コンマ区切り (CSV) ファイルがサポートされていません。 ただし、場合によっては、SQL Server に対してデータを一括インポートする際、CSV ファイルをデータ ファイルとして使用できます。 CSV ファイルのフィールド ターミネータは必ずしもコンマである必要はありません。 詳細については、「[一括エクスポートまたは一括インポートのデータの準備 (SQL Server)](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)」を参照してください。

> [!NOTE]
> Azure SQL Database と Azure SQL DW で区切られたファイルをインポートおよびエクスポートするには、bcp ユーティリティのみがサポートされています。
  
##  <a name="FFs"></a> フォーマット ファイル  
 [bcp ユーティリティ](../../tools/bcp-utility.md)、[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)、および [INSERT ...SELECT * FROM OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md) では、*フォーマット ファイル*という特殊なファイルを使用して、データ ファイル内のフィールドごとにフォーマット情報を格納することができます。 また、フォーマット ファイルには、対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに関する情報が含まれる場合もあります。 フォーマット ファイルは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスからデータを一括エクスポートしたり、このインスタンスにデータを一括インポートしたりするのに必要なすべてのフォーマット情報を指定するために使用できます。  
  
 フォーマット ファイルを使用すると、インポートの際にデータ ファイルの形式に従ってデータを解釈したり、エクスポートの際にデータ ファイル内のデータに形式を適用する処理を柔軟に行えるようになります。 これにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または外部アプリケーションの特定の必要性に応じてデータの解釈や再フォーマットを行うことだけを目的としたプログラムを作成する必要がなくなります。 たとえば、コンマ区切り値が必要なアプリケーションに読み込まれるデータを一括インポートする場合、フォーマット ファイルを使用すると、エクスポートされたデータにフィールド ターミネータとしてコンマを挿入できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  では、XML フォーマット ファイルと XML 以外のフォーマット ファイルの 2 種類がサポートされます。  
  
 フォーマット ファイルを生成できるツールは、[bcp ユーティリティ](../../tools/bcp-utility.md)だけです。 詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](../../relational-databases/import-export/create-a-format-file-sql-server.md)」をご覧ください。 フォーマット ファイルの使用方法の詳細は、「[データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。  
  
> [!NOTE]
> 一括エクスポート操作または一括インポート操作でフォーマット ファイルが正しく提供されなかった場合に備えて、ユーザーはコマンド ラインで既定の形式を上書きすることもできます。

|関連項目|
|---|
|[一括エクスポートまたは一括インポートのデータの準備 (SQL Server)](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)|
|[一括インポートまたは一括エクスポートのデータ形式 (SQL Server)](../../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)<br />&emsp;&#9679;&emsp;[ネイティブ形式を使用したデータのインポートまたはエクスポート (SQL Server)](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)<br />&emsp;&#9679;&emsp;[文字形式を使用したデータのインポートまたはエクスポート (SQL Server)](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)<br />&emsp;&#9679;&emsp;[Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート (SQL Server)](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)<br />&emsp;&#9679;&emsp;[Unicode 文字形式を使用したデータのインポートまたはエクスポート (SQL Server)](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)<br />&emsp;&#9679;&emsp;[以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)|
|[bcp を使用した互換性のためのデータ形式の指定 (SQL Server)](../../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)<br />&emsp;&#9679;&emsp;[bcp を使用したファイル ストレージ型の指定 (SQL Server)](../../relational-databases/import-export/specify-file-storage-type-by-using-bcp-sql-server.md)<br />&emsp;&#9679;&emsp;[bcp を使用したデータ ファイルのプレフィックス長の指定 (SQL Server)](../../relational-databases/import-export/specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)<br />&emsp;&#9679;&emsp;[bcp を使用したフィールド長の指定 (SQL Server)](../../relational-databases/import-export/specify-field-length-by-using-bcp-sql-server.md)<br />&emsp;&#9679;&emsp;[フィールド ターミネータと行ターミネータの指定 (SQL Server)](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)|
|[一括インポート中の NULL の保持または既定値の使用 (SQL Server)](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)|
|[データの一括インポート時の ID 値の保持 (SQL Server)](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)|
|[データのインポートまたはエクスポート用のフォーマット ファイル (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)<br />&emsp;&#9679;&emsp;[フォーマット ファイルの作成 (SQL Server)](../../relational-databases/import-export/create-a-format-file-sql-server.md)<br />&emsp;&#9679;&emsp;[データの一括インポートでのフォーマット ファイルの使用 (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)<br />&emsp;&#9679;&emsp;[フォーマット ファイルを使用したテーブル列のスキップ (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)<br />&emsp;&#9679;&emsp;[フォーマット ファイルを使用したデータ フィールドのスキップ (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)<br />&emsp;&#9679;&emsp;[フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)<p>                                                                                                                                                                                                                  </p>|
 
  
## その他の情報  
 [一括インポートで最小ログ記録を行うための前提条件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)   
 [XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)   
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)   
 [他のサーバーへのデータベースのコピー](../../relational-databases/databases/copy-databases-to-other-servers.md)   
 [XML データの一括読み込みの実行 &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)   
 [一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)   

  
  