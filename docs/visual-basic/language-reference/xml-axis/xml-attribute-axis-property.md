---
description: '詳細情報: XML 属性軸プロパティ (Visual Basic)'
title: XML Attribute Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 2085ef2151e7aef7c5642e0ba9ac2e6fa90bfd4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795171"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="80176-103">XML 属性軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80176-103">XML Attribute Axis Property (Visual Basic)</span></span>

<span data-ttu-id="80176-104"><xref:System.Xml.Linq.XElement> オブジェクトの属性の値または <xref:System.Xml.Linq.XElement> オブジェクト コレクションの最初の要素にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="80176-104">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80176-105">構文</span><span class="sxs-lookup"><span data-stu-id="80176-105">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="80176-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="80176-106">Parts</span></span>  

 `object`  
 <span data-ttu-id="80176-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="80176-107">Required.</span></span> <span data-ttu-id="80176-108"><xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="80176-108">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="80176-109">.@</span><span class="sxs-lookup"><span data-stu-id="80176-109">.@</span></span>  
 <span data-ttu-id="80176-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="80176-110">Required.</span></span> <span data-ttu-id="80176-111">属性軸プロパティの先頭を表します。</span><span class="sxs-lookup"><span data-stu-id="80176-111">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="80176-112">任意。</span><span class="sxs-lookup"><span data-stu-id="80176-112">Optional.</span></span> <span data-ttu-id="80176-113">Visual Basic で `attribute` が有効な識別子ではない場合に、属性の名前の先頭を表します。</span><span class="sxs-lookup"><span data-stu-id="80176-113">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="80176-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="80176-114">Required.</span></span> <span data-ttu-id="80176-115">アクセスする属性の名前。[`prefix`:]`name` の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="80176-115">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="80176-116">パーツ</span><span class="sxs-lookup"><span data-stu-id="80176-116">Part</span></span>|<span data-ttu-id="80176-117">説明</span><span class="sxs-lookup"><span data-stu-id="80176-117">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="80176-118">任意。</span><span class="sxs-lookup"><span data-stu-id="80176-118">Optional.</span></span> <span data-ttu-id="80176-119">属性の XML 名前空間プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="80176-119">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="80176-120">`Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80176-120">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="80176-121">必須です。</span><span class="sxs-lookup"><span data-stu-id="80176-121">Required.</span></span> <span data-ttu-id="80176-122">ローカル属性名。</span><span class="sxs-lookup"><span data-stu-id="80176-122">Local attribute name.</span></span> <span data-ttu-id="80176-123">「[宣言する XML 要素と属性の名前](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80176-123">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="80176-124">任意。</span><span class="sxs-lookup"><span data-stu-id="80176-124">Optional.</span></span> <span data-ttu-id="80176-125">Visual Basic で `attribute` が有効な識別子ではない場合に、属性の名前の末尾を表します。</span><span class="sxs-lookup"><span data-stu-id="80176-125">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80176-126">戻り値</span><span class="sxs-lookup"><span data-stu-id="80176-126">Return Value</span></span>  

 <span data-ttu-id="80176-127">`attribute` の値を格納する文字列。</span><span class="sxs-lookup"><span data-stu-id="80176-127">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="80176-128">属性名が存在しない場合は `Nothing` が返されます。</span><span class="sxs-lookup"><span data-stu-id="80176-128">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80176-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="80176-129">Remarks</span></span>  

 <span data-ttu-id="80176-130">XML 属性軸プロパティを使用すると、名前を指定して、<xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XElement> オブジェクト コレクションの最初の要素から属性値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="80176-130">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="80176-131">名前を使って属性値を取得することも、新しい名前の前に @ 識別子を指定して新しい属性を要素に追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="80176-131">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="80176-132">@ 識別子を使用して XML 属性を参照すると、属性値は文字列として返されるため、<xref:System.Xml.Linq.XAttribute.Value%2A> プロパティを明示的に指定する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="80176-132">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="80176-133">XML 属性の名前付けルールは、Visual Basic 識別子の名前付けルールとは異なります。</span><span class="sxs-lookup"><span data-stu-id="80176-133">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="80176-134">名前が有効な Visual Basic 識別子ではない XML 属性にアクセスするには、山かっこ (\< and >) で名前を囲みます。</span><span class="sxs-lookup"><span data-stu-id="80176-134">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="80176-135">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="80176-135">XML Namespaces</span></span>  

 <span data-ttu-id="80176-136">属性軸プロパティの名前では、`Imports` ステートメントを使用してグローバルに宣言されている XML 名前空間プレフィックスのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="80176-136">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="80176-137">XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="80176-137">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="80176-138">詳細については、「[Imports ステートメント (XML 名前空間)](../statements/imports-statement-xml-namespace.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80176-138">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80176-139">例</span><span class="sxs-lookup"><span data-stu-id="80176-139">Example</span></span>  

 <span data-ttu-id="80176-140">次の例は、`type` という名前の XML 属性の値を、`phone` という名前の XML 要素のコレクションから取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="80176-140">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="80176-141">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80176-141">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="80176-142">例</span><span class="sxs-lookup"><span data-stu-id="80176-142">Example</span></span>  

 <span data-ttu-id="80176-143">次の例は、XML 要素の属性を、宣言によって XML の一部として作成する方法と、<xref:System.Xml.Linq.XElement> オブジェクトのインスタンスに属性を追加して動的に作成する方法の両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="80176-143">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="80176-144">`type` 属性は宣言によって作成され、`owner` 属性は動的に作成されています。</span><span class="sxs-lookup"><span data-stu-id="80176-144">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="80176-145">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80176-145">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="80176-146">例</span><span class="sxs-lookup"><span data-stu-id="80176-146">Example</span></span>  

 <span data-ttu-id="80176-147">次の例では、山かっこ構文を使用して、Visual Basic の有効な識別子ではない、`number-type` という名前の XML 属性値を取得します。</span><span class="sxs-lookup"><span data-stu-id="80176-147">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="80176-148">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80176-148">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="80176-149">例</span><span class="sxs-lookup"><span data-stu-id="80176-149">Example</span></span>  

 <span data-ttu-id="80176-150">次の例では、`ns` を名前空間プレフィックスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="80176-150">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="80176-151">その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名が "`ns:name`" の最初の子ノードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="80176-151">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="80176-152">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80176-152">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="80176-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="80176-153">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="80176-154">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="80176-154">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="80176-155">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="80176-155">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="80176-156">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="80176-156">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="80176-157">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="80176-157">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
