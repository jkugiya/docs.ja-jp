---
description: '詳細については、「方法: 双方向コントラクトを使用してサービスにアクセスする」を参照してください。'
title: '方法: 双方向コントラクトを使用してサービスにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: e58225e6b77115004c3c201d606e328aab184b75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742889"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="372ee-103">方法: 双方向コントラクトを使用してサービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="372ee-103">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="372ee-104">Windows Communication Foundation (WCF) の1つの機能は、双方向のメッセージングパターンを使用するサービスを作成する機能です。</span><span class="sxs-lookup"><span data-stu-id="372ee-104">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="372ee-105">双方向のメッセージング パターンを使用するサービスは、コールバックを通じてクライアントと通信できます。</span><span class="sxs-lookup"><span data-stu-id="372ee-105">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="372ee-106">このトピックでは、コールバックインターフェイスを実装するクライアントクラスで WCF クライアントを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="372ee-106">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="372ee-107">二重バインディングでは、クライアントの IP アドレスをサービスに公開します。</span><span class="sxs-lookup"><span data-stu-id="372ee-107">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="372ee-108">クライアントは、セキュリティを使用して信頼するサービスだけに接続できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="372ee-108">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="372ee-109">基本的な WCF サービスとクライアントの作成に関するチュートリアルについては、 [はじめにチュートリアル](../getting-started-tutorial.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="372ee-109">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="372ee-110">双方向サービスにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="372ee-110">To access a duplex service</span></span>

1. <span data-ttu-id="372ee-111">2 つのインターフェイスを含むサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="372ee-111">Create a service that contains two interfaces.</span></span> <span data-ttu-id="372ee-112">1 つ目のインターフェイスはサービスに使用し、2 つ目のインターフェイスはコールバックに使用します。</span><span class="sxs-lookup"><span data-stu-id="372ee-112">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="372ee-113">双方向サービスの作成の詳細については、「 [方法: 双方向コントラクトを作成](how-to-create-a-duplex-contract.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="372ee-113">For more information about creating a duplex service, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="372ee-114">サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="372ee-114">Run the service.</span></span>

3. <span data-ttu-id="372ee-115">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、クライアントのコントラクト (インターフェイス) を生成します。</span><span class="sxs-lookup"><span data-stu-id="372ee-115">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="372ee-116">この方法の詳細については、「  [方法: クライアントを作成](../how-to-create-a-wcf-client.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="372ee-116">For information about how to do this, see  [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="372ee-117">次の例に示すように、クライアント クラスにコールバック インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="372ee-117">Implement the callback interface in the client class, as shown in the following example.</span></span>

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. <span data-ttu-id="372ee-118"><xref:System.ServiceModel.InstanceContext> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="372ee-118">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="372ee-119">コンストラクターには、クライアント クラスのインスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="372ee-119">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="372ee-120">オブジェクトを必要とするコンストラクターを使用して、WCF クライアントのインスタンスを作成し <xref:System.ServiceModel.InstanceContext> ます。</span><span class="sxs-lookup"><span data-stu-id="372ee-120">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="372ee-121">コンストラクターの 2 番目のパラメーターは、構成ファイルに含まれるエンドポイントの名前です。</span><span class="sxs-lookup"><span data-stu-id="372ee-121">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="372ee-122">必要に応じて、WCF クライアントのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="372ee-122">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="372ee-123">例</span><span class="sxs-lookup"><span data-stu-id="372ee-123">Example</span></span>

<span data-ttu-id="372ee-124">双方向コントラクトにアクセスするクライアント クラスを作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="372ee-124">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="372ee-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="372ee-125">See also</span></span>

- [<span data-ttu-id="372ee-126">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="372ee-126">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="372ee-127">方法: 双方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="372ee-127">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="372ee-128">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="372ee-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="372ee-129">方法: クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="372ee-129">How to: Create a Client</span></span>](../how-to-create-a-wcf-client.md)
- [<span data-ttu-id="372ee-130">方法: ChannelFactory を使用する</span><span class="sxs-lookup"><span data-stu-id="372ee-130">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
