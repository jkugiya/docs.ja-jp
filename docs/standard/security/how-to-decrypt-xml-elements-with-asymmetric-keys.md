---
description: '詳細については、「方法: 非対称キーを使用して XML 要素を復号化する」を参照してください。'
title: '方法: 非対称キーで XML 要素を復号化する'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: bd3bd142aa5800efa83bc20a4b1af6d5bc61eba2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675573"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="b2148-103">方法: 非対称キーで XML 要素を復号化する</span><span class="sxs-lookup"><span data-stu-id="b2148-103">How to: Decrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="b2148-104"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化および復号化することができます。</span><span class="sxs-lookup"><span data-stu-id="b2148-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="b2148-105">XML 暗号化は、データが簡単に読み取られる心配なく、暗号化された XML データを交換または保存する標準的な方法です。</span><span class="sxs-lookup"><span data-stu-id="b2148-105">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="b2148-106">XML 暗号化標準の詳細については、「World Wide Web コンソーシアム (W3C) 勧告」 [Xml 署名の構文と処理](https://www.w3.org/TR/xmldsig-core/)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2148-106">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  

> [!NOTE]
> <span data-ttu-id="b2148-107">この記事のコードは、Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b2148-107">The code in this article applies to Windows.</span></span>

<span data-ttu-id="b2148-108">この手順の例では、「 [方法: 非対称キーで Xml 要素を暗号化](how-to-encrypt-xml-elements-with-asymmetric-keys.md)する」で説明されているメソッドを使用して、暗号化された xml 要素を復号化します。</span><span class="sxs-lookup"><span data-stu-id="b2148-108">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="b2148-109"><> 要素を検索し、要素を復号化して `EncryptedData` から、要素を元のプレーンテキスト XML 要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b2148-109">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="b2148-110">この例では、2 つのキーを使用して XML 要素を復号化します。</span><span class="sxs-lookup"><span data-stu-id="b2148-110">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="b2148-111">以前に生成された RSA 秘密キーをキーコンテナーから取得し、その RSA キーを使用して、 `EncryptedKey` <> 要素の <> 要素に格納されているセッションキーを復号化し `EncryptedData` ます。</span><span class="sxs-lookup"><span data-stu-id="b2148-111">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="b2148-112">例では、セッション キーを使用して XML 要素を復号化します。</span><span class="sxs-lookup"><span data-stu-id="b2148-112">The example then uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="b2148-113">この例は、複数のアプリケーションが暗号化されたデータを共有する必要がある状況や、1 つのアプリケーションが、実行する時間の間に暗号化されたデータを保存する必要がある状況に適しています。</span><span class="sxs-lookup"><span data-stu-id="b2148-113">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="b2148-114">非対称キーで XML 要素を復号化するには</span><span class="sxs-lookup"><span data-stu-id="b2148-114">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="b2148-115"><xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、キーのコンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2148-115">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="b2148-116"><xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトを使用して、コンテナーから以前に生成された非対称キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="b2148-116">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="b2148-117"><xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> コンストラクターに渡すと、キー コンテナーからキーが自動的に取得されます。</span><span class="sxs-lookup"><span data-stu-id="b2148-117">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="b2148-118"><xref:System.Security.Cryptography.Xml.EncryptedXml> オブジェクトを新規作成してドキュメントを復号化します。</span><span class="sxs-lookup"><span data-stu-id="b2148-118">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="b2148-119">復号化が必要なドキュメント内で RSA キーと要素と関連付けるには、キーと名前のマッピングを追加します。</span><span class="sxs-lookup"><span data-stu-id="b2148-119">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="b2148-120">ドキュメントを暗号化したときに使用したキーと同じ名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2148-120">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="b2148-121">この名前は、手順 1 で指定されたキー コンテナー内のキーを識別するために使用する名前とは別であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b2148-121">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="b2148-122">メソッドを呼び出して <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 、<> 要素の暗号化を解除し `EncryptedData` ます。</span><span class="sxs-lookup"><span data-stu-id="b2148-122">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="b2148-123">このメソッドは、RSA キーを使用してセッション キーを復号化してから、自動的にセッション キーを使用して、XML 要素を復号化します。</span><span class="sxs-lookup"><span data-stu-id="b2148-123">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="b2148-124">また、<`EncryptedData`> 要素を元のプレーンテキストに自動的に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b2148-124">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="b2148-125">XML ドキュメントを保存します。</span><span class="sxs-lookup"><span data-stu-id="b2148-125">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b2148-126">例</span><span class="sxs-lookup"><span data-stu-id="b2148-126">Example</span></span>

<span data-ttu-id="b2148-127">この例では、`test.xml` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b2148-127">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="b2148-128">また、「 `test.xml` [方法: 非対称キーで xml 要素を暗号化](how-to-encrypt-xml-elements-with-asymmetric-keys.md)する」で説明されている手法を使用して暗号化された xml 要素がに含まれていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b2148-128">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2148-129">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b2148-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="b2148-130">.NET Framework を対象とするプロジェクトでは、への参照を含め `System.Security.dll` ます。</span><span class="sxs-lookup"><span data-stu-id="b2148-130">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="b2148-131">.NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b2148-131">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="b2148-132">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="b2148-132">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="b2148-133">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b2148-133">.NET Security</span></span>  

<span data-ttu-id="b2148-134">対称暗号化キーをプレーンテキストで保存したり、対称キーをコンピューター間でプレーンテキストで転送したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="b2148-134">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="b2148-135">加えて、非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2148-135">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="b2148-136">対称暗号化キーと非対称暗号化キーの詳細については、「 [暗号化と復号化のためのキーの生成](generating-keys-for-encryption-and-decryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2148-136">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="b2148-137">キーをソース コードに直接埋め込まないでください。</span><span class="sxs-lookup"><span data-stu-id="b2148-137">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="b2148-138">埋め込みキーは、 [Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用するか、メモ帳などのテキストエディターでアセンブリを開くことによって、簡単にアセンブリから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="b2148-138">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="b2148-139">暗号化キーを使用して完了したら、各バイトをゼロ (0) にするか、マネージド暗号化クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> メソッドを呼び出してメモリから消去します。</span><span class="sxs-lookup"><span data-stu-id="b2148-139">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="b2148-140">暗号化キーは、デバッガーによってメモリから読み取られるか、メモリの位置がディスクにページングされている場合はハード ドライブから読み取られることがあります。</span><span class="sxs-lookup"><span data-stu-id="b2148-140">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2148-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2148-141">See also</span></span>

- [<span data-ttu-id="b2148-142">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="b2148-142">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="b2148-143">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="b2148-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="b2148-144">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="b2148-144">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="b2148-145">方法: 非対称キーで XML 要素を暗号化する</span><span class="sxs-lookup"><span data-stu-id="b2148-145">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="b2148-146">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2148-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
