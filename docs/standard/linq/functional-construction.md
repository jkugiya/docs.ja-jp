---
title: 関数型構築 - LINQ to XML
description: LINQ to XML からは関数型構築が提供されます。この構築では、1 つのステートメントで XML ツリーを作成できます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: bcdc153d7f60cfb165dcb741d62b6af5c07a148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103365992"
---
# <a name="functional-construction-linq-to-xml"></a><span data-ttu-id="5ac74-103">関数型構築 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5ac74-103">Functional construction (LINQ to XML)</span></span>

<span data-ttu-id="5ac74-104">LINQ to XML には、"*関数型構築*" と呼ばれる強力な XML 要素作成機能があります。</span><span class="sxs-lookup"><span data-stu-id="5ac74-104">LINQ to XML provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="5ac74-105">関数型構築では、1 つのステートメントで XML ツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-105">Functional construction enables you to create an XML tree in a single statement.</span></span>

<span data-ttu-id="5ac74-106">LINQ to XML プログラミング インターフェイスの重要な機能のいくつかが関数型構築で使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-106">Several key features of the LINQ to XML programming interface are used in functional construction:</span></span>

- <span data-ttu-id="5ac74-107"><xref:System.Xml.Linq.XElement> コンストラクターは、さまざまな種類のコンテンツ引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5ac74-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="5ac74-108">たとえば、このコンストラクターに、子要素になる別の <xref:System.Xml.Linq.XElement> オブジェクトや、</span><span class="sxs-lookup"><span data-stu-id="5ac74-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="5ac74-109">要素の属性になる <xref:System.Xml.Linq.XAttribute> オブジェクトを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="5ac74-110">また、文字列に変換され、要素のテキスト コンテンツになる他の任意の種類のオブジェクトを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>
- <span data-ttu-id="5ac74-111"><xref:System.Xml.Linq.XElement> コンストラクターは、`params` 型の <xref:System.Object> 配列を受け取ります。そのため、任意の数のオブジェクトを配列に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="5ac74-112">これにより、複雑なコンテンツを持つ要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-112">This enables you to create an element that has complex content.</span></span>
- <span data-ttu-id="5ac74-113">オブジェクトが <xref:System.Collections.Generic.IEnumerable%601> を実装している場合、オブジェクト内のコレクションが列挙され、コレクション内のすべての項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="5ac74-114">コレクションに <xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XAttribute> オブジェクトが含まれている場合、コレクション内の各項目が個別に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="5ac74-115">これは重要な機能といえます。その理由は、この機能により、LINQ クエリの結果をコンストラクターに渡すことができるためです。</span><span class="sxs-lookup"><span data-stu-id="5ac74-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>

## <a name="example-create-an-xml-tree"></a><span data-ttu-id="5ac74-116">例: XML ツリーを作成する</span><span class="sxs-lookup"><span data-stu-id="5ac74-116">Example: Create an XML tree</span></span>

<span data-ttu-id="5ac74-117">関数型構築を使用し、XML ツリーを作成するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-117">You can use functional construction to write code to create an XML tree.</span></span> <span data-ttu-id="5ac74-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5ac74-118">The following is an example:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

## <a name="example-create-an-xml-tree-using-linq-query-results"></a><span data-ttu-id="5ac74-119">例: LINQ クエリの結果を利用し、XML ツリーを作成する</span><span class="sxs-lookup"><span data-stu-id="5ac74-119">Example: Create an XML tree using LINQ query results</span></span>

<span data-ttu-id="5ac74-120">次の例のように、これらの機能では、XML ツリーを作成するときに、LINQ クエリの結果を使用するコードを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-120">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

<span data-ttu-id="5ac74-121">Visual Basic では、XML リテラルで同じことをできます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-121">In Visual Basic, the same thing is accomplished with XML literals:</span></span>

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where CInt(el) > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="5ac74-122">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5ac74-122">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="5ac74-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ac74-123">See also</span></span>

- [<span data-ttu-id="5ac74-124">C# で XML ツリーを作成する</span><span class="sxs-lookup"><span data-stu-id="5ac74-124">Create XML Trees in C#</span></span>](create-xml-trees.md)
- [<span data-ttu-id="5ac74-125">Visual Basic の XML リテラル</span><span class="sxs-lookup"><span data-stu-id="5ac74-125">XML literals in Visual Basic</span></span>](xml-literals.md)
