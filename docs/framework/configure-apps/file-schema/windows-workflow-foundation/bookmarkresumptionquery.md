---
description: '詳細情報: <bookmarkResumptionQuery>'
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 4e6637b6edd54d9c1cf1a44986b362eb616bf14d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725247"
---
# \<bookmarkResumptionQuery>

<span data-ttu-id="a0ab4-102">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="a0ab4-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a0ab4-103">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="a0ab4-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="a0ab4-104">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0ab4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="a0ab4-105">構文</span><span class="sxs-lookup"><span data-stu-id="a0ab4-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0ab4-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a0ab4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a0ab4-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0ab4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0ab4-108">属性</span><span class="sxs-lookup"><span data-stu-id="a0ab4-108">Attributes</span></span>  
  
|<span data-ttu-id="a0ab4-109">属性</span><span class="sxs-lookup"><span data-stu-id="a0ab4-109">Attribute</span></span>|<span data-ttu-id="a0ab4-110">説明</span><span class="sxs-lookup"><span data-stu-id="a0ab4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0ab4-111">name</span><span class="sxs-lookup"><span data-stu-id="a0ab4-111">name</span></span>|<span data-ttu-id="a0ab4-112">定期受信するブックマーク レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="a0ab4-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0ab4-113">子要素</span><span class="sxs-lookup"><span data-stu-id="a0ab4-113">Child Elements</span></span>  

 <span data-ttu-id="a0ab4-114">なし。</span><span class="sxs-lookup"><span data-stu-id="a0ab4-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0ab4-115">親要素</span><span class="sxs-lookup"><span data-stu-id="a0ab4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a0ab4-116">要素</span><span class="sxs-lookup"><span data-stu-id="a0ab4-116">Element</span></span>|<span data-ttu-id="a0ab4-117">説明</span><span class="sxs-lookup"><span data-stu-id="a0ab4-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="a0ab4-118">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="a0ab4-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0ab4-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0ab4-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a0ab4-120">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="a0ab4-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a0ab4-121">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="a0ab4-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
