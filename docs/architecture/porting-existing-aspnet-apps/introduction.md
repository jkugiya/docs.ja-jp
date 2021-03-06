---
title: .NET Core へのアプリの移植の概要
description: この章では、既存の ASP.NET アプリを .NET Core に移行することを検討しているチーム向けの考慮事項の一覧を示します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a346d1c693389cc4ca682b41a3b7fc094cfa5482
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401231"
---
# <a name="introduction-to-porting-apps-to-net-core"></a><span data-ttu-id="60e18-103">.NET Core へのアプリの移植の概要</span><span class="sxs-lookup"><span data-stu-id="60e18-103">Introduction to porting apps to .NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="60e18-104">.NET Core は .NET Framework からの画期的なステップです。</span><span class="sxs-lookup"><span data-stu-id="60e18-104">.NET Core is a revolutionary step forward from .NET Framework.</span></span> <span data-ttu-id="60e18-105">また、クロスプラットフォームのサポートから開発者の満足度まで、生産性からパフォーマンスまで、.NET Framework よりも優れたホストを提供します。</span><span class="sxs-lookup"><span data-stu-id="60e18-105">It offers a host of advantages over .NET Framework across the board from productivity to performance, from cross-platform support to developer satisfaction.</span></span> <span data-ttu-id="60e18-106">ASP.NET Core は、 [2020 Stack Overflow 開発者アンケート](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)の中でも、最適な web フレームワークに投票しました。</span><span class="sxs-lookup"><span data-stu-id="60e18-106">ASP.NET Core was even voted the most-loved web framework in the [2020 Stack Overflow developer survey](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks).</span></span> <span data-ttu-id="60e18-107">移行を検討すべき理由は明らかです。</span><span class="sxs-lookup"><span data-stu-id="60e18-107">Clearly there are strong reasons to consider migrating.</span></span>

<span data-ttu-id="60e18-108">[.Net Core は .net の未来](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)であることを念頭に置くことが重要です。</span><span class="sxs-lookup"><span data-stu-id="60e18-108">It's important to keep in mind that [.NET Core is the Future of .NET](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/).</span></span> <span data-ttu-id="60e18-109">この記事を引用するには:</span><span class="sxs-lookup"><span data-stu-id="60e18-109">To quote this article:</span></span>

> <span data-ttu-id="60e18-110">新しいアプリは .NET Core 上に構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e18-110">New apps should be built on .NET Core.</span></span> <span data-ttu-id="60e18-111">.Net Core は、.NET における将来の投資が行われる場所です。</span><span class="sxs-lookup"><span data-stu-id="60e18-111">.NET Core is where future investments in .NET will happen.</span></span> <span data-ttu-id="60e18-112">既存のアプリは、サポートされる .NET Framework に安全に維持されます。</span><span class="sxs-lookup"><span data-stu-id="60e18-112">Existing apps are safe to remain on .NET Framework which will be supported.</span></span> <span data-ttu-id="60e18-113">.NET の新機能を利用する既存のアプリでは、.NET Core への移行を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e18-113">Existing apps that want to take advantage of the new features in .NET should consider moving to .NET Core.</span></span> <span data-ttu-id="60e18-114">今後の計画では、プラットフォームにさらに多くの機能が導入される予定です。</span><span class="sxs-lookup"><span data-stu-id="60e18-114">As we plan into the future, we will be bringing in even more capabilities to the platform.</span></span>

<span data-ttu-id="60e18-115">ただし、アプリを ASP.NET Core にアップグレードするには、いくつかの作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="60e18-115">However, upgrading your app to ASP.NET Core will require some effort.</span></span> <span data-ttu-id="60e18-116">この作業は、ビジネス価値と目標に対してバランスを取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e18-116">That effort should be balanced against business value and goals.</span></span> <span data-ttu-id="60e18-117">.NET Framework のアプリには長い時間がかかっており、将来、Windows に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="60e18-117">.NET Framework apps have a long life ahead of them, with support built into Windows for the foreseeable future.</span></span> <span data-ttu-id="60e18-118">.NET Core への移行を決定する前に考慮する必要がある質問のいくつかを次の中からお選びください。</span><span class="sxs-lookup"><span data-stu-id="60e18-118">What are some of the questions you should consider before deciding migration to .NET Core is appropriate?</span></span> <span data-ttu-id="60e18-119">期待される利点は何ですか。</span><span class="sxs-lookup"><span data-stu-id="60e18-119">What are the expected advantages?</span></span> <span data-ttu-id="60e18-120">トレードオフとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="60e18-120">What are the tradeoffs?</span></span> <span data-ttu-id="60e18-121">どの程度の労力が関係していますか?</span><span class="sxs-lookup"><span data-stu-id="60e18-121">How much effort is involved?</span></span> <span data-ttu-id="60e18-122">これらの明らかな質問は最初のものですが、チームは今日と明日のアプリで顧客のニーズをサポートする方法を検討することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60e18-122">These obvious questions are just the beginning, but make for a great starting point as teams consider how to support their customers' needs with apps today and tomorrow.</span></span>

- <span data-ttu-id="60e18-123">.NET Core への移行は適切ですか?</span><span class="sxs-lookup"><span data-stu-id="60e18-123">Is migration to .NET Core appropriate?</span></span>
- <span data-ttu-id="60e18-124">.NET Framework にとどまるのはいつでしょうか。</span><span class="sxs-lookup"><span data-stu-id="60e18-124">When does it make sense to remain on .NET Framework?</span></span>
- <span data-ttu-id="60e18-125">アプリのターゲットをステップ実行のストーンとして 2.1 ASP.NET Core する必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="60e18-125">Should apps target ASP.NET Core 2.1 as a stepping stone?</span></span>
- <span data-ttu-id="60e18-126">対象とする適切な .NET Core バージョンをチームでどのように選択すればよいですか。</span><span class="sxs-lookup"><span data-stu-id="60e18-126">How should teams choose the right .NET Core version to target?</span></span>
- <span data-ttu-id="60e18-127">大規模なアプリの増分移行には、どのような戦略が推奨されますか。</span><span class="sxs-lookup"><span data-stu-id="60e18-127">What strategies are recommended for incremental migration of large apps?</span></span>
- <span data-ttu-id="60e18-128">.NET Core に移植するときに考慮する必要があるデプロイメント戦略</span><span class="sxs-lookup"><span data-stu-id="60e18-128">What deployment strategies should be considered when porting to .NET Core?</span></span>
- <span data-ttu-id="60e18-129">その他のリソースはどこで入手できますか。</span><span class="sxs-lookup"><span data-stu-id="60e18-129">Where can we find additional resources?</span></span>

<span data-ttu-id="60e18-130">この入門編では、今後の章で、より具体的で技術的な考慮事項に進む前に、これらのすべての質問とその詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="60e18-130">This introductory chapter addresses all of these questions and more before moving on to more specific and technical considerations in future chapters.</span></span>

## <a name="references"></a><span data-ttu-id="60e18-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="60e18-131">References</span></span>

- [<span data-ttu-id="60e18-132">2020 Stack Overflow 開発者にとって最も人気のある web フレームワーク</span><span class="sxs-lookup"><span data-stu-id="60e18-132">2020 Stack Overflow developer survey most loved web frameworks</span></span>](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)
- [<span data-ttu-id="60e18-133">.Net Core は .NET の未来です</span><span class="sxs-lookup"><span data-stu-id="60e18-133">.NET Core is the Future of .NET</span></span>](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)

>[!div class="step-by-step"]
><span data-ttu-id="60e18-134">[前へ](index.md)
>[次へ](migration-considerations.md)</span><span class="sxs-lookup"><span data-stu-id="60e18-134">[Previous](index.md)
[Next](migration-considerations.md)</span></span>
