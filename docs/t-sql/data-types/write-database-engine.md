---
title: Write (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 4a420df5291b958f4f7a5882808fdf6b8bfb308b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="write-database-engine"></a>Write (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

書き込み のバイナリ表現を書き込みます **SqlHierarchyId** を渡されたに **BinaryWriter**です。 書き込み [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して呼び出すことができない です。 代わりに、CAST または CONVERT を使用してください。
  
## <a name="syntax"></a>構文  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>引数  
*w*  
wA **BinaryWriter** オブジェクトをこのバイナリ表現 **hierarchyid** ノードが書き出されます。
  
## <a name="return-types"></a>戻り値の型  
**CLR の戻り値の型: void**
  
## <a name="remarks"></a>Remarks  
書き込み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部で使用される 必要な場合など**からデータを読み込むときに、 hierarchyid** 列です。 Write は、**hierarchyid** と **varbinary**間で変換が行われる場合も呼び出されます。
  
## <a name="examples"></a>使用例  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>参照
[読み取りと #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/read-database-engine.md)  
[ToString (&) #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/tostring-database-engine.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
