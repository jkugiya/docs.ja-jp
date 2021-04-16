---
description: '詳細情報: 暗号署名'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685297"
---
# <a name="cryptographic-signatures"></a>暗号署名

暗号デジタル署名は、公開キー アルゴリズムを使用してデータの整合性を提供します。 デジタル署名を使用してデータに署名すると、第三者が署名を検証し、データが署名者から発信され、署名後に変更されていないことを証明できます。 デジタル署名の詳細については、「 [Cryptographic Services](cryptographic-services.md)」を参照してください。

ここでは、 <xref:System.Security.Cryptography> 名前空間のクラスを使用してデジタル署名を生成して検証する方法について説明します。

## <a name="generating-signatures"></a>署名の生成

デジタル署名は、通常、大きなデータを表現するハッシュ値に適用されます。 ハッシュ値にデジタル署名を適用する例を次に示します。 まず、 <xref:System.Security.Cryptography.RSA> クラスの新しいインスタンスを作成して、公開キー/秘密キーのペアを生成します。 次に、 <xref:System.Security.Cryptography.RSA> を <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> クラスの新しいインスタンスに渡します。 これにより、デジタル署名を実際に実行する <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>に秘密キーが渡されます。 ハッシュ コードに署名するためには、使用するハッシュ アルゴリズムを指定する必要があります。 この例では、SHA1 アルゴリズムを使用します。 最後に、 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> メソッドを呼び出して署名を実行します。

SHA1 には競合の問題があるため、SHA256 以上をお勧めします。

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

## <a name="verifying-signatures"></a>署名の検証

データが特定の関係者によって署名されたことを検証するには、次の情報が必要です。

- データに署名した関係者の公開キー。

- デジタル署名。

- 署名されたデータ。

- 署名者が使用したハッシュ アルゴリズム。

<xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> クラスによって署名された署名を検証するには、 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> クラスを使用します。 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> クラスに対しては、署名者の公開キーを提供する必要があります。 RSA では、公開キーを指定するために剰余と指数部の値が必要になります。 (これらの値は、公開および秘密キーのペアの生成者が提供する必要があります。)まず、署名を検証する公開キーを保持するための <xref:System.Security.Cryptography.RSA> オブジェクトを作成します。次に、<xref:System.Security.Cryptography.RSAParameters> 構造体を、公開キーを指定する剰余と指数部の値に初期化します。

次のコードは、 <xref:System.Security.Cryptography.RSAParameters> 構造体の作成を示しています。 `Modulus` プロパティは `modulusData` というバイト配列の値に設定し、 `Exponent` プロパティは `exponentData`というバイト配列の値に設定します。

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

<xref:System.Security.Cryptography.RSAParameters> オブジェクトを作成した後、<xref:System.Security.Cryptography.RSA> 実装クラスの新しいインスタンスを <xref:System.Security.Cryptography.RSAParameters> で指定された値に初期設定できます。 次に、<xref:System.Security.Cryptography.RSA> インスタンスが <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> のコンストラクターに引き渡され、キーが転送されます。

このプロセスを説明する例を次に示します。 この例で、 `hashValue` と `signedHashValue` は、リモートにいる関係者から提供されるバイト配列です。 リモートにいる関係者は、SHA1 アルゴリズムを使用して `hashValue` に署名し、デジタル署名 `signedHashValue`を生成します。 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> メソッドでは、デジタル署名が有効であることと、そのデジタル署名を使用して `hashValue` が署名されたことを検証します。

SHA1 には競合の問題があるため、SHA256 以上をお勧めします。  ただし、署名の作成に SHA1 を使用した場合は、SHA1 を使用して署名を検証する必要があります。

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

上記のコードでは、署名が有効であれば "`The signature is valid`" を表示し、署名が無効であれば "`The signature is not valid`" を表示します。

## <a name="see-also"></a>関連項目

- [Cryptographic Services](cryptographic-services.md)
- [暗号モデル](cryptography-model.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- [ASP.NET Core データ保護](/aspnet/core/security/data-protection/introduction)
