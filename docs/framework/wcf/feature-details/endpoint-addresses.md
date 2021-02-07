---
description: '詳細情報: エンドポイントアドレス'
title: エンドポイント アドレス
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: 009b34a3931bda3b16c9079316b97ea2f1680ffb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704785"
---
# <a name="endpoint-addresses"></a><span data-ttu-id="9dc9a-103">エンドポイント アドレス</span><span class="sxs-lookup"><span data-stu-id="9dc9a-103">Endpoint Addresses</span></span>

<span data-ttu-id="9dc9a-104">すべてのエンドポイントにはこれと関連するアドレスがあり、エンドポイントの検索と識別に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-104">Every endpoint has an address associated with it, which is used to locate and identify the endpoint.</span></span> <span data-ttu-id="9dc9a-105">このアドレスは主にエンドポイントの位置を指定する URI (Uniform Resource Identifier) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-105">This address consists primarily of a Uniform Resource Identifier (URI), which specifies the location of the endpoint.</span></span> <span data-ttu-id="9dc9a-106">エンドポイントアドレスは、Windows Communication Foundation (WCF) プログラミングモデルでクラスによって表されます。これには、 <xref:System.ServiceModel.EndpointAddress> <xref:System.ServiceModel.EndpointAddress.Identity%2A> メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にするオプションのプロパティと、 <xref:System.ServiceModel.EndpointAddress.Headers%2A> サービスに接続するために必要な他の SOAP ヘッダーを定義するオプションのプロパティのセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-106">The endpoint address is represented in the Windows Communication Foundation (WCF) programming model by the <xref:System.ServiceModel.EndpointAddress> class, which contains an optional <xref:System.ServiceModel.EndpointAddress.Identity%2A> property that enables the authentication of the endpoint by other endpoints that exchange messages with it, and a set of optional <xref:System.ServiceModel.EndpointAddress.Headers%2A> properties, which define any other SOAP headers required to reach the service.</span></span> <span data-ttu-id="9dc9a-107">オプションのヘッダーは、サービス エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-107">The optional headers provide additional and more detailed addressing information to identify or interact with the service endpoint.</span></span> <span data-ttu-id="9dc9a-108">エンドポイントのアドレスは、ネットワーク上では WS-Addressing エンドポイント参照 (EPR) として表されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-108">The address of an endpoint is represented on the wire as a WS-Addressing endpoint reference (EPR).</span></span>  
  
## <a name="uri-structure-of-an-address"></a><span data-ttu-id="9dc9a-109">アドレスの URI 構造</span><span class="sxs-lookup"><span data-stu-id="9dc9a-109">URI Structure of an Address</span></span>  

 <span data-ttu-id="9dc9a-110">ほとんどのトランスポートの URI アドレスは、4 つの部分から構成されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-110">The address URI for most transports has four parts.</span></span> <span data-ttu-id="9dc9a-111">たとえば、URI の4つの部分は次のようにまとめ `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` られています。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-111">For example, the four parts of the URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` can be itemized as follows:</span></span>  
  
- <span data-ttu-id="9dc9a-112">スキーム: `http:`</span><span class="sxs-lookup"><span data-stu-id="9dc9a-112">Scheme: `http:`</span></span>
  
- <span data-ttu-id="9dc9a-113">装置 `www.fabrikam.com`</span><span class="sxs-lookup"><span data-stu-id="9dc9a-113">Machine: `www.fabrikam.com`</span></span>  
  
- <span data-ttu-id="9dc9a-114">(省略可能) ポート : 322</span><span class="sxs-lookup"><span data-stu-id="9dc9a-114">(optional) Port: 322</span></span>  
  
- <span data-ttu-id="9dc9a-115">パス : /mathservice.svc/secureEndpoint</span><span class="sxs-lookup"><span data-stu-id="9dc9a-115">Path: /mathservice.svc/secureEndpoint</span></span>  
  
## <a name="defining-an-address-for-a-service"></a><span data-ttu-id="9dc9a-116">サービスのアドレスの定義</span><span class="sxs-lookup"><span data-stu-id="9dc9a-116">Defining an Address for a Service</span></span>  

 <span data-ttu-id="9dc9a-117">サービスのエンドポイント アドレスは、コードを使用して命令的に、または構成を通じて宣言的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-117">The endpoint address for a service can be specified either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="9dc9a-118">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-118">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="9dc9a-119">一般に、サービス エンドポイントの定義にはコードではなく、構成を使用する方がより実用的です。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-119">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="9dc9a-120">バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-120">Keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
### <a name="defining-an-address-in-configuration"></a><span data-ttu-id="9dc9a-121">構成によるアドレス定義</span><span class="sxs-lookup"><span data-stu-id="9dc9a-121">Defining an Address in Configuration</span></span>  

 <span data-ttu-id="9dc9a-122">構成ファイルでエンドポイントを定義するには、要素を使用し [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-122">To define an endpoint in a configuration file, use the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="9dc9a-123">詳細と例については、「 [エンドポイントアドレスの指定](../specifying-an-endpoint-address.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-123">For details and an example, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>  
  
### <a name="defining-an-address-in-code"></a><span data-ttu-id="9dc9a-124">コードによるアドレス定義</span><span class="sxs-lookup"><span data-stu-id="9dc9a-124">Defining an Address in Code</span></span>  

 <span data-ttu-id="9dc9a-125">エンドポイント アドレスは、コードで <xref:System.ServiceModel.EndpointAddress> クラスを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-125">An endpoint address can be created in code with the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="9dc9a-126">詳細と例については、「 [エンドポイントアドレスの指定](../specifying-an-endpoint-address.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-126">For details and an example, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>  
  
### <a name="endpoints-in-wsdl"></a><span data-ttu-id="9dc9a-127">WSDL のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="9dc9a-127">Endpoints in WSDL</span></span>  

 <span data-ttu-id="9dc9a-128">エンドポイント アドレスは、対応するエンドポイントの `wsdl:port` 要素内の WS-Addressing EPR 要素として WSDL で表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-128">An endpoint address can also be represented in WSDL as a WS-Addressing EPR element inside the corresponding endpoint's `wsdl:port` element.</span></span> <span data-ttu-id="9dc9a-129">EPR には、エンドポイントのアドレスのほかに、アドレスのすべてのプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-129">The EPR contains the endpoint's address as well as any address properties.</span></span> <span data-ttu-id="9dc9a-130">詳細と例については、「 [エンドポイントアドレスの指定](../specifying-an-endpoint-address.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-130">For details and an example, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a><span data-ttu-id="9dc9a-131">.NET Framework 3.5 での複数の IIS バインディングのサポート</span><span class="sxs-lookup"><span data-stu-id="9dc9a-131">Multiple IIS Binding Support in .NET Framework 3.5</span></span>  

 <span data-ttu-id="9dc9a-132">インターネット サービス プロバイダーは、多くの場合、サイトの密度を高めて総所有コストを抑えるため、同じサーバーまたはサイト上で複数のアプリケーションをホストしています。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-132">Internet service providers often host many applications on the same server and site to increase the site density and lower total cost of ownership.</span></span> <span data-ttu-id="9dc9a-133">通常、これらのアプリケーションは、異なるベース アドレスにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-133">These applications are typically bound to different base addresses.</span></span> <span data-ttu-id="9dc9a-134">インターネット インフォメーション サービス (IIS) Web サイトは、複数のアプリケーションを格納できます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-134">An Internet Information Services (IIS) Web site can contain multiple applications.</span></span> <span data-ttu-id="9dc9a-135">サイト内のアプリケーションに、1 つ以上の IIS バインディングからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-135">The applications in a site can be accessed through one or more IIS bindings.</span></span>  
  
 <span data-ttu-id="9dc9a-136">IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-136">IIS bindings provide two pieces of information: a binding protocol, and binding information.</span></span> <span data-ttu-id="9dc9a-137">バインディング プロトコルは通信を行うスキームを定義するもので、バインディング情報はサイトにアクセスするために使用する情報です。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-137">The binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span>  
  
 <span data-ttu-id="9dc9a-138">IIS バインディングに使用されるコンポーネントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-138">The following example shows the components that can be present in an IIS binding:</span></span>  
  
- <span data-ttu-id="9dc9a-139">バインディング プロトコル : HTTP</span><span class="sxs-lookup"><span data-stu-id="9dc9a-139">Binding protocol: HTTP</span></span>  
  
- <span data-ttu-id="9dc9a-140">バインディング情報 : IP アドレス、ポート、ホスト ヘッダー</span><span class="sxs-lookup"><span data-stu-id="9dc9a-140">Binding Information: IP Address, Port, Host header</span></span>  
  
 <span data-ttu-id="9dc9a-141">IIS ではサイトごとに複数の IIS バインディングを指定でき、これによりスキームごとに複数のベース アドレスをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-141">IIS can specify multiple bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="9dc9a-142">.NET Framework 3.5 より前では、WCF ではスキーマの複数のアドレスがサポートされていませんでしたが、指定されている場合は、 <xref:System.ArgumentException> アクティブ化時にがスローされました。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-142">Prior to .NET Framework 3.5, WCF did not support multiple addresses for a schema and, if they were specified, threw a <xref:System.ArgumentException> during activation.</span></span>  
  
 <span data-ttu-id="9dc9a-143">.NET Framework 3.5 では、インターネットサービスプロバイダーは、同じサイト上の同じスキームに対して異なるベースアドレスを持つ複数のアプリケーションをホストできます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-143">The .NET Framework 3.5 enables Internet service providers to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="9dc9a-144">たとえば、サイトで次のベース アドレスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-144">For example, a site could contain the following base addresses:</span></span>  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 <span data-ttu-id="9dc9a-145">.NET Framework 3.5 では、構成ファイルの AppDomain レベルでプレフィックスフィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-145">With .NET Framework 3.5, you specify a prefix filter at the AppDomain level in the configuration file.</span></span> <span data-ttu-id="9dc9a-146">これを行うには、 [\<baseAddressPrefixFilters>](../../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) プレフィックスのリストを含む要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-146">You do this with the [\<baseAddressPrefixFilters>](../../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) element, which contains a list of prefixes.</span></span> <span data-ttu-id="9dc9a-147">IIS によって指定される受信ベース アドレスは、オプションのプレフィックス一覧に基づいてフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-147">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list.</span></span> <span data-ttu-id="9dc9a-148">既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-148">By default, when a prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="9dc9a-149">プレフィックスを指定すると、そのスキームに一致するベース アドレスだけが渡されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-149">Specifying the prefix results in only the matching base address for that scheme to be passed through.</span></span>  
  
 <span data-ttu-id="9dc9a-150">プレフィックス フィルターを使用する構成コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-150">The following is an example of configuration code that uses the prefix filters.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9dc9a-151">前の例で `net.tcp://payroll.myorg.com:8000` は、と `http://shipping.myorg.com:8000` が、それぞれのスキームに対して渡される唯一のベースアドレスです。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-151">In the preceding example, `net.tcp://payroll.myorg.com:8000` and `http://shipping.myorg.com:8000` are the only base addresses, for their respective schemes, which are passed through.</span></span>  
  
 <span data-ttu-id="9dc9a-152">`baseAddressPrefixFilter` では、ワイルカードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-152">The `baseAddressPrefixFilter` does not support wildcards.</span></span>  
  
 <span data-ttu-id="9dc9a-153">IIS が提供するベース アドレスには、`baseAddressPrefixFilters` 一覧に存在しない他のスキームにバインドされたアドレスが指定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-153">The base addresses supplied by IIS may have addresses bound to other schemes not present in `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="9dc9a-154">これらのアドレスはフィルターで除外されません。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-154">These addresses are not filtered out.</span></span>  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a><span data-ttu-id="9dc9a-155">.NET Framework 4 以降での複数の IIS バインディングのサポート</span><span class="sxs-lookup"><span data-stu-id="9dc9a-155">Multiple IIS Binding Support in .NET Framework 4 and later</span></span>  

 <span data-ttu-id="9dc9a-156">.NET 4 以降、<xref:System.ServiceModel.ServiceHostingEnvironment> の <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 設定を true に設定するだけで、1 つのベース アドレスを選択しなくても、IIS で複数のバインディングのサポートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-156">Starting in .NET 4, you can enable support for multiple bindings in IIS without having to pick a single base address, by setting <xref:System.ServiceModel.ServiceHostingEnvironment>’s <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> setting to true.</span></span> <span data-ttu-id="9dc9a-157">このサポートは、HTTP プロトコル スキームに限定されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-157">This support is limited to HTTP protocol schemes.</span></span>  
  
 <span data-ttu-id="9dc9a-158">MultipleSiteBindingsEnabled を on に使用する構成コードの例を次に示し [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) ます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-158">The following is an example of configuration code that uses multipleSiteBindingsEnabled on [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9dc9a-159">複数のサイト バインディングがこの設定を使用して有効になっている場合、HTTP プロトコルと非 HTTP プロトコルの両方について、baseAddressPrefixFilters 設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-159">Any baseAddressPrefixFilters settings are ignored, for both HTTP and non-HTTP protocols, when multiple site bindings are enabled using this setting.</span></span>  
  
 <span data-ttu-id="9dc9a-160">詳細と例については、「 [複数の IIS サイトバインドのサポート](supporting-multiple-iis-site-bindings.md) 」および「」を参照してください <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-160">For details and examples, see [Supporting Multiple IIS Site Bindings](supporting-multiple-iis-site-bindings.md) and <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.</span></span>  
  
## <a name="extending-addressing-in-wcf-services"></a><span data-ttu-id="9dc9a-161">WCF サービスによるアドレスの拡張</span><span class="sxs-lookup"><span data-stu-id="9dc9a-161">Extending Addressing in WCF Services</span></span>  

 <span data-ttu-id="9dc9a-162">WCF サービスの既定のアドレス指定モデルでは、次の目的でエンドポイントアドレス URI が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-162">The default addressing model of WCF services uses the endpoint address URI for the following purposes:</span></span>  
  
- <span data-ttu-id="9dc9a-163">サービスがリッスンするアドレス、つまりエンドポイントがメッセージをリッスンする位置の指定</span><span class="sxs-lookup"><span data-stu-id="9dc9a-163">To specify the service listening address, the location at which the endpoint listens for messages,</span></span>  
  
- <span data-ttu-id="9dc9a-164">SOAP アドレス フィルター、つまりエンドポイントが SOAP ヘッダーとして待機するアドレスの指定</span><span class="sxs-lookup"><span data-stu-id="9dc9a-164">To specify the SOAP address filter, the address an endpoint expects as a SOAP header.</span></span>  
  
 <span data-ttu-id="9dc9a-165">これらの目的で使用する値は個別に指定することができるため、アドレス指定の拡張が可能になり、次に示すような役に立つシナリオに対応します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-165">The values for each of these purposes can be specified separately, allowing several extensions of addressing that cover useful scenarios:</span></span>  
  
- <span data-ttu-id="9dc9a-166">SOAP 中継局 : クライアントが送信したメッセージは、最終目的地に到達する前にメッセージを処理する 1 つ以上の追加サービスを経由します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-166">SOAP intermediaries: a message sent by a client traverses one or more additional services that process the message before it reaches its final destination.</span></span> <span data-ttu-id="9dc9a-167">SOAP 中継局は、メッセージのキャッシュ、ルーティング、負荷分散、スキーム検証など多様なタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-167">SOAP intermediaries can perform various tasks, such as caching, routing, load-balancing, or schema validation on the messages.</span></span> <span data-ttu-id="9dc9a-168">このシナリオは、最終的な送信先である論理アドレス (`via`) ではなく、中継局を目的とする独立した物理アドレス (`wsa:To`) にメッセージを送信することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-168">This scenario is accomplished by sending messages to a separate physical address (`via`) that targets the intermediary rather than just to a logical address (`wsa:To`) that targets the ultimate destination.</span></span>  
  
- <span data-ttu-id="9dc9a-169">エンドポイントがリッスンするアドレスはプライベート URI であり、`listenURI` プロパティとは異なる値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-169">The listening address of the endpoint is a private URI and is set to a different value than its `listenURI` property.</span></span>  
  
 <span data-ttu-id="9dc9a-170">`via` が指定するトランスポート アドレスはメッセージが最初に送信される場所で、この後にメッセージは、`to` パラメーターによって指定された、サービスが存在する別のリモート アドレスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-170">The transport address that the `via` specifies is the location to which a message should initially be sent on its way to some other remote address specified by the `to` parameter at which the service is located.</span></span> <span data-ttu-id="9dc9a-171">インターネットの場合、`via` URI は、サービスの最終的な <xref:System.ServiceModel.EndpointAddress.Uri%2A> アドレスの `to` プロパティと同じになります。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-171">In most Internet scenarios, the `via` URI is the same as the <xref:System.ServiceModel.EndpointAddress.Uri%2A> property of the final `to` address of the service.</span></span> <span data-ttu-id="9dc9a-172">この 2 つのアドレスを区別するのは、手動ルーティングを行う必要がある場合のみです。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-172">You only distinguish between these two addresses when you must do manual routing.</span></span>  
  
### <a name="addressing-headers"></a><span data-ttu-id="9dc9a-173">ヘッダーのアドレス指定</span><span class="sxs-lookup"><span data-stu-id="9dc9a-173">Addressing Headers</span></span>  

 <span data-ttu-id="9dc9a-174">エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-174">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="9dc9a-175">これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-175">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span>  
  
 <span data-ttu-id="9dc9a-176">カスタムのアドレス ヘッダーは、コードまたは構成のいずれかを使用して次のように定義できます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-176">You can define custom address headers in two ways—by using either code or configuration:</span></span>  
  
- <span data-ttu-id="9dc9a-177">コードを使用する場合、カスタムのアドレス ヘッダーは <xref:System.ServiceModel.Channels.AddressHeader> クラスを使用して作成し、<xref:System.ServiceModel.EndpointAddress> の構築時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-177">In code, create custom address headers by using the <xref:System.ServiceModel.Channels.AddressHeader> class, and then used in the construction of an <xref:System.ServiceModel.EndpointAddress>.</span></span>  
  
- <span data-ttu-id="9dc9a-178">構成では、カスタム [\<headers>](../../configure-apps/file-schema/wcf/headers.md) は要素の子として指定され [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) ます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-178">In configuration, custom [\<headers>](../../configure-apps/file-schema/wcf/headers.md) are specified as children of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element.</span></span>  
  
 <span data-ttu-id="9dc9a-179">配置後もヘッダーを変更できるため、コードよりも構成を使用する方法を一般的にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-179">Configuration is generally preferable to code, as it allows you to change the headers after deployment.</span></span>  
  
### <a name="custom-listening-addresses"></a><span data-ttu-id="9dc9a-180">カスタム リッスン アドレス</span><span class="sxs-lookup"><span data-stu-id="9dc9a-180">Custom Listening Addresses</span></span>  

 <span data-ttu-id="9dc9a-181">リッスンするアドレスには、エンドポイントの URI とは異なる値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-181">You can set the listening address to a different value than the endpoint’s URI.</span></span> <span data-ttu-id="9dc9a-182">これは、SOAP アドレスがパブリックな SOAP 中継局として公開される一方、エンドポイントが実際にリッスンするアドレスはプライベートなネットワーク アドレスであるような中継局シナリオの場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-182">This is useful in intermediary scenarios where the SOAP address to be exposed is that of a public SOAP intermediary, whereas the address where the endpoint actually listens is a private network address.</span></span>  
  
 <span data-ttu-id="9dc9a-183">カスタム リッスン アドレスは、コードまたは構成のいずれかを使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-183">You can specify a custom listening address by using either code or configuration:</span></span>  
  
- <span data-ttu-id="9dc9a-184">コードを使用する場合、カスタム リッスン アドレスはエンドポイントの動作コレクションに <xref:System.ServiceModel.Description.ClientViaBehavior> クラスを追加して指定します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-184">In code, specify a custom listening address by adding a <xref:System.ServiceModel.Description.ClientViaBehavior> class to the endpoint’s behavior collection.</span></span>  
  
- <span data-ttu-id="9dc9a-185">[構成] で、サービス要素の属性を使用して、カスタムリッスンアドレスを指定し `ListenUri` [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-185">In configuration, specify a custom listening address with the `ListenUri` attribute of the service [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span>  
  
### <a name="custom-soap-address-filter"></a><span data-ttu-id="9dc9a-186">カスタム SOAP アドレス フィルター</span><span class="sxs-lookup"><span data-stu-id="9dc9a-186">Custom SOAP Address Filter</span></span>  

 <span data-ttu-id="9dc9a-187">エンドポイントの SOAP アドレス フィルター (<xref:System.ServiceModel.EndpointAddress.Uri%2A>) を定義するには、<xref:System.ServiceModel.EndpointAddress.Headers%2A> に任意の <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> プロパティを組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-187">The <xref:System.ServiceModel.EndpointAddress.Uri%2A> is used in conjunction with any <xref:System.ServiceModel.EndpointAddress.Headers%2A> property to define an endpoint’s SOAP address filter (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>).</span></span> <span data-ttu-id="9dc9a-188">既定では、このフィルターは受信メッセージの `To` メッセージ ヘッダーが、エンドポイントの URI に一致し、必要なすべてのエンドポイント ヘッダーがメッセージ内に存在していることを検証します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-188">By default, this filter verifies that an incoming message has a `To` message header that matches the endpoint’s URI and that all of the required endpoint headers are present in the message.</span></span>  
  
 <span data-ttu-id="9dc9a-189">シナリオによっては、適切な `To` ヘッダーを持つメッセージだけではなく、基になるトランスポートに到着したすべてのメッセージをエンドポイントで受信します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-189">In some scenarios, an endpoint receives all messages that arrive on the underlying transport, and not just those with the appropriate `To` header.</span></span> <span data-ttu-id="9dc9a-190">これを行うには、ユーザーは <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="9dc9a-190">To enable this, the user can use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc9a-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dc9a-191">See also</span></span>

- [<span data-ttu-id="9dc9a-192">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="9dc9a-192">Specifying an Endpoint Address</span></span>](../specifying-an-endpoint-address.md)
- [<span data-ttu-id="9dc9a-193">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="9dc9a-193">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
