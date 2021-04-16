---
description: '詳細情報: 方法: ハードウェア暗号化デバイスにアクセスする'
title: '方法: ハードウェア暗号化デバイスにアクセスする'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: fcf12314490542848d20bd3a4977d68c386853bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685271"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="ddf62-103">方法: ハードウェア暗号化デバイスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="ddf62-103">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="ddf62-104">この記事は Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ddf62-104">This article applies to Windows.</span></span>

<span data-ttu-id="ddf62-105">ハードウェア暗号化デバイスにアクセスするには、<xref:System.Security.Cryptography.CspParameters> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-105">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="ddf62-106">たとえば、このクラスを使用すると、アプリケーションをスマート カード、ハードウェアの乱数ジェネレーター、または特定の暗号化アルゴリズムのハードウェア実装と統合することができます。</span><span class="sxs-lookup"><span data-stu-id="ddf62-106">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="ddf62-107"><xref:System.Security.Cryptography.CspParameters> クラスは、正しくインストールされたハードウェア暗号化デバイスにアクセスする暗号化サービス プロバイダー (CSP) を作成します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-107">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="ddf62-108">レジストリ エディター (Regedit.exe)  を使用してレジストリ キー (HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider) を調べることで、CSP を使用できるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ddf62-108">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="ddf62-109">キー カードを使用してデータに署名するには</span><span class="sxs-lookup"><span data-stu-id="ddf62-109">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="ddf62-110">整数のプロバイダー型とプロバイダーの名前をコンストラクターに渡す、<xref:System.Security.Cryptography.CspParameters> クラスのインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-110">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="ddf62-111">新規作成された <xref:System.Security.Cryptography.CspParameters> オブジェクトの <xref:System.Security.Cryptography.CspParameters.Flags%2A> プロパティに適切なフラグを渡します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-111">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="ddf62-112">たとえば、<xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> フラグを渡します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-112">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="ddf62-113"><xref:System.Security.Cryptography.CspParameters> オブジェクトをコンストラクターに渡す、<xref:System.Security.Cryptography.AsymmetricAlgorithm> クラス (<xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスなど) のインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-113">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="ddf62-114">`Sign` メソッドのいずれかを使用してデータに署名し、`Verify` メソッドのいずれかを使用してデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-114">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="ddf62-115">ハードウェアの乱数ジェネレーターを使用して乱数を生成するには</span><span class="sxs-lookup"><span data-stu-id="ddf62-115">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="ddf62-116">整数のプロバイダー型とプロバイダーの名前をコンストラクターに渡す、<xref:System.Security.Cryptography.CspParameters> クラスのインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-116">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="ddf62-117"><xref:System.Security.Cryptography.CspParameters> オブジェクトをコンストラクターに渡す、<xref:System.Security.Cryptography.RNGCryptoServiceProvider> のインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-117">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="ddf62-118"><xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> メソッドまたは <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> メソッドを使用してランダムな値を作成します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-118">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddf62-119">例</span><span class="sxs-lookup"><span data-stu-id="ddf62-119">Example</span></span>

<span data-ttu-id="ddf62-120">次のコード例は、スマート カードを使用してデータに署名する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ddf62-120">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="ddf62-121">このコード例は、スマート カードを公開する <xref:System.Security.Cryptography.CspParameters> オブジェクトを作成してから、CSP を使用して <xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="ddf62-121">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="ddf62-122">コード例では、続いて幾らかのデータの署名と確認を行います。</span><span class="sxs-lookup"><span data-stu-id="ddf62-122">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="ddf62-123">SHA1 には競合の問題があるため、SHA256 以上をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ddf62-123">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ddf62-124">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ddf62-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="ddf62-125"><xref:System> 名前空間と <xref:System.Security.Cryptography> 名前空間を含めます。</span><span class="sxs-lookup"><span data-stu-id="ddf62-125">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="ddf62-126">スマート カード リーダーとドライバーをコンピューターにインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddf62-126">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="ddf62-127">カード リーダー固有の情報を使用して、<xref:System.Security.Cryptography.CspParameters> オブジェクトを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddf62-127">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="ddf62-128">詳細については、カード リーダーのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddf62-128">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddf62-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddf62-129">See also</span></span>

- [<span data-ttu-id="ddf62-130">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="ddf62-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="ddf62-131">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="ddf62-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="ddf62-132">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="ddf62-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="ddf62-133">ASP.NET Core データ保護</span><span class="sxs-lookup"><span data-stu-id="ddf62-133">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
