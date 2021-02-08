---
description: 詳細については、「カスタムバインドを使用したセキュリティ機能」を参照してください。
title: カスタム バインディングを使用したセキュリティ機能
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 0d4298bcb0b22d607c4abb15d879e3b093394bad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779843"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="d78ec-103">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="d78ec-103">Security Capabilities with Custom Bindings</span></span>

<span data-ttu-id="d78ec-104">一般的なセキュリティ タスクのほとんどは、システム指定のバインディングのいずれかを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="d78ec-104">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="d78ec-105">ただし、より高度な制御が必要な場合は、以下のトピックで説明するように、<xref:System.ServiceModel.Channels.SecurityBindingElement> を使用してカスタム バインドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d78ec-105">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="d78ec-106">カスタムバインディングの詳細については、「 [カスタムバインド](../extending/custom-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d78ec-106">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d78ec-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d78ec-107">In This Section</span></span>  

 [<span data-ttu-id="d78ec-108">SecurityBindingElement 認証モード</span><span class="sxs-lookup"><span data-stu-id="d78ec-108">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="d78ec-109">カスタム バインドで使用できる認証モードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-109">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="d78ec-110">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="d78ec-110">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="d78ec-111">セキュリティ要素を使用してカスタム バインディングを作成するための基本手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-111">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="d78ec-112">方法: 指定した認証モード用の SecurityBindingElement を作成する</span><span class="sxs-lookup"><span data-stu-id="d78ec-112">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="d78ec-113">指定した認証モード用のセキュリティ要素を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-113">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="d78ec-114">方法: WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする</span><span class="sxs-lookup"><span data-stu-id="d78ec-114">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="d78ec-115">フェデレーション サービスを作成する際に、セキュリティで保護されたセッションを無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-115">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="d78ec-116">方法: メッセージ リプレイ検出を有効にする</span><span class="sxs-lookup"><span data-stu-id="d78ec-116">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="d78ec-117">リプレイ攻撃の発生を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-117">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="d78ec-118">方法: サポート資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="d78ec-118">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="d78ec-119">必要な場合に、サービスにサポート資格情報を提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-119">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="d78ec-120">方法: 署名確認を設定する</span><span class="sxs-lookup"><span data-stu-id="d78ec-120">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="d78ec-121">メッセージにデジタル署名する際に署名を確認する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-121">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="d78ec-122">方法: 時刻のずれの最大値を設定する</span><span class="sxs-lookup"><span data-stu-id="d78ec-122">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="d78ec-123">サービスとクライアント間で許容される最大の時刻のずれを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-123">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="d78ec-124">方法: デジタル署名の暗号化を無効にする</span><span class="sxs-lookup"><span data-stu-id="d78ec-124">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="d78ec-125">デジタル署名の暗号化を無効にするとどのようなパフォーマンス上の利点があるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="d78ec-125">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d78ec-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="d78ec-126">Reference</span></span>  

 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="d78ec-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d78ec-127">Related Sections</span></span>  

 [<span data-ttu-id="d78ec-128">保護レベルの理解</span><span class="sxs-lookup"><span data-stu-id="d78ec-128">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="d78ec-129">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d78ec-129">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="d78ec-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="d78ec-130">See also</span></span>

- [<span data-ttu-id="d78ec-131">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="d78ec-131">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="d78ec-132">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="d78ec-132">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="d78ec-133">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="d78ec-133">System-Provided Bindings</span></span>](../system-provided-bindings.md)
