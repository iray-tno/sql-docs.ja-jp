---
title: "CHECK 制約の変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CHECK 制約、変更"
  - "制約の変更"
  - "制約 [SQL Server]、CHECK"
  - "制約 [SQL Server]、変更"
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# CHECK 制約の変更
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、制約式を変更するとき、または特定の条件の制約を有効または無効にするオプションを変更するときは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して CHECK 制約を変更できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **CHECK 制約を変更するための方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### CHECK 制約を変更するには  
  
1.  **オブジェクト エクスプローラー**で、CHECK 制約を含むテーブルを右クリックし、**[デザイン]** をクリックします。  
  
2.  **[テーブル デザイナー]** メニューの **[CHECK 制約]**をクリックします。  
  
3.  **[CHECK 制約]** ダイアログ ボックスの **[選択された制約のチェック]**で、編集する制約を選択します。  
  
4.  次の表の操作を完了します。  
  
    |変換先|手順|  
    |--------|------------------------|  
    |制約式を編集する。|**[式]** フィールドに新しい式を入力します。|  
    |制約名を変更する。|**[名前]** フィールドに新しい名前を入力します。|  
    |既存のデータに制約を適用する。|**[作成時または再度有効化するときに既存データを確認]** チェック ボックスをオンにします。|  
    |テーブルに新しいデータを追加する場合、またはテーブル内の既存のデータを更新する場合に、制約を無効にする。|**[INSERTs および UPDATEs に適用]** チェック ボックスをオフにします。|  
    |レプリケーション エージェントによってテーブルにデータが挿入された場合やデータが更新された場合に制約を無効にする。|**[レプリケーションに対して適用]** チェック ボックスをオフにします。|  
  
    > [!NOTE]  
    >  CHECK 制約に対して異なる機能を持つデータベースもあります。  
  
5.  **[閉じる]**をクリックします。  
  
6.  **[ファイル]** メニューの **table name***の保存]*をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **CHECK 制約を変更するには**  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して `CHECK` 制約を変更するには、最初に既存の `CHECK` 制約を削除してから、新しい定義を使用して再作成する必要があります。 詳細については、「[CHECK 制約の削除](../../relational-databases/tables/delete-check-constraints.md)」および「[CHECK 制約の作成](../../relational-databases/tables/create-check-constraints.md)」を参照してください。  
  
###  <a name="TsqlExample"></a>  