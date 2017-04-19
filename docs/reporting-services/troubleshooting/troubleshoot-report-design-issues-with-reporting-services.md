---
title: "Reporting Services でのレポートのデザインに関する問題のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0d103da-5a3e-475c-a71a-9e23476095e2
caps.latest.revision: 5
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 5
---
# Reporting Services でのレポートのデザインに関する問題のトラブルシューティング
レポートのデザインに関する問題は、レポート作成アプリケーションのデザイン ビューでレポート レイアウトを作成しているときに発生することがあります。 このトピックでは、このような問題のトラブルシューティングについて説明します。   
  
## テキスト ボックスに値が 1 つしか表示されず、行ごとに繰り返し表示されない  
データセット フィールド参照を含むテキスト ボックスは 1 回だけ表示され、データセットの最初の値を表示します。   
  
**テキスト ボックスの親がレポート本文になる**  
  
  
デザイン画面に直接追加したテキスト ボックスには、データセットの集計値のみを表示できます。  
  
テキスト ボックスの親コンテナーを確認するには、テキスト ボックスを選択し、プロパティ ペインで **[親]** までスクロールします。   
  
データセットの各値を表示するテキスト ボックスが必要な場合は、テーブルやマトリックスなどのデータ領域を使用します。 テーブルまたはマトリックスの各セルには、既定でテキスト ボックスが含まれます。 各セルにデータセット フィールドをドラッグします。   
  
## レポートに総ページ数を追加できない  
組み込みフィールド `[&PageNumber]` および `[&TotalPages]` は、レポート本文では無効です。   
  
PageNumber と TotalPages がページ ヘッダーとページ フッターでのみ有効になる  
  
  
組み込みフィールド [&PageNumber] および [&TotalPages] は、ページ ヘッダーとページ フッターでのみ有効です。   
  
[&PageNumber] または [&TotalPages] をレポートに追加するには、まずページ ヘッダーまたはページ フッターを追加する必要があります。 詳細については、「[ページ ヘッダーの追加または削除](../../reporting-services/report-design/add-or-remove-a-page-header-or-footer-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
> [&TotalPages] をページ ヘッダーまたはページ フッターに含めると、レポート処理に影響する可能性があります。 詳細については、「レポートのトラブルシューティング : 特定のファイル形式にエクスポートされるレポート」を参照してください。  
[Reporting Services レポートの処理のトラブルシューティング](../../reporting-services/troubleshooting/troubleshoot-processing-of-reporting-services-reports.md)  
  
## 2 つのテーブルをデザインするかグラフとテーブルを 1 つずつデザインして並べて表示する方法  
レポートのデザインは、WYSIWYG (What You See Is What You Get) では行われません。 レポート プロセッサによってデータ、レポート アイテム、空白などのレポート レイアウト情報、コンテナー、および式が結合され、コンパイル済みのレポートが生成されます。このレポートはレポート レンダラーに渡され、指定どおりに表示されるように "レイアウト" されます。レポートは、HTML ブラウザー用に対話的に表示されるか、ファイル形式で表示されます。 自動配置アルゴリズムによって生成されるレポート レイアウトは、変更が必要な場合もあります。   
  
### レイアウトを決定するために表示規則でページ サイズ、コンテナー、ピア オブジェクト、相対的な位置、および空白が使用される  
一般に、レポートはそのデータが収まるように拡大され、その他のレポート アイテムは除外されます。   
  
複数のデータ領域またはレポート アイテムをグループ化するには、同じ親コンテナーに配置します。 たとえば、グラフとテーブルを四角形のコンテナーに配置し、それらの上端を揃えて並べて表示します。 詳細については、「[レポート ビルダーでのレンダリングの動作](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)」を参照してください。  
  
## 参照  
[Reporting Services レポートのデータ取得に関する問題のトラブルシューティング](../../reporting-services/troubleshooting/troubleshoot-data-retrieval-issues-with-reporting-services-reports.md)  
[Reporting Services のサブスクリプションと配信に関するトラブルシューティング](../../reporting-services/troubleshooting/troubleshoot-reporting-services-subscriptions-and-delivery.md)  
  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect.md)]