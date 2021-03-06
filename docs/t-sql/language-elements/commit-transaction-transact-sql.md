---
title: COMMIT TRANSACTION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COMMIT
- COMMIT TRANSACTION
- COMMIT_TSQL
- COMMIT_TRANSACTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ending transactions [SQL Server]
- user-defined transactions [SQL Server]
- committed transactions
- transactions [SQL Server], ending
- marking end of transactions [SQL Server]
- implicit transactions
- distributed transactions [SQL Server], committed
- transactions [SQL Server], committed
- COMMIT TRANSACTION statement
- rolling back transactions, COMMIT TRANSACTION
ms.assetid: f8fe26a9-7911-497e-b348-4e69c7435dc1
caps.latest.revision: 53
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 95cf2d72d7e522d672ad791388a317cae8467ca3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="commit-transaction-transact-sql"></a>COMMIT TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  正常終了した暗黙的または明示的なトランザクションの終点をマークします。 @@TRANCOUNT が 1 の場合、COMMIT TRANSACTION はトランザクションの開始以降加えられたすべてのデータ修正をデータベースに永久保存し、そのトランザクションによって保持されているリソースを解放してから @@TRANCOUNT を 0 に減らします。 @@TRANCOUNT が 1 より大きい場合、COMMIT TRANSACTION は @@TRANCOUNT を 1 だけ減らし、トランザクションをアクティブに保ちます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Applies to SQL Server (starting with 2008) and Azure SQL Database
  
COMMIT [ { TRAN | TRANSACTION }  [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]  
[ ; ]  
```  
 
```  
-- Applies to Azure SQL Data Warehouse and Parallel Data Warehouse Database
  
COMMIT [ TRAN | TRANSACTION ] 
[ ; ]  
``` 
 
  
## <a name="arguments"></a>引数  
 *transaction_name*  
 **適用対象:** SQL Server および Azure SQL Database
 
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] では無視されます。 *transaction_name* には前の BEGIN TRANSACTION により割り当てられるトランザクション名を指定します。 *transaction_name* は識別子の規則に従っている必要があります。ただし、32 文字を超えることはできません。 *transaction_name* を使用すると、プログラマは入れ子にされた BEGIN TRANSACTION と COMMIT TRANSACTION の関連を把握しやすくなります。  
  
 *@tran_name_variable*  
 **適用対象:** SQL Server および Azure SQL Database  
 
有効なトランザクション名を格納しているユーザー定義変数の名前を指定します。 変数は、char、varchar、nchar、または nvarchar データ型を使用して宣言する必要があります。 変数に 32 文字を超える文字が渡された場合は、32 文字だけが使用され、残りの文字は切り捨てられます。  
  
 DELAYED_DURABILITY  
 **適用対象:** SQL Server および Azure SQL Database   

 このトランザクションを持続性が遅延した状態でコミットすることを要求するオプション。 データベースが `DELAYED_DURABILITY = DISABLED` または `DELAYED_DURABILITY = FORCED` によって変更されている場合、要求は無視されます。 詳細については、「[トランザクションの持続性の制御](../../relational-databases/logs/control-transaction-durability.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] のプログラマは、トランザクションで参照されるすべてのデータが論理的に正しいことを確認したうえで COMMIT TRANSACTION を実行する必要があります。  
  
 コミットされるトランザクションが [!INCLUDE[tsql](../../includes/tsql-md.md)] 分散トランザクションの場合、COMMIT TRANSACTION では MS DTC が起動され、2 フェーズ コミット プロトコルによって、トランザクションに参加しているすべてのサーバーがコミットされます。 ローカル トランザクションで、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の同じインスタンス上にある 2 つ以上のデータベースが対象となっている場合、インスタンスでは内部の 2 フェーズ コミットにより、トランザクションに参加しているすべてのデータベースがコミットされます。  
  
 入れ子にされたトランザクションで使用する場合は、入れ子内のトランザクションをコミットしてもリソースは解放されず、修正も永久保存されません。 データ修正が永久保存され、リソースが解放されるのは、入れ子の外側のトランザクションをコミットした場合だけです。 @@TRANCOUNT が 1 より大きくなると、COMMIT TRANSACTION が実行され、実行のたびに @@TRANCOUNT が単純に 1 ずつ減少します。 最終的に @@TRANCOUNT が 0 になると、外側のトランザクション全体がコミットされます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では *transaction_name* は無視されるので、入れ子内に完了していないトランザクションがあるとき、外側のトランザクションの名前を参照する COMMIT TRANSACTION を実行しても、@@TRANCOUNT が 1 減少されるだけです。  
  
 @@TRANCOUNT が 0 のときに COMMIT TRANSACTION を実行すると、対応する BEGIN TRANSACTION がないためエラーが発生します。  
  
 COMMIT TRANSACTION ステートメントの実行後は、データ修正がデータベースに永久保存されるので、トランザクションをロールバックすることはできません。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では、ステートメントの開始時点でトランザクション数が 0 の場合にのみ、ステートメント内のトランザクション数が増加します。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-committing-a-transaction"></a>A. トランザクションをコミットする  
**適用対象:** SQL Server、Azure SQL Database、Azure SQL Data Warehouse、Parallel Data Warehouse   

次の例では、ジョブ候補を削除します。 AdventureWorks を使用します。 
  
```   
BEGIN TRANSACTION;   
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;   
COMMIT TRANSACTION;   
```  
  
### <a name="b-committing-a-nested-transaction"></a>B. 入れ子になったトランザクションをコミットする  
**適用対象:** SQL Server および Azure SQL Database    

次の例では、テーブルを作成し、3 レベルの入れ子にされたトランザクションを生成してから、入れ子になったトランザクションをコミットします。 各 `COMMIT TRANSACTION` ステートメントには *transaction_name* パラメーターがありますが、`COMMIT TRANSACTION` ステートメントと `BEGIN TRANSACTION` ステートメントの間に関連はありません。 *transaction_name* パラメーターは、参考情報としてのみ利用できます。プログラム時にこのパラメーターを参照すると、適切なコミット数を指定して `@@TRANCOUNT` を 0 まで減らし、外側のトランザクションを正しくコミットできるようになります。 
  
```   
IF OBJECT_ID(N'TestTran',N'U') IS NOT NULL  
    DROP TABLE TestTran;  
GO  
CREATE TABLE TestTran (Cola int PRIMARY KEY, Colb char(3));  
GO  
-- This statement sets @@TRANCOUNT to 1.  
BEGIN TRANSACTION OuterTran;  
  
PRINT N'Transaction count after BEGIN OuterTran = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
 
INSERT INTO TestTran VALUES (1, 'aaa');  
 
-- This statement sets @@TRANCOUNT to 2.  
BEGIN TRANSACTION Inner1;  
 
PRINT N'Transaction count after BEGIN Inner1 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
INSERT INTO TestTran VALUES (2, 'bbb');  
  
-- This statement sets @@TRANCOUNT to 3.  
BEGIN TRANSACTION Inner2;  
  
PRINT N'Transaction count after BEGIN Inner2 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
INSERT INTO TestTran VALUES (3, 'ccc');  
  
-- This statement decrements @@TRANCOUNT to 2.  
-- Nothing is committed.  
COMMIT TRANSACTION Inner2;  
 
PRINT N'Transaction count after COMMIT Inner2 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
 
-- This statement decrements @@TRANCOUNT to 1.  
-- Nothing is committed.  
COMMIT TRANSACTION Inner1;  
 
PRINT N'Transaction count after COMMIT Inner1 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
-- This statement decrements @@TRANCOUNT to 0 and  
-- commits outer transaction OuterTran.  
COMMIT TRANSACTION OuterTran;  
  
PRINT N'Transaction count after COMMIT OuterTran = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT WORK &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
