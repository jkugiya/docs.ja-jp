---
description: '詳細情報: WMI クラスリファレンス'
title: WMI クラスの参照
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 6413065b5740b190aee122ef34727da120737afa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757022"
---
# <a name="wmi-class-reference"></a><span data-ttu-id="9805e-103">WMI クラスの参照</span><span class="sxs-lookup"><span data-stu-id="9805e-103">WMI Class Reference</span></span>

<span data-ttu-id="9805e-104">ここでは、Windows Communication Foundation (WCF) WMI プロバイダーによって公開されるすべての WMI クラスの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9805e-104">This section lists all the WMI classes exposed by the Windows Communication Foundation (WCF) WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="9805e-105">WMI インスタンスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="9805e-105">Accessing WMI Instances</span></span>  

 <span data-ttu-id="9805e-106">WMI オブジェクト リファレンスに記載されているクラスはすべて、インスタンスを直接生成することはできません。ただし Service、AppDomain、Contract、ServiceAppDomain、ServiceToEndpointAssociation、Endpoint の各クラスを除きます。</span><span class="sxs-lookup"><span data-stu-id="9805e-106">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="9805e-107">他のインスタンスには、これらのトップ レベル クラスのプロパティからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9805e-107">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="9805e-108">たとえば、TransportBindingElement インスタンスにアクセスするには、エンドポイントインスタンスから > バインド > BindingElements を使用します。</span><span class="sxs-lookup"><span data-stu-id="9805e-108">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9805e-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9805e-109">In This Section</span></span>  

 [<span data-ttu-id="9805e-110">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="9805e-110">ActivityTransfer</span></span>](activitytransfer.md)  
  
 [<span data-ttu-id="9805e-111">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="9805e-111">AppDomainInfo</span></span>](appdomaininfo.md)  
  
 [<span data-ttu-id="9805e-112">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="9805e-112">AspNetCompatibilityRequirementsAttribute</span></span>](aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="9805e-113">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-113">AsymmetricSecurityBindingElement</span></span>](asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="9805e-114">"Behavior クラス"</span><span class="sxs-lookup"><span data-stu-id="9805e-114">"Behavior class"</span></span>  
  
 [<span data-ttu-id="9805e-115">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-115">BinaryMessageEncodingBindingElement</span></span>](binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="9805e-116">Binding</span><span class="sxs-lookup"><span data-stu-id="9805e-116">Binding</span></span>](binding.md)  
  
 [<span data-ttu-id="9805e-117">BindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-117">BindingElement</span></span>](bindingelement.md)  
  
 [<span data-ttu-id="9805e-118">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-118">CallbackBehavior</span></span>](callbackbehavior.md)  
  
 [<span data-ttu-id="9805e-119">チャネル クラス</span><span class="sxs-lookup"><span data-stu-id="9805e-119">Channel class</span></span>](channel-class.md)  
  
 [<span data-ttu-id="9805e-120">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9805e-120">ChannelPoolSettings</span></span>](channelpoolsettings.md)  
  
 [<span data-ttu-id="9805e-121">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="9805e-121">ClientCredentials</span></span>](clientcredentials.md)  
  
 [<span data-ttu-id="9805e-122">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-122">ClientViaBehavior</span></span>](clientviabehavior.md)  
  
 [<span data-ttu-id="9805e-123">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-123">CompositeDuplexBindingElement</span></span>](compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="9805e-124">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-124">ConnectionOrientedTransportBindingElement</span></span>](connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="9805e-125">決め</span><span class="sxs-lookup"><span data-stu-id="9805e-125">Contract</span></span>](contract.md)  
  
 [<span data-ttu-id="9805e-126">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-126">CustomBindingElement</span></span>](custombindingelement.md)  
  
 [<span data-ttu-id="9805e-127">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="9805e-127">DeliveryRequirementsAttribute</span></span>](deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="9805e-128">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="9805e-128">Endpoint</span></span>](endpoint.md)  
  
 [<span data-ttu-id="9805e-129">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-129">HttpsTransportBindingElement</span></span>](httpstransportbindingelement.md)  
  
 [<span data-ttu-id="9805e-130">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-130">HttpTransportBindingElement</span></span>](httptransportbindingelement.md)  
  
 [<span data-ttu-id="9805e-131">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9805e-131">LocalServiceSecuritySettings</span></span>](localservicesecuritysettings.md)  
  
 [<span data-ttu-id="9805e-132">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-132">MatchAllEndpointBehavior</span></span>](matchallendpointbehavior.md)  
  
 [<span data-ttu-id="9805e-133">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-133">MessageEncodingBindingElement</span></span>](messageencodingbindingelement.md)  
  
 [<span data-ttu-id="9805e-134">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="9805e-134">MsmqBindingElementBase</span></span>](msmqbindingelementbase.md)  
  
 [<span data-ttu-id="9805e-135">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-135">MsmqIntegrationBindingElement</span></span>](msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="9805e-136">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-136">MsmqTransportBindingElement</span></span>](msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="9805e-137">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-137">MtomMessageEncodingBindingElement</span></span>](mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="9805e-138">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-138">MustUnderstandBehavior</span></span>](mustunderstandbehavior.md)  
  
 [<span data-ttu-id="9805e-139">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9805e-139">NamedPipeConnectionPoolSettings</span></span>](namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="9805e-140">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-140">NamedPipeTransportBindingElement</span></span>](namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="9805e-141">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-141">OneWayBindingElement</span></span>](onewaybindingelement.md)  
  
 <span data-ttu-id="9805e-142">"Operation クラス"</span><span class="sxs-lookup"><span data-stu-id="9805e-142">"Operation class"</span></span>  
  
 [<span data-ttu-id="9805e-143">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="9805e-143">OperationBehaviorAttribute</span></span>](operationbehaviorattribute.md)  
  
 [<span data-ttu-id="9805e-144">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-144">PeerCustomResolverBindingElement</span></span>](peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="9805e-145">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-145">PeerResolverBindingElement</span></span>](peerresolverbindingelement.md)  
  
 [<span data-ttu-id="9805e-146">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9805e-146">PeerSecuritySettings</span></span>](peersecuritysettings.md)  
  
 [<span data-ttu-id="9805e-147">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-147">PeerTransportBindingElement</span></span>](peertransportbindingelement.md)  
  
 [<span data-ttu-id="9805e-148">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9805e-148">PeerTransportSecuritySettings</span></span>](peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="9805e-149">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-149">PnrpPeerResolverBindingElement</span></span>](pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="9805e-150">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-150">PrivacyNoticeBindingElement</span></span>](privacynoticebindingelement.md)  
  
 [<span data-ttu-id="9805e-151">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-151">ReliableSessionBindingElement</span></span>](reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="9805e-152">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-152">SecurityBindingElement</span></span>](securitybindingelement.md)  
  
 [<span data-ttu-id="9805e-153">サービス</span><span class="sxs-lookup"><span data-stu-id="9805e-153">Service</span></span>](service.md)  
  
 [<span data-ttu-id="9805e-154">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="9805e-154">ServiceAppDomain</span></span>](serviceappdomain.md)  
  
 [<span data-ttu-id="9805e-155">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-155">ServiceAuthorizationBehavior</span></span>](serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="9805e-156">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="9805e-156">ServiceBehaviorAttribute</span></span>](servicebehaviorattribute.md)  
  
 [<span data-ttu-id="9805e-157">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="9805e-157">ServiceCredentials</span></span>](servicecredentials.md)  
  
 [<span data-ttu-id="9805e-158">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-158">ServiceDebugBehavior</span></span>](servicedebugbehavior.md)  
  
 [<span data-ttu-id="9805e-159">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-159">ServiceMetadataBehavior</span></span>](servicemetadatabehavior.md)  
  
 [<span data-ttu-id="9805e-160">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-160">ServiceSecurityAuditBehavior</span></span>](servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="9805e-161">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-161">ServiceThrottlingBehavior</span></span>](servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="9805e-162">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-162">ServiceTimeoutsBehavior</span></span>](servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="9805e-163">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="9805e-163">ServiceToEndpointAssociation</span></span>](servicetoendpointassociation.md)  
  
 [<span data-ttu-id="9805e-164">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-164">SslStreamSecurityBindingElement</span></span>](sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="9805e-165">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-165">SymmetricSecurityBindingElement</span></span>](symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="9805e-166">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-166">SynchronousReceiveBehavior</span></span>](synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="9805e-167">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9805e-167">TcpConnectionPoolSettings</span></span>](tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="9805e-168">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-168">TcpTransportBindingElement</span></span>](tcptransportbindingelement.md)  
  
 [<span data-ttu-id="9805e-169">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-169">TextMessageEncodingBindingElement</span></span>](textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="9805e-170">TraceListener</span><span class="sxs-lookup"><span data-stu-id="9805e-170">TraceListener</span></span>](tracelistener.md)  
  
 [<span data-ttu-id="9805e-171">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="9805e-171">TraceListenerArgument</span></span>](tracelistenerargument.md)  
  
 [<span data-ttu-id="9805e-172">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-172">TransactedBatchingBehavior</span></span>](transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="9805e-173">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="9805e-173">TransactionFlowAttribute</span></span>](transactionflowattribute.md)  
  
 [<span data-ttu-id="9805e-174">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-174">TransactionFlowBindingElement</span></span>](transactionflowbindingelement.md)  
  
 [<span data-ttu-id="9805e-175">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-175">TransportBindingElement</span></span>](transportbindingelement.md)  
  
 [<span data-ttu-id="9805e-176">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-176">TransportSecurityBindingElement</span></span>](transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="9805e-177">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-177">UseManagedPresentationBindingElement</span></span>](usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="9805e-178">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9805e-178">WindowsStreamSecurityBindingElement</span></span>](windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="9805e-179">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="9805e-179">WSAT_TraceEvent</span></span>](wsat-traceevent.md)  
  
 [<span data-ttu-id="9805e-180">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="9805e-180">WSAT_TraceProvider</span></span>](wsat-traceprovider.md)  
  
 [<span data-ttu-id="9805e-181">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="9805e-181">WSAT_TraceRecord</span></span>](wsat-tracerecord.md)  
  
 [<span data-ttu-id="9805e-182">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="9805e-182">XmlDictionaryReaderQuotas</span></span>](xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="9805e-183">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="9805e-183">XmlSerializerOperationBehavior</span></span>](xmlserializeroperationbehavior.md)
