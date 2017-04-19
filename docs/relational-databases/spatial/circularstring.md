---
title: "CircularString | Microsoft Docs"
ms.custom: ""
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# CircularString
  **CircularString** は、0 個以上の連続する円弧セグメントのコレクションです。 円弧セグメントは、2 次元平面内の 3 つの点によって定義された曲線セグメントです。最初のポイントを 3 番目のポイントと同じにすることはできません。 円弧セグメントの 3 つのポイントすべてが同一線上にある場合は、円弧セグメントが直線セグメントとして扱われます。  
  
> [!IMPORTANT]  
>  **CircularString** サブタイプを含む、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] で導入された新しい空間機能の詳細な説明とサンプルについては、ホワイト ペーパー『[New Spatial Features in SQL Server 2012 (SQL Server 2012 の新しい空間機能)](http://go.microsoft.com/fwlink/?LinkId=226407)』をダウンロードして参照してください。  
  
## CircularString インスタンス  
 次の図は有効な **CircularString** インスタンスを示しています。  
  
 ![5ff17e34-b578-4873-9d33-79500940d0bc](../../relational-databases/spatial/media/5ff17e34-b578-4873-9d33-79500940d0bc.gif)
  
### 許容されるインスタンス  
 **CircularString** インスタンスが空か、含まれているポイント n の数が奇数である場合 (n > 1) は、このインスタンスが許容されます。 次に示す **CircularString** インスタンスは許容されます。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';  
```  
  
 `@g3` の場合、**CircularString** インスタンスは許容されることがありますが、有効ではありません。 次に示す CircularString インスタンスの宣言は許容されません。 この宣言は `System.FormatException` をスローします。  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';  
```  
  
### 有効なインスタンス  
 有効な **CircularString** インスタンスは、空であるか、または次の属性を持つ必要があります。  
  
-   少なくとも 1 つの円弧のセグメントが含まれている (つまり、最低限 3 つのポイントがある)。  
  
-   最後のセグメントを除き、シーケンス内の各円弧セグメントの最後エンドポイントが、シーケンス内の次のセグメントの最初のエンドポイントになっている。  
  
-   ポイントの数が奇数である。  
  
-   このインスタンス自体を間隔に重ねることはできない。  
  
-   **CircularString** インスタンスは線分を含むことができるが、これらの線分は、同一線上の 3 つのポイントによって定義される必要がある。  
  
 次の例は、有効な **CircularString** インスタンスを示しています。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';  
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();  
```  
  
 **CircularString** インスタンスでは、完全な円を定義するためには、少なくとも 2 つの円弧セグメントを含める必要があります。 **CircularString** インスタンスでは、(1 1, 3 1, 1 1) など 1 つの円弧セグメントを使用して完全な円を定義することはできません。 (1 1, 2 2, 3 1, 2 0, 1 1) を使用して円を定義してください。  
  
 次の例は、無効な CircularString インスタンスを示しています。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';  
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
### 同一線上のポイントを持つインスタンス  
 次の場合、円弧セグメントは直線セグメントとして扱われます。  
  
-   3 つのすべてのポイントが同一直線上にある場合 (例: (1 3, 4 4, 7 5))。  
  
-   最初のポイントと中間のポイントは同一だが、3 番目のポイントが異なる場合 (例: (1 3, 1 3, 7 5))。  
  
-   中間のポイントと最後のポイントは同一だが、最初のポイントが異なる場合 (例: (1 3, 4 4, 4 4))。  
  
## 使用例  
  
### A. 空の CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、空の **CircularString** インスタンスを作成する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');  
```  
  
### B. 1 つの CircularString を含む CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、1 つの円弧のセグメント (半円) を持つ **CircularString** インスタンスを作成する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);  
SELECT @g.ToString();  
```  
  
### C. 複数の円弧セグメントを含む CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、複数の円弧のセグメント (完全な円) を持つ **CircularString** インスタンスを作成する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');  
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));    
```  
  
 結果は、次のようになります。  
  
```  
Circumference = 6.28319  
```  
  
 **CircularString** の代わりに **LineString** が使用される場合は出力結果を比較してください。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);  
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```  
  
 結果は、次のようになります。  
  
```  
Perimeter = 5.65685  
```  
  
 **CircularString** の例の値は、円の実際の円周である 2∏ に近いことに注意してください。  
  
### D. CircularString を同じステートメント内で使用して geometry インスタンスを宣言およびインスタンス化する  
 このスニペットは、**CircularString** を同じステートメント内で使用して **geometry** インスタンスを宣言およびインスタンス化する方法を示しています。  
  
```tsql  
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
```  
  
### E. CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、**CircularString** を使用して **geography** インスタンスを宣言およびインスタンス化する方法を示しています。  
  
```tsql  
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
```  
  
### F. 直線の CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、直線の **CircularString** インスタンスを作成する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);  
```  
  
## 参照  
 [空間データ型の概要](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)   
 [MakeValid &#40;geography データ型&#41;](../../t-sql/spatial-geography/makevalid-geography-data-type.md)   
 [MakeValid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)   
 [STIsValid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [STIsValid &#40;geography データ型&#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)   
 [STLength &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STStartPoint &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/ststartpoint-geometry-data-type.md)   
 [STEndpoint &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stendpoint-geometry-data-type.md)   
 [STPointN &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md)   
 [STNumPoints &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)   
 [STIsRing &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stisring-geometry-data-type.md)   
 [STIsClosed &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [STPointOnSurface &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)   
 [LineString](../../relational-databases/spatial/linestring.md)  
  
  