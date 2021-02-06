---
description: 詳細については、「WCF」を参照してください。 <cancelRequestedQuery>
title: <cancelRequestedQuery> WCF の
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: e477e33650eb901cf2e9275570d8538196c52b6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639173"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="9ad1a-103">\<cancelRequestedQuery> WCF の</span><span class="sxs-lookup"><span data-stu-id="9ad1a-103">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="9ad1a-104">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="9ad1a-104">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="9ad1a-105">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="9ad1a-105">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="9ad1a-106">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ad1a-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="9ad1a-107">構文</span><span class="sxs-lookup"><span data-stu-id="9ad1a-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ad1a-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="9ad1a-108">Attributes and elements</span></span>

<span data-ttu-id="9ad1a-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ad1a-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ad1a-110">属性</span><span class="sxs-lookup"><span data-stu-id="9ad1a-110">Attributes</span></span>  
  
|<span data-ttu-id="9ad1a-111">属性</span><span class="sxs-lookup"><span data-stu-id="9ad1a-111">Attribute</span></span>|<span data-ttu-id="9ad1a-112">説明</span><span class="sxs-lookup"><span data-stu-id="9ad1a-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="9ad1a-113">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="9ad1a-113">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="9ad1a-114">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="9ad1a-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ad1a-115">子要素</span><span class="sxs-lookup"><span data-stu-id="9ad1a-115">Child elements</span></span>

<span data-ttu-id="9ad1a-116">なし。</span><span class="sxs-lookup"><span data-stu-id="9ad1a-116">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="9ad1a-117">親要素</span><span class="sxs-lookup"><span data-stu-id="9ad1a-117">Parent elements</span></span>
  
|<span data-ttu-id="9ad1a-118">要素</span><span class="sxs-lookup"><span data-stu-id="9ad1a-118">Element</span></span>|<span data-ttu-id="9ad1a-119">説明</span><span class="sxs-lookup"><span data-stu-id="9ad1a-119">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="9ad1a-120">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="9ad1a-120">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ad1a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ad1a-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9ad1a-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="9ad1a-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9ad1a-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="9ad1a-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
