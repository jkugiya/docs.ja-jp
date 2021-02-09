---
description: '詳細情報: LINQ to DataSet'
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 74b5f97d9fecb05b1fd13e986dd0cbcc10fa1456
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681670"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="cb142-103">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="cb142-103">LINQ to DataSet</span></span>

<span data-ttu-id="cb142-104">LINQ to DataSet を使うと、<xref:System.Data.DataSet> オブジェクトにキャッシュされたデータに対するクエリを、いっそう簡単かつ高速に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb142-104">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="cb142-105">具体的には、LINQ to DataSet では、クエリを記述するのにクエリ言語ではなくプログラミング言語そのものを使用できるので、クエリ操作が容易になります。</span><span class="sxs-lookup"><span data-stu-id="cb142-105">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="cb142-106">これは、Visual Studio 開発者にとって特に便利で、Visual Studio によって提供されるコンパイル時の構文チェック、静的な型指定、IntelliSense のサポートをクエリで利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb142-106">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="cb142-107">また、LINQ to DataSet を使用すると、1 つまたは複数のデータ ソースから取得して統合したデータを照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb142-107">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="cb142-108">これにより、ローカルに集計されたデータのクエリや Web アプリケーションでの中間層のキャッシュなど、データの表現方法や扱いに柔軟性が要求されるさまざまなシナリオが実現します。</span><span class="sxs-lookup"><span data-stu-id="cb142-108">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="cb142-109">特に、汎用のレポート作成、分析、ビジネス インテリジェンスを行うアプリケーションでは、この手法を用いたデータ操作が欠かせません。</span><span class="sxs-lookup"><span data-stu-id="cb142-109">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="cb142-110">LINQ to DataSet の機能は、主に <xref:System.Data.DataRowExtensions> クラスと <xref:System.Data.DataTableExtensions> クラスの拡張メソッドを通して公開されます。</span><span class="sxs-lookup"><span data-stu-id="cb142-110">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="cb142-111">LINQ to DataSet は、既存の ADO.NET アーキテクチャを基にして構築され、それを使用するようになっており、アプリケーション コードで ADO.NET に代わるものではありません。</span><span class="sxs-lookup"><span data-stu-id="cb142-111">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="cb142-112">既存の ADO.NET コードは、LINQ to DataSet アプリケーションでも引き続き機能します。</span><span class="sxs-lookup"><span data-stu-id="cb142-112">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="cb142-113">LINQ to DataSet と ADO.NET の関係およびデータ ストアを、次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="cb142-113">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![LINQ to DataSet が ADO.NET プロバイダーに基づいていることを示す図。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="cb142-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="cb142-115">In This Section</span></span>  

 [<span data-ttu-id="cb142-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="cb142-116">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="cb142-117">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cb142-117">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="cb142-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb142-118">Reference</span></span>  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="cb142-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb142-119">See also</span></span>

- [<span data-ttu-id="cb142-120">統合言語クエリ (LINQ) - C#</span><span class="sxs-lookup"><span data-stu-id="cb142-120">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="cb142-121">統合言語クエリ (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb142-121">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="cb142-122">LINQ と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cb142-122">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="cb142-123">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cb142-123">ADO.NET</span></span>](index.md)
