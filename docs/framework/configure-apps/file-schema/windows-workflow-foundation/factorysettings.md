---
description: '詳細情報: <factorySettings>'
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: 766e68bbf2a48725b2603221bfbbcd25b0a83acb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795067"
---
# \<factorySettings>

<span data-ttu-id="408f5-102">チャネル ファクトリ キャッシュの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="408f5-102">Specifies the settings of the channel factory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<factorySettings>**  
  
## <a name="syntax"></a><span data-ttu-id="408f5-103">構文</span><span class="sxs-lookup"><span data-stu-id="408f5-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="408f5-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="408f5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="408f5-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="408f5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="408f5-106">属性</span><span class="sxs-lookup"><span data-stu-id="408f5-106">Attributes</span></span>  
  
|<span data-ttu-id="408f5-107">属性</span><span class="sxs-lookup"><span data-stu-id="408f5-107">Attribute</span></span>|<span data-ttu-id="408f5-108">説明</span><span class="sxs-lookup"><span data-stu-id="408f5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="408f5-109">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="408f5-109">idleTimeout</span></span>|<span data-ttu-id="408f5-110">オブジェクトが破棄されるまでにキャッシュ内でアイドル状態を維持できる最大時間を指定する TimeSpan 値。</span><span class="sxs-lookup"><span data-stu-id="408f5-110">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="408f5-111">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="408f5-111">leaseTimeout</span></span>|<span data-ttu-id="408f5-112">オブジェクトがキャッシュから削除されるまでの時間間隔を指定する TimeSpan 値。</span><span class="sxs-lookup"><span data-stu-id="408f5-112">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="408f5-113">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="408f5-113">maxItemsInCache</span></span>|<span data-ttu-id="408f5-114">キャッシュに置くことができるオブジェクトの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="408f5-114">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="408f5-115">子要素</span><span class="sxs-lookup"><span data-stu-id="408f5-115">Child Elements</span></span>  

 <span data-ttu-id="408f5-116">なし。</span><span class="sxs-lookup"><span data-stu-id="408f5-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="408f5-117">親要素</span><span class="sxs-lookup"><span data-stu-id="408f5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="408f5-118">要素</span><span class="sxs-lookup"><span data-stu-id="408f5-118">Element</span></span>|<span data-ttu-id="408f5-119">説明</span><span class="sxs-lookup"><span data-stu-id="408f5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="408f5-120">キャッシュの共有レベルのカスタマイズや、チャネル ファクトリ キャッシュの設定を可能にするほか、Send メッセージング アクティビティを使用してサービス エンドポイントにメッセージを送信するワークフローのチャネル キャッシュの設定も可能にするサービス動作。</span><span class="sxs-lookup"><span data-stu-id="408f5-120">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="408f5-121">解説</span><span class="sxs-lookup"><span data-stu-id="408f5-121">Remarks</span></span>  

 <span data-ttu-id="408f5-122">このサービス動作は、サービス エンドポイントにメッセージを送信するワークフローを対象としています。</span><span class="sxs-lookup"><span data-stu-id="408f5-122">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="408f5-123">これらのワークフローは、通常はクライアント ワークフローですが、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるワークフロー サービスである場合もあります。</span><span class="sxs-lookup"><span data-stu-id="408f5-123">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="408f5-124">既定では、<xref:System.ServiceModel.WorkflowServiceHost> によってホストされるワークフローでは、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティが使用するキャッシュは <xref:System.ServiceModel.WorkflowServiceHost> のすべてのワークフロー インスタンス間で共有されます (ホストレベルのキャッシュ)。</span><span class="sxs-lookup"><span data-stu-id="408f5-124">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="408f5-125"><xref:System.ServiceModel.WorkflowServiceHost> によってホストされないクライアント ワークフローの場合、キャッシュを使用できるのはワークフロー インスタンスだけです (インスタンスレベルのキャッシュ)。</span><span class="sxs-lookup"><span data-stu-id="408f5-125">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="408f5-126">構成でエンドポイントが定義されているワークフローに送信アクティビティがある場合、キャッシュは既定で無効になります。</span><span class="sxs-lookup"><span data-stu-id="408f5-126">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="408f5-127">チャネルファクトリおよびチャネルキャッシュの既定のキャッシュ共有レベルとキャッシュ設定を変更する方法の詳細については、「 [Send アクティビティのキャッシュ共有レベルの変更](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="408f5-127">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="408f5-128">例</span><span class="sxs-lookup"><span data-stu-id="408f5-128">Example</span></span>  

 <span data-ttu-id="408f5-129">ホストされたワークフロー サービスでは、ファクトリ キャッシュとチャネル キャッシュの設定をアプリケーション構成ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="408f5-129">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="408f5-130">これを行うには、ファクトリ キャッシュおよびチャネル キャッシュのキャッシュ設定を含むサービス動作を追加し、そのサービス動作をサービスに追加します。</span><span class="sxs-lookup"><span data-stu-id="408f5-130">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="408f5-131">次の例は、 `MyChannelCacheBehavior` カスタムファクトリキャッシュとチャネルキャッシュ設定を使用したサービス動作を含む構成ファイルの内容を示しています。</span><span class="sxs-lookup"><span data-stu-id="408f5-131">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="408f5-132">このサービス動作は、属性を通じてサービスに追加され `behaviorConfiguration` ます。</span><span class="sxs-lookup"><span data-stu-id="408f5-132">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="408f5-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="408f5-133">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="408f5-134">Send アクティビティのキャッシュ共有レベルの変更</span><span class="sxs-lookup"><span data-stu-id="408f5-134">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
