---
description: '詳細については、「方法: 探索プロキシを実装する」を参照してください。'
title: '方法: 探索プロキシを実装する'
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: e7bd9833ac0d449eefd5e439b442ecb0eee121ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793754"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="3d512-103">方法: 探索プロキシを実装する</span><span class="sxs-lookup"><span data-stu-id="3d512-103">How to: Implement a Discovery Proxy</span></span>

<span data-ttu-id="3d512-104">このトピックでは、探索プロキシの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3d512-104">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="3d512-105">Windows Communication Foundation (WCF) の検出機能の詳細については、「 [Wcf discovery の概要](wcf-discovery-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d512-105">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span> <span data-ttu-id="3d512-106">探索プロキシを実装するには、抽象クラス <xref:System.ServiceModel.Discovery.DiscoveryProxy> を拡張するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d512-106">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="3d512-107">このサンプルでは、他の多くのサポート クラスも定義され、使用されています。</span><span class="sxs-lookup"><span data-stu-id="3d512-107">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="3d512-108">`OnResolveAsyncResult`、 `OnFindAsyncResult`、および `AsyncResult`。</span><span class="sxs-lookup"><span data-stu-id="3d512-108">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="3d512-109">これらのクラスは、<xref:System.IAsyncResult> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="3d512-109">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="3d512-110">詳細については、 <xref:System.IAsyncResult> 「system.servicemodel [インターフェイス](xref:System.IAsyncResult)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d512-110">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="3d512-111">このトピックでは、探索プロキシの実装を 3 つの主要な部分に分けて説明します。</span><span class="sxs-lookup"><span data-stu-id="3d512-111">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

- <span data-ttu-id="3d512-112">データ ストアを含み、抽象クラス <xref:System.ServiceModel.Discovery.DiscoveryProxy> を拡張するクラスを定義する。</span><span class="sxs-lookup"><span data-stu-id="3d512-112">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

- <span data-ttu-id="3d512-113">ヘルパー クラス `AsyncResult` を実装する。</span><span class="sxs-lookup"><span data-stu-id="3d512-113">Implement the helper `AsyncResult` class.</span></span>

- <span data-ttu-id="3d512-114">探索プロキシをホストする。</span><span class="sxs-lookup"><span data-stu-id="3d512-114">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="3d512-115">新しいコンソール アプリケーション プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="3d512-115">To create a new console application project</span></span>

1. <span data-ttu-id="3d512-116">Visual Studio 2012 を起動します。</span><span class="sxs-lookup"><span data-stu-id="3d512-116">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="3d512-117">新しいコンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d512-117">Create a new console application project.</span></span> <span data-ttu-id="3d512-118">プロジェクトに「`DiscoveryProxy`」という名前を付け、ソリューションに「`DiscoveryProxyExample`」という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="3d512-118">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="3d512-119">プロジェクトに次の参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-119">Add the following references to the project</span></span>

    1. <span data-ttu-id="3d512-120">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="3d512-120">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="3d512-121">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="3d512-121">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    > <span data-ttu-id="3d512-122">必ず、これらのアセンブリのバージョン 4.0 以降を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d512-122">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="3d512-123">ProxyDiscoveryService クラスを実装するには</span><span class="sxs-lookup"><span data-stu-id="3d512-123">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="3d512-124">新しいコード ファイルをプロジェクトに追加し、DiscoveryProxy.cs という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="3d512-124">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="3d512-125">次の `using` ステートメントを DiscoveryProxy.cs に追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-125">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="3d512-126">`DiscoveryProxyService` から <xref:System.ServiceModel.Discovery.DiscoveryProxy> を派生させます。</span><span class="sxs-lookup"><span data-stu-id="3d512-126">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="3d512-127">下の例に示すように、`ServiceBehavior` 属性をクラスに適用します。</span><span class="sxs-lookup"><span data-stu-id="3d512-127">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```csharp
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="3d512-128">`DiscoveryProxy` クラス内で、登録済みサービスを保持するディクショナリを定義します。</span><span class="sxs-lookup"><span data-stu-id="3d512-128">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```csharp
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="3d512-129">ディクショナリを初期化するコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="3d512-129">Define a constructor that initializes the dictionary.</span></span>

    ```csharp
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="3d512-130">探索プロキシ キャッシュの更新に使用するメソッドを定義するには</span><span class="sxs-lookup"><span data-stu-id="3d512-130">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="3d512-131">`AddOnlineservice` メソッドを実装して、サービスをキャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-131">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="3d512-132">これは、プロキシがアナウンス メッセージを受け取るたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-132">This is called every time the proxy receives an announcement message.</span></span>

    ```csharp
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        lock (this.onlineServices)
        {
            this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
        }

        PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
    }
    ```

2. <span data-ttu-id="3d512-133">キャッシュからサービスを削除するのに使用する `RemoveOnlineService` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="3d512-133">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```csharp
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        if (endpointDiscoveryMetadata != null)
        {
            lock (this.onlineServices)
            {
                this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
        }
    }
    ```

3. <span data-ttu-id="3d512-134">サービスをディクショナリ内のサービスと照合する、`MatchFromOnlineService` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="3d512-134">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```csharp
    void MatchFromOnlineService(FindRequestContext findRequestContext)
    {
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                {
                    findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                }
            }
        }
    }
    ```

    ```csharp
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
    {
        EndpointDiscoveryMetadata matchingEndpoint = null;
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (criteria.Address == endpointDiscoveryMetadata.Address)
                {
                    matchingEndpoint = endpointDiscoveryMetadata;
                }
            }
        }
        return matchingEndpoint;
    }
    ```

4. <span data-ttu-id="3d512-135">探索プロキシの処理に関するコンソール テキスト出力をユーザーに提供する、`PrintDiscoveryMetadata` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="3d512-135">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```csharp
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
    {
        Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
        foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
        {
            Console.WriteLine("** " + contractName.ToString());
            break;
        }
        Console.WriteLine("**** Operation Completed");
    }
    ```

5. <span data-ttu-id="3d512-136">次の AsyncResult クラスを DiscoveryProxyService に追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-136">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="3d512-137">これらのクラスは、非同期操作の各結果を区別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-137">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```csharp
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
    {
        public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
    {
        public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnFindAsyncResult : AsyncResult
    {
        public OnFindAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnFindAsyncResult>(result);
        }
    }

    sealed class OnResolveAsyncResult : AsyncResult
    {
        EndpointDiscoveryMetadata matchingEndpoint;

        public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.matchingEndpoint = matchingEndpoint;
            this.Complete(true);
        }

        public static EndpointDiscoveryMetadata End(IAsyncResult result)
        {
            OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
            return thisPtr.matchingEndpoint;
        }
    }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="3d512-138">探索プロキシ機能を実装するメソッドを定義するには</span><span class="sxs-lookup"><span data-stu-id="3d512-138">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="3d512-139"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d512-139">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d512-140">このメソッドは、探索プロキシがオンライン アナウンス メッセージを受け取ると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-140">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```csharp
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
    protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.AddOnlineService(endpointDiscoveryMetadata);
        return new OnOnlineAnnouncementAsyncResult(callback, state);
    }
    ```

2. <span data-ttu-id="3d512-141"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d512-141">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d512-142">このメソッドは、探索プロキシがアナウンス メッセージの処理を終了すると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-142">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```csharp
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
    {
        OnOnlineAnnouncementAsyncResult.End(result);
    }
    ```

3. <span data-ttu-id="3d512-143"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d512-143">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d512-144">このメソッドは、探索プロキシがオフライン アナウンス メッセージを受け取ると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-144">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```csharp
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
    protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.RemoveOnlineService(endpointDiscoveryMetadata);
        return new OnOfflineAnnouncementAsyncResult(callback, state);
    }
    ```

4. <span data-ttu-id="3d512-145"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d512-145">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d512-146">このメソッドは、探索プロキシがオフライン アナウンス メッセージの処理を終了すると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-146">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```csharp
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
    {
        OnOfflineAnnouncementAsyncResult.End(result);
    }
    ```

5. <span data-ttu-id="3d512-147"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d512-147">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d512-148">このメソッドは、探索プロキシが検索要求を受け取ると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-148">This method is called when the discovery proxy receives a find request.</span></span>

    ```csharp
    // OnBeginFind method is called when a Probe request message is received by the Proxy
    protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
    {
        this.MatchFromOnlineService(findRequestContext);
        return new OnFindAsyncResult(callback, state);
    }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="3d512-149"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d512-149">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d512-150">このメソッドは、探索プロキシが検索要求の処理を終了すると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-150">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```csharp
    protected override void OnEndFind(IAsyncResult result)
    {
        OnFindAsyncResult.End(result);
    }
    ```

7. <span data-ttu-id="3d512-151"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d512-151">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d512-152">このメソッドは、探索プロキシが解決メッセージを受け取ると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-152">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```csharp
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
    protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
    }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="3d512-153"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d512-153">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d512-154">このメソッドは、探索プロキシが解決メッセージの処理を終了すると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-154">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```csharp
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

<span data-ttu-id="3d512-155">OnBegin.</span><span class="sxs-lookup"><span data-stu-id="3d512-155">The OnBegin..</span></span> <span data-ttu-id="3d512-156">/ OnEnd.</span><span class="sxs-lookup"><span data-stu-id="3d512-156">/ OnEnd..</span></span> <span data-ttu-id="3d512-157"> メソッドは、以降の探索操作のロジックを提供します。</span><span class="sxs-lookup"><span data-stu-id="3d512-157">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="3d512-158">たとえば、<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> メソッドおよび <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> メソッドは、探索プロキシの検索ロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="3d512-158">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="3d512-159">探索プロキシがプローブ メッセージを受け取ると、これらのメソッドが実行されて、クライアントに応答が返されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-159">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="3d512-160">必要に応じて、検索ロジックを変更できます。たとえば、アルゴリズムによるカスタム スコープ一致や、検索操作の一環として解析するアプリケーション固有の XML メタデータを組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="3d512-160">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="3d512-161">AsyncResult クラスを実装するには</span><span class="sxs-lookup"><span data-stu-id="3d512-161">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="3d512-162">各種の非同期結果クラスを派生させるために使用する抽象基本クラス AsyncResult を定義します。</span><span class="sxs-lookup"><span data-stu-id="3d512-162">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="3d512-163">AsyncResult.cs という名前の新しいコード ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d512-163">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="3d512-164">次の `using` ステートメントを AsyncResult.cs に追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-164">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```csharp
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="3d512-165">次の AsyncResult クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-165">Add the following AsyncResult class.</span></span>

    ```csharp
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="3d512-166">DiscoveryProxy をホストするには</span><span class="sxs-lookup"><span data-stu-id="3d512-166">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="3d512-167">DiscoveryProxyExample プロジェクトで Program.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3d512-167">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="3d512-168">次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-168">Add the following `using` statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="3d512-169">`Main()` メソッド内に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-169">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="3d512-170">これにより、`DiscoveryProxy` クラスのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3d512-170">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```csharp
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Host the DiscoveryProxy service
    ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="3d512-171">次に、探索エンドポイントとアナウンス エンドポイントを追加する、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3d512-171">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```csharp
    try
    {
        // Add DiscoveryEndpoint to receive Probe and Resolve messages
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
        discoveryEndpoint.IsSystemEndpoint = false;

        // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

        proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
        proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

        proxyServiceHost.Open();

        Console.WriteLine("Proxy Service started.");
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        proxyServiceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (proxyServiceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        proxyServiceHost.Abort();
    }
    ```

<span data-ttu-id="3d512-172">これで、探索プロキシの実装が完了しました。</span><span class="sxs-lookup"><span data-stu-id="3d512-172">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="3d512-173">[「方法: 探索プロキシに登録する探索可能なサービスを実装](discoverable-service-that-registers-with-the-discovery-proxy.md)する」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="3d512-173">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="3d512-174">例</span><span class="sxs-lookup"><span data-stu-id="3d512-174">Example</span></span>

<span data-ttu-id="3d512-175">このトピックで使用するコード全体の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d512-175">This is the full listing of the code used in this topic.</span></span>

```csharp
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```csharp
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```csharp
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="3d512-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d512-176">See also</span></span>

- [<span data-ttu-id="3d512-177">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="3d512-177">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="3d512-178">方法: 探索プロキシで登録される探索可能なサービスの実装する</span><span class="sxs-lookup"><span data-stu-id="3d512-178">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="3d512-179">方法: 探索プロキシを使用してサービスを検索するクライアント アプリケーションを実装する</span><span class="sxs-lookup"><span data-stu-id="3d512-179">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="3d512-180">方法: 探索プロキシをテストする</span><span class="sxs-lookup"><span data-stu-id="3d512-180">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)
