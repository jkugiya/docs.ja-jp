---
description: '詳細情報: 改ざん'
title: 改ざん
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 3b14fef66e5c98737d8d2f6a8b889f16c83020f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793325"
---
# <a name="tampering"></a><span data-ttu-id="f7713-103">改ざん</span><span class="sxs-lookup"><span data-stu-id="f7713-103">Tampering</span></span>

<span data-ttu-id="f7713-104">*改ざん* とは、メッセージを変更したり、メッセージの配信を行ったり、変更されたメッセージを目的以外の目的で使用したりする行為です。</span><span class="sxs-lookup"><span data-stu-id="f7713-104">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="f7713-105">WS-Addressing を無効にしない</span><span class="sxs-lookup"><span data-stu-id="f7713-105">Do Not Disable WS-Addressing</span></span>  

 <span data-ttu-id="f7713-106">WS-Addressing の仕様では、各メッセージにアドレス ヘッダーが提供されるため、メッセージの受信者はメッセージの送信者を検証できます。</span><span class="sxs-lookup"><span data-stu-id="f7713-106">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="f7713-107">この機能を無効にするには、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="f7713-107">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="f7713-108">セキュリティ モードが Message に設定された状態で、WS-Addressing が無効になっていると、攻撃者がクライアントから要求を取得して、これを別のサービスに送信した場合、要求を受信したサービスは、このメッセージが元のクライアントから送信されたことを検出できません。</span><span class="sxs-lookup"><span data-stu-id="f7713-108">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="f7713-109">事実上、最初のサービスは、2 番目のサービスと対話するときに、自分をクライアントと偽ることができます。</span><span class="sxs-lookup"><span data-stu-id="f7713-109">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="f7713-110">これを防ぐには、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを絶対に <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定しないようにし、静的 <xref:System.ServiceModel.Channels.MessageVersion> プロパティのように、<xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> プロパティを <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> に設定する <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> の使用を避けます。</span><span class="sxs-lookup"><span data-stu-id="f7713-110">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7713-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7713-111">See also</span></span>

- [<span data-ttu-id="f7713-112">セキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="f7713-112">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="f7713-113">情報漏えい</span><span class="sxs-lookup"><span data-stu-id="f7713-113">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="f7713-114">特権の昇格</span><span class="sxs-lookup"><span data-stu-id="f7713-114">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="f7713-115">サービス拒否</span><span class="sxs-lookup"><span data-stu-id="f7713-115">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="f7713-116">サポートされていないシナリオ</span><span class="sxs-lookup"><span data-stu-id="f7713-116">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="f7713-117">リプレイ攻撃</span><span class="sxs-lookup"><span data-stu-id="f7713-117">Replay Attacks</span></span>](replay-attacks.md)
