---
description: '詳細については、「方法: 非永続化インスタンスを照会する」を参照してください。'
title: '方法: 非永続的インスタンスを検索する'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 2cef64f97b32c5f1d31fa078200bc2fe15179485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777659"
---
# <a name="how-to-query-for-non-persisted-instances"></a><span data-ttu-id="d5115-103">方法: 非永続的インスタンスを検索する</span><span class="sxs-lookup"><span data-stu-id="d5115-103">How to: Query for Non-persisted Instances</span></span>

<span data-ttu-id="d5115-104">サービスに SQL Workflow Instance Store の動作が定義されている場合、サービスの新しいインスタンスが作成されると、サービス ホストにより、そのサービス インスタンスの初期エントリがインスタンス ストアに作成されます。</span><span class="sxs-lookup"><span data-stu-id="d5115-104">When a new instance of a service is created and the service has the SQL Workflow Instance Store behavior defined, the service host creates a initial entry for that service instance in the instance store.</span></span> <span data-ttu-id="d5115-105">その後、そのサービス インスタンスが初めて永続化されると、SQL Workflow Instance Store の動作により、現在のインスタンスの状態が、アクティベーション、回復、および制御に必要な追加データと共に格納されます。</span><span class="sxs-lookup"><span data-stu-id="d5115-105">Subsequently when the service instance persists for the first time, the SQL Workflow Instance Store behavior stores the current instance state together with additional data that is required for activation, recovery, and control.</span></span>

<span data-ttu-id="d5115-106">インスタンスの初期エントリが作成された後にインスタンスが永続化されていない場合、そのサービス インスタンスの状態を非永続的状態と呼びます。</span><span class="sxs-lookup"><span data-stu-id="d5115-106">If an instance is not persisted after the initial entry for the instance is created, the service instance is said to be in the non-persisted state.</span></span> <span data-ttu-id="d5115-107">永続的サービス インスタンスはすべてクエリおよび制御できますが、</span><span class="sxs-lookup"><span data-stu-id="d5115-107">All the persisted service instances can be queried and controlled.</span></span> <span data-ttu-id="d5115-108">非永続的サービス インスタンスはクエリも制御もできません。</span><span class="sxs-lookup"><span data-stu-id="d5115-108">Non-persisted service instances can neither be queried nor controlled.</span></span> <span data-ttu-id="d5115-109">非永続的インスタンスが未処理の例外によって中断された場合は、クエリはできますが制御はできません。</span><span class="sxs-lookup"><span data-stu-id="d5115-109">If a non-persisted instance is suspended due to an unhandled exception it can be queried but not controlled.</span></span>

<span data-ttu-id="d5115-110">次のような場合、まだ永続化されていない永続性サービス インスタンスが非永続的状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="d5115-110">Durable service instances that are not yet persisted remain in a non-persisted state in the following scenarios:</span></span>

- <span data-ttu-id="d5115-111">インスタンスが初めて永続化される前にサービス ホストがクラッシュした場合。</span><span class="sxs-lookup"><span data-stu-id="d5115-111">The service host crashes before the instance persisted for the first time.</span></span> <span data-ttu-id="d5115-112">インスタンスの初期エントリがインスタンス ストアに残ります。</span><span class="sxs-lookup"><span data-stu-id="d5115-112">The initial entry for the instance remains in the instance store.</span></span> <span data-ttu-id="d5115-113">インスタンスを回復することはできません。</span><span class="sxs-lookup"><span data-stu-id="d5115-113">The instance is not recoverable.</span></span> <span data-ttu-id="d5115-114">関連付けられるメッセージが受信されると、インスタンスが再びアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="d5115-114">If a correlated message arrives, the instance becomes active again.</span></span>

- <span data-ttu-id="d5115-115">インスタンスが初めて永続化される前にインスタンスで未処理の例外が発生した場合。</span><span class="sxs-lookup"><span data-stu-id="d5115-115">The instance experiences an unhandled exception before it persisted for the first time.</span></span> <span data-ttu-id="d5115-116">次の状況が発生します。</span><span class="sxs-lookup"><span data-stu-id="d5115-116">The following scenarios arise</span></span>

  - <span data-ttu-id="d5115-117">**Unhandledexceptionaction** プロパティの値が "**破棄**" に設定されている場合は、サービスの配置情報がインスタンスストアに書き込まれ、インスタンスがメモリからアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="d5115-117">If the value of the **UnhandledExceptionAction** property is set to **Abandon**, the service deployment information is written to the instance store and the instance is unloaded from memory.</span></span> <span data-ttu-id="d5115-118">インスタンスは、非永続的状態のまま永続性データベースに残ります。</span><span class="sxs-lookup"><span data-stu-id="d5115-118">The instance remains in non-persisted state in the persistence database.</span></span>

  - <span data-ttu-id="d5115-119">**Unhandledexceptionaction** プロパティの値が **AbandonAndSuspend** に設定されている場合、サービスの配置情報は永続性データベースに書き込まれ、インスタンスの状態は "**中断**" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d5115-119">If the value of the **UnhandledExceptionAction** property is set to **AbandonAndSuspend**, the service deployment information is written to the persistence database and the instance state is set to **Suspended**.</span></span> <span data-ttu-id="d5115-120">インスタンスを再開、取り消し、または終了することはできません。</span><span class="sxs-lookup"><span data-stu-id="d5115-120">The instance cannot be resumed, canceled, or terminated.</span></span> <span data-ttu-id="d5115-121">インスタンスはまだ永続化されておらず、インスタンスのデータベース エントリが完成していないため、サービス ホストはインスタンスを読み込むことができません。</span><span class="sxs-lookup"><span data-stu-id="d5115-121">The service host cannot load the instance because the instance hasn't persisted yet and, hence the database entry for the instance is not complete.</span></span>

  - <span data-ttu-id="d5115-122">**Unhandledexceptionaction** プロパティの値が **Cancel** または **Terminate** に設定されている場合は、サービスのデプロイ情報がインスタンスストアに書き込まれ、インスタンスの状態が **Completed** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d5115-122">If the value of the **UnhandledExceptionAction** property is set to **Cancel** or **Terminate**, the service deployment information is written to the instance store and the instance state is set to **Completed**.</span></span>

<span data-ttu-id="d5115-123">以降では、SQL 永続性データベースで非永続的インスタンスを検索するためのサンプル クエリと、それらのインスタンスをデータベースから削除するためのサンプル クエリを紹介します。</span><span class="sxs-lookup"><span data-stu-id="d5115-123">The following sections provide sample queries to find non-persisted instances in the SQL persistence database and to delete these instances from the database.</span></span>

## <a name="to-find-all-instances-not-persisted-yet"></a><span data-ttu-id="d5115-124">まだ永続化されていないインスタンスをすべて検索するには</span><span class="sxs-lookup"><span data-stu-id="d5115-124">To find all instances not persisted yet</span></span>

<span data-ttu-id="d5115-125">次の SQL クエリは、まだ永続性データベースに永続化されていないすべてのインスタンスの ID と作成時刻を返します。</span><span class="sxs-lookup"><span data-stu-id="d5115-125">The following SQL query returns the ID and creation time for all instances that are not persisted in to the persistence database yet.</span></span>

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;
```

## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a><span data-ttu-id="d5115-126">まだ永続化されておらず、読み込まれてもいないインスタンスをすべて検索するには</span><span class="sxs-lookup"><span data-stu-id="d5115-126">To find all instances not persisted yet and also not loaded</span></span>

 <span data-ttu-id="d5115-127">次の SQL クエリは、まだ永続化されておらず、読み込まれてもいないすべてのインスタンスの ID と作成時刻を返します。</span><span class="sxs-lookup"><span data-stu-id="d5115-127">The following SQL query returns ID and creation time for all instances that are not persisted and also are not loaded.</span></span>

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;
```

## <a name="to-find-all-suspended-instances-not-persisted-yet"></a><span data-ttu-id="d5115-128">まだ永続化されていない中断されたインスタンスをすべて検索するには</span><span class="sxs-lookup"><span data-stu-id="d5115-128">To find all suspended instances not persisted yet</span></span>

<span data-ttu-id="d5115-129">次の SQL クエリは、まだ永続化されていない中断状態のすべてのインスタンスの ID、作成時刻、中断の理由、および中断例外の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="d5115-129">The following SQL query returns ID, creation time, suspension reason, and suspension exception name for all instances that are not persisted and also in a suspended state.</span></span>

```sql
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;
```

## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a><span data-ttu-id="d5115-130">非永続的インスタンスを永続性データベースから削除するには</span><span class="sxs-lookup"><span data-stu-id="d5115-130">To delete non-persisted instances from the persistence database</span></span>

<span data-ttu-id="d5115-131">非永続的インスタンスがないかどうかをインスタンス ストアで定期的に確認して、関連付けられるメッセージをもう受信しないことがわかっている場合は、インスタンス ストアから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5115-131">You should periodically check the instance store for non-persisted instances and remove instances from the instance store if you are sure that the instance will not receive a correlated message.</span></span> <span data-ttu-id="d5115-132">たとえば、数か月にわたってデータベースに残っているインスタンスがある場合、そのワークフローの通常の有効期間が数日程度なら、クラッシュした未初期化のインスタンスと見なしても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="d5115-132">For example, if the instance has been in the database for several months and you know that the workflow typically has a lifetime of a few days, it would be safe to assume that this is an uninitialized instance that had crashed.</span></span>

<span data-ttu-id="d5115-133">一般に、非永続的インスタンスは、中断されていない場合や読み込まれていない場合は安全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="d5115-133">In general, it is safe to delete non-persisted instances that are not suspended or not loaded.</span></span> <span data-ttu-id="d5115-134">このインスタンスセットには、作成したばかりでまだ永続化されていないインスタンスが含まれているため、永続化されていない **すべて** のインスタンスを削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="d5115-134">You should not delete **all** the non-persisted instances because this instance set includes instances that are just created but are not persisted yet.</span></span> <span data-ttu-id="d5115-135">削除する必要があるのは、インスタンスを読み込んだワークフロー サービス ホストで例外が発生したり、インスタンス自体で例外が発生したりしたために永続化されずに残っているインスタンスだけです。</span><span class="sxs-lookup"><span data-stu-id="d5115-135">You should only delete non-persisted instances that are left over because the workflow service host that had the instance loaded caused an exception or the instance itself caused an exception.</span></span>

> [!WARNING]
> <span data-ttu-id="d5115-136">非永続的インスタンスをインスタンス ストアから削除すると、ストアのサイズが小さくなって、ストア操作のパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d5115-136">Deleting non-persisted instances from the instance store decreases the size of the store and may improve the performance of store operations.</span></span>
