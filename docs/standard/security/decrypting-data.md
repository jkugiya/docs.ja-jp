---
title: データの暗号化解除
description: .NET で対称アルゴリズムまたは非対称アルゴリズムを使用してデータを復号化する方法について説明します。
ms.date: 03/22/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 14d8b6185c1c5b3aaee4f2041f98c500f2d3c313
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027910"
---
# <a name="decrypting-data"></a>データの暗号化解除

復号化は、暗号化の逆の操作です。 秘密キーの暗号化では、データの暗号化に使用されたキーと IV の両方を把握しておく必要があります。 公開キーの暗号化では、公開キー (データが秘密キーで暗号化された場合) または秘密キー (データが公開キーで暗号化された場合) のいずれかを把握しておく必要があります。

## <a name="symmetric-decryption"></a>対称暗号化解除

対称アルゴリズムで暗号化されたデータの復号化は、対称アルゴリズムでデータを暗号化する際に使用するプロセスと似ています。 任意のマネージド ストリーム オブジェクトから読み取られたデータを復号化するために、<xref:System.Security.Cryptography.CryptoStream> クラスが、.NET によって提供されている対称暗号化クラスと共に使用されます。

次の例は、<xref:System.Security.Cryptography.Aes> アルゴリズム用の既定の実装クラスの新しいインスタンスを作成する方法を示しています。 このインスタンスは、<xref:System.Security.Cryptography.CryptoStream> オブジェクトに対して復号化を実行するために使用されます。 この例では、まず <xref:System.Security.Cryptography.Aes> 実装クラスの新しいインスタンスを作成します。 これは、マネージド ストリーム変数 `myStream` から初期化ベクター (IV) 値を読み取ります。 次に、<xref:System.Security.Cryptography.CryptoStream> オブジェクトのインスタンスを作成し、それを `myStream` インスタンスの値に初期化します。 <xref:System.Security.Cryptography.Aes> インスタンスの <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> メソッドには、暗号化に使用されたのと同じ IV 値とキーが渡されます。

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(
    myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(
    myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

次の例は、ストリームの作成、ストリームの復号化、ストリームからの読み取り、およびストリームを閉じるプロセス全体を示しています。 *TestData.txt* という名前のファイルを読み取るファイル ストリーム オブジェクトが作成されます。 次に、このファイル ストリームが **CryptoStream** クラスと **Aes** クラスを使用して復号化されます。 この例では、[データの暗号化](encrypting-data.md)の対称暗号化の例で使用されたキーの値を指定しています。 これらの値の暗号化および転送に必要なコードは示されていません。

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

上の例では、[データの暗号化](encrypting-data.md)の対称暗号化の例で使用されたのと同じキーとアルゴリズムを使用しています。 その例によって作成された *TestData.txt* ファイルを復号化し、元のテキストをコンソールに表示します。

## <a name="asymmetric-decryption"></a>非対称暗号化解除

通常は、パーティ (パーティ A) は、公開キーと秘密キーの両方を生成し、メモリ内、または暗号化キー コンテナーのいずれかに格納します。 パーティ A は公開キーを別のパーティ (パーティ B) に送信します。 パーティ B は、公開キーを使用して、データを暗号化してからパーティ A に返送します。パーティ A は、データを受信すると、対応する秘密キーを使用して復号化します。 復号化は、パーティ B がデータの暗号化に使用した公開キーに対応する秘密キーをパーティ A が使用する場合にのみ成功します。

セキュリティで保護された暗号化キー コンテナーに非対称キーを格納する方法と、その後非対称キーを取得する方法については、「 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)」を参照してください。

次の例は、対称キーと IV を表す 2 つのバイト配列の復号化を示しています。 第三者に簡単に送信できる形式で <xref:System.Security.Cryptography.RSA> オブジェクトから非対称の公開キーを抽出する方法については、「 [Encrypting Data](encrypting-data.md)というマネージ ストリームの値に初期化します。

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a>関連項目

- [暗号化と暗号化解除のためのキーの生成](generating-keys-for-encryption-and-decryption.md)
- [データの暗号化](encrypting-data.md)
- [暗号化サービス](cryptographic-services.md)
- [暗号モデル](cryptography-model.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- [パディングを使用した CBC モードの対称復号化に関するタイミングの脆弱性](vulnerabilities-cbc-mode.md)
- [ASP.NET Core データ保護](/aspnet/core/security/data-protection/introduction)
