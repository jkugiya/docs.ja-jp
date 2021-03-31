---
title: エンコードされたドキュメントを読み書きする方法 - LINQ to XML
description: XDeclaration を XML ツリーに追加して、エンコードされた XML ドキュメントを作成する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: 66d4fd5521118c76788c677efc75fcce564f0a5c
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412081"
---
# <a name="how-to-read-and-write-an-encoded-document-linq-to-xml"></a><span data-ttu-id="df9a4-103">エンコードされたドキュメントを読み書きする方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="df9a4-103">How to read and write an encoded document (LINQ to XML)</span></span>

<span data-ttu-id="df9a4-104">エンコードされた XML ドキュメントを作成するには、<xref:System.Xml.Linq.XDeclaration> を XML ツリーに追加し、エンコーディングを目的のコード ページ名に設定します。</span><span class="sxs-lookup"><span data-stu-id="df9a4-104">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>

<span data-ttu-id="df9a4-105"><xref:System.Text.Encoding.WebName%2A> から返される値はすべて有効な値です。</span><span class="sxs-lookup"><span data-stu-id="df9a4-105">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>

<span data-ttu-id="df9a4-106">エンコードされたドキュメントを読み込むと、<xref:System.Xml.Linq.XDeclaration.Encoding%2A> プロパティがコード ページ名に設定されます。</span><span class="sxs-lookup"><span data-stu-id="df9a4-106">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>

<span data-ttu-id="df9a4-107"><xref:System.Xml.Linq.XDeclaration.Encoding%2A> を有効なコード ページ名に設定すると、指定したエンコードで LINQ to XML によってシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="df9a4-107">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, LINQ to XML will serialize with the specified encoding.</span></span>

## <a name="example-create-two-documents-that-have-different-encoding-and-identify-the-encoding"></a><span data-ttu-id="df9a4-108">例: エンコードが異なる 2 つのドキュメントを作成し、エンコードを識別する</span><span class="sxs-lookup"><span data-stu-id="df9a4-108">Example: Create two documents that have different encoding and identify the encoding.</span></span>

<span data-ttu-id="df9a4-109">次の例では、UTF-8 エンコーディングのドキュメントと UTF-16 エンコーディングのドキュメントを 1 つずつ作成します。</span><span class="sxs-lookup"><span data-stu-id="df9a4-109">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="df9a4-110">次に、ドキュメントを読み込み、エンコーディングをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="df9a4-110">It then loads the documents and prints the encoding to the console.</span></span>

```csharp
Console.WriteLine("Creating a document with utf-8 encoding");
XDocument encodedDoc8 = new XDocument(
    new XDeclaration("1.0", "utf-8", "yes"),
    new XElement("Root", "Content")
);
encodedDoc8.Save("EncodedUtf8.xml");
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);
Console.WriteLine();

Console.WriteLine("Creating a document with utf-16 encoding");
XDocument encodedDoc16 = new XDocument(
    new XDeclaration("1.0", "utf-16", "yes"),
    new XElement("Root", "Content")
);
encodedDoc16.Save("EncodedUtf16.xml");
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);
Console.WriteLine();

XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");
Console.WriteLine("Encoded document:");
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));
Console.WriteLine();
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);
Console.WriteLine();

XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");
Console.WriteLine("Encoded document:");
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));
Console.WriteLine();
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);
```

```vb
Console.WriteLine("Creating a document with utf-8 encoding")
Dim encodedDoc8 As XDocument = _
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>
        <Root>Content</Root>

encodedDoc8.Save("EncodedUtf8.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)
Console.WriteLine()

Console.WriteLine("Creating a document with utf-16 encoding")
Dim encodedDoc16 As XDocument = _
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>
        <Root>Content</Root>

encodedDoc16.Save("EncodedUtf16.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)
Console.WriteLine()

Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)
Console.WriteLine()

Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)
```

<span data-ttu-id="df9a4-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="df9a4-111">This example produces the following output:</span></span>

```output
Creating a document with utf-8 encoding
Encoding is:utf-8

Creating a document with utf-16 encoding
Encoding is:utf-16

Encoded document:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-8

Encoded document:
<?xml version="1.0" encoding="utf-16" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-16
```

## <a name="see-also"></a><span data-ttu-id="df9a4-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="df9a4-112">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
