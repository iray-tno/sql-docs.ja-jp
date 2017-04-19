---
title: "列ストア インデックスのバージョン管理機能の概要 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1fe5ea05-5b19-45a4-9b7a-8ae5ca367897
caps.latest.revision: 28
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 27
---
# 列ストア インデックスのバージョン管理機能の概要
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各バージョンと、Azure SQL Database Premium Edition、Azure SQL Data Warehouse、および Parallel Data Warehouse の最新リリースで使用できる列ストア機能の概要。  

 >[!NOTE]
 > Azure SQL Database の場合、列ストア インデックスは Premium Edition でのみ使用できます。
 
## <a name="feature-summary-for-product-releases"></a>製品リリースの機能の概要  
 列ストア インデックスの主な機能と、これらの機能を利用できる製品をまとめた表を次に示します。  

  
|列ストア インデックスの機能|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]|  
|-------------------------------|---------------------------|---------------------------|---------------------------|--------------------------------------------|-------------------------|  
|マルチ スレッド クエリのバッチ実行|はい|はい|はい|はい|はい|  
|シングル スレッド クエリのバッチ実行|||はい|はい|はい|  
|アーカイブ圧縮オプション||はい|はい|はい|はい|  
|スナップショット分離および Read Committed スナップショット分離|||はい|はい|はい|  
|テーブルの作成時に、列ストア インデックスを指定する|||はい|はい|はい|  
|AlwaysOn は列ストア インデックスをサポートする|はい|はい|はい|はい|はい|  
|AlwaysOn の読み取り可能なセカンダリは非クラスター化列ストア インデックスをサポートする|はい|はい|はい|はい|はい|  
|AlwaysOn の読み取り可能なセカンダリは、更新可能な列ストア インデックスをサポートする|||はい|||  
|ヒープまたは B ツリーの読み取り専用の非クラスター化列ストア インデックス|はい|はい|はい*|はい*|はい*|  
|ヒープまたは B ツリーの更新可能な非クラスター化列ストア インデックス|||はい|はい|はい|  
|ヒープまたは B ツリーで許容される追加の B ツリー インデックスには非クラスター化列ストア インデックスがある|はい|はい|はい|はい|はい|  
|更新可能なクラスター化列ストア インデックス||はい|はい|はい|はい|  
|クラスター化列ストア インデックスの B ツリー インデックス|||はい|はい|はい|  
|メモリ最適化テーブルの列ストア インデックス|||はい|はい|はい|  
|非クラスター化列ストア インデックスの定義では、フィルター適用条件の使用をサポートする|||はい|はい|はい|  
|CREATE TABLE および ALTER TABLE での列ストア インデックスの圧縮遅延オプション|||はい|はい|はい|   
  
 * 読み取り可能な非クラスター化列ストア インデックスを作成するには、読み取り専用ファイル グループにインデックスを格納します。  
  
## [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] には、パフォーマンスと列ストア インデックスの柔軟性を向上させるために重要な機能強化が追加されます。 これにより、データ ウェアハウスのシナリオが強化され、リアルタイムの運用分析が可能になります。  
  
### <a name="functional"></a>機能  
  
-   行ストア テーブルで、更新可能な非クラスター化列ストア インデックスを 1 つ使用できます。 以前、非クラスター化列ストア インデックスは、読み取り専用でした。  
  
-   非クラスター化列ストア インデックスの定義で、フィルター適用条件の使用をサポートします。 この機能を使用すると、運用ワークロードのコールド データに対してのみ非クラスター化列ストア インデックスが作成されます。 これにより、列ストア インデックスの使用が OLTP テーブルに及ぼすパフォーマンス上の影響は最小限に抑えられます。  
  
-   インメモリ テーブルでは、列ストア インデックスを 1 つ使用できます。 これは、テーブルの作成時に作成することも、後で [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md) を使用して追加することもできます。 以前は、列ストア インデックスを保持できたのはディスク ベースのテーブルのみでした。  
  
-   クラスター化列ストア インデックスでは、1 つ以上の非クラスター化行ストア インデックスを使用できます。 以前、列ストア インデックスでは、非クラスター化インデックスはサポートされていませんでした。 SQL Server では、DML 操作の非クラスター化インデックスが自動的に維持されます。  
  
-   B ツリー インデックスを使用して主キーと外部キーをサポートし、これらの制約をクラスター化列ストア インデックスに適用します。  
  
-   列ストア インデックスには、リアルタイム運用分析時にトランザクション ワークロードが受ける影響を最小限に抑える圧縮遅延オプションが用意されています。  このオプションでは、頻繁に変更される行が安定するように配慮してから、それらの行を列ストアに圧縮します。 詳細については、「[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)」および「[列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)」を参照してください。  
  
### <a name="performance-for-database-compatibility-level-120-or-130"></a>データベースの互換性レベルが 120 または 130 の場合のパフォーマンス  
  
-   列ストア インデックスでは、Read Committed スナップショット分離レベル (RCSI) とスナップショット分離 (SI) をサポートします。 これにより、ロックなしのトランザクション一貫性分析クエリが有効になります。  
  
-   列ストアでは、削除された行を取り除くことでインデックス最適化をサポートしており、明示的にインデックスを再構築する必要はありません。 ALTER INDEX … REORGANIZE ステートメントは、オンライン操作として、内部的に定義されたポリシーに基づいて、削除された行を列ストアから削除します。  
  
-   列ストア インデックスには、AlwaysOn の読み取り可能なセカンダリ レプリカでアクセスできます。 AlwaysOn セカンダリ レプリカに分析クエリをオフロードすることで、運用分析のパフォーマンスを向上させることができます。  
  
-   パフォーマンスを高めるために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、データ型で使われているバイト数が 8 バイト以下で、かつデータ型が文字列でない場合、テーブルのスキャン中に集計関数 MIN、MAX、SUM、COUNT、AVG を計算します。 クラスター化列ストア インデックスおよび非クラスター化列ストア インデックスの両方で、Group By 句を使用するかどうかに関係なく集計プッシュ ダウンがサポートされています。  
  
-   述語のプッシュ ダウンは、[v] char 型または n [v] char 型の文字列を比較するクエリを高速化します。 これは、一般的な比較演算子に適用され、ビットマップ フィルターを使用する演算子 (LIKE など) が含まれます。 SQL Server がサポートするすべての照合順序で動作します。  
  
### <a name="performance-for-database-compatibility-level-130"></a>データベースの互換性レベルが 130 の場合のパフォーマンス  
  
-   次のいずれかの操作を使用して、クエリの新しいバッチ モード実行をサポートします。  
  
    -   SORT  
  
    -   複数の異なる関数では集計します。 例: COUNT/COUNT、AVG/SUM、CHECKSUM_AGG、STDEV/STDEVP  
  
    -   ウィンドウ集計関数: COUNT、COUNT_BIG、SUM、AVG、MIN、MAX、CLR  
  
    -   ユーザー定義のウィンドウ集計関数: CHECKSUM_AGG、STDEV、STDEVP、VAR、VARP、GROUPING  
  
    -   ウィンドウ集計分析関数: LAG< LEAD、FIRST_VALUE、LAST_VALUE、PERCENTILE_CONT、PERCENTILE_DISC、CUME_DIST、および PERCENT_RANK  
  
-   MAXDOP 1 または直列クエリ プランで実行されるシングル スレッド クエリは、バッチ モードで実行されます。 以前は、マルチ スレッド クエリのみがバッチ モードで実行されていました。  
  
-   メモリ最適化テーブル クエリでは、行ストア インデックスまたは列ストア インデックス内のデータにアクセスする際に、並列プランを SQL 相互運用モードで使用できます。  
  
### <a name="supportability"></a>サポート性  
 次に、列ストア用の新しいシステム ビューを示します。  
  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  
  
-   [sys.dm_column_store_object_pool &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)  
  
-   [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
-   [sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)  
  
 これらのインメモリ OLTP ベースの DMV には、列ストアに対する更新が含まれます。  
  
-   [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-memory-consumers-transact-sql.md)  
  
-   [sys.dm_db_xtp_nonclustered_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-nonclustered-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_object_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-object-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql.md)  
  
### <a name="limitations"></a>制限事項  
  
-   クラスター化列ストア インデックスに対して B ツリー インデックスが定義されている場合、MERGE は無効になります。  
  
-   インメモリ テーブルの場合、列ストア インデックスにはすべての列が含まれている必要があります。列ストア インデックスにフィルター適用条件を含めることはできません。  
  
-   インメモリ テーブルの場合、列ストア インデックスに対するクエリは相互運用モードでのみ実行され、インメモリ ネイティブ モードでは実行されません。 並列実行がサポートされています。  
  
## <a name="sql-server-2014"></a>SQL Server 2014  
 SQL Server 2014 では、プライマリ ストレージ形式として、クラスター化列ストア インデックスが導入されました。 これにより、通常の読み込みに加えて、更新、削除、および挿入の操作が可能になりました。  
  
-   テーブルでは、プライマリ テーブル ストレージとしてクラスター化列ストア インデックスを使用できます。 テーブルで他のインデックスは使用できません。ただし、クラスター化列ストア インデックスは更新できるため、通常の読み込みを実行し、個々の行に変更を加えることができます。  
  
-   非クラスター化列ストア インデックスについては、バッチ モードで実行可能になった演算子が追加されたことを除けば、SQL Server 2012 の場合と同じ機能を引き続き備えています。 更新は相変わらずサポートされていません。ただし、再構築およびパーティションの切り替えによる更新は除きます。 非クラスター化列ストア インデックスは、ディスクベースのテーブルでのみサポートされており、インメモリ テーブルではサポートされていません。  
  
-   クラスター化および非クラスター化列ストア インデックスには、データをさらに圧縮するアーカイブ圧縮オプションがあります。 アーカイブ オプションは、メモリ内でもディスク上でもデータ サイズを縮小するのに便利ですが、クエリのパフォーマンスを低下させます。 アクセス頻度の低いデータに対して適切に機能します。  
  
-   クラスター化列ストア インデックスと非クラスター化列ストア インデックスには類似点が多数あります。両者は、同じ列ストレージ形式、同じクエリ処理エンジン、および同じ動的管理ビュー セットを使用します。 違いは、一方がプライマリ インデックス型で他方がセカンダリ インデックス型であることです。非クラスター化列ストア インデックスは読み取り専用です。  
  
-   Scan、Filter、Project、Join、Group By、Union All の各演算子は、マルチ スレッド クエリではバッチ モードで実行されます。  
  
## <a name="sql-server-2012"></a>SQL Server 2012  
 SQL Server 2012 では、行ストア テーブルに対するもう 1 つのインデックス型としての非クラスター化列ストア インデックスと、列ストア データに対するクエリのバッチ処理が導入されました。  
  
-   行ストア テーブルでは、非クラスター化列ストア インデックスを 1 つ使用することができます。  
  
-   列ストア インデックスは読み取り専用です。 列ストア インデックスの作成後は、挿入、削除、および更新の操作で、テーブルを更新することはできません。これらの操作を実行するには、インデックスを削除し、テーブルを更新し、列ストア インデックスを再構築する必要があります。 パーティション切り替えを使用することで、テーブルに追加データを読み込むことができます。 パーティション切り替えの利点は、列ストア インデックスを削除して再構築しなくても、データを読み込むことができることです。  
  
-   列ストア インデックスでは、データのコピーを格納するため、常に余分な (通常は、行ストアより 10% 多い) ストレージを確保しておく必要があります。  
  
-   バッチ処理は、クエリのパフォーマンスを 2 倍以上向上させますが、並列クエリの実行でしか利用できません。  
  
## <a name="see-also"></a>参照  
 [列ストア インデックス ガイド](../Topic/Columnstore%20Indexes%20Guide.md)   
 [列ストア インデックス データの読み込み](../Topic/Columnstore%20Indexes%20Data%20Loading.md)   
 [列ストア インデックスのクエリ パフォーマンス](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [データ ウェアハウスの列ストア インデックス](../Topic/Columnstore%20Indexes%20for%20Data%20Warehousing.md)   
 [列ストア インデックスの最適化](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  