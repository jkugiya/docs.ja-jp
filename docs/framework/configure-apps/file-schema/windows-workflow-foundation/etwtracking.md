---
description: '詳細情報: <etwTracking>'
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: b89d832e73440d5b60a05477ccf85178c2f43a2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795080"
---
# \<etwTracking>

<span data-ttu-id="2587d-102"><xref:System.Activities.Tracking.EtwTrackingParticipant> を使用して、サービスで ETW 追跡を利用するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="2587d-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="2587d-103">構文</span><span class="sxs-lookup"><span data-stu-id="2587d-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2587d-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2587d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2587d-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2587d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2587d-106">属性</span><span class="sxs-lookup"><span data-stu-id="2587d-106">Attributes</span></span>  
  
|<span data-ttu-id="2587d-107">属性</span><span class="sxs-lookup"><span data-stu-id="2587d-107">Attribute</span></span>|<span data-ttu-id="2587d-108">説明</span><span class="sxs-lookup"><span data-stu-id="2587d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2587d-109">profileName</span><span class="sxs-lookup"><span data-stu-id="2587d-109">profileName</span></span>|<span data-ttu-id="2587d-110">この動作に関連付けられた追跡プロファイルの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2587d-110">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2587d-111">子要素</span><span class="sxs-lookup"><span data-stu-id="2587d-111">Child Elements</span></span>  

 <span data-ttu-id="2587d-112">なし。</span><span class="sxs-lookup"><span data-stu-id="2587d-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2587d-113">親要素</span><span class="sxs-lookup"><span data-stu-id="2587d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2587d-114">要素</span><span class="sxs-lookup"><span data-stu-id="2587d-114">Element</span></span>|<span data-ttu-id="2587d-115">説明</span><span class="sxs-lookup"><span data-stu-id="2587d-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2587d-116">\<serviceBehaviors> の \<behavior></span><span class="sxs-lookup"><span data-stu-id="2587d-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="2587d-117">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="2587d-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2587d-118">解説</span><span class="sxs-lookup"><span data-stu-id="2587d-118">Remarks</span></span>  

 <span data-ttu-id="2587d-119">サービスの動作構成に追加すると、この構成要素により、ワークフロー サービスの追跡参加要素が構成されます。</span><span class="sxs-lookup"><span data-stu-id="2587d-119">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="2587d-120">追跡参加要素は、ワークフローから生成される追跡データを取得し、それを別のメディアに保存するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2587d-120">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="2587d-121">同様に、追跡レコードの後処理はすべて、追跡参加要素内でも実行できます。</span><span class="sxs-lookup"><span data-stu-id="2587d-121">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2587d-122">例</span><span class="sxs-lookup"><span data-stu-id="2587d-122">Example</span></span>  

 <span data-ttu-id="2587d-123">次の構成例は、Web.config ファイルで構成されている標準の ETW 追跡参加要素を示します。</span><span class="sxs-lookup"><span data-stu-id="2587d-123">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="2587d-124">Etw 追跡参加要素が追跡レコードを ETW に書き込むために使用するプロバイダー Id は、セクションで定義され **\<diagnostics>** ます。</span><span class="sxs-lookup"><span data-stu-id="2587d-124">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="2587d-125">追跡参加要素には、その要素が定期受信した追跡レコードを指定するためのプロファイルが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="2587d-125">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="2587d-126">これは、要素の **profileName** 属性によって定義され **\<add>** ます。</span><span class="sxs-lookup"><span data-stu-id="2587d-126">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="2587d-127">これらが定義されると、サービスの動作に追跡参加要素が追加され **\<etwTracking>** ます。</span><span class="sxs-lookup"><span data-stu-id="2587d-127">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="2587d-128">これにより、選択した追跡参加要素がワークフロー インスタンスの拡張機能に追加され、追跡レコードの受信が開始されます。</span><span class="sxs-lookup"><span data-stu-id="2587d-128">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile"/>
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2587d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="2587d-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="2587d-130">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="2587d-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2587d-131">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="2587d-131">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
