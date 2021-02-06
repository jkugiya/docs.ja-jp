---
description: '詳細情報: 信頼できるセッションの概要'
title: 信頼できるセッションの概要
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 51de6012245b4fc0a367069d02fe69ee031f2b30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632894"
---
# <a name="reliable-sessions-overview"></a><span data-ttu-id="f7f39-103">信頼できるセッションの概要</span><span class="sxs-lookup"><span data-stu-id="f7f39-103">Reliable Sessions Overview</span></span>

<span data-ttu-id="f7f39-104">Windows Communication Foundation (WCF) SOAP reliable messaging は、SOAP エンドポイント間でエンドツーエンドのメッセージ転送の信頼性を提供します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-104">Windows Communication Foundation (WCF) SOAP reliable messaging provides end-to-end message transfer reliability between SOAP endpoints.</span></span> <span data-ttu-id="f7f39-105">これにより、信頼性の低いネットワーク上でも、トランスポート エラーや SOAP メッセージ レベルのエラーに対処できます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-105">It does this on networks that are unreliable by overcoming transport failures and SOAP message-level failures.</span></span> <span data-ttu-id="f7f39-106">具体的には、SOAP またはトランスポート中継局を経由して送信されるメッセージに関して、1 回だけの配信や (オプションで) 順序保証の配信がセッション ベースで提供されます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-106">In particular, it provides session-based, single, and (optionally) ordered delivery for messages sent across SOAP or transport intermediaries.</span></span> <span data-ttu-id="f7f39-107">セッションベースの配信では、オプションでメッセージの順序を指定して、セッション内のメッセージをグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-107">Session-based delivery provides for grouping messages in a session with optional ordering of the messages.</span></span>

<span data-ttu-id="f7f39-108">このトピックでは、信頼できるセッション、それらをいつどのように使用するか、およびそれらをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-108">This topic describes reliable sessions, how and when to use them, and how to secure them.</span></span>

## <a name="wcf-reliable-sessions"></a><span data-ttu-id="f7f39-109">WCF の信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="f7f39-109">WCF reliable sessions</span></span>

<span data-ttu-id="f7f39-110">WCF reliable sessions は、WS-ReliableMessaging プロトコルで定義されている SOAP reliable messaging の実装です。</span><span class="sxs-lookup"><span data-stu-id="f7f39-110">WCF reliable sessions is an implementation of SOAP reliable messaging as defined by the WS-ReliableMessaging protocol.</span></span>

<span data-ttu-id="f7f39-111">WCF SOAP reliable messaging は、メッセージングエンドポイントを分離する中継局の数や種類に関係なく、2つのエンドポイント間のエンドツーエンドの信頼できるセッションを提供します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-111">WCF SOAP reliable messaging provides an end-to-end reliable session between two endpoints, regardless of the number or type of intermediaries that separate the messaging endpoints.</span></span> <span data-ttu-id="f7f39-112">これには、soap を使用しないトランスポート仲介 (HTTP プロキシなど) や、エンドポイント間のメッセージフローに必要な soap (SOAP ベースのルーターやブリッジなど) を使用する中継局が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-112">This includes any transport intermediaries that don't use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="f7f39-113">信頼できるセッションチャネルは、 *対話型* 通信をサポートしているので、このようなチャネルに接続されているサービスは同時に実行され、待機時間が短い状況 (比較的短い間隔) でメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-113">A reliable session channel supports *interactive* communication so that the services connected by such a channel run concurrently and exchange and process messages under conditions of low latency, that is, within relatively short intervals of time.</span></span> <span data-ttu-id="f7f39-114">この結合によって、これらのコンポーネントの進行状況がまとめられたり、失敗したりします。そのため、これらのコンポーネント間に分離が提供されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f7f39-114">This coupling means that these components make progress together or fail together, so there's no isolation provided between them.</span></span>

<span data-ttu-id="f7f39-115">信頼できるセッションでは次の 2 種類のエラーがマスクされます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-115">A reliable session masks two kinds of failures:</span></span>

- <span data-ttu-id="f7f39-116">SOAP メッセージ レベルのエラー (メッセージの喪失または重複、および送信順序と異なる順序で到着するメッセージを含む)</span><span class="sxs-lookup"><span data-stu-id="f7f39-116">SOAP message-level failures, which includes lost or duplicated messages and messages that arrive in a different order from the order in which they were sent.</span></span>

- <span data-ttu-id="f7f39-117">トランスポート エラー</span><span class="sxs-lookup"><span data-stu-id="f7f39-117">Transport failures.</span></span>

<span data-ttu-id="f7f39-118">信頼できるセッションは、WS-ReliableMessaging プロトコルとメモリ内転送ウィンドウを実装することにより、トランスポート エラーが発生した場合に SOAP メッセージ レベルのエラーをマスクし、接続を再確立します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-118">A reliable session implements the WS-ReliableMessaging protocol and an in-memory transfer window to mask SOAP message-level failures and re-establishes connections in the case of transport failures.</span></span>

<span data-ttu-id="f7f39-119">信頼できるセッションは、TCP が IP パケットに提供する信頼性を SOAP メッセージに提供します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-119">A reliable session provides for SOAP messages what TCP provides for IP packets.</span></span> <span data-ttu-id="f7f39-120">TCP ソケット接続では、ノード間で IP パケットが 1 回のみ、正しい順序で転送されます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-120">A TCP socket connection provides a singular, in-order transfer of IP packets between nodes.</span></span> <span data-ttu-id="f7f39-121">信頼できるチャネルでも、これと同じタイプの信頼できる転送が提供されますが、次の点で TCP ソケットの信頼性とは異なります。</span><span class="sxs-lookup"><span data-stu-id="f7f39-121">The reliable channel provides the same type of reliable transfer, but it differs from TCP socket reliability in the following ways:</span></span>

- <span data-ttu-id="f7f39-122">信頼性は、任意のサイズのバイト パケットに対してではなく、SOAP メッセージ レベルで提供されます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-122">The reliability is at the SOAP message level, not for an arbitrarily sized packet of bytes.</span></span>

- <span data-ttu-id="f7f39-123">信頼性は、TCP 経由の転送だけでなく、トランスポートに依存しません。</span><span class="sxs-lookup"><span data-stu-id="f7f39-123">The reliability is transport-neutral, not just for transfer over TCP.</span></span>

- <span data-ttu-id="f7f39-124">信頼性は、特定のトランスポートセッション (たとえば、TCP 接続が提供するセッション) に関連付けられておらず、信頼できるセッションの有効期間にわたって複数のトランスポートセッションを同時に、または順番に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-124">The reliability isn't tied to a particular transport session (for example, the session a TCP connection provides) and can use multiple transport sessions concurrently or sequentially over the lifetime of the reliable session.</span></span>

- <span data-ttu-id="f7f39-125">信頼できるセッションは、送信側と受信側の SOAP エンドポイント間の接続に必要なトランスポート接続の数に関係なく、両者の間で提供されます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-125">The reliable session is between the sender and receiver SOAP endpoints, regardless of the number of transport connections required for connectivity between them.</span></span> <span data-ttu-id="f7f39-126">つまり、TCP の信頼性は、トランスポート接続が終了する場所で終了しますが、信頼できるセッションではエンドツーエンドの信頼性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-126">In short, TCP reliability ends where the transport connection ends, while a reliable session provides end-to-end reliability.</span></span>

## <a name="reliable-sessions-and-bindings"></a><span data-ttu-id="f7f39-127">信頼できるセッションとバインド</span><span class="sxs-lookup"><span data-stu-id="f7f39-127">Reliable sessions and bindings</span></span>

<span data-ttu-id="f7f39-128">既に説明したように、信頼できるセッションはトランスポートに依存しません。</span><span class="sxs-lookup"><span data-stu-id="f7f39-128">As mentioned earlier, a reliable session is transport neutral.</span></span> <span data-ttu-id="f7f39-129">また、要求/応答や双方向など、多くのメッセージ交換パターンに対して信頼できるセッションを確立することもできます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-129">Also, you can establish a reliable session over many message exchange patterns, such as request-reply or duplex.</span></span> <span data-ttu-id="f7f39-130">WCF の信頼できるセッションは、一連のバインドのプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-130">A WCF reliable session is exposed as a property of a set of bindings.</span></span>

<span data-ttu-id="f7f39-131">次のものを使用するエンドポイントで信頼できるセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-131">Use a reliable session on endpoints that use:</span></span>

- <span data-ttu-id="f7f39-132">HTTP ベース トランスポートの標準バインディング</span><span class="sxs-lookup"><span data-stu-id="f7f39-132">HTTP-based transport standard bindings:</span></span>

  - <span data-ttu-id="f7f39-133">`WsHttpBinding` : 要求/応答または一方向のコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-133">`WsHttpBinding` and expose request-reply or one-way contracts.</span></span>

  - <span data-ttu-id="f7f39-134">要求/応答または単純な一方向のサービスコントラクトに対して信頼できるセッションを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="f7f39-134">When using reliable session over a request-reply or simple one-way service contract.</span></span>

  - <span data-ttu-id="f7f39-135">`WsDualHttpBinding` : 双方向、要求/応答、または一方向のコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-135">`WsDualHttpBinding` and expose duplex, request-reply, or one-way contracts.</span></span>

  - <span data-ttu-id="f7f39-136">`WsFederationHttpBinding` : 要求/応答または一方向のコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-136">`WsFederationHttpBinding` and expose request-reply or one-way contracts.</span></span>

- <span data-ttu-id="f7f39-137">TCP ベース トランスポートの標準バインディング</span><span class="sxs-lookup"><span data-stu-id="f7f39-137">TCP-based transport standard bindings:</span></span>

  - <span data-ttu-id="f7f39-138">`NetTcpBinding` : 双方向、要求/応答、または一方向のコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-138">`NetTcpBinding` and expose duplex, request reply, or one-way contracts.</span></span>

<span data-ttu-id="f7f39-139">HTTPS (問題の詳細については、「 <a href="#reliable-sessions-and-security">信頼できるセッションとセキュリティ</a>」を参照) または名前付きパイプバインドを作成して、その他のバインディングで信頼できるセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-139">Use a reliable session on any other bindings by creating a custom binding, such as HTTPS (for more information about issues, see <a href="#reliable-sessions-and-security">Reliable sessions and security</a>) or a named pipe binding.</span></span>

<span data-ttu-id="f7f39-140">信頼できるセッションは、基になるさまざまな種類のチャネルにスタックでき、結果として得られる信頼できるセッションチャネルの形状は異なります。</span><span class="sxs-lookup"><span data-stu-id="f7f39-140">You can stack a reliable session on different underlying channel types, and the resulting reliable session channel shape varies.</span></span> <span data-ttu-id="f7f39-141">クライアントとサーバーの両方で、サポートされている信頼できるセッションチャネルの種類は、使用される基になるチャネルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f7f39-141">On both the client and the server, the type of reliable session channel supported depends on the type of underlying channel used.</span></span> <span data-ttu-id="f7f39-142">次の表では、基になるチャネルの種類ごとに、クライアントでサポートされるセッション チャネルの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-142">The following table lists the types of session channels supported on the client as a function of the underlying channel type.</span></span>

| <span data-ttu-id="f7f39-143">サポートされている信頼できるセッションチャネルの種類&#8224;</span><span class="sxs-lookup"><span data-stu-id="f7f39-143">Supported reliable session channel types&#8224;</span></span> | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | <span data-ttu-id="f7f39-144">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-144">Yes</span></span>               | <span data-ttu-id="f7f39-145">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-145">Yes</span></span>                      | <span data-ttu-id="f7f39-146">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-146">Yes</span></span>              | <span data-ttu-id="f7f39-147">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-147">Yes</span></span>                     |
| `IRequestSessionChannel`                        | <span data-ttu-id="f7f39-148">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-148">Yes</span></span>               | <span data-ttu-id="f7f39-149">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-149">Yes</span></span>                      | <span data-ttu-id="f7f39-150">いいえ</span><span class="sxs-lookup"><span data-stu-id="f7f39-150">No</span></span>               | <span data-ttu-id="f7f39-151">いいえ</span><span class="sxs-lookup"><span data-stu-id="f7f39-151">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="f7f39-152">いいえ</span><span class="sxs-lookup"><span data-stu-id="f7f39-152">No</span></span>                | <span data-ttu-id="f7f39-153">いいえ</span><span class="sxs-lookup"><span data-stu-id="f7f39-153">No</span></span>                       | <span data-ttu-id="f7f39-154">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-154">Yes</span></span>              | <span data-ttu-id="f7f39-155">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-155">Yes</span></span>                     |

<span data-ttu-id="f7f39-156">サポートされているチャネルの種類 &#8224;、 `TChannel` メソッドに渡されるジェネリックパラメーター値に使用できる値です <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> 。</span><span class="sxs-lookup"><span data-stu-id="f7f39-156">&#8224;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

<span data-ttu-id="f7f39-157">次の表では、基になるチャネルの種類ごとに、サーバーでサポートされるセッション チャネルの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-157">The following table lists the types of session channels supported on the server as a function of the underlying channel type.</span></span>

| <span data-ttu-id="f7f39-158">サポートされている信頼できるセッションチャネルの種類&#8225;</span><span class="sxs-lookup"><span data-stu-id="f7f39-158">Supported reliable session channel types&#8225;</span></span> | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | <span data-ttu-id="f7f39-159">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-159">Yes</span></span>             | <span data-ttu-id="f7f39-160">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-160">Yes</span></span>                    | <span data-ttu-id="f7f39-161">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-161">Yes</span></span>              | <span data-ttu-id="f7f39-162">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-162">Yes</span></span>                     |
| `IReplySessionChannel`                          | <span data-ttu-id="f7f39-163">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-163">Yes</span></span>             | <span data-ttu-id="f7f39-164">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-164">Yes</span></span>                    | <span data-ttu-id="f7f39-165">いいえ</span><span class="sxs-lookup"><span data-stu-id="f7f39-165">No</span></span>               | <span data-ttu-id="f7f39-166">いいえ</span><span class="sxs-lookup"><span data-stu-id="f7f39-166">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="f7f39-167">いいえ</span><span class="sxs-lookup"><span data-stu-id="f7f39-167">No</span></span>              | <span data-ttu-id="f7f39-168">いいえ</span><span class="sxs-lookup"><span data-stu-id="f7f39-168">No</span></span>                     | <span data-ttu-id="f7f39-169">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-169">Yes</span></span>              | <span data-ttu-id="f7f39-170">はい</span><span class="sxs-lookup"><span data-stu-id="f7f39-170">Yes</span></span>                     |

<span data-ttu-id="f7f39-171">サポートされているチャネルの種類 &#8225;、 `TChannel` メソッドに渡されるジェネリックパラメーター値に使用できる値です <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> 。</span><span class="sxs-lookup"><span data-stu-id="f7f39-171">&#8225;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

## <a name="reliable-sessions-and-security"></a><span data-ttu-id="f7f39-172">信頼できるセッションとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="f7f39-172">Reliable sessions and security</span></span>

<span data-ttu-id="f7f39-173">信頼できるセッションをセキュリティで保護することは、通信パーティ (サービスとクライアント) が認証され、セッションで交換されるメッセージが改ざんされないようにするために重要です。</span><span class="sxs-lookup"><span data-stu-id="f7f39-173">Securing a reliable session is important to ensure that the communicating parties (service and client) are authenticated and that the messages exchanged in the session aren't tampered with.</span></span> <span data-ttu-id="f7f39-174">さらに、それぞれの信頼できるセッションの整合性を確保することが重要です。</span><span class="sxs-lookup"><span data-stu-id="f7f39-174">Furthermore, it's important to ensure the integrity of each individual reliable session.</span></span> <span data-ttu-id="f7f39-175">信頼できるセッションは、セキュリティセッションチャネルによって表され、管理されるセキュリティコンテキストにバインドすることによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-175">A reliable session is secured by binding it to a security context that's represented and managed by a security session channel.</span></span> <span data-ttu-id="f7f39-176">セキュリティ チャネルによって、セキュリティ セッションが可能になります。</span><span class="sxs-lookup"><span data-stu-id="f7f39-176">The security channel provides a security session.</span></span> <span data-ttu-id="f7f39-177">セッション確立中に交換されるセキュリティ トークンは、信頼できるセッションでメッセージをセキュリティで保護するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-177">Security tokens exchanged during the session establishment are then used to secure the messages in the reliable session.</span></span>

<span data-ttu-id="f7f39-178">信頼できるセッションが TCP-S を介している場合、TCP セッションは信頼できるセッションに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-178">When a reliable session is over TCP-S, the TCP session is tied to the reliable session.</span></span> <span data-ttu-id="f7f39-179">したがって、トランスポートセキュリティにより、セキュリティも信頼できるセッションに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f7f39-179">Therefore, transport security ensures that security is also tied to the reliable session.</span></span> <span data-ttu-id="f7f39-180">この場合、接続の再確立は無効になります。</span><span class="sxs-lookup"><span data-stu-id="f7f39-180">In this case, connection re-establishment is turned off.</span></span>

<span data-ttu-id="f7f39-181">唯一の例外は、HTTPS の使用時です。</span><span class="sxs-lookup"><span data-stu-id="f7f39-181">The only exception is when using HTTPS.</span></span> <span data-ttu-id="f7f39-182">Secure Sockets Layer (SSL) セッションが信頼できるセッションにバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="f7f39-182">The Secure Sockets Layer (SSL) session isn't bound to the reliable session.</span></span> <span data-ttu-id="f7f39-183">これにより、セキュリティコンテキスト (SSL セッション) を共有しているセッションが相互に保護されていないため、脅威が生じます。これは、アプリケーションによっては実際の脅威ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7f39-183">This imposes a threat because sessions that are sharing a security context (the SSL session) aren't protected from each other; this might or might not be a real threat depending on the application.</span></span>

## <a name="using-reliable-sessions"></a><span data-ttu-id="f7f39-184">信頼できるセッションの使用</span><span class="sxs-lookup"><span data-stu-id="f7f39-184">Using reliable sessions</span></span>

<span data-ttu-id="f7f39-185">WCF の信頼できるセッションを使用するには、信頼できるセッションをサポートするバインディングを使用してエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-185">To use WCF reliable sessions, create an endpoint with a binding that supports a reliable session.</span></span> <span data-ttu-id="f7f39-186">WCF によって提供される、信頼できるセッションが有効になっているシステム指定のバインディングの1つを使用するか、これを行う独自のカスタムバインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-186">Use one of the system-provided bindings that WCF provides with the reliable session enabled or create your own custom binding that does this.</span></span>

<span data-ttu-id="f7f39-187">信頼できるセッションが既定でサポートおよび有効化されているシステム定義のバインディングは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f7f39-187">The system-defined bindings that support and enable a reliable session by default include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

<span data-ttu-id="f7f39-188">オプションとして信頼できるセッションをサポートするが、既定では有効にしないシステム指定のバインディングには、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="f7f39-188">The system-provided bindings that support a reliable session as an option but don't enable one by default include:</span></span>

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

<span data-ttu-id="f7f39-189">カスタムバインディングを作成する方法の例については、「 [方法: HTTPS を使用してカスタムの信頼できるセッションのバインディングを作成](how-to-create-a-custom-reliable-session-binding-with-https.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7f39-189">For an example of how to create a custom binding, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

<span data-ttu-id="f7f39-190">信頼できるセッションをサポートする WCF バインディングの詳細については、「 [システム指定のバインディング](../system-provided-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7f39-190">For a discussion of WCF bindings that support reliable sessions, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

## <a name="when-to-use-reliable-sessions"></a><span data-ttu-id="f7f39-191">信頼できるセッションを使用する場合</span><span class="sxs-lookup"><span data-stu-id="f7f39-191">When to use reliable sessions</span></span>

<span data-ttu-id="f7f39-192">アプリケーションで信頼できるセッションを使用するタイミングを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="f7f39-192">It's important to understand when to use reliable sessions in your application.</span></span> <span data-ttu-id="f7f39-193">WCF は、アクティブなエンドポイントとアクティブなエンドポイント間の信頼できるセッションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f7f39-193">WCF supports reliable sessions between endpoints that are active and alive at the same time.</span></span> <span data-ttu-id="f7f39-194">アプリケーションでエンドポイントのいずれかが使用できなくなることが必要な場合は、キューを使用して信頼性を確保します。</span><span class="sxs-lookup"><span data-stu-id="f7f39-194">If your application requires one of the endpoints be unavailable for a duration of time, then use queues to achieve reliability.</span></span>

<span data-ttu-id="f7f39-195">このシナリオで2つのエンドポイントが TCP 経由で接続されている必要がある場合、信頼性の高いメッセージ交換を実現するために TCP が十分である可能性があります</span><span class="sxs-lookup"><span data-stu-id="f7f39-195">If the scenario requires two endpoints connected over TCP, then TCP may be sufficient to provide reliable message exchanges.</span></span> <span data-ttu-id="f7f39-196">ただし、TCP ではパケットが順番に受信され、1回だけ到着することが保証されるため、信頼できるセッションを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f7f39-196">Although, it isn't necessary to use a reliable session, since TCP ensures that the packets arrive in order and only once.</span></span>

<span data-ttu-id="f7f39-197">シナリオに次のいずれかの特性がある場合は、信頼できるセッションの使用を真剣に検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7f39-197">If your scenario has any of the following characteristics, then you must seriously consider using a reliable session.</span></span>

- <span data-ttu-id="f7f39-198">Soap ルーターなどの SOAP 中継局</span><span class="sxs-lookup"><span data-stu-id="f7f39-198">SOAP intermediaries, such as SOAP routers</span></span>

- <span data-ttu-id="f7f39-199">プロキシ中継局またはトランスポートブリッジ</span><span class="sxs-lookup"><span data-stu-id="f7f39-199">Proxy intermediaries or transport bridges</span></span>

- <span data-ttu-id="f7f39-200">断続的な接続</span><span class="sxs-lookup"><span data-stu-id="f7f39-200">Intermittent connectivity</span></span>

- <span data-ttu-id="f7f39-201">HTTP 経由のセッション</span><span class="sxs-lookup"><span data-stu-id="f7f39-201">Sessions over HTTP</span></span>

## <a name="see-also"></a><span data-ttu-id="f7f39-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7f39-202">See also</span></span>

- [<span data-ttu-id="f7f39-203">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="f7f39-203">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f7f39-204">WS 信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="f7f39-204">WS Reliable Session</span></span>](../samples/ws-reliable-session.md)
