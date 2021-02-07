---
description: 詳細については、構成ファイルでの検出の構成に関するページを参照してください。
title: 構成ファイルにおける探索の構成
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 95ac1a08d40f16141dc5c8763640a258b15ef497
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743292"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="4dcdc-103">構成ファイルにおける探索の構成</span><span class="sxs-lookup"><span data-stu-id="4dcdc-103">Configuring Discovery in a Configuration File</span></span>

<span data-ttu-id="4dcdc-104">探索で使用される構成設定は、4 つの主なグループに分類されます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-104">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="4dcdc-105">このトピックでは、各グループについて簡単に説明し、各グループの構成方法の例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-105">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="4dcdc-106">以下の各セクションは、各領域についてのより詳細なドキュメントにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-106">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="4dcdc-107">動作の構成</span><span class="sxs-lookup"><span data-stu-id="4dcdc-107">Behavior Configuration</span></span>  

 <span data-ttu-id="4dcdc-108">探索では、サービスの動作とエンドポイントの動作が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-108">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="4dcdc-109"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 動作により、サービスのすべてのエンドポイントの探索が有効になるだけでなく、アナウンス エンドポイントの指定が可能になります。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-109">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="4dcdc-110">次の例は、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> を追加し、アナウンス エンドポイントを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-110">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="4dcdc-111">動作を指定したら、 `service` 次の例に示すように、<> 要素からこの動作を参照します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-111">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </services>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4dcdc-112">サービスを探索可能にするには、探索エンドポイントを追加する必要もあります。上の例では、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 標準エンドポイントを追加しています。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-112">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="4dcdc-113">アナウンスエンドポイントを追加する場合は、 `services` 次の例に示すように、<> 要素にアナウンスリスナーサービスを追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-113">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>
```  
  
 <span data-ttu-id="4dcdc-114"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 動作は、特定のエンドポイントの探索を有効または無効にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-114">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="4dcdc-115">次の例では、サービスに 2 つのアプリケーション エンドポイントを構成します。1 つのエンドポイントでは探索を有効し、もう 1 つでは探索を無効にします。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-115">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="4dcdc-116">それぞれのエンドポイントには <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 動作が追加されます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-116">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
   <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4dcdc-117"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 動作を使用すると、サービスから返されるエンドポイント メタデータにカスタム メタデータを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-117">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="4dcdc-118">次の例は、その方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-118">The following example shows how to do this.</span></span>  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="4dcdc-119"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 動作を使用すると、クライアントがサービスの検索に使用するスコープと型を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-119">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="4dcdc-120">クライアント側の構成ファイルでこの構成を行う方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-120">The following example shows how to do this in a client side configuration file.</span></span>  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="4dcdc-121">の詳細については <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 、 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 「 [WCF Discovery の概要](wcf-discovery-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-121">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="4dcdc-122">バインド要素の構成</span><span class="sxs-lookup"><span data-stu-id="4dcdc-122">Binding Element Configuration</span></span>  

 <span data-ttu-id="4dcdc-123">バインディング要素の構成は、クライアント側で最も興味深い構成です。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-123">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="4dcdc-124">構成を使用して、WCF クライアント アプリケーションからのサービスの探索に使用する検索条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-124">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="4dcdc-125">次の例では、<xref:System.ServiceModel.Discovery.DiscoveryClient> チャネルとのカスタム バインドを作成し、型とスコープを含む検索条件を指定しています。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-125">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="4dcdc-126">また、<xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> プロパティと <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> プロパティの値も指定しています。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-126">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
      </binding>
   </customBinding>
</bindings>  
```  
  
 <span data-ttu-id="4dcdc-127">このカスタム バインディング構成は、クライアント エンドポイントから参照される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-127">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="4dcdc-128">検索条件の詳細については [、「探索検索と findcriteria](discovery-find-and-findcriteria.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-128">For more information about find criteria see [Discovery Find and FindCriteria](discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="4dcdc-129">検出要素とバインド要素の詳細については、「 [WCF discovery の概要](wcf-discovery-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-129">For more information about discovery and binding elements see, [WCF Discovery Overview](wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="4dcdc-130">標準エンドポイントの構成</span><span class="sxs-lookup"><span data-stu-id="4dcdc-130">Standard Endpoint Configuration</span></span>  

 <span data-ttu-id="4dcdc-131">標準エンドポイントは定義済みのエンドポイントで、これには、1 つ以上のプロパティ (アドレス、バインディング、またはコントラクト) の既定値、または、変更できない 1 つ以上のプロパティ値が設定されています。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-131">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="4dcdc-132">.NET 4 には、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>、<xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>、および <xref:System.ServiceModel.Discovery.DynamicEndpoint> という 3 種類の探索関連の標準エンドポイントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-132">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="4dcdc-133"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> は、UDP マルチキャスト バインディングを使用した探索操作用に事前に構成されている標準エンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-133">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="4dcdc-134"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> は、UDP バインディングを使用したアナウンスの送信用に事前に構成されている標準エンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-134">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="4dcdc-135"><xref:System.ServiceModel.Discovery.DynamicEndpoint> は、実行時に探索対象のサービスのエンドポイント アドレスを動的に検索するために探索が使用する標準エンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-135">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="4dcdc-136">標準バインディングは、 `endpoint` 追加する標準エンドポイントの種類を指定した kind 属性を含む <> 要素を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-136">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="4dcdc-137"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> および <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> を追加する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-137">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 <span data-ttu-id="4dcdc-138">標準エンドポイントは、<> 要素で構成され `standardEndpoints` ます。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-138">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="4dcdc-139"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> および <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> を構成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-139">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint
            name="udpAnnouncementEndpointSettings"
            multicastAddress="soap.udp://239.255.255.250:3703"
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="4dcdc-140">標準エンドポイント構成を追加したら、 `endpoint` 次の例に示すように、各エンドポイントの <> 要素で構成を参照します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-140">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 <span data-ttu-id="4dcdc-141">探索で使用されるその他の標準エンドポイントとは異なり、<xref:System.ServiceModel.Discovery.DynamicEndpoint> にはバインディングとコントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-141">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="4dcdc-142"><xref:System.ServiceModel.Discovery.DynamicEndpoint> を追加し、構成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-142">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 <span data-ttu-id="4dcdc-143">標準エンドポイントの詳細については、「 [標準エンドポイント](standard-endpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dcdc-143">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
