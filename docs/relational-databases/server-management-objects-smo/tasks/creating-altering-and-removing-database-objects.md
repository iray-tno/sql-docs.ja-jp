---
title: データベース オブジェクトの操作 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 37b8491bc441db0a2457ea4d87e6bb372326cafb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32966587"
---
# <a name="creating-altering-and-removing-database-objects"></a>作成、変更、およびデータベース オブジェクトを削除します。
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  SMO オブジェクトの作成には次の段階があります。  
  
1.  オブジェクトのインスタンスの作成。  
  
2.  オブジェクト プロパティの設定。  
  
3.  子オブジェクトのインスタンスの作成。  
  
4.  子オブジェクト プロパティの設定。  
  
5.  オブジェクトの作成。  
  
 インスタンスに存在しない、SMO アプリケーションで SMO オブジェクトのインスタンスが作成されると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]まで、**作成**メソッドを発行します。 ただし、発行する必要はありません、**作成**個々 のオブジェクトに対してメソッドです。 親オブジェクトのみが実行に必要なオブジェクトに子オブジェクトのセットがある場合、**作成**メソッドです。 たとえば、テーブルの定義には、テーブルに含まれている列が 1 つ以上必要になります。 一方、テーブルがなくては列が独立して存在することはできません。 テーブルとテーブルの列の間には共存関係があります。  
  
 <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> メソッドを使用すると、オブジェクトへの変更を行うことができます。 オブジェクト コレクションの 1 つへの子オブジェクトの追加や、プロパティ値の変更など、1 つのオブジェクトに対する複数の変更は、バッチ化されて 1 つの変更として実行されます。 **Alter**メソッドは、ネットワーク トラフィックが減少し、全体的なパフォーマンスが向上します。  
  
 **ドロップ**オブジェクトおよびオブジェクトを最初に作成する必要があるをすべての共存子オブジェクトを削除するステートメントを使用します。  
  
## <a name="see-also"></a>参照  
 [SMO オブジェクト モデル](../../../relational-databases/server-management-objects-smo/smo-object-model.md)  
  
  
