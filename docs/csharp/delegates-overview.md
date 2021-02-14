---
title: デリゲートの概要
description: この概要の記事では、基本的な概念を紹介し、デリゲートの言語上の設計目標について説明します。
ms.date: 02/02/2021
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 72086301a6dd0552ab25baf732978802ad62669b
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548345"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="6cf2d-103">デリゲートの概要</span><span class="sxs-lookup"><span data-stu-id="6cf2d-103">Introduction to Delegates</span></span>

<span data-ttu-id="6cf2d-104">デリゲートは、.NET における "*遅延バインディング*" のメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-104">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="6cf2d-105">遅延バインディングとは、皆さんが作成するアルゴリズムについて、その一部を実装するメソッドを呼び出し元からも少なくとも 1 つ与えることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-105">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="6cf2d-106">たとえば天文学アプリケーションで、一連の星を並べ替えることを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-106">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="6cf2d-107">星の並べ替え基準には、地球からの距離や星の等級、知覚的な明るさを選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-107">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="6cf2d-108">いずれの場合も、Sort() メソッドが行うことは基本的に同じです。つまり何らかの比較に基づいて一連の項目を整列します。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-108">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="6cf2d-109">しかし、2 つの星を比較するコードは、並べ替えの基準によって異なります。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-109">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="6cf2d-110">ソフトウェアには、この種の手法が半世紀にわたって使用されてきました。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-110">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="6cf2d-111">C# 言語のデリゲートの概念は、きわめて優れた言語機能と、その概念を中心にしたタイプ セーフ機能を実現します。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-111">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="6cf2d-112">本シリーズの中で後述しているように、このようなアルゴリズム向けに記述された C# コードはタイプ セーフであり、引数や戻り値の型については、言語規則とコンパイラの機能を使用して型の一致が保証されます。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-112">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and uses the language rules and the compiler to ensure that the types match for arguments and return types.</span></span>

<span data-ttu-id="6cf2d-113">同様のシナリオで、呼び出し規則をより細かく制御する必要がある場合のために、[関数ポインター](~/_csharplang/proposals/csharp-9.0/function-pointers.md)が C# 9 に追加されました。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-113">[Function pointers](~/_csharplang/proposals/csharp-9.0/function-pointers.md) were added to C# 9 for similar scenarios, where you need more control over the calling convention.</span></span> <span data-ttu-id="6cf2d-114">デリゲートに関連付けられたコードは、デリゲート型に追加された仮想メソッドを使用して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-114">The code associated with a delegate is invoked using a virtual method added to a delegate type.</span></span> <span data-ttu-id="6cf2d-115">関数ポインターを使用して、さまざまな規則を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-115">Using function pointers, you can specify different conventions.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="6cf2d-116">デリゲートの言語上の設計目標</span><span class="sxs-lookup"><span data-stu-id="6cf2d-116">Language Design Goals for Delegates</span></span>

<span data-ttu-id="6cf2d-117">最終的にデリゲートとなる機能を実現するにあたって、言語の設計者たちはさまざまな目標を設定しました。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-117">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="6cf2d-118">設計チームが目指したのは、あらゆる遅延バインディング アルゴリズムに適用できる共通の言語概念です。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-118">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="6cf2d-119">デリゲートによって、開発者が 1 つの概念を身に付け、ソフトウェアに関するさまざまな課題にその知識を応用できるような言語の実現を目標に掲げたのです。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-119">Delegates enable developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="6cf2d-120">次に設計チームが目指したのは、シングルキャストとマルチキャストの両方のメソッド呼び出しをサポートすることでした。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-120">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="6cf2d-121">(マルチキャスト デリゲートは、複数のメソッド呼び出しを連結するデリゲートです。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-121">(Multicast delegates are delegates that chain together multiple method calls.</span></span>
<span data-ttu-id="6cf2d-122">[このシリーズの後の記事](delegate-class.md)で例を見ます。)</span><span class="sxs-lookup"><span data-stu-id="6cf2d-122">You'll see examples [later in this series](delegate-class.md).)</span></span>

<span data-ttu-id="6cf2d-123">設計チームは、C# のあらゆるコード要素に関して開発者たちが当然と考えるレベルのタイプ セーフティをデリゲートにおいても実現したいと考えていたのです。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-123">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span>

<span data-ttu-id="6cf2d-124">また、設計チームは、デリゲートを初めとする遅延バインディング アルゴリズムの利便性が大いに発揮される具体的なパターンは、イベント パターンであると認識していました。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-124">Finally, the team recognized an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="6cf2d-125">.NET のイベントの基本的なパターンをデリゲートのコードで確実に実現したいと考えていたのです。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-125">The team wanted to ensure the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="6cf2d-126">そうした目標に向けたすべての作業の成果として C# と .NET にサポートされたのが、デリゲートとイベントです。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-126">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="6cf2d-127">以降このセクションの記事では、言語の機能やライブラリのサポート、デリゲートを扱う際に用いられる一般的な用語について取り上げています。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-127">The remaining articles in this section will cover language features, library support, and common idioms used when you work with delegates.</span></span>

<span data-ttu-id="6cf2d-128">`delegate` キーワードとそれによって生成されるコード、</span><span class="sxs-lookup"><span data-stu-id="6cf2d-128">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="6cf2d-129">`System.Delegate` クラスの機能とその使い方、</span><span class="sxs-lookup"><span data-stu-id="6cf2d-129">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="6cf2d-130">タイプ セーフなデリゲートの作成方法、デリゲート経由で呼び出すことのできるメソッドの作成方法のほか、</span><span class="sxs-lookup"><span data-stu-id="6cf2d-130">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="6cf2d-131">ラムダ式を使ったデリゲートやイベントの扱い方、</span><span class="sxs-lookup"><span data-stu-id="6cf2d-131">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="6cf2d-132">LINQ の構成要素としてデリゲートがどこで使われているか、</span><span class="sxs-lookup"><span data-stu-id="6cf2d-132">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="6cf2d-133">.NET のイベント パターンの基礎としてデリゲートがどのように使われ、両者がどのように違うのかについても説明します。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-133">You'll learn how delegates are the basis for the .NET event pattern, and how they're different.</span></span>

<span data-ttu-id="6cf2d-134">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="6cf2d-134">Let's get started.</span></span>

[<span data-ttu-id="6cf2d-135">次へ</span><span class="sxs-lookup"><span data-stu-id="6cf2d-135">Next</span></span>](delegate-class.md)
