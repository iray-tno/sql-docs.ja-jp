---
title: "データの同期 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "同期 [SQL Server レプリケーション], 同期について"
  - "マージ レプリケーションの同期 [SQL Server レプリケーション]"
  - "スクリプト [SQL Server レプリケーション], 同期および"
  - "同期 [SQL Server レプリケーション]"
  - "スナップショット レプリケーション [SQL Server], 同期"
  - "トランザクション レプリケーション, 同期"
  - "サブスクリプション [SQL Server レプリケーション], 同期"
  - "要求時スクリプト実行"
  - "レプリケーション [SQL Server], 同期"
  - "スクリプト [SQL Server レプリケーション]"
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# データの同期
  データの同期とは、初期スナップショットをサブスクライバーで適用した後に、パブリッシャーとサブスクライバーの間でデータとスキーマ変更を反映する処理のことです。 同期は、次のように実行されます。  
  
-   連続して実行。これは通常、トランザクション レプリケーションの場合です。  
  
-   要求時に実行。これは通常、マージ レプリケーションの場合です。  
  
-   スケジュールに基づいて実行。これは通常、スナップショット レプリケーションの場合です。  
  
 サブスクリプションが同期されると、使用しているレプリケーションの種類に基づいて異なる処理が実行されます。  
  
-   スナップショット レプリケーション。 同期とは、ディストリビューション エージェントがサブスクライバーでスナップショットを再適用して、サブスクリプション データベースのスキーマおよびデータがパブリケーション データベースとの一貫性を持つようにすることを意味します。  
  
     データまたはスキーマへの変更がパブリッシャーで行われている場合、サブスクライバーに変更を反映させるために、新しいスナップショットを生成する必要があります。  
  
-   トランザクション レプリケーション。 同期とは、ディストリビューション エージェントが更新、挿入、削除、およびその他の変更をディストリビューション データベースからサブスクライバーに転送することを意味します。  
  
-   マージ レプリケーション。 同期とは、マージ エージェントがサブスクライバーからパブリッシャーに変更をアップロードし、パブリッシャーからサブスクライバーに変更をダウンロードすることを意味します。 競合が存在する場合は、検出されて解決されます。 データは集約され、最終的にパブリッシャーとすべてのサブスクライバーでデータ値が同じになります。 競合が検出されて解決された場合、一部のユーザーがコミットした作業は、定義されたポリシーに応じて、競合が解決するように変更されます。  
  
 スナップショット パブリケーションでは、同期が発生するたびに、サブスクライバーでスキーマが完全に更新されます。そのため、すべてのスキーマ変更がサブスクライバーに適用されます。 トランザクション レプリケーションとマージ レプリケーションでも、最も一般的なスキーマ変更がサポートされます。 詳細については、次を参照してください。 [パブリケーション データベースでスキーマ変更を行う](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)です。  
  
 プッシュ サブスクリプションを同期するには、次を参照してください。 [プッシュ サブスクリプションを同期](../../relational-databases/replication/synchronize-a-push-subscription.md)です。  
  
 プル サブスクリプションを同期するには、次を参照してください。 [プル サブスクリプションを同期](../../relational-databases/replication/synchronize-a-pull-subscription.md)です。  
  
 同期スケジュールを設定するを参照してください。 [同期スケジュールの指定](../../relational-databases/replication/specify-synchronization-schedules.md)です。  
  
 **同期の競合を表示および解決するには**  
  
-   [!含める [ssManStudioFull] (../Token/ssManStudioFull_md.md)]: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   [!含める [ssManStudioFull] (../Token/ssManStudioFull_md.md)]: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
## 同期中のコード実行  
 レプリケーションでは、同期中にコードを実行する方法が 2 つサポートされています。  
  
-   要求時スクリプト実行は、トランザクション レプリケーションおよびマージ レプリケーションでサポートされています。 要求時スクリプト実行を使用すると、同期中に実行する SQL スクリプトを指定できます。 スクリプトが、サブスクライバーにコピーを使用して実行 **sqlcmd** 同期プロセスの開始時です。 スクリプトは、レプリケートされた変更をサブスクライバーに適用するときに、それらの変更へはアクセスしません。 詳細については、次を参照してください。 [同期中にスクリプトを実行する (&) #40 です。レプリケーション TRANSACT-SQL プログラミングと #41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)です。  
  
-   ビジネス ロジック ハンドラーは、マージ レプリケーションでサポートされています。 ビジネス ロジック ハンドラー フレームワークを使用すると、マネージ コードのアセンブリを記述して、マージ同期処理中に呼び出すことができます。 このアセンブリには、データの変更、競合、およびエラーなど、同期中に発生するさまざまな状況に対処するためのビジネス ロジックを記述できます。 詳細については、次を参照してください。 [マージ同期中にビジネス ロジックを実行](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)します。  
  
## 参照  
 [マージ レプリケーションの競合の検出と解決](../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md)  
  
  