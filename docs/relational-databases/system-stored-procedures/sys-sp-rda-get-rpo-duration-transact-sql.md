---
title: sys.sp_rda_get_rpo_duration (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_get_rpo_duration
- sys.sp_rda_get_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_get_rpo_duration stored procedure
ms.assetid: 35882067-3072-47ff-9024-ca453c0f49a7
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 92ebe382c16c270fea93cd3040141757d530869c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32998499"
---
# <a name="syssprdagetrpoduration-transact-sql"></a>sys.sp_rda_get_rpo_duration (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  確実に、リモート Azure データベースの完全復元ポイントイン タイム復元が必要な場合にステージング テーブル内の SQL Server が保持される移行データの時間数を取得します。 
  
  詳細については、次を参照してください。 [Stretch Database が移行された行を一時的に保持して、Azure データのデータ損失のリスクを軽減](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)です。  
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>構文    
    
```    
    
sp_rda_get_rpo_duration @durationinhours output    
    
```    
    
## <a name="output-parameter"></a>出力パラメーター    
 *@durationinhours*    
  時間の数です (null 以外の整数値) の SQL Server が現在の拡張が有効なデータベースが保持される移行データ。    
    
## <a name="permissions"></a>権限    
 Db_owner アクセス許可が必要です。    
    
## <a name="remarks"></a>解説    
 実行して、値を変更する[sys.sp_rda_set_rpo_duration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)です。    
    
## <a name="see-also"></a>参照    
 [sys.sp_rda_set_rpo_duration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)     
 [データベースの復元 Stretch が有効な (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)    
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
