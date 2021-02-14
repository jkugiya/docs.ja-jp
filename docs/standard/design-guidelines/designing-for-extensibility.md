---
description: '詳細情報: 機能拡張のデザイン'
title: 機能拡張のデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 148ae25380698a5a1161fb9fbdd3cc60102e865d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642267"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="df172-103">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="df172-103">Designing for Extensibility</span></span>

<span data-ttu-id="df172-104">フレームワークを設計するときに重要な点の 1 つは、フレームワークの拡張性を慎重に考慮することです。</span><span class="sxs-lookup"><span data-stu-id="df172-104">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="df172-105">これには、さまざまな拡張メカニズムに関連するコストと利点を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df172-105">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="df172-106">この章は、どの拡張メカニズム (サブクラス化、イベント、仮想メンバー、コールバックなど) が自分のフレームワークの要件に最適かを判断するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="df172-106">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="df172-107">フレームワークで拡張性を実現するには、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="df172-107">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="df172-108">これは、非力でも低コストのものから、強力でも高コストのものまでさまざまです。</span><span class="sxs-lookup"><span data-stu-id="df172-108">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="df172-109">特定の拡張要件について、要件を満たす最も低コストの拡張性メカニズムを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df172-109">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="df172-110">通常、後で拡張機能を追加することはできますが、破壊的変更を発生させずにそれを取り除くことはできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="df172-110">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df172-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="df172-111">In This Section</span></span>  

 [<span data-ttu-id="df172-112">シールされていないクラス</span><span class="sxs-lookup"><span data-stu-id="df172-112">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="df172-113">プロテクト メンバー</span><span class="sxs-lookup"><span data-stu-id="df172-113">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="df172-114">イベントとコールバック</span><span class="sxs-lookup"><span data-stu-id="df172-114">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="df172-115">仮想メンバー</span><span class="sxs-lookup"><span data-stu-id="df172-115">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="df172-116">抽象化 (抽象型およびインターフェイス)</span><span class="sxs-lookup"><span data-stu-id="df172-116">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="df172-117">抽象化の実装用の基本クラス</span><span class="sxs-lookup"><span data-stu-id="df172-117">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="df172-118">シール</span><span class="sxs-lookup"><span data-stu-id="df172-118">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="df172-119">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="df172-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="df172-120">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="df172-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df172-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="df172-121">See also</span></span>

- [<span data-ttu-id="df172-122">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="df172-122">Framework Design Guidelines</span></span>](index.md)
