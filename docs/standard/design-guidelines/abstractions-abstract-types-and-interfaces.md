---
description: '詳細情報: 抽象化 (抽象型およびインターフェイス)'
title: 抽象化 (抽象型およびインターフェイス)
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: 8dc82f004d655429e842c63fab4defff0fd74ab2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642442"
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="62390-103">抽象化 (抽象型およびインターフェイス)</span><span class="sxs-lookup"><span data-stu-id="62390-103">Abstractions (Abstract Types and Interfaces)</span></span>

<span data-ttu-id="62390-104">抽象化はコントラクトを記述する型ですが、コントラクトの完全な実装は提供しません。</span><span class="sxs-lookup"><span data-stu-id="62390-104">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="62390-105">抽象化は通常、抽象クラスまたは抽象インターフェイスとして実装され、付属する適切に定義された一連の参照ドキュメントで、コントラクトを実装する型の必要なセマンティクスが説明されています。</span><span class="sxs-lookup"><span data-stu-id="62390-105">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="62390-106">.NET Framework の最も重要な抽象化は、<xref:System.IO.Stream>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Object> などです。</span><span class="sxs-lookup"><span data-stu-id="62390-106">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>

 <span data-ttu-id="62390-107">抽象化のコントラクトをサポートする具象型を実装し、抽象化を使用する (操作する) フレームワーク API でこの具象型を使用することにより、フレームワークを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="62390-107">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>

 <span data-ttu-id="62390-108">時が経っても変わらずに意味があり有用な抽象化を設計することは、非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="62390-108">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="62390-109">最も難しいのは、多すぎも少なすぎもしない適切なメンバーのセットを作成することです。</span><span class="sxs-lookup"><span data-stu-id="62390-109">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="62390-110">抽象化のメンバーが多すぎると、実装が困難になるか、不可能になることさえあります。</span><span class="sxs-lookup"><span data-stu-id="62390-110">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="62390-111">約束された機能に対してメンバーが少なすぎると、多くの興味深いシナリオで役に立たなくなります。</span><span class="sxs-lookup"><span data-stu-id="62390-111">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>

 <span data-ttu-id="62390-112">フレームワークの抽象化が多すぎても、フレームワークの使いやすさに悪影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="62390-112">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="62390-113">多くの場合、抽象化が基になっている具象実装と API の全体像に抽象化がどのように当てはまるのかを理解しないで抽象化を理解することは、非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="62390-113">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="62390-114">また、抽象化とそのメンバーの名前はどうしても抽象的になるので、それらが使用される広範なコンテキストを最初に理解してからでないと、わかりにくく使いづらいことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="62390-114">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>

 <span data-ttu-id="62390-115">ただし、抽象化によって提供される非常に強力な拡張性は、多くの場合、他の拡張メカニズムでは実現できません。</span><span class="sxs-lookup"><span data-stu-id="62390-115">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="62390-116">それらは、プラグイン、制御の反転 (IoC)、パイプラインなど、多くのアーキテクチャ パターンの中核になるものです。</span><span class="sxs-lookup"><span data-stu-id="62390-116">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="62390-117">また、それらはフレームワークのテストの容易性にとっても極めて重要です。</span><span class="sxs-lookup"><span data-stu-id="62390-117">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="62390-118">適切に抽象化されていると、単体テストのために多くの依存関係をスタブ化できます。</span><span class="sxs-lookup"><span data-stu-id="62390-118">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="62390-119">まとめると、抽象化は、最新のオブジェクト指向フレームワークで求められる豊富な機能の鍵を握るものです。</span><span class="sxs-lookup"><span data-stu-id="62390-119">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>

 <span data-ttu-id="62390-120">❌ 抽象化を使用するいくつかの具象実装と API を開発することによってテストしてからでない限り、抽象化を提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="62390-120">❌ DO NOT provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>

 <span data-ttu-id="62390-121">✔️ 抽象化を設計するときは、抽象クラスにするかインターフェイスにするかを慎重に選択します。</span><span class="sxs-lookup"><span data-stu-id="62390-121">✔️ DO choose carefully between an abstract class and an interface when designing an abstraction.</span></span>

 <span data-ttu-id="62390-122">✔️ 抽象化の具象実装のために参照テストを提供することを検討します。</span><span class="sxs-lookup"><span data-stu-id="62390-122">✔️ CONSIDER providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="62390-123">そのようなテストがあると、ユーザーは実装でコントラクトが正しく実装されているかどうかをテストできます。</span><span class="sxs-lookup"><span data-stu-id="62390-123">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>

 <span data-ttu-id="62390-124">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="62390-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="62390-125">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="62390-125">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="62390-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="62390-126">See also</span></span>

- [<span data-ttu-id="62390-127">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="62390-127">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="62390-128">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="62390-128">Designing for Extensibility</span></span>](designing-for-extensibility.md)
