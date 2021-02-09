---
description: '詳細情報: ピア名と PNRP ID'
title: ピア名と PNRP ID
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: ff9f77917ef05754f2373369d623b66e66b5a753
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801866"
---
# <a name="peer-names-and-pnrp-ids"></a><span data-ttu-id="ca72f-103">ピア名と PNRP ID</span><span class="sxs-lookup"><span data-stu-id="ca72f-103">Peer Names and PNRP IDs</span></span>

<span data-ttu-id="ca72f-104">ピア名は通信のエンドポイントを表します。ピア名には、コンピューター、ユーザー、グループ、サービスのほか、ピアに関連付けられていて IPv6 アドレスに変換できるすべてのものを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ca72f-104">A Peer Name represents an endpoint for communication, which can be a computer, a user, a group, a service, or anything associated with a Peer that can be resolved to an IPv6 address.</span></span> <span data-ttu-id="ca72f-105">ピア名解決プロトコル (PNRP) は、クラウド メンバーの識別に使用される PNRP ID を作成するために、統計的に一意なピア名を取得します。</span><span class="sxs-lookup"><span data-stu-id="ca72f-105">The Peer Name Resolution Protocol (PNRP) takes the statistically unique Peer Name for the creation of a PNRP ID, which is used to identify cloud members.</span></span>  
  
## <a name="peer-names"></a><span data-ttu-id="ca72f-106">ピア名</span><span class="sxs-lookup"><span data-stu-id="ca72f-106">Peer Names</span></span>  

 <span data-ttu-id="ca72f-107">ピア名は、セキュリティで保護するか、またはセキュリティで保護せずに登録できます。</span><span class="sxs-lookup"><span data-stu-id="ca72f-107">Peer names can be registered as unsecured or secured.</span></span> <span data-ttu-id="ca72f-108">セキュリティで保護されていない名前は単純なテキスト文字列で、だれでも複製して登録できるため、スプーフィングのターゲットとなる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="ca72f-108">Unsecured names are just text strings that are subject to spoofing, as anyone can register a duplicate unsecured name.</span></span> <span data-ttu-id="ca72f-109">セキュリティで保護されていない名前は、プライベート ネットワークか、セキュリティ保護されたネットワークでの使用が適しています。</span><span class="sxs-lookup"><span data-stu-id="ca72f-109">Unsecured names are best used in private or otherwise protected networks.</span></span> <span data-ttu-id="ca72f-110">セキュリティで保護された名前は、証明書とデジタル署名で保護されています。</span><span class="sxs-lookup"><span data-stu-id="ca72f-110">Secured names are protected with a certificate and a digital signature.</span></span> <span data-ttu-id="ca72f-111">セキュリティで保護された名前は、その元の発行者のみが所有権を証明できます。</span><span class="sxs-lookup"><span data-stu-id="ca72f-111">Only the original publisher will be able to prove ownership of a secured name.</span></span>  
  
 <span data-ttu-id="ca72f-112">クラウドとスコープを組み合わせることによって、PNRP アクティビティに参加するピアに対して合理的な安全性を備えた環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="ca72f-112">The combination of cloud and scope provides a reasonably secure environment for peers that participate in PNRP activity.</span></span> <span data-ttu-id="ca72f-113">ただし、セキュリティで保護されたピア名を使用しても、ネットワーキング アプリケーション全体のセキュリティを確保できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ca72f-113">However, using a secured peer name does not ensure the overall security of the networking application.</span></span> <span data-ttu-id="ca72f-114">アプリケーションのセキュリティは、実装によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ca72f-114">Security of the application is implementation-dependent.</span></span>  
  
 <span data-ttu-id="ca72f-115">セキュリティで保護されたピア名は、所有者によってのみ登録され、公開キー暗号化によって保護されます。</span><span class="sxs-lookup"><span data-stu-id="ca72f-115">Secured peer names are only registered by their owner and are protected with public key cryptography.</span></span> <span data-ttu-id="ca72f-116">セキュリティで保護されたピア名の所有者は、対応する秘密キーを持つピア エンティティであると想定されます。</span><span class="sxs-lookup"><span data-stu-id="ca72f-116">A secured peer name is considered owned by the peer entity having the corresponding private key.</span></span> <span data-ttu-id="ca72f-117">秘密キーを使用して署名された、認定済みピア アドレス (CPA) によって、所有権を証明できます。</span><span class="sxs-lookup"><span data-stu-id="ca72f-117">Ownership can be proved via the certified peer address (CPA), which is signed using the private key.</span></span> <span data-ttu-id="ca72f-118">悪意のあるユーザーは、対応する秘密キーのないピア名の所有権を偽造できません。</span><span class="sxs-lookup"><span data-stu-id="ca72f-118">A malicious user cannot forge ownership of a peer name without the corresponding private key.</span></span>  
  
## <a name="pnrp-ids"></a><span data-ttu-id="ca72f-119">PNRP ID</span><span class="sxs-lookup"><span data-stu-id="ca72f-119">PNRP IDs</span></span>  

 <span data-ttu-id="ca72f-120">![PNRP ID](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span><span class="sxs-lookup"><span data-stu-id="ca72f-120">![PNRP ID](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span></span>  
  
 <span data-ttu-id="ca72f-121">PNRP ID は次の部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="ca72f-121">PNRP IDs are composed of the following:</span></span>  
  
- <span data-ttu-id="ca72f-122">上位 128 ビット (ピアツーピア (P2P) ID として知られる) は、エンドポイントに割り当てられたピア名のハッシュです。</span><span class="sxs-lookup"><span data-stu-id="ca72f-122">The high-order 128 bits, known as the peer-to-peer (P2P) ID, are a hash of a peer name assigned to the endpoint.</span></span> <span data-ttu-id="ca72f-123">ピア名は、*Authority.Classifier* という形式です。</span><span class="sxs-lookup"><span data-stu-id="ca72f-123">The peer name has the following format: *Authority.Classifier*.</span></span> <span data-ttu-id="ca72f-124">セキュリティで保護された名前の場合、*Authority* は、ピア名の公開キーのセキュア ハッシュ アルゴリズム 1 (SHA1) ハッシュ (16 進数の数字で出力される) です。</span><span class="sxs-lookup"><span data-stu-id="ca72f-124">For secured names, *Authority* is the Secure Hash Algorithm 1 (SHA1) hash of the public key of the peer name in hexadecimal characters.</span></span> <span data-ttu-id="ca72f-125">セキュリティで保護されていない名前の場合、*Authority* は "0" です (単一文字)。</span><span class="sxs-lookup"><span data-stu-id="ca72f-125">For unsecured names, the *Authority* is the single character "0".</span></span> <span data-ttu-id="ca72f-126">*Classifier* は、アプリケーションを識別する文字列です。</span><span class="sxs-lookup"><span data-stu-id="ca72f-126">*Classifier* is a string that identifies the application.</span></span> <span data-ttu-id="ca72f-127">ピア名の分類子は、`null` ターミネータを含めて 149 文字より長くすることができます。</span><span class="sxs-lookup"><span data-stu-id="ca72f-127">No peer name classifier can be greater than 149 characters long, including the `null` terminator.</span></span>  
  
- <span data-ttu-id="ca72f-128">下位 128 ビットは、サービスの場所に割り当てられています。同じクラウド内の同じ P2P ID を持つ異なるインスタンスを識別するために生成された数字です。</span><span class="sxs-lookup"><span data-stu-id="ca72f-128">The low-order 128 bits are used for the Service Location, which is a generated number that identifies different instances of the same P2P ID in the same cloud.</span></span>  
  
 <span data-ttu-id="ca72f-129">P2P ID とサービスの場所の組み合わせを使用すると、1 台のコンピューターから複数の PNRP ID を登録できます。</span><span class="sxs-lookup"><span data-stu-id="ca72f-129">This combination of P2P ID and Service Location allows multiple PNRP IDs to be registered from a single computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca72f-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca72f-130">See also</span></span>

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
