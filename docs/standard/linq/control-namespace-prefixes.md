---
title: 名前空間プレフィックスを制御する方法 - LINQ to XML
description: C# と Visual Basic で XML ツリーをシリアル化するとき、名前空間プレフィックスを制御できます。 これを行うには、名前空間を宣言する属性を挿入します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 07efc23c11cd0dc0d281968911cf24d6ecbc76a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411974"
---
# <a name="how-to-control-namespace-prefixes-linq-to-xml"></a><span data-ttu-id="5c5a0-104">名前空間プレフィックスを制御する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5c5a0-104">How to control namespace prefixes (LINQ to XML)</span></span>

<span data-ttu-id="5c5a0-105">この記事では、C# と Visual Basic で XML ツリーをシリアル化するとき、名前空間プレフィックスを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-105">This article describes how to control namespace prefixes when serializing an XML tree in C# and Visual Basic.</span></span>

<span data-ttu-id="5c5a0-106">多くの場合、名前空間プレフィックスを制御する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-106">In many situations, it's not necessary to control namespace prefixes.</span></span> <span data-ttu-id="5c5a0-107">ただし、特定の XML プログラミング ツールではそれが必要になります。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-107">However, certain XML programming tools require it.</span></span> <span data-ttu-id="5c5a0-108">たとえば、特定の名前空間プレフィックスを参照する組み込み XPath 式が含まれる XSLT スタイル シートまたは XAML ドキュメントを操作することがあります。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes.</span></span> <span data-ttu-id="5c5a0-109">その場合、そのプレフィックスでドキュメントをシリアル化することが重要です。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-109">In such a case, it's important that the document be serialized with those prefixes.</span></span> <span data-ttu-id="5c5a0-110">これは、名前空間プレフィックスを制御する一般的な理由です。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-110">This is a common reason for controlling namespace prefixes.</span></span>

<span data-ttu-id="5c5a0-111">もう 1 つの理由として、ユーザーが XML ドキュメントを手動で編集できるようにし、ユーザーにとって入力しやすい名前空間プレフィックスを作成する必要性が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-111">Another reason is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="5c5a0-112">たとえば、XSD ドキュメントを生成するとします。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-112">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="5c5a0-113">スキーマの規則では、スキーマ名前空間のプレフィックスとして `xs` または `xsd` のいずれかを使用することが推奨されています。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-113">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>

<span data-ttu-id="5c5a0-114">名前空間プレフィックスを制御するには、名前空間を宣言する属性を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-114">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="5c5a0-115">特定のプレフィックスを持つ名前空間を宣言すると、LINQ to XML はシリアル化の場合にその名前空間プレフィックスの使用を試みます。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-115">If you declare the namespaces with specific prefixes, LINQ to XML will attempt to honor the namespace prefixes when serializing.</span></span>

<span data-ttu-id="5c5a0-116">プレフィックスを持つ名前空間を宣言する属性を作成するには、属性の名前の名前空間が <xref:System.Xml.Linq.XNamespace.Xmlns%2A> で、属性の名前が名前空間プレフィックスであるような属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-116">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="5c5a0-117">属性の値は、名前空間の URI です。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-117">The value of the attribute is the URI of the namespace.</span></span>

## <a name="example-create-two-namespaces-that-have-prefixes"></a><span data-ttu-id="5c5a0-118">例: プレフィックスを持つ名前空間を 2 つ作成する</span><span class="sxs-lookup"><span data-stu-id="5c5a0-118">Example: Create two namespaces that have prefixes</span></span>

<span data-ttu-id="5c5a0-119">この例では、2 つの名前空間を宣言します。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-119">This example declares two namespaces.</span></span> <span data-ttu-id="5c5a0-120">`http://www.adventure-works.com` 名前空間にプレフィックス `aw` を指定し、`www.fourthcoffee.com` 名前空間にプレフィックス `fc` を指定します。</span><span class="sxs-lookup"><span data-stu-id="5c5a0-120">It specifies the prefix `aw` for the `http://www.adventure-works.com` namespace, and the prefix `fc` for the `www.fourthcoffee.com` namespace.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

This example produces the following output:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="5c5a0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c5a0-121">See also</span></span>

- [<span data-ttu-id="5c5a0-122">名前空間の概要</span><span class="sxs-lookup"><span data-stu-id="5c5a0-122">Namespaces overview</span></span>](namespaces-overview.md)
