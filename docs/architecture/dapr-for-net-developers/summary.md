---
title: まとめと今後
description: 鍵となる主な結論の概要と、事前に見てみましょう。
ms.date: 02/04/2021
author: robvet
ms.openlocfilehash: c15104f861dd6cfb999d3f67f19b988d1a8ffb03
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401423"
---
# <a name="summary-and-the-road-ahead"></a><span data-ttu-id="b9c05-103">まとめと今後</span><span class="sxs-lookup"><span data-stu-id="b9c05-103">Summary and the road ahead</span></span>

<span data-ttu-id="b9c05-104">私たちは、私たちの Dapr フライトの終わりです。</span><span class="sxs-lookup"><span data-stu-id="b9c05-104">We're at the end of our Dapr flight.</span></span> <span data-ttu-id="b9c05-105">[第2章](dapr-at-20000-feet.md)から2万フィートに飛んでいるジェット機は、最終的なアプローチと着陸に向けています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-105">The jet plane flying at 20,000 feet from [chapter 2](dapr-at-20000-feet.md) is on final approach and about to land.</span></span>

<span data-ttu-id="b9c05-106">プレーンがゲートにタクシーするにつれて、このガイドのいくつかの重要な結論を確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="b9c05-106">As the plane taxis to the gate, let's take a minute to review some important conclusions from this guide:</span></span>

- <span data-ttu-id="b9c05-107">**Dapr** -dapr は、分散アプリケーションの構築方法を合理化する *分散アプリケーションランタイム* です。</span><span class="sxs-lookup"><span data-stu-id="b9c05-107">**Dapr** - Dapr is a *Distributed Application Runtime* that streamlines how you build distributed applications.</span></span> <span data-ttu-id="b9c05-108">これは、構成要素とプラグ可能なコンポーネントのアーキテクチャを公開します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-108">It exposes an architecture of building blocks and pluggable components.</span></span> <span data-ttu-id="b9c05-109">Dapr は、アプリケーションを Dapr ランタイムに存在するインフラストラクチャ機能にバインドする **動的接着** を提供します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-109">Dapr provides a **dynamic glue** that binds your application with infrastructure capabilities that exist in the Dapr runtime.</span></span> <span data-ttu-id="b9c05-110">インフラストラクチャの組み込みを構築する代わりに、お客様とチームはビジネス機能を顧客に提供することに注力しています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-110">Instead of building infrastructure plumbing, you and your team focus on delivering business features to customers.</span></span>

- <span data-ttu-id="b9c05-111">**オープンソースとクロスプラットフォーム** -ネイティブ DAPR API は、HTTP または grpc をサポートする *任意のプラットフォーム* で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9c05-111">**Open source and cross-platform** - The native Dapr API can be consumed by *any platform* that supports HTTP or gRPC.</span></span> <span data-ttu-id="b9c05-112">Dapr には、一般的な開発プラットフォーム向けの言語固有の Sdk も用意されています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-112">Dapr also provides language-specific SDKs for popular development platforms.</span></span> <span data-ttu-id="b9c05-113">Dapr v1.0 では、ゴー、Python、.NET、Java、PHP、および JavaScript がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-113">Dapr v1.0 supports Go, Python, .NET, Java, PHP, and JavaScript.</span></span>

- <span data-ttu-id="b9c05-114">**ビルディングブロック** と dapr ビルディングブロックは、分散アプリケーション機能をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-114">**Building blocks** - Dapr building blocks encapsulate distributed application functionality.</span></span> <span data-ttu-id="b9c05-115">このドキュメントの執筆時点では、Dapr は、図11-1 に示す7つの構成要素をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-115">At the time of this writing, Dapr supports the seven building blocks shown in figure 11-1.</span></span>

![Dapr の構成要素](./media/dapr-at-20000-feet/building-blocks.png)

<span data-ttu-id="b9c05-117">**図 11-1**.</span><span class="sxs-lookup"><span data-stu-id="b9c05-117">**Figure 11-1**.</span></span> <span data-ttu-id="b9c05-118">Dapr のビルディングブロック。</span><span class="sxs-lookup"><span data-stu-id="b9c05-118">Dapr building blocks.</span></span>

- <span data-ttu-id="b9c05-119">**コンポーネント** と dapr コンポーネントは、各 dapr ビルディングブロック機能の具象実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-119">**Components** - Dapr components provide the concrete implementation for each Dapr building block capability.</span></span> <span data-ttu-id="b9c05-120">開発者がアプリケーションコードを変更せずにコンポーネントの実装を交換できる共通のインターフェイスを公開します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-120">They expose a common interface that enables developers to swap out component implementations without changing application code.</span></span> <span data-ttu-id="b9c05-121">図11-2 に、コンポーネント、構成要素、およびサービス間の関係を示します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-121">Figure 11-2 shows the relationship among components, building blocks, and your service.</span></span>

![Dapr 構成ブロックの統合](./media/dapr-at-20000-feet/building-blocks-integration.png)

<span data-ttu-id="b9c05-123">**図 11-2**.</span><span class="sxs-lookup"><span data-stu-id="b9c05-123">**Figure 11-2**.</span></span> <span data-ttu-id="b9c05-124">Dapr ビルディングブロック統合。</span><span class="sxs-lookup"><span data-stu-id="b9c05-124">Dapr building block integration.</span></span>

- <span data-ttu-id="b9c05-125">**サイドカー** は、コンテナーの別個のプロセスとして、sidecars アーキテクチャでアプリケーションと共に実行されます。</span><span class="sxs-lookup"><span data-stu-id="b9c05-125">**Sidecars** - Dapr runs alongside your application in a sidecar architecture, either as a separate process of a container.</span></span> <span data-ttu-id="b9c05-126">アプリケーションは、HTTP と gRPC を介して Dapr Api と通信します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-126">Your application communicates with the Dapr APIs over HTTP and gRPC.</span></span> <span data-ttu-id="b9c05-127">Sidecars、サービスの一部ではなく、接続されているため、分離とカプセル化を提供します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-127">Sidecars provide isolation and encapsulation as they aren't part of the service, but connected to it.</span></span> <span data-ttu-id="b9c05-128">図11-3 は、サイドカーアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-128">Figure 11-3 shows a sidecar architecture.</span></span>

![Sidecar アーキテクチャ](./media/dapr-at-20000-feet/sidecar-generic.png)

<span data-ttu-id="b9c05-130">**図 11-3**. </span><span class="sxs-lookup"><span data-stu-id="b9c05-130">**Figure 11-3**.</span></span> <span data-ttu-id="b9c05-131">Sidecar アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="b9c05-131">Sidecar architecture.</span></span>

- <span data-ttu-id="b9c05-132">**ホスティング環境** Dapr はクロスプラットフォームをサポートしており、複数の環境で実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9c05-132">**Hosting environments** Dapr has cross-platform support and can run in multiple environments.</span></span> <span data-ttu-id="b9c05-133">このドキュメントの執筆時点では、ローカルの自己ホスト型モードと Kubernetes が環境に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-133">At the time of this writing, the environments include a local self-hosted mode and Kubernetes.</span></span>

- <span data-ttu-id="b9c05-134">**eShopOnDapr** -この本には、 [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr)という付属の参照アプリケーションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-134">**eShopOnDapr** - This book includes an accompanying reference application entitled [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr).</span></span> <span data-ttu-id="b9c05-135">一般的な e コマースアプリケーションドメインを使用して、参照アプリケーションは各ビルディングブロックの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b9c05-135">Using a popular e-commerce application domain, the reference application demonstrates the usage of each building block.</span></span> <span data-ttu-id="b9c05-136">これは、数年前にリリースされた広く普及している [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)の進化です。</span><span class="sxs-lookup"><span data-stu-id="b9c05-136">It's an evolution of the widely popular [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers), released several years ago.</span></span>

## <a name="the-road-ahead"></a><span data-ttu-id="b9c05-137">先読み</span><span class="sxs-lookup"><span data-stu-id="b9c05-137">The road ahead</span></span>

<span data-ttu-id="b9c05-138">今後、Dapr は、分散アプリケーションの開発に大きな影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9c05-138">Looking forward, Dapr has the potential to have a profound impact on distributed application development.</span></span> <span data-ttu-id="b9c05-139">Dapr チームとそのオープンソースの共同作成者に期待できることは何ですか。</span><span class="sxs-lookup"><span data-stu-id="b9c05-139">What can you expect from the Dapr team and its open-source contributors?</span></span>

<span data-ttu-id="b9c05-140">このドキュメントの執筆時点では、Dapr に関して提案されている拡張機能の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-140">At the time of writing, the list of proposed enhancements for Dapr include:</span></span>

- <span data-ttu-id="b9c05-141">既存の構成要素に対する機能の強化:</span><span class="sxs-lookup"><span data-stu-id="b9c05-141">Feature enhancements to existing building blocks:</span></span>
  - <span data-ttu-id="b9c05-142">状態管理のクエリ機能により、複数の値を取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b9c05-142">Query capabilities in state management enabling you to retrieve multiple values.</span></span>
  - <span data-ttu-id="b9c05-143">トピック「pub/sub でのフィルター処理」を使用すると、コンテンツに基づいてトピックをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="b9c05-143">Topic filtering in pub/sub enabling you to filter topics based on their content.</span></span>
  - <span data-ttu-id="b9c05-144">可観測性のアプリケーショントレース API。特定のライブラリにバインドすることなく、アプリケーションで直接トレースを提供します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-144">An application tracing API in observability that provides tracing in the application directly without having to bind to specific libraries.</span></span>
  - <span data-ttu-id="b9c05-145">アクタープログラミングモデルにイベントドリブン機能を提供するアクターのバインディングと発行/サブスクライブのサポート。</span><span class="sxs-lookup"><span data-stu-id="b9c05-145">Binding and pub/sub support for actors providing event driven capabilities to the actor programming model.</span></span> <span data-ttu-id="b9c05-146">バインドされたコンポーネントは、イベントをトリガーし、アクター内のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-146">Bound components will trigger events and messages invoke methods in the actor.</span></span>

- <span data-ttu-id="b9c05-147">新しい構成要素:</span><span class="sxs-lookup"><span data-stu-id="b9c05-147">New building blocks:</span></span>
  - <span data-ttu-id="b9c05-148">構成データの読み取りと書き込みを行うための構成 API の構成ブロック。</span><span class="sxs-lookup"><span data-stu-id="b9c05-148">Configuration API building block for reading and writing configuration data.</span></span> <span data-ttu-id="b9c05-149">ブロックは、Azure Configuration Manager または GCP 構成管理を含むプロバイダーにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="b9c05-149">The block will bind to providers that include Azure Configuration Manager or GCP Configuration Management.</span></span>
  - <span data-ttu-id="b9c05-150">Http スケールからゼロへの自動スケール。</span><span class="sxs-lookup"><span data-stu-id="b9c05-150">Http scale-to-zero autoscale.</span></span>
  - <span data-ttu-id="b9c05-151">シングルトンインスタンスを提供し、セマンティック機能をロックするリーダー選択の構成ブロック。</span><span class="sxs-lookup"><span data-stu-id="b9c05-151">Leader election building block to provide singleton instances and locking semantic capabilities.</span></span>
  - <span data-ttu-id="b9c05-152">サービス呼び出し用の透過的なプロキシ構成ブロック。ネットワークレベルで Url または DNS アドレスに基づいてメッセージをルーティングできます。</span><span class="sxs-lookup"><span data-stu-id="b9c05-152">Transparent proxying building block for service invocation, enabling you to route messages based on URLs or DNS addresses at the network level.</span></span>
  - <span data-ttu-id="b9c05-153">回復性の構成ブロック (サーキットブレーカー、バルクヘッド & タイムアウト)。</span><span class="sxs-lookup"><span data-stu-id="b9c05-153">Resiliency building block (circuit breakers, bulkheads & timeouts).</span></span>

- <span data-ttu-id="b9c05-154">フレームワークおよびクラウドネイティブテクノロジとの統合。</span><span class="sxs-lookup"><span data-stu-id="b9c05-154">Integration with frameworks and cloud native technologies.</span></span> <span data-ttu-id="b9c05-155">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="b9c05-155">Some examples include:</span></span>
  - <span data-ttu-id="b9c05-156">Django</span><span class="sxs-lookup"><span data-stu-id="b9c05-156">Django</span></span>
  - <span data-ttu-id="b9c05-157">Nodejs</span><span class="sxs-lookup"><span data-stu-id="b9c05-157">Nodejs</span></span>
  - <span data-ttu-id="b9c05-158">Express</span><span class="sxs-lookup"><span data-stu-id="b9c05-158">Express</span></span>
  - <span data-ttu-id="b9c05-159">Kyma</span><span class="sxs-lookup"><span data-stu-id="b9c05-159">Kyma</span></span>
  - <span data-ttu-id="b9c05-160">中間</span><span class="sxs-lookup"><span data-stu-id="b9c05-160">Midway</span></span>

- <span data-ttu-id="b9c05-161">新しい言語 Sdk:</span><span class="sxs-lookup"><span data-stu-id="b9c05-161">New language SDKs:</span></span>
  - <span data-ttu-id="b9c05-162">JavaScript</span><span class="sxs-lookup"><span data-stu-id="b9c05-162">JavaScript</span></span>
  - <span data-ttu-id="b9c05-163">RUST</span><span class="sxs-lookup"><span data-stu-id="b9c05-163">RUST</span></span>
  - <span data-ttu-id="b9c05-164">C++</span><span class="sxs-lookup"><span data-stu-id="b9c05-164">C++</span></span>

- <span data-ttu-id="b9c05-165">新しいホスティングプラットフォーム:</span><span class="sxs-lookup"><span data-stu-id="b9c05-165">New hosting platforms:</span></span>
  - <span data-ttu-id="b9c05-166">VM</span><span class="sxs-lookup"><span data-stu-id="b9c05-166">VMs</span></span>
  - <span data-ttu-id="b9c05-167">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="b9c05-167">Azure IoT Edge</span></span>
  - <span data-ttu-id="b9c05-168">Azure Stack Edge</span><span class="sxs-lookup"><span data-stu-id="b9c05-168">Azure Stack Edge</span></span>
  - <span data-ttu-id="b9c05-169">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="b9c05-169">Azure Service Fabric</span></span>

- <span data-ttu-id="b9c05-170">開発者およびオペレーターの生産性ツール:</span><span class="sxs-lookup"><span data-stu-id="b9c05-170">Developer and operator productivity tooling:</span></span>
  - <span data-ttu-id="b9c05-171">VS Code 拡張機能。</span><span class="sxs-lookup"><span data-stu-id="b9c05-171">VS Code extension.</span></span>
  - <span data-ttu-id="b9c05-172">DevOps パイプライン開発のローカルデバッグ用のリモート開発コンテナー。</span><span class="sxs-lookup"><span data-stu-id="b9c05-172">Remote Dev Containers for local debugging a DevOps pipeline development.</span></span>
  - <span data-ttu-id="b9c05-173">Dapr アプリケーションを管理する際の運用上の問題をより詳しく把握できるようにする、dapr の運用ダッシュボードの機能強化。</span><span class="sxs-lookup"><span data-stu-id="b9c05-173">Dapr operational dashboard enhancements that will provide deeper visibility into the operational concerns of managing Dapr applications.</span></span>

<span data-ttu-id="b9c05-174">Dapr バージョン1.0 では、開発者は、分散アプリケーションを構築するための説得力のあるツールボックスを利用できます。</span><span class="sxs-lookup"><span data-stu-id="b9c05-174">Dapr version 1.0 provides developers with a compelling toolbox for building distributed applications.</span></span> <span data-ttu-id="b9c05-175">提案された拡張機能リストに示すように、Dapr は多くの新機能を備えたアクティブな開発の下にあります。</span><span class="sxs-lookup"><span data-stu-id="b9c05-175">As the proposed enhancement list shows, Dapr is under active development with many new capabilities to come.</span></span> <span data-ttu-id="b9c05-176">今後の更新については、 [dapr サイト](https://dapr.io/) および [dapr の発表](https://cloudblogs.microsoft.com/opensource/2019/10/16/announcing-dapr-open-source-project-build-microservice-applications/) に関するブログをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b9c05-176">Stay tuned to the [Dapr site](https://dapr.io/) and [Dapr announcement blog](https://cloudblogs.microsoft.com/opensource/2019/10/16/announcing-dapr-open-source-project-build-microservice-applications/) for future updates.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b9c05-177">[[戻る]](secrets.md)</span><span class="sxs-lookup"><span data-stu-id="b9c05-177">[Previous](secrets.md)</span></span>
