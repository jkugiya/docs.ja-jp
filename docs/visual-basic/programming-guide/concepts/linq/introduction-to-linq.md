---
description: '詳細情報: LINQ の概要 (Visual Basic)'
title: LINQ の概要
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: b6be93bbf9b458ca19068961617ee08f67601edc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426791"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="a3e28-103">LINQ の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3e28-103">Introduction to LINQ (Visual Basic)</span></span>

<span data-ttu-id="a3e28-104">統合言語クエリ (LINQ) は、.NET Framework Version 3.5 で導入された、オブジェクトとデータの溝を埋める画期的な手法です。</span><span class="sxs-lookup"><span data-stu-id="a3e28-104">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="a3e28-105">これまでは、データに対するクエリは、コンパイル時の型チェックや IntelliSense のサポートがない単純な文字列として表現されてきました。</span><span class="sxs-lookup"><span data-stu-id="a3e28-105">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="a3e28-106">さらに、SQL データベース、XML ドキュメント、さまざまな Web サービスなど、各種データ ソースの異なるクエリ言語を学習する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3e28-106">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="a3e28-107">LINQ により、"*クエリ*" は Visual Basic の高度な言語構成要素になります。</span><span class="sxs-lookup"><span data-stu-id="a3e28-107">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="a3e28-108">厳密に型指定されているオブジェクトのコレクションに対して、言語キーワードと使い慣れた演算子を用いてクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="a3e28-108">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="a3e28-109">Visual Basic を使って LINQ クエリを記述できます。対象は、<xref:System.Collections.IEnumerable> またはジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスをサポートする SQL Server データベース、XML ドキュメント、ADO.NET データセット、その他のオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="a3e28-109">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="a3e28-110">サード パーティからも、多くの Web サービスとその他のデータベース実装に対する LINQ のサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="a3e28-110">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="a3e28-111">新しいプロジェクトで LINQ クエリを使用できるほか、既存のプロジェクトで LINQ 以外のクエリを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a3e28-111">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="a3e28-112">唯一の要件は、プロジェクトが .NET Framework 3.5 以降をターゲットとしていることです。</span><span class="sxs-lookup"><span data-stu-id="a3e28-112">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="a3e28-113">次の Visual Studio の図は、SQL Server データベースに対して部分的に完了した LINQ クエリを示しています。このクエリは C# および Visual Basic の両方で記述されており、完全な型チェックと IntelliSense に対応しています。</span><span class="sxs-lookup"><span data-stu-id="a3e28-113">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![Intellisense を使用する LINQ クエリを示す図。](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="a3e28-115">次の手順</span><span class="sxs-lookup"><span data-stu-id="a3e28-115">Next Steps</span></span>  

 <span data-ttu-id="a3e28-116">LINQ の詳細については、最初に「[Visual Basic の LINQ の概要](getting-started-with-linq.md)」の概要に関するセクションで基本的な概念を理解し、次に関心のある LINQ テクノロジのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3e28-116">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="a3e28-117">SQL Server データベース:[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="a3e28-117">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="a3e28-118">XML ドキュメント:[LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span><span class="sxs-lookup"><span data-stu-id="a3e28-118">XML documents: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span></span>  
  
- <span data-ttu-id="a3e28-119">ADO.NET データセット:[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="a3e28-119">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="a3e28-120">.NET のコレクション、ファイル、文字列など:[LINQ to Objects (Visual Basic)](linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="a3e28-120">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e28-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3e28-121">See also</span></span>

- [<span data-ttu-id="a3e28-122">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3e28-122">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
