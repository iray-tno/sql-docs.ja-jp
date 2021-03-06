---
title: sp_revoke_proxy_from_subsystem (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_revoke_login_from_subsystem
- sp_revoke_login_from_subsystem_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revoke_proxy_from_subsystem
ms.assetid: b87bc8ba-3ea8-4aed-b54b-32c3d82d9d2a
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c80739e4a888316837b22838b92f6d5919c998d0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33261862"
---
# <a name="sprevokeproxyfromsubsystem-transact-sql"></a>sp_revoke_proxy_from_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブシステムに対するアクセス権をプロキシから取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_revoke_proxy_from_subsystem   
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>引数  
 [ **@proxy_id** =] *id*  
 アクセス権を取り消すプロキシのプロキシ識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。 いずれか*proxy_id*または*proxy_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@proxy_name** =] **'***proxy_name***'**  
 アクセス権を取り消すプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。 いずれか*proxy_id*または*proxy_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@subsystem_id** =] *id*  
 取り消すアクセス権の対象となるサブシステムの ID 番号を指定します。 *Subsystem_id*は**int**、既定値は NULL です。 いずれか*subsystem_id*または*subsystem_name*指定する必要がありますが、両方を指定することはできません。 次の表は、各サブシステムの ID に指定できる値の一覧です。  
  
|値|説明|  
|-----------|-----------------|  
|**2**|ActiveX スクリプト<br /><br /> **\*\* 重要な \*\*** ActiveX スクリプティング サブシステムはから削除する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の将来のバージョンのエージェント[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。|  
|**3**|オペレーティング システム (CmdExec)|  
|**4**|レプリケーション スナップショット エージェント|  
|**5**|レプリケーション ログ リーダー エージェント|  
|**6**|レプリケーション ディストリビューション エージェント|  
|**7**|レプリケーション マージ エージェント|  
|**8**|レプリケーション キュー リーダー エージェント|  
|**9**|Analysis Services コマンド|  
|"**10**"|Analysis Services クエリ|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ実行|  
|**12**|PowerShell スクリプト|  
  
 [ **@subsystem_name**=] **'***subsystem_name***'**  
 取り消すアクセス権の対象となるサブシステムの名前を指定します。 *Subsystem_name*は**sysname**、既定値は NULL です。 いずれか*subsystem_id*または*subsystem_name*指定する必要がありますが、両方を指定することはできません。 次の表は、各サブシステムの ID に指定できる値の一覧です。  
  
|値|Description|  
|-----------|-----------------|  
|ActiveScripting|ActiveX スクリプト|  
|CmdExec|オペレーティング システム (CmdExec)|  
|スナップショット|レプリケーション スナップショット エージェント|  
|LogReader|レプリケーション ログ リーダー エージェント|  
|Distribution|レプリケーション ディストリビューション エージェント|  
|Merge|レプリケーション マージ エージェント|  
|QueueReader|レプリケーション キュー リーダー エージェント|  
|ANALYSISQUERY|Analysis Services コマンド|  
|ANALYSISCOMMAND|Analysis Services クエリ|  
|Dts|[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ実行|  
|PowerShell|PowerShell スクリプト|  
  
## <a name="remarks"></a>解説  
 サブシステムへのアクセス権を取り消しても、プロキシで指定されているプリンシパルに対する権限は変更されません。  
  
> [!NOTE]  
>  プロキシを参照するジョブ ステップを特定するのには、右、**プロキシ**ノードの下**SQL Server エージェント**microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、クリックして**プロパティ**です。 **プロキシ アカウントのプロパティ**ダイアログ ボックスで、**参照**このプロキシを参照するすべてのジョブ ステップを表示するページ。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_revoke_proxy_from_subsystem**です。  
  
## <a name="examples"></a>使用例  
 次の例では、プロキシ `Catalog application proxy` が持つ [!INCLUDE[ssIS](../../includes/ssis-md.md)] サブシステムへのアクセス権を取り消します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_revoke_proxy_from_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_name = N'Dts';  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [SQL Server エージェントのセキュリティを実装します。](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_grant_proxy_to_subsystem &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
