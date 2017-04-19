---
title: "PowerShell を使用した Always Encrypted の構成 | Microsoft Docs"
ms.custom: ""
ms.date: "09/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-security"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12f2bde5-e100-41fa-b474-2d2332fc7650
caps.latest.revision: 15
author: "stevestein"
ms.author: "sstein"
manager: "jhubbard"
caps.handback.revision: 13
---
# PowerShell を使用した Always Encrypted の構成
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

SqlServer PowerShell モジュールは、Azure SQL Database および SQL Server 2016 両方で [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) を構成するコマンドレットを提供します。

SqlServer モジュールの Always Encrypted 用コマンドレットのほとんどは、Always Encrypted キーまたは暗号化された列に格納されている機密データを操作するので、安全なコンピューターでコマンドレットを実行することが重要です。 Always Encrypted を管理するときは、SQL Server インスタンスをホストするコンピューターとは異なるコンピューターからコマンドレットを実行します。 

Always Encrypted の主な目的は、データベース システムが侵害されても、暗号化された機密データが確実に保護されるようにすることにあるので、SQL Server コンピューター上でキーまたは機密データを処理する PowerShell スクリプトが実行されると、機能の効果が低下したり無効になったりするおそれがあります。 セキュリティ関連のその他の推奨事項については、[Security Considerations for Key Management](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md#SecurityForKeyManagement) (キー管理でのセキュリティに関する考慮事項) をご覧ください。

個々のコマンドレットに関する記事へのリンクは[このページの下](#aecmdletreference)にあります。

## 前提条件

SQL Server インスタンスをホストしているコンピューターではない安全なコンピューターに [SqlServer モジュール](https://msdn.microsoft.com/library/mt740629.aspx)をインストールします。 

SqlServer モジュールをインストールするには、[SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) の最新版をインストールします。
*SqlServer* モジュールは *sqlps* モジュールとは異なることに注意してください。sqlps モジュールは Always Encrypted をサポートしていません。 詳細については、チームのブログ投稿「[SQL PowerShell - July 2016 Update](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update)」 (SQL PowerShell - 2016 年 7 月更新プログラム) をご覧ください。

## <a name="importsqlservermodule"></a> SqlServer モジュールをインポートする 

SqlServer モジュールを読み込むには:

1.  適切なスクリプト実行ポリシーを設定するには、**Set-ExecutionPolicy** コマンドレットを使用します。
2.  SqlServer モジュールをインポートするには、**Import-Module** コマンドレットを使用します。

次に示すのは SqlServer モジュールを読み込む例です。

```
# Import the SQL Server Module.  
Import-Module "SqlServer" 
```

## <a name="connectingtodatabase"></a> データベースに接続する

一部の Always Encrypted コマンドレットはデータベースのデータまたはメタデータを操作するので、最初にデータベースに接続する必要があります。 SqlServer モジュールを使用して Always Encrypted を構成するときに推奨されるデータベース接続方法は次の 2 つです。 
1. SQL Server PowerShell を使用して接続します。
2. SQL Server 管理オブジェクト (SMO) を使用して接続します。

### SQL Server PowerShell の使用

この方法は SQL Server の場合にのみ使用できます (Azure SQL Database では使用できません)。

SQL Server PowerShell では、ファイル システムのパスの操作に一般的に使用されているコマンドと同様の Windows PowerShell の別名を使用して、パスを操作できます。 ターゲットのインスタンスおよびデータベースに移動した後、後続のコマンドレットは次の例で示すようにそのデータベースをターゲットにします。

```
# Import the SqlServer module.
Import-Module "SqlServer"
# Navigate to the database in the remote instance.
cd SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
# List column master keys in the above database.
Get-SqlColumnMasterKey
```

 
データベースに移動する代わりに、汎用の **Path** パラメーターを使用してデータベース パスを指定することもできます。


```
# Import the SqlServer module.
Import-Module "SqlServer" 
# List column master keys for the specified database.
Get-SqlColumnMasterKey -Path SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
```
 
### SMO の使用

この方法は、Azure SQL Database と SQL Server の両方に使用できます。
SMO では、[データベース クラス](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.database.aspx)のオブジェクトを作成した後、コマンドレットの **InputObject** パラメーターを使用してデータベースに接続するオブジェクトを渡すことができます。


```
# Import the SqlServer module
Import-Module "SqlServer"  

# Connect to your database (Azure SQL database).
$serverName = "<Azure SQL server name>.database.windows.net"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Authentication = Active Directory Integrated"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName] 

# List column master keys for the specified database.
Get-SqlColumnMasterKey -InputObject $database
```


代わりに、パイプを使用することもできます。


```
$database | Get-SqlColumnMasterKey
```

## PowerShell を使用した Always Encrypted のタスク

- [PowerShell を使用して Always Encrypted キーの構成](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md) 
- [PowerShell を使用した Always Encrypted キーの交換](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
- [PowerShell を使用して列の暗号化の構成](../../../relational-databases/security/encryption/configure-column-encryption-using-powershell.md)


##  <a name="aecmdletreference"></a> Always Encrypted コマンドレット リファレンス

Always Encrypted では次の PowerShell コマンドレットを使用できます。

|コマンドレット |説明
|:---|:---
|**[Add-SqlAzureAuthenticationContext](https://msdn.microsoft.com/library/mt759815.aspx)**  |Azure への認証を実行し、認証トークンを取得します。
|**[Add-SqlColumnEncryptionKeyValue](https://msdn.microsoft.com/library/mt759817.aspx)**    |データベースの既存の列暗号化キー オブジェクトに新しく暗号化された値を追加します。
|**[Complete-SqlColumnMasterKeyRotation](https://msdn.microsoft.com/library/mt759791.aspx)**    |列マスター キーのローテーションを完了します。
|**[Get-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759814.aspx)** |データベースで定義されているすべての列暗号化キー オブジェクトを返すか、指定された名前の特定の列暗号化キー オブジェクトを返します。
|**[Get-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759782.aspx)** |データベースで定義されている列マスター キー オブジェクトを返すか、指定された名前の特定の列マスター キー オブジェクトを返します。
|**[Invoke-SqlColumnMasterKeyRotation](https://msdn.microsoft.com/library/mt759810.aspx)**  |列マスター キーのローテーションを開始します。
|**[New-SqlAzureKeyVaultColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759795.aspx)**    |Azure Key Vault に格納されている非対称キーを記述する SqlColumnMasterKeySettings オブジェクトを作成します。
|**[New-SqlCngColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759818.aspx)**  |Cryptography Next Generation (CNG) API をサポートするキー ストアに格納されている非対称キーを記述する SqlColumnMasterKeySettings オブジェクトを作成します。
|**[New-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759808.aspx)** |データベースに新しい列暗号化キー オブジェクトを作成します。
|**[New-SqlColumnEncryptionKeyEncryptedValue](https://msdn.microsoft.com/library/mt759794.aspx)**   |列暗号化キーの暗号化された値を生成します。
|**[New-SqlColumnEncryptionSettings](https://msdn.microsoft.com/library/mt759825.aspx)**    |1 つの列の暗号化に関する情報をカプセル化する新しい SqlColumnEncryptionSettings オブジェクトを作成します。CEK と暗号化の種類を含みます。
|**[New-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759813.aspx)** |データベースに新しい列マスター キー オブジェクトを作成します。
|**New-SqlColumnMasterKeySettings**|指定されたプロバイダーとキーのパスを使用して、列マスター キーの SqlColumnMasterKeySettings オブジェクトを作成します。
|**[New-SqlCspColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759784.aspx)**  |Cryptography API (CAPI) をサポートする暗号化サービス プロバイダー (CSP) によってキー ストアに格納されている非対称キーを記述する SqlColumnMasterKeySettings オブジェクトを作成します。
|**[Remove-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759786.aspx)**  |データベースから列暗号化キー オブジェクトを削除します。
|**[Remove-SqlColumnEncryptionKeyValue](https://msdn.microsoft.com/library/mt759783.aspx)** |データベースの既存の列暗号化キー オブジェクトから暗号化された値を削除します。
|**[Remove-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759800.aspx)**  |データベースから列マスター キー オブジェクトを削除します。
|**[Set-SqlColumnEncryption](https://msdn.microsoft.com/library/mt759790.aspx)**    |データベースの指定された列を暗号化、復号化、または再暗号化します。



## その他のリソース

- [Always Encrypted (Database Engine) (Always Encrypted (データベース エンジン))](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Always Encrypted のキー管理の概要](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Always Encrypted と .NET Framework Data Provider for SQL Server を使用する](../../../relational-databases/security/encryption/always-encrypted-client-development.md)
- [SQL Server Management Studio を使用した Always Encrypted の構成](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)
