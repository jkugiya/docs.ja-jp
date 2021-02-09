---
description: '詳細情報: IPv6 のルーティング'
title: IPv6 のルーティング
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 75499a7380ab0ea7c38c83a6407a0c2a269b5fce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672037"
---
# <a name="ipv6-routing"></a><span data-ttu-id="dfea2-103">IPv6 のルーティング</span><span class="sxs-lookup"><span data-stu-id="dfea2-103">IPv6 Routing</span></span>

<span data-ttu-id="dfea2-104">柔軟なルーティング メカニズムは、IPv6 の利点です。</span><span class="sxs-lookup"><span data-stu-id="dfea2-104">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="dfea2-105">IPv4 ネットワーク ID が割り当てられた方法のために、インターネット バックボーン上にあるルーターは大規模なルーティング テーブルを保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfea2-105">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="dfea2-106">これらのルーターは、インターネット上の任意のノードに送られる可能性のあるパケットを転送するために、すべてのルートを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfea2-106">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="dfea2-107">アドレスを集計する機能により、IPv6 では、柔軟なアドレス指定が可能であり、ルーティング テーブルのサイズを大幅に縮小することができます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-107">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="dfea2-108">この新しいアドレス指定アーキテクチャでは、中間のルーターは、ネットワークのローカル部分だけを追跡すれば、メッセージを適切に転送できます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-108">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="dfea2-109">近隣探索</span><span class="sxs-lookup"><span data-stu-id="dfea2-109">Neighbor Discovery</span></span>  

 <span data-ttu-id="dfea2-110">近隣探索によって次の機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-110">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="dfea2-111">ルーター探索。</span><span class="sxs-lookup"><span data-stu-id="dfea2-111">Router discovery.</span></span> <span data-ttu-id="dfea2-112">これにより、ホストがローカル ルーターを識別できます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-112">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="dfea2-113">アドレス解決。</span><span class="sxs-lookup"><span data-stu-id="dfea2-113">Address resolution.</span></span> <span data-ttu-id="dfea2-114">これにより、ノードが対応する次ホップ アドレスのリンク層アドレス (アドレス解決プロトコル (ARP) の代替) を解決することができます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-114">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="dfea2-115">アドレスの自動構成。</span><span class="sxs-lookup"><span data-stu-id="dfea2-115">Address auto-configuration.</span></span> <span data-ttu-id="dfea2-116">これにより、ホストが、サイト ローカル アドレスおよびグローバル アドレスを自動的に構成することができます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-116">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="dfea2-117">近隣探索では、次のものを含む IPv6 のインターネット制御メッセージ プロトコル (ICMPv6) メッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="dfea2-117">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="dfea2-118">ルーター アドバタイズ。</span><span class="sxs-lookup"><span data-stu-id="dfea2-118">Router advertisement.</span></span> <span data-ttu-id="dfea2-119">擬似定期的にまたはルーター要請に応じてルーターによって送信されます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-119">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="dfea2-120">IPv6 ルーターは、ルーター アドバタイズを使用して、その可用性、アドレス プレフィックス、およびその他のパラメーターをアドバタイズします。</span><span class="sxs-lookup"><span data-stu-id="dfea2-120">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="dfea2-121">ルーター要請。</span><span class="sxs-lookup"><span data-stu-id="dfea2-121">Router solicitation.</span></span> <span data-ttu-id="dfea2-122">ホストによって送信され、リンク上のルーターがルーター アドバタイズをすぐに送信することを要求します。</span><span class="sxs-lookup"><span data-stu-id="dfea2-122">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="dfea2-123">近隣要請。</span><span class="sxs-lookup"><span data-stu-id="dfea2-123">Neighbor solicitation.</span></span> <span data-ttu-id="dfea2-124">アドレス解決、重複アドレスの検出、または近隣ノードが到達可能であることを確認するためにノードによって送信されます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-124">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="dfea2-125">近隣アドバタイズ。</span><span class="sxs-lookup"><span data-stu-id="dfea2-125">Neighbor advertisement.</span></span> <span data-ttu-id="dfea2-126">近隣要請に応答するかまたはリンク層アドレスの変更を近隣ノードに通知するために、ノードによって送信されます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-126">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="dfea2-127">リダイレクト。</span><span class="sxs-lookup"><span data-stu-id="dfea2-127">Redirect.</span></span> <span data-ttu-id="dfea2-128">送信元ノード向けに特定の宛先へのより良い次ホップ アドレスを示すために、ルーターによって送信されます。</span><span class="sxs-lookup"><span data-stu-id="dfea2-128">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfea2-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfea2-129">See also</span></span>

- [<span data-ttu-id="dfea2-130">インターネット プロトコル バージョン 6</span><span class="sxs-lookup"><span data-stu-id="dfea2-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="dfea2-131">ソケット</span><span class="sxs-lookup"><span data-stu-id="dfea2-131">Sockets</span></span>](sockets.md)
