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
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>方法: 共通キーで XML 要素を復号化する

<xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化することができます。  XML の暗号化を使用すると、データが簡単に読み取られる心配をせずに機密性の高い XML を格納またはトランスポートできます。  このコード例では、Advanced Encryption Standard (AES) アルゴリズムを使用して XML 要素を復号化します。
  
 この手順を使用して XML 要素を暗号化する方法については、「[方法: 対称キーで XML 要素を暗号化する](how-to-encrypt-xml-elements-with-symmetric-keys.md)」を参照してください。  
  
 XML データの暗号化に AES のような対称アルゴリズムを使用するときは、XML データの暗号化と復号化に同じキーを使用する必要があります。  この手順の例では、暗号化された XML が同じキーを使用して暗号化されたこと、および暗号化側と復号化側で使用するアルゴリズムとキーが一致していることを前提としています。  この例では、暗号化された XML 内での AES キーの格納や暗号化は行いません。  
  
 この例は、1 つのアプリケーションが、メモリ内に格納されたセッション キーに基づいて、またはパスワードから派生した暗号強度の高いキーに基づいてデータを暗号化する必要がある状況に適しています。  複数のアプリケーションが暗号化された XML データを共有する必要がある場合は、非対称アルゴリズムまたは X.509 証明書に基づく暗号化スキームの使用を検討してください。  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>対称キーで XML 要素を復号化するには  
  
1. 「[方法: 対称キーで XML 要素を暗号化する](how-to-encrypt-xml-elements-with-symmetric-keys.md)」で説明されている手法を使用して、以前に生成されたキーで XML 要素を暗号化します。  
  
2. 暗号化された XML を含む <xref:System.Xml.XmlDocument> オブジェクトにある <`EncryptedData`> 要素 (XML 暗号化基準で定義) を検索し、その要素を表す <xref:System.Xml.XmlElement> オブジェクトを新規作成します。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. 以前に作成した <xref:System.Xml.XmlElement> オブジェクトから XML の生データを読み込んで <xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトを作成します。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <xref:System.Security.Cryptography.Xml.EncryptedXml> オブジェクトを新規作成し、これを使用して、暗号化に使用したキーと同じキーで XML データを復号化します。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. 暗号化された要素を、XML ドキュメント内の新しく復号化されたプレーンテキストの要素に置き換えます。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
- .NET Framework を対象とするプロジェクトでは、`System.Security.dll` への参照を含めます。

- .NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml) をインストールします。
  
- 名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。  
  
## <a name="net-security"></a>.NET セキュリティ
  
暗号化キーをプレーンテキストで保存したり、コンピューター間でプレーンテキストでキーを転送したりしないでください。  
  
対称暗号化キーを使用して完了したら、各バイトをゼロ (0) にするか、マネージド暗号化クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> メソッドを呼び出してメモリから消去します。  
  
## <a name="see-also"></a>関連項目

- [暗号モデル](cryptography-model.md)
- [Cryptographic Services](cryptographic-services.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [方法: 共通キーで XML 要素を暗号化する](how-to-encrypt-xml-elements-with-symmetric-keys.md)
- [ASP.NET Core データ保護](/aspnet/core/security/data-protection/introduction)
