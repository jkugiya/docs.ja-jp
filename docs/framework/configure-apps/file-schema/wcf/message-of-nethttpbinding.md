---
description: 詳細については <message> 、 <netHttpBinding>
title: <message> の <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 508e58e58dbb298081a075588ddda87289c1a3d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749616"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="aa37b-103">\<message> の \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="aa37b-103">\<message> of \<netHttpBinding></span></span>

<span data-ttu-id="aa37b-104">のメッセージレベルのセキュリティの設定を定義し [\<netHttpBinding>](nethttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-104">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="aa37b-105">構文</span><span class="sxs-lookup"><span data-stu-id="aa37b-105">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa37b-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="aa37b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="aa37b-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="aa37b-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa37b-108">属性</span><span class="sxs-lookup"><span data-stu-id="aa37b-108">Attributes</span></span>  
  
|<span data-ttu-id="aa37b-109">属性</span><span class="sxs-lookup"><span data-stu-id="aa37b-109">Attribute</span></span>|<span data-ttu-id="aa37b-110">説明</span><span class="sxs-lookup"><span data-stu-id="aa37b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa37b-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="aa37b-111">algorithmSuite</span></span>|<span data-ttu-id="aa37b-112">メッセージの暗号化とキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="aa37b-112">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="aa37b-113">この属性は、アルゴリズムとキー サイズを指定する <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。</span><span class="sxs-lookup"><span data-stu-id="aa37b-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="aa37b-114">これらのアルゴリズムは、セキュリティ ポリシー言語 (WS-SecurityPolicy) 仕様で指定されたアルゴリズムにマップされます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-114">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="aa37b-115">既定値は `Basic256` です。</span><span class="sxs-lookup"><span data-stu-id="aa37b-115">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="aa37b-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="aa37b-116">clientCredentialType</span></span>|<span data-ttu-id="aa37b-117">メッセージ ベースのセキュリティを使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="aa37b-117">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="aa37b-118">既定値は、`UserName` です。</span><span class="sxs-lookup"><span data-stu-id="aa37b-118">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="aa37b-119">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="aa37b-119">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="aa37b-120">値</span><span class="sxs-lookup"><span data-stu-id="aa37b-120">Value</span></span>|<span data-ttu-id="aa37b-121">説明</span><span class="sxs-lookup"><span data-stu-id="aa37b-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa37b-122">UserName</span><span class="sxs-lookup"><span data-stu-id="aa37b-122">UserName</span></span>|<span data-ttu-id="aa37b-123">-クライアントがユーザー名資格情報を使用してサーバーに対して認証される必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa37b-123">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="aa37b-124">この資格情報は、<> 要素を使用して指定する必要があり `clientCredentials` ます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-124">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="aa37b-125">-WCF では、パスワードダイジェストの送信や、パスワードを使用したキーの派生、およびメッセージセキュリティのためのこのようなキーの使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="aa37b-125">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="aa37b-126">そのため、ユーザー名の資格情報を使用する場合、WCF はトランスポートをセキュリティで保護するように強制します。</span><span class="sxs-lookup"><span data-stu-id="aa37b-126">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="aa37b-127">`basicHttpBinding` の場合は、SSL チャネルの設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="aa37b-127">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="aa37b-128">Certificate</span><span class="sxs-lookup"><span data-stu-id="aa37b-128">Certificate</span></span>|<span data-ttu-id="aa37b-129">証明書を使用してクライアントをサーバーに認証するように要求します。</span><span class="sxs-lookup"><span data-stu-id="aa37b-129">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="aa37b-130">この場合のクライアント資格情報は、<> と <> を使用して指定する必要があり `clientCredentials` `clientCertificate` ます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-130">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="aa37b-131">さらに、メッセージのセキュリティ モードを使用する場合は、クライアントにサービス証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa37b-131">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="aa37b-132">この場合のサービス資格情報は、 <xref:System.ServiceModel.Description.ClientCredentials> クラスまたは動作要素を使用して指定 `ClientCredentials` し、serviceCredentials の要素を使用してサービス証明書を指定する必要があり \<serviceCertificate> ます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-132">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa37b-133">子要素</span><span class="sxs-lookup"><span data-stu-id="aa37b-133">Child Elements</span></span>  

 <span data-ttu-id="aa37b-134">なし</span><span class="sxs-lookup"><span data-stu-id="aa37b-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa37b-135">親要素</span><span class="sxs-lookup"><span data-stu-id="aa37b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="aa37b-136">要素</span><span class="sxs-lookup"><span data-stu-id="aa37b-136">Element</span></span>|<span data-ttu-id="aa37b-137">説明</span><span class="sxs-lookup"><span data-stu-id="aa37b-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa37b-138"><`security` <の> 要素 `netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="aa37b-138"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="aa37b-139"><> 要素のセキュリティ機能を定義 `netHttpBinding` します。</span><span class="sxs-lookup"><span data-stu-id="aa37b-139">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aa37b-140">例</span><span class="sxs-lookup"><span data-stu-id="aa37b-140">Example</span></span>  

 <span data-ttu-id="aa37b-141">このサンプルでは、basicHttpBinding とメッセージ セキュリティを使用するアプリケーションを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="aa37b-141">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="aa37b-142">サービスの次の構成例では、エンドポイント定義によって basicHttpBinding が指定され、`Binding1` という名前のバインディング構成が参照されます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-142">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="aa37b-143">サービスがクライアントに対してサービス自体を認証するために使用する証明書は、`behaviors` 要素の下にある構成ファイルの `serviceCredentials` セクションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-143">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="aa37b-144">クライアントがサービスに対してクライアント自体を認証するために使用する証明書に適用される検証モードも、`behaviors` 要素の下にある `clientCertificate` セクションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-144">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="aa37b-145">同じバインディングとセキュリティの詳細が、クライアントの構成ファイルで指定されます。</span><span class="sxs-lookup"><span data-stu-id="aa37b-145">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- This configuration defines the SecurityMode as Message and
           the clientCredentialType as Certificate. -->
      <binding name="Binding1" >
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
                 is in the user's Trusted People store, then it will be trusted without performing a
                 validation of the certificate's issuer chain. This setting is used here for convenience so that the
                 sample can be run without having to have certificates issued by a certification authority (CA).
                 This setting is less secure than the default, ChainTrust. The security implications of this
                 setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="aa37b-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa37b-146">See also</span></span>

- [<span data-ttu-id="aa37b-147">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="aa37b-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="aa37b-148">バインド</span><span class="sxs-lookup"><span data-stu-id="aa37b-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aa37b-149">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="aa37b-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="aa37b-150">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="aa37b-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
