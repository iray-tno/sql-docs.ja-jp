---
title: "MSSQL_ENG014164 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014164 エラー"
ms.assetid: cd81b601-2ec3-4358-ad58-c2655496e6a1
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# MSSQL_ENG014164
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14164|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|パブリケーション [%s] のしきい値 [%s:%s] が設定されています。 マージ エージェントが実行されており、必要な要件に適合することを確認してください。|  
  
## 説明  
 レプリケーションでは、いくつかの条件に対して警告を有効にできます。 これには、マージ パブリッシャーとサブスクライバー間で変更を同期する際、十分な数の行を処理できないエラーも含まれます。 LAN 接続とダイヤルアップ接続には異なる時間を指定できます。  
  
 レプリケーション モニターを使用して、警告を有効にすると、または [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), 、警告がトリガーされたときを決定するしきい値を指定します。 指定したしきい値に達するか、そのしきい値を超えた場合、警告がレプリケーション モニターに表示され、イベントが Windows イベント ログに書き込まれます。 しきい値に達した時点で、SQL Server エージェントの警告を表示させることもできます。 詳細については、次を参照してください。 [しきい値の設定とレプリケーション モニターで警告](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) と [プログラムでレプリケーションの監視](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)します。  
  
## ユーザーの操作  
 サブスクリプションが行処理しきい値に達していない場合、システムでパフォーマンスの問題が発生しているかどうか、またはしきい値を調整する必要があるかどうかを確認する必要があります。 レプリケーションを構成したら、パフォーマンス基準を策定します。これにより、アプリケーションおよびトポロジにおける通常のワークロードに対するレプリケーションの動作方法について判断できるようになります。 このパフォーマンス基準に処理される行数を組み入れ、適切なしきい値を設定できるようにします。  
  
 しきい値が適切でも、その値を超えた場合は、システム内のパフォーマンスのボトルネックになる部分を特定する必要があります。 レプリケーション パフォーマンスの監視とトラブルシューティングを行う方法の詳細については、次のトピックを参照してください。  
  
-   [レプリケーション モニターでパフォーマンスを監視](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) (特にセクション「を表示する詳細な同期パフォーマンスのマージ レプリケーション)  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  