---
description: '詳細情報: シール'
title: シール
ms.date: 10/22/2008
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: 94673f793aa7373e1076e13cbda900fba83786f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731722"
---
# <a name="sealing"></a><span data-ttu-id="90363-103">シール</span><span class="sxs-lookup"><span data-stu-id="90363-103">Sealing</span></span>

<span data-ttu-id="90363-104">オブジェクト指向フレームワークの機能の 1 つは、フレームワーク デザイナーが予期しないような方法で、開発者がそれを拡張およびカスタマイズできることです。</span><span class="sxs-lookup"><span data-stu-id="90363-104">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="90363-105">これは、拡張可能な設計の威力であると同時に危険性でもあります。</span><span class="sxs-lookup"><span data-stu-id="90363-105">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="90363-106">したがって、フレームワークを設計するときは、拡張性が望ましいときはそれを慎重に設計し、危険なときは拡張性を制限することが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="90363-106">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="90363-107">拡張性を防ぐための強力なメカニズムがシールです。</span><span class="sxs-lookup"><span data-stu-id="90363-107">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="90363-108">クラスまたは個々のメンバーをシールできます。</span><span class="sxs-lookup"><span data-stu-id="90363-108">You can seal either the class or individual members.</span></span> <span data-ttu-id="90363-109">クラスをシールすると、ユーザーはそのクラスから継承できなくなります。</span><span class="sxs-lookup"><span data-stu-id="90363-109">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="90363-110">メンバーをシールすると、ユーザーは特定のメンバーをオーバーライドできなくなります。</span><span class="sxs-lookup"><span data-stu-id="90363-110">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="90363-111">❌ それを行う十分な理由なしに、クラスをシールしないでください。</span><span class="sxs-lookup"><span data-stu-id="90363-111">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="90363-112">拡張シナリオを思い付かないためにクラスをシールすることは、適切な理由ではありません。</span><span class="sxs-lookup"><span data-stu-id="90363-112">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="90363-113">フレームワークのユーザーは、便利なメンバーの追加のような、よくわからないさまざまな理由でクラスを継承することを好みます。</span><span class="sxs-lookup"><span data-stu-id="90363-113">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="90363-114">ユーザーが型を継承しようとする明白でない理由の例については、「[シールされていないクラス](unsealed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90363-114">See [Unsealed Classes](unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="90363-115">クラスをシールする適切な理由としては、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="90363-115">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="90363-116">クラスが静的クラスである。</span><span class="sxs-lookup"><span data-stu-id="90363-116">The class is a static class.</span></span> <span data-ttu-id="90363-117">「[静的クラスのデザイン](static-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90363-117">See [Static Class Design](static-class.md).</span></span>

- <span data-ttu-id="90363-118">クラスの継承されたプロテクト メンバーに、セキュリティ上の注意が必要なシークレットが格納される。</span><span class="sxs-lookup"><span data-stu-id="90363-118">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="90363-119">クラスで多くの仮想メンバーが継承されており、それらを個別にシールするコストが、クラスをアンシールドのままにする利点よりも大きい。</span><span class="sxs-lookup"><span data-stu-id="90363-119">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="90363-120">クラスが、非常に高速のランタイム参照を必要とする属性である。</span><span class="sxs-lookup"><span data-stu-id="90363-120">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="90363-121">シールド属性の方が、アンシールドのものより、パフォーマンス レベルが若干高くなります。</span><span class="sxs-lookup"><span data-stu-id="90363-121">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="90363-122">「[属性](attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90363-122">See [Attributes](attributes.md).</span></span>

 <span data-ttu-id="90363-123">❌ シールド型では、プロテクト メンバーまたは仮想メンバーを宣言しないでください。</span><span class="sxs-lookup"><span data-stu-id="90363-123">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="90363-124">定義により、シールド型から継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="90363-124">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="90363-125">つまり、シールド型のプロテクト メンバーを呼び出すことはできず、シールド型の仮想メソッドをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="90363-125">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="90363-126">✔️ オーバーライドするメンバーをシールすることを検討します。</span><span class="sxs-lookup"><span data-stu-id="90363-126">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="90363-127">仮想メンバーの導入によって発生する可能性のある問題 (「[仮想メンバー](virtual-members.md)」で説明されています) は、程度は若干低くなりますが、オーバーライドにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="90363-127">Problems that can result from introducing virtual members (discussed in [Virtual Members](virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="90363-128">オーバーライドをシールすると、継承階層内のそのポイント以降について、これらの問題を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="90363-128">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="90363-129">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="90363-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="90363-130">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="90363-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="90363-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="90363-131">See also</span></span>

- [<span data-ttu-id="90363-132">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="90363-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="90363-133">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="90363-133">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="90363-134">シールされていないクラス</span><span class="sxs-lookup"><span data-stu-id="90363-134">Unsealed Classes</span></span>](unsealed-classes.md)
