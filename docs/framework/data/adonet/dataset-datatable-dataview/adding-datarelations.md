---
description: '詳細情報: DataRelation の追加'
title: DataRelation の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 56438c9b69fab71c4843582b6cfea50fa057eb44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725221"
---
# <a name="adding-datarelations"></a><span data-ttu-id="994ec-103">DataRelation の追加</span><span class="sxs-lookup"><span data-stu-id="994ec-103">Adding DataRelations</span></span>

<span data-ttu-id="994ec-104">複数の <xref:System.Data.DataSet> オブジェクトを含む <xref:System.Data.DataTable> では、<xref:System.Data.DataRelation> オブジェクトを使用して 1 つのテーブルを別のテーブルに関連付けたり、テーブル間を移動したり、関連付けたテーブルから子または親の行を戻したりできます。</span><span class="sxs-lookup"><span data-stu-id="994ec-104">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="994ec-105">**DataRelation** の作成に必要な引数は、作成する **DataRelation** の名前、およびそのリレーションシップで親子の列となる列への 1 つ以上の <xref:System.Data.DataColumn> 参照の配列です。</span><span class="sxs-lookup"><span data-stu-id="994ec-105">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="994ec-106">**DataRelation** を作成した後は、それを使用して、テーブル間の移動や値の取得を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="994ec-106">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="994ec-107"><xref:System.Data.DataSet> に **DataRelation** を追加すると、既定では、<xref:System.Data.UniqueConstraint> が親テーブルに、<xref:System.Data.ForeignKeyConstraint> が子テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="994ec-107">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="994ec-108">これらの既定の制約について詳しくは、「[DataTable の制約](datatable-constraints.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="994ec-108">For more information about these default constraints, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="994ec-109">次のコード例では、<xref:System.Data.DataSet> の 2 つの <xref:System.Data.DataTable> オブジェクトを使用して、**DataRelation** を作成します。</span><span class="sxs-lookup"><span data-stu-id="994ec-109">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="994ec-110">各 <xref:System.Data.DataTable> にある **CustID** という名前の列は、2 つの <xref:System.Data.DataTable> オブジェクト間のリンクとして機能します。</span><span class="sxs-lookup"><span data-stu-id="994ec-110">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="994ec-111">例では、単一の **DataRelation** が <xref:System.Data.DataSet> の **Relations** コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="994ec-111">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="994ec-112">例の最初の引数では、作成する **DataRelation** の名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="994ec-112">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="994ec-113">2 番目の引数では親の **DataColumn** が設定され、3 番目の引数では子の **DataColumn** が設定されます。</span><span class="sxs-lookup"><span data-stu-id="994ec-113">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="994ec-114">**DataRelation** には、**Nested** プロパティもあります。それを **true** に設定すると、<xref:System.Data.DataSet.WriteXml%2A> を使用して XML 要素として書き込んだときに、子テーブルの行が、親テーブルの関連付けられた行の中に入れ子になります。</span><span class="sxs-lookup"><span data-stu-id="994ec-114">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="994ec-115">詳しくは、「[DataSet での XML の使用](using-xml-in-a-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="994ec-115">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="994ec-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="994ec-116">See also</span></span>

- [<span data-ttu-id="994ec-117">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="994ec-117">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="994ec-118">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="994ec-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
