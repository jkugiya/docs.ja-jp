---
description: partial メソッド - C# リファレンス
title: partial メソッド - C# リファレンス
ms.date: 03/23/2021
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 240ad6f2f5792e4db9b032e36991f3c398f1d2f9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111011"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="bf309-103">partial メソッド (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="bf309-103">partial method (C# Reference)</span></span>

<span data-ttu-id="bf309-104">部分メソッドには、部分型の一部に定義されたシグネチャ、および部分型の別の部分に定義された実装があります。</span><span class="sxs-lookup"><span data-stu-id="bf309-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="bf309-105">部分メソッドを使用すると、イベント ハンドラーと同じように、開発者が実装するかどうかを決定できるメソッド フックをクラス デザイナーで提供できます。</span><span class="sxs-lookup"><span data-stu-id="bf309-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="bf309-106">開発者が実装を指定しない場合、コンパイラはコンパイル時にシグネチャを削除します。</span><span class="sxs-lookup"><span data-stu-id="bf309-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="bf309-107">部分メソッドには次の条件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="bf309-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="bf309-108">宣言は、コンテキスト キーワード [partial](../../language-reference/keywords/partial-type.md) で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf309-108">Declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md).</span></span>

- <span data-ttu-id="bf309-109">部分型の両方の部分のシグネチャが一致する必要がある。</span><span class="sxs-lookup"><span data-stu-id="bf309-109">Signatures in both parts of the partial type must match.</span></span>

<span data-ttu-id="bf309-110">次の場合には、部分メソッドを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bf309-110">A partial method isn't required to have an implementation in the following cases:</span></span>

- <span data-ttu-id="bf309-111">アクセシビリティ修飾子 (既定の [private](../../language-reference/keywords/private.md) を含む) はありません。</span><span class="sxs-lookup"><span data-stu-id="bf309-111">It doesn't have any accessibility modifiers (including the default [private](../../language-reference/keywords/private.md)).</span></span>

- <span data-ttu-id="bf309-112">[void](../../language-reference/builtin-types/void.md) を返します。</span><span class="sxs-lookup"><span data-stu-id="bf309-112">It returns [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="bf309-113">[out](../../language-reference/keywords/out-parameter-modifier.md) パラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="bf309-113">It doesn't have any [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="bf309-114">[virtual](../../language-reference/keywords/virtual.md)、[override](../../language-reference/keywords/override.md)、[sealed](../../language-reference/keywords/sealed.md)、[new](../../language-reference/keywords/new-modifier.md)、[extern](../../language-reference/keywords/extern.md) のいずれの修飾子もありません。</span><span class="sxs-lookup"><span data-stu-id="bf309-114">It doesn't have any of the following modifiers [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), [sealed](../../language-reference/keywords/sealed.md), [new](../../language-reference/keywords/new-modifier.md), or [extern](../../language-reference/keywords/extern.md).</span></span>

<span data-ttu-id="bf309-115">これらのすべての制限に準拠していないメソッド (`public virtual partial void` メソッドなど) は、実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf309-115">Any method that doesn't conform to all those restrictions (for example, `public virtual partial void` method), must provide an implementation.</span></span>

<span data-ttu-id="bf309-116">部分クラスの 2 つの部分に定義された部分メソッドを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="bf309-116">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="bf309-117">部分メソッドは、ソース ジェネレーターと組み合わせて使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bf309-117">Partial methods can also be useful in combination with source generators.</span></span> <span data-ttu-id="bf309-118">たとえば、regex は、次のパターンを使用して定義できます。</span><span class="sxs-lookup"><span data-stu-id="bf309-118">For example a regex could be defined using the following pattern:</span></span>

```csharp
[RegexGenerated("(dog|cat|fish)")]
partial bool IsPetMatch(string input);
```

<span data-ttu-id="bf309-119">詳細については、「[部分クラスと部分メソッド](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf309-119">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf309-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf309-120">See also</span></span>

- [<span data-ttu-id="bf309-121">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="bf309-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bf309-122">partial 型</span><span class="sxs-lookup"><span data-stu-id="bf309-122">partial type</span></span>](partial-type.md)
