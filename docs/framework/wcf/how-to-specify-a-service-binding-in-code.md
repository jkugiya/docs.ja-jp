---
description: '詳細については、「方法: コード内でサービスバインディングを指定する」を参照してください。'
title: '方法: コード内でサービス バインディングを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 744919fee4ec28d7df4581ac1d608d1fa9e99a29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755942"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="bfd67-103">方法: コード内でサービス バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="bfd67-103">How to: Specify a Service Binding in Code</span></span>

<span data-ttu-id="bfd67-104">この例では、電卓サービスに `ICalculator` コントラクトを定義し、そのサービスを `CalculatorService` クラスに実装し、コード内でサービス エンドポイントを定義します。このエンドポイントでは、サービスが <xref:System.ServiceModel.BasicHttpBinding> クラスを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="bfd67-104">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="bfd67-105">通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。</span><span class="sxs-lookup"><span data-stu-id="bfd67-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="bfd67-106">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="bfd67-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="bfd67-107">一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="bfd67-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="bfd67-108">コードの代わりに構成要素を使用してこのサービスを構成する方法の詳細については、「 [方法: 構成でサービスバインディングを指定](how-to-specify-a-service-binding-in-configuration.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfd67-108">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="bfd67-109">サービスで BasicHttpBinding が使用されるようにコードで指定するには</span><span class="sxs-lookup"><span data-stu-id="bfd67-109">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="bfd67-110">サービスの種類にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="bfd67-110">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="bfd67-111">サービス クラスにサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="bfd67-111">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="bfd67-112">ホスト アプリケーションで、サービスのベース アドレスとサービスで使用するバインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="bfd67-112">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="bfd67-113">サービスのホストを作成し、エンドポイントを追加して、ホストを開きます。</span><span class="sxs-lookup"><span data-stu-id="bfd67-113">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="bfd67-114">バインディング プロパティの既定値を変更するには</span><span class="sxs-lookup"><span data-stu-id="bfd67-114">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="bfd67-115"><xref:System.ServiceModel.BasicHttpBinding> クラスの既定のプロパティ値を変更するには、ホストを作成する前に、バインディングのプロパティ値を新しい値に設定します。</span><span class="sxs-lookup"><span data-stu-id="bfd67-115">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="bfd67-116">たとえば、開くおよび閉じる操作の既定のタイムアウト値を 1 分から 2 分に変更するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="bfd67-116">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="bfd67-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfd67-117">See also</span></span>

- [<span data-ttu-id="bfd67-118">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="bfd67-118">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bfd67-119">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="bfd67-119">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
