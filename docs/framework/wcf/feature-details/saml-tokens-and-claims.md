---
title: SAML トークンとクレーム
description: WFC により、SAML トークンを使用してステートメント (特定のエンティティによって他のエンティティに関して作成されるクレームのセット) がどのように伝達されるかを説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: a1de58ae28041b8e89822120c9369612217eb3b7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288517"
---
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="c1541-103">SAML トークンとクレーム</span><span class="sxs-lookup"><span data-stu-id="c1541-103">SAML Tokens and Claims</span></span>

<span data-ttu-id="c1541-104">SAML (Security Assertion Markup Language) "*トークン*" は、クレームの XML 表現です。</span><span class="sxs-lookup"><span data-stu-id="c1541-104">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="c1541-105">既定では、フェデレーション セキュリティのシナリオで使用される SAML トークン Windows Communication Foundation (WCF) は、"*発行済みトークン*" です。</span><span class="sxs-lookup"><span data-stu-id="c1541-105">By default, SAML tokens Windows Communication Foundation (WCF) uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="c1541-106">SAML トークンは、ステートメント (特定のエンティティによって他のエンティティに関して作成されるクレームのセット) を伝達します。</span><span class="sxs-lookup"><span data-stu-id="c1541-106">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="c1541-107">たとえば、フェデレーション セキュリティ シナリオでは、ステートメントがセキュリティ トークン サービスによって、システム内の特定のユーザーに関して作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1541-107">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="c1541-108">セキュリティ トークン サービスは、トークンに含まれるステートメントの信憑性を示すために SAML トークンに署名します。</span><span class="sxs-lookup"><span data-stu-id="c1541-108">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="c1541-109">また、SAML トークンは、SAML トークンのユーザーが証明として提示する暗号化キー マテリアルに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="c1541-109">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="c1541-110">これが証拠となり、証明書利用者は、SAML トークンが実際にそのユーザーに対して発行されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c1541-110">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="c1541-111">一般的なシナリオでの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c1541-111">For example, in a typical scenario:</span></span>  
  
1. <span data-ttu-id="c1541-112">クライアントは、セキュリティ トークン サービスから SAML トークンを要求し、Windows 資格情報を使用して、そのセキュリティ トークン サービスに対して認証を行います。</span><span class="sxs-lookup"><span data-stu-id="c1541-112">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2. <span data-ttu-id="c1541-113">セキュリティ トークン サービスは、SAML トークンをクライアントに発行します。</span><span class="sxs-lookup"><span data-stu-id="c1541-113">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="c1541-114">SAML トークンは、セキュリティ トークン サービスに関連付けられた証明書を使用して署名され、ターゲット サービス用に暗号化された証明キーを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="c1541-114">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3. <span data-ttu-id="c1541-115">クライアントにより、"*証明キー*" のコピーの受け取りも行われます。</span><span class="sxs-lookup"><span data-stu-id="c1541-115">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="c1541-116">クライアントにより、SAML トークンがアプリケーション サービス ("*証明書利用者*") に提示され、その証明キーを使用したメッセージへの署名が行われます。</span><span class="sxs-lookup"><span data-stu-id="c1541-116">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4. <span data-ttu-id="c1541-117">SAML トークンの署名は、そのトークンがセキュリティ トークン サービスによって発行されたことを証明書利用者に示します。</span><span class="sxs-lookup"><span data-stu-id="c1541-117">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="c1541-118">また、証明キーを使用して作成されたメッセージ署名は、トークンがそのクライアントに対して発行されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c1541-118">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="c1541-119">クレームから SamlAttributes</span><span class="sxs-lookup"><span data-stu-id="c1541-119">From Claims to SamlAttributes</span></span>  

 <span data-ttu-id="c1541-120">WCF では、SAML トークン内のステートメントは <xref:System.IdentityModel.Tokens.SamlAttribute> オブジェクトとしてモデル化されています。<xref:System.IdentityModel.Claims.Claim> オブジェクトが <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> の <xref:System.IdentityModel.Claims.Claim.Right%2A> プロパティを持ち、<xref:System.IdentityModel.Claims.Claim.Resource%2A> プロパティが <xref:System.String> 型である場合、これは <xref:System.IdentityModel.Claims.Claim> オブジェクトから直接設定できます。</span><span class="sxs-lookup"><span data-stu-id="c1541-120">In WCF, statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="c1541-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c1541-121">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> <span data-ttu-id="c1541-122">セキュリティ トークン サービスによって発行されたか、または認証の一部としてクライアントからサービスに提示されたときに、SAML トークンがメッセージ内にシリアル化される場合、メッセージの最大クォータ サイズが、SAML トークンおよびメッセージの他の部分を格納できるだけの大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1541-122">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="c1541-123">通常は、既定のメッセージ クォータ サイズで十分です。</span><span class="sxs-lookup"><span data-stu-id="c1541-123">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="c1541-124">ただし、何百ものクレームを含んでいるために SAML トークンのサイズが大きい場合には、シリアル化されたトークンを格納できるように、クォータを増やす必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="c1541-124">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> <span data-ttu-id="c1541-125">詳しくは、「[データに関するセキュリティ上の考慮事項](security-considerations-for-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1541-125">For more information, see [Security Considerations for Data](security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="c1541-126">SamlAttributes からクレーム</span><span class="sxs-lookup"><span data-stu-id="c1541-126">From SamlAttributes to Claims</span></span>  

 <span data-ttu-id="c1541-127">SAML トークンがメッセージで受信されると、SAML トークン内のさまざまなステートメントは、 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> オブジェクトに変換され、<xref:System.IdentityModel.Policy.AuthorizationContext> に配置されます。</span><span class="sxs-lookup"><span data-stu-id="c1541-127">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="c1541-128">各 SAML ステートメントのクレームは <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> の <xref:System.IdentityModel.Policy.AuthorizationContext> プロパティによって返され、これを調べることによってユーザーの認証と承認を行うかどうかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="c1541-128">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1541-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1541-129">See also</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="c1541-130">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="c1541-130">Federation</span></span>](federation.md)
- [<span data-ttu-id="c1541-131">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="c1541-131">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="c1541-132">方法: フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="c1541-132">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="c1541-133">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="c1541-133">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="c1541-134">クレームとトークン</span><span class="sxs-lookup"><span data-stu-id="c1541-134">Claims and Tokens</span></span>](claims-and-tokens.md)
- [<span data-ttu-id="c1541-135">クレームの作成とリソース値</span><span class="sxs-lookup"><span data-stu-id="c1541-135">Claim Creation and Resource Values</span></span>](claim-creation-and-resource-values.md)
- [<span data-ttu-id="c1541-136">方法: カスタム クレームを作成する</span><span class="sxs-lookup"><span data-stu-id="c1541-136">How to: Create a Custom Claim</span></span>](../extending/how-to-create-a-custom-claim.md)
