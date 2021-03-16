---
description: '詳細情報: 等値演算子'
title: 等値演算子
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 8678ed1b4bc320f685cf7ae172f064b3dededd04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642241"
---
# <a name="equality-operators"></a><span data-ttu-id="9ac43-103">等値演算子</span><span class="sxs-lookup"><span data-stu-id="9ac43-103">Equality Operators</span></span>

<span data-ttu-id="9ac43-104">このセクションでは、等値演算子のオーバーロードについて説明し、`operator==` と `operator!=` を等値演算子と呼びます。</span><span class="sxs-lookup"><span data-stu-id="9ac43-104">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="9ac43-105">❌ 等値演算子のどちらか一方だけをオーバーロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="9ac43-105">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="9ac43-106">✔️ <xref:System.Object.Equals%2A?displayProperty=nameWithType> と等値演算子が、まったく同じセマンティクスを持ち、同じようなパフォーマンス特性を備えるようにします。</span><span class="sxs-lookup"><span data-stu-id="9ac43-106">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="9ac43-107">これは、多くの場合、等値演算子をオーバーロードするときは、`Object.Equals` をオーバーライドする必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9ac43-107">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="9ac43-108">❌ 等値演算子からは例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="9ac43-108">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="9ac43-109">たとえば、いずれかの引数が null の場合は、`NullReferenceException` をスローするのではなく、false を返します。</span><span class="sxs-lookup"><span data-stu-id="9ac43-109">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="9ac43-110">値型での等値演算子</span><span class="sxs-lookup"><span data-stu-id="9ac43-110">Equality Operators on Value Types</span></span>

 <span data-ttu-id="9ac43-111">✔️ 等値性に意味がある場合は、値型で等値演算子をオーバーロードます。</span><span class="sxs-lookup"><span data-stu-id="9ac43-111">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="9ac43-112">ほとんどのプログラミング言語では、値型に `operator==` の既定の実装はありません。</span><span class="sxs-lookup"><span data-stu-id="9ac43-112">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="9ac43-113">参照型での等値演算子</span><span class="sxs-lookup"><span data-stu-id="9ac43-113">Equality Operators on Reference Types</span></span>

 <span data-ttu-id="9ac43-114">❌ 変更可能な参照型では、等値演算子をオーバーロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="9ac43-114">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="9ac43-115">多くの言語には、参照型に組み込みの等値演算子があります。</span><span class="sxs-lookup"><span data-stu-id="9ac43-115">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="9ac43-116">通常、組み込みの演算子には参照の等値性が実装されており、多くの開発者は、既定の動作が値の等値性に変更されると驚きます。</span><span class="sxs-lookup"><span data-stu-id="9ac43-116">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="9ac43-117">不変性によって参照の等値性と値の等値性の違いがわかりにくくなるため、この問題は、変更不可能な参照型については軽減されます。</span><span class="sxs-lookup"><span data-stu-id="9ac43-117">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="9ac43-118">❌ 実装が参照の等値性のものより大幅に遅くなる場合は、参照型で等値演算子をオーバーロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="9ac43-118">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="9ac43-119">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="9ac43-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9ac43-120">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="9ac43-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9ac43-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ac43-121">See also</span></span>

- [<span data-ttu-id="9ac43-122">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="9ac43-122">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="9ac43-123">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="9ac43-123">Usage Guidelines</span></span>](usage-guidelines.md)
