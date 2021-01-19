---
title: Peer Name Resolution Protocol
description: セキュリティで保護され、拡張性があり動的な名前登録および名前解決プロトコルであるピア名解決プロトコル (PNRP) について説明します。
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 9ab46566b3c0d6ceff694eca266bdb6e10441374
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98191236"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="8001d-103">Peer Name Resolution Protocol</span><span class="sxs-lookup"><span data-stu-id="8001d-103">Peer Name Resolution Protocol</span></span>

<span data-ttu-id="8001d-104">ピアツーピア環境において、ピアは特定の名前解決システムを使用して、互いのネットワーク上の場所 (アドレス、プロトコル、およびポート) をその名前や他の識別子から解決します。</span><span class="sxs-lookup"><span data-stu-id="8001d-104">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="8001d-105">これまで、ドメイン ネーム システム (DNS) でのピア名の解決は、本質的に一時的な接続やその他の不具合によって複雑化していました。</span><span class="sxs-lookup"><span data-stu-id="8001d-105">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="8001d-106">Microsoft® Windows® ピアツーピア ネットワーク プラットフォームは、ピア名解決プロトコル (PNRP) を使用してこの問題を解決します。PNRP は、セキュリティで保護されたスケーラブルかつ動的な名前登録および名前解決プロトコルで、当初 Windows XP 用に開発され、Windows Vista™ でアップグレードされました。</span><span class="sxs-lookup"><span data-stu-id="8001d-106">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="8001d-107">PNRP は、従来の名前解決システムとは機能が大きく異なり、アプリケーション開発者にとってエキサイティングかつ新しい可能性を開拓します。</span><span class="sxs-lookup"><span data-stu-id="8001d-107">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="8001d-108">PNRP によって、コンピューターまたはコンピューター上の個々のアプリケーションやサービスにピア名を適用できます。</span><span class="sxs-lookup"><span data-stu-id="8001d-108">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="8001d-109">ピア名解決では、アドレス、ポート、拡張ペイロードの名前解決が可能です。</span><span class="sxs-lookup"><span data-stu-id="8001d-109">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="8001d-110">このシステムには、フォールト トレランスがある、ボトルネックが存在しない、古いアドレスが返されない名前解決という利点があり、そのためこのプロトコルは、モバイル ユーザーを検索するための優れたソリューションになります。</span><span class="sxs-lookup"><span data-stu-id="8001d-110">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="8001d-111">セキュリティに関しては、セキュリティで保護するか、セキュリティで保護せずにピア名を公開できます。</span><span class="sxs-lookup"><span data-stu-id="8001d-111">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="8001d-112">PNRP は公開キーの暗号化を使用して、セキュリティで保護されたピア名のなりすましを防止します。コンピューターとサービスの両方に PNRP で名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="8001d-112">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="8001d-113">ピア名解決プロトコルには次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="8001d-113">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="8001d-114">分散型で、ほぼすべてサーバーレス。</span><span class="sxs-lookup"><span data-stu-id="8001d-114">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="8001d-115">サーバーはブートストラップ プロセスのみに必要です。</span><span class="sxs-lookup"><span data-stu-id="8001d-115">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="8001d-116">第三者が関与しないセキュリティで保護された名前の公開。</span><span class="sxs-lookup"><span data-stu-id="8001d-116">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="8001d-117">DNS の名前公開とは異なり、PNRP では即時に名前を公開でき、金銭的コストがかかりません。</span><span class="sxs-lookup"><span data-stu-id="8001d-117">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="8001d-118">PNRP はリアルタイムで更新されるため、古いアドレスの解決が発生しません。</span><span class="sxs-lookup"><span data-stu-id="8001d-118">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="8001d-119">PNRP による名前の解決はコンピューター以外にも拡張でき、サービスの名前解決も可能です。</span><span class="sxs-lookup"><span data-stu-id="8001d-119">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="8001d-120">System.Net.PeerToPeer 名前空間</span><span class="sxs-lookup"><span data-stu-id="8001d-120">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="8001d-121">PNRP の機能は、.NET Framework Version 3.5 内で <xref:System.Net.PeerToPeer> 名前空間によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="8001d-121">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="8001d-122">この機能は、使用可能な PNRP サービスにピア名を登録して解決するために使用できる型のセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="8001d-122">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="8001d-123">(<xref:System.ServiceModel.PeerResolvers> 名前空間で提供される型を使用して、PNRP とカスタム ピア リゾルバーを作成し、インスタンス化することができます。)</span><span class="sxs-lookup"><span data-stu-id="8001d-123">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="8001d-124">使用可能な PNRP サービスに名前を登録して解決するために使用する基本的な型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8001d-124">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="8001d-125"><xref:System.Net.PeerToPeer.Cloud>:使用可能な PNRP クラウドとそのスコープを説明する情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="8001d-125"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="8001d-126"><xref:System.Net.PeerToPeer.PeerName>:クラウド内でピアを登録し、その後解決するために使用できるピア名を定義します。</span><span class="sxs-lookup"><span data-stu-id="8001d-126"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="8001d-127"><xref:System.Net.PeerToPeer.PeerNameRecord>:ピアの登録情報を含む、PNRP クラウド内のレコードを定義します。この情報は、ピアに接続できるネットワーク エンドポイントを含みます。</span><span class="sxs-lookup"><span data-stu-id="8001d-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="8001d-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>:ピア名の登録を開始および停止するメソッドを含む、ピア名の登録プロセスを定義します。</span><span class="sxs-lookup"><span data-stu-id="8001d-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="8001d-129"><xref:System.Net.PeerToPeer.PeerNameResolver>:解決の同期および非同期のメソッドなど、ピア名をネットワーク エンドポイントに解決するためのプロセスを定義します。</span><span class="sxs-lookup"><span data-stu-id="8001d-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8001d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="8001d-130">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="8001d-131">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="8001d-131">Network Programming Samples</span></span>](network-programming-samples.md)
