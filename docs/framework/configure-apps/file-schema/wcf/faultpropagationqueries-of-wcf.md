---
description: 詳細については、「WCF」を参照してください。 <faultPropagationQueries>
title: <faultPropagationQueries> WCF の
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: e3ed504b3aada87246fabe54c0b32ef5ad60b34b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684439"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="00eef-103">\<faultPropagationQueries> WCF の</span><span class="sxs-lookup"><span data-stu-id="00eef-103">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="00eef-104">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="00eef-104">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="00eef-105">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="00eef-105">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="00eef-106">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00eef-106">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="00eef-107">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="00eef-107">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="00eef-108">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00eef-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="00eef-109">構文</span><span class="sxs-lookup"><span data-stu-id="00eef-109">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00eef-110">属性と要素</span><span class="sxs-lookup"><span data-stu-id="00eef-110">Attributes and elements</span></span>

<span data-ttu-id="00eef-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="00eef-111">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="00eef-112">属性</span><span class="sxs-lookup"><span data-stu-id="00eef-112">Attributes</span></span>

<span data-ttu-id="00eef-113">なし。</span><span class="sxs-lookup"><span data-stu-id="00eef-113">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="00eef-114">子要素</span><span class="sxs-lookup"><span data-stu-id="00eef-114">Child elements</span></span>

|<span data-ttu-id="00eef-115">要素</span><span class="sxs-lookup"><span data-stu-id="00eef-115">Element</span></span>|<span data-ttu-id="00eef-116">説明</span><span class="sxs-lookup"><span data-stu-id="00eef-116">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="00eef-117">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="00eef-117">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="00eef-118">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="00eef-118">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00eef-119">親要素</span><span class="sxs-lookup"><span data-stu-id="00eef-119">Parent elements</span></span>  
  
|<span data-ttu-id="00eef-120">要素</span><span class="sxs-lookup"><span data-stu-id="00eef-120">Element</span></span>|<span data-ttu-id="00eef-121">説明</span><span class="sxs-lookup"><span data-stu-id="00eef-121">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="00eef-122">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="00eef-122">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00eef-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="00eef-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="00eef-124">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="00eef-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="00eef-125">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="00eef-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
