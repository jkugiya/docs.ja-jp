---
description: '詳細情報: セキュリティで保護されたセッション'
title: セキュリティで保護されたセッション
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 8a4a2d23d5a27f5066bd5f004582829e499f714c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733074"
---
# <a name="secure-sessions"></a><span data-ttu-id="feaa3-103">セキュリティで保護されたセッション</span><span class="sxs-lookup"><span data-stu-id="feaa3-103">Secure Sessions</span></span>

<span data-ttu-id="feaa3-104">Windows Communication Foundation (WCF) の機能は、メッセージが送信された順序で受信されることを保証する信頼できるセッションです。</span><span class="sxs-lookup"><span data-stu-id="feaa3-104">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="feaa3-105">このセクションの各トピックでは、信頼できるセッションを作成する際に考慮する必要のあるセキュリティへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="feaa3-105">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="feaa3-106">信頼できるセッションの詳細については、「 [セッションの使用](../using-sessions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="feaa3-106">For more information about reliable sessions, see [Using Sessions](../using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="feaa3-107">Windows XP で偽装が必要な場合は、ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用しない、セキュリティで保護されたセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="feaa3-107">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="feaa3-108">ステートフル SCT が偽装と共に使用されると、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="feaa3-108">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="feaa3-109">詳細については、「サポートされ [ないシナリオ](unsupported-scenarios.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="feaa3-109">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="feaa3-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="feaa3-110">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="feaa3-111">セキュリティ保護されたメッセージ交換とセッション</span><span class="sxs-lookup"><span data-stu-id="feaa3-111">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)|<span data-ttu-id="feaa3-112">セキュリティで保護されたメッセージ交換とセキュリティで保護されたセッションは、同じ意味で使用されます。</span><span class="sxs-lookup"><span data-stu-id="feaa3-112">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="feaa3-113">ここでは、セキュリティで保護されたメッセージ交換のしくみ、およびこのパターンを使用する状況と理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="feaa3-113">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="feaa3-114">方法: セキュリティで保護されたセッションを作成する</span><span class="sxs-lookup"><span data-stu-id="feaa3-114">How to: Create a Secure Session</span></span>](how-to-create-a-secure-session.md)|<span data-ttu-id="feaa3-115">セキュリティで保護されたセッションの基本的な作成手順を説明するチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="feaa3-115">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="feaa3-116">方法: セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する</span><span class="sxs-lookup"><span data-stu-id="feaa3-116">How to: Create a Security Context Token for a Secure Session</span></span>](how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="feaa3-117">クライアントの状態とセッションを保持する Web ファームを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="feaa3-117">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="feaa3-118">セキュリティで保護されたセッションに関するセキュリティの検討</span><span class="sxs-lookup"><span data-stu-id="feaa3-118">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)|<span data-ttu-id="feaa3-119">セキュリティで保護されたセッションに関する特別な考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="feaa3-119">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="feaa3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="feaa3-120">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="feaa3-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="feaa3-121">Related Sections</span></span>  

 [<span data-ttu-id="feaa3-122">セッション、インスタンス化、およびコンカレンシー</span><span class="sxs-lookup"><span data-stu-id="feaa3-122">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="feaa3-123">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="feaa3-123">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="feaa3-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="feaa3-124">See also</span></span>

- [<span data-ttu-id="feaa3-125">方法: メッセージ リプレイ検出を有効にする</span><span class="sxs-lookup"><span data-stu-id="feaa3-125">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="feaa3-126">リプレイ攻撃</span><span class="sxs-lookup"><span data-stu-id="feaa3-126">Replay Attacks</span></span>](replay-attacks.md)
- [<span data-ttu-id="feaa3-127">方法: セッションを必要とするサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="feaa3-127">How to: Create a Service That Requires Sessions</span></span>](how-to-create-a-service-that-requires-sessions.md)
