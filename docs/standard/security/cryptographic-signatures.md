---
description: '詳細情報: 暗号化署名'
title: 暗号署名
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET], signatures
- security [.NET], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: 082f55af648b73b6447d69edd5912804e9332d03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685297"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="4ba9d-103">暗号署名</span><span class="sxs-lookup"><span data-stu-id="4ba9d-103">Cryptographic Signatures</span></span>

<span data-ttu-id="4ba9d-104">暗号デジタル署名は、公開キー アルゴリズムを使用してデータの整合性を提供します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-104">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="4ba9d-105">デジタル署名を使用してデータに署名すると、第三者が署名を検証し、データが署名者から発信され、署名後に変更されていないことを証明できます。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-105">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="4ba9d-106">デジタル署名の詳細については、「 [Cryptographic Services](cryptographic-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-106">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="4ba9d-107">ここでは、 <xref:System.Security.Cryptography> 名前空間のクラスを使用してデジタル署名を生成して検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-107">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="4ba9d-108">署名の生成</span><span class="sxs-lookup"><span data-stu-id="4ba9d-108">Generating Signatures</span></span>

<span data-ttu-id="4ba9d-109">デジタル署名は、通常、大きなデータを表現するハッシュ値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-109">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="4ba9d-110">ハッシュ値にデジタル署名を適用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-110">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="4ba9d-111">まず、 <xref:System.Security.Cryptography.RSA> クラスの新しいインスタンスを作成して、公開キー/秘密キーのペアを生成します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-111">First, a new instance of the <xref:System.Security.Cryptography.RSA> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="4ba9d-112">次に、 <xref:System.Security.Cryptography.RSA> を <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> クラスの新しいインスタンスに渡します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-112">Next, the <xref:System.Security.Cryptography.RSA> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="4ba9d-113">これにより、デジタル署名を実際に実行する <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>に秘密キーが渡されます。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-113">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="4ba9d-114">ハッシュ コードに署名するためには、使用するハッシュ アルゴリズムを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-114">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="4ba9d-115">この例では、SHA1 アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-115">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="4ba9d-116">最後に、 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> メソッドを呼び出して署名を実行します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-116">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="4ba9d-117">SHA1 との衝突の問題により、SHA256 以上をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-117">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As RSA = RSA.Create()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSA instance to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
    End Sub
End Module
```

```csharp
using System;
using System.Security.Cryptography;

class Class1
{
   static void Main()
   {
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSA rsa = RSA.Create();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSA instance to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

## <a name="verifying-signatures"></a><span data-ttu-id="4ba9d-118">署名の検証</span><span class="sxs-lookup"><span data-stu-id="4ba9d-118">Verifying Signatures</span></span>

<span data-ttu-id="4ba9d-119">データが特定の関係者によって署名されたことを検証するには、次の情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-119">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="4ba9d-120">データに署名した関係者の公開キー。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-120">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="4ba9d-121">デジタル署名。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-121">The digital signature.</span></span>

- <span data-ttu-id="4ba9d-122">署名されたデータ。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-122">The data that was signed.</span></span>

- <span data-ttu-id="4ba9d-123">署名者が使用したハッシュ アルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-123">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="4ba9d-124"><xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> クラスによって署名された署名を検証するには、 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-124">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="4ba9d-125"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> クラスに対しては、署名者の公開キーを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-125">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="4ba9d-126">RSA の場合、公開キーを指定するには、剰余と指数部の値が必要です。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-126">For RSA, you will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="4ba9d-127">(公開キーと秘密キーのペアを生成したパーティは、これらの値を提供する必要があります)。まず、 <xref:System.Security.Cryptography.RSA> 署名を検証する公開キーを保持するオブジェクトを作成し、次に、 <xref:System.Security.Cryptography.RSAParameters> 公開キーを指定する剰余と指数の値に構造体を初期化します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-127">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSA> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="4ba9d-128">次のコードは、 <xref:System.Security.Cryptography.RSAParameters> 構造体の作成を示しています。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-128">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="4ba9d-129">`Modulus` プロパティは `modulusData` というバイト配列の値に設定し、 `Exponent` プロパティは `exponentData`というバイト配列の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-129">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

<span data-ttu-id="4ba9d-130">オブジェクトを作成したら <xref:System.Security.Cryptography.RSAParameters> 、実装クラスの新しいインスタンスを、 <xref:System.Security.Cryptography.RSA> で指定した値に初期化でき <xref:System.Security.Cryptography.RSAParameters> ます。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-130">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSA> implementation class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="4ba9d-131">さらに、 <xref:System.Security.Cryptography.RSA> インスタンスは、キーを転送するためにのコンストラクターに渡され <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> ます。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-131">The <xref:System.Security.Cryptography.RSA> instance is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="4ba9d-132">このプロセスを説明する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-132">The following example illustrates this process.</span></span> <span data-ttu-id="4ba9d-133">この例で、 `hashValue` と `signedHashValue` は、リモートにいる関係者から提供されるバイト配列です。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-133">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="4ba9d-134">リモートにいる関係者は、SHA1 アルゴリズムを使用して `hashValue` に署名し、デジタル署名 `signedHashValue`を生成します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-134">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="4ba9d-135">メソッドは、 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> デジタル署名が有効であり、に署名するために使用されたことを確認し `hashValue` ます。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-135">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

<span data-ttu-id="4ba9d-136">SHA1 との衝突の問題により、SHA256 以上をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-136">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>  <span data-ttu-id="4ba9d-137">ただし、署名の作成に SHA1 を使用した場合は、SHA1 を使用して署名を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-137">However, if SHA1 was used to create the signature, you have to use SHA1 to verify the signature.</span></span>

```vb
Dim rsa As RSA = RSA.Create()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSA rsa = RSA.Create();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

<span data-ttu-id="4ba9d-138">上記のコードでは、署名が有効であれば "`The signature is valid`" を表示し、署名が無効であれば "`The signature is not valid`" を表示します。</span><span class="sxs-lookup"><span data-stu-id="4ba9d-138">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ba9d-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ba9d-139">See also</span></span>

- [<span data-ttu-id="4ba9d-140">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="4ba9d-140">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="4ba9d-141">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="4ba9d-141">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="4ba9d-142">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="4ba9d-142">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="4ba9d-143">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4ba9d-143">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
