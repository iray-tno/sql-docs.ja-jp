---
title: State プロパティ (SqlService クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- State Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
caps.latest.revision: 36
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 350d59fa026f16007cffd279f4f6298eeca86e6c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33009500"
---
# <a name="state-property-sqlservice-class"></a>State プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービスの現在の状態を取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.State [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスの状態を指定する uint32 値。  
  
 値は、次のいずれかを指定できます。  
  
 1  
 停止中。 サービスは停止しています。  
  
 2  
 開始保留中。 サービスは開始を待機しています。  
  
 3  
 停止保留中。 サービスは停止を待機しています。  
  
 4  
 実行中です。 サービスは実行中です。  
  
 5  
 継続保留中。 サービスは継続を待機しています。  
  
 6  
 一時停止保留中。 サービスは一時停止を待機しています。  
  
 7  
 一時停止。 サービスは一時停止しています。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
