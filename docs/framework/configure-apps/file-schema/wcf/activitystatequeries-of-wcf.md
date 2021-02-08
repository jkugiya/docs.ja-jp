---
description: 詳細については、「WCF」を参照してください。 <activityStateQueries>
title: <activityStateQueries> WCF の
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 00795a26a37f62fae8aa884b5a4188be79453186
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782235"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="5a9bb-103">\<activityStateQueries> WCF の</span><span class="sxs-lookup"><span data-stu-id="5a9bb-103">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="5a9bb-104">ワークフロー インスタンスを構成するアクティビティのライフサイクルの変化を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-104">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="5a9bb-105">たとえば、ワークフローインスタンス内で "電子メールの送信" アクティビティが完了するたびに追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-105">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="5a9bb-106">追跡参加要素がアクティビティ状態レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-106">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="5a9bb-107">定期受信可能な状態は ActivityStates で指定します。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-107">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="5a9bb-108">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="5a9bb-109">構文</span><span class="sxs-lookup"><span data-stu-id="5a9bb-109">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="5a9bb-110">属性と要素</span><span class="sxs-lookup"><span data-stu-id="5a9bb-110">Attributes and elements</span></span>

<span data-ttu-id="5a9bb-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="5a9bb-112">属性</span><span class="sxs-lookup"><span data-stu-id="5a9bb-112">Attributes</span></span>  

<span data-ttu-id="5a9bb-113">なし。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-113">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="5a9bb-114">子要素</span><span class="sxs-lookup"><span data-stu-id="5a9bb-114">Child elements</span></span>

|<span data-ttu-id="5a9bb-115">要素</span><span class="sxs-lookup"><span data-stu-id="5a9bb-115">Element</span></span>|<span data-ttu-id="5a9bb-116">説明</span><span class="sxs-lookup"><span data-stu-id="5a9bb-116">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="5a9bb-117">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-117">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5a9bb-118">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-118">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5a9bb-119">親要素</span><span class="sxs-lookup"><span data-stu-id="5a9bb-119">Parent elements</span></span>

|<span data-ttu-id="5a9bb-120">要素</span><span class="sxs-lookup"><span data-stu-id="5a9bb-120">Element</span></span>|<span data-ttu-id="5a9bb-121">説明</span><span class="sxs-lookup"><span data-stu-id="5a9bb-121">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="5a9bb-122">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="5a9bb-122">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5a9bb-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a9bb-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="5a9bb-124">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="5a9bb-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5a9bb-125">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="5a9bb-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
