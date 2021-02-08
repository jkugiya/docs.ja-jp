---
description: インターネットにセキュリティで保護されていないクライアントとサービスの詳細情報
title: セキュリティで保護されていないインターネット環境のクライアントとサービス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 8b402b276c80b2e1c148de0837d8644aad7a2d4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802776"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="4d476-103">セキュリティで保護されていないインターネット環境のクライアントとサービス</span><span class="sxs-lookup"><span data-stu-id="4d476-103">Internet Unsecured Client and Service</span></span>

<span data-ttu-id="4d476-104">次の図は、セキュリティで保護されていないパブリック Windows Communication Foundation (WCF) クライアントとサービスの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="4d476-104">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![セキュリティで保護されていないインターネットシナリオを示すスクリーンショット](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="4d476-106">特徴</span><span class="sxs-lookup"><span data-stu-id="4d476-106">Characteristic</span></span>|<span data-ttu-id="4d476-107">説明</span><span class="sxs-lookup"><span data-stu-id="4d476-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4d476-108">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="4d476-108">Security Mode</span></span>|<span data-ttu-id="4d476-109">なし</span><span class="sxs-lookup"><span data-stu-id="4d476-109">None</span></span>|  
|<span data-ttu-id="4d476-110">トランスポート</span><span class="sxs-lookup"><span data-stu-id="4d476-110">Transport</span></span>|<span data-ttu-id="4d476-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="4d476-111">HTTP</span></span>|  
|<span data-ttu-id="4d476-112">バインド</span><span class="sxs-lookup"><span data-stu-id="4d476-112">Binding</span></span>|<span data-ttu-id="4d476-113"><xref:System.ServiceModel.BasicHttpBinding> コード内、または [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 構成内の要素。</span><span class="sxs-lookup"><span data-stu-id="4d476-113"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="4d476-114">相互運用性</span><span class="sxs-lookup"><span data-stu-id="4d476-114">Interoperability</span></span>|<span data-ttu-id="4d476-115">既存の Web サービス クライアントとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="4d476-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="4d476-116">認証</span><span class="sxs-lookup"><span data-stu-id="4d476-116">Authentication</span></span>|<span data-ttu-id="4d476-117">なし</span><span class="sxs-lookup"><span data-stu-id="4d476-117">None</span></span>|  
|<span data-ttu-id="4d476-118">整合性</span><span class="sxs-lookup"><span data-stu-id="4d476-118">Integrity</span></span>|<span data-ttu-id="4d476-119">なし</span><span class="sxs-lookup"><span data-stu-id="4d476-119">None</span></span>|  
|<span data-ttu-id="4d476-120">機密性</span><span class="sxs-lookup"><span data-stu-id="4d476-120">Confidentiality</span></span>|<span data-ttu-id="4d476-121">なし</span><span class="sxs-lookup"><span data-stu-id="4d476-121">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="4d476-122">サービス</span><span class="sxs-lookup"><span data-stu-id="4d476-122">Service</span></span>  

 <span data-ttu-id="4d476-123">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="4d476-123">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4d476-124">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="4d476-124">Do one of the following:</span></span>  
  
- <span data-ttu-id="4d476-125">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d476-125">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="4d476-126">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="4d476-126">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4d476-127">コード</span><span class="sxs-lookup"><span data-stu-id="4d476-127">Code</span></span>  

 <span data-ttu-id="4d476-128">次のコードは、セキュリティで保護されないエンドポイントを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4d476-128">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="4d476-129">既定では、<xref:System.ServiceModel.BasicHttpBinding> のセキュリティ モードは <xref:System.ServiceModel.BasicHttpSecurityMode.None> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4d476-129">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="4d476-130">サービス構成</span><span class="sxs-lookup"><span data-stu-id="4d476-130">Service Configuration</span></span>  

 <span data-ttu-id="4d476-131">次のコードは、構成を使用して同一のエンドポイントをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="4d476-131">The following code sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="4d476-132">クライアント</span><span class="sxs-lookup"><span data-stu-id="4d476-132">Client</span></span>  

 <span data-ttu-id="4d476-133">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="4d476-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4d476-134">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="4d476-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="4d476-135">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d476-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="4d476-136">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d476-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="4d476-137">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d476-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="4d476-138">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4d476-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="4d476-139">コード</span><span class="sxs-lookup"><span data-stu-id="4d476-139">Code</span></span>  

 <span data-ttu-id="4d476-140">次のコードは、セキュリティで保護されていないエンドポイントにアクセスする基本的な WCF クライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="4d476-140">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="4d476-141">クライアント構成</span><span class="sxs-lookup"><span data-stu-id="4d476-141">Client Configuration</span></span>  

 <span data-ttu-id="4d476-142">クライアントを構成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4d476-142">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d476-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d476-143">See also</span></span>

- [<span data-ttu-id="4d476-144">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="4d476-144">Common Security Scenarios</span></span>](common-security-scenarios.md)
- [<span data-ttu-id="4d476-145">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="4d476-145">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="4d476-146">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4d476-146">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
