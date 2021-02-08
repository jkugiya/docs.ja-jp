---
description: 詳細については <states> 、「」を参照してください。 <workflowInstanceQuery>
title: <states> WCF の <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 66b3008b352d1f76c30aab9a0ec038836f33d408
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786643"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="437e1-103">\<states> WCF の \<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="437e1-103">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="437e1-104">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="437e1-104">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="437e1-105">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="437e1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="437e1-106">構文</span><span class="sxs-lookup"><span data-stu-id="437e1-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="437e1-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="437e1-107">Attributes and elements</span></span>

<span data-ttu-id="437e1-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="437e1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="437e1-109">属性</span><span class="sxs-lookup"><span data-stu-id="437e1-109">Attributes</span></span>  

<span data-ttu-id="437e1-110">なし。</span><span class="sxs-lookup"><span data-stu-id="437e1-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="437e1-111">子要素</span><span class="sxs-lookup"><span data-stu-id="437e1-111">Child elements</span></span>
  
|<span data-ttu-id="437e1-112">要素</span><span class="sxs-lookup"><span data-stu-id="437e1-112">Element</span></span>|<span data-ttu-id="437e1-113">説明</span><span class="sxs-lookup"><span data-stu-id="437e1-113">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="437e1-114">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態。</span><span class="sxs-lookup"><span data-stu-id="437e1-114">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="437e1-115">親要素</span><span class="sxs-lookup"><span data-stu-id="437e1-115">Parent elements</span></span>  
  
|<span data-ttu-id="437e1-116">要素</span><span class="sxs-lookup"><span data-stu-id="437e1-116">Element</span></span>|<span data-ttu-id="437e1-117">説明</span><span class="sxs-lookup"><span data-stu-id="437e1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="437e1-118">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリ。</span><span class="sxs-lookup"><span data-stu-id="437e1-118">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="437e1-119">解説</span><span class="sxs-lookup"><span data-stu-id="437e1-119">Remarks</span></span>

<span data-ttu-id="437e1-120">返されたレコードは、このコレクションの状態でフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="437e1-120">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="437e1-121">次の表に、有効な状態の値を示します。</span><span class="sxs-lookup"><span data-stu-id="437e1-121">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="437e1-122">状態</span><span class="sxs-lookup"><span data-stu-id="437e1-122">State</span></span>|<span data-ttu-id="437e1-123">説明</span><span class="sxs-lookup"><span data-stu-id="437e1-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="437e1-124">Aborted</span><span class="sxs-lookup"><span data-stu-id="437e1-124">Aborted</span></span>|<span data-ttu-id="437e1-125">ワークフロー インスタンスは中止されました。</span><span class="sxs-lookup"><span data-stu-id="437e1-125">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="437e1-126">完了</span><span class="sxs-lookup"><span data-stu-id="437e1-126">Completed</span></span>|<span data-ttu-id="437e1-127">ワークフロー インスタンスは完了しました。</span><span class="sxs-lookup"><span data-stu-id="437e1-127">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="437e1-128">Deleted</span><span class="sxs-lookup"><span data-stu-id="437e1-128">Deleted</span></span>|<span data-ttu-id="437e1-129">ワークフロー インスタンスは削除されました。</span><span class="sxs-lookup"><span data-stu-id="437e1-129">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="437e1-130">アイドル</span><span class="sxs-lookup"><span data-stu-id="437e1-130">Idle</span></span>|<span data-ttu-id="437e1-131">ワークフロー インスタンスはアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="437e1-131">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="437e1-132">Persisted</span><span class="sxs-lookup"><span data-stu-id="437e1-132">Persisted</span></span>|<span data-ttu-id="437e1-133">ワークフロー インスタンスは永続化されました。</span><span class="sxs-lookup"><span data-stu-id="437e1-133">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="437e1-134">Resumed</span><span class="sxs-lookup"><span data-stu-id="437e1-134">Resumed</span></span>|<span data-ttu-id="437e1-135">ワークフロー インスタンスが再開されました。</span><span class="sxs-lookup"><span data-stu-id="437e1-135">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="437e1-136">Started</span><span class="sxs-lookup"><span data-stu-id="437e1-136">Started</span></span>|<span data-ttu-id="437e1-137">ワークフロー インスタンスが開始されました。</span><span class="sxs-lookup"><span data-stu-id="437e1-137">The workflow instance is started.</span></span>|  
|<span data-ttu-id="437e1-138">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="437e1-138">UnhandledException</span></span>|<span data-ttu-id="437e1-139">ワークフロー インスタンスで未処理の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="437e1-139">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="437e1-140">アンロードされました</span><span class="sxs-lookup"><span data-stu-id="437e1-140">Unloaded</span></span>|<span data-ttu-id="437e1-141">ワークフロー インスタンスはアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="437e1-141">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="437e1-142">Canceled</span><span class="sxs-lookup"><span data-stu-id="437e1-142">Canceled</span></span>|<span data-ttu-id="437e1-143">ワークフロー インスタンスは取り消されました。</span><span class="sxs-lookup"><span data-stu-id="437e1-143">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="437e1-144">Suspended</span><span class="sxs-lookup"><span data-stu-id="437e1-144">Suspended</span></span>|<span data-ttu-id="437e1-145">ワークフロー インスタンスが中断されています。</span><span class="sxs-lookup"><span data-stu-id="437e1-145">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="437e1-146">終了</span><span class="sxs-lookup"><span data-stu-id="437e1-146">Terminated</span></span>|<span data-ttu-id="437e1-147">ワークフロー インスタンスは終了しました。</span><span class="sxs-lookup"><span data-stu-id="437e1-147">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="437e1-148">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="437e1-148">Unsuspended</span></span>|<span data-ttu-id="437e1-149">ワークフロー インスタンスの中断が解除されました。</span><span class="sxs-lookup"><span data-stu-id="437e1-149">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="437e1-150">例</span><span class="sxs-lookup"><span data-stu-id="437e1-150">Example</span></span>

<span data-ttu-id="437e1-151">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="437e1-151">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="437e1-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="437e1-152">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="437e1-153">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="437e1-153">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="437e1-154">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="437e1-154">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
