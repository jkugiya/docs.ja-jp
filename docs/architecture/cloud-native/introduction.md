---
title: クラウドネイティブなアプリケーションの概要
description: クラウドネイティブコンピューティングについて
author: robvet
ms.date: 01/19/2021
ms.openlocfilehash: 852eed27d4cfcaefdfa89a73c54414a6306ed28d
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506098"
---
# <a name="introduction-to-cloud-native-applications"></a><span data-ttu-id="8da98-103">クラウドネイティブなアプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="8da98-103">Introduction to cloud-native applications</span></span>

<span data-ttu-id="8da98-104">もう1日、オフィスでは、「次の大きなこと」に取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="8da98-104">Another day, at the office, working on "the next big thing."</span></span>

<span data-ttu-id="8da98-105">Cellphone リング。</span><span class="sxs-lookup"><span data-stu-id="8da98-105">Your cellphone rings.</span></span> <span data-ttu-id="8da98-106">お客様のフレンドリな採用者です。新しいジョブについて1日に2回呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8da98-106">It's your friendly recruiter - the one who calls you twice a day about new jobs.</span></span>

<span data-ttu-id="8da98-107">しかし、今回は、開始、資本、および大量の資金調達も異なります。</span><span class="sxs-lookup"><span data-stu-id="8da98-107">But this time it's different: Start-up, equity, and plenty of funding.</span></span>

<span data-ttu-id="8da98-108">クラウドと最先端のテクノロジについては、エッジに対してお話しします。</span><span class="sxs-lookup"><span data-stu-id="8da98-108">The mention of the cloud and cutting-edge technology pushes you over the edge.</span></span>

<span data-ttu-id="8da98-109">数週間後、設計セッションの新しい従業員が、主要な e コマースアプリケーションを設計しています。</span><span class="sxs-lookup"><span data-stu-id="8da98-109">Fast forward a few weeks and you're now a new employee in a design session architecting a major eCommerce application.</span></span> <span data-ttu-id="8da98-110">お客様は、大手 e コマースサイトと競争します。</span><span class="sxs-lookup"><span data-stu-id="8da98-110">You're going to compete with the leading eCommerce sites.</span></span>

<span data-ttu-id="8da98-111">どのようにしてビルドするのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="8da98-111">How will you build it?</span></span>

<span data-ttu-id="8da98-112">15年前のガイダンスに従っている場合は、図1.1 に示すシステムが構築される可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="8da98-112">If you follow the guidance from past 15 years, you'll most likely build the system shown in Figure 1.1.</span></span>

![従来のモノリシック設計](./media/monolithic-design.png)

<span data-ttu-id="8da98-114">**(図 1-1)** 。</span><span class="sxs-lookup"><span data-stu-id="8da98-114">**Figure 1-1**.</span></span> <span data-ttu-id="8da98-115">従来のモノリシック設計</span><span class="sxs-lookup"><span data-stu-id="8da98-115">Traditional monolithic design</span></span>

<span data-ttu-id="8da98-116">すべてのドメインロジックを含む大規模なコアアプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="8da98-116">You construct a large core application containing all of your domain logic.</span></span> <span data-ttu-id="8da98-117">これには、Id、カタログ、順序付けなどのモジュールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8da98-117">It includes modules such as Identity, Catalog, Ordering, and more.</span></span> <span data-ttu-id="8da98-118">コアアプリは、大規模なリレーショナルデータベースと通信します。</span><span class="sxs-lookup"><span data-stu-id="8da98-118">The core app communicates with a large relational database.</span></span> <span data-ttu-id="8da98-119">コアは、HTML インターフェイスを介して機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="8da98-119">The core exposes functionality via an HTML interface.</span></span>

<span data-ttu-id="8da98-120">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="8da98-120">Congratulations!</span></span>  <span data-ttu-id="8da98-121">モノリシックアプリケーションを作成したばかりです。</span><span class="sxs-lookup"><span data-stu-id="8da98-121">You just created a monolithic application.</span></span>

<span data-ttu-id="8da98-122">すべてが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="8da98-122">Not all is bad.</span></span> <span data-ttu-id="8da98-123">モノリスには、いくつかの異なる利点があります。</span><span class="sxs-lookup"><span data-stu-id="8da98-123">Monoliths offer some distinct advantages.</span></span> <span data-ttu-id="8da98-124">たとえば、次のように簡単です。</span><span class="sxs-lookup"><span data-stu-id="8da98-124">For example, they're straightforward to...</span></span>

- <span data-ttu-id="8da98-125">build</span><span class="sxs-lookup"><span data-stu-id="8da98-125">build</span></span>
- <span data-ttu-id="8da98-126">テスト</span><span class="sxs-lookup"><span data-stu-id="8da98-126">test</span></span>
- <span data-ttu-id="8da98-127">配置 (deploy)</span><span class="sxs-lookup"><span data-stu-id="8da98-127">deploy</span></span>
- <span data-ttu-id="8da98-128">解決</span><span class="sxs-lookup"><span data-stu-id="8da98-128">troubleshoot</span></span>
- <span data-ttu-id="8da98-129">scale</span><span class="sxs-lookup"><span data-stu-id="8da98-129">scale</span></span>

<span data-ttu-id="8da98-130">現在存在する正常なアプリの多くはモノリスとして作成されました。</span><span class="sxs-lookup"><span data-stu-id="8da98-130">Many successful apps that exist today were created as monoliths.</span></span> <span data-ttu-id="8da98-131">アプリはヒットし、継続的に進化し続け、イテレーション後に反復処理を行い、機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="8da98-131">The app is a hit and continues to evolve, iteration after iteration, adding more functionality.</span></span>

<span data-ttu-id="8da98-132">しかし、ある時点で不快感を感じ始めます。</span><span class="sxs-lookup"><span data-stu-id="8da98-132">At some point, however, you begin to feel uncomfortable.</span></span> <span data-ttu-id="8da98-133">アプリケーションの制御が失われていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8da98-133">You find yourself losing control of the application.</span></span> <span data-ttu-id="8da98-134">時間が入ると、気がより大きくなり、最終的にはと呼ばれる状態に `Fear Cycle` なります。</span><span class="sxs-lookup"><span data-stu-id="8da98-134">As time goes on, the feeling becomes more intense and you eventually enter a state known as the `Fear Cycle`.</span></span>

- <span data-ttu-id="8da98-135">アプリが非常に複雑になり、1人のユーザーがそれを理解することは overwhelmingly ありません。</span><span class="sxs-lookup"><span data-stu-id="8da98-135">The app has become so overwhelmingly complicated that no single person understands it.</span></span>
- <span data-ttu-id="8da98-136">変更を懸念しています。変更は、意図せず、コストのかかる副作用があります。</span><span class="sxs-lookup"><span data-stu-id="8da98-136">You fear making changes - each change has unintended and costly side effects.</span></span>
- <span data-ttu-id="8da98-137">新機能と修正プログラムは、複雑になり、時間がかかり、実装にコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="8da98-137">New features/fixes become tricky, time-consuming, and expensive to implement.</span></span>
- <span data-ttu-id="8da98-138">各リリースは可能な限り小さく、アプリケーション全体を完全に展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8da98-138">Each release as small as possible and requires a full deployment of the entire application.</span></span>
- <span data-ttu-id="8da98-139">不安定なコンポーネントの1つは、システム全体をクラッシュさせる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8da98-139">One unstable component can crash the entire system.</span></span>
- <span data-ttu-id="8da98-140">新しいテクノロジとフレームワークはオプションではありません。</span><span class="sxs-lookup"><span data-stu-id="8da98-140">New technologies and frameworks aren't an option.</span></span>
- <span data-ttu-id="8da98-141">アジャイル配信方法論を実装することは困難です。</span><span class="sxs-lookup"><span data-stu-id="8da98-141">It's difficult to implement agile delivery methodologies.</span></span>
- <span data-ttu-id="8da98-142">アーキテクチャ erosion は、をコードベース悪化として設定します。</span><span class="sxs-lookup"><span data-stu-id="8da98-142">Architectural erosion sets in as the code base deteriorates with never-ending "special cases."</span></span>
- <span data-ttu-id="8da98-143">コンサルタントによって、再作成するように指示されます。</span><span class="sxs-lookup"><span data-stu-id="8da98-143">The consultants tell you to rewrite it.</span></span>

<span data-ttu-id="8da98-144">多くの組織は、システムを構築するためのクラウドネイティブアプローチを採用することで、モノリシックな懸念サイクルに取り組んできました。</span><span class="sxs-lookup"><span data-stu-id="8da98-144">Many organizations have addressed the monolithic fear cycle by adopting a cloud-native approach to building systems.</span></span> <span data-ttu-id="8da98-145">図1-2 は、クラウドネイティブの手法とプラクティスを適用して構築された同じシステムを示しています。</span><span class="sxs-lookup"><span data-stu-id="8da98-145">Figure 1-2 shows the same system built applying cloud-native techniques and practices.</span></span>

![Cloud-Native の設計](./media/cloud-native-design.png)

<span data-ttu-id="8da98-147">**図 1-2**.</span><span class="sxs-lookup"><span data-stu-id="8da98-147">**Figure 1-2**.</span></span> <span data-ttu-id="8da98-148">クラウドネイティブ設計</span><span class="sxs-lookup"><span data-stu-id="8da98-148">Cloud-native design</span></span>

<span data-ttu-id="8da98-149">小さな分離マイクロサービスのセットにわたってアプリケーションがどのように分解されるかに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8da98-149">Note how the application is decomposed across a set of small isolated microservices.</span></span> <span data-ttu-id="8da98-150">各サービスは自己完結型であり、独自のコード、データ、および依存関係をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="8da98-150">Each service is self-contained and encapsulates its own code, data, and dependencies.</span></span> <span data-ttu-id="8da98-151">各は、ソフトウェアコンテナーに展開され、コンテナー orchestrator によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="8da98-151">Each is deployed in a software container and managed by a container orchestrator.</span></span> <span data-ttu-id="8da98-152">大規模なリレーショナルデータベースの代わりに、各サービスが独自のデータストアを所有しています。この種類は、データのニーズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="8da98-152">Instead of a large relational database, each service owns it own datastore, the type of which vary based upon the data needs.</span></span> <span data-ttu-id="8da98-153">一部のサービスはリレーショナルデータベースに依存しますが、他のサービスは NoSQL データベースに依存します。</span><span class="sxs-lookup"><span data-stu-id="8da98-153">Note how some services depend on a relational database, but other on NoSQL databases.</span></span> <span data-ttu-id="8da98-154">1つのサービスでは、その状態が分散キャッシュに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8da98-154">One service stores its state in a distributed cache.</span></span> <span data-ttu-id="8da98-155">すべてのトラフィックが、コアバックエンドサービスへのトラフィックの転送を担当する API ゲートウェイサービスを介してルーティングされ、さまざまな横断的懸念が適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8da98-155">Note how all traffic routes through an API Gateway service that is responsible for directing traffic to the core back-end services and enforcing many cross-cutting concerns.</span></span> <span data-ttu-id="8da98-156">最も重要なのは、アプリケーションは、最新のクラウドプラットフォームで検出されたスケーラビリティ、可用性、回復性の機能を最大限に活用することです。</span><span class="sxs-lookup"><span data-stu-id="8da98-156">Most importantly, the application takes full advantage of the scalability, availability, and resiliency features found in modern cloud platforms.</span></span>

### <a name="cloud-native-computing"></a><span data-ttu-id="8da98-157">クラウドネイティブコンピューティング</span><span class="sxs-lookup"><span data-stu-id="8da98-157">Cloud-native computing</span></span>

<span data-ttu-id="8da98-158">んん。。。ここでは、 _クラウドネイティブ_ という用語を使用していました。</span><span class="sxs-lookup"><span data-stu-id="8da98-158">Hmm... We just used the term, _Cloud Native_.</span></span> <span data-ttu-id="8da98-159">最初に考えられるのは、"何を意味するのでしょうか" ということです。</span><span class="sxs-lookup"><span data-stu-id="8da98-159">Your first thought might be, "What exactly does that mean?"</span></span> <span data-ttu-id="8da98-160">もう1つの業界流行 concocted は、ソフトウェアベンダーによってさらに市場を拡大しています。」</span><span class="sxs-lookup"><span data-stu-id="8da98-160">Another industry buzzword concocted by software vendors to market more stuff?"</span></span>

<span data-ttu-id="8da98-161">幸いなことに、この書籍はお客様を説得するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8da98-161">Fortunately it's far different and hopefully this book will help convince you.</span></span>

<span data-ttu-id="8da98-162">クラウドのネイティブは、ソフトウェア業界の推進傾向になっています。</span><span class="sxs-lookup"><span data-stu-id="8da98-162">Within a short time, cloud native has become a driving trend in the software industry.</span></span> <span data-ttu-id="8da98-163">これは、大規模で複雑なシステムを構築するための新しい方法であり、最新のソフトウェア開発プラクティス、テクノロジ、およびクラウドインフラストラクチャを最大限に活用するアプローチです。</span><span class="sxs-lookup"><span data-stu-id="8da98-163">It's a new way to think about building large, complex systems, an approach that takes full advantage of modern software development practices, technologies, and cloud infrastructure.</span></span> <span data-ttu-id="8da98-164">このアプローチは、システムの設計、実装、展開、および運用化の方法を変更します。</span><span class="sxs-lookup"><span data-stu-id="8da98-164">The approach changes the way you design, implement, deploy, and operationalize systems.</span></span>

<span data-ttu-id="8da98-165">業界を促進する継続的な誇大広告とは異なり、クラウド _の_ ネイティブはを対象としています。</span><span class="sxs-lookup"><span data-stu-id="8da98-165">Unlike the continuous hype that drives our industry, cloud native is _for-real_.</span></span> <span data-ttu-id="8da98-166">クラウドネイティブコンピューティングをテクノロジとクラウドスタック全体で広く利用できるようにするために、300の主要企業のコンソーシアムである [クラウドネイティブコンピューティングファンデーション](https://www.cncf.io/) (cncf) について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="8da98-166">Consider the [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), a consortium of over 300 major corporations with a charter to make cloud-native computing ubiquitous across technology and cloud stacks.</span></span> <span data-ttu-id="8da98-167">最も影響力の高いオープンソースグループの1つとして、GitHub で急速に成長するオープンソースプロジェクトの多くをホストしています。</span><span class="sxs-lookup"><span data-stu-id="8da98-167">As one of the most influential open-source groups, it hosts many of the fastest-growing open source-projects in GitHub.</span></span> <span data-ttu-id="8da98-168">これには、 [Kubernetes](https://kubernetes.io/)、 [prometheus](https://prometheus.io/)、 [ヘルム](https://helm.sh/)、 [エンボイ](https://www.envoyproxy.io/)、 [grpc](https://grpc.io/)などのプロジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8da98-168">They include projects such as [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [Envoy](https://www.envoyproxy.io/), and [gRPC](https://grpc.io/).</span></span>

<span data-ttu-id="8da98-169">CNCF は、オープンソースとベンダーニュートラルのエコシステムを促進します。</span><span class="sxs-lookup"><span data-stu-id="8da98-169">The CNCF fosters an ecosystem of open-source and vendor-neutrality.</span></span> <span data-ttu-id="8da98-170">この書籍では、クラウドネイティブの原則、パターン、およびテクノロジに依存しないベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8da98-170">Following that lead, this book presents cloud-native principles, patterns, and best practices that are technology agnostic.</span></span> <span data-ttu-id="8da98-171">同時に、クラウドネイティブシステムを構築するために Microsoft Azure クラウドで利用できるサービスとインフラストラクチャについても説明します。</span><span class="sxs-lookup"><span data-stu-id="8da98-171">At the same time, we discuss the services and infrastructure available in the Microsoft Azure cloud for constructing cloud-native systems.</span></span>

<span data-ttu-id="8da98-172">クラウドネイティブとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="8da98-172">So, what exactly is Cloud Native?</span></span> <span data-ttu-id="8da98-173">戻ってリラックスし、この新しい世界を探検してみてください。</span><span class="sxs-lookup"><span data-stu-id="8da98-173">Sit back, relax, and let us help you explore this new world.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8da98-174">[前へ](index.md)
>[次へ](definition.md)</span><span class="sxs-lookup"><span data-stu-id="8da98-174">[Previous](index.md)
[Next](definition.md)</span></span>
