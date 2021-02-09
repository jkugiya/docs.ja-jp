---
description: '詳細情報: アプリケーション開発での PNRP'
title: アプリケーション開発での PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: d3e6e9a329f292d3cde7fb906b28452a4e67fb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794885"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="aef5f-103">アプリケーション開発での PNRP</span><span class="sxs-lookup"><span data-stu-id="aef5f-103">PNRP in Application Development</span></span>

<span data-ttu-id="aef5f-104">Windows Vista では、ネットワーク アプリケーションは、簡単な PNRP アプリケーション プログラミング インターフェイス (API) を通して名前発行および名前解決機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="aef5f-104">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="aef5f-105">ピア名解決プロトコルの実装</span><span class="sxs-lookup"><span data-stu-id="aef5f-105">Implementing the Peer Name Resolution Protocol</span></span>  

 <span data-ttu-id="aef5f-106">簡略化された PNRP API では、名前とアドレスを登録するためにクラウドを明示的に指定することはありません。PNRP コンポーネントは、参加する適切なクラウドと、クラウド内で公開するアドレスを、自動的に決定ます。</span><span class="sxs-lookup"><span data-stu-id="aef5f-106">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="aef5f-107">Windows Vista の非常に簡略化された PNRP 名前解決では、Windows Sockets 関数 getaddrinfo() に PNRP 名が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="aef5f-107">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="aef5f-108">PNRP を使って名前を IPv6 アドレスに変換する場合、getaddrinfo() 関数を使って完全修飾ドメイン名 (FQDN) name.prnp.net を解決できます。ここで name は解決されるピア名です。</span><span class="sxs-lookup"><span data-stu-id="aef5f-108">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="aef5f-109">pnrp.net ドメインは、PNRP 名前解決のために Windows Vista で予約されているドメインです。</span><span class="sxs-lookup"><span data-stu-id="aef5f-109">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="aef5f-110">PeerToPeer アプリケーション間でのメッセージの受け渡しは、依然として PeerChannel や WCF の[大規模データとストリーミング](../wcf/feature-details/large-data-and-streaming.md)などの、基盤のアーキテクチャによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="aef5f-110">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef5f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="aef5f-111">See also</span></span>

- <xref:System.Net.PeerToPeer>
