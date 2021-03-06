---
title: フェッチされた行の数と状態 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- number of rows fetched [ODBC]
- result sets [ODBC], row status array
ms.assetid: a069b979-5108-4905-932f-8ae8e7905ff2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16bc3a279e2d4565529dd175c16bce01f9431403
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914007"
---
# <a name="number-of-rows-fetched-and-status"></a>フェッチされた行の数と状態
バッファーへの呼び出しによってフェッチされた行の数を表すオブジェクトを指定 SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性が設定されている場合**SQLFetch**または**SQLFetchScroll**、およびエラーの行。 (この数は、ステータス SQL_ROW_NO_ROWS を持たないすべての行の数です)。呼び出しの後に**SQLBulkOperations**または**SQLSetPos**バッファーには、関数によって実行される一括操作の影響を受けた行の数が含まれています。 SQL_ATTR_ROW_STATUS_PTR ステートメント属性が設定されている場合**SQLFetch**または**SQLFetchScroll**を返します、*行状態配列、* ごとの状態を提供します。返された行。 アプリケーションによって割り当てられているこれらのフィールドによって示されるバッファーの両方は、およびドライバーによって設定します。 アプリケーションは、カーソルが閉じられるまで、これらのポインターが有効なままいることを確認してください。  
  
 行の状態配列内のエントリが更新されたかどうかが正常に、各の行がフェッチされたかどうかは、追加、または、行をフェッチ中にエラーが発生したかどうかと、前回のフェッチ後、削除します。 場合**SQLFetch**または**SQLFetchScroll**複数行の行セットの 1 つの行を取得中にエラーが発生した場合、または**SQLBulkOperations**で、*操作* SQL_FETCH_BY_BOOKMARK の引数には、一括フェッチを実行中にエラーが発生した、SQL_ROW_ERROR 行の状態配列内の対応する値を設定、引き続き、行をフェッチし、sql_success_with_info が返されます。 エラー処理と行の状態配列の詳細については、次を参照してください。、 [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)と[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)関数の説明。
