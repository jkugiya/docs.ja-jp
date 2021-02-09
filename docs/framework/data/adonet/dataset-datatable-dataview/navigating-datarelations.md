---
description: '詳細情報: DataRelation の移動'
title: DataRelation の移動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 72d5bbb282b3b43434e528390769e1203519e8e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651809"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="438d8-103">DataRelation の移動</span><span class="sxs-lookup"><span data-stu-id="438d8-103">Navigating DataRelations</span></span>

<span data-ttu-id="438d8-104"><xref:System.Data.DataRelation> の主な機能の 1 つは、<xref:System.Data.DataTable> の 1 つの <xref:System.Data.DataSet> から別の  を移動できることです。</span><span class="sxs-lookup"><span data-stu-id="438d8-104">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="438d8-105">これにより、関連付けられた **DataTable** から単一の **DataRow** を指定して、関連するすべての <xref:System.Data.DataRow> オブジェクトを 1 つの **DataTable** に取得できます。</span><span class="sxs-lookup"><span data-stu-id="438d8-105">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="438d8-106">たとえば、顧客のテーブルと注文のテーブル間に **DataRelation** を確立した後、**GetChildRows** を使用して、特定の顧客行に対するすべての注文行を取得できます。</span><span class="sxs-lookup"><span data-stu-id="438d8-106">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="438d8-107">次のコード例では、**DataSet** の **Customers** テーブルと **Orders** テーブルの間に **DataRelation** を作成し、各顧客に対するすべての注文を返します。</span><span class="sxs-lookup"><span data-stu-id="438d8-107">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="438d8-108">上記の例に基づいて、4 つのテーブルを相互に関連付け、そのテーブルのリレーションシップ間を移動する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="438d8-108">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="438d8-109">上の例のように、**CustomerID** によって **Customers** テーブルが **Orders** テーブルに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="438d8-109">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="438d8-110">特定の顧客の注文数とその **OrderID** の値を返すため、**Customers** テーブルの顧客ごとに、**Orders** テーブル内のすべての子の行が特定されます。</span><span class="sxs-lookup"><span data-stu-id="438d8-110">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="438d8-111">展開された例では、**OrderDetails** テーブルと **Products** テーブルからも値が返されます。</span><span class="sxs-lookup"><span data-stu-id="438d8-111">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="438d8-112">**OrderID** を使用して **Orders** テーブルが **OrderDetails** テーブルに関連付けられ、顧客の注文ごとに、注文された製品と数量が特定されます。</span><span class="sxs-lookup"><span data-stu-id="438d8-112">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="438d8-113">**OrderDetails** テーブルに含まれるのは、注文された製品の **ProductID** だけなので、**ProductName** を返すため、**ProductID** を使用して、**OrderDetails** が **Products** に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="438d8-113">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="438d8-114">この関係では、**Products** テーブルが親となり、**Order Details** テーブルが子となります。</span><span class="sxs-lookup"><span data-stu-id="438d8-114">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="438d8-115">その結果、**OrderDetails** テーブルの反復処理では、**GetParentRow** を呼び出して、関連付けられた **ProductName** の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="438d8-115">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="438d8-116">**DataRelation** が **Customers** テーブルと **Orders** テーブルに対して作成されるとき、**createConstraints** フラグに対して値が指定されていないことに注意してください (既定値は **true**)。</span><span class="sxs-lookup"><span data-stu-id="438d8-116">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="438d8-117">これにより、**Orders** テーブルのすべての行に対して、親の **Customers** テーブルに **CustomerID** の値が存在するものと設定されます。</span><span class="sxs-lookup"><span data-stu-id="438d8-117">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="438d8-118">**Customers** テーブルに存在しない **CustomerID** が **Orders** テーブルに存在した場合、<xref:System.Data.ForeignKeyConstraint> では例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="438d8-118">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="438d8-119">親の列に含まれていない値が子の列に含まれる場合は、**DataRelation** を追加するときに、**createConstraints** フラグを **false** に設定します。</span><span class="sxs-lookup"><span data-stu-id="438d8-119">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="438d8-120">この例では、**Orders** テーブルと **OrderDetails** テーブルの間の **DataRelation** に対して、**createConstraints** フラグが **false** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="438d8-120">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="438d8-121">このため、このアプリケーションでは、実行時に例外を生成せずに、**OrderDetails** テーブルのすべてのレコードと、**Orders** テーブルのレコードのサブセットだけを、返すことができます。</span><span class="sxs-lookup"><span data-stu-id="438d8-121">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="438d8-122">展開された例では、次の形式で出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="438d8-122">The expanded sample generates output in the following format.</span></span>  
  
```output  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 <span data-ttu-id="438d8-123">次のコード例はサンプルを拡張したものであり、**OrderDetails** テーブルと **Products** テーブルから値が返され、**Orders** テーブルからはレコードのサブセットだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="438d8-123">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="438d8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="438d8-124">See also</span></span>

- [<span data-ttu-id="438d8-125">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="438d8-125">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="438d8-126">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="438d8-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
