---
title: Dapr 可観測性ビルディングブロック
description: 可観測性ビルディングブロックの説明、その機能、利点、適用方法
author: edwinvw
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: c7c941625f5867ad58eee602bfc42183bee87183
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401451"
---
# <a name="the-dapr-observability-building-block"></a><span data-ttu-id="c6b64-103">Dapr 可観測性ビルディングブロック</span><span class="sxs-lookup"><span data-stu-id="c6b64-103">The Dapr observability building block</span></span>

<span data-ttu-id="c6b64-104">最新の分散システムは複雑です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-104">Modern distributed systems are complex.</span></span> <span data-ttu-id="c6b64-105">小規模で疎結合のデプロイ可能なサービスから始めることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-105">You start with small, loosely coupled, independently deployable services.</span></span> <span data-ttu-id="c6b64-106">これらのサービスは、プロセスとサーバーの境界を越えています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-106">These services cross process and server boundaries.</span></span> <span data-ttu-id="c6b64-107">次に、さまざまな種類のインフラストラクチャバッキングサービス (データベース、メッセージブローカー、キーコンテナー) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-107">They then consume different kinds of infrastructure backing services (databases, message brokers, key vaults).</span></span> <span data-ttu-id="c6b64-108">最後に、これらの異なる部分は、アプリケーションを形成するためにまとめられています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-108">Finally, these disparate pieces compose together to form an application.</span></span>

<span data-ttu-id="c6b64-109">複数の独立した部品を使用して、何が起こっているのかをどのように理解しているのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="c6b64-109">With so many separate, moving parts, how do you make sense of what is going on?</span></span> <span data-ttu-id="c6b64-110">残念ながら、従来の監視アプローチは十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-110">Unfortunately, legacy monitoring approaches from the past aren't enough.</span></span> <span data-ttu-id="c6b64-111">代わりに、システムをエンドツー **エンドで監視可能に** する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-111">Instead, the system must be **observable** from end-to-end.</span></span> <span data-ttu-id="c6b64-112">最新の [可観測性](../cloud-native/observability-patterns.md) プラクティスでは、アプリケーションの正常性を常に把握し、洞察を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-112">Modern [observability](../cloud-native/observability-patterns.md) practices provide visibility and insight into the health of the application at all times.</span></span> <span data-ttu-id="c6b64-113">これにより、出力を観察することによって内部状態を推論できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-113">They enable you to infer the internal state by observing the output.</span></span> <span data-ttu-id="c6b64-114">可観測性は、分散アプリケーションの監視とトラブルシューティングに必須です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-114">Observability is mandatory for monitoring and troubleshooting distributed applications.</span></span>

<span data-ttu-id="c6b64-115">可観測性を取得するために使用されるシステム情報を **テレメトリ** と呼びます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-115">The system information used to gain observability is referred to as **telemetry**.</span></span> <span data-ttu-id="c6b64-116">これは、次の4つの広範なカテゴリに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-116">It can be divided into four broad categories:</span></span>

1. <span data-ttu-id="c6b64-117">**分散トレース** は、分散トランザクションに関係するサービスとサービス間のトラフィックに関する洞察を提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-117">**Distributed tracing** provides insight into the traffic between services and services involved in distributed transactions.</span></span>
1. <span data-ttu-id="c6b64-118">**メトリック** により、サービスのパフォーマンスとそのリソース消費量を把握できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-118">**Metrics** provides insight into the performance of a service and its resource consumption.</span></span>
1. <span data-ttu-id="c6b64-119">**ログ記録** を使用すると、コードの実行状況やエラーが発生したかどうかを把握できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-119">**Logging** provides insight into how the code is executing and if errors have occurred.</span></span>
1. <span data-ttu-id="c6b64-120">**正常性** エンドポイントは、サービスの可用性に関する洞察を提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-120">**Health** endpoints provide insight into the availability of a service.</span></span>

<span data-ttu-id="c6b64-121">テレメトリの深さは、アプリケーションプラットフォームの可観測性機能によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-121">The depth of telemetry is determined by the observability features of an application platform.</span></span> <span data-ttu-id="c6b64-122">Azure クラウドを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="c6b64-122">Consider the Azure cloud.</span></span> <span data-ttu-id="c6b64-123">すべてのテレメトリカテゴリを含む豊富なテレメトリエクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-123">It provides a rich telemetry experience that includes all of the telemetry categories.</span></span> <span data-ttu-id="c6b64-124">構成がない場合、ほとんどの Azure IaaS および PaaS サービスは、テレメトリを [Azure アプリケーション Insights](/azure/azure-monitor/app/app-insights-overview) サービスに伝達して公開します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-124">Without any configuration, most Azure IaaS and PaaS services propagate and publish telemetry to the [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview) service.</span></span> <span data-ttu-id="c6b64-125">Application Insights には、高度に視覚化されたダッシュボードでシステムログ、トレース、問題領域が示されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-125">Application Insights presents system logging, tracing, and problem areas with highly visual dashboards.</span></span> <span data-ttu-id="c6b64-126">また、通信に基づいてサービス間の依存関係を示す図を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-126">It can even render a diagram showing the dependencies between services based on their communication.</span></span>

<span data-ttu-id="c6b64-127">ただし、アプリケーションで Azure PaaS と IaaS リソースを使用できない場合はどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="c6b64-127">However, what if an application can't use Azure PaaS and IaaS resources?</span></span> <span data-ttu-id="c6b64-128">Application Insights の豊富なテレメトリエクスペリエンスを利用できますか。</span><span class="sxs-lookup"><span data-stu-id="c6b64-128">Is it still possible to take advantage of the rich telemetry experience of Application Insights?</span></span> <span data-ttu-id="c6b64-129">答えは [はい] です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-129">The answer is yes.</span></span> <span data-ttu-id="c6b64-130">Azure 以外のアプリケーションでは、ライブラリをインポートし、構成を追加し、コードをインストルメント化してテレメトリを Azure アプリケーション Insights に出力できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-130">A non-Azure application can import libraries, add configuration, and instrument code to emit telemetry to Azure Application Insights.</span></span> <span data-ttu-id="c6b64-131">ただし、この方法では、アプリケーションが Application Insights に **密** に結合されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-131">However, this approach **tightly couples** the application to Application Insights.</span></span> <span data-ttu-id="c6b64-132">別の監視プラットフォームにアプリを移動すると、負荷の高いリファクタリングが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-132">Moving the app to a different monitoring platform could involve expensive refactoring.</span></span> <span data-ttu-id="c6b64-133">密結合を回避し、コード外で可観測性を使用するのはすばらしいことではないでしょうか。</span><span class="sxs-lookup"><span data-stu-id="c6b64-133">Wouldn't it be great to avoid tight coupling and consume observability outside of the code?</span></span>

<span data-ttu-id="c6b64-134">Dapr を使用すると、できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-134">With Dapr, you can.</span></span> <span data-ttu-id="c6b64-135">Dapr が可観測性を分散アプリケーションに追加する方法を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="c6b64-135">Let's look at how Dapr can add observability to our distributed applications.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="c6b64-136">解決方法</span><span class="sxs-lookup"><span data-stu-id="c6b64-136">What it solves</span></span>

<span data-ttu-id="c6b64-137">Dapr 可観測性ビルディングブロックは、アプリケーションから可観測性を分離します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-137">The Dapr observability building block decouples observability from the application.</span></span> <span data-ttu-id="c6b64-138">Dapr のシステムサービスによって生成されたトラフィックを自動的にキャプチャし、dapr コントロールプレーンを構成します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-138">It automatically captures traffic generated by Dapr sidecars and Dapr system services that make up the Dapr control plane.</span></span> <span data-ttu-id="c6b64-139">ブロックは、複数のサービスにまたがる1つの操作からのトラフィックを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-139">The block correlates traffic from a single operation that spans multiple services.</span></span> <span data-ttu-id="c6b64-140">また、パフォーマンスメトリック、リソース使用率、システムの正常性も公開します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-140">It also exposes performance metrics, resource utilization, and the health of the system.</span></span> <span data-ttu-id="c6b64-141">テレメトリはオープン標準形式で公開されており、選択した監視バックエンドに情報を取り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-141">Telemetry is published in open-standard formats enabling information to be fed into your monitoring back end of choice.</span></span> <span data-ttu-id="c6b64-142">ここで、情報を視覚化、照会、および分析することができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-142">There, the information can be visualized, queried, and analyzed.</span></span>

<span data-ttu-id="c6b64-143">Dapr がプラミングを抽象化するため、アプリケーションは可観測性がどのように実装されているかを認識しません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-143">As Dapr abstracts away the plumbing, the application is unaware of how observability is implemented.</span></span> <span data-ttu-id="c6b64-144">ライブラリを参照したり、カスタムインストルメンテーションコードを実装したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-144">There's no need to reference libraries or implement custom instrumentation code.</span></span> <span data-ttu-id="c6b64-145">Dapr を使用すると、開発者はビジネスロジックの構築に集中することができ、可観測性することはできません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-145">Dapr allows the developer to focus on building business logic and not observability plumbing.</span></span> <span data-ttu-id="c6b64-146">可観測性は Dapr レベルで構成され、さまざまなチームによって作成され、さまざまなテクノロジスタックを使用して構築された場合でも、サービス間で一貫しています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-146">Observability is configured at the Dapr level and is consistent across services, even when created by different teams, and built with different technology stacks.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="c6b64-147">しくみ</span><span class="sxs-lookup"><span data-stu-id="c6b64-147">How it works</span></span>

<span data-ttu-id="c6b64-148">Dapr の [サイドカーアーキテクチャ](dapr-at-20000-feet.md#sidecar-architecture) は、組み込みの可観測性機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c6b64-148">Dapr's [sidecar architecture](dapr-at-20000-feet.md#sidecar-architecture) enables built-in observability features.</span></span> <span data-ttu-id="c6b64-149">サービスが通信する際、Dapr はトラフィックをインターセプトし、トレース、メトリック、およびログ情報を抽出します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-149">As services communicate, Dapr sidecars intercept the traffic and extract tracing, metrics, and logging information.</span></span> <span data-ttu-id="c6b64-150">テレメトリはオープン標準形式で公開されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-150">Telemetry is published in an open standards format.</span></span> <span data-ttu-id="c6b64-151">既定では、Dapr は [OpenTelemetry](https://opentelemetry.io/) と [Zipkin](https://zipkin.io/)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-151">By default, Dapr supports [OpenTelemetry](https://opentelemetry.io/) and [Zipkin](https://zipkin.io/).</span></span>

<span data-ttu-id="c6b64-152">Dapr には、さまざまなバックエンド監視ツールにテレメトリを発行できる [コレクター](https://docs.dapr.io/operations/monitoring/open-telemetry-collector/) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-152">Dapr provides [collectors](https://docs.dapr.io/operations/monitoring/open-telemetry-collector/) that can publish telemetry to different back-end monitoring tools.</span></span> <span data-ttu-id="c6b64-153">これらのツールは、分析とクエリのために Dapr テレメトリを提示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-153">These tools present Dapr telemetry for analysis and querying.</span></span> <span data-ttu-id="c6b64-154">図9-1 は、Dapr 可観測性アーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-154">Figure 9-1 shows the Dapr observability architecture:</span></span>

![Dapr 可観測性アーキテクチャ](media/observability/observability-architecture.png)

<span data-ttu-id="c6b64-156">**図 9-1**</span><span class="sxs-lookup"><span data-stu-id="c6b64-156">**Figure 9-1**.</span></span> <span data-ttu-id="c6b64-157">Dapr 可観測性アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="c6b64-157">Dapr observability architecture.</span></span>

1. <span data-ttu-id="c6b64-158">サービス A がサービス B に対して操作を呼び出します。この呼び出しは、サービス a の dapr サイドカーからサービス B のサイドカーにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-158">Service A calls an operation on Service B. The call is routed from a Dapr sidecar for Service A to a sidecar for Service B.</span></span>
1. <span data-ttu-id="c6b64-159">サービス B が操作を完了すると、応答が Dapr フォールバックを通じてサービス A に返されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-159">When Service B completes the operation, a response is sent back to Service A through the Dapr sidecars.</span></span> <span data-ttu-id="c6b64-160">すべての要求と応答に対して利用可能なすべてのテレメトリを収集して公開します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-160">They gather and publish all available telemetry for every request and response.</span></span>
1. <span data-ttu-id="c6b64-161">構成されたコレクターはテレメトリを取り込みし、それを監視バックエンドに送信します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-161">The configured collector ingests the telemetry and sends it to the monitoring back end.</span></span>  

<span data-ttu-id="c6b64-162">開発者として、可観測性の追加は、pub/sub や state management など、他の Dapr 構成要素の構成とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-162">As a developer, keep in mind that adding observability is different from configuring other Dapr building blocks, like pub/sub or state management.</span></span> <span data-ttu-id="c6b64-163">ビルディングブロックを参照する代わりに、コレクターと監視バックエンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-163">Instead of referencing a building block, you add a collector and a monitoring back end.</span></span> <span data-ttu-id="c6b64-164">図9-1 は、さまざまな監視バックエンドと統合する複数のコレクターを構成できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-164">Figure 9-1 shows it's possible to configure multiple collectors that integrate with different monitoring back ends.</span></span>

<span data-ttu-id="c6b64-165">この章の最初に、4つのカテゴリのテレメトリが識別されました。</span><span class="sxs-lookup"><span data-stu-id="c6b64-165">At the beginning of this chapter, four categories of telemetry were identified.</span></span> <span data-ttu-id="c6b64-166">次のセクションでは、各カテゴリの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-166">The following sections will provide detail for each category.</span></span> <span data-ttu-id="c6b64-167">一般的な監視バックエンドと統合するコレクターを構成する方法についての指示が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-167">They'll include instruction on how to configure collectors that integrate with popular monitoring back ends.</span></span>

### <a name="distributed-tracing"></a><span data-ttu-id="c6b64-168">分散トレース</span><span class="sxs-lookup"><span data-stu-id="c6b64-168">Distributed tracing</span></span>

<span data-ttu-id="c6b64-169">分散トレースを使用すると、分散アプリケーション内のサービス間を流れるトラフィックについての洞察を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-169">Distributed tracing provides insight into the traffic that flows across services in a distributed application.</span></span> <span data-ttu-id="c6b64-170">交換された要求メッセージと応答メッセージのログは、問題のトラブルシューティングを行うための非常に重要な情報源です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-170">The log of exchanged request and response messages is an invaluable source of information for troubleshooting issues.</span></span> <span data-ttu-id="c6b64-171">ハードパートは、同じ操作から送信されるメッセージを相互に *関連付け* ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-171">The hard part is *correlating messages* that originate from the same operation.</span></span>

<span data-ttu-id="c6b64-172">Dapr は、 [W3C トレースコンテキスト](https://www.w3.org/TR/trace-context) を使用して関連メッセージを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-172">Dapr uses the [W3C Trace Context](https://www.w3.org/TR/trace-context) to correlate related messages.</span></span> <span data-ttu-id="c6b64-173">同じコンテキスト情報を要求と応答に挿入して、一意の操作を形成します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-173">It injects the same context information into requests and responses that form a unique operation.</span></span> <span data-ttu-id="c6b64-174">図9-2 は、相関関係のしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-174">Figure 9-2 shows how correlation works:</span></span>

![W3C トレースコンテキストの例](media/observability/w3c-trace-context.png)

<span data-ttu-id="c6b64-176">**図 9-2**</span><span class="sxs-lookup"><span data-stu-id="c6b64-176">**Figure 9-2**.</span></span> <span data-ttu-id="c6b64-177">W3C トレースコンテキストの例。</span><span class="sxs-lookup"><span data-stu-id="c6b64-177">W3C Trace Context example.</span></span>

1. <span data-ttu-id="c6b64-178">サービス A がサービス B に対して操作を呼び出します。サービス A が呼び出しを開始すると、Dapr は一意のトレースコンテキストを作成し、要求に挿入します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-178">Service A invokes an operation on Service B. As Service A starts the call, Dapr creates a unique trace context and injects it into the request.</span></span>
1. <span data-ttu-id="c6b64-179">サービス B は要求を受信し、サービス C に対して操作を呼び出します。 Dapr は、受信要求にトレースコンテキストが含まれていることを検出し、それをサービス C に送信する要求に挿入することによって伝達します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-179">Service B receives the request and invokes an operation on Service C. Dapr detects that the incoming request contains a trace context and propagates it by injecting it into the outgoing request to Service C.</span></span>  
1. <span data-ttu-id="c6b64-180">サービス C は、要求を受信して処理します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-180">Service C receives the request and handles it.</span></span> <span data-ttu-id="c6b64-181">Dapr は、受信要求にトレースコンテキストが含まれていることを検出し、それをサービス B への送信応答に挿入することによって伝達します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-181">Dapr detects that the incoming request contains a trace context and propagates it by injecting it into the outgoing response back to Service B.</span></span>
1. <span data-ttu-id="c6b64-182">サービス B は応答を受信して処理します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-182">Service B receives the response and handles it.</span></span> <span data-ttu-id="c6b64-183">次に、新しい応答を作成し、それをサービス A に送信する応答に挿入して、トレースコンテキストを伝達します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-183">It then creates a new response and propagates the trace context by injecting it into the outgoing response back to Service A.</span></span>

<span data-ttu-id="c6b64-184">まとめて属する一連の要求と応答は、 *トレース* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-184">A set of requests and responses that belong together is called a *trace*.</span></span> <span data-ttu-id="c6b64-185">図9-3 にトレースを示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-185">Figure 9-3 shows a trace:</span></span>

![トレースとスパン](media/observability/traces-spans.png)

<span data-ttu-id="c6b64-187">**図 9-3**</span><span class="sxs-lookup"><span data-stu-id="c6b64-187">**Figure 9-3**.</span></span> <span data-ttu-id="c6b64-188">トレースとスパン。</span><span class="sxs-lookup"><span data-stu-id="c6b64-188">Traces and spans.</span></span>

<span data-ttu-id="c6b64-189">図では、トレースが、多くのサービスに対して実行される一意のアプリケーショントランザクションを表していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-189">In the figure, note how the trace represents a unique application transaction that takes place across many services.</span></span> <span data-ttu-id="c6b64-190">トレースは、 *範囲* のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-190">A trace is a collection of *spans*.</span></span> <span data-ttu-id="c6b64-191">各スパンは、トレース内で実行された1つの操作または作業単位を表します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-191">Each span represents a single operation or unit of work done within the trace.</span></span> <span data-ttu-id="c6b64-192">範囲は、一意のトランザクションを実装するサービス間で送信される要求と応答です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-192">Spans are the requests and responses that are sent between services that implement the unique transaction.</span></span>

<span data-ttu-id="c6b64-193">次のセクションでは、トレーステレメトリを監視バックエンドに公開して、そのテレメトリを検査する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-193">The next sections discuss how to inspect tracing telemetry by publishing it to a monitoring back end.</span></span>

#### <a name="use-a-zipkin-monitoring-back-end"></a><span data-ttu-id="c6b64-194">Zipkin monitoring バックエンドを使用する</span><span class="sxs-lookup"><span data-stu-id="c6b64-194">Use a Zipkin monitoring back end</span></span>

<span data-ttu-id="c6b64-195">[Zipkin](https://zipkin.io/) は、オープンソースの分散トレースシステムです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-195">[Zipkin](https://zipkin.io/) is an open-source distributed tracing system.</span></span> <span data-ttu-id="c6b64-196">テレメトリデータを取り込み、視覚化することができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-196">It can ingest and visualize telemetry data.</span></span> <span data-ttu-id="c6b64-197">Dapr は、Zipkin の既定のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-197">Dapr offers default support for Zipkin.</span></span> <span data-ttu-id="c6b64-198">次の例は、Dapr テレメトリを視覚化するように Zipkin を構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-198">The following example demonstrates how to configure Zipkin to visualize Dapr telemetry.</span></span>

##### <a name="enable-and-configure-tracing"></a><span data-ttu-id="c6b64-199">トレースの有効化と構成</span><span class="sxs-lookup"><span data-stu-id="c6b64-199">Enable and configure tracing</span></span>

<span data-ttu-id="c6b64-200">開始するには、dapr 構成ファイルを使用して Dapr ランタイムに対してトレースを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-200">To start, tracing must be enabled for the Dapr runtime using a Dapr configuration file.</span></span> <span data-ttu-id="c6b64-201">次に、という名前の構成ファイルの例を示し `tracing-config.yaml` ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-201">Here's an example of a configuration file named `tracing-config.yaml`:</span></span>  

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: tracing-config
  namespace: default
spec:
  tracing:
    samplingRate: "1"
    zipkin:
      endpointAddress: "http://zipkin.default.svc.cluster.local:9411/api/v2/spans"
```

<span data-ttu-id="c6b64-202">属性は、 `samplingRate` トレースの発行に使用する間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-202">The `samplingRate` attribute specifies the interval used for publishing traces.</span></span> <span data-ttu-id="c6b64-203">値は `0` (トレースが無効) と `1` (すべてのトレースが公開されている) の間である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-203">The value must be between `0` (tracing disabled) and `1` (every trace is published).</span></span> <span data-ttu-id="c6b64-204">たとえば、という値を指定すると、 `0.5` 他のすべてのトレースが公開され、パブリッシュされたトラフィックが大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-204">With a value of `0.5`, for example, every other trace is published, significantly reducing published traffic.</span></span> <span data-ttu-id="c6b64-205">は、 `endpointAddress` Kubernetes クラスターで実行されている Zipkin サーバー上のエンドポイントを指します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-205">The `endpointAddress` points to an endpoint on a Zipkin server running in a Kubernetes cluster.</span></span> <span data-ttu-id="c6b64-206">Zipkin の既定のポートは `9411` です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-206">The default port for Zipkin is `9411`.</span></span> <span data-ttu-id="c6b64-207">構成は、Kubernetes CLI を使用して Kubernetes クラスターに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-207">The configuration must be applied to the Kubernetes cluster using the Kubernetes CLI:</span></span>

```console
kubectl apply -f tracing-config.yaml
```

##### <a name="install-the-zipkin-server"></a><span data-ttu-id="c6b64-208">Zipkin サーバーをインストールする</span><span class="sxs-lookup"><span data-stu-id="c6b64-208">Install the Zipkin server</span></span>

<span data-ttu-id="c6b64-209">Dapr を自己ホスト型のモードでインストールすると、Zipkin サーバーが自動的にインストールされ、または Windows 上の既定の構成ファイルでトレースが有効になり `$HOME/.dapr/config.yaml` `%USERPROFILE%\.dapr\config.yaml` ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-209">When installing Dapr in self-hosted mode, a Zipkin server is automatically installed and tracing is enabled in the default configuration file located in `$HOME/.dapr/config.yaml` or `%USERPROFILE%\.dapr\config.yaml` on Windows.</span></span>

<span data-ttu-id="c6b64-210">ただし、Dapr を Kubernetes クラスターにインストールする場合、Zipkin は既定では追加されません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-210">When installing Dapr on a Kubernetes cluster though, Zipkin isn't added by default.</span></span> <span data-ttu-id="c6b64-211">という名前の次の Kubernetes マニフェストファイルは `zipkin.yaml` 、標準の Zipkin サーバーをクラスターにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="c6b64-211">The following Kubernetes manifest file named `zipkin.yaml`, deploys a standard Zipkin server to the cluster:</span></span>

```yaml
kind: Deployment
apiVersion: apps/v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  replicas: 1
  selector:
    matchLabels:
      service: zipkin
  template:
    metadata:
      labels:
        service: zipkin
    spec:
      containers:
        - name: zipkin
          image: openzipkin/zipkin-slim
          imagePullPolicy: IfNotPresent
          ports:
            - name: http
              containerPort: 9411
              protocol: TCP

---

kind: Service
apiVersion: v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  type: NodePort
  ports:
    - port: 9411
      targetPort: 9411
      nodePort: 32411
      protocol: TCP
      name: zipkin
  selector:
    service: zipkin

```

<span data-ttu-id="c6b64-212">デプロイでは、標準のコンテナーイメージを使用し `openzipkin/zipkin-slim` ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-212">The deployment uses the standard `openzipkin/zipkin-slim` container image.</span></span> <span data-ttu-id="c6b64-213">Zipkin サービスは、ポートでテレメトリを表示するために使用できる Zipkin web フロントエンドを公開し `32411` ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-213">The Zipkin service exposes the Zipkin web front end, which you can use to view the telemetry on port `32411`.</span></span> <span data-ttu-id="c6b64-214">Kubernetes CLI を使用して、Zipkin マニフェストファイルを Kubernetes クラスターに適用し、Zipkin サーバーをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="c6b64-214">Use the Kubernetes CLI to apply the Zipkin manifest file to the Kubernetes cluster and deploy the Zipkin server:</span></span>

```console
kubectl apply -f zipkin.yaml
```

##### <a name="configure-the-services-to-use-the-tracing-configuration"></a><span data-ttu-id="c6b64-215">トレース構成を使用するようにサービスを構成する</span><span class="sxs-lookup"><span data-stu-id="c6b64-215">Configure the services to use the tracing configuration</span></span>

<span data-ttu-id="c6b64-216">これで、テレメトリの発行を開始するためのすべてが正しく設定されました。</span><span class="sxs-lookup"><span data-stu-id="c6b64-216">Now everything is set up correctly to start publishing telemetry.</span></span> <span data-ttu-id="c6b64-217">アプリケーションの一部としてデプロイされているすべての Dapr サイドカーは、開始時にテレメトリを出力するように指示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-217">Every Dapr sidecar that is deployed as part of the application must be instructed to emit telemetry when started.</span></span> <span data-ttu-id="c6b64-218">これを行うには、 `dapr.io/config` `tracing-config` 各サービスの配置に構成を参照する注釈を追加します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-218">To do that, add a `dapr.io/config` annotation that references the `tracing-config` configuration to the deployment of each service.</span></span> <span data-ttu-id="c6b64-219">次に、注釈を含む、eShop 注文 API サービスのマニフェストファイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-219">Here's an example of the eShop ordering API service's manifest file containing the annotation:</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ordering-api
  namespace: eshop
  labels:
    app: eshop
spec:
  replicas: 1
  selector:
    matchLabels:
      app: eshop
  template:
    metadata:
      labels:
        app: simulation
      annotations:
        dapr.io/enabled: "true"
        dapr.io/app-id: "ordering-api"
        dapr.io/config: "tracing-config"
    spec:
      containers:
      - name: simulation
        image: eshop/ordering.api:linux-latest
```

##### <a name="inspect-the-telemetry-in-zipkin"></a><span data-ttu-id="c6b64-220">Zipkin でテレメトリを検査する</span><span class="sxs-lookup"><span data-stu-id="c6b64-220">Inspect the telemetry in Zipkin</span></span>

<span data-ttu-id="c6b64-221">アプリケーションが起動すると、Dapr サイドカーが Zipkin サーバーにテレメトリを出力します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-221">Once the application is started, the Dapr sidecars will emit telemetry to the Zipkin server.</span></span> <span data-ttu-id="c6b64-222">このテレメトリを検査するには、web ブラウザーでをポイント <http://localhost:32411> します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-222">To inspect this telemetry, point a web-browser to <http://localhost:32411>.</span></span> <span data-ttu-id="c6b64-223">Zipkin web フロントエンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-223">You'll see the Zipkin web front end:</span></span>

![Zipkin スタートページ](media/observability/zipkin.png)

<span data-ttu-id="c6b64-225">[ *トレースの検索* ] タブで、トレースを照会できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-225">On the *Find a trace* tab, you can query traces.</span></span> <span data-ttu-id="c6b64-226">制限を指定せずに [ *クエリの実行* ] ボタンを押すと、すべての取り込まれた *トレース* が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-226">Pressing the *RUN QUERY* button without specifying any restrictions will show all the ingested *traces*:</span></span>

![トレースの一覧](media/observability/zipkin-traces-overview.png)

<span data-ttu-id="c6b64-228">特定のトレースの横にある [ *表示* ] ボタンをクリックすると、そのトレースの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-228">Clicking the *SHOW* button next to a specific trace, will show the details of that trace:</span></span>

![トレースの詳細](media/observability/zipkin-trace-details.png)

<span data-ttu-id="c6b64-230">[詳細] ページの各項目は、選択したトレースの一部である要求を表すスパンです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-230">Each item on the details page, is a span that represents a request that is part of the selected trace.</span></span>

##### <a name="inspect-the-dependencies-between-services"></a><span data-ttu-id="c6b64-231">サービス間の依存関係を検査する</span><span class="sxs-lookup"><span data-stu-id="c6b64-231">Inspect the dependencies between services</span></span>

<span data-ttu-id="c6b64-232">Dapr sidecars はサービス間のトラフィックを処理するので、トレース情報を使用してサービス間の依存関係を判断できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-232">Because Dapr sidecars handle traffic between services, Zipkin can use the trace information to determine the dependencies between the services.</span></span> <span data-ttu-id="c6b64-233">実際の動作を確認するには、Zipkin web ページの [ *依存関係* ] タブにアクセスし、虫眼鏡付きのボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-233">To see it in action, go to the *Dependencies* tab on the Zipkin web page and select the button with the magnifying glass.</span></span> <span data-ttu-id="c6b64-234">Zipkin には、サービスとその依存関係の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-234">Zipkin will show an overview of the services and their dependencies:</span></span>

![Zipkin の依存関係グラフ](media/observability/zipkin-dependencies.png)

<span data-ttu-id="c6b64-236">サービス間の線のアニメーション化されたドットは、要求を表し、転送元から送信先に移動します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-236">The animated dots on the lines between the services represent requests and move from source to destination.</span></span> <span data-ttu-id="c6b64-237">赤い点は、要求が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-237">Red dots indicate a failed request.</span></span>

#### <a name="use-a-jaeger-or-new-relic-monitoring-back-end"></a><span data-ttu-id="c6b64-238">Jaeger または新しい聖を監視するバックエンドを使用する</span><span class="sxs-lookup"><span data-stu-id="c6b64-238">Use a Jaeger or New Relic monitoring back end</span></span>

<span data-ttu-id="c6b64-239">Zipkin 自体以外の監視バックエンドソフトウェアでは、Zipkin 形式を使用した取り込みテレメトリもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-239">Beyond Zipkin itself, other monitoring back-end software also supports ingesting telemetry using the Zipkin format.</span></span> <span data-ttu-id="c6b64-240">[Jaeger](https://www.jaegertracing.io/) は、Uber テクノロジによって作成されたオープンソースのトレースシステムです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-240">[Jaeger](https://www.jaegertracing.io/) is an open source tracing system created by Uber Technologies.</span></span> <span data-ttu-id="c6b64-241">これは、分散サービス間のトランザクションをトレースし、複雑なマイクロサービス環境のトラブルシューティングを行うために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-241">It's used to trace transactions between distributed services and troubleshoot complex microservices environments.</span></span> <span data-ttu-id="c6b64-242">[新しい聖箱](https://newrelic.com/) は、 *フルスタック* の可観測性プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-242">[New Relic](https://newrelic.com/) is a *full-stack* observability platform.</span></span> <span data-ttu-id="c6b64-243">分散アプリケーションから関連するデータをリンクして、システムの全体像を提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-243">It links relevant data from a distributed application to provide a complete picture of your system.</span></span> <span data-ttu-id="c6b64-244">これを試すには、 `endpointAddress` Dapr 構成ファイルで Jaeger または新しい聖剣サーバーをポイントするを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-244">To try them out, specify an `endpointAddress` pointing to either a Jaeger or New Relic server in the Dapr configuration file.</span></span> <span data-ttu-id="c6b64-245">Jaeger サーバーにテレメトリを送信するように Dapr を構成する構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-245">Here's an example of a configuration file that configures Dapr to send telemetry to a Jaeger server.</span></span> <span data-ttu-id="c6b64-246">Jaeger の URL は、Zipkin の URL と同じです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-246">The URL for Jaeger is identical to the URL for the Zipkin.</span></span> <span data-ttu-id="c6b64-247">唯一の違いは、サーバーが実行されているポートです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-247">The only difference is the port on which the server runs:</span></span>

 ```yaml
 apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "http://localhost:9415/api/v2/spans"
 ```

<span data-ttu-id="c6b64-248">新しい聖箱をお試しになるには、新しい聖数点の API のエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-248">To try out New Relic, specify the endpoint of the New Relic API.</span></span> <span data-ttu-id="c6b64-249">新しい聖箱の構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-249">Here's an example of a configuration file for New Relic:</span></span>

 ```yaml
apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "https://trace-api.newrelic.com/trace/v1?Api-Key=<NR-API-KEY>&Data-Format=zipkin&Data-Format-Version=2"
 ```

<span data-ttu-id="c6b64-250">使用方法の詳細については、Jaeger と新しい聖数の web サイトをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-250">Check out the Jaeger and New Relic websites for more information on how to use them.</span></span>

### <a name="metrics"></a><span data-ttu-id="c6b64-251">メトリック</span><span class="sxs-lookup"><span data-stu-id="c6b64-251">Metrics</span></span>

<span data-ttu-id="c6b64-252">メトリックを使用すると、パフォーマンスとリソース消費に関する洞察を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-252">Metrics provide insight into performance and resource consumption.</span></span> <span data-ttu-id="c6b64-253">内部的には、Dapr はシステムとランタイムのさまざまなメトリックのコレクションを生成します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-253">Under the hood, Dapr emits a wide collection of system and runtime metrics.</span></span> <span data-ttu-id="c6b64-254">Dapr は、 [Prometheus](https://prometheus.io/) をメトリック標準として使用します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-254">Dapr uses [Prometheus](https://prometheus.io/) as a metric standard.</span></span> <span data-ttu-id="c6b64-255">Dapr サイドカーとシステムサービスは、ポートでメトリックエンドポイントを公開し `9090` ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-255">Dapr sidecars and system services, expose a metrics endpoint on port `9090`.</span></span> <span data-ttu-id="c6b64-256">*Prometheus よう* は、メトリックを収集するために、事前に定義された間隔でこのエンドポイントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-256">A *Prometheus scraper* calls this endpoint at a predefined interval to collect metrics.</span></span> <span data-ttu-id="c6b64-257">ようは、メトリック値を監視バックエンドに送信します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-257">The scraper sends metric values to a monitoring back end.</span></span> <span data-ttu-id="c6b64-258">図9-4 は、スクラッププロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-258">Figure 9-4 shows the scraping process:</span></span>

![スクラップ Prometheus メトリック](media/observability/prometheus-scraper.png)

<span data-ttu-id="c6b64-260">**図 9-4**.</span><span class="sxs-lookup"><span data-stu-id="c6b64-260">**Figure 9-4**.</span></span> <span data-ttu-id="c6b64-261">スクラップ Prometheus メトリック。</span><span class="sxs-lookup"><span data-stu-id="c6b64-261">Scraping Prometheus metrics.</span></span>

<span data-ttu-id="c6b64-262">上の図では、各サイドカーとシステムサービスが、ポート9090でリッスンするメトリックエンドポイントを公開しています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-262">In the above figure, each sidecar and system service exposes a metric endpoint that listens on port 9090.</span></span> <span data-ttu-id="c6b64-263">Prometheus メトリック Scrapper は、各エンドポイントからメトリックをキャプチャし、その情報を監視バックエンドに発行します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-263">The Prometheus Metrics Scrapper captures metrics from each endpoint and published the information to the monitoring back end.</span></span>  

#### <a name="service-discovery"></a><span data-ttu-id="c6b64-264">サービス検出</span><span class="sxs-lookup"><span data-stu-id="c6b64-264">Service discovery</span></span>

<span data-ttu-id="c6b64-265">メトリックを収集する場所をメトリックようが認識していることを不思議に思うかもしれません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-265">You might wonder how the metrics scraper knows where to collect metrics.</span></span> <span data-ttu-id="c6b64-266">Prometheus は、ターゲットデプロイ環境に組み込まれている検出メカニズムと統合できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-266">Prometheus can integrate with discovery mechanisms built into target deployment environments.</span></span> <span data-ttu-id="c6b64-267">たとえば、Kubernetes で実行すると、Prometheus は Kubernetes API と統合して、環境で実行されている使用可能なすべての Kubernetes リソースを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-267">For example, when running in Kubernetes, Prometheus can integrate with the Kubernetes API to find all available Kubernetes resources running in the environment.</span></span>

#### <a name="metrics-list"></a><span data-ttu-id="c6b64-268">メトリックの一覧</span><span class="sxs-lookup"><span data-stu-id="c6b64-268">Metrics list</span></span>

<span data-ttu-id="c6b64-269">Dapr は、Dapr システムサービスとそのランタイムに対して多数のメトリックを生成します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-269">Dapr generates a large set of metrics for Dapr system services and its runtime.</span></span> <span data-ttu-id="c6b64-270">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-270">Some examples include:</span></span>

| <span data-ttu-id="c6b64-271">メトリック</span><span class="sxs-lookup"><span data-stu-id="c6b64-271">Metric</span></span>                                         | <span data-ttu-id="c6b64-272">source</span><span class="sxs-lookup"><span data-stu-id="c6b64-272">Source</span></span> | <span data-ttu-id="c6b64-273">説明</span><span class="sxs-lookup"><span data-stu-id="c6b64-273">Description</span></span>                                                  |
| ---------------------------------------------- | :----: | ------------------------------------------------------------ |
| <span data-ttu-id="c6b64-274">dapr_operator_service_created_total</span><span class="sxs-lookup"><span data-stu-id="c6b64-274">dapr_operator_service_created_total</span></span>            | <span data-ttu-id="c6b64-275">システム</span><span class="sxs-lookup"><span data-stu-id="c6b64-275">System</span></span> | <span data-ttu-id="c6b64-276">Dapr オペレーターサービスによって作成された Dapr サービスの合計数。</span><span class="sxs-lookup"><span data-stu-id="c6b64-276">The total number of Dapr services created by the Dapr Operator service.</span></span> |
| <span data-ttu-id="c6b64-277">dapr_injector_sidecar_injection/requests_total</span><span class="sxs-lookup"><span data-stu-id="c6b64-277">dapr_injector_sidecar_injection/requests_total</span></span> | <span data-ttu-id="c6b64-278">システム</span><span class="sxs-lookup"><span data-stu-id="c6b64-278">System</span></span> | <span data-ttu-id="c6b64-279">Dapr Sidecar-Injector サービスによって受信されたサイドカーインジェクション要求の合計数。</span><span class="sxs-lookup"><span data-stu-id="c6b64-279">The total number of sidecar injection requests received by the Dapr Sidecar-Injector service.</span></span> |
| <span data-ttu-id="c6b64-280">dapr_placement_runtimes_total</span><span class="sxs-lookup"><span data-stu-id="c6b64-280">dapr_placement_runtimes_total</span></span>                  | <span data-ttu-id="c6b64-281">システム</span><span class="sxs-lookup"><span data-stu-id="c6b64-281">System</span></span> | <span data-ttu-id="c6b64-282">Dapr 配置サービスに報告されたホストの合計数。</span><span class="sxs-lookup"><span data-stu-id="c6b64-282">The total number of hosts reported to the Dapr Placement service.</span></span> |
| <span data-ttu-id="c6b64-283">dapr_sentry_cert_sign_request_received_total</span><span class="sxs-lookup"><span data-stu-id="c6b64-283">dapr_sentry_cert_sign_request_received_total</span></span>   | <span data-ttu-id="c6b64-284">システム</span><span class="sxs-lookup"><span data-stu-id="c6b64-284">System</span></span> | <span data-ttu-id="c6b64-285">Dapr Sentry サービスによって受信された証明書署名要求 (CRSs) の数。</span><span class="sxs-lookup"><span data-stu-id="c6b64-285">The number of certificate signing requests (CRSs) received by the Dapr Sentry service.</span></span> |
| <span data-ttu-id="c6b64-286">dapr_runtime_component_loaded</span><span class="sxs-lookup"><span data-stu-id="c6b64-286">dapr_runtime_component_loaded</span></span>      | <span data-ttu-id="c6b64-287">ランタイム</span><span class="sxs-lookup"><span data-stu-id="c6b64-287">Runtime</span></span> | <span data-ttu-id="c6b64-288">正常に読み込まれた Dapr コンポーネントの数。</span><span class="sxs-lookup"><span data-stu-id="c6b64-288">The number of successfully loaded Dapr components.</span></span>           |
| <span data-ttu-id="c6b64-289">dapr_grpc_io_server_completed_rpcs</span><span class="sxs-lookup"><span data-stu-id="c6b64-289">dapr_grpc_io_server_completed_rpcs</span></span> | <span data-ttu-id="c6b64-290">ランタイム</span><span class="sxs-lookup"><span data-stu-id="c6b64-290">Runtime</span></span> | <span data-ttu-id="c6b64-291">メソッドとステータスによる gRPC 呼び出しの数。</span><span class="sxs-lookup"><span data-stu-id="c6b64-291">Count of gRPC calls by method and status.</span></span>                    |
| <span data-ttu-id="c6b64-292">dapr_http_server_request_count</span><span class="sxs-lookup"><span data-stu-id="c6b64-292">dapr_http_server_request_count</span></span>     | <span data-ttu-id="c6b64-293">ランタイム</span><span class="sxs-lookup"><span data-stu-id="c6b64-293">Runtime</span></span> | <span data-ttu-id="c6b64-294">HTTP サーバーで開始された HTTP 要求の数。</span><span class="sxs-lookup"><span data-stu-id="c6b64-294">Number of HTTP requests started in an HTTP server.</span></span>           |
| <span data-ttu-id="c6b64-295">dapr_http/クライアント/sent_bytes</span><span class="sxs-lookup"><span data-stu-id="c6b64-295">dapr_http/client/sent_bytes</span></span>        | <span data-ttu-id="c6b64-296">ランタイム</span><span class="sxs-lookup"><span data-stu-id="c6b64-296">Runtime</span></span> | <span data-ttu-id="c6b64-297">HTTP クライアントによって要求本文で送信された合計バイト数 (ヘッダーは含まれません)。</span><span class="sxs-lookup"><span data-stu-id="c6b64-297">Total bytes sent in request body (not including headers) by an HTTP client.</span></span> |

<span data-ttu-id="c6b64-298">使用可能なメトリックの詳細については、 [Dapr メトリックのドキュメント](https://docs.dapr.io/developing-applications/building-blocks/observability/metrics)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-298">For more information on available metrics, see the [Dapr metrics documentation](https://docs.dapr.io/developing-applications/building-blocks/observability/metrics).</span></span>

#### <a name="configure-dapr-metrics"></a><span data-ttu-id="c6b64-299">Dapr メトリックを構成する</span><span class="sxs-lookup"><span data-stu-id="c6b64-299">Configure Dapr metrics</span></span>

<span data-ttu-id="c6b64-300">実行時に、Dapr コマンドに引数を含めることで、メトリックコレクションエンドポイントを無効にでき `--enable-metrics=false` ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-300">At runtime, you can disable the metrics collection endpoint by including the `--enable-metrics=false` argument in the Dapr command.</span></span> <span data-ttu-id="c6b64-301">または、引数を使用して、エンドポイントの既定のポートを変更することもでき `--metrics-port 9090` ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-301">Or, you can also change the default port for the endpoint with the `--metrics-port 9090` argument.</span></span>

<span data-ttu-id="c6b64-302">また、Dapr 構成ファイルを使用して、ランタイムメトリックコレクションを静的に有効または無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-302">You can also use a Dapr configuration file to statically enable or disable runtime metrics collection:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  metric:
    enabled: false
```

#### <a name="visualize-dapr-metrics"></a><span data-ttu-id="c6b64-303">Dapr メトリックを視覚化する</span><span class="sxs-lookup"><span data-stu-id="c6b64-303">Visualize Dapr metrics</span></span>

<span data-ttu-id="c6b64-304">Prometheus ようが監視バックエンドにメトリックを収集して公開することにより、生データをどのように意味するのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="c6b64-304">With the Prometheus scraper collecting and publishing metrics into the monitoring back end, how do you make sense of the raw data?</span></span> <span data-ttu-id="c6b64-305">メトリックを分析するための一般的な視覚化ツールは [Grafana](https://grafana.com/grafana/)です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-305">A popular visualization tool for analyzing metrics is [Grafana](https://grafana.com/grafana/).</span></span> <span data-ttu-id="c6b64-306">Grafana を使用すると、利用可能なメトリックからダッシュボードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-306">With Grafana, you can create dashboards from the available metrics.</span></span> <span data-ttu-id="c6b64-307">次に、Dapr システムサービスのメトリックを表示するダッシュボードの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-307">Here's an example of a dashboard displaying Dapr system services metrics:</span></span>

![Dapr システムサービスのメトリックを表示する Grafana ダッシュボード](media/observability/grafana-sample.png)

<span data-ttu-id="c6b64-309">Dapr のドキュメントには、 [Prometheus と Grafana をインストールするためのチュートリアル](https://docs.dapr.io/operations/monitoring/grafana/)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-309">The Dapr documentation includes a [tutorial for installing Prometheus and Grafana](https://docs.dapr.io/operations/monitoring/grafana/).</span></span>

### <a name="logging"></a><span data-ttu-id="c6b64-310">ログの記録</span><span class="sxs-lookup"><span data-stu-id="c6b64-310">Logging</span></span>

<span data-ttu-id="c6b64-311">ログ記録を使用すると、実行時にサービスに何が起こっているかを把握できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-311">Logging provides insight into what is happening with a service at runtime.</span></span> <span data-ttu-id="c6b64-312">アプリケーションを実行すると、dapr は Dapr システムサービスと Dapr システムサービスからログエントリを自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-312">When running an application, Dapr automatically emits log entries from Dapr sidecars and Dapr system services.</span></span> <span data-ttu-id="c6b64-313">ただし、アプリケーションコードでインストルメント化されたログエントリは、自動的には含まれ **ません** 。</span><span class="sxs-lookup"><span data-stu-id="c6b64-313">However, logging entries instrumented in your application code **aren't** automatically included.</span></span> <span data-ttu-id="c6b64-314">アプリケーションコードからログを出力するには、 [OPENTELEMETRY sdk for .net](https://opentelemetry.io/docs/net/)などの特定の sdk をインポートします。</span><span class="sxs-lookup"><span data-stu-id="c6b64-314">To emit logging from application code, you can import a specific SDK like [OpenTelemetry SDK for .NET](https://opentelemetry.io/docs/net/).</span></span> <span data-ttu-id="c6b64-315">アプリケーションコードのログ記録については、この章の「 *Dapr .NET SDK の使用*」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-315">Logging application code is covered later in this chapter in the section *Using the Dapr .NET SDK*.</span></span>  

#### <a name="log-entry-structure"></a><span data-ttu-id="c6b64-316">ログ エントリの構造</span><span class="sxs-lookup"><span data-stu-id="c6b64-316">Log entry structure</span></span>

<span data-ttu-id="c6b64-317">Dapr は構造化ログを出力します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-317">Dapr emits structured logging.</span></span> <span data-ttu-id="c6b64-318">各ログエントリの形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-318">Each log entry has the following format:</span></span>

| <span data-ttu-id="c6b64-319">フィールド</span><span class="sxs-lookup"><span data-stu-id="c6b64-319">Field</span></span>    | <span data-ttu-id="c6b64-320">説明</span><span class="sxs-lookup"><span data-stu-id="c6b64-320">Description</span></span>                                          | <span data-ttu-id="c6b64-321">例</span><span class="sxs-lookup"><span data-stu-id="c6b64-321">Example</span></span>                             |
| -------- | ---------------------------------------------------- | ----------------------------------- |
| <span data-ttu-id="c6b64-322">time</span><span class="sxs-lookup"><span data-stu-id="c6b64-322">time</span></span>     | <span data-ttu-id="c6b64-323">全形式で書式設定されたタイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="c6b64-323">ISO8601 formatted timestamp</span></span>                          | `2021-01-10T14:19:31.000Z`          |
| <span data-ttu-id="c6b64-324">level</span><span class="sxs-lookup"><span data-stu-id="c6b64-324">level</span></span>    | <span data-ttu-id="c6b64-325">エントリのレベル ( `debug` \| `info` \| `warn` \| `error` )  </span><span class="sxs-lookup"><span data-stu-id="c6b64-325">Level of the entry (`debug` \| `info` \| `warn`  \| `error`)</span></span> | `info`                              |
| <span data-ttu-id="c6b64-326">type</span><span class="sxs-lookup"><span data-stu-id="c6b64-326">type</span></span>     | <span data-ttu-id="c6b64-327">ログの種類</span><span class="sxs-lookup"><span data-stu-id="c6b64-327">Log Type</span></span>                                             | `log`                               |
| <span data-ttu-id="c6b64-328">msg</span><span class="sxs-lookup"><span data-stu-id="c6b64-328">msg</span></span>      | <span data-ttu-id="c6b64-329">ログメッセージ</span><span class="sxs-lookup"><span data-stu-id="c6b64-329">Log Message</span></span>                                          | `metrics server started on :62408/` |
| <span data-ttu-id="c6b64-330">scope</span><span class="sxs-lookup"><span data-stu-id="c6b64-330">scope</span></span>    | <span data-ttu-id="c6b64-331">ログのスコープ</span><span class="sxs-lookup"><span data-stu-id="c6b64-331">Logging Scope</span></span>                                        | `dapr.runtime`                      |
| <span data-ttu-id="c6b64-332">instance</span><span class="sxs-lookup"><span data-stu-id="c6b64-332">instance</span></span> | <span data-ttu-id="c6b64-333">Dapr が実行されるホスト名</span><span class="sxs-lookup"><span data-stu-id="c6b64-333">Hostname where Dapr runs</span></span>                             | <span data-ttu-id="c6b64-334">TSTSRV01</span><span class="sxs-lookup"><span data-stu-id="c6b64-334">TSTSRV01</span></span>                            |
| <span data-ttu-id="c6b64-335">app_id</span><span class="sxs-lookup"><span data-stu-id="c6b64-335">app_id</span></span>   | <span data-ttu-id="c6b64-336">Dapr アプリ ID</span><span class="sxs-lookup"><span data-stu-id="c6b64-336">Dapr App ID</span></span>                                          | <span data-ttu-id="c6b64-337">ordering-api</span><span class="sxs-lookup"><span data-stu-id="c6b64-337">ordering-api</span></span>                        |
| <span data-ttu-id="c6b64-338">ver</span><span class="sxs-lookup"><span data-stu-id="c6b64-338">ver</span></span>      | <span data-ttu-id="c6b64-339">Dapr ランタイムバージョン</span><span class="sxs-lookup"><span data-stu-id="c6b64-339">Dapr Runtime Version</span></span>                                 | <span data-ttu-id="c6b64-340">`1.0.0`-rc. 2</span><span class="sxs-lookup"><span data-stu-id="c6b64-340">`1.0.0`-rc.2</span></span>                        |

<span data-ttu-id="c6b64-341">トラブルシューティングのシナリオでログエントリを検索する場合は、 `time` `level` フィールドとフィールドが特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-341">When searching through logging entries in a troubleshooting scenario, the `time` and `level` fields are especially helpful.</span></span> <span data-ttu-id="c6b64-342">時刻フィールドは、特定の期間を特定できるようにログエントリを順序付けます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-342">The time field orders log entries so that you can pinpoint specific time periods.</span></span> <span data-ttu-id="c6b64-343">トラブルシューティングの際には、 *デバッグレベル* のログエントリによって、コードの動作に関する詳細情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-343">When troubleshooting, log entries at the *debug level* provide more information on the behavior of the code.</span></span>

#### <a name="plain-text-versus-json-format"></a><span data-ttu-id="c6b64-344">プレーンテキストと JSON 形式</span><span class="sxs-lookup"><span data-stu-id="c6b64-344">Plain text versus JSON format</span></span>

<span data-ttu-id="c6b64-345">既定では、Dapr は構造化されたログをプレーンテキスト形式で出力します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-345">By default, Dapr emits structured logging in plain-text format.</span></span> <span data-ttu-id="c6b64-346">すべてのログエントリは、キーと値のペアを含む文字列として書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-346">Every log entry is formatted as a string containing key/value pairs.</span></span> <span data-ttu-id="c6b64-347">プレーンテキストでのログ記録の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-347">Here's an example of logging in plain text:</span></span>

```text
== DAPR == time="2021-01-12T16:11:39.4669323+01:00" level=info msg="starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="log level set to: info" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="metrics server started on :62408/" app_id=ordering-api instance=TSTSRV03 scope=dapr.metrics type=log ver=1.0.0-rc.2
```

<span data-ttu-id="c6b64-348">単純に、この形式は解析が困難です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-348">While simple, this format is difficult to parse.</span></span> <span data-ttu-id="c6b64-349">監視ツールでログエントリを表示する場合は、JSON 形式のログ記録を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6b64-349">If viewing log entries with a monitoring tool, you'll want to enable JSON formatted logging.</span></span> <span data-ttu-id="c6b64-350">JSON エントリを使用すると、監視ツールは個々のフィールドにインデックスを作成し、クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-350">With JSON entries, a monitoring tool can index and query individual fields.</span></span> <span data-ttu-id="c6b64-351">JSON 形式のログエントリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-351">Here's the same log entries in JSON format:</span></span>

```json
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d", "scope": "dapr.runtime", "time": "2021-01-12T16:11:39.4669323+01:00", "type": "log", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "log level set to: info", "scope": "dapr.runtime", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "metrics server started on :62408/", "scope": "dapr.metrics", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
```

<span data-ttu-id="c6b64-352">JSON の書式設定を有効にするには、各 Dapr sidecar を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-352">To enable JSON formatting, you need to configure each Dapr sidecar.</span></span> <span data-ttu-id="c6b64-353">自己ホスト型モードでは、コマンドラインでフラグを指定でき `--log-as-json` ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-353">In self-hosted mode, you can specify the flag `--log-as-json` on the command line:</span></span>

```console
dapr run --app-id ordering-api --log-level info --log-as-json dotnet run
```

<span data-ttu-id="c6b64-354">Kubernetes では、 `dapr.io/log-as-json` アプリケーションの各デプロイに注釈を追加できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-354">In Kubernetes, you can add a `dapr.io/log-as-json` annotation to each deployment for the application:</span></span>

```yaml
annotations:
   dapr.io/enabled: "true"
   dapr.io/app-id: "ordering-api"
   dapr.io/app-port: "80"
   dapr.io/config: "dapr-config"
   dapr.io/log-as-json: "true"
```

<span data-ttu-id="c6b64-355">Kubernetes クラスターに、ヘルムを使用して Dapr をインストールすると、すべての Dapr システムサービスで JSON 形式のログ記録を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-355">When you install Dapr in a Kubernetes cluster using Helm, you can enable JSON formatted logging for all the Dapr system services:</span></span>

```console
helm repo add dapr https://dapr.github.io/helm-charts/
helm repo update
kubectl create namespace dapr-system
helm install dapr dapr/dapr --namespace dapr-system --set global.logAsJson=true
```

#### <a name="collect-logs"></a><span data-ttu-id="c6b64-356">ログの収集</span><span class="sxs-lookup"><span data-stu-id="c6b64-356">Collect logs</span></span>

<span data-ttu-id="c6b64-357">Dapr によって出力されたログは、分析のために監視バックエンドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-357">The logs emitted by Dapr can be fed into a monitoring back end for analysis.</span></span> <span data-ttu-id="c6b64-358">ログコレクターは、システムからログを収集して監視バックエンドに送信するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-358">A log collector is a component that collects logs from a system and sends them to a monitoring back end.</span></span> <span data-ttu-id="c6b64-359">一般的なログコレクターは [Fluentd](https://www.fluentd.org/)です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-359">A popular log collector is [Fluentd](https://www.fluentd.org/).</span></span> <span data-ttu-id="c6b64-360">「 [How to: Set Up Fluentd, エラスティック search And Kibana In Kubernetes in](https://docs.dapr.io/operations/monitoring/fluentd/) The dapr documentation」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-360">Check out the [How-To: Set up Fluentd, Elastic search and Kibana in Kubernetes](https://docs.dapr.io/operations/monitoring/fluentd/) in the Dapr documentation.</span></span> <span data-ttu-id="c6b64-361">この記事では、Fluentd を log collector として設定し、 [ELK Stack](https://www.elastic.co/elastic-stack) (エラスティック検索と Kibana) を監視バックエンドとして設定する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-361">This article contains instructions for setting up Fluentd as log collector and the [ELK Stack](https://www.elastic.co/elastic-stack) (Elastic Search and Kibana) as a monitoring back end.</span></span>

### <a name="health-status"></a><span data-ttu-id="c6b64-362">正常性状態</span><span class="sxs-lookup"><span data-stu-id="c6b64-362">Health status</span></span>

<span data-ttu-id="c6b64-363">サービスの正常性状態は、その可用性に関する洞察を提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-363">The health status of a service provides insight into its availability.</span></span> <span data-ttu-id="c6b64-364">各 dapr サイドカーは、ホスト環境でサイドカーの正常性を判断するために使用できる正常性 API を公開します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-364">Each Dapr sidecar exposes a health API that can be used by the hosting environment to determine the health of the sidecar.</span></span> <span data-ttu-id="c6b64-365">API には、次の1つの操作があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-365">The API has one operation:</span></span>

```console
GET http://localhost:3500/v1.0/healthz
```

<span data-ttu-id="c6b64-366">この操作では、次の2つの HTTP 状態コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-366">The operation returns two HTTP status codes:</span></span>

- <span data-ttu-id="c6b64-367">204: サイドカーが正常な状態である場合</span><span class="sxs-lookup"><span data-stu-id="c6b64-367">204: When the sidecar is healthy</span></span>
- <span data-ttu-id="c6b64-368">500: サイドカーが正常でない場合</span><span class="sxs-lookup"><span data-stu-id="c6b64-368">500: when the sidecar isn't healthy</span></span>

<span data-ttu-id="c6b64-369">自己ホスト型モードで実行している場合、正常性 API は自動的には呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-369">When running in self-hosted mode, the health API isn't automatically invoked.</span></span> <span data-ttu-id="c6b64-370">アプリケーションコードまたは正常性監視ツールから API を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-370">You can invoke the API though from application code or a health monitoring tool.</span></span>

<span data-ttu-id="c6b64-371">Kubernetes で実行されている場合、Dapr sidecar は、自動的に Kubernetes を構成して、 *ライブプローブ* および *準備プローブ* を実行するための正常性 API を使用するようにを構成します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-371">When running in Kubernetes, the Dapr sidecar-injector automatically configures Kubernetes to use the health API for executing *liveness probes* and *readiness probes*.</span></span>

<span data-ttu-id="c6b64-372">Kubernetes は、ライブプローブを使用して、コンテナーが起動して実行されているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-372">Kubernetes uses liveness probes to determine whether a container is up and running.</span></span> <span data-ttu-id="c6b64-373">Liveness probe がエラーコードを返した場合、Kubernetes はコンテナーが停止していると見なし、自動的に再起動します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-373">If a liveness probe returns a failure code, Kubernetes will assume the container is dead and automatically restart it.</span></span> <span data-ttu-id="c6b64-374">この機能により、アプリケーションの全体的な可用性が向上します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-374">This feature increases the overall availability of your application.</span></span>

<span data-ttu-id="c6b64-375">Kubernetes は、準備プローブを使用して、コンテナーがトラフィックの受け入れを開始する準備ができているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-375">Kubernetes uses readiness probes to determine whether a container is ready to start accepting traffic.</span></span> <span data-ttu-id="c6b64-376">すべてのコンテナーの準備が整ったら、ポッドは準備完了と見なされます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-376">A pod is considered ready when all of its containers are ready.</span></span> <span data-ttu-id="c6b64-377">準備とは、Kubernetes サービスが負荷分散シナリオでポッドにトラフィックを送信できるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-377">Readiness determines whether a Kubernetes service can direct traffic to a pod in a load-balancing scenario.</span></span> <span data-ttu-id="c6b64-378">準備ができていないポッドは、ロードバランサーから自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-378">Pods that aren't ready are automatically removed from the load-balancer.</span></span>

<span data-ttu-id="c6b64-379">ライブおよび準備プローブには、いくつかの構成可能なパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-379">Liveness and readiness probes have several configurable parameters.</span></span> <span data-ttu-id="c6b64-380">どちらも、ポッドのマニフェストファイルのコンテナー仕様セクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-380">Both are configured in the container spec section of a pod's manifest file.</span></span> <span data-ttu-id="c6b64-381">既定では、Dapr は各サイドカーコンテナーに対して次の構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-381">By default, Dapr uses the following configuration for each sidecar container:</span></span>

```yaml
livenessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold : 3
readinessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold: 3
```

 <span data-ttu-id="c6b64-382">プローブでは、次のパラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-382">The following parameters are available for the probes:</span></span>

- <span data-ttu-id="c6b64-383">は、 `path` Dapr HEALTH API エンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-383">The `path` specifies the Dapr health API endpoint.</span></span>
- <span data-ttu-id="c6b64-384">は、 `port` Dapr HEALTH API ポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-384">The `port` specifies the Dapr health API port.</span></span>
- <span data-ttu-id="c6b64-385">は、 `initialDelaySeconds` 最初にコンテナーのプローブを開始する前に Kubernetes が待機する秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-385">The `initialDelaySeconds`specifies the number of seconds Kubernetes will wait before it starts probing a container for the first time.</span></span>
- <span data-ttu-id="c6b64-386">は、 `periodSeconds` 各プローブ間で Kubernetes が待機する秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-386">The `periodSeconds` specifies the number of seconds Kubernetes will wait between each probe.</span></span>
- <span data-ttu-id="c6b64-387">は、 `timeoutSeconds` タイムアウトするまでに Kubernetes が API からの応答を待機する秒数を指定します。タイムアウトはエラーとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-387">The `timeoutSeconds` specifies the number of seconds Kubernetes will wait on a response from the API before timing out. A timeout is interpreted as a failure.</span></span>
- <span data-ttu-id="c6b64-388">は、コンテナーが動作して `failureThreshold` いないか準備されていないと見なす前に、Kubernetes が受け入れる失敗状態コードの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-388">The `failureThreshold`specifies the number of failed status code Kubernetes will accept before considering the container not alive or not ready.</span></span>

### <a name="dapr-dashboard"></a><span data-ttu-id="c6b64-389">Dapr ダッシュボード</span><span class="sxs-lookup"><span data-stu-id="c6b64-389">Dapr dashboard</span></span>

<span data-ttu-id="c6b64-390">Dapr は、Dapr アプリケーション、コンポーネント、および構成に関するステータス情報を示すダッシュボードを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-390">Dapr offers a dashboard that presents status information on Dapr applications, components, and configurations.</span></span> <span data-ttu-id="c6b64-391">Dapr CLI を使用して、ポート8080でローカルコンピューター上の web アプリケーションとしてダッシュボードを開始します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-391">Use the Dapr CLI to start the dashboard as a web-application on the local machine on port 8080:</span></span>

```console
dapr dashboard
```

<span data-ttu-id="c6b64-392">Kubernetes で実行されている Dapr アプリケーションの場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-392">For Dapr application running in Kubernetes, use the following command:</span></span>

```console
dapr dashboard -k
```

<span data-ttu-id="c6b64-393">ダッシュボードが開き、アプリケーション内のすべてのサービスの概要が表示されます。これには、Dapr sidecar があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-393">The dashboard opens with an overview of all services in your application that have a Dapr sidecar.</span></span> <span data-ttu-id="c6b64-394">次のスクリーンショットは、Kubernetes で実行されている eShopOnDapr アプリケーションの Dapr ダッシュボードを示しています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-394">The following screenshot shows the Dapr dashboard for the eShopOnDapr application running in Kubernetes:</span></span>

![Dapr ダッシュボードの [概要] ページ](media/observability/dapr-dashboard-overview.png)

<span data-ttu-id="c6b64-396">Dapr ダッシュボードは、Dapr アプリケーションのトラブルシューティングを行うときに非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-396">The Dapr dashboard is invaluable when troubleshooting a Dapr application.</span></span> <span data-ttu-id="c6b64-397">Dapr とシステムサービスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-397">It provides information about Dapr sidecars and system services.</span></span> <span data-ttu-id="c6b64-398">ログエントリなど、各サービスの構成をドリルダウンすることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-398">You can drill down into the configuration of each service, including the logging entries.</span></span>

<span data-ttu-id="c6b64-399">ダッシュボードには、アプリケーションの構成済みのコンポーネント (およびその構成) も表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-399">The dashboard also shows the configured components (and their configuration) for your application:</span></span>

![[Dapr ダッシュボードコンポーネント] ページ](media/observability/dapr-dashboard-components.png)

<span data-ttu-id="c6b64-401">ダッシュボードでは、大量の情報が提供されています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-401">There's a large amount of information available through the dashboard.</span></span> <span data-ttu-id="c6b64-402">これを検出するには、Dapr アプリケーションを実行し、ダッシュボードを参照します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-402">You can discover it by running a Dapr application and browsing the dashboard.</span></span> <span data-ttu-id="c6b64-403">付属の eShopOnDapr アプリケーションを使用してを開始できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-403">You can use the accompanying eShopOnDapr application to start.</span></span>

<span data-ttu-id="c6b64-404">Dapr ダッシュボードコマンドの詳細については、dapr ドキュメントの「 [dapr DASHBOARD CLI コマンドリファレンス](https://docs.dapr.io/reference/cli/dapr-dashboard/) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-404">Check out the [Dapr dashboard CLI command reference](https://docs.dapr.io/reference/cli/dapr-dashboard/) in the Dapr docs for more information on the Dapr dashboard commands.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="c6b64-405">Dapr .NET SDK を使用する</span><span class="sxs-lookup"><span data-stu-id="c6b64-405">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="c6b64-406">Dapr .NET SDK には、特定の可観測性機能が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-406">The Dapr .NET SDK doesn't contain any specific observability features.</span></span> <span data-ttu-id="c6b64-407">可観測性のすべての機能は、Dapr レベルで提供されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-407">All observability features are offered at the Dapr level.</span></span>

<span data-ttu-id="c6b64-408">.NET アプリケーションコードからテレメトリを生成する場合は、 [OPENTELEMETRY SDK for .net](https://opentelemetry.io/docs/net/)を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-408">If you want to emit telemetry from your .NET application code, you should consider the [OpenTelemetry SDK for .NET](https://opentelemetry.io/docs/net/).</span></span> <span data-ttu-id="c6b64-409">オープンテレメトリプロジェクトは、クロスプラットフォーム、オープンソース、およびベンダーに依存しないプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-409">The Open Telemetry project is cross-platform, open source, and vendor agnostic.</span></span> <span data-ttu-id="c6b64-410">テレメトリデータを生成、出力、収集、処理、およびエクスポートするためのエンドツーエンドの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-410">It provides an end-to-end implementation to generate, emit, collect, process, and export telemetry data.</span></span> <span data-ttu-id="c6b64-411">自動および手動のインストルメンテーションをサポートする言語ごとに1つのインストルメンテーションライブラリがあります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-411">There's a single instrumentation library per language that supports automatic and manual instrumentation.</span></span> <span data-ttu-id="c6b64-412">テレメトリはオープンテレメトリ標準を使用して公開されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-412">Telemetry is published using the Open Telemetry standard.</span></span> <span data-ttu-id="c6b64-413">このプロジェクトには、クラウドプロバイダー、ベンダー、およびエンドユーザーからの幅広い業界サポートと導入が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-413">The project has broad industry support and adoption from cloud providers, vendors, and end users.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="c6b64-414">参照アプリケーション: eShopOnDapr</span><span class="sxs-lookup"><span data-stu-id="c6b64-414">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="c6b64-415">付随する eShopOnDapr reference アプリケーションの可観測性は、いくつかの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-415">Observability in accompanying eShopOnDapr reference application consists of several parts.</span></span> <span data-ttu-id="c6b64-416">すべてのサイドカーのテレメトリがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-416">Telemetry from all of the sidecars is captured.</span></span> <span data-ttu-id="c6b64-417">また、以前の eShopOnContainers サンプルから継承された他の可観測性機能もあります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-417">Additionally, there are other observability features inherited from the earlier eShopOnContainers sample.</span></span>

### <a name="custom-health-dashboard"></a><span data-ttu-id="c6b64-418">カスタム正常性ダッシュボード</span><span class="sxs-lookup"><span data-stu-id="c6b64-418">Custom health dashboard</span></span>

<span data-ttu-id="c6b64-419">EShopOnDapr の **Webstatus** プロジェクトは、eShop サービスの正常性に関する洞察を提供するカスタム正常性ダッシュボードです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-419">The **WebStatus** project in eShopOnDapr is a custom health dashboard that gives insight into the health of the eShop services.</span></span> <span data-ttu-id="c6b64-420">このダッシュボードは Dapr health API を使用しませんが、ASP.NET Core の組み込みの [正常性チェックメカニズム](/aspnet/core/host-and-deploy/health-checks) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-420">This dashboard doesn't use the Dapr health API but uses the built-in [health checks mechanism](/aspnet/core/host-and-deploy/health-checks) of ASP.NET Core.</span></span> <span data-ttu-id="c6b64-421">ダッシュボードは、サービスの正常性状態だけでなく、サービスの依存関係の正常性状態も提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-421">The dashboard not only provides the health status of the services, but also the health of the dependencies of the services.</span></span> <span data-ttu-id="c6b64-422">たとえば、データベースを使用するサービスは、次のスクリーンショットに示すように、このデータベースの正常性状態も提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-422">For example, a service that uses a database also provides the health status of this database as shown in the following screenshot:</span></span>

![eShopOnDapr カスタム正常性ダッシュボード](media/observability/eshop-health-dashboard.png)

### <a name="seq-log-aggregator"></a><span data-ttu-id="c6b64-424">Seq ログアグリゲーター</span><span class="sxs-lookup"><span data-stu-id="c6b64-424">Seq log aggregator</span></span>

<span data-ttu-id="c6b64-425">[Seq](https://datalust.co/seq) は、ログを集計するために eShopOnDapr で使用される一般的なログアグリゲーターサーバーです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-425">[Seq](https://datalust.co/seq) is a popular log aggregator server that is used in eShopOnDapr to aggregate logs.</span></span> <span data-ttu-id="c6b64-426">Seq 取り込みは、Dapr システムサービスやサイドカーからではなく、アプリケーションサービスからのログ記録を行います。</span><span class="sxs-lookup"><span data-stu-id="c6b64-426">Seq ingests logging from application services, but not from Dapr system services or sidecars.</span></span> <span data-ttu-id="c6b64-427">Seq インデックスはアプリケーションログを記録し、ログを分析してクエリを実行するための web フロントエンドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-427">Seq indexes application logging and offers a web front end for analyzing and querying the logs.</span></span> <span data-ttu-id="c6b64-428">また、監視ダッシュボードを構築するための機能も用意されています。</span><span class="sxs-lookup"><span data-stu-id="c6b64-428">It also offers functionality for building monitoring dashboards.</span></span>

<span data-ttu-id="c6b64-429">EShopOnDapr アプリケーションサービスは、 [Serilog](https://serilog.net/) ログライブラリを使用して構造化ログを出力します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-429">The eShopOnDapr application services emit structured logging using the [SeriLog](https://serilog.net/) logging library.</span></span> <span data-ttu-id="c6b64-430">Serilog は、 **シンク** と呼ばれる構成要素にログイベントを発行します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-430">Serilog publishes log events to a construct called a **sink**.</span></span> <span data-ttu-id="c6b64-431">シンクは、Serilog がログイベントを書き込むターゲットプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-431">A sink is simply a target platform to which Serilog writes its logging events.</span></span> <span data-ttu-id="c6b64-432">Seq 用に1つなど、[多数の Serilog シンクを使用でき](https://github.com/serilog/serilog/wiki/Provided-Sinks)ます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-432">[Many Serilog sinks are available](https://github.com/serilog/serilog/wiki/Provided-Sinks), including one for Seq.</span></span> <span data-ttu-id="c6b64-433">Seq は、eShopOnDapr で使用される Serilog シンクです。</span><span class="sxs-lookup"><span data-stu-id="c6b64-433">Seq is the Serilog sink used in eShopOnDapr.</span></span>

### <a name="application-insights"></a><span data-ttu-id="c6b64-434">Application Insights</span><span class="sxs-lookup"><span data-stu-id="c6b64-434">Application Insights</span></span>

<span data-ttu-id="c6b64-435">また、eShopOnDapr services は、Microsoft Application Insights SDK for .NET Core を使用して Azure アプリケーションインサイトに直接テレメトリを送信します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-435">eShopOnDapr services also send telemetry directly to Azure Application Insights using the Microsoft Application Insights SDK for .NET Core.</span></span> <span data-ttu-id="c6b64-436">詳細については、Microsoft docs の「 [ASP.NET Core アプリケーションの Azure アプリケーションインサイト](/azure/azure-monitor/app/asp-net-core) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-436">For more information, see [Azure Application Insights for ASP.NET Core applications](/azure/azure-monitor/app/asp-net-core) in the Microsoft docs.</span></span>

## <a name="summary"></a><span data-ttu-id="c6b64-437">まとめ</span><span class="sxs-lookup"><span data-stu-id="c6b64-437">Summary</span></span>

<span data-ttu-id="c6b64-438">運用環境で分散システムを実行する場合は、優れた可観測性が不可欠です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-438">Good observability is crucial when running a distributed system in production.</span></span>

<span data-ttu-id="c6b64-439">Dapr は、分散トレース、ログ記録、メトリック、正常性状態など、さまざまな種類のテレメトリを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-439">Dapr provides different types of telemetry, including distributed tracing, logging, metrics, and health status.</span></span>

<span data-ttu-id="c6b64-440">Dapr は、Dapr システムサービスと sidecars のテレメトリのみを生成します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-440">Dapr only produces telemetry for the Dapr system services and sidecars.</span></span> <span data-ttu-id="c6b64-441">アプリケーションコードからのテレメトリは自動的に含まれません。</span><span class="sxs-lookup"><span data-stu-id="c6b64-441">Telemetry from your application code isn't automatically included.</span></span> <span data-ttu-id="c6b64-442">ただし、OpenTelemetry SDK for .NET などの特定の SDK を使用して、アプリケーションコードからテレメトリを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-442">You can however use a specific SDK like the OpenTelemetry SDK for .NET to emit telemetry from your application code.</span></span>

<span data-ttu-id="c6b64-443">Dapr テレメトリはオープン標準ベースの形式で生成されるため、使用可能な多数の監視ツールによって取り込まれたできます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-443">Dapr telemetry is produced in an open-standards based format so it can be ingested by a large set of available monitoring tools.</span></span> <span data-ttu-id="c6b64-444">例として、Zipkin、Azure アプリケーション Insights、ELK Stack、New 聖箱、Grafana などがあります。</span><span class="sxs-lookup"><span data-stu-id="c6b64-444">Some examples are: Zipkin, Azure Application Insights, the ELK Stack, New Relic, and Grafana.</span></span> <span data-ttu-id="c6b64-445">特定の監視バックエンドを使用して Dapr アプリケーションを監視する方法については、dapr のドキュメントで「 [dapr を使用したアプリケーションの監視](https://docs.dapr.io/operations/monitoring/) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6b64-445">See [Monitor your application with Dapr](https://docs.dapr.io/operations/monitoring/) in the Dapr documentation for tutorials on how to monitor your Dapr applications with specific monitoring back ends.</span></span>

<span data-ttu-id="c6b64-446">テレメトリを取り込みして監視バックエンドに公開するテレメトリようが必要です。</span><span class="sxs-lookup"><span data-stu-id="c6b64-446">You'll need a telemetry scraper that ingests telemetry and publishes it to the monitoring back end.</span></span>

<span data-ttu-id="c6b64-447">Dapr は、構造化されたログを出力するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-447">Dapr can be configured to emit structured logging.</span></span> <span data-ttu-id="c6b64-448">構造化ログは、バックエンド監視ツールでインデックスを作成できるため、優先されます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-448">Structured logging is favored as it can be indexed by back-end monitoring tools.</span></span> <span data-ttu-id="c6b64-449">インデックス付きログを使用すると、ログの検索時にリッチクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c6b64-449">Indexed logging enables users to execute rich queries when searching through the logging.</span></span>

<span data-ttu-id="c6b64-450">Dapr は、Dapr サービスと構成に関する情報を提示するダッシュボードを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b64-450">Dapr offers a dashboard that presents information about the Dapr services and configuration.</span></span>

## <a name="references"></a><span data-ttu-id="c6b64-451">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6b64-451">References</span></span>

- [<span data-ttu-id="c6b64-452">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="c6b64-452">Azure Application Insights</span></span>](/azure/azure-monitor/app/app-insights-overview/)
- [<span data-ttu-id="c6b64-453">テレメトリを開く</span><span class="sxs-lookup"><span data-stu-id="c6b64-453">Open Telemetry</span></span>](https://opentelemetry.io/)
- [<span data-ttu-id="c6b64-454">Zipkin</span><span class="sxs-lookup"><span data-stu-id="c6b64-454">Zipkin</span></span>](https://zipkin.io/)
- [<span data-ttu-id="c6b64-455">W3C トレースコンテキスト</span><span class="sxs-lookup"><span data-stu-id="c6b64-455">W3C Trace Context</span></span>](https://www.w3.org/TR/trace-context/)
- [<span data-ttu-id="c6b64-456">Jaeger</span><span class="sxs-lookup"><span data-stu-id="c6b64-456">Jaeger</span></span>](https://www.jaegertracing.io/)
- [<span data-ttu-id="c6b64-457">New Relic</span><span class="sxs-lookup"><span data-stu-id="c6b64-457">New Relic</span></span>](https://newrelic.com/)
- [<span data-ttu-id="c6b64-458">Prometheus</span><span class="sxs-lookup"><span data-stu-id="c6b64-458">Prometheus</span></span>](https://prometheus.io/)
- [<span data-ttu-id="c6b64-459">Grafana</span><span class="sxs-lookup"><span data-stu-id="c6b64-459">Grafana</span></span>](https://grafana.com/grafana/)
- [<span data-ttu-id="c6b64-460">.NET 用テレメトリ SDK を開く</span><span class="sxs-lookup"><span data-stu-id="c6b64-460">Open Telemetry SDK for .NET</span></span>](https://opentelemetry.io/docs/net/)
- [<span data-ttu-id="c6b64-461">Fluentd</span><span class="sxs-lookup"><span data-stu-id="c6b64-461">Fluentd</span></span>](https://www.fluentd.org/)
- [<span data-ttu-id="c6b64-462">ELK スタック</span><span class="sxs-lookup"><span data-stu-id="c6b64-462">ELK stack</span></span>](https://www.elastic.co/elastic-stack)
- [<span data-ttu-id="c6b64-463">Seq</span><span class="sxs-lookup"><span data-stu-id="c6b64-463">Seq</span></span>](https://datalust.co/seq)
- [<span data-ttu-id="c6b64-464">Serilog</span><span class="sxs-lookup"><span data-stu-id="c6b64-464">Serilog</span></span>](https://serilog.net/)

> [!div class="step-by-step"]
> <span data-ttu-id="c6b64-465">[前へ](bindings.md)
> [次へ](secrets.md)</span><span class="sxs-lookup"><span data-stu-id="c6b64-465">[Previous](bindings.md)
[Next](secrets.md)</span></span>
