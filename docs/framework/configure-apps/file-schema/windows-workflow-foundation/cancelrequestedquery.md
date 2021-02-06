---
description: '詳細情報: <cancelRequestedQuery>'
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: efd908fb52d2bc32bf05fce9099c7105abdc9b1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652641"
---
# \<cancelRequestedQuery>

<span data-ttu-id="8aad8-102">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="8aad8-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8aad8-103">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="8aad8-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="8aad8-104">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aad8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="8aad8-105">構文</span><span class="sxs-lookup"><span data-stu-id="8aad8-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8aad8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8aad8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8aad8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aad8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8aad8-108">属性</span><span class="sxs-lookup"><span data-stu-id="8aad8-108">Attributes</span></span>  
  
|<span data-ttu-id="8aad8-109">属性</span><span class="sxs-lookup"><span data-stu-id="8aad8-109">Attribute</span></span>|<span data-ttu-id="8aad8-110">説明</span><span class="sxs-lookup"><span data-stu-id="8aad8-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8aad8-111">activityName</span><span class="sxs-lookup"><span data-stu-id="8aad8-111">activityName</span></span>|<span data-ttu-id="8aad8-112">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="8aad8-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="8aad8-113">childActivityName</span><span class="sxs-lookup"><span data-stu-id="8aad8-113">childActivityName</span></span>|<span data-ttu-id="8aad8-114">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="8aad8-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8aad8-115">子要素</span><span class="sxs-lookup"><span data-stu-id="8aad8-115">Child Elements</span></span>  

 <span data-ttu-id="8aad8-116">なし。</span><span class="sxs-lookup"><span data-stu-id="8aad8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8aad8-117">親要素</span><span class="sxs-lookup"><span data-stu-id="8aad8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8aad8-118">要素</span><span class="sxs-lookup"><span data-stu-id="8aad8-118">Element</span></span>|<span data-ttu-id="8aad8-119">説明</span><span class="sxs-lookup"><span data-stu-id="8aad8-119">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="8aad8-120">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="8aad8-120">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8aad8-121">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="8aad8-121">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8aad8-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8aad8-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8aad8-123">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="8aad8-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8aad8-124">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="8aad8-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
