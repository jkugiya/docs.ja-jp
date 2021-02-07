---
description: 詳細については、「ユーザー名クライアントを使用したメッセージセキュリティ」を参照してください。
title: ユーザー名クライアントを使用したメッセージ セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 4502635df3b52ba069c19fca7a73cc9395dd105d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756111"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="39bc0-103">ユーザー名クライアントを使用したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="39bc0-103">Message Security with a User Name Client</span></span>

<span data-ttu-id="39bc0-104">次の図は、メッセージレベルのセキュリティを使用してセキュリティで保護された Windows Communication Foundation (WCF) サービスとクライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="39bc0-104">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="39bc0-105">サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="39bc0-105">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="39bc0-106">クライアントはユーザー名とパスワードを使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="39bc0-106">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="39bc0-107">サンプルアプリケーションについては、「 [メッセージセキュリティユーザー名](../samples/message-security-user-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39bc0-107">For a sample application, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="39bc0-108">![ユーザー名認証を使用したメッセージ セキュリティ](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="39bc0-108">![Message security using username authentication](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="39bc0-109">特徴</span><span class="sxs-lookup"><span data-stu-id="39bc0-109">Characteristic</span></span>|<span data-ttu-id="39bc0-110">説明</span><span class="sxs-lookup"><span data-stu-id="39bc0-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="39bc0-111">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="39bc0-111">Security Mode</span></span>|<span data-ttu-id="39bc0-112">Message</span><span class="sxs-lookup"><span data-stu-id="39bc0-112">Message</span></span>|  
|<span data-ttu-id="39bc0-113">相互運用性</span><span class="sxs-lookup"><span data-stu-id="39bc0-113">Interoperability</span></span>|<span data-ttu-id="39bc0-114">Windows Communication Foundation (WCF) のみ</span><span class="sxs-lookup"><span data-stu-id="39bc0-114">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="39bc0-115">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="39bc0-115">Authentication (Server)</span></span>|<span data-ttu-id="39bc0-116">初期ネゴシエーションにはサーバー認証が必要</span><span class="sxs-lookup"><span data-stu-id="39bc0-116">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="39bc0-117">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="39bc0-117">Authentication (Client)</span></span>|<span data-ttu-id="39bc0-118">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="39bc0-118">User name/password</span></span>|  
|<span data-ttu-id="39bc0-119">整合性</span><span class="sxs-lookup"><span data-stu-id="39bc0-119">Integrity</span></span>|<span data-ttu-id="39bc0-120">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="39bc0-120">Yes, using shared security context</span></span>|  
|<span data-ttu-id="39bc0-121">機密性</span><span class="sxs-lookup"><span data-stu-id="39bc0-121">Confidentiality</span></span>|<span data-ttu-id="39bc0-122">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="39bc0-122">Yes, using shared security context</span></span>|  
|<span data-ttu-id="39bc0-123">トランスポート</span><span class="sxs-lookup"><span data-stu-id="39bc0-123">Transport</span></span>|<span data-ttu-id="39bc0-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="39bc0-124">HTTP</span></span>|  
|<span data-ttu-id="39bc0-125">バインド</span><span class="sxs-lookup"><span data-stu-id="39bc0-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="39bc0-126">サービス</span><span class="sxs-lookup"><span data-stu-id="39bc0-126">Service</span></span>  

 <span data-ttu-id="39bc0-127">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="39bc0-128">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="39bc0-129">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="39bc0-130">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="39bc0-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="39bc0-131">コード</span><span class="sxs-lookup"><span data-stu-id="39bc0-131">Code</span></span>  

 <span data-ttu-id="39bc0-132">次のコードは、メッセージ セキュリティを使用するサービス エンドポイントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-132">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="39bc0-133">構成</span><span class="sxs-lookup"><span data-stu-id="39bc0-133">Configuration</span></span>  

 <span data-ttu-id="39bc0-134">コードの代わりに次の構成を使用できます。</span><span class="sxs-lookup"><span data-stu-id="39bc0-134">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
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
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="39bc0-135">クライアント</span><span class="sxs-lookup"><span data-stu-id="39bc0-135">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="39bc0-136">コード</span><span class="sxs-lookup"><span data-stu-id="39bc0-136">Code</span></span>  

 <span data-ttu-id="39bc0-137">クライアントを作成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-137">The following code creates the client.</span></span> <span data-ttu-id="39bc0-138">バインディングではメッセージ モード セキュリティを使用し、クライアント資格情報の種類は `UserName` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-138">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="39bc0-139">ユーザー名とパスワードの指定はコードを使用する場合に限られます (構成可能ではありません)。</span><span class="sxs-lookup"><span data-stu-id="39bc0-139">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="39bc0-140">ユーザー名とパスワードを返すコードは、アプリケーション レベルで実行される必要があるため、ここには示しません。</span><span class="sxs-lookup"><span data-stu-id="39bc0-140">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="39bc0-141">たとえば、Windows フォーム ダイアログ ボックスを使用してユーザーにデータを照会します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-141">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="39bc0-142">構成</span><span class="sxs-lookup"><span data-stu-id="39bc0-142">Configuration</span></span>  

 <span data-ttu-id="39bc0-143">クライアントを構成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-143">The following code configures the client.</span></span> <span data-ttu-id="39bc0-144">バインディングではメッセージ モード セキュリティを使用し、クライアント資格情報の種類は `UserName` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39bc0-144">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="39bc0-145">ユーザー名とパスワードの指定はコードを使用する場合に限られます (構成可能ではありません)。</span><span class="sxs-lookup"><span data-stu-id="39bc0-145">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39bc0-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="39bc0-146">See also</span></span>

- [<span data-ttu-id="39bc0-147">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="39bc0-147">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="39bc0-148">メッセージ セキュリティ ユーザー名</span><span class="sxs-lookup"><span data-stu-id="39bc0-148">Message Security User Name</span></span>](../samples/message-security-user-name.md)
- [<span data-ttu-id="39bc0-149">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="39bc0-149">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="39bc0-150">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="39bc0-150">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
