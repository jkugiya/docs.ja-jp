---
description: '詳細情報: Send アクティビティのキャッシュ共有レベルを変更する'
title: Send アクティビティのキャッシュ共有レベルの変更
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 7ced6a8a18779a0c0d5914e63fde658b6d0130ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705214"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="cb35c-103">Send アクティビティのキャッシュ共有レベルの変更</span><span class="sxs-lookup"><span data-stu-id="cb35c-103">Changing the Cache Sharing Levels for Send Activities</span></span>

<span data-ttu-id="cb35c-104"><xref:System.ServiceModel.Activities.SendMessageChannelCache> 拡張機能により、キャッシュ共有レベルのカスタマイズやチャネル ファクトリ キャッシュの設定のカスタマイズを行えるほか、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティを使用してサービス エンドポイントにメッセージを送信するワークフローのチャネル キャッシュの設定のカスタマイズも可能になります。</span><span class="sxs-lookup"><span data-stu-id="cb35c-104">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="cb35c-105">これらのワークフローは、通常はクライアント ワークフローですが、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるワークフロー サービスである場合もあります。</span><span class="sxs-lookup"><span data-stu-id="cb35c-105">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="cb35c-106">チャネル ファクトリ キャッシュには、<xref:System.ServiceModel.ChannelFactory%601> オブジェクトがキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-106">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="cb35c-107">チャネル キャッシュには、チャネルがキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-107">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb35c-108">ワークフローは <xref:System.ServiceModel.Activities.Send> メッセージング アクティビティを使用してメッセージまたはパラメーターを送信できます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-108">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="cb35c-109">このワークフローのランタイムはチャネル ファクトリをキャッシュに追加しますが、チャネル ファクトリで作成されるチャネルは、<xref:System.ServiceModel.Channels.IRequestChannel> アクティビティを <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティと共に使用したときは <xref:System.ServiceModel.Activities.Send> 型で、<xref:System.ServiceModel.Channels.IOutputChannel> アクティビティだけを (<xref:System.ServiceModel.Activities.Send> なしで) 使用したときは <xref:System.ServiceModel.Activities.ReceiveReply> 型です。</span><span class="sxs-lookup"><span data-stu-id="cb35c-109">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="cb35c-110">キャッシュ共有レベル</span><span class="sxs-lookup"><span data-stu-id="cb35c-110">The Cache Sharing Levels</span></span>  

 <span data-ttu-id="cb35c-111">既定では、<xref:System.ServiceModel.WorkflowServiceHost> によってホストされるワークフローにおいて、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティが使用するキャッシュは <xref:System.ServiceModel.WorkflowServiceHost> のすべてのワークフロー インスタンス間で共有されます (ホストレベルのキャッシュ)。</span><span class="sxs-lookup"><span data-stu-id="cb35c-111">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="cb35c-112"><xref:System.ServiceModel.WorkflowServiceHost> によってホストされないクライアント ワークフローの場合、キャッシュを使用できるのはワークフロー インスタンスだけです (インスタンスレベルのキャッシュ)。</span><span class="sxs-lookup"><span data-stu-id="cb35c-112">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="cb35c-113">このキャッシュは、アンセーフ キャッシュが有効になっている場合を除き、構成で定義されているエンドポイントを使用しない <xref:System.ServiceModel.Activities.Send> アクティビティに対してのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="cb35c-113">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="cb35c-114">ワークフローの <xref:System.ServiceModel.Activities.Send> アクティビティに使用可能なさまざまなキャッシュ共有レベルと、推奨される使用方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-114">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="cb35c-115">**ホストレベル**: ホスト共有レベルでは、キャッシュは、ワークフローサービスホストでホストされているワークフローインスタンスでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-115">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="cb35c-116">キャッシュはプロセス全体のキャッシュのワークフロー サービス ホスト間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-116">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="cb35c-117">**インスタンスレベル**: インスタンスの共有レベルでは、特定のワークフローインスタンスが有効期間中はキャッシュを使用できますが、他のワークフローインスタンスはキャッシュを使用できません。</span><span class="sxs-lookup"><span data-stu-id="cb35c-117">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="cb35c-118">**キャッシュなし**: 構成で定義されたエンドポイントを使用するワークフローがある場合、キャッシュは既定でオフになっています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-118">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="cb35c-119">この場合、キャッシュをオンにすると安全性が損なわれることがあるため、オフにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cb35c-119">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="cb35c-120">たとえば、送信ごとに異なる ID (異なる資格情報、または偽装の使用) が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb35c-120">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="cb35c-121">クライアント ワークフローのキャッシュ共有レベルの変更</span><span class="sxs-lookup"><span data-stu-id="cb35c-121">Changing the Cache Sharing Level for a Client Workflow</span></span>  

 <span data-ttu-id="cb35c-122">クライアント ワークフローでのキャッシュの共有を設定するには、<xref:System.ServiceModel.Activities.SendMessageChannelCache> クラスのインスタンスを目的のワークフロー インスタンスのセットに拡張として追加します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-122">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="cb35c-123">この結果、すべてのワークフロー インスタンス間でキャッシュが共有されます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-123">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="cb35c-124">次のコード例は、この手順を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-124">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="cb35c-125">まず、<xref:System.ServiceModel.Activities.SendMessageChannelCache> 型のインスタンスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-125">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="cb35c-126">次に、各クライアント ワークフローのインスタンスにキャッシュ拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-126">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="cb35c-127">ホストされるワークフロー サービスのキャッシュ共有レベルの変更</span><span class="sxs-lookup"><span data-stu-id="cb35c-127">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  

 <span data-ttu-id="cb35c-128">ホストされるワークフロー サービスでのキャッシュの共有を設定するには、<xref:System.ServiceModel.Activities.SendMessageChannelCache> クラスのインスタンスをすべてのワークフロー サービス ホストに拡張として追加します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-128">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="cb35c-129">この結果、すべてのワークフロー サービス ホスト間でキャッシュが共有されます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-129">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="cb35c-130">次のコード例は、この手順を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-130">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="cb35c-131">まず、<xref:System.ServiceModel.Activities.SendMessageChannelCache> 型のインスタンスをクラス レベルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-131">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="cb35c-132">次に、各ワークフロー サービス ホストに静的キャッシュ拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-132">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="cb35c-133">ホストされるワークフロー サービスでのキャッシュ共有をインスタンス レベルに設定するには、`Func<SendMessageChannelCache>` デリゲートをワークフロー サービス ホストに拡張として追加し、<xref:System.ServiceModel.Activities.SendMessageChannelCache> クラスの新しいインスタンスをインスタンス化するコードにこのデリゲートを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-133">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="cb35c-134">この結果、ワークフロー サービス ホストのすべてのワークフロー インスタンスで 1 つのキャッシュが共有されるのではなく、ワークフロー インスタンスごとに異なるキャッシュが使用されます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-134">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="cb35c-135">次のコード例は、このデリゲートがポイントする <xref:System.ServiceModel.Activities.SendMessageChannelCache> 拡張を直接定義するラムダ式を使用して上記の処理を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-135">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```csharp
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="cb35c-136">キャッシュ設定のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="cb35c-136">Customizing Cache Settings</span></span>  

 <span data-ttu-id="cb35c-137">チャネル ファクトリ キャッシュおよびチャネル キャッシュのキャッシュ設定をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-137">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="cb35c-138">キャッシュ設定は <xref:System.ServiceModel.Activities.ChannelCacheSettings> クラスで定義されています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-138">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="cb35c-139">クラスは、 <xref:System.ServiceModel.Activities.SendMessageChannelCache> チャネルファクトリキャッシュの既定のキャッシュ設定と、パラメーターなしのコンストラクターのチャネルキャッシュを定義します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-139">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="cb35c-140">次の表は、これらのキャッシュ設定の既定値をキャッシュのタイプごとに示しています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-140">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="cb35c-141">Settings</span><span class="sxs-lookup"><span data-stu-id="cb35c-141">Settings</span></span>|<span data-ttu-id="cb35c-142">LeaseTimeout (分)</span><span class="sxs-lookup"><span data-stu-id="cb35c-142">LeaseTimeout (min)</span></span>|<span data-ttu-id="cb35c-143">IdleTimeout (分)</span><span class="sxs-lookup"><span data-stu-id="cb35c-143">IdleTimeout (min)</span></span>|<span data-ttu-id="cb35c-144">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="cb35c-144">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="cb35c-145">ファクトリ キャッシュの既定値</span><span class="sxs-lookup"><span data-stu-id="cb35c-145">Factory Cache Default</span></span>|<span data-ttu-id="cb35c-146">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="cb35c-146">TimeSpan.MaxValue</span></span>|<span data-ttu-id="cb35c-147">2</span><span class="sxs-lookup"><span data-stu-id="cb35c-147">2</span></span>|<span data-ttu-id="cb35c-148">16</span><span class="sxs-lookup"><span data-stu-id="cb35c-148">16</span></span>|  
|<span data-ttu-id="cb35c-149">チャネル キャッシュの既定値</span><span class="sxs-lookup"><span data-stu-id="cb35c-149">Channel Cache Default</span></span>|<span data-ttu-id="cb35c-150">5</span><span class="sxs-lookup"><span data-stu-id="cb35c-150">5</span></span>|<span data-ttu-id="cb35c-151">2</span><span class="sxs-lookup"><span data-stu-id="cb35c-151">2</span></span>|<span data-ttu-id="cb35c-152">16</span><span class="sxs-lookup"><span data-stu-id="cb35c-152">16</span></span>|  
  
 <span data-ttu-id="cb35c-153">ファクトリ キャッシュおよびチャネル キャッシュの設定をカスタマイズするには、パラメーター化されたコンストラクター <xref:System.ServiceModel.Activities.SendMessageChannelCache> を使用して <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> クラスをインスタンス化し、<xref:System.ServiceModel.Activities.ChannelCacheSettings> の新しいインスタンスをカスタム値と共に `factorySettings` パラメーターおよび `channelSettings` パラメーターにそれぞれ渡します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-153">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="cb35c-154">次に、このクラスの新しいインスタンスをワークフロー サービス ホストまたはワークフロー インスタンスに拡張として追加します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-154">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="cb35c-155">次のコード例は、ワークフロー インスタンスに対してこの手順を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-155">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(5),
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="cb35c-156">構成で定義されているエンドポイントがワークフロー サービスにある場合にキャッシュを有効にするには、<xref:System.ServiceModel.Activities.SendMessageChannelCache> パラメーターが <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> に設定された、パラメーター化されたコンストラクター `allowUnsafeCaching` を使用して `true` クラスをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-156">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="cb35c-157">次に、このクラスの新しいインスタンスをワークフロー サービス ホストまたはワークフロー インスタンスに拡張として追加します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-157">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="cb35c-158">次のコード例は、ワークフロー インスタンスのキャッシュを有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-158">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="cb35c-159">チャネル ファクトリおよびチャネルのキャッシュを完全に無効にするには、チャネル ファクトリ キャッシュを無効にします。</span><span class="sxs-lookup"><span data-stu-id="cb35c-159">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="cb35c-160">こうすると、対応するチャネル ファクトリにチャネルが所有されるので、チャネル キャッシュもオフになります。</span><span class="sxs-lookup"><span data-stu-id="cb35c-160">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="cb35c-161">チャネル ファクトリ キャッシュを無効にするには、`factorySettings` 値が 0 の <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> インスタンスに初期化された <xref:System.ServiceModel.Activities.ChannelCacheSettings> コンストラクターに <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> パラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-161">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="cb35c-162">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-162">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="cb35c-163">チャネル ファクトリ キャッシュのみを使用し、チャネル キャッシュを無効にするには、`channelSettings` 値が 0 の <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> インスタンスに初期化された <xref:System.ServiceModel.Activities.ChannelCacheSettings> コンストラクターに <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> パラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-163">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="cb35c-164">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-164">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="cb35c-165">ホストされたワークフロー サービスでは、ファクトリ キャッシュとチャネル キャッシュの設定をアプリケーション構成ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-165">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="cb35c-166">これを行うには、ファクトリ キャッシュおよびチャネル キャッシュのキャッシュ設定を含むサービス動作を追加し、そのサービス動作をサービスに追加します。</span><span class="sxs-lookup"><span data-stu-id="cb35c-166">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="cb35c-167">次の例は、 `MyChannelCacheBehavior` カスタムファクトリキャッシュとチャネルキャッシュ設定を使用したサービス動作を含む構成ファイルの内容を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb35c-167">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="cb35c-168">このサービス動作は、属性を通じてサービスに追加され `behaviorConfiguration` ます。</span><span class="sxs-lookup"><span data-stu-id="cb35c-168">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
