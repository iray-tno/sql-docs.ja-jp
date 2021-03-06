---
title: 評価レポート (MySQLToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 5525d989-024c-402d-9e84-faa4721cc5b9
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 602509c1c8d1f2de14513e67e4d850da24774e7a
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34775658"
---
# <a name="assessment-report-mysqltosql"></a>評価レポート (MySQLToSQL)
評価 [レポート] ウィンドウは、データベース オブジェクトの変換結果を示しています。[!INCLUDE[tsql](../../includes/tsql_md.md)]構文、およびヘルプの複雑さと、移行プロジェクトの費用を見積もることができます。  
  
ソース メタデータ エクスプ ローラーで、変換するオブジェクトの選択、評価レポートにアクセスを右クリックして**スキーマ**、し、**レポートの作成**です。  
  
## <a name="options"></a>および  
  
|||  
|-|-|  
|**項目**|**定義**|  
|**変換の統計情報**|ステートメントの種類別の変換の統計情報を示します。 このウィンドウは、スキーマなどのグループ オブジェクトのときに表示されるまたは左側のウィンドウでコードがないオブジェクトを選択します。|  
|**カテゴリ別にオブジェクト**|カテゴリ別のオブジェクトの数を示します。 このウィンドウは、スキーマなどのグループ オブジェクト場合にのみ表示または左側のウィンドウでコードがないオブジェクトを選択します。|  
|**統計**|選択したオブジェクトの変換の統計情報を示します。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。 展開する必要があります**統計**をすぐに、**ソース** ウィンドウでこのウィンドウを表示します。|  
|**ソース**|変換されていないコードを示し、選択したオブジェクトの MySQL コードを示しています[!INCLUDE[tsql](../../includes/tsql_md.md)]です。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。<br /><br />行番号を設定またはブックマークをクリア をクリックします。 ウィンドウの上部にあるボタンを使用して、コード内を移動します。|  
|**移行先**|変換の結果を示しています。[!INCLUDE[tsql](../../includes/tsql_md.md)]は変換されていないコードのエラー メッセージと、選択したオブジェクトのコード。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。<br /><br />行番号を設定またはブックマークをクリア をクリックします。 ウィンドウの上部にあるボタンを使用して、コード内を移動します。|  
|**[メッセージ] ウィンドウ**|エラー、警告、および評価レポートを作成するときに生成された情報のメッセージを示しています。 メッセージは、番号でグループ化されます。 エラーの原因となったコードを表示するクリックして**エラー**、**警告**、または**情報**メッセージのカテゴリを展開し、[メッセージ] をクリックします。|  
  
