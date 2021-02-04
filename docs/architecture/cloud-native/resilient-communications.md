---
title: 回復性のある通信
description: Azure 向けのクラウドネイティブ .NET アプリの設計 |回復力のある通信
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 52f08c066767175c699f5a058267cb42d2b1d4aa
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99547695"
---
# <a name="resilient-communications"></a><span data-ttu-id="44a9f-103">回復力のある通信</span><span class="sxs-lookup"><span data-stu-id="44a9f-103">Resilient communications</span></span>

<span data-ttu-id="44a9f-104">この書籍全体で、マイクロサービスベースのアーキテクチャアプローチを採用しています。</span><span class="sxs-lookup"><span data-stu-id="44a9f-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="44a9f-105">このアーキテクチャには重要な利点がありますが、多くの課題があります。</span><span class="sxs-lookup"><span data-stu-id="44a9f-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="44a9f-106">*プロセス外のネットワーク通信。*</span><span class="sxs-lookup"><span data-stu-id="44a9f-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="44a9f-107">各マイクロサービスはネットワークプロトコルを介して通信し、ネットワークの輻輳、待機時間、および一時的な障害を発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="44a9f-108">*サービス検出。*</span><span class="sxs-lookup"><span data-stu-id="44a9f-108">*Service discovery.*</span></span> <span data-ttu-id="44a9f-109">異なる IP アドレスとポートを持つマシンのクラスターで実行している場合、マイクロサービスはどのようにして互いを検出し、相互に通信しますか。</span><span class="sxs-lookup"><span data-stu-id="44a9f-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="44a9f-110">*柔軟性.*</span><span class="sxs-lookup"><span data-stu-id="44a9f-110">*Resiliency.*</span></span> <span data-ttu-id="44a9f-111">短時間の障害を管理し、システムの安定性を維持するにはどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="44a9f-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="44a9f-112">*負荷分散。*</span><span class="sxs-lookup"><span data-stu-id="44a9f-112">*Load balancing.*</span></span> <span data-ttu-id="44a9f-113">受信トラフィックは、マイクロサービスの複数のインスタンスにどのように分散されるのですか。</span><span class="sxs-lookup"><span data-stu-id="44a9f-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="44a9f-114">*セキュリティ。*</span><span class="sxs-lookup"><span data-stu-id="44a9f-114">*Security.*</span></span> <span data-ttu-id="44a9f-115">トランスポートレベルの暗号化と証明書の管理などのセキュリティの問題はどのように適用されますか。</span><span class="sxs-lookup"><span data-stu-id="44a9f-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="44a9f-116">*分散型監視。*</span><span class="sxs-lookup"><span data-stu-id="44a9f-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="44a9f-117">-複数のマイクロサービスにまたがる1つの要求について、追跡可能性と監視を相互に関連付けてキャプチャする方法を教えてください。</span><span class="sxs-lookup"><span data-stu-id="44a9f-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="44a9f-118">さまざまなライブラリやフレームワークでこれらの問題に対処できますが、実装はコストが高く、複雑で、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="44a9f-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="44a9f-119">また、インフラストラクチャに関する懸念事項をビジネスロジックと組み合わせることもできます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="44a9f-120">サービスメッシュ</span><span class="sxs-lookup"><span data-stu-id="44a9f-120">Service mesh</span></span>

<span data-ttu-id="44a9f-121">より優れたアプローチは、 *サービスメッシュ* を利用する進化テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="44a9f-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="44a9f-122">[サービスメッシュ](https://www.nginx.com/blog/what-is-a-service-mesh/)は、構成可能なインフラストラクチャレイヤーであり、サービスの通信と上記の他の課題に対処するための組み込みの機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="44a9f-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="44a9f-123">これらの問題は、サービスプロキシに移動することで分離されます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="44a9f-124">プロキシは、ビジネスコードから分離するために、別のプロセス (サイド [カーと呼ばれます) に](/azure/architecture/patterns/sidecar)展開されます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-124">The proxy is deployed into a separate process (called a [sidecar](/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="44a9f-125">ただし、サイドカーはサービスにリンクされており、それを使用して作成され、ライフサイクルを共有します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="44a9f-126">図6-7 はこのシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="44a9f-126">Figure 6-7 shows this scenario.</span></span>

![サイドカーを使用したサービスメッシュ](./media/service-mesh-with-side-car.png)

<span data-ttu-id="44a9f-128">**図 6-7**。</span><span class="sxs-lookup"><span data-stu-id="44a9f-128">**Figure 6-7**.</span></span> <span data-ttu-id="44a9f-129">サイドカーを使用したサービスメッシュ</span><span class="sxs-lookup"><span data-stu-id="44a9f-129">Service mesh with a side car</span></span>

<span data-ttu-id="44a9f-130">前の図では、プロキシがマイクロサービスとクラスター間の通信を傍受して管理する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="44a9f-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="44a9f-131">サービスメッシュは、 [データプレーン](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) と [コントロールプレーン](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)の2つの異なるコンポーネントに論理的に分割されます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="44a9f-132">図6-8 は、これらのコンポーネントとその役割を示しています。</span><span class="sxs-lookup"><span data-stu-id="44a9f-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![サービスメッシュ制御とデータプレーン](./media/istio-control-and-data-plane.png)

<span data-ttu-id="44a9f-134">**図 6-8.**</span><span class="sxs-lookup"><span data-stu-id="44a9f-134">**Figure 6-8.**</span></span> <span data-ttu-id="44a9f-135">サービスメッシュ制御とデータプレーン</span><span class="sxs-lookup"><span data-stu-id="44a9f-135">Service mesh control and data plane</span></span>

<span data-ttu-id="44a9f-136">構成が完了すると、サービスメッシュが非常に機能します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="44a9f-137">サービス探索エンドポイントから、対応するインスタンスのプールを取得できます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="44a9f-138">その後、メッシュは特定のインスタンスに要求を送信し、結果の待機時間と応答の種類を記録できます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="44a9f-139">メッシュでは、最近の要求の待機時間など、多くの要因に基づいて高速な応答を返す可能性の高いインスタンスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="44a9f-140">インスタンスが応答しない場合、または失敗した場合、メッシュは別のインスタンスで要求を再試行します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="44a9f-141">エラーが返された場合、メッシュは負荷分散プールからインスタンスを削除し、復旧後にそのインスタンスを再度実行します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="44a9f-142">要求がタイムアウトになると、メッシュが失敗し、要求を再試行することができます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="44a9f-143">メッシュは、メトリックをキャプチャし、集中型のメトリックシステムに分散トレースを出力します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="44a9f-144">Iとエンボイ</span><span class="sxs-lookup"><span data-stu-id="44a9f-144">Istio and Envoy</span></span>

<span data-ttu-id="44a9f-145">現在、いくつかのサービスメッシュオプションが存在しますが、このドキュメントの執筆時点では、 [iws-at o](https://istio.io/docs/concepts/what-is-istio/) が最も人気です。</span><span class="sxs-lookup"><span data-stu-id="44a9f-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="44a9f-146">Iフェロー o は、IBM、Google、およびその他の顧客との共同事業です。</span><span class="sxs-lookup"><span data-stu-id="44a9f-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="44a9f-147">これは、新規または既存の分散アプリケーションに統合できるオープンソースのオファリングです。</span><span class="sxs-lookup"><span data-stu-id="44a9f-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="44a9f-148">このテクノロジは、マイクロサービスのセキュリティ保護、接続、監視を行うための一貫した完全なソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="44a9f-149">次のような機能があります。</span><span class="sxs-lookup"><span data-stu-id="44a9f-149">Its features include:</span></span>

- <span data-ttu-id="44a9f-150">強力な id ベースの認証と承認を使用して、クラスター内のサービス間通信をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="44a9f-151">HTTP、 [Grpc](https://grpc.io/)、WEBSOCKET、TCP トラフィックの自動負荷分散。</span><span class="sxs-lookup"><span data-stu-id="44a9f-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="44a9f-152">豊富なルーティング規則、再試行、フェールオーバー、およびフォールトインジェクションにより、トラフィックの動作をきめ細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="44a9f-153">アクセス制御、レート制限、クォータをサポートするプラグ可能なポリシーレイヤーと構成 API。</span><span class="sxs-lookup"><span data-stu-id="44a9f-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="44a9f-154">クラスター内のすべてのトラフィック (クラスターの受信と送信を含む) の自動メトリック、ログ、およびトレース。</span><span class="sxs-lookup"><span data-stu-id="44a9f-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="44a9f-155">Iの実装の主要なコンポーネントは、 [エンボイプロキシ](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)を持つプロキシサービスです。</span><span class="sxs-lookup"><span data-stu-id="44a9f-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="44a9f-156">各サービスと共に実行され、次の機能のためのプラットフォームに依存しない基盤を提供します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="44a9f-157">動的サービスの検出。</span><span class="sxs-lookup"><span data-stu-id="44a9f-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="44a9f-158">負荷分散。</span><span class="sxs-lookup"><span data-stu-id="44a9f-158">Load balancing.</span></span>
- <span data-ttu-id="44a9f-159">TLS の終了。</span><span class="sxs-lookup"><span data-stu-id="44a9f-159">TLS termination.</span></span>
- <span data-ttu-id="44a9f-160">HTTP および gRPC プロキシ。</span><span class="sxs-lookup"><span data-stu-id="44a9f-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="44a9f-161">サーキットブレーカーの回復性。</span><span class="sxs-lookup"><span data-stu-id="44a9f-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="44a9f-162">正常性チェック。</span><span class="sxs-lookup"><span data-stu-id="44a9f-162">Health checks.</span></span>
- <span data-ttu-id="44a9f-163">[カナリア](https://martinfowler.com/bliki/CanaryRelease.html)デプロイによる更新のローリング。</span><span class="sxs-lookup"><span data-stu-id="44a9f-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="44a9f-164">既に説明したように、エンボイはクラスター内の各マイクロサービスにサイドカーとしてデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="44a9f-165">Azure Kubernetes Services との統合</span><span class="sxs-lookup"><span data-stu-id="44a9f-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="44a9f-166">Azure クラウドは、azure Kubernetes Services 内での直接サポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="44a9f-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="44a9f-167">次のリンクを使用して作業を開始できます。</span><span class="sxs-lookup"><span data-stu-id="44a9f-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="44a9f-168">AKS での Ip のインストール</span><span class="sxs-lookup"><span data-stu-id="44a9f-168">Installing Istio in AKS</span></span>](/azure/aks/istio-install)
- [<span data-ttu-id="44a9f-169">AKS と Iを使用する</span><span class="sxs-lookup"><span data-stu-id="44a9f-169">Using AKS and Istio</span></span>](/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="44a9f-170">References</span><span class="sxs-lookup"><span data-stu-id="44a9f-170">References</span></span>

- [<span data-ttu-id="44a9f-171">Polly</span><span class="sxs-lookup"><span data-stu-id="44a9f-171">Polly</span></span>](https://dotnetfoundation.org/projects/polly)

- [<span data-ttu-id="44a9f-172">再試行パターン</span><span class="sxs-lookup"><span data-stu-id="44a9f-172">Retry pattern</span></span>](/azure/architecture/patterns/retry)

- [<span data-ttu-id="44a9f-173">サーキット ブレーカー パターン</span><span class="sxs-lookup"><span data-stu-id="44a9f-173">Circuit Breaker pattern</span></span>](/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="44a9f-174">Azure での復元に関するホワイトペーパー</span><span class="sxs-lookup"><span data-stu-id="44a9f-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="44a9f-175">ネットワーク待機時間</span><span class="sxs-lookup"><span data-stu-id="44a9f-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="44a9f-176">冗長性</span><span class="sxs-lookup"><span data-stu-id="44a9f-176">Redundancy</span></span>](/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="44a9f-177">geo レプリケーション</span><span class="sxs-lookup"><span data-stu-id="44a9f-177">geo-replication</span></span>](/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="44a9f-178">Azure の Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="44a9f-178">Azure Traffic Manager</span></span>](/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="44a9f-179">自動スケール ガイダンス</span><span class="sxs-lookup"><span data-stu-id="44a9f-179">Autoscaling guidance</span></span>](/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="44a9f-180">Istio</span><span class="sxs-lookup"><span data-stu-id="44a9f-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="44a9f-181">エンボイプロキシ</span><span class="sxs-lookup"><span data-stu-id="44a9f-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="44a9f-182">[前へ](infrastructure-resiliency-azure.md)
>[次へ](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="44a9f-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>
