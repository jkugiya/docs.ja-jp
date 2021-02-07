---
description: 詳細については、「キューと信頼できるセッション」を参照してください。
title: キューと信頼できるセッション
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: 87c2d7cd65228f0218082d9126989db8c9275c70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726911"
---
# <a name="queues-and-reliable-sessions"></a><span data-ttu-id="094c7-103">キューと信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="094c7-103">Queues and Reliable Sessions</span></span>

<span data-ttu-id="094c7-104">キューと信頼できるセッションは、信頼できるメッセージングを実装する Windows Communication Foundation (WCF) 機能です。</span><span class="sxs-lookup"><span data-stu-id="094c7-104">Queues and reliable sessions are the Windows Communication Foundation (WCF) features that implement reliable messaging.</span></span> <span data-ttu-id="094c7-105">このセクションに記載されているトピックでは、WCF の信頼できるメッセージング機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="094c7-105">The topics contained in this section discuss the WCF reliable messaging features.</span></span>  
  
 <span data-ttu-id="094c7-106">信頼できるメッセージングとは、信頼できるメッセージング送信元 (送信元と呼ぶ) から信頼できるメッセージング送信先 (送信先と呼ぶ) にメッセージを確実に転送することを指します。</span><span class="sxs-lookup"><span data-stu-id="094c7-106">Reliable messaging is how a reliable messaging source (called the source) transfers messages reliably to a reliable messaging destination (called the destination).</span></span>  
  
 <span data-ttu-id="094c7-107">信頼できるメッセージングの主要な側面は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="094c7-107">Reliable messaging has the following key aspects:</span></span>  
  
- <span data-ttu-id="094c7-108">メッセージ転送エラーまたはトランスポート エラーに関係なく、送信元から送信先に送られるメッセージの転送が保証されること。</span><span class="sxs-lookup"><span data-stu-id="094c7-108">Transfer assurances for messages sent from a source to a destination regardless of message transfer failure or transport failures.</span></span>  
  
- <span data-ttu-id="094c7-109">送信元と送信先を互いに分離することにより、送信元または送信先が利用できない場合でも、送信元と送信先でのそれぞれ独立したエラーと回復が可能になると共に、信頼できるメッセージの転送と配信が実現されること。</span><span class="sxs-lookup"><span data-stu-id="094c7-109">Separation of the source and the destination from each other, which provides independent failure and recovery of the source and the destination as well as reliable transfer and delivery of messages even though the source or destination is unavailable.</span></span>  
  
 <span data-ttu-id="094c7-110">信頼できるメッセージングを実現すると、待ち時間が長くなることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="094c7-110">Reliable messaging frequently comes at the cost of high latency.</span></span> <span data-ttu-id="094c7-111">待ち時間とは、メッセージが送信元から送信先に到達するまでにかかる時間です。</span><span class="sxs-lookup"><span data-stu-id="094c7-111">Latency is the time it takes for the message to reach the destination from the source.</span></span> <span data-ttu-id="094c7-112">したがって、WCF では、次の種類の信頼できるメッセージングを提供します。</span><span class="sxs-lookup"><span data-stu-id="094c7-112">WCF, therefore, provides the following types of reliable messaging:</span></span>  
  
- <span data-ttu-id="094c7-113">高待機時間のコストなしで信頼性の高い転送を実現する、[信頼できるセッション](reliable-sessions.md)</span><span class="sxs-lookup"><span data-stu-id="094c7-113">[Reliable Sessions](reliable-sessions.md), which offer reliable transfer without the cost of high latency</span></span>  
  
- <span data-ttu-id="094c7-114">[WCF のキュー](queues-in-wcf.md)。信頼できる転送と、ソースと宛先の分離の両方を提供します。</span><span class="sxs-lookup"><span data-stu-id="094c7-114">[Queues in WCF](queues-in-wcf.md), which offer both reliable transfers and separation between the source and the destination.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="094c7-115">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="094c7-115">Reliable Sessions</span></span>  

 <span data-ttu-id="094c7-116">信頼できるセッションでは、メッセージング (送信元および送信先) エンドポイントを分離する中継局の数や種類に関係なく、WS-ReliableMessaging プロトコルを使用して、送信元から送信先へのエンドツーエンドの信頼できるメッセージ転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="094c7-116">Reliable sessions provide end-to-end reliable transfer of messages between a source and a destination using the WS-ReliableMessaging protocol regardless of the number or type of intermediaries that separate the messaging (source and destination) endpoints.</span></span> <span data-ttu-id="094c7-117">これには SOAP を使用しないトランスポート手段 (HTTP プロキシなど)、またはエンドポイント間でメッセージをやりとりする場合に必要となる SOAP を使用する手段 (SOAP ベースのルーターやブリッジなど) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="094c7-117">This includes any transport intermediaries that do not use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="094c7-118">信頼できるセッションでは、メモリ内転送ウィンドウを使用して、トランスポート エラーが発生した場合に SOAP メッセージ レベル エラーをマスクし、接続を再確立します。</span><span class="sxs-lookup"><span data-stu-id="094c7-118">Reliable sessions use an in-memory transfer window to mask SOAP message-level failures and re-establish connections in the case of transport failures.</span></span>  
  
 <span data-ttu-id="094c7-119">信頼できるセッションは、待ち時間の短い、信頼できるメッセージ転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="094c7-119">Reliable sessions provide low-latency reliable message transfers.</span></span> <span data-ttu-id="094c7-120">これらは、TCP が IP ブリッジ経由のパケットで実現するものと同等の転送を、プロキシや中継局経由の SOAP メッセージで実現します。</span><span class="sxs-lookup"><span data-stu-id="094c7-120">They provide for SOAP messages over any proxies or intermediaries, equivalent to what TCP provides for packets over IP bridges.</span></span> <span data-ttu-id="094c7-121">信頼できるセッションの詳細については、「 [信頼できるセッション](reliable-sessions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="094c7-121">For more information about reliable sessions, see [Reliable Sessions](reliable-sessions.md).</span></span>  
  
## <a name="queues"></a><span data-ttu-id="094c7-122">キュー</span><span class="sxs-lookup"><span data-stu-id="094c7-122">Queues</span></span>  

 <span data-ttu-id="094c7-123">WCF のキューは、待機時間の長いコストで、メッセージの信頼性の高い転送と、送信元と送信先の分離の両方を提供します。</span><span class="sxs-lookup"><span data-stu-id="094c7-123">Queues in WCF provide both reliable transfers of messages and separation between sources and destinations at the cost of high latency.</span></span> <span data-ttu-id="094c7-124">WCF キュー通信は、メッセージキュー (MSMQ とも呼ばれる) 上に構築されています。</span><span class="sxs-lookup"><span data-stu-id="094c7-124">WCF queued communication is built on top of Message Queuing (also known as MSMQ).</span></span>  
  
 <span data-ttu-id="094c7-125">MSMQ は Windows にオプションとして付属し、NT サービスの 1 つとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="094c7-125">MSMQ is shipped as an option with Windows that runs as an NT service.</span></span> <span data-ttu-id="094c7-126">MSMQ サービスは、送信元の代わりに転送キューで転送用のメッセージを取得し、ターゲット キューに配信します。</span><span class="sxs-lookup"><span data-stu-id="094c7-126">It captures messages for transmission in a transmission queue on behalf of the source and delivers it to a target queue.</span></span> <span data-ttu-id="094c7-127">ターゲット キューは、送信先の代わりにメッセージを受け取り、後で送信先がメッセージを要求したときに配信します。</span><span class="sxs-lookup"><span data-stu-id="094c7-127">The target queue accepts messages on behalf of the destination for later delivery whenever the destination requests for messages.</span></span> <span data-ttu-id="094c7-128">MSMQ キュー マネージャーは信頼できるメッセージ転送プロトコルを実装して、送信中にメッセージが失われないようにします。</span><span class="sxs-lookup"><span data-stu-id="094c7-128">The MSMQ queue managers implement a reliable message-transfer protocol so that messages are not lost in transmission.</span></span> <span data-ttu-id="094c7-129">このプロトコルは、ネイティブまたは SOAP リライアブル メッセージ プロトコル (SRMP) などの SOAP ベースのプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="094c7-129">The protocol can be native or SOAP-based, such as Soap Reliable Messaging Protocol (SRMP).</span></span>  
  
 <span data-ttu-id="094c7-130">キュー間でのメッセージの信頼できる転送に加え、送信元と送信先の分離により、疎結合されたアプリケーションで信頼できる通信を実現できます。</span><span class="sxs-lookup"><span data-stu-id="094c7-130">The separation, coupled with reliable message transfers between queues, enables applications that are loosely coupled to communicate reliably.</span></span> <span data-ttu-id="094c7-131">信頼できるセッションとは異なり、送信元と送信先が同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="094c7-131">Unlike reliable sessions, the source and destination do not have to be running at the same time.</span></span> <span data-ttu-id="094c7-132">このため、送信元によるメッセージの生成レートと送信先によるメッセージの消費レートが一致しないときに、キューを実質的に負荷平準化機構として使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="094c7-132">This implicitly enables scenarios where queues are, in effect, used as a load-leveling mechanism when there is a mismatch between the rate of message production by the source and the rate of the message consumption by the destination.</span></span> <span data-ttu-id="094c7-133">キューの詳細については、「 [WCF のキュー](queues-in-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="094c7-133">For more information about queues, see [Queues in WCF](queues-in-wcf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="094c7-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="094c7-134">See also</span></span>

- [<span data-ttu-id="094c7-135">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="094c7-135">Queues in WCF</span></span>](queues-in-wcf.md)
- [<span data-ttu-id="094c7-136">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="094c7-136">Queuing in WCF</span></span>](queuing-in-wcf.md)
- [<span data-ttu-id="094c7-137">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="094c7-137">Reliable Sessions</span></span>](reliable-sessions.md)
- [<span data-ttu-id="094c7-138">信頼できるセッションの概要</span><span class="sxs-lookup"><span data-stu-id="094c7-138">Reliable Sessions Overview</span></span>](reliable-sessions-overview.md)
