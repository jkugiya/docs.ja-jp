---
description: '詳細情報: メンバーのオーバーロード'
title: メンバーのオーバーロード
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: d3a545bfec552686e55c9f713d58784497946819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641955"
---
# <a name="member-overloading"></a><span data-ttu-id="5c1c9-103">メンバーのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="5c1c9-103">Member Overloading</span></span>

<span data-ttu-id="5c1c9-104">メンバーのオーバーロードとは、パラメーターの数または型は異なっているが名前は同じである同じ型の複数のメンバーを作成することです。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-104">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="5c1c9-105">たとえば、以下では、`WriteLine` メソッドがオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-105">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="5c1c9-106">パラメーターを使用できるのはメソッド、コンストラクター、およびインデックス付きプロパティだけなので、これらのメンバーのみをオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-106">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="5c1c9-107">オーバーロードは、再利用可能なライブラリの有用性、生産性、および可読性を向上させるための最も重要な手法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-107">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="5c1c9-108">パラメーターの数をオーバーロードすることで、より単純なバージョンのコンストラクターとメソッドを用意することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-108">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="5c1c9-109">パラメーターの型をオーバーロードすると、型が異なる選択セットに対して同じ操作を実行するメンバーで、同じメンバー名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-109">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="5c1c9-110">✔️ 説明的なパラメーター名を使用して、短いオーバーロードによって使用される既定の設定を指示するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-110">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="5c1c9-111">❌ オーバーロード内のパラメーター名を任意に変更することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-111">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="5c1c9-112">1 つのオーバーロード内のパラメーターが別のオーバーロード内のパラメーターと同じ入力を表している場合、パラメーターの名前は同じにしてください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-112">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="5c1c9-113">❌ オーバーロードされたメンバーのパラメーターの順序を一貫性のないものにすることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-113">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="5c1c9-114">同じ名前のパラメーターは、すべてのオーバーロード内で同じ位置に出現するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-114">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="5c1c9-115">✔️ 最も長いオーバーロードだけを仮想にしてください (拡張性が必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-115">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="5c1c9-116">短いオーバーロードは、長いオーバーロードを通して呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-116">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="5c1c9-117">❌ `ref` または `out` 修飾子を使用してメンバーをオーバーロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-117">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="5c1c9-118">一部の言語では、このようなオーバーロードに対する呼び出しを解決することができません。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-118">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="5c1c9-119">また、このようなオーバーロードのセマンティクスは、通常は完全に異なっているため、おそらくオーバーロードすべきではありません。代わりに 2 つの異なるメソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-119">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="5c1c9-120">❌ セマンティクスは異なるが、同じ位置に似たような型があるパラメーターを使用してオーバーロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-120">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="5c1c9-121">✔️ 省略可能な引数に対して `null` を渡すことを許可してください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-121">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="5c1c9-122">✔️ 既定の引数があるメンバーを定義する代わりに、メンバーのオーバーロードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-122">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="5c1c9-123">既定の引数は CLS 準拠ではありません。</span><span class="sxs-lookup"><span data-stu-id="5c1c9-123">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="5c1c9-124">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="5c1c9-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5c1c9-125">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="5c1c9-125">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5c1c9-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c1c9-126">See also</span></span>

- [<span data-ttu-id="5c1c9-127">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5c1c9-127">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="5c1c9-128">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5c1c9-128">Framework Design Guidelines</span></span>](index.md)
