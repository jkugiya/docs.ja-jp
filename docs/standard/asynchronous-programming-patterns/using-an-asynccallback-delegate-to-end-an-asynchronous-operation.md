---
description: '詳細情報: AsyncCallback デリゲートの使用による非同期操作の終了'
title: AsyncCallback デリゲートの使用による非同期操作の終了
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c97be1b9dbf225cfb76f8d9392269297fc1d123c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732190"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="6db1f-103">AsyncCallback デリゲートの使用による非同期操作の終了</span><span class="sxs-lookup"><span data-stu-id="6db1f-103">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>

<span data-ttu-id="6db1f-104">非同期操作の結果の待機中に、他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6db1f-104">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="6db1f-105">次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、手順の実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="6db1f-105">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="6db1f-106"><xref:System.AsyncCallback> デリゲートを使用し、個別のスレッドで非同期操作の結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="6db1f-106">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="6db1f-107">このトピックでは、この方法のデモが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6db1f-107">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="6db1f-108">非同期操作の **Begin**_OperationName_ メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.IsCompleted%2A> プロパティを使用して、その操作が完了したかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="6db1f-108">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="6db1f-109">この方法のデモを実行する例については、「[非同期操作のステータスのポーリング](polling-for-the-status-of-an-asynchronous-operation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6db1f-109">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6db1f-110">例</span><span class="sxs-lookup"><span data-stu-id="6db1f-110">Example</span></span>  

 <span data-ttu-id="6db1f-111">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム (DNS) 情報を取得するために、<xref:System.Net.Dns> クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="6db1f-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="6db1f-112">この例では、`ProcessDnsInformation` メソッドを参照する <xref:System.AsyncCallback> デリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="6db1f-112">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="6db1f-113">このメソッドは、DNS 情報に対する非同期要求ごとに 1 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6db1f-113">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="6db1f-114">ユーザー指定のホストは、<xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> パラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="6db1f-114">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="6db1f-115">複雑な状態オブジェクトの定義と使用に関するデモを実行する例については、「[AsyncCallback デリゲートおよび状態オブジェクトの使用](using-an-asynccallback-delegate-and-state-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6db1f-115">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6db1f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6db1f-116">See also</span></span>

- [<span data-ttu-id="6db1f-117">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="6db1f-117">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="6db1f-118">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="6db1f-118">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="6db1f-119">IAsyncResult を使用した非同期メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="6db1f-119">Calling Asynchronous Methods Using IAsyncResult</span></span>](calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="6db1f-120">AsyncCallback デリゲートおよび状態オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="6db1f-120">Using an AsyncCallback Delegate and State Object</span></span>](using-an-asynccallback-delegate-and-state-object.md)
