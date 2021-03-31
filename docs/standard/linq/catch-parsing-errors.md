---
title: 解析エラーをキャッチする方法 - LINQ to XML
description: XElement.Parse などのメソッドで無効な XML を解析しようとした場合、C# または Visual Basic プログラムでは、例外が発生することがあります。 そのような例外をキャッチし、それに応答するプログラムを記述できます。
ms.date: 7/20/2015
dev_langs:
- csharp
- vb
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: f7679bd5a0726c669eb47ad6ad66e0f64259264b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411975"
---
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a><span data-ttu-id="4ae73-104">解析エラーをキャッチする方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4ae73-104">How to catch parsing errors (LINQ to XML)</span></span>

<span data-ttu-id="4ae73-105">この記事では、C# または Visual Basic で、形式が正しくないか無効な XML を検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae73-105">This article shows how to detect badly formed or invalid XML in C# or Visual Basic.</span></span>

<span data-ttu-id="4ae73-106">LINQ to XML は <xref:System.Xml.XmlReader> を使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="4ae73-106">LINQ to XML is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="4ae73-107">形式が正しくない XML や無効な XML が LINQ to XML に渡されると、基になる <xref:System.Xml.XmlReader> クラスから例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4ae73-107">If badly formed or invalid XML is passed to LINQ to XML, the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="4ae73-108">XML を解析するさまざまなメソッド (<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> など) はこの例外をキャッチしません。この例外は、アプリケーションでキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="4ae73-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, don't catch the exception; the exception can then be caught by your application.</span></span>

## <a name="example-parse-invalid-xml"></a><span data-ttu-id="4ae73-109">例: 無効な XML を解析する</span><span class="sxs-lookup"><span data-stu-id="4ae73-109">Example: Parse invalid XML</span></span>

<span data-ttu-id="4ae73-110">次のコードでは、無効な XML の解析を試行します。</span><span class="sxs-lookup"><span data-stu-id="4ae73-110">The following code tries to parse invalid XML.</span></span>

```csharp
try {
    XElement contacts = XElement.Parse(
        @"<Contacts>
            <Contact>
                <Name>Jim Wilson</Name>
            </Contact>
          </Contcts>");

    Console.WriteLine(contacts);
}
catch (System.Xml.XmlException e)
{
    Console.WriteLine(e.Message);
}
```

```vb
Try
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _
        "    <Contact>" & vbCrLf & _
        "        <Name>Jim Wilson</Name>" & vbCrLf & _
        "    </Contact>" & vbCrLf & _
        "</Contcts>")

    Console.WriteLine(contacts)
Catch e As System.Xml.XmlException
    Console.WriteLine(e.Message)
End Try
```

<span data-ttu-id="4ae73-111">終了タグ `</Contcts>` が無効であるため、この例では次の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4ae73-111">Because of the invalid end tag `</Contcts>`, the example throws the following exception:</span></span>

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

<span data-ttu-id="4ae73-112"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> メソッドによってスローされる例外の詳細については、<xref:System.Xml.XmlReader> のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ae73-112">For information about the exceptions that the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ae73-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ae73-113">See also</span></span>

- [<span data-ttu-id="4ae73-114">文字列を解析する方法</span><span class="sxs-lookup"><span data-stu-id="4ae73-114">How to parse a string</span></span>](parse-string.md)
