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
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>方法: デジタル署名で XML ドキュメントに署名する

<xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用すると、XML ドキュメントまたは XML ドキュメントの一部にデジタル署名で署名することができます。  XML デジタル署名 (XMLDSIG) を使用すると、データが署名後に変更されなかったことを確認できます。  XMLDSIG の基準の詳細については、World Wide Web コンソーシアム (W3C) の推奨事項「[XML 署名の構文と処理](https://www.w3.org/TR/xmldsig-core/)」を参照してください。  
  
> [!NOTE]
> この記事のコードは、Windows に適用されます。

この手順のコード例は、XML ドキュメント全体にデジタル署名する方法、および <`Signature`> 要素内のドキュメントに署名を付す方法を示しています。  この例では、RSA 署名キーを作成し、キーをセキュリティで保護されたキー コンテナーに追加してから、キーを使用して XML ドキュメントにデジタル署名しています。  キーは、XML デジタル署名を確認するために取得したり、別の XML ドキュメントの署名に使用したりすることができます。  
  
この手順を使用して作成された XML デジタル署名を確認する方法については、「[方法: XML ドキュメントのデジタル署名を検証する](how-to-verify-the-digital-signatures-of-xml-documents.md)」を参照してください。  
  
### <a name="to-digitally-sign-an-xml-document"></a>XML ドキュメントにデジタル署名するには  
  
1. <xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、キーのコンテナーの名前を指定します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して非対称キーを生成します。  <xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キーは自動的にキー コンテナーに保存されます。  このキーは、XML ドキュメントの署名に使用されます。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。  <xref:System.Xml.XmlDocument> オブジェクトには、暗号化する XML 要素が含まれています。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトを新規作成し、それに <xref:System.Xml.XmlDocument> オブジェクトを渡します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. 署名する RSA キーを <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに追加します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. 署名内容について記述する <xref:System.Security.Cryptography.Xml.Reference> オブジェクトを作成します。  ドキュメント全体に署名するには、<xref:System.Security.Cryptography.Xml.Reference.Uri%2A> プロパティを `""` に設定します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> オブジェクトを <xref:System.Security.Cryptography.Xml.Reference> オブジェクトに追加します。  変換を使用すると、検証側は、署名側が使用した方法と同一の方法で XML データを表すことができます。  XML データはさまざまな方法で表すことができるため、この手順は検証にとって重要です。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <xref:System.Security.Cryptography.Xml.Reference> オブジェクトを <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに追加します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> メソッドを呼び出して署名を計算します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. 署名の XML 表記 (<`Signature`> 要素) を取得して、新しい <xref:System.Xml.XmlElement> オブジェクトに保存します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <xref:System.Xml.XmlDocument> オブジェクトに要素を追加します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. ドキュメントを保存します。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>例  

 この例では、`test.xml` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。  次の XML を `test.xml` というファイルに配置し、この例で使用することができます。  
  
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
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
- .NET Framework を対象とするプロジェクトでは、`System.Security.dll` への参照を含めます。

- .NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml) をインストールします。
  
- 名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。  
  
## <a name="net-security"></a>.NET セキュリティ

非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。  対称および非対称暗号化キーの詳細については、「[暗号化と復号化のためのキーの生成](generating-keys-for-encryption-and-decryption.md)」を参照してください。  
  
秘密キーをソース コードに直接埋め込まないでください。  埋め込まれたキーは、[Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用するか、メモ帳などのテキスト エディターでアセンブリを開くことで、アセンブリから簡単に読み取ることができます。  
  
## <a name="see-also"></a>関連項目

- [暗号モデル](cryptography-model.md)
- [Cryptographic Services](cryptographic-services.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [方法: XML ドキュメントのデジタル署名を検証する](how-to-verify-the-digital-signatures-of-xml-documents.md)
- [ASP.NET Core データ保護](/aspnet/core/security/data-protection/introduction)
