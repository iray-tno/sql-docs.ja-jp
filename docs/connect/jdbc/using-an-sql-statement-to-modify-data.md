---
title: SQL ステートメントを使用してデータを変更する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4704199b-c0ae-4c77-8a2e-6963715b4ffb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d02d5187e869eb626cfddde9e12bcf55feed51a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851387"
---
# <a name="using-an-sql-statement-to-modify-data"></a>SQL ステートメントを使用したデータの変更
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  含まれているデータを変更する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース、SQL ステートメントを使用すると、使用することができます、 [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。 ExecuteUpdate メソッドは、処理にデータベースに SQL ステートメントを渡すし、影響を受けた行の数を示す値を返します。  
  
 これを行うには、作成する必要が最初に、SQLServerStatement オブジェクトを使用して、 [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]関数に渡し、サンプル データベース、テーブルに新しいデータを追加する SQL ステートメントが作成されて、ステートメントが実行され、戻り値が表示されます。  
  
 [!code[JDBC#UsingSQLToModifyData1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_1_1.java)]  
  
> [!NOTE]  
>  データを変更するパラメーターを含む SQL ステートメントを使用する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 、データベースを使用してください、 [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)のメソッド、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスです。  
>   
>  データの挿入先の列にスペースなどの特殊文字が含まれる場合は、それが既定値である場合を含め、挿入する値を指定する必要があります。 ここで指定しないと、挿入操作が失敗します。  
>   
>  JDBC ドライバで、発生した可能性があるすべてのトリガが返した更新数を含む、すべての更新数を返す場合、lastUpdateCount 接続文字列プロパティを "false" に設定します。 LastUpdateCount プロパティの詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [SQL でのステートメントの使用](../../connect/jdbc/using-statements-with-sql.md)  
  
  
