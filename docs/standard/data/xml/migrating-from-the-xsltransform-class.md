---
description: '詳細情報: XslTransform クラスからの移行'
title: XslTransform クラスからの移行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 6f4a08d3448f5735b9bd9e4c418ec3613fdc6a37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713625"
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="e5e33-103">XslTransform クラスからの移行</span><span class="sxs-lookup"><span data-stu-id="e5e33-103">Migrating From the XslTransform Class</span></span>

<span data-ttu-id="e5e33-104">XSLT アーキテクチャは、Visual Studio 2005 リリースで設計が変更されました。</span><span class="sxs-lookup"><span data-stu-id="e5e33-104">The XSLT architecture was redesigned in the Visual Studio 2005 release.</span></span> <span data-ttu-id="e5e33-105"><xref:System.Xml.Xsl.XslTransform> クラスは <xref:System.Xml.Xsl.XslCompiledTransform> クラスで置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="e5e33-105">The <xref:System.Xml.Xsl.XslTransform> class was replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

<span data-ttu-id="e5e33-106">以降では、<xref:System.Xml.Xsl.XslCompiledTransform> クラスと <xref:System.Xml.Xsl.XslTransform> クラスの主な相違点について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5e33-106">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>

## <a name="performance"></a><span data-ttu-id="e5e33-107">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="e5e33-107">Performance</span></span>

<span data-ttu-id="e5e33-108"><xref:System.Xml.Xsl.XslCompiledTransform> クラスでは多くのパフォーマンスの向上が図られています。</span><span class="sxs-lookup"><span data-stu-id="e5e33-108">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="e5e33-109">新しい XSLT プロセッサは XSLT スタイル シートを、共通言語ランタイム (CLR) が他のプログラム言語で行うのと同様に、共通の中間形式にコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e5e33-109">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="e5e33-110">いったんスタイル シートがコンパイルされると、それをキャッシュして再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-110">Once the style sheet is compiled, it can be cached and reused.</span></span>

<span data-ttu-id="e5e33-111"><xref:System.Xml.Xsl.XslCompiledTransform> クラスには、このクラスを <xref:System.Xml.Xsl.XslTransform> クラスよりも大幅に高速化する他の最適化も含まれています。</span><span class="sxs-lookup"><span data-stu-id="e5e33-111">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

> [!NOTE]
> <span data-ttu-id="e5e33-112">全体的なパフォーマンスは <xref:System.Xml.Xsl.XslCompiledTransform> クラスの方が <xref:System.Xml.Xsl.XslTransform> クラスより優れていますが、<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> クラスの <xref:System.Xml.Xsl.XslCompiledTransform> メソッドが変換で初めて呼び出されたときは、<xref:System.Xml.Xsl.XslTransform.Load%2A> クラスの <xref:System.Xml.Xsl.XslTransform> メソッドよりパフォーマンスが劣る場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-112">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="e5e33-113">これは、XSLT ファイルを読み込む前にコンパイルする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="e5e33-113">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="e5e33-114">詳細については、ブログ記事「[XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)」(XslCompiledTransform は XslTransform より遅いか?) というブログ記事をお読みください。</span><span class="sxs-lookup"><span data-stu-id="e5e33-114">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>

## <a name="security"></a><span data-ttu-id="e5e33-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e5e33-115">Security</span></span>

<span data-ttu-id="e5e33-116">既定で、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでは XSLT `document()` 関数と埋め込みスクリプトのサポートが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="e5e33-116">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="e5e33-117">これらの機能を有効にするには、機能が有効になっている <xref:System.Xml.Xsl.XsltSettings> オブジェクトを作成し、それを <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e5e33-117">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="e5e33-118">スクリプト作成を有効にして XSLT 変換を実行する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="e5e33-118">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

<span data-ttu-id="e5e33-119">詳しくは、「[XSLT のセキュリティに関する考慮事項](xslt-security-considerations.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e5e33-119">For more information, see [XSLT Security Considerations](xslt-security-considerations.md).</span></span>

## <a name="new-features"></a><span data-ttu-id="e5e33-120">新機能</span><span class="sxs-lookup"><span data-stu-id="e5e33-120">New Features</span></span>

### <a name="temporary-files"></a><span data-ttu-id="e5e33-121">一時テーブル</span><span class="sxs-lookup"><span data-stu-id="e5e33-121">Temporary Files</span></span>

<span data-ttu-id="e5e33-122">XSLT の処理中に一時ファイルが生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-122">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="e5e33-123">スタイル シートにスクリプト ブロックが含まれる場合、またはデバッグ設定を true に設定してスタイル シートをコンパイルした場合、%TEMP% フォルダーに一時ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-123">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="e5e33-124">タイミングの問題で、一部の一時ファイルが削除されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-124">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="e5e33-125">たとえば、一時ファイルが現在の AppDomain やデバッガーにより使用されると、<xref:System.CodeDom.Compiler.TempFileCollection> オブジェクトの終了処理でそのファイルを削除できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-125">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>

<span data-ttu-id="e5e33-126">クライアントのすべての一時ファイルが削除されるように、<xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> プロパティを使用して追加のクリーンアップを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-126">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="e5e33-127">xsl:output 要素と XmlWriter のサポート</span><span class="sxs-lookup"><span data-stu-id="e5e33-127">Support for the xsl:output Element and XmlWriter</span></span>

<span data-ttu-id="e5e33-128">変換出力が <xref:System.Xml.Xsl.XslTransform> オブジェクトに送られる場合、`xsl:output` クラスでは <xref:System.Xml.XmlWriter> の設定が無視されていました。</span><span class="sxs-lookup"><span data-stu-id="e5e33-128">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="e5e33-129"><xref:System.Xml.Xsl.XslCompiledTransform> クラスには、スタイル シートの <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> 要素から取得された出力情報を含む <xref:System.Xml.XmlWriterSettings> オブジェクトを返す `xsl:output` プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-129">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="e5e33-130"><xref:System.Xml.XmlWriterSettings> オブジェクトを使用して、適切に設定された <xref:System.Xml.XmlWriter> オブジェクトを作成し、それを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-130">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="e5e33-131">次の C# コードに、この処理を示します。</span><span class="sxs-lookup"><span data-stu-id="e5e33-131">The following C# code illustrates this behavior:</span></span>

```csharp
// Create the XslTransform object and load the style sheet.
XslCompiledTransform xslt = new XslCompiledTransform();
xslt.Load(stylesheet);

// Load the file to transform.
XPathDocument doc = new XPathDocument(filename);

// Create the writer.
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);

// Transform the file and send the output to the console.
xslt.Transform(doc, writer);
writer.Close();
```

### <a name="debug-option"></a><span data-ttu-id="e5e33-132">デバッグ オプション</span><span class="sxs-lookup"><span data-stu-id="e5e33-132">Debug Option</span></span>

<span data-ttu-id="e5e33-133"><xref:System.Xml.Xsl.XslCompiledTransform> クラスによりデバッグ情報を生成できます。この機能を利用して、Microsoft Visual Studio デバッガーを使用してスタイル シートをデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-133">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft Visual Studio Debugger.</span></span> <span data-ttu-id="e5e33-134">詳細については、「<xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5e33-134">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="e5e33-135">動作の違い</span><span class="sxs-lookup"><span data-stu-id="e5e33-135">Behavioral Differences</span></span>

### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="e5e33-136">XmlReader への変換</span><span class="sxs-lookup"><span data-stu-id="e5e33-136">Transforming to an XmlReader</span></span>

<span data-ttu-id="e5e33-137"><xref:System.Xml.Xsl.XslTransform> クラスには、変換結果を <xref:System.Xml.XmlReader> オブジェクトとして返す Transform オーバーロードが数種類あります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-137">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="e5e33-138">このオーバーロードを使用することで、生成される XML ツリーのシリアル化と逆シリアル化によるオーバーヘッドを生じることなく、変換結果をメモり内表現 (<xref:System.Xml.XmlDocument> または <xref:System.Xml.XPath.XPathDocument>) に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-138">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="e5e33-139">次の C# コード例で、<xref:System.Xml.XmlDocument> オブジェクトに変換結果を読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e5e33-139">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<span data-ttu-id="e5e33-140"><xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、<xref:System.Xml.XmlReader> オブジェクトへの変換がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e5e33-140">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="e5e33-141">ただし、<xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> メソッドを使用して、生成される XML ツリーを <xref:System.Xml.XmlWriter> から直接読み込むことはできます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-141">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="e5e33-142">次の C# コード例では、同じタスクを <xref:System.Xml.Xsl.XslCompiledTransform> を使用して行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e5e33-142">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a><span data-ttu-id="e5e33-143">随意動作</span><span class="sxs-lookup"><span data-stu-id="e5e33-143">Discretionary Behavior</span></span>

<span data-ttu-id="e5e33-144">W3C 勧告『XSL Transformations (XSLT) Version 1.0』には、対処方法を実装者が決定できる事項があります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-144">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="e5e33-145">このような事項は、随意動作と見なされています。</span><span class="sxs-lookup"><span data-stu-id="e5e33-145">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="e5e33-146">事項によっては、<xref:System.Xml.Xsl.XslCompiledTransform> クラスと <xref:System.Xml.Xsl.XslTransform> クラスで動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-146">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="e5e33-147">詳しくは、「[XSLT エラーの解決](recoverable-xslt-errors.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e5e33-147">For more information, see [Recoverable XSLT Errors](recoverable-xslt-errors.md).</span></span>

### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="e5e33-148">拡張オブジェクトとスクリプト関数</span><span class="sxs-lookup"><span data-stu-id="e5e33-148">Extension Objects and Script Functions</span></span>

<span data-ttu-id="e5e33-149"><xref:System.Xml.Xsl.XslCompiledTransform> では、スクリプト関数の使用に関して新たに 2 つの制限が加えられています。</span><span class="sxs-lookup"><span data-stu-id="e5e33-149"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>

- <span data-ttu-id="e5e33-150">XPath 式からはパブリック メソッドのみを呼び出すことができる。</span><span class="sxs-lookup"><span data-stu-id="e5e33-150">Only public methods may be called from XPath expressions.</span></span>

- <span data-ttu-id="e5e33-151">オーバーロードは引数の数に基づいて区別される。</span><span class="sxs-lookup"><span data-stu-id="e5e33-151">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="e5e33-152">引数の数が同じオーバーロードが複数存在する場合、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="e5e33-152">If more than one overload has the same number of arguments, an exception will be raised.</span></span>

<span data-ttu-id="e5e33-153"><xref:System.Xml.Xsl.XslCompiledTransform> では、スクリプト関数へのバインド (メソッド名参照) がコンパイル時に実行されます。XslTransform を利用するスタイル シートを <xref:System.Xml.Xsl.XslCompiledTransform> によって読み込むと、例外が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5e33-153">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTransform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="e5e33-154"><xref:System.Xml.Xsl.XslCompiledTransform> では、`msxsl:using` 要素内に子要素として `msxsl:assembly` および `msxsl:script` を含めることがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-154"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="e5e33-155">`msxsl:using` 要素と `msxsl:assembly` 要素を使用して、スクリプト ブロックで使用する追加の名前空間とアセンブリを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-155">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="e5e33-156">詳しくは、「[msxsl:script を使用したスクリプト ブロック](script-blocks-using-msxsl-script.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e5e33-156">See [Script Blocks Using msxsl:script](script-blocks-using-msxsl-script.md) for more information.</span></span>

<span data-ttu-id="e5e33-157"><xref:System.Xml.Xsl.XslCompiledTransform> では、複数のオーバーロードおよびそれと同数の引数を含む拡張オブジェクトは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e5e33-157"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>

### <a name="msxml-functions"></a><span data-ttu-id="e5e33-158">MSXML 関数</span><span class="sxs-lookup"><span data-stu-id="e5e33-158">MSXML Functions</span></span>

<span data-ttu-id="e5e33-159"><xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、新しい MSXML 関数のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="e5e33-159">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="e5e33-160">新しい関数または強化された関数は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e5e33-160">The following list describes new or improved functionality:</span></span>

- <span data-ttu-id="e5e33-161">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> では、[node-set 関数](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100))の引数を結果ツリー フラグメントにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="e5e33-161">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) function to be a result tree fragment.</span></span> <span data-ttu-id="e5e33-162"><xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、この要件がありません。</span><span class="sxs-lookup"><span data-stu-id="e5e33-162">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>

- <span data-ttu-id="e5e33-163">msxsl:version:この関数は、<xref:System.Xml.Xsl.XslCompiledTransform> でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-163">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

- <span data-ttu-id="e5e33-164">XPath 拡張関数:[ms:string-compare 関数](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100))、[ms:utc 関数](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100))、[ms:namespace-uri 関数](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100))、[ms:local-name 関数](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100))、[ms:number 関数](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100))、[ms:format-date 関数](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))、[ms:format-time 関数](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100))がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e5e33-164">XPath extension functions: The [ms:string-compare Function](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), and [ms:format-time Function](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) functions are now supported.</span></span>

- <span data-ttu-id="e5e33-165">スキーマ関連 XPath 拡張機能:これらの関数は <xref:System.Xml.Xsl.XslCompiledTransform> でネイティブ サポートされません。</span><span class="sxs-lookup"><span data-stu-id="e5e33-165">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="e5e33-166">ただし、拡張関数として実装することはできます。</span><span class="sxs-lookup"><span data-stu-id="e5e33-166">However, they can be implemented as extension functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5e33-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5e33-167">See also</span></span>

- [<span data-ttu-id="e5e33-168">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="e5e33-168">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="e5e33-169">XslCompiledTransform クラスの使用</span><span class="sxs-lookup"><span data-stu-id="e5e33-169">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
