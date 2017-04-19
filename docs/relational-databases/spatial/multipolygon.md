---
title: "MultiPolygon | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "geometry サブタイプ MultiPolygon [SQL Server]"
  - "geometry 型のサブタイプ [SQL Server]"
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# MultiPolygon
  **MultiPolygon** インスタンスは、0 個以上の **Polygon** インスタンスのコレクションです。  
  
## Polygon インスタンス  
 次の図は、**MultiPolygon** インスタンスの例です。  
  
 ![geometry MultiPolygon インスタンスの例](../../relational-databases/spatial/media/multipolygon.png "geometry MultiPolygon インスタンスの例")  
  
 この図は次のことを示しています。  
  
-   図 1 は、2 つの **Polygon** 要素がある **MultiPolygon** インスタンスです。 境界は、2 つの外部リングと 3 つの内部リングによって定義されています。  
  
-   図 2 は、2 つの **Polygon** 要素がある **MultiPolygon** インスタンスです。 境界は、2 つの外部リングと 3 つの内部リングによって定義されています。 2 つの **Polygon** 要素は接点で交差しています。  
  
### 許容されるインスタンス  
 次のいずれかの条件が満たされている場合、**MultiPolygon** インスタンスは許容されます。  
  
-   これは空の **MultiPolygon** インスタンスです。  
  
-   **MultiPolygon** を構成するすべてのインスタンスは、許容される **Polygon** インスタンスです。 許容される **Polygon** インスタンスの詳細については、「[Polygon](../../relational-databases/spatial/polygon.md)」を参照してください。  
  
 次の例に、許容される **MultiPolygon** インスタンスを示します。  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
```  
  
 次の例に、`System.FormatException` をスローする MultiPolygon インスタンスを示します。  
  
```  
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';  
```  
  
 MultiPolygon の 2 番目のインスタンスは LineString インスタンスであり、許容される Polygon インスタンスではありません。  
  
### 有効なインスタンス  
 **MultiPolygon** インスタンスは、空の **MultiPolygon** インスタンスであるか、次の条件を満たす場合に有効です。  
  
1.  **MultiPolygon** インスタンスを構成するすべてのインスタンスは有効な **Polygon** インスタンスです。 有効な **Polygon** インスタンスについては、「[Polygon](../../relational-databases/spatial/polygon.md)」を参照してください。  
  
2.  **MultiPolygon** インスタンスを構成する **Polygon** インスタンスは重複しません。  
  
 次に、2 つの有効な **MultiPolygon** インスタンスと 1 つの無効な **MultiPolygon** インスタンスの例を示します。  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g2` は、2 つの **Polygon** インスタンスが 1 つの接点のみで接しているため有効です。 `@g3` は、2 つの **Polygon** インスタンスの内部が互いに重なっているため無効です。  
  
## 使用例  
 次の例では、`geometry``MultiPolygon` インスタンスを作成し、2 つ目の構成要素の Well-Known Text (WKT) を返します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');  
SELECT @g.STGeometryN(2).STAsText();  
```  
  
 次の例では、空の `MultiPolygon` インスタンスを作成します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');  
```  
  
## 参照  
 [多角形](../../relational-databases/spatial/polygon.md)   
 [STArea &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/starea-geometry-data-type.md)   
 [STCentroid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stcentroid-geometry-data-type.md)   
 [STPointOnSurface &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  