---
title: ISSAsynchStatus (OLE DB) |Microsoft ドキュメント
description: ISSAsynchStatus (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ca37010f2c0c0e42dd7e75f2dc87b0654fb31474
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **ISSAsynchStatus**インターフェイスのサポートが公開[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]非同期操作です。 これは、主要な OLE DB インターフェイスから継承される省略可能なインターフェイス**IDBAsynchStatus**です。 加え、**中止**と**GetStatus**から継承されたメソッド**IDBAsynchStatus**、 **ISSAsynchStatus** 1 つの新しいメソッドを提供します。非同期操作が完了したか、タイムアウトが発生するまで待機するを使用します。  
  
|方法|Description|  
|------------|-----------------|  
|[Issasynchstatus::abort &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-abort-ole-db.md)|非同期に実行されている操作を取り消します。|  
|[Issasynchstatus::getstatus &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|非同期に実行されている操作の状態を返します。|  
|[Issasynchstatus::waitforasynchcompletion &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|非同期に実行されている操作が完了するかタイムアウトが発生するまで待機します。|  
  
## <a name="remarks"></a>解説  
 **ISSAsynchStatus**の実装、 **issasynchstatus::getstatus**メソッドと同じ、 **idbasynchstatus::getstatus**似ているが、メソッド、データ ソース オブジェクトの初期化が中止されると、E_UNEXPECTED が返される DB_E_CANCELED ではなく (ただし**issasynchstatus::waitforasynchcompletion** DB_E_CANCELED が返されます)。 データ ソース オブジェクトされていない状態で残るため、通常中止操作では、次の追加の初期化操作が試行されることをお勧めします。  
  
 次に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の非同期実行の使用をサポートしているメソッドを示します。  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>参照  
 [インターフェイス (&) #40";"OLE DB"&"#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [非同期操作の実行](../../oledb/features/performing-asynchronous-operations.md)  
  
  
