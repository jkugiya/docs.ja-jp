---
description: '詳細情報: 方法: XML ドキュメントのデジタル署名を検証する'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685037"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>方法: XML ドキュメントのデジタル署名を検証する

<xref:System.Security.Cryptography.Xml> 名前空間にあるクラスを使用すると、デジタル署名で署名された XML データを検証できます。 XML デジタル署名 (XMLDSIG) を使用すると、データが署名後に変更されなかったことを確認できます。 XMLDSIG 標準の詳細については、<https://www.w3.org/TR/xmldsig-core/> の W3C (World Wide Web コンソーシアム) 仕様を参照してください。
  
> [!NOTE]
> この記事のコードは、Windows に適用されます。

この手順のコード例では、<`Signature`> 要素に格納されている XML デジタル署名の検証方法を示します。  この例では、キー コンテナーから RSA 公開キーを取得してから、キーを使用して署名を確認します。  
  
この手法を使用して検証できるデジタル署名を作成する方法については、「[方法: デジタル署名で XML ドキュメントに署名する](how-to-sign-xml-documents-with-digital-signatures.md)」を参照してください。  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>XML ドキュメントのデジタル署名を検証するには  
  
1. ドキュメントを検証するには、署名に使用した非対称キーと同じ非対称キーを使用する必要があります。  <xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、署名に使用したキー コンテナーの名前を指定します。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して公開キーを取得します。  <xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キー コンテナーからキーが名前順で自動的に読み込まれます。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。  <xref:System.Xml.XmlDocument> オブジェクトには、確認対象の署名済みの XML ドキュメントが含まています。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトを新規作成し、それに <xref:System.Xml.XmlDocument> オブジェクトを渡します。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <`signature`> 要素を検索し、<xref:System.Xml.XmlNodeList> オブジェクトを新規作成します。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. 最初の <`signature`> 要素の XML を <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに読み込みます。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> メソッドと RSA の公開キーを使用して署名を確認します。  このメソッドは、成功または失敗を示すブール値を返します。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>例

この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。  `"test.xml"` ファイルは、「[方法: デジタル署名で XML ドキュメントに署名する](how-to-sign-xml-documents-with-digital-signatures.md)」で説明する手法を使用して署名する必要があります。  
  
[!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
[!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
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
- [方法: デジタル署名で XML ドキュメントに署名する](how-to-sign-xml-documents-with-digital-signatures.md)
- [ASP.NET Core データ保護](/aspnet/core/security/data-protection/introduction)
