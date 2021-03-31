---
description: '詳細情報: 属性を適用する'
title: 属性の適用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET], attributes
- attributes [.NET], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 18825d3b4d6fc20b23755f58f355c783c0734041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732164"
---
# <a name="apply-attributes"></a><span data-ttu-id="83091-103">属性を適用する</span><span class="sxs-lookup"><span data-stu-id="83091-103">Apply attributes</span></span>

<span data-ttu-id="83091-104">コードの要素に属性を適用するには、次のプロセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="83091-104">Use the following process to apply an attribute to an element of your code.</span></span>

1. <span data-ttu-id="83091-105">新しい属性を定義するか、既存の .NET 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="83091-105">Define a new attribute or use an existing .NET attribute.</span></span>

2. <span data-ttu-id="83091-106">属性をコード要素の直前に記述することで、その要素に属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="83091-106">Apply the attribute to the code element by placing it immediately before the element.</span></span>

     <span data-ttu-id="83091-107">各言語には独自の属性構文があります。</span><span class="sxs-lookup"><span data-stu-id="83091-107">Each language has its own attribute syntax.</span></span> <span data-ttu-id="83091-108">C++ および C# では、属性が角かっこで囲まれ、要素とは空白で区切られます。属性と要素の間には改行を入れることもできます。</span><span class="sxs-lookup"><span data-stu-id="83091-108">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="83091-109">Visual Basic では、属性が山かっこで囲まれ、同じ論理行に記述されている必要があります。改行が必要な場合は、行連結文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="83091-109">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>

3. <span data-ttu-id="83091-110">属性に、位置指定パラメーターと名前付きパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="83091-110">Specify positional parameters and named parameters for the attribute.</span></span>

     <span data-ttu-id="83091-111">"*位置指定*" パラメーターは必須で、名前付きパラメーターの前に指定する必要があり、1 つの属性のコンストラクターのパラメーターに対応します。</span><span class="sxs-lookup"><span data-stu-id="83091-111">*Positional* parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="83091-112">"*名前付き*" パラメーターは省略可能で、属性の読み取り/書き込みプロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="83091-112">*Named* parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="83091-113">C++ と C# では、オプションのパラメーターごとに `name=value` を指定します。`name` はプロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="83091-113">In C++, and C#, specify `name=value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="83091-114">Visual Basic では、`name:=value` を指定します。</span><span class="sxs-lookup"><span data-stu-id="83091-114">In Visual Basic, specify `name:=value`.</span></span>

 <span data-ttu-id="83091-115">コードをコンパイルすると属性がメタデータに格納され、ランタイム リフレクション サービスを通じて共通言語ランタイム、すべてのカスタム ツールやアプリケーションで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="83091-115">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>

 <span data-ttu-id="83091-116">規則では、属性の名前の最後は "Attribute" にします。</span><span class="sxs-lookup"><span data-stu-id="83091-116">By convention, all attribute names end with "Attribute".</span></span> <span data-ttu-id="83091-117">ただし、Visual Basic や C# など、ランタイムを対象とする言語では、属性をフルネームで指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="83091-117">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="83091-118">たとえば、<xref:System.ObsoleteAttribute?displayProperty=nameWithType> を初期化する場合は、**Obsolete** と指定するだけで参照できます。</span><span class="sxs-lookup"><span data-stu-id="83091-118">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>

## <a name="apply-an-attribute-to-a-method"></a><span data-ttu-id="83091-119">メソッドに属性を適用する</span><span class="sxs-lookup"><span data-stu-id="83091-119">Apply an attribute to a method</span></span>

 <span data-ttu-id="83091-120">次のコードからは、コードに非推奨を指定する **System.ObsoleteAttribute** の使用方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="83091-120">The following code example shows how to use **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="83091-121">文字列 `"Will be removed in next version"` が属性に渡されます。</span><span class="sxs-lookup"><span data-stu-id="83091-121">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="83091-122">属性が記述されているコードが呼び出された時点で、渡された文字列を示すコンパイラの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83091-122">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a><span data-ttu-id="83091-123">アセンブリ レベルで属性を適用する</span><span class="sxs-lookup"><span data-stu-id="83091-123">Apply attributes at the assembly level</span></span>

 <span data-ttu-id="83091-124">アセンブリ レベルで属性を適用する場合は、キーワード `assembly` (Visual Basic では `Assembly`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="83091-124">If you want to apply an attribute at the assembly level, use the `assembly` (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="83091-125">**AssemblyTitleAttribute** をアセンブリ レベルで適用するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="83091-125">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 <span data-ttu-id="83091-126">この属性が適用されると、ファイルのメタデータ部分のアセンブリ マニフェストの中に、文字列 `"My Assembly"` が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="83091-126">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="83091-127">この属性を表示するには、[MSIL 逆アセンブラー (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用するか、または属性を取得するためのプログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="83091-127">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="83091-128">参照</span><span class="sxs-lookup"><span data-stu-id="83091-128">See also</span></span>

- [<span data-ttu-id="83091-129">属性</span><span class="sxs-lookup"><span data-stu-id="83091-129">Attributes</span></span>](index.md)
- [<span data-ttu-id="83091-130">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="83091-130">Retrieving Information Stored in Attributes</span></span>](retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="83091-131">概念</span><span class="sxs-lookup"><span data-stu-id="83091-131">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)
- [<span data-ttu-id="83091-132">属性 (C#)</span><span class="sxs-lookup"><span data-stu-id="83091-132">Attributes (C#)</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="83091-133">属性の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83091-133">Attributes overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)
