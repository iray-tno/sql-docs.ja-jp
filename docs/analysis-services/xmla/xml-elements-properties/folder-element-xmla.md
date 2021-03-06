---
title: Folder 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 47919671460d83e4b7c470c110da8d002c6ba53f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575154"
---
# <a name="folder-element-xmla"></a>Folder 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  更新するファイル システム ストレージの場所が含まれています、[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)実行中に、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)または[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Folders>  
   ...  
   <Folder>  
      <Original>...</Original>  
      <New>...</New>  
   </Folder>  
   ...  
</Folders>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|子要素|[新しい](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md)、[元](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **フォルダー**要素を指定すると、変更、記憶域オブジェクトの場所に含まれるバックアップ ファイル (の**復元**コマンド) またはソース インスタンス上のデータベース (の**同期**コマンド) の値に一致する、**元**要素の値を**新規**要素。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
## <a name="see-also"></a>参照
 [StorageLocation 要素&#40;ASSL&#41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
