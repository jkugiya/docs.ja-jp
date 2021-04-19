---
title: クラウドネイティブなアプリケーションの概要
description: クラウドネイティブ コンピューティングについて説明します
author: robvet
ms.date: 01/19/2021
ms.openlocfilehash: 852eed27d4cfcaefdfa89a73c54414a6306ed28d
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506098"
---
# <a name="introduction-to-cloud-native-applications"></a><span data-ttu-id="a6aef-103">クラウドネイティブなアプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="a6aef-103">Introduction to cloud-native applications</span></span>

<span data-ttu-id="a6aef-104">ある日、オフィスで "次の大きな仕事" に取り組んでいました。</span><span class="sxs-lookup"><span data-stu-id="a6aef-104">Another day, at the office, working on "the next big thing."</span></span>

<span data-ttu-id="a6aef-105">携帯電話が鳴ります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-105">Your cellphone rings.</span></span> <span data-ttu-id="a6aef-106">親しくしているリクルーターからです。1 日に 2 回、新しい仕事について電話をかけてくる人物です。</span><span class="sxs-lookup"><span data-stu-id="a6aef-106">It's your friendly recruiter - the one who calls you twice a day about new jobs.</span></span>

<span data-ttu-id="a6aef-107">ただし、今回は違います。スタートアップ、株式、多額の資金提供についてです。</span><span class="sxs-lookup"><span data-stu-id="a6aef-107">But this time it's different: Start-up, equity, and plenty of funding.</span></span>

<span data-ttu-id="a6aef-108">クラウドや最先端テクノロジの話を聞いて、あなたはいても立ってもいられなくなります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-108">The mention of the cloud and cutting-edge technology pushes you over the edge.</span></span>

<span data-ttu-id="a6aef-109">その数週間後、あなたは新入社員になり、大規模な e コマース アプリケーションを設計する設計セッションに参加しています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-109">Fast forward a few weeks and you're now a new employee in a design session architecting a major eCommerce application.</span></span> <span data-ttu-id="a6aef-110">大手の e コマース サイトと競合することになります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-110">You're going to compete with the leading eCommerce sites.</span></span>

<span data-ttu-id="a6aef-111">どのように構築すればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a6aef-111">How will you build it?</span></span>

<span data-ttu-id="a6aef-112">過去 15 年間のガイダンスに従うと、おそらく図 1.1 のようなシステムを構築することになるでしょう。</span><span class="sxs-lookup"><span data-stu-id="a6aef-112">If you follow the guidance from past 15 years, you'll most likely build the system shown in Figure 1.1.</span></span>

![従来のモノリシック設計](./media/monolithic-design.png)

<span data-ttu-id="a6aef-114">**(図 1-1)** 。</span><span class="sxs-lookup"><span data-stu-id="a6aef-114">**Figure 1-1**.</span></span> <span data-ttu-id="a6aef-115">従来のモノリシック設計</span><span class="sxs-lookup"><span data-stu-id="a6aef-115">Traditional monolithic design</span></span>

<span data-ttu-id="a6aef-116">すべてのドメイン ロジックを含む大規模なコア アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="a6aef-116">You construct a large core application containing all of your domain logic.</span></span> <span data-ttu-id="a6aef-117">これには、ID、カタログ、注文などのモジュールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-117">It includes modules such as Identity, Catalog, Ordering, and more.</span></span> <span data-ttu-id="a6aef-118">コア アプリは、大規模なリレーショナル データベースと通信します。</span><span class="sxs-lookup"><span data-stu-id="a6aef-118">The core app communicates with a large relational database.</span></span> <span data-ttu-id="a6aef-119">コアの機能は、HTML インターフェイスを介して公開されます。</span><span class="sxs-lookup"><span data-stu-id="a6aef-119">The core exposes functionality via an HTML interface.</span></span>

<span data-ttu-id="a6aef-120">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="a6aef-120">Congratulations!</span></span>  <span data-ttu-id="a6aef-121">これでモノリシック アプリケーションの完成です。</span><span class="sxs-lookup"><span data-stu-id="a6aef-121">You just created a monolithic application.</span></span>

<span data-ttu-id="a6aef-122">すべてが悪いわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a6aef-122">Not all is bad.</span></span> <span data-ttu-id="a6aef-123">モノリスにはいくつかの明確な利点があります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-123">Monoliths offer some distinct advantages.</span></span> <span data-ttu-id="a6aef-124">たとえば、以下のことが簡単です。</span><span class="sxs-lookup"><span data-stu-id="a6aef-124">For example, they're straightforward to...</span></span>

- <span data-ttu-id="a6aef-125">build</span><span class="sxs-lookup"><span data-stu-id="a6aef-125">build</span></span>
- <span data-ttu-id="a6aef-126">テスト</span><span class="sxs-lookup"><span data-stu-id="a6aef-126">test</span></span>
- <span data-ttu-id="a6aef-127">配置 (deploy)</span><span class="sxs-lookup"><span data-stu-id="a6aef-127">deploy</span></span>
- <span data-ttu-id="a6aef-128">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a6aef-128">troubleshoot</span></span>
- <span data-ttu-id="a6aef-129">scale</span><span class="sxs-lookup"><span data-stu-id="a6aef-129">scale</span></span>

<span data-ttu-id="a6aef-130">現存する多くの成功したアプリは、モノリスとして作成されました。</span><span class="sxs-lookup"><span data-stu-id="a6aef-130">Many successful apps that exist today were created as monoliths.</span></span> <span data-ttu-id="a6aef-131">このアプリはヒットし、機能を追加しながら、反復に次ぐ反復で進化し続けています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-131">The app is a hit and continues to evolve, iteration after iteration, adding more functionality.</span></span>

<span data-ttu-id="a6aef-132">ただし、ある時点で違和感を覚えるようになります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-132">At some point, however, you begin to feel uncomfortable.</span></span> <span data-ttu-id="a6aef-133">自分がアプリケーションを制御できていないことに気づくのです。</span><span class="sxs-lookup"><span data-stu-id="a6aef-133">You find yourself losing control of the application.</span></span> <span data-ttu-id="a6aef-134">時間が経つにつれ、その感覚はさらに強くなり、最終的には `Fear Cycle` と呼ばれる状態になります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-134">As time goes on, the feeling becomes more intense and you eventually enter a state known as the `Fear Cycle`.</span></span>

- <span data-ttu-id="a6aef-135">アプリは非常に複雑になり、誰も理解できません。</span><span class="sxs-lookup"><span data-stu-id="a6aef-135">The app has become so overwhelmingly complicated that no single person understands it.</span></span>
- <span data-ttu-id="a6aef-136">変更を加えるのが怖くなります。変更するたびに、意図しない、そしてコストのかかる副作用が生じます。</span><span class="sxs-lookup"><span data-stu-id="a6aef-136">You fear making changes - each change has unintended and costly side effects.</span></span>
- <span data-ttu-id="a6aef-137">新しい機能や修正を実装するのは、厄介で時間がかかり、コストもかかります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-137">New features/fixes become tricky, time-consuming, and expensive to implement.</span></span>
- <span data-ttu-id="a6aef-138">各リリースを最小限に抑えます。また、アプリケーション全体をデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-138">Each release as small as possible and requires a full deployment of the entire application.</span></span>
- <span data-ttu-id="a6aef-139">1 つの不安定なコンポーネントが原因で、システム全体がクラッシュする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-139">One unstable component can crash the entire system.</span></span>
- <span data-ttu-id="a6aef-140">新しいテクノロジやフレームワークは選択肢に入りません。</span><span class="sxs-lookup"><span data-stu-id="a6aef-140">New technologies and frameworks aren't an option.</span></span>
- <span data-ttu-id="a6aef-141">アジャイル配信手法を実装することは困難です。</span><span class="sxs-lookup"><span data-stu-id="a6aef-141">It's difficult to implement agile delivery methodologies.</span></span>
- <span data-ttu-id="a6aef-142">終わりのない "特殊なケース" によってコード ベースが劣化すると、アーキテクチャの侵食が始まります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-142">Architectural erosion sets in as the code base deteriorates with never-ending "special cases."</span></span>
- <span data-ttu-id="a6aef-143">コンサルタントからは書き換えるように指示されます。</span><span class="sxs-lookup"><span data-stu-id="a6aef-143">The consultants tell you to rewrite it.</span></span>

<span data-ttu-id="a6aef-144">多くの企業は、システム構築にクラウドネイティブ アプローチを採用することで、モノリシックの恐怖のサイクルに取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="a6aef-144">Many organizations have addressed the monolithic fear cycle by adopting a cloud-native approach to building systems.</span></span> <span data-ttu-id="a6aef-145">図 1-2 は、クラウドネイティブのテクノロジと手法を適用して構築した同じシステムを示しています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-145">Figure 1-2 shows the same system built applying cloud-native techniques and practices.</span></span>

![クラウドネイティブ設計](./media/cloud-native-design.png)

<span data-ttu-id="a6aef-147">**図 1-2**.</span><span class="sxs-lookup"><span data-stu-id="a6aef-147">**Figure 1-2**.</span></span> <span data-ttu-id="a6aef-148">クラウドネイティブ設計</span><span class="sxs-lookup"><span data-stu-id="a6aef-148">Cloud-native design</span></span>

<span data-ttu-id="a6aef-149">このアプリケーションが、孤立した小さな一連のマイクロサービスにどのように分解されているかに注目してください。</span><span class="sxs-lookup"><span data-stu-id="a6aef-149">Note how the application is decomposed across a set of small isolated microservices.</span></span> <span data-ttu-id="a6aef-150">各サービスは自己完結型であり、独自のコード、データ、依存関係がカプセル化されています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-150">Each service is self-contained and encapsulates its own code, data, and dependencies.</span></span> <span data-ttu-id="a6aef-151">それぞれがソフトウェア コンテナーにデプロイされ、コンテナー オーケストレーターによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="a6aef-151">Each is deployed in a software container and managed by a container orchestrator.</span></span> <span data-ttu-id="a6aef-152">大規模な 1 つのリレーショナル データベースではなく、各サービスは独自のデータ ストアを所有し、その種類はデータのニーズに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-152">Instead of a large relational database, each service owns it own datastore, the type of which vary based upon the data needs.</span></span> <span data-ttu-id="a6aef-153">依存先がリレーショナル データベースのサービスもあれば、NoSQL データベースのものもあります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-153">Note how some services depend on a relational database, but other on NoSQL databases.</span></span> <span data-ttu-id="a6aef-154">分散キャッシュに状態を格納しているサービスもあります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-154">One service stores its state in a distributed cache.</span></span> <span data-ttu-id="a6aef-155">すべてのトラフィックが API Gateway サービスを経由していることに注目してください。これには、コア バックエンド サービスへとトラフィックを誘導し、多くの横断的な懸念事項に対処する役割があります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-155">Note how all traffic routes through an API Gateway service that is responsible for directing traffic to the core back-end services and enforcing many cross-cutting concerns.</span></span> <span data-ttu-id="a6aef-156">最も重要な点は、最新のクラウド プラットフォームに備わっているスケーラビリティ、可用性、回復性の機能をこのアプリケーションから最大限に活用できることです。</span><span class="sxs-lookup"><span data-stu-id="a6aef-156">Most importantly, the application takes full advantage of the scalability, availability, and resiliency features found in modern cloud platforms.</span></span>

### <a name="cloud-native-computing"></a><span data-ttu-id="a6aef-157">クラウドネイティブ コンピューティング</span><span class="sxs-lookup"><span data-stu-id="a6aef-157">Cloud-native computing</span></span>

<span data-ttu-id="a6aef-158">うーん...今、_クラウド ネイティブ_ という用語を使いました。</span><span class="sxs-lookup"><span data-stu-id="a6aef-158">Hmm... We just used the term, _Cloud Native_.</span></span> <span data-ttu-id="a6aef-159">まず、「一体どういう意味だろう。</span><span class="sxs-lookup"><span data-stu-id="a6aef-159">Your first thought might be, "What exactly does that mean?"</span></span> <span data-ttu-id="a6aef-160">またソフトウェア ベンダーが製品を売るために作った業界の流行語かな」などと考えるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="a6aef-160">Another industry buzzword concocted by software vendors to market more stuff?"</span></span>

<span data-ttu-id="a6aef-161">ただし、それはまったく違います。本書を読んで納得していただければ幸いです。</span><span class="sxs-lookup"><span data-stu-id="a6aef-161">Fortunately it's far different and hopefully this book will help convince you.</span></span>

<span data-ttu-id="a6aef-162">クラウド ネイティブは、短期間のうちにソフトウェア業界をけん引するトレンドとなりました。</span><span class="sxs-lookup"><span data-stu-id="a6aef-162">Within a short time, cloud native has become a driving trend in the software industry.</span></span> <span data-ttu-id="a6aef-163">これは、大規模で複雑なシステムを構築するための新しい考え方であり、最新のソフトウェア開発手法、テクノロジ、クラウド インフラストラクチャを最大限に利用するアプローチです。</span><span class="sxs-lookup"><span data-stu-id="a6aef-163">It's a new way to think about building large, complex systems, an approach that takes full advantage of modern software development practices, technologies, and cloud infrastructure.</span></span> <span data-ttu-id="a6aef-164">このアプローチにより、システムの設計、実装、デプロイ、運用の方法が変わります。</span><span class="sxs-lookup"><span data-stu-id="a6aef-164">The approach changes the way you design, implement, deploy, and operationalize systems.</span></span>

<span data-ttu-id="a6aef-165">クラウド ネイティブは、業界をけん引する継続的な誇大広告ではなく、"_現実的なもの_" です。</span><span class="sxs-lookup"><span data-stu-id="a6aef-165">Unlike the continuous hype that drives our industry, cloud native is _for-real_.</span></span> <span data-ttu-id="a6aef-166">[Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF) について考えてみましょう。これは 300 社を超える大手企業が参加するコンソーシアムであり、テクノロジやクラウド スタック全体でクラウドネイティブ コンピューティングを普及させることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-166">Consider the [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), a consortium of over 300 major corporations with a charter to make cloud-native computing ubiquitous across technology and cloud stacks.</span></span> <span data-ttu-id="a6aef-167">最も影響力のあるオープンソース グループの 1 つであり、GitHub で最も急成長しているオープンソース プロジェクトの多くをホストしています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-167">As one of the most influential open-source groups, it hosts many of the fastest-growing open source-projects in GitHub.</span></span> <span data-ttu-id="a6aef-168">その中には、[Kubernetes](https://kubernetes.io/)、[Prometheus](https://prometheus.io/)、[Helm](https://helm.sh/)、[Envoy](https://www.envoyproxy.io/)、[gRPC](https://grpc.io/) などのプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-168">They include projects such as [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [Envoy](https://www.envoyproxy.io/), and [gRPC](https://grpc.io/).</span></span>

<span data-ttu-id="a6aef-169">CNCF は、オープンソースとベンダー中立のエコシステムを促進しています。</span><span class="sxs-lookup"><span data-stu-id="a6aef-169">The CNCF fosters an ecosystem of open-source and vendor-neutrality.</span></span> <span data-ttu-id="a6aef-170">本書はそれに従い、テクノロジにとらわれないクラウドネイティブの原則、パターン、ベスト プラクティスを提示します。</span><span class="sxs-lookup"><span data-stu-id="a6aef-170">Following that lead, this book presents cloud-native principles, patterns, and best practices that are technology agnostic.</span></span> <span data-ttu-id="a6aef-171">同時に、クラウドネイティブ システムを構築するために、Microsoft Azure クラウドで使用できるサービスやインフラストラクチャについても説明します。</span><span class="sxs-lookup"><span data-stu-id="a6aef-171">At the same time, we discuss the services and infrastructure available in the Microsoft Azure cloud for constructing cloud-native systems.</span></span>

<span data-ttu-id="a6aef-172">さて、クラウド ネイティブとは一体何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="a6aef-172">So, what exactly is Cloud Native?</span></span> <span data-ttu-id="a6aef-173">ゆったりくつろいでいてください。この新しい世界の探索をお手伝いします。</span><span class="sxs-lookup"><span data-stu-id="a6aef-173">Sit back, relax, and let us help you explore this new world.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a6aef-174">[前へ](index.md)
>[次へ](definition.md)</span><span class="sxs-lookup"><span data-stu-id="a6aef-174">[Previous](index.md)
[Next](definition.md)</span></span>
