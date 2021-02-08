---
description: '詳細については、「方法: コントラクトインターフェイスを使用してサービスを作成する」を参照してください。'
title: '方法: コントラクト インターフェイスを使用してサービスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 5080f6bb45030811b87f952fb62a74801bc1ef88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793832"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="1ad4c-103">方法: コントラクト インターフェイスを使用してサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="1ad4c-103">How to: Create a Service with a Contract Interface</span></span>

<span data-ttu-id="1ad4c-104">Windows Communication Foundation (WCF) コントラクトを作成するには、インターフェイスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-104">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="1ad4c-105">このコントラクトでは、サービスが提供する操作にアクセスするために必要なメッセージのコレクションと構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-105">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="1ad4c-106">このインターフェイスでは、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用し、公開するメソッドに <xref:System.ServiceModel.OperationContractAttribute> クラスを適用して、入力と出力の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-106">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="1ad4c-107">サービスコントラクトの詳細については、「 [サービスコントラクトの設計](../designing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-107">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="1ad4c-108">インターフェイスを使用した WCF コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="1ad4c-108">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="1ad4c-109">Visual Basic、C#、またはその他の共通言語ランタイム言語を使用して、新しいインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-109">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="1ad4c-110">インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-110">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="1ad4c-111">インターフェイスのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-111">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="1ad4c-112"><xref:System.ServiceModel.OperationContractAttribute>パブリック WCF コントラクトの一部として公開する必要がある各メソッドにクラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-112">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ad4c-113">例</span><span class="sxs-lookup"><span data-stu-id="1ad4c-113">Example</span></span>  

 <span data-ttu-id="1ad4c-114">次のコード例は、サービス コントラクトを定義するインターフェイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-114">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="1ad4c-115"><xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求/応答メッセージ パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-115">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="1ad4c-116">このメッセージパターンの詳細については、「 [方法: Request-Reply コントラクトを作成](how-to-create-a-request-reply-contract.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-116">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="1ad4c-117">属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-117">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="1ad4c-118">その他の例については、「 [方法: One-Way コントラクトを作成](how-to-create-a-one-way-contract.md) する」および「 [方法: 双方向コントラクトを作成する](how-to-create-a-duplex-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ad4c-118">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad4c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ad4c-119">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
