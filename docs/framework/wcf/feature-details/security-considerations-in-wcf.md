---
description: 詳細については、「WCF でのセキュリティに関する考慮事項」をご覧ください。
title: WCF でのセキュリティの考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: d75ff0d6eede4a46a5b795873e83445a04532993
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632478"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="aca1f-103">WCF でのセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="aca1f-103">Security Considerations in WCF</span></span>

<span data-ttu-id="aca1f-104">このセクションのトピックでは、Windows Communication Foundation (WCF) アプリケーションを設計する際に考慮する必要があるさまざまなセキュリティ関連の項目を示します。</span><span class="sxs-lookup"><span data-stu-id="aca1f-104">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aca1f-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="aca1f-105">In This Section</span></span>  

 [<span data-ttu-id="aca1f-106">情報漏えい</span><span class="sxs-lookup"><span data-stu-id="aca1f-106">Information Disclosure</span></span>](information-disclosure.md)  
 <span data-ttu-id="aca1f-107">情報が開示または攻撃されるさまざまな方法、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aca1f-107">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="aca1f-108">特権の昇格</span><span class="sxs-lookup"><span data-stu-id="aca1f-108">Elevation of Privilege</span></span>](elevation-of-privilege.md)  
 <span data-ttu-id="aca1f-109">最初に付与されたものよりも高い承認アクセス許可を攻撃者に与えることの影響、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aca1f-109">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="aca1f-110">サービス拒否</span><span class="sxs-lookup"><span data-stu-id="aca1f-110">Denial of Service</span></span>](denial-of-service.md)  
 <span data-ttu-id="aca1f-111">システムがメッセージを適切に処理できない場合の影響、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aca1f-111">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="aca1f-112">改ざん</span><span class="sxs-lookup"><span data-stu-id="aca1f-112">Tampering</span></span>](tampering.md)  
 <span data-ttu-id="aca1f-113">メッセージの改ざんやメッセージの配信先の変更、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aca1f-113">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="aca1f-114">リプレイ攻撃</span><span class="sxs-lookup"><span data-stu-id="aca1f-114">Replay Attacks</span></span>](replay-attacks.md)  
 <span data-ttu-id="aca1f-115">攻撃者がメッセージのストリームを送受信者間でコピーし、そのストリームを 1 つ以上の第三者に対してリプレイすることによる影響、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aca1f-115">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="aca1f-116">セキュリティで保護されたセッションに関するセキュリティの検討</span><span class="sxs-lookup"><span data-stu-id="aca1f-116">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="aca1f-117">セキュリティで保護されたセッションを実装する場合に、セキュリティに影響を及ぼす次の項目について説明します。</span><span class="sxs-lookup"><span data-stu-id="aca1f-117">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="aca1f-118">サポートされていないシナリオ</span><span class="sxs-lookup"><span data-stu-id="aca1f-118">Unsupported Scenarios</span></span>](unsupported-scenarios.md)  
 <span data-ttu-id="aca1f-119">セキュリティの特定の側面がサポートされないため、避けたり配慮したりする必要のあるさまざまなシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="aca1f-119">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aca1f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="aca1f-120">Reference</span></span>  

 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="aca1f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="aca1f-121">Related Sections</span></span>  

 [<span data-ttu-id="aca1f-122">セキュリティ ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="aca1f-122">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="aca1f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="aca1f-123">See also</span></span>

- [<span data-ttu-id="aca1f-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="aca1f-124">Security</span></span>](security.md)
