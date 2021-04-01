---
title: XML ツリーのクエリの概要 - LINQ to XML
description: XML ツリーにクエリを実行する方法と、クエリと関数型構築を組み合わせ、ツリーを作り変える方法について説明します。
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 3529650aa5ee0575331653f5714c841d1fc1dfb5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366012"
---
# <a name="query-xml-trees-overview-linq-to-xml"></a><span data-ttu-id="d7fde-103">XML ツリーのクエリの概要 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d7fde-103">Query XML trees overview (LINQ to XML)</span></span>

<span data-ttu-id="d7fde-104">XML ツリーをインスタンス化してからクエリを記述することが、ツリーからデータを抽出する最も効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="d7fde-104">After you've instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="d7fde-105">また、関数型構築と組み合わせてクエリを実行すると、元のドキュメントとは異なる形式の新しい XML ドキュメントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d7fde-105">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>

<span data-ttu-id="d7fde-106">LINQ クエリの背景情報については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7fde-106">For background information about LINQ queries, see:</span></span>

- [<span data-ttu-id="d7fde-107">LINQ クエリの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="d7fde-107">Introduction to LINQ Queries (C#)</span></span>](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="d7fde-108">初めての LINQ クエリの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7fde-108">Writing Your First LINQ Query (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)

## <a name="in-this-section"></a><span data-ttu-id="d7fde-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d7fde-109">In this section</span></span>

<span data-ttu-id="d7fde-110">記事のこのセクションでは、例を含む、LINQ to XML クエリに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d7fde-110">This section of articles provides information, including examples, about LINQ to XML queries.</span></span> <span data-ttu-id="d7fde-111">次のサブセクションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="d7fde-111">It comprises the following subsections:</span></span>

|<span data-ttu-id="d7fde-112">[アーティクル]</span><span class="sxs-lookup"><span data-stu-id="d7fde-112">Article</span></span>|<span data-ttu-id="d7fde-113">説明</span><span class="sxs-lookup"><span data-stu-id="d7fde-113">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="d7fde-114">基本的なクエリ</span><span class="sxs-lookup"><span data-stu-id="d7fde-114">Basic queries</span></span>](find-element-specific-attribute.md)|<span data-ttu-id="d7fde-115">XML ツリーのクエリの一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7fde-115">Provides common examples of querying XML trees.</span></span>|
|[<span data-ttu-id="d7fde-116">射影と変換</span><span class="sxs-lookup"><span data-stu-id="d7fde-116">Projections and transformations</span></span>](work-dictionaries-linq-xml.md)|<span data-ttu-id="d7fde-117">XML ツリーからの射影と XML ツリーの変換の一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7fde-117">Provides common examples of projecting from and transforming XML trees.</span></span>|
|[<span data-ttu-id="d7fde-118">高度なクエリ手法</span><span class="sxs-lookup"><span data-stu-id="d7fde-118">Advanced query techniques</span></span>](join-two-collections.md)|<span data-ttu-id="d7fde-119">より高度なシナリオで役立つクエリ手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7fde-119">Provides query techniques that are useful in more advanced scenarios.</span></span>|
|[<span data-ttu-id="d7fde-120">XPath ユーザー向けの LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="d7fde-120">LINQ to XML for XPath users</span></span>](comparison-xpath-linq-xml.md)|<span data-ttu-id="d7fde-121">多くの XPath 式とそれらに対応する LINQ to XML の式について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7fde-121">Presents a number of XPath expressions and their LINQ to XML equivalents.</span></span>|
|[<span data-ttu-id="d7fde-122">純粋関数型変換の概要</span><span class="sxs-lookup"><span data-stu-id="d7fde-122">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)|<span data-ttu-id="d7fde-123">関数型のプログラミング形式でクエリを記述する簡単なチュートリアルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d7fde-123">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d7fde-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7fde-124">See also</span></span>

- [<span data-ttu-id="d7fde-125">統合言語クエリ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d7fde-125">Language-Integrated Query (LINQ) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d7fde-126">LINQ クエリの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="d7fde-126">Introduction to LINQ Queries (C#)</span></span>](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="d7fde-127">LINQ (Visual Basic における)</span><span class="sxs-lookup"><span data-stu-id="d7fde-127">LINQ in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="d7fde-128">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7fde-128">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d7fde-129">Visual Basic の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="d7fde-129">Getting Started with LINQ in Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="d7fde-130">初めての LINQ クエリの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7fde-130">Writing Your First LINQ Query (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)
