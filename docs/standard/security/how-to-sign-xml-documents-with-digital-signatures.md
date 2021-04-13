---
title: '方法: デジタル署名で XML ドキュメントに署名する'
description: デジタル署名で XML ドキュメントに署名する方法を説明します。 .NET の System.Security.Cryptography.Xml 名前空間のクラスを使用します。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSA class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: 2cb63fd91b1aeb51c762975103ea665e0d8539b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726679"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="9f58f-104">方法: デジタル署名で XML ドキュメントに署名する</span><span class="sxs-lookup"><span data-stu-id="9f58f-104">How to: Sign XML Documents with Digital Signatures</span></span>

<span data-ttu-id="9f58f-105"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用すると、XML ドキュメントまたは XML ドキュメントの一部にデジタル署名で署名することができます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-105">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="9f58f-106">XML デジタル署名 (XMLDSIG) を使用すると、データが署名後に変更されなかったことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-106">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="9f58f-107">XMLDSIG の基準の詳細については、World Wide Web コンソーシアム (W3C) の推奨事項「[XML 署名の構文と処理](https://www.w3.org/TR/xmldsig-core/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f58f-107">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f58f-108">この記事のコードは、Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-108">The code in this article applies to Windows.</span></span>

<span data-ttu-id="9f58f-109">この手順のコード例は、XML ドキュメント全体にデジタル署名する方法、および <`Signature`> 要素内のドキュメントに署名を付す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9f58f-109">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="9f58f-110">この例では、RSA 署名キーを作成し、キーをセキュリティで保護されたキー コンテナーに追加してから、キーを使用して XML ドキュメントにデジタル署名しています。</span><span class="sxs-lookup"><span data-stu-id="9f58f-110">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="9f58f-111">キーは、XML デジタル署名を確認するために取得したり、別の XML ドキュメントの署名に使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-111">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
<span data-ttu-id="9f58f-112">この手順を使用して作成された XML デジタル署名を確認する方法については、「[方法: XML ドキュメントのデジタル署名を検証する](how-to-verify-the-digital-signatures-of-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f58f-112">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="9f58f-113">XML ドキュメントにデジタル署名するには</span><span class="sxs-lookup"><span data-stu-id="9f58f-113">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="9f58f-114"><xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、キーのコンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-114">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="9f58f-115"><xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して非対称キーを生成します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-115">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="9f58f-116"><xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キーは自動的にキー コンテナーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-116">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="9f58f-117">このキーは、XML ドキュメントの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-117">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="9f58f-118">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-118">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="9f58f-119"><xref:System.Xml.XmlDocument> オブジェクトには、暗号化する XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9f58f-119">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="9f58f-120"><xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトを新規作成し、それに <xref:System.Xml.XmlDocument> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-120">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="9f58f-121">署名する RSA キーを <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-121">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="9f58f-122">署名内容について記述する <xref:System.Security.Cryptography.Xml.Reference> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-122">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="9f58f-123">ドキュメント全体に署名するには、<xref:System.Security.Cryptography.Xml.Reference.Uri%2A> プロパティを `""` に設定します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-123">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="9f58f-124"><xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> オブジェクトを <xref:System.Security.Cryptography.Xml.Reference> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-124">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="9f58f-125">変換を使用すると、検証側は、署名側が使用した方法と同一の方法で XML データを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-125">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="9f58f-126">XML データはさまざまな方法で表すことができるため、この手順は検証にとって重要です。</span><span class="sxs-lookup"><span data-stu-id="9f58f-126">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="9f58f-127"><xref:System.Security.Cryptography.Xml.Reference> オブジェクトを <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-127">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="9f58f-128"><xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> メソッドを呼び出して署名を計算します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-128">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="9f58f-129">署名の XML 表記 (<`Signature`> 要素) を取得して、新しい <xref:System.Xml.XmlElement> オブジェクトに保存します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-129">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="9f58f-130"><xref:System.Xml.XmlDocument> オブジェクトに要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-130">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="9f58f-131">ドキュメントを保存します。</span><span class="sxs-lookup"><span data-stu-id="9f58f-131">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="9f58f-132">例</span><span class="sxs-lookup"><span data-stu-id="9f58f-132">Example</span></span>  

 <span data-ttu-id="9f58f-133">この例では、`test.xml` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="9f58f-133">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="9f58f-134">次の XML を `test.xml` というファイルに配置し、この例で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-134">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f58f-135">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9f58f-135">Compiling the Code</span></span>  
  
- <span data-ttu-id="9f58f-136">.NET Framework を対象とするプロジェクトでは、`System.Security.dll` への参照を含めます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-136">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="9f58f-137">.NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9f58f-137">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="9f58f-138">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-138">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="9f58f-139">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9f58f-139">.NET Security</span></span>

<span data-ttu-id="9f58f-140">非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f58f-140">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="9f58f-141">対称および非対称暗号化キーの詳細については、「[暗号化と復号化のためのキーの生成](generating-keys-for-encryption-and-decryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f58f-141">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="9f58f-142">秘密キーをソース コードに直接埋め込まないでください。</span><span class="sxs-lookup"><span data-stu-id="9f58f-142">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="9f58f-143">埋め込まれたキーは、[Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用するか、メモ帳などのテキスト エディターでアセンブリを開くことで、アセンブリから簡単に読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9f58f-143">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f58f-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f58f-144">See also</span></span>

- [<span data-ttu-id="9f58f-145">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="9f58f-145">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="9f58f-146">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="9f58f-146">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="9f58f-147">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="9f58f-147">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="9f58f-148">方法: XML ドキュメントのデジタル署名を検証する</span><span class="sxs-lookup"><span data-stu-id="9f58f-148">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
- [<span data-ttu-id="9f58f-149">ASP.NET Core データ保護</span><span class="sxs-lookup"><span data-stu-id="9f58f-149">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
