---
description: 永続化されていないワークフローインスタンスについての詳細情報
title: 非永続化ワークフロー インスタンス
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 0ee5968426a6bb800b9e70ac592c6da191c22511
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787904"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="e97ac-103">非永続化ワークフロー インスタンス</span><span class="sxs-lookup"><span data-stu-id="e97ac-103">Non-Persisted Workflow Instances</span></span>

<span data-ttu-id="e97ac-104">状態が永続するワークフローの新しいインスタンスを <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> に作成すると、サービス ホストはそのサービスのエントリをインスタンス ストアに作成します。</span><span class="sxs-lookup"><span data-stu-id="e97ac-104">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="e97ac-105">その後、ワークフロー インスタンスが初めて永続化されると、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> は現在のインスタンス状態を格納します。</span><span class="sxs-lookup"><span data-stu-id="e97ac-105">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="e97ac-106">ワークフローが Windows プロセス アクティブ化サービスにホストされている場合は、インスタンスが初めて永続化するとサービス配置データもインスタンス ストアに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e97ac-106">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>

<span data-ttu-id="e97ac-107">ワークフローインスタンスが永続化されていない限り、 **永続化** されていない状態になります。</span><span class="sxs-lookup"><span data-stu-id="e97ac-107">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="e97ac-108">この状態の場合、アプリケーション ドメインのリサイクル、ホストの障害、またはコンピューターの障害の後にワークフロー インスタンスを回復することはできません。</span><span class="sxs-lookup"><span data-stu-id="e97ac-108">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>

## <a name="the-non-persisted-state"></a><span data-ttu-id="e97ac-109">非永続化状態</span><span class="sxs-lookup"><span data-stu-id="e97ac-109">The Non-Persisted State</span></span>

<span data-ttu-id="e97ac-110">次のような場合、まだ永続化されていない永続性ワークフロー インスタンスが非永続的状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="e97ac-110">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>

- <span data-ttu-id="e97ac-111">ワークフロー インスタンスが初めて永続化される前にサービス ホストがクラッシュした場合。</span><span class="sxs-lookup"><span data-stu-id="e97ac-111">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="e97ac-112">ワークフロー インスタンスはインスタンス ストアに残り、回復されません。</span><span class="sxs-lookup"><span data-stu-id="e97ac-112">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="e97ac-113">関連付けられるメッセージが受信されると、ワークフロー インスタンスが再びアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="e97ac-113">If a correlated message arrives, the workflow instance becomes active again.</span></span>

- <span data-ttu-id="e97ac-114">ワークフロー インスタンスが初めて永続化される前にインスタンスで例外が発生した場合。</span><span class="sxs-lookup"><span data-stu-id="e97ac-114">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="e97ac-115">返される <xref:System.Activities.UnhandledExceptionAction> に応じて、次のシナリオが発生します。</span><span class="sxs-lookup"><span data-stu-id="e97ac-115">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>

  - <span data-ttu-id="e97ac-116"><xref:System.Activities.UnhandledExceptionAction> が <xref:System.Activities.UnhandledExceptionAction.Abort> に設定されている場合:  例外が発生すると、サービス配置情報がインスタンス ストアに書き込まれ、ワークフロー インスタンスがメモリからアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="e97ac-116"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="e97ac-117">ワークフロー インスタンスは非永続化状態となり、再読み込みできません。</span><span class="sxs-lookup"><span data-stu-id="e97ac-117">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>

  - <span data-ttu-id="e97ac-118"><xref:System.Activities.UnhandledExceptionAction> が <xref:System.Activities.UnhandledExceptionAction.Cancel> または <xref:System.Activities.UnhandledExceptionAction.Terminate> に設定されている場合:  例外が発生すると、サービス配置情報がインスタンス ストアに書き込まれ、アクティビティ インスタンスの状態が <xref:System.Activities.ActivityInstanceState.Closed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e97ac-118"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>

<span data-ttu-id="e97ac-119">アンロードされている非永続化ワークフロー インスタンスが発生するリスクを最低限に抑えるため、ライフサイクルの早い段階でワークフローを永続化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e97ac-119">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>

## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="e97ac-120">非永続化インスタンスの検出と削除</span><span class="sxs-lookup"><span data-stu-id="e97ac-120">Detection and Removal of Non-Persisted Instances</span></span>

<span data-ttu-id="e97ac-121"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> は非永続化ワークフロー インスタンスをインスタンス ストアから削除しません。</span><span class="sxs-lookup"><span data-stu-id="e97ac-121">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="e97ac-122">非永続化ワークフロー インスタンスが関連付けられている期限切れのロックの所有者も削除されません。</span><span class="sxs-lookup"><span data-stu-id="e97ac-122">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>

<span data-ttu-id="e97ac-123">管理者は定期的にインスタンス ストアの非永続化インスタンスを調べることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e97ac-123">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="e97ac-124">管理者はこのワークフローが相関メッセージを受信しないことがわかっている限り、これらのインスタンスをインスタンス ストアから削除することができます。</span><span class="sxs-lookup"><span data-stu-id="e97ac-124">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="e97ac-125">たとえば、数か月にわたってデータベースに残っているインスタンスがある場合、そのワークフローの通常の有効期間が数日程度なら、クラッシュした初期化済みのインスタンスと見なしても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="e97ac-125">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>

<span data-ttu-id="e97ac-126">SQL Workflow Instance Store 内の非永続化インスタンスを見つけるには、次の SQL クエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e97ac-126">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>

- <span data-ttu-id="e97ac-127">このクエリは、まだ永続化されていないすべてのインスタンスを検索し、その ID と作成時刻 (UTC 時刻で格納) を返します。</span><span class="sxs-lookup"><span data-stu-id="e97ac-127">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- <span data-ttu-id="e97ac-128">このクエリは、まだ永続化されておらず、読み込まれてもいないすべてのインスタンスを検索し、その ID と作成時刻 (UTC 時刻で格納) を返します。</span><span class="sxs-lookup"><span data-stu-id="e97ac-128">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- <span data-ttu-id="e97ac-129">このクエリは、まだ永続化されていない中断されたすべてのインスタンスを検索し、その ID、作成時刻 (UTC 時刻で格納)、中断の理由、およびその例外名を返します。</span><span class="sxs-lookup"><span data-stu-id="e97ac-129">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

<span data-ttu-id="e97ac-130">非永続化インスタンスを削除する際は注意してください。</span><span class="sxs-lookup"><span data-stu-id="e97ac-130">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="e97ac-131">一般に、<xref:System.ServiceModel.Activities.WorkflowServiceHost> によって作成された非永続化インスタンスは、中断されている場合や読み込まれていない場合は安全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="e97ac-131">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="e97ac-132">これらの特定のインスタンスは、次の SQL コマンドを正しいインスタンス ID に置き換えて使用し、`[System.Activities.DurableInstancing].[Instances]` ビューから削除することで、ストアから削除することが可能です。</span><span class="sxs-lookup"><span data-stu-id="e97ac-132">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> <span data-ttu-id="e97ac-133">作成されたばかりでまだ永続化されていないインスタンスもあるため、非永続的インスタンスをすべて削除することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="e97ac-133">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
