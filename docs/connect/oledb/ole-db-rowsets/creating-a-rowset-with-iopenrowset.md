---
title: IOpenRowset による行セットの作成 |Microsoft ドキュメント
description: SQL Server 用の OLE DB Driver IOpenRowset インターフェイスを持つ行セットの作成
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d518a5e7f2b4f5823317f20bd1669d8bd3adeeb7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-rowset-with-iopenrowset"></a>IOpenRowset を使用した行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL Server の OLE DB ドライバーをサポートしている、 **iopenrowset::openrowset**メソッドを次の制限。  
  
-   ベース テーブルまたはビューを指定してください、データベースの ID (DBID) 構造体、 *pTableID*パラメーターをポイントします。  
  
-   DBID *eKind*メンバーは dbkind_name に示す必要があります。  
  
-   DBID *uName*メンバーは、Unicode 文字の文字列として既存の基本テーブルまたはビューの名前を指定する必要があります。  
  
-   *PIndexID*のパラメーター **OpenRowset** NULL にする必要があります。  
  
 結果セットは**iopenrowset::openrowset**単一の行セットが含まれています。 単一の行セットを含む結果セットをサポートできる[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソル。 開発者はカーソル サポートによって、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の同時実行メカニズムを使用できます。  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
