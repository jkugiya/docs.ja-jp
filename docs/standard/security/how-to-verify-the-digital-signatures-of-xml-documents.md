---
description: '詳細については、「方法: XML ドキュメントのデジタル署名を検証する」を参照してください。'
title: '方法: XML ドキュメントのデジタル署名を検証する'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSA class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: 37ef72c6bedf73ced7c2dde4335034f603190946
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685037"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="3b1d9-103">方法: XML ドキュメントのデジタル署名を検証する</span><span class="sxs-lookup"><span data-stu-id="3b1d9-103">How to: Verify the Digital Signatures of XML Documents</span></span>

<span data-ttu-id="3b1d9-104"><xref:System.Security.Cryptography.Xml> 名前空間にあるクラスを使用すると、デジタル署名で署名された XML データを検証できます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="3b1d9-105">XML デジタル署名 (XMLDSIG) を使用すると、データが署名後に変更されなかったことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-105">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="3b1d9-106">XMLDSIG 標準の詳細については、「」の World Wide Web コンソーシアム (W3C) の仕様を参照してください <https://www.w3.org/TR/xmldsig-core/> 。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-106">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3b1d9-107">この記事のコードは、Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-107">The code in this article applies to Windows.</span></span>

<span data-ttu-id="3b1d9-108">この手順のコード例では、<> 要素に含まれている XML デジタル署名を検証する方法を示し `Signature` ます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-108">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="3b1d9-109">この例では、キー コンテナーから RSA 公開キーを取得してから、キーを使用して署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-109">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
<span data-ttu-id="3b1d9-110">この手法を使用して検証できるデジタル署名を作成する方法については、「 [方法: デジタル署名で XML ドキュメントに署名](how-to-sign-xml-documents-with-digital-signatures.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-110">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="3b1d9-111">XML ドキュメントのデジタル署名を検証するには</span><span class="sxs-lookup"><span data-stu-id="3b1d9-111">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="3b1d9-112">ドキュメントを検証するには、署名に使用した非対称キーと同じ非対称キーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-112">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="3b1d9-113"><xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、署名に使用したキー コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="3b1d9-114"><xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-114">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="3b1d9-115"><xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キー コンテナーからキーが名前順で自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-115">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="3b1d9-116">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-116">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="3b1d9-117"><xref:System.Xml.XmlDocument> オブジェクトには、確認対象の署名済みの XML ドキュメントが含まています。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-117">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="3b1d9-118"><xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトを新規作成し、それに <xref:System.Xml.XmlDocument> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-118">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="3b1d9-119"><`signature`> 要素を検索し、新しいオブジェクトを作成し <xref:System.Xml.XmlNodeList> ます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-119">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="3b1d9-120">最初の <> 要素の XML を `signature` オブジェクトに読み込み <xref:System.Security.Cryptography.Xml.SignedXml> ます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-120">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="3b1d9-121"><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> メソッドと RSA の公開キーを使用して署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-121">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="3b1d9-122">このメソッドは、成功または失敗を示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-122">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="3b1d9-123">例</span><span class="sxs-lookup"><span data-stu-id="3b1d9-123">Example</span></span>

<span data-ttu-id="3b1d9-124">この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-124">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="3b1d9-125">`"test.xml"`「[方法: デジタル署名で XML ドキュメントに署名](how-to-sign-xml-documents-with-digital-signatures.md)する」で説明されている方法を使用して、ファイルに署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-125">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
[!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
[!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b1d9-126">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="3b1d9-126">Compiling the Code</span></span>  
  
- <span data-ttu-id="3b1d9-127">.NET Framework を対象とするプロジェクトでは、への参照を含め `System.Security.dll` ます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-127">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="3b1d9-128">.NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-128">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="3b1d9-129">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="3b1d9-130">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3b1d9-130">.NET Security</span></span>

<span data-ttu-id="3b1d9-131">非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-131">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="3b1d9-132">対称暗号化キーと非対称暗号化キーの詳細については、「 [暗号化と復号化のためのキーの生成](generating-keys-for-encryption-and-decryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-132">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="3b1d9-133">秘密キーをソース コードに直接埋め込まないでください。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-133">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="3b1d9-134">埋め込みキーは、 [Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用するか、メモ帳などのテキストエディターでアセンブリを開くことで、アセンブリから簡単に読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="3b1d9-134">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1d9-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b1d9-135">See also</span></span>

- [<span data-ttu-id="3b1d9-136">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="3b1d9-136">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="3b1d9-137">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="3b1d9-137">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="3b1d9-138">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="3b1d9-138">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="3b1d9-139">方法: デジタル署名で XML ドキュメントに署名する</span><span class="sxs-lookup"><span data-stu-id="3b1d9-139">How to: Sign XML Documents with Digital Signatures</span></span>](how-to-sign-xml-documents-with-digital-signatures.md)
- [<span data-ttu-id="3b1d9-140">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3b1d9-140">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
