---
title: sysarticleupdates (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysarticleupdates_TSQL
- sysarticleupdates
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticleupdates system table
ms.assetid: 11a53bcd-a215-4d0b-9db8-233981d3ef5d
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 384e6abd93369bd1913bddf31b8dec6f8541e0d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33005579"
---
# <a name="sysarticleupdates-transact-sql"></a>sysarticleupdates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  即時更新するサブスクリプションをサポートするアーティクルごとに、1 行のデータを格納します。 このテーブルは、レプリケートされたデータベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの一意な ID 番号を示す ID 列。|  
|**pubid**|**int**|そのアーティクルが属するパブリケーションの ID です。|  
|**sync_ins_proc**|**int**|挿入同期トランザクションを処理するストアド プロシージャの ID。|  
|**sync_upd_proc**|**int**|更新同期トランザクションを処理するストアド プロシージャの ID。|  
|**sync_del_proc**|**int**|削除同期トランザクションを処理するストアド プロシージャの ID。|  
|**autogen**|**bit**|ストアド プロシージャが自動的に生成されるかどうかを示します。<br /><br /> **0** = false、自動ではありません。<br /><br /> **1**自動 = true、します。|  
|**sync_upd_trig**|**int**|アーティクル テーブルでの、自動バージョン トリガーの ID。|  
|**conflict_tableid**|**int**|競合テーブルの ID。|  
|**ins_conflict_proc**|**int**|競合を書き込むためのプロシージャの ID、 **conflict_table**です。|  
|**identity_support**|**bit**|キュー更新の使用時に、ID 範囲の自動処理が有効かどうかを示します。 **0**範囲サポートの識別情報がないことを意味します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
