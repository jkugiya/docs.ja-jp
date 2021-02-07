---
description: '詳細情報: ピアメッシュ'
title: ピア メッシュ
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: bedb8931c4ed4c4f62cb3556699d7f9f07f6f022
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733386"
---
# <a name="peer-meshes"></a><span data-ttu-id="726f4-103">ピア メッシュ</span><span class="sxs-lookup"><span data-stu-id="726f4-103">Peer Meshes</span></span>

<span data-ttu-id="726f4-104">*メッシュ* とは、ピアノードの名前付きコレクション (相互接続されたグラフ) であり、一意のメッシュ ID によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="726f4-104">A *mesh* is a named collection (an interconnected graph) of peer nodes that can communicate among themselves and that are identified by a unique mesh ID.</span></span> <span data-ttu-id="726f4-105">各ノードは複数の別のノードに接続されています。</span><span class="sxs-lookup"><span data-stu-id="726f4-105">Each node is connected to multiple other nodes.</span></span> <span data-ttu-id="726f4-106">適切に接続されたメッシュでは、任意の2つのノード間にパスがあります。メッシュの最も遠い端のノード間には比較的少ないホップがあり、一部のノードまたは接続が削除されてもメッシュは接続されたままになります。メッシュ内のアクティブノードは、他のピアが検出できるように、対応するメッシュ ID を使用してエンドポイント情報を発行します。</span><span class="sxs-lookup"><span data-stu-id="726f4-106">In a well-connected mesh, there is a path between any two nodes, with relatively few hops between the nodes on the furthest edges of the mesh, and the mesh will remain connected even if some nodes or connections drop out. Active nodes in the mesh publish their endpoint information with a corresponding mesh ID so that other peers can find them.</span></span>  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a><span data-ttu-id="726f4-107">ピア メッシュを使用して作成されたメッシュの特徴</span><span class="sxs-lookup"><span data-stu-id="726f4-107">Characteristics of a Mesh Created Using Peer Channel</span></span>  
  
#### <a name="uniquely-identified"></a><span data-ttu-id="726f4-108">一意の識別</span><span class="sxs-lookup"><span data-stu-id="726f4-108">Uniquely Identified</span></span>  
  
- <span data-ttu-id="726f4-109">一意の ID によって各メッシュが識別されます。</span><span class="sxs-lookup"><span data-stu-id="726f4-109">A unique ID identifies each mesh.</span></span> <span data-ttu-id="726f4-110">メッシュ名 (メッシュ ID) はドメイン ネーム システム (DNS) ホスト名と同じ形式です。</span><span class="sxs-lookup"><span data-stu-id="726f4-110">The name of the mesh (or mesh ID) is in the same format as a Domain Name System (DNS) host name.</span></span> <span data-ttu-id="726f4-111">したがって、このメッシュ ID は、アプリケーションの対象クライアントに対して、リゾルバーの使用範囲内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="726f4-111">As such, this mesh ID must be unique for the intended client of the application within the scope of the resolver being used.</span></span> <span data-ttu-id="726f4-112">"MyFamilysPeers" や "KevinsPokerTable" のような一般的な名前にすると、他のユーザー名と容易に衝突する可能性があり、意図しないピア エンドポイントの情報が返る場合があります。その結果、プライバシーの問題が発生したり、接続の待ち時間が増加したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="726f4-112">A common name such as "MyFamilysPeers" or "KevinsPokerTable," may easily collide with other user names and may return unintended peer endpoint information, which could result in privacy issues or increase connection latency.</span></span> <span data-ttu-id="726f4-113">このような問題を回避する 1 つの方法は、一意の ID をメッシュのニックネームの接尾辞として追加することです (たとえば、"KevinsPokerTable90210" のようにします)。</span><span class="sxs-lookup"><span data-stu-id="726f4-113">One way to avoid these issues may be to add a unique ID as a postfix to the nickname for the mesh (for example, "KevinsPokerTable90210").</span></span>  
  
#### <a name="message-flooding"></a><span data-ttu-id="726f4-114">大量のメッセージ</span><span class="sxs-lookup"><span data-stu-id="726f4-114">Message Flooding</span></span>  
  
- <span data-ttu-id="726f4-115">メッシュでは、1 人以上の送信者から同じメッシュ内の他のすべてのピア ノードにメッセージを伝達できます。</span><span class="sxs-lookup"><span data-stu-id="726f4-115">The mesh allows messages to be propagated from one or more senders to all other peer nodes in the same mesh.</span></span> <span data-ttu-id="726f4-116">ピア ノードから大量に送られたメッセージは、`http://schemas.microsoft.com/net/2006/05/peer` の名前空間で指定されたヘッダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="726f4-116">Messages flooded by peer nodes use headers specified in the namespace at `http://schemas.microsoft.com/net/2006/05/peer`.</span></span>  
  
#### <a name="optimized-connections"></a><span data-ttu-id="726f4-117">最適化された接続</span><span class="sxs-lookup"><span data-stu-id="726f4-117">Optimized Connections</span></span>  
  
- <span data-ttu-id="726f4-118">ノードが参加したり離脱したりすると、ピア チャネル メッシュが自動的に調整されます。これにより、良好な接続が維持され、パーティション (互いに分離するノード グループ) が作成される可能性はほとんどなくなります。</span><span class="sxs-lookup"><span data-stu-id="726f4-118">A Peer Channel mesh automatically adjusts when nodes join and leave, ensuring that all nodes have good connectivity with little chance of creating partitions (groups of nodes isolated from each other).</span></span> <span data-ttu-id="726f4-119">メッシュ内の接続は現在のトラフィック パターンに基づいて動的に最適化され、送信者から受信者へのメッセージの待ち時間は可能な限り短縮されます。</span><span class="sxs-lookup"><span data-stu-id="726f4-119">Connections in the mesh are also dynamically optimized based on current traffic patterns so that message latency from sender to receiver is as small as possible.</span></span>  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a><span data-ttu-id="726f4-120">ピア チャネルで提供されない一般的なネットワーク機能</span><span class="sxs-lookup"><span data-stu-id="726f4-120">Popular Network Features That Peer Channel Does Not Provide</span></span>  

 <span data-ttu-id="726f4-121">ピア チャネルで提供されない一般的なネットワーク機能を認識しておくことは重要です。</span><span class="sxs-lookup"><span data-stu-id="726f4-121">It is important to be aware of popular network features that Peer Channel does not provide.</span></span> <span data-ttu-id="726f4-122">その機能 (ピア チャネルの上にすべて構築される場合もあります) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="726f4-122">These features, which may all be built on top of Peer Channel, include the following:</span></span>  
  
- <span data-ttu-id="726f4-123">**メッセージの順序付け:** 1つのソースから送信されたメッセージは、同じ順序で、または送信元が送信した順序で、他のすべてのパーティに到達することはできません。</span><span class="sxs-lookup"><span data-stu-id="726f4-123">**Message ordering:** Messages originating from a single source may not arrive at all other parties in the same order or in the order that the source sent.</span></span> <span data-ttu-id="726f4-124">メッセージを特定の順序で配信する必要のあるアプリケーションでは、その順序をアプリケーションに組み込む必要があります (決まった値で増加する ID をすべてのメッセージに含めるなど)。</span><span class="sxs-lookup"><span data-stu-id="726f4-124">Applications that require messages be delivered in a certain order must build it into their applications (for example, by including a monotonically increasing ID with all messages).</span></span>  
  
- <span data-ttu-id="726f4-125">**信頼できるメッセージング:** ピアチャネルには、すべてのピアによるメッセージの受信を保証するメカニズムは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="726f4-125">**Reliable messaging:** Peer Channel does not include a mechanism to ensure message reception by all peers.</span></span> <span data-ttu-id="726f4-126">メッセージの配信を保証するには、信頼性の層をピア チャネルの上に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="726f4-126">To guarantee message delivery, you must write a reliability layer on top of Peer Channel.</span></span>
