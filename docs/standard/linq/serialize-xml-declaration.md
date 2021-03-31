---
title: XML 宣言付きでシリアル化する - LINQ to XML
description: C# または Visual Basic で XML をシリアル化するときに、XML 宣言を生成するかどうかを制御できます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 8d25d199b149ac6aeb2aa37dc248523e79847220
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412180"
---
# <a name="serialize-with-an-xml-declaration-linq-to-xml"></a><span data-ttu-id="2f8f5-103">XML 宣言付きでシリアル化する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2f8f5-103">Serialize with an XML declaration (LINQ to XML)</span></span>

<span data-ttu-id="2f8f5-104">この記事では、C# または Visual Basic で XML をシリアル化するときに、XML 宣言を生成するかどうかを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f8f5-104">This article describes how to control whether an XML declaration is generated when you serialize XML in C# or Visual Basic.</span></span>

<span data-ttu-id="2f8f5-105"><xref:System.IO.File> メソッドまたは <xref:System.IO.TextWriter> メソッドを使用して <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> または <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> にシリアル化すると、XML 宣言が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f5-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="2f8f5-106"><xref:System.Xml.XmlWriter> にシリアル化する場合は、ライター設定 (<xref:System.Xml.XmlWriterSettings> オブジェクトで指定) により、XML 宣言が生成されるかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f5-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated.</span></span>

<span data-ttu-id="2f8f5-107">`ToString` メソッドを使用して文字列にシリアル化する場合、生成される XML には XML 宣言は含まれません。</span><span class="sxs-lookup"><span data-stu-id="2f8f5-107">If you're serializing to a string using the `ToString` method, the resulting XML won't include an XML declaration.</span></span>

## <a name="example-serialize-with-an-xml-declaration"></a><span data-ttu-id="2f8f5-108">例: XML 宣言付きでシリアル化する</span><span class="sxs-lookup"><span data-stu-id="2f8f5-108">Example: Serialize with an XML declaration</span></span>

<span data-ttu-id="2f8f5-109">次の例では、<xref:System.Xml.Linq.XElement> を作成し、ドキュメントをファイルに保存して、そのファイルをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="2f8f5-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child", "child content")
);
root.Save("Root.xml");
string str = File.ReadAllText("Root.xml");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root>
                           <Child>child content</Child>
                       </Root>
root.Save("Root.xml")
Dim str As String = File.ReadAllText("Root.xml")
Console.WriteLine(str)
```

<span data-ttu-id="2f8f5-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f5-110">This example produces the following output:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Child>child content</Child>
</Root>
```

## <a name="example-serialize-without-an-xml-declaration"></a><span data-ttu-id="2f8f5-111">例: XML 宣言なしでシリアル化する</span><span class="sxs-lookup"><span data-stu-id="2f8f5-111">Example: Serialize without an XML declaration</span></span>

<span data-ttu-id="2f8f5-112"><xref:System.Xml.Linq.XElement> を <xref:System.Xml.XmlWriter> に保存する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2f8f5-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>

```csharp
StringBuilder sb = new StringBuilder();
XmlWriterSettings xws = new XmlWriterSettings();
xws.OmitXmlDeclaration = true;

using (XmlWriter xw = XmlWriter.Create(sb, xws)) {
    XElement root = new XElement("Root",
        new XElement("Child", "child content")
    );
    root.Save(xw);
}
Console.WriteLine(sb.ToString());
```

```vb
Dim sb As StringBuilder = New StringBuilder()
Dim xws As XmlWriterSettings = New XmlWriterSettings()
xws.OmitXmlDeclaration = True

Using xw As XmlWriter = XmlWriter.Create(sb, xws)
    Dim root = <Root>
                   <Child>child content</Child>
               </Root>
    root.Save(xw)
End Using
Console.WriteLine(sb.ToString())
```

<span data-ttu-id="2f8f5-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f5-113">This example produces the following output:</span></span>

```xml
<Root><Child>child content</Child></Root>
```
