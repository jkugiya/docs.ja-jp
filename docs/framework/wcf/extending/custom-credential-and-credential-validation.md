---
description: 詳細については、「カスタム資格情報と資格情報の検証」を参照してください。
title: カスタム資格情報と資格情報の検証
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: f1ceb8cf46cca01ac31faeb9485cbeb6c8663d31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735310"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="4f067-103">カスタム資格情報と資格情報の検証</span><span class="sxs-lookup"><span data-stu-id="4f067-103">Custom Credential and Credential Validation</span></span>

<span data-ttu-id="4f067-104">Windows Communication Foundation (WCF) のセキュリティは、サービスとクライアント間の資格情報の交換に基づいています。</span><span class="sxs-lookup"><span data-stu-id="4f067-104">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="4f067-105">セキュリティ シナリオの多くは、Windows (Kerberos)、ユーザー名とパスワード、証明書などの共通の資格情報の種類を使用して満たされます。</span><span class="sxs-lookup"><span data-stu-id="4f067-105">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="4f067-106">ただし、新しい種類の資格情報が必要な場合があります。このセクションのこのトピックでは、その新しい種類の処理方法と検証方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f067-106">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f067-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4f067-107">In This Section</span></span>  

 [<span data-ttu-id="4f067-108">方法: カスタム証明書検証を使用するサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="4f067-108">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="4f067-109">クラスから継承することによって WCF 検証をカスタマイズする方法について説明 <xref:System.IdentityModel.Selectors.X509CertificateValidator> します。</span><span class="sxs-lookup"><span data-stu-id="4f067-109">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="4f067-110">チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="4f067-110">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="4f067-111"><xref:System.ServiceModel.Description.ClientCredentials> <xref:System.ServiceModel.Description.ServiceCredentials> 新しい資格情報の種類に対応するために、クラスとクラスを拡張する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4f067-111">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="4f067-112">これは、カスタム資格情報の種類の作成を実現するトピック シリーズの 1 番目です。</span><span class="sxs-lookup"><span data-stu-id="4f067-112">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="4f067-113">方法: カスタム セキュリティ トークン プロバイダーを作成する</span><span class="sxs-lookup"><span data-stu-id="4f067-113">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="4f067-114">セキュリティ トークン プロバイダーを作成して新しい資格情報の種類を処理し、その資格情報の新しいトークンを返す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4f067-114">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="4f067-115">これは、シリーズの 2 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="4f067-115">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="4f067-116">方法: カスタム セキュリティ トークン認証システムを作成する</span><span class="sxs-lookup"><span data-stu-id="4f067-116">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="4f067-117">カスタム認証システムを作成して新しい資格情報の種類を認証する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4f067-117">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="4f067-118">これは、シリーズの 3 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="4f067-118">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4f067-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f067-119">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="4f067-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f067-120">Related Sections</span></span>  

 [<span data-ttu-id="4f067-121">認証</span><span class="sxs-lookup"><span data-stu-id="4f067-121">Authentication</span></span>](../feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="4f067-122">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="4f067-122">Federation and Issued Tokens</span></span>](../feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="4f067-123">承認</span><span class="sxs-lookup"><span data-stu-id="4f067-123">Authorization</span></span>](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f067-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f067-124">See also</span></span>

- [<span data-ttu-id="4f067-125">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4f067-125">Security</span></span>](../feature-details/security.md)
