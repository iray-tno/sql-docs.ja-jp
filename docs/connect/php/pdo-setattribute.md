---
title: Pdo::setattribute |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 56f9ee96-e1d2-46cc-b137-38f06a251863
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2a5bbd2370839cf1483d251f87588743994b081
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239342"
---
# <a name="pdosetattribute"></a>PDO::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

定義済み PDO 属性またはカスタム ドライバー属性を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDO::setAttribute ( $attribute, $value );  
```  
  
#### <a name="parameters"></a>パラメーター  
*$attribute*: 設定する属性。 サポートされる属性の一覧については、「解説」セクションを参照してください。  
  
*$value*: 値 (混在型)。  
  
## <a name="return-value"></a>戻り値  
成功した場合は TRUE、それ以外の場合は FALSE を返します。  
  
## <a name="remarks"></a>コメント  
  
|属性|処理を行った機能|サポートされている値|説明|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR_CASE|PDO|PDO::CASE_LOWER<br /><br />PDO::CASE_NATURAL<br /><br />PDO::CASE_UPPER|列名の大文字/小文字を指定します。<br /><br />:Case_lower は列名を小文字に変換します。<br /><br />Pdo::case_natural (既定) には、データベースによって返される列名が表示されます。<br /><br />PDO::CASE_UPPER は列名を大文字にします。<br /><br />この属性は PDO::setAttribute を使用して設定できます。|  
|PDO::ATTR_DEFAULT_FETCH_MODE|PDO|PDO のドキュメントを参照してください。|PDO のドキュメントを参照してください。|  
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|ドライバーがエラーを報告する方法を指定します。<br /><br />PDO::ERRMODE_SILENT (既定値) は、エラー コードと情報を設定します。<br /><br />Pdo::errmode_warning は E_WARNING を生成します。<br /><br />Pdo::errmode_exception がスローされる例外が発生します。<br /><br />この属性は PDO::setAttribute を使用して設定できます。|  
|PDO::ATTR_ORACLE_NULLS|PDO|PDO のドキュメントを参照してください。|null を返す方法を指定します。<br /><br />PDO::NULL_NATURAL は変換を行いません。<br /><br />PDO::NULL_EMPTY_STRING は空の文字列を null に変換します。<br /><br />PDO::NULL_TO_STRING は null を空の文字列に変換します。|  
|PDO::ATTR_STATEMENT_CLASS|PDO|PDO のドキュメントを参照してください。|PDOStatement から誘導されたユーザー指定のステートメント クラスを設定します。<br /><br />`array(string classname, array(mixed constructor_args))`を必要とします。<br /><br />詳細については、PDO のドキュメントを参照してください。|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|true または false|データの取得時に数値を文字列に変換します。|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PHP メモリの制限に 1。|結果セットを保持するバッファーのサイズを設定します。<br /><br />既定では 10,240 KB (10 MB) です。<br /><br />クライアント側カーソルを作成するクエリの詳細については、次を参照してください。[カーソルの種類&#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)です。|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true<br /><br />false|クエリの直接実行または準備された実行を指定します。 詳細については、「 [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)」 (PDO_SQLSRV ドライバーでの直接ステートメント実行と準備されたステートメントの実行) を参照してください。|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM.|ドライバーがサーバーとの通信に使用する文字セット エンコーディングを設定します。<br /><br />PDO::SQLSRV_ENCODING_BINARY はサポートされていません。<br /><br />既定値は PDO::SQLSRV_ENCODING_UTF8 です。|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true または false|数値の SQL 型 (ビット、integer、smallint、tinyint、float または real) と列からの数値のフェッチを処理します。<br /><br />接続オプション フラグ ATTR_STRINGIFY_FETCHES が on の場合は、SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がある場合でも文字列は、戻り値です。<br /><br />バインド列で返される PDO 型 PDO_PARAM_INT がある場合は、SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がオフの場合でも、int は整数型の列からの戻り値です。|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|整数 (integer)|クエリのタイムアウト (秒単位) を設定します。<br /><br />既定値は 0 であり、ドライバーは結果をいつまでも待ちます。<br /><br />負の数値は許可できません。|  
|PDO::SQLSRV_CLIENT_BUFFER_MAX_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|整数 (integer)|クエリ バッファーのサイズを設定します。<br /><br />既定値 10240 KB は、指定しなかった場合は、php.ini ファイルでします。<br /><br />0、負の数値は許可されていません。<br /><br />クライアント側カーソルを作成するクエリの詳細については、次を参照してください。[カーソルの種類&#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)です。|  
  
一部の定義済み属性は PDO で処理されますが、他の属性はドライバーで処理する必要があります。 カスタム属性と接続オプションはすべてドライバーにより処理されます。 サポートされていない属性、接続オプション、またはサポートされていない値は pdo::attr_errmode の設定に基づいて報告されます。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
このサンプルは、PDO::ATTR_ERRMODE 属性を設定する方法を示しています。  
  
```  
<?php  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
  
   $attributes1 = array( "ERRMODE" );  
   foreach ( $attributes1 as $val ) {  
      echo "PDO::ATTR_$val: ";  
      var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
   }  
  
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
  
   $attributes1 = array( "ERRMODE" );  
   foreach ( $attributes1 as $val ) {  
      echo "PDO::ATTR_$val: ";  
      var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
   }  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
