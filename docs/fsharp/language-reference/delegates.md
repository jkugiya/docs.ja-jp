---
title: デリゲート
description: F# のデリゲートを操作する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630372"
---
# <a name="delegates"></a><span data-ttu-id="069cc-103">代理人</span><span class="sxs-lookup"><span data-stu-id="069cc-103">Delegates</span></span>

<span data-ttu-id="069cc-104">デリゲートによって、関数呼び出しはオブジェクトとして表されます。</span><span class="sxs-lookup"><span data-stu-id="069cc-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="069cc-105">通常、F# では、関数をファーストクラスの値として表すために関数の値を使用する必要があります。ただし、デリゲートは .NET Framework で使用され、それを予期する API と相互運用するときに必要になります。</span><span class="sxs-lookup"><span data-stu-id="069cc-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="069cc-106">また、他の .NET Framework 言語から使用するように設計されたライブラリを作成するときにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="069cc-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="069cc-107">構文</span><span class="sxs-lookup"><span data-stu-id="069cc-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="069cc-108">解説</span><span class="sxs-lookup"><span data-stu-id="069cc-108">Remarks</span></span>

<span data-ttu-id="069cc-109">前の構文では、`type1` は引数の型を表し、`type2` は戻り値の型を表します。</span><span class="sxs-lookup"><span data-stu-id="069cc-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="069cc-110">`type1` によって表される引数の型は、自動的にカリー化されます。</span><span class="sxs-lookup"><span data-stu-id="069cc-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="069cc-111">これが示唆するのは、この型では、対象の関数の引数がカリー化されている場合はタプル形式を使用し、既にタプル形式の引数にはかっこで囲まれたタプルを使用するということです。</span><span class="sxs-lookup"><span data-stu-id="069cc-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="069cc-112">自動カリー化により、一連のかっこが削除され、対象のメソッドに一致するタプル引数が残されます。</span><span class="sxs-lookup"><span data-stu-id="069cc-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="069cc-113">各ケースで使用する構文については、コード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="069cc-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="069cc-114">デリゲートは、F# 関数の値、および静的またはインスタンス メソッドにアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="069cc-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="069cc-115">F# 関数の値は、引数としてデリゲート コンストラクターに直接渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="069cc-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="069cc-116">静的メソッドの場合は、クラスの名前とメソッドを使用してデリゲートを構築します。</span><span class="sxs-lookup"><span data-stu-id="069cc-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="069cc-117">インスタンス メソッドの場合は、1 つの引数にオブジェクト インスタンスとメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="069cc-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="069cc-118">どちらの場合も、メンバー アクセス演算子 (`.`) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="069cc-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="069cc-119">デリゲート型の `Invoke` メソッドは、カプセル化された関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="069cc-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="069cc-120">また、デリゲートは、かっこを使用しないで Invoke メソッド名を参照することにより、関数の値として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="069cc-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="069cc-121">次のコードは、クラス内のさまざまなメソッドを表すデリゲートを作成するための構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="069cc-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="069cc-122">メソッドが静的メソッドまたはインスタンス メソッドのどちらであるか、また引数がタプル形式とカリー化された形式のどちらであるかによって、デリゲートの宣言と割り当ての構文は少し異なります。</span><span class="sxs-lookup"><span data-stu-id="069cc-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="069cc-123">次のコードは、デリゲートを操作するためのさまざまな方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="069cc-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="069cc-124">前のコード例の出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="069cc-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="069cc-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="069cc-125">See also</span></span>

- [<span data-ttu-id="069cc-126">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="069cc-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="069cc-127">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="069cc-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="069cc-128">イベント</span><span class="sxs-lookup"><span data-stu-id="069cc-128">Events</span></span>](./members/events.md)
