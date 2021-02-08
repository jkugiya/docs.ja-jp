---
description: 詳細については、「フェデレーションと発行済みトークン」を参照してください。
title: フェデレーションと発行済みトークン
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: 209a3f158e2ffc00c3fd09053374340c430cc823
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780246"
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="a1c80-103">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="a1c80-103">Federation and Issued Tokens</span></span>

<span data-ttu-id="a1c80-104">Windows Communication Foundation (WCF) を使用すると、WS-Federation と WS-Trust の仕様を実装するサービスと安全に通信するクライアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a1c80-104">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="a1c80-105">これらの仕様では、異なる信頼領域間での認証と承認を可能にする機構を提供するために、XML、SOAP、および Web サービス記述言語 (WSDL: Web Services Description Language) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1c80-105">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1c80-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a1c80-106">In This Section</span></span>  

 [<span data-ttu-id="a1c80-107">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="a1c80-107">Federation</span></span>](federation.md)  
 <span data-ttu-id="a1c80-108">フェデレーションの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-108">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="a1c80-109">フェデレーションと信頼</span><span class="sxs-lookup"><span data-stu-id="a1c80-109">Federation and Trust</span></span>](federation-and-trust.md)  
 <span data-ttu-id="a1c80-110">フェデレーション サービスまたはクライアントを作成するときに注意する必要がある設計上の問題を示します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-110">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="a1c80-111">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="a1c80-111">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)  
 <span data-ttu-id="a1c80-112">WCF を使用したフェデレーションクライアントの作成の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-112">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="a1c80-113">方法: フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="a1c80-113">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="a1c80-114">フェデレーション サービスを作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-114">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="a1c80-115">方法: WSFederationHttpBinding を作成する</span><span class="sxs-lookup"><span data-stu-id="a1c80-115">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="a1c80-116">`WSFederationHttpBinding` を使用するクライアントおよびサービスを構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-116">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="a1c80-117">方法: セキュリティ トークン サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="a1c80-117">How to: Create a Security Token Service</span></span>](how-to-create-a-security-token-service.md)  
 <span data-ttu-id="a1c80-118">セキュリティ トークン サービスを作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-118">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="a1c80-119">SAML (Security Assertions Markup Language) トークンとクレーム</span><span class="sxs-lookup"><span data-stu-id="a1c80-119">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](saml-tokens-and-claims.md)  
 <span data-ttu-id="a1c80-120">多様なクレームの種類を作成できる拡張可能な SAML (Security Assertions Markup Language) トークンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-120">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="a1c80-121">方法: ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="a1c80-121">How to: Configure a Local Issuer</span></span>](how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="a1c80-122">セキュリティ トークンのローカル発行者の作成方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-122">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="a1c80-123">方法: WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする</span><span class="sxs-lookup"><span data-stu-id="a1c80-123">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="a1c80-124">`WSFederationHttpBinding` のセキュリティで保護されたセッションを無効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1c80-124">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="a1c80-125">クライアントごとにセッションが必要になる Web ファームを作成する場合には、セキュリティで保護されたセッションを無効化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1c80-125">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a1c80-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1c80-126">Reference</span></span>  

 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="a1c80-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1c80-127">See also</span></span>

- [<span data-ttu-id="a1c80-128">承認</span><span class="sxs-lookup"><span data-stu-id="a1c80-128">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="a1c80-129">カスタム トークン</span><span class="sxs-lookup"><span data-stu-id="a1c80-129">Custom Tokens</span></span>](../extending/custom-tokens.md)
- <span data-ttu-id="a1c80-130">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a1c80-130">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
