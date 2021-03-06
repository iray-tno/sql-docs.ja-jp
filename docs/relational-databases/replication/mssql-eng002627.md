---
title: MSSQL_ENG002627 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002627 error
ms.assetid: 7f4136ac-3784-4a41-a98c-8a02308e4883
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 73325c4e30524ff5d1b9db33491cec9df1d2ea33
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32958717"
---
# <a name="mssqleng002627"></a>MSSQL_ENG002627
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2627|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名|なし|  
|メッセージ テキスト|制約 '%.*ls' の %ls 違反。 オブジェクト '%.\*ls' には重複したキーを挿入できません。|  
  
## <a name="explanation"></a>説明  
 このエラーは、データベースがレプリケートされたかどうかにかかわらず発生する一般エラーです。 レプリケートされたデータベースでは、このエラーは、一般に主キーがトポロジ間で適切に管理されなかった場合に発生します。 分散環境では、主キー列などの一意の列に複数のノードで同じ値が挿入されないようにすることが不可欠です。 以下のような原因が考えられます。  
  
-   行の挿入と更新が複数のノードで行われた。 マージ レプリケーションとトランザクション レプリケーションの更新可能なサブスクリプションには、どちらも競合を検出して解決する機能がありますが、それでも行を 1 つのノード上だけで挿入または更新することが推奨されます。 ピア ツー ピアのトランザクション レプリケーションでは、競合を検出し解決する機能はありません。挿入と更新をパーティション分割する必要があります。  
  
-   読み取り専用のサブスクライバーで行が挿入された。 更新可能なサブスクリプションまたはピア ツー ピアのトランザクション レプリケーションを使用していない場合、スナップショット パブリケーションのサブスクライバーは、トランザクション パブリケーションのサブスクライバーと同様に、読み取り専用として扱われる必要があります。  
  
-   ID 列を持つテーブルが使用されているが、列が正しく管理されていない。  
  
## <a name="user-action"></a>ユーザーの操作  
 必要なアクションは、エラーが発生した原因によって異なります。  
  
-   行の挿入と更新が複数のノードで行われた。  
  
     使用するレプリケーションの種類にかかわらず、できる限り挿入と更新をパーティション分割することをお勧めします。これにより、競合の検出と対処に必要な処理を減らすことができます。 ピア ツー ピアのトランザクション レプリケーションの場合は、挿入と更新のパーティション分割は必須です。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
-   読み取り専用のサブスクライバーで行が挿入された。  
  
     マージ レプリケーション、更新可能なサブスクリプションを使用したトランザクション レプリケーション、またはピア ツー ピアのトランザクション レプリケーションを使用していない場合は、サブスクライバーで行を挿入または更新しないでください。  
  
-   ID 列を持つテーブルが使用されているが、列が正しく管理されていない。  
  
     マージ レプリケーションおよび更新可能なサブスクリプションを使用したトランザクション レプリケーションの場合は、ID 列はレプリケーションで自動的に管理してください。 ピア ツー ピアのトランザクション レプリケーションの場合は、手動で管理する必要があります。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [マージ レプリケーション](../../relational-databases/replication/merge/merge-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
