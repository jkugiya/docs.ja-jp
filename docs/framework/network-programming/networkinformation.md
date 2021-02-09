---
description: '詳細情報: NetworkInformation'
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 9092fd0593d9046f419018b882c08066a6bc654c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785706"
---
# <a name="networkinformation"></a><span data-ttu-id="f9ed6-103">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="f9ed6-103">NetworkInformation</span></span>

<span data-ttu-id="f9ed6-104"><xref:System.Net.NetworkInformation> 名前空間を使用すると、ネットワーク イベント、変更、統計、プロパティについての情報を収集できます。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-104">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="f9ed6-105">また、<xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> クラスを使用して、リモート ホストに到達可能かどうかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-105">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="f9ed6-106">ネットワークの可用性とイベント</span><span class="sxs-lookup"><span data-stu-id="f9ed6-106">Network Availability and Events</span></span>  

 <span data-ttu-id="f9ed6-107"><xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> クラスを使用して、ネットワークのアドレスまたは可用性が変更されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-107">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="f9ed6-108">このクラスを使用するには、変更を処理するイベント ハンドラーを作成し、それを <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> または <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler> に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-108">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="f9ed6-109">詳細については、「[方法: ネットワークの可用性とアドレスの変更を検出する](how-to-detect-network-availability-and-address-changes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-109">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="f9ed6-110">ネットワークの統計情報とプロパティ</span><span class="sxs-lookup"><span data-stu-id="f9ed6-110">Network Statistics and Properties</span></span>  

 <span data-ttu-id="f9ed6-111">インターフェイスまたはプロトコルを使用して、ネットワークの統計情報とプロパティを収集できます。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-111">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="f9ed6-112"><xref:System.Net.NetworkInformation.NetworkInterface>、<xref:System.Net.NetworkInformation.NetworkInterfaceType>、<xref:System.Net.NetworkInformation.PhysicalAddress> の各クラスは、特定のネットワーク インターフェイスについての情報を提供します。一方、<xref:System.Net.NetworkInformation.IPInterfaceProperties>、<xref:System.Net.NetworkInformation.IPGlobalProperties>、<xref:System.Net.NetworkInformation.IPGlobalStatistics>、<xref:System.Net.NetworkInformation.TcpStatistics>、<xref:System.Net.NetworkInformation.UdpStatistics> の各クラスは、レイヤー 3 とレイヤー 4 のパケットについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-112">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="f9ed6-113">詳細については、「[方法: インターフェイス情報とプロトコル情報を取得する](how-to-get-interface-and-protocol-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-113">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="f9ed6-114">リモート ホストに到達可能かどうかの確認</span><span class="sxs-lookup"><span data-stu-id="f9ed6-114">Determine if a Remote Host is Reachable</span></span>  

 <span data-ttu-id="f9ed6-115"><xref:System.Net.NetworkInformation.Ping> クラスを使用して、リモート ホストがネットワークで稼働しているかどうか、また到達可能かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-115">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="f9ed6-116">詳細については、「[方法: ホストに対して ping を実行](how-to-ping-a-host.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9ed6-116">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ed6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9ed6-117">See also</span></span>

- [<span data-ttu-id="f9ed6-118">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="f9ed6-118">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
