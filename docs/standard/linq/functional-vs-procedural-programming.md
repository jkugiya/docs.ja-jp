---
title: 関数型プログラミングと手続き型プログラミング
description: LINQ to XML では、XML アプリケーションを作成するために関数型構築と手続き型手法の両方がサポートされています。 関数型構築は宣言型の方法です。 手続き型手法では、XML ツリーをメモリ内で変更できます。
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: a2753a31e88fd338dad61063f559431869b9e17f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103365988"
---
# <a name="functional-vs-procedural-programming-linq-to-xml"></a><span data-ttu-id="bf254-105">関数型プログラミングと手続き型プログラミング (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bf254-105">Functional vs. procedural programming (LINQ to XML)</span></span>

<span data-ttu-id="bf254-106">XML アプリケーションには、次のようにさまざまな種類があります。</span><span class="sxs-lookup"><span data-stu-id="bf254-106">There are various types of XML applications:</span></span>

- <span data-ttu-id="bf254-107">ソース XML ドキュメントを受け取り、そのドキュメントとは構造の異なる新しい XML ドキュメントを生成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="bf254-107">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>
- <span data-ttu-id="bf254-108">ソース XML ドキュメントを受け取り、HTML や CSV テキスト ファイルなどのまったく異なる形式のドキュメントを生成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="bf254-108">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>
- <span data-ttu-id="bf254-109">ソース XML ドキュメントを受け取り、データベースにレコードを挿入するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="bf254-109">Some applications take source XML documents, and insert records into a database.</span></span>
- <span data-ttu-id="bf254-110">データベースなどの別のソースからデータを受け取り、そのデータから XML ドキュメントを作成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="bf254-110">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>

<span data-ttu-id="bf254-111">XML アプリケーションには他にも種類がありますが、上記のアプリケーションは XML プログラマが実装する必要がある代表的な機能です。</span><span class="sxs-lookup"><span data-stu-id="bf254-111">These aren't all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>

<span data-ttu-id="bf254-112">上記のすべてのアプリケーションで、開発者は 2 つの対照的な方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf254-112">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>

- <span data-ttu-id="bf254-113">宣言型の方法を使用する関数型構築</span><span class="sxs-lookup"><span data-stu-id="bf254-113">Functional construction using a declarative approach.</span></span>
- <span data-ttu-id="bf254-114">プロシージャ コードを使用するメモリ内の XML ツリーの変更</span><span class="sxs-lookup"><span data-stu-id="bf254-114">In-memory XML tree modification using procedural code.</span></span>

<span data-ttu-id="bf254-115">LINQ to XML は両方の方法をサポートします。</span><span class="sxs-lookup"><span data-stu-id="bf254-115">LINQ to XML supports both approaches.</span></span>

<span data-ttu-id="bf254-116">関数型の方法を使用する場合は、ソース ドキュメントを受け取り、必要な構造を持つ完全に新しいドキュメントが生成される変換を記述します。</span><span class="sxs-lookup"><span data-stu-id="bf254-116">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>

<span data-ttu-id="bf254-117">XML ツリーを直接変更する場合は、メモリ内の XML ツリーでノード間を移動し、必要に応じてノードを挿入、削除、変更します。</span><span class="sxs-lookup"><span data-stu-id="bf254-117">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>

<span data-ttu-id="bf254-118">いずれの方法でも LINQ to XML を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf254-118">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="bf254-119">同じクラスを使用し、場合によっては同じメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf254-119">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="bf254-120">ただし、2 つの方法の構造と目標は異なります。</span><span class="sxs-lookup"><span data-stu-id="bf254-120">However, the structure and goals of the two approaches are different.</span></span> <span data-ttu-id="bf254-121">たとえば、これらの方法のうち、どちらのパフォーマンスが優れているか、また使用するメモリ量はどちらが多い (または少ない) かは、状況によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf254-121">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="bf254-122">また、どちらの方法が保守性に優れたコードをより簡単に記述し生成できるかも、状況によって異なります。</span><span class="sxs-lookup"><span data-stu-id="bf254-122">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>

<span data-ttu-id="bf254-123">2 つの方法の違いについては、「[メモリ内の XML ツリーの変更と関数型構築の比較](in-memory-xml-tree-modification-vs-functional-construction.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf254-123">To see the two approaches contrasted, see [In-memory XML tree modification vs. functional construction](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

<span data-ttu-id="bf254-124">関数型変換の記述に関するチュートリアルについては、「[純粋関数型変換の概要](introduction-pure-functional-transformations.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf254-124">For a tutorial on writing functional transformations, see [Introduction to pure functional transformations](introduction-pure-functional-transformations.md).</span></span>
