---
description: '詳細情報: System.Net.PeerToPeer.Collaboration 名前空間について'
title: System.Net.PeerToPeer.Collaboration 名前空間について
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: cb51208b2424b93e963101943652c57f0266baf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801918"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a><span data-ttu-id="67a6e-103">System.Net.PeerToPeer.Collaboration 名前空間について</span><span class="sxs-lookup"><span data-stu-id="67a6e-103">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>

<span data-ttu-id="67a6e-104"><xref:System.Net.PeerToPeer.Collaboration> 名前空間は、ピア ツー ピア共同作業インフラストラクチャを使用してピア共同作業アクティビティを実装するために使用されるクラスと API を提供します。</span><span class="sxs-lookup"><span data-stu-id="67a6e-104">The <xref:System.Net.PeerToPeer.Collaboration> namespace provides classes and APIs that are used to implement peer collaboration activities using the Peer-to-Peer Collaboration Infrastructure.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="67a6e-105">クラス</span><span class="sxs-lookup"><span data-stu-id="67a6e-105">Classes</span></span>  

 <span data-ttu-id="67a6e-106">ピア ツー ピア共同作業アクティビティの実装に使用される主なクラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="67a6e-106">The main classes used in the implementation of a Peer-to-Peer Collaboration activity are:</span></span>  
  
- <span data-ttu-id="67a6e-107">ピアの連絡先を格納するために使用できる <xref:System.Net.PeerToPeer.Collaboration.ContactManager>。</span><span class="sxs-lookup"><span data-stu-id="67a6e-107">The <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, which can be used to store peer contacts.</span></span>  
  
- <span data-ttu-id="67a6e-108">ゲーム、チャット クライアント、または会議ソリューションなど、共同作業を行う <xref:System.Net.PeerToPeer.Collaboration.PeerApplication>。</span><span class="sxs-lookup"><span data-stu-id="67a6e-108">The <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> in which to collaborate, such as a game, chat client, or conferencing solution.</span></span>  
  
- <span data-ttu-id="67a6e-109">アクティビティで共同作業を行うピア。</span><span class="sxs-lookup"><span data-stu-id="67a6e-109">The peers that will be collaborating in an activity.</span></span>  <span data-ttu-id="67a6e-110">これらのピアは <xref:System.Net.PeerToPeer.Collaboration.PeerContact>、<xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>、または <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> オブジェクトとして表すことができます。</span><span class="sxs-lookup"><span data-stu-id="67a6e-110">These peers can be represented as <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, or <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> objects.</span></span>  
  
- <span data-ttu-id="67a6e-111">使用可能なアプリケーションと、そのアプリケーションに参加するピアを指定する、静的な <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> クラス自体。</span><span class="sxs-lookup"><span data-stu-id="67a6e-111">The static <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> class itself, which specifies which applications are available and which peers are participating in them.</span></span>  
  
 <span data-ttu-id="67a6e-112"><xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> メソッドは、共同作業セッションにピアを招待するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="67a6e-112">The <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> methods are used to invite peers to a collaboration session.</span></span>  <span data-ttu-id="67a6e-113">呼び出し元のピアは、共同作業セッションに関連付けられているアプリケーション、オブジェクト、またはプレゼンス情報の更新を通知するイベントの別のピアにサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="67a6e-113">A calling peer can subscribe to another peer for events that signal updates to application, object, or presence information affiliated with the collaboration session.</span></span> <span data-ttu-id="67a6e-114">プレゼンス クラスは <xref:System.Net.PeerToPeer.Collaboration.Peer> が共同作業で使用可能かどうかを指定し、<xref:System.Net.PeerToPeer.Collaboration.PeerScope> クラスはピアに許可される参加レベルとして <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (グローバル)、<xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe> (サブネット) または <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None> を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="67a6e-114">Presence classes specify whether a <xref:System.Net.PeerToPeer.Collaboration.Peer> is available for collaboration, and the <xref:System.Net.PeerToPeer.Collaboration.PeerScope> class is used to specify how much participation is allowed for a peer:  <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (global), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (subnet) or <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.</span></span>  
  
 <span data-ttu-id="67a6e-115">共同作業セッションは、次の 4 つの手順で構成されます。</span><span class="sxs-lookup"><span data-stu-id="67a6e-115">A collaboration session is comprised of four steps:</span></span>  
  
- <span data-ttu-id="67a6e-116">検出。</span><span class="sxs-lookup"><span data-stu-id="67a6e-116">Discovery.</span></span> <span data-ttu-id="67a6e-117">アプリケーション、ピア、およびプレゼンス情報を検出または公開します。</span><span class="sxs-lookup"><span data-stu-id="67a6e-117">Discover or publish applications, peers, and presence information.</span></span>  <span data-ttu-id="67a6e-118">たとえば、同じゲームをインストールしている、ローカル サブネット上の他のユーザーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="67a6e-118">For instance, find other people on the local subnet that have the same games installed.</span></span>  
  
- <span data-ttu-id="67a6e-119">招待。</span><span class="sxs-lookup"><span data-stu-id="67a6e-119">Invitation.</span></span> <span data-ttu-id="67a6e-120"><xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> セッションを開始する、またはそのセッションに参加するリモート ピア (複数可) のセキュリティで保護された招待状を送信および承諾します。</span><span class="sxs-lookup"><span data-stu-id="67a6e-120">Send and accept secure invitations for remote peer(s) to start or join <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> sessions.</span></span>  
  
- <span data-ttu-id="67a6e-121">連絡先の管理。</span><span class="sxs-lookup"><span data-stu-id="67a6e-121">Contact Management.</span></span> <span data-ttu-id="67a6e-122"><xref:System.Net.PeerToPeer.Collaboration.ContactManager> に連絡先として検出されたピアを追加します。</span><span class="sxs-lookup"><span data-stu-id="67a6e-122">Add discovered peers as a contact to a <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.</span></span>  
  
- <span data-ttu-id="67a6e-123">通信。</span><span class="sxs-lookup"><span data-stu-id="67a6e-123">Communication.</span></span> <span data-ttu-id="67a6e-124">通信が確立されたら、<xref:System.Net> API、<xref:System.Net.PeerToPeer> API、または Windows Communication Foundation のピア チャネル クラス (マルチパーティ通信用) を使用します。</span><span class="sxs-lookup"><span data-stu-id="67a6e-124">When communication is established, use the <xref:System.Net> APIs, the <xref:System.Net.PeerToPeer> API, or the Windows Communication Foundation Peer Channel classes for multiparty communications.</span></span>  
  
 <span data-ttu-id="67a6e-125">たとえば、ホスト ピアは共同作業セッションを開始し、<xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> メソッドを利用して、リモート ピアとそのローカル ピアのいずれかをホスト ピアの Contact Manager に追加します。</span><span class="sxs-lookup"><span data-stu-id="67a6e-125">For example, the host peer starts a collaboration session, and utilizes the <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> method to add a remote peer and one of its local peers to the Contact Manager of the host peer.</span></span>  <span data-ttu-id="67a6e-126">その後、3 人のユーザーは独自のプライベート共同作業セッションに参加します。</span><span class="sxs-lookup"><span data-stu-id="67a6e-126">The three users will then participate in their own private collaboration session.</span></span>  
  
 <span data-ttu-id="67a6e-127">一般的な P2P アプリケーションには、共有ノート作成機能またはホワイトボードを利用する電話会議、サーバーレスのチャット アプリケーション、双方向広告、およびオンライン ゲーム セッションなどがあります。</span><span class="sxs-lookup"><span data-stu-id="67a6e-127">Typical P2P applications are: conference calls for collaborative note-taking or whiteboarding, serverless chat applications, interactive advertisements, and online gaming sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a6e-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="67a6e-128">See also</span></span>

- <xref:System.Net.PeerToPeer.Collaboration>
