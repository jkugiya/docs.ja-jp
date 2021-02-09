---
description: '詳細情報: ピアツーピア コラボレーション'
title: ピアツーピア コラボレーション
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 824ab3152c1ad765c2d19f5c6e719242255f606d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738281"
---
# <a name="peer-to-peer-collaboration"></a><span data-ttu-id="d4271-103">ピアツーピア コラボレーション</span><span class="sxs-lookup"><span data-stu-id="d4271-103">Peer-to-peer collaboration</span></span>

<span data-ttu-id="d4271-104">ピアツーピア ネットワーキングは、インターネットのエッジに存在する比較的処理能力の高いコンピューター (パーソナル コンピューター) を、単なるクライアントベースのコンピューティング以上のタスクに利用する方法です。</span><span class="sxs-lookup"><span data-stu-id="d4271-104">Peer-to-peer networking is the utilization of the relatively powerful computers (personal computers) that exist at the edge of the Internet for more than just client-based computing tasks.</span></span> <span data-ttu-id="d4271-105">最新のパーソナル コンピューター (PC) は、非常に高速なプロセッサに大容量のメモリとハード ディスクを備えています。しかし、メールや Web 閲覧などの一般的なコンピューティング タスクを実行するとき、それらはいずれも最大活用されていません。</span><span class="sxs-lookup"><span data-stu-id="d4271-105">The modern personal computer (PC) has a very fast processor, vast memory, and a large hard disk, none of which are being fully utilized when performing common computing tasks such as email and Web browsing.</span></span> <span data-ttu-id="d4271-106">最新の PC は、さまざまな種類のアプリケーションでクライアントとサーバーの両方 (ピア) として簡単に機能できます。</span><span class="sxs-lookup"><span data-stu-id="d4271-106">The modern PC can easily act as both a client and server (a peer) for many types of applications.</span></span>  
  
<span data-ttu-id="d4271-107">ピアツーピア コラボレーションのインフラストラクチャは、Windows Vista 以降のプラットフォームの "近くの人と接続" サービスを利用する Microsoft Windows ピアツーピア インフラストラクチャを簡略化した実装です。</span><span class="sxs-lookup"><span data-stu-id="d4271-107">The Peer-to-Peer Collaboration Infrastructure is a simplified implementation of the Microsoft Windows Peer-to-Peer Infrastructure that leverages the People Near Me service in Windows Vista and later platforms.</span></span> <span data-ttu-id="d4271-108">"近くの人と接続" サービスが機能するサブネット内のピア対応アプリケーションでの使用に適していますが、インターネットのエンドポイントや連絡先も処理できます。</span><span class="sxs-lookup"><span data-stu-id="d4271-108">It is best used for peer-enabled applications within a subnet for which the People Near Me service operates, although it can service internet endpoints or contacts as well.</span></span> <span data-ttu-id="d4271-109">一般的な連絡先マネージャーが組み込まれており、それを Live Messenger やその他の Live 対応アプリケーションで使用して、連絡先エンドポイント、空き時間、プレゼンスを確認できます。</span><span class="sxs-lookup"><span data-stu-id="d4271-109">It incorporates the common Contact Manager that is used by Live Messenger and other Live-aware applications to determine contact endpoints, availability, and presence.</span></span>  
  
## <a name="collaboration-applications"></a><span data-ttu-id="d4271-110">コラボレーション アプリケーション</span><span class="sxs-lookup"><span data-stu-id="d4271-110">Collaboration applications</span></span>

 <span data-ttu-id="d4271-111">一般的なピアツーピア コラボレーション アプリケーションで実行されるステップは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d4271-111">A typical peer-to-peer collaboration application is comprised of the following steps:</span></span>  
  
- <span data-ttu-id="d4271-112">ピアが、コラボレーション セッションをホストすることに関心があるピアの ID を確認します。</span><span class="sxs-lookup"><span data-stu-id="d4271-112">Peer determines the identity of a peer who is interested in hosting a collaboration session</span></span>  
  
- <span data-ttu-id="d4271-113">セッションをホストする要求が送信され、ホスト ピアが、コラボレーション活動を管理することに同意します。</span><span class="sxs-lookup"><span data-stu-id="d4271-113">A request to host a session is sent, somehow, and the host peer agrees to manage collaboration activity.</span></span>  
  
- <span data-ttu-id="d4271-114">ホストがサブネット上の連絡先 (要求元を含む) をセッションに招待します。</span><span class="sxs-lookup"><span data-stu-id="d4271-114">The host invites contacts on the subnet (including the requestor) to a session.</span></span>  
  
- <span data-ttu-id="d4271-115">コラボレーションを希望するすべてのピアが、ホストを連絡先マネージャーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="d4271-115">All peers who want to collaborate may add the host to their contact managers.</span></span>  
  
- <span data-ttu-id="d4271-116">ほとんどのピアが、適切なタイミングで招待への応答 (承諾または拒否) をホスト ピアに送信します。</span><span class="sxs-lookup"><span data-stu-id="d4271-116">Most peers will send invitation responses, whether accepted or declined, back to the host peer in a timely fashion.</span></span>  
  
- <span data-ttu-id="d4271-117">コラボレーションを希望するすべてのピアが、ホスト ピアにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="d4271-117">All peers who want to collaborate will subscribe to the host peer.</span></span>  
  
- <span data-ttu-id="d4271-118">ピアが初期コラボレーション活動を実行している間、ホスト ピアはリモート ピアを連絡先マネージャーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="d4271-118">While the peers are performing their initial collaboration activity, the host peer may add remote peers to its contact manager.</span></span> <span data-ttu-id="d4271-119">また、招待へのすべての応答を処理して、どのピアが承諾または拒否したか、どのピアが未応答かを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4271-119">It also processes all invitation responses to determine who has accepted, who has declined, and who has not answered.</span></span>  <span data-ttu-id="d4271-120">未応答のピアへの招待を取り消したり、他の活動を実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="d4271-120">It may cancel invitations to those who have not answered, or perform some other activity.</span></span>  
  
- <span data-ttu-id="d4271-121">この時点で、ホスト ピアは招待したすべてのピアとのコラボレーション セッションを開始できます。または、コラボレーション インフラストラクチャにアプリケーションを登録できます。</span><span class="sxs-lookup"><span data-stu-id="d4271-121">At this point, the host peer can start a collaboration session with all invited peers, or register an application with the collaboration infrastructure.</span></span>  <span data-ttu-id="d4271-122">P2P アプリケーションは、ピアツーピア コラボレーション インフラストラクチャと <xref:System.Net.PeerToPeer.Collaboration> 名前空間を使用して、ゲーム、掲示板、会議、およびその他のサーバーなしのプレゼンス アプリケーションの通信を調整します。</span><span class="sxs-lookup"><span data-stu-id="d4271-122">P2P applications use the Peer-to-Peer Collaboration Infrastructure and the <xref:System.Net.PeerToPeer.Collaboration> namespace to coordinate communications for games, bulletin boards, conferencing, and other serverless presence applications.</span></span>  
  
## <a name="peer-to-peer-networking-security"></a><span data-ttu-id="d4271-123">ピアツーピア ネットワーキングのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="d4271-123">Peer-to-peer networking security</span></span>  

 <span data-ttu-id="d4271-124">Active Directory ドメインでは、ドメイン コントローラーが Kerberos を使用した認証サービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d4271-124">In an Active Directory domain, domain controllers provide authentication services using Kerberos.</span></span> <span data-ttu-id="d4271-125">サーバーなしのピア環境では、ピアは独自の認証を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4271-125">In a serverless peer environment, the peers must provide their own authentication.</span></span> <span data-ttu-id="d4271-126">ピアツーピア ネットワーキングでは、どのノードも CA として活動できるため、各ピアの信頼されたルート ストアにルート証明書は不要です。</span><span class="sxs-lookup"><span data-stu-id="d4271-126">For Peer-to-Peer Networking, any node can act as a CA, removing the requirement of a root certificate in each peer's trusted root store.</span></span> <span data-ttu-id="d4271-127">認証は、X.509 証明書として書式設定された自己署名証明書を使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="d4271-127">Authentication is provided using self-signed certificates, formatted as X.509 certificates.</span></span> <span data-ttu-id="d4271-128">これらの証明書は各ピアによって作成されます。各ピアは、公開キーおよび秘密キーのペアと、秘密キーを使用して署名された証明書を生成します。</span><span class="sxs-lookup"><span data-stu-id="d4271-128">These are certificates that are created by each peer, which generates the public key/private key pair and the certificate that is signed using the private key.</span></span> <span data-ttu-id="d4271-129">自己署名証明書は、認証のために、また、ピア エンティティについての情報を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d4271-129">The self-signed certificate is used for authentication and to provide information about the peer entity.</span></span> <span data-ttu-id="d4271-130">X.509 認証と同様に、ピア ネットワーキング認証は、信頼された公開キーまでさかのぼることができる証明書チェーンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="d4271-130">Like X.509 authentication, peer networking authentication relies upon a chain of certificates tracing back to a public key that is trusted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4271-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4271-131">See also</span></span>

- <xref:System.Net.PeerToPeer.Collaboration>
- [<span data-ttu-id="d4271-132">System.Net.PeerToPeer.Collaboration 名前空間について</span><span class="sxs-lookup"><span data-stu-id="d4271-132">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>](about-the-system-net-peertopeer-collaboration-namespace.md)
