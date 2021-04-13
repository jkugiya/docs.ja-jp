---
title: '方法: 非同期サービス操作を実装する'
description: WFC 内での非同期サービス操作の構造について説明します。 サービス操作は、非同期的または同期的に実装できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 157311f29b203e0c26be21a89d2d5b560543094b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267833"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="1f610-104">方法: 非同期サービス操作を実装する</span><span class="sxs-lookup"><span data-stu-id="1f610-104">How to: Implement an Asynchronous Service Operation</span></span>

<span data-ttu-id="1f610-105">Windows Communication Foundation (WCF) アプリケーションでは、クライアントに呼び出し方法を指示することなく、サービス操作を非同期的または同期的に実装できます。</span><span class="sxs-lookup"><span data-stu-id="1f610-105">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="1f610-106">たとえば、非同期サービス操作を同期的に呼び出すことも、同期サービス操作を非同期的に呼び出すことも可能です。</span><span class="sxs-lookup"><span data-stu-id="1f610-106">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="1f610-107">クライアント アプリケーションから操作を非同期で呼び出す方法を示す例については、[サービス操作を非同期に呼び出す方法](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f610-107">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="1f610-108">同期および非同期操作の詳細については、「[サービス コントラクトの設計](designing-service-contracts.md)」および「[同期操作と非同期操作](synchronous-and-asynchronous-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f610-108">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="1f610-109">このトピックでは、非同期サービス操作の基本構造について説明します。コードは部分的なコードです。</span><span class="sxs-lookup"><span data-stu-id="1f610-109">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="1f610-110">サービスとクライアントの両方の側の完全な例については、「[非同期](/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f610-110">For a complete example of both the service and client sides, see [Asynchronous](/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="1f610-111">非同期サービス操作の実装</span><span class="sxs-lookup"><span data-stu-id="1f610-111">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="1f610-112">サービス コントラクトで、.NET 非同期デザイン ガイドラインに従って非同期メソッドのペアを宣言します。</span><span class="sxs-lookup"><span data-stu-id="1f610-112">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="1f610-113">`Begin` メソッドは、パラメーター、コールバック オブジェクト、状態オブジェクトを受け取って <xref:System.IAsyncResult?displayProperty=nameWithType> を返し、組になる `End` メソッドは <xref:System.IAsyncResult?displayProperty=nameWithType> を受け取って戻り値を返します。</span><span class="sxs-lookup"><span data-stu-id="1f610-113">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="1f610-114">非同期呼び出しの詳細については、「[非同期プログラミングのデザイン パターン](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f610-114">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
2. <span data-ttu-id="1f610-115">非同期メソッド ペアの `Begin` メソッドを <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 属性を使用してマークし、<xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1f610-115">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="1f610-116">たとえば、次のコード例では手順 1. と 2. を実行します。</span><span class="sxs-lookup"><span data-stu-id="1f610-116">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="1f610-117">非同期デザインのガイドラインに従って、`Begin/End` メソッド ペアをサービス クラスに実装します。</span><span class="sxs-lookup"><span data-stu-id="1f610-117">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="1f610-118">たとえば、次のコード例では、非同期サービス操作の `Begin` および `End` の両方の部分の文字列がコンソールに書き出され、`End` 操作の戻り値がクライアントに返される実装を示します。</span><span class="sxs-lookup"><span data-stu-id="1f610-118">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="1f610-119">コード例全体については、「使用例」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f610-119">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="1f610-120">例</span><span class="sxs-lookup"><span data-stu-id="1f610-120">Example</span></span>  

 <span data-ttu-id="1f610-121">このコード例では次のものが示されます。</span><span class="sxs-lookup"><span data-stu-id="1f610-121">The following code examples show:</span></span>  
  
1. <span data-ttu-id="1f610-122">次の操作とのサービス コントラクト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f610-122">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="1f610-123">同期 `SampleMethod` 操作</span><span class="sxs-lookup"><span data-stu-id="1f610-123">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="1f610-124">非同期 `BeginSampleMethod` 操作</span><span class="sxs-lookup"><span data-stu-id="1f610-124">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="1f610-125">非同期 `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` 操作のペア。</span><span class="sxs-lookup"><span data-stu-id="1f610-125">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="1f610-126"><xref:System.IAsyncResult?displayProperty=nameWithType> オブジェクトを使用したサービスの実装</span><span class="sxs-lookup"><span data-stu-id="1f610-126">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1f610-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f610-127">See also</span></span>

- [<span data-ttu-id="1f610-128">サービス コントラクトの設計</span><span class="sxs-lookup"><span data-stu-id="1f610-128">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="1f610-129">同期操作と非同期操作</span><span class="sxs-lookup"><span data-stu-id="1f610-129">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
