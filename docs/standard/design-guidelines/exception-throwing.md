---
description: '詳細情報: 例外のスロー'
title: 例外のスロー
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: b1cf7a4eecc32a9f76ea06c47dd6c16d3afe5470
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642137"
---
# <a name="exception-throwing"></a><span data-ttu-id="1fe66-103">例外のスロー</span><span class="sxs-lookup"><span data-stu-id="1fe66-103">Exception Throwing</span></span>

<span data-ttu-id="1fe66-104">このセクションで説明する例外のスローに関するガイドラインでは、実行失敗の意味を適切に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fe66-104">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="1fe66-105">実行失敗は、メンバーが実行するように設計されていたこと (メンバー名が示すもの) を実行できない場合に常に発生します。</span><span class="sxs-lookup"><span data-stu-id="1fe66-105">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="1fe66-106">たとえば、`OpenFile` メソッドが開かれたファイルのハンドルを呼び出し元に返すことができない場合、実行失敗と見なされます。</span><span class="sxs-lookup"><span data-stu-id="1fe66-106">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="1fe66-107">ほとんどの開発者は、0 による除算や null 参照などの使用エラーに対し、例外を使用することに慣れています。</span><span class="sxs-lookup"><span data-stu-id="1fe66-107">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="1fe66-108">フレームワークでは、実行エラーを含むすべてのエラー状態に対して例外が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fe66-108">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="1fe66-109">❌ エラー コードを返さないでください。</span><span class="sxs-lookup"><span data-stu-id="1fe66-109">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="1fe66-110">例外は、フレームワークでエラーを報告するための主な手段です。</span><span class="sxs-lookup"><span data-stu-id="1fe66-110">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="1fe66-111">✔️ 例外をスローすることにより、実行失敗を報告します。</span><span class="sxs-lookup"><span data-stu-id="1fe66-111">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="1fe66-112">✔️ 実行を続けると安全ではない状況がコードで発生した場合は、例外をスローするのではなく、`System.Environment.FailFast` (.NET Framework 2.0 の機能) を呼び出してプロセスを終了することを検討します。</span><span class="sxs-lookup"><span data-stu-id="1fe66-112">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="1fe66-113">❌ 可能であれば、通常の制御フローには例外を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1fe66-113">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="1fe66-114">システム障害や競合状態の可能性がある操作の場合を除き、フレームワーク デザイナーは、ユーザーが例外をスローしないコードを記述できるように、API を設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fe66-114">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="1fe66-115">たとえば、例外をスローしないコードをユーザーが記述できるように、メンバーを呼び出す前に事前条件をチェックする手段を提供できます。</span><span class="sxs-lookup"><span data-stu-id="1fe66-115">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="1fe66-116">通常、別のメンバーの事前条件をチェックするために使用されるメンバーはテスターと呼ばれ、実際に作業を行うメンバーはドゥーアーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1fe66-116">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="1fe66-117">Tester-Doer パターンを使用すると許容できないパフォーマンスのオーバーヘッドが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1fe66-117">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="1fe66-118">そのような場合は、いわゆる Try-Parse パターンを検討する必要があります (詳細については、「[例外とパフォーマンス](exceptions-and-performance.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="1fe66-118">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="1fe66-119">✔️ 例外をスローした場合のパフォーマンスへの影響を考慮します。</span><span class="sxs-lookup"><span data-stu-id="1fe66-119">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="1fe66-120">1 秒間に 100 回を超える割合でスローすると、ほとんどのアプリケーションでパフォーマンスが著しく低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1fe66-120">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="1fe66-121">✔️ パブリックに呼び出し可能なメンバーによって、(システム障害ではなく) メンバー コントラクトの違反のためにスローされるすべての例外をドキュメントに記載し、それらをコントラクトの一部として処理します。</span><span class="sxs-lookup"><span data-stu-id="1fe66-121">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="1fe66-122">コントラクトの一部である例外は、バージョン間で変更することはできません (つまり、例外の種類を変更してはならず、新しい例外を追加してはなりません)。</span><span class="sxs-lookup"><span data-stu-id="1fe66-122">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="1fe66-123">❌ 何らかのオプションに基づいてスローが可能または不可能なパブリック メンバーを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1fe66-123">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="1fe66-124">❌ 戻り値または `out` パラメーターとして例外を返すパブリック メンバーを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1fe66-124">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="1fe66-125">パブリック API から例外をスローするのではなく返すと、例外ベースのエラー報告の利点の多くが損なわれます。</span><span class="sxs-lookup"><span data-stu-id="1fe66-125">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="1fe66-126">✔️ 例外ビルダーメ ソッドを使用することを検討します。</span><span class="sxs-lookup"><span data-stu-id="1fe66-126">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="1fe66-127">同じ例外を異なる場所からスローすることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="1fe66-127">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="1fe66-128">コードの肥大化を回避するため、例外を作成してプロパティを初期化するヘルパー メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1fe66-128">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="1fe66-129">また、例外をスローするメンバーはインライン展開されません。</span><span class="sxs-lookup"><span data-stu-id="1fe66-129">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="1fe66-130">throw ステートメントをビルダー内で移動すると、そのメンバーがインライン化される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1fe66-130">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="1fe66-131">❌ 例外フィルター ブロックから例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="1fe66-131">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="1fe66-132">例外フィルターで例外が発生すると、CLR によって例外がキャッチされ、フィルターからは false が返されます。</span><span class="sxs-lookup"><span data-stu-id="1fe66-132">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="1fe66-133">この動作は、実行して明示的に false を返すフィルターと区別できないため、デバッグが非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="1fe66-133">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="1fe66-134">❌ finally ブロックから明示的に例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="1fe66-134">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="1fe66-135">スローするメソッドの呼び出しによって発生する暗黙的にスローされる例外は、許容されます。</span><span class="sxs-lookup"><span data-stu-id="1fe66-135">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="1fe66-136">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="1fe66-136">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1fe66-137">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="1fe66-137">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1fe66-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fe66-138">See also</span></span>

- [<span data-ttu-id="1fe66-139">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1fe66-139">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="1fe66-140">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1fe66-140">Design Guidelines for Exceptions</span></span>](exceptions.md)
