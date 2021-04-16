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
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>方法: X.509 証明書で XML 要素を復号化する

<xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化および復号化することができます。  XML 暗号化は、データが簡単に読み取られる心配なく、暗号化された XML データを交換または保存する標準的な方法です。  XML 暗号化の規格の詳細については、<https://www.w3.org/TR/xmldsig-core/> にある World Wide Web コンソーシアム (W3C) の XML 暗号化の仕様を参照してください。  
  
 この例では、「[方法: X.509 証明書で XML 要素を暗号化する](how-to-encrypt-xml-elements-with-x-509-certificates.md)」に記載された方法を使用して暗号化された XML 要素を復号化しています。  <`EncryptedData`> 要素を検出し、要素を復号化してから、要素を元のプレーン テキストの XML 要素に置き換えます。  
  
この手順のコード例では、現在のユーザー アカウントのローカルの証明書ストアから X.509 証明書を使用して XML 要素を復号化しています。  この例では、<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドを使用して、自動的に X.509 証明書を取得します。また、<`EncryptedData`> 要素の <`EncryptedKey`> 要素に格納されたセッション キーを復号化します。  次に、<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドは、自動的にセッション キーを使用して XML 要素を復号化します。  
  
この例は、複数のアプリケーションが暗号化されたデータを共有する必要がある状況や、1 つのアプリケーションが、実行する時間の間に暗号化されたデータを保存する必要がある状況に適しています。  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>X.509 キーで XML 要素を復号化するには  
  
1. ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。  <xref:System.Xml.XmlDocument> オブジェクトには、復号化する XML 要素が含まれています。  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <xref:System.Xml.XmlDocument> オブジェクトをコンストラクターに渡して <xref:System.Security.Cryptography.Xml.EncryptedXml> オブジェクトを新規作成します。  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドを使用して XML ドキュメントを復号化します。  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <xref:System.Xml.XmlDocument> オブジェクトを保存します。  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>例

この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。  また、`"test.xml"` には `"creditcard"` 要素が含まれることも前提としています。  次の XML を `test.xml` というファイルに配置し、この例で使用することができます。  
  
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
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
- .NET Framework を対象とするプロジェクトでは、`System.Security.dll` への参照を含めます。

- .NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml) をインストールします。

- 名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。  
  
## <a name="net-security"></a>.NET セキュリティ

この例で使用される X.509 証明書は、テスト専用です。  アプリケーションでは、信頼できる証明機関によって生成された X.509 証明書を使用する必要があります。  
  
## <a name="see-also"></a>関連項目

- [暗号モデル](cryptography-model.md)
- [Cryptographic Services](cryptographic-services.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [方法: X.509 証明書で XML 要素を暗号化する](how-to-encrypt-xml-elements-with-x-509-certificates.md)
- [ASP.NET Core データ保護](/aspnet/core/security/data-protection/introduction)
