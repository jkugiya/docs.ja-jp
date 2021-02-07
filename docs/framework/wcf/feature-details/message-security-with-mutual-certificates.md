---
description: '詳細情報: 相互証明書を使用したメッセージセキュリティ'
title: メッセージ セキュリティと相互の証明書
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: c894f457dcd0fdc449c2f94eaee15004300df5fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726989"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="b753c-103">メッセージ セキュリティと相互の証明書</span><span class="sxs-lookup"><span data-stu-id="b753c-103">Message Security with Mutual Certificates</span></span>

<span data-ttu-id="b753c-104">次のシナリオは、メッセージセキュリティモードを使用してセキュリティで保護された Windows Communication Foundation (WCF) サービスとクライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="b753c-104">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="b753c-105">クライアントとサービスは、証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="b753c-105">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="b753c-106">このシナリオは、X.509 証明書トークン プロファイルと共に WS-Security を使用するため、相互運用性があります。</span><span class="sxs-lookup"><span data-stu-id="b753c-106">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b753c-107">このシナリオでは、サービス証明書のネゴシエーションは実行されません。</span><span class="sxs-lookup"><span data-stu-id="b753c-107">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="b753c-108">通信を開始する前に、サービス証明書をクライアントに提供しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b753c-108">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="b753c-109">サーバー証明書は、アプリケーションと共に配布したり、帯域外通信で提供できます。</span><span class="sxs-lookup"><span data-stu-id="b753c-109">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="b753c-110">![相互証明書を使用したメッセージセキュリティ](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="b753c-110">![Message security with mutual certificates](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="b753c-111">特徴</span><span class="sxs-lookup"><span data-stu-id="b753c-111">Characteristic</span></span>|<span data-ttu-id="b753c-112">説明</span><span class="sxs-lookup"><span data-stu-id="b753c-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b753c-113">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="b753c-113">Security Mode</span></span>|<span data-ttu-id="b753c-114">Message</span><span class="sxs-lookup"><span data-stu-id="b753c-114">Message</span></span>|  
|<span data-ttu-id="b753c-115">相互運用性</span><span class="sxs-lookup"><span data-stu-id="b753c-115">Interoperability</span></span>|<span data-ttu-id="b753c-116">○ WS-Security および X.509 証明書トークン プロファイルと互換性があるクライアントとサービスで相互運用性があります。</span><span class="sxs-lookup"><span data-stu-id="b753c-116">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="b753c-117">認証</span><span class="sxs-lookup"><span data-stu-id="b753c-117">Authentication</span></span>|<span data-ttu-id="b753c-118">サーバーとクライアントの相互認証</span><span class="sxs-lookup"><span data-stu-id="b753c-118">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="b753c-119">整合性</span><span class="sxs-lookup"><span data-stu-id="b753c-119">Integrity</span></span>|<span data-ttu-id="b753c-120">はい</span><span class="sxs-lookup"><span data-stu-id="b753c-120">Yes</span></span>|  
|<span data-ttu-id="b753c-121">機密性</span><span class="sxs-lookup"><span data-stu-id="b753c-121">Confidentiality</span></span>|<span data-ttu-id="b753c-122">はい</span><span class="sxs-lookup"><span data-stu-id="b753c-122">Yes</span></span>|  
|<span data-ttu-id="b753c-123">トランスポート</span><span class="sxs-lookup"><span data-stu-id="b753c-123">Transport</span></span>|<span data-ttu-id="b753c-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="b753c-124">HTTP</span></span>|  
|<span data-ttu-id="b753c-125">バインド</span><span class="sxs-lookup"><span data-stu-id="b753c-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="b753c-126">サービス</span><span class="sxs-lookup"><span data-stu-id="b753c-126">Service</span></span>  

 <span data-ttu-id="b753c-127">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="b753c-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b753c-128">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="b753c-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="b753c-129">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b753c-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="b753c-130">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="b753c-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b753c-131">コード</span><span class="sxs-lookup"><span data-stu-id="b753c-131">Code</span></span>  

 <span data-ttu-id="b753c-132">次のコードでは、メッセージ セキュリティを使用するサービス エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b753c-132">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="b753c-133">サービスには、自身を認証するための証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="b753c-133">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="b753c-134">構成</span><span class="sxs-lookup"><span data-stu-id="b753c-134">Configuration</span></span>  

 <span data-ttu-id="b753c-135">コードの代わりに次の構成を使用して、同じサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b753c-135">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="b753c-136">クライアント</span><span class="sxs-lookup"><span data-stu-id="b753c-136">Client</span></span>  

 <span data-ttu-id="b753c-137">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="b753c-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b753c-138">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="b753c-138">Do one of the following:</span></span>  
  
- <span data-ttu-id="b753c-139">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b753c-139">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="b753c-140">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b753c-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b753c-141">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="b753c-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b753c-142">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b753c-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="b753c-143">コード</span><span class="sxs-lookup"><span data-stu-id="b753c-143">Code</span></span>  

 <span data-ttu-id="b753c-144">クライアントを作成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b753c-144">The following code creates the client.</span></span> <span data-ttu-id="b753c-145">セキュリティ モードは Message に設定され、クライアント資格情報の種類は Certificate に設定されています。</span><span class="sxs-lookup"><span data-stu-id="b753c-145">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="b753c-146">構成</span><span class="sxs-lookup"><span data-stu-id="b753c-146">Configuration</span></span>  

 <span data-ttu-id="b753c-147">次のコードは、クライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="b753c-147">The following configures the client.</span></span> <span data-ttu-id="b753c-148">クライアント証明書は、を使用して指定する必要があり [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="b753c-148">A client certificate must be specified using the [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="b753c-149">また、サービス証明書はを使用して指定され [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="b753c-149">Also, the service certificate is specified using the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b753c-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="b753c-150">See also</span></span>

- [<span data-ttu-id="b753c-151">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="b753c-151">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="b753c-152">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b753c-152">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="b753c-153">[方法: 開発時にトランスポートセキュリティのために WCF で一時的な証明書を作成およびインストールする](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="b753c-153">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
