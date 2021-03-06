---
title: 環境ハンドル |Microsoft ドキュメント
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
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a84e7d5939eb4d4c57b7f59db6d719627cf4be3b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911437"
---
# <a name="environment-handles"></a>環境ハンドル
*環境*はデータにアクセスするためのグローバル コンテキストは、環境に関連付けられているなど、本質的にグローバルに適用される情報。  
  
-   環境の状態  
  
-   現在の環境レベルの診断  
  
-   環境に現在割り当てられている接続の処理  
  
-   環境の各属性の現在の設定  
  
 ODBC ドライバー マネージャー (ドライバー) を実装するコードの部分、内では、環境ハンドルは、この情報を格納する構造体を識別します。  
  
 環境ハンドルは、ODBC アプリケーションで頻繁には使用されません。 呼び出しで常に使用される**SQLDataSources**と**SQLDrivers**への呼び出しでときどき使わと**SQLAllocHandle**、 **SQLEndTran**、**SQLFreeHandle**、 **SQLGetDiagField**、および**SQLGetDiagRec**です。  
  
 ODBC ドライバー マネージャー (ドライバー) を実装するコードの各部分には、1 つまたは複数の環境ハンドルが含まれています。 たとえば、ドライバー マネージャーは、それに接続されている各アプリケーションの別の環境ハンドルを保持します。 環境ハンドルが割り当てられます**SQLAllocHandle**およびに解放された**SQLFreeHandle**です。
