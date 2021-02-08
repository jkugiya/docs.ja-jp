---
description: '詳細については、「方法: チャネルファクトリを使用して操作を非同期に呼び出す」を参照してください。'
title: '方法: チャネル ファクトリを使用して、非同期的に操作を呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 081211d0202550e93e3aabb5c8b5b5b5adbcdcde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780194"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="aeb2e-103">方法: チャネル ファクトリを使用して、非同期的に操作を呼び出す</span><span class="sxs-lookup"><span data-stu-id="aeb2e-103">How to: Call Operations Asynchronously Using a Channel Factory</span></span>

<span data-ttu-id="aeb2e-104">ここでは、<xref:System.ServiceModel.ChannelFactory%601> ベースのクライアント アプリケーションを使用する場合に、クライアントからサービス操作に非同期にアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-104">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="aeb2e-105">サービスを呼び出すために <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> オブジェクトを使用する場合は、イベント ドリブンの非同期呼び出しモデルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-105">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="aeb2e-106">詳細については、「 [方法: サービス操作を非同期に呼び出す](how-to-call-wcf-service-operations-asynchronously.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-106">For more information, see [How to: Call Service Operations Asynchronously](how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="aeb2e-107">イベントベースの非同期呼び出しモデルの詳細については、「 [イベントベースの非同期パターン (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-107">For more information about the event-based asynchronous calling model, see [Event-based Asynchronous Pattern (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)</span></span>  
  
 <span data-ttu-id="aeb2e-108">このトピックのサービスは、`ICalculator` インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-108">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="aeb2e-109">クライアントはこのインターフェイスにある操作を非同期に呼び出すことができます。これはたとえば `Add` という操作を `BeginAdd` と `EndAdd` の 2 つのメソッドに分割できることを意味します。前者によって呼び出しを開始し、後者によって操作の完了時に結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-109">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="aeb2e-110">サービスで操作を非同期に実装する方法を示す例については、「 [方法: 非同期サービス操作を実装](../how-to-implement-an-asynchronous-service-operation.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-110">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="aeb2e-111">同期操作と非同期操作の詳細については、「 [同期操作と非同期操作](../synchronous-and-asynchronous-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-111">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="aeb2e-112">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="aeb2e-112">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="aeb2e-113">WCF サービス操作を非同期に呼び出すには</span><span class="sxs-lookup"><span data-stu-id="aeb2e-113">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="aeb2e-114">次のコマンドに示すように、オプションを指定して [ServiceModel Metadata Utility tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) ツールを実行し `/async` ます。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-114">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="aeb2e-115">これにより、操作の非同期クライアント版のサービス コントラクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-115">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2. <span data-ttu-id="aeb2e-116">次のサンプル コードに示すように、非同期操作の完了時に呼び出されるコールバック関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-116">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. <span data-ttu-id="aeb2e-117">サービス操作に非同期にアクセスするには、次のサンプル コードに示すように、クライアントを作成して `Begin[Operation]` (たとえば `BeginAdd`) を呼び出し、コールバック関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-117">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="aeb2e-118">コールバック関数が実行されると、クライアントは `End<operation>` (`EndAdd` など) を呼び出して結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-118">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeb2e-119">例</span><span class="sxs-lookup"><span data-stu-id="aeb2e-119">Example</span></span>  

 <span data-ttu-id="aeb2e-120">上記の手順で使用したクライアント コードで使用するサービスは、次のコードに示すように `ICalculator` インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-120">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="aeb2e-121">サービス側では、 `Add` `Subtract` 前のクライアントの手順がクライアント上で非同期に呼び出されている場合でも、コントラクトの操作と操作は、WINDOWS COMMUNICATION FOUNDATION (WCF) の実行時によって同期的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-121">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the Windows Communication Foundation (WCF) run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="aeb2e-122">`Multiply` 操作と `Divide` 操作は、クライアントで同期して呼び出される場合でも、サービス側ではサービスを非同期に呼び出すように使用されます。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-122">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="aeb2e-123">この例では、<xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-123">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="aeb2e-124">このプロパティ設定は、.NET Framework 非同期パターンの実装と組み合わせて、操作を非同期的に呼び出すように実行時に指示します。</span><span class="sxs-lookup"><span data-stu-id="aeb2e-124">This property setting, in combination with the implementation of the .NET Framework asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
