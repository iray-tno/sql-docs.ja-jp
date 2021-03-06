---
title: OLE DB テーブル値パラメーター型のサポート (メソッド) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
ms.assetid: e3c2a450-8fd4-44cb-93d8-affe1b65c68e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 56dcc0ea893714a2ddb42a986cd5ab63828998c7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950267"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>OLE DB テーブル値パラメーターの型のサポート (メソッド)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  次の OLE DB 標準メソッドでは、テーブル値パラメーターがサポートされます。  
  
|方法|テーブル値パラメーターのサポート|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|テーブル値パラメーターの型情報がわかっており、その型情報に基づいてテーブル値パラメーターの行セット オブジェクトのインスタンスを作成する場合に使用します。<br /><br /> 詳細については、「静的なシナリオ」を参照してください[テーブル値パラメーター行セットの作成](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)です。|  
|IOpenRowset::OpenRowset|テーブル値パラメーターの型情報がわかっておらず、サーバーから取得したメタデータ情報に基づいてテーブル値パラメーターの行セット オブジェクトのインスタンスを作成する場合に使用します。<br /><br /> 詳細については、「動的なシナリオ」を参照してください[テーブル値パラメーター行セットの作成](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)です。|  
|ISSCommandWithParameters::SetParameterInfo|テーブル値パラメーターのコマンド パラメーターを指定する、コンシューマーの種類を指定、パラメーター"table"または"DBTYPE_TABLE"としての*pwszName* DBPARAMBINDINFO 構造体のメンバーです。 *UlParamSize*に設定されている ~ 0 です。 詳細については、「テーブル値パラメーターの指定」を参照してください[Executing Commands Containing Table-Valued パラメーター](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)です。|  
|Isscommandwithparameters::setparameterproperties|スキーマ名、型名、列の順序、既定の列など、テーブル値パラメーター固有のプロパティを設定します。<br /><br /> コンシューマーでパラメーターの序数を指定する、 *iOrdinal* SSPARAMPROPS 構造体の。 要求されるプロパティ セットは DBPROPSET_SQLSERVERPARAMETER です。|  
|ISSCommandWithParameters::GetParameterInfo|指定されたコマンドのすべてのパラメーターの型を取得します。<br /><br /> テーブル値パラメーターの*wType* DBPARAMINFO 構造体のフィールド型は DBTYPE_TABLE になります。 *UlParamSize*フィールドが設定されます ~ 0 で不明な長さを示します。|  
|Isscommandwithparameters::getparameterproperties|DBTYPE_TABLE 型のパラメーターの追加の型情報を取得します。<br /><br /> コンシューマーでパラメーターの序数を指定する、 *iOrdinal* SSPARAMPROPS 構造体のメンバーです。 コンシューマーは、任意の isscommandwithparameters::setparameterproperties に表示される DBPROPSET_SQLSERVERPARAMETER プロパティ セット内のプロパティを要求できます。<br /><br /> コンシューマーではテーブル値パラメーターの型がわからないため、プロバイダーは SSPROP_PARAM_TYPE_TYPENAME、SSPROP_PARAM_TYPE_SCHEMANAME、および SSPROP_PARAM_TYPE_CATALOGNAME に正しい値を設定する必要があります。 残りのプロパティ、SSPROP_PARAM_TABLE_DEFAULT_COLUMNS および SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER の値は、既定の値になります。 コンシューマーがテーブル値パラメーターの型名は、検出された後は、このテーブル値パラメーターのテーブル値パラメーターの型の名前を指定するインスタンスを作成するのに iopenrowset::openrowset が使用されます。 詳細については、次を参照してください。[テーブル値パラメーターの型の検出](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)です。|  
|Irowsetinfo:|テーブル値パラメーターの行セット プロパティを取得します。 コンシューマーはこれらのプロパティを使用して、バインドを最適に設定することができます。|  
|IColumnsRowset::GetColumnsRowset|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに関するメタデータ情報を取得します。 テーブル値パラメーターの場合、この同じインターフェイスにより、次のような各列に関する詳細なメタデータ情報が提供されます。<br /><br /> DBCOLUMN_FLAGS では、DBCOLUMNFLAGS_ISNULLABLE ビットを使用して NULL 値許容を示します。<br /><br /> DBCOLUMN_ISUNIQUE では、列が ID 列かどうかを示します。<br /><br /> DBCOLUMN_COMPUTEMODE は、列が計算列かどうかを示します。|  
|IAccessor::CreateAccessor|アクセサーを作成するテーブル値パラメーター行セット オブジェクトをコマンド パラメーターをバインドする、 *wType*メンバー DBTYPE_TABLE に設定します。 DBOBJECT 構造体には IID_IRowset、または その他の有効な行セット オブジェクト インターフェイスが含まれます、 *iid*メンバー。 フィールドの残りの部分は、DBTYPE_IUNKNOWN と同じように扱われます。|  
  
## <a name="see-also"></a>参照  
 [OLE DB テーブル値パラメーターの型のサポート](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [テーブル値パラメーター行セットの作成](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB (&) #41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
