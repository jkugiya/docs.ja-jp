---
description: '詳細情報: 型指定されたデータセットのクエリを実行する'
title: 型指定された DataSet のクエリ
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 5bcf8bb587a0ed0eaca1bbe9b3a7d7143757780e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723700"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="58655-103">型指定されたデータセットのクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="58655-103">Query typed DataSets</span></span>

<span data-ttu-id="58655-104">アプリケーションの設計時に <xref:System.Data.DataSet> のスキーマがわかっている場合は、LINQ to DataSet を使用するときに、型指定された <xref:System.Data.DataSet> を用いることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58655-104">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="58655-105">型指定された <xref:System.Data.DataSet> とは、<xref:System.Data.DataSet> から派生されたクラスのことです。</span><span class="sxs-lookup"><span data-stu-id="58655-105">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="58655-106">したがって、型指定されたデータセットは <xref:System.Data.DataSet> のすべてのメソッド、イベント、およびプロパティを継承します。</span><span class="sxs-lookup"><span data-stu-id="58655-106">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="58655-107">さらに、型指定された <xref:System.Data.DataSet> には、厳密に型指定されたメソッド、イベント、プロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="58655-107">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="58655-108">つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="58655-108">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="58655-109">これによりクエリが簡素化され、読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="58655-109">This makes queries simpler and more readable.</span></span> <span data-ttu-id="58655-110">詳しくは、「[型指定されたデータセット](./dataset-datatable-dataview/typed-datasets.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="58655-110">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="58655-111">LINQ to DataSet では、型指定された <xref:System.Data.DataSet> に対するクエリもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="58655-111">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="58655-112">型指定された <xref:System.Data.DataSet> では、列データにアクセスするために、ジェネリック メソッドの <xref:System.Data.DataRowExtensions.Field%2A> または <xref:System.Data.DataRowExtensions.SetField%2A> を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="58655-112">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="58655-113"><xref:System.Data.DataSet> に型情報が含まれているため、プロパティ名をコンパイル時に利用できます。</span><span class="sxs-lookup"><span data-stu-id="58655-113">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="58655-114">LINQ to DataSet では、適切な型として列の値にアクセスできるため、実行時ではなくコードのコンパイル時に型の不一致エラーがキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="58655-114">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="58655-115">型指定された <xref:System.Data.DataSet> に対してクエリを実行するには、Visual Studio の **データセット デザイナー** を使用してあらかじめクラスを生成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="58655-115">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="58655-116">詳しくは、「[データセットを作成および構成する](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="58655-116">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="58655-117">例</span><span class="sxs-lookup"><span data-stu-id="58655-117">Example</span></span>

<span data-ttu-id="58655-118">次の例では、型指定された <xref:System.Data.DataSet> に対してクエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="58655-118">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a><span data-ttu-id="58655-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="58655-119">See also</span></span>

- [<span data-ttu-id="58655-120">DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="58655-120">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="58655-121">複数テーブルにまたがるクエリ</span><span class="sxs-lookup"><span data-stu-id="58655-121">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="58655-122">単一テーブルのクエリ</span><span class="sxs-lookup"><span data-stu-id="58655-122">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
