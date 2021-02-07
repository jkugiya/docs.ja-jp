---
description: '詳細情報: Windows クライアントを使用したメッセージセキュリティ'
title: Windows クライアントとのメッセージ セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: 97d415f68b4374ab2b18360347d7753f6be51313
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756098"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="afeed-103">Windows クライアントとのメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="afeed-103">Message Security with a Windows Client</span></span>

<span data-ttu-id="afeed-104">このシナリオは、メッセージセキュリティモードによってセキュリティ保護された Windows Communication Foundation (WCF) クライアントおよびサーバーを示しています。</span><span class="sxs-lookup"><span data-stu-id="afeed-104">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="afeed-105">クライアントとサービスは、Windows 資格情報を使用して認証します。</span><span class="sxs-lookup"><span data-stu-id="afeed-105">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="afeed-106">![Windows クライアントを使用したメッセージセキュリティ](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="afeed-106">![Message security with a Windows client](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="afeed-107">特徴</span><span class="sxs-lookup"><span data-stu-id="afeed-107">Characteristic</span></span>|<span data-ttu-id="afeed-108">説明</span><span class="sxs-lookup"><span data-stu-id="afeed-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="afeed-109">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="afeed-109">Security Mode</span></span>|<span data-ttu-id="afeed-110">Message</span><span class="sxs-lookup"><span data-stu-id="afeed-110">Message</span></span>|  
|<span data-ttu-id="afeed-111">相互運用性</span><span class="sxs-lookup"><span data-stu-id="afeed-111">Interoperability</span></span>|<span data-ttu-id="afeed-112">WCF のみ</span><span class="sxs-lookup"><span data-stu-id="afeed-112">WCF Only</span></span>|  
|<span data-ttu-id="afeed-113">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="afeed-113">Authentication (Server)</span></span>|<span data-ttu-id="afeed-114">サーバーとクライアントの相互認証</span><span class="sxs-lookup"><span data-stu-id="afeed-114">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="afeed-115">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="afeed-115">Authentication (Client)</span></span>|<span data-ttu-id="afeed-116">サーバーとクライアントの相互認証</span><span class="sxs-lookup"><span data-stu-id="afeed-116">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="afeed-117">整合性</span><span class="sxs-lookup"><span data-stu-id="afeed-117">Integrity</span></span>|<span data-ttu-id="afeed-118">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="afeed-118">Yes, using shared security context</span></span>|  
|<span data-ttu-id="afeed-119">機密性</span><span class="sxs-lookup"><span data-stu-id="afeed-119">Confidentiality</span></span>|<span data-ttu-id="afeed-120">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="afeed-120">Yes, using shared security context</span></span>|  
|<span data-ttu-id="afeed-121">トランスポート</span><span class="sxs-lookup"><span data-stu-id="afeed-121">Transport</span></span>|<span data-ttu-id="afeed-122">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="afeed-122">NET.TCP</span></span>|  
|<span data-ttu-id="afeed-123">バインド</span><span class="sxs-lookup"><span data-stu-id="afeed-123">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="afeed-124">サービス</span><span class="sxs-lookup"><span data-stu-id="afeed-124">Service</span></span>  

 <span data-ttu-id="afeed-125">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="afeed-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="afeed-126">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="afeed-126">Do one of the following:</span></span>  
  
- <span data-ttu-id="afeed-127">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="afeed-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="afeed-128">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="afeed-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="afeed-129">コード</span><span class="sxs-lookup"><span data-stu-id="afeed-129">Code</span></span>  

 <span data-ttu-id="afeed-130">次のコードでは、メッセージ セキュリティを使用するサービス エンドポイントを作成し、Windows コンピューターとの間にセキュリティで保護されたコンテキストを確立する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="afeed-130">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="afeed-131">構成</span><span class="sxs-lookup"><span data-stu-id="afeed-131">Configuration</span></span>  

 <span data-ttu-id="afeed-132">コードの代わりに次の構成を使用して、サービスをセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="afeed-132">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="afeed-133">クライアント</span><span class="sxs-lookup"><span data-stu-id="afeed-133">Client</span></span>  

 <span data-ttu-id="afeed-134">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="afeed-134">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="afeed-135">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="afeed-135">Do one of the following:</span></span>  
  
- <span data-ttu-id="afeed-136">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="afeed-136">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="afeed-137">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="afeed-137">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="afeed-138">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="afeed-138">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="afeed-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="afeed-139">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="afeed-140">コード</span><span class="sxs-lookup"><span data-stu-id="afeed-140">Code</span></span>  

 <span data-ttu-id="afeed-141">クライアントを作成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="afeed-141">The following code creates a client.</span></span> <span data-ttu-id="afeed-142">バインディングはメッセージ モード セキュリティに対して行い、クライアント資格情報の種類は `Windows` に設定します。</span><span class="sxs-lookup"><span data-stu-id="afeed-142">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="afeed-143">構成</span><span class="sxs-lookup"><span data-stu-id="afeed-143">Configuration</span></span>  

 <span data-ttu-id="afeed-144">次の構成を使用してクライアントのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="afeed-144">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="afeed-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="afeed-145">See also</span></span>

- [<span data-ttu-id="afeed-146">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="afeed-146">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="afeed-147">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="afeed-147">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
