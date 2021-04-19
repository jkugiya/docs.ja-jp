---
title: '方法: コード内にサービス エンドポイントを作成する'
description: クラス内でサービスを実装し、そのエンドポイントをプログラムで定義する方法について説明します。 WCF では、エンドポイントは通常、構成ファイル内で定義されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 6f5e06154ff19129da0bce77dd70736037c2dc92
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294418"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a><span data-ttu-id="f2873-104">方法: コード内にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="f2873-104">How to: Create a Service Endpoint in Code</span></span>

<span data-ttu-id="f2873-105">この例では、電卓サービスに `ICalculator` コントラクトを定義し、そのサービスを `CalculatorService` クラスに実装し、コード内でサービス エンドポイントを定義します。このエンドポイントでは、サービスが <xref:System.ServiceModel.BasicHttpBinding> クラスを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="f2873-105">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="f2873-106">通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。</span><span class="sxs-lookup"><span data-stu-id="f2873-106">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="f2873-107">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="f2873-107">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="f2873-108">一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="f2873-108">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
#### <a name="to-create-a-service-endpoint-in-code"></a><span data-ttu-id="f2873-109">コード内にサービス エンドポイントを作成するには</span><span class="sxs-lookup"><span data-stu-id="f2873-109">To create a service endpoint in code</span></span>  
  
1. <span data-ttu-id="f2873-110">サービス コントラクトを定義するインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2873-110">Create the interface that defines the service contract.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="f2873-111">手順 1. で定義したサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="f2873-111">Implement the service contract defined in step 1.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="f2873-112">アプリケーションをホストする場合は、サービスで使用するサービスとバインディングのベース アドレスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2873-112">In the hosting application, create the base address for the service and the binding to be used with the service.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="f2873-113">ホストを作成し、<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> または他のオーバーロードの 1 つを呼び出して、ホストのサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f2873-113">Create the host and call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> or one of the other overloads to add the service endpoint for the host.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     <span data-ttu-id="f2873-114">コード内ではバインディングを指定するものの、ランタイムによって提供された既定のエンドポイントを使用する場合は、<xref:System.ServiceModel.ServiceHost> の作成時にベース アドレスをコンストラクターに渡します。<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType> は呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="f2873-114">To specify the binding in code but to use the default endpoints provided by the runtime, pass the base address into the constructor when creating the <xref:System.ServiceModel.ServiceHost>, and do not call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     <span data-ttu-id="f2873-115">既定のエンドポイントの詳細については、「[簡易構成](../simplified-configuration.md)」と「[WCF サービスの簡易構成](../samples/simplified-configuration-for-wcf-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2873-115">For more information about default endpoints, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2873-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2873-116">See also</span></span>

- [<span data-ttu-id="f2873-117">方法: コード内でサービス バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="f2873-117">How to: Specify a Service Binding in Code</span></span>](../how-to-specify-a-service-binding-in-code.md)
