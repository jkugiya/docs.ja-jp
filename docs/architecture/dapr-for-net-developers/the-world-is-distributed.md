---
title: 世界は分散型
description: モノリシックおよび SOA アプローチを使用した分散アプリケーションの利点と課題。
author: robvet
ms.date: 02/07/2021
ms.openlocfilehash: b857355880c3942526d751312d98f2b822704759
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401426"
---
# <a name="the-world-is-distributed"></a><span data-ttu-id="9b3c7-103">世界は分散型</span><span class="sxs-lookup"><span data-stu-id="9b3c7-103">The world is distributed</span></span>

<span data-ttu-id="9b3c7-104">「クールな子供」と聞いてみてください。*最新の分散システムはにあり、モノリシックアプリはありません*。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-104">Just ask any 'cool kid': *Modern, distributed systems are in, and monolithic apps are out!*</span></span>

<span data-ttu-id="9b3c7-105">しかし、"すばらしい子供" ではありません。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-105">But, it's not just "cool kids."</span></span> <span data-ttu-id="9b3c7-106">最先端の IT リーダー、企業のアーキテクト、ずる賢いの開発者は、最新の分散アプリケーションを探索して評価する際に、これらと同じ考えをお試しください。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-106">Progressive IT Leaders, corporate architects, and astute developers are echoing these same thoughts as they explore and evaluate modern distributed applications.</span></span> <span data-ttu-id="9b3c7-107">多くの製品が購入されています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-107">Many have bought in.</span></span> <span data-ttu-id="9b3c7-108">分散マイクロサービスアプリケーションの原則、パターン、プラクティスに従って、既存のエンタープライズアプリケーションを新規に設計し、基幹しています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-108">They're designing new and replatforming existing enterprise applications following the principles, patterns, and practices of distributed microservice applications.</span></span>

<span data-ttu-id="9b3c7-109">しかし、この進化によって多くの質問が発生します...</span><span class="sxs-lookup"><span data-stu-id="9b3c7-109">But, this evolution raises many questions...</span></span>

- <span data-ttu-id="9b3c7-110">分散アプリケーションとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-110">What exactly is a distributed application?</span></span>
- <span data-ttu-id="9b3c7-111">なぜ人気が高まっているのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-111">Why are they gaining popularity?</span></span>
- <span data-ttu-id="9b3c7-112">コストはどのようなものですか?</span><span class="sxs-lookup"><span data-stu-id="9b3c7-112">What are the costs?</span></span>
- <span data-ttu-id="9b3c7-113">そして、トレードオフとは何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-113">And, importantly, what are the tradeoffs?</span></span>

<span data-ttu-id="9b3c7-114">まず、過去15年間を巻き戻して見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-114">To start, let's rewind and look at the past 15 years.</span></span> <span data-ttu-id="9b3c7-115">この期間中は、通常、単一のモノリシックユニットとしてアプリケーションを構築しています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-115">During this period, we typically constructed applications as a single, monolithic unit.</span></span> <span data-ttu-id="9b3c7-116">図1-1 にアーキテクチャを示します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-116">Figure 1-1 shows the architecture.</span></span>

![モノリシックアーキテクチャ。](./media/the-world-is-distributed/monolithic-design.png)

<span data-ttu-id="9b3c7-118">**(図 1-1)** 。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-118">**Figure 1-1**.</span></span> <span data-ttu-id="9b3c7-119">モノリシックアーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-119">Monolithic architecture.</span></span>

<span data-ttu-id="9b3c7-120">注文、Id、およびマーケティングのモジュールが単一サーバープロセスで実行されるしくみに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-120">Note how the modules for Ordering, Identity, and Marketing execute in a single-server process.</span></span> <span data-ttu-id="9b3c7-121">アプリケーションデータは、共有データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-121">Application data is stored in a shared database.</span></span> <span data-ttu-id="9b3c7-122">ビジネス機能は、HTML および RESTful インターフェイスを介して公開されます。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-122">Business functionality is exposed via HTML and RESTful interfaces.</span></span>

<span data-ttu-id="9b3c7-123">多くの点でモノリシックアプリは `straightforward` です。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-123">In many ways, monolithic apps are `straightforward`.</span></span> <span data-ttu-id="9b3c7-124">次のような簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-124">They're straightforward to:</span></span>

- <span data-ttu-id="9b3c7-125">Build</span><span class="sxs-lookup"><span data-stu-id="9b3c7-125">Build</span></span>
- <span data-ttu-id="9b3c7-126">テスト</span><span class="sxs-lookup"><span data-stu-id="9b3c7-126">Test</span></span>
- <span data-ttu-id="9b3c7-127">デプロイ</span><span class="sxs-lookup"><span data-stu-id="9b3c7-127">Deploy</span></span>
- <span data-ttu-id="9b3c7-128">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9b3c7-128">Troubleshoot</span></span>
- <span data-ttu-id="9b3c7-129">垂直方向にスケール (スケールアップ)</span><span class="sxs-lookup"><span data-stu-id="9b3c7-129">Scale vertically (scale up)</span></span>

<span data-ttu-id="9b3c7-130">ただし、モノリシックアーキテクチャでは大きな課題が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-130">However, monolithic architectures can present significant challenges.</span></span>

<span data-ttu-id="9b3c7-131">時間が経つにつれて、制御が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-131">Over time, you may reach a point where you begin to lose control...</span></span>

- <span data-ttu-id="9b3c7-132">モノリスは、1人のユーザーがそれを理解しなくても、overwhelmingly が複雑になっています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-132">The monolith has become so overwhelmingly complicated that no single person understands it.</span></span>
- <span data-ttu-id="9b3c7-133">それぞれが意図せずコストの高い副作用をもたらすため、変更を加えることになります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-133">You fear making changes as each brings unintended and costly side effects.</span></span>
- <span data-ttu-id="9b3c7-134">新機能と修正プログラムは、時間がかかり、実装にコストがかかるようになります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-134">New features/fixes become time-consuming and expensive to implement.</span></span>
- <span data-ttu-id="9b3c7-135">最小限の変更でも、アプリケーション全体を完全に展開する必要があります (コストとリスクがあります)。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-135">Even the smallest change requires full deployment of the entire application - expensive and risky.</span></span>
- <span data-ttu-id="9b3c7-136">不安定なコンポーネントの1つは、システム全体をクラッシュさせる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-136">One unstable component can crash the entire system.</span></span>
- <span data-ttu-id="9b3c7-137">新しいテクノロジやフレームワークを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-137">Adding new technologies and frameworks aren't an option.</span></span>
- <span data-ttu-id="9b3c7-138">アジャイル配信手法の実装は困難です。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-138">Implementing agile delivery methodologies are difficult.</span></span>
- <span data-ttu-id="9b3c7-139">アーキテクチャ erosion は、をコードベース悪化として設定します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-139">Architectural erosion sets in as the code base deteriorates with never-ending "special cases."</span></span>
- <span data-ttu-id="9b3c7-140">最終的には、コンサルタントが登場し、再作成するように指示されます。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-140">Eventually the consultants come in and tell you to rewrite it.</span></span>

<span data-ttu-id="9b3c7-141">IT 専門家は、この条件 `the Fear Cycle` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-141">IT practitioners call this condition `the Fear Cycle`.</span></span> <span data-ttu-id="9b3c7-142">どのような時間でもテクノロジを使用していた場合は、経験があると思います。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-142">If you've been in the technology business for any length of time, good chance you've experienced it.</span></span> <span data-ttu-id="9b3c7-143">負荷があり、IT 予算を使い果たしています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-143">It's stressful and exhausts your IT budget.</span></span> <span data-ttu-id="9b3c7-144">新しい革新的なソリューションを構築するのではなく、ほとんどの予算をレガシアプリの保守に費やします。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-144">Instead of building new and innovative solutions, most of your budget is spent maintaining legacy apps.</span></span>

<span data-ttu-id="9b3c7-145">心配する必要は `speed and agility` ありません。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-145">Instead of fear, businesses require `speed and agility`.</span></span> <span data-ttu-id="9b3c7-146">彼らは、市場の状況に迅速に対応できるアーキテクチャスタイルを模索しています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-146">They seek an architectural style with which they can rapidly respond to market conditions.</span></span> <span data-ttu-id="9b3c7-147">ライブアプリケーションの小さな領域を瞬時に更新し、個別にスケールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-147">They need to instantaneously update and individually scale small areas of a live application.</span></span>

<span data-ttu-id="9b3c7-148">速度と機敏性を実現するための早期の試みは、 [サービス指向アーキテクチャ](https://en.wikipedia.org/wiki/Service-oriented_architecture)またはの形になりました `SOA` 。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-148">An early attempt to gain speed and agility came in the form of [Service Oriented Architecture](https://en.wikipedia.org/wiki/Service-oriented_architecture), or `SOA`.</span></span> <span data-ttu-id="9b3c7-149">このモデルでは、サービスコンシューマーおよびサービスプロバイダーはミドルウェアメッセージングコンポーネント (多くの場合、 [エンタープライズ Service Bus](https://en.wikipedia.org/wiki/Enterprise_service_bus)と呼ばれます) を介して共同で使用さ `ESB` れます。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-149">In this model, service consumers and service providers collaborated via middleware messaging components, often referred to as an [Enterprise Service Bus](https://en.wikipedia.org/wiki/Enterprise_service_bus), or `ESB`.</span></span> <span data-ttu-id="9b3c7-150">図1-2 にアーキテクチャを示します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-150">Figure 1-2 shows the architecture.</span></span>

![SOA.](./media/the-world-is-distributed/soa-basic.png)

<span data-ttu-id="9b3c7-152">**図 1-2**.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-152">**Figure 1-2**.</span></span> <span data-ttu-id="9b3c7-153">SOA アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-153">SOA architecture.</span></span>

<span data-ttu-id="9b3c7-154">SOA を使用して、ESB に登録された一元化されたサービスプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-154">With SOA, centralized service providers registered with the ESB.</span></span> <span data-ttu-id="9b3c7-155">ビジネスロジックは、プロバイダーとコンシューマーを統合するために ESB に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-155">Business logic would be built into the ESB to integrate providers and consumers.</span></span> <span data-ttu-id="9b3c7-156">サービスコンシューマーは、ESB を使用してこれらのプロバイダーを見つけて通信できます。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-156">Service consumers could then find and communicate with these providers using the ESB.</span></span>

<span data-ttu-id="9b3c7-157">SOA の約束にもかかわらず、多くの場合、このアプローチを実装すると複雑さが増し、ボトルネックが発生します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-157">Despite the promises of SOA, implementing this approach often increased complexity and introduced bottlenecks.</span></span> <span data-ttu-id="9b3c7-158">メンテナンスコストが高くなり、ESB ミドルウェアの負荷が高くなりました。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-158">Maintenance costs became high and ESB middleware expensive.</span></span> <span data-ttu-id="9b3c7-159">サービスは大きくなる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-159">Services tended to be large.</span></span> <span data-ttu-id="9b3c7-160">多くの場合、依存関係とデータストレージが共有されています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-160">They often shared dependencies and data storage.</span></span> <span data-ttu-id="9b3c7-161">最後に、SOAs によって、変更に対する耐性のある一元化されたサービスを含む "分散モノリシック" 構造が発生することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-161">In the end, SOAs often resulted in a 'distributed monolithic' structure with centralized services that were resistant to change.</span></span>

<span data-ttu-id="9b3c7-162">今日、多くの組織は、システムの構築に分散マイクロサービスアーキテクチャアプローチを採用することで、速度と機敏性を実現しています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-162">Nowadays, many organizations have realized speed and agility by adopting a distributed microservice architectural approach to building systems.</span></span> <span data-ttu-id="9b3c7-163">図1-3 は、分散技術およびプラクティスを使用して構築された同じシステムを示しています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-163">Figure 1-3 shows the same system built using distributed techniques and practices.</span></span>

![分散アーキテクチャ。](./media/the-world-is-distributed/distributed-design.png)

<span data-ttu-id="9b3c7-165">**図 1-3**.</span><span class="sxs-lookup"><span data-stu-id="9b3c7-165">**Figure 1-3**.</span></span> <span data-ttu-id="9b3c7-166">分散アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-166">Distributed architecture.</span></span>

<span data-ttu-id="9b3c7-167">分散サービスのセット全体で同じアプリケーションが分解されるしくみに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-167">Note how the same application is decomposed across a set of distributed services.</span></span> <span data-ttu-id="9b3c7-168">各は自己完結型であり、独自のコード、データ、および依存関係をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-168">Each is self-contained and encapsulates its own code, data, and dependencies.</span></span> <span data-ttu-id="9b3c7-169">各は、ソフトウェアコンテナーに展開され、コンテナー orchestrator によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-169">Each is deployed in a software container and managed by a container orchestrator.</span></span> <span data-ttu-id="9b3c7-170">1つのデータベースが複数のサービスで共有されるのではなく、各サービスがプライベートデータベースを所有します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-170">Instead of a single database shared by multiple services, each service owns a private database.</span></span> <span data-ttu-id="9b3c7-171">他のサービスは、このデータベースに直接アクセスできず、それを所有するサービスのパブリック API を介して公開されているデータのみを取得できます。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-171">Other services can't access this database directly and can only get to data that is exposed through the public API of the service that owns it.</span></span> <span data-ttu-id="9b3c7-172">一部のサービスでは、完全なリレーショナルデータベースを必要としますが、他のサービスでは NoSQL データストアを必要とします。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-172">Note how some services require a full relational database, but others, a NoSQL datastore.</span></span> <span data-ttu-id="9b3c7-173">バスケットサービスは、その状態を分散キー/値キャッシュに格納します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-173">The basket service stores its state in a distributed key/value cache.</span></span> <span data-ttu-id="9b3c7-174">受信トラフィックが API ゲートウェイサービス経由でルーティングするしくみに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-174">Note how inbound traffic routes through an API Gateway service.</span></span> <span data-ttu-id="9b3c7-175">サービスへの呼び出しを指示し、横断的な懸念を適用する責任があります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-175">It's responsible for directing calls to  services and enforcing cross-cutting concerns.</span></span> <span data-ttu-id="9b3c7-176">最も重要なのは、アプリケーションは、最新のクラウドプラットフォームで検出されたスケーラビリティ、可用性、回復性の機能を最大限に活用することです。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-176">Most importantly, the application takes full advantage of the scalability, availability, and resiliency features found in modern cloud platforms.</span></span>

<span data-ttu-id="9b3c7-177">しかし、分散サービスは機敏性と速度を提供できますが、さまざまな課題があります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-177">But, while distributed services can provide agility and speed, they present a different set of challenges.</span></span> <span data-ttu-id="9b3c7-178">次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-178">Consider the following...</span></span>

- <span data-ttu-id="9b3c7-179">分散サービスは相互に検出し、同期的に通信するにはどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-179">How can distributed services discover each other and communicate synchronously?</span></span>
- <span data-ttu-id="9b3c7-180">非同期メッセージングを実装するにはどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-180">How can they implement asynchronous messaging?</span></span>
- <span data-ttu-id="9b3c7-181">トランザクション全体でコンテキスト情報を管理するにはどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-181">How can they maintain contextual information across a transaction?</span></span>
- <span data-ttu-id="9b3c7-182">障害に対する回復力はどのようになりますか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-182">How can they become resilient to failure?</span></span>
- <span data-ttu-id="9b3c7-183">変動する需要に合わせて拡張するにはどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-183">How can they scale to meet fluctuating demand?</span></span>
- <span data-ttu-id="9b3c7-184">どのように監視および観察されますか。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-184">How are they monitored and observed?</span></span>

<span data-ttu-id="9b3c7-185">これらの課題については、多くの場合、複数の製品を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-185">For each of these challenges, multiple products are often available.</span></span> <span data-ttu-id="9b3c7-186">しかし、製品の違いからアプリケーションをシールドし、コードの保守性と移植性を維持することは困難になります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-186">But, shielding your application from product differences and keeping code maintainable and portable become a challenge.</span></span>

<span data-ttu-id="9b3c7-187">この書籍では、Dapr が導入されています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-187">This book introduces Dapr.</span></span> <span data-ttu-id="9b3c7-188">Dapr は、分散アプリケーションランタイムです。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-188">Dapr is a distributed application runtime.</span></span> <span data-ttu-id="9b3c7-189">これは、分散アプリケーションと共に発生する多くの課題に直接対応します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-189">It directly addresses many of the challenges found that come along with distributed applications.</span></span> <span data-ttu-id="9b3c7-190">今後、Dapr は、分散アプリケーションの開発に大きな影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-190">Looking ahead, Dapr has the potential to have a profound impact on distributed application development.</span></span>

## <a name="summary"></a><span data-ttu-id="9b3c7-191">まとめ</span><span class="sxs-lookup"><span data-stu-id="9b3c7-191">Summary</span></span>

<span data-ttu-id="9b3c7-192">この章では、分散アプリケーションの導入について説明しました。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-192">In this chapter, we discussed the adoption of distributed applications.</span></span> <span data-ttu-id="9b3c7-193">比較のシステムアプローチは、分散サービスの場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-193">We contrasted a monolithic system approach with that of distributed services.</span></span> <span data-ttu-id="9b3c7-194">分散型のアプローチを検討する際には、一般的な課題の多くを指摘しています。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-194">We pointed out many of the common challenges when considering a distributed approach.</span></span>

<span data-ttu-id="9b3c7-195">ここでは、Dapr の新しい世界を紹介します。</span><span class="sxs-lookup"><span data-stu-id="9b3c7-195">Now, sit back, relax, and let us introduce you the new world of Dapr.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9b3c7-196">[前へ](foreword.md)
>[次へ](dapr-at-20000-feet.md)</span><span class="sxs-lookup"><span data-stu-id="9b3c7-196">[Previous](foreword.md)
[Next](dapr-at-20000-feet.md)</span></span>
