---
description: '詳細情報: WCF の <bookmarkResumptionQueries>'
title: WCF の <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: dfe631865549915760255b1df22ee970b806e368
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639368"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="0899a-103">WCF の \<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="0899a-103">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="0899a-104">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="0899a-104">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="0899a-105">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="0899a-105">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="0899a-106">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0899a-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="0899a-107">構文</span><span class="sxs-lookup"><span data-stu-id="0899a-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0899a-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="0899a-108">Attributes and elements</span></span>  
  
<span data-ttu-id="0899a-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0899a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0899a-110">属性</span><span class="sxs-lookup"><span data-stu-id="0899a-110">Attributes</span></span>  
  
<span data-ttu-id="0899a-111">なし。</span><span class="sxs-lookup"><span data-stu-id="0899a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0899a-112">子要素</span><span class="sxs-lookup"><span data-stu-id="0899a-112">Child elements</span></span>  
  
|<span data-ttu-id="0899a-113">要素</span><span class="sxs-lookup"><span data-stu-id="0899a-113">Element</span></span>|<span data-ttu-id="0899a-114">説明</span><span class="sxs-lookup"><span data-stu-id="0899a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="0899a-115">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="0899a-115">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="0899a-116">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="0899a-116">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0899a-117">親要素</span><span class="sxs-lookup"><span data-stu-id="0899a-117">Parent elements</span></span>  
  
|<span data-ttu-id="0899a-118">要素</span><span class="sxs-lookup"><span data-stu-id="0899a-118">Element</span></span>|<span data-ttu-id="0899a-119">説明</span><span class="sxs-lookup"><span data-stu-id="0899a-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="0899a-120">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="0899a-120">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0899a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0899a-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0899a-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="0899a-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0899a-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="0899a-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
