---
title: デプロイ戦略
description: ASP.NET から ASP.NET Core に移行する際にチームが使用できるデプロイ戦略 増分移行により、.NET Framework と .NET Core アプリをサイドバイサイドでデプロイできるため、シームレスなエンドユーザーエクスペリエンスが実現しますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 6691a4878205d6422cf8b6153353abefd9764d18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401383"
---
# <a name="deployment-strategies"></a><span data-ttu-id="97b22-104">デプロイ戦略</span><span class="sxs-lookup"><span data-stu-id="97b22-104">Deployment strategies</span></span>

<span data-ttu-id="97b22-105">ASP.NET Core するための大規模な ASP.NET アプリの移行を計画する際の考慮事項の1つは、新しいアプリをデプロイする方法です。</span><span class="sxs-lookup"><span data-stu-id="97b22-105">One consideration as you plan the migration of your large ASP.NET app to ASP.NET Core is how you'll deploy the new app.</span></span> <span data-ttu-id="97b22-106">ASP.NET では、配置オプションは Windows 上の IIS に限定されていました。</span><span class="sxs-lookup"><span data-stu-id="97b22-106">With ASP.NET, deployment options were limited to IIS on Windows.</span></span> <span data-ttu-id="97b22-107">ASP.NET Core を使用すると、より広範な展開オプションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="97b22-107">With ASP.NET Core, a much wider array of deployment options is available.</span></span>

## <a name="cross-platform-options"></a><span data-ttu-id="97b22-108">クロスプラットフォームオプション</span><span class="sxs-lookup"><span data-stu-id="97b22-108">Cross-platform options</span></span>

<span data-ttu-id="97b22-109">.NET Core は Linux 上で実行されるため、以前は考慮されていなかったホスティングオプションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="97b22-109">Because .NET Core runs on Linux, you'll find some hosting options available that weren't a consideration previously.</span></span> <span data-ttu-id="97b22-110">Linux ベースのホスティングは、次の理由で推奨されます。</span><span class="sxs-lookup"><span data-stu-id="97b22-110">Linux-based hosting may be preferable for the following reasons:</span></span>

* <span data-ttu-id="97b22-111">組織にはインフラストラクチャまたは専門知識があります。</span><span class="sxs-lookup"><span data-stu-id="97b22-111">Your organization has infrastructure or expertise.</span></span>
* <span data-ttu-id="97b22-112">ホスティングプロバイダーは、Linux ベースのホスティングの優れた機能や価格を提供します。</span><span class="sxs-lookup"><span data-stu-id="97b22-112">Hosting providers offer attractive features or pricing for Linux-based hosting.</span></span>

<span data-ttu-id="97b22-113">.NET Core が開き、これらのオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="97b22-113">.NET Core opens to door to these options.</span></span>

## <a name="cloud-native-development"></a><span data-ttu-id="97b22-114">クラウドネイティブ開発</span><span class="sxs-lookup"><span data-stu-id="97b22-114">Cloud native development</span></span>

<span data-ttu-id="97b22-115">現在、ほとんどの組織は、少なくともそのソフトウェア機能の一部に対してクラウドプラットフォームを使用しています。</span><span class="sxs-lookup"><span data-stu-id="97b22-115">Most organizations today are using cloud platforms for at least some of their software capabilities.</span></span> <span data-ttu-id="97b22-116">.NET Core へのアプリの移行では、クラウドホスティングを考慮してアプリを意図的に記述する必要があるかどうかを検討することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="97b22-116">With an app migration to .NET Core, it's a good time to consider whether the app should be purposefully written with cloud hosting in mind.</span></span> <span data-ttu-id="97b22-117">このような *クラウドネイティブ* アプリでは、サーバーレスのマイクロサービスのようなクラウド機能を適用することができ、デプロイの方法と場所の下位レベルの詳細についてはあまり注意が必要ありません。</span><span class="sxs-lookup"><span data-stu-id="97b22-117">Such *cloud native* apps are better able to apply cloud capabilities like serverless, microservices, and can be less concerned with the low-level details of how and where they may be deployed.</span></span>

<span data-ttu-id="97b22-118">クラウドネイティブアプリの開発の詳細については、 [Azure 向けのクラウドネイティブ .Net アプリケーションの設計](../cloud-native/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="97b22-118">Learn more about cloud native app development in this free e-book, [Architecting Cloud Native .NET Applications for Azure](../cloud-native/index.md).</span></span>

## <a name="leverage-containers"></a><span data-ttu-id="97b22-119">コンテナーを活用する</span><span class="sxs-lookup"><span data-stu-id="97b22-119">Leverage containers</span></span>

<span data-ttu-id="97b22-120">モダンアプリでは、多くの場合、ホスト環境間の変動を減らす手段としてコンテナーを利用しています。</span><span class="sxs-lookup"><span data-stu-id="97b22-120">Modern apps often leverage containers as a means of reducing variation between hosting environments.</span></span> <span data-ttu-id="97b22-121">アプリを特定のコンテナーにデプロイすることによって、コンテナーでホストされるアプリは、開発者のノート pc で実行されているか、運用環境で実行されているかにかかわらず、同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="97b22-121">By deploying an app to a particular container, the container-hosted app will run the same whether it's running on a developer's laptop or in production.</span></span> <span data-ttu-id="97b22-122">.NET Core への移行の一環として、アプリが完全なモノリスとして、または複数の小さなコンテナー化されたアプリに分割されている場合でも、コンテナーを使用したデプロイによってメリットが得られるかどうかを検討することが理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="97b22-122">As part of a migration to .NET Core, it may make sense to consider whether the app would benefit from deployment via container, either as a full monolith or broken up into multiple smaller containerized apps.</span></span>

## <a name="side-by-side-deployment-options"></a><span data-ttu-id="97b22-123">サイドバイサイド展開オプション</span><span class="sxs-lookup"><span data-stu-id="97b22-123">Side-by-side deployment options</span></span>

<span data-ttu-id="97b22-124">多くの場合、大規模な .NET Framework アプリを .NET Core に移行するにはかなりの労力が必要です。</span><span class="sxs-lookup"><span data-stu-id="97b22-124">Migrating large .NET Framework apps to .NET Core often requires a substantial effort.</span></span> <span data-ttu-id="97b22-125">ほとんどの組織では、この作業を何らかの方法で中断できるようにする必要があります。これにより、移行全体が完了する前に、アプリの一部を運用環境に移行して展開することができます。</span><span class="sxs-lookup"><span data-stu-id="97b22-125">Most organizations will want to be able to break this effort up in some fashion, so that pieces of the app can be migrated and deployed in production before the entire migration is complete.</span></span> <span data-ttu-id="97b22-126">元の ASP.NET アプリと新しく移行された ASP.NET Core サブアプリの両方をサイドバイサイドで実行することは、よく見られる目標です。</span><span class="sxs-lookup"><span data-stu-id="97b22-126">Running both the original ASP.NET app and its newly-migrated ASP.NET Core sub-app(s) side by side is a frequently cited goal.</span></span> <span data-ttu-id="97b22-127">これは、 [5 章](deployment-scenarios.md)で説明されている IIS ルーティングを利用するなど、さまざまなメカニズムによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="97b22-127">This can be achieved through a number of mechanisms including leveraging IIS routing, which is covered in [chapter 5](deployment-scenarios.md).</span></span> <span data-ttu-id="97b22-128">その他のオプションとしては、アプリゲートウェイを利用したり、 [バックエンドのフロントエンドの](/azure/architecture/patterns/backends-for-frontends) ようなクラウド設計パターンを使用して ASP.NET Web api のセットを管理したり、api エンドポイントを ASP.NET Core できます。</span><span class="sxs-lookup"><span data-stu-id="97b22-128">Other options include leveraging app gateways or cloud design patterns like [backends for frontends](/azure/architecture/patterns/backends-for-frontends) to manage sets of ASP.NET Web APIs and ASP.NET Core API endpoints.</span></span>

## <a name="iis-on-windows"></a><span data-ttu-id="97b22-129">Windows 上の IIS</span><span class="sxs-lookup"><span data-stu-id="97b22-129">IIS on Windows</span></span>

<span data-ttu-id="97b22-130">Windows で実行されている IIS でアプリのホスティングを続行できます。</span><span class="sxs-lookup"><span data-stu-id="97b22-130">You can continue hosting your apps on IIS running on Windows.</span></span> <span data-ttu-id="97b22-131">これは、現在のデプロイメントモデルを変更せずに ASP.NET Core の機能を利用することを希望するお客様にとっては、この方法が適しています。</span><span class="sxs-lookup"><span data-stu-id="97b22-131">This is a fine option for customers who want to take advantage of ASP.NET Core features without changing their current deployment model.</span></span> <span data-ttu-id="97b22-132">ASP.NET Core への移行では、アプリを展開する方法と場所に関してより多くのオプションが提供されますが、Windows で実証済みの IIS の組み合わせを使用している状態から変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="97b22-132">While moving to ASP.NET Core provides more options in terms of how and where to deploy your apps, it doesn't require that you change from the status quo of using the proven combination of IIS on Windows.</span></span>

## <a name="other-options-on-windows"></a><span data-ttu-id="97b22-133">Windows のその他のオプション</span><span class="sxs-lookup"><span data-stu-id="97b22-133">Other options on Windows</span></span>

<span data-ttu-id="97b22-134">必要に応じて、Docker コンテナーに加えて、Kestrel、HTTP.sys、および IIS ホストの任意の組み合わせを使用して、Windows 上でアプリをサイドバイサイドでホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="97b22-134">You can host apps side-by-side apps on Windows using any combination of Kestrel, HTTP.sys, and IIS hosts, in addition to Docker containers, if needed.</span></span> <span data-ttu-id="97b22-135">アプリで Windows と Linux のサービスを組み合わせて使用する必要がある場合は、 [Wsl](/windows/wsl/about) および linux Docker コンテナーがある windows server でホストすることで、アプリのすべての部分をホストする単一のサーバーソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="97b22-135">If your app requires a combination of Windows and Linux services, hosting on a Windows server with [WSL](/windows/wsl/about) and/or Linux Docker containers provides a single server solution to hosting all parts of the app.</span></span>

## <a name="references"></a><span data-ttu-id="97b22-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="97b22-136">References</span></span>

- [<span data-ttu-id="97b22-137">ASP.NET Core のホストと展開</span><span class="sxs-lookup"><span data-stu-id="97b22-137">Host and deploy ASP.NET Core</span></span>](/aspnet/core/host-and-deploy/)
- [<span data-ttu-id="97b22-138">IIS を使用した Windows での ASP.NET Core のホスト</span><span class="sxs-lookup"><span data-stu-id="97b22-138">Host ASP.NET Core on Windows with IIS</span></span>](/aspnet/core/host-and-deploy/iis/)
- [<span data-ttu-id="97b22-139">Azure App Service および IIS での ASP.NET Core のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="97b22-139">Troubleshooting ASP.NET Core on Azure App Service and IIS</span></span>](/aspnet/core/test/troubleshoot-azure-iis)

>[!div class="step-by-step"]
><span data-ttu-id="97b22-140">[前へ](migrate-web-forms.md)
>[次へ](additional-migration-resources.md)</span><span class="sxs-lookup"><span data-stu-id="97b22-140">[Previous](migrate-web-forms.md)
[Next](additional-migration-resources.md)</span></span>
