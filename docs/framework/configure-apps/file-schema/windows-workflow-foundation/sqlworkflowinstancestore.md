---
description: '詳細情報: <sqlWorkflowInstanceStore>'
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 8fcf5dd970adf5aa668d90b012c94e04c5373752
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782012"
---
# \<sqlWorkflowInstanceStore>

<span data-ttu-id="6f0b8-102">ワークフロー サービス インスタンスの状態情報の永続化を SQL Server 2005 または SQL Server 2008 データベースでサポートする <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 機能を構成するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-102">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="6f0b8-103">この機能の詳細については、「 [SQL Workflow Instance Store](../../../windows-workflow-foundation/sql-workflow-instance-store.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-103">For more information on this feature, see [SQL Workflow Instance Store](../../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sqlWorkflowInstanceStore>**  
  
## <a name="syntax"></a><span data-ttu-id="6f0b8-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f0b8-104">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String"
                                hostLockRenewalPeriod="TimeSpan"
                                instanceCompletionAction="DeleteNothing/DeleteAll"
                                instanceEncodingAction="None/GZip"
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f0b8-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6f0b8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6f0b8-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f0b8-107">属性</span><span class="sxs-lookup"><span data-stu-id="6f0b8-107">Attributes</span></span>  
  
|<span data-ttu-id="6f0b8-108">属性</span><span class="sxs-lookup"><span data-stu-id="6f0b8-108">Attribute</span></span>|<span data-ttu-id="6f0b8-109">説明</span><span class="sxs-lookup"><span data-stu-id="6f0b8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f0b8-110">connectionString</span><span class="sxs-lookup"><span data-stu-id="6f0b8-110">connectionString</span></span>|<span data-ttu-id="6f0b8-111">基になる永続性データベースへの接続に使用する接続文字列を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-111">A string that contains a connection string used to connect to an underlying persistence database.</span></span>|  
|<span data-ttu-id="6f0b8-112">connectionStringName</span><span class="sxs-lookup"><span data-stu-id="6f0b8-112">connectionStringName</span></span>|<span data-ttu-id="6f0b8-113">データベース サーバーへの名前付き接続文字列を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-113">A string that contains a named connection string to the database server.</span></span> <span data-ttu-id="6f0b8-114">名前付き接続文字列の例としては、"DefaultConnectionString" などがあります。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-114">An example of a named connection string is "DefaultConnectionString".</span></span>|  
|<span data-ttu-id="6f0b8-115">hostLockRenewalPeriod</span><span class="sxs-lookup"><span data-stu-id="6f0b8-115">hostLockRenewalPeriod</span></span>|<span data-ttu-id="6f0b8-116">ホストがインスタンスのロックを更新するまでの時間を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-116">A Timespan value that specifies the time period in which the host must renew the lock on an instance.</span></span> <span data-ttu-id="6f0b8-117">指定した時間内にホストがロックを更新しない場合は、インスタンスのロックが解除され、他のホストがそのインスタンスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-117">If the host does not renew the lock in the specified time period, the instance is unlocked and may be picked up by another host.</span></span><br /><br /> <span data-ttu-id="6f0b8-118">ワークフローをアンロードすることは、同時に、永続化することも意味します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-118">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="6f0b8-119">この属性をゼロに設定した場合は、ワークフローがアイドル状態になった直後に、ワークフロー インスタンスが永続化され、アンロードされます。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-119">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="6f0b8-120">この属性を TimeSpan.MaxValue に設定すると、アンロード操作を事実上、無効にします。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-120">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="6f0b8-121">アイドル状態になったワークフロー インスタンスはアンロードされません。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-121">Idle workflow instances are never unloaded.</span></span>|  
|<span data-ttu-id="6f0b8-122">instanceCompletionAction</span><span class="sxs-lookup"><span data-stu-id="6f0b8-122">instanceCompletionAction</span></span>|<span data-ttu-id="6f0b8-123">ワークフロー インスタンス完了後にワークフロー インスタンス データを永続化ストアに保持するか、またはその時点で削除するかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-123">A value that specifies whether workflow instance data is kept in the persistence store after the workflow instance completes or if it is deleted at that point.</span></span> <span data-ttu-id="6f0b8-124">この値は、<xref:System.Activities.DurableInstancing.InstanceCompletionAction> 型です。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-124">This value is of type <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.</span></span><br /><br /> <span data-ttu-id="6f0b8-125">列挙されるアクションは、インスタンスがその操作を完了したとき、永続化ストアからインスタンス データを削除するかどうかで構成されます。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-125">The enumerated actions consist of deleting the instance data from the persistence store or not deleting the instance data from the persistence store, when the instance has completed its operation.</span></span><br /><br /> <span data-ttu-id="6f0b8-126">完了後にインスタンスを保持すると、永続性データベースが急速に増大して、データベースのパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-126">Keeping instances after completion causes the persistence database to grow rapidly and this affects the performance of the database.</span></span> <span data-ttu-id="6f0b8-127">データベースのパフォーマンスがパフォーマンス要件を満たすレベルになるように、これらのレコードを定期的に削除するパージ ポリシーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-127">You should configure a database purge policy to delete these records periodically to ensure that the performance of the database is at the level that satisfy your performance requirements.</span></span>|  
|<span data-ttu-id="6f0b8-128">instanceEncodingOption</span><span class="sxs-lookup"><span data-stu-id="6f0b8-128">instanceEncodingOption</span></span>|<span data-ttu-id="6f0b8-129">インスタンス状態情報を永続化ストアに格納する前に、GZip アルゴリズムで圧縮するかどうかを指定する、省略可能な値。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-129">An optional value that specifies  whether the instance state information is compressed using the GZip algorithm before the information is saved in the persistence store..</span></span> <span data-ttu-id="6f0b8-130">この値は、<xref:System.Activities.DurableInstancing.InstanceEncodingOption> 型です。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-130">This value is of type <xref:System.Activities.DurableInstancing.InstanceEncodingOption>.</span></span> <span data-ttu-id="6f0b8-131">このプロパティに指定できる値はで、圧縮が指定されてい <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None> ません <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip> 。また、はインスタンスデータを圧縮し、gzip アルゴリズムを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-131">Possible values for this property are <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>, which specifies no compression, and <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>, which specifies that instance data is compressed and uses the gzip algorithm.</span></span>|  
|<span data-ttu-id="6f0b8-132">instanceLockedExceptionAction</span><span class="sxs-lookup"><span data-stu-id="6f0b8-132">instanceLockedExceptionAction</span></span>|<span data-ttu-id="6f0b8-133">現在、他のホストにロックされているインスタンスをホストがロックしようとしたときにスローされる例外への応答として発生するアクションを指定する値。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-133">A value that specifies the action that occurs in response to an exception that is thrown when the host tries to lock an instance because the instance is currently locked by another host.</span></span> <span data-ttu-id="6f0b8-134">この値は、<xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> 型です。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-134">This value is of type <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.</span></span><br /><br /> <span data-ttu-id="6f0b8-135">このフィールドで使用できるオプションは、None、Basic Retry、および Aggressive Retry です。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-135">The options allowed for this field are: None, Basic Retry, and Aggressive Retry.</span></span> <span data-ttu-id="6f0b8-136">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-136">The default value is None.</span></span> <span data-ttu-id="6f0b8-137">これら 3 つのオプションの説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-137">The following list provides you with the descriptions for these three options:</span></span><br /><br /> <span data-ttu-id="6f0b8-138">- なし。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-138">-   None.</span></span> <span data-ttu-id="6f0b8-139">サービス ホストはインスタンスをロックしようとせず、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-139">The service host does not attempt to lock the instance and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller.</span></span><br /><span data-ttu-id="6f0b8-140">-基本的な再試行。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-140">-   Basic Retry.</span></span> <span data-ttu-id="6f0b8-141">サービス ホストは一定の再試行間隔でインスタンスのロックを再試行し、シーケンスの最後に例外を呼び出し元に渡します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-141">The service host reattempts to lock the instance with a linear retry interval and passes the exception to the caller at the end of the sequence.</span></span><br /><span data-ttu-id="6f0b8-142">-積極的に再試行します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-142">-   Aggressive Retry.</span></span> <span data-ttu-id="6f0b8-143">サービス ホストは指数関数的に増加する遅延を使用してインスタンスのロックを再試行し、シーケンスの最後に <xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-143">The service host reattempts to lock the instance with an exponentially increasing delay and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller at the end of the sequence.</span></span>|  
|<span data-ttu-id="6f0b8-144">runnableInstancesDetectionPeriod</span><span class="sxs-lookup"><span data-stu-id="6f0b8-144">runnableInstancesDetectionPeriod</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="6f0b8-145">子要素</span><span class="sxs-lookup"><span data-stu-id="6f0b8-145">Child Elements</span></span>  

 <span data-ttu-id="6f0b8-146">なし。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-146">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f0b8-147">親要素</span><span class="sxs-lookup"><span data-stu-id="6f0b8-147">Parent Elements</span></span>  
  
|<span data-ttu-id="6f0b8-148">要素</span><span class="sxs-lookup"><span data-stu-id="6f0b8-148">Element</span></span>|<span data-ttu-id="6f0b8-149">説明</span><span class="sxs-lookup"><span data-stu-id="6f0b8-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f0b8-150">\<serviceBehaviors> の \<behavior></span><span class="sxs-lookup"><span data-stu-id="6f0b8-150">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="6f0b8-151">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f0b8-151">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f0b8-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f0b8-152">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [<span data-ttu-id="6f0b8-153">SQL Workflow Instance Store</span><span class="sxs-lookup"><span data-stu-id="6f0b8-153">SQL Workflow Instance Store</span></span>](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
