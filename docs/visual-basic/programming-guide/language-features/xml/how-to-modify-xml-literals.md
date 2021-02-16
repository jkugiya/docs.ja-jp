---
description: '詳細情報: 方法:XML リテラルの変更 (Visual Basic)'
title: '方法: XML リテラルの変更'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 23b900c3da5864ac7a91e6c7a43f44a0d4ab1a21
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483613"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="66f9b-103">方法: XML リテラルの変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66f9b-103">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="66f9b-104">Visual Basic には、XML リテラルを変更する便利な方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="66f9b-104">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="66f9b-105">要素と属性を追加したり削除したりでき、既存の要素を新しい XML 要素に置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-105">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="66f9b-106">このトピックでは、既存の XML リテラルを変更する方法の例をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-106">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="66f9b-107">XML リテラルの値を変更するには</span><span class="sxs-lookup"><span data-stu-id="66f9b-107">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="66f9b-108">XML リテラルの値を変更するには、XML リテラルへの参照を取得し、`Value` プロパティを目的の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-108">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="66f9b-109">次のコード例では、XML ドキュメント内のすべての \<Price> 要素の値が更新されます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-109">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="66f9b-110">次に、このコード例のソースの XML と変更後の XML の例を示します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-110">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="66f9b-111">ソースの XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-111">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="66f9b-112">変更後の XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-112">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > <span data-ttu-id="66f9b-113">`Value` プロパティを使用して、コレクション内の最初の XML 要素を参照します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-113">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="66f9b-114">コレクション内に同じ名前の要素が複数ある場合、`Value` プロパティの設定は、コレクション内の最初の要素にのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-114">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="66f9b-115">XML リテラルに属性を追加するには</span><span class="sxs-lookup"><span data-stu-id="66f9b-115">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="66f9b-116">XML リテラルに属性を追加するには、最初に XML リテラルへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-116">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="66f9b-117">次に、新しい XML 属性軸プロパティを追加して、属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-117">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="66f9b-118">また、<xref:System.Xml.Linq.XContainer.Add%2A> メソッドを使用して、新しい <xref:System.Xml.Linq.XAttribute> オブジェクトを XML リテラルに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-118">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="66f9b-119">次の例は、両方のオプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="66f9b-119">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="66f9b-120">次に、このコード例のソースの XML と変更後の XML の例を示します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-120">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="66f9b-121">ソースの XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-121">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="66f9b-122">変更後の XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-122">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="66f9b-123">XML 属性軸プロパティの詳細については、[XML 属性軸プロパティ](../../../language-reference/xml-axis/xml-attribute-axis-property.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66f9b-123">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="66f9b-124">XML リテラルに要素を追加するには</span><span class="sxs-lookup"><span data-stu-id="66f9b-124">To add an element to an XML literal</span></span>

1. <span data-ttu-id="66f9b-125">XML リテラルに要素を追加するには、最初に XML リテラルへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-125">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="66f9b-126">次に、<xref:System.Xml.Linq.XContainer.Add%2A> メソッドを使用すると、新しい <xref:System.Xml.Linq.XElement> オブジェクトを要素の最後のサブ要素として追加できます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-126">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="66f9b-127"><xref:System.Xml.Linq.XContainer.AddFirst%2A> メソッドを使用すると、新しい <xref:System.Xml.Linq.XElement> オブジェクトを最初のサブ要素として追加できます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-127">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="66f9b-128">他のサブ要素を基準として特定の位置に新しい要素を追加するには、最初に隣接するサブ要素への参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-128">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="66f9b-129">次に、<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> メソッドを使用して、隣接するサブ要素の前に新しい <xref:System.Xml.Linq.XElement> オブジェクトを追加できます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-129">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="66f9b-130">また、<xref:System.Xml.Linq.XNode.AddAfterSelf%2A> メソッドを使用して、隣接するサブ要素の後に新しい <xref:System.Xml.Linq.XElement> オブジェクトを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-130">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="66f9b-131">次の例は、これらの各手法の例を示しています。</span><span class="sxs-lookup"><span data-stu-id="66f9b-131">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="66f9b-132">次に、このコード例のソースの XML と変更後の XML の例を示します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-132">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="66f9b-133">ソースの XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-133">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="66f9b-134">変更後の XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-134">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="66f9b-135">XML リテラルから要素または属性を削除するには</span><span class="sxs-lookup"><span data-stu-id="66f9b-135">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="66f9b-136">XML リテラルから要素または属性を削除するには、次の例に示すように、要素または属性への参照を取得し、`Remove` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-136">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="66f9b-137">次に、このコード例のソースの XML と変更後の XML の例を示します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-137">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="66f9b-138">ソースの XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-138">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    <span data-ttu-id="66f9b-139">変更後の XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-139">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    <span data-ttu-id="66f9b-140">XML リテラルからすべての要素または属性を削除するには、XML リテラルへの参照を取得し、<xref:System.Xml.Linq.XElement.RemoveAll%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-140">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="66f9b-141">XML リテラルを変更するには</span><span class="sxs-lookup"><span data-stu-id="66f9b-141">To modify an XML literal</span></span>

1. <span data-ttu-id="66f9b-142">XML 要素の名前を変更するには、最初に要素への参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-142">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="66f9b-143">次に、新しい名前を持つ新しい <xref:System.Xml.Linq.XElement> オブジェクトを作成し、この新しい <xref:System.Xml.Linq.XElement> オブジェクトを既存の <xref:System.Xml.Linq.XElement> オブジェクトの <xref:System.Xml.Linq.XNode.ReplaceWith%2A> メソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-143">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="66f9b-144">置換する要素に、保持が必要なサブ要素がある場合は、新しい <xref:System.Xml.Linq.XElement> オブジェクトの値を既存の要素の <xref:System.Xml.Linq.XContainer.Nodes%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-144">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="66f9b-145">これにより、新しい要素の値が既存の要素の内部 XML に設定されます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-145">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="66f9b-146">それ以外の場合は、新しい要素の値を、既存の要素の `Value` プロパティに設定できます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-146">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="66f9b-147">次のコード例では、すべての \<Description> 要素が \<Abstract> 要素に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-147">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="66f9b-148">\<Description> 要素の内容は、\<Description> <xref:System.Xml.Linq.XElement> オブジェクトの <xref:System.Xml.Linq.XContainer.Nodes%2A> プロパティを使用して、新しい \<Abstract> 要素に保持されます。</span><span class="sxs-lookup"><span data-stu-id="66f9b-148">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="66f9b-149">次に、このコード例のソースの XML と変更後の XML の例を示します。</span><span class="sxs-lookup"><span data-stu-id="66f9b-149">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="66f9b-150">ソースの XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-150">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
        <Description>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Description>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <Description>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="66f9b-151">変更後の XML:</span><span class="sxs-lookup"><span data-stu-id="66f9b-151">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a><span data-ttu-id="66f9b-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="66f9b-152">See also</span></span>

- [<span data-ttu-id="66f9b-153">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="66f9b-153">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="66f9b-154">XML</span><span class="sxs-lookup"><span data-stu-id="66f9b-154">XML</span></span>](index.md)
- [<span data-ttu-id="66f9b-155">方法: ファイル、文字列、またはストリームからの XML の読み込み</span><span class="sxs-lookup"><span data-stu-id="66f9b-155">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="66f9b-156">LINQ</span><span class="sxs-lookup"><span data-stu-id="66f9b-156">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="66f9b-157">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="66f9b-157">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
