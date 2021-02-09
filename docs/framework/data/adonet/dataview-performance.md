---
description: '詳細情報: DataView のパフォーマンス'
title: DataView のパフォーマンス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 6319eb3846f116b0297df701e9a6abc6c1deb2b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651289"
---
# <a name="dataview-performance"></a><span data-ttu-id="34dae-103">DataView のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="34dae-103">DataView Performance</span></span>

<span data-ttu-id="34dae-104">このトピックでは、<xref:System.Data.DataView.Find%2A> クラスの <xref:System.Data.DataView.FindRows%2A> メソッドと <xref:System.Data.DataView> メソッドを使用すること、および、Web アプリケーションで <xref:System.Data.DataView> をキャッシュすることのパフォーマンス上の利点について説明します。</span><span class="sxs-lookup"><span data-stu-id="34dae-104">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="34dae-105">Find と FindRows</span><span class="sxs-lookup"><span data-stu-id="34dae-105">Find and FindRows</span></span>  

 <span data-ttu-id="34dae-106"><xref:System.Data.DataView> はインデックスを構築します。</span><span class="sxs-lookup"><span data-stu-id="34dae-106"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="34dae-107">インデックスには、テーブル内またはビュー内の 1 つ以上の列から構築されたキーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="34dae-107">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="34dae-108">これらのキーは特定の構造内に格納され、<xref:System.Data.DataView> はその構造を使用して、キー値に関連した 1 つ以上の行を効率よく迅速に検出できます。</span><span class="sxs-lookup"><span data-stu-id="34dae-108">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="34dae-109">フィルター処理や並べ替えなど、インデックスを使用した操作では、大幅なパフォーマンス向上が期待できます。</span><span class="sxs-lookup"><span data-stu-id="34dae-109">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="34dae-110"><xref:System.Data.DataView> のインデックスは、<xref:System.Data.DataView> の作成時に構築されるほか、並べ替えまたはフィルター処理の情報が変更されたときにも構築されます。</span><span class="sxs-lookup"><span data-stu-id="34dae-110">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="34dae-111"><xref:System.Data.DataView> を作成した後で、並べ替えまたはフィルター処理の情報を設定した場合、インデックスが最低でも 2 回 (<xref:System.Data.DataView> の作成時と、並べ替えまたはフィルターのプロパティの変更時) 構築されることになります。</span><span class="sxs-lookup"><span data-stu-id="34dae-111">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="34dae-112"><xref:System.Data.DataView> でのフィルター処理と並べ替えについて詳しくは、「[DataView によるフィルター処理](filtering-with-dataview-linq-to-dataset.md)」および「[DataView による並べ替え](sorting-with-dataview-linq-to-dataset.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34dae-112">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="34dae-113">データ サブセットの動的ビューの作成とは対照的に、データに対する特定のクエリの結果を取得する場合は、<xref:System.Data.DataView.Find%2A> プロパティを設定する代わりに <xref:System.Data.DataView.FindRows%2A> の <xref:System.Data.DataView> メソッドまたは <xref:System.Data.DataView.RowFilter%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="34dae-113">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="34dae-114"><xref:System.Data.DataView.RowFilter%2A> プロパティは、データ連結アプリケーションでの使用に適しています。このアプリケーションでは、連結されたコントロールによってフィルター処理結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="34dae-114">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="34dae-115"><xref:System.Data.DataView.RowFilter%2A> プロパティを設定すると、データのインデックスが再構築され、アプリケーションのオーバーヘッドが増加してパフォーマンスの低下を招きます。</span><span class="sxs-lookup"><span data-stu-id="34dae-115">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="34dae-116"><xref:System.Data.DataView.Find%2A> メソッドと <xref:System.Data.DataView.FindRows%2A> メソッドでは、現在のインデックスが使用されます。このため、インデックスを再構築する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="34dae-116">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="34dae-117"><xref:System.Data.DataView.Find%2A> または <xref:System.Data.DataView.FindRows%2A> を 1 回だけ呼び出す場合は、既存の <xref:System.Data.DataView> を使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="34dae-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="34dae-118"><xref:System.Data.DataView.Find%2A> または <xref:System.Data.DataView.FindRows%2A> を複数回呼び出す場合は、新しい <xref:System.Data.DataView> を作成して検索対象の列のインデックスを再構築した後、<xref:System.Data.DataView.Find%2A> メソッドまたは <xref:System.Data.DataView.FindRows%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="34dae-118">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="34dae-119"><xref:System.Data.DataView.Find%2A> メソッドおよび <xref:System.Data.DataView.FindRows%2A> メソッドについて詳しくは、「[行の検索](./dataset-datatable-dataview/finding-rows.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34dae-119">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="34dae-120">次の例では、<xref:System.Data.DataView.Find%2A> メソッドを使用して、姓が "Zhu" である連絡先を検索します。</span><span class="sxs-lookup"><span data-stu-id="34dae-120">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="34dae-121">次の例では、<xref:System.Data.DataView.FindRows%2A> メソッドを使用して、赤色の製品をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="34dae-121">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="34dae-122">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="34dae-122">ASP.NET</span></span>  

 <span data-ttu-id="34dae-123">ASP.NET は、メモリ内に作成するときにサーバー リソースを激しく消費するオブジェクトを保存するためのキャッシュ メカニズムを備えています。</span><span class="sxs-lookup"><span data-stu-id="34dae-123">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="34dae-124">こうしたリソースをキャッシュすることで、アプリケーションのパフォーマンスを大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="34dae-124">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="34dae-125">キャッシュは、<xref:System.Web.Caching.Cache> クラスに実装されています。キャッシュ インスタンスは、アプリケーションごとにプライベートに保たれます。</span><span class="sxs-lookup"><span data-stu-id="34dae-125">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="34dae-126">新しい <xref:System.Data.DataView> オブジェクトの作成はリソースを大量に消費する処理です。Web アプリケーションにこのキャッシュ機能を使用すれば、Web ページが更新されるたびに <xref:System.Data.DataView> を再構築する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="34dae-126">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="34dae-127">次の例では、ページが更新されたときにデータの並べ替えをし直さなくても済むように、<xref:System.Data.DataView> をキャッシュしています。</span><span class="sxs-lookup"><span data-stu-id="34dae-127">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
```vb  
If (Cache("ordersView") = Nothing) Then  
  
Dim dataSet As New DataSet()  
  
   FillDataSet(dataSet)  
  
   Dim orders As DataTable = dataSet.Tables("SalesOrderHeader")  
  
   Dim query = _  
                    From order In orders.AsEnumerable() _  
                    Where order.Field(Of Boolean)("OnlineOrderFlag") = True _  
                    Order By order.Field(Of Decimal)("TotalDue") _  
                    Select order  
  
   Dim view As DataView = query.AsDataView()  
  
   Cache.Insert("ordersView", view)  
  
End If  
  
Dim ordersView = CType(Cache("ordersView"), DataView)  
  
GridView1.DataSource = ordersView  
GridView1.DataBind()  
```  
  
```csharp  
if (Cache["ordersView"] == null)  
{  
   // Fill the DataSet.
   DataSet dataSet = FillDataSet();  
  
   DataTable orders = dataSet.Tables["SalesOrderHeader"];  
  
   EnumerableRowCollection<DataRow> query =  
                        from order in orders.AsEnumerable()  
                        where order.Field<bool>("OnlineOrderFlag") == true  
                        orderby order.Field<decimal>("TotalDue")  
                        select order;  
  
   DataView view = query.AsDataView();  
   Cache.Insert("ordersView", view);  
}  
  
DataView ordersView = (DataView)Cache["ordersView"];  
  
GridView1.DataSource = ordersView;  
GridView1.DataBind();  
```  
  
## <a name="see-also"></a><span data-ttu-id="34dae-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="34dae-128">See also</span></span>

- [<span data-ttu-id="34dae-129">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="34dae-129">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
