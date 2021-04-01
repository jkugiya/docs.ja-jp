---
description: '詳細情報: XSLT コンパイラ (xsltc.exe)'
title: XSLT コンパイラ (xsltc.exe)
ms.date: 03/30/2017
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
ms.openlocfilehash: 96236e7a7c985c4a71c2f09ffd3ad720bb3d40f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782547"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="d261b-103">XSLT コンパイラ (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="d261b-103">XSLT Compiler (xsltc.exe)</span></span>

<span data-ttu-id="d261b-104">XSLT コンパイラ (xsltc.exe) は、XSLT スタイル シートをコンパイルしてアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="d261b-104">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="d261b-105">コンパイルしたスタイル シートを <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> メソッドに直接渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d261b-105">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d261b-106">xsltc.exe を使用して署名があるアセンブリを生成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d261b-106">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="d261b-107">xsltc.exe ツールは Visual Studio に付属しています。</span><span class="sxs-lookup"><span data-stu-id="d261b-107">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="d261b-108">詳細については、[Visual Studio のダウンロード](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d261b-108">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d261b-109">構文</span><span class="sxs-lookup"><span data-stu-id="d261b-109">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="d261b-110">引数</span><span class="sxs-lookup"><span data-stu-id="d261b-110">Argument</span></span>  
  
|<span data-ttu-id="d261b-111">引数</span><span class="sxs-lookup"><span data-stu-id="d261b-111">Argument</span></span>|<span data-ttu-id="d261b-112">説明</span><span class="sxs-lookup"><span data-stu-id="d261b-112">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="d261b-113">スタイル シートの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d261b-113">Specifies the name of the style sheet.</span></span> <span data-ttu-id="d261b-114">スタイル シートはローカル ファイルであるか、イントラネット上に置かれていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="d261b-114">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="d261b-115">オプション</span><span class="sxs-lookup"><span data-stu-id="d261b-115">Options</span></span>  
  
|<span data-ttu-id="d261b-116">オプション</span><span class="sxs-lookup"><span data-stu-id="d261b-116">Option</span></span>|<span data-ttu-id="d261b-117">説明</span><span class="sxs-lookup"><span data-stu-id="d261b-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d261b-118">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="d261b-118">`/c[lass]:` `name`</span></span>|<span data-ttu-id="d261b-119">以降のスタイル シートのクラス名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d261b-119">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="d261b-120">クラス名には完全修飾名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d261b-120">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="d261b-121">既定のクラス名は、スタイル シートの名前です。</span><span class="sxs-lookup"><span data-stu-id="d261b-121">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="d261b-122">たとえば、スタイル シート customers.xsl をコンパイルした場合、既定のクラス名は customers になります。</span><span class="sxs-lookup"><span data-stu-id="d261b-122">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="d261b-123">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="d261b-123">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="d261b-124">デバッグ情報を生成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d261b-124">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="d261b-125">`+` または `/debug` を指定すると、コンパイラによりデバッグ情報が生成され、プログラム データベース (PDB) ファイルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-125">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="d261b-126">生成される PDB ファイルの名前は `assemblyName`.pdb です。</span><span class="sxs-lookup"><span data-stu-id="d261b-126">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="d261b-127">`-` を指定しない場合、`/debug` の指定が有効となります。これを指定した場合、デバッグ情報は作成されません。</span><span class="sxs-lookup"><span data-stu-id="d261b-127">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="d261b-128">製品版のアセンブリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-128">A retail assembly is generated.</span></span> <span data-ttu-id="d261b-129">**注:** デバッグ モードでコンパイルすると、XSLT のパフォーマンスが大きな影響を受けることがあります。</span><span class="sxs-lookup"><span data-stu-id="d261b-129">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="d261b-130">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="d261b-130">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="d261b-131">コンパイラの著作権メッセージが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="d261b-131">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="d261b-132">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="d261b-132">`/platform:` `string`</span></span>|<span data-ttu-id="d261b-133">アセンブリを実行できるプラットフォームを指定します。</span><span class="sxs-lookup"><span data-stu-id="d261b-133">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="d261b-134">次に、有効なプラットフォームの値を示します。</span><span class="sxs-lookup"><span data-stu-id="d261b-134">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="d261b-135">`x86` : 32 ビット x86 互換共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d261b-135">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="d261b-136">`x64` : AMD64 または EM64T 命令セットをサポートするコンピューターで 64 ビット共通言語ランタイムにより実行できるように、アセンブリをコンパイルします</span><span class="sxs-lookup"><span data-stu-id="d261b-136">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="d261b-137">Itanium は、Itanium プロセッサを搭載したコンピューターで 64 ビット共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d261b-137">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="d261b-138">`anycpu` : 任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d261b-138">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="d261b-139">既定値です。</span><span class="sxs-lookup"><span data-stu-id="d261b-139">This is the default.</span></span>|  
|<span data-ttu-id="d261b-140">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="d261b-140">`/out:` `assemblyName`</span></span>|<span data-ttu-id="d261b-141">出力となるアセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d261b-141">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="d261b-142">複数のスタイル シートが存在している場合、既定のアセンブリ名はメインのスタイル シートか最初のスタイル シートの名前になります。</span><span class="sxs-lookup"><span data-stu-id="d261b-142">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="d261b-143">スタイル シートにスクリプトが含まれている場合、スクリプトは別のアセンブリに保存されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-143">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="d261b-144">スクリプト アセンブリ名は、メインのアセンブリ名から生成されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-144">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="d261b-145">たとえば、アセンブリ名を CustOrders.dll と指定した場合、最初のスクリプト アセンブリは CustOrders_Script1.dll という名前になります。</span><span class="sxs-lookup"><span data-stu-id="d261b-145">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="d261b-146">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="d261b-146">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="d261b-147">スタイル シートで `document()` 関数、XSLT スクリプト、またはドキュメント型定義 (DTD) を許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d261b-147">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="d261b-148">既定では、DTD、`document()` 関数、スクリプトのサポートは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="d261b-148">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="d261b-149">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="d261b-149">`@` `file`</span></span>|<span data-ttu-id="d261b-150">コンパイラ オプションを含むファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d261b-150">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="d261b-151">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="d261b-151">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d261b-152">Remarks</span><span class="sxs-lookup"><span data-stu-id="d261b-152">Remarks</span></span>  

 <span data-ttu-id="d261b-153">XSLT ソリューションは、複数のスタイル シート モジュールで構成できます。</span><span class="sxs-lookup"><span data-stu-id="d261b-153">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="d261b-154">xsltc.exe ツールを使用して、スタイル シートからアセンブリを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d261b-154">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="d261b-155">このアセンブリを <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> メソッドに直接渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d261b-155">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d261b-156">XSLT の配置シナリオによっては、これによってパフォーマンス コストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="d261b-156">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d261b-157">アプリケーションには、コンパイル済みのアセンブリも参照として含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="d261b-157">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="d261b-158">xsltc.exe ツールでは、クラス名 (`/class:`*name*) やアセンブリ名 (`/out:`*assemblyName*) が検証されません。</span><span class="sxs-lookup"><span data-stu-id="d261b-158">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="d261b-159">名前が無効である場合、共通言語ランタイムによってエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="d261b-159">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d261b-160">使用例</span><span class="sxs-lookup"><span data-stu-id="d261b-160">Examples</span></span>  

 <span data-ttu-id="d261b-161">次のコマンドを実行すると、スタイル シートがコンパイルされ、booksort.dll という名前のアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-161">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="d261b-162">次のコマンドを実行すると、スタイル シートがコンパイルされ、booksort.dll という名前のアセンブリと booksort.pdb という名前の PDB ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-162">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="d261b-163">次のコマンドを実行すると、msxsl:script 要素を含むスタイル シートがコンパイルされ、calc.dll および calc_Script1.dll という 2 つのアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-163">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="d261b-164">次のコマンドを実行すると、DTD 処理とスタイルのサポートが有効になり、myTest.dll および myTest_Script1.dll という 2 つのアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-164">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="d261b-165">次のコマンドを実行すると、2 つのスタイル シート モジュールがコンパイルされ、booksort.dll という名前のアセンブリが 1 つ作成されます。</span><span class="sxs-lookup"><span data-stu-id="d261b-165">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="d261b-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="d261b-166">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="d261b-167">方法: アセンブリを使用して XSLT 変換を実行する</span><span class="sxs-lookup"><span data-stu-id="d261b-167">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="d261b-168">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="d261b-168">XSLT Transformations</span></span>](xslt-transformations.md)
