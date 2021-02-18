---
description: '詳細情報: -doc'
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: da1ff6ad133dd2f46484b61ff73e1c6159eae557
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461425"
---
# <a name="-doc"></a><span data-ttu-id="dc882-103">-doc</span><span class="sxs-lookup"><span data-stu-id="dc882-103">-doc</span></span>

<span data-ttu-id="dc882-104">ドキュメント コメントを XML ファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="dc882-104">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc882-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc882-105">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="dc882-106">or</span><span class="sxs-lookup"><span data-stu-id="dc882-106">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc882-107">引数</span><span class="sxs-lookup"><span data-stu-id="dc882-107">Arguments</span></span>  
  
|<span data-ttu-id="dc882-108">用語</span><span class="sxs-lookup"><span data-stu-id="dc882-108">Term</span></span>|<span data-ttu-id="dc882-109">定義</span><span class="sxs-lookup"><span data-stu-id="dc882-109">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="dc882-110">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="dc882-110">`+` &#124; `-`</span></span>|<span data-ttu-id="dc882-111">任意。</span><span class="sxs-lookup"><span data-stu-id="dc882-111">Optional.</span></span> <span data-ttu-id="dc882-112">+、または単に `-doc` を指定すると、コンパイラによってドキュメント情報が生成され、XML ファイル内に置かれます。</span><span class="sxs-lookup"><span data-stu-id="dc882-112">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="dc882-113">`-` を指定することは `-doc` を指定しないことと同じで、この場合ドキュメント情報は作成されません。</span><span class="sxs-lookup"><span data-stu-id="dc882-113">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="dc882-114">`-doc:` を使用する場合に、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="dc882-114">Required if `-doc:` is used.</span></span> <span data-ttu-id="dc882-115">出力の XML ファイルを指定します。これにはコンパイルのソース コード ファイルからのコメントが入力されます。</span><span class="sxs-lookup"><span data-stu-id="dc882-115">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="dc882-116">ファイル名に空白が含まれている場合は、名前を引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="dc882-116">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc882-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="dc882-117">Remarks</span></span>  

 <span data-ttu-id="dc882-118">`-doc` オプションでは、コンパイラにドキュメント コメントを含む XML ファイルを生成させるかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="dc882-118">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="dc882-119">`-doc:file` 構文を使用する場合、`file` パラメーターによって XML ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc882-119">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="dc882-120">`-doc` または `-doc+` を使用する場合、コンパイラは、コンパイラが作成中の実行可能ファイルまたはライブラリから XML ファイルの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc882-120">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="dc882-121">`-doc-` を使用する場合、または `-doc` オプションを指定しない場合、コンパイラは XML ファイルを作成しません。</span><span class="sxs-lookup"><span data-stu-id="dc882-121">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="dc882-122">ソース コード ファイルで、ドキュメント コメントを次の定義の前に置くことができます。</span><span class="sxs-lookup"><span data-stu-id="dc882-122">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="dc882-123">[クラス](../../language-reference/statements/class-statement.md)や[インターフェイス](../../language-reference/statements/interface-statement.md)などのユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="dc882-123">User-defined types, such as a [class](../../language-reference/statements/class-statement.md) or [interface](../../language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="dc882-124">フィールド、[イベント](../../language-reference/statements/event-statement.md)、[プロパティ](../../language-reference/statements/property-statement.md)、[関数](../../language-reference/statements/function-statement.md)、[サブルーチン](../../language-reference/statements/sub-statement.md)などのメンバー。</span><span class="sxs-lookup"><span data-stu-id="dc882-124">Members, such as a field, [event](../../language-reference/statements/event-statement.md), [property](../../language-reference/statements/property-statement.md), [function](../../language-reference/statements/function-statement.md), or [subroutine](../../language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="dc882-125">Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) 機能で生成された XML ファイルを使用するには、XML ファイルの名前をサポートするアセンブリの名前と同じにします。</span><span class="sxs-lookup"><span data-stu-id="dc882-125">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="dc882-126">Visual Studio プロジェクトでアセンブリが参照されたときに .xml ファイルがうまく見つかるようにするために、XML ファイルがアセンブリと同じディレクトリにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dc882-126">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="dc882-127">IntelliSense をプロジェクト内のコード、またはプロジェクトに参照されるプロジェクト内のコードに対して動作させるために、XML ドキュメント ファイルは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="dc882-127">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="dc882-128">`-target:module` を使用してコンパイルしない限り、XML ファイルにはタグ `<assembly></assembly>` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc882-128">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="dc882-129">これらのタグでは、コンパイルの出力ファイルに向けたアセンブリ マニフェストを含むファイルの名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="dc882-129">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="dc882-130">コード内のコメントからドキュメントを生成する方法については、「[XML のコメント用タグ](../../language-reference/xmldoc/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc882-130">See [XML Comment Tags](../../language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="dc882-131">Visual Studio 統合開発環境で -doc を設定するには</span><span class="sxs-lookup"><span data-stu-id="dc882-131">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="dc882-132">1.**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc882-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="dc882-133">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc882-133">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="dc882-134">2. **[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc882-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="dc882-135">3. **[XML ドキュメント ファイルを生成する]** ボックスに値を設定します。</span><span class="sxs-lookup"><span data-stu-id="dc882-135">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dc882-136">例</span><span class="sxs-lookup"><span data-stu-id="dc882-136">Example</span></span>  

 <span data-ttu-id="dc882-137">サンプルについては、「[XML の使用によるコードのドキュメントの作成](../../programming-guide/program-structure/documenting-your-code-with-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc882-137">See [Documenting Your Code with XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc882-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc882-138">See also</span></span>

- [<span data-ttu-id="dc882-139">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="dc882-139">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="dc882-140">XML の使用によるコードのドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="dc882-140">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
