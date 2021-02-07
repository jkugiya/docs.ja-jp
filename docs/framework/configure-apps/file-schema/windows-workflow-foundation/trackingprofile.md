---
description: '詳細情報: <trackingProfile>'
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 4e0973cb44f61340e6cec7497362627cdccbd494
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697986"
---
# \<trackingProfile>

<span data-ttu-id="3187a-102">追跡参加要素内でワークフロー追跡レコードのサブスクリプションを作成するための、構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="3187a-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="3187a-103">追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3187a-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="3187a-104">追跡プロファイル セクション内で定義されたクエリでは、サブスクリプションによって返されるイベントの種類が定義されます。</span><span class="sxs-lookup"><span data-stu-id="3187a-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="3187a-105">ワークフロー追跡とその構成の詳細については、「 [ワークフローの追跡とトレース](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 」と「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3187a-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="3187a-106">構文</span><span class="sxs-lookup"><span data-stu-id="3187a-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3187a-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3187a-107">Attributes and Elements</span></span>  

 <span data-ttu-id="3187a-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3187a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3187a-109">属性</span><span class="sxs-lookup"><span data-stu-id="3187a-109">Attributes</span></span>  
  
|<span data-ttu-id="3187a-110">属性</span><span class="sxs-lookup"><span data-stu-id="3187a-110">Attribute</span></span>|<span data-ttu-id="3187a-111">説明</span><span class="sxs-lookup"><span data-stu-id="3187a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3187a-112">name</span><span class="sxs-lookup"><span data-stu-id="3187a-112">name</span></span>|<span data-ttu-id="3187a-113">追跡プロファイルの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="3187a-113">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3187a-114">子要素</span><span class="sxs-lookup"><span data-stu-id="3187a-114">Child Elements</span></span>  
  
|<span data-ttu-id="3187a-115">要素</span><span class="sxs-lookup"><span data-stu-id="3187a-115">Element</span></span>|<span data-ttu-id="3187a-116">説明</span><span class="sxs-lookup"><span data-stu-id="3187a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="3187a-117"><xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="3187a-117">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3187a-118">親要素</span><span class="sxs-lookup"><span data-stu-id="3187a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3187a-119">要素</span><span class="sxs-lookup"><span data-stu-id="3187a-119">Element</span></span>|<span data-ttu-id="3187a-120">説明</span><span class="sxs-lookup"><span data-stu-id="3187a-120">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](tracking.md)|<span data-ttu-id="3187a-121">ワークフロー サービスの追跡設定を定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="3187a-121">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3187a-122">解説</span><span class="sxs-lookup"><span data-stu-id="3187a-122">Remarks</span></span>  

 <span data-ttu-id="3187a-123">追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3187a-123">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="3187a-124">監視の要件に応じて、ワークフローの主な状態変化の少数のセットを定期受信する、大まかなプロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3187a-124">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="3187a-125">それとは反対に、結果として得られるイベントが、後で詳細な実行フローを十分に再構築できるほど豊富な、詳細なプロファイルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3187a-125">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="3187a-126">追跡プロファイルは、特定の追跡レコードを対象としてワークフロー ランタイムを照会できる、追跡レコード用の宣言型のサブスクリプションとして構築されます。</span><span class="sxs-lookup"><span data-stu-id="3187a-126">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="3187a-127">オブジェクトのさまざまなクラスをサブスクライブできるクエリの種類がいくつかあり <xref:System.Activities.Tracking.TrackingRecord> ます。</span><span class="sxs-lookup"><span data-stu-id="3187a-127">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="3187a-128">クエリの完全な一覧については、「」 [\<participants>](participants.md) および「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3187a-128">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="3187a-129">次の例は、追跡参加要素がワークフローイベントとワークフローイベントをサブスクライブできるようにする、構成ファイル内の追跡プロファイルを示して `Started` `Completed` います。</span><span class="sxs-lookup"><span data-stu-id="3187a-129">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3187a-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="3187a-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="3187a-131">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="3187a-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3187a-132">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="3187a-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
