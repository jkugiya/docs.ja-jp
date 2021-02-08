---
description: '詳細については、次を参照してください: Reliable Services'
title: Reliable Service
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: c38f949e57b1891da2433875571443656c7044dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779206"
---
# <a name="reliable-services"></a><span data-ttu-id="ab7ca-103">Reliable Service</span><span class="sxs-lookup"><span data-stu-id="ab7ca-103">Reliable Services</span></span>

<span data-ttu-id="ab7ca-104">キューと信頼できるセッションは、信頼できるメッセージングを実装する Windows Communication Foundation (WCF) 機能です。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-104">Queues and reliable sessions are the Windows Communication Foundation (WCF) features that implement reliable messaging.</span></span> <span data-ttu-id="ab7ca-105">このトピックでは、WCF の信頼できるメッセージング機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-105">This topic explains the reliable messaging features of WCF.</span></span>  
  
 <span data-ttu-id="ab7ca-106">信頼できる *メッセージング* とは、信頼できるメッセージの送信元 (*送信元* と呼ばれます) が、信頼できるメッセージの送信先 (*送信先* と呼ばれます) にメッセージを確実に転送する方法です。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-106">*Reliable messaging* is how a reliable messaging source (called the *source*) transfers messages reliably to a reliable messaging destination (called the *destination*).</span></span>  
  
 <span data-ttu-id="ab7ca-107">信頼できるメッセージングは、次の機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-107">Reliable messaging performs the following functions:</span></span>  
  
- <span data-ttu-id="ab7ca-108">メッセージ転送エラーまたはトランスポート エラーに関係なく、送信元から送信先に送られるメッセージの転送が保証されること。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-108">Transfers assurances for messages sent from a source to a destination regardless of message transfer or transport failures.</span></span>  
  
- <span data-ttu-id="ab7ca-109">送信元と送信先を互いに分離すること。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-109">Separates the source and the destination from each other.</span></span> <span data-ttu-id="ab7ca-110">これにより、送信元または送信先が利用できない場合でも、送信元と送信先でのそれぞれ独立したエラーと回復が可能になると共に、信頼できるメッセージの転送と配信が実現されます。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-110">This provides independent failure and recovery of the source and the destination, as well as reliable transfer and delivery of messages, even when the source or destination is unavailable.</span></span>  
  
 <span data-ttu-id="ab7ca-111">信頼できるメッセージングを実現すると、待ち時間が長くなることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-111">Reliable messaging frequently comes at the cost of high latency.</span></span> <span data-ttu-id="ab7ca-112">*待機* 時間とは、メッセージが送信元から送信先に到着するまでにかかる時間です。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-112">*Latency* is the time it takes for the message to reach the destination from the source.</span></span> <span data-ttu-id="ab7ca-113">したがって、WCF では、次の種類の信頼できるメッセージングを提供します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-113">WCF, therefore, provides the following types of reliable messaging:</span></span>  
  
- <span data-ttu-id="ab7ca-114">[信頼できるセッション](./feature-details/reliable-sessions.md)。高待機時間のコストを発生させることなく、信頼性の高い転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-114">[Reliable Sessions](./feature-details/reliable-sessions.md), which offers reliable transfer without the cost of high latency.</span></span>  
  
- <span data-ttu-id="ab7ca-115">[WCF のキュー](./feature-details/queues-in-wcf.md)。信頼できる転送と、ソースと宛先の分離の両方を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-115">[Queues in WCF](./feature-details/queues-in-wcf.md), which offers both reliable transfers and separation between the source and the destination.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="ab7ca-116">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="ab7ca-116">Reliable Sessions</span></span>  

 <span data-ttu-id="ab7ca-117">信頼できるセッションでは、メッセージング (送信元および送信先) エンドポイントを分離する中継局の数や種類に関係なく、WS-ReliableMessaging プロトコルを使用して、送信元から送信先へのエンドツーエンドの信頼できるメッセージ転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-117">Reliable sessions provide end-to-end reliable transfer of messages between a source and a destination using the WS-Reliable Messaging protocol, regardless of the number or type of intermediaries that separate the messaging (source and destination) endpoints.</span></span> <span data-ttu-id="ab7ca-118">これには SOAP を使用しないトランスポート手段 (HTTP プロキシなど)、またはエンドポイント間でメッセージをやりとりする場合に必要となる SOAP を使用する手段 (SOAP ベースのルーターやブリッジなど) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-118">This includes any transport intermediaries that do not use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="ab7ca-119">信頼できるセッションでは、メモリ内転送ウィンドウを使用して、トランスポート エラーが発生した場合に SOAP メッセージ レベル エラーをマスクし、接続を再確立します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-119">Reliable sessions use an in-memory transfer window to mask SOAP message-level failures and re-establish connections in the case of transport failures.</span></span>  
  
 <span data-ttu-id="ab7ca-120">信頼できるセッションは、待ち時間の短い、信頼できるメッセージ転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-120">Reliable sessions provide low-latency reliable message transfers.</span></span> <span data-ttu-id="ab7ca-121">これらは、TCP が IP ブリッジ経由のパケットで実現するものと同等の転送を、プロキシや中継局経由の SOAP メッセージで実現します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-121">They provide for SOAP messages over any proxies or intermediaries, equivalent to what TCP provides for packets over IP bridges.</span></span> <span data-ttu-id="ab7ca-122">信頼できるセッションの詳細については、「 [信頼できるセッション](./feature-details/reliable-sessions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-122">For more information about reliable sessions, see [Reliable Sessions](./feature-details/reliable-sessions.md).</span></span>  
  
### <a name="queues"></a><span data-ttu-id="ab7ca-123">キュー</span><span class="sxs-lookup"><span data-stu-id="ab7ca-123">Queues</span></span>  

 <span data-ttu-id="ab7ca-124">WCF のキューは、待機時間の長いコストで、メッセージの信頼性の高い転送と、送信元と送信先の分離の両方を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-124">Queues in WCF provide both reliable transfers of messages and separation between sources and destinations at the cost of high latency.</span></span> <span data-ttu-id="ab7ca-125">WCF キュー通信は、メッセージキュー (MSMQ) 上に構築されています。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-125">WCF queued communication is built on top of Message Queuing (MSMQ).</span></span>  
  
 <span data-ttu-id="ab7ca-126">MSMQ は Windows のオプション コンポーネントとして付属します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-126">MSMQ ships as an optional component with Windows.</span></span> <span data-ttu-id="ab7ca-127">MSMQ サービスは Windows サービスの 1 つとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-127">The MSMQ service runs as a Windows Service.</span></span> <span data-ttu-id="ab7ca-128">MSMQ サービスは、送信元の代わりに転送キューで転送用のメッセージを取得し、ターゲット キューに配信します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-128">It captures messages for transmission in a transmission queue on behalf of the source and delivers it to a target queue.</span></span> <span data-ttu-id="ab7ca-129">ターゲット キューは、送信先の代わりにメッセージを受け取り、後で送信先がメッセージを要求したときに配信します。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-129">The target queue accepts messages on behalf of the destination for later delivery whenever the destination requests messages.</span></span> <span data-ttu-id="ab7ca-130">MSMQ マネージャーは信頼できるメッセージ転送プロトコルを実装するため、転送中にメッセージが失われることはありません。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-130">The MSMQ managers implement a reliable message-transfer protocol so that messages are not lost in transmission.</span></span> <span data-ttu-id="ab7ca-131">このプロトコルは、ネイティブまたは SOAP リライアブル メッセージ プロトコル (SRMP) と呼ばれる SOAP ベースのプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-131">The protocol can be native or a SOAP-based protocol called SOAP Reliable Messaging Protocol (SRMP).</span></span>  
  
 <span data-ttu-id="ab7ca-132">キュー間でのメッセージの信頼できる転送に加え、送信元と送信先の分離により、疎結合されたアプリケーションで信頼できる通信を実現できます。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-132">The separation, coupled with reliable message transfers between queues, enables applications that are loosely coupled to communicate reliably.</span></span> <span data-ttu-id="ab7ca-133">信頼できるセッションとは異なり、送信元と送信先が同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-133">Unlike reliable sessions, the source and destination do not have to be running at the same time.</span></span> <span data-ttu-id="ab7ca-134">このため、送信元によるメッセージの生成レートと送信先によるメッセージの消費レートが一致しないときに、キューが実質上、負荷平準化機構として使用されるというシナリオが暗黙的に可能になります。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-134">This implicitly enables scenarios where queues are, in effect, used as a load-leveling mechanism when the source's rate of message production and the destination's rate of the message consumption do not match.</span></span> <span data-ttu-id="ab7ca-135">キューの詳細については、「 [WCF のキュー](./feature-details/queues-in-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab7ca-135">For more information about queues, see [Queues in WCF](./feature-details/queues-in-wcf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7ca-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab7ca-136">See also</span></span>

- [<span data-ttu-id="ab7ca-137">信頼できるセッションの概要</span><span class="sxs-lookup"><span data-stu-id="ab7ca-137">Reliable Sessions Overview</span></span>](./feature-details/reliable-sessions-overview.md)
- [<span data-ttu-id="ab7ca-138">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="ab7ca-138">Queuing in WCF</span></span>](./feature-details/queuing-in-wcf.md)
