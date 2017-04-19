---
title: "メジャー グループのプロパティの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロパティ [Analysis Services], メジャー グループ"
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# メジャー グループのプロパティの構成
  メジャー グループには、メジャー グループの動作を定義できるプロパティがあります。  
  
## メジャー グループのプロパティ  
 メジャー グループのプロパティは、メジャー グループ全体の動作を指定し、メジャー グループ内のメジャーの特定プロパティの既定の動作を決定します。  
  
|プロパティ|定義|  
|--------------|----------------|  
|**AggregationPrefix**|ROLAP ストレージに適用されます。 このメジャー グループに関連付けられているパーティションの集計の格納に使用する SQL Server のインデックス付きビューに、共通のプレフィックスを割り当てます。|  
|**DataAggregation**|このプロパティは、将来使用するために予約済みであり、現在のところ何も効果がありません。 そのため、この設定を変更しないことをお勧めします。|  
|**Description**|このプロパティを使用すると、メジャー グループを文書化することができます。|  
|**ErrorConfiguration**|重複するキー、不明なキー、NULL キー、エラーの制限、エラー検出時のアクション、およびエラー ログ ファイルを処理するための、構成可能なエラー処理設定です。 「[キューブ、パーティション、およびディメンションに関する処理のエラー構成 &#40;SSAS - 多次元&#41;](../../analysis-services/multidimensional-models/error configuration for cube, partition, and dimension processing.md)」をご覧ください。|  
|**EstimatedRows**|ファクト テーブルの推定行数を指定します。|  
|**EstimatedSize**|メジャー グループの推定サイズを指定します (バイト単位)。|  
|**ID**|オブジェクト識別子を指定します。|  
|**IgnoreUnrelatedDimensions**|メジャー グループに関連付けられていないディメンションのメンバーがクエリに含まれているときに、関連付けられていないディメンションをトップ レベルに強制するかどうかを指定します。 既定値の設定は **True**です。|  
|**名前**|メジャーの名前。 このプロパティは読み取り専用です。|  
|**プロアクティブ キャッシュ**|重複するキー、不明なキー、NULL キー、エラーの制限、エラー検出時のアクション、およびエラー ログ ファイルを処理するための、構成可能なエラー処理設定です。|  
|**ProcessingMode**|インデックス作成と集計を処理中に行うか、処理後に行うかを指定します。 オプションは Regular または LazyAggregations です。 LazyAggregations を使用すると、バック グラウンド タスクとして集計を実行できます。|  
|**ProcessingPriority**|レイジー集計やインデックス作成など、バックグラウンド操作中のキューブの処理の優先度を決定します。 既定値は **0** です。|  
|**[StorageLocation]**|メジャー グループのファイル システム ストレージの場所です。 指定しなければ、ストレージの場所はメジャー グループが含まれているキューブから継承されます。|  
|**StorageMode**|メジャー グループのストレージ モードです。 使用できる値は MOLAP、ROLAP、または HOLAP です。|  
|**型**|メジャー グループの種類を指定します。|  
  
  