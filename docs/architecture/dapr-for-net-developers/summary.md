---
title: まとめと今後
description: Dapr のまとめと今後の展開を示します。
ms.date: 02/17/2021
author: robvet
ms.openlocfilehash: fdbb92d067c29db56aa7449b8fe3c974c8c132b8
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624072"
---
# <a name="summary-and-the-road-ahead"></a><span data-ttu-id="ff5b1-103">まとめと今後</span><span class="sxs-lookup"><span data-stu-id="ff5b1-103">Summary and the road ahead</span></span>

<span data-ttu-id="ff5b1-104">Dapr のフライトも終わりを迎えました。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-104">We're at the end of our Dapr flight.</span></span> <span data-ttu-id="ff5b1-105">[第 2 章](dapr-at-20000-feet.md)から 2 万フィートを飛んだジェット機は最終進入を開始し、着陸しようとしています。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-105">The jet plane flying at 20,000 feet from [chapter 2](dapr-at-20000-feet.md) is on final approach and about to land.</span></span>

<span data-ttu-id="ff5b1-106">機体がゲートに向かっている間に、このガイドのいくつかの重要な結論を確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-106">As the plane taxis to the gate, let's take a minute to review some important conclusions from this guide:</span></span>

- <span data-ttu-id="ff5b1-107">**Dapr** - Dapr は、分散型アプリケーションの構築方法を効率化する *Distributed Application Runtime* です。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-107">**Dapr** - Dapr is a *Distributed Application Runtime* that streamlines how you build distributed applications.</span></span> <span data-ttu-id="ff5b1-108">これは、ビルディング ブロックとプラグ可能なコンポーネントのアーキテクチャを公開します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-108">It exposes an architecture of building blocks and pluggable components.</span></span> <span data-ttu-id="ff5b1-109">Dapr は、Dapr ランタイムに存在するインフラストラクチャ機能にアプリケーションをバインドする **動的な接着剤** を提供します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-109">Dapr provides a **dynamic glue** that binds your application with infrastructure capabilities that exist in the Dapr runtime.</span></span> <span data-ttu-id="ff5b1-110">インフラストラクチャの組み込みを構築する代わりに、ユーザーとチームはビジネス機能を顧客に提供することに注力します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-110">Instead of building infrastructure plumbing, you and your team focus on delivering business features to customers.</span></span>

- <span data-ttu-id="ff5b1-111">**オープンソースとクロスプラットフォーム** - ネイティブの Dapr API は、HTTP または gRPC をサポートする "*任意のプラットフォーム*" で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-111">**Open source and cross-platform** - The native Dapr API can be consumed by *any platform* that supports HTTP or gRPC.</span></span> <span data-ttu-id="ff5b1-112">Dapr には、一般的な開発プラットフォーム向けの言語固有の SDK も用意されています。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-112">Dapr also provides language-specific SDKs for popular development platforms.</span></span> <span data-ttu-id="ff5b1-113">Dapr v1.0 では、Go、Python、.NET、Java、PHP、JavaScript がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-113">Dapr v1.0 supports Go, Python, .NET, Java, PHP, and JavaScript.</span></span>

- <span data-ttu-id="ff5b1-114">**ビルディング ブロック** - Dapr のビルディング ブロックは、分散型アプリケーションの機能をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-114">**Building blocks** - Dapr building blocks encapsulate distributed application functionality.</span></span> <span data-ttu-id="ff5b1-115">このドキュメントの執筆時点では、図 11-1 に示す 7 つのビルディング ブロックが Dapr でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-115">At the time of this writing, Dapr supports the seven building blocks shown in figure 11-1.</span></span>

![Dapr のビルディング ブロック](./media/dapr-at-20000-feet/building-blocks.png)

<span data-ttu-id="ff5b1-117">**図 11-1**.</span><span class="sxs-lookup"><span data-stu-id="ff5b1-117">**Figure 11-1**.</span></span> <span data-ttu-id="ff5b1-118">Dapr のビルディング ブロック。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-118">Dapr building blocks.</span></span>

- <span data-ttu-id="ff5b1-119">**コンポーネント** - Dapr のコンポーネントは、Dapr の各ビルディング ブロック機能の具体的な実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-119">**Components** - Dapr components provide the concrete implementation for each Dapr building block capability.</span></span> <span data-ttu-id="ff5b1-120">また、開発者がアプリケーション コードを変更せずにコンポーネントの実装を交換できる共通のインターフェイスを公開します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-120">They expose a common interface that enables developers to swap out component implementations without changing application code.</span></span> <span data-ttu-id="ff5b1-121">図 11-2 は、コンポーネント、ビルディング ブロック、およびサービス間の関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-121">Figure 11-2 shows the relationship among components, building blocks, and your service.</span></span>

![Dapr のビルディング ブロックの統合](./media/dapr-at-20000-feet/building-blocks-integration.png)

<span data-ttu-id="ff5b1-123">**図 11-2**.</span><span class="sxs-lookup"><span data-stu-id="ff5b1-123">**Figure 11-2**.</span></span> <span data-ttu-id="ff5b1-124">Dapr のビルディング ブロックの統合。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-124">Dapr building block integration.</span></span>

- <span data-ttu-id="ff5b1-125">**サイドカー** - Dapr は、コンテナーの個別のプロセスとして、サイドカー アーキテクチャでアプリケーションと共に実行されます。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-125">**Sidecars** - Dapr runs alongside your application in a sidecar architecture, either as a separate process of a container.</span></span> <span data-ttu-id="ff5b1-126">アプリケーションは、HTTP と gRPC を使用して Dapr API と通信します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-126">Your application communicates with the Dapr APIs over HTTP and gRPC.</span></span> <span data-ttu-id="ff5b1-127">サイドカーはサービスの一部ではなく、サービスに接続されているため、分離とカプセル化が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-127">Sidecars provide isolation and encapsulation as they aren't part of the service, but connected to it.</span></span> <span data-ttu-id="ff5b1-128">図 11-3 は、サイドカー アーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-128">Figure 11-3 shows a sidecar architecture.</span></span>

![サイドカー アーキテクチャ](./media/dapr-at-20000-feet/sidecar-generic.png)

<span data-ttu-id="ff5b1-130">**図 11-3**. </span><span class="sxs-lookup"><span data-stu-id="ff5b1-130">**Figure 11-3**.</span></span> <span data-ttu-id="ff5b1-131">サイドカー アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-131">Sidecar architecture.</span></span>

- <span data-ttu-id="ff5b1-132">**ホスティング環境** - Dapr はクロスプラットフォームをサポートしており、複数の環境で実行できます。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-132">**Hosting environments** Dapr has cross-platform support and can run in multiple environments.</span></span> <span data-ttu-id="ff5b1-133">このドキュメントの執筆時点で対象となる環境は、ローカルのセルフホステッド モードと Kubernetes です。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-133">At the time of this writing, the environments include a local self-hosted mode and Kubernetes.</span></span>

- <span data-ttu-id="ff5b1-134">**eShopOnDapr** - 本書には、[eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) という参照アプリケーションが付属しています。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-134">**eShopOnDapr** - This book includes an accompanying reference application entitled [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr).</span></span> <span data-ttu-id="ff5b1-135">この参照アプリケーションでは、一般的な eコマース アプリケーション ドメインを使用して、各ビルディング ブロックの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-135">Using a popular e-commerce application domain, the reference application demonstrates the usage of each building block.</span></span> <span data-ttu-id="ff5b1-136">これは、数年前にリリースされ、広く普及している [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) を進化させたものです。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-136">It's an evolution of the widely popular [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers), released several years ago.</span></span>

## <a name="the-road-ahead"></a><span data-ttu-id="ff5b1-137">今後の展開</span><span class="sxs-lookup"><span data-stu-id="ff5b1-137">The road ahead</span></span>

<span data-ttu-id="ff5b1-138">今後 Dapr は、分散型アプリケーションの開発に大きな影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-138">Looking forward, Dapr has the potential to have a profound impact on distributed application development.</span></span> <span data-ttu-id="ff5b1-139">Dapr チームとそのオープンソースの共同作成者に期待することは何でしょう。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-139">What can you expect from the Dapr team and its open-source contributors?</span></span>

<span data-ttu-id="ff5b1-140">このドキュメントの執筆時点で、Dapr に関して提案されている機能強化の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-140">At the time of writing, the list of proposed enhancements for Dapr include:</span></span>

- <span data-ttu-id="ff5b1-141">既存のビルディング ブロックに対する機能の強化:</span><span class="sxs-lookup"><span data-stu-id="ff5b1-141">Feature enhancements to existing building blocks:</span></span>
  - <span data-ttu-id="ff5b1-142">状態管理におけるクエリ機能 - 複数の値を取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-142">Query capabilities in state management enabling you to retrieve multiple values.</span></span>
  - <span data-ttu-id="ff5b1-143">パブリッシュ/サブスクライブにおけるトピック フィルタリング - コンテンツに基づいてトピックをフィルター処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-143">Topic filtering in pub/sub enabling you to filter topics based on their content.</span></span>
  - <span data-ttu-id="ff5b1-144">監視におけるアプリケーション トレース API - 特定のライブラリにバインドすることなく、アプリケーションで直接トレースを提供します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-144">An application tracing API in observability that provides tracing in the application directly without having to bind to specific libraries.</span></span>
  - <span data-ttu-id="ff5b1-145">アクターのバインディングとパブリッシュ/サブスクライブのサポート - アクター プログラミング モデルに対してイベント ドリブン機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-145">Binding and pub/sub support for actors providing event driven capabilities to the actor programming model.</span></span> <span data-ttu-id="ff5b1-146">バインドされたコンポーネントはイベントをトリガーし、メッセージはアクター内のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-146">Bound components will trigger events and messages invoke methods in the actor.</span></span>

- <span data-ttu-id="ff5b1-147">新しいビルディング ブロック:</span><span class="sxs-lookup"><span data-stu-id="ff5b1-147">New building blocks:</span></span>
  - <span data-ttu-id="ff5b1-148">構成データの読み取りと書き込みを行うための構成 API ビルディング ブロック。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-148">Configuration API building block for reading and writing configuration data.</span></span> <span data-ttu-id="ff5b1-149">このブロックは、Azure 構成マネージャーまたは GCP 構成管理を含むプロバイダーにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-149">The block will bind to providers that include Azure Configuration Manager or GCP Configuration Management.</span></span>
  - <span data-ttu-id="ff5b1-150">HTTP のゼロまでのスケーリングによる自動スケーリング。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-150">Http scale-to-zero autoscale.</span></span>
  - <span data-ttu-id="ff5b1-151">シングルトン インスタンスとセマンティック機能のロックを提供するリーダー選挙ビルディング ブロック。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-151">Leader election building block to provide singleton instances and locking semantic capabilities.</span></span>
  - <span data-ttu-id="ff5b1-152">サービス呼び出し用の透過プロキシ ビルディング ブロック。ネットワーク レベルで URL または DNS アドレスに基づいてメッセージをルーティングできるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-152">Transparent proxying building block for service invocation, enabling you to route messages based on URLs or DNS addresses at the network level.</span></span>
  - <span data-ttu-id="ff5b1-153">回復性ビルディング ブロック (サーキット ブレーカー、バルクヘッド、タイムアウト)。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-153">Resiliency building block (circuit breakers, bulkheads & timeouts).</span></span>

- <span data-ttu-id="ff5b1-154">フレームワークおよびクラウドネイティブ テクノロジとの統合。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-154">Integration with frameworks and cloud native technologies.</span></span> <span data-ttu-id="ff5b1-155">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-155">Some examples include:</span></span>
  - <span data-ttu-id="ff5b1-156">Django</span><span class="sxs-lookup"><span data-stu-id="ff5b1-156">Django</span></span>
  - <span data-ttu-id="ff5b1-157">Nodejs</span><span class="sxs-lookup"><span data-stu-id="ff5b1-157">Nodejs</span></span>
  - <span data-ttu-id="ff5b1-158">Express</span><span class="sxs-lookup"><span data-stu-id="ff5b1-158">Express</span></span>
  - <span data-ttu-id="ff5b1-159">Kyma</span><span class="sxs-lookup"><span data-stu-id="ff5b1-159">Kyma</span></span>
  - <span data-ttu-id="ff5b1-160">Midway</span><span class="sxs-lookup"><span data-stu-id="ff5b1-160">Midway</span></span>

- <span data-ttu-id="ff5b1-161">新しい言語 SDK:</span><span class="sxs-lookup"><span data-stu-id="ff5b1-161">New language SDKs:</span></span>
  - <span data-ttu-id="ff5b1-162">JavaScript</span><span class="sxs-lookup"><span data-stu-id="ff5b1-162">JavaScript</span></span>
  - <span data-ttu-id="ff5b1-163">RUST</span><span class="sxs-lookup"><span data-stu-id="ff5b1-163">RUST</span></span>
  - <span data-ttu-id="ff5b1-164">C++</span><span class="sxs-lookup"><span data-stu-id="ff5b1-164">C++</span></span>

- <span data-ttu-id="ff5b1-165">新しいホスティング プラットフォーム:</span><span class="sxs-lookup"><span data-stu-id="ff5b1-165">New hosting platforms:</span></span>
  - <span data-ttu-id="ff5b1-166">VM</span><span class="sxs-lookup"><span data-stu-id="ff5b1-166">VMs</span></span>
  - <span data-ttu-id="ff5b1-167">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="ff5b1-167">Azure IoT Edge</span></span>
  - <span data-ttu-id="ff5b1-168">Azure Stack Edge</span><span class="sxs-lookup"><span data-stu-id="ff5b1-168">Azure Stack Edge</span></span>
  - <span data-ttu-id="ff5b1-169">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="ff5b1-169">Azure Service Fabric</span></span>

- <span data-ttu-id="ff5b1-170">開発者とオペレーター向けの生産性ツール:</span><span class="sxs-lookup"><span data-stu-id="ff5b1-170">Developer and operator productivity tooling:</span></span>
  - <span data-ttu-id="ff5b1-171">VS Code 拡張機能。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-171">VS Code extension.</span></span>
  - <span data-ttu-id="ff5b1-172">DevOps パイプライン開発のローカル デバッグ用のリモート開発コンテナー。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-172">Remote Dev Containers for local debugging a DevOps pipeline development.</span></span>
  - <span data-ttu-id="ff5b1-173">Dapr アプリケーションの管理に関する運用上の問題を詳細に可視化できるようにする Dapr の操作ダッシュボードの機能強化。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-173">Dapr operational dashboard enhancements that will provide deeper visibility into the operational concerns of managing Dapr applications.</span></span>

<span data-ttu-id="ff5b1-174">Dapr バージョン 1.0 には、開発者が分散型アプリケーションを構築するための魅力的なツールボックスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-174">Dapr version 1.0 provides developers with a compelling toolbox for building distributed applications.</span></span> <span data-ttu-id="ff5b1-175">提案されている機能強化の一覧に示すとおり、多くの新機能と共に Dapr の開発は積極的に進められています。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-175">As the proposed enhancement list shows, Dapr is under active development with many new capabilities to come.</span></span> <span data-ttu-id="ff5b1-176">今後の更新予定については、[Dapr のサイト](https://dapr.io/)および [Dapr の公式発表に関するブログ](https://cloudblogs.microsoft.com/opensource/2019/10/16/announcing-dapr-open-source-project-build-microservice-applications/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff5b1-176">Stay tuned to the [Dapr site](https://dapr.io/) and [Dapr announcement blog](https://cloudblogs.microsoft.com/opensource/2019/10/16/announcing-dapr-open-source-project-build-microservice-applications/) for future updates.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ff5b1-177">[[戻る]](secrets.md)</span><span class="sxs-lookup"><span data-stu-id="ff5b1-177">[Previous](secrets.md)</span></span>
