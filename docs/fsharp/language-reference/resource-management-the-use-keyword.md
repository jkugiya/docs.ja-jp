---
title: 'リソースの管理: use キーワード'
description: リソースの初期化と解放を制御できる F# キーワード 'use' および 'using' 関数について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627255"
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="6d672-103">リソースの管理: use キーワード</span><span class="sxs-lookup"><span data-stu-id="6d672-103">Resource Management: The use Keyword</span></span>

<span data-ttu-id="6d672-104">このトピックでは、リソースの初期化と解放を制御できるキーワード `use` および `using` 関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="6d672-104">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="6d672-105">リソース</span><span class="sxs-lookup"><span data-stu-id="6d672-105">Resources</span></span>

<span data-ttu-id="6d672-106">*"リソース"* という用語は、さまざまな形で使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d672-106">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="6d672-107">リソースは、アプリケーションで使用される文字列やグラフィックスなどのデータを指す場合がありますが、このコンテキストでは、 *"リソース"* は、グラフィックス デバイス コンテキスト、ファイル ハンドル、ネットワークとデータベース接続、待機ハンドルなどの同時実行オブジェクトなど、ソフトウェアまたはオペレーティング システムのリソースを指します。</span><span class="sxs-lookup"><span data-stu-id="6d672-107">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="6d672-108">これらのリソースのアプリケーションでの使用には、オペレーティング システムまたは他のリソース プロバイダーからリソースを取得し、その後、リソースをプールに解放することにより、別のアプリケーションに提供できるようにすることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6d672-108">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="6d672-109">アプリケーションでリソースが共通プールに解放されないと、問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="6d672-109">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="6d672-110">リソースの管理</span><span class="sxs-lookup"><span data-stu-id="6d672-110">Managing Resources</span></span>

<span data-ttu-id="6d672-111">アプリケーションでリソースを効率的かつ確実に管理するには、リソースを迅速かつ予測可能な方法で解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d672-111">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="6d672-112">.NET Framework を使用すると `System.IDisposable` インターフェイスが提供され、行いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="6d672-112">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="6d672-113">`System.IDisposable` を実装する型には、リソースを正しく解放する `System.IDisposable.Dispose` メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="6d672-113">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="6d672-114">適切に作成されたアプリケーションを使用すると、制限されているリソースを保持するオブジェクトが不要になったときに `System.IDisposable.Dispose` が迅速かつ確実に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6d672-114">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="6d672-115">幸いなことに、ほとんどの .NET 言語では、これを容易にするためのサポートが提供されており、F# も例外ではありません。</span><span class="sxs-lookup"><span data-stu-id="6d672-115">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="6d672-116">破棄パターンをサポートする便利な言語構成要素として、`use` バインディングと `using` 関数の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="6d672-116">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="6d672-117">use バインディング</span><span class="sxs-lookup"><span data-stu-id="6d672-117">use Binding</span></span>

<span data-ttu-id="6d672-118">`use` キーワードには、`let` バインディングのそれと似た以下の形式のものがあります。</span><span class="sxs-lookup"><span data-stu-id="6d672-118">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="6d672-119">use *value* = *expression*</span><span class="sxs-lookup"><span data-stu-id="6d672-119">use *value* = *expression*</span></span>

<span data-ttu-id="6d672-120">これは `let` バインディングと同じ機能を提供しますが、値がスコープ外になったときに `Dispose` への呼び出しを値に追加します。</span><span class="sxs-lookup"><span data-stu-id="6d672-120">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="6d672-121">コンパイラにより値に null チェックが挿入されるため、値が `null` の場合、`Dispose` への呼び出しは試行されないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="6d672-121">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="6d672-122">次の例は、`use` キーワードを使用してファイルを自動的に閉じる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d672-122">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> <span data-ttu-id="6d672-123">`use` は、コンピュテーション式で使用することができます。その場合は、`use` 式のカスタマイズされたバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d672-123">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="6d672-124">詳細については、「[シーケンス](sequences.md)」、「[非同期ワークフロー](asynchronous-workflows.md)」、「[コンピュテーション式](computation-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d672-124">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="using-function"></a><span data-ttu-id="6d672-125">using 関数</span><span class="sxs-lookup"><span data-stu-id="6d672-125">using Function</span></span>

<span data-ttu-id="6d672-126">`using` 関数の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6d672-126">The `using` function has the following form:</span></span>

<span data-ttu-id="6d672-127">`using` (*expression1*) *function-or-lambda*</span><span class="sxs-lookup"><span data-stu-id="6d672-127">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="6d672-128">`using` 式では、*expression1* により、破棄する必要のあるオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6d672-128">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="6d672-129">*expression1* (破棄する必要のあるオブジェクト) の結果は、*function-or-lambda* に対する引数 *value* になります。これは、*expression1* によって生成された値と一致する型の残りの 1 つの引数を予期する関数、またはその型の引数を予期するラムダ式のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="6d672-129">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="6d672-130">関数の実行が終了すると、ランタイムにより `Dispose` が呼び出され、リソースが解放されます (値が `null` の場合を除きます。この場合、Dispose への呼び出しは試行されません)。</span><span class="sxs-lookup"><span data-stu-id="6d672-130">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="6d672-131">次の例は、ラムダ式を含む `using` 式を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d672-131">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="6d672-132">次の例は、関数を含む `using` 式を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d672-132">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="6d672-133">関数は、いくつかの引数が既に適用されている関数である可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6d672-133">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="6d672-134">次のコード例はこの処理方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d672-134">The following code example demonstrates this.</span></span> <span data-ttu-id="6d672-135">文字列 `XYZ` を含むファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6d672-135">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="6d672-136">`using` 関数と `use` バインディングは、同じことを実現するためのほぼ同じ手法です。</span><span class="sxs-lookup"><span data-stu-id="6d672-136">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="6d672-137">`using` キーワードを使用すると、`Dispose` が呼び出されるタイミングをより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="6d672-137">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="6d672-138">`using` を使用すると、関数またはラムダ式の末尾で `Dispose` が呼び出されます。`use` キーワードを使用すると、含まれているコード ブロックの末尾で `Dispose` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6d672-138">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="6d672-139">一般に、`using` 関数ではなく、`use` を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6d672-139">In general, you should prefer to use `use` instead of the `using` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d672-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d672-140">See also</span></span>

- [<span data-ttu-id="6d672-141">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="6d672-141">F# Language Reference</span></span>](index.md)
