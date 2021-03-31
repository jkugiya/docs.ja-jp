---
description: '詳細情報: XSLT のセキュリティに関する考慮事項'
title: XSLT のセキュリティに関する考慮事項
ms.date: 03/30/2017
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: 6d233447bd9d616c72e7f6663934f44721e3f393
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782508"
---
# <a name="xslt-security-considerations"></a><span data-ttu-id="7a2a2-103">XSLT のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="7a2a2-103">XSLT Security Considerations</span></span>

<span data-ttu-id="7a2a2-104">XSLT 言語には、優れた性能と柔軟性を兼ね備えた豊富な機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-104">The XSLT language has a rich set of features that give you a great deal of power and flexibility.</span></span> <span data-ttu-id="7a2a2-105">ただし、多くの機能を利用できることが便利であると同時に、外部から不正に利用される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-105">It includes many features that, while useful, could also be exploited by outside sources.</span></span> <span data-ttu-id="7a2a2-106">XSLT を安全に使用するために、XSLT の使用に伴うさまざまなセキュリティ上の問題とそのリスクを軽減するための基本的な対策を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-106">In order to use XSLT safely, you must understand the types of security issues that arise when using XSLT, and the basic strategies that you can employ to mitigate these risks.</span></span>  
  
## <a name="xslt-extensions"></a><span data-ttu-id="7a2a2-107">XSLT 拡張機能</span><span class="sxs-lookup"><span data-stu-id="7a2a2-107">XSLT Extensions</span></span>  

 <span data-ttu-id="7a2a2-108">スタイル シート スクリプトと拡張オブジェクトの 2 つは、XSLT の一般的な拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-108">Two popular XSLT extensions are style sheet scripting and extension objects.</span></span> <span data-ttu-id="7a2a2-109">これらの拡張機能を使用すると、XSLT プロセッサでコードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-109">These extensions allow the XSLT processor to execute code.</span></span>  
  
- <span data-ttu-id="7a2a2-110">拡張オブジェクトは、XSLT にプログラミング機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-110">Extension objects add programming capabilities to XSL transformations.</span></span>  
  
- <span data-ttu-id="7a2a2-111">スクリプトは、拡張要素である `msxsl:script` 要素を使用してスタイル シートに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-111">Scripts can be embedded in the style sheet using the `msxsl:script` extension element.</span></span>  
  
### <a name="extension-objects"></a><span data-ttu-id="7a2a2-112">拡張オブジェクト</span><span class="sxs-lookup"><span data-stu-id="7a2a2-112">Extension Objects</span></span>  

 <span data-ttu-id="7a2a2-113">拡張オブジェクトは、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用して追加します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-113">Extension objects are added using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="7a2a2-114">拡張オブジェクトをサポートするには、FullTrust アクセス許可セットが必要です。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-114">The FullTrust permission set is required to support extension objects.</span></span> <span data-ttu-id="7a2a2-115">このアクセス許可セットを設定すれば、拡張オブジェクト コードの実行時にアクセス許可の昇格が起こりません。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-115">This ensures that elevation of permissions does not happen when extension object code is executed.</span></span> <span data-ttu-id="7a2a2-116">FullTrust アクセス許可なしで <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを呼び出そうとすると、セキュリティ例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-116">Attempting to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method without FullTrust permissions results in a security exception being thrown.</span></span>  
  
### <a name="style-sheet-scripts"></a><span data-ttu-id="7a2a2-117">スタイル シート スクリプト</span><span class="sxs-lookup"><span data-stu-id="7a2a2-117">Style Sheet Scripts</span></span>  

 <span data-ttu-id="7a2a2-118">スクリプトは、`msxsl:script` 拡張要素を使用してスタイル シートに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-118">Scripts can be embedded in a style sheet using the `msxsl:script` extension element.</span></span> <span data-ttu-id="7a2a2-119">スクリプトのサポートは、<xref:System.Xml.Xsl.XslCompiledTransform> クラス (既定で無効) のオプションの機能です。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-119">Script support is an optional feature on the <xref:System.Xml.Xsl.XslCompiledTransform> class that is disabled by default.</span></span> <span data-ttu-id="7a2a2-120">スクリプト機能を有効にするには、<xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> プロパティを `true` に設定して、<xref:System.Xml.Xsl.XsltSettings> オブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-120">Scripting can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="7a2a2-121">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="7a2a2-121">Guidelines</span></span>  

 <span data-ttu-id="7a2a2-122">スクリプト機能を有効にするのは、スタイル シートの作成元が信頼できる場合のみにしてください。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-122">Enable scripting only when the style sheet comes from a trusted source.</span></span> <span data-ttu-id="7a2a2-123">スタイル シートの作成元が確認できない場合、またはスタイル シートの作成元が信頼できない場合には、XSLT 設定の引数に `null` を渡してください。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-123">If you cannot verify the source of the style sheet, or if the style sheet does not come from a trusted source, pass in `null` for the XSLT settings argument.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="7a2a2-124">外部リソース</span><span class="sxs-lookup"><span data-stu-id="7a2a2-124">External Resources</span></span>  

 <span data-ttu-id="7a2a2-125">XSLT 言語には、`xsl:import`、`xsl:include`、または `document()` 関数などの機能があります。これらの機能では、プロセッサが URI リファレンスを解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-125">The XSLT language has features such as `xsl:import`, `xsl:include`, or the `document()` function, where the processor needs to resolve URI references.</span></span> <span data-ttu-id="7a2a2-126">外部リソースを解決するには、<xref:System.Xml.XmlResolver> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-126">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="7a2a2-127">外部リソースの解決が必要になる可能性があるのは、次の 2 つの場合です。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-127">External resources may need to be resolved in the following two cases:</span></span>  
  
- <span data-ttu-id="7a2a2-128">スタイル シートをコンパイルする場合には、<xref:System.Xml.XmlResolver> および `xsl:import` を解決するために `xsl:include` を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-128">When compiling a style sheet, the <xref:System.Xml.XmlResolver> is used for `xsl:import` and `xsl:include` resolution.</span></span>  
  
- <span data-ttu-id="7a2a2-129">変換を実行する場合には、<xref:System.Xml.XmlResolver> 関数を解決するために `document()` を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-129">When executing the transformation, the <xref:System.Xml.XmlResolver> is used to resolve the `document()` function.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7a2a2-130">`document()` クラスでは、<xref:System.Xml.Xsl.XslCompiledTransform> 関数は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-130">The `document()` function is disabled by default on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="7a2a2-131">この機能を有効にするには、<xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> プロパティを `true` に設定して、<xref:System.Xml.Xsl.XsltSettings> オブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-131">This feature can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
 <span data-ttu-id="7a2a2-132"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> および <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドには、<xref:System.Xml.XmlResolver> を引数の 1 つとして許容するオーバーロードがそれぞれ含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-132">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods each include overloads that accept an <xref:System.Xml.XmlResolver> as one of its arguments.</span></span> <span data-ttu-id="7a2a2-133"><xref:System.Xml.XmlResolver> を指定しない場合は、資格情報を持たない既定の <xref:System.Xml.XmlUrlResolver> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-133">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="7a2a2-134">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="7a2a2-134">Guidelines</span></span>  

 <span data-ttu-id="7a2a2-135">`document()` 関数を有効にするのは、スタイル シートの作成元が信頼できる場合のみにしてください。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-135">Enable the `document()` function only when the style sheet comes from a trusted source.</span></span>  
  
 <span data-ttu-id="7a2a2-136"><xref:System.Xml.XmlResolver> オブジェクトを使用する場合の説明を次の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-136">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="7a2a2-137">XSLT 処理で認証が必要なネットワーク リソースにアクセスする必要がある場合、必要な資格情報に対して <xref:System.Xml.XmlResolver> を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-137">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="7a2a2-138">XSLT 処理がアクセスできるリソースを制限する場合、適切なアクセス許可セットに対して <xref:System.Xml.XmlSecureResolver> を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-138">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="7a2a2-139">制御対象外の (信頼できない) リソースを開く場合には、<xref:System.Xml.XmlSecureResolver> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-139">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="7a2a2-140">動作をカスタマイズする場合は、独自の <xref:System.Xml.XmlResolver> クラスを実装し、これを使用してリソースを解決することができます。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-140">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="7a2a2-141">外部リソースにアクセスできないようにする場合は、<xref:System.Xml.XmlResolver> の引数に `null` を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a2a2-141">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a2a2-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a2a2-142">See also</span></span>

- [<span data-ttu-id="7a2a2-143">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="7a2a2-143">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="7a2a2-144">XSLT 処理中の外部リソースの解決</span><span class="sxs-lookup"><span data-stu-id="7a2a2-144">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)
- [<span data-ttu-id="7a2a2-145">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7a2a2-145">Code Access Security</span></span>](../../../framework/misc/code-access-security.md)
