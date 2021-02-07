---
description: '詳細情報: <bookmarkResumptionQueries>'
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: e8ff21e2183fe31411674e9d4de6bf3d99d14836
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698155"
---
# \<bookmarkResumptionQueries>

<span data-ttu-id="547a0-102">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="547a0-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="547a0-103">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="547a0-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="547a0-104">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="547a0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="547a0-105">構文</span><span class="sxs-lookup"><span data-stu-id="547a0-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="547a0-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="547a0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="547a0-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="547a0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="547a0-108">属性</span><span class="sxs-lookup"><span data-stu-id="547a0-108">Attributes</span></span>  

 <span data-ttu-id="547a0-109">なし。</span><span class="sxs-lookup"><span data-stu-id="547a0-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="547a0-110">子要素</span><span class="sxs-lookup"><span data-stu-id="547a0-110">Child Elements</span></span>  
  
|<span data-ttu-id="547a0-111">要素</span><span class="sxs-lookup"><span data-stu-id="547a0-111">Element</span></span>|<span data-ttu-id="547a0-112">説明</span><span class="sxs-lookup"><span data-stu-id="547a0-112">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="547a0-113">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="547a0-113">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="547a0-114">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="547a0-114">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="547a0-115">親要素</span><span class="sxs-lookup"><span data-stu-id="547a0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="547a0-116">要素</span><span class="sxs-lookup"><span data-stu-id="547a0-116">Element</span></span>|<span data-ttu-id="547a0-117">説明</span><span class="sxs-lookup"><span data-stu-id="547a0-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="547a0-118">**ActivityDefinitionId** プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="547a0-118">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="547a0-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="547a0-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="547a0-120">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="547a0-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="547a0-121">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="547a0-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
