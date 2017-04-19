---
title: "DQS ログ ファイルの詳細設定の構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログ ファイル, 詳細設定"
  - "dqs ログ ファイル, 詳細設定"
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# DQS ログ ファイルの詳細設定の構成
  このトピックでは、[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログ ファイルと [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ログ ファイルの詳細設定を構成する方法 (ログ ファイルのローリング ファイル サイズの制限の設定、イベントのタイム スタンプ パターンの設定など) について説明します。  
  
> [!NOTE]  
>  これらのアクティビティは [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] を使用して実行できません。また、これらのアクティビティは上級ユーザーだけが実行できます。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
  
-   DQS_MAIN データベースの A_CONFIGURATION テーブルで構成の設定を変更するには、Windows ユーザー アカウントが SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。  
  
-   [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のログ設定を構成するには、DQLog.Client.xml ファイルを変更するコンピューターの Administrators グループのメンバーとしてログオンする必要があります。  
  
##  <a name="DQSServer"></a> Data Quality Server のログ設定の構成  
  [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログの設定は XML 形式で存在、 **値** の列、 **ServerLogging** DQS_MAIN データベースの A_CONFIGURATION テーブル内の行。 構成情報を表示するには、次の SQL クエリを実行します。  
  
```  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
```  
  
 該当する情報を更新する必要があります、 **値** の列、 **ServerLogging** の構成設定を変更する行 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログ記録します。 この例では、[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログ設定を更新して、ローリング ファイルのサイズ制限を 25000 KB (既定値は 20000 KB) に設定します。  
  
1.  Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。  
  
2.  オブジェクト エクスプ ローラーで、サーバーを右クリックし、をクリックして **新しいクエリ**します。  
  
3.  クエリ エディター ウィンドウで、SQL ステートメントをコピーします。  
  
    ```  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  F5 キーを押してステートメントを実行します。 **[結果]** ペインを確認してステートメントが正常に実行されたことを確認します。  
  
5.  [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のログ構成の変更を適用するには、次の Transact-SQL ステートメントを実行する必要があります。 新しいクエリ エディター ウィンドウを開き、次の Transact-SQL ステートメントを貼り付けます。  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
  
    ```  
  
6.  F5 キーを押してステートメントを実行します。 **[結果]** ペインを確認してステートメントが正常に実行されたことを確認します。  
  
> [!NOTE]  
>   [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] は、動的に生成され、DQS_MAIN に格納されているログ設定の構成。通常、C:\Program files \microsoft SQL Server\MSSQL13 で利用可能なログ ファイルです。SQL Server の既定のインスタンスがインストールされている場合は、MSSQLSERVER\MSSQL\Log です。 ただし、このファイルで直接変更した内容は保持されず、DQS_MAIN データベースの A_CONFIGURATION テーブルの構成設定で上書きされます。  
  
##  <a name="DQSClient"></a> Data Quality Client のログ設定の構成  
  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ログ設定の構成ファイルである DQLog.Client.xml は C:\Program files \microsoft SQL Server\130\Tools\Binn\DQ\config で通常使用できます。 この XML ファイルの内容は、前に [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のログ構成設定で変更した XML ファイルと似ています。 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のログ設定を構成するには、次の手順を実行します。  
  
1.  管理者として、任意の XML 編集ツールやメモ帳を実行します。  
  
2.  DQLog.Client.xml ファイルをツールやメモ帳で開きます。  
  
3.  必要な変更を行い、ファイルを保存して、新しいログの変更を適用します。  
  
## 参照  
 [Configure Severity Levels for DQS Log Files](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  