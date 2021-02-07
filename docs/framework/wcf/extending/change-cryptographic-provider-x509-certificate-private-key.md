---
description: '詳細については、「方法: x.509 証明書の秘密キーの暗号化サービスプロバイダーを変更する」を参照してください。'
title: '方法: X.509 証明書の秘密キーの暗号化プロバイダーを変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: e68f4ffb5626a2c332853bd97eb513516401a185
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756709"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificates-private-key"></a><span data-ttu-id="b2f24-103">方法: X.509 証明書の秘密キーの暗号化プロバイダーを変更する</span><span class="sxs-lookup"><span data-stu-id="b2f24-103">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>

<span data-ttu-id="b2f24-104">このトピックでは、x.509 証明書の秘密キーを提供するために使用する暗号化サービスプロバイダーを変更する方法と、プロバイダーを Windows Communication Foundation (WCF) セキュリティフレームワークに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-104">This topic shows how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) security framework.</span></span> <span data-ttu-id="b2f24-105">証明書の使用方法の詳細については、「 [証明書の](../feature-details/working-with-certificates.md)使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2f24-105">For more information about using certificates, see [Working with Certificates](../feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="b2f24-106">WCF セキュリティフレームワークには、「 [方法: カスタムトークンを作成](how-to-create-a-custom-token.md)する」の説明に従って、新しいセキュリティトークンの種類を導入する方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b2f24-106">The WCF security framework provides a way to introduce new security token types as described in [How to: Create a Custom Token](how-to-create-a-custom-token.md).</span></span> <span data-ttu-id="b2f24-107">また、カスタム トークンを使用して既存のシステム指定のトークンを置き換えることも可能です。</span><span class="sxs-lookup"><span data-stu-id="b2f24-107">It is also possible to use a custom token to replace existing system-provided token types.</span></span>  
  
 <span data-ttu-id="b2f24-108">このトピックでは、システム指定の X.509 セキュリティ トークンが、証明書の秘密キーに別の実装を提供するカスタムの X.509 トークンによって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="b2f24-108">In this topic, the system-provided X.509 security token is replaced by a custom X.509 token that provides a different implementation for the certificate private key.</span></span> <span data-ttu-id="b2f24-109">これは、実際の秘密キーが、既定の Windows 暗号化プロバイダーとは異なる暗号化プロバイダーから提供されるシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b2f24-109">This is useful in scenarios where the actual private key is provided by a different cryptographic provider than the default Windows cryptographic provider.</span></span> <span data-ttu-id="b2f24-110">別の暗号化プロバイダーの例として、ハードウェア セキュリティ モジュールがあります。このモジュールでは、すべての秘密キー関連の暗号操作を実行し、メモリに秘密キーを格納しないので、システムのセキュリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-110">One example of an alternative cryptographic provider is a hardware security module that performs all private key related cryptographic operations, and does not store the private keys in memory, thus improving security of the system.</span></span>  
  
 <span data-ttu-id="b2f24-111">次の例は、デモンストレーションのためだけに作成されています。</span><span class="sxs-lookup"><span data-stu-id="b2f24-111">The following example is for demonstration purposes only.</span></span> <span data-ttu-id="b2f24-112">この例では、既定の Windows 暗号化プロバイダーを置き換えていませんが、Windows 暗号化プロバイダーをどこで統合できるかを示します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-112">It does not replace the default Windows cryptographic provider, but it shows where such a provider could be integrated.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="b2f24-113">手順</span><span class="sxs-lookup"><span data-stu-id="b2f24-113">Procedures</span></span>  

 <span data-ttu-id="b2f24-114">セキュリティ キーが関連付けられているセキュリティ トークンごとに、セキュリティ トークンのインスタンスからキーのコレクションを返す <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> プロパティを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2f24-114">Every security token that has an associated security key or keys must implement the <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> property, which returns a collection of keys from the security token instance.</span></span> <span data-ttu-id="b2f24-115">トークンが X.509 セキュリティ トークンの場合、コレクションには、証明書に関連付けられた公開キーと秘密キーの両方を表す <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> クラスのインスタンスが 1 つ追加されます。</span><span class="sxs-lookup"><span data-stu-id="b2f24-115">If the token is an X.509 security token, the collection contains a single instance of the <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> class that represents both public and private keys associated with the certificate.</span></span> <span data-ttu-id="b2f24-116">証明書のキーの提供に使用する既定の暗号化プロバイダーを置き換えるには、このクラスの新しい実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-116">To replace the default cryptographic provider used to provide the certificate's keys, create a new implementation of this class.</span></span>  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a><span data-ttu-id="b2f24-117">カスタムの X.509 非対称キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b2f24-117">To create a custom X.509 asymmetric key</span></span>  
  
1. <span data-ttu-id="b2f24-118"><xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> クラスから派生する新しいクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-118">Define a new class derived from the <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> class.</span></span>  
  
2. <span data-ttu-id="b2f24-119"><xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> 読み取り専用プロパティをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b2f24-119">Override the <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> read-only property.</span></span> <span data-ttu-id="b2f24-120">このプロパティは、証明書の公開キーと秘密キーのペアの実際のキー サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-120">This property returns the actual key size of the certificate's public/private key pair.</span></span>  
  
3. <span data-ttu-id="b2f24-121"><xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b2f24-121">Override the <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> method.</span></span> <span data-ttu-id="b2f24-122">このメソッドは、証明書の秘密キーを使用して対称キーを復号化するために、WCF セキュリティフレームワークによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b2f24-122">This method is called by the WCF security framework to decrypt a symmetric key with the certificate's private key.</span></span> <span data-ttu-id="b2f24-123">(このキーは、以前に証明書の公開キーで暗号化されています)。</span><span class="sxs-lookup"><span data-stu-id="b2f24-123">(The key was previously encrypted with the certificate's public key.)</span></span>  
  
4. <span data-ttu-id="b2f24-124"><xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b2f24-124">Override the <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> method.</span></span> <span data-ttu-id="b2f24-125">このメソッドは、 <xref:System.Security.Cryptography.AsymmetricAlgorithm> メソッドに渡されたパラメーターに応じて、証明書の秘密キーまたは公開キーの暗号化サービスプロバイダーを表すクラスのインスタンスを取得するために、WCF セキュリティフレームワークによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b2f24-125">This method is called by the WCF security framework to obtain an instance of the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class that represents the cryptographic provider for either the certificate's private or public key, depending on the parameters passed to the method.</span></span>  
  
5. <span data-ttu-id="b2f24-126">任意。</span><span class="sxs-lookup"><span data-stu-id="b2f24-126">Optional.</span></span> <span data-ttu-id="b2f24-127"><xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b2f24-127">Override the <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> method.</span></span> <span data-ttu-id="b2f24-128"><xref:System.Security.Cryptography.HashAlgorithm> クラスの別の実装が必要な場合は、このメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b2f24-128">Override this method if a different implementation of the <xref:System.Security.Cryptography.HashAlgorithm> class is required.</span></span>  
  
6. <span data-ttu-id="b2f24-129"><xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b2f24-129">Override the <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> method.</span></span> <span data-ttu-id="b2f24-130">このメソッドは、証明書の秘密キーに関連付けられた <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> クラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-130">This method returns an instance of the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> class that is associated with the certificate's private key.</span></span>  
  
7. <span data-ttu-id="b2f24-131"><xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b2f24-131">Override the <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> method.</span></span> <span data-ttu-id="b2f24-132">このメソッドを使用して、特定の暗号アルゴリズムがセキュリティ キー実装によってサポートされているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-132">This method is used to indicate whether a particular cryptographic algorithm is supported by the security key implementation.</span></span>  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 <span data-ttu-id="b2f24-133">次の手順では、システムによって提供される x.509 セキュリティトークンを置き換えるために、前の手順で作成したカスタムの x.509 非対称セキュリティキーの実装を WCF セキュリティフレームワークに統合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-133">The following procedure shows how to integrate the custom X.509 asymmetric security key implementation created in the preceding procedure with the WCF security framework in order to replace the system-provided X.509 security token.</span></span>  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a><span data-ttu-id="b2f24-134">システム指定の X.509 セキュリティ トークンをカスタムの X.509 非対称セキュリティ キー トークンで置き換えるには</span><span class="sxs-lookup"><span data-stu-id="b2f24-134">To replace the system-provided X.509 security token with a custom X.509 asymmetric security key token</span></span>  
  
1. <span data-ttu-id="b2f24-135">次の例に示すように、システム指定のセキュリティ キーではなく、カスタムの X.509 非対称セキュリティ キーを返すカスタムの X.509 非対称セキュリティ トークンを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-135">Create a custom X.509 security token that returns the custom X.509 asymmetric security key instead of the system-provided security key, as shown in the following example.</span></span> <span data-ttu-id="b2f24-136">カスタムセキュリティトークンの詳細については、「 [方法: カスタムトークンを作成](how-to-create-a-custom-token.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2f24-136">For more information about custom security tokens, see [How to: Create a Custom Token](how-to-create-a-custom-token.md).</span></span>  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2. <span data-ttu-id="b2f24-137">次の例に示すように、カスタムの X.509 セキュリティ トークンを返すカスタムのセキュリティ トークン プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-137">Create a custom security token provider that returns a custom X.509 security token, as shown in the example.</span></span> <span data-ttu-id="b2f24-138">カスタムセキュリティトークンプロバイダーの詳細については、「 [方法: カスタムセキュリティトークンプロバイダーを作成](how-to-create-a-custom-security-token-provider.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2f24-138">For more information about custom security token providers, see [How to: Create a Custom Security Token Provider](how-to-create-a-custom-security-token-provider.md).</span></span>  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3. <span data-ttu-id="b2f24-139">イニシエーター側でカスタム セキュリティ キーを使用する必要がある場合、次の例に示すように、カスタムのクライアント セキュリティ トークン マネージャーとカスタムのクライアント資格情報クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-139">If the custom security key needs to be used on the initiator side, create a custom client security token manager and custom client credentials classes, as shown in the following example.</span></span> <span data-ttu-id="b2f24-140">カスタムのクライアント資格情報とクライアントセキュリティトークンマネージャーの詳細については、「 [チュートリアル: カスタムクライアントおよびサービスの資格情報の作成](walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2f24-140">For more information about custom client credentials and client security token managers, see [Walkthrough: Creating Custom Client and Service Credentials](walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4. <span data-ttu-id="b2f24-141">受信側でカスタム セキュリティ キーを使用する必要がある場合、次の例に示すように、カスタムのサービス セキュリティ トークン マネージャーとカスタムのサービス資格情報クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2f24-141">If the custom security key needs to be used on the recipient side, create a custom service security token manager and custom service credentials, as shown in the following example.</span></span> <span data-ttu-id="b2f24-142">カスタムサービス資格情報とサービスセキュリティトークンマネージャーの詳細については、「 [チュートリアル: カスタムクライアントおよびサービスの資格情報の作成](walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2f24-142">For more information about custom service credentials and service security token managers, see [Walkthrough: Creating Custom Client and Service Credentials](walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b2f24-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2f24-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.Security.Cryptography.AsymmetricAlgorithm>
- <xref:System.Security.Cryptography.HashAlgorithm>
- <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>
- [<span data-ttu-id="b2f24-144">チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="b2f24-144">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)
- [<span data-ttu-id="b2f24-145">方法: カスタム セキュリティ トークン認証システムを作成する</span><span class="sxs-lookup"><span data-stu-id="b2f24-145">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)
- [<span data-ttu-id="b2f24-146">方法: カスタム セキュリティ トークン プロバイダーを作成する</span><span class="sxs-lookup"><span data-stu-id="b2f24-146">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)
- [<span data-ttu-id="b2f24-147">方法: カスタム トークンを作成する</span><span class="sxs-lookup"><span data-stu-id="b2f24-147">How to: Create a Custom Token</span></span>](how-to-create-a-custom-token.md)
