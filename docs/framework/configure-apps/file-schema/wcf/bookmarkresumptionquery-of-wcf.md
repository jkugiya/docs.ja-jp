---
description: '詳細情報: WCF の <bookmarkResumptionQuery>'
title: WCF の <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 9dadab3e304a2507a404bf43c377df46d5b33dda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639329"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="26642-103">WCF の \<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="26642-103">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="26642-104">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="26642-104">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="26642-105">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="26642-105">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="26642-106">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26642-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="26642-107">構文</span><span class="sxs-lookup"><span data-stu-id="26642-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26642-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="26642-108">Attributes and elements</span></span>

<span data-ttu-id="26642-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="26642-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26642-110">属性</span><span class="sxs-lookup"><span data-stu-id="26642-110">Attributes</span></span>  
  
|<span data-ttu-id="26642-111">属性</span><span class="sxs-lookup"><span data-stu-id="26642-111">Attribute</span></span>|<span data-ttu-id="26642-112">説明</span><span class="sxs-lookup"><span data-stu-id="26642-112">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="26642-113">定期受信するブックマーク レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="26642-113">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26642-114">子要素</span><span class="sxs-lookup"><span data-stu-id="26642-114">Child elements</span></span>

<span data-ttu-id="26642-115">なし。</span><span class="sxs-lookup"><span data-stu-id="26642-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="26642-116">親要素</span><span class="sxs-lookup"><span data-stu-id="26642-116">Parent elements</span></span>  
  
|<span data-ttu-id="26642-117">要素</span><span class="sxs-lookup"><span data-stu-id="26642-117">Element</span></span>|<span data-ttu-id="26642-118">説明</span><span class="sxs-lookup"><span data-stu-id="26642-118">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="26642-119">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="26642-119">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26642-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="26642-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="26642-121">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="26642-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="26642-122">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="26642-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
