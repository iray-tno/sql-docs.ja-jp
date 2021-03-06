---
title: Create 要素 (DTA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f27263bc2d9506dc233793e335842c96061f988b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33070199"
---
# <a name="create-element-dta"></a>Create 要素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ユーザー指定の構成内のインデックス、統計、ヒープ構造に関する情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|物理デザイン構造の各種類 (インデックス、統計、ヒープ構造) につき 1 回の出現が必要です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Recommendation 要素 &#40;DTA&#41;](../../tools/dta/recommendation-element-dta.md)|  
|**子要素**|[Index 要素 &#40;DTA&#41;](../../tools/dta/index-element-dta.md)<br /><br /> **Statistics** 要素 (詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://schemas.microsoft.com/sqlserver/) を参照してください)<br /><br /> **Heap** 要素 (詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://schemas.microsoft.com/sqlserver/) を参照してください)|  
  
## <a name="remarks"></a>Remarks  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **CreateTypecomplexType** の名前です。 ユーザー指定の構成でインデックス、統計、ヒープ構造を作成するために使用します。 この **Create** 要素を、ビューを作成するための**CreateViewType**やパーティション分割を作成するための**CreatePType**という他の種類の要素と混同しないでください。 これら他の種類の [Create](http://schemas.microsoft.com/sqlserver/) 要素の詳細については、 **データベース エンジン チューニング アドバイザーの XML スキーマ** を参照してください。  
  
## <a name="example"></a>例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
