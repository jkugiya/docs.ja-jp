---
title: .NET 暗号化モデル
description: .NET での通常の暗号化アルゴリズムの実装を確認します。 オブジェクトの継承、ストリームのデザイン、& 構成の拡張可能な暗号化モデルについて説明します。
ms.date: 02/26/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 2208e36ac4521f43cfd2960d92588c8349a119ca
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106931"
---
# <a name="net-cryptography-model"></a><span data-ttu-id="53b95-104">.NET 暗号化モデル</span><span class="sxs-lookup"><span data-stu-id="53b95-104">.NET cryptography model</span></span>

<span data-ttu-id="53b95-105">.NET には、多くの標準的な暗号化アルゴリズムの実装が用意されており、.NET 暗号化モデルは拡張可能です。</span><span class="sxs-lookup"><span data-stu-id="53b95-105">.NET provides implementations of many standard cryptographic algorithms, and the .NET cryptography model is extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="53b95-106">オブジェクトの継承</span><span class="sxs-lookup"><span data-stu-id="53b95-106">Object inheritance</span></span>

<span data-ttu-id="53b95-107">.NET 暗号化システムは、派生クラスの継承の拡張可能なパターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="53b95-107">The .NET cryptography system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="53b95-108">階層は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="53b95-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="53b95-109">アルゴリズムの種類クラス (、、など) <xref:System.Security.Cryptography.SymmetricAlgorithm>  <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.HashAlgorithm> 。</span><span class="sxs-lookup"><span data-stu-id="53b95-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm>, or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="53b95-110">このレベルは抽象レベルです。</span><span class="sxs-lookup"><span data-stu-id="53b95-110">This level is abstract.</span></span>

- <span data-ttu-id="53b95-111"><xref:System.Security.Cryptography.Aes>、<xref:System.Security.Cryptography.RSA>、または <xref:System.Security.Cryptography.ECDiffieHellman> など、アルゴリズム型クラスから継承されるアルゴリズム クラス。</span><span class="sxs-lookup"><span data-stu-id="53b95-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RSA>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="53b95-112">このレベルは抽象レベルです。</span><span class="sxs-lookup"><span data-stu-id="53b95-112">This level is abstract.</span></span>

- <span data-ttu-id="53b95-113"><xref:System.Security.Cryptography.AesManaged>、<xref:System.Security.Cryptography.RC2CryptoServiceProvider>、または <xref:System.Security.Cryptography.ECDiffieHellmanCng> など、アルゴリズム クラスから継承されるアルゴリズム クラスの実装。</span><span class="sxs-lookup"><span data-stu-id="53b95-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="53b95-114">このレベルは完全に実装されます。</span><span class="sxs-lookup"><span data-stu-id="53b95-114">This level is fully implemented.</span></span>

<span data-ttu-id="53b95-115">この派生クラスのパターンを使用すると、新しいアルゴリズムを追加したり、既存のアルゴリズムの新しい実装を追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="53b95-115">This pattern of derived classes lets you add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="53b95-116">たとえば、新しい公開キー アルゴリズムを作成するには、<xref:System.Security.Cryptography.AsymmetricAlgorithm> クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="53b95-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="53b95-117">特定のアルゴリズムの実装を新しく作成するには、そのアルゴリズムの非抽象派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="53b95-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-net"></a><span data-ttu-id="53b95-118">.NET でのアルゴリズムの実装方法</span><span class="sxs-lookup"><span data-stu-id="53b95-118">How algorithms are implemented in .NET</span></span>

<span data-ttu-id="53b95-119">アルゴリズムに使用できるさまざまな実装例として、対称アルゴリズムを検討します。</span><span class="sxs-lookup"><span data-stu-id="53b95-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="53b95-120">すべての対称アルゴリズムの基本は、、 <xref:System.Security.Cryptography.SymmetricAlgorithm> <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.TripleDES> 、および推奨されなくなった他のすべての対称アルゴリズムによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="53b95-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.TripleDES>, and others that are no longer recommended.</span></span>

<span data-ttu-id="53b95-121"><xref:System.Security.Cryptography.Aes> は、、、およびによって継承され <xref:System.Security.Cryptography.AesCryptoServiceProvider> <xref:System.Security.Cryptography.AesCng> <xref:System.Security.Cryptography.AesManaged> ます。</span><span class="sxs-lookup"><span data-stu-id="53b95-121"><xref:System.Security.Cryptography.Aes> is inherited by <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.AesCng>, and <xref:System.Security.Cryptography.AesManaged>.</span></span>

<span data-ttu-id="53b95-122">Windows の .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="53b95-122">In .NET Framework on Windows:</span></span>

* <span data-ttu-id="53b95-123">`*CryptoServiceProvider` アルゴリズムクラス (など) <xref:System.Security.Cryptography.AesCryptoServiceProvider> は、アルゴリズムの Windows CRYPTOGRAPHY API (CAPI) 実装のラッパーです。</span><span class="sxs-lookup"><span data-stu-id="53b95-123">`*CryptoServiceProvider` algorithm classes, such as <xref:System.Security.Cryptography.AesCryptoServiceProvider>, are wrappers around the Windows Cryptography API (CAPI) implementation of an algorithm.</span></span>
* <span data-ttu-id="53b95-124">`*Cng` などのアルゴリズムクラス <xref:System.Security.Cryptography.ECDiffieHellmanCng> は、Windows Cryptography Next Generation (CNG) 実装のラッパーです。</span><span class="sxs-lookup"><span data-stu-id="53b95-124">`*Cng` algorithm classes, such as <xref:System.Security.Cryptography.ECDiffieHellmanCng>, are wrappers around the Windows Cryptography Next Generation (CNG) implementation.</span></span>
* <span data-ttu-id="53b95-125">`*Managed` などのクラス <xref:System.Security.Cryptography.AesManaged> は、完全にマネージコードで記述されます。</span><span class="sxs-lookup"><span data-stu-id="53b95-125">`*Managed` classes, such as <xref:System.Security.Cryptography.AesManaged>, are written entirely in managed code.</span></span> <span data-ttu-id="53b95-126">`*Managed` 実装は、連邦情報処理規格 (FIPS) によって認定されていないため、およびラッパークラスよりも低速になる可能性があり `*CryptoServiceProvider` `*Cng` ます。</span><span class="sxs-lookup"><span data-stu-id="53b95-126">`*Managed` implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the `*CryptoServiceProvider` and `*Cng` wrapper classes.</span></span>

<span data-ttu-id="53b95-127">.NET Core と .NET 5 以降のバージョンでは、すべての実装クラス ( `*CryptoServiceProvider` 、 `*Managed` 、および `*Cng` ) は、オペレーティングシステム (os) アルゴリズムのラッパーです。</span><span class="sxs-lookup"><span data-stu-id="53b95-127">In .NET Core and .NET 5 and later versions, all implementation classes (`*CryptoServiceProvider`, `*Managed`, and `*Cng`) are wrappers for the operating system (OS) algorithms.</span></span> <span data-ttu-id="53b95-128">OS アルゴリズムが FIPS 認定の場合、.NET は FIPS 認定アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="53b95-128">If the OS algorithms are FIPS-certified, then .NET uses FIPS-certified algorithms.</span></span> <span data-ttu-id="53b95-129">詳細については、「 [クロスプラットフォーム暗号化](cross-platform-cryptography.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53b95-129">For more information, see [Cross-Platform Cryptography](cross-platform-cryptography.md).</span></span>

<span data-ttu-id="53b95-130">ほとんどの場合、などのアルゴリズム実装クラスを直接参照する必要はありません `AesCryptoServiceProvider` 。</span><span class="sxs-lookup"><span data-stu-id="53b95-130">In most cases, you don't need to directly reference an algorithm implementation class, such as `AesCryptoServiceProvider`.</span></span> <span data-ttu-id="53b95-131">通常必要なメソッドとプロパティは、のような基本アルゴリズムクラスにあり `Aes` ます。</span><span class="sxs-lookup"><span data-stu-id="53b95-131">The methods and properties you typically need are on the base algorithm class, such as `Aes`.</span></span> <span data-ttu-id="53b95-132">基本アルゴリズムクラスのファクトリメソッドを使用して、既定の実装クラスのインスタンスを作成し、基本アルゴリズムクラスを参照します。</span><span class="sxs-lookup"><span data-stu-id="53b95-132">Create an instance of a default implementation class by using a factory method on the base algorithm class, and refer to the base algorithm class.</span></span> <span data-ttu-id="53b95-133">たとえば、次の例で強調表示されているコード行を確認します。</span><span class="sxs-lookup"><span data-stu-id="53b95-133">For example, see the highlighted line of code in the following example:</span></span>

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="20":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="17":::

## <a name="cryptographic-configuration"></a><span data-ttu-id="53b95-134">暗号化の構成</span><span class="sxs-lookup"><span data-stu-id="53b95-134">Cryptographic configuration</span></span>

<span data-ttu-id="53b95-135">暗号化の構成を使用すると、アルゴリズムの特定の実装をアルゴリズム名に解決して、.NET 暗号化クラスの機能拡張を可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="53b95-135">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET cryptography classes.</span></span> <span data-ttu-id="53b95-136">アルゴリズムの独自のハードウェアまたはソフトウェア実装を追加して、実装を任意のアルゴリズム名にマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="53b95-136">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="53b95-137">構成ファイルでアルゴリズムを指定しない場合は、既定の設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="53b95-137">If an algorithm is not specified in the configuration file, the default settings are used.</span></span>

## <a name="choose-an-algorithm"></a><span data-ttu-id="53b95-138">アルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="53b95-138">Choose an algorithm</span></span>

<span data-ttu-id="53b95-139">データの整合性、データのプライバシー保護、またはキー生成など、さまざまな理由のためにアルゴリズムを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="53b95-139">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="53b95-140">対称アルゴリズムおよびハッシュ アルゴリズムは、整合性の理由 (変更の防止) またはプライバシー上の理由 (表示の防止) のいずれかのためにデータを保護することを意図しています。</span><span class="sxs-lookup"><span data-stu-id="53b95-140">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="53b95-141">ハッシュ アルゴリズムは、主にデータの整合性用に使用されます。</span><span class="sxs-lookup"><span data-stu-id="53b95-141">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="53b95-142">アプリケーションで推奨されるアルゴリズムの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="53b95-142">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="53b95-143">データのプライバシー : </span><span class="sxs-lookup"><span data-stu-id="53b95-143">Data privacy:</span></span>
  - <xref:System.Security.Cryptography.Aes>
- <span data-ttu-id="53b95-144">データの整合性 : </span><span class="sxs-lookup"><span data-stu-id="53b95-144">Data integrity:</span></span>
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- <span data-ttu-id="53b95-145">デジタル署名 : </span><span class="sxs-lookup"><span data-stu-id="53b95-145">Digital signature:</span></span>
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="53b95-146">キー交換 : </span><span class="sxs-lookup"><span data-stu-id="53b95-146">Key exchange:</span></span>
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="53b95-147">乱数生成 : </span><span class="sxs-lookup"><span data-stu-id="53b95-147">Random number generation:</span></span>
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- <span data-ttu-id="53b95-148">パスワードからのキー生成 :  </span><span class="sxs-lookup"><span data-stu-id="53b95-148">Generating a key from a password:</span></span>
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="53b95-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="53b95-149">See also</span></span>

- [<span data-ttu-id="53b95-150">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="53b95-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="53b95-151">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="53b95-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="53b95-152">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="53b95-152">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
