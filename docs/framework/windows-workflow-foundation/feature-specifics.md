---
title: Windows Workflow Foundation の機能仕様
description: この記事では、.NET Framework 4 によって Windows Workflow Foundation に追加される新機能と、その機能が役立つ可能性があるシナリオについて説明します。
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 6c508e184aee0e4aa0634d128de94ac45ef78f45
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716292"
---
# <a name="windows-workflow-foundation-feature-specifics"></a><span data-ttu-id="9297d-103">Windows Workflow Foundation の機能仕様</span><span class="sxs-lookup"><span data-stu-id="9297d-103">Windows Workflow Foundation Feature Specifics</span></span>

<span data-ttu-id="9297d-104">.NET Framework 4 では、Windows Workflow Foundation にいくつかの機能が追加されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-104">.NET Framework 4 adds a number of features to Windows Workflow Foundation.</span></span> <span data-ttu-id="9297d-105">このドキュメントでは、いくつかの新機能について説明し、役に立つ可能性のあるシナリオの詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="9297d-105">This document describes a number of the new features, and gives details about scenarios in which they may be useful.</span></span>

## <a name="messaging-activities"></a><span data-ttu-id="9297d-106">メッセージング アクティビティ</span><span class="sxs-lookup"><span data-stu-id="9297d-106">Messaging Activities</span></span>

<span data-ttu-id="9297d-107">メッセージング アクティビティ (<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.ReceiveReply>) は、ワークフローから WCF メッセージを送受信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-107">The messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) are used to send and receive WCF messages from your workflow.</span></span> <span data-ttu-id="9297d-108"><xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply> アクティビティは、標準の WCF Web サービスと同様に、WSDL 経由で公開される Windows Communication Foundation (WCF) サービス操作を形成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-108"><xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities are used to form a Windows Communication Foundation (WCF) service operation that is exposed via WSDL just like standard WCF web services.</span></span> <span data-ttu-id="9297d-109"><xref:System.ServiceModel.Activities.Send> と <xref:System.ServiceModel.Activities.ReceiveReply> は、WCF <xref:System.ServiceModel.ChannelFactory> と同様に Web サービスを使用するために使用されます。事前に構成されたアクティビティを生成する Workflow Foundation 用の **サービス参照の追加** エクスペリエンスもあります。</span><span class="sxs-lookup"><span data-stu-id="9297d-109"><xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> are used to consume a web service similar to a WCF <xref:System.ServiceModel.ChannelFactory>; an **Add Service Reference** experience also exists for Workflow Foundation that generates pre-configured activities.</span></span>

### <a name="getting-started-with-messaging-activities"></a><span data-ttu-id="9297d-110">メッセージング アクティビティの概要</span><span class="sxs-lookup"><span data-stu-id="9297d-110">Getting Started with Messaging Activities</span></span>

- <span data-ttu-id="9297d-111">Visual Studio 2012 で、WCF ワークフロー サービス アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-111">In Visual Studio 2012, create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="9297d-112"><xref:System.ServiceModel.Activities.Receive> と <xref:System.ServiceModel.Activities.SendReply> のペアがキャンバスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-112">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas.</span></span>

- <span data-ttu-id="9297d-113">プロジェクトを右クリックし、 **[サービス参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9297d-113">Right-click on the project and select **Add Service Reference**.</span></span> <span data-ttu-id="9297d-114">既存の Web サービス WSDL をポイントし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9297d-114">Point to an existing web service WSDL and click **OK**.</span></span> <span data-ttu-id="9297d-115">プロジェクトをビルドして、生成されたアクティビティ (<xref:System.ServiceModel.Activities.Send> と <xref:System.ServiceModel.Activities.ReceiveReply> を使用して実装) をツールボックスに表示します。</span><span class="sxs-lookup"><span data-stu-id="9297d-115">Build your project to show the generated activities (implemented using <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply>) in your toolbox.</span></span>

- [<span data-ttu-id="9297d-116">ワークフロー サービスのドキュメント</span><span class="sxs-lookup"><span data-stu-id="9297d-116">Workflow services documentation</span></span>](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a><span data-ttu-id="9297d-117">メッセージング アクティビティのシナリオ例</span><span class="sxs-lookup"><span data-stu-id="9297d-117">Messaging Activities Example Scenario</span></span>

<span data-ttu-id="9297d-118">`BestPriceFinder` サービスでは、複数の航空会社サービスを呼び出して、特定の航路の最良チケット価格を探します。</span><span class="sxs-lookup"><span data-stu-id="9297d-118">A `BestPriceFinder` service calls out to multiple airline services to find the best ticket price for a particular route.</span></span> <span data-ttu-id="9297d-119">このシナリオを実装するには、メッセージ アクティビティを使用して価格要求を受信し、バックエンド サービスから価格を取得して、価格要求に最良価格で応答する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-119">Implementing this scenario would require you to use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span> <span data-ttu-id="9297d-120">他の事前定義アクティビティを使用して、最良価格を計算するビジネス ロジックを作成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="9297d-120">It would also require you to use other out-of-box activities to create the business logic for calculating the best price.</span></span>

## <a name="workflowservicehost"></a><span data-ttu-id="9297d-121">WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="9297d-121">WorkflowServiceHost</span></span>

<span data-ttu-id="9297d-122"><xref:System.ServiceModel.WorkflowServiceHost> は、複数のインスタンス、構成、および WCF メッセージングをサポートする標準ワークフロー ホストです (ワークフローがホストされるためにメッセージングを使用する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="9297d-122">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren't required to use messaging in order to be hosted).</span></span> <span data-ttu-id="9297d-123">また、一連のサービス動作を介して永続性、追跡、およびインスタンス コントロールを統合します。</span><span class="sxs-lookup"><span data-stu-id="9297d-123">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span> <span data-ttu-id="9297d-124">WCF の <xref:System.ServiceModel.ServiceHost> と同様に、<xref:System.ServiceModel.WorkflowServiceHost> は、コンソール/WinForms/WPF アプリケーションまたは Windows サービスでの自己ホスト、または IIS や WAS での Web ホスト (.xamlx ファイルとして) が可能です。</span><span class="sxs-lookup"><span data-stu-id="9297d-124">Just like WCF's <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in a console/WinForms/WPF application or Windows service, or web-hosted (as a .xamlx file) in IIS or WAS.</span></span>

### <a name="getting-started-with-workflow-service-host"></a><span data-ttu-id="9297d-125">ワークフロー サービス ホストの概要</span><span class="sxs-lookup"><span data-stu-id="9297d-125">Getting Started with Workflow Service Host</span></span>

- <span data-ttu-id="9297d-126">Visual Studio 2010 で、WCF ワークフロー サービス アプリケーション プロジェクトを作成します。このプロジェクトは、Web ホスト環境で <xref:System.ServiceModel.WorkflowServiceHost> を使用するように設定されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-126">In Visual Studio 2010, create a WCF Workflow Service Application project: this project will be set up to use <xref:System.ServiceModel.WorkflowServiceHost> in a web-host environment.</span></span>

- <span data-ttu-id="9297d-127">非メッセージング ワークフローをホストするには、メッセージに基づいてインスタンスを作成するカスタム <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> を追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-127">In order to host a non-messaging workflow, add a custom <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> that will create the instance based on a message.</span></span>

- <span data-ttu-id="9297d-128">ワークフロー インスタンスは、<xref:System.ServiceModel.Activities.WorkflowControlEndpoint> を <xref:System.ServiceModel.WorkflowServiceHost> に追加し、<xref:System.ServiceModel.Activities.WorkflowControlClient> を使用することで制御 (中断や終了など) できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-128">Workflow instances can be controlled (e.g. suspended or terminated) by adding a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> to the <xref:System.ServiceModel.WorkflowServiceHost> and then using a <xref:System.ServiceModel.Activities.WorkflowControlClient>.</span></span>

- <span data-ttu-id="9297d-129"><xref:System.ServiceModel.WorkflowServiceHost> のサンプルは次のセクションにあります。</span><span class="sxs-lookup"><span data-stu-id="9297d-129">Samples for the <xref:System.ServiceModel.WorkflowServiceHost> can be found in the following sections:</span></span>

  - [<span data-ttu-id="9297d-130">実行</span><span class="sxs-lookup"><span data-stu-id="9297d-130">Execution</span></span>](./samples/execution.md)

  - <span data-ttu-id="9297d-131">アプリケーション: [中断されたインスタンスの管理](./samples/suspended-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-131">Application: [Suspended Instance Management](./samples/suspended-instance-management.md)</span></span>

- [<span data-ttu-id="9297d-132">ワークフロー サービスのホストの概要</span><span class="sxs-lookup"><span data-stu-id="9297d-132">Hosting Workflow services overview</span></span>](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a><span data-ttu-id="9297d-133">WorkflowServiceHost のシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-133">WorkflowServiceHost Scenario</span></span>

<span data-ttu-id="9297d-134">BestPriceFinder サービスでは、複数の航空会社サービスを呼び出して、特定の航路の最良チケット価格を探します。</span><span class="sxs-lookup"><span data-stu-id="9297d-134">A BestPriceFinder service calls out to multiple airline services to find the best ticket price for a particular route.</span></span> <span data-ttu-id="9297d-135">このシナリオを実装するには、<xref:System.ServiceModel.WorkflowServiceHost> にワークフローをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-135">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="9297d-136">メッセージ アクティビティを使用して価格要求を受信し、バックエンド サービスから価格を取得して、価格要求に最良価格で応答する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="9297d-136">It would also use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span>

## <a name="correlation"></a><span data-ttu-id="9297d-137">相関関係</span><span class="sxs-lookup"><span data-stu-id="9297d-137">Correlation</span></span>

<span data-ttu-id="9297d-138">相関関係は次の 2 つのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="9297d-138">A correlation is one of two things:</span></span>

- <span data-ttu-id="9297d-139">メッセージをグループ化する方法。つまり、要求メッセージとその応答の関係。</span><span class="sxs-lookup"><span data-stu-id="9297d-139">A way of grouping messages together; that is, the relationship between a request message and its reply.</span></span>

- <span data-ttu-id="9297d-140">サービス インスタンスにデータの一部をマッピングする方法。</span><span class="sxs-lookup"><span data-stu-id="9297d-140">A way of mapping a piece of data to a service instance</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-141">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-141">Getting Started</span></span>

- <span data-ttu-id="9297d-142">相関を開始するには、Visual Studio で新規プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-142">To get started with correlation, create a new project in Visual Studio.</span></span> <span data-ttu-id="9297d-143"><xref:System.ServiceModel.Activities.CorrelationHandle> 型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-143">Create a variable of type <xref:System.ServiceModel.Activities.CorrelationHandle>.</span></span>

- <span data-ttu-id="9297d-144">メッセージのグループ化に使用する相関関係の例は、メッセージをグループ化する要求/応答の相関関係です。</span><span class="sxs-lookup"><span data-stu-id="9297d-144">An example of correlation used to group messages together is a Request-Reply correlation that groups messages together.</span></span>

  - <span data-ttu-id="9297d-145"><xref:System.ServiceModel.Activities.Receive> アクティビティで、<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> プロパティをクリックし、前の最初のステップで作成した CorrelationHandle を使用して <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> を追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-145">On a <xref:System.ServiceModel.Activities.Receive> activity, click on the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> property and add a <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> using the CorrelationHandle created in the first step above.</span></span>

  - <span data-ttu-id="9297d-146"><xref:System.ServiceModel.Activities.Receive> を右クリックし、[SendReply の作成] をクリックして <xref:System.ServiceModel.Activities.SendReply> アクティビティを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-146">Create a <xref:System.ServiceModel.Activities.SendReply> activity by right-clicking on the <xref:System.ServiceModel.Activities.Receive> and clicking "Create SendReply".</span></span> <span data-ttu-id="9297d-147">これをワークフローの <xref:System.ServiceModel.Activities.Receive> アクティビティの後に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9297d-147">Paste it into your workflow after the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

- <span data-ttu-id="9297d-148">データの一部をサービス インスタンスにマッピングする例は、データの一部 (オーダー ID など) を特定のワークフロー インスタンスにマップするコンテンツ ベースの相関関係です。</span><span class="sxs-lookup"><span data-stu-id="9297d-148">An example of mapping a piece of data to a service instance is content-based correlation which maps a piece of data (for example, an order ID) to a particular workflow instance.</span></span>

  - <span data-ttu-id="9297d-149">任意のメッセージング アクティビティで、`CorrelationInitializers` プロパティをクリックし、上記で作成した <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 変数を使用して <xref:System.ServiceModel.Activities.CorrelationHandle> を追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-149">On any messaging activity, click on the `CorrelationInitializers` property and add a <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> using the <xref:System.ServiceModel.Activities.CorrelationHandle> variable created above.</span></span> <span data-ttu-id="9297d-150">ドロップダウン メニューで、メッセージ上の目的のプロパティ (OrderID など) をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9297d-150">Double-click on the desired property on the message (e.g. OrderID) from the drop-down menu.</span></span> <span data-ttu-id="9297d-151">`CorrelatesWith` プロパティを上記で使用した <xref:System.ServiceModel.Activities.CorrelationHandle> 変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="9297d-151">Set the `CorrelatesWith` property to the <xref:System.ServiceModel.Activities.CorrelationHandle> variable used above.</span></span>

- [<span data-ttu-id="9297d-152">相関関係の概念説明ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9297d-152">Correlation Conceptual Documentation</span></span>](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a><span data-ttu-id="9297d-153">相関関係のシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-153">Correlation Scenario</span></span>

<span data-ttu-id="9297d-154">注文処理ワークフローを使用して、新規注文の作成と、処理中の既存の注文の更新を処理します。</span><span class="sxs-lookup"><span data-stu-id="9297d-154">An order-processing workflow is used to handle new order creation and updating existing orders that are in process.</span></span> <span data-ttu-id="9297d-155">このシナリオを実装するには、ワークフローを <xref:System.ServiceModel.WorkflowServiceHost> にホストし、メッセージング アクティビティを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-155">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost> and use the messaging activities.</span></span> <span data-ttu-id="9297d-156">適切なワークフローに更新が行われるようにするために `orderId` に基づく相関関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="9297d-156">It would also require correlation based on the `orderId` to ensure that updates are made to the correct workflow.</span></span>

## <a name="simplified-configuration"></a><span data-ttu-id="9297d-157">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="9297d-157">Simplified Configuration</span></span>

<span data-ttu-id="9297d-158">WCF 構成スキーマは複雑であり、探すのが難しい多くの機能をユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="9297d-158">The WCF configuration schema is complex and provides users with many hard to find features.</span></span> <span data-ttu-id="9297d-159">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] では、次の機能で WCF ユーザーによるサービスの構成を支援することに重点を置いていました。</span><span class="sxs-lookup"><span data-stu-id="9297d-159">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], we have focused on helping WCF users configure their services with the following features:</span></span>

- <span data-ttu-id="9297d-160">サービスごとの明示的な構成の必要性をなくします。</span><span class="sxs-lookup"><span data-stu-id="9297d-160">Removing the need for explicit per-service configuration.</span></span> <span data-ttu-id="9297d-161">サービスに対して \<service> 要素を構成せず、かつ、サービスでエンドポイントがプログラムによって定義されない場合は、エンドポイントのセットが、サービスのベース アドレスごとに 1 つ、サービスによって実装されるコントラクトごとに 1 つ、サービスに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-161">If you do not configure any \<service> elements for your service, and your service does not define programmatically any endpoint, then a set of endpoints will be automatically added to your service, one per service base address and per contract implemented by your service.</span></span>

- <span data-ttu-id="9297d-162">明示的な構成のないサービスに適用される WCF バインディングおよび動作の既定値をユーザーが定義できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9297d-162">Enables the user to define default values for WCF bindings and behaviors, which will be applied to services with no explicit configuration.</span></span>

- <span data-ttu-id="9297d-163">標準のエンドポイントは、事前に構成された再利用可能なエンドポイントを定義します。このエンドポイントは、1 つ以上のエンドポイント プロパティ (アドレス、バインド、およびコントラクト) に対して固定値を持ち、カスタム プロパティを定義できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9297d-163">Standard endpoints define reusable preconfigured endpoints, which have fixed values for one or more of the endpoint properties (address, binding and contract), and allow defining custom properties.</span></span>

- <span data-ttu-id="9297d-164">最後に、<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> では WCF クライアント構成を集中管理できます。これは、アプリケーション ドメインの読み込み時の後に構成が選択または変更されるシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9297d-164">Finally, the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows you to do central management of WCF client configuration, useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-165">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-165">Getting Started</span></span>

- <span data-ttu-id="9297d-166">[WCF 4.0 開発者ガイド](/previous-versions/dotnet/articles/ee354381(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="9297d-166">[A Developer's Guide to WCF 4.0](/previous-versions/dotnet/articles/ee354381(v=msdn.10))</span></span>

- [<span data-ttu-id="9297d-167">構成チャネル ファクトリ</span><span class="sxs-lookup"><span data-stu-id="9297d-167">Configuration Channel Factory</span></span>](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [<span data-ttu-id="9297d-168">標準エンドポイント要素</span><span class="sxs-lookup"><span data-stu-id="9297d-168">Standard Endpoint Element</span></span>](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [<span data-ttu-id="9297d-169">.NET Framework 4 でのサービス構成の向上</span><span class="sxs-lookup"><span data-stu-id="9297d-169">Service configuration improvements in .NET Framework 4</span></span>](/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [<span data-ttu-id="9297d-170">.NET 4 でよくあるユーザーの誤り: WF/WCF サービス構成名の入力ミス</span><span class="sxs-lookup"><span data-stu-id="9297d-170">Common User Mistake in .NET 4: Mistyping the WF/WCF Service Configuration Name</span></span>](/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a><span data-ttu-id="9297d-171">簡略化された構成のシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-171">Simplified Configuration Scenarios</span></span>

- <span data-ttu-id="9297d-172">経験豊富な ASMX 開発者が WCF の使用開始を希望しています。</span><span class="sxs-lookup"><span data-stu-id="9297d-172">An experienced ASMX developer wants to start using WCF.</span></span> <span data-ttu-id="9297d-173">しかし、WCF は複雑すぎると思われます。</span><span class="sxs-lookup"><span data-stu-id="9297d-173">However, WCF seems way too complicated!</span></span> <span data-ttu-id="9297d-174">構成ファイルに書き込む必要のある情報は何ですか。</span><span class="sxs-lookup"><span data-stu-id="9297d-174">What is all that information that I need to write in a configuration file?</span></span> <span data-ttu-id="9297d-175">.NET 4 では、構成ファイルをまったく使用しないこともできます。</span><span class="sxs-lookup"><span data-stu-id="9297d-175">In .NET 4, you can even decide to not have a configuration file at all.</span></span>

- <span data-ttu-id="9297d-176">既存の WCF サービスのセットは構成とメンテナンスが非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="9297d-176">An existing set of WCF services are very difficult to configure and maintain.</span></span> <span data-ttu-id="9297d-177">構成ファイルには、変更するのが非常に危険な XML コードが何千行もあります。</span><span class="sxs-lookup"><span data-stu-id="9297d-177">The configuration file has thousands of lines of XML code that are extremely dangerous to touch.</span></span> <span data-ttu-id="9297d-178">コード量を管理しやすい量に減らすための支援が必要です。</span><span class="sxs-lookup"><span data-stu-id="9297d-178">Help is needed to reduce that amount of code to something more manageable.</span></span>

## <a name="data-contract-resolver"></a><span data-ttu-id="9297d-179">データ コントラクト リゾルバー</span><span class="sxs-lookup"><span data-stu-id="9297d-179">Data Contract Resolver</span></span>

<span data-ttu-id="9297d-180">.NET Framework 3.5 では、既知の型の設計にいくつかの制限がありました。</span><span class="sxs-lookup"><span data-stu-id="9297d-180">In .NET Framework 3.5, there were a few limitations in the design of known types:</span></span>

- <span data-ttu-id="9297d-181">シリアル化または逆シリアル化中に既知の型を動的に追加することはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="9297d-181">Adding known types dynamically, during serialization or deserialization, was not possible.</span></span>

- <span data-ttu-id="9297d-182">シリアライザーは不明な xsi:type の情報を処理できませんでした。</span><span class="sxs-lookup"><span data-stu-id="9297d-182">Serializers could not deal with unknown xsi:type information.</span></span>

- <span data-ttu-id="9297d-183">ユーザーは、ネットワーク上のシリアル化インスタンスのサイズを小さくするなど、ネットワーク上に出現する xsi:type を指定できませんでした。</span><span class="sxs-lookup"><span data-stu-id="9297d-183">It was not possible for users to specify what xsi:type they would like to have appear on the wire to, for instance, make the size of a serialization instance on the wire smaller.</span></span>

<span data-ttu-id="9297d-184">[DataContractResolver](../wcf/samples/datacontractresolver.md) では、.NET Framework 4.5 でこれらの問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-184">The [DataContractResolver](../wcf/samples/datacontractresolver.md) solves these issues in .NET Framework 4.5.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-185">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-185">Getting Started</span></span>

- [<span data-ttu-id="9297d-186">データ コントラクト リゾルバー API のドキュメント</span><span class="sxs-lookup"><span data-stu-id="9297d-186">Data Contract Resolver API documentation</span></span>](xref:System.Runtime.Serialization.DataContractResolver)

- [<span data-ttu-id="9297d-187">データ コントラクト リゾルバーの概要</span><span class="sxs-lookup"><span data-stu-id="9297d-187">Introducing the Data Contract Resolver</span></span>](/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- <span data-ttu-id="9297d-188">サンプル:</span><span class="sxs-lookup"><span data-stu-id="9297d-188">Samples:</span></span>

  - [<span data-ttu-id="9297d-189">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="9297d-189">DataContractResolver</span></span>](../wcf/samples/datacontractresolver.md)

  - [<span data-ttu-id="9297d-190">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="9297d-190">KnownAssemblyAttribute</span></span>](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a><span data-ttu-id="9297d-191">データ コントラクト リゾルバーのシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-191">Data Contract Resolver Scenarios</span></span>

- <span data-ttu-id="9297d-192">数十の <xref:System.Runtime.Serialization.KnownTypeAttribute> オブジェクトをサービスで宣言する必要性の回避。</span><span class="sxs-lookup"><span data-stu-id="9297d-192">Avoiding having to declare tens of <xref:System.Runtime.Serialization.KnownTypeAttribute> objects in a service.</span></span>

- <span data-ttu-id="9297d-193">XML BLOB のサイズの削減。</span><span class="sxs-lookup"><span data-stu-id="9297d-193">Reducing the size of the XML blob.</span></span>

## <a name="flowchart"></a><span data-ttu-id="9297d-194">フローチャート</span><span class="sxs-lookup"><span data-stu-id="9297d-194">Flowchart</span></span>

<span data-ttu-id="9297d-195">フローチャートは、ドメインの問題を視覚的に表すための既知のパラダイムです。</span><span class="sxs-lookup"><span data-stu-id="9297d-195">Flowchart is a well-known paradigm to visually represent domain problems.</span></span> <span data-ttu-id="9297d-196">これは .NET Framework 4 で導入される新しい制御フロー スタイルです。</span><span class="sxs-lookup"><span data-stu-id="9297d-196">It is a new control flow style we're introducing in .NET Framework 4.</span></span> <span data-ttu-id="9297d-197">フローチャートの主な特性は、一度に 1 つのアクティビティのみ実行されることです。</span><span class="sxs-lookup"><span data-stu-id="9297d-197">A core characteristic of Flowchart is that only one activity is executed at any given time.</span></span> <span data-ttu-id="9297d-198">フローチャートはループと代替結果を表すことができますが、その性質上、複数ノードの同時実行を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="9297d-198">Flowcharts can express loops and alternative outcomes, but cannot natively express concurrent execution of multiple nodes.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-199">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-199">Getting Started</span></span>

- <span data-ttu-id="9297d-200">Visual Studio 2012 内で、ワークフロー コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-200">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="9297d-201">ワークフロー デザイナーにフローチャートを追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-201">Add a Flowchart in the workflow designer.</span></span>

- <span data-ttu-id="9297d-202">フローチャート機能では、次のクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="9297d-202">The flowchart feature uses the following classes:</span></span>

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- <span data-ttu-id="9297d-203">サンプル:</span><span class="sxs-lookup"><span data-stu-id="9297d-203">Samples:</span></span>

  - [<span data-ttu-id="9297d-204">TryCatch を使用した Flowchart アクティビティでのエラー処理</span><span class="sxs-lookup"><span data-stu-id="9297d-204">Fault Handling in a Flowchart Activity Using TryCatch</span></span>](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [<span data-ttu-id="9297d-205">雇用プロセス</span><span class="sxs-lookup"><span data-stu-id="9297d-205">Hiring Process</span></span>](./samples/hiring-process.md)

- <span data-ttu-id="9297d-206">デザイナー ドキュメント:</span><span class="sxs-lookup"><span data-stu-id="9297d-206">Designer Documentation:</span></span>

  - [<span data-ttu-id="9297d-207">フローチャート アクティビティ デザイナー</span><span class="sxs-lookup"><span data-stu-id="9297d-207">Flowchart Activity Designers</span></span>](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a><span data-ttu-id="9297d-208">フローチャートのシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-208">Flowchart Scenarios</span></span>

<span data-ttu-id="9297d-209">フローチャート アクティビティを使用して推測ゲームを実装できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-209">A flowchart activity can be used to implement a guessing game.</span></span> <span data-ttu-id="9297d-210">推測ゲームは非常に単純です。コンピューターによってランダムな数値が選択され、プレーヤーはその数値を推測する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-210">The guessing game is very simple: the computer selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="9297d-211">プレーヤーが推測を送信すると、コンピューターにヒント ("もっと小さい数字を試してください" など) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-211">When the player submits each guess, the computer shows them a hint (i.e. "try a lower number").</span></span> <span data-ttu-id="9297d-212">プレーヤーが 6 回以下で数値を見つけた場合は、特別な祝福のメッセージがコンピューターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-212">If the player finds the number in less than 7 attempts, they receive a special congratulation from the computer.</span></span> <span data-ttu-id="9297d-213">このゲームは、次の手続き型アクティビティの組み合わせで実装できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-213">This game can be implemented with a combination of the following procedural activities:</span></span>

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a><span data-ttu-id="9297d-214">手続き型アクティビティ (Sequence、If、ForEach、Switch、Assign、DoWhile、While)</span><span class="sxs-lookup"><span data-stu-id="9297d-214">Procedural activities (Sequence, If, ForEach, Switch, Assign, DoWhile, While)</span></span>

<span data-ttu-id="9297d-215">手続き型アクティビティは、プログラマになじみのある概念を使用してシーケンシャル制御フローをモデル化するメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="9297d-215">Procedural activities provide a mechanism to model sequential control flow using concepts that are familiar to programmers.</span></span> <span data-ttu-id="9297d-216">これらのアクティビティにより、従来の構造型プログラミング言語の構成要素が有効になり、該当する場合には C# や Visual Basic などの一般的な手続き型言語と同等の言語が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-216">These activities enable traditionally structured programming language constructs and, when appropriate, provide language parity with common procedural languages such as C# and Visual Basic.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-217">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-217">Getting Started</span></span>

- <span data-ttu-id="9297d-218">Visual Studio 2012 内で、ワークフロー コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-218">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="9297d-219">ワークフロー デザイナーで、手続き型アクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-219">Add procedural activities in the workflow designer.</span></span>

- <span data-ttu-id="9297d-220">サンプル:</span><span class="sxs-lookup"><span data-stu-id="9297d-220">Samples:</span></span>

  - [<span data-ttu-id="9297d-221">雇用プロセス</span><span class="sxs-lookup"><span data-stu-id="9297d-221">Hiring Process</span></span>](./samples/hiring-process.md)

  - [<span data-ttu-id="9297d-222">企業の購買プロセス</span><span class="sxs-lookup"><span data-stu-id="9297d-222">Corporate Purchase Process</span></span>](./samples/corporate-purchase-process.md)

- <span data-ttu-id="9297d-223">デザイナー ドキュメント:</span><span class="sxs-lookup"><span data-stu-id="9297d-223">Designer Documentation:</span></span>

  - [<span data-ttu-id="9297d-224">Parallel アクティビティ デザイナー</span><span class="sxs-lookup"><span data-stu-id="9297d-224">Parallel Activity Designer</span></span>](/visualstudio/workflow-designer/parallel-activity-designer)

  - [<span data-ttu-id="9297d-225">ParallelForEach\<T> アクティビティ デザイナーの使用</span><span class="sxs-lookup"><span data-stu-id="9297d-225">ParallelForEach\<T> Activity Designer</span></span>](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a><span data-ttu-id="9297d-226">手続き型アクティビティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-226">Procedural Activity Scenarios</span></span>

- <span data-ttu-id="9297d-227"><xref:System.Activities.Statements.Parallel>: イントラネット ドキュメント管理システムにドキュメント承認ワークフローがあります。</span><span class="sxs-lookup"><span data-stu-id="9297d-227"><xref:System.Activities.Statements.Parallel>: An intranet document management system has a document approval workflow.</span></span> <span data-ttu-id="9297d-228">ドキュメントは、イントラネットに公開する前に、複数の部門の担当者によって承認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-228">Documents need to be approved by people in several departments before they can be published to the intranet.</span></span> <span data-ttu-id="9297d-229">設定されている承認順序はありません。ドキュメントが "承認保留" フェーズにあるときにいつでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9297d-229">There isn't an established order for the approvals; they can occur at any time while the document is in the "approval pending" phase.</span></span> <span data-ttu-id="9297d-230">ユーザーがレビューのためにドキュメントを送信した場合は、直属のマネージャー、イントラネット管理者、および内部コミュニケーション マネージャーがそれを承認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-230">When a user submits a document for review, it must be approved by their direct manager, the intranet administrator, and the internal communications manager.</span></span>

- <span data-ttu-id="9297d-231"><xref:System.Activities.Statements.ParallelForEach%601>: WF アプリケーションは、大規模企業内での企業購買を管理します。</span><span class="sxs-lookup"><span data-stu-id="9297d-231"><xref:System.Activities.Statements.ParallelForEach%601>: A WF application manages corporate buys within a large company.</span></span> <span data-ttu-id="9297d-232">企業の規則では、購買作業を計画する前に 3 社の異なるベンダーを評価する必要があると規定されています。</span><span class="sxs-lookup"><span data-stu-id="9297d-232">The corporate rules dictate that before planning any purchase operation, the valuations of three different vendors is required.</span></span> <span data-ttu-id="9297d-233">購買部門の従業員は、企業のベンダー リストから 3 社のベンダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="9297d-233">An employee from the buying department selects three vendors from the company's vendor list.</span></span> <span data-ttu-id="9297d-234">これらのベンダーを選択し、通知した後で、企業は経済提案書を待ちます。</span><span class="sxs-lookup"><span data-stu-id="9297d-234">After these vendors have been selected and notified, the company will wait for their economic proposals.</span></span> <span data-ttu-id="9297d-235">提案書は任意の順序で到着します。</span><span class="sxs-lookup"><span data-stu-id="9297d-235">The proposals can come in any order.</span></span> <span data-ttu-id="9297d-236">WF でこのシナリオを実装するには、ベンダーのコレクションを反復処理して経済提案書を求める <xref:System.Activities.Statements.ParallelForEach%601> を使用します。</span><span class="sxs-lookup"><span data-stu-id="9297d-236">To implement this scenario in WF, we use a <xref:System.Activities.Statements.ParallelForEach%601> that will iterate through our collection of vendors and ask for their economic proposals.</span></span> <span data-ttu-id="9297d-237">すべての提案が収集された後で、最良の提案が選択されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-237">After all offers are gathered, the best one is selected and displayed.</span></span>

## <a name="invokemethod"></a><span data-ttu-id="9297d-238">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9297d-238">InvokeMethod</span></span>

<span data-ttu-id="9297d-239"><xref:System.Activities.Statements.InvokeMethod> アクティビティでは、オブジェクト内のパブリック メソッドまたはスコープ内の型を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9297d-239">The <xref:System.Activities.Statements.InvokeMethod> activity allows invoking public methods in objects or types in scope.</span></span> <span data-ttu-id="9297d-240">パラメーター付きまたはパラメーターなし (パラメーター配列を含む) でのインスタンス メソッドおよび静的メソッドの呼び出し、および汎用メソッドの呼び出しがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9297d-240">It supports invoking instance and static methods with or without parameters (including parameter arrays), and generic methods.</span></span> <span data-ttu-id="9297d-241">メソッドを同期および非同期で実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="9297d-241">It also allows executing method synchronously and asynchronously.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-242">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-242">Getting Started</span></span>

- <span data-ttu-id="9297d-243">Visual Studio 2012 内で、ワークフロー コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-243">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="9297d-244">ワークフロー デザイナーに <xref:System.Activities.Statements.InvokeMethod> アクティビティを追加し、そこに静的メソッドとインスタンス メソッドを構成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-244">Add an <xref:System.Activities.Statements.InvokeMethod> activity in the workflow designer, and configure static and instance methods on it.</span></span>

- <span data-ttu-id="9297d-245">デザイナー ドキュメント: [InvokeMethod アクティビティ デザイナー](/visualstudio/workflow-designer/invokemethod-activity-designer)</span><span class="sxs-lookup"><span data-stu-id="9297d-245">Designer Documentation: [InvokeMethod Activity Designer](/visualstudio/workflow-designer/invokemethod-activity-designer)</span></span>

### <a name="invokemethod-scenarios"></a><span data-ttu-id="9297d-246">InvokeMethod のシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-246">InvokeMethod Scenarios</span></span>

- <span data-ttu-id="9297d-247">スコープ内のオブジェクトのメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-247">A method in an object in scope needs to be invoked.</span></span> <span data-ttu-id="9297d-248">たとえば、辞書に値を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-248">For example, a value needs to be added to a dictionary.</span></span> <span data-ttu-id="9297d-249">辞書のインスタンスの Add メソッドが呼び出され、キーと値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-249">The Add method of the instance of the dictionary is invoked, and the key and value are provided.</span></span>

- <span data-ttu-id="9297d-250">レガシー CLR オブジェクトに対してメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-250">A method needs to be invoked on a legacy CLR object.</span></span> <span data-ttu-id="9297d-251">カスタム アクティビティを作成してそのレガシー クラスの呼び出しをラップする代わりに、ワークフロー実行中にそのクラスがスコープ内にある場合には <xref:System.Activities.Statements.InvokeMethod> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-251">Instead of creating a custom activity to wrap the call to that legacy class, if it is in scope during the workflow execution, <xref:System.Activities.Statements.InvokeMethod> can be used.</span></span>

## <a name="error-handling-activities"></a><span data-ttu-id="9297d-252">エラー処理アクティビティ</span><span class="sxs-lookup"><span data-stu-id="9297d-252">Error handling activities</span></span>

<span data-ttu-id="9297d-253"><xref:System.Activities.Statements.TryCatch> アクティビティには、含まれるアクティビティのセットの実行中に発生する例外をキャッチするメカニズムが用意されています (C# や Visual Basic の Try/Catch コンストラクトに類似)。</span><span class="sxs-lookup"><span data-stu-id="9297d-253">The <xref:System.Activities.Statements.TryCatch> activity provides a mechanism for catching exceptions that occur during the execution of a set of contained activities (similar to the Try/Catch construct in C# and Visual Basic).</span></span> <span data-ttu-id="9297d-254"><xref:System.Activities.Statements.TryCatch> はワークフロー レベルの例外処理を提供します。</span><span class="sxs-lookup"><span data-stu-id="9297d-254"><xref:System.Activities.Statements.TryCatch> provides exception handling at the workflow level.</span></span> <span data-ttu-id="9297d-255">ハンドルされない例外がスローされると、ワークフローが中止され、Finally ブロックは実行されません。</span><span class="sxs-lookup"><span data-stu-id="9297d-255">When an unhandled exception is thrown, the workflow is aborted and the Finally block won't be executed.</span></span> <span data-ttu-id="9297d-256">この動作は C# と一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-256">This behavior is consistent with C#.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-257">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-257">Getting Started</span></span>

- <span data-ttu-id="9297d-258">Visual Studio 2012 内で、ワークフロー コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-258">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="9297d-259">ワークフロー デザイナーで <xref:System.Activities.Statements.TryCatch> アクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-259">Add a <xref:System.Activities.Statements.TryCatch> activity in the workflow designer.</span></span>

- <span data-ttu-id="9297d-260">サンプル: [TryCatch を使用した Flowchart アクティビティでのエラー処理](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-260">Sample: [Fault Handling in a Flowchart Activity Using TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)</span></span>

- <span data-ttu-id="9297d-261">デザイナー ドキュメント: [エラー処理アクティビティ デザイナー](/visualstudio/workflow-designer/error-handling-activity-designers)</span><span class="sxs-lookup"><span data-stu-id="9297d-261">Designer Documentation: [Error Handling Activity Designers](/visualstudio/workflow-designer/error-handling-activity-designers)</span></span>

### <a name="error-handling-scenarios"></a><span data-ttu-id="9297d-262">エラー処理のシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-262">Error handling scenarios</span></span>

<span data-ttu-id="9297d-263">アクティビティのセットを実行する必要があり、エラーの発生時に特定のロジックを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-263">A set of activities needs to be executed, and specific logic needs to be executed when an error occurs.</span></span> <span data-ttu-id="9297d-264">そのエラー処理ロジック中にエラーが回復不能であることがわかった場合は、例外が再スローされ、親アクティビティ (またはホスト) によって問題が処理されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-264">If during that error handling logic it is found that the error is not recoverable, the exception will be rethrown, and the parent activity (or the host) will deal with the problem.</span></span>

## <a name="pick-activity"></a><span data-ttu-id="9297d-265">Pick アクティビティ</span><span class="sxs-lookup"><span data-stu-id="9297d-265">Pick activity</span></span>

<span data-ttu-id="9297d-266"><xref:System.Activities.Statements.Pick> アクティビティは、WF でイベント ベースの制御フロー モデリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="9297d-266">The <xref:System.Activities.Statements.Pick> Activity provides event-based control flow modeling in WF.</span></span> <span data-ttu-id="9297d-267"><xref:System.Activities.Statements.Pick> には、多数の分岐が含まれています。各分岐は、特定のイベントが発生すると実行されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-267"><xref:System.Activities.Statements.Pick> contains many branches where each branch waits for a particular event to occur before running.</span></span> <span data-ttu-id="9297d-268">この設定では、<xref:System.Activities.Statements.Pick> は、アクティビティがリッスンしているイベント セットの 1 つのみを実行する <xref:System.Activities.Statements.Switch%601> と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="9297d-268">In this setup, a <xref:System.Activities.Statements.Pick> behaves similar to a <xref:System.Activities.Statements.Switch%601> to which the Activity will execute only one of the set of events it is listening.</span></span> <span data-ttu-id="9297d-269">各分岐はイベント ドリブンなので、発生したイベントが対応する分岐を実行します。</span><span class="sxs-lookup"><span data-stu-id="9297d-269">Each branch is event driven and the event that occurs runs the corresponding branch first.</span></span> <span data-ttu-id="9297d-270">他のすべての分岐は、イベントのリッスンをキャンセルし、停止します。</span><span class="sxs-lookup"><span data-stu-id="9297d-270">All other branches cancel and stop listening for events.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-271">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-271">Getting Started</span></span>

- <span data-ttu-id="9297d-272">Visual Studio 2012 内で、ワークフロー コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-272">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="9297d-273">ワークフロー デザイナーで <xref:System.Activities.Statements.Pick> アクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-273">Add a <xref:System.Activities.Statements.Pick> activity in the workflow designer.</span></span>

- <span data-ttu-id="9297d-274">サンプル: [Pick アクティビティの使用](./samples/using-the-pick-activity.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-274">Sample: [Using the Pick Activity](./samples/using-the-pick-activity.md)</span></span>

- <span data-ttu-id="9297d-275">デザイナー ドキュメント: [Pick アクティビティ デザイナー](/visualstudio/workflow-designer/pick-activity-designer)</span><span class="sxs-lookup"><span data-stu-id="9297d-275">Designer documentation: [Pick Activity Designer](/visualstudio/workflow-designer/pick-activity-designer)</span></span>

### <a name="pick-scenario"></a><span data-ttu-id="9297d-276">Pick のシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-276">Pick Scenario</span></span>

<span data-ttu-id="9297d-277">ユーザーに入力を求めるプロンプトを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-277">A user needs to be prompted for input.</span></span> <span data-ttu-id="9297d-278">通常の状況下では、開発者は <xref:System.Console.ReadLine%2A> のようなメソッド呼び出しを使用してユーザーの入力を求めます。</span><span class="sxs-lookup"><span data-stu-id="9297d-278">Under normal circumstances, the developer would use a method call like <xref:System.Console.ReadLine%2A> to prompt for a user's input.</span></span> <span data-ttu-id="9297d-279">この設定の問題は、ユーザーが何か入力するまでプログラムが待機することです。</span><span class="sxs-lookup"><span data-stu-id="9297d-279">The problem with this setup is that the program waits until the user enters something.</span></span> <span data-ttu-id="9297d-280">このシナリオでは、ブロッキング アクティビティのブロックを解除するためにタイムアウトが必要です。</span><span class="sxs-lookup"><span data-stu-id="9297d-280">In this scenario, a time-out is needed to unblock a blocking activity.</span></span> <span data-ttu-id="9297d-281">一般的なシナリオでは、特定の期間内にタスクが完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-281">A common scenario is one that requires a task to be completed within a given time duration.</span></span> <span data-ttu-id="9297d-282">ブロッキング アクティビティのタイムアウトは、Pick が大量の値を追加するシナリオです。</span><span class="sxs-lookup"><span data-stu-id="9297d-282">Timing out a blocking activity is a scenario where Pick adds a lot of value.</span></span>

## <a name="wcf-routing-service"></a><span data-ttu-id="9297d-283">WCF ルーティング サービス</span><span class="sxs-lookup"><span data-stu-id="9297d-283">WCF Routing Service</span></span>

<span data-ttu-id="9297d-284">ルーティング サービスは、クライアントとサービス間で WCF メッセージがどのように流れるかを制御できる汎用ソフトウェア ルーターとなるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="9297d-284">The Routing Service is designed to be a generic software Router that allows you to control how WCF messages flow in between your clients and services.</span></span> <span data-ttu-id="9297d-285">ルーティング サービスにより、クライアントをサービスから切り離し、サポートできる構成の自由度と、サービスをホストする方法を検討するときの柔軟性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="9297d-285">The Routing Service allows you to decouple your clients from your services, which gives you much more freedom in terms of the configurations that you can support and the flexibility you have when considering how to host your services.</span></span> <span data-ttu-id="9297d-286">.NET Framework 3.5 では、クライアントとサービスが密接に結び付いていました。クライアントは、対話する必要のあるすべてのサービスについて、およびそれらが置かれている場所を知っている必要がありました。</span><span class="sxs-lookup"><span data-stu-id="9297d-286">In .NET Framework 3.5, clients and services were tightly coupled; a client had to know about all of the services it needed to talk to and where they were located.</span></span> <span data-ttu-id="9297d-287">また、.NET Framework 3.5 の WCF には次の制限がありました。</span><span class="sxs-lookup"><span data-stu-id="9297d-287">In addition, WCF in .NET Framework 3.5 had the following limitations:</span></span>

- <span data-ttu-id="9297d-288">ロジックをクライアントにハードコーディングする必要があったため、エラー処理が複雑でした。</span><span class="sxs-lookup"><span data-stu-id="9297d-288">Error handling was complex, as this logic had to be hard-coded into the client.</span></span>

- <span data-ttu-id="9297d-289">クライアントとサービスは常に同じバインディングを使用する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="9297d-289">Clients and services had to always use the same bindings.</span></span>

- <span data-ttu-id="9297d-290">サービスが適切に分類されていることはほとんどありませんでした。複数のサービス間で選択するよりも、クライアントがすべてを実装する 1 つのサービスと対話する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="9297d-290">Services were rarely well factored: it is easier to have the client talk to one service which implements everything, rather than needing to choose between multiple services.</span></span>

<span data-ttu-id="9297d-291">.NET 4 のルーティング サービスは、これらの問題を簡単に解決できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="9297d-291">The routing service in .NET 4 is designed to make these problems easier to solve.</span></span> <span data-ttu-id="9297d-292">新しいルーティング サービスには次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-292">The new routing service has the following features:</span></span>

1. <span data-ttu-id="9297d-293">コンテント ベースのルーティング (<xref:System.ServiceModel.Dispatcher.MessageFilter> オブジェクトがメッセージを調べて送信先を判断します。)</span><span class="sxs-lookup"><span data-stu-id="9297d-293">Content based routing (<xref:System.ServiceModel.Dispatcher.MessageFilter> objects examine a message to determine where it should be sent.)</span></span>

2. <span data-ttu-id="9297d-294">プロトコル ブリッジ (トランスポートとメッセージ)</span><span class="sxs-lookup"><span data-stu-id="9297d-294">Protocol bridging (transport & message)</span></span>

3. <span data-ttu-id="9297d-295">エラー処理 (ルーターは、通信例外をキャッチし、バックアップ エンドポイントにフェールオーバーします)</span><span class="sxs-lookup"><span data-stu-id="9297d-295">Error handling (the router catches communication exceptions and fails over to backup endpoints)</span></span>

4. <span data-ttu-id="9297d-296"><xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> およびルーティング構成の動的 (メモリ内) 更新。</span><span class="sxs-lookup"><span data-stu-id="9297d-296">Dynamic (in memory) update of <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> and Routing Configuration.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-297">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-297">Getting Started</span></span>

1. <span data-ttu-id="9297d-298">ドキュメント: [ルーティング](../wcf/feature-details/routing.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-298">Documentation: [Routing](../wcf/feature-details/routing.md)</span></span>

2. <span data-ttu-id="9297d-299">サンプル: [ルーティング サービス &#91;WCF サンプル&#93;](../wcf/samples/routing-services.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-299">Samples: [Routing Services &#91;WCF Samples&#93;](../wcf/samples/routing-services.md)</span></span>

3. <span data-ttu-id="9297d-300">ブログ: [ルーティング規則](/archive/blogs/RoutingRules/)</span><span class="sxs-lookup"><span data-stu-id="9297d-300">Blog: [Routing Rules!](/archive/blogs/RoutingRules/)</span></span>

### <a name="routing-scenarios"></a><span data-ttu-id="9297d-301">ルーティング シナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-301">Routing Scenarios</span></span>

<span data-ttu-id="9297d-302">ルーティング サービスは、次のシナリオに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9297d-302">The routing service is useful in the following scenarios:</span></span>

- <span data-ttu-id="9297d-303">クライアントは、複数のサービスを直接アドレス指定することなく、これらのサービスと対話できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-303">Clients can talk to multiple services without having to address them all directly.</span></span>

- <span data-ttu-id="9297d-304">クライアントは、ルーティング先を判断するためにクライアント要求で追加のロジックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-304">Clients can perform additional logic on a client request to determine where to route it</span></span>

- <span data-ttu-id="9297d-305">クライアントをリファクタリングすることなく、クライアントが実行する操作を複数のサービス実装に分解します。</span><span class="sxs-lookup"><span data-stu-id="9297d-305">Decompose the operations a client performs into multiple service implementations without refactoring the client.</span></span>

- <span data-ttu-id="9297d-306">クライアントとサービスは、異なるセキュリティ設定の異なるバインディングで会話できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-306">Clients and services can speak different bindings with different security settings.</span></span>

- <span data-ttu-id="9297d-307">クライアントは、障害またはサービスの使用不能に対してより堅牢になることができます。</span><span class="sxs-lookup"><span data-stu-id="9297d-307">Clients can be enabled to be more robust against failure or the unavailability of services.</span></span>

## <a name="wcf-discovery"></a><span data-ttu-id="9297d-308">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="9297d-308">WCF Discovery</span></span>

<span data-ttu-id="9297d-309">WCF Discovery は、アプリケーション インフラストラクチャに探索メカニズムを組み込むことのできるフレームワーク テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="9297d-309">WCF Discovery is a framework technology that allows you to incorporate a discovery mechanism to your application infrastructure.</span></span> <span data-ttu-id="9297d-310">これを使用して、サービスを探索可能にし、サービスを検索するようにクライアントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-310">You can use this to make your service discoverable, and configure your clients to search for services.</span></span> <span data-ttu-id="9297d-311">クライアントはエンドポイントでハードコーディングする必要がなくなるため、アプリケーションはより堅牢になりフォールト トレランスが向上します。</span><span class="sxs-lookup"><span data-stu-id="9297d-311">Clients no longer need to be hard coded with endpoint, making your application more robust and fault tolerant.</span></span> <span data-ttu-id="9297d-312">探索は、アプリケーションに自動構成機能をビルドするための最適なプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="9297d-312">Discovery is the perfect platform to build auto-configuration capabilities into your application.</span></span>

<span data-ttu-id="9297d-313">製品は、WS-Discovery 標準の上に構築されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-313">The product is built on top of the WS-Discovery standard.</span></span> <span data-ttu-id="9297d-314">相互運用可能、拡張可能、および汎用的になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="9297d-314">It's designed to be interoperable, extensible, and generic.</span></span> <span data-ttu-id="9297d-315">製品では 2 つの操作モードがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9297d-315">The product supports two modes of operation:</span></span>

1. <span data-ttu-id="9297d-316">マネージド: 既存のサービスに関する知識を持つエンティティがネットワーク上にあり、クライアントは情報を直接クエリします。</span><span class="sxs-lookup"><span data-stu-id="9297d-316">Managed: where there is an entity on the network knowledgeable about existing services, clients query it directly for information.</span></span> <span data-ttu-id="9297d-317">これは Active Directory に類似しています。</span><span class="sxs-lookup"><span data-stu-id="9297d-317">This is analogous to Active Directory.</span></span>

2. <span data-ttu-id="9297d-318">アドホック: クライアントはマルチキャスト メッセージを使用してサービスを特定します。</span><span class="sxs-lookup"><span data-stu-id="9297d-318">Ad-hoc: where clients use multicast messages to locate services.</span></span>

<span data-ttu-id="9297d-319">さらに、探索メッセージはネットワーク プロトコルに依存しません。モード要件をサポートする任意のプロトコル上でこれらを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-319">Furthermore, discovery messages are network protocol agnostic; you can use them on top any protocol that supports the mode requirements.</span></span> <span data-ttu-id="9297d-320">たとえば、探索マルチキャスト メッセージを UDP チャネル上またはマルチキャスト メッセージングをサポートする他の任意のネットワーク上に送信できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-320">For example, discovery multicast messages can be sent over the UDP channel or any other network that supports multicast messaging.</span></span> <span data-ttu-id="9297d-321">これらの設計ポイントが機能の柔軟性と結合されて、探索をソリューションだけに適応させることができます。</span><span class="sxs-lookup"><span data-stu-id="9297d-321">These design points, combined with feature flexibility, allow you to adapt the discovery specifically to your solution.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-322">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-322">Getting Started</span></span>

- <span data-ttu-id="9297d-323">ドキュメント: [WCF Discovery](../wcf/feature-details/wcf-discovery.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-323">Documentation: [WCF Discovery](../wcf/feature-details/wcf-discovery.md)</span></span>

- <span data-ttu-id="9297d-324">サンプル: [探索 (サンプル)](../wcf/samples/discovery-samples.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-324">Samples: [Discovery (Samples)](../wcf/samples/discovery-samples.md)</span></span>

### <a name="discovery-scenarios"></a><span data-ttu-id="9297d-325">探索のシナリオ</span><span class="sxs-lookup"><span data-stu-id="9297d-325">Discovery Scenarios</span></span>

<span data-ttu-id="9297d-326">サービスがいつ使用可能になるかが不明なため、開発者はエンドポイントのハードコーディングを望みません。</span><span class="sxs-lookup"><span data-stu-id="9297d-326">A developer doesn't want to hard code endpoints, since it is unknown when my service will be available.</span></span> <span data-ttu-id="9297d-327">代わりに、開発者は実行時にサービスを選択することを望んでいます。</span><span class="sxs-lookup"><span data-stu-id="9297d-327">Instead, the developer wants to choose a service at runtime.</span></span> <span data-ttu-id="9297d-328">アプリケーションのコンポーネント間に、切り離し、堅牢性、および自動構成がさらに必要です。</span><span class="sxs-lookup"><span data-stu-id="9297d-328">More decoupling, robustness, and auto-configuration is needed between the components in the application.</span></span>

## <a name="tracking"></a><span data-ttu-id="9297d-329">追跡</span><span class="sxs-lookup"><span data-stu-id="9297d-329">Tracking</span></span>

<span data-ttu-id="9297d-330">ワークフロー追跡では、ワークフロー インスタンスの実行を把握できます。</span><span class="sxs-lookup"><span data-stu-id="9297d-330">Workflow tracking provides insight into the execution of a workflow instance.</span></span> <span data-ttu-id="9297d-331">追跡イベントは、ワークフロー インスタンス レベルで、またワークフロー内のアクティビティの実行時にワークフローから出力されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-331">The tracking events are emitted from a workflow at the workflow instance level and when activities within the workflow execute.</span></span> <span data-ttu-id="9297d-332">追跡レコードを定期受信するにはワークフロー追跡参加要素をワークフロー ホストに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9297d-332">A workflow tracking participant needs to be added to the workflow host to subscribe to tracking records.</span></span> <span data-ttu-id="9297d-333">追跡レコードは、追跡プロファイルを使用してフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-333">The tracking records are filtered using a tracking profile.</span></span> <span data-ttu-id="9297d-334">.NET Framework には ETW (Event Tracing for Windows) 追跡参加要素が用意されており、基本プロファイルが machine.config ファイルにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9297d-334">The .NET Framework provides an ETW (Event Tracing for Windows) tracking participant, and a basic profile is installed in the machine.config file.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-335">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-335">Getting Started</span></span>

1. <span data-ttu-id="9297d-336">Visual Studio 2010 で、WCF ワークフロー サービス アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-336">In Visual Studio 2010, create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="9297d-337">開始するキャンバスに <xref:System.ServiceModel.Activities.Receive> と <xref:System.ServiceModel.Activities.SendReply> のペアが配置されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-337">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas to start.</span></span>

2. <span data-ttu-id="9297d-338">web.config を開き、プロファイルなしで ETW 追跡動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-338">Open the web.config and add an ETW tracking behavior with no profile.</span></span>

    1. <span data-ttu-id="9297d-339">既定のプロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9297d-339">The default profile is used.</span></span>

    2. <span data-ttu-id="9297d-340">イベント ビューアーを開き、 **[イベント ビューアー]** 、 **[アプリケーションとサービス ログ]** 、 **[Microsoft]** 、 **[Windows]** 、 **[アプリケーション サーバー - アプリケーション]** のノードで分析チャネルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9297d-340">Open event viewer and enable the analytic channel in the following node: **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="9297d-341">**[分析]** を右クリックし、 **[ログを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9297d-341">Right-click **Analytic** and select **Enable Log**.</span></span>

    3. <span data-ttu-id="9297d-342">ワークフロー サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="9297d-342">Run the workflow service.</span></span>

    4. <span data-ttu-id="9297d-343">イベント ビューアーでワークフロー追跡イベントを確認します。</span><span class="sxs-lookup"><span data-stu-id="9297d-343">Observe the workflow tracking events in event viewer.</span></span>

3. <span data-ttu-id="9297d-344">サンプル: [追跡](./samples/tracking.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-344">Samples: [Tracking](./samples/tracking.md)</span></span>

4. <span data-ttu-id="9297d-345">概念説明のドキュメント: [ワークフローの追跡とトレース](workflow-tracking-and-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="9297d-345">Conceptual documentation: [Workflow Tracking and Tracing](workflow-tracking-and-tracing.md)</span></span>

## <a name="sql-workflow-instance-store"></a><span data-ttu-id="9297d-346">SQL Workflow Instance Store</span><span class="sxs-lookup"><span data-stu-id="9297d-346">SQL Workflow Instance Store</span></span>

<span data-ttu-id="9297d-347"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> は、SQL Server ベースのインスタンス ストアの実装です。</span><span class="sxs-lookup"><span data-stu-id="9297d-347">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is a SQL Server-based implementation of an instance store.</span></span> <span data-ttu-id="9297d-348">インスタンス ストアは、実行中のインスタンスの状態を、そのインスタンスの読み込みと再開に必要なすべてのデータと共に格納します。</span><span class="sxs-lookup"><span data-stu-id="9297d-348">An instance store stores the state of a running instance together with all data necessary to load and resume that instance.</span></span> <span data-ttu-id="9297d-349">サービス ホストは、ワークフローが永続的な場合にインスタンス状態を保存するようインスタンス ストアに指示し、そのインスタンスのメッセージが到着するか遅延アクティビティが期限切れになったときにインスタンス状態を読み込むようインスタンス ストアに指示します。</span><span class="sxs-lookup"><span data-stu-id="9297d-349">The service host instructs the instance store to save the instance state if the workflow persists, and it instructs the instance store to load the instance state when a message arrives for that instance or a delay activity expires.</span></span>

### <a name="getting-started"></a><span data-ttu-id="9297d-350">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9297d-350">Getting Started</span></span>

1. <span data-ttu-id="9297d-351">Visual Studio 2012 内で、暗黙的または明示的な <xref:System.Activities.Statements.Persist> アクティビティを含むワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="9297d-351">In Visual Studio 2012, create a Workflow that contains an implicit or explicit <xref:System.Activities.Statements.Persist> activity.</span></span> <span data-ttu-id="9297d-352"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 動作をワークフロー サービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="9297d-352">Add the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> behavior to your workflow service host.</span></span> <span data-ttu-id="9297d-353">これはコードまたはアプリケーション構成ファイルで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9297d-353">This can be done in code or in the application configuration file.</span></span>

2. <span data-ttu-id="9297d-354">サンプル:[永続性](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="9297d-354">Samples: [Persistence](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))</span></span>

3. <span data-ttu-id="9297d-355">概念説明のドキュメント: [SQL Workflow Instance Store](sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="9297d-355">Conceptual documentation: [SQL Workflow Instance Store](sql-workflow-instance-store.md).</span></span>
