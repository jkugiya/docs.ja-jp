---
description: '詳細については、「方法: Request-Reply コントラクトを作成する」を参照してください。'
title: '方法: 要求/応答コントラクトを作成する'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: f5e63538a405aa451ffd3be114485604c00fa407
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734699"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="415fb-103">方法: 要求/応答コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="415fb-103">How to: Create a Request-Reply Contract</span></span>

<span data-ttu-id="415fb-104">要求/応答コントラクトは、応答を返すメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="415fb-104">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="415fb-105">応答が送信され、このコントラクトの条件の下で要求に関連付けられる必要があります。</span><span class="sxs-lookup"><span data-stu-id="415fb-105">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="415fb-106">メソッドが応答を返さない場合 (C# の場合は `void` または Visual Basic の場合は `Sub`) でも、インフラストラクチャは、空のメッセージを作成して送信することで、メソッドが返ったことを呼び出し元に示します。</span><span class="sxs-lookup"><span data-stu-id="415fb-106">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="415fb-107">空の応答メッセージが送信されるのを防ぐには、操作で 1 方向コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="415fb-107">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="415fb-108">要求/応答コントラクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="415fb-108">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="415fb-109">選択したプログラミング言語でインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="415fb-109">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="415fb-110">インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="415fb-110">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="415fb-111">クライアントが呼び出すことのできる各メソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="415fb-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="415fb-112">任意。</span><span class="sxs-lookup"><span data-stu-id="415fb-112">Optional.</span></span> <span data-ttu-id="415fb-113"><xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティの値を `true` に設定して、空の応答メッセージが送信されることを防止します。</span><span class="sxs-lookup"><span data-stu-id="415fb-113">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="415fb-114">既定では、すべての操作は要求/応答コントラクトです。</span><span class="sxs-lookup"><span data-stu-id="415fb-114">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="415fb-115">例</span><span class="sxs-lookup"><span data-stu-id="415fb-115">Example</span></span>  

 <span data-ttu-id="415fb-116">次のサンプルは、`Add` メソッドと `Subtract` メソッドを提供する電卓サービスのコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="415fb-116">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="415fb-117">`Multiply` メソッドは <xref:System.ServiceModel.OperationContractAttribute> クラスでマークされていないため、このコントラクトの一部ではありません。したがって、クライアントからはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="415fb-117">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- <span data-ttu-id="415fb-118">操作コントラクトを指定する方法の詳細については、 <xref:System.ServiceModel.OperationContractAttribute> クラスとプロパティを参照してください <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 。</span><span class="sxs-lookup"><span data-stu-id="415fb-118">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="415fb-119"><xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性を適用すると、サービスを展開した後に Web サービス記述言語 (WSDL) ドキュメントでサービス コントラクト定義が自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="415fb-119">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="415fb-120">ドキュメントは、サービスの HTTP ベース アドレスに `?wsdl` を付け加えてしてダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="415fb-120">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="415fb-121">たとえば、`http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="415fb-121">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415fb-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="415fb-122">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="415fb-123">サービス コントラクトの設計</span><span class="sxs-lookup"><span data-stu-id="415fb-123">Designing Service Contracts</span></span>](../designing-service-contracts.md)
- [<span data-ttu-id="415fb-124">方法: 双方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="415fb-124">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
