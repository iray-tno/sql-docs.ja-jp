---
title: "SQL Server ユーティリティからの SQL Server のインスタンスの削除 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.utility.remove.f1"
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# SQL Server ユーティリティからの SQL Server のインスタンスの削除
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスを削除するには、次の手順を実行します。 この手順では、UCP リスト ビューから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが削除されるため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのデータ収集が停止します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスはアンインストールされません。  
  
> [!IMPORTANT]  
>  この手順を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを削除する前に、削除するインスタンス上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および SQL Server エージェントのサービスが実行されていることを確認します。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のユーティリティ エクスプローラーで、**[マネージ インスタンス]** をクリックします。 ユーティリティ エクスプローラーのコンテンツ ウィンドウで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスのリスト ビューを確認します。  
  
2.  リスト ビューの **[SQL Server インスタンス名]** 列で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを選択します。 削除するインスタンスを右クリックし、**[マネージ インスタンスの削除]** をクリックします。  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに、管理者特権のある資格情報を指定します。これには、**[接続]** をクリックし、**[サーバーへの接続]** ダイアログ ボックスで情報を確認して、**[接続]** をクリックします。 **[マネージ インスタンスの削除]** ダイアログ ボックスにログイン情報が表示されます。  
  
4.  操作を実行する場合は **[OK]** をクリックします。 操作を終了する場合は **[キャンセル]** をクリックします。  
  
## SQL Server ユーティリティから SQL Server のマネージ インスタンスを手動で削除する  
 この手順では、UCP リスト ビューから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが削除され、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのデータ収集が停止されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスはアンインストールされません。  
  
 PowerShell を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスを削除するには、 このスクリプトで、次の操作を実行します。  
  
-   サーバー インスタンス名で UCP を取得します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除します。  
  
```  
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object –Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に格納されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名を正確に参照することが重要です。 大文字と小文字を区別する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの場合、@@SERVERNAME によって返された文字種を正確に使用して、インスタンス名を指定する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスのインスタンス名を取得するには、マネージ インスタンスで次のクエリを実行します。  
  
```  
select @@SERVERNAME AS instance_name  
```  
  
 この時点で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスは UCP から完全に削除されます。 このインスタンスは、次に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのデータを更新すると、リスト ビューに表示されなくなります。 この状態は、ユーザーが SSMS ユーザー インターフェイスで、マネージ インスタンスの削除操作を正常に完了した場合と同じです。  
  
## 参照  
 [ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [SQL Server ユーティリティのトラブルシューティング](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  