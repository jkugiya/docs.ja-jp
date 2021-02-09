---
description: '詳細情報: XML 要素リテラル (Visual Basic)'
title: XML 要素リテラル
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: dfc78beded5c6f472b67fa272835ef0aa29d0187
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787540"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="528f9-103">XML 要素リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="528f9-103">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="528f9-104"><xref:System.Xml.Linq.XElement> オブジェクトを表すリテラル。</span><span class="sxs-lookup"><span data-stu-id="528f9-104">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="528f9-105">構文</span><span class="sxs-lookup"><span data-stu-id="528f9-105">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="528f9-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="528f9-106">Parts</span></span>

- `<`

  <span data-ttu-id="528f9-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="528f9-107">Required.</span></span> <span data-ttu-id="528f9-108">開始要素タグを開きます。</span><span class="sxs-lookup"><span data-stu-id="528f9-108">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="528f9-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="528f9-109">Required.</span></span> <span data-ttu-id="528f9-110">要素名</span><span class="sxs-lookup"><span data-stu-id="528f9-110">Name of the element.</span></span> <span data-ttu-id="528f9-111">形式は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="528f9-111">The format is one of the following:</span></span>

  - <span data-ttu-id="528f9-112">要素名のリテラル テキスト。`[ePrefix:]eName` の形式で指定します。各項目の内容を次に示します。</span><span class="sxs-lookup"><span data-stu-id="528f9-112">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="528f9-113">パーツ</span><span class="sxs-lookup"><span data-stu-id="528f9-113">Part</span></span>|<span data-ttu-id="528f9-114">説明</span><span class="sxs-lookup"><span data-stu-id="528f9-114">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="528f9-115">任意。</span><span class="sxs-lookup"><span data-stu-id="528f9-115">Optional.</span></span> <span data-ttu-id="528f9-116">要素の XML 名前空間プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="528f9-116">XML namespace prefix for the element.</span></span> <span data-ttu-id="528f9-117">ファイル内またはプロジェクト レベルで `Imports` ステートメントで定義されたグローバル XML 名前空間か、この要素または親要素で定義されたローカル XML 名前空間である必要があります。</span><span class="sxs-lookup"><span data-stu-id="528f9-117">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="528f9-118">必須です。</span><span class="sxs-lookup"><span data-stu-id="528f9-118">Required.</span></span> <span data-ttu-id="528f9-119">要素名</span><span class="sxs-lookup"><span data-stu-id="528f9-119">Name of the element.</span></span> <span data-ttu-id="528f9-120">形式は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="528f9-120">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="528f9-121">- リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="528f9-121">- Literal text.</span></span> <span data-ttu-id="528f9-122">「[宣言する XML 要素と属性の名前](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="528f9-123">- `<%= eNameExp %>` 形式の埋め込み式。</span><span class="sxs-lookup"><span data-stu-id="528f9-123">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="528f9-124">`eNameExp` の型は `String` か、暗黙的に <xref:System.Xml.Linq.XName> に変換可能な型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="528f9-124">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="528f9-125">`<%= nameExp %>` 形式の埋め込み式。</span><span class="sxs-lookup"><span data-stu-id="528f9-125">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="528f9-126">`nameExp` の型は `String` か、暗黙的に <xref:System.Xml.Linq.XName> に変換可能な型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="528f9-126">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="528f9-127">埋め込み式は、要素の終了タグでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="528f9-127">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="528f9-128">任意。</span><span class="sxs-lookup"><span data-stu-id="528f9-128">Optional.</span></span> <span data-ttu-id="528f9-129">リテラルで宣言された属性のリスト。</span><span class="sxs-lookup"><span data-stu-id="528f9-129">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="528f9-130">各 `attribute` の構文は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="528f9-130">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="528f9-131">属性割り当て。`[aPrefix:]aName=aValue` の形式で指定します。各項目の内容を次に示します。</span><span class="sxs-lookup"><span data-stu-id="528f9-131">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="528f9-132">パーツ</span><span class="sxs-lookup"><span data-stu-id="528f9-132">Part</span></span>|<span data-ttu-id="528f9-133">説明</span><span class="sxs-lookup"><span data-stu-id="528f9-133">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="528f9-134">任意。</span><span class="sxs-lookup"><span data-stu-id="528f9-134">Optional.</span></span> <span data-ttu-id="528f9-135">属性の XML 名前空間プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="528f9-135">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="528f9-136">`Imports` ステートメントで定義されたグローバル XML 名前空間か、この要素または親要素で定義されたローカル XML 名前空間である必要があります。</span><span class="sxs-lookup"><span data-stu-id="528f9-136">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="528f9-137">必須です。</span><span class="sxs-lookup"><span data-stu-id="528f9-137">Required.</span></span> <span data-ttu-id="528f9-138">属性の名前。</span><span class="sxs-lookup"><span data-stu-id="528f9-138">Name of the attribute.</span></span> <span data-ttu-id="528f9-139">形式は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="528f9-139">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="528f9-140">- リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="528f9-140">- Literal text.</span></span> <span data-ttu-id="528f9-141">「[宣言する XML 要素と属性の名前](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-141">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="528f9-142">- `<%= aNameExp %>` 形式の埋め込み式。</span><span class="sxs-lookup"><span data-stu-id="528f9-142">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="528f9-143">`aNameExp` の型は `String` か、暗黙的に <xref:System.Xml.Linq.XName> に変換可能な型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="528f9-143">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="528f9-144">任意。</span><span class="sxs-lookup"><span data-stu-id="528f9-144">Optional.</span></span> <span data-ttu-id="528f9-145">属性の値。</span><span class="sxs-lookup"><span data-stu-id="528f9-145">Value of the attribute.</span></span> <span data-ttu-id="528f9-146">形式は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="528f9-146">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="528f9-147">- 引用符で囲まれたリテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="528f9-147">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="528f9-148">- `<%= aValueExp %>` 形式の埋め込み式。</span><span class="sxs-lookup"><span data-stu-id="528f9-148">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="528f9-149">任意の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="528f9-149">Any type is allowed.</span></span>|

  - <span data-ttu-id="528f9-150">`<%= aExp %>` 形式の埋め込み式。</span><span class="sxs-lookup"><span data-stu-id="528f9-150">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="528f9-151">任意。</span><span class="sxs-lookup"><span data-stu-id="528f9-151">Optional.</span></span> <span data-ttu-id="528f9-152">コンテンツのない空の要素であることを示します。</span><span class="sxs-lookup"><span data-stu-id="528f9-152">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="528f9-153">必須です。</span><span class="sxs-lookup"><span data-stu-id="528f9-153">Required.</span></span> <span data-ttu-id="528f9-154">開始タグまたは空の要素タグを終了します。</span><span class="sxs-lookup"><span data-stu-id="528f9-154">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="528f9-155">任意。</span><span class="sxs-lookup"><span data-stu-id="528f9-155">Optional.</span></span> <span data-ttu-id="528f9-156">要素のコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="528f9-156">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="528f9-157">各 `content` に次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="528f9-157">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="528f9-158">リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="528f9-158">Literal text.</span></span> <span data-ttu-id="528f9-159">リテラル テキストがある場合、`elementContents` のすべての空白が有意になります。</span><span class="sxs-lookup"><span data-stu-id="528f9-159">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="528f9-160">`<%= contentExp %>` 形式の埋め込み式。</span><span class="sxs-lookup"><span data-stu-id="528f9-160">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="528f9-161">XML 要素リテラル。</span><span class="sxs-lookup"><span data-stu-id="528f9-161">XML element literal.</span></span>

  - <span data-ttu-id="528f9-162">XML コメント リテラル。</span><span class="sxs-lookup"><span data-stu-id="528f9-162">XML comment literal.</span></span> <span data-ttu-id="528f9-163">「[XML コメント リテラル](xml-comment-literal.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-163">See [XML Comment Literal](xml-comment-literal.md).</span></span>

  - <span data-ttu-id="528f9-164">XML 処理命令リテラル。</span><span class="sxs-lookup"><span data-stu-id="528f9-164">XML processing instruction literal.</span></span> <span data-ttu-id="528f9-165">「[XML 処理命令リテラル](xml-processing-instruction-literal.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-165">See [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="528f9-166">XML CDATA リテラル。</span><span class="sxs-lookup"><span data-stu-id="528f9-166">XML CDATA literal.</span></span> <span data-ttu-id="528f9-167">「[XML CDATA リテラル](xml-cdata-literal.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-167">See [XML CDATA Literal](xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="528f9-168">任意。</span><span class="sxs-lookup"><span data-stu-id="528f9-168">Optional.</span></span> <span data-ttu-id="528f9-169">要素の終了タグを表します。</span><span class="sxs-lookup"><span data-stu-id="528f9-169">Represents the closing tag for the element.</span></span> <span data-ttu-id="528f9-170">埋め込み式の結果である場合、省略可能な `name` パラメーターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="528f9-170">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="528f9-171">戻り値</span><span class="sxs-lookup"><span data-stu-id="528f9-171">Return Value</span></span>

<span data-ttu-id="528f9-172"><xref:System.Xml.Linq.XElement> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="528f9-172">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="528f9-173">Remarks</span><span class="sxs-lookup"><span data-stu-id="528f9-173">Remarks</span></span>

<span data-ttu-id="528f9-174">XML 要素リテラル構文を使用して、コード内に <xref:System.Xml.Linq.XElement> オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="528f9-174">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="528f9-175">XML リテラルは、行連結文字を使用せずに、複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="528f9-175">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="528f9-176">この機能を使用すると、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="528f9-176">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="528f9-177">`<%= exp %>` 形式の埋め込み式を使用すると、XML 要素リテラルに動的な情報を追加できます。</span><span class="sxs-lookup"><span data-stu-id="528f9-177">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="528f9-178">詳細については、「[XML での埋め込み式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-178">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="528f9-179">XML 要素リテラルは、Visual Basic コンパイラによって、<xref:System.Xml.Linq.XElement.%23ctor%2A> コンストラクターへの呼び出しに変換されます。また、必要に応じて、<xref:System.Xml.Linq.XAttribute.%23ctor%2A> コンストラクターへの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="528f9-179">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="528f9-180">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="528f9-180">XML Namespaces</span></span>

<span data-ttu-id="528f9-181">XML 名前空間プレフィックスは、コード内で同じ名前空間の要素を使用して XML リテラルを何度も作成する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="528f9-181">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="528f9-182">グローバル XML 名前空間プレフィックス (`Imports` ステートメントを使用して定義) またはローカル プレフィックス (`xmlns:xmlPrefix="xmlNamespace"` 属性構文を使用して定義) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="528f9-182">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="528f9-183">詳細については、「[Imports ステートメント (XML 名前空間)](../statements/imports-statement-xml-namespace.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-183">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="528f9-184">XML 名前空間のスコープ規則に従って、ローカル プレフィックスはグローバル プレフィックスよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="528f9-184">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="528f9-185">ただし、XML リテラルで XML 名前空間が定義されている場合、その名前空間は、埋め込み式に出現する式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="528f9-185">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="528f9-186">埋め込み式は、グローバル XML 名前空間だけにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="528f9-186">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="528f9-187">XML リテラルで使用されているグローバル XML 名前空間はそれぞれ、Visual Basic コンパイラによって生成されたコード内では、1 つのローカル名前空間定義に変換されます。</span><span class="sxs-lookup"><span data-stu-id="528f9-187">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="528f9-188">使用されていないグローバル XML 名前空間は、生成されたコードに表示されません。</span><span class="sxs-lookup"><span data-stu-id="528f9-188">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="528f9-189">例</span><span class="sxs-lookup"><span data-stu-id="528f9-189">Example</span></span>

<span data-ttu-id="528f9-190">次の例は、入れ子にされた 2 つの空の要素が含まれる、シンプルな XML 要素を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="528f9-190">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="528f9-191">この例では、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="528f9-191">The example displays the following text.</span></span> <span data-ttu-id="528f9-192">リテラルでは空の要素の構造が保持されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-192">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="528f9-193">例</span><span class="sxs-lookup"><span data-stu-id="528f9-193">Example</span></span>

<span data-ttu-id="528f9-194">次の例は、埋め込み式を使用して要素に名前を付けて、属性を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="528f9-194">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="528f9-195">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="528f9-195">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="528f9-196">例</span><span class="sxs-lookup"><span data-stu-id="528f9-196">Example</span></span>

<span data-ttu-id="528f9-197">次の例では、`ns` を名前空間プレフィックスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="528f9-197">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="528f9-198">その後、名前空間のプレフィックスを使用して XML リテラルを作成し、要素の最終形式を表示します。</span><span class="sxs-lookup"><span data-stu-id="528f9-198">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="528f9-199">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="528f9-199">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="528f9-200">コンパイラによって、グローバル XML 名前空間のプレフィックスが、XML 名前空間のプレフィックス定義に変換されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="528f9-200">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="528f9-201">\<ns:middle> 要素により、\<ns:inner1> 要素の XML 名前空間プレフィックスが再定義されます。</span><span class="sxs-lookup"><span data-stu-id="528f9-201">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="528f9-202">ただし、\<ns:inner2> 要素では、`Imports` ステートメントで定義された名前空間が使用されます。</span><span class="sxs-lookup"><span data-stu-id="528f9-202">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="528f9-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="528f9-203">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="528f9-204">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="528f9-204">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="528f9-205">XML コメント リテラル</span><span class="sxs-lookup"><span data-stu-id="528f9-205">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="528f9-206">XML CDATA リテラル</span><span class="sxs-lookup"><span data-stu-id="528f9-206">XML CDATA Literal</span></span>](xml-cdata-literal.md)
- [<span data-ttu-id="528f9-207">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="528f9-207">XML Literals</span></span>](index.md)
- [<span data-ttu-id="528f9-208">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="528f9-208">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="528f9-209">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="528f9-209">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="528f9-210">Imports ステートメント (XML 名前空間)</span><span class="sxs-lookup"><span data-stu-id="528f9-210">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
