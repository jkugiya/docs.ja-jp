---
description: '詳細情報: WCF の <cancelRequestedQueries>'
title: WCF の <cancelRequestedQueries>
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 3850d7efd01f9092312567a0eba68a6e9547baad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639186"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="cb0ab-103">WCF の \<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="cb0ab-103">\<cancelRequestedQueries> of WCF</span></span>

<span data-ttu-id="cb0ab-104">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="cb0ab-104">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="cb0ab-105">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="cb0ab-105">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="cb0ab-106">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="cb0ab-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="cb0ab-107">構文</span><span class="sxs-lookup"><span data-stu-id="cb0ab-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb0ab-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="cb0ab-108">Attributes and elements</span></span>  

<span data-ttu-id="cb0ab-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb0ab-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb0ab-110">属性</span><span class="sxs-lookup"><span data-stu-id="cb0ab-110">Attributes</span></span>

<span data-ttu-id="cb0ab-111">なし。</span><span class="sxs-lookup"><span data-stu-id="cb0ab-111">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="cb0ab-112">子要素</span><span class="sxs-lookup"><span data-stu-id="cb0ab-112">Child elements</span></span>
  
|<span data-ttu-id="cb0ab-113">要素</span><span class="sxs-lookup"><span data-stu-id="cb0ab-113">Element</span></span>|<span data-ttu-id="cb0ab-114">説明</span><span class="sxs-lookup"><span data-stu-id="cb0ab-114">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="cb0ab-115">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="cb0ab-115">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb0ab-116">親要素</span><span class="sxs-lookup"><span data-stu-id="cb0ab-116">Parent elements</span></span>  
  
|<span data-ttu-id="cb0ab-117">要素</span><span class="sxs-lookup"><span data-stu-id="cb0ab-117">Element</span></span>|<span data-ttu-id="cb0ab-118">説明</span><span class="sxs-lookup"><span data-stu-id="cb0ab-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="cb0ab-119"><xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="cb0ab-119">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb0ab-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb0ab-120">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="cb0ab-121">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="cb0ab-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cb0ab-122">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="cb0ab-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
