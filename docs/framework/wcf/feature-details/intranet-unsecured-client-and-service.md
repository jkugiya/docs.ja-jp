---
description: '詳細情報: イントラネットのセキュリティで保護されていないクライアントとサービス'
title: セキュリティで保護されていないイントラネットのクライアントとサービス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: a03abc5b8eb0317c4d5d19347b3974d615570069
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704525"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="9be5c-103">セキュリティで保護されていないイントラネットのクライアントとサービス</span><span class="sxs-lookup"><span data-stu-id="9be5c-103">Intranet Unsecured Client and Service</span></span>

<span data-ttu-id="9be5c-104">次の図は、セキュリティで保護されたプライベートネットワークに関する情報を WCF アプリケーションに提供するために開発された simple Windows Communication Foundation (WCF) サービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9be5c-104">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="9be5c-105">データが重要度の低い、ネットワークが本質的にセキュリティで保護されている、または WCF インフラストラクチャの下にあるレイヤーによってセキュリティが提供されるため、セキュリティは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9be5c-105">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![イントラネットのセキュリティで保護されていないクライアントとサービスのシナリオ。](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="9be5c-107">特徴</span><span class="sxs-lookup"><span data-stu-id="9be5c-107">Characteristic</span></span>|<span data-ttu-id="9be5c-108">説明</span><span class="sxs-lookup"><span data-stu-id="9be5c-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9be5c-109">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="9be5c-109">Security Mode</span></span>|<span data-ttu-id="9be5c-110">なし</span><span class="sxs-lookup"><span data-stu-id="9be5c-110">None</span></span>|  
|<span data-ttu-id="9be5c-111">トランスポート</span><span class="sxs-lookup"><span data-stu-id="9be5c-111">Transport</span></span>|<span data-ttu-id="9be5c-112">TCP</span><span class="sxs-lookup"><span data-stu-id="9be5c-112">TCP</span></span>|  
|<span data-ttu-id="9be5c-113">バインド</span><span class="sxs-lookup"><span data-stu-id="9be5c-113">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="9be5c-114">相互運用性</span><span class="sxs-lookup"><span data-stu-id="9be5c-114">Interoperability</span></span>|<span data-ttu-id="9be5c-115">WCF のみ</span><span class="sxs-lookup"><span data-stu-id="9be5c-115">WCF only</span></span>|  
|<span data-ttu-id="9be5c-116">認証</span><span class="sxs-lookup"><span data-stu-id="9be5c-116">Authentication</span></span>|<span data-ttu-id="9be5c-117">なし</span><span class="sxs-lookup"><span data-stu-id="9be5c-117">None</span></span>|  
|<span data-ttu-id="9be5c-118">整合性</span><span class="sxs-lookup"><span data-stu-id="9be5c-118">Integrity</span></span>|<span data-ttu-id="9be5c-119">なし</span><span class="sxs-lookup"><span data-stu-id="9be5c-119">None</span></span>|  
|<span data-ttu-id="9be5c-120">機密性</span><span class="sxs-lookup"><span data-stu-id="9be5c-120">Confidentiality</span></span>|<span data-ttu-id="9be5c-121">なし</span><span class="sxs-lookup"><span data-stu-id="9be5c-121">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="9be5c-122">サービス</span><span class="sxs-lookup"><span data-stu-id="9be5c-122">Service</span></span>  

 <span data-ttu-id="9be5c-123">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-123">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="9be5c-124">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-124">Do one of the following:</span></span>  
  
- <span data-ttu-id="9be5c-125">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-125">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="9be5c-126">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="9be5c-126">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9be5c-127">コード</span><span class="sxs-lookup"><span data-stu-id="9be5c-127">Code</span></span>  

 <span data-ttu-id="9be5c-128">次のコードは、セキュリティで保護されないエンドポイントを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9be5c-128">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="9be5c-129">構成</span><span class="sxs-lookup"><span data-stu-id="9be5c-129">Configuration</span></span>  

 <span data-ttu-id="9be5c-130">次のコードは、次に示す構成を使用して同一のエンドポイントをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="9be5c-130">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="9be5c-131">クライアント</span><span class="sxs-lookup"><span data-stu-id="9be5c-131">Client</span></span>  

 <span data-ttu-id="9be5c-132">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="9be5c-133">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="9be5c-134">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="9be5c-135">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="9be5c-136">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="9be5c-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9be5c-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="9be5c-138">コード</span><span class="sxs-lookup"><span data-stu-id="9be5c-138">Code</span></span>  

 <span data-ttu-id="9be5c-139">次のコードは、TCP プロトコルを使用してセキュリティで保護されていないエンドポイントにアクセスする基本的な WCF クライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="9be5c-139">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="9be5c-140">構成</span><span class="sxs-lookup"><span data-stu-id="9be5c-140">Configuration</span></span>  

 <span data-ttu-id="9be5c-141">次の構成コードは、クライアントに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9be5c-141">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9be5c-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="9be5c-142">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="9be5c-143">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="9be5c-143">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="9be5c-144">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9be5c-144">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
