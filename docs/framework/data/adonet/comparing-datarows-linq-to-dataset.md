---
description: '詳細情報: DataRow の比較 (LINQ to DataSet)'
title: DataRow の比較 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: df410432ab31d5ee284cb1d7cd15661db65ca503
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663938"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="e7e97-103">DataRow の比較 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e7e97-103">Comparing DataRows (LINQ to DataSet)</span></span>

<span data-ttu-id="e7e97-104">LINQ (統合言語クエリ) では、ソース要素を比較し、両者が等しいかどうかを調べるための各種の集合演算子が定義されています。</span><span class="sxs-lookup"><span data-stu-id="e7e97-104">Language-Integrated Query (LINQ) defines various set operators to compare source elements to see if they are equal.</span></span> <span data-ttu-id="e7e97-105">LINQ で提供されている集合演算子は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e7e97-105">LINQ provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="e7e97-106">これらの演算子は、要素のコレクションに対して <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> メソッドおよび <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> メソッドを呼び出すことによってソース要素を比較します。</span><span class="sxs-lookup"><span data-stu-id="e7e97-106">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="e7e97-107"><xref:System.Data.DataRow> の場合、これらの演算子によって実行されるのは参照の比較です。表形式のデータに対する集合演算においては適切な動作とは言えません。</span><span class="sxs-lookup"><span data-stu-id="e7e97-107">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="e7e97-108">通常、集合演算で重要なのは要素の値が等しいかどうかであって、要素の参照が等しいかどうかではありません。</span><span class="sxs-lookup"><span data-stu-id="e7e97-108">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="e7e97-109">このような理由から、<xref:System.Data.DataRowComparer> クラスが LINQ to DataSet に追加されました。</span><span class="sxs-lookup"><span data-stu-id="e7e97-109">Therefore, the <xref:System.Data.DataRowComparer> class has been added to LINQ to DataSet.</span></span> <span data-ttu-id="e7e97-110">このクラスを使用することで行の値を比較できます。</span><span class="sxs-lookup"><span data-stu-id="e7e97-110">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="e7e97-111"><xref:System.Data.DataRowComparer> クラスには、<xref:System.Data.DataRow> の値を比較するための機能が実装されています。このクラスを <xref:System.Linq.Enumerable.Distinct%2A> などの集合演算に使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7e97-111">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="e7e97-112">このクラスを直接インスタンス化することはできません。代わりに、<xref:System.Data.DataRowComparer.Default%2A> プロパティを使用して、<xref:System.Data.DataRowComparer%601> のインスタンスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7e97-112">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="e7e97-113">その後、<xref:System.Data.DataRowComparer%601.Equals%2A> メソッドを呼び出す際、比較する 2 つの <xref:System.Data.DataRow> オブジェクトを入力パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="e7e97-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="e7e97-114"><xref:System.Data.DataRowComparer%601.Equals%2A> メソッドは、2 つの `true` オブジェクトに含まれる一連の列値が等しければ <xref:System.Data.DataRow> を、それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="e7e97-114">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7e97-115">例</span><span class="sxs-lookup"><span data-stu-id="e7e97-115">Example</span></span>  

 <span data-ttu-id="e7e97-116">この例では、両方のテーブルに存在する連絡先を `Intersect` を使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="e7e97-116">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="e7e97-117">例</span><span class="sxs-lookup"><span data-stu-id="e7e97-117">Example</span></span>  

 <span data-ttu-id="e7e97-118">次の例では、2 つの行を比較して、そのハッシュ コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="e7e97-118">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="e7e97-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7e97-119">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="e7e97-120">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="e7e97-120">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="e7e97-121">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="e7e97-121">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
