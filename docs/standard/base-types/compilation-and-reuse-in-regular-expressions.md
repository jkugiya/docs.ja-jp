---
title: 正規表現におけるコンパイルと再利用
description: 正規表現におけるコンパイルと再利用について説明します。
ms.topic: conceptual
ms.date: 03/30/2017
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET regular expressions, engines
- .NET regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
ms.openlocfilehash: c834817856d799c5621359a28b8a4c54ea6000d4
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693060"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a><span data-ttu-id="77fd7-103">正規表現におけるコンパイルと再利用</span><span class="sxs-lookup"><span data-stu-id="77fd7-103">Compilation and Reuse in Regular Expressions</span></span>

<span data-ttu-id="77fd7-104">正規表現エンジンが式をどのようにコンパイルするか、および正規表現がどのようにキャッシュされるかを理解することで、正規表現を幅広く使用するアプリケーションのパフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-104">You can optimize the performance of applications that make extensive use of regular expressions by understanding how the regular expression engine compiles expressions and by understanding how regular expressions are cached.</span></span> <span data-ttu-id="77fd7-105">このトピックでは、コンパイルとキャッシュの両方について説明します。</span><span class="sxs-lookup"><span data-stu-id="77fd7-105">This topic discusses both compilation and caching.</span></span>  
  
## <a name="compiled-regular-expressions"></a><span data-ttu-id="77fd7-106">コンパイルされた正規表現</span><span class="sxs-lookup"><span data-stu-id="77fd7-106">Compiled Regular Expressions</span></span>  

 <span data-ttu-id="77fd7-107">既定では、正規表現エンジンは、内部命令のシーケンス (Microsoft 中間言語 (MSIL) とは異なる高度なコード) に正規表現をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="77fd7-107">By default, the regular expression engine compiles a regular expression to a sequence of internal instructions (these are high-level codes that are different from Microsoft intermediate language, or MSIL).</span></span> <span data-ttu-id="77fd7-108">エンジンは、正規表現を実行するときに内部コードを解釈します。</span><span class="sxs-lookup"><span data-stu-id="77fd7-108">When the engine executes a regular expression, it interprets the internal codes.</span></span>  
  
 <span data-ttu-id="77fd7-109"><xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> オプションを使用して <xref:System.Text.RegularExpressions.Regex> オブジェクトを構築した場合、このオブジェクトは、高度な正規表現の内部命令ではなく明示的な MSIL コードに正規表現をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="77fd7-109">If a <xref:System.Text.RegularExpressions.Regex> object is constructed with the <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option, it compiles the regular expression to explicit MSIL code instead of high-level regular expression internal instructions.</span></span> <span data-ttu-id="77fd7-110">これにより、.NET の Just-In-Time (JIT) コンパイラは、式をネイティブのマシン コードに変換してパフォーマンスを高めることができます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-110">This allows .NET's just-in-time (JIT) compiler to convert the expression to native machine code for higher performance.</span></span>  <span data-ttu-id="77fd7-111"><xref:System.Text.RegularExpressions.Regex> オブジェクトの作成にかかるコストは高くなる場合がありますが、それとの照合の実行にかかるコストは大幅に小さくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="77fd7-111">The cost of constructing the <xref:System.Text.RegularExpressions.Regex> object may be higher, but the cost of performing matches with it is likely to be much smaller.</span></span>

 <span data-ttu-id="77fd7-112">事前にコンパイルされた正規表現を使用するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="77fd7-112">An alternative is to use precompiled regular expressions.</span></span> <span data-ttu-id="77fd7-113"><xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> メソッドを利用し、すべての式をコンパイルして再利用可能な DLL を作成できます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-113">You can compile all of your expressions into a reusable DLL by using the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> method.</span></span> <span data-ttu-id="77fd7-114">これにより、コンパイルされた高速な正規表現を利用しながら、実行時にコンパイルする必要性を回避できます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-114">This avoids the need to compile at run time while still benefiting from the speed of compiled regular expressions.</span></span>  
  
## <a name="the-regular-expressions-cache"></a><span data-ttu-id="77fd7-115">正規表現のキャッシュ</span><span class="sxs-lookup"><span data-stu-id="77fd7-115">The Regular Expressions Cache</span></span>  

 <span data-ttu-id="77fd7-116">パフォーマンスを高めるために、正規表現エンジンは、コンパイルされた正規表現のアプリケーション全体のキャッシュを保持します。</span><span class="sxs-lookup"><span data-stu-id="77fd7-116">To improve performance, the regular expression engine maintains an application-wide cache of compiled regular expressions.</span></span> <span data-ttu-id="77fd7-117">キャッシュは、静的メソッド呼び出しでのみ使用される正規表現パターンを格納します</span><span class="sxs-lookup"><span data-stu-id="77fd7-117">The cache stores regular expression patterns that are used only in static method calls.</span></span> <span data-ttu-id="77fd7-118">(インスタンス メソッドに渡される正規表現パターンはキャッシュされません)。これにより、式を使用するたびに高度なバイト コードに再解析する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="77fd7-118">(Regular expression patterns supplied to instance methods are not cached.) This avoids the need to reparse an expression into high-level byte code each time it is used.</span></span>  
  
 <span data-ttu-id="77fd7-119">キャッシュされる正規表現の最大数は、`static` (Visual Basic では `Shared`) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> プロパティの値によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-119">The maximum number of cached regular expressions is determined by the value of the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="77fd7-120">既定では、正規表現エンジンは最大 15 個のコンパイルされた正規表現をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="77fd7-120">By default, the regular expression engine caches up to 15 compiled regular expressions.</span></span> <span data-ttu-id="77fd7-121">コンパイルされた正規表現の数がキャッシュ サイズを超えた場合は、最近の使用頻度が最も低い正規表現が破棄され、新しい正規表現がキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-121">If the number of compiled regular expressions exceeds the cache size, the least recently used regular expression is discarded and the new regular expression is cached.</span></span>  
  
 <span data-ttu-id="77fd7-122">アプリケーションでは、次の 2 つの方法のいずれかで正規表現を再利用できます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-122">Your application can reuse regular expressions in one of the following two ways:</span></span>  
  
- <span data-ttu-id="77fd7-123"><xref:System.Text.RegularExpressions.Regex> オブジェクトの静的メソッドを使用して、正規表現を定義する。</span><span class="sxs-lookup"><span data-stu-id="77fd7-123">By using a static method of the <xref:System.Text.RegularExpressions.Regex> object to define the regular expression.</span></span> <span data-ttu-id="77fd7-124">別の静的メソッド呼び出しで既に定義されている正規表現パターンを使用している場合、正規表現エンジンではキャッシュからのその取得が試みられます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-124">If you're using a regular expression pattern that has already been defined by another static method call, the regular expression engine will try to retrieve it from the cache.</span></span> <span data-ttu-id="77fd7-125">キャッシュに使用できるものがない場合、エンジンによって正規表現がコンパイルされてキャッシュに追加されます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-125">If it's not available in the cache, the engine will compile the regular expression and add it to the cache.</span></span>
  
- <span data-ttu-id="77fd7-126">既存の <xref:System.Text.RegularExpressions.Regex> オブジェクトの正規表現パターンが必要な間、このオブジェクトを再利用する。</span><span class="sxs-lookup"><span data-stu-id="77fd7-126">By reusing an existing <xref:System.Text.RegularExpressions.Regex> object as long as its regular expression pattern is needed.</span></span>  
  
 <span data-ttu-id="77fd7-127">オブジェクトのインスタンス化および正規表現のコンパイルのオーバーヘッドが原因となり、さまざまな <xref:System.Text.RegularExpressions.Regex> オブジェクトを作成してすぐに破棄するプロセスは非常にコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="77fd7-127">Because of the overhead of object instantiation and regular expression compilation, creating and rapidly destroying numerous <xref:System.Text.RegularExpressions.Regex> objects is a very expensive process.</span></span> <span data-ttu-id="77fd7-128">多数の異なる正規表現を使用するアプリケーションの場合は、静的 `Regex` メソッドの呼び出しを使用することで、および場合によっては正規表現キャッシュのサイズを大きくすることで、パフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="77fd7-128">For applications that use a large number of different regular expressions, you can optimize performance by using calls to static `Regex` methods and possibly by increasing the size of the regular expression cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fd7-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="77fd7-129">See also</span></span>

- [<span data-ttu-id="77fd7-130">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="77fd7-130">.NET Regular Expressions</span></span>](regular-expressions.md)
