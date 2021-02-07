---
description: '詳細については、「方法: カスタムセキュリティトークンプロバイダーを作成する」を参照してください。'
title: '方法: カスタム セキュリティ トークン プロバイダーを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 4e0970ff01be74d0eb9f4ae8968bd100a0dafe00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735037"
---
# <a name="how-to-create-a-custom-security-token-provider"></a><span data-ttu-id="c82a7-103">方法: カスタム セキュリティ トークン プロバイダーを作成する</span><span class="sxs-lookup"><span data-stu-id="c82a7-103">How to: Create a Custom Security Token Provider</span></span>

<span data-ttu-id="c82a7-104">ここでは、カスタム セキュリティ トークン プロバイダーを持つ新しいトークンの種類を作成する方法と、そのプロバイダーをカスタム セキュリティ トークン マネージャーと統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-104">This topic shows how to create new token types with a custom security token provider and how to integrate the provider with a custom security token manager.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c82a7-105"><xref:System.IdentityModel.Tokens> 名前空間にあるシステム指定のトークンがユーザーの要件に一致しない場合、カスタム トークン プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-105">Create a custom token provider if the system-provided tokens found in the <xref:System.IdentityModel.Tokens> namespace do not match your requirements.</span></span>  
  
 <span data-ttu-id="c82a7-106">セキュリティ トークン プロバイダーは、クライアントまたはサービスの資格情報に基づいてセキュリティ トークンの表現を作成します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-106">The security token provider creates a security token representation based on information in the client or service credentials.</span></span> <span data-ttu-id="c82a7-107">Windows Communication Foundation (WCF) セキュリティでカスタムセキュリティトークンプロバイダーを使用するには、カスタム資格情報とセキュリティトークンマネージャーの実装を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c82a7-107">To use the custom security token provider in Windows Communication Foundation (WCF) security, you must create custom credentials and security token manager implementations.</span></span>  
  
 <span data-ttu-id="c82a7-108">カスタム資格情報とセキュリティトークンマネージャーの詳細については、「 [チュートリアル: カスタムクライアントおよびサービスの資格情報の作成](walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c82a7-108">For more information about custom credentials and security token manager see the [Walkthrough: Creating Custom Client and Service Credentials](walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
### <a name="to-create-a-custom-security-token-provider"></a><span data-ttu-id="c82a7-109">カスタム セキュリティ トークン プロバイダーを作成するには</span><span class="sxs-lookup"><span data-stu-id="c82a7-109">To create a custom security token provider</span></span>  
  
1. <span data-ttu-id="c82a7-110"><xref:System.IdentityModel.Selectors.SecurityTokenProvider> クラスから派生する新しいクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-110">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class.</span></span>  
  
2. <span data-ttu-id="c82a7-111"><xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-111">Implement the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="c82a7-112">このメソッドは、セキュリティ トークンのインスタンスを作成して返す役割を担います。</span><span class="sxs-lookup"><span data-stu-id="c82a7-112">The method is responsible for creating and returning an instance of the security token.</span></span> <span data-ttu-id="c82a7-113">`MySecurityTokenProvider` という名前のクラスを作成し、<xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> メソッドをオーバーライドして <xref:System.IdentityModel.Tokens.X509SecurityToken> クラスのインスタンスを返す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-113">The following example creates a class named `MySecurityTokenProvider`, and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method to return an instance of the <xref:System.IdentityModel.Tokens.X509SecurityToken> class.</span></span> <span data-ttu-id="c82a7-114">クラス コンストラクターには <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> クラスのインスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="c82a7-114">The class constructor requires an instance of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> class.</span></span>  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a><span data-ttu-id="c82a7-115">カスタム セキュリティ トークン マネージャーにカスタム セキュリティ トークン プロバイダーを統合するには</span><span class="sxs-lookup"><span data-stu-id="c82a7-115">To integrate a custom security token provider with a custom security token manager</span></span>  
  
1. <span data-ttu-id="c82a7-116"><xref:System.IdentityModel.Selectors.SecurityTokenManager> クラスから派生する新しいクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-116">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.</span></span> <span data-ttu-id="c82a7-117">以下の例は、<xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスから派生した <xref:System.IdentityModel.Selectors.SecurityTokenManager> クラスから派生したクラスです。</span><span class="sxs-lookup"><span data-stu-id="c82a7-117">(The example below derives from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class, which derives from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.)</span></span>  
  
2. <span data-ttu-id="c82a7-118">まだオーバーライドされていない場合は、<xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="c82a7-118">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method if is not already overridden.</span></span>  
  
     <span data-ttu-id="c82a7-119">メソッドは、 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> <xref:System.IdentityModel.Selectors.SecurityTokenProvider> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> WCF セキュリティフレームワークによってメソッドに渡されたパラメーターに適したクラスのインスタンスを返す役割を担います。</span><span class="sxs-lookup"><span data-stu-id="c82a7-119">The <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method is responsible for returning an instance of the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class appropriate to the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter passed to the method by the WCF security framework.</span></span> <span data-ttu-id="c82a7-120">メソッドが適切なセキュリティ トークン パラメーターで呼び出された場合に、カスタム セキュリティ トークン プロバイダーの実装 (以前の手順で作成済み) を返すようにメソッドを変更します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-120">Modify the method to return the custom security token provider implementation (created in the previous procedure) when the method is called with an appropriate security token parameter.</span></span> <span data-ttu-id="c82a7-121">セキュリティトークンマネージャーの詳細については、「 [チュートリアル: カスタムクライアントおよびサービスの資格情報の作成](walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c82a7-121">For more information about the security token manager, see the [Walkthrough: Creating Custom Client and Service Credentials](walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
3. <span data-ttu-id="c82a7-122"><xref:System.IdentityModel.Selectors.SecurityTokenRequirement> パラメーターに基づいてカスタム セキュリティ トークン プロバイダーを返すカスタム ロジックをメソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-122">Add custom logic to the method to enable it to return your custom security token provider based on the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter.</span></span> <span data-ttu-id="c82a7-123">トークンの要件が満たされた場合に、カスタム セキュリティ トークン プロバイダーを返す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-123">The following sample returns the custom security token provider if the token requirements are met.</span></span> <span data-ttu-id="c82a7-124">要件には、X.509 セキュリティ トークンとメッセージの方向 (メッセージ出力にトークンが使用される) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c82a7-124">The requirements include an X.509 security token and the message direction (that the token is used for message output).</span></span> <span data-ttu-id="c82a7-125">他のすべての場合で、コードは基本クラスを呼び出し、他のセキュリティ トークンの要件に合わせてシステム指定の動作を維持します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-125">For all other cases, the code calls the base class to maintain the system-provided behavior for other security token requirements.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="c82a7-126">例</span><span class="sxs-lookup"><span data-stu-id="c82a7-126">Example</span></span>  

 <span data-ttu-id="c82a7-127">完全な <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 実装と対応する <xref:System.IdentityModel.Selectors.SecurityTokenManager> 実装を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c82a7-127">The following shows a complete <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation along with a corresponding <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementation.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="c82a7-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c82a7-128">See also</span></span>

- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.X509SecurityToken>
- [<span data-ttu-id="c82a7-129">チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="c82a7-129">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)
- [<span data-ttu-id="c82a7-130">方法: カスタム セキュリティ トークン認証システムを作成する</span><span class="sxs-lookup"><span data-stu-id="c82a7-130">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)
