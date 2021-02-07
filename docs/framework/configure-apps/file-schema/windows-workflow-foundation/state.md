---
description: '詳細情報: <state>'
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: c04ba8a791d08e65337ffc28cd86f5a4a6af150f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729759"
---
# \<state>

<span data-ttu-id="5e3c2-102">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="5e3c2-103">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="5e3c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="5e3c2-104">Syntax</span></span>  
  
```xml  
<tracking>
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
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e3c2-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5e3c2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5e3c2-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e3c2-107">属性</span><span class="sxs-lookup"><span data-stu-id="5e3c2-107">Attributes</span></span>  
  
|<span data-ttu-id="5e3c2-108">属性</span><span class="sxs-lookup"><span data-stu-id="5e3c2-108">Attribute</span></span>|<span data-ttu-id="5e3c2-109">説明</span><span class="sxs-lookup"><span data-stu-id="5e3c2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e3c2-110">name</span><span class="sxs-lookup"><span data-stu-id="5e3c2-110">name</span></span>|<span data-ttu-id="5e3c2-111">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-111">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e3c2-112">子要素</span><span class="sxs-lookup"><span data-stu-id="5e3c2-112">Child Elements</span></span>  

 <span data-ttu-id="5e3c2-113">なし。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e3c2-114">親要素</span><span class="sxs-lookup"><span data-stu-id="5e3c2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5e3c2-115">要素</span><span class="sxs-lookup"><span data-stu-id="5e3c2-115">Element</span></span>|<span data-ttu-id="5e3c2-116">説明</span><span class="sxs-lookup"><span data-stu-id="5e3c2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="5e3c2-117">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクション。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-117">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e3c2-118">解説</span><span class="sxs-lookup"><span data-stu-id="5e3c2-118">Remarks</span></span>  

 <span data-ttu-id="5e3c2-119">返されたレコードは、このコレクションの状態でフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-119">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="5e3c2-120">次の表に、有効な状態の値を示します。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="5e3c2-121">状態</span><span class="sxs-lookup"><span data-stu-id="5e3c2-121">State</span></span>|<span data-ttu-id="5e3c2-122">説明</span><span class="sxs-lookup"><span data-stu-id="5e3c2-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e3c2-123">Aborted</span><span class="sxs-lookup"><span data-stu-id="5e3c2-123">Aborted</span></span>|<span data-ttu-id="5e3c2-124">ワークフロー インスタンスは中止されました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="5e3c2-125">完了</span><span class="sxs-lookup"><span data-stu-id="5e3c2-125">Completed</span></span>|<span data-ttu-id="5e3c2-126">ワークフロー インスタンスは完了しました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="5e3c2-127">Deleted</span><span class="sxs-lookup"><span data-stu-id="5e3c2-127">Deleted</span></span>|<span data-ttu-id="5e3c2-128">ワークフロー インスタンスは削除されました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="5e3c2-129">アイドル</span><span class="sxs-lookup"><span data-stu-id="5e3c2-129">Idle</span></span>|<span data-ttu-id="5e3c2-130">ワークフロー インスタンスはアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="5e3c2-131">Persisted</span><span class="sxs-lookup"><span data-stu-id="5e3c2-131">Persisted</span></span>|<span data-ttu-id="5e3c2-132">ワークフロー インスタンスは永続化されました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="5e3c2-133">Resumed</span><span class="sxs-lookup"><span data-stu-id="5e3c2-133">Resumed</span></span>|<span data-ttu-id="5e3c2-134">ワークフロー インスタンスが再開されました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="5e3c2-135">Started</span><span class="sxs-lookup"><span data-stu-id="5e3c2-135">Started</span></span>|<span data-ttu-id="5e3c2-136">ワークフロー インスタンスが開始されました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="5e3c2-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="5e3c2-137">UnhandledException</span></span>|<span data-ttu-id="5e3c2-138">ワークフロー インスタンスで未処理の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="5e3c2-139">アンロードされました</span><span class="sxs-lookup"><span data-stu-id="5e3c2-139">Unloaded</span></span>|<span data-ttu-id="5e3c2-140">ワークフロー インスタンスはアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="5e3c2-141">Canceled</span><span class="sxs-lookup"><span data-stu-id="5e3c2-141">Canceled</span></span>|<span data-ttu-id="5e3c2-142">ワークフロー インスタンスは取り消されました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="5e3c2-143">Suspended</span><span class="sxs-lookup"><span data-stu-id="5e3c2-143">Suspended</span></span>|<span data-ttu-id="5e3c2-144">ワークフロー インスタンスが中断されています。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="5e3c2-145">終了</span><span class="sxs-lookup"><span data-stu-id="5e3c2-145">Terminated</span></span>|<span data-ttu-id="5e3c2-146">ワークフロー インスタンスは終了しました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="5e3c2-147">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="5e3c2-147">Unsuspended</span></span>|<span data-ttu-id="5e3c2-148">ワークフロー インスタンスの中断が解除されました。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5e3c2-149">例</span><span class="sxs-lookup"><span data-stu-id="5e3c2-149">Example</span></span>  

 <span data-ttu-id="5e3c2-150">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="5e3c2-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e3c2-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e3c2-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5e3c2-152">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="5e3c2-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5e3c2-153">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="5e3c2-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
