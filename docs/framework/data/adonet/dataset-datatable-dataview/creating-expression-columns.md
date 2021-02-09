---
description: '詳細情報: 式列の作成'
title: 式列の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 96b445734d645a957951a1d4cbd9d72ed254068f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724987"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="987f9-103">式列の作成</span><span class="sxs-lookup"><span data-stu-id="987f9-103">Creating Expression Columns</span></span>

<span data-ttu-id="987f9-104">列の式を定義すると、同じ行の他の列値またはテーブル内の複数の行の列値に基づいて計算した値を、その列に格納できます。</span><span class="sxs-lookup"><span data-stu-id="987f9-104">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="987f9-105">評価する式を定義するには、対象の列の <xref:System.Data.DataColumn.Expression%2A> プロパティを使用し、その式で <xref:System.Data.DataColumn.ColumnName%2A> プロパティを使用して他の列を参照します。</span><span class="sxs-lookup"><span data-stu-id="987f9-105">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="987f9-106">式列の <xref:System.Data.DataColumn.DataType%2A> は、その式が返す値に適した型であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="987f9-106">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="987f9-107">テーブル内の式列で使用できるいくつかの式の種類を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="987f9-107">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="987f9-108">式の種類</span><span class="sxs-lookup"><span data-stu-id="987f9-108">Expression type</span></span>|<span data-ttu-id="987f9-109">例</span><span class="sxs-lookup"><span data-stu-id="987f9-109">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="987f9-110">比較</span><span class="sxs-lookup"><span data-stu-id="987f9-110">Comparison</span></span>|<span data-ttu-id="987f9-111">"Total >= 500"</span><span class="sxs-lookup"><span data-stu-id="987f9-111">"Total >= 500"</span></span>|  
|<span data-ttu-id="987f9-112">計算</span><span class="sxs-lookup"><span data-stu-id="987f9-112">Computation</span></span>|<span data-ttu-id="987f9-113">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="987f9-113">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="987f9-114">集約</span><span class="sxs-lookup"><span data-stu-id="987f9-114">Aggregation</span></span>|<span data-ttu-id="987f9-115">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="987f9-115">Sum(Price)</span></span>|  
  
 <span data-ttu-id="987f9-116">次の例に示すように、既存の **DataColumn** オブジェクトの **Expression** プロパティを設定したり、このプロパティを <xref:System.Data.DataColumn> コンストラクターに渡す 3 番目の引数として使用したりできます。</span><span class="sxs-lookup"><span data-stu-id="987f9-116">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="987f9-117">式は他の式列を参照できます。ただし、2 つの式が相互に参照し合う循環参照の場合は、例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="987f9-117">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="987f9-118">式の記述の規則については、**DataColumn** クラスの <xref:System.Data.DataColumn.Expression%2A> プロパティのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="987f9-118">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987f9-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="987f9-119">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="987f9-120">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="987f9-120">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="987f9-121">DataTables</span><span class="sxs-lookup"><span data-stu-id="987f9-121">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="987f9-122">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="987f9-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
