---
title: getDate (int, java.util.Calendar) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getDate (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38ce7b75-2623-4eff-bc18-8cf7193adec8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cdf89172da4d3b0d465a3eae452922e5a5a4877
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32834957"
---
# <a name="getdate-method-int-javautilcalendar"></a>getDate (int, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターのインデックスとオブジェクトのカレンダー、Java プログラミング言語の java.sql.Date オブジェクトとして指定されたパラメーターの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Date getDate(int index,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**パラメーター インデックスを示すです。  
  
 *cal*  
  
 予定表オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 Date オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getDate メソッドは、getDate、java.sql.CallableStatement インターフェイスのメソッドでによって指定されます。  
  
 このメソッドの有効な日付部分を返します、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime**または**smalldatetime**データ型、時刻部分は、Java のベースラインの時刻 00:00 (午前 0 時) に設定します。  
  
## <a name="see-also"></a>参照  
 [getDate メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
