---
title: Dapr 状態管理構成ブロック
description: 状態管理のビルディングブロック、その機能、利点、およびその適用方法の説明。
author: amolenk
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: 05daf18ece1da377f3d5d6a91c4839f196f14f80
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401427"
---
# <a name="the-dapr-state-management-building-block"></a><span data-ttu-id="90e4b-103">Dapr 状態管理構成ブロック</span><span class="sxs-lookup"><span data-stu-id="90e4b-103">The Dapr state management building block</span></span>

<span data-ttu-id="90e4b-104">分散アプリケーションは、独立したサービスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-104">Distributed applications are composed of independent services.</span></span> <span data-ttu-id="90e4b-105">各サービスはステートレスである必要がありますが、一部のサービスでは、ビジネス操作を完了するために状態を追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-105">While each service should be stateless, some services must track state to complete business operations.</span></span> <span data-ttu-id="90e4b-106">E コマースサイトのショッピングバスケットサービスについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="90e4b-106">Consider a shopping basket service for an e-Commerce site.</span></span> <span data-ttu-id="90e4b-107">サービスが状態を追跡できない場合、顧客は web サイトを離れることによって買い物かごのコンテンツを無駄にする可能性があり、その結果、販売が失われ、カスタマーエクスペリエンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-107">If the service can't track state, the customer could loose the shopping basket content by leaving the website, resulting in a lost sale and an unhappy customer experience.</span></span> <span data-ttu-id="90e4b-108">これらのシナリオでは、状態を分散状態ストアに永続化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-108">For these scenarios, state needs to be persisted to a distributed state store.</span></span> <span data-ttu-id="90e4b-109">[Dapr state management ビルディングブロック](https://docs.dapr.io/developing-applications/building-blocks/state-management/)は、状態の追跡を簡略化し、さまざまなデータストア間で高度な機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-109">The [Dapr state management building block](https://docs.dapr.io/developing-applications/building-blocks/state-management/) simplifies state tracking and offers advanced features across various data stores.</span></span>

<span data-ttu-id="90e4b-110">State management ビルディングブロックを試すには、 [第3章のカウンタアプリケーションサンプル](getting-started.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90e4b-110">To try out the state management building block, have a look at the [counter application sample in chapter 3](getting-started.md).</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="90e4b-111">解決方法</span><span class="sxs-lookup"><span data-stu-id="90e4b-111">What it solves</span></span>

<span data-ttu-id="90e4b-112">分散アプリケーションの状態を追跡することは困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-112">Tracking state in a distributed application can be challenging.</span></span> <span data-ttu-id="90e4b-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-113">For example:</span></span>

- <span data-ttu-id="90e4b-114">アプリケーションによっては、さまざまな種類のデータストアが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-114">The application may require different types of data stores.</span></span>
- <span data-ttu-id="90e4b-115">データへのアクセスやデータの更新には、異なる一貫性レベルが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-115">Different consistency levels may be required for accessing and updating data.</span></span>
- <span data-ttu-id="90e4b-116">複数のユーザーが同時にデータを更新して、競合の解決が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-116">Multiple users may update data at the same time, requiring  conflict resolution.</span></span>
- <span data-ttu-id="90e4b-117">サービスは、データストアとの対話中に発生する [一時的なエラー](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) をすべて再試行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-117">Services must retry any short-lived [transient errors](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) that  occur while interacting with the data store.</span></span>

<span data-ttu-id="90e4b-118">Dapr state management ビルディングブロックは、これらの課題に対処します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-118">The Dapr state management building block addresses these challenges.</span></span> <span data-ttu-id="90e4b-119">依存関係がない追跡状態や、サードパーティのストレージ Sdk の学習曲線を合理化します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-119">It streamlines tracking state without dependencies or a learning curve on third-party storage SDKs.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90e4b-120">Dapr 状態管理には、 [キー/値](/azure/architecture/guide/technology-choices/data-store-overview#keyvalue-stores) API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-120">Dapr state management offers a [key/value](/azure/architecture/guide/technology-choices/data-store-overview#keyvalue-stores) API.</span></span> <span data-ttu-id="90e4b-121">この機能は、リレーショナルデータストレージまたはグラフデータストレージをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="90e4b-121">The feature doesn't support relational or graph data storage.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="90e4b-122">しくみ</span><span class="sxs-lookup"><span data-stu-id="90e4b-122">How it works</span></span>

<span data-ttu-id="90e4b-123">アプリケーションは Dapr サイドカーとやり取りして、キー/値データを格納および取得します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-123">The application interacts with a Dapr sidecar to store and retrieve key/value data.</span></span> <span data-ttu-id="90e4b-124">内部的には、サイドカー API はデータを永続化するために、構成可能な状態ストアコンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-124">Under the hood, the sidecar API consumes a configurable state store component to persist data.</span></span> <span data-ttu-id="90e4b-125">開発者は、Azure Cosmos DB、SQL Server、Cassandra など、 [サポートされている状態ストア](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/) のコレクションから選択できます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-125">Developers can choose from a growing collection of [supported state stores](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/) that include Azure Cosmos DB, SQL Server, and Cassandra.</span></span>

<span data-ttu-id="90e4b-126">API は、HTTP または gRPC を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-126">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="90e4b-127">次の URL を使用して HTTP API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-127">Use the following URL to call the HTTP API:</span></span>

```http
http://localhost:<dapr-port>/v1.0/state/<store-name>/
```

- <span data-ttu-id="90e4b-128">`<dapr-port>`: Dapr がリッスンする HTTP ポート。</span><span class="sxs-lookup"><span data-stu-id="90e4b-128">`<dapr-port>`: the HTTP port that Dapr listens on.</span></span>
- <span data-ttu-id="90e4b-129">`<store-name>`: 使用する状態ストアコンポーネントの名前。</span><span class="sxs-lookup"><span data-stu-id="90e4b-129">`<store-name>`: the name of the state store component to use.</span></span>

<span data-ttu-id="90e4b-130">図5-1 は、Dapr が有効なショッピングバスケットサービスが、という名前の Dapr 状態ストアコンポーネントを使用してキーと値のペアを格納する方法を示して `statestore` います。</span><span class="sxs-lookup"><span data-stu-id="90e4b-130">Figure 5-1 shows how a Dapr-enabled shopping basket service stores a key/value pair using the Dapr state store component named `statestore`.</span></span>

![Dapr 状態ストアにキーと値のペアを格納する図。](media/state-management/state-management-flow.png)

<span data-ttu-id="90e4b-132">**図 5-1**.</span><span class="sxs-lookup"><span data-stu-id="90e4b-132">**Figure 5-1**.</span></span> <span data-ttu-id="90e4b-133">Dapr 状態ストアにキーと値のペアを格納する。</span><span class="sxs-lookup"><span data-stu-id="90e4b-133">Storing a key/value pair in a Dapr state store.</span></span>

<span data-ttu-id="90e4b-134">前の図の手順を確認してください。</span><span class="sxs-lookup"><span data-stu-id="90e4b-134">Note the steps in the previous figure:</span></span>

1. <span data-ttu-id="90e4b-135">バスケットサービスは、Dapr サイドカーで状態管理 API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-135">The basket service calls the state management API on the Dapr sidecar.</span></span> <span data-ttu-id="90e4b-136">要求の本文は、複数のキーと値のペアを含むことができる JSON 配列を囲みます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-136">The body of the request encloses a JSON array that can contain multiple key/value pairs.</span></span>
1. <span data-ttu-id="90e4b-137">Dapr サイドカーは、コンポーネント構成ファイルに基づいて状態ストアを決定します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-137">The Dapr sidecar determines the state store based on the component configuration file.</span></span> <span data-ttu-id="90e4b-138">この例では、Redis cache の状態ストアです。</span><span class="sxs-lookup"><span data-stu-id="90e4b-138">In this case, it's a Redis cache state store.</span></span>
1. <span data-ttu-id="90e4b-139">サイドカーは、Redis cache にデータを永続化します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-139">The sidecar persists the data to the Redis cache.</span></span>

<span data-ttu-id="90e4b-140">格納されたデータの取得は、同様の API 呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="90e4b-140">Retrieving the stored data is a similar API call.</span></span> <span data-ttu-id="90e4b-141">次の例では、 *curl* コマンドは dapr サイドカー API を呼び出してデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-141">In the example below, a *curl* command retrieves the data by calling the Dapr sidecar API:</span></span>

```console
curl http://localhost:3500/v1.0/state/statestore/basket1
```

<span data-ttu-id="90e4b-142">コマンドは、次のように、格納されている状態を応答の本文に返します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-142">The command returns the stored state in the response body:</span></span>

```json
{
  "items": [
    {
      "itemId": "DaprHoodie",
      "quantity": 1
    }
  ],
  "customerId": 1
}
```

<span data-ttu-id="90e4b-143">以下のセクションでは、state management ビルディングブロックの高度な機能を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-143">The following sections explain how to use the more advanced features of the state management building block.</span></span>

### <a name="consistency"></a><span data-ttu-id="90e4b-144">一貫性</span><span class="sxs-lookup"><span data-stu-id="90e4b-144">Consistency</span></span>

<span data-ttu-id="90e4b-145">[CAP 定理](https://en.wikipedia.org/wiki/CAP_theorem)は、状態を格納する分散システムに適用される一連の原則です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-145">The [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem) is a set of principles that apply to distributed systems that store state.</span></span> <span data-ttu-id="90e4b-146">図5-2 は、キャップ定理の3つのプロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-146">Figure 5-2 shows the three properties of the CAP theorem.</span></span>

![キャップ定理。](media/state-management/cap-theorem.png)

<span data-ttu-id="90e4b-148">**図 5-2**</span><span class="sxs-lookup"><span data-stu-id="90e4b-148">**Figure 5-2**.</span></span> <span data-ttu-id="90e4b-149">キャップ定理。</span><span class="sxs-lookup"><span data-stu-id="90e4b-149">The CAP theorem.</span></span>

<span data-ttu-id="90e4b-150">定理は、分散データシステムが整合性、可用性、およびパーティションの許容範囲のトレードオフを提供していることを示しています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-150">The theorem states that distributed data systems offer a trade-off between consistency, availability, and partition tolerance.</span></span> <span data-ttu-id="90e4b-151">また、すべてのデータストアは、次 *の3つのプロパティのうち2つ* だけを保証できます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-151">And, that any datastore can only *guarantee two of the three properties*:</span></span>

- <span data-ttu-id="90e4b-152">*整合性* (**C**)。</span><span class="sxs-lookup"><span data-stu-id="90e4b-152">*Consistency* (**C**).</span></span> <span data-ttu-id="90e4b-153">すべてのレプリカが更新されるまで、システムが要求をブロックする必要がある場合でも、クラスター内のすべてのノードが最新のデータで応答します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-153">Every node in the cluster responds with the most recent data, even if the system must block the request until all replicas update.</span></span> <span data-ttu-id="90e4b-154">現在更新中の項目に対して "一貫性のあるシステム" を照会した場合、すべてのレプリカが正常に更新されるまで応答は返されません。</span><span class="sxs-lookup"><span data-stu-id="90e4b-154">If you query a "consistent system" for an item that is currently updating, you won't get a response until all replicas successfully update.</span></span> <span data-ttu-id="90e4b-155">ただし、常に最新のデータを受け取ることになります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-155">However, you'll always receive the most current data.</span></span>

- <span data-ttu-id="90e4b-156">*可用性* (**A**)。</span><span class="sxs-lookup"><span data-stu-id="90e4b-156">*Availability* (**A**).</span></span> <span data-ttu-id="90e4b-157">すべてのノードは、応答が最新のデータではない場合でも、直ちに応答を返します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-157">Every node returns an immediate response, even if that response isn't the most recent data.</span></span> <span data-ttu-id="90e4b-158">更新中の項目に対して "使用可能なシステム" を照会すると、その時点でサービスが提供できる最適な回答が得られます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-158">If you query an "available system" for an item that is updating, you'll get the best possible answer the service can provide at that moment.</span></span>

- <span data-ttu-id="90e4b-159">*パーティションの許容範囲* (**P**)。</span><span class="sxs-lookup"><span data-stu-id="90e4b-159">*Partition Tolerance* (**P**).</span></span> <span data-ttu-id="90e4b-160">レプリケートされたデータノードで障害が発生した場合や、他のレプリケートされたデータノードとの接続が失われた場合でも、システムの動作が保証されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-160">Guarantees the system continues to operate even if a replicated data node fails or loses connectivity with other replicated data nodes.</span></span>

<span data-ttu-id="90e4b-161">分散アプリケーションは、 **P** プロパティを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-161">Distributed applications must handle the **P** property.</span></span> <span data-ttu-id="90e4b-162">サービスがネットワーク呼び出しを使用して相互に通信するため、ネットワークの中断 (**P**) が発生します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-162">As services communicate among each other with network calls, network disruptions (**P**) will occur.</span></span> <span data-ttu-id="90e4b-163">この点を念頭に置いて、分散アプリケーションは **AP** または **CP** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-163">With that in mind, distributed applications must either be **AP** or **CP**.</span></span>

<span data-ttu-id="90e4b-164">**AP** アプリケーションは、整合性を超える可用性を選択します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-164">**AP** applications choose availability over consistency.</span></span> <span data-ttu-id="90e4b-165">Dapr は、 **最終的な整合性** 戦略でこの選択をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-165">Dapr supports this choice with its **eventual consistency** strategy.</span></span> <span data-ttu-id="90e4b-166">複数のレプリカに冗長データを格納する Azure CosmosDB など、基になるデータストアについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="90e4b-166">Consider an underlying data store, such as Azure CosmosDB, which stores redundant data on multiple replicas.</span></span> <span data-ttu-id="90e4b-167">最終的な整合性を確保するために、状態ストアは更新を1つのレプリカに書き込み、クライアントとの書き込み要求を完了します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-167">With eventual consistency, the state store writes the update to one replica and completes the write request with the client.</span></span> <span data-ttu-id="90e4b-168">この時間が経過すると、ストアはレプリカを非同期的に更新します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-168">After this time, the store will asynchronously update its replicas.</span></span> <span data-ttu-id="90e4b-169">読み取り要求では、最新の更新を受信していないレプリカも含め、任意のレプリカからデータを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-169">Read requests can return data from any of the replicas, including those replicas that haven't yet received the latest update.</span></span>

<span data-ttu-id="90e4b-170">**CP** アプリケーションは、可用性よりも整合性を選択します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-170">**CP** applications choose consistency over availability.</span></span> <span data-ttu-id="90e4b-171">Dapr は、 **強力な整合性** 戦略でこの選択をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-171">Dapr supports this choice with its **strong consistency** strategy.</span></span> <span data-ttu-id="90e4b-172">このシナリオでは、書き込み要求を完了 *する前に*、必要なレプリカ *を (場合* によっては *クォーラム* として) 同期的に更新します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-172">In this scenario, the state store will synchronously update *all* (or, in some cases, a *quorum* of) required replicas *before* completing the write request.</span></span> <span data-ttu-id="90e4b-173">読み取り操作では、レプリカ間で常に最新のデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-173">Read operations will return the most up-to-date data consistently across replicas.</span></span>

<span data-ttu-id="90e4b-174">状態操作の一貫性レベルは、操作に *整合性ヒント* をアタッチすることによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-174">The consistency level for a state operation is specified by attaching a *consistency hint* to the operation.</span></span> <span data-ttu-id="90e4b-175">次の *curl* コマンドは、 `Hello=World` 厳密な整合性ヒントを使用して、キーと値のペアを状態ストアに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-175">The following *curl* command writes a `Hello=World` key/value pair to a state store using a strong consistency hint:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        {
          "key": "Hello",
          "value": "World",
          "options": {
            "consistency": "strong"
          }
        }
      ]'
```

> [!IMPORTANT]
> <span data-ttu-id="90e4b-176">操作にアタッチされている整合性ヒントを満たすには、Dapr 状態ストアコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-176">It is up to the Dapr state store component to fulfill the consistency hint attached to the operation.</span></span> <span data-ttu-id="90e4b-177">すべてのデータストアが両方の整合性レベルをサポートしているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="90e4b-177">Not all data stores support both consistency levels.</span></span> <span data-ttu-id="90e4b-178">整合性ヒントが設定されていない場合、既定の動作は **最終的** にはになります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-178">If no consistency hint is set, the default behavior is **eventual**.</span></span>

### <a name="concurrency"></a><span data-ttu-id="90e4b-179">コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="90e4b-179">Concurrency</span></span>

<span data-ttu-id="90e4b-180">マルチユーザーアプリケーションでは、複数のユーザーが同時に (同時に) 同じデータを更新する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-180">In a multi-user application, there's a chance that multiple users will update the same data concurrently (at the same time).</span></span> <span data-ttu-id="90e4b-181">Dapr は、オプティミスティック同時実行制御 (OCC) をサポートして競合を管理します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-181">Dapr supports optimistic concurrency control (OCC) to manage conflicts.</span></span> <span data-ttu-id="90e4b-182">OCC は、ユーザーがデータのさまざまな部分を操作するため、更新の競合が発生することがないという前提に基づいています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-182">OCC is based on an assumption that update conflicts are uncommon because users work on different parts of the data.</span></span> <span data-ttu-id="90e4b-183">更新が成功し、そうでない場合は再試行する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-183">It's more efficient to assume an update will succeed and retry if it doesn't.</span></span> <span data-ttu-id="90e4b-184">別の方法として、ペシミスティックロックを実装すると、実行時間の長いロックによってパフォーマンスが低下し、データ競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-184">The alternative, implementing pessimistic locking, can affect performance with long-running locking causing data contention.</span></span>

<span data-ttu-id="90e4b-185">Dapr は、Etag を使用したオプティミスティック同時実行制御 (OCC) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-185">Dapr supports optimistic concurrency control (OCC) using ETags.</span></span> <span data-ttu-id="90e4b-186">ETag は、格納されているキーと値のペアの特定のバージョンに関連付けられた値です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-186">An ETag is a value associated with a specific version of a stored key/value pair.</span></span> <span data-ttu-id="90e4b-187">キーと値のペアが更新されるたびに、ETag 値も更新されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-187">Each time a key/value pair updates, the ETag value updates as well.</span></span> <span data-ttu-id="90e4b-188">クライアントがキーと値のペアを取得すると、応答には現在の ETag の値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-188">When a client retrieves a key/value pair, the response includes the current ETag value.</span></span> <span data-ttu-id="90e4b-189">クライアントは、キーと値のペアを更新または削除するときに、その ETag 値を要求本文に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-189">When a client updates or deletes a key/value pair, it must send that ETag value back in the request body.</span></span> <span data-ttu-id="90e4b-190">別のクライアントがその間にデータを更新した場合、Etag は一致せず、要求は失敗します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-190">If another client has updated the data in the meantime, the ETags won't match and the request will fail.</span></span> <span data-ttu-id="90e4b-191">この時点で、クライアントは更新されたデータを取得し、再度変更を加えて、更新を再送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-191">At this point, the client must retrieve the updated data, make the change again, and resubmit the update.</span></span> <span data-ttu-id="90e4b-192">この方法は **、最初の書き込み-優先** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-192">This strategy is called **first-write-wins**.</span></span>

<span data-ttu-id="90e4b-193">Dapr は、 **最終書き込み優先** 戦略もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-193">Dapr also supports a **last-write-wins** strategy.</span></span> <span data-ttu-id="90e4b-194">この方法では、クライアントは ETag を書き込み要求にアタッチしません。</span><span class="sxs-lookup"><span data-stu-id="90e4b-194">With this approach, the client doesn't attach an ETag to the write request.</span></span> <span data-ttu-id="90e4b-195">セッション中に基になる値が変更された場合でも、状態ストアコンポーネントは常に更新を許可します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-195">The state store component will always allow the update, even if the underlying value has changed during the session.</span></span> <span data-ttu-id="90e4b-196">最後の書き込み-wins は、データの競合が少ない高スループットの書き込みシナリオに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-196">Last-write-wins is useful for high-throughput write scenarios with low data contention.</span></span> <span data-ttu-id="90e4b-197">また、ユーザーの不定期な更新を上書きすることもできます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-197">As well, overwriting an occasional user update can be tolerated.</span></span>

### <a name="transactions"></a><span data-ttu-id="90e4b-198">トランザクション</span><span class="sxs-lookup"><span data-stu-id="90e4b-198">Transactions</span></span>

<span data-ttu-id="90e4b-199">Dapr は、トランザクションとして実装された単一の操作として、データストアに *複数項目の変更* を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-199">Dapr can write *multi-item changes* to a data store as a single operation implemented as a transaction.</span></span> <span data-ttu-id="90e4b-200">この機能は、 [ACID](https://en.wikipedia.org/wiki/ACID) トランザクションをサポートするデータストアに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-200">This functionality is only available for data stores that support [ACID](https://en.wikipedia.org/wiki/ACID) transactions.</span></span> <span data-ttu-id="90e4b-201">このドキュメントの執筆時点では、Redis、MongoDB、PostgreSQL、SQL Server、Azure CosmosDB が含まれています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-201">At the time of this writing, these stores include Redis, MongoDB, PostgreSQL, SQL Server, and Azure CosmosDB.</span></span>

<span data-ttu-id="90e4b-202">次の例では、複数項目の操作が1つのトランザクションの状態ストアに送信されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-202">In the example below, a multi-item operation is sent to the state store in a single transaction.</span></span> <span data-ttu-id="90e4b-203">トランザクションをコミットするには、すべての操作を成功させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-203">All operations must succeed for the transaction to commit.</span></span> <span data-ttu-id="90e4b-204">1つ以上の操作が失敗した場合、トランザクション全体がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-204">If one or more of the operations fail, the entire transaction rolls back.</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name>/transaction \
  -H "Content-Type: application/json" \
  -d '{
        "operations": [
          {
            "operation": "upsert",
            "request": { "key": "Key1", "value": "Value1"
            }
          },
          {
            "operation": "delete",
            "request": { "key": "Key2" }
          }
        ]
      }'
```

<span data-ttu-id="90e4b-205">トランザクションをサポートしていないデータストアの場合、複数のキーを1つの要求として送信できます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-205">For data stores that don't support transactions, multiple keys can still be sent as a single request.</span></span> <span data-ttu-id="90e4b-206">次の例は、 **一括** 書き込み操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-206">The following example shows a **bulk** write operation:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        { "key": "Key1", "value": "Value1" },
        { "key": "Key2", "value": "Value2" }
      ]'
```

<span data-ttu-id="90e4b-207">一括操作の場合、Dapr は各キー/値ペアの更新をデータストアに個別の要求として送信します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-207">For bulk operations, Dapr will submit each key/value pair update as a separate request to the data store.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="90e4b-208">Dapr .NET SDK を使用する</span><span class="sxs-lookup"><span data-stu-id="90e4b-208">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="90e4b-209">Dapr .NET SDK は、.NET Core プラットフォームの言語固有のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-209">The Dapr .NET SDK provides language-specific support for .NET Core platform.</span></span> <span data-ttu-id="90e4b-210">開発者は、 `DaprClient` [第3章](getting-started.md) で導入されたクラスを使用して、データの読み取りと書き込みを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-210">Developers can use the `DaprClient` class introduced in [chapter 3](getting-started.md) to read and write data.</span></span> <span data-ttu-id="90e4b-211">次の例は、メソッドを使用して `DaprClient.GetStateAsync<TValue>` 状態ストアからデータを読み取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-211">The following example shows how to use the `DaprClient.GetStateAsync<TValue>` method to read data from a state store.</span></span> <span data-ttu-id="90e4b-212">メソッドでは、 `statestore` パラメーターとして、ストア名、、およびキーが必要 `AMS` です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-212">The method expects the store name, `statestore`, and key, `AMS`, as parameters:</span></span>

```csharp
var weatherForecast = await daprClient.GetStateAsync<WeatherForecast>("statestore", "AMS");
```

<span data-ttu-id="90e4b-213">状態ストアにキーのデータが含まれていない場合、結果はになり `AMS` `default(WeatherForecast)` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-213">If the state store contains no data for key `AMS`, the result will be `default(WeatherForecast)`.</span></span>

<span data-ttu-id="90e4b-214">データをデータストアに書き込むには、メソッドを使用し `DaprClient.SaveStateAsync<TValue>` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-214">To write data to the data store, use the `DaprClient.SaveStateAsync<TValue>` method:</span></span>

```csharp
daprClient.SaveStateAsync("statestore", "AMS", weatherForecast);
```

<span data-ttu-id="90e4b-215">この例では、ETag 値が状態ストアコンポーネントに渡されないため、 **最後の書き込み優先** の方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-215">The example uses the **last-write-wins** strategy as an ETag value isn't passed to the state store component.</span></span> <span data-ttu-id="90e4b-216">**最初の書き込み優先** 戦略でオプティミスティック同時実行制御 (occ) を使用するには、最初にメソッドを使用して現在の ETag を取得し `DaprClient.GetStateAndETagAsync` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-216">To use optimistic concurrency control (OCC) with a **first-write-wins** strategy, first retrieve the current ETag using the `DaprClient.GetStateAndETagAsync` method.</span></span> <span data-ttu-id="90e4b-217">次に、更新された値を書き込み、メソッドを使用して取得した ETag に沿って渡し `DaprClient.TrySaveStateAsync` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-217">Then write the updated value and pass along the retrieved ETag using the `DaprClient.TrySaveStateAsync` method.</span></span>

```csharp
var (weatherForecast, etag) = await daprClient.GetStateAndETagAsync<WeatherForecast>("statestore", city);

// ... make some changes to the retrieved weather forecast

var result = await daprClient.TrySaveStateAsync("statestore", city, weatherForecast, etag);
```

<span data-ttu-id="90e4b-218">データが取得され `DaprClient.TrySaveStateAsync` た後、状態ストアでデータ (および関連する ETag) が変更されている場合、メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-218">The `DaprClient.TrySaveStateAsync` method fails when the data (and associated ETag) has been changed in the state store after the data was retrieved.</span></span> <span data-ttu-id="90e4b-219">メソッドは、呼び出しが成功したかどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-219">The method returns a boolean value to indicate whether the call succeeded.</span></span> <span data-ttu-id="90e4b-220">障害を処理するには、単に状態ストアから更新されたデータを再読み込みし、変更を加えてから更新を再送信します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-220">A strategy to handle the failure is to simply reload the updated data from the state store, make the change again, and resubmit the update.</span></span>

<span data-ttu-id="90e4b-221">データに対するその他の変更に関係なく書き込みが常に成功するようにするには、 **最終書き込み優先** 戦略を使用します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-221">If you always want a write to succeed regardless of other changes to the data, use the **last-write-wins** strategy.</span></span>

<span data-ttu-id="90e4b-222">SDK には、データを一括で取得したり、データを削除したり、トランザクションを実行したりする他の方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-222">The SDK provides other methods to retrieve data in bulk, delete data, and execute transactions.</span></span> <span data-ttu-id="90e4b-223">詳細については、 [Dapr .NET SDK リポジトリ](https://github.com/dapr/dotnet-sdk)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90e4b-223">For more information, see the [Dapr .NET SDK repository](https://github.com/dapr/dotnet-sdk).</span></span>

### <a name="aspnet-core-integration"></a><span data-ttu-id="90e4b-224">ASP.NET Core の統合</span><span class="sxs-lookup"><span data-stu-id="90e4b-224">ASP.NET Core integration</span></span>

<span data-ttu-id="90e4b-225">Dapr は、最新のクラウドベースの web アプリケーションを構築するためのクロスプラットフォームフレームワークである ASP.NET Core もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-225">Dapr also supports ASP.NET Core, a cross-platform framework for building modern cloud-based web applications.</span></span> <span data-ttu-id="90e4b-226">Dapr SDK は、状態管理機能を [ASP.NET Core モデルバインディング](/aspnet/core/mvc/models/model-binding) 機能に直接統合します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-226">The Dapr SDK integrates state management capabilities directly into the [ASP.NET Core model binding](/aspnet/core/mvc/models/model-binding) capabilities.</span></span> <span data-ttu-id="90e4b-227">構成は簡単です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-227">Configuration is simple.</span></span> <span data-ttu-id="90e4b-228">次の `IMVCBuilder.AddDapr` `.AddDapr` 例に示すように、クラスに拡張メソッドを追加してを追加し `Startup.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-228">Add the `IMVCBuilder.AddDapr` by appending the `.AddDapr` extension method in your `Startup.cs` class as shown in the next example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers().AddDapr();
}
```

<span data-ttu-id="90e4b-229">構成が完了すると、Dapr は、ASP.NET Core 属性を使用して、キーと値のペアをコントローラーアクションに直接挿入でき `FromState` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-229">Once configured, Dapr can inject a key/value pair directly into a controller action using the ASP.NET Core `FromState` attribute.</span></span> <span data-ttu-id="90e4b-230">オブジェクトを参照する `DaprClient` 必要はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="90e4b-230">Referencing the `DaprClient` object is no longer necessary.</span></span> <span data-ttu-id="90e4b-231">次の例は、特定の都市の天気予報を返す Web API を示しています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-231">The next example shows a Web API that returns the weather forecast for a given city:</span></span>

```csharp
[HttpGet("{city}")]
public ActionResult<WeatherForecast> Get([FromState("statestore", "city")] StateEntry<WeatherForecast> forecast)
{
    if (forecast.Value == null)
    {
      return NotFound();
    }

    return forecast.Value;
}
```

<span data-ttu-id="90e4b-232">この例では、コントローラーは属性を使用して天気予報を読み込み `FromState` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-232">In the example, the controller loads the weather forecast using the `FromState` attribute.</span></span> <span data-ttu-id="90e4b-233">最初の属性パラメーターは、状態ストア () です `statestore` 。</span><span class="sxs-lookup"><span data-stu-id="90e4b-233">The first attribute parameter is the state store, `statestore`.</span></span> <span data-ttu-id="90e4b-234">2番目の属性パラメーターは、 `city` 状態キーを取得する [ルートテンプレート](/aspnet/core/mvc/controllers/routing#route-templates) 変数の名前です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-234">The second attribute parameter, `city`, is the name of the [route template](/aspnet/core/mvc/controllers/routing#route-templates) variable to get the state key.</span></span> <span data-ttu-id="90e4b-235">2番目のパラメーターを省略した場合は、バインドされたメソッドパラメーター () の名前を使用して `forecast` ルートテンプレート変数が検索されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-235">If you omit the second parameter, the name of the bound method parameter (`forecast`) is used to look up the route template variable.</span></span>

<span data-ttu-id="90e4b-236">クラスには `StateEntry` 、1つのキーと値のペアに対して取得されるすべての情報 (、、、および) のプロパティが含まれてい `StoreName` `Key` `Value` `ETag` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-236">The `StateEntry` class contains properties for all the information that is retrieved for a single key/value pair: `StoreName`, `Key`, `Value`, and `ETag`.</span></span> <span data-ttu-id="90e4b-237">ETag は、オプティミスティック同時実行制御 (OCC) 戦略を実装する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-237">The ETag is useful for implementing optimistic concurrency control (OCC) strategy.</span></span> <span data-ttu-id="90e4b-238">クラスには、インスタンスを必要とせずに取得したキー/値データを削除または更新するメソッドも用意されて `DaprClient` います。</span><span class="sxs-lookup"><span data-stu-id="90e4b-238">The class also provides methods to delete or update retrieved key/value data without requiring a `DaprClient` instance.</span></span> <span data-ttu-id="90e4b-239">次の例では、 `TrySaveAsync` メソッドを使用して、OCC を使用して取得された気象予測を更新します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-239">In the next example, the `TrySaveAsync` method is used to update the retrieved weather forecast using OCC.</span></span>

```csharp
[HttpPut("{city}")]
public async Task Put(WeatherForecast updatedForecast, [FromState("statestore", "city")] StateEntry<WeatherForecast> currentForecast)
{
    // update cached current forecast with updated forecast passed into service endpoint
    currentForecast.Value = updatedForecast;

    // update state store
    var success = await currentForecast.TrySaveAsync();

    // ... check result
}
```

## <a name="state-store-components"></a><span data-ttu-id="90e4b-240">状態ストアのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="90e4b-240">State store components</span></span>

<span data-ttu-id="90e4b-241">このドキュメントの執筆時点では、Dapr は次のトランザクション状態ストアをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-241">At the time of this writing, Dapr provides support for the following transactional state stores:</span></span>

- <span data-ttu-id="90e4b-242">Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="90e4b-242">Azure CosmosDB</span></span>
- <span data-ttu-id="90e4b-243">Azure SQL Server</span><span class="sxs-lookup"><span data-stu-id="90e4b-243">Azure SQL Server</span></span>
- <span data-ttu-id="90e4b-244">MongoDB</span><span class="sxs-lookup"><span data-stu-id="90e4b-244">MongoDB</span></span>
- <span data-ttu-id="90e4b-245">PostgreSQL</span><span class="sxs-lookup"><span data-stu-id="90e4b-245">PostgreSQL</span></span>
- <span data-ttu-id="90e4b-246">Redis</span><span class="sxs-lookup"><span data-stu-id="90e4b-246">Redis</span></span>

<span data-ttu-id="90e4b-247">Dapr には、CRUD 操作をサポートするがトランザクション機能ではない状態ストアのサポートも含まれています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-247">Dapr also includes support for state stores that support CRUD operations, but not transactional capabilities:</span></span>

- <span data-ttu-id="90e4b-248">Aerospike</span><span class="sxs-lookup"><span data-stu-id="90e4b-248">Aerospike</span></span>
- <span data-ttu-id="90e4b-249">Azure Blob Storage</span><span class="sxs-lookup"><span data-stu-id="90e4b-249">Azure Blob Storage</span></span>
- <span data-ttu-id="90e4b-250">Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="90e4b-250">Azure Table Storage</span></span>
- <span data-ttu-id="90e4b-251">Cassandra</span><span class="sxs-lookup"><span data-stu-id="90e4b-251">Cassandra</span></span>
- <span data-ttu-id="90e4b-252">Cloudstate</span><span class="sxs-lookup"><span data-stu-id="90e4b-252">Cloudstate</span></span>
- <span data-ttu-id="90e4b-253">Couchbase</span><span class="sxs-lookup"><span data-stu-id="90e4b-253">Couchbase</span></span>
- <span data-ttu-id="90e4b-254">etcd</span><span class="sxs-lookup"><span data-stu-id="90e4b-254">etcd</span></span>
- <span data-ttu-id="90e4b-255">Google Cloud Firestore</span><span class="sxs-lookup"><span data-stu-id="90e4b-255">Google Cloud Firestore</span></span>
- <span data-ttu-id="90e4b-256">Hashicorp Consul</span><span class="sxs-lookup"><span data-stu-id="90e4b-256">Hashicorp Consul</span></span>
- <span data-ttu-id="90e4b-257">Hazelcast</span><span class="sxs-lookup"><span data-stu-id="90e4b-257">Hazelcast</span></span>
- <span data-ttu-id="90e4b-258">Memcached</span><span class="sxs-lookup"><span data-stu-id="90e4b-258">Memcached</span></span>
- <span data-ttu-id="90e4b-259">Zookeeper</span><span class="sxs-lookup"><span data-stu-id="90e4b-259">Zookeeper</span></span>

### <a name="configuration"></a><span data-ttu-id="90e4b-260">構成</span><span class="sxs-lookup"><span data-stu-id="90e4b-260">Configuration</span></span>

<span data-ttu-id="90e4b-261">自己ホスト型のローカル開発用に初期化された場合、Dapr は Redis を既定の状態ストアとして登録します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-261">When initialized for local, self-hosted development, Dapr registers Redis as the default state store.</span></span> <span data-ttu-id="90e4b-262">既定の状態ストア構成の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-262">Here's an example of the default state store configuration.</span></span> <span data-ttu-id="90e4b-263">既定の名前に注意して `statestore` ください。</span><span class="sxs-lookup"><span data-stu-id="90e4b-263">Note the default name, `statestore`:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

 > [!NOTE]
 > <span data-ttu-id="90e4b-264">多くの状態ストアは、別々の名前を持つ1つのアプリケーションに登録できます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-264">Many state stores can be registered to a single application each with a different name.</span></span>

<span data-ttu-id="90e4b-265">Redis 状態ストアには `redisHost` 、 `redisPassword` redis インスタンスに接続するためのメタデータとメタデータが必要です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-265">The Redis state store requires `redisHost` and `redisPassword` metadata to connect to the Redis instance.</span></span> <span data-ttu-id="90e4b-266">上の例では、Redis パスワード (既定では空の文字列) がプレーン文字列として格納されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-266">In the example above, the Redis password (which is an empty string by default) is stored as a plain string.</span></span> <span data-ttu-id="90e4b-267">ベストプラクティスとしては、クリアテキスト文字列を避け、常にシークレット参照を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="90e4b-267">The best practice is to avoid clear-text strings and always use secret references.</span></span> <span data-ttu-id="90e4b-268">シークレット管理の詳細については、 [第10章](secrets.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90e4b-268">To learn more about secret management, see [chapter 10](secrets.md).</span></span>

<span data-ttu-id="90e4b-269">もう1つのメタデータフィールドは、 `actorStateStore` 状態ストアをアクター構成ブロックで使用できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-269">The other metadata field, `actorStateStore`, indicates whether the state store can be consumed by the actors building block.</span></span>

### <a name="key-prefix-strategies"></a><span data-ttu-id="90e4b-270">キープレフィックス戦略</span><span class="sxs-lookup"><span data-stu-id="90e4b-270">Key prefix strategies</span></span>

<span data-ttu-id="90e4b-271">状態ストアコンポーネントを使用すると、キーと値のペアを基になるストアに格納するさまざまな方法が有効になります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-271">State store components enable different strategies to store key/value pairs in the underlying store.</span></span> <span data-ttu-id="90e4b-272">顧客が購入する品目を格納するショッピングバスケットサービスの例を思い出してください。</span><span class="sxs-lookup"><span data-stu-id="90e4b-272">Recall the earlier example of a shopping basket service storing items a customer wishes to purchase:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/statestore \
  -H "Content-Type: application/json" \
  -d '[{
        "key": "basket1",
        "value": {
          "customerId": 1,
          "items": [
            { "itemId": "DaprHoodie", "quantity": 1 }
          ]
        }
     }]'
```

<span data-ttu-id="90e4b-273">Redis コンソールツールを使用して、redis cache の内部を調べて、Redis 状態ストアコンポーネントがどのようにデータを永続化したかを確認します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-273">Using the Redis Console tool, look inside the Redis cache to see how the Redis state store component persisted the data:</span></span>

```
127.0.0.1:6379> KEYS *
1) "basketservice||basket1"

127.0.0.1:6379> HGETALL basketservice||basket1
1) "data"
2) "{\"items\":[{\"itemId\":\"DaprHoodie\",\"quantity\":1}],\"customerId\":1}"
3) "version"
4) "1"
```

<span data-ttu-id="90e4b-274">出力には、データの完全な Redis **キー** がとして表示され `basketservice||basket1` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-274">The output shows the full Redis **key** for the data as `basketservice||basket1`.</span></span> <span data-ttu-id="90e4b-275">既定では、Dapr は、 `application id` dapr インスタンス () のを `basketservice` キーのプレフィックスとして使用します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-275">By default, Dapr uses the `application id` of the Dapr instance (`basketservice`) as a prefix for the key.</span></span> <span data-ttu-id="90e4b-276">この名前付け規則を使用すると、複数の Dapr インスタンスで、キー名の競合を発生させずに同じデータストアを共有できます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-276">This naming convention enables multiple Dapr instances to share the same data store without key name collisions.</span></span> <span data-ttu-id="90e4b-277">開発者にとっては、 `application id` Dapr でアプリケーションを実行するときは常に同じを指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-277">For the developer, it's critical always to specify the same `application id` when running the application with Dapr.</span></span> <span data-ttu-id="90e4b-278">省略した場合、Dapr は一意のアプリケーション ID を生成します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-278">If omitted, Dapr will generate a unique application ID.</span></span> <span data-ttu-id="90e4b-279">が変更されると、 `application id` アプリケーションは前のキープレフィックスで格納された状態にアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-279">If the `application id` changes, the application can no longer access the state stored with the previous key prefix.</span></span>

<span data-ttu-id="90e4b-280">とは言うものの、状態ストアのコンポーネントファイルのメタデータフィールドで、キープレフィックスの *定数値* を構成することができ `keyPrefix` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-280">That said, it's possible to configure a *constant value* for the key prefix in the `keyPrefix` metadata field in the state store component file.</span></span> <span data-ttu-id="90e4b-281">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="90e4b-281">Consider the following example:</span></span>

```yaml
spec:
  metadata:
  - name: keyPrefix
  - value: MyPrefix
```

<span data-ttu-id="90e4b-282">定数キープレフィックスを使用すると、複数の Dapr アプリケーション間で状態ストアにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-282">A constant key prefix enables the state store to be accessed across multiple Dapr applications.</span></span> <span data-ttu-id="90e4b-283">さらに、を設定して、 `keyPrefix` `none` プレフィックスを完全に省略します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-283">What's more, setting the `keyPrefix` to `none` omits the prefix completely.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="90e4b-284">参照アプリケーション: eShopOnDapr</span><span class="sxs-lookup"><span data-stu-id="90e4b-284">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="90e4b-285">この書籍には、資格のある参照アプリケーションが含まれてい `eShopOnDapr` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-285">This book includes a reference application entitled `eShopOnDapr`.</span></span> <span data-ttu-id="90e4b-286">これは、以前の Microsoft マイクロサービス参照アプリケーションからモデル化さ `eShopOnContainers` れています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-286">It's modeled from an earlier Microsoft microservices reference application, `eShopOnContainers`.</span></span>

<span data-ttu-id="90e4b-287">元の [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) アーキテクチャは、インターフェイスを使用して `IBasketRepository` バスケットサービスのデータの読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="90e4b-287">The original [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) architecture used an `IBasketRepository` interface to read and write data for the basket service.</span></span> <span data-ttu-id="90e4b-288">クラスは、 `RedisBasketRepository` 基になるデータストアとして Redis を使用して実装を提供しました。</span><span class="sxs-lookup"><span data-stu-id="90e4b-288">The `RedisBasketRepository` class provided the implementation using Redis as the underlying data store:</span></span>

```csharp
public class RedisBasketRepository : IBasketRepository
{
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _database;

    public RedisBasketRepository(ConnectionMultiplexer redis)
    {
        _redis = redis;
        _database = redis.GetDatabase();
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        var data = await _database.StringGetAsync(customerId);

        if (data.IsNullOrEmpty)
        {
            return null;
        }

        return JsonConvert.DeserializeObject<CustomerBasket>(data);
    }

    // ...
}
```

<span data-ttu-id="90e4b-289">このコードでは、サードパーティの NuGet パッケージを使用し `StackExchange.Redis` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-289">This code uses the third-party `StackExchange.Redis` NuGet package.</span></span> <span data-ttu-id="90e4b-290">特定の顧客に対して買い物かごを読み込むには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-290">The following steps are required to load the shopping basket for a given customer:</span></span>

1. <span data-ttu-id="90e4b-291">を `ConnectionMultiplexer` コンストラクターに挿入します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-291">Inject a `ConnectionMultiplexer` into the constructor.</span></span> <span data-ttu-id="90e4b-292">は、 `ConnectionMultiplexer` ファイルの依存関係挿入フレームワークに登録され `Startup.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-292">The `ConnectionMultiplexer` is registered with the dependency injection framework in the `Startup.cs` file:</span></span>

   ```csharp
   services.AddSingleton<ConnectionMultiplexer>(sp =>
   {
       var settings = sp.GetRequiredService<IOptions<BasketSettings>>().Value;
       var configuration = ConfigurationOptions.Parse(settings.ConnectionString, true);
       configuration.ResolveDns = true;
       return ConnectionMultiplexer.Connect(configuration);
   });
   ```

1. <span data-ttu-id="90e4b-293">使用 `ConnectionMultiplexer` する各クラスにインスタンスを作成するには、を使用し `IDatabase` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-293">Use the `ConnectionMultiplexer` to create an `IDatabase` instance in each consuming class.</span></span>

1. <span data-ttu-id="90e4b-294">`IDatabase`キーとして指定されたを使用して Redis StringGet 呼び出しを実行するには、インスタンスを使用し `customerId` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-294">Use the `IDatabase` instance to execute a Redis StringGet call using the given `customerId` as the key.</span></span>

1. <span data-ttu-id="90e4b-295">データが Redis から読み込まれているかどうかを確認します。それ以外の場合は、を返し `null` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-295">Check if data is loaded from Redis; if not, return `null`.</span></span>

1. <span data-ttu-id="90e4b-296">Redis からオブジェクトにデータを逆シリアル化し、その `CustomerBasket` 結果を返します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-296">Deserialize the data from Redis to a `CustomerBasket` object and return the result.</span></span>

<span data-ttu-id="90e4b-297">更新された [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) 参照アプリケーションでは、クラスを新しい `DaprBasketRepository` クラスで置き換え `RedisBasketRepository` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-297">In the updated [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) reference application, a new `DaprBasketRepository` class replaces the `RedisBasketRepository` class:</span></span>

```csharp
public class DaprBasketRepository : IBasketRepository
{
    private const string StoreName = "eshop-basket-statestore";

    private readonly DaprClient _daprClient;

    public DaprBasketRepository(DaprClient daprClient)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));;
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        return await _daprClient.GetStateAsync<CustomerBasket>(StoreName, customerId);
    }

    // ...
}
```

<span data-ttu-id="90e4b-298">更新されたコードでは、Dapr .NET SDK を使用して、state management ビルディングブロックを使用してデータの読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="90e4b-298">The updated code uses the Dapr .NET SDK to read and write data using the state management building block.</span></span> <span data-ttu-id="90e4b-299">顧客向けにバスケットを読み込む新しい手順は、大幅に簡素化されています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-299">The new steps to load the basket for a customer are dramatically simplified:</span></span>

1. <span data-ttu-id="90e4b-300">を `DaprClient` コンストラクターに挿入します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-300">Inject a `DaprClient` into the constructor.</span></span> <span data-ttu-id="90e4b-301">は、 `DaprClient` ファイルの依存関係挿入フレームワークに登録され `Startup.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-301">The `DaprClient` is registered with the dependency injection framework in the `Startup.cs` file.</span></span>
1. <span data-ttu-id="90e4b-302">メソッドを使用し `DaprClient.GetStateAsync` て、構成済みの状態ストアから顧客の買い物かご項目を読み込み、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-302">Use the `DaprClient.GetStateAsync` method to load the customer's shopping basket items from the configured state store and return the result.</span></span>

<span data-ttu-id="90e4b-303">更新された実装では、引き続き Redis が基になるデータストアとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-303">The updated implementation still uses Redis as the underlying data store.</span></span> <span data-ttu-id="90e4b-304">しかし、Dapr は、 `StackExchange.Redis` アプリケーションから参照と複雑さを抽象化します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-304">But, Dapr abstracts the `StackExchange.Redis` references and complexity from the application.</span></span> <span data-ttu-id="90e4b-305">Dapr 構成ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="90e4b-305">A Dapr configuration file is all that's needed:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="90e4b-306">Dapr の実装により、基になるデータストアの変更も簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-306">The Dapr implementation also simplifies changing the underlying data store.</span></span> <span data-ttu-id="90e4b-307">たとえば、Azure Table Storage に切り替えるには、構成ファイルの内容のみを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-307">For example, switching to Azure Table Storage requires only changing the contents of the configuration file.</span></span> <span data-ttu-id="90e4b-308">コードに変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="90e4b-308">No code changes are necessary.</span></span>

## <a name="summary"></a><span data-ttu-id="90e4b-309">まとめ</span><span class="sxs-lookup"><span data-stu-id="90e4b-309">Summary</span></span>

<span data-ttu-id="90e4b-310">Dapr state management ビルディングブロックは、さまざまなデータストア間でキー/値データを格納するための API を提供します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-310">The Dapr state management building block offers an API for storing key/value data across various data stores.</span></span> <span data-ttu-id="90e4b-311">API では、次の機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90e4b-311">The API provides support for:</span></span>

- <span data-ttu-id="90e4b-312">一括操作</span><span class="sxs-lookup"><span data-stu-id="90e4b-312">Bulk operations</span></span>
- <span data-ttu-id="90e4b-313">強力で最終的な整合性</span><span class="sxs-lookup"><span data-stu-id="90e4b-313">Strong and eventual consistency</span></span>
- <span data-ttu-id="90e4b-314">オプティミスティック コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="90e4b-314">Optimistic concurrency control</span></span>
- <span data-ttu-id="90e4b-315">複数項目のトランザクション</span><span class="sxs-lookup"><span data-stu-id="90e4b-315">Multi-item transactions</span></span>

<span data-ttu-id="90e4b-316">.NET SDK は、.NET Core と ASP.NET Core の言語固有のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="90e4b-316">The .NET SDK provides language-specific support for .NET Core and ASP.NET Core.</span></span> <span data-ttu-id="90e4b-317">モデルバインディングの統合により、ASP.NET Core コントローラーアクションメソッドからの状態へのアクセスと更新が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="90e4b-317">Model binding integration simplifies accessing and updating state from ASP.NET Core controller action methods.</span></span>

<span data-ttu-id="90e4b-318">EShopOnDapr reference アプリケーションでは、Dapr 状態管理に移行する利点は明らかです。</span><span class="sxs-lookup"><span data-stu-id="90e4b-318">In the eShopOnDapr reference application, the benefits to moving to Dapr state management are clear:</span></span>

1. <span data-ttu-id="90e4b-319">新しい実装では、より少数のコード行が使用されます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-319">The new implementation uses fewer lines of code.</span></span>
1. <span data-ttu-id="90e4b-320">これにより、サードパーティの API の複雑さが解消され `StackExchange.Redis` ます。</span><span class="sxs-lookup"><span data-stu-id="90e4b-320">It abstracts away the complexity of the third-party `StackExchange.Redis` API.</span></span>
1. <span data-ttu-id="90e4b-321">基になる Redis キャッシュを別の種類のデータストアに置き換えるには、状態ストアの構成ファイルの変更のみが必要になりました。</span><span class="sxs-lookup"><span data-stu-id="90e4b-321">Replacing the underlying Redis cache with a different type of data store now only requires changes to the state store configuration file.</span></span>

### <a name="references"></a><span data-ttu-id="90e4b-322">関連項目</span><span class="sxs-lookup"><span data-stu-id="90e4b-322">References</span></span>

- [<span data-ttu-id="90e4b-323">Dapr がサポートする状態ストア</span><span class="sxs-lookup"><span data-stu-id="90e4b-323">Dapr supported state stores</span></span>](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/)

> [!div class="step-by-step"]
> <span data-ttu-id="90e4b-324">[前へ](reference-application.md)
> [次へ](service-invocation.md)</span><span class="sxs-lookup"><span data-stu-id="90e4b-324">[Previous](reference-application.md)
[Next](service-invocation.md)</span></span>
