---
description: '詳細情報: XML 子軸プロパティ (Visual Basic)'
title: XML Child Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 54920ebd35635f215eb6cb58867be1e4a7acd847
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768793"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="3ce00-103">XML 子軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce00-103">XML Child Axis Property (Visual Basic)</span></span>

<span data-ttu-id="3ce00-104"><xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションのいずれかの子にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3ce00-104">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce00-105">構文</span><span class="sxs-lookup"><span data-stu-id="3ce00-105">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="3ce00-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="3ce00-106">Parts</span></span>  
  
|<span data-ttu-id="3ce00-107">用語</span><span class="sxs-lookup"><span data-stu-id="3ce00-107">Term</span></span>|<span data-ttu-id="3ce00-108">定義</span><span class="sxs-lookup"><span data-stu-id="3ce00-108">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="3ce00-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="3ce00-109">Required.</span></span> <span data-ttu-id="3ce00-110"><xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="3ce00-110">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="3ce00-111">.<</span><span class="sxs-lookup"><span data-stu-id="3ce00-111">.<</span></span>|<span data-ttu-id="3ce00-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="3ce00-112">Required.</span></span> <span data-ttu-id="3ce00-113">子軸プロパティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="3ce00-113">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="3ce00-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="3ce00-114">Required.</span></span> <span data-ttu-id="3ce00-115">アクセスする子ノードの名前です。`[prefix:]name` の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="3ce00-115">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="3ce00-116">-   `Prefix` - 省略可能。</span><span class="sxs-lookup"><span data-stu-id="3ce00-116">-   `Prefix` - Optional.</span></span> <span data-ttu-id="3ce00-117">子ノードの XML 名前空間プレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="3ce00-117">XML namespace prefix for the child node.</span></span> <span data-ttu-id="3ce00-118">`Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ce00-118">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="3ce00-119">-   `Name` - 必須。</span><span class="sxs-lookup"><span data-stu-id="3ce00-119">-   `Name` - Required.</span></span> <span data-ttu-id="3ce00-120">ローカル子ノードの名前です。</span><span class="sxs-lookup"><span data-stu-id="3ce00-120">Local child node name.</span></span> <span data-ttu-id="3ce00-121">「[宣言する XML 要素と属性の名前](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ce00-121">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="3ce00-122">必須です。</span><span class="sxs-lookup"><span data-stu-id="3ce00-122">Required.</span></span> <span data-ttu-id="3ce00-123">子軸プロパティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="3ce00-123">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="3ce00-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="3ce00-124">Return Value</span></span>  

 <span data-ttu-id="3ce00-125"><xref:System.Xml.Linq.XElement> オブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="3ce00-125">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ce00-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ce00-126">Remarks</span></span>  

 <span data-ttu-id="3ce00-127">XML 子軸プロパティを使用すると、<xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションから子ノードに名前でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3ce00-127">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="3ce00-128">返されるコレクションの最初の子ノードの値にアクセスするには、XML の `Value` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ce00-128">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="3ce00-129">詳細については、「[XML Value プロパティ](xml-value-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ce00-129">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
 <span data-ttu-id="3ce00-130">Visual Basic コンパイラは、子軸プロパティを <xref:System.Xml.Linq.XContainer.Elements%2A> メソッドの呼び出しに変換します。</span><span class="sxs-lookup"><span data-stu-id="3ce00-130">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="3ce00-131">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="3ce00-131">XML Namespaces</span></span>  

 <span data-ttu-id="3ce00-132">子軸プロパティの名前では、`Imports` ステートメントでグローバルに宣言されている XML 名前空間プレフィックスのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3ce00-132">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="3ce00-133">XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="3ce00-133">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="3ce00-134">詳細については、「[Imports ステートメント (XML 名前空間)](../statements/imports-statement-xml-namespace.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ce00-134">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ce00-135">例</span><span class="sxs-lookup"><span data-stu-id="3ce00-135">Example</span></span>  

 <span data-ttu-id="3ce00-136">次の例は、`contact` オブジェクトの `phone` という名前の子ノードにアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3ce00-136">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="3ce00-137">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3ce00-137">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="3ce00-138">例</span><span class="sxs-lookup"><span data-stu-id="3ce00-138">Example</span></span>  

 <span data-ttu-id="3ce00-139">次の例は、`contacts` オブジェクトの `contact` 子軸プロパティによって返されたコレクションの、`phone` という名前の子ノードにアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3ce00-139">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="3ce00-140">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3ce00-140">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="3ce00-141">例</span><span class="sxs-lookup"><span data-stu-id="3ce00-141">Example</span></span>  

 <span data-ttu-id="3ce00-142">次の例では、`ns` を名前空間プレフィックスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="3ce00-142">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="3ce00-143">その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3ce00-143">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="3ce00-144">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3ce00-144">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="3ce00-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ce00-145">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="3ce00-146">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="3ce00-146">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="3ce00-147">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="3ce00-147">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="3ce00-148">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="3ce00-148">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="3ce00-149">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="3ce00-149">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
