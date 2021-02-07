---
description: '詳細情報: <cancelRequestedQueries>'
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: a508de97bce604284d9af00a3344fe5f35dc8bea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698077"
---
# \<cancelRequestedQueries>

<span data-ttu-id="35b91-102">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="35b91-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="35b91-103">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="35b91-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="35b91-104">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35b91-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="35b91-105">構文</span><span class="sxs-lookup"><span data-stu-id="35b91-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35b91-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="35b91-106">Attributes and Elements</span></span>  

 <span data-ttu-id="35b91-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="35b91-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35b91-108">属性</span><span class="sxs-lookup"><span data-stu-id="35b91-108">Attributes</span></span>  

 <span data-ttu-id="35b91-109">なし。</span><span class="sxs-lookup"><span data-stu-id="35b91-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="35b91-110">子要素</span><span class="sxs-lookup"><span data-stu-id="35b91-110">Child Elements</span></span>  
  
|<span data-ttu-id="35b91-111">要素</span><span class="sxs-lookup"><span data-stu-id="35b91-111">Element</span></span>|<span data-ttu-id="35b91-112">説明</span><span class="sxs-lookup"><span data-stu-id="35b91-112">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="35b91-113">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="35b91-113">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35b91-114">親要素</span><span class="sxs-lookup"><span data-stu-id="35b91-114">Parent Elements</span></span>  
  
|<span data-ttu-id="35b91-115">要素</span><span class="sxs-lookup"><span data-stu-id="35b91-115">Element</span></span>|<span data-ttu-id="35b91-116">説明</span><span class="sxs-lookup"><span data-stu-id="35b91-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="35b91-117">**ActivityDefinitionId** プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="35b91-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35b91-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="35b91-118">See also</span></span>

- [<span data-ttu-id="35b91-119">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="35b91-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="35b91-120">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="35b91-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
