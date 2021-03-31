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
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a>解析エラーをキャッチする方法 (LINQ to XML)

この記事では、C# または Visual Basic で、形式が正しくないか無効な XML を検出する方法について説明します。

LINQ to XML は <xref:System.Xml.XmlReader> を使用して実装されます。 形式が正しくない XML や無効な XML が LINQ to XML に渡されると、基になる <xref:System.Xml.XmlReader> クラスから例外がスローされます。 XML を解析するさまざまなメソッド (<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> など) はこの例外をキャッチしません。この例外は、アプリケーションでキャッチできます。

## <a name="example-parse-invalid-xml"></a>例: 無効な XML を解析する

次のコードでは、無効な XML の解析を試行します。

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

終了タグ `</Contcts>` が無効であるため、この例では次の例外がスローされます。

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> メソッドによってスローされる例外の詳細については、<xref:System.Xml.XmlReader> のドキュメントを参照してください。

## <a name="see-also"></a>関連項目

- [文字列を解析する方法](parse-string.md)
