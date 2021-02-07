---
description: '詳細情報: 信頼されたサブシステム'
title: 信頼できるサブシステム
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 41c2943c7794206dba06ef8b5bbee762931ce0c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733048"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="a0d9b-103">信頼できるサブシステム</span><span class="sxs-lookup"><span data-stu-id="a0d9b-103">Trusted Subsystem</span></span>

<span data-ttu-id="a0d9b-104">クライアントは、ネットワーク全体に分散している 1 つ以上の Web サービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-104">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="a0d9b-105">Web サービスは、追加のリソース (データベースや他の Web サービスなど) に対するアクセスが、Web サービスのビジネス ロジック内にカプセル化されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-105">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="a0d9b-106">これらのリソースは、非承認のアクセスに対して保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-106">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="a0d9b-107">信頼できるサブシステムの処理を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-107">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="a0d9b-108">![信頼されたサブシステム](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="a0d9b-108">![Trusted subsystem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="a0d9b-109">上図に示した信頼できるサブシステムの処理について、以下の手順で説明します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-109">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="a0d9b-110">クライアントが、信頼できるサブシステムに、資格情報と共に要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-110">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="a0d9b-111">信頼できるサブシステムが、ユーザーの認証と承認を行います。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-111">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="a0d9b-112">信頼できるサブシステムは、リモート リソースに要求メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-112">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="a0d9b-113">この要求には、信頼できるサブシステムの資格情報 (または信頼できるサブシステムの処理を実行しているサービス アカウント) が付属しています。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-113">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="a0d9b-114">バックエンド リソースが、信頼できるサブシステムの認証と承認を行います。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-114">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="a0d9b-115">次にバックエンド リソースは要求を処理し、信頼できるサブシステムへの応答を発行します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-115">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="a0d9b-116">信頼できるサブシステムはこの応答を処理し、自身の応答をクライアントに発行します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-116">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="a0d9b-117">特徴</span><span class="sxs-lookup"><span data-stu-id="a0d9b-117">Characteristic</span></span>|<span data-ttu-id="a0d9b-118">説明</span><span class="sxs-lookup"><span data-stu-id="a0d9b-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a0d9b-119">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="a0d9b-119">Security Mode</span></span>|<span data-ttu-id="a0d9b-120">Message</span><span class="sxs-lookup"><span data-stu-id="a0d9b-120">Message</span></span>|  
|<span data-ttu-id="a0d9b-121">相互運用性</span><span class="sxs-lookup"><span data-stu-id="a0d9b-121">Interoperability</span></span>|<span data-ttu-id="a0d9b-122">Windows Communication Foundation (WCF) のみ。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-122">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="a0d9b-123">認証 (サービス)</span><span class="sxs-lookup"><span data-stu-id="a0d9b-123">Authentication (service)</span></span>|<span data-ttu-id="a0d9b-124">セキュリティ トークン サービスはクライアントの認証と承認を行います。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-124">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="a0d9b-125">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="a0d9b-125">Authentication (client)</span></span>|<span data-ttu-id="a0d9b-126">信頼できるサブシステムがクライアントを認証し、リソースが信頼できるサブシステム サービスを認証します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-126">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="a0d9b-127">整合性</span><span class="sxs-lookup"><span data-stu-id="a0d9b-127">Integrity</span></span>|<span data-ttu-id="a0d9b-128">はい</span><span class="sxs-lookup"><span data-stu-id="a0d9b-128">Yes</span></span>|  
|<span data-ttu-id="a0d9b-129">機密性</span><span class="sxs-lookup"><span data-stu-id="a0d9b-129">Confidentiality</span></span>|<span data-ttu-id="a0d9b-130">はい</span><span class="sxs-lookup"><span data-stu-id="a0d9b-130">Yes</span></span>|  
|<span data-ttu-id="a0d9b-131">トランスポート</span><span class="sxs-lookup"><span data-stu-id="a0d9b-131">Transport</span></span>|<span data-ttu-id="a0d9b-132">クライアントと信頼できるサブシステム サービス間にある HTTP</span><span class="sxs-lookup"><span data-stu-id="a0d9b-132">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="a0d9b-133">信頼できるサブシステム サービスとリソース (バックエンド サービス) の間にある NET.TCP</span><span class="sxs-lookup"><span data-stu-id="a0d9b-133">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="a0d9b-134">バインド</span><span class="sxs-lookup"><span data-stu-id="a0d9b-134">Binding</span></span>|<span data-ttu-id="a0d9b-135"><xref:System.ServiceModel.WSHttpBinding> そして <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a0d9b-135"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="a0d9b-136">リソース (バックエンド サービス)</span><span class="sxs-lookup"><span data-stu-id="a0d9b-136">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="a0d9b-137">コード</span><span class="sxs-lookup"><span data-stu-id="a0d9b-137">Code</span></span>  

 <span data-ttu-id="a0d9b-138">次のコードでは、TCP トランスポート プロトコル上でトランスポート セキュリティを使用するリソースのサービス エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-138">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="a0d9b-139">構成</span><span class="sxs-lookup"><span data-stu-id="a0d9b-139">Configuration</span></span>  

 <span data-ttu-id="a0d9b-140">次の構成では、構成を使用して同一のエンドポイントをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-140">The following configuration sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a><span data-ttu-id="a0d9b-141">信頼できるサブシステム</span><span class="sxs-lookup"><span data-stu-id="a0d9b-141">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="a0d9b-142">コード</span><span class="sxs-lookup"><span data-stu-id="a0d9b-142">Code</span></span>  

 <span data-ttu-id="a0d9b-143">次のコードでは、HTTP プロトコル上のメッセージ セキュリティで認証にユーザー名とパスワードを使用する、信頼できるサブシステムのサービス エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-143">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="a0d9b-144">次のコードでは、TCP トランスポート プロトコル上でトランスポート セキュリティを使用してバックエンド サービスと通信を行う、信頼できるサブシステムのサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-144">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="a0d9b-145">構成</span><span class="sxs-lookup"><span data-stu-id="a0d9b-145">Configuration</span></span>  

 <span data-ttu-id="a0d9b-146">次の構成では、構成を使用して同一のエンドポイントをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-146">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="a0d9b-147">2 つのバインディングがあることに注意してください。1 つは、信頼できるサブシステムでホストされるサービスをセキュリティで保護するバインディングで、もう 1 つは、信頼できるサブシステムとバックエンド サービスの間の通信のためのバインディングです。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-147">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="a0d9b-148">クライアント</span><span class="sxs-lookup"><span data-stu-id="a0d9b-148">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="a0d9b-149">コード</span><span class="sxs-lookup"><span data-stu-id="a0d9b-149">Code</span></span>  

 <span data-ttu-id="a0d9b-150">次のコードでは、HTTP プロトコル上のメッセージ セキュリティで認証にユーザー名とパスワードを使用することで、信頼できるサブシステムと通信を行うクライアントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-150">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="a0d9b-151">構成</span><span class="sxs-lookup"><span data-stu-id="a0d9b-151">Configuration</span></span>  

 <span data-ttu-id="a0d9b-152">次のコードでは、HTTP プロトコル上のメッセージ セキュリティ、および認証用のユーザー名とパスワードを使用するようにクライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-152">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="a0d9b-153">ユーザー名とパスワードの指定はコードを使用する場合に限られます (構成可能ではありません)。</span><span class="sxs-lookup"><span data-stu-id="a0d9b-153">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0d9b-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0d9b-154">See also</span></span>

- [<span data-ttu-id="a0d9b-155">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="a0d9b-155">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="a0d9b-156">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a0d9b-156">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
