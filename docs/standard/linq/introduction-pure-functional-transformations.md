---
title: 純粋関数型変換の概要 - LINQ to XML
description: 関数型変換の概要について、その基になる概念や、それをサポートする言語構成要素も含めて説明します。
ms.date: 07/20/2015
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
ms.openlocfilehash: a2284c1ddff0234bc33f974ee001dde9819cf627
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412112"
---
# <a name="introduction-to-pure-functional-transformations-linq-to-xml"></a><span data-ttu-id="ebd1f-103">純粋関数型変換の概要 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ebd1f-103">Introduction to pure functional transformations (LINQ to XML)</span></span>

<span data-ttu-id="ebd1f-104">ここでは、関数型変換の概要について、その基になる概念や、それをサポートする言語構成要素も含めて説明します。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-104">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="ebd1f-105">また、オブジェクト指向変換と関数型変換という 2 つのプログラミング方法を対比させて、関数型変換に移行するためのアドバイスを紹介します。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-105">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="ebd1f-106">関数型変換はさまざまなプログラミング シナリオで使用できますが、ここでは XML 変換を具体例として取り上げます。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-106">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>

 <span data-ttu-id="ebd1f-107">「[チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作](xml-shape-wordprocessingml-documents.md)」チュートリアルは、それぞれ直前の例を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-107">The [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="ebd1f-108">これらの例では、純粋関数型変換を使用して XML を操作する方法を説明する複数の例が示されています。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-108">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span> <span data-ttu-id="ebd1f-109">このチュートリアルでは、C# または Visual Basic に関する実践的な知識を前提としています。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-109">This tutorial assumes a working knowledge of C# or Visual Basic.</span></span> <span data-ttu-id="ebd1f-110">このチュートリアルでは言語構造の詳細なセマンティクスについては説明しませんが、必要に応じて言語ドキュメントへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-110">Detailed semantics of the language constructs aren't provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>

 <span data-ttu-id="ebd1f-111">コンピューター科学の基本概念と、XML 名前空間など XML に関する実践的な知識も前提としています。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-111">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ebd1f-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ebd1f-112">In this section</span></span>

|<span data-ttu-id="ebd1f-113">[アーティクル]</span><span class="sxs-lookup"><span data-stu-id="ebd1f-113">Article</span></span>|<span data-ttu-id="ebd1f-114">説明</span><span class="sxs-lookup"><span data-stu-id="ebd1f-114">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="ebd1f-115">概念と用語 (関数型変換)</span><span class="sxs-lookup"><span data-stu-id="ebd1f-115">Concepts and terminology (functional transformation)</span></span>](concepts-terminology-functional-transformation.md)|<span data-ttu-id="ebd1f-116">純粋関数型変換の概念と用語について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-116">Introduces the concepts and terminology of pure functional transformations.</span></span>|
|[<span data-ttu-id="ebd1f-117">関数型プログラミングと命令型プログラミング</span><span class="sxs-lookup"><span data-stu-id="ebd1f-117">Functional programming vs. imperative programming</span></span>](functional-vs-imperative-programming.md)|<span data-ttu-id="ebd1f-118">関数型プログラミングを従来の命令型 (手続き型) プログラミングと比較対照します。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-118">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|
|[<span data-ttu-id="ebd1f-119">純粋関数にリファクタリングする</span><span class="sxs-lookup"><span data-stu-id="ebd1f-119">Refactor into pure functions</span></span>](refactor-pure-functions.md)|<span data-ttu-id="ebd1f-120">純粋関数について説明し、純粋関数と純粋でない関数の例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-120">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|
|[<span data-ttu-id="ebd1f-121">関数型変換の適用範囲</span><span class="sxs-lookup"><span data-stu-id="ebd1f-121">Applicability of functional transformation</span></span>](applicability-functional-transformation.md)|<span data-ttu-id="ebd1f-122">関数型変換の一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-122">Describes typical scenarios for functional transformations.</span></span>|
|[<span data-ttu-id="ebd1f-123">XML の関数型変換</span><span class="sxs-lookup"><span data-stu-id="ebd1f-123">Functional transformation of XML</span></span>](functional-transformation-xml.md)|<span data-ttu-id="ebd1f-124">XML ツリーの変換のコンテキストにおける関数型変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebd1f-124">Describes functional transformations in the context of transforming XML trees.</span></span>|
