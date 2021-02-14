---
description: '詳細情報: 仮想メンバー'
title: 仮想メンバー
ms.date: 10/22/2008
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 7618686764fb3a24ef53e5168b871366b7ffb5bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641786"
---
# <a name="virtual-members"></a><span data-ttu-id="7a1c2-103">仮想メンバー</span><span class="sxs-lookup"><span data-stu-id="7a1c2-103">Virtual Members</span></span>

<span data-ttu-id="7a1c2-104">仮想メンバーはオーバーライドすることができ、それによってサブクラスの動作を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-104">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="7a1c2-105">それらは、提供される機能拡張に関してコールバックとよく似ていますが、実行のパフォーマンスとメモリの消費に関してはそれよりも優れています。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-105">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="7a1c2-106">また、仮想メンバーは、特別な種類の既存の型を作成 (特殊化) する必要があるシナリオでは、より自然に感じられます。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-106">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="7a1c2-107">仮想メンバーのパフォーマンスは、コールバックとイベントよりも優れていますが、非仮想メソッドほどは優れていません。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-107">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="7a1c2-108">仮想メンバーの主な欠点は、仮想メンバーの動作はコンパイル時にのみ変更できることです。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-108">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="7a1c2-109">コールバックの動作は、実行時に変更できます。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-109">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="7a1c2-110">仮想メンバーは、コールバックのように (おそらくコールバック以上に)、設計、テスト、およびメンテナンスにコストがかかります。これは、仮想メンバーへのすべての呼び出しは予測不可能な方法でオーバーライドされ、任意のコードが実行される可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-110">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="7a1c2-111">また、仮想メンバーのコントラクトを明確に定義するには、通常はさらに多くの労力が必要であるため、それらを設計して文書化するコストが高くなります。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-111">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="7a1c2-112">❌ メンバーを仮想にする正当な理由があり、かつ仮想メンバーの設計、テスト、およびメンテナンスに関連するすべてのコストを把握している場合を除いて、メンバーを仮想にしないでください。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-112">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="7a1c2-113">仮想メンバーは、互換性を損なわずに実行できる変更という観点から見ると、許容度が低くなっています。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-113">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="7a1c2-114">また、ほとんどの場合、仮想メンバーへの呼び出しはインライン化されないため、非仮想メンバーよりも処理速度が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-114">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="7a1c2-115">✔️ 絶対に必要な範囲にのみ、機能拡張を制限することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-115">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="7a1c2-116">✔️ 仮想メンバーに対するアクセシビリティは、パブリックなものよりも保護されたものを優先してください。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-116">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="7a1c2-117">パブリック メンバーは、保護された仮想メンバーを呼び出すことで (必要に応じて) 拡張性を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-117">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="7a1c2-118">クラスのパブリック メンバーは、そのクラスを直接使用するものに対して、適切な機能セットを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-118">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="7a1c2-119">仮想メンバーはサブクラスでオーバーライドされるように設計されており、保護されたアクセシビリティは、すべての仮想拡張ポイントのスコープを、それらが使用できる場所に設定するための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="7a1c2-119">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="7a1c2-120">*Portions &copy; 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="7a1c2-120">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7a1c2-121">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="7a1c2-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7a1c2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a1c2-122">See also</span></span>

- [<span data-ttu-id="7a1c2-123">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7a1c2-123">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="7a1c2-124">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="7a1c2-124">Designing for Extensibility</span></span>](designing-for-extensibility.md)
