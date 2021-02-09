---
description: '詳細情報: DataView の DataRowView コレクションの照会'
title: DataView の DataRowView コレクションの照会
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 2158e1c82c530c48d7edad71f46f03cbfe566536
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695932"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="111e7-103">DataView の DataRowView コレクションの照会</span><span class="sxs-lookup"><span data-stu-id="111e7-103">Querying the DataRowView Collection in a DataView</span></span>

<span data-ttu-id="111e7-104"><xref:System.Data.DataView> は、<xref:System.Data.DataRowView> オブジェクトの列挙可能なコレクションを公開します。</span><span class="sxs-lookup"><span data-stu-id="111e7-104">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="111e7-105"><xref:System.Data.DataRowView> は、<xref:System.Data.DataRow> のカスタマイズされたビューを表し、<xref:System.Data.DataRow> の特定のバージョンをコントロールに表示します。</span><span class="sxs-lookup"><span data-stu-id="111e7-105"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="111e7-106"><xref:System.Data.DataRow> などのコントロールを通じて、<xref:System.Windows.Forms.DataGridView> のバージョンを 1 つだけ表示できます。</span><span class="sxs-lookup"><span data-stu-id="111e7-106">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="111e7-107"><xref:System.Data.DataRow> が <xref:System.Data.DataRowView> の <xref:System.Data.DataRowView.Row%2A> プロパティを使用して公開している <xref:System.Data.DataRowView> にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="111e7-107">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="111e7-108"><xref:System.Data.DataRowView> を使用して値を表示している場合は、<xref:System.Data.DataView.RowStateFilter%2A> プロパティによって、基になる <xref:System.Data.DataRow> から公開される行バージョンが決まります。</span><span class="sxs-lookup"><span data-stu-id="111e7-108">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="111e7-109"><xref:System.Data.DataRow> を使用してさまざまな行バージョンにアクセスする方法については、「[行の状態とバージョン](./dataset-datatable-dataview/row-states-and-row-versions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="111e7-109">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](./dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="111e7-110"><xref:System.Data.DataView> によって公開される <xref:System.Data.DataRowView> オブジェクトのコレクションは列挙可能であるため、LINQ to DataSet を使用してクエリできます。</span><span class="sxs-lookup"><span data-stu-id="111e7-110">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use LINQ to DataSet to query over it.</span></span>  
  
 <span data-ttu-id="111e7-111">次の例では、`Product` テーブルに対して赤色の製品を照会し、そのクエリに基づくテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="111e7-111">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="111e7-112">このテーブルから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView.RowStateFilter%2A> プロパティに、削除行と変更行を条件とするフィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="111e7-112">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="111e7-113">次に <xref:System.Data.DataView> を LINQ クエリのソースとして使用し、変更済みおよび削除済みの <xref:System.Data.DataRowView> オブジェクトを <xref:System.Windows.Forms.DataGridView> コントロールにバインドします。</span><span class="sxs-lookup"><span data-stu-id="111e7-113">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="111e7-114">次の例では、<xref:System.Windows.Forms.DataGridView> コントロールにバインドされたビューから製品のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="111e7-114">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="111e7-115"><xref:System.Data.DataView> に対して赤色の製品を照会し、並べ替えた結果を <xref:System.Windows.Forms.DataGridView> コントロールにバインドしています。</span><span class="sxs-lookup"><span data-stu-id="111e7-115">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="111e7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="111e7-116">See also</span></span>

- [<span data-ttu-id="111e7-117">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="111e7-117">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
