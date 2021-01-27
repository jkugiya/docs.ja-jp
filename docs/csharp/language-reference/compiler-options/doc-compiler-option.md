---
description: -doc (C# コンパイラ オプション)
title: -doc (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: e55b86e5b028fb871f309d80217477cfd164c106
ms.sourcegitcommit: f0eb7eeedf3ceec726499fa678786d03083214ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/21/2021
ms.locfileid: "98629255"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="2cb33-103">-doc (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2cb33-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="2cb33-104">**-doc** オプションを使用すると、XML ファイル内にドキュメント コメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb33-105">構文</span><span class="sxs-lookup"><span data-stu-id="2cb33-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="2cb33-106">引数</span><span class="sxs-lookup"><span data-stu-id="2cb33-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="2cb33-107">XML の出力ファイル。コンパイルのソース コード ファイルのコメントが入力されます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb33-108">注釈</span><span class="sxs-lookup"><span data-stu-id="2cb33-108">Remarks</span></span>  

 <span data-ttu-id="2cb33-109">ソース コード ファイルで、次の項目の前にあるドキュメント コメントを処理し、XML ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="2cb33-110">[クラス](../keywords/class.md)、[デリゲート](../builtin-types/reference-types.md#the-delegate-type)、[インターフェイス](../keywords/interface.md)などのユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="2cb33-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="2cb33-111">フィールド、[イベント](../keywords/event.md)、[プロパティ](../../programming-guide/classes-and-structs/using-properties.md)、メソッドなどのメンバー</span><span class="sxs-lookup"><span data-stu-id="2cb33-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="2cb33-112">Main を含むソース コード ファイルが最初に XML に出力されます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="2cb33-113">生成された .xml ファイルで [IntelliSense](/visualstudio/ide/using-intellisense) 機能を使用するには、サポートするアセンブリの名前と .xml ファイル名を同じにして、その .xml ファイルをアセンブリと同じディレクトリに置きます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="2cb33-114">これで、アセンブリが Visual Studio プロジェクトで参照されると、.xml ファイルも同様に検出されます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="2cb33-115">詳細については、[コード コメントの追加](/visualstudio/ide/reference/generate-xml-documentation-comments)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb33-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="2cb33-116">[-target:module](./target-module-compiler-option.md) でコンパイルしない限り、`file` には \<assembly>\</assembly> タグが追加されます。これにより、コンパイルの出力ファイルのアセンブリ マニフェストを含むファイルの名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cb33-117">-doc オプションは、すべての入力ファイル (プロジェクトの設定で設定された場合、そのプロジェクト内のすべてのファイル) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="2cb33-118">特定のファイルまたはコードの特定のセクションについて、ドキュメントのコメントに関する警告を無効にするには、[#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cb33-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="2cb33-119">コードのコメントからドキュメントを生成する方法については、「[ドキュメント コメント用の推奨タグ](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb33-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-2019-development-environment"></a><span data-ttu-id="2cb33-120">Visual Studio 2019 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="2cb33-120">To set this compiler option in the Visual Studio 2019 development environment</span></span>  

1. <span data-ttu-id="2cb33-121">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-121">Open the project's **Properties** page.</span></span>  
2. <span data-ttu-id="2cb33-122">**[ビルド]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb33-122">Click the **Build** tab.</span></span>
3. <span data-ttu-id="2cb33-123">**[XML ドキュメント ファイル]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="2cb33-123">Modify the **XML documentation file** property.</span></span>
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-for-mac-development-environment"></a><span data-ttu-id="2cb33-124">Visual Studio for Mac 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="2cb33-124">To set this compiler option in the Visual Studio for Mac development environment</span></span>  
  
1. <span data-ttu-id="2cb33-125">プロジェクトの **[オプション]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2cb33-125">Open the project's **Options** page.</span></span>
2. <span data-ttu-id="2cb33-126">**[コンパイラ]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb33-126">Select the **Compiler** tab.</span></span>
3. <span data-ttu-id="2cb33-127">**[XML ドキュメントを生成する]** を選択してから、テキスト ボックスにファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cb33-127">Select **Generate xml documentation** and enter the file name in the text box.</span></span>

<span data-ttu-id="2cb33-128">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb33-128">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb33-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cb33-129">See also</span></span>

- [<span data-ttu-id="2cb33-130">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="2cb33-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2cb33-131">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="2cb33-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
