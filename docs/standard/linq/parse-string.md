---
title: 文字列を解析する方法 - LINQ to XML
description: XElement.Parse を使用して文字列を解析し、C# および Visual Basic で XML ツリーを作成し、Visual Basic で XML リテラルを使用して XML ツリーを作成することができます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: f4bd22acbf3b11d801c791cc591d882810450fd4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412185"
---
# <a name="how-to-parse-a-string-linq-to-xml"></a><span data-ttu-id="cb212-103">文字列を解析する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cb212-103">How to parse a string (LINQ to XML)</span></span>

<span data-ttu-id="cb212-104">この記事では、文字列を解析して C# および Visual Basic で XML ツリーを作成する方法について示します。</span><span class="sxs-lookup"><span data-stu-id="cb212-104">This article shows how to parse a string to create an XML tree in C# and in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="cb212-105">例</span><span class="sxs-lookup"><span data-stu-id="cb212-105">Example</span></span>

<span data-ttu-id="cb212-106">次の C# コードは、XML 文字列を解析する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb212-106">The following C# code shows how to parse an XML string:</span></span>

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

<span data-ttu-id="cb212-107">Visual Basic でも同様の方法で文字列を解析できます。</span><span class="sxs-lookup"><span data-stu-id="cb212-107">You can parse a string in Visual Basic in a similar manner.</span></span> <span data-ttu-id="cb212-108">しかし、次のコードに示すように XML リテラルを使用する方が効率的です。これは、XML リテラルでは、文字列から XML を解析する場合のようなパフォーマンスの低下がないためです。</span><span class="sxs-lookup"><span data-stu-id="cb212-108">However, it's more efficient to use XML literals, as shown in following code, because XML literals don't suffer from the same performance penalties as parsing XML from a string.</span></span>

<span data-ttu-id="cb212-109">XML リテラルを使用すると、XML を Visual Basic プログラムに単にコピーして貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="cb212-109">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>

> [!NOTE]
> <span data-ttu-id="cb212-110">テキストの解析やテキスト ファイルからの XML ドキュメントの読み込みは、関数型構築より非効率です。</span><span class="sxs-lookup"><span data-stu-id="cb212-110">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="cb212-111">XML ツリーをコードから初期化する場合、関数型構築を使用するプロセッサ時間は、テキストを解析するよりも短くなります。</span><span class="sxs-lookup"><span data-stu-id="cb212-111">If you're initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>

```vb
Dim contacts as XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="home">206-555-0144</Phone>
            <Phone Type="work">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type="mobile">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>
```

<span data-ttu-id="cb212-112">ルート `Contacts` ノードには、2 つの `Contact` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="cb212-112">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="cb212-113">解析された XML 内の特定のデータにアクセスするには、[XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) メソッドを使用します。この例では、ルート `Contacts` ノードの子要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="cb212-113">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="cb212-114">次の例では、最初の `Contact` ノードをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="cb212-114">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

```vb
Dim contactNodes As List(Of XElement) = contacts.Elements("Contact").ToList()
Console.WriteLine(contactNodes(0))
```

## <a name="see-also"></a><span data-ttu-id="cb212-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb212-115">See also</span></span>

- [<span data-ttu-id="cb212-116">特定の属性を持つ要素を検索する方法</span><span class="sxs-lookup"><span data-stu-id="cb212-116">How to find an element with a specific attribute</span></span>](find-element-specific-attribute.md)
