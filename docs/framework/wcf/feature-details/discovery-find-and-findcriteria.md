---
description: '詳細情報: 検出検索と FindCriteria'
title: 探索検索と FindCriteria
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: 3a4428a89ba4122f528d1c01e4b5a6b8ea8d2935
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756319"
---
# <a name="discovery-find-and-findcriteria"></a><span data-ttu-id="f800d-103">探索検索と FindCriteria</span><span class="sxs-lookup"><span data-stu-id="f800d-103">Discovery Find and FindCriteria</span></span>

<span data-ttu-id="f800d-104">探索検索操作は、1 つ以上のサービスを探索するためにクライアントによって開始される操作であり、探索における主要なアクションの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f800d-104">A discovery find operation is initiated by a client to discover one or more services and is one of the main actions in discovery.</span></span> <span data-ttu-id="f800d-105">検索を実行すると、WS-Discovery Probe メッセージがネットワークを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="f800d-105">Performing a find sends a WS-Discovery Probe message over the network.</span></span> <span data-ttu-id="f800d-106">指定された条件に一致するサービスは、WS-Discovery ProbeMatch メッセージを使用して応答します。</span><span class="sxs-lookup"><span data-stu-id="f800d-106">Services that match the criteria specified reply with WS-Discovery ProbeMatch messages.</span></span> <span data-ttu-id="f800d-107">探索メッセージの詳細については、「 [ws-management 仕様](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f800d-107">For more information about discovery messages, see the [WS-Discovery specification](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).</span></span>

## <a name="discoveryclient"></a><span data-ttu-id="f800d-108">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="f800d-108">DiscoveryClient</span></span>

<span data-ttu-id="f800d-109"><xref:System.ServiceModel.Discovery.DiscoveryClient> クラスは、検索操作を実行するメカニズムを提供し、探索クライアントの操作を簡単に実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f800d-109">The <xref:System.ServiceModel.Discovery.DiscoveryClient> class provides the mechanism to perform find operations and makes performing discovery client operations easy.</span></span> <span data-ttu-id="f800d-110">このクラスには、(ブロックする) 同期検索を実行する <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> メソッドと、ブロックしない非同期検索を実行する <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f800d-110">It contains a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method, which performs a (blocking) synchronous find, and a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method, which initiates a non-blocking asynchronous find.</span></span> <span data-ttu-id="f800d-111">どちらのメソッドも <xref:System.ServiceModel.Discovery.FindCriteria> パラメーターを使用し、<xref:System.ServiceModel.Discovery.FindResponse> オブジェクトを介してユーザーに結果を提供します。</span><span class="sxs-lookup"><span data-stu-id="f800d-111">Both methods take a <xref:System.ServiceModel.Discovery.FindCriteria> parameter, and provide results to the user through a <xref:System.ServiceModel.Discovery.FindResponse> object.</span></span>

## <a name="findcriteria"></a><span data-ttu-id="f800d-112">FindCriteria</span><span class="sxs-lookup"><span data-stu-id="f800d-112">FindCriteria</span></span>

<span data-ttu-id="f800d-113"><xref:System.ServiceModel.Discovery.FindCriteria> にはいくつかのプロパティがあり、検索対象のサービスを指定する検索条件と、検索を続行する期間を指定する検索終了条件に分類できます。</span><span class="sxs-lookup"><span data-stu-id="f800d-113"><xref:System.ServiceModel.Discovery.FindCriteria> has several properties, which can be grouped into search criteria, which specify what services you are looking for, and find termination criteria (how long the search should last).</span></span> <span data-ttu-id="f800d-114"><xref:System.ServiceModel.Discovery.FindCriteria> には、複数の検索条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f800d-114">A <xref:System.ServiceModel.Discovery.FindCriteria> can contain multiple search criteria.</span></span> <span data-ttu-id="f800d-115">既定では、サービスがすべての条件に一致する必要があり、そうでない場合は、サービスがそれ自体を一致サービスと見なしません。</span><span class="sxs-lookup"><span data-stu-id="f800d-115">By default, the service has to match all of the components otherwise it does not consider itself a matching service.</span></span> <span data-ttu-id="f800d-116">条件の一部にのみ一致するサービスを検索する場合は、サービスにカスタムの検索ロジックを実装するか、複数のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="f800d-116">If you want to find services that only match some of the criteria, you can implement custom find logic on the service or you can use multiple queries.</span></span>

<span data-ttu-id="f800d-117">検索条件は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f800d-117">Search criteria include:</span></span>

- <span data-ttu-id="f800d-118"><xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> - 省略できます。</span><span class="sxs-lookup"><span data-stu-id="f800d-118"><xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> - Optional.</span></span> <span data-ttu-id="f800d-119">検索対象のサービスのコントラクト名、およびサービスの検索に通常使用される条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="f800d-119">The contract name of the service being searched for and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="f800d-120">複数のコントラクト名が指定されると、すべてのコントラクトに一致するサービス エンドポイントのみが応答します。</span><span class="sxs-lookup"><span data-stu-id="f800d-120">If more than one contract name is specified, only service endpoints matching ALL contracts reply.</span></span> <span data-ttu-id="f800d-121">WCF では、エンドポイントは1つのコントラクトしかサポートできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f800d-121">Note that in WCF an endpoint can only support one contract.</span></span>

- <span data-ttu-id="f800d-122"><xref:System.ServiceModel.Discovery.Configuration.ScopeElement> - 省略できます。</span><span class="sxs-lookup"><span data-stu-id="f800d-122"><xref:System.ServiceModel.Discovery.Configuration.ScopeElement> - Optional.</span></span> <span data-ttu-id="f800d-123">Scopes は、個々のサービス エンドポイントの分類に使用される絶対 URI です。</span><span class="sxs-lookup"><span data-stu-id="f800d-123">Scopes are absolute URIs that are used to categorize individual service endpoints.</span></span> <span data-ttu-id="f800d-124">複数のエンドポイントが同じコントラクトを公開し、これらのエンドポイントのサブセットを検索する手段が必要な場合は、これを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f800d-124">You may want to use this in scenarios where multiple endpoints expose the same contract and you want a way to search for a subset of the endpoints.</span></span> <span data-ttu-id="f800d-125">複数のスコープが指定されると、すべてのスコープに一致するサービス エンドポイントのみが応答します。</span><span class="sxs-lookup"><span data-stu-id="f800d-125">If more than one scope is specified, only service endpoints matching ALL scopes reply.</span></span>

- <span data-ttu-id="f800d-126"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> - Probe メッセージのスコープとエンドポイントのスコープとの一致の判定に使用する、一致アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="f800d-126"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> - Specifies the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span> <span data-ttu-id="f800d-127">サポートされているスコープ一致規則は、次の 5 つです。</span><span class="sxs-lookup"><span data-stu-id="f800d-127">There are five supported scope-matching rules:</span></span>

  - <span data-ttu-id="f800d-128"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>: 大文字と小文字が区別される基本の文字列比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="f800d-128"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> does a basic case-sensitive string comparison.</span></span>

  - <span data-ttu-id="f800d-129"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> "/" で区切られたセグメントで一致します。</span><span class="sxs-lookup"><span data-stu-id="f800d-129"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> matches by segments separated by "/".</span></span> <span data-ttu-id="f800d-130">の検索は、 `http://contoso/building1` スコープを持つサービスと一致 `http://contoso/building/floor1` します。</span><span class="sxs-lookup"><span data-stu-id="f800d-130">A search for `http://contoso/building1` matches a service with scope `http://contoso/building/floor1`.</span></span> <span data-ttu-id="f800d-131">`http://contoso/building100`最後の2つのセグメントが一致しないため、一致しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f800d-131">Note that it does not match `http://contoso/building100` because the last two segments do not match.</span></span>

  - <span data-ttu-id="f800d-132"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>: LDAP URL を使用してセグメント単位でスコープの一致を判定します。</span><span class="sxs-lookup"><span data-stu-id="f800d-132"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> matches scopes by segments using an LDAP URL.</span></span>

  - <span data-ttu-id="f800d-133"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>: UUID 文字列を使用して、スコープが完全に一致するかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="f800d-133"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> matches scopes exactly using a UUID string.</span></span>

  - <span data-ttu-id="f800d-134"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType>: スコープを指定していないサービスのみを対象に一致を判定します。</span><span class="sxs-lookup"><span data-stu-id="f800d-134"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> matches only those services that do not specify a scope.</span></span>

  <span data-ttu-id="f800d-135">スコープ一致規則が指定されていない場合は、<xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f800d-135">If a scope-matching rule is not specified, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> is used.</span></span>

<span data-ttu-id="f800d-136">終了条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f800d-136">Termination criteria include:</span></span>

1. <span data-ttu-id="f800d-137"><xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> - ネットワーク上でサービスからの応答を待機する最長時間。</span><span class="sxs-lookup"><span data-stu-id="f800d-137"><xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> - The maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="f800d-138">既定の時間は 20 秒です。</span><span class="sxs-lookup"><span data-stu-id="f800d-138">The default duration is 20 seconds.</span></span>

2. <span data-ttu-id="f800d-139"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> - 待機する応答の最大件数。</span><span class="sxs-lookup"><span data-stu-id="f800d-139"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> - The maximum number of replies to wait for.</span></span> <span data-ttu-id="f800d-140"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> が経過する前に <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 応答が受信された場合は、検出操作が終了します。</span><span class="sxs-lookup"><span data-stu-id="f800d-140">If <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> replies are received before <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed, the find operation ends.</span></span>

## <a name="findresponse"></a><span data-ttu-id="f800d-141">FindResponse</span><span class="sxs-lookup"><span data-stu-id="f800d-141">FindResponse</span></span>

<span data-ttu-id="f800d-142"><xref:System.ServiceModel.Discovery.FindResponse> には、ネットワーク上で一致するサービスから送信された応答を保持する <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> コレクション プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="f800d-142"><xref:System.ServiceModel.Discovery.FindResponse> has an <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> collection property that contains any replies sent by matching services on the network.</span></span> <span data-ttu-id="f800d-143">応答したサービスがない場合、このコレクションは空です。</span><span class="sxs-lookup"><span data-stu-id="f800d-143">If no services replied, the collection is empty.</span></span> <span data-ttu-id="f800d-144">1 つ以上のサービスが応答した場合、各応答は <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> オブジェクトに格納されます。これには、アドレスやコントラクトなど、サービスについての追加情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f800d-144">If one or more services replied, each reply is stored in an <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> object, which contains the address, contract, and some additional information about the service.</span></span>

<span data-ttu-id="f800d-145">次の例は、コードで検索操作を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f800d-145">The following example shows how to perform a find operation in code.</span></span>

```csharp
// Create DiscoveryClient
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());

// Create FindCriteria
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));
findCriteria.Duration = TimeSpan.FromSeconds(10);

// Find ICalculatorService endpoints
FindResponse findResponse = discoveryClient.Find(findCriteria);

Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)
```

## <a name="see-also"></a><span data-ttu-id="f800d-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="f800d-146">See also</span></span>

- [<span data-ttu-id="f800d-147">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="f800d-147">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="f800d-148">探索クライアント チャネルの使用</span><span class="sxs-lookup"><span data-stu-id="f800d-148">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
- [<span data-ttu-id="f800d-149">スコープを使用した探索</span><span class="sxs-lookup"><span data-stu-id="f800d-149">Discovery with Scopes</span></span>](../samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="f800d-150">Basic</span><span class="sxs-lookup"><span data-stu-id="f800d-150">Basic</span></span>](../samples/basic-sample.md)
