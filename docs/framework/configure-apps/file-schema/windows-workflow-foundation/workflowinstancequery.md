---
description: '詳細情報: <workflowInstanceQuery>'
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 39949b99e7c6c12ff8618e6aa3a43582d15d4133
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697791"
---
# \<workflowInstanceQuery>

<span data-ttu-id="99dba-102">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="99dba-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="99dba-103">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99dba-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="99dba-104">構文</span><span class="sxs-lookup"><span data-stu-id="99dba-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99dba-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="99dba-105">Attributes and Elements</span></span>  

 <span data-ttu-id="99dba-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="99dba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99dba-107">属性</span><span class="sxs-lookup"><span data-stu-id="99dba-107">Attributes</span></span>  

 <span data-ttu-id="99dba-108">なし。</span><span class="sxs-lookup"><span data-stu-id="99dba-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99dba-109">子要素</span><span class="sxs-lookup"><span data-stu-id="99dba-109">Child Elements</span></span>  
  
|<span data-ttu-id="99dba-110">要素</span><span class="sxs-lookup"><span data-stu-id="99dba-110">Element</span></span>|<span data-ttu-id="99dba-111">説明</span><span class="sxs-lookup"><span data-stu-id="99dba-111">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="99dba-112">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクション。</span><span class="sxs-lookup"><span data-stu-id="99dba-112">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99dba-113">親要素</span><span class="sxs-lookup"><span data-stu-id="99dba-113">Parent Elements</span></span>  
  
|<span data-ttu-id="99dba-114">要素</span><span class="sxs-lookup"><span data-stu-id="99dba-114">Element</span></span>|<span data-ttu-id="99dba-115">説明</span><span class="sxs-lookup"><span data-stu-id="99dba-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="99dba-116">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="99dba-116">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99dba-117">解説</span><span class="sxs-lookup"><span data-stu-id="99dba-117">Remarks</span></span>  

 <span data-ttu-id="99dba-118"><xref:System.Activities.Tracking.WorkflowInstanceQuery> は、次の <xref:System.Activities.Tracking.TrackingRecord> オブジェクトの定期受信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="99dba-118">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="99dba-119">例</span><span class="sxs-lookup"><span data-stu-id="99dba-119">Example</span></span>  

 <span data-ttu-id="99dba-120">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="99dba-120">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99dba-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="99dba-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="99dba-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="99dba-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="99dba-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="99dba-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
