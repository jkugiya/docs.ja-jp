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
# <a name="decrypting-data"></a><span data-ttu-id="081e3-103">データの暗号化解除</span><span class="sxs-lookup"><span data-stu-id="081e3-103">Decrypting data</span></span>

<span data-ttu-id="081e3-104">復号化は、暗号化の逆の操作です。</span><span class="sxs-lookup"><span data-stu-id="081e3-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="081e3-105">秘密キーの暗号化では、データの暗号化に使用されたキーと IV の両方を把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="081e3-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="081e3-106">公開キーの暗号化では、公開キー (データが秘密キーで暗号化された場合) または秘密キー (データが公開キーで暗号化された場合) のいずれかを把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="081e3-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="081e3-107">対称暗号化解除</span><span class="sxs-lookup"><span data-stu-id="081e3-107">Symmetric decryption</span></span>

<span data-ttu-id="081e3-108">対称アルゴリズムで暗号化されたデータの復号化は、対称アルゴリズムでデータを暗号化する際に使用するプロセスと似ています。</span><span class="sxs-lookup"><span data-stu-id="081e3-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="081e3-109">任意のマネージド ストリーム オブジェクトから読み取られたデータを復号化するために、<xref:System.Security.Cryptography.CryptoStream> クラスが、.NET によって提供されている対称暗号化クラスと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="081e3-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="081e3-110">次の例は、<xref:System.Security.Cryptography.Aes> アルゴリズム用の既定の実装クラスの新しいインスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="081e3-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="081e3-111">このインスタンスは、<xref:System.Security.Cryptography.CryptoStream> オブジェクトに対して復号化を実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="081e3-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="081e3-112">この例では、まず <xref:System.Security.Cryptography.Aes> 実装クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="081e3-112">This example first creates a new instance of the <xref:System.Security.Cryptography.Aes> implementation class.</span></span> <span data-ttu-id="081e3-113">これは、マネージド ストリーム変数 `myStream` から初期化ベクター (IV) 値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="081e3-113">It reads the initialization vector (IV) value from a managed stream variable, `myStream`.</span></span> <span data-ttu-id="081e3-114">次に、<xref:System.Security.Cryptography.CryptoStream> オブジェクトのインスタンスを作成し、それを `myStream` インスタンスの値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="081e3-114">Next it instantiates a <xref:System.Security.Cryptography.CryptoStream> object and initializes it to the value of the `myStream` instance.</span></span> <span data-ttu-id="081e3-115"><xref:System.Security.Cryptography.Aes> インスタンスの <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> メソッドには、暗号化に使用されたのと同じ IV 値とキーが渡されます。</span><span class="sxs-lookup"><span data-stu-id="081e3-115">The <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> method from the <xref:System.Security.Cryptography.Aes> instance is passed the IV value and the same key that was used for encryption.</span></span>

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

<span data-ttu-id="081e3-116">次の例は、ストリームの作成、ストリームの復号化、ストリームからの読み取り、およびストリームを閉じるプロセス全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="081e3-116">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="081e3-117">*TestData.txt* という名前のファイルを読み取るファイル ストリーム オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="081e3-117">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="081e3-118">次に、このファイル ストリームが **CryptoStream** クラスと **Aes** クラスを使用して復号化されます。</span><span class="sxs-lookup"><span data-stu-id="081e3-118">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="081e3-119">この例では、[データの暗号化](encrypting-data.md)の対称暗号化の例で使用されたキーの値を指定しています。</span><span class="sxs-lookup"><span data-stu-id="081e3-119">This example specifies key value that is used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="081e3-120">これらの値の暗号化および転送に必要なコードは示されていません。</span><span class="sxs-lookup"><span data-stu-id="081e3-120">It does not show the code needed to encrypt and transfer these values.</span></span>

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

<span data-ttu-id="081e3-121">上の例では、[データの暗号化](encrypting-data.md)の対称暗号化の例で使用されたのと同じキーとアルゴリズムを使用しています。</span><span class="sxs-lookup"><span data-stu-id="081e3-121">The preceding example uses the same key, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="081e3-122">その例によって作成された *TestData.txt* ファイルを復号化し、元のテキストをコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="081e3-122">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="081e3-123">非対称暗号化解除</span><span class="sxs-lookup"><span data-stu-id="081e3-123">Asymmetric decryption</span></span>

<span data-ttu-id="081e3-124">通常は、パーティ (パーティ A) は、公開キーと秘密キーの両方を生成し、メモリ内、または暗号化キー コンテナーのいずれかに格納します。</span><span class="sxs-lookup"><span data-stu-id="081e3-124">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="081e3-125">パーティ A は公開キーを別のパーティ (パーティ B) に送信します。</span><span class="sxs-lookup"><span data-stu-id="081e3-125">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="081e3-126">パーティ B は、公開キーを使用して、データを暗号化してからパーティ A に返送します。パーティ A は、データを受信すると、対応する秘密キーを使用して復号化します。</span><span class="sxs-lookup"><span data-stu-id="081e3-126">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="081e3-127">復号化は、パーティ B がデータの暗号化に使用した公開キーに対応する秘密キーをパーティ A が使用する場合にのみ成功します。</span><span class="sxs-lookup"><span data-stu-id="081e3-127">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="081e3-128">セキュリティで保護された暗号化キー コンテナーに非対称キーを格納する方法と、その後非対称キーを取得する方法については、「 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="081e3-128">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="081e3-129">次の例は、対称キーと IV を表す 2 つのバイト配列の復号化を示しています。</span><span class="sxs-lookup"><span data-stu-id="081e3-129">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="081e3-130">第三者に簡単に送信できる形式で <xref:System.Security.Cryptography.RSA> オブジェクトから非対称の公開キーを抽出する方法については、「 [Encrypting Data](encrypting-data.md)というマネージ ストリームの値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="081e3-130">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="081e3-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="081e3-131">See also</span></span>

- [<span data-ttu-id="081e3-132">暗号化と暗号化解除のためのキーの生成</span><span class="sxs-lookup"><span data-stu-id="081e3-132">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="081e3-133">データの暗号化</span><span class="sxs-lookup"><span data-stu-id="081e3-133">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="081e3-134">暗号化サービス</span><span class="sxs-lookup"><span data-stu-id="081e3-134">Cryptographic services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="081e3-135">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="081e3-135">Cryptography model</span></span>](cryptography-model.md)
- [<span data-ttu-id="081e3-136">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="081e3-136">Cross-platform cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="081e3-137">パディングを使用した CBC モードの対称復号化に関するタイミングの脆弱性</span><span class="sxs-lookup"><span data-stu-id="081e3-137">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="081e3-138">ASP.NET Core データ保護</span><span class="sxs-lookup"><span data-stu-id="081e3-138">ASP.NET Core data protection</span></span>](/aspnet/core/security/data-protection/introduction)
