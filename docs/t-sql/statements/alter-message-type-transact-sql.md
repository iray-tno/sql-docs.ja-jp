---
title: ALTER MESSAGE TYPE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER_MESSAGE_TYPE_TSQL
- ALTER MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER MESSAGE TYPE statement
- modifying message types
- message types [Service Broker], modifying
ms.assetid: 98c94176-2bdf-4725-b4bc-d33b6b14817d
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1989db77e1f786694e794a2626a544cc1659d9ea
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33700625"
---
# <a name="alter-message-type-transact-sql"></a>ALTER MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メッセージ型のプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER MESSAGE TYPE message_type_name  
   VALIDATION =  
    {  NONE   
     | EMPTY   
     | WELL_FORMED_XML   
     | VALID_XML WITH SCHEMA COLLECTION schema_collection_name }  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *message_type_name*  
 変更するメッセージ型の名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
 VALIDATION   
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] によって、この型のメッセージの本文が検証される方法を指定します。  
  
 なし  
 検証が実行されません。 メッセージ本文には何らかのデータが含まれることがあれば、NULL の場合もあります。  
  
 EMPTY  
 メッセージの本文は NULL であることが必要です。  
  
 WELL_FORMED_XML   
 メッセージの本文には、整形式の XML が含まれている必要があります。  
  
 VALID_XML_WITH_SCHEMA = *schema_collection_name*  
 メッセージの本文には、指定されたスキーマ コレクションのスキーマに準拠する XML が含まれている必要があります。 *schema_collection_name* は、既存の XML スキーマ コレクションの名前であることが必要です。  
  
## <a name="remarks"></a>Remarks  
 メッセージ型の検証を変更しても、既にキューに配布されているメッセージには影響しません。  
  
 メッセージ型の AUTHORIZATION を変更するには、ALTER AUTHORIZATION ステートメントを使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メッセージ型を変更する権限は、既定ではメッセージ型の所有者、**db_ddladmin** 固定データベース ロールまたは **db_owner** 固定データベース ロールのメンバーと **sysadmin** 固定サーバー ロールのメンバーに与えられています。  
  
 ALTER MESSAGE TYPE ステートメントがスキーマ コレクションを指定する場合、ステートメントを実行するユーザーは、指定されているスキーマ コレクションに対する REFERENCES 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、メッセージ型 `//Adventure-Works.com/Expenses/SubmitExpense` を変更し、メッセージ本文に整形式の XML ドキュメントが含まれることを要求します。  
  
```  
ALTER MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = WELL_FORMED_XML ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-message-type-transact-sql.md)   
 [DROP MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
