---
description: '詳細情報: 方法: 対称キーで XML 要素を復号化する'
title: '方法: 共通キーで XML 要素を復号化する'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: 894b202143daf2af767fd9877266e2323e0057e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685180"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="f3dd6-103">方法: 共通キーで XML 要素を復号化する</span><span class="sxs-lookup"><span data-stu-id="f3dd6-103">How to: Decrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="f3dd6-104"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化することができます。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="f3dd6-105">XML の暗号化を使用すると、データが簡単に読み取られる心配をせずに機密性の高い XML を格納またはトランスポートできます。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-105">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="f3dd6-106">このコード例では、Advanced Encryption Standard (AES) アルゴリズムを使用して XML 要素を復号化します。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-106">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>
  
 <span data-ttu-id="f3dd6-107">この手順を使用して XML 要素を暗号化する方法については、「[方法: 対称キーで XML 要素を暗号化する](how-to-encrypt-xml-elements-with-symmetric-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-107">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="f3dd6-108">XML データの暗号化に AES のような対称アルゴリズムを使用するときは、XML データの暗号化と復号化に同じキーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-108">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="f3dd6-109">この手順の例では、暗号化された XML が同じキーを使用して暗号化されたこと、および暗号化側と復号化側で使用するアルゴリズムとキーが一致していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-109">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="f3dd6-110">この例では、暗号化された XML 内での AES キーの格納や暗号化は行いません。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-110">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="f3dd6-111">この例は、1 つのアプリケーションが、メモリ内に格納されたセッション キーに基づいて、またはパスワードから派生した暗号強度の高いキーに基づいてデータを暗号化する必要がある状況に適しています。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-111">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="f3dd6-112">複数のアプリケーションが暗号化された XML データを共有する必要がある場合は、非対称アルゴリズムまたは X.509 証明書に基づく暗号化スキームの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-112">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="f3dd6-113">対称キーで XML 要素を復号化するには</span><span class="sxs-lookup"><span data-stu-id="f3dd6-113">To decrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="f3dd6-114">「[方法: 対称キーで XML 要素を暗号化する](how-to-encrypt-xml-elements-with-symmetric-keys.md)」で説明されている手法を使用して、以前に生成されたキーで XML 要素を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-114">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2. <span data-ttu-id="f3dd6-115">暗号化された XML を含む <xref:System.Xml.XmlDocument> オブジェクトにある <`EncryptedData`> 要素 (XML 暗号化基準で定義) を検索し、その要素を表す <xref:System.Xml.XmlElement> オブジェクトを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-115">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. <span data-ttu-id="f3dd6-116">以前に作成した <xref:System.Xml.XmlElement> オブジェクトから XML の生データを読み込んで <xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-116">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <span data-ttu-id="f3dd6-117"><xref:System.Security.Cryptography.Xml.EncryptedXml> オブジェクトを新規作成し、これを使用して、暗号化に使用したキーと同じキーで XML データを復号化します。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-117">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. <span data-ttu-id="f3dd6-118">暗号化された要素を、XML ドキュメント内の新しく復号化されたプレーンテキストの要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-118">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="f3dd6-119">例</span><span class="sxs-lookup"><span data-stu-id="f3dd6-119">Example</span></span>  

 <span data-ttu-id="f3dd6-120">この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-120">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="f3dd6-121">また、`"test.xml"` には `"creditcard"` 要素が含まれることも前提としています。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-121">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="f3dd6-122">次の XML を `test.xml` というファイルに配置し、この例で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-122">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3dd6-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f3dd6-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="f3dd6-124">.NET Framework を対象とするプロジェクトでは、`System.Security.dll` への参照を含めます。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-124">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="f3dd6-125">.NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-125">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="f3dd6-126">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="f3dd6-127">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f3dd6-127">.NET Security</span></span>
  
<span data-ttu-id="f3dd6-128">暗号化キーをプレーンテキストで保存したり、コンピューター間でプレーンテキストでキーを転送したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-128">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
<span data-ttu-id="f3dd6-129">対称暗号化キーを使用して完了したら、各バイトをゼロ (0) にするか、マネージド暗号化クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> メソッドを呼び出してメモリから消去します。</span><span class="sxs-lookup"><span data-stu-id="f3dd6-129">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dd6-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3dd6-130">See also</span></span>

- [<span data-ttu-id="f3dd6-131">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="f3dd6-131">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="f3dd6-132">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="f3dd6-132">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="f3dd6-133">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="f3dd6-133">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="f3dd6-134">方法: 共通キーで XML 要素を暗号化する</span><span class="sxs-lookup"><span data-stu-id="f3dd6-134">How to: Encrypt XML Elements with Symmetric Keys</span></span>](how-to-encrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="f3dd6-135">ASP.NET Core データ保護</span><span class="sxs-lookup"><span data-stu-id="f3dd6-135">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
