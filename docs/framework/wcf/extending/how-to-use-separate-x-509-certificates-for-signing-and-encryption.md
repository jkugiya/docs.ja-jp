---
description: '詳細については、「方法: 署名と暗号化に個別の x.509 証明書を使用する」を参照してください。'
title: '方法: 署名および暗号化に個別の X.509 証明書を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
ms.openlocfilehash: a1cb72265d9fa2742718b88bd574efe4cc9a4918
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644243"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a><span data-ttu-id="80562-103">方法: 署名および暗号化に個別の X.509 証明書を使用する</span><span class="sxs-lookup"><span data-stu-id="80562-103">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>

<span data-ttu-id="80562-104">このトピックでは、クライアントとサービスの両方で、メッセージの署名と暗号化に異なる証明書を使用するように Windows Communication Foundation (WCF) を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80562-104">This topic shows how to configure Windows Communication Foundation (WCF) to use different certificates for message signing and encryption on both the client and service.</span></span>

<span data-ttu-id="80562-105">個別の証明書を署名と暗号化に使用できるようにするには、カスタムクライアントまたはサービスの資格情報 (またはその両方) を作成する必要があります。これは、WCF では、複数のクライアントまたはサービス証明書を設定するための API を提供しないためです。</span><span class="sxs-lookup"><span data-stu-id="80562-105">To enable separate certificates to be used for signing and encryption, a custom client or service credentials (or both) must be created because WCF does not provide an API to set multiple client or service certificates.</span></span> <span data-ttu-id="80562-106">さらに、複数の証明書の情報を利用し、指定されたキーの使用方法やメッセージの方向について適切なセキュリティ トークン プロバイダーを作成するために、セキュリティ トークン マネージャーを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80562-106">Additionally, a security token manager must be provided to leverage the multiple certificates' information and to create an appropriate security token provider for specified key usage and message direction.</span></span>

<span data-ttu-id="80562-107">使用される主要なクラス、そのクラスの継承元のクラス (上向きの矢印で表示)、および特定のメソッドおよびプロパティの戻り値の型を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="80562-107">The following diagram shows the main classes used, the classes they inherit from (shown by an upward-pointing arrow), and the return types of certain methods and properties.</span></span>

- <span data-ttu-id="80562-108">`MyClientCredentials` は、<xref:System.ServiceModel.Description.ClientCredentials> のカスタム実装です。</span><span class="sxs-lookup"><span data-stu-id="80562-108">`MyClientCredentials` is a custom implementation of <xref:System.ServiceModel.Description.ClientCredentials>.</span></span>

  - <span data-ttu-id="80562-109">図に示されたすべてのプロパティは、すべて <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="80562-109">Its properties shown in the diagram all return instances of <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.</span></span>

  - <span data-ttu-id="80562-110">メソッド <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> は、`MyClientCredentialsSecurityTokenManager` のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="80562-110">Its method <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> returns an instance of `MyClientCredentialsSecurityTokenManager`.</span></span>

- <span data-ttu-id="80562-111">`MyClientCredentialsSecurityTokenManager` は、<xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> のカスタム実装です。</span><span class="sxs-lookup"><span data-stu-id="80562-111">`MyClientCredentialsSecurityTokenManager` is a custom implementation of <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.</span></span>

  - <span data-ttu-id="80562-112">メソッド <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> は、<xref:System.IdentityModel.Selectors.X509SecurityTokenProvider> のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="80562-112">Its method <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> returns an instance of <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.</span></span>

<span data-ttu-id="80562-113">![クライアント資格情報がどのように使用されるのかを示す図](./media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")</span><span class="sxs-lookup"><span data-stu-id="80562-113">![Chart showing how client credentials are used](./media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")</span></span>

<span data-ttu-id="80562-114">カスタム資格情報の詳細については、「 [チュートリアル: カスタムクライアントおよびサービスの資格情報の作成](walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80562-114">For more information about custom credentials, see [Walkthrough: Creating Custom Client and Service Credentials](walkthrough-creating-custom-client-and-service-credentials.md).</span></span>

<span data-ttu-id="80562-115">また、カスタム ID 検証機能を作成し、カスタム バインドのセキュリティ バインド要素にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80562-115">In addition, you must create a custom identity verifier, and link it to a security binding element in a custom binding.</span></span> <span data-ttu-id="80562-116">さらに、既定の資格情報の代わりにカスタム資格情報を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80562-116">You must also use the custom credentials instead of the default credentials.</span></span>

<span data-ttu-id="80562-117">カスタム バインドに関連したクラス、およびカスタム ID 検証機能のリンク方法を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="80562-117">The following diagram shows the classes involved in the custom binding, and how the custom identity verifier is linked.</span></span> <span data-ttu-id="80562-118">関連するバインド要素はいくつかありますが、そのすべてが <xref:System.ServiceModel.Channels.BindingElement> から継承されています。</span><span class="sxs-lookup"><span data-stu-id="80562-118">There are several binding elements involved, all of which inherit from <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="80562-119"><xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> には、<xref:System.ServiceModel.Channels.LocalClientSecuritySettings> プロパティがあります。このプロパティは、<xref:System.ServiceModel.Security.IdentityVerifier> のカスタマイズの元となる `MyIdentityVerifier` のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="80562-119">The <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> has the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> property, which returns an instance of <xref:System.ServiceModel.Security.IdentityVerifier>, from which `MyIdentityVerifier` is customized.</span></span>

<span data-ttu-id="80562-120">![カスタム バインディング要素を示す図](./media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")</span><span class="sxs-lookup"><span data-stu-id="80562-120">![Chart showing a custom binding element](./media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")</span></span>

<span data-ttu-id="80562-121">カスタム id 検証機能の作成の詳細については、「方法: [カスタムクライアント Id 検証](how-to-create-a-custom-client-identity-verifier.md)機能を作成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80562-121">For more information about creating a custom identity verifier, see How to: [How to: Create a Custom Client Identity Verifier](how-to-create-a-custom-client-identity-verifier.md).</span></span>

### <a name="to-use-separate-certificates-for-signing-and-encryption"></a><span data-ttu-id="80562-122">署名と暗号化に別個の証明書を使用するには</span><span class="sxs-lookup"><span data-stu-id="80562-122">To use separate certificates for signing and encryption</span></span>

1. <span data-ttu-id="80562-123"><xref:System.ServiceModel.Description.ClientCredentials> クラスを継承する新しいクライアント資格情報クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="80562-123">Define a new client credentials class that inherits from the <xref:System.ServiceModel.Description.ClientCredentials> class.</span></span> <span data-ttu-id="80562-124">複数の証明書を指定できるようにする、`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate`、および `ServiceEncryptingCertificate` の 4 つの新しいプロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="80562-124">Implement four new properties to allow multiple certificates specification: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, and `ServiceEncryptingCertificate`.</span></span> <span data-ttu-id="80562-125">また、<xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> メソッドをオーバーライドして、次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスのインスタンスを返すように設定します。</span><span class="sxs-lookup"><span data-stu-id="80562-125">Also override the <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> method to return an instance of the customized <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class that is defined in the next step.</span></span>

     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]

2. <span data-ttu-id="80562-126"><xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスを継承する新しいクライアント セキュリティ トークン マネージャーを定義します。</span><span class="sxs-lookup"><span data-stu-id="80562-126">Define a new client security token manager that inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class.</span></span> <span data-ttu-id="80562-127">適切なセキュリティ トークン プロバイダーを作成するために、<xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="80562-127">Override the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> method to create an appropriate security token provider.</span></span> <span data-ttu-id="80562-128">メッセージの方向とキーの使用方法は、`requirement` パラメーター (<xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) で提供されます。</span><span class="sxs-lookup"><span data-stu-id="80562-128">The `requirement` parameter (a <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) provides the message direction and key usage.</span></span>

     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]

3. <span data-ttu-id="80562-129"><xref:System.ServiceModel.Description.ServiceCredentials> クラスを継承する新しいサービス資格情報クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="80562-129">Define a new service credentials class that inherits from the <xref:System.ServiceModel.Description.ServiceCredentials> class.</span></span> <span data-ttu-id="80562-130">複数の証明書を指定できるようにする、`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate`、および `ServiceEncryptingCertificate` の 4 つの新しいプロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="80562-130">Implement four new properties to allow multiple certificates specification: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, and `ServiceEncryptingCertificate`.</span></span> <span data-ttu-id="80562-131">また、<xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> メソッドをオーバーライドして、次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> クラスのインスタンスを返すように設定します。</span><span class="sxs-lookup"><span data-stu-id="80562-131">Also override the <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> method to return an instance of the customized <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class that is defined in the next step.</span></span>

     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]

4. <span data-ttu-id="80562-132"><xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> クラスを継承する新しいサービス セキュリティ トークン マネージャーを定義します。</span><span class="sxs-lookup"><span data-stu-id="80562-132">Define a new service security token manager that inherits from the <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class.</span></span> <span data-ttu-id="80562-133">渡されたメッセージの方向とキーの使用方法について適切なセキュリティ トークン プロバイダーを作成するために、<xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="80562-133">Override the <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> method to create an appropriate security token provider given the passed-in message direction and key usage.</span></span>

     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]

### <a name="to-use-multiple-certificates-on-the-client"></a><span data-ttu-id="80562-134">クライアントで複数の証明書を使用するには</span><span class="sxs-lookup"><span data-stu-id="80562-134">To use multiple certificates on the client</span></span>

1. <span data-ttu-id="80562-135">カスタム バインドの作成</span><span class="sxs-lookup"><span data-stu-id="80562-135">Create a custom binding.</span></span> <span data-ttu-id="80562-136">セキュリティ バインド要素は、要求と応答について異なるセキュリティ トークン プロバイダーが存在することを可能にする二重モードで動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80562-136">The security binding element must operate in duplex mode to allow different security token providers to be present for requests and responses.</span></span> <span data-ttu-id="80562-137">これを行うには、二重モード対応のトランスポートを使用するか、次のコードで示すように <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> を使用します。</span><span class="sxs-lookup"><span data-stu-id="80562-137">One way to do this is to use a duplex-capable transport or to use the <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> as shown in the following code.</span></span> <span data-ttu-id="80562-138">次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.Security.IdentityVerifier> をセキュリティ バインド要素にリンクします。</span><span class="sxs-lookup"><span data-stu-id="80562-138">Link the customized <xref:System.ServiceModel.Security.IdentityVerifier> which is defined in the next step to the security binding element.</span></span> <span data-ttu-id="80562-139">既定のクライアント資格情報を、事前に作成したカスタマイズ済みのクライアント資格情報に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="80562-139">Replace the default client credentials with the customized client credentials previously created.</span></span>

     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]

2. <span data-ttu-id="80562-140">カスタム <xref:System.ServiceModel.Security.IdentityVerifier> を定義します。</span><span class="sxs-lookup"><span data-stu-id="80562-140">Define a custom <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="80562-141">要求の暗号化と応答への署名で異なる証明書が使用されるため、サービスには複数の ID があります。</span><span class="sxs-lookup"><span data-stu-id="80562-141">The service has multiple identities because different certificates are used to encrypt the request and to sign the response.</span></span>

    > [!NOTE]
    > <span data-ttu-id="80562-142">次のサンプルで用意されたカスタム ID 検証方法では、デモンストレーション用であるため、エンドポイント ID 検査がまったく行われません。</span><span class="sxs-lookup"><span data-stu-id="80562-142">In the following sample, the provided custom identity verifier does not perform any endpoint identity checking for demonstration purposes.</span></span> <span data-ttu-id="80562-143">これは製品版のコードでは、お勧めしません。</span><span class="sxs-lookup"><span data-stu-id="80562-143">This is not recommended practice for production code.</span></span>

     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]

### <a name="to-use-multiple-certificates-on-the-service"></a><span data-ttu-id="80562-144">サービスで複数の証明書を使用するには</span><span class="sxs-lookup"><span data-stu-id="80562-144">To use multiple certificates on the service</span></span>

1. <span data-ttu-id="80562-145">カスタム バインドの作成</span><span class="sxs-lookup"><span data-stu-id="80562-145">Create a custom binding.</span></span> <span data-ttu-id="80562-146">セキュリティ バインド要素は、要求と応答について異なるセキュリティ トークン プロバイダーが存在することを可能にする二重モードで動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80562-146">The security binding element must operate in a duplex mode to allow different security token providers to be present for requests and responses.</span></span> <span data-ttu-id="80562-147">クライアントの場合と同様に、二重モード対応のトランスポートを使用するか、次のコードで示すように <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> を使用します。</span><span class="sxs-lookup"><span data-stu-id="80562-147">As with the client, use a duplex-capable transport or use <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> as shown in the following code.</span></span> <span data-ttu-id="80562-148">既定のサービス資格情報を、事前に作成したカスタマイズ済みのサービス資格情報に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="80562-148">Replace the default service credentials with the customized service credentials previously created.</span></span>

     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]

## <a name="see-also"></a><span data-ttu-id="80562-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="80562-149">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="80562-150">チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="80562-150">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)
