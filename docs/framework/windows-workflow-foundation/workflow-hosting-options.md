---
description: 詳細については、「ワークフローホスティングオプション」を参照してください。
title: ワークフロー ホスティングのオプション
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 64d02decd3a096b4c83555729826c5fc07b13cbf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754889"
---
# <a name="workflow-hosting-options"></a><span data-ttu-id="3ba01-103">ワークフロー ホスティングのオプション</span><span class="sxs-lookup"><span data-stu-id="3ba01-103">Workflow Hosting Options</span></span>

<span data-ttu-id="3ba01-104">ほとんどの Windows Workflow Foundation (WF) のサンプルでは、コンソールアプリケーションでホストされているワークフローを使用しますが、これは実際のワークフローにとって現実的なシナリオではありません。</span><span class="sxs-lookup"><span data-stu-id="3ba01-104">Most of the Windows Workflow Foundation (WF) samples use workflows that are hosted in a console application, but this isn't a realistic scenario for real-world workflows.</span></span> <span data-ttu-id="3ba01-105">実際のビジネスアプリケーションのワークフローは、開発者が作成した Windows サービスまたは IIS 7.0 や AppFabric などのサーバーアプリケーションのいずれかの永続的なプロセスでホストされます。</span><span class="sxs-lookup"><span data-stu-id="3ba01-105">Workflows in actual business applications will be hosted in persistent processes- either a Windows service authored by the developer, or a server application such as IIS 7.0 or AppFabric.</span></span> <span data-ttu-id="3ba01-106">これらの方法の違いを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3ba01-106">The differences between these approaches are as follows.</span></span>

## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a><span data-ttu-id="3ba01-107">Windows AppFabric を使用した IIS でのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="3ba01-107">Hosting workflows in IIS with Windows AppFabric</span></span>

<span data-ttu-id="3ba01-108">IIS と AppFabric は、ワークフローに推奨されるホストです。</span><span class="sxs-lookup"><span data-stu-id="3ba01-108">Using IIS with AppFabric is the preferred host for workflows.</span></span> <span data-ttu-id="3ba01-109">AppFabric を使用したワークフローのホスト アプリケーションは Windows プロセス アクティブ化サービスで、これは IIS を介した HTTP への依存関係のみを解消します。</span><span class="sxs-lookup"><span data-stu-id="3ba01-109">The host application for workflows using AppFabric is Windows Activation Service, which removes the dependency on HTTP over IIS alone.</span></span>

## <a name="hosting-workflows-in-iis-alone"></a><span data-ttu-id="3ba01-110">IIS のみでのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="3ba01-110">Hosting workflows in IIS alone</span></span>

<span data-ttu-id="3ba01-111">実行中のアプリケーションのメンテナンスを容易にする AppFabric で使用できる管理ツールと監視ツールがあるため、IIS 7.0 だけを使用することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="3ba01-111">Using IIS 7.0 alone is not recommended, as there are management and monitoring tools available with AppFabric that facilitate maintenance of running applications.</span></span> <span data-ttu-id="3ba01-112">AppFabric への移行に関するインフラストラクチャの問題がある場合、ワークフローは IIS 7.0 のみでホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ba01-112">Workflows should only be hosted in IIS 7.0 alone if there are infrastructure concerns with moving to AppFabric.</span></span>

> [!WARNING]
> <span data-ttu-id="3ba01-113">IIS 7.0 は、さまざまな理由でアプリケーションプールを定期的にリサイクルします。</span><span class="sxs-lookup"><span data-stu-id="3ba01-113">IIS 7.0 recycles application pools periodically for various reasons.</span></span> <span data-ttu-id="3ba01-114">アプリケーション プールがリサイクルされると、IIS は古いプールへのメッセージの受け取りを中止し、新しいアプリケーション プールをインスタンス化して新しい要求を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3ba01-114">When an application pool is recycled, IIS stops accepting messages to the old pool, and instantiates a new application pool to accept new requests.</span></span> <span data-ttu-id="3ba01-115">応答を送信した後もワークフローが動作を続ける場合、IIS 7.0 は、実行されている作業を認識しないため、ホストしているアプリケーションプールをリサイクルする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3ba01-115">If a workflow continues working after sending a response, IIS 7.0 will not be aware of the work being done, and may recycle the hosting application pool.</span></span> <span data-ttu-id="3ba01-116">これが発生すると、ワークフローが中止され、追跡サービスによって、"理由" フィールドが空の [1004-WorkflowInstanceAborted](1004-workflowinstanceaborted.md) メッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="3ba01-116">If this happens, the workflow will abort, and tracking services will record a [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md) message with an empty Reason field.</span></span>
>
> <span data-ttu-id="3ba01-117">永続化を使用する場合、ホストは、最後の永続性ポイントから、中止されたインスタンスを明示的に再開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ba01-117">If persistence is used, the host must explicitly restart aborted instances from the last persistence point.</span></span>
>
> <span data-ttu-id="3ba01-118">AppFabric を使用する場合、永続化を使用すると、ワークフロー管理サービスは、最終的に、最後に成功した永続性ポイントからワークフローを再開します。</span><span class="sxs-lookup"><span data-stu-id="3ba01-118">If AppFabric is used, the workflow management service will eventually resume the workflow from the last successful persistence point if persistence is used.</span></span> <span data-ttu-id="3ba01-119">永続化を使用せず、ワークフローが要求/応答パターン以外の操作を実行している場合、ワークフローが中止されるとデータは失われます。</span><span class="sxs-lookup"><span data-stu-id="3ba01-119">If no persistence is used, and the workflow performs operations outside a Request/Response pattern, data will be lost when the workflow aborts.</span></span>

## <a name="hosting-a-workflow-in-a-custom-windows-service"></a><span data-ttu-id="3ba01-120">カスタム Windows サービスでのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="3ba01-120">Hosting a workflow in a custom Windows Service</span></span>

<span data-ttu-id="3ba01-121">カスタム ワークフロー サービスを作成してワークフローをホストする場合、開発者は AppFabric に標準搭載されている多くの機能を複製する必要がありますが、カスタム機能をより柔軟に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3ba01-121">Creating a custom workflow service to host the workflow will require the developer to duplicate a lot of the functionality provided out-of-box by AppFabric, but will allow for more flexibility with custom functionality.</span></span> <span data-ttu-id="3ba01-122">このオプションは、AppFabric を選択できない場合にのみ検討してください。</span><span class="sxs-lookup"><span data-stu-id="3ba01-122">This option should only be considered if AppFabric proves to not be an option.</span></span>
