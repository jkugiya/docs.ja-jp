---
description: '詳細情報: インターフェイスのデザイン'
title: インターフェイスのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 387f921f8bdbe6c6d398aa31dcc8a22c7da455f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641981"
---
# <a name="interface-design"></a><span data-ttu-id="16733-103">インターフェイスのデザイン</span><span class="sxs-lookup"><span data-stu-id="16733-103">Interface Design</span></span>

<span data-ttu-id="16733-104">ほとんどの API はクラスと構造体を使用して最良のモデル化が行われますが、インターフェイスのほうが適している場合や、インターフェイスが唯一のオプションである場合があります。</span><span class="sxs-lookup"><span data-stu-id="16733-104">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="16733-105">CLR では複数の継承はサポートされていません (つまり、複数の基底クラスから CLR クラスを継承することはできません) が、１ つの基底クラスからの継承に加えて、型で 1 つまたは複数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="16733-105">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="16733-106">したがって、多くの場合、インターフェイスは、多重継承の効果を実現するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="16733-106">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="16733-107">たとえば、<xref:System.IDisposable> は、参加する必要のある他の継承階層とは無関係に、型で廃棄性をサポートできるようにするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="16733-107">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="16733-108">インターフェイスを定義することが適している他の状況としては、いくつかの値型を含む複数の型によってサポートされることが可能な共通インターフェイスを作成することがあります。</span><span class="sxs-lookup"><span data-stu-id="16733-108">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="16733-109">値型は <xref:System.ValueType> 以外の型から継承することはできませんが、インターフェイスを実装することはできるため、インターフェイスを使用することが共通の基本データ型を提供するための唯一のオプションになります。</span><span class="sxs-lookup"><span data-stu-id="16733-109">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="16733-110">✔️ 値型を含む型セットによってサポートされる何らかの共通 API が必要な場合は、インターフェイスを定義してください。</span><span class="sxs-lookup"><span data-stu-id="16733-110">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="16733-111">✔️ 他の型から既に継承されている型に対してインターフェイスの機能をサポートする必要がある場合は、インターフェイスを定義することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="16733-111">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="16733-112">❌ マーカー インターフェイス (メンバーのないインターフェイス) を使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="16733-112">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="16733-113">クラスを特定の特性 (マーカー) を持っているとマークする必要がある場合は、通常は、インターフェイスではなくカスタム属性を使用してください。</span><span class="sxs-lookup"><span data-stu-id="16733-113">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="16733-114">✔️ インターフェイスの実装である型を少なくとも 1 つ用意してください。</span><span class="sxs-lookup"><span data-stu-id="16733-114">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="16733-115">これを行うと、インターフェイスの設計を検証するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="16733-115">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="16733-116">たとえば、<xref:System.Collections.Generic.List%601> は <xref:System.Collections.Generic.IList%601> インターフェイスの実装です。</span><span class="sxs-lookup"><span data-stu-id="16733-116">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="16733-117">✔️ 定義した各インターフェイスを使用する API (インターフェイスをパラメーターとして使用するメソッドまたはインターフェイスと型指定されたプロパティ) を少なくとも 1 つ用意してください。</span><span class="sxs-lookup"><span data-stu-id="16733-117">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="16733-118">これを行うと、インターフェイスの設計を検証するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="16733-118">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="16733-119">たとえば、<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> では <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> インターフェイスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="16733-119">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="16733-120">❌ 以前に出荷されているインターフェイスにメンバーを追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="16733-120">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="16733-121">これを行うと、インターフェイスの実装が中断されます。</span><span class="sxs-lookup"><span data-stu-id="16733-121">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="16733-122">バージョンの問題を回避するために、新しいインターフェイスを作成してください。</span><span class="sxs-lookup"><span data-stu-id="16733-122">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="16733-123">これらのガイドラインで説明されている状況を除き、一般に、マネージド コードの再利用可能なライブラリの設計では、インターフェイスではなくクラスを選択してください。</span><span class="sxs-lookup"><span data-stu-id="16733-123">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="16733-124">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="16733-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="16733-125">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="16733-125">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="16733-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="16733-126">See also</span></span>

- [<span data-ttu-id="16733-127">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="16733-127">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="16733-128">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="16733-128">Framework Design Guidelines</span></span>](index.md)
