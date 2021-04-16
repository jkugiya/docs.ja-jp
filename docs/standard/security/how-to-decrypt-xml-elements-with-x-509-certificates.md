---
description: '詳細情報: 方法: X.509 証明書で XML 要素を復号化する'
title: '方法: X.509 証明書で XML 要素を復号化する'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
ms.openlocfilehash: 40006ca1d3e76dbbc0899c0c22090b27c2cfb0de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792376"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="7335f-103">方法: X.509 証明書で XML 要素を復号化する</span><span class="sxs-lookup"><span data-stu-id="7335f-103">How to: Decrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="7335f-104"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化および復号化することができます。</span><span class="sxs-lookup"><span data-stu-id="7335f-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="7335f-105">XML 暗号化は、データが簡単に読み取られる心配なく、暗号化された XML データを交換または保存する標準的な方法です。</span><span class="sxs-lookup"><span data-stu-id="7335f-105">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="7335f-106">XML 暗号化の規格の詳細については、<https://www.w3.org/TR/xmldsig-core/> にある World Wide Web コンソーシアム (W3C) の XML 暗号化の仕様を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7335f-106">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="7335f-107">この例では、「[方法: X.509 証明書で XML 要素を暗号化する](how-to-encrypt-xml-elements-with-x-509-certificates.md)」に記載された方法を使用して暗号化された XML 要素を復号化しています。</span><span class="sxs-lookup"><span data-stu-id="7335f-107">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="7335f-108"><`EncryptedData`> 要素を検出し、要素を復号化してから、要素を元のプレーン テキストの XML 要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7335f-108">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="7335f-109">この手順のコード例では、現在のユーザー アカウントのローカルの証明書ストアから X.509 証明書を使用して XML 要素を復号化しています。</span><span class="sxs-lookup"><span data-stu-id="7335f-109">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="7335f-110">この例では、<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドを使用して、自動的に X.509 証明書を取得します。また、<`EncryptedData`> 要素の <`EncryptedKey`> 要素に格納されたセッション キーを復号化します。</span><span class="sxs-lookup"><span data-stu-id="7335f-110">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="7335f-111">次に、<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドは、自動的にセッション キーを使用して XML 要素を復号化します。</span><span class="sxs-lookup"><span data-stu-id="7335f-111">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="7335f-112">この例は、複数のアプリケーションが暗号化されたデータを共有する必要がある状況や、1 つのアプリケーションが、実行する時間の間に暗号化されたデータを保存する必要がある状況に適しています。</span><span class="sxs-lookup"><span data-stu-id="7335f-112">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="7335f-113">X.509 キーで XML 要素を復号化するには</span><span class="sxs-lookup"><span data-stu-id="7335f-113">To decrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="7335f-114">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7335f-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="7335f-115"><xref:System.Xml.XmlDocument> オブジェクトには、復号化する XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7335f-115">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <span data-ttu-id="7335f-116"><xref:System.Xml.XmlDocument> オブジェクトをコンストラクターに渡して <xref:System.Security.Cryptography.Xml.EncryptedXml> オブジェクトを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="7335f-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <span data-ttu-id="7335f-117"><xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドを使用して XML ドキュメントを復号化します。</span><span class="sxs-lookup"><span data-stu-id="7335f-117">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <span data-ttu-id="7335f-118"><xref:System.Xml.XmlDocument> オブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="7335f-118">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="7335f-119">例</span><span class="sxs-lookup"><span data-stu-id="7335f-119">Example</span></span>

<span data-ttu-id="7335f-120">この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="7335f-120">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="7335f-121">また、`"test.xml"` には `"creditcard"` 要素が含まれることも前提としています。</span><span class="sxs-lookup"><span data-stu-id="7335f-121">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="7335f-122">次の XML を `test.xml` というファイルに配置し、この例で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="7335f-122">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
[!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7335f-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="7335f-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="7335f-124">.NET Framework を対象とするプロジェクトでは、`System.Security.dll` への参照を含めます。</span><span class="sxs-lookup"><span data-stu-id="7335f-124">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="7335f-125">.NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7335f-125">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>

- <span data-ttu-id="7335f-126">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="7335f-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="7335f-127">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7335f-127">.NET Security</span></span>

<span data-ttu-id="7335f-128">この例で使用される X.509 証明書は、テスト専用です。</span><span class="sxs-lookup"><span data-stu-id="7335f-128">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="7335f-129">アプリケーションでは、信頼できる証明機関によって生成された X.509 証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7335f-129">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7335f-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="7335f-130">See also</span></span>

- [<span data-ttu-id="7335f-131">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="7335f-131">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="7335f-132">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="7335f-132">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="7335f-133">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="7335f-133">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="7335f-134">方法: X.509 証明書で XML 要素を暗号化する</span><span class="sxs-lookup"><span data-stu-id="7335f-134">How to: Encrypt XML Elements with X.509 Certificates</span></span>](how-to-encrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="7335f-135">ASP.NET Core データ保護</span><span class="sxs-lookup"><span data-stu-id="7335f-135">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
