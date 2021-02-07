---
description: 詳細については、「WCF」を参照してください。 <customTrackingQueries>
title: <customTrackingQueries> WCF の
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: ac1cdcc074201b97344b3727f6957e1b62c88dab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754473"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="42c0d-103">\<customTrackingQueries> WCF の</span><span class="sxs-lookup"><span data-stu-id="42c0d-103">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="42c0d-104">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="42c0d-104">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="42c0d-105">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="42c0d-105">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="42c0d-106">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42c0d-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="42c0d-107">構文</span><span class="sxs-lookup"><span data-stu-id="42c0d-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42c0d-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="42c0d-108">Attributes and elements</span></span>

<span data-ttu-id="42c0d-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="42c0d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42c0d-110">属性</span><span class="sxs-lookup"><span data-stu-id="42c0d-110">Attributes</span></span>

<span data-ttu-id="42c0d-111">なし。</span><span class="sxs-lookup"><span data-stu-id="42c0d-111">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="42c0d-112">子要素</span><span class="sxs-lookup"><span data-stu-id="42c0d-112">Child elements</span></span>
  
|<span data-ttu-id="42c0d-113">要素</span><span class="sxs-lookup"><span data-stu-id="42c0d-113">Element</span></span>|<span data-ttu-id="42c0d-114">説明</span><span class="sxs-lookup"><span data-stu-id="42c0d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="42c0d-115">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="42c0d-115">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42c0d-116">親要素</span><span class="sxs-lookup"><span data-stu-id="42c0d-116">Parent elements</span></span>  
  
|<span data-ttu-id="42c0d-117">要素</span><span class="sxs-lookup"><span data-stu-id="42c0d-117">Element</span></span>|<span data-ttu-id="42c0d-118">説明</span><span class="sxs-lookup"><span data-stu-id="42c0d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="42c0d-119">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="42c0d-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42c0d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="42c0d-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="42c0d-121">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="42c0d-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="42c0d-122">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="42c0d-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
