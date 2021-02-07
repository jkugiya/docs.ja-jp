---
description: 詳細については、「匿名クライアントを使用したメッセージセキュリティ」を参照してください。
title: メッセージ セキュリティと匿名クライアント
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 921ddd9e8e7d2a860f3516c452870bc2bb150911
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726976"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="71c3e-103">メッセージ セキュリティと匿名クライアント</span><span class="sxs-lookup"><span data-stu-id="71c3e-103">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="71c3e-104">次のシナリオは、Windows Communication Foundation (WCF) メッセージセキュリティによってセキュリティ保護されたクライアントとサービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="71c3e-104">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="71c3e-105">設計目標は、トランスポート セキュリティではなくメッセージ セキュリティを使用することです。これによって将来、多様なクレームに基づくモデルをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="71c3e-105">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="71c3e-106">高度な要求を使用した承認の詳細については、「 [Id モデルを使用したクレームと承認の管理](managing-claims-and-authorization-with-the-identity-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71c3e-106">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="71c3e-107">サンプルアプリケーションについては、「 [メッセージセキュリティ匿名](../samples/message-security-anonymous.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71c3e-107">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="71c3e-108">![匿名クライアントを使用したメッセージセキュリティ](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="71c3e-108">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="71c3e-109">特徴</span><span class="sxs-lookup"><span data-stu-id="71c3e-109">Characteristic</span></span>|<span data-ttu-id="71c3e-110">説明</span><span class="sxs-lookup"><span data-stu-id="71c3e-110">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="71c3e-111">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="71c3e-111">Security Mode</span></span>|<span data-ttu-id="71c3e-112">Message</span><span class="sxs-lookup"><span data-stu-id="71c3e-112">Message</span></span>|
|<span data-ttu-id="71c3e-113">相互運用性</span><span class="sxs-lookup"><span data-stu-id="71c3e-113">Interoperability</span></span>|<span data-ttu-id="71c3e-114">WCF のみ</span><span class="sxs-lookup"><span data-stu-id="71c3e-114">WCF only</span></span>|
|<span data-ttu-id="71c3e-115">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="71c3e-115">Authentication (Server)</span></span>|<span data-ttu-id="71c3e-116">初期ネゴシエーションには、サーバー認証が必要ですが、クライアント認証は不要です</span><span class="sxs-lookup"><span data-stu-id="71c3e-116">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="71c3e-117">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="71c3e-117">Authentication (Client)</span></span>|<span data-ttu-id="71c3e-118">なし</span><span class="sxs-lookup"><span data-stu-id="71c3e-118">None</span></span>|
|<span data-ttu-id="71c3e-119">整合性</span><span class="sxs-lookup"><span data-stu-id="71c3e-119">Integrity</span></span>|<span data-ttu-id="71c3e-120">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="71c3e-120">Yes, using shared security context</span></span>|
|<span data-ttu-id="71c3e-121">機密性</span><span class="sxs-lookup"><span data-stu-id="71c3e-121">Confidentiality</span></span>|<span data-ttu-id="71c3e-122">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="71c3e-122">Yes, using shared security context</span></span>|
|<span data-ttu-id="71c3e-123">トランスポート</span><span class="sxs-lookup"><span data-stu-id="71c3e-123">Transport</span></span>|<span data-ttu-id="71c3e-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="71c3e-124">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="71c3e-125">サービス</span><span class="sxs-lookup"><span data-stu-id="71c3e-125">Service</span></span>

<span data-ttu-id="71c3e-126">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="71c3e-127">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-127">Do one of the following:</span></span>

- <span data-ttu-id="71c3e-128">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="71c3e-129">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="71c3e-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="71c3e-130">コード</span><span class="sxs-lookup"><span data-stu-id="71c3e-130">Code</span></span>

<span data-ttu-id="71c3e-131">次のコードは、メッセージ セキュリティを使用するサービス エンドポイントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-131">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="71c3e-132">構成</span><span class="sxs-lookup"><span data-stu-id="71c3e-132">Configuration</span></span>

<span data-ttu-id="71c3e-133">コードの代わりに次の構成を使用できます。</span><span class="sxs-lookup"><span data-stu-id="71c3e-133">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="71c3e-134">サービス動作要素を使用して、クライアントに対するサービスの認証に使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-134">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="71c3e-135">サービス要素は、`behaviorConfiguration` 属性を使用して動作を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71c3e-135">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="71c3e-136">バインド要素で、クライアント資格情報の種類が `None` であることを指定します。この資格情報の種類では、匿名クライアントがサービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="71c3e-136">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="71c3e-137">クライアント</span><span class="sxs-lookup"><span data-stu-id="71c3e-137">Client</span></span>

<span data-ttu-id="71c3e-138">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="71c3e-139">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-139">Do one of the following:</span></span>

- <span data-ttu-id="71c3e-140">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="71c3e-141">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="71c3e-142">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="71c3e-143">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-143">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="71c3e-144">コード</span><span class="sxs-lookup"><span data-stu-id="71c3e-144">Code</span></span>

<span data-ttu-id="71c3e-145">クライアントのインスタンスを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-145">The following code creates an instance of the client.</span></span> <span data-ttu-id="71c3e-146">バインディングはメッセージ モード セキュリティを使用し、クライアント資格情報の種類は None に設定されます。</span><span class="sxs-lookup"><span data-stu-id="71c3e-146">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="71c3e-147">構成</span><span class="sxs-lookup"><span data-stu-id="71c3e-147">Configuration</span></span>

<span data-ttu-id="71c3e-148">クライアントを構成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="71c3e-148">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
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
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="71c3e-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="71c3e-149">See also</span></span>

- [<span data-ttu-id="71c3e-150">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="71c3e-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="71c3e-151">分散アプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="71c3e-151">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="71c3e-152">メッセージ セキュリティ匿名</span><span class="sxs-lookup"><span data-stu-id="71c3e-152">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="71c3e-153">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="71c3e-153">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="71c3e-154">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="71c3e-154">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
