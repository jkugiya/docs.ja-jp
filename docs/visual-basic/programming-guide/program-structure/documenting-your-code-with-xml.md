---
description: '詳細情報: XML の使用によるコードのドキュメントの作成 (Visual Basic)'
title: XML の使用によるコードのドキュメントの作成
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: b554007bdd5183d0d92dc7ff62d08885f4b7f486
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476008"
---
# <a name="document-your-code-with-xml-visual-basic"></a><span data-ttu-id="c4319-103">XML の使用によるコードのドキュメントの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4319-103">Document your code with XML (Visual Basic)</span></span>

<span data-ttu-id="c4319-104">Visual Basic では、XML を使用してコードを文書化できます。</span><span class="sxs-lookup"><span data-stu-id="c4319-104">In Visual Basic, you can document your code using XML.</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="c4319-105">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="c4319-105">XML documentation comments</span></span>

<span data-ttu-id="c4319-106">Visual Basic には、プロジェクトの XML ドキュメントを自動的に作成する簡単な方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c4319-106">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="c4319-107">型とメンバーの XML スケルトンを自動的に生成し、概要、各パラメーターの説明ドキュメント、その他の注釈を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c4319-107">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="c4319-108">適切な設定により、XML ドキュメントは、ご利用のプロジェクトと同じルート ファイル名を使用して XML ファイルに自動的に出力されます。</span><span class="sxs-lookup"><span data-stu-id="c4319-108">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same root file name as your project.</span></span> <span data-ttu-id="c4319-109">詳細については、「[-doc](../../reference/command-line-compiler/doc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4319-109">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="c4319-110">XML ファイルは、XML として使用したり、操作したりできます。</span><span class="sxs-lookup"><span data-stu-id="c4319-110">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="c4319-111">このファイルは、プロジェクトの出力 .exe または .dll ファイルと同じディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="c4319-111">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="c4319-112">XML ドキュメントは `'''` で始まります。</span><span class="sxs-lookup"><span data-stu-id="c4319-112">XML documentation starts with `'''`.</span></span> <span data-ttu-id="c4319-113">これらのコメントの処理にはいくつか制限があります。</span><span class="sxs-lookup"><span data-stu-id="c4319-113">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="c4319-114">ドキュメントは整形式の XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4319-114">The documentation must be well-formed XML.</span></span> <span data-ttu-id="c4319-115">XML が整形式ではない場合は、警告が生成され、エラーが発生したことを示すコメントがドキュメント ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4319-115">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="c4319-116">開発者は、独自のタグ セットを自由に作成できます。</span><span class="sxs-lookup"><span data-stu-id="c4319-116">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="c4319-117">推奨されるタグのセットがあります ([XML のコメント用タグ](../../language-reference/xmldoc/index.md)に関するページを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="c4319-117">There is a recommended set of tags (see [XML Comment Tags](../../language-reference/xmldoc/index.md)).</span></span> <span data-ttu-id="c4319-118">推奨されるタグの一部には特別な意味があります。</span><span class="sxs-lookup"><span data-stu-id="c4319-118">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="c4319-119">\<param> タグは、パラメーターの記述に使用します。</span><span class="sxs-lookup"><span data-stu-id="c4319-119">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="c4319-120">このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4319-120">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="c4319-121">検証が失敗すると、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="c4319-121">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="c4319-122">`cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="c4319-122">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="c4319-123">コンパイラは、このコード要素が存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4319-123">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="c4319-124">検証が失敗すると、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="c4319-124">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="c4319-125">また、コンパイラは、`cref` 属性で記述されている型を探すときに、`Imports` ステートメントを優先します。</span><span class="sxs-lookup"><span data-stu-id="c4319-125">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="c4319-126">\<summary> タグは、型またはメンバーに関する追加情報を表示するために、Visual Studio の IntelliSense によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4319-126">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c4319-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4319-127">Related sections</span></span>

<span data-ttu-id="c4319-128">ドキュメント コメントを含む XML ファイルの作成方法の詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c4319-128">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="c4319-129">-doc</span><span class="sxs-lookup"><span data-stu-id="c4319-129">-doc</span></span>](../../reference/command-line-compiler/doc.md)

- [<span data-ttu-id="c4319-130">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="c4319-130">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)

- [<span data-ttu-id="c4319-131">XML ファイルの処理</span><span class="sxs-lookup"><span data-stu-id="c4319-131">Processing the XML File</span></span>](processing-the-xml-file.md)

- [<span data-ttu-id="c4319-132">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="c4319-132">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)

- [<span data-ttu-id="c4319-133">Visual Studio の XML ツール</span><span class="sxs-lookup"><span data-stu-id="c4319-133">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="c4319-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4319-134">See also</span></span>

- [<span data-ttu-id="c4319-135">Visual Basic でのアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="c4319-135">Developing Applications with Visual Basic</span></span>](../../developing-apps/index.md)
- [<span data-ttu-id="c4319-136">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c4319-136">Visual Basic Programming Guide</span></span>](../index.md)
