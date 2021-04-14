---
title: デプロイ戦略
description: ASP.NET から ASP.NET Core に移行する際に、チームはどのような展開戦略を使用できるでしょうか? 段階的移行を使用すると、.NET Framework アプリと .NET Core アプリをサイドバイサイドで展開してシームレスなエンド ユーザー エクスペリエンスを実現できるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 6691a4878205d6422cf8b6153353abefd9764d18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401383"
---
# <a name="deployment-strategies"></a><span data-ttu-id="13fb5-104">デプロイ戦略</span><span class="sxs-lookup"><span data-stu-id="13fb5-104">Deployment strategies</span></span>

<span data-ttu-id="13fb5-105">大規模な ASP.NET アプリの ASP.NET Core への移行を計画するときの考慮事項の 1 つに、新しいアプリをどのように展開するかという点があります。</span><span class="sxs-lookup"><span data-stu-id="13fb5-105">One consideration as you plan the migration of your large ASP.NET app to ASP.NET Core is how you'll deploy the new app.</span></span> <span data-ttu-id="13fb5-106">ASP.NET では、展開オプションは Windows 上の IIS のみに限られていました。</span><span class="sxs-lookup"><span data-stu-id="13fb5-106">With ASP.NET, deployment options were limited to IIS on Windows.</span></span> <span data-ttu-id="13fb5-107">ASP.NET Core では、はるかに幅広い展開オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="13fb5-107">With ASP.NET Core, a much wider array of deployment options is available.</span></span>

## <a name="cross-platform-options"></a><span data-ttu-id="13fb5-108">クロスプラットフォーム オプション</span><span class="sxs-lookup"><span data-stu-id="13fb5-108">Cross-platform options</span></span>

<span data-ttu-id="13fb5-109">.NET Core は Linux 上で実行されるため、以前は検討対象になかったホスティング オプションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="13fb5-109">Because .NET Core runs on Linux, you'll find some hosting options available that weren't a consideration previously.</span></span> <span data-ttu-id="13fb5-110">以下の理由から、Linux ベースのホスティングをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13fb5-110">Linux-based hosting may be preferable for the following reasons:</span></span>

* <span data-ttu-id="13fb5-111">組織にインフラストラクチャや専門知識がある。</span><span class="sxs-lookup"><span data-stu-id="13fb5-111">Your organization has infrastructure or expertise.</span></span>
* <span data-ttu-id="13fb5-112">Linux ベースのホスティングに関しては、ホスティング プロバイダーから魅力的な機能や価格が提供されている。</span><span class="sxs-lookup"><span data-stu-id="13fb5-112">Hosting providers offer attractive features or pricing for Linux-based hosting.</span></span>

<span data-ttu-id="13fb5-113">.NET Core により、これらのオプションを利用する機会が得られます。</span><span class="sxs-lookup"><span data-stu-id="13fb5-113">.NET Core opens to door to these options.</span></span>

## <a name="cloud-native-development"></a><span data-ttu-id="13fb5-114">クラウド ネイティブ開発</span><span class="sxs-lookup"><span data-stu-id="13fb5-114">Cloud native development</span></span>

<span data-ttu-id="13fb5-115">今日のほとんどの組織は、少なくともそのソフトウェア機能の一部に対して、クラウド プラットフォームを使用しています。</span><span class="sxs-lookup"><span data-stu-id="13fb5-115">Most organizations today are using cloud platforms for at least some of their software capabilities.</span></span> <span data-ttu-id="13fb5-116">.NET Core へのアプリの移行に伴い、意図的にクラウド ホスティングを念頭に置いてアプリを記述するべきかどうかを検討することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13fb5-116">With an app migration to .NET Core, it's a good time to consider whether the app should be purposefully written with cloud hosting in mind.</span></span> <span data-ttu-id="13fb5-117">このような "*クラウド ネイティブ*" アプリは、サーバーレスやマイクロサービスなどのクラウド機能を適用しやすく、それらの展開方法や展開場所といった下位レベルの詳細についての懸念も少なくなります。</span><span class="sxs-lookup"><span data-stu-id="13fb5-117">Such *cloud native* apps are better able to apply cloud capabilities like serverless, microservices, and can be less concerned with the low-level details of how and where they may be deployed.</span></span>

<span data-ttu-id="13fb5-118">クラウド ネイティブ アプリの開発の詳細については、無料の電子書籍「[Azure 向けクラウド ネイティブ .NET アプリケーションの設計](../cloud-native/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13fb5-118">Learn more about cloud native app development in this free e-book, [Architecting Cloud Native .NET Applications for Azure](../cloud-native/index.md).</span></span>

## <a name="leverage-containers"></a><span data-ttu-id="13fb5-119">コンテナーの利用</span><span class="sxs-lookup"><span data-stu-id="13fb5-119">Leverage containers</span></span>

<span data-ttu-id="13fb5-120">最新のアプリでは、多くの場合、ホスト環境間のばらつきを低減する手段としてコンテナーを利用しています。</span><span class="sxs-lookup"><span data-stu-id="13fb5-120">Modern apps often leverage containers as a means of reducing variation between hosting environments.</span></span> <span data-ttu-id="13fb5-121">特定のコンテナーにアプリを展開することにより、そのコンテナーでホストされるアプリを開発者のノート PC 上でも運用環境でも同じように実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="13fb5-121">By deploying an app to a particular container, the container-hosted app will run the same whether it's running on a developer's laptop or in production.</span></span> <span data-ttu-id="13fb5-122">.NET Core への移行の一環として、コンテナーを使用して (1 つの完全なモノリスとして、または複数のより小規模なコンテナー化されたアプリに分割して) 展開することでアプリがベネフィットを得られるかどうかを検討することは理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="13fb5-122">As part of a migration to .NET Core, it may make sense to consider whether the app would benefit from deployment via container, either as a full monolith or broken up into multiple smaller containerized apps.</span></span>

## <a name="side-by-side-deployment-options"></a><span data-ttu-id="13fb5-123">サイドバイサイド展開オプション</span><span class="sxs-lookup"><span data-stu-id="13fb5-123">Side-by-side deployment options</span></span>

<span data-ttu-id="13fb5-124">多くの場合、大規模な .NET Framework アプリを .NET Core に移行するにはかなりの作業量が必要となります。</span><span class="sxs-lookup"><span data-stu-id="13fb5-124">Migrating large .NET Framework apps to .NET Core often requires a substantial effort.</span></span> <span data-ttu-id="13fb5-125">ほとんどの組織では、この作業を何らかの方法で分割して、移行全体を完了する前にアプリの一部を移行し、運用環境に展開できるようにしたいと考えることでしょう。</span><span class="sxs-lookup"><span data-stu-id="13fb5-125">Most organizations will want to be able to break this effort up in some fashion, so that pieces of the app can be migrated and deployed in production before the entire migration is complete.</span></span> <span data-ttu-id="13fb5-126">元の ASP.NET アプリとその新しく移行された ASP.NET Core サブアプリをサイドバイサイドで実行することは、よく挙げられる目標です。</span><span class="sxs-lookup"><span data-stu-id="13fb5-126">Running both the original ASP.NET app and its newly-migrated ASP.NET Core sub-app(s) side by side is a frequently cited goal.</span></span> <span data-ttu-id="13fb5-127">これは IIS ルーティングの活用など、さまざまなメカニズムによって実現できます。これについては[第 5 章](deployment-scenarios.md)で説明します。</span><span class="sxs-lookup"><span data-stu-id="13fb5-127">This can be achieved through a number of mechanisms including leveraging IIS routing, which is covered in [chapter 5](deployment-scenarios.md).</span></span> <span data-ttu-id="13fb5-128">その他のオプションとしては、アプリ ゲートウェイやクラウド設計パターン ([フロントエンド用バックエンド](/azure/architecture/patterns/backends-for-frontends) など) を利用して一連の ASP.NET Web API と ASP.NET Core API エンドポイントを管理する方法などがあります。</span><span class="sxs-lookup"><span data-stu-id="13fb5-128">Other options include leveraging app gateways or cloud design patterns like [backends for frontends](/azure/architecture/patterns/backends-for-frontends) to manage sets of ASP.NET Web APIs and ASP.NET Core API endpoints.</span></span>

## <a name="iis-on-windows"></a><span data-ttu-id="13fb5-129">Windows 上の IIS</span><span class="sxs-lookup"><span data-stu-id="13fb5-129">IIS on Windows</span></span>

<span data-ttu-id="13fb5-130">Windows で実行されている IIS 上で、引き続きアプリをホストできます。</span><span class="sxs-lookup"><span data-stu-id="13fb5-130">You can continue hosting your apps on IIS running on Windows.</span></span> <span data-ttu-id="13fb5-131">これは、現在の展開モデルを変更することなく ASP.NET Core の機能を利用したいと考えているお客様に適したオプションです。</span><span class="sxs-lookup"><span data-stu-id="13fb5-131">This is a fine option for customers who want to take advantage of ASP.NET Core features without changing their current deployment model.</span></span> <span data-ttu-id="13fb5-132">ASP.NET Core への移行時には、アプリの展開方法と展開場所に関して幅広いオプションが用意されていますが、Windows 上の IIS という定評のある組み合わせを使用している現状を変えなければならないわけではありません。</span><span class="sxs-lookup"><span data-stu-id="13fb5-132">While moving to ASP.NET Core provides more options in terms of how and where to deploy your apps, it doesn't require that you change from the status quo of using the proven combination of IIS on Windows.</span></span>

## <a name="other-options-on-windows"></a><span data-ttu-id="13fb5-133">Windows 上のその他のオプション</span><span class="sxs-lookup"><span data-stu-id="13fb5-133">Other options on Windows</span></span>

<span data-ttu-id="13fb5-134">必要に応じて、Docker コンテナーに加えて Kestrel、HTTP.sys、および IIS ホストの任意の組み合わせを使用して、アプリを Windows 上でサイドバイサイドでホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="13fb5-134">You can host apps side-by-side apps on Windows using any combination of Kestrel, HTTP.sys, and IIS hosts, in addition to Docker containers, if needed.</span></span> <span data-ttu-id="13fb5-135">アプリで Windows のサービスと Linux のサービスを組み合わせる必要がある場合は、[WSL](/windows/wsl/about) または Linux Docker コンテナー (あるいはその両方) を使用して Windows サーバー上でホストすることで、アプリのすべての部分をホストする単一のソリューションを提供できます。</span><span class="sxs-lookup"><span data-stu-id="13fb5-135">If your app requires a combination of Windows and Linux services, hosting on a Windows server with [WSL](/windows/wsl/about) and/or Linux Docker containers provides a single server solution to hosting all parts of the app.</span></span>

## <a name="references"></a><span data-ttu-id="13fb5-136">リファレンス</span><span class="sxs-lookup"><span data-stu-id="13fb5-136">References</span></span>

- [<span data-ttu-id="13fb5-137">ASP.NET Core のホストと展開</span><span class="sxs-lookup"><span data-stu-id="13fb5-137">Host and deploy ASP.NET Core</span></span>](/aspnet/core/host-and-deploy/)
- [<span data-ttu-id="13fb5-138">IIS を使用した Windows での ASP.NET Core のホスト</span><span class="sxs-lookup"><span data-stu-id="13fb5-138">Host ASP.NET Core on Windows with IIS</span></span>](/aspnet/core/host-and-deploy/iis/)
- [<span data-ttu-id="13fb5-139">Azure App Service および IIS での ASP.NET Core のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="13fb5-139">Troubleshooting ASP.NET Core on Azure App Service and IIS</span></span>](/aspnet/core/test/troubleshoot-azure-iis)

>[!div class="step-by-step"]
><span data-ttu-id="13fb5-140">[前へ](migrate-web-forms.md)
>[次へ](additional-migration-resources.md)</span><span class="sxs-lookup"><span data-stu-id="13fb5-140">[Previous](migrate-web-forms.md)
[Next](additional-migration-resources.md)</span></span>
