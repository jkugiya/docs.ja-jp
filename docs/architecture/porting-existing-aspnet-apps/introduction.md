---
title: .NET Core へのアプリの移植の概要
description: この章では、既存の ASP.NET アプリから .NET Core への移行を検討しているチーム向けの考慮事項の一覧を示します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a346d1c693389cc4ca682b41a3b7fc094cfa5482
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401231"
---
# <a name="introduction-to-porting-apps-to-net-core"></a><span data-ttu-id="c7780-103">.NET Core へのアプリの移植の概要</span><span class="sxs-lookup"><span data-stu-id="c7780-103">Introduction to porting apps to .NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c7780-104">.NET Core は、.NET Framework を画期的に進歩させたものです。</span><span class="sxs-lookup"><span data-stu-id="c7780-104">.NET Core is a revolutionary step forward from .NET Framework.</span></span> <span data-ttu-id="c7780-105">生産性からパフォーマンスまで、またクロスプラットフォーム サポートから開発者満足度まで、.NET Framework 全体にわたって数多くのメリットをもたらします。</span><span class="sxs-lookup"><span data-stu-id="c7780-105">It offers a host of advantages over .NET Framework across the board from productivity to performance, from cross-platform support to developer satisfaction.</span></span> <span data-ttu-id="c7780-106">ASP.NET Core は、[Stack Overflow の 2020 年開発者調査](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)で、最も人気のある Web フレームワークに選ばれました。</span><span class="sxs-lookup"><span data-stu-id="c7780-106">ASP.NET Core was even voted the most-loved web framework in the [2020 Stack Overflow developer survey](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks).</span></span> <span data-ttu-id="c7780-107">移行を検討するだけの強力な理由があるのは明らかです。</span><span class="sxs-lookup"><span data-stu-id="c7780-107">Clearly there are strong reasons to consider migrating.</span></span>

<span data-ttu-id="c7780-108">[.NET Core は .NET の未来である](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)ことを念頭に置いておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="c7780-108">It's important to keep in mind that [.NET Core is the Future of .NET](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/).</span></span> <span data-ttu-id="c7780-109">以下は、この記事からの引用です。</span><span class="sxs-lookup"><span data-stu-id="c7780-109">To quote this article:</span></span>

> <span data-ttu-id="c7780-110">新しいアプリは .NET Core 上で構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7780-110">New apps should be built on .NET Core.</span></span> <span data-ttu-id="c7780-111">.Net Core は、.NET への今後の投資が行われる場所です。</span><span class="sxs-lookup"><span data-stu-id="c7780-111">.NET Core is where future investments in .NET will happen.</span></span> <span data-ttu-id="c7780-112">既存のアプリは、今後サポートされる .NET Framework 上で安全に維持できます。</span><span class="sxs-lookup"><span data-stu-id="c7780-112">Existing apps are safe to remain on .NET Framework which will be supported.</span></span> <span data-ttu-id="c7780-113">.NET の新機能を利用したい既存のアプリは、.NET Core に移行することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7780-113">Existing apps that want to take advantage of the new features in .NET should consider moving to .NET Core.</span></span> <span data-ttu-id="c7780-114">Microsoft の今後の計画では、さらに多くの機能がこのプラットフォームに導入される予定です。</span><span class="sxs-lookup"><span data-stu-id="c7780-114">As we plan into the future, we will be bringing in even more capabilities to the platform.</span></span>

<span data-ttu-id="c7780-115">ただし、アプリを ASP.NET Core にアップグレードするにはいくつかの作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c7780-115">However, upgrading your app to ASP.NET Core will require some effort.</span></span> <span data-ttu-id="c7780-116">その作業量と、ビジネス バリューおよびゴールとを天秤にかける必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7780-116">That effort should be balanced against business value and goals.</span></span> <span data-ttu-id="c7780-117">.NET Framework アプリは、当面の間 Windows にサポートが組み込まれるため、まだ長い寿命があります。</span><span class="sxs-lookup"><span data-stu-id="c7780-117">.NET Framework apps have a long life ahead of them, with support built into Windows for the foreseeable future.</span></span> <span data-ttu-id="c7780-118">.NET Core への移行が適切であると判断する前に、どのような疑問について検討する必要があるでしょうか?</span><span class="sxs-lookup"><span data-stu-id="c7780-118">What are some of the questions you should consider before deciding migration to .NET Core is appropriate?</span></span> <span data-ttu-id="c7780-119">期待されるメリットは何ですか?</span><span class="sxs-lookup"><span data-stu-id="c7780-119">What are the expected advantages?</span></span> <span data-ttu-id="c7780-120">どのようなトレードオフがありますか?</span><span class="sxs-lookup"><span data-stu-id="c7780-120">What are the tradeoffs?</span></span> <span data-ttu-id="c7780-121">どれだけの作業量が必要になりますか?</span><span class="sxs-lookup"><span data-stu-id="c7780-121">How much effort is involved?</span></span> <span data-ttu-id="c7780-122">これらの明白な質問はほんの始まりにすぎませんが、チームが現在と将来のアプリに関する顧客のニーズをどのようにサポートするかを検討する際の良い出発点となります。</span><span class="sxs-lookup"><span data-stu-id="c7780-122">These obvious questions are just the beginning, but make for a great starting point as teams consider how to support their customers' needs with apps today and tomorrow.</span></span>

- <span data-ttu-id="c7780-123">.NET Core への移行は適切ですか?</span><span class="sxs-lookup"><span data-stu-id="c7780-123">Is migration to .NET Core appropriate?</span></span>
- <span data-ttu-id="c7780-124">.NET Framework にとどまることが理にかなっているのはどのような場合ですか?</span><span class="sxs-lookup"><span data-stu-id="c7780-124">When does it make sense to remain on .NET Framework?</span></span>
- <span data-ttu-id="c7780-125">足がかりとして、ASP.NET Core 2.1 をアプリのターゲットにする必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="c7780-125">Should apps target ASP.NET Core 2.1 as a stepping stone?</span></span>
- <span data-ttu-id="c7780-126">チームは、ターゲットにする適切な .NET Core のバージョンをどのように選択しますか?</span><span class="sxs-lookup"><span data-stu-id="c7780-126">How should teams choose the right .NET Core version to target?</span></span>
- <span data-ttu-id="c7780-127">大規模なアプリの段階的な移行には、どのような戦略が推奨されますか?</span><span class="sxs-lookup"><span data-stu-id="c7780-127">What strategies are recommended for incremental migration of large apps?</span></span>
- <span data-ttu-id="c7780-128">.NET Core への移行時にはどのような展開戦略を検討する必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="c7780-128">What deployment strategies should be considered when porting to .NET Core?</span></span>
- <span data-ttu-id="c7780-129">追加のリソースはどこで入手できますか?</span><span class="sxs-lookup"><span data-stu-id="c7780-129">Where can we find additional resources?</span></span>

<span data-ttu-id="c7780-130">この序章では、後の章でより具体的かつ技術的な考慮事項に進む前に、これらすべてを含めたさまざまな疑問に答えます。</span><span class="sxs-lookup"><span data-stu-id="c7780-130">This introductory chapter addresses all of these questions and more before moving on to more specific and technical considerations in future chapters.</span></span>

## <a name="references"></a><span data-ttu-id="c7780-131">リファレンス</span><span class="sxs-lookup"><span data-stu-id="c7780-131">References</span></span>

- [<span data-ttu-id="c7780-132">Stack Overflow の 2020 年開発者調査における最も人気のある Web フレームワーク</span><span class="sxs-lookup"><span data-stu-id="c7780-132">2020 Stack Overflow developer survey most loved web frameworks</span></span>](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)
- [<span data-ttu-id="c7780-133">.Net Core は .NET の未来である</span><span class="sxs-lookup"><span data-stu-id="c7780-133">.NET Core is the Future of .NET</span></span>](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)

>[!div class="step-by-step"]
><span data-ttu-id="c7780-134">[前へ](index.md)
>[次へ](migration-considerations.md)</span><span class="sxs-lookup"><span data-stu-id="c7780-134">[Previous](index.md)
[Next](migration-considerations.md)</span></span>
