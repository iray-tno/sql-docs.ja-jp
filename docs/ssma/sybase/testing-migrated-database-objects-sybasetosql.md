---
title: テストに移行したデータベース オブジェクト (SybaseToSQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6f95ab1a14679d919a11fcc5a0c26554ac6120f2
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779408"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>移行されたデータベース オブジェクト (SybaseToSQL) のテスト
Microsoft SQL Server Migration Assistant for Sybase Tester (SSMA テスター) が自動的にテスト データベース オブジェクトへの変換と SSMA によって行われたデータの移行。 SSMA のすべての移行手順が完了したら後、は、SSMA Tester を使用して、変換したオブジェクトが同じように動作し、すべてのデータが正常に転送されることを確認してください。  
  
> [!NOTE]  
> Azure の接続の場合は、テスト担当者のコンポーネントが無効です。  
  
SSMA Tester では、次のオブジェクトの種類をテストできます。  
  
-   テーブル  
  
-   ストアド プロシージャ  
  
-   表示モード。  
  
-   スタンドアロンのステートメント。  
  
SSMA テスターは、Sybase および対応する SQL Server でのテスト用に選択されたオブジェクトを実行します。 その後、次の条件に基づいて結果を比較します。  
  
-   変更テーブル データと同じですか。  
  
-   プロシージャおよび関数の出力パラメーターの値が同じですか。  
  
-   関数は同じ結果を返します。  
  
-   結果セットと同じですか。  
  
> [!NOTE]  
> 注意してください。 実稼働システムでは、SSMA Tester を使用しないでください。 テストの実行中に、送信元スキーマとデータが変更されます。 一方で、元の状態の完全な復元はテスト対象コードの種類によって可能なでない可能性があります。  
  
## <a name="prerequisites"></a>前提条件  
SSMA Tester を使用する場合は、SSMA Sybase 拡張機能パックをインストール、 **Tester データベースのインストール**オプションをオンにします。  
  
さらに、次の点を確認します。  
  
-   Sybase OLE DB プロバイダーがコンピューターにインストールされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を実行します。  
  
-   共通言語ランタイム (CLR) 統合を有効になっている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース エンジン。  
  
SSMA テスターの現在のバージョンによって、同じソースまたはターゲット サーバーに複数のユーザーによって並列実行がサポートされていないことに注意します。  
  
## <a name="getting-started"></a>作業の開始  
[テスト_ケースの作成&#40;SybaseToSQL&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>参照  
[SSMA コンポーネントを SQL Server インストール&#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[プロジェクト設定&#40;変換&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
