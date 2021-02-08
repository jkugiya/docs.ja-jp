---
description: 詳細については、「HTTP、TCP、または Named-Pipe を使用した非同期シナリオ」を参照してください。
title: HTTP、TCP、または名前付きパイプを使用した非同期シナリオ
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 5e01866cd20d63796741a097a6d7d774ea45d3d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770951"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="4bc5f-103">HTTP、TCP、または名前付きパイプを使用した非同期シナリオ</span><span class="sxs-lookup"><span data-stu-id="4bc5f-103">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>

<span data-ttu-id="4bc5f-104">ここでは、マルチスレッド要求で HTTP、TCP、または名前付きパイプを使用したときの、さまざまな非同期要求/応答シナリオでのアクティビティおよび転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-104">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="4bc5f-105">エラーを伴わない非同期要求/応答</span><span class="sxs-lookup"><span data-stu-id="4bc5f-105">Asynchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="4bc5f-106">ここでは、マルチスレッド クライアントを使用したときの、非同期要求/応答シナリオでのアクティビティおよび転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-106">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="4bc5f-107">呼び出し元アクティビティは、`beginCall` が返され、`endCall` が返されると終了します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-107">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="4bc5f-108">コールバックが呼び出されたときは、そのコールバックが返されます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-108">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="4bc5f-109">呼び出されたアクティビティは、`beginCall` が返され、`endCall` が返されると終了します。または、そのアクティビティからコールバックが呼び出された場合は、コールバックが返されると終了します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-109">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="4bc5f-110">コールバックを伴わない非同期クライアント</span><span class="sxs-lookup"><span data-stu-id="4bc5f-110">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="4bc5f-111">HTTP を使用して、両方の側で伝達が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="4bc5f-111">Propagation is Enabled on Both Sides, using HTTP</span></span>  

 ![コールバックのない非同期クライアント。両側で propagateActivity が true に設定されています。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 <span data-ttu-id="4bc5f-113">`propagateActivity=true`の場合、"メッセージは、転送先の ProcessAction アクティビティを示します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-113">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="4bc5f-114">HTTP ベースのシナリオでは、最初に送信するメッセージで "バイトを受信" が呼び出され、要求の有効期間だけ存在します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-114">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="4bc5f-115">HTTP を使用して、両方の側で伝達が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="4bc5f-115">Propagation is Disabled on Either Sides, using HTTP</span></span>  

 <span data-ttu-id="4bc5f-116">`propagateActivity=false`どちらの側でも、"メッセージは、転送先の ProcessAction アクティビティを示しません。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-116">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="4bc5f-117">したがって、新しい ID を使用して、新しい一時的な "アクションを処理" アクティビティが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-117">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="4bc5f-118">非同期応答と ServiceModel コード内の要求が一致する場合は、アクティビティ ID をローカル コンテキストから取得できます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-118">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="4bc5f-119">その ID を使用して、実際の "アクションを処理" アクティビティに転送できます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-119">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![いずれかの側で propagateActivity が false に設定されているコールバックのない非同期クライアント。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 <span data-ttu-id="4bc5f-121">HTTP ベースのシナリオでは、最初に送信するメッセージで "バイトを受信" が呼び出され、要求の有効期間だけ存在します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-121">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="4bc5f-122">プロセスアクションアクティビティは、 `propagateActivity=false` 呼び出し元または呼び出し先の場合、および応答メッセージに Action ヘッダーが含まれていない場合に、非同期クライアントで作成されます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-122">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="4bc5f-123">TCP または名前付きパイプを使用して、両方の側で伝達が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="4bc5f-123">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  

 ![コールバックのない非同期クライアント。両側と名前付きパイプ/TCP で propagateActivity が true に設定されています。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="4bc5f-125">名前付きパイプまたは TCP ベースのシナリオでは、クライアントが開かれるときに "バイトを受信" が呼び出され、接続の有効期間だけ存在します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-125">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="4bc5f-126">最初のイメージに似て `propagateActivity=true` います。の場合、"メッセージは、転送先の ProcessAction アクティビティを示します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-126">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="4bc5f-127">TCP または名前付きパイプを使用して、両方の側で伝達が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="4bc5f-127">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  

 <span data-ttu-id="4bc5f-128">名前付きパイプまたは TCP ベースのシナリオでは、クライアントが開かれるときに "バイトを受信" が呼び出され、接続の有効期間だけ存在します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-128">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="4bc5f-129">2番目のイメージに似て `propagateActivity=false` いますが、どちらの側でも、"メッセージは、転送先の ProcessAction アクティビティを示していません。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-129">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="4bc5f-130">したがって、新しい ID を使用して、新しい一時的な "アクションを処理" アクティビティが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-130">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="4bc5f-131">非同期応答と ServiceModel コード内の要求が一致する場合は、アクティビティ ID をローカル コンテキストから取得できます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-131">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="4bc5f-132">その ID を使用して、実際の "アクションを処理" アクティビティに転送できます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-132">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![コールバックのない非同期クライアント (サイドと名前付きパイプ/TCP で propagateActivity が false に設定されている場合)。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="4bc5f-134">コールバックを伴う非同期クライアント</span><span class="sxs-lookup"><span data-stu-id="4bc5f-134">Asynchronous client with Callback</span></span>  

 <span data-ttu-id="4bc5f-135">このシナリオでは、コールバックと `endCall` に対するアクティビティ G と A’、およびその転送 (送受信) が追加されています。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-135">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="4bc5f-136">このセクションでは、で HTTP を使用する方法のみを示し `propagateActivity` = `true` ます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-136">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="4bc5f-137">ただし、追加のアクティビティと転送も、他のケース (つまり、 `propagateActivity` = `false` TCP または名前付きパイプを使用) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-137">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="4bc5f-138">クライアントがユーザー コードを呼び出して結果の準備が完了したことを通知すると、コールバックは新しいアクティビティ (G) を作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-138">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="4bc5f-139">ユーザー コードは、次に、コールバック内 (図 5 を参照) またはコールバック外 (図 6 を参照) で `endCall` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-139">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="4bc5f-140">どのユーザーアクティビティが呼び出されているかが不明であるため `endCall` 、このアクティビティにはというラベルが付けられ `A’` ます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-140">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="4bc5f-141">A’ と A が同じである場合もありますし、異なる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-141">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![コールバックのコールバックがある非同期クライアントを表示します。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![コールバックの外部のコールバックを持つ非同期クライアントを表示します。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="4bc5f-144">コールバックを伴う非同期サーバー</span><span class="sxs-lookup"><span data-stu-id="4bc5f-144">Asynchronous Server with Callback</span></span>  

 ![コールバックがある非同期サーバーを表示します。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 <span data-ttu-id="4bc5f-146">チャネル スタックは、"メッセージを受信" でクライアントをコールバックします。この処理のトレースは、"要求を処理" アクティビティ自体で出力されます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-146">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="4bc5f-147">エラーを伴う非同期要求/応答</span><span class="sxs-lookup"><span data-stu-id="4bc5f-147">Asynchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="4bc5f-148">エラー メッセージは、`endCall` 中に受信されます。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-148">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="4bc5f-149">この点を除き、アクティビティおよび転送は前のシナリオと同様です。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-149">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="4bc5f-150">エラーを伴う/伴わない非同期一方向要求/応答</span><span class="sxs-lookup"><span data-stu-id="4bc5f-150">Asynchronous One-Way with or without Errors</span></span>  

 <span data-ttu-id="4bc5f-151">クライアントに返される応答やエラーはありません。</span><span class="sxs-lookup"><span data-stu-id="4bc5f-151">No response or fault is returned to the client.</span></span>
