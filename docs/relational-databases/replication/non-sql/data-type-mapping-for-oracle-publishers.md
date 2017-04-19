---
title: "Oracle パブリッシャーのデータ型マッピング | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Oracle パブリッシング [SQL Server レプリケーション]、データ型マッピング"
  - "データ型 [SQL Server レプリケーション]、Oracle パブリッシング"
  - "マッピング データ型 [SQL Server レプリケーション]"
ms.assetid: 6da0e4f4-f252-4b7e-ba60-d2e912aa278e
caps.latest.revision: 47
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 47
---
# Oracle パブリッシャーのデータ型マッピング
  Oracle データ型と [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型は常に正確に一致しません。 Oracle のテーブルをパブリッシュするときは、可能な限り、一致するデータ型が自動的に選択されます。 単一のデータ型マッピングが明らかでない場合は、代替のデータ型マッピングが提供されます。 代替マッピングの選択方法の詳細については、以下の「代替データ型マッピングの指定」を参照してください。  
  
 次の表に、Oracle パブリッシャーから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターにデータを移動したときに、Oracle と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の間で、データ型が既定でどのようにマッピングされるかを示します。 「代替」列は、代替マッピングが使用可能かどうかを示しています。  
  
|Oracle データ型|SQL Server データ型|代替|  
|----------------------|--------------------------|------------------|  
|BFILE|VARBINARY(MAX)|はい|  
|BLOB|VARBINARY(MAX)|はい|  
|CHAR([1-2000])|CHAR([1-2000])|はい|  
|CLOB|VARCHAR(MAX)|可|  
|[DATE]|DATETIME|はい|  
|[FLOAT]|[FLOAT]|いいえ|  
|FLOAT([1-53])|FLOAT([1-53])|いいえ|  
|FLOAT([54-126])|[FLOAT]|いいえ|  
|INT|NUMERIC(38)|可|  
|INTERVAL|DATETIME|はい|  
|LONG|VARCHAR(MAX)|はい|  
|LONG RAW|IMAGE|はい|  
|NCHAR([1-1000])|NCHAR([1-1000])|いいえ|  
|NCLOB|NVARCHAR(MAX)|可|  
|NUMBER|[FLOAT]|はい|  
|NUMBER([1-38])|NUMERIC([1-38])|いいえ|  
|NUMBER([0-38],[1-38])|NUMERIC([0-38],[1-38])|はい|  
|NVARCHAR2([1-2000])|NVARCHAR([1-2000])|いいえ|  
|RAW([1-2000])|VARBINARY([1-2000])|いいえ|  
|REAL|[FLOAT]|いいえ|  
|ROWID|CHAR(18)|いいえ|  
|TIMESTAMP|DATETIME|はい|  
|TIMESTAMP(0-7)|DATETIME|はい|  
|TIMESTAMP(8-9)|DATETIME|可|  
|TIMESTAMP(0-7) WITH TIME ZONE|VARCHAR(37)|はい|  
|TIMESTAMP(8-9) WITH TIME ZONE|VARCHAR(37)|いいえ|  
|TIMESTAMP(0-7) WITH LOCAL TIME ZONE|VARCHAR(37)|可|  
|TIMESTAMP(8-9) WITH LOCAL TIME ZONE|VARCHAR(37)|いいえ|  
|UROWID|CHAR(18)|いいえ|  
|VARCHAR2([1-4000])|VARCHAR([1-4000])|はい|  
  
## データ型マッピングに関する注意点  
 Oracle データベースからデータをレプリケートするときは、データ型に関する次の問題に注意してください。  
  
### サポートされていないデータ型  
 次のデータ型はサポートされていません。これらの型の列はレプリケートできません。  
  
-   オブジェクト型  
  
-   XML 型  
  
-   Varray 型  
  
-   入れ子になったテーブル  
  
-   REF を使用する列  
  
### DATE データ型  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の日付の範囲は 1753 A.D. から  9999 A.D. までですが、Oracle の日付の範囲は 4712 B.C. から  4712 A.D. までです。 DATE 型の列に SQL Server の日付範囲を超える値が含まれている場合は、その列の代替データ型である VARCHAR(19) を選択してください。  
  
### FLOAT 型と NUMBER 型  
 FLOAT データ型と NUMBER データ型のマッピング時に指定される小数点以下桁数および有効桁数は、列に対して Oracle データベースのデータ型を使って指定された小数点以下桁数および有効桁数で決まります。 有効桁数は、数値全体の桁数です。 小数点以下桁数は、数値の中で小数点より右側の桁数です。 たとえば、123.45 という値の場合、有効桁数は 5 で、小数点以下桁数は 2 になります。  
  
 Oracle では、NUMBER(4,5) のように、有効桁数よりも大きな小数点以下桁数の数値を定義できます。しかし、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、有効桁数を小数点以下桁数と同じか、それ以上にする必要があります。 データの切り捨てが発生しないようにするため、Oracle パブリッシャーで小数点以下桁数が有効桁数よりも大きい場合は、データ型をマップするときに、有効桁数が小数点以下桁数と同じ値に設定されます。つまり、NUMBER(4,5) は NUMERIC(5,5) としてマップされます。  
  
> [!NOTE]  
>  NUMBER の小数点以下桁数および有効桁数を指定しない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定値には、最大の小数点以下桁数 (8) および有効桁数 (38) が使用されます。 データをレプリケートするときは、使用領域とパフォーマンスを向上させるために、Oracle で特定の小数点以下桁数と有効桁数を設定することをお勧めします。  
  
### Large Object 型  
 Oracle は最大 4 ギガバイト (GB) のデータをサポートします。一方、SQL Server は最大 2 GB のデータをサポートします。 2 GB を超えてレプリケートされたデータは、切り捨てられます。  
  
 Oracle のテーブルに BFILE 列が含まれている場合、この列のデータはファイル システムに格納されます。 レプリケーション管理ユーザー アカウントには、次の構文を使用して、このデータが格納されているディレクトリへのアクセスを許可する必要があります。  
  
 `GRANT READ ON DIRECTORY <directory_name> TO <replication_administrative_user_schema>`  
  
 ラージ オブジェクトの種類の詳細については、「Large Object の注意点」セクションを参照してください [設計に関する考慮事項と Oracle パブリッシャーに対して制限](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md)します。  
  
## 代替データ型マッピングの指定  
 通常、既定のデータ型マッピングは適切な設定です。しかし、多くの Oracle データ型に対して、既定のマッピングを使用しないで一連の代替マッピングからデータ型マッピングを選択することができます。 代替マッピングを指定する方法は 2 つあります。  
  
-   ストアド プロシージャまたはパブリケーションの新規作成ウィザードを使用して、アーティクルごとに既定値を上書きします。  
  
-   ストアド プロシージャを使用して、以降のすべてのアーティクルの既定値をグローバルに変更します (既存のアーティクルの既定値は変更されません)。  
  
 代替データ型マッピングを指定するを参照してください。 [Oracle パブリッシャーのデータ型マッピングを指定](../../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)します。  
  
## 参照  
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシャーの設計上の注意点および制限](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  