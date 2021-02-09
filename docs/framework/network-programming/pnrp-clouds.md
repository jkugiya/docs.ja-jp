---
description: '詳細情報: PNRP クラウド'
title: PNRP クラウド
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 82e9fe85e019d1ef53fa35ed49d55cd2759b4335
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794898"
---
# <a name="pnrp-clouds"></a><span data-ttu-id="b0166-103">PNRP クラウド</span><span class="sxs-lookup"><span data-stu-id="b0166-103">PNRP Clouds</span></span>

<span data-ttu-id="b0166-104">PNRP "クラウド" は、ネットワーク経由で相互に通信できるノードのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="b0166-104">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="b0166-105">"クラウド" という用語は、"ピア メッシュ" や "ピアツーピア グラフ" と同義です。</span><span class="sxs-lookup"><span data-stu-id="b0166-105">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="b0166-106">異なるクラウド間でノード間通信を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="b0166-106">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="b0166-107"><xref:System.Net.PeerToPeer.Cloud> インスタンスは、名前によって一意に識別されます。名前は大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="b0166-107">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="b0166-108">1 つのピアまたはノードを、複数のクラウドに接続できます。</span><span class="sxs-lookup"><span data-stu-id="b0166-108">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="b0166-109">クラウドは、ネットワーク インターフェイスに非常に密接に結び付けられています。</span><span class="sxs-lookup"><span data-stu-id="b0166-109">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="b0166-110">異なるサブネットに接続された 2 つのネットワーク カードを備えるマルチホーム コンピューターでは、3 つのクラウドが返されます。1 インターフェイスにつきリンクローカル アドレスごとに 1 つ、グローバル スコープ クラウド用に 1 つです。</span><span class="sxs-lookup"><span data-stu-id="b0166-110">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="b0166-111">PNRP は 3 つのクラウド "スコープ" を使います。スコープとは、互いに検出可能なコンピューターをグループ化したものです。</span><span class="sxs-lookup"><span data-stu-id="b0166-111">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
- <span data-ttu-id="b0166-112">グローバル クラウドはグローバル IPv6 アドレス スコープとグローバル アドレスに対応し、IPv6 インターネット全体のすべてのコンピューターを表しています。</span><span class="sxs-lookup"><span data-stu-id="b0166-112">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="b0166-113">グローバル クラウドは 1 つしか存在しません。</span><span class="sxs-lookup"><span data-stu-id="b0166-113">There is only a single global cloud.</span></span>  
  
- <span data-ttu-id="b0166-114">リンクローカル クラウドは、リンクローカル IPv6 アドレス スコープとリンクローカル アドレスに対応します。</span><span class="sxs-lookup"><span data-stu-id="b0166-114">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="b0166-115">リンクローカル クラウドは特定のリンクに使います。このリンクは通常、ローカルにアタッチされているサブネットに相当します。</span><span class="sxs-lookup"><span data-stu-id="b0166-115">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="b0166-116">リンクローカル クラウドは複数存在できます。</span><span class="sxs-lookup"><span data-stu-id="b0166-116">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="b0166-117">3 番目のクラウドであるサイト固有クラウドは、IPv6 アドレス スコープとサイトローカル アドレスに対応します。</span><span class="sxs-lookup"><span data-stu-id="b0166-117">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="b0166-118">サイト固有クラウドは非推奨とされますが、PNRP ではまだサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b0166-118">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="b0166-119">クラウド</span><span class="sxs-lookup"><span data-stu-id="b0166-119">Clouds</span></span>  

 <span data-ttu-id="b0166-120">PNRP クラウドは、<xref:System.Net.PeerToPeer.Cloud> クラスのインスタンスで表されます。</span><span class="sxs-lookup"><span data-stu-id="b0166-120">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="b0166-121">ピアを使うクラウドのグループは、列挙可能な <xref:System.Net.PeerToPeer.CloudCollection> クラスのインスタンスによって表されます。</span><span class="sxs-lookup"><span data-stu-id="b0166-121">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="b0166-122">現在のピアに認識される PNRP クラウドのコレクションは、静的 <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> メソッドを呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="b0166-122">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="b0166-123">個々のクラウドには、256 文字の Unicode 文字列として表される一意の名前があります。</span><span class="sxs-lookup"><span data-stu-id="b0166-123">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="b0166-124">これらの名前および上記のスコープは、クラウド クラスの一意のインスタンスを作成するために使われます。</span><span class="sxs-lookup"><span data-stu-id="b0166-124">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="b0166-125">これらのインスタンスは、永続的な使用のためにシリアル化および再構築できます。</span><span class="sxs-lookup"><span data-stu-id="b0166-125">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="b0166-126">クラウド インスタンスを作成または取得した後は、それにピア名を登録して、既知のピアのメッシュを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b0166-126">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0166-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0166-127">See also</span></span>

- <xref:System.Net.PeerToPeer.Cloud>
- [<span data-ttu-id="b0166-128">ピア名解決プロトコル</span><span class="sxs-lookup"><span data-stu-id="b0166-128">Peer Name Resolution Protocol</span></span>](peer-name-resolution-protocol.md)
