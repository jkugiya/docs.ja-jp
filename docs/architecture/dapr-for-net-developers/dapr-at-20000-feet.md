---
title: 2 万フィートの Dapr
description: Dapr の概要、その機能、およびしくみについて説明します。
author: robvet
ms.date: 02/07/2021
ms.openlocfilehash: f0efb4652aaa35961d59979cb561941e5280a575
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604750"
---
# <a name="dapr-at-20000-feet"></a><span data-ttu-id="da085-103">2 万フィートの Dapr</span><span class="sxs-lookup"><span data-stu-id="da085-103">Dapr at 20,000 feet</span></span>

<span data-ttu-id="da085-104">第1章では、分散マイクロサービスアプリケーションの魅力を説明しました。</span><span class="sxs-lookup"><span data-stu-id="da085-104">In chapter 1, we discussed the appeal of distributed microservice applications.</span></span> <span data-ttu-id="da085-105">しかし、アーキテクチャや運用上の複雑さを劇的に向上させることも指摘しました。</span><span class="sxs-lookup"><span data-stu-id="da085-105">But, we also pointed out that they dramatically increase architectural and operational complexity.</span></span> <span data-ttu-id="da085-106">そのことを念頭に置いて、"ケーキ" と "食べ" をどのようにして使用できるのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="da085-106">With that in mind, the question becomes, how can you "have your cake" and "eat it too?".</span></span> <span data-ttu-id="da085-107">つまり、分散アーキテクチャの機敏性を活用し、複雑さを最小限に抑えるにはどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="da085-107">That is, how can you take advantage of the agility of distributed architecture, and minimize its complexity?</span></span>

<span data-ttu-id="da085-108">Dapr ( *分散アプリケーションランタイム*) は、最新の分散アプリケーションを構築するための新しい方法です。</span><span class="sxs-lookup"><span data-stu-id="da085-108">Dapr, or *Distributed Application Runtime*, is a new way to build modern distributed applications.</span></span>

<span data-ttu-id="da085-109">プロトタイプとして開始されたことが、優れたオープンソースプロジェクトに発展しました。</span><span class="sxs-lookup"><span data-stu-id="da085-109">What started as a prototype has evolved into a highly successful open-source project.</span></span> <span data-ttu-id="da085-110">Microsoft のスポンサーであるスポンサーは、Dapr を設計および構築するために、お客様とオープンソースコミュニティと緊密に提携しています。</span><span class="sxs-lookup"><span data-stu-id="da085-110">Its sponsor, Microsoft, has closely partnered with customers and the open-source community to design and build Dapr.</span></span> <span data-ttu-id="da085-111">Dapr プロジェクトは、すべての背景から開発者を集めて、分散アプリケーションの開発に関する困難な課題をいくつか解決します。</span><span class="sxs-lookup"><span data-stu-id="da085-111">The Dapr project brings together developers from all backgrounds to solve some of the toughest challenges of developing distributed applications.</span></span>

<span data-ttu-id="da085-112">この書籍では、.NET 開発者の視点から見た、Dapr について見ていきます。</span><span class="sxs-lookup"><span data-stu-id="da085-112">This book looks at Dapr from the viewpoint of a .NET developer.</span></span> <span data-ttu-id="da085-113">この章では、Dapr とそのしくみの概念を理解します。</span><span class="sxs-lookup"><span data-stu-id="da085-113">In this chapter, you'll build a conceptual understanding of Dapr and how it works.</span></span> <span data-ttu-id="da085-114">後で、アプリケーションで Dapr を使用する方法について、実践的な実践的な指示を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-114">Later on, we present practical, hands-on instruction on how you can use Dapr in your applications.</span></span>

<span data-ttu-id="da085-115">ジェットで2万フィートに飛ぶことを想像してください。</span><span class="sxs-lookup"><span data-stu-id="da085-115">Imagine flying in a jet at 20,000 feet.</span></span> <span data-ttu-id="da085-116">ウィンドウを見て、以下の横長を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="da085-116">You look out the window and see the landscape below from a wide perspective.</span></span> <span data-ttu-id="da085-117">Dapr についても同様です。</span><span class="sxs-lookup"><span data-stu-id="da085-117">Let's do the same for Dapr.</span></span> <span data-ttu-id="da085-118">Dapr を2万フィートで飛ぶことを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="da085-118">Visualize yourself flying over Dapr at 20,000 feet.</span></span> <span data-ttu-id="da085-119">表示内容</span><span class="sxs-lookup"><span data-stu-id="da085-119">What would you see?</span></span>

## <a name="dapr-and-the-problem-it-solves"></a><span data-ttu-id="da085-120">Dapr とそれが解決する問題</span><span class="sxs-lookup"><span data-stu-id="da085-120">Dapr and the problem it solves</span></span>

<span data-ttu-id="da085-121">Dapr は、最新の分散アプリケーションに固有の大きな課題に対処します。 **複雑さ**。</span><span class="sxs-lookup"><span data-stu-id="da085-121">Dapr addresses a large challenge inherent in modern distributed applications: **Complexity**.</span></span>

<span data-ttu-id="da085-122">プラグ可能なコンポーネントのアーキテクチャを通じて、Dapr は分散アプリケーションの背後を大幅に簡略化します。</span><span class="sxs-lookup"><span data-stu-id="da085-122">Through an architecture of pluggable components, Dapr greatly simplifies the plumbing behind distributed applications.</span></span> <span data-ttu-id="da085-123">これは、アプリケーションを Dapr ランタイムからインフラストラクチャ機能にバインドする **動的接着** を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-123">It provides a **dynamic glue** that binds your application with infrastructure capabilities from the Dapr runtime.</span></span> <span data-ttu-id="da085-124">たとえば、アプリケーションで状態ストアが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="da085-124">For example, your application may require a state store.</span></span> <span data-ttu-id="da085-125">Redis Cache を対象とするカスタムコードを作成し、実行時にサービスに挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="da085-125">You could write custom code to target Redis Cache and inject it into your service at runtime.</span></span> <span data-ttu-id="da085-126">ただし、Dapr は、すぐに使用できる分散キャッシュ機能を提供することで、エクスペリエンスを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="da085-126">However, Dapr simplifies your experience by providing a distributed cache capability out-of-the-box.</span></span> <span data-ttu-id="da085-127">サービスは、Dapr **構成** を介して Redis Cache **コンポーネント** に動的にバインドする dapr **ビルディングブロック** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="da085-127">Your service invokes a Dapr **building block** that dynamically binds to Redis Cache **component** via a Dapr **configuration**.</span></span> <span data-ttu-id="da085-128">このモデルでは、サービスによって Dapr への呼び出しが委任されます。この呼び出しは、お客様の代わりに Redis を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="da085-128">With this model, your service delegates the call to Dapr, which calls Redis on your behalf.</span></span> <span data-ttu-id="da085-129">サービスには、Redis への SDK、ライブラリ、または直接参照がありません。</span><span class="sxs-lookup"><span data-stu-id="da085-129">Your service has no SDK, library, or direct reference to Redis.</span></span> <span data-ttu-id="da085-130">Redis Cache API ではなく、一般的な Dapr state management API に対してコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="da085-130">You code against the common Dapr state management API, not the Redis Cache API.</span></span>

<span data-ttu-id="da085-131">図2-1 は、2万フィートの Dapr を示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-131">Figure 2-1 shows Dapr from 20,000 feet.</span></span>

<span data-ttu-id="da085-132">![Dapr、2万フィートの ](./media/dapr-at-20000-feet/dapr-high-level.png)
 **図 2-1**。</span><span class="sxs-lookup"><span data-stu-id="da085-132">![Dapr at 20,000 feet](./media/dapr-at-20000-feet/dapr-high-level.png)
**Figure 2-1**.</span></span> <span data-ttu-id="da085-133">Dapr は2万フィートです。</span><span class="sxs-lookup"><span data-stu-id="da085-133">Dapr at 20,000 feet.</span></span>

<span data-ttu-id="da085-134">図の一番上の行で、Dapr が一般的な開発プラットフォーム向けの言語固有の Sdk を提供するしくみに注意してください。</span><span class="sxs-lookup"><span data-stu-id="da085-134">In the top row of the figure, note how Dapr provides language-specific SDKs for popular development platforms.</span></span> <span data-ttu-id="da085-135">Dapr v 1.0 には、ゴー、Node.js、Python、.NET、Java、および JavaScript がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="da085-135">Dapr v 1.0 includes supports Go, Node.js, Python, .NET, Java, and JavaScript.</span></span> <span data-ttu-id="da085-136">この書籍では、Dapr .NET SDK に焦点を当てています。これにより、ASP.NET Core 統合も直接サポートされます。</span><span class="sxs-lookup"><span data-stu-id="da085-136">This book focuses on the Dapr .NET SDK, which also provides direct support for ASP.NET Core integration.</span></span>

<span data-ttu-id="da085-137">言語固有の Sdk によって開発者のエクスペリエンスが向上しますが、Dapr はプラットフォームに依存しません。</span><span class="sxs-lookup"><span data-stu-id="da085-137">While language-specific SDKs enhance the developer experience, Dapr is platform agnostic.</span></span> <span data-ttu-id="da085-138">内部的には、Dapr のプログラミングモデルは、標準の HTTP/gRPC 通信プロトコルを介して機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="da085-138">Under the hood, Dapr's programming model exposes capabilities through standard HTTP/gRPC communication protocols.</span></span> <span data-ttu-id="da085-139">すべてのプログラミングプラットフォームは、ネイティブの HTTP および gRPC Api を介して Dapr を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="da085-139">Any programming platform can call Dapr via its native HTTP and gRPC APIs.</span></span>  

<span data-ttu-id="da085-140">図の中心にある青いボックスは、Dapr の構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="da085-140">The blue boxes across the center of the figure represent the Dapr building blocks.</span></span> <span data-ttu-id="da085-141">各は、アプリケーションが使用できる分散アプリケーション機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="da085-141">Each exposes a distributed application capability that your application can consume.</span></span>

<span data-ttu-id="da085-142">下の行は、Dapr と実行可能なさまざまな環境の移植性を強調しています。</span><span class="sxs-lookup"><span data-stu-id="da085-142">The bottom row highlights the portability of Dapr and the diverse environments across which it can run.</span></span>

## <a name="dapr-architecture"></a><span data-ttu-id="da085-143">Dapr アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="da085-143">Dapr architecture</span></span>

<span data-ttu-id="da085-144">この時点で、ジェットは、Dapr に戻り、高度に下ります。 Dapr がどのように機能するかについて詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="da085-144">At this point, the jet turns around and flies back over Dapr, descending in altitude, giving you a closer look at how Dapr works.</span></span>

### <a name="building-blocks"></a><span data-ttu-id="da085-145">構成要素</span><span class="sxs-lookup"><span data-stu-id="da085-145">Building blocks</span></span>

<span data-ttu-id="da085-146">新しいパースペクティブから、Dapr の **構成要素** の詳細なビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da085-146">From the new perspective, you see a more detailed view of the Dapr **building blocks**.</span></span>

<span data-ttu-id="da085-147">ビルディングブロックは、分散インフラストラクチャ機能をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="da085-147">A building block encapsulates a distributed infrastructure capability.</span></span> <span data-ttu-id="da085-148">この機能には、HTTP または gRPC Api を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="da085-148">You can access the functionality through the HTTP or gRPC APIs.</span></span> <span data-ttu-id="da085-149">図2-2 は、Dapr v 1.0 で使用可能なブロックを示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-149">Figure 2-2 shows the available blocks for Dapr v 1.0.</span></span>

![Dapr の構成要素](./media/dapr-at-20000-feet/building-blocks.png)

<span data-ttu-id="da085-151">**図 2-2**.</span><span class="sxs-lookup"><span data-stu-id="da085-151">**Figure 2-2**.</span></span> <span data-ttu-id="da085-152">Dapr のビルディングブロック。</span><span class="sxs-lookup"><span data-stu-id="da085-152">Dapr building blocks.</span></span>

<span data-ttu-id="da085-153">次の表では、各ブロックによって提供されるインフラストラクチャサービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="da085-153">The following table describes the infrastructure services provided by each block.</span></span>

| <span data-ttu-id="da085-154">構成要素</span><span class="sxs-lookup"><span data-stu-id="da085-154">Building block</span></span> | <span data-ttu-id="da085-155">説明</span><span class="sxs-lookup"><span data-stu-id="da085-155">Description</span></span> |
|----------------|-------------|
| [<span data-ttu-id="da085-156">状態管理</span><span class="sxs-lookup"><span data-stu-id="da085-156">State management</span></span>](state-management.md) | <span data-ttu-id="da085-157">長時間実行されるステートフルサービスのコンテキスト情報をサポートします。</span><span class="sxs-lookup"><span data-stu-id="da085-157">Support contextual information for long running stateful services.</span></span> |
| [<span data-ttu-id="da085-158">サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="da085-158">Service invocation</span></span>](service-invocation.md) | <span data-ttu-id="da085-159">プラットフォームに依存しないプロトコルと既知のエンドポイントを使用して、直接、安全なサービス間呼び出しを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="da085-159">Invoke direct, secure service-to-service calls using platform agnostic protocols and well-known endpoints.</span></span> |
| [<span data-ttu-id="da085-160">パブリッシュとサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="da085-160">Publish and subscribe</span></span>](publish-subscribe.md) | <span data-ttu-id="da085-161">サービス間にセキュリティで保護されたスケーラブルな公開/サブメッセージングを実装します。</span><span class="sxs-lookup"><span data-stu-id="da085-161">Implement secure, scalable pub/sub messaging between services.</span></span> |
| [<span data-ttu-id="da085-162">バインド</span><span class="sxs-lookup"><span data-stu-id="da085-162">Bindings</span></span>](bindings.md) | <span data-ttu-id="da085-163">双方向通信で外部リソースによって発生したイベントからコードをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="da085-163">Trigger code from events raised by external resources with bi-directional communication.</span></span> |
| [<span data-ttu-id="da085-164">可観測性</span><span class="sxs-lookup"><span data-stu-id="da085-164">Observability</span></span>](observability.md) | <span data-ttu-id="da085-165">ネットワークに接続されたサービス間でのメッセージ呼び出しを監視して測定します。</span><span class="sxs-lookup"><span data-stu-id="da085-165">Monitor and measure message calls across networked services.</span></span> |
| [<span data-ttu-id="da085-166">シークレット</span><span class="sxs-lookup"><span data-stu-id="da085-166">Secrets</span></span>](secrets.md) | <span data-ttu-id="da085-167">外部シークレットストアに安全にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="da085-167">Securely access external secret stores.</span></span> |
| <span data-ttu-id="da085-168">アクター</span><span class="sxs-lookup"><span data-stu-id="da085-168">Actors</span></span> | <span data-ttu-id="da085-169">再利用可能なアクターオブジェクトでロジックとデータをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="da085-169">Encapsulate logic and data in reusable actor objects.</span></span> |

<span data-ttu-id="da085-170">構成要素は、サービスからの分散アプリケーション機能の実装を抽象化します。</span><span class="sxs-lookup"><span data-stu-id="da085-170">Building blocks abstract the implementation of distributed application capabilities from your services.</span></span> <span data-ttu-id="da085-171">図2-3 は、この相互作用を示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-171">Figure 2-3 shows this interaction.</span></span>

![Dapr 構成ブロックの統合](./media/dapr-at-20000-feet/building-blocks-integration.png)

<span data-ttu-id="da085-173">**図 2-3**.</span><span class="sxs-lookup"><span data-stu-id="da085-173">**Figure 2-3**.</span></span> <span data-ttu-id="da085-174">Dapr ビルディングブロック統合。</span><span class="sxs-lookup"><span data-stu-id="da085-174">Dapr building block integration.</span></span>

<span data-ttu-id="da085-175">構成要素は、各リソースの具象実装を提供する Dapr コンポーネントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="da085-175">Building blocks invoke Dapr components that provide the concrete implementation for each resource.</span></span> <span data-ttu-id="da085-176">サービスのコードは、ビルディングブロックだけを認識します。</span><span class="sxs-lookup"><span data-stu-id="da085-176">The code for your service is only aware of the building block.</span></span> <span data-ttu-id="da085-177">外部 Sdk またはライブラリへの依存関係はありません。 Dapr は、組み込みを処理します。</span><span class="sxs-lookup"><span data-stu-id="da085-177">It takes no dependencies on external SDKs or libraries - Dapr handles the plumbing for you.</span></span> <span data-ttu-id="da085-178">各構成要素は独立しています。</span><span class="sxs-lookup"><span data-stu-id="da085-178">Each building block is independent.</span></span> <span data-ttu-id="da085-179">アプリケーションでは、そのうちの1つ、一部、またはすべてを使用できます。</span><span class="sxs-lookup"><span data-stu-id="da085-179">You can use one, some, or all of them in your application.</span></span> <span data-ttu-id="da085-180">焼き付けるとして、Dapr は、包括的な可観測性を含む業界のベストプラクティスに従っています。</span><span class="sxs-lookup"><span data-stu-id="da085-180">As a value-add, Dapr building blocks bake in industry best practices including comprehensive observability.</span></span>

<span data-ttu-id="da085-181">各 Dapr ビルディングブロックの詳細な説明とコードサンプルについては、今後の章で説明します。</span><span class="sxs-lookup"><span data-stu-id="da085-181">We provide detailed explanation and code samples for each Dapr building block in the upcoming chapters.</span></span> <span data-ttu-id="da085-182">この時点で、jet はさらに多くのことを降下します。</span><span class="sxs-lookup"><span data-stu-id="da085-182">At this point, the jet descends even more.</span></span> <span data-ttu-id="da085-183">新しいパースペクティブから、Dapr コンポーネントレイヤーについて詳しく見ていきます。</span><span class="sxs-lookup"><span data-stu-id="da085-183">From the new perspective, you now have a closer look at the Dapr components layer.</span></span>

### <a name="components"></a><span data-ttu-id="da085-184">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="da085-184">Components</span></span>

<span data-ttu-id="da085-185">ビルドブロックは、分散アプリケーション機能を呼び出すための API を公開しますが、Dapr コンポーネントは、それを実現するための具象実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-185">While building blocks expose an API to invoke distributed application capabilities, Dapr components provide the concrete implementation to make it happen.</span></span>

<span data-ttu-id="da085-186">Dapr **状態ストア** コンポーネントを検討してください。</span><span class="sxs-lookup"><span data-stu-id="da085-186">Consider, the Dapr **state store** component.</span></span> <span data-ttu-id="da085-187">CRUD 操作の状態を管理するための一貫した方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-187">It provides a uniform way to manage state for CRUD operations.</span></span> <span data-ttu-id="da085-188">サービスコードに変更を加えることなく、次のいずれかの Dapr 状態コンポーネントを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="da085-188">Without any change to your service code, you could switch between any of the following Dapr state components:</span></span>

- <span data-ttu-id="da085-189">AWS DynamoDB</span><span class="sxs-lookup"><span data-stu-id="da085-189">AWS DynamoDB</span></span>
- <span data-ttu-id="da085-190">Aerospike</span><span class="sxs-lookup"><span data-stu-id="da085-190">Aerospike</span></span>
- <span data-ttu-id="da085-191">Azure Blob Storage</span><span class="sxs-lookup"><span data-stu-id="da085-191">Azure Blob Storage</span></span>
- <span data-ttu-id="da085-192">Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="da085-192">Azure CosmosDB</span></span>
- <span data-ttu-id="da085-193">Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="da085-193">Azure Table Storage</span></span>
- <span data-ttu-id="da085-194">Cassandra</span><span class="sxs-lookup"><span data-stu-id="da085-194">Cassandra</span></span>
- <span data-ttu-id="da085-195">クラウド Firestore (データストアモード)</span><span class="sxs-lookup"><span data-stu-id="da085-195">Cloud Firestore (Datastore mode)</span></span>
- <span data-ttu-id="da085-196">CloudState</span><span class="sxs-lookup"><span data-stu-id="da085-196">CloudState</span></span>
- <span data-ttu-id="da085-197">Couchbase</span><span class="sxs-lookup"><span data-stu-id="da085-197">Couchbase</span></span>
- <span data-ttu-id="da085-198">Etcd</span><span class="sxs-lookup"><span data-stu-id="da085-198">Etcd</span></span>
- <span data-ttu-id="da085-199">HashiCorp Consul</span><span class="sxs-lookup"><span data-stu-id="da085-199">HashiCorp Consul</span></span>
- <span data-ttu-id="da085-200">Hazelcast</span><span class="sxs-lookup"><span data-stu-id="da085-200">Hazelcast</span></span>
- <span data-ttu-id="da085-201">Memcached</span><span class="sxs-lookup"><span data-stu-id="da085-201">Memcached</span></span>
- <span data-ttu-id="da085-202">MongoDB</span><span class="sxs-lookup"><span data-stu-id="da085-202">MongoDB</span></span>
- <span data-ttu-id="da085-203">PostgreSQL</span><span class="sxs-lookup"><span data-stu-id="da085-203">PostgreSQL</span></span>
- <span data-ttu-id="da085-204">Redis</span><span class="sxs-lookup"><span data-stu-id="da085-204">Redis</span></span>
- <span data-ttu-id="da085-205">RethinkDB</span><span class="sxs-lookup"><span data-stu-id="da085-205">RethinkDB</span></span>
- <span data-ttu-id="da085-206">SQL Server</span><span class="sxs-lookup"><span data-stu-id="da085-206">SQL Server</span></span>
- <span data-ttu-id="da085-207">Zookeeper</span><span class="sxs-lookup"><span data-stu-id="da085-207">Zookeeper</span></span>

<span data-ttu-id="da085-208">各コンポーネントは、共通の状態管理インターフェイスによって必要な実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-208">Each component provides the necessary implementation through a common state management interface:</span></span>

```go
 type Store interface {
   Init(metadata Metadata) error
   Delete(req *DeleteRequest) error
   BulkDelete(req []DeleteRequest) error
   Get(req *GetRequest) (*GetResponse, error)
   Set(req *SetRequest) error
   BulkSet(req []SetRequest) error
}
```

> [!TIP]
> <span data-ttu-id="da085-209">Dapr ランタイムとすべての Dapr コンポーネントは、Golang、またはゴー言語で記述されています。</span><span class="sxs-lookup"><span data-stu-id="da085-209">The Dapr runtime as well as all of the Dapr components have been written in the Golang, or Go, language.</span></span> <span data-ttu-id="da085-210">外出先は、オープンソースコミュニティで広く普及している言語であり、Dapr のクロスプラットフォームコミットメントをはしています。</span><span class="sxs-lookup"><span data-stu-id="da085-210">Go is a popular language across the open source community and attests to cross-platform commitment of Dapr.</span></span>

<span data-ttu-id="da085-211">おそらく、状態ストアとして Azure Redis Cache から開始します。</span><span class="sxs-lookup"><span data-stu-id="da085-211">Perhaps you start with Azure Redis Cache as your state store.</span></span> <span data-ttu-id="da085-212">次の構成で指定します。</span><span class="sxs-lookup"><span data-stu-id="da085-212">You specify it with the following configuration:</span></span>

 ```yaml
 apiVersion: dapr.io/v1alpha1
 kind: Component
 metadata:
   name: statestore
   namespace: default
 spec:
   type: state.redis
   version: v1
   metadata:
   - name: redisHost
     value: <HOST>
   - name: redisPassword
     value: <PASSWORD>
   - name: enableTLS
     value: <bool> # Optional. Allowed: true, false.
   - name: failover
     value: <bool> # Optional. Allowed: true, false.
 ```

<span data-ttu-id="da085-213">[ **Spec** ] セクションでは、状態管理に Redis Cache を使用するように dapr を構成します。</span><span class="sxs-lookup"><span data-stu-id="da085-213">In the **spec** section, you configure Dapr to use the Redis Cache for state management.</span></span> <span data-ttu-id="da085-214">このセクションには、コンポーネント固有のメタデータも含まれています。</span><span class="sxs-lookup"><span data-stu-id="da085-214">The section also contains component-specific metadata.</span></span> <span data-ttu-id="da085-215">この場合は、追加の Redis 設定を構成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="da085-215">In this case, you can use it to configure additional Redis settings.</span></span>

<span data-ttu-id="da085-216">後で、アプリケーションを運用環境に移行する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="da085-216">At a later time, the application is ready to go to production.</span></span> <span data-ttu-id="da085-217">運用環境では、状態管理を Azure Table Storage に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="da085-217">For the production environment, you may want to change your state management to Azure Table Storage.</span></span> <span data-ttu-id="da085-218">Azure Table Storage は、低価格で耐久性の高い状態管理機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-218">Azure Table Storage provides state management capabilities that are affordable and highly durable.</span></span>

<span data-ttu-id="da085-219">このドキュメントの執筆時点では、Dapr によって次のコンポーネントの種類が提供されています。</span><span class="sxs-lookup"><span data-stu-id="da085-219">At the time of this writing, the following component types are provided by Dapr:</span></span>

| <span data-ttu-id="da085-220">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="da085-220">Component</span></span> | <span data-ttu-id="da085-221">説明</span><span class="sxs-lookup"><span data-stu-id="da085-221">Description</span></span> |
|-----------|-------------|
| [<span data-ttu-id="da085-222">サービスの検出</span><span class="sxs-lookup"><span data-stu-id="da085-222">Service discovery</span></span>](https://github.com/dapr/components-contrib/tree/master/nameresolution) | <span data-ttu-id="da085-223">サービス呼び出しの構成要素によって使用され、ホスト環境と統合してサービス間検出を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-223">Used by the service invocation building block to integrate with the hosting environment to provide service-to-service discovery.</span></span> |
| [<span data-ttu-id="da085-224">State</span><span class="sxs-lookup"><span data-stu-id="da085-224">State</span></span>](https://github.com/dapr/components-contrib/tree/master/state) | <span data-ttu-id="da085-225">さまざまな状態ストアの実装と対話するための、統一されたインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-225">Provides a uniform interface to interact with a wide variety of state store implementations.</span></span> |
| [<span data-ttu-id="da085-226">Pub/sub</span><span class="sxs-lookup"><span data-stu-id="da085-226">Pub/sub</span></span>](https://github.com/dapr/components-contrib/tree/master/pubsub) | <span data-ttu-id="da085-227">は、さまざまなメッセージバスの実装と対話するための、統一されたインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-227">Provides a uniform interface to interact with a wide variety of message bus implementations.</span></span> |
| [<span data-ttu-id="da085-228">バインド</span><span class="sxs-lookup"><span data-stu-id="da085-228">Bindings</span></span>](https://github.com/dapr/components-contrib/tree/master/bindings) | <span data-ttu-id="da085-229">外部システムからアプリケーションイベントをトリガーし、オプションのデータペイロードを使用して外部システムを呼び出すための、統一されたインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-229">Provides a uniform interface to trigger application events from external systems and invoke external systems with optional data payloads.</span></span> |
| [<span data-ttu-id="da085-230">ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="da085-230">Middleware</span></span>](https://github.com/dapr/components-contrib/tree/master/middleware) | <span data-ttu-id="da085-231">カスタムミドルウェアが要求処理パイプラインにプラグインし、要求または応答に対して追加のアクションを呼び出すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="da085-231">Allows custom middleware to plug into the request processing pipeline and invoke additional actions on a request or response.</span></span> |
| [<span data-ttu-id="da085-232">シークレットストア</span><span class="sxs-lookup"><span data-stu-id="da085-232">Secret stores</span></span>](https://github.com/dapr/components-contrib/tree/master/secretstores) | <span data-ttu-id="da085-233">クラウド、エッジ、商用、オープンソースサービスなど、外部シークレットストアと対話するための統一インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-233">Provides a uniform interface to interact with external secret stores, including cloud, edge, commercial, open-source services.</span></span> |

<span data-ttu-id="da085-234">ジェットが Dapr に対して実行を完了すると、後でもう一度確認し、相互に接続する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="da085-234">As the jet completes its fly over of Dapr, you look back once more and can see how it connects together.</span></span>

### <a name="sidecar-architecture"></a><span data-ttu-id="da085-235">Sidecar アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="da085-235">Sidecar architecture</span></span>

<span data-ttu-id="da085-236">Dapr は、 [サイドカーアーキテクチャ](/azure/architecture/patterns/sidecar)を通じて、その構成要素とコンポーネントを公開します。</span><span class="sxs-lookup"><span data-stu-id="da085-236">Dapr exposes its building blocks and components through a [sidecar architecture](/azure/architecture/patterns/sidecar).</span></span> <span data-ttu-id="da085-237">サイドカーを使用すると、Dapr を別のメモリプロセスで、またはサービスと共に個別のコンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="da085-237">A sidecar enables Dapr to run in a separate memory process or separate container alongside your service.</span></span> <span data-ttu-id="da085-238">Sidecars、サービスの一部ではなく、接続されているため、分離とカプセル化を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-238">Sidecars provide isolation and encapsulation as they aren't part of the service, but connected to it.</span></span> <span data-ttu-id="da085-239">この分離により、それぞれに独自のランタイム環境を持たせることができ、さまざまなプログラミングプラットフォームに基づいてビルドできます。</span><span class="sxs-lookup"><span data-stu-id="da085-239">This separation enables each to have its own runtime environment and be built upon different programming platforms.</span></span> <span data-ttu-id="da085-240">図2-4 は、サイドカーパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-240">Figure 2-4 shows a sidecar pattern.</span></span>

![Sidecar アーキテクチャ](./media/dapr-at-20000-feet/sidecar-generic.png)

<span data-ttu-id="da085-242">**図 2-4**</span><span class="sxs-lookup"><span data-stu-id="da085-242">**Figure 2-4**.</span></span> <span data-ttu-id="da085-243">Sidecar アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="da085-243">Sidecar architecture.</span></span>

<span data-ttu-id="da085-244">このパターンは、オートバイに取り付けられるサイドカーに似ているため、"サイドカー" と名付けられています。</span><span class="sxs-lookup"><span data-stu-id="da085-244">This pattern is named Sidecar because it resembles a sidecar attached to a motorcycle.</span></span> <span data-ttu-id="da085-245">前の図では、分散アプリケーション機能を提供するために、dapr サイドカーがサービスにどのようにアタッチされているかに注目してください。</span><span class="sxs-lookup"><span data-stu-id="da085-245">In the previous figure, note how the Dapr sidecar is attached to your service to provide distributed application capabilities.</span></span>

### <a name="hosting-environments"></a><span data-ttu-id="da085-246">ホスティング環境</span><span class="sxs-lookup"><span data-stu-id="da085-246">Hosting environments</span></span>

<span data-ttu-id="da085-247">Dapr はクロスプラットフォームのサポートを備えており、さまざまな環境で実行できます。</span><span class="sxs-lookup"><span data-stu-id="da085-247">Dapr has cross-platform support and can run in many different environments.</span></span> <span data-ttu-id="da085-248">これらの環境には、Kubernetes、Vm のグループ、Azure IoT Edge などのエッジ環境が含まれます。</span><span class="sxs-lookup"><span data-stu-id="da085-248">These environments include Kubernetes, a group of VMs, or edge environments such as Azure IoT Edge.</span></span>

<span data-ttu-id="da085-249">ローカル開発の場合、開始する最も簡単な方法は、 [自己ホスト型モード](https://docs.dapr.io/concepts/overview/#self-hosted)を使用することです。</span><span class="sxs-lookup"><span data-stu-id="da085-249">For local development, the easiest way to get started is with [self-hosted mode](https://docs.dapr.io/concepts/overview/#self-hosted).</span></span> <span data-ttu-id="da085-250">自己ホスト型モードでは、マイクロサービスと Dapr サイドカーは、Kubernetes などのコンテナー orchestrator を使用せずに個別のローカルプロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="da085-250">In self-hosted mode, the microservices and Dapr sidecars run in separate local processes without a container orchestrator such as Kubernetes.</span></span> <span data-ttu-id="da085-251">詳細については、「 [Dapr CLI のダウンロードとインストール](https://docs.dapr.io/getting-started/install-dapr/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da085-251">For more information, see [download and install the Dapr CLI](https://docs.dapr.io/getting-started/install-dapr/).</span></span>

<span data-ttu-id="da085-252">図2-5 は、HTTP または gRPC を介して通信する2つの別個のメモリプロセスでホストされるアプリケーションと Dapr を示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-252">Figure 2-5 shows an application and Dapr hosted in two separate memory processes communicating via HTTP or gRPC.</span></span>

![自己ホスト型のサイドカーアーキテクチャ](./media/dapr-at-20000-feet/self-hosted-dapr-sidecar.png)

<span data-ttu-id="da085-254">**図 2-5**.</span><span class="sxs-lookup"><span data-stu-id="da085-254">**Figure 2-5**.</span></span> <span data-ttu-id="da085-255">自己ホスト型 Dapr sidecar。</span><span class="sxs-lookup"><span data-stu-id="da085-255">Self-hosted Dapr sidecar.</span></span>

<span data-ttu-id="da085-256">既定では、Dapr は Redis および Zipkin 用の Docker コンテナーをインストールして、既定の状態管理と可観測性を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-256">By default, Dapr installs Docker containers for Redis and Zipkin to provide default state management and observability.</span></span> <span data-ttu-id="da085-257">ローカルコンピューターに Docker をインストールしない場合は、 [docker コンテナーを使用せずに、自己ホスト型モードで Dapr を実行](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/)することもできます。</span><span class="sxs-lookup"><span data-stu-id="da085-257">If you don't want to install Docker on your local machine, you can even [run Dapr in self-hosted mode without any Docker containers](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/).</span></span> <span data-ttu-id="da085-258">ただし、状態管理のための Redis、pub/sub などの既定のコンポーネントを手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="da085-258">However, you must install default components such as Redis for state management and pub/sub manually.</span></span>

<span data-ttu-id="da085-259">Dapr は、Kubernetes などのコンテナー化された [環境](https://docs.dapr.io/concepts/overview/#kubernetes-hosted)でも実行されます。</span><span class="sxs-lookup"><span data-stu-id="da085-259">Dapr also runs in [containerized environments](https://docs.dapr.io/concepts/overview/#kubernetes-hosted), such as Kubernetes.</span></span> <span data-ttu-id="da085-260">図2-6 は、同じ Kubernetes ポッド内のアプリケーションコンテナーと共に、別のサイドカーコンテナーで実行されている Dapr を示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-260">Figure 2-6 shows Dapr running in a separate side-car container along with the application container in the same Kubernetes pod.</span></span>

![Kubernetes-ホストされたサイドカーアーキテクチャ](./media/dapr-at-20000-feet/kubernetes-hosted-dapr-sidecar.png)

<span data-ttu-id="da085-262">**図 2-6**.</span><span class="sxs-lookup"><span data-stu-id="da085-262">**Figure 2-6**.</span></span> <span data-ttu-id="da085-263">Kubernetes Dapr sidecar。</span><span class="sxs-lookup"><span data-stu-id="da085-263">Kubernetes-hosted Dapr sidecar.</span></span>

## <a name="dapr-performance-considerations"></a><span data-ttu-id="da085-264">Dapr のパフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="da085-264">Dapr performance considerations</span></span>

<span data-ttu-id="da085-265">既に説明したように、Dapr は、アプリケーションを分散アプリケーションの機能から分離するためのサイドカーアーキテクチャを公開しています。</span><span class="sxs-lookup"><span data-stu-id="da085-265">As you've seen, Dapr exposes a sidecar architecture to decouple your application from distributed application capabilities.</span></span> <span data-ttu-id="da085-266">Dapr 操作を呼び出すには、少なくとも1つのプロセス外ネットワーク呼び出しが必要です。</span><span class="sxs-lookup"><span data-stu-id="da085-266">Invoking a Dapr operation requires at least one out-of-process network call.</span></span> <span data-ttu-id="da085-267">図2-7 は、Dapr トラフィックパターンの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-267">Figure 2-7 presents an example of a Dapr traffic pattern.</span></span>

![Dapr トラフィックパターン](./media/dapr-at-20000-feet/dapr-traffic-patterns.png)

<span data-ttu-id="da085-269">**図 2-7**.</span><span class="sxs-lookup"><span data-stu-id="da085-269">**Figure 2-7**.</span></span> <span data-ttu-id="da085-270">Dapr トラフィックパターン。</span><span class="sxs-lookup"><span data-stu-id="da085-270">Dapr traffic patterns.</span></span>

<span data-ttu-id="da085-271">前の図を見ると、各呼び出しに発生した待機時間とオーバーヘッドを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="da085-271">Looking at the previous figure, one might question the latency and overhead incurred for each call.</span></span>  

<span data-ttu-id="da085-272">Dapr チームは、パフォーマンスに大きく投資してきました。</span><span class="sxs-lookup"><span data-stu-id="da085-272">The Dapr team has invested heavily in performance.</span></span> <span data-ttu-id="da085-273">エンジニアリング作業の膨大な量が、Dapr の効率を高めることになりました。</span><span class="sxs-lookup"><span data-stu-id="da085-273">A tremendous amount of engineering effort has gone into making Dapr efficient.</span></span> <span data-ttu-id="da085-274">Dapr サイドカーの間の呼び出しは、高いパフォーマンスと小さいバイナリペイロードを提供する gRPC で常に行われます。</span><span class="sxs-lookup"><span data-stu-id="da085-274">Calls between Dapr sidecars are always made with gRPC, which delivers high performance and small binary payloads.</span></span> <span data-ttu-id="da085-275">ほとんどの場合、追加のオーバーヘッドは、ミリ秒単位にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="da085-275">In most cases, the additional overhead should be sub-millisecond.</span></span>

<span data-ttu-id="da085-276">パフォーマンスを向上させるために、開発者は gRPC を使用して Dapr ビルディングブロックを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="da085-276">To increase performance, developers can call the Dapr building blocks with gRPC.</span></span>

<span data-ttu-id="da085-277">gRPC は、古い [リモートプロシージャコール (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) プロトコルを進化させる最新の高パフォーマンスフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="da085-277">gRPC is a modern, high-performance framework that evolves the age-old [remote procedure call (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) protocol.</span></span> <span data-ttu-id="da085-278">gRPC は、トランスポートプロトコルとして HTTP/2 を使用します。これにより、次のような HTTP RESTFul サービスよりも大幅なパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="da085-278">gRPC uses HTTP/2 for its transport protocol, which provides significant performance enhancements over HTTP RESTFul service, including:</span></span>

- <span data-ttu-id="da085-279">同一の接続で複数の並列要求を送信するための多重化サポート-HTTP 1.1 は、一度に1つの要求/応答メッセージに処理を制限します。</span><span class="sxs-lookup"><span data-stu-id="da085-279">Multiplexing support for sending multiple parallel requests over the same connection - HTTP 1.1 limits processing to one request/response message at a time.</span></span>
- <span data-ttu-id="da085-280">クライアント要求とサーバー応答の両方を同時に送信するための双方向の全二重通信。</span><span class="sxs-lookup"><span data-stu-id="da085-280">Bidirectional full-duplex communication for sending both client requests and server responses simultaneously.</span></span>
- <span data-ttu-id="da085-281">要求と応答を有効にして、大きなデータセットを非同期的にストリーム配信できる組み込みのストリーミング。</span><span class="sxs-lookup"><span data-stu-id="da085-281">Built-in streaming enabling requests and responses to asynchronously stream large data sets.</span></span>

## <a name="dapr-and-service-meshes"></a><span data-ttu-id="da085-282">Dapr とサービスメッシュ</span><span class="sxs-lookup"><span data-stu-id="da085-282">Dapr and service meshes</span></span>

<span data-ttu-id="da085-283">サービスメッシュは、分散アプリケーションのための、急速に進化するもう1つのテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="da085-283">Service mesh is another rapidly evolving technology for distributed applications.</span></span>

<span data-ttu-id="da085-284">サービスメッシュは、サービス間の通信、回復性、負荷分散、テレメトリのキャプチャを処理する組み込みの機能を備えた、構成可能なインフラストラクチャレイヤーです。</span><span class="sxs-lookup"><span data-stu-id="da085-284">A service mesh is a configurable infrastructure layer with built-in capabilities to handle service-to-service communication, resiliency, load balancing, and telemetry capture.</span></span> <span data-ttu-id="da085-285">これらの問題に対する責任は、サービスとサービスメッシュレイヤーの間で分担されます。</span><span class="sxs-lookup"><span data-stu-id="da085-285">It moves the responsibility for these concerns out of the services and into the service mesh layer.</span></span> <span data-ttu-id="da085-286">Dapr と同様に、サービスメッシュもサイドカーアーキテクチャに従います。</span><span class="sxs-lookup"><span data-stu-id="da085-286">Like Dapr, a service mesh also follows a sidecar architecture.</span></span>

<span data-ttu-id="da085-287">図2-8 は、サービスメッシュテクノロジを実装するアプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-287">Figure 2-8 shows an application that implements service mesh technology.</span></span>

![サービスメッシュ](./media/dapr-at-20000-feet/service-mesh-with-side-car.png)

<span data-ttu-id="da085-289">**図 2-8**.</span><span class="sxs-lookup"><span data-stu-id="da085-289">**Figure 2-8**.</span></span> <span data-ttu-id="da085-290">サイドカーを使用したサービスメッシュ。</span><span class="sxs-lookup"><span data-stu-id="da085-290">Service mesh with a side car.</span></span>

<span data-ttu-id="da085-291">前の図は、各サービスと共に実行されるプロキシによってメッセージが傍受される方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-291">The previous figure shows how messages are intercepted by a proxy that runs alongside each service.</span></span> <span data-ttu-id="da085-292">各プロキシは、サービスに固有のトラフィックルールを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="da085-292">Each proxy can be configured with traffic rules specific to the service.</span></span> <span data-ttu-id="da085-293">メッセージを認識し、サービスや外部との間でルーティングできます。</span><span class="sxs-lookup"><span data-stu-id="da085-293">It understands messages and can route them across your services and the outside world.</span></span>

<span data-ttu-id="da085-294">この質問は、「サービスメッシュが Dapr であるか」となります。</span><span class="sxs-lookup"><span data-stu-id="da085-294">So the question becomes, "Is Dapr a service mesh?".</span></span>

<span data-ttu-id="da085-295">どちらもサイドカーアーキテクチャを使用しますが、各テクノロジの目的は異なります。</span><span class="sxs-lookup"><span data-stu-id="da085-295">While both use a sidecar architecture, each technology has a different purpose.</span></span> <span data-ttu-id="da085-296">Dapr は、分散アプリケーション機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-296">Dapr provides distributed application features.</span></span> <span data-ttu-id="da085-297">サービスメッシュには、専用のネットワークインフラストラクチャレイヤーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="da085-297">A service mesh provides a dedicated network infrastructure layer.</span></span>

<span data-ttu-id="da085-298">それぞれが異なるレベルで動作するため、両方とも同じアプリケーションで連携できます。</span><span class="sxs-lookup"><span data-stu-id="da085-298">As each works at a different level, both can work together in the same application.</span></span> <span data-ttu-id="da085-299">たとえば、サービスメッシュは、サービス間のネットワーク通信を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-299">For example, a service mesh could provide networking communication between services.</span></span> <span data-ttu-id="da085-300">Dapr は、状態管理やアクターサービスなどのアプリケーションサービスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="da085-300">Dapr could provide application services such as state management or actor services.</span></span>

<span data-ttu-id="da085-301">図2-9 は、Dapr とサービスメッシュテクノロジの両方を実装するアプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="da085-301">Figure 2-9 shows an application that implements both Dapr and service mesh technology.</span></span>

![Dapr とサービスメッシュの組み合わせ](./media/dapr-at-20000-feet/dapr-and-service-mesh.png)

<span data-ttu-id="da085-303">**図 2-9**.</span><span class="sxs-lookup"><span data-stu-id="da085-303">**Figure 2-9**.</span></span> <span data-ttu-id="da085-304">Dapr とサービスメッシュの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="da085-304">Dapr and service mesh together.</span></span>

<span data-ttu-id="da085-305">書籍「 [Learning Dapr](https://www.amazon.com/Learning-Dapr-Building-Distributed-Applications/dp/1492072427/ref=sr_1_1?dchild=1&keywords=dapr&qid=1604794794&sr=8-1), Authors Haishi Bai And Yaron Schneider」では、dapr とサービスメッシュの統合について説明しています。</span><span class="sxs-lookup"><span data-stu-id="da085-305">In the book, [Learning Dapr](https://www.amazon.com/Learning-Dapr-Building-Distributed-Applications/dp/1492072427/ref=sr_1_1?dchild=1&keywords=dapr&qid=1604794794&sr=8-1), authors Haishi Bai and Yaron Schneider, cover the integration of Dapr and service mesh.</span></span>

## <a name="summary"></a><span data-ttu-id="da085-306">まとめ</span><span class="sxs-lookup"><span data-stu-id="da085-306">Summary</span></span>

<span data-ttu-id="da085-307">この章では、分散アプリケーションランタイムである Dapr について紹介しました。</span><span class="sxs-lookup"><span data-stu-id="da085-307">This chapter introduced you to Dapr, a Distributed Application Runtime.</span></span>

<span data-ttu-id="da085-308">Dapr は、お客様とオープンソースコミュニティとの密接な共同作業により、Microsoft がスポンサーとするオープンソースプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="da085-308">Dapr is an open-source project sponsored by Microsoft with close collaboration from customers and the open-source community.</span></span>

<span data-ttu-id="da085-309">Dapr は、中核となる分散マイクロサービスアプリケーションの本質的な複雑さを軽減するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="da085-309">At its core, Dapr helps reduce the inherent complexity of distributed microservice applications.</span></span> <span data-ttu-id="da085-310">これは、ブロック Api の構築の概念に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="da085-310">It's built upon a concept of building block APIs.</span></span> <span data-ttu-id="da085-311">Dapr ビルディングブロックは、状態管理、サービス間の呼び出し、発行/サブスクライブメッセージングなどの一般的な分散アプリケーション機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="da085-311">Dapr building blocks expose common distributed application capabilities, such as state management, service-to-service invocation, and pub/sub messaging.</span></span> <span data-ttu-id="da085-312">Dapr コンポーネントは、構成要素の下に配置され、各機能の具象実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="da085-312">Dapr components lie beneath the building blocks and provide the concrete implementation for each capability.</span></span> <span data-ttu-id="da085-313">アプリケーションは、構成ファイルを介してさまざまなコンポーネントにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="da085-313">Applications bind to various components through configuration files.</span></span>

<span data-ttu-id="da085-314">次の章では、アプリケーションでの Dapr の使用方法について、実践的な実践的な指示を提供しています。</span><span class="sxs-lookup"><span data-stu-id="da085-314">In the next chapters, we present practical, hands-on instruction on how to use Dapr in your applications.</span></span>

### <a name="references"></a><span data-ttu-id="da085-315">リファレンス</span><span class="sxs-lookup"><span data-stu-id="da085-315">References</span></span>

- [<span data-ttu-id="da085-316">Dapr のドキュメント</span><span class="sxs-lookup"><span data-stu-id="da085-316">Dapr documentation</span></span>](https://dapr.io/)
- [<span data-ttu-id="da085-317">Dapr の学習</span><span class="sxs-lookup"><span data-stu-id="da085-317">Learning Dapr</span></span>](https://www.amazon.com/Learning-Dapr-Building-Distributed-Applications/dp/1492072427/ref=sr_1_1?dchild=1&keywords=dapr&qid=1604794794&sr=8-1)
- [<span data-ttu-id="da085-318">.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="da085-318">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)
- [<span data-ttu-id="da085-319">Azure 向け Cloud-Native .NET アプリの設計</span><span class="sxs-lookup"><span data-stu-id="da085-319">Architecting Cloud-Native .NET Apps for Azure</span></span>](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf)

> [!div class="step-by-step"]
> <span data-ttu-id="da085-320">[前へ](the-world-is-distributed.md)
> [次へ](getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="da085-320">[Previous](the-world-is-distributed.md)
[Next](getting-started.md)</span></span>
