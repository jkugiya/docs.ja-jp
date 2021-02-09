---
description: '詳細情報: DataSet のクエリ (LINQ to DataSet)'
title: DataSet のクエリ (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 609de99069d39317d8d372cb2a7f43ea301ada2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663457"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="7c8b9-103">DataSet のクエリ (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7c8b9-103">Querying DataSets (LINQ to DataSet)</span></span>

<span data-ttu-id="7c8b9-104"><xref:System.Data.DataSet> オブジェクトへのデータの読み込みが完了すると、そのデータセットに対してクエリを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-104">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="7c8b9-105">LINQ to DataSet でのクエリの作成は、他の LINQ (統合言語クエリ) 対応データ ソースに対して LINQ を使用する場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-105">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="7c8b9-106">ただし、<xref:System.Data.DataSet> オブジェクトに対して LINQ クエリを使用する場合は、カスタム型の列挙型ではなく、<xref:System.Data.DataRow> オブジェクトの列挙型のクエリを実行しているということに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-106">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="7c8b9-107">つまり、LINQ クエリでは、<xref:System.Data.DataRow> クラスの任意のメンバーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-107">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="7c8b9-108">これにより、高度で複雑なクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-108">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="7c8b9-109">LINQ の他の実装と同じように、LINQ to DataSet クエリは、クエリ式の構文とメソッド ベースのクエリ構文という 2 つの異なる形式で作成できます。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-109">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="7c8b9-110">クエリ式の構文またはメソッド ベースのクエリ構文を使用して、<xref:System.Data.DataSet> 内の単一テーブル、<xref:System.Data.DataSet> 内の複数テーブル、または、型指定された <xref:System.Data.DataSet> 内のテーブルを対象にクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c8b9-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7c8b9-111">In This Section</span></span>  

 [<span data-ttu-id="7c8b9-112">単一テーブルのクエリ</span><span class="sxs-lookup"><span data-stu-id="7c8b9-112">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="7c8b9-113">単一テーブルのクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="7c8b9-114">複数テーブルにまたがるクエリ</span><span class="sxs-lookup"><span data-stu-id="7c8b9-114">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="7c8b9-115">複数テーブルにまたがるクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="7c8b9-116">型指定された DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="7c8b9-116">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="7c8b9-117">型指定された <xref:System.Data.DataSet> オブジェクトに対してクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7c8b9-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8b9-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c8b9-118">See also</span></span>

- [<span data-ttu-id="7c8b9-119">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="7c8b9-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="7c8b9-120">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="7c8b9-120">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
