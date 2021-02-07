---
description: '詳細情報: <baseAddressPrefixFilters>'
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 9212838393ead04bdcd475b314bb2707e6f899ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749676"
---
# \<baseAddressPrefixFilters>

<span data-ttu-id="3002b-102">パススルーフィルターを指定する構成要素のコレクションを表します。パススルーフィルターは、IIS で Windows Communication Foundation (WCF) アプリケーションをホストするときに適切なインターネットインフォメーションサービス (IIS) バインドを選択するメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="3002b-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="3002b-103">\<baseAddressPrefixFilters> は "localhost" を認識しません。代わりに、完全修飾コンピューター名を使用してください。</span><span class="sxs-lookup"><span data-stu-id="3002b-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**  
  
## <a name="syntax"></a><span data-ttu-id="3002b-104">構文</span><span class="sxs-lookup"><span data-stu-id="3002b-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3002b-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3002b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3002b-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3002b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3002b-107">属性</span><span class="sxs-lookup"><span data-stu-id="3002b-107">Attributes</span></span>  

 <span data-ttu-id="3002b-108">なし。</span><span class="sxs-lookup"><span data-stu-id="3002b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3002b-109">子要素</span><span class="sxs-lookup"><span data-stu-id="3002b-109">Child Elements</span></span>  
  
|<span data-ttu-id="3002b-110">要素</span><span class="sxs-lookup"><span data-stu-id="3002b-110">Element</span></span>|<span data-ttu-id="3002b-111">説明</span><span class="sxs-lookup"><span data-stu-id="3002b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="3002b-112">サービス ホストによって使用されるベース アドレスのプレフィックス フィルターを指定する構成要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="3002b-112">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3002b-113">親要素</span><span class="sxs-lookup"><span data-stu-id="3002b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="3002b-114">要素</span><span class="sxs-lookup"><span data-stu-id="3002b-114">Element</span></span>|<span data-ttu-id="3002b-115">説明</span><span class="sxs-lookup"><span data-stu-id="3002b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="3002b-116">環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="3002b-116">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3002b-117">解説</span><span class="sxs-lookup"><span data-stu-id="3002b-117">Remarks</span></span>  

 <span data-ttu-id="3002b-118">プレフィックス フィルターは、サービスによって使用される URI を、共有ホスティング プロバイダーが指定できるようにする手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="3002b-118">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="3002b-119">これにより、共有ホストは、同じサイト上の同じスキームに対して、別々のベース アドレスを使用して複数のアプリケーションをホストできるようになります。</span><span class="sxs-lookup"><span data-stu-id="3002b-119">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="3002b-120">IIS Web サイトは、仮想ディレクトリを含む仮想アプリケーションのコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="3002b-120">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="3002b-121">サイト内のアプリケーションには、1 つ以上の IIS バインディングからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3002b-121">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="3002b-122">IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3002b-122">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="3002b-123">バインディング プロトコル (HTTP など) は通信を行うスキームを定義し、バインディング情報 (IP アドレス、ポート、ホスト ヘッダーなど) にはサイトにアクセスするために使用するデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3002b-123">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="3002b-124">IIS では、サイトごとに複数の IIS バインディングを指定できるので、各スキームに複数のベース アドレスが定義されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3002b-124">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="3002b-125">サイトでホストされる WCF サービスでは、スキームごとに1つのベースアドレスにしかバインドできないため、プレフィックスフィルター機能を使用して、ホステッドサービスの必要なベースアドレスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3002b-125">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="3002b-126">IIS によって指定される受信ベース アドレスは、オプションのプレフィックス リスト フィルターに基づいてフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="3002b-126">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="3002b-127">たとえば、サイトに次のベースアドレスを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3002b-127">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="3002b-128">次の構成ファイルを使用して、appdomain レベルでプレフィックス フィルターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3002b-128">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="3002b-129">この例では、`net.tcp://test1.fabrikam.com:8000` と `http://test2.fabrikam.com:9000` が、対応するスキームに渡される唯一のベース アドレスです。</span><span class="sxs-lookup"><span data-stu-id="3002b-129">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="3002b-130">既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。</span><span class="sxs-lookup"><span data-stu-id="3002b-130">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="3002b-131">プレフィックスだけを指定すると、そのスキームに一致するベース アドレスを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="3002b-131">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3002b-132">フィルターでワイルドカードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3002b-132">The filter does not support any wildcards.</span></span> <span data-ttu-id="3002b-133">また、IIS が提供する baseAddresses には、`baseAddressPrefixFilters` リストに存在しない他のスキームにバインドされたアドレスが指定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="3002b-133">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="3002b-134">これらのアドレスはフィルターで除外されません。</span><span class="sxs-lookup"><span data-stu-id="3002b-134">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3002b-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="3002b-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="3002b-136">ホスティング</span><span class="sxs-lookup"><span data-stu-id="3002b-136">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
