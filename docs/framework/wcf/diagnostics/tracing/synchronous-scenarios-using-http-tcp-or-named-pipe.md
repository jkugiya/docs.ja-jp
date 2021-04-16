---
description: '詳細情報: HTTP、TCP、または名前付きパイプを使用した同期シナリオ'
title: HTTP、TCP、または名前付きパイプを使用した同期シナリオ
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: fd6605be99a9419de27f000b378720adf0ae1a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635416"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="2e1ea-103">HTTP、TCP、または名前付きパイプを使用した同期シナリオ</span><span class="sxs-lookup"><span data-stu-id="2e1ea-103">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>

<span data-ttu-id="2e1ea-104">ここでは、シングル スレッド クライアントで HTTP、TCP、または名前付きパイプを使用したときの、さまざまな同期要求/応答シナリオでのアクティビティと転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-104">This topic describes the activities and transfers for different synchronous request/reply scenarios, with a single-threaded client, using HTTP, TCP or named pipe.</span></span> <span data-ttu-id="2e1ea-105">マルチスレッド要求の詳細については、「[HTTP、TCP、または名前付きパイプを使用した非同期シナリオ](asynchronous-scenarios-using-http-tcp-or-named-pipe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-105">See [Asynchronous Scenarios using HTTP, TCP, or Named-Pipe](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) for more information on multi-threaded requests.</span></span>  
  
## <a name="synchronous-requestreply-without-errors"></a><span data-ttu-id="2e1ea-106">エラーを伴わない同期要求/応答</span><span class="sxs-lookup"><span data-stu-id="2e1ea-106">Synchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="2e1ea-107">ここでは、シングル スレッド クライアントを使用したときの、有効な同期要求/応答シナリオでのアクティビティおよび転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-107">This section describes the activities and transfers for a valid synchronous request/reply scenario, with single-threaded client.</span></span>  
  
### <a name="client"></a><span data-ttu-id="2e1ea-108">Client</span><span class="sxs-lookup"><span data-stu-id="2e1ea-108">Client</span></span>  
  
#### <a name="establishing-communication-with-service-endpoint"></a><span data-ttu-id="2e1ea-109">サービス エンドポイントとの通信の確立</span><span class="sxs-lookup"><span data-stu-id="2e1ea-109">Establishing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="2e1ea-110">クライアントを構築して開きます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-110">A client is constructed and opened.</span></span> <span data-ttu-id="2e1ea-111">各手順では、アンビエント アクティビティ (A) が "クライアントの構築" アクティビティ (B) と "クライアントを開く" アクティビティ (C) にそれぞれ転送されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-111">For each of these steps, the ambient activity (A) is transferred to a "Construct Client" (B) and "Open Client" (C) activity respectively.</span></span> <span data-ttu-id="2e1ea-112">転送されるアクティビティごとに、転送が返されるまで (つまり、ServiceModel コードが実行されるまで) アンビエント アクティビティは中断されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-112">For each activity being transferred to, the ambient activity is suspended until there is a transfer back, that is, until ServiceModel code is executed.</span></span>  
  
#### <a name="making-a-request-to-service-endpoint"></a><span data-ttu-id="2e1ea-113">サービス エンドポイントへの要求</span><span class="sxs-lookup"><span data-stu-id="2e1ea-113">Making a Request to Service Endpoint</span></span>  

 <span data-ttu-id="2e1ea-114">アンビエント アクティビティが "アクションを処理" アクティビティ (D) に転送されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-114">The ambient activity is transferred to a "ProcessAction" (D) activity.</span></span> <span data-ttu-id="2e1ea-115">このアクティビティでは、要求メッセージが送信され、応答メッセージが受信されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-115">Within this activity, a request message is sent, and a response message is received.</span></span> <span data-ttu-id="2e1ea-116">このアクティビティは、ユーザー コードに制御が戻ると終了します。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-116">The activity ends when control returns to user code.</span></span> <span data-ttu-id="2e1ea-117">これは同期要求であるため、制御が戻るまでアンビエント アクティビティは中断されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-117">Because this is a synchronous request, the ambient activity suspends until control returns.</span></span>  
  
#### <a name="closing-communication-with-service-endpoint"></a><span data-ttu-id="2e1ea-118">サービス エンドポイントとの通信の終了</span><span class="sxs-lookup"><span data-stu-id="2e1ea-118">Closing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="2e1ea-119">クライアントの "閉じる" アクティビティ (I) が、アンビエント アクティビティから作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-119">The client's close activity (I) is created from the ambient activity.</span></span> <span data-ttu-id="2e1ea-120">これは、"新規" や "開く" と同じです。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-120">This is identical to new and open.</span></span>  
  
### <a name="server"></a><span data-ttu-id="2e1ea-121">サーバー</span><span class="sxs-lookup"><span data-stu-id="2e1ea-121">Server</span></span>  
  
#### <a name="setting-up-a-service-host"></a><span data-ttu-id="2e1ea-122">サービス ホストの設定</span><span class="sxs-lookup"><span data-stu-id="2e1ea-122">Setting up a Service Host</span></span>  

 <span data-ttu-id="2e1ea-123">ServiceHost の "新規" アクティビティ (N) および "開く" アクティビティ (O) は、アンビエント アクティビティ (M) から作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-123">The ServiceHost’s new and open activities (N and O) are created from the ambient activity (M).</span></span>  
  
 <span data-ttu-id="2e1ea-124">リスナー アクティビティ (P) は、各リスナーの ServiceHost を開くと作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-124">A listener activity (P) is created from opening a ServiceHost for each listener.</span></span> <span data-ttu-id="2e1ea-125">リスナー アクティビティは、待機してデータを受信および処理します。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-125">The listener activity waits to receive and process data.</span></span>  
  
#### <a name="receiving-data-on-the-wire"></a><span data-ttu-id="2e1ea-126">ネットワーク上のデータの受信</span><span class="sxs-lookup"><span data-stu-id="2e1ea-126">Receiving Data on the Wire</span></span>  

 <span data-ttu-id="2e1ea-127">データがネットワークに到着すると、受信したデータを処理するために "バイトを受信" アクティビティ (Q) が作成されます (まだ存在しない場合)。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-127">When data arrives on the wire, a "ReceiveBytes" activity is created if it does not already exist (Q) to process the received data.</span></span> <span data-ttu-id="2e1ea-128">このアクティビティは、接続またはキュー内の複数のメッセージに再使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-128">This activity can be reused for multiple messages within a connection or queue.</span></span>  
  
 <span data-ttu-id="2e1ea-129">SOAP アクション メッセージを作成するための十分なデータがある場合、"バイトを受信" アクティビティは "メッセージを処理" アクティビティ (R) を起動します。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-129">The ReceiveBytes activity launches a ProcessMessage activity (R) if it has enough data to form a SOAP action message.</span></span>  
  
 <span data-ttu-id="2e1ea-130">アクティビティ R では、メッセージ ヘッダーが処理され、アクティビティ ID ヘッダーが確認されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-130">In activity R, the message headers are processed, and the activityID header is verified.</span></span> <span data-ttu-id="2e1ea-131">このヘッダーが存在する場合、アクティビティ ID は "アクションを処理" アクティビティに設定されます。それ以外の場合は、新しい ID が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-131">If this header is present, the activity ID is set to the ProcessAction activity; otherwise, a new ID is created.</span></span>  
  
 <span data-ttu-id="2e1ea-132">呼び出しが処理されると、"アクションを処理" アクティビティ (S) が作成されて転送されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-132">ProcessAction activity (S) is created and being transferred to, when the call is processed.</span></span> <span data-ttu-id="2e1ea-133">このアクティビティは、受信メッセージに関連するすべての処理 ("ユーザー コードを実行" (T) と "応答メッセージを送信" (該当する場合) を含む) が完了すると終了します。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-133">This activity ends when all processing related to the incoming message is completed, including executing user code (T) and sending the response message if applicable.</span></span>  
  
#### <a name="closing-a-service-host"></a><span data-ttu-id="2e1ea-134">サービス ホストの終了</span><span class="sxs-lookup"><span data-stu-id="2e1ea-134">Closing a Service Host</span></span>  

 <span data-ttu-id="2e1ea-135">ServiceHost の "閉じる" アクティビティ (Z) は、アンビエント アクティビティから作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-135">The ServiceHost’s close activity (Z) is created from the ambient activity.</span></span>  
  
 ![同期シナリオを示した図: HTTP、TCP、または名前付きパイプ。](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 <span data-ttu-id="2e1ea-137">\<A: name> の `A` は、前の説明および表 3 に含まれるアクティビティを表すショートカット シンボルです。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-137">In \<A: name>, `A` is a shortcut symbol that describes the activity in the previous text and in table 3.</span></span> <span data-ttu-id="2e1ea-138">`Name` は、アクティビティの短縮名です。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-138">`Name` is a shortened name of the activity.</span></span>  
  
 <span data-ttu-id="2e1ea-139">`propagateActivity`=`true` の場合、クライアントとサービスの "アクションを処理" アクティビティはどちらも同じアクティビティ ID を持ちます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-139">If `propagateActivity`=`true`, Process Action on both the client and service have the same activity ID.</span></span>  
  
## <a name="synchronous-requestreply-with-errors"></a><span data-ttu-id="2e1ea-140">エラーを伴う同期要求/応答</span><span class="sxs-lookup"><span data-stu-id="2e1ea-140">Synchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="2e1ea-141">前述のシナリオとの違いは、応答メッセージとして SOAP エラー メッセージが返されることだけです。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-141">The only difference with the previous scenario is that a SOAP fault message is returned as a response message.</span></span> <span data-ttu-id="2e1ea-142">`propagateActivity`=`true` の場合は、要求メッセージのアクティビティ ID が SOAP エラー メッセージに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-142">If `propagateActivity`=`true`, the activity ID of the request message is added to the SOAP fault message.</span></span>  
  
## <a name="synchronous-one-way-without-errors"></a><span data-ttu-id="2e1ea-143">エラーを伴わない同期一方向</span><span class="sxs-lookup"><span data-stu-id="2e1ea-143">Synchronous One-Way without Errors</span></span>  

 <span data-ttu-id="2e1ea-144">最初のシナリオとの違いは、メッセージがサーバーに返されないことだけです。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-144">The only difference with the first scenario is that no message is returned to the server.</span></span> <span data-ttu-id="2e1ea-145">HTTP ベースのプロトコルの場合は、ステータス (有効またはエラー) がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-145">For HTTP-based protocols, a status (valid or error) is still returned to the client.</span></span> <span data-ttu-id="2e1ea-146">それは、WCF プロトコル スタックのなかで HTTP プロトコルだけが、要求/応答セマンティクスを使用するからです。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-146">This is because HTTP is the only protocol with a request-response semantics that is part of the WCF protocol stack.</span></span> <span data-ttu-id="2e1ea-147">TCP 処理は WCF からは見えないため、受信確認はクライアントに送信されません。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-147">Because TCP processing is hidden from WCF, no acknowledgement is sent to the client.</span></span>  
  
## <a name="synchronous-one-way-with-errors"></a><span data-ttu-id="2e1ea-148">エラーを伴う同期一方向</span><span class="sxs-lookup"><span data-stu-id="2e1ea-148">Synchronous One-Way with Errors</span></span>  

 <span data-ttu-id="2e1ea-149">メッセージの処理中 (Q 以降) にエラーが発生しても、クライアントには通知が返されません。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-149">If an error occurs while processing the message (Q or beyond), no notification is returned to the client.</span></span> <span data-ttu-id="2e1ea-150">これは、「エラーを伴わない同期一方向要求/応答」のシナリオと同じです。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-150">This is identical to the "Synchronous One-Way without Errors" scenario.</span></span> <span data-ttu-id="2e1ea-151">エラー メッセージを受信する必要がある場合は、一方向のシナリオを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-151">You should not use a One-Way scenario if you want to receive an error message.</span></span>  
  
## <a name="duplex"></a><span data-ttu-id="2e1ea-152">二重</span><span class="sxs-lookup"><span data-stu-id="2e1ea-152">Duplex</span></span>  

 <span data-ttu-id="2e1ea-153">上述のシナリオとの違いは、クライアントがサービスとして動作することです。この場合、非同期のシナリオと同様、クライアントは "バイトを受信" アクティビティと "メッセージを処理" アクティビティを作成します。</span><span class="sxs-lookup"><span data-stu-id="2e1ea-153">The difference with the previous scenarios is that the client acts as a service, in which it creates the ReceiveBytes and ProcessMessage activities, similar to the Asynchronous scenarios.</span></span>
