---
title: "トレースの作成 (Transact-SQL) | Microsoft Docs"
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
  - "トレース [SQL Server], 例"
  - "トレース [SQL Server], 作成"
ms.assetid: 79dd4254-e3c6-467a-bb6f-f99e51757e99
caps.latest.revision: 19
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 19
---
# トレースの作成 (Transact-SQL)
  このトピックでは、ストアド プロシージャを使用してトレースを作成する方法について説明します。  
  
### トレースを作成するには  
  
1.  必要なパラメーターを指定して **sp_trace_create** を実行し、新しいトレースを作成します。 新しいトレースは停止状態 (*status* の値が **0**) になります。  
  
2.  必要なパラメーターを指定して **sp_trace_setevent** を実行し、トレースするイベントおよび列を選択します。  
  
3.  必要に応じて、**sp_trace_setfilter** を実行し、フィルターまたはフィルターの組み合わせを設定します。  
  
     **sp_trace_setevent** と **sp_trace_setfilter** は、停止状態の既存のトレースに対してのみ実行できます。  
  
    > [!IMPORTANT]  
    >  通常のストアド プロシージャとは異なり、すべての SQL Server Profiler ストアド プロシージャ (**sp_trace_*xx***) のパラメーターでは、データ型が厳密に定義されており、データ型の自動変換はサポートされていません。 これらのパラメーターが、引数の説明で指定されている正しいデータ型で呼び出されないと、このストアド プロシージャではエラーが返されます。  
  
## 例  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してトレースを作成するコードを次に示します。 トレースの作成、トレース ファイルの設定、およびトレースの停止の、3 つのセクションで構成されています。 トレースするイベントを追加して、トレースをカスタマイズしてください。 イベントと列の一覧については、「[sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)」を参照してください。  
  
 次のコードでは、トレースを作成してイベントを追加し、トレースを開始します。  
  
```  
DECLARE @RC int, @TraceID int, @on BIT  
EXEC @rc = sp_trace_create @TraceID output, 0, N'C:\SampleTrace'  
  
-- Select the return code to see if the trace creation was successful.  
SELECT RC = @RC, TraceID = @TraceID  
  
-- Set the events and data columns you need to capture.  
SELECT @on = 1  
  
-- 10 is RPC:Completed event. 1 is TextData column.   
EXEC sp_trace_setevent @TraceID, 10, 1, @on   
-- 13 is SQL:BatchStarting, 11 is LoginName  
EXEC sp_trace_setevent @TraceID, 13, 11, @on   
-- 13 is SQL:BatchStarting, 14 is StartTime  
EXEC sp_trace_setevent @TraceID, 13, 14, @on   
-- 12 is SQL:BatchCompleted, 15 is EndTime  
EXEC sp_trace_setevent @TraceID, 12, 15, @on   
-- 13 is SQL:BatchStarting, 1 is TextData  
EXEC sp_trace_setevent @TraceID, 13, 1, @on   
  
-- Set any filter. Not provided in this example  
--EXEC sp_trace_setfilter 1, 10, 0, 6, N'%Profiler%'  
  
-- Start Trace (status 1 = start)  
EXEC @RC = sp_trace_setstatus @TraceID, 1  
GO  
  
```  
  
## 例  
 トレースが作成および開始されたので、次のコードを実行して、トレースにアクティビティを設定します。  
  
```  
SELECT * FROM master.sys.databases  
GO  
SELECT * FROM ::fn_trace_getinfo(default)  
GO  
  
```  
  
## 例  
 トレースは、いつでも停止および再開できます。 この例では次のコードを実行して、トレースを停止し、閉じ、トレース定義を削除します。  
  
```  
DECLARE @TraceID int  
-- Populate a variable with the trace_id of the current trace  
SELECT  @TraceID = TraceID FROM ::fn_trace_getinfo(default) WHERE VALUE = N'C:\SampleTrace.trc'  
  
-- First stop the trace.   
EXEC sp_trace_setstatus @TraceID, 0  
  
-- Close and then delete its definition from SQL Server.   
EXEC sp_trace_setstatus @TraceID, 2  
  
```  
  
## 例  
 トレース ファイルを調べるには、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して SampleTrace.trc ファイルを開きます。  
  
## 参照  
 [SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)  
  
  