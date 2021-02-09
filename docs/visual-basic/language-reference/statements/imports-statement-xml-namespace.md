---
description: '詳細情報: Imports ステートメント (XML 名前空間)'
title: Imports ステートメント - XML 名前空間
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 2ca285c9104c5a03b265dd15ce38a378e66d6916
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768962"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="d815b-103">Imports ステートメント (XML 名前空間)</span><span class="sxs-lookup"><span data-stu-id="d815b-103">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="d815b-104">XML リテラルおよび XML 軸プロパティで使用するために、XML 名前空間プレフィックスをインポートします。</span><span class="sxs-lookup"><span data-stu-id="d815b-104">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="d815b-105">構文</span><span class="sxs-lookup"><span data-stu-id="d815b-105">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="d815b-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="d815b-106">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="d815b-107">任意。</span><span class="sxs-lookup"><span data-stu-id="d815b-107">Optional.</span></span> <span data-ttu-id="d815b-108">XML 要素と属性で `xmlNamespaceName` を参照できる文字列。</span><span class="sxs-lookup"><span data-stu-id="d815b-108">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="d815b-109">`xmlNamespacePrefix` を指定していない場合、インポートされた XML 名前空間が既定の XML 名前空間になります。</span><span class="sxs-lookup"><span data-stu-id="d815b-109">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="d815b-110">有効な XML 識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d815b-110">Must be a valid XML identifier.</span></span> <span data-ttu-id="d815b-111">詳細については、「[宣言する XML 要素と属性の名前](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d815b-111">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="d815b-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="d815b-112">Required.</span></span> <span data-ttu-id="d815b-113">インポートされる XML 名前空間を識別する文字列。</span><span class="sxs-lookup"><span data-stu-id="d815b-113">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="d815b-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="d815b-114">Remarks</span></span>

<span data-ttu-id="d815b-115">`Imports` ステートメントを使用して、XML リテラルおよび XML 軸プロパティで、または `GetXmlNamespace` 演算子に渡されるパラメーターとして、使用できるグローバル XML 名前空間を定義できます。</span><span class="sxs-lookup"><span data-stu-id="d815b-115">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="d815b-116">(`Imports` ステートメントを使用して、コードで型名を使用する場所で使用できる別名をインポートする方法については、「[Imports ステートメント (.NET 名前空間および型)](imports-statement-net-namespace-and-type.md)」を参照してください。)`Imports` ステートメントを使用して XML 名前空間を宣言する構文は、XML で使用する構文と同じです。</span><span class="sxs-lookup"><span data-stu-id="d815b-116">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="d815b-117">そのため、XML ファイルから名前空間宣言をコピーし、それを `Imports` ステートメントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d815b-117">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="d815b-118">XML 名前空間プレフィックスは、同じ名前空間にある XML 要素を繰り返し作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="d815b-118">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="d815b-119">`Imports` ステートメントで宣言された XML 名前空間プレフィックスは、ファイル内のすべてのコードで使用できるという意味でグローバルです。</span><span class="sxs-lookup"><span data-stu-id="d815b-119">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="d815b-120">XML 要素リテラルを作成するとき、および XML 軸プロパティにアクセスするときにそれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d815b-120">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="d815b-121">詳細については、「[XML 要素リテラル](../xml-literals/xml-element-literal.md)」と「[XML 軸プロパティ](../xml-axis/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d815b-121">For more information, see [XML Element Literal](../xml-literals/xml-element-literal.md) and [XML Axis Properties](../xml-axis/index.md).</span></span>

<span data-ttu-id="d815b-122">名前空間プレフィックスを指定せずにグローバル XML 名前空間を定義した場合 (`Imports <xmlns="http://SomeNameSpace>"` など)、その名前空間は既定の XML 名前空間と見なされます。</span><span class="sxs-lookup"><span data-stu-id="d815b-122">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="d815b-123">既定の XML 名前空間は、名前空間を明示的に指定していない XML 要素リテラルまたは XML 属性軸プロパティに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d815b-123">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="d815b-124">さらに既定の名前空間は、指定された名前空間が空の名前空間 (つまり、`xmlns=""`) の場合にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="d815b-124">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="d815b-125">既定の XML 名前空間は、XML リテラルの XML 属性、または名前空間を持たない XML 属性軸プロパティには適用されません。</span><span class="sxs-lookup"><span data-stu-id="d815b-125">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="d815b-126">XML リテラルに定義されている XML 名前空間は、*ローカル XML 名前空間* と呼ばれ、`Imports` ステートメントでグローバルとして定義されている XML 名前空間よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="d815b-126">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="d815b-127">`Imports` ステートメントで定義された XML 名前空間は、Visual Basic プロジェクトにインポートされた XML 名前空間よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="d815b-127">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="d815b-128">XML リテラルで XML 名前空間を定義している場合、そのローカル名前空間は埋め込み式に適用されません。</span><span class="sxs-lookup"><span data-stu-id="d815b-128">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="d815b-129">グローバル XML 名前空間は .NET Framework 名前空間と同じスコープおよび定義ルールに従います。</span><span class="sxs-lookup"><span data-stu-id="d815b-129">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="d815b-130">そのため、.NET Framework 名前空間をインポート可能などこでも、`Imports` ステートメントを含めてグローバル XML 名前空間を定義できます。</span><span class="sxs-lookup"><span data-stu-id="d815b-130">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="d815b-131">これには、コード ファイルとプロジェクトレベルの両方でインポートされた名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d815b-131">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="d815b-132">プロジェクトレベルでインポートされた名前空間については、「[[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d815b-132">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="d815b-133">各ソース ファイルには、任意の数の `Imports` ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d815b-133">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="d815b-134">これらは、`Option Strict` ステートメントなど、オプションの宣言の後に続く必要があり、`Module` や `Class` ステートメントなどのプログラミング要素の宣言の前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d815b-134">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="d815b-135">例</span><span class="sxs-lookup"><span data-stu-id="d815b-135">Example</span></span>

<span data-ttu-id="d815b-136">次の例では、既定の XML 名前空間と、プレフィックス `ns` で識別される XML 名前空間をインポートしています。</span><span class="sxs-lookup"><span data-stu-id="d815b-136">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="d815b-137">次に、両方の名前空間を使用する XML リテラルを作成しています。</span><span class="sxs-lookup"><span data-stu-id="d815b-137">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="d815b-138">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d815b-138">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="d815b-139">例</span><span class="sxs-lookup"><span data-stu-id="d815b-139">Example</span></span>

<span data-ttu-id="d815b-140">次の例では、名前空間プレフィックス `ns` をインポートしています。</span><span class="sxs-lookup"><span data-stu-id="d815b-140">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="d815b-141">次に、名前空間プレフィックスを使用する XML リテラルを作成し、要素の最終形式を表示します。</span><span class="sxs-lookup"><span data-stu-id="d815b-141">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="d815b-142">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d815b-142">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="d815b-143">コンパイラによって、XML 名前空間プレフィックスがグローバル プレフィックスからローカル プレフィックス定義に変換されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d815b-143">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="d815b-144">例</span><span class="sxs-lookup"><span data-stu-id="d815b-144">Example</span></span>

<span data-ttu-id="d815b-145">次の例では、名前空間プレフィックス `ns` をインポートしています。</span><span class="sxs-lookup"><span data-stu-id="d815b-145">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="d815b-146">その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d815b-146">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="d815b-147">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d815b-147">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="d815b-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="d815b-148">See also</span></span>

- [<span data-ttu-id="d815b-149">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="d815b-149">XML Element Literal</span></span>](../xml-literals/xml-element-literal.md)
- [<span data-ttu-id="d815b-150">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="d815b-150">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="d815b-151">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="d815b-151">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="d815b-152">GetXmlNamespace 演算子</span><span class="sxs-lookup"><span data-stu-id="d815b-152">GetXmlNamespace Operator</span></span>](../operators/getxmlnamespace-operator.md)
