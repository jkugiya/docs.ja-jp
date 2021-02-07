---
description: '詳細情報: <faultPropagationQueries>'
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 13bd19a3673846bfbd641cd2f8eeafc20b8186f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719071"
---
# \<faultPropagationQueries>

<span data-ttu-id="f212d-102">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="f212d-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f212d-103">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="f212d-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f212d-104">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f212d-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f212d-105">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="f212d-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="f212d-106">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f212d-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="f212d-107">構文</span><span class="sxs-lookup"><span data-stu-id="f212d-107">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f212d-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f212d-108">Attributes and Elements</span></span>  

 <span data-ttu-id="f212d-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f212d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f212d-110">属性</span><span class="sxs-lookup"><span data-stu-id="f212d-110">Attributes</span></span>  

 <span data-ttu-id="f212d-111">なし。</span><span class="sxs-lookup"><span data-stu-id="f212d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f212d-112">子要素</span><span class="sxs-lookup"><span data-stu-id="f212d-112">Child Elements</span></span>  
  
|<span data-ttu-id="f212d-113">要素</span><span class="sxs-lookup"><span data-stu-id="f212d-113">Element</span></span>|<span data-ttu-id="f212d-114">説明</span><span class="sxs-lookup"><span data-stu-id="f212d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="f212d-115">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="f212d-115">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f212d-116">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="f212d-116">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f212d-117">親要素</span><span class="sxs-lookup"><span data-stu-id="f212d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f212d-118">要素</span><span class="sxs-lookup"><span data-stu-id="f212d-118">Element</span></span>|<span data-ttu-id="f212d-119">説明</span><span class="sxs-lookup"><span data-stu-id="f212d-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="f212d-120">**ActivityDefinitionId** プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="f212d-120">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f212d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f212d-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f212d-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="f212d-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f212d-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="f212d-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
