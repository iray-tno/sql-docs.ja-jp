---
title: "Progress Report: Online Index Operation イベント クラス | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Progress Report: Online Index Operation イベント クラス [SQL Server]"
ms.assetid: 491616c1-f666-4b16-a5ea-1192bf156692
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Progress Report: Online Index Operation イベント クラス
  Progress Report: Online Index Operation イベント クラスは、ビルド プロセスの実行時に、オンライン インデックス構築操作の進行状況を示します。  
  
## Progress Report: Online Index Operation イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|BigintData1|**bigint**|挿入された行数。|52|はい|  
|BigintData2|**bigint**|0 は直列実行プランです。それ以外の場合は、並列実行時のスレッド ID です。|53|はい|  
|ClientProcessID|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。|9|はい|  
|DatabaseID|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|可|  
|DatabaseName|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|可|  
|Duration|**bigint**|イベントにかかった時間 (マイクロ秒)。|13|はい|  
|EndTime|**datetime**|オンライン インデックス操作が完了した時刻。|15|可|  
|EventClass|**int**|イベントの種類 = 190。|27|いいえ|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|不可|  
|EventSubClass|**int**|イベント サブクラスの種類。<br /><br /> 1 = 起動<br /><br /> 2 = ステージ 1 実行開始<br /><br /> 3 = ステージ 1 実行終了<br /><br /> 4 = ステージ 2 実行開始<br /><br /> 5 = ステージ 2 実行終了<br /><br /> 6 = 挿入された行数<br /><br /> 7 = 完了<br /><br /> ステージ 1 は、基本オブジェクト (クラスター化インデックスまたはヒープ) を参照します。または、インデックス操作に非クラスター化インデックスが 1 つだけ含まれている場合に使用されます。 ステージ 2 は、インデックス構築操作に元の再構築されるインデックスと追加の非クラスター化インデックスの両方が含まれている場合に使用されます。  たとえば、オブジェクトに 1 つのクラスター化インデックスと複数の非クラスター化インデックスがある場合、'rebuild all' によってすべてのインデックスが再構築されます。 基本オブジェクト (クラスター化インデックス) はステージ 1 で再構築され、非クラスター化インデックスはすべてステージ 2 で再構築されます。|21|可|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|HostName|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|IndexID|**int**|イベントの影響を受けるオブジェクトに付けられたインデックス用の ID。|24|はい|  
|IsSystem|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|可|  
|LoginName|**nvarchar**|ユーザーのログイン名 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|可|  
|LoginSid|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|可|  
|NTDomainName|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|はい|  
|NTUserName|**nvarchar**|Windows のユーザー名。|6|可|  
|ObjectID|**int**|システムによって割り当てられたオブジェクト ID。|22|はい|  
|ObjectName|**nvarchar**|参照されているオブジェクトの名前。|34|はい|  
|PartitionId|**bigint**|作成されているパーティションの ID。|65|はい|  
|PartitionNumber|**int**|作成されているパーティションの序数。|25|はい|  
|ServerName|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|不可|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|可|  
|SPID|**int**|イベントが発生したセッションの ID。|12|はい|  
|StartTime|**datetime**|イベントの開始時刻。|14|可|  
|TransactionID|**bigint**|システムによって割り当てられたトランザクション ID。|4|はい|  
  
## 参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  