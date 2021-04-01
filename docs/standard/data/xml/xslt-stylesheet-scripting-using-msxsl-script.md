---
description: '詳細情報: <msxsl:script> を使用した XSLT スタイルシートのスクリプト'
title: <msxsl:script> を使用した XSLT スタイルシートのスクリプト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 4ed2caf5b31fb5a6494c294b2619535699e09905
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731982"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="e50c2-103">\<msxsl:script> を使用した XSLT スタイルシートのスクリプト</span><span class="sxs-lookup"><span data-stu-id="e50c2-103">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>

<span data-ttu-id="e50c2-104"><xref:System.Xml.Xsl.XslTransform> クラスは、`script` 要素を使用した埋め込みスクリプトをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e50c2-104">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e50c2-105">.NET Framework 2.0 では <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="e50c2-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="e50c2-106"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="e50c2-107">詳しくは、「[XslCompiledTransform クラスの使用](using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](migrating-from-the-xsltransform-class.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e50c2-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="e50c2-108"><xref:System.Xml.Xsl.XslTransform> クラスは、`script` 要素を使用した埋め込みスクリプトをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e50c2-108">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="e50c2-109">スタイル シートが読み込まれると、定義されているすべての関数がクラス定義でラップされることによって Microsoft Intermediate Language (MSIL) にコンパイルされるため、パフォーマンスが低下しません。</span><span class="sxs-lookup"><span data-stu-id="e50c2-109">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="e50c2-110">`<msxsl:script>` 要素は、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-110">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="e50c2-111">`msxsl` は、名前空間 `urn:schemas-microsoft-com:xslt` に関連付けられたプレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="e50c2-111">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="e50c2-112">`language` 属性は必須ではありませんが、指定する場合は、値を `C#`、`VB`、`JScript`、`JavaScript`、`VisualBasic`、`CSharp` のいずれかにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-112">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="e50c2-113">language 属性を指定しない場合、既定の言語は JScript です。</span><span class="sxs-lookup"><span data-stu-id="e50c2-113">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="e50c2-114">`language-name` では大文字小文字が区別されないため、"JavaScript" と "javascript" は同じものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-114">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="e50c2-115">`implements-prefix` 属性は必須です。</span><span class="sxs-lookup"><span data-stu-id="e50c2-115">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="e50c2-116">この属性は、名前空間を宣言し、それをスクリプト ブロックに関連付けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-116">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="e50c2-117">この属性の値は、名前空間を表すプレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="e50c2-117">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="e50c2-118">この名前空間は、スタイル シート内の任意の場所で定義できます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-118">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="e50c2-119">`msxsl:script` 要素は名前空間 `urn:schemas-microsoft-com:xslt` に属しているため、スタイル シートには、名前空間宣言 `xmlns:msxsl=urn:schemas-microsoft-com:xslt` が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-119">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="e50c2-120">スクリプトの呼び出し元が <xref:System.Security.Permissions.SecurityPermissionFlag> へのアクセス許可を持っていない場合は、スタイル シート内のスクリプトがコンパイルされず、<xref:System.Xml.Xsl.XslTransform.Load%2A> への呼び出しが失敗します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-120">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="e50c2-121">呼び出し元が `UnmanagedCode` へのアクセス許可を持っている場合、スクリプトはコンパイルされますが、許可される操作は、読み込み時に指定される証拠によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-121">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="e50c2-122"><xref:System.Xml.XmlReader> または <xref:System.Xml.XPath.XPathNavigator> を受け取る <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドを使用してスタイル シートを読み込む場合は、<xref:System.Security.Policy.Evidence> パラメーターを引数として受け取る <xref:System.Xml.Xsl.XslTransform.Load%2A> オーバーロードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-122">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="e50c2-123">証拠を指定する場合、呼び出し元は、スクリプト アセンブリの `Evidence` を渡すための <xref:System.Security.Permissions.SecurityPermissionFlag> へのアクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-123">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="e50c2-124">呼び出し元がこのアクセス許可を持っていない場合は、`Evidence` パラメーターが `null` に設定されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-124">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="e50c2-125">その場合は、<xref:System.Xml.Xsl.XslTransform.Load%2A> 関数がスクリプトを見つけると、処理が失敗します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-125">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="e50c2-126">`ControlEvidence` へのアクセス許可は、非常に強力なアクセス権であるため、信頼性の高いコード以外に与えてはいけません。</span><span class="sxs-lookup"><span data-stu-id="e50c2-126">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="e50c2-127">アセンブリから証拠を取得するには、`this.GetType().Assembly.Evidence` を使用します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-127">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="e50c2-128">URI (Uniform Resource Identifier) から証拠を取得するには、`Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)` を使用します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-128">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="e50c2-129"><xref:System.Xml.Xsl.XslTransform.Load%2A> を受け取り、<xref:System.Xml.XmlResolver> を受け取らない `Evidence` メソッドを使う場合、アセンブリのセキュリティ ゾーンは既定で Full Trust に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-129">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="e50c2-130">詳しくは、「<xref:System.Security.SecurityZone>」および「[名前付き権限セット](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e50c2-130">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="e50c2-131">関数は、`msxsl:script` 要素内で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-131">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="e50c2-132">既定でサポートされる名前空間を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-132">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="e50c2-133">表に示す名前空間の外側でもクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-133">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="e50c2-134">ただし、これらのクラスには、完全修飾名が指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-134">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="e50c2-135">既定の名前空間</span><span class="sxs-lookup"><span data-stu-id="e50c2-135">Default Namespaces</span></span>|<span data-ttu-id="e50c2-136">説明</span><span class="sxs-lookup"><span data-stu-id="e50c2-136">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="e50c2-137">システム</span><span class="sxs-lookup"><span data-stu-id="e50c2-137">System</span></span>|<span data-ttu-id="e50c2-138">システム クラス</span><span class="sxs-lookup"><span data-stu-id="e50c2-138">System class.</span></span>|  
|<span data-ttu-id="e50c2-139">System.Collection</span><span class="sxs-lookup"><span data-stu-id="e50c2-139">System.Collection</span></span>|<span data-ttu-id="e50c2-140">コレクション クラス</span><span class="sxs-lookup"><span data-stu-id="e50c2-140">Collection classes.</span></span>|  
|<span data-ttu-id="e50c2-141">System.Text</span><span class="sxs-lookup"><span data-stu-id="e50c2-141">System.Text</span></span>|<span data-ttu-id="e50c2-142">テキスト クラス</span><span class="sxs-lookup"><span data-stu-id="e50c2-142">Text classes.</span></span>|  
|<span data-ttu-id="e50c2-143">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="e50c2-143">System.Text.RegularExpressions</span></span>|<span data-ttu-id="e50c2-144">正規表現クラス</span><span class="sxs-lookup"><span data-stu-id="e50c2-144">Regular expression classes.</span></span>|  
|<span data-ttu-id="e50c2-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="e50c2-145">System.Xml</span></span>|<span data-ttu-id="e50c2-146">コア XML クラス</span><span class="sxs-lookup"><span data-stu-id="e50c2-146">Core XML classes.</span></span>|  
|<span data-ttu-id="e50c2-147">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="e50c2-147">System.Xml.Xsl</span></span>|<span data-ttu-id="e50c2-148">XSLT クラス</span><span class="sxs-lookup"><span data-stu-id="e50c2-148">XSLT classes.</span></span>|  
|<span data-ttu-id="e50c2-149">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="e50c2-149">System.Xml.XPath</span></span>|<span data-ttu-id="e50c2-150">XPath (XML Path Language) クラス</span><span class="sxs-lookup"><span data-stu-id="e50c2-150">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="e50c2-151">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="e50c2-151">Microsoft.VisualBasic</span></span>|<span data-ttu-id="e50c2-152">Microsoft Visual Basic スクリプト用のクラス。</span><span class="sxs-lookup"><span data-stu-id="e50c2-152">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="e50c2-153">関数が宣言されると、その関数はスクリプト ブロックに含まれます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-153">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="e50c2-154">スタイル シートには、相互に独立して機能する複数のスクリプト ブロックを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-154">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="e50c2-155">このため、1 つのスクリプト ブロック内で実行しているときに、別のスクリプト ブロックで定義した関数を呼び出すことはできません。ただし、そのブロックが同じ名前空間とスクリプト言語を持つように宣言されている場合は例外です。</span><span class="sxs-lookup"><span data-stu-id="e50c2-155">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="e50c2-156">各スクリプト ブロックは独自の言語で記述でき、ブロックはその言語に対応するパーサーの文法規則に従って解析されるため、使われている言語の正しい構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-156">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="e50c2-157">たとえば、C# スクリプト ブロック内で XML コメント ノード `<!-- an XML comment -->` を使用すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-157">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="e50c2-158">スクリプト関数で定義されている引数および戻り値は、W3C (World Wide Web Consortium) XPath 型または XSLT 型のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e50c2-158">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="e50c2-159">対応する W3C 型、それと同等の .NET Framework のクラス (型)、および W3C 型が XPath 型または XSLT 型のどちらかを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-159">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="e50c2-160">型</span><span class="sxs-lookup"><span data-stu-id="e50c2-160">Type</span></span>|<span data-ttu-id="e50c2-161">対応する .NET Framework クラス (型)</span><span class="sxs-lookup"><span data-stu-id="e50c2-161">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="e50c2-162">XPath 型または XSLT 型</span><span class="sxs-lookup"><span data-stu-id="e50c2-162">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="e50c2-163">String</span><span class="sxs-lookup"><span data-stu-id="e50c2-163">String</span></span>|<span data-ttu-id="e50c2-164">System.String</span><span class="sxs-lookup"><span data-stu-id="e50c2-164">System.String</span></span>|<span data-ttu-id="e50c2-165">XPath</span><span class="sxs-lookup"><span data-stu-id="e50c2-165">XPath</span></span>|  
|<span data-ttu-id="e50c2-166">ブール型</span><span class="sxs-lookup"><span data-stu-id="e50c2-166">Boolean</span></span>|<span data-ttu-id="e50c2-167">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="e50c2-167">System.Boolean</span></span>|<span data-ttu-id="e50c2-168">XPath</span><span class="sxs-lookup"><span data-stu-id="e50c2-168">XPath</span></span>|  
|<span data-ttu-id="e50c2-169">数値</span><span class="sxs-lookup"><span data-stu-id="e50c2-169">Number</span></span>|<span data-ttu-id="e50c2-170">System.Double</span><span class="sxs-lookup"><span data-stu-id="e50c2-170">System.Double</span></span>|<span data-ttu-id="e50c2-171">XPath</span><span class="sxs-lookup"><span data-stu-id="e50c2-171">XPath</span></span>|  
|<span data-ttu-id="e50c2-172">Result Tree Fragment</span><span class="sxs-lookup"><span data-stu-id="e50c2-172">Result Tree Fragment</span></span>|<span data-ttu-id="e50c2-173">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e50c2-173">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="e50c2-174">XSLT</span><span class="sxs-lookup"><span data-stu-id="e50c2-174">XSLT</span></span>|  
|<span data-ttu-id="e50c2-175">Node Set</span><span class="sxs-lookup"><span data-stu-id="e50c2-175">Node Set</span></span>|<span data-ttu-id="e50c2-176">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="e50c2-176">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="e50c2-177">XPath</span><span class="sxs-lookup"><span data-stu-id="e50c2-177">XPath</span></span>|  
  
 <span data-ttu-id="e50c2-178">スクリプト関数が数値型Int16、UInt16、Int32、UInt32、Int64、UInt64、Single、または Decimal を使用する場合、これらの数値型は、W3C XPath 数値型に対応する Double に強制的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-178">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="e50c2-179">その他の型はすべて、`ToString` メソッドを呼び出して強制的に文字列に変換されます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-179">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="e50c2-180">スクリプト関数が上記以外の型を使用したり、スタイル シートが <xref:System.Xml.Xsl.XslTransform> オブジェクトに読み込まれるときにスクリプト関数がコンパイルを実行しなかったりすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-180">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="e50c2-181">`msxsl:script` 要素を使うときは、言語に関係なく、スクリプトを CDATA セクション内に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e50c2-181">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="e50c2-182">コードが配置されている CDATA セクションのテンプレートを示す XML の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-182">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="e50c2-183">特定の言語の演算子、識別子、または区切り記号が誤って XML として解釈される可能性があるため、スクリプトのすべての内容を CDATA セクション内に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e50c2-183">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="e50c2-184">スクリプトで論理 AND 演算子を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-184">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="e50c2-185">この例では、アンパサンドがエスケープされないため、結果として例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e50c2-185">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="e50c2-186">このドキュメントは XML として読み込まれ、`msxsl:script` 要素タグ間にあるテキストに対して特別な処理は適用されません。</span><span class="sxs-lookup"><span data-stu-id="e50c2-186">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e50c2-187">例</span><span class="sxs-lookup"><span data-stu-id="e50c2-187">Example</span></span>  

 <span data-ttu-id="e50c2-188">埋め込みスクリプトを使用して、半径が指定された円の円周を算出する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e50c2-188">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="e50c2-189">入力</span><span class="sxs-lookup"><span data-stu-id="e50c2-189">Input</span></span>  

 <span data-ttu-id="e50c2-190">number.xml</span><span class="sxs-lookup"><span data-stu-id="e50c2-190">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="e50c2-191">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="e50c2-191">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="e50c2-192">出力</span><span class="sxs-lookup"><span data-stu-id="e50c2-192">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>
```  
  
## <a name="see-also"></a><span data-ttu-id="e50c2-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="e50c2-193">See also</span></span>

- [<span data-ttu-id="e50c2-194">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="e50c2-194">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
