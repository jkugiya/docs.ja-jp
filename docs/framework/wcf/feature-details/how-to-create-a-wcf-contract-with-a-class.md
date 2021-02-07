---
description: '詳細については、「方法: クラスを使用して Windows Communication Foundation コントラクトを作成する」を参照してください。'
title: '方法 : クラスを使用して Windows Communication Foundation コントラクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 63a5cc4e6a7966af69f2d5f3c7db0c7f4e313faf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756163"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="1d65e-103">方法 : クラスを使用して Windows Communication Foundation コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="1d65e-103">How to: Create a Windows Communication Foundation Contract with a Class</span></span>

<span data-ttu-id="1d65e-104">Windows Communication Foundation (WCF) コントラクトを作成する場合は、インターフェイスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1d65e-104">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="1d65e-105">詳細については、「 [方法: サービスコントラクトを定義](../how-to-define-a-wcf-service-contract.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d65e-105">For more information, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="1d65e-106">ここで説明する代替方法では、クラスを作成してから、<xref:System.ServiceModel.ServiceContractAttribute> 属性を直接そのクラスに適用し、<xref:System.ServiceModel.OperationContractAttribute> 属性をコントラクトに含まれるクラス内の各メソッドに適用します。</span><span class="sxs-lookup"><span data-stu-id="1d65e-106">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1d65e-107">`[ServiceContract]` と `[ServiceContractAttribute]` は、同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="1d65e-107">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="1d65e-108">とについても同じことが当てはまり `[OperationContract]` `[OperationContractAttribute]` ます。</span><span class="sxs-lookup"><span data-stu-id="1d65e-108">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="1d65e-109">どちらの場合も、前者は後者の短縮形です。</span><span class="sxs-lookup"><span data-stu-id="1d65e-109">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="1d65e-110">サービスコントラクトの詳細については、「 [サービスコントラクトの設計](../designing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d65e-110">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="1d65e-111">クラスを使用した Windows Communication Foundation コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="1d65e-111">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="1d65e-112">Visual Basic、C#、またはその他の共通言語ランタイム言語を使用して、新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d65e-112">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="1d65e-113">クラスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="1d65e-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="1d65e-114">クラスでメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d65e-114">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="1d65e-115"><xref:System.ServiceModel.OperationContractAttribute>パブリック WCF コントラクトの一部として公開する必要がある各メソッドにクラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="1d65e-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d65e-116">例</span><span class="sxs-lookup"><span data-stu-id="1d65e-116">Example</span></span>  

 <span data-ttu-id="1d65e-117">次のコード例は、サービス コントラクトを定義するクラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="1d65e-117">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="1d65e-118"><xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求/応答メッセージ パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="1d65e-118">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="1d65e-119">このメッセージパターンの詳細については、「 [方法: Request-Reply コントラクトを作成](how-to-create-a-request-reply-contract.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d65e-119">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="1d65e-120">属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1d65e-120">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="1d65e-121">その他の例については、「 [方法: One-Way コントラクトを作成](how-to-create-a-one-way-contract.md) する」および「 [方法: 双方向コントラクトを作成する](how-to-create-a-duplex-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d65e-121">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d65e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d65e-122">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
