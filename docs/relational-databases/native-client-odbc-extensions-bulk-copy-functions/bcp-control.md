---
title: bcp_control |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_control
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
caps.latest.revision: 60
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 31efad83f947d774b6602fe4da85046ad6b9e198
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32948007"
---
# <a name="bcpcontrol"></a>bcp_control
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ファイルと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の間の一括コピーに使用するさまざまな制御パラメーターの既定の設定を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_control (  
        HDBC hdbc,  
        INT eOption,  
        void* iValue);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *eOption*  
 次のいずれかを指定します。  
  
 BCPABORT   
 既に実行中の一括コピー操作を停止します。 呼び出す**bcp_control**で、 *eOption*の実行が停止別のスレッドから bcpabort を指定して一括コピー操作をします。 *IValue*パラメーターは無視されます。  
  
 BCPBATCH   
 バッチごとの行の数です。 既定値は 0 です。既定値を指定すると、データを抽出するときはテーブル内のすべての行が抽出されることを示し、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするときはユーザー データ ファイル内のすべての行がコピーされることを示します。 1 より小さい値を指定すると、BCPBATCH は既定値にリセットされます。  
  
 BCPDELAYREADFMT  
 ブール値の場合は、true に設定すると、 [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)実行時に読み取り。 場合は false (既定値)、bcp_readfmt がすぐには、フォーマット ファイルを読み取る。 BCPDELAYREADFMT が true と bcp_columns または bcp_setcolfmt 呼び出しシーケンス エラーが発生します。  
  
 呼び出す場合にもシーケンス エラーが発生`bcp_control(hdbc,`BCPDELAYREADFMT`, (void *)FALSE)`呼び出した後`bcp_control(hdbc,`BCPDELAYREADFMT`, (void *)TRUE)` bcp_writefmt とします。  
  
 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)です。  
  
 BCPFILECP  
 *iValue*データ ファイルのコード ページの数が含まれています。 1252 や 850 などのコード ページ番号を指定するか、次のいずれかの値を指定できます。  
  
 BCPFILE_ACP を指定すると、ファイル内のデータには、クライアントの Microsoft Windows&#xAE; コード ページが使用されます。  
  
 BCPFILE_OEMCP を指定すると、ファイル内のデータには、クライアントの OEM コード ページ (既定) が使用されます。  
  
 BCPFILE_RAW を指定すると、ファイル内のデータには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコード ページが使用されます。  
  
 BCPFILEFMT  
 データ ファイル形式のバージョン番号を指定します。 80 を使用できます ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)])、90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)])、100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)])、110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])、または 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)])。 120 が既定値です。 このオプションは、以前のバージョンのサーバーでサポートされていた形式でデータをエクスポートおよびインポートする際に便利です。 テキストの列から取得されたデータをインポートするなど、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]のサーバーに、 **varchar (max)** 内の列、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のサーバーでは、80 を指定する必要があります。 同様からのデータをエクスポートするときに 80 を指定する場合、 **varchar (max)** 列、保存されるのでにテキスト列を保存する場合と同じように、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]書式設定、およびのテキスト列にインポートすることができます、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サーバー。  
  
 BCPFIRST   
 ファイルまたはテーブルにコピーする最初のデータ行を指定します。 既定値は 1 です。1 未満の値を指定すると、このオプションは既定値にリセットされます。  
  
 BCPFIRSTEX  
 BCP out 操作の場合は、データ ファイルにコピーするための、データベース テーブルの最初の行を指定します。  
  
 BCP in 操作の場合は、データベース テーブルにコピーするための、データ ファイルの最初の行を指定します。  
  
 *IValue*値を表す符号付き 64 ビット整数のアドレスを指定するパラメーターが必要です。 BCPFIRSTEX に渡すことができる最大値は 2 ^63-1。  
  
 BCPFMTXML  
 XML 形式のフォーマット ファイルが生成されることを指定します。 既定では無効になっています。  
  
 XML フォーマット ファイルより柔軟なは、いくつかの制約を追加します。 たとえば、されませんを指定できますプレフィックスとターミネータのフィールドを同時に、可能なフォーマット ファイルの古いであった。  
  
> [!NOTE]  
>  XML フォーマット ファイルがサポートされるのは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client と共にインストールした場合だけです。  
  
 BCPHINTS  
 *iValue* SQLTCHAR 文字列ポインターが含まれています。 ポインターが指す文字列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一括コピー処理ヒント、または結果セットを返す Transact-SQL ステートメントを指定します。 複数の結果セットを返す Transact-SQL ステートメントを指定すると、1 つ目以外の結果セットはすべて無視されます。 一括コピー処理ヒントの詳細については、次を参照してください。 [bcp ユーティリティ](../../tools/bcp-utility.md)です。  
  
 BCPKEEPIDENTITY  
 ときに*iValue* TRUE は、一括コピー関数が指定されているデータ値を挿入することを指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列 identity 制約を定義します。 入力ファイルには ID 列の値を指定する必要があります。 このオプションを設定しないと、挿入される行に対して新しい ID 値が生成されます。 ファイル内に存在する ID 列用のデータはすべて無視されます。  
  
 BCPKEEPNULLS   
 ファイル内の空のデータ値を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルで NULL 値に変換するかどうかを指定します。 ときに*iValue*が true の場合、空の値は NULL に変換されます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 既定では、空の値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列の既定値 (存在する場合) に変換されます。  
  
 BCPLAST   
 コピーする最後の行がします。 既定では、すべての行がコピーされます。1 より小さい値を指定すると、このオプションは既定値にリセットされます。  
  
 BCPLASTEX  
 BCP out 操作の場合は、データ ファイルにコピーするための、データベース テーブルの最後の行を指定します。  
  
 BCP in 操作の場合は、データベース テーブルにコピーするための、データ ファイルの最後の行を指定します。  
  
 *IValue*値を表す符号付き 64 ビット整数のアドレスを指定するパラメーターが必要です。 BCPLASTEX に渡すことができる最大値は 2^63-1 です。  
  
 BCPMAXERRS   
 一括コピー操作が失敗するまでに発生してもかまわないエラーの数です。 既定値は 10 です。1 より小さい値は、その既定値には、このオプションをリセットします。 一括コピーでは、最大 65,535 個のエラーが許容されます。 このオプションに 65,535 を超える値を設定しようとすると、65,535 が設定されます。  
  
 BCPODBC  
 TRUE の場合、指定される**datetime**と**smalldatetime** ODBC タイムスタンプ エスケープ シーケンスのプレフィックスとサフィックス文字形式で保存された値が使用されます。 BCPODBC オプションは、DB_OUT にのみ適用されます。  
  
 FALSE の場合、 **datetime** 1997 年 1 月 1 日を表す値は、文字の文字列に変換されます。 1997-01-01 00:00:00.000 されます。 TRUE の場合、同じ**datetime**として表される値: {ts ' 1997-01-01 00:00:00.000'}。  
  
 BCPROWCOUNT  
 現在 (または最後) の BCP 操作で処理された行数を返します。  
  
 BCPTEXTFILE  
 TRUE の場合、データ ファイルがバイナリ ファイルではなくテキスト ファイルであることを示します。 ファイルがテキスト ファイルの場合、BCP では、データ ファイルの先頭 2 バイトに含まれる Unicode バイト マーカーをチェックして、そのファイルが Unicode 形式かどうかを判断します。  
  
 BCPUNICODEFILE  
 TRUE の場合、入力ファイルが Unicode ファイルであることを指定します。  
  
 *iValue*  
 指定された値は、 *eOption*です。 *iValue*は、整数値 (LONGLONG) を 64 ビット値に拡張できるように void ポインターにキャストします。  
  
## <a name="returns"></a>返します。  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 この関数では、一括コピー操作のさまざまな制御パラメーターを設定します。たとえば、一括コピーが取り消されるまでに発生してもかまわないエラーの数、データ ファイルから最初にコピーする行番号や最後にコピーする行番号、バッチ サイズなどを設定します。  
  
 また、この関数は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SELECT ステートメントの結果セットを一括コピーするときに、その SELECT ステートメントを指定するためにも使用します。 設定*eOption*を BCPHINTS に設定し*iValue*に SELECT ステートメントを含む SQLTCHAR 文字列へのポインター。  
  
 これらの制御パラメーターは、ユーザー ファイルと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルの間でコピーを行う場合のみ意味があります。 制御パラメーターの設定がある影響しないにコピーされる行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)です。  
  
## <a name="example"></a>例  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
