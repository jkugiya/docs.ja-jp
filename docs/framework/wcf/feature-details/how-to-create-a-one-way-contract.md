---
description: '詳細については、「方法: One-Way コントラクトを作成する」を参照してください。'
title: '方法: 一方向コントラクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 465dc2da20288c918a70743fcbe3ed931620b33b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734725"
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="efe7b-103">方法: 一方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="efe7b-103">How to: Create a One-Way Contract</span></span>

<span data-ttu-id="efe7b-104">ここでは、一方向コントラクトを使用するメソッドを作成するための基本手順を示します。</span><span class="sxs-lookup"><span data-stu-id="efe7b-104">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="efe7b-105">このようなメソッドは、クライアントから Windows Communication Foundation (WCF) サービスに対して操作を呼び出しますが、応答を想定していません。</span><span class="sxs-lookup"><span data-stu-id="efe7b-105">Such methods invoke operations on a Windows Communication Foundation (WCF) service from a client but do not expect a reply.</span></span> <span data-ttu-id="efe7b-106">この種のコントラクトは、たとえば、多数のサブスクライバーに対して通知を発行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="efe7b-106">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="efe7b-107">一方向コントラクトは、二重のコントラクトを作成する場合にも使用できます。その場合は、クライアントとサーバーが互いに独立して通信できるため、どちらからでも相手の呼び出しを開始できます。</span><span class="sxs-lookup"><span data-stu-id="efe7b-107">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="efe7b-108">これにより、特にサーバーは、クライアントがイベントとして処理できる一方向の呼び出しをクライアントに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="efe7b-108">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="efe7b-109">一方向メソッドの指定の詳細については、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティおよび <xref:System.ServiceModel.OperationContractAttribute> クラスのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe7b-109">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 <span data-ttu-id="efe7b-110">双方向コントラクト用のクライアントアプリケーションの作成の詳細については、「 [方法: One-Way と Request-Reply のコントラクトを使用してサービスにアクセスする](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe7b-110">For more information about creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="efe7b-111">実際のサンプルについては、 [一方向](../samples/one-way.md) のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe7b-111">For a working sample, see the [One-Way](../samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="efe7b-112">一方向コントラクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="efe7b-112">To create a one-way contract</span></span>  
  
1. <span data-ttu-id="efe7b-113">サービスにより実装されるメソッドを定義するインターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用することにより、サービス コントラクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="efe7b-113">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2. <span data-ttu-id="efe7b-114"><xref:System.ServiceModel.OperationContractAttribute> クラスをメソッドに適用する際に、クライアントが呼び出すことのできるインターフェイスのメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="efe7b-114">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3. <span data-ttu-id="efe7b-115"><xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `true` に設定することにより、出力を行わない (戻り値および出力または参照パラメーターを持たない) 一方向の操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="efe7b-115">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="efe7b-116"><xref:System.ServiceModel.OperationContractAttribute> プロパティの既定値は <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> であるため、`false` クラスを持つ操作では、既定で要求/応答コントラクトが満たされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="efe7b-116">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="efe7b-117">したがって、このメソッドに一方向コントラクトが必要な場合は、この属性プロパティの値を明示的に `true` に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efe7b-117">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efe7b-118">例</span><span class="sxs-lookup"><span data-stu-id="efe7b-118">Example</span></span>  

 <span data-ttu-id="efe7b-119">複数の一方向メソッドを含むサービスのコントラクトを定義する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="efe7b-119">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="efe7b-120">`Equals` (既定で応答/要求コントラクトに設定され、結果を返します) を除き、すべてのメソッドは一方向コントラクトを持ちます。</span><span class="sxs-lookup"><span data-stu-id="efe7b-120">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="efe7b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="efe7b-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="efe7b-122">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="efe7b-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="efe7b-123">方法: サービス コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="efe7b-123">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="efe7b-124">セッション</span><span class="sxs-lookup"><span data-stu-id="efe7b-124">Session</span></span>](../samples/session.md)
- [<span data-ttu-id="efe7b-125">方法: 双方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="efe7b-125">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
