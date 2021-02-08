---
description: 詳細については、「WCF」を参照してください。 <faultPropagationQuery>
title: <faultPropagationQuery> WCF の
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: cd26bf76fec54371ef0455b93c98650bdab19068
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782066"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="8d180-103">\<faultPropagationQuery> WCF の</span><span class="sxs-lookup"><span data-stu-id="8d180-103">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="8d180-104">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="8d180-104">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="8d180-105">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="8d180-105">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="8d180-106">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d180-106">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="8d180-107">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="8d180-107">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="8d180-108">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d180-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="8d180-109">構文</span><span class="sxs-lookup"><span data-stu-id="8d180-109">Syntax</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8d180-110">属性と要素</span><span class="sxs-lookup"><span data-stu-id="8d180-110">Attributes and elements</span></span>

<span data-ttu-id="8d180-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d180-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8d180-112">属性</span><span class="sxs-lookup"><span data-stu-id="8d180-112">Attributes</span></span>

|<span data-ttu-id="8d180-113">属性</span><span class="sxs-lookup"><span data-stu-id="8d180-113">Attribute</span></span>|<span data-ttu-id="8d180-114">説明</span><span class="sxs-lookup"><span data-stu-id="8d180-114">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="8d180-115">エラーを伝達したエラーハンドラーアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="8d180-115">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="8d180-116">既定値は \* で、すべてのアクティビティについてエラー伝達レコードが返されることを示します。</span><span class="sxs-lookup"><span data-stu-id="8d180-116">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="8d180-117">エラーの原因となったアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="8d180-117">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8d180-118">子要素</span><span class="sxs-lookup"><span data-stu-id="8d180-118">Child elements</span></span>

<span data-ttu-id="8d180-119">なし。</span><span class="sxs-lookup"><span data-stu-id="8d180-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8d180-120">親要素</span><span class="sxs-lookup"><span data-stu-id="8d180-120">Parent elements</span></span>

|<span data-ttu-id="8d180-121">要素</span><span class="sxs-lookup"><span data-stu-id="8d180-121">Element</span></span>|<span data-ttu-id="8d180-122">説明</span><span class="sxs-lookup"><span data-stu-id="8d180-122">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="8d180-123">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="8d180-123">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="8d180-124">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="8d180-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8d180-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d180-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8d180-126">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="8d180-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8d180-127">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="8d180-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
