---
title: 分散トレース - .NET
description: .NET の分散トレースの概要です。
ms.date: 03/15/2021
ms.openlocfilehash: 274a058bf9daf096958813575901e83a3976a3a4
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111115"
---
# <a name="net-distributed-tracing"></a><span data-ttu-id="09e78-103">.NET の分散トレース</span><span class="sxs-lookup"><span data-stu-id="09e78-103">.NET Distributed Tracing</span></span>

<span data-ttu-id="09e78-104">分散トレースは、特に複数のコンピューターやプロセスに分散される可能性があるアプリケーション内のエラーとパフォーマンスの問題を、エンジニアがローカライズするのに役立つ診断手法です。</span><span class="sxs-lookup"><span data-stu-id="09e78-104">Distributed tracing is a diagnostic technique that helps engineers localize failures and performance issues within applications, especially those that may be distributed across multiple machines or processes.</span></span> <span data-ttu-id="09e78-105">この手法は、アプリケーションを介して要求を追跡し、さまざまなアプリケーション コンポーネントによって実行される作業を相互に関連付けて、アプリケーションが同時要求に対して実行する可能性がある他の作業から分離します。</span><span class="sxs-lookup"><span data-stu-id="09e78-105">This technique tracks requests through an application correlating together work done by different application components and separating it from other work the application may be doing for concurrent requests.</span></span> <span data-ttu-id="09e78-106">たとえば、一般的な Web サービスへの要求は、最初にロード バランサーによって受信され、次に Web サーバー プロセスに転送され、その後、データベースに対して複数のクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="09e78-106">For example a request to a typical web service might be first received by a load balancer, then forwarded to a web server process, which then makes several queries to a database.</span></span> <span data-ttu-id="09e78-107">分散トレースを使用すると、エンジニアは、これらのステップのいずれかが失敗したかどうか、各ステップにかかった時間、および実行時に各ステップによって生成されたメッセージをログする可能性を見分けることができます。</span><span class="sxs-lookup"><span data-stu-id="09e78-107">Using distributed tracing allows engineers to distinguish if any of those steps failed, how long each step took, and potentially logging messages produced by each step as it ran.</span></span>

## <a name="getting-started-for-net-app-developers"></a><span data-ttu-id="09e78-108">.NET アプリ開発者向けの概要</span><span class="sxs-lookup"><span data-stu-id="09e78-108">Getting started for .NET app developers</span></span>

<span data-ttu-id="09e78-109">主要な .NET ライブラリは、分散トレース情報を自動的に生成するためにインストルメント化されますが、後で確認できるように、この情報を収集して保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e78-109">Key .NET libraries are instrumented to produce distributed tracing information automatically but this information needs to be collected and stored so that it will be available for review later.</span></span>
<span data-ttu-id="09e78-110">通常、アプリ開発者は、このトレース情報を格納するテレメトリ サービスを選択し、対応するライブラリを使用して、選択したサービスに分散トレース テレメトリを送信します。</span><span class="sxs-lookup"><span data-stu-id="09e78-110">Typically app developers will select a telemetry service that stores this trace information for them and then use a corresponding library to transmit the distributed tracing telemetry to their chosen service.</span></span> <span data-ttu-id="09e78-111">[OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) は複数のサービスをサポートするベンダー中立ライブラリで、[Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) は Microsoft が提供する完全な機能を備えたサービスです。また、統合された .NET ソリューションを提供する高品質のサード パーティの APM ベンダーも多数存在します。</span><span class="sxs-lookup"><span data-stu-id="09e78-111">[OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) is a vendor neutral library that supports several services, [Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) is a full featured service provided by Microsoft, and there are many high quality 3rd party APM vendors that offer integrated .NET solutions.</span></span>

- [<span data-ttu-id="09e78-112">分散トレースの概念を理解する</span><span class="sxs-lookup"><span data-stu-id="09e78-112">Understand distributed tracing concepts</span></span>](distributed-tracing-concepts.md)
- <span data-ttu-id="09e78-113">ガイド</span><span class="sxs-lookup"><span data-stu-id="09e78-113">Guides</span></span>
  - [<span data-ttu-id="09e78-114">Application Insights を使用した分散トレースの収集</span><span class="sxs-lookup"><span data-stu-id="09e78-114">Collect distributed traces with Application Insights</span></span>](distributed-tracing-collection-walkthroughs.md#collect-traces-using-application-insights)
  - [<span data-ttu-id="09e78-115">OpenTelemetry を使用した分散トレースの収集</span><span class="sxs-lookup"><span data-stu-id="09e78-115">Collect distributed traces with OpenTelemetry</span></span>](distributed-tracing-collection-walkthroughs.md#collect-traces-using-opentelemetry)
  - [<span data-ttu-id="09e78-116">カスタム ロジックを使用した分散トレースの収集</span><span class="sxs-lookup"><span data-stu-id="09e78-116">Collect distributed traces with custom logic</span></span>](distributed-tracing-collection-walkthroughs.md#collect-traces-using-custom-logic)
  - [<span data-ttu-id="09e78-117">カスタム分散トレース インストルメンテーションの追加</span><span class="sxs-lookup"><span data-stu-id="09e78-117">Adding custom distributed trace instrumentation</span></span>](distributed-tracing-instrumentation-walkthroughs.md)

<span data-ttu-id="09e78-118">サード パーティのテレメトリ収集サービスについては、ベンダーから提供されているセットアップ手順に従います。</span><span class="sxs-lookup"><span data-stu-id="09e78-118">For 3rd party telemetry collection services follow the setup instructions provided by the vendor.</span></span>

## <a name="getting-started-for-net-library-developers"></a><span data-ttu-id="09e78-119">.NET ライブラリ開発者向けの概要</span><span class="sxs-lookup"><span data-stu-id="09e78-119">Getting started for .NET library developers</span></span>

<span data-ttu-id="09e78-120">.NET ライブラリでは、テレメトリが最終的にどのように収集されるかを考慮する必要はなく、どのように生成されるかだけを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e78-120">.NET libraries don't need to be concerned with how telemetry is ultimately collected, only with how it is produced.</span></span> <span data-ttu-id="09e78-121">ライブラリを使用する .NET アプリ開発者が、ライブラリで実行される作業を分散トレースで詳細に確認できると思われる場合は、それをサポートする分散トレース インストルメンテーションを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e78-121">If you believe .NET app developers that use your library would appreciate seeing the work that it does detailed in a distributed trace then you should add distributed tracing instrumentation to support it.</span></span>

- [<span data-ttu-id="09e78-122">分散トレースの概念を理解する</span><span class="sxs-lookup"><span data-stu-id="09e78-122">Understand distributed tracing concepts</span></span>](distributed-tracing-concepts.md)
- <span data-ttu-id="09e78-123">ガイド</span><span class="sxs-lookup"><span data-stu-id="09e78-123">Guides</span></span>
  - [<span data-ttu-id="09e78-124">カスタム分散トレース インストルメンテーションの追加</span><span class="sxs-lookup"><span data-stu-id="09e78-124">Adding custom distributed trace instrumentation</span></span>](distributed-tracing-instrumentation-walkthroughs.md)
