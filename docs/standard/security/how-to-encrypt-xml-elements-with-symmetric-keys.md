---
description: '詳細情報: 方法: 対称キーで XML 要素を暗号化する'
title: '方法: 共通キーで XML 要素を暗号化する'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET], symmetric keys
- encryption [.NET], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- Advanced Encryption Standard algorithm
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: 137e1592a73ff9eb25fd6a5ba29b92c839f44575
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685115"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="a94eb-103">方法: 共通キーで XML 要素を暗号化する</span><span class="sxs-lookup"><span data-stu-id="a94eb-103">How to: Encrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="a94eb-104"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化することができます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="a94eb-105">XML の暗号化を使用すると、データが簡単に読み取られる心配をせずに機密性の高い XML を格納またはトランスポートできます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-105">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="a94eb-106">この手順では、Advanced Encryption Standard (AES) アルゴリズムを使用して XML 要素を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-106">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>  
  
 <span data-ttu-id="a94eb-107">この手順を使用して暗号化された XML 要素を復号化する方法については、「[方法: 対称キーで XML 要素を復号化する](how-to-decrypt-xml-elements-with-symmetric-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a94eb-107">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="a94eb-108">XML データの暗号化に AES のような対称アルゴリズムを使用するときは、XML データの暗号化と復号化に同じキーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a94eb-108">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="a94eb-109">この手順の例では、暗号化された XML が同じキーを使用して復号化されること、および暗号化側と復号化側で使用するアルゴリズムとキーが一致していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a94eb-109">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="a94eb-110">この例では、暗号化された XML 内での AES キーの格納や暗号化は行いません。</span><span class="sxs-lookup"><span data-stu-id="a94eb-110">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="a94eb-111">この例は、1 つのアプリケーションが、メモリ内に格納されたセッション キーに基づいて、またはパスワードから派生した暗号強度の高いキーに基づいてデータを暗号化する必要がある状況に適しています。</span><span class="sxs-lookup"><span data-stu-id="a94eb-111">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="a94eb-112">複数のアプリケーションが暗号化された XML データを共有する必要がある場合は、非対称アルゴリズムまたは X.509 証明書に基づく暗号化スキームの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a94eb-112">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="a94eb-113">対称キーで XML 要素を暗号化するには</span><span class="sxs-lookup"><span data-stu-id="a94eb-113">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="a94eb-114"><xref:System.Security.Cryptography.Aes> クラスを使用して対称キーを生成します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-114">Generate a symmetric key using the <xref:System.Security.Cryptography.Aes> class.</span></span>  <span data-ttu-id="a94eb-115">このキーは、XML 要素の暗号化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-115">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="a94eb-116">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-116">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="a94eb-117"><xref:System.Xml.XmlDocument> オブジェクトには、暗号化する XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a94eb-117">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="a94eb-118"><xref:System.Xml.XmlDocument> オブジェクトで指定された要素を検索し、暗号化する要素を表す新しい <xref:System.Xml.XmlElement> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-118">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="a94eb-119">この例では、`"creditcard"` 要素が暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-119">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="a94eb-120"><xref:System.Security.Cryptography.Xml.EncryptedXml> クラスの新しいインスタンスを作成し、これを使用して対称キーで <xref:System.Xml.XmlElement> を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-120">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="a94eb-121"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> メソッドは、暗号化された要素を、暗号化されたバイトの配列として返します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-121">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="a94eb-122"><xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトを構築し、XML 暗号化要素の URL 識別子を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-122">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="a94eb-123">この URL 識別子は、復号化側に、XML に暗号化された要素が含まれていることを知らせます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-123">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="a94eb-124"><xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> フィールドを使用して URL 識別子を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-124">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="a94eb-125">キーの生成に使用する暗号化アルゴリズムの URL 識別子に初期化された <xref:System.Security.Cryptography.Xml.EncryptionMethod> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-125">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="a94eb-126"><xref:System.Security.Cryptography.Xml.EncryptionMethod> オブジェクトを <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> プロパティに渡します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-126">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="a94eb-127">暗号化された要素のデータを <xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-127">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="a94eb-128">元の <xref:System.Xml.XmlDocument> オブジェクトの要素を <xref:System.Security.Cryptography.Xml.EncryptedData> 要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-128">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="a94eb-129">例</span><span class="sxs-lookup"><span data-stu-id="a94eb-129">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a94eb-130">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a94eb-130">Compiling the Code</span></span>  
  
- <span data-ttu-id="a94eb-131">.NET Framework を対象とするプロジェクトでは、`System.Security.dll` への参照を含めます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-131">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="a94eb-132">.NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a94eb-132">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="a94eb-133">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="a94eb-133">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="a94eb-134">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a94eb-134">.NET Security</span></span>

<span data-ttu-id="a94eb-135">暗号化キーをプレーンテキストで保存したり、コンピューター間でプレーンテキストでキーを転送したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="a94eb-135">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="a94eb-136">代わりに、セキュリティで保護されたキー コンテナーを使用して暗号化キーを格納します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-136">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
<span data-ttu-id="a94eb-137">暗号化キーを使用して完了したら、各バイトをゼロ (0) にするか、マネージド暗号化クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> メソッドを呼び出してメモリから消去します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-137">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a94eb-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="a94eb-138">See also</span></span>

- <span data-ttu-id="a94eb-139">[暗号化モデル](cryptography-model.md) - 基底クラス ライブラリに暗号化がどのように実装されているかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a94eb-139">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="a94eb-140">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="a94eb-140">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="a94eb-141">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="a94eb-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="a94eb-142">方法: 共通キーで XML 要素を復号化する</span><span class="sxs-lookup"><span data-stu-id="a94eb-142">How to: Decrypt XML Elements with Symmetric Keys</span></span>](how-to-decrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="a94eb-143">ASP.NET Core データ保護</span><span class="sxs-lookup"><span data-stu-id="a94eb-143">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
