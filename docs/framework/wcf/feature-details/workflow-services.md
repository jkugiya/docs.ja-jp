---
description: 詳細については、「ワークフローサービス」を参照してください。
title: ワークフロー サービス
ms.date: 03/30/2017
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
ms.openlocfilehash: 195ecf0322146a8735362dfbb82dc19bf1c04312
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704473"
---
# <a name="workflow-services"></a><span data-ttu-id="0a0d4-103">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="0a0d4-103">Workflow Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="0a0d4-104">では、ワークフロー ベースのサービスを XAML で宣言によって記述できます。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-104">allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="0a0d4-105">サービスを実装するワークフローの定義、およびサービスが公開するエンドポイントの説明を、すべて XAML で実行できます。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-105">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="0a0d4-106">このセクションの各トピックでは、宣言によるサービスの記述をサポートするプログラミング モデルについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-106">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a0d4-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0a0d4-107">In This Section</span></span>  

 [<span data-ttu-id="0a0d4-108">ワークフロー サービスの概要</span><span class="sxs-lookup"><span data-stu-id="0a0d4-108">Workflow Services Overview</span></span>](workflow-services-overview.md)  
 <span data-ttu-id="0a0d4-109">ワークフロー サービスの作成およびホストに関与するコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-109">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="0a0d4-110">メッセージング アクティビティ</span><span class="sxs-lookup"><span data-stu-id="0a0d4-110">Messaging Activities</span></span>](messaging-activities.md)  
 <span data-ttu-id="0a0d4-111">ワークフローがメッセージを送受信できるようにするアクティビティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-111">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="0a0d4-112">方法: メッセージング アクティビティを使用してワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="0a0d4-112">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="0a0d4-113">メッセージング アクティビティを使用してワークフロー サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-113">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="0a0d4-114">方法: ワークフロー アプリケーションからサービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="0a0d4-114">How To: Access a Service From a Workflow Application</span></span>](how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="0a0d4-115">ワークフロー アプリケーションからサービスを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-115">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="0a0d4-116">相関関係</span><span class="sxs-lookup"><span data-stu-id="0a0d4-116">Correlation</span></span>](correlation.md)  
 <span data-ttu-id="0a0d4-117">相関関係によってメッセージを相互に、またはインスタンスにマップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-117">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="0a0d4-118">順番を無視したメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="0a0d4-118">Out-of-Order Message Processing</span></span>](out-of-order-message-processing.md)  
 <span data-ttu-id="0a0d4-119">順番を無視したメッセージを受け入れるようにサービスを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-119">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="0a0d4-120">コントラクト優先ワークフロー サービスの開発</span><span class="sxs-lookup"><span data-stu-id="0a0d4-120">Contract First Workflow Service Development</span></span>](../../windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="0a0d4-121">既存のサービス コントラクトに基づいてワークフロー サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-121">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="0a0d4-122">方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="0a0d4-122">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="0a0d4-123">既存のサービス コントラクトを使用してワークフロー サービスを作成する例を操作手順に従って説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-123">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="0a0d4-124">ワークフロー サービスのホストの概要</span><span class="sxs-lookup"><span data-stu-id="0a0d4-124">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)  
 <span data-ttu-id="0a0d4-125">ワークフロー サービスのホストのさまざまな側面について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-125">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="0a0d4-126">ワークフロー内でのコントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="0a0d4-126">Using Contracts in Workflow</span></span>](using-contracts-in-workflow.md)  
 <span data-ttu-id="0a0d4-127">コントラクトおよびコントラクト推論のさまざまな種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a0d4-127">Describes the different types of contracts and contract inference.</span></span>
