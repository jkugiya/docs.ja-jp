---
title: Resgen.exe (リソース ファイル ジェネレーター)
description: Resgen.exe (リソース ファイル ジェネレーター) を使用します。 テキスト (.txt、.restext) および XML リソース形式 (.resx) ファイルを、埋め込み可能な CLR ランタイム バイナリ (.resources) に変換します。
ms.date: 03/30/2017
helpviewer_keywords:
- resource files, .resources files
- resource files, .resx files
- resx files (resource files)
- .resources files
- files, converting
- Resource File Generator
- .resx files
- Resgen.exe
- resource files, converting
- converting files, Resource File Generator
- binary resources files
- embedding files in runtime binary executable
ms.assetid: 8ef159de-b660-4bec-9213-c3fbc4d1c6f4
ms.openlocfilehash: 61ae4503876718e63993af5a180dead34540afde
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259112"
---
# <a name="resgenexe-resource-file-generator"></a><span data-ttu-id="76855-104">Resgen.exe (リソース ファイル ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="76855-104">Resgen.exe (Resource File Generator)</span></span>

<span data-ttu-id="76855-105">リソース ファイル ジェネレーター (Resgen.exe) は、テキスト (.txt または .restext) ファイルおよび XML ベースのリソース形式 (.resx) ファイルを共通言語ランタイムのバイナリ (.resources) ファイルに変換します。この .resources ファイルは、ランタイム バイナリ実行可能ファイルまたはサテライト アセンブリに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="76855-105">The Resource File Generator (Resgen.exe) converts text (.txt or .restext) files and XML-based resource format (.resx) files to common language runtime binary (.resources) files that can be embedded in a runtime binary executable or satellite assembly.</span></span> <span data-ttu-id="76855-106">「[リソース ファイルの作成](../resources/creating-resource-files-for-desktop-apps.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76855-106">(See [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).)</span></span>  
  
 <span data-ttu-id="76855-107">Resgen.exe は、次のタスクを実行する汎用のリソース変換ユーティリィティです。</span><span class="sxs-lookup"><span data-stu-id="76855-107">Resgen.exe is a general-purpose resource conversion utility that performs the following tasks:</span></span>  
  
- <span data-ttu-id="76855-108">.txt または .restext ファイルから .resources または .resx ファイルへの変換。</span><span class="sxs-lookup"><span data-stu-id="76855-108">Converts .txt or .restext files to .resources or .resx files.</span></span> <span data-ttu-id="76855-109">(.restext ファイルの形式は .txt ファイルの形式と同じです。</span><span class="sxs-lookup"><span data-stu-id="76855-109">(The format of .restext files is identical to the format of .txt files.</span></span> <span data-ttu-id="76855-110">ただし、拡張子 .restext を使用すると、リソース定義を含むテキスト ファイルをより簡単に識別できます)。</span><span class="sxs-lookup"><span data-stu-id="76855-110">However, the .restext extension helps you identify text files that contain resource definitions more easily.)</span></span>  
  
- <span data-ttu-id="76855-111">.resources ファイルからテキスト ファイルまたは .resx ファイルへの変換。</span><span class="sxs-lookup"><span data-stu-id="76855-111">Converts .resources files to text or .resx files.</span></span>  
  
- <span data-ttu-id="76855-112">.resx ファイルからテキスト ファイルまたは .resources ファイルへの変換。</span><span class="sxs-lookup"><span data-stu-id="76855-112">Converts .resx files to text or .resources files.</span></span>  
  
- <span data-ttu-id="76855-113">アセンブリからの文字列リソースを Windows 8.x Store アプリケーションでの使用に適した .resw ファイルに抽出します。</span><span class="sxs-lookup"><span data-stu-id="76855-113">Extracts the string resources from an assembly into a .resw file that is suitable for use in a Windows 8.x Store app.</span></span>  
  
- <span data-ttu-id="76855-114">個々の名前付きリソースと <xref:System.Resources.ResourceManager> インスタンスへのアクセスを提供する厳密に型指定されたクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="76855-114">Creates a strongly typed class that provides access to individual named resources and to the <xref:System.Resources.ResourceManager> instance.</span></span>  
  
 <span data-ttu-id="76855-115">何らかの理由により Resgen.exe が失敗した場合は、戻り値は –1 です。</span><span class="sxs-lookup"><span data-stu-id="76855-115">If Resgen.exe fails for any reason, the return value is –1.</span></span>  
  
 <span data-ttu-id="76855-116">Resgen.exe のヘルプを表示する場合は、オプションを指定せずに次のコマンドを使用して Resgen.exe のコマンド構文およびオプションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="76855-116">To get help with Resgen.exe, you can use the following command, with no options specified, to display the command syntax and options for Resgen.exe:</span></span>  
  
```console  
resgen  
```  
  
 <span data-ttu-id="76855-117">`/?` スイッチを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="76855-117">You can also use the `/?` switch:</span></span>  
  
```console  
resgen /?  
```  
  
 <span data-ttu-id="76855-118">Resgen.exe を使用してバイナリ .resources ファイルを生成する場合は、言語コンパイラを使用して実行可能アセンブリにバイナリ ファイルを埋め込むか、[アセンブリ リンカー (Al.exe)](al-exe-assembly-linker.md) を使用してサテライト アセンブリにコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="76855-118">If you use Resgen.exe to generate binary .resources files, you can use a language compiler to embed the binary files into executable assemblies, or you can use the [Assembly Linker (Al.exe)](al-exe-assembly-linker.md) to compile them into satellite assemblies.</span></span>  
  
 <span data-ttu-id="76855-119">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="76855-119">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="76855-120">ツールを実行するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。</span><span class="sxs-lookup"><span data-stu-id="76855-120">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="76855-121">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="76855-121">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76855-122">構文</span><span class="sxs-lookup"><span data-stu-id="76855-122">Syntax</span></span>  
  
```console  
resgen  [-define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]
```  
  
```console  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a><span data-ttu-id="76855-123">パラメーター</span><span class="sxs-lookup"><span data-stu-id="76855-123">Parameters</span></span>  
  
|<span data-ttu-id="76855-124">パラメーターまたはスイッチ</span><span class="sxs-lookup"><span data-stu-id="76855-124">Parameter or switch</span></span>|<span data-ttu-id="76855-125">説明</span><span class="sxs-lookup"><span data-stu-id="76855-125">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="76855-126">`/define:` *symbol1*[, *symbol2*,...]</span><span class="sxs-lookup"><span data-stu-id="76855-126">`/define:` *symbol1*[, *symbol2*,...]</span></span>|<span data-ttu-id="76855-127">.NET Framework 4.5 以降、テキスト ベース (.txt または .restext) リソース ファイル内の条件付きコンパイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="76855-127">Starting with the .NET Framework 4.5, supports conditional compilation in text-based (.txt or .restext) resource files.</span></span> <span data-ttu-id="76855-128">*symbol* が `#ifdef` コンストラクト内の入力テキスト ファイルに含まれるシンボルに対応している場合は、関連の文字列リソースが .resources ファイルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="76855-128">If *symbol* corresponds to a symbol included in the input text file within a `#ifdef` construct, the associated string resource is included in the .resources file.</span></span> <span data-ttu-id="76855-129">`#if !` スイッチによって定義されていないシンボルと共に `/define` ステートメントが入力テキスト ファイルに含まれている場合、関連の文字列リソースがリソース ファイルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="76855-129">If the input text file includes an `#if !` statement with a symbol that is not defined by the `/define` switch, the associated string resource is included in the resources file.</span></span><br /><br /> <span data-ttu-id="76855-130">テキスト ファイル以外で使用される場合、`/define` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="76855-130">`/define` is ignored if it is used with non-text files.</span></span> <span data-ttu-id="76855-131">シンボルでは、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="76855-131">Symbols are case-sensitive.</span></span><br /><br /> <span data-ttu-id="76855-132">このオプションについて詳しくは、このトピックの「[リソースの条件付きコンパイル](#Conditional)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76855-132">For more information about this option, see [Conditionally Compiling Resources](#Conditional) later in this topic.</span></span>|  
|`useSourcePath`|<span data-ttu-id="76855-133">入力ファイルの現在のディレクトリを使用して相対ファイル パスを解決することを指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-133">Specifies that the input file's current directory is to be used to resolve relative file paths.</span></span>|  
|`/compile`|<span data-ttu-id="76855-134">複数の .resx ファイルまたはテキスト ファイルを指定して、一括した操作で複数の .resources ファイルに変換できるようにします。</span><span class="sxs-lookup"><span data-stu-id="76855-134">Enables you to specify multiple .resx or text files to convert to multiple .resources files in a single bulk operation.</span></span> <span data-ttu-id="76855-135">このオプションを指定しない場合、指定できる入力ファイル引数は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="76855-135">If you do not specify this option, you can specify only one input file argument.</span></span> <span data-ttu-id="76855-136">出力ファイルには、*filename*.resources という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="76855-136">Output files are named *filename*.resources.</span></span><br /><br /> <span data-ttu-id="76855-137">このオプションは、`/str:` オプションと一緒に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="76855-137">This option cannot be used with the `/str:` option.</span></span><br /><br /> <span data-ttu-id="76855-138">このオプションについて詳しくは、このトピックの「[複数のファイルのコンパイルまたは変換](#Multiple)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76855-138">For more information about this option, see [Compiling or Converting Multiple Files](#Multiple) later in this topic.</span></span>|  
|<span data-ttu-id="76855-139">`/r:` `assembly`</span><span class="sxs-lookup"><span data-stu-id="76855-139">`/r:` `assembly`</span></span>|<span data-ttu-id="76855-140">指定されたアセンブリからメタデータを参照します。</span><span class="sxs-lookup"><span data-stu-id="76855-140">References metadata from the specified assembly.</span></span> <span data-ttu-id="76855-141">これは、.resx ファイルを変換するときに使用され、Resgen.exe がオブジェクト リソースをシリアル化または非シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="76855-141">It is used when converting .resx files and allows Resgen.exe to serialize or deserialize object resources.</span></span> <span data-ttu-id="76855-142">C# および Visual Basic コンパイラの `/reference:` や `/r:` オプションに似ています。</span><span class="sxs-lookup"><span data-stu-id="76855-142">It is similar to the `/reference:` or `/r:` options for the C# and Visual Basic compilers.</span></span>|  
|`filename.extension`|<span data-ttu-id="76855-143">変換対象の入力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-143">Specifies the name of the input file to convert.</span></span> <span data-ttu-id="76855-144">この表の前に示した 1 番目の長いコマンド ライン構文を使用する場合は、`extension` が以下のいずれかであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="76855-144">If you're using the first, lengthier command-line syntax presented before this table,  `extension` must be one of the following:</span></span><br /><br /> <span data-ttu-id="76855-145">.txt または .restext</span><span class="sxs-lookup"><span data-stu-id="76855-145">.txt or .restext</span></span><br /> <span data-ttu-id="76855-146">.resources ファイルまたは .resx ファイルに変換するテキスト ファイル。</span><span class="sxs-lookup"><span data-stu-id="76855-146">A text file to convert to a .resources or a .resx file.</span></span> <span data-ttu-id="76855-147">テキスト ファイルには、文字列リソースだけを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="76855-147">Text files can contain only string resources.</span></span> <span data-ttu-id="76855-148">ファイル形式については、「[リソース ファイルの作成](../resources/creating-resource-files-for-desktop-apps.md)」の「テキスト ファイル内のリソース」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76855-148">For information about the file format, see the "Resources in Text Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).</span></span><br /><br /> <span data-ttu-id="76855-149">.resx</span><span class="sxs-lookup"><span data-stu-id="76855-149">.resx</span></span><br /> <span data-ttu-id="76855-150">.resources ファイルまたはテキスト (.txt または .restext) ファイルに変換する、XML ベースのリソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="76855-150">An XML-based resource file to convert to a .resources or a text (.txt or .restext) file.</span></span><br /><br /> <span data-ttu-id="76855-151">.resources</span><span class="sxs-lookup"><span data-stu-id="76855-151">.resources</span></span><br /> <span data-ttu-id="76855-152">.resx ファイルまたはテキスト (.txt または .restext) ファイルに変換するバイナリ リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="76855-152">A binary resource file to convert to a .resx or a text (.txt or .restext) file.</span></span><br /><br /> <span data-ttu-id="76855-153">この表の前に示した 2 番目の短いコマンド ライン構文を使用する場合は、`extension` が以下のいずれかであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="76855-153">If you're using the second, shorter command-line syntax presented before this table, `extension` must be the following:</span></span><br /><br /> <span data-ttu-id="76855-154">.exe または .dll</span><span class="sxs-lookup"><span data-stu-id="76855-154">.exe or .dll</span></span><br /> <span data-ttu-id="76855-155">文字列リソースが Windows 8.x Store アプリケーションの開発で使用するための .resw ファイルに抽出される .NET Framework アセンブリ (実行可能ファイルまたはライブラリ)。</span><span class="sxs-lookup"><span data-stu-id="76855-155">A .NET Framework assembly (executable or library) whose string resources are to be extracted to a .resw file for use in developing Windows 8.x Store apps.</span></span>|  
|`outputFilename.extension`|<span data-ttu-id="76855-156">作成するリソース ファイルの名前および種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-156">Specifies the name and type of the resource file to create.</span></span><br /><br /> <span data-ttu-id="76855-157">.txt ファイル、.restext ファイル、または .resx ファイルから .resources ファイルへ変換する場合、この引数は省略できます。</span><span class="sxs-lookup"><span data-stu-id="76855-157">This argument is optional when converting from a .txt, .restext, or .resx file to a .resources file.</span></span> <span data-ttu-id="76855-158">`outputFilename` を指定しないと、入力 `filename` ファイルに拡張子 .resources が追加され、そのファイルが `filename,extension` を含むディレクトリに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="76855-158">If you do not specify `outputFilename`, Resgen.exe appends a .resources extension to the input `filename` and writes the file to the directory that contains `filename,extension`.</span></span><br /><br /> <span data-ttu-id="76855-159">.resources ファイルから変換する場合、引数 `outputFilename.extension` は必ず指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-159">The `outputFilename.extension` argument is mandatory when converting from a .resources file.</span></span> <span data-ttu-id="76855-160">.resources ファイルを XML ベースのリソース ファイルに変換する場合は、拡張子が .resx のファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-160">Specify a file name with the .resx extension when converting a .resources file to an XML-based resource file.</span></span> <span data-ttu-id="76855-161">.resources ファイルをテキスト ファイルに変換する場合は、拡張子が .txt または .restext のファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-161">Specify a file name with the .txt or .restext extension when converting a .resources file to a text file.</span></span> <span data-ttu-id="76855-162">.resources ファイルを .txt ファイルに変換するのは、.resource ファイルに文字列値だけが含まれている場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="76855-162">You should convert a .resources file to a .txt file only when the .resources file contains only string values.</span></span>|  
|`outputDirectory`|<span data-ttu-id="76855-163">Windows 8.x Store アプリケーションの場合は、`filename.extension` に文字列リソースを含む .resw ファイルが書き込まれるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-163">For Windows 8.x Store apps, specifies the directory in which a .resw file that contains the string resources in `filename.extension` will be written.</span></span> <span data-ttu-id="76855-164">`outputDirectory` は既に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-164">`outputDirectory` must already exist.</span></span>|  
|<span data-ttu-id="76855-165">`/str:` `language[,namespace[,classname[,filename]]]`</span><span class="sxs-lookup"><span data-stu-id="76855-165">`/str:` `language[,namespace[,classname[,filename]]]`</span></span>|<span data-ttu-id="76855-166">`language` オプションで指定されたプログラミング言語で、厳密に型指定されたリソース クラス ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="76855-166">Creates a strongly typed resource class file in the programming language specified in the `language` option.</span></span> <span data-ttu-id="76855-167">`language` は、次のリテラルの 1 つで構成できます:</span><span class="sxs-lookup"><span data-stu-id="76855-167">`language` can consist of one of the following literals:</span></span><br /><br /> <span data-ttu-id="76855-168">-   C# の場合: `c#`、`cs`、または `csharp`。</span><span class="sxs-lookup"><span data-stu-id="76855-168">-   For C#: `c#`, `cs`, or `csharp`.</span></span><br /><span data-ttu-id="76855-169">-   Visual Basic の場合: `vb` または `visualbasic`。</span><span class="sxs-lookup"><span data-stu-id="76855-169">-   For Visual Basic: `vb` or `visualbasic`.</span></span><br /><span data-ttu-id="76855-170">-   VBScript の場合: `vbs` または `vbscript`。</span><span class="sxs-lookup"><span data-stu-id="76855-170">-   For VBScript: `vbs` or `vbscript`.</span></span><br /><span data-ttu-id="76855-171">-   C++ の場合: `c++`、`mc`、または `cpp`。</span><span class="sxs-lookup"><span data-stu-id="76855-171">-   For C++: `c++`, `mc`, or `cpp`.</span></span><br /><span data-ttu-id="76855-172">-   JavaScript の場合: `js`、`jscript`、または `javascript`。</span><span class="sxs-lookup"><span data-stu-id="76855-172">-   For JavaScript: `js`, `jscript`, or `javascript`.</span></span><br /><br /> <span data-ttu-id="76855-173">`namespace` オプションではプロジェクトの既定の名前空間を指定し、`classname` オプションでは生成されるクラスの名前を指定し、`filename` オプションではクラス ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-173">The `namespace` option specifies the project's default namespace, the `classname` option specifies the name of the generated class, and the `filename` option specifies the name of the class file.</span></span><br /><br /> <span data-ttu-id="76855-174">`/str:` オプションは 1 つの入力ファイルにのみ対応しているため、`/compile` オプションと一緒に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="76855-174">The `/str:` option allows only one input file, so it cannot be used with the `/compile` option.</span></span><br /><br /> <span data-ttu-id="76855-175">`namespace` を指定して、`classname` を指定しない場合、出力ファイル名からクラス名が派生します (たとえば、ピリオドがアンダースコアに置き換えられます)。</span><span class="sxs-lookup"><span data-stu-id="76855-175">If `namespace` is specified but `classname` is not, the class name is derived from the output file name (for example, underscores are substituted for periods).</span></span> <span data-ttu-id="76855-176">このため、厳密に型指定されたリソースが正常に機能しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="76855-176">The strongly typed resources might not work correctly as a result.</span></span> <span data-ttu-id="76855-177">この問題を回避するには、クラス名と出力ファイル名の両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-177">To avoid this, specify both class name and output file name.</span></span><br /><br /> <span data-ttu-id="76855-178">このオプションについて詳しくは、このトピックの「[厳密に型指定されたリソース クラスの生成](#Strong)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76855-178">For more information about this option, see [Generating a Strongly Typed Resource Class](#Strong) later in this topic.</span></span>|  
|`/publicClass`|<span data-ttu-id="76855-179">厳密に型指定されたリソース クラスをパブリック クラスとして作成します。</span><span class="sxs-lookup"><span data-stu-id="76855-179">Creates a strongly typed resource class as a public class.</span></span> <span data-ttu-id="76855-180">既定では、リソース クラスは、C# の場合 `internal`、Visual Basic の場合 `Friend` です。</span><span class="sxs-lookup"><span data-stu-id="76855-180">By default, the resource class is `internal` in C# and `Friend` in Visual Basic.</span></span><br /><br /> <span data-ttu-id="76855-181">`/str:` オプションを使用しない場合、このオプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="76855-181">This option is ignored if the `/str:` option is not used.</span></span>|  
  
## <a name="resgenexe-and-resource-file-types"></a><span data-ttu-id="76855-182">Resgen.exe とリソース ファイルの種類</span><span class="sxs-lookup"><span data-stu-id="76855-182">Resgen.exe and Resource File Types</span></span>  

 <span data-ttu-id="76855-183">Resgen.exe で正常にリソースを変換するには、テキストおよび .resx ファイルが正しい形式になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-183">In order for Resgen.exe to successfully convert resources, text and .resx files must follow the correct format.</span></span>  
  
### <a name="text-txt-and-restext-files"></a><span data-ttu-id="76855-184">テキスト (.txt および .restext) ファイル</span><span class="sxs-lookup"><span data-stu-id="76855-184">Text (.txt and .restext) Files</span></span>  

 <span data-ttu-id="76855-185">テキスト (.txt または .restext) ファイルには、文字列リソースのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="76855-185">Text (.txt or .restext) files may contain only string resources.</span></span> <span data-ttu-id="76855-186">文字列リソースは、文字列を複数の言語に翻訳する必要があるアプリケーションを記述する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="76855-186">String resources are useful if you are writing an application that must have strings translated into several languages.</span></span> <span data-ttu-id="76855-187">たとえば、適切な文字列リソースを使用することで、メニュー文字列を簡単に地域固有の文字列に変更できます。</span><span class="sxs-lookup"><span data-stu-id="76855-187">For example, you can easily regionalize menu strings by using the appropriate string resource.</span></span> <span data-ttu-id="76855-188">Resgen.exe は名前と値のペアを含むテキスト ファイルを読み取ります。名前はリソースを説明する文字列で、値はリソース文字列そのものです。</span><span class="sxs-lookup"><span data-stu-id="76855-188">Resgen.exe reads text files that contain name/value pairs, where the name is a string that describes the resource and the value is the resource string itself.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76855-189">.txt ファイルと .restext ファイルの形式については、「[リソース ファイルの作成](../resources/creating-resource-files-for-desktop-apps.md)」の「テキスト ファイル内のリソース」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76855-189">For information about the format of .txt and .restext files, see the "Resources in Text Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).</span></span>  
  
 <span data-ttu-id="76855-190">リソースを格納するテキスト ファイルは、基本ラテンの範囲の文字だけ (U+007F まで) が含まれていない限り、UTF-8 エンコーディングまたは Unicode (UTF-16) エンコーディングで格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-190">A text file that contains resources must be saved with UTF-8 or Unicode (UTF-16) encoding unless it contains only characters in the Basic Latin range (to U+007F).</span></span> <span data-ttu-id="76855-191">Resgen.exe は、ANSI エンコーディングを使用して保存されたテキスト ファイルを処理するときに拡張 ANSI 文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="76855-191">Resgen.exe removes extended ANSI characters when it processes a text file that is saved using ANSI encoding.</span></span>  
  
 <span data-ttu-id="76855-192">Resgen.exe は、テキスト ファイルの中でリソース名が重複していないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="76855-192">Resgen.exe checks the text file for duplicate resource names.</span></span> <span data-ttu-id="76855-193">テキスト ファイルの中でリソース名が重複している場合は、警告メッセージが出され、2 つ目の値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="76855-193">If the text file contains duplicate resource names, Resgen.exe will emit a warning and ignore the second value.</span></span>  
  
### <a name="resx-files"></a><span data-ttu-id="76855-194">.resx ファイル</span><span class="sxs-lookup"><span data-stu-id="76855-194">.resx Files</span></span>  

 <span data-ttu-id="76855-195">.resx リソース ファイル形式は、XML エントリから構成されます。</span><span class="sxs-lookup"><span data-stu-id="76855-195">The .resx resource file format consists of XML entries.</span></span> <span data-ttu-id="76855-196">テキスト ファイルの場合と同様に、これらの XML エントリの中に文字列リソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="76855-196">You can specify string resources within these XML entries, as you would in text files.</span></span> <span data-ttu-id="76855-197">.resx ファイルがテキスト ファイルよりも優れている点は、オブジェクトの指定や埋め込みもできることです。</span><span class="sxs-lookup"><span data-stu-id="76855-197">A primary advantage of .resx files over text files is that you can also specify or embed objects.</span></span> <span data-ttu-id="76855-198">.resx ファイルを表示してみると、埋め込みオブジェクト (画像など) のバイナリ形式を参照できます (このバイナリ情報がリソース マニフェストの一部に含まれている場合)。</span><span class="sxs-lookup"><span data-stu-id="76855-198">When you view a .resx file, you can see the binary form of an embedded object (for example, a picture) when this binary information is a part of the resource manifest.</span></span> <span data-ttu-id="76855-199">テキスト ファイルと同様に、.resx ファイルはテキスト エディター (メモ帳や Microsoft Word など) で開き、内容を書き込み、解析、操作できます。</span><span class="sxs-lookup"><span data-stu-id="76855-199">As with text files, you can open a .resx file with a text editor (such as Notepad or Microsoft Word) and write, parse, and manipulate its contents.</span></span> <span data-ttu-id="76855-200">そのためには、XML のタグや .resx ファイルの構造を十分に知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-200">Note that this requires a good knowledge of XML tags and the .resx file structure.</span></span> <span data-ttu-id="76855-201">.resx ファイル形式について詳しくは、「[リソース ファイルの作成](../resources/creating-resource-files-for-desktop-apps.md)」の「.resx ファイル内のリソース」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76855-201">For more details on the .resx file format, see the "Resources in .resx Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).</span></span>  
  
 <span data-ttu-id="76855-202">文字列以外の埋め込みオブジェクトを含む .resources ファイルを作成するには、それらのオブジェクトを含む .resx ファイルを Resgen.exe で変換するか、<xref:System.Resources.ResourceWriter> クラスで提供されているメソッドを呼び出して、オブジェクト リソースをコードから直接ファイルに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-202">In order to create a .resources file that contains embedded nonstring objects, you must either use Resgen.exe to convert a .resx file containing objects or add the object resources to your file directly from code by calling the methods provided by the <xref:System.Resources.ResourceWriter> class.</span></span>  
  
 <span data-ttu-id="76855-203">.resx または .resources ファイルにオブジェクトが含まれ、Resgen.exe を使用してそれをテキスト ファイルに変換する場合、文字列リソースはすべて正しく変換されますが、非文字列オブジェクトのデータ型も文字列としてファイルに書き込まれることになります。</span><span class="sxs-lookup"><span data-stu-id="76855-203">If your .resx or .resources file contains objects and you use Resgen.exe to convert it to a text file, all the string resources will be converted correctly, but the data types of the nonstring objects will also be written to the file as strings.</span></span> <span data-ttu-id="76855-204">この変換処理では埋め込みオブジェクトが失われるため、リソースの取得時にエラーが発生したと報告されます。</span><span class="sxs-lookup"><span data-stu-id="76855-204">You will lose the embedded objects in the conversion, and Resgen.exe will report that an error occurred in retrieving the resources.</span></span>  
  
### <a name="converting-between-resources-file-types"></a><span data-ttu-id="76855-205">リソース ファイルの種類間の変換</span><span class="sxs-lookup"><span data-stu-id="76855-205">Converting Between Resources File Types</span></span>  

 <span data-ttu-id="76855-206">異なる種類のリソース ファイル間で変換を行うと、変換元と変換先のファイルの種類によっては、Resgen.exe が変換を実行できないか、特定のリソースに関する情報が失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="76855-206">When you convert between different resource file types, Resgen.exe may not be able to perform the conversion or may lose information about specific resources, depending on the source and target file types.</span></span> <span data-ttu-id="76855-207">次の表は、あるリソース ファイルの種類から別の種類に変換するとき、正常な変換の種類を指定しています。</span><span class="sxs-lookup"><span data-stu-id="76855-207">The following table specifies the types of conversions that are successful when converting from one resource file type to another.</span></span>  
  
|<span data-ttu-id="76855-208">変換元</span><span class="sxs-lookup"><span data-stu-id="76855-208">Convert from</span></span>|<span data-ttu-id="76855-209">テキスト ファイルへ</span><span class="sxs-lookup"><span data-stu-id="76855-209">To text file</span></span>|<span data-ttu-id="76855-210">.resx ファイルへ</span><span class="sxs-lookup"><span data-stu-id="76855-210">To .resx file</span></span>|<span data-ttu-id="76855-211">.resw ファイルへ</span><span class="sxs-lookup"><span data-stu-id="76855-211">To .resw file</span></span>|<span data-ttu-id="76855-212">.resources ファイルへ</span><span class="sxs-lookup"><span data-stu-id="76855-212">To .resources file</span></span>|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|<span data-ttu-id="76855-213">テキスト (.txt または .restext) ファイル</span><span class="sxs-lookup"><span data-stu-id="76855-213">Text (.txt or .restext) file</span></span>|--|<span data-ttu-id="76855-214">問題なし</span><span class="sxs-lookup"><span data-stu-id="76855-214">No issues</span></span>|<span data-ttu-id="76855-215">サポートなし</span><span class="sxs-lookup"><span data-stu-id="76855-215">Not supported</span></span>|<span data-ttu-id="76855-216">問題なし</span><span class="sxs-lookup"><span data-stu-id="76855-216">No issues</span></span>|  
|<span data-ttu-id="76855-217">.resx ファイル</span><span class="sxs-lookup"><span data-stu-id="76855-217">.resx file</span></span>|<span data-ttu-id="76855-218">変換は、ファイルに文字列以外のリソース (ファイル リンクを含む) が含まれている場合は失敗します</span><span class="sxs-lookup"><span data-stu-id="76855-218">Conversion fails if file contains non-string resources (including file links)</span></span>|--|<span data-ttu-id="76855-219">サポートなし</span><span class="sxs-lookup"><span data-stu-id="76855-219">Not supported</span></span>|<span data-ttu-id="76855-220">問題なし</span><span class="sxs-lookup"><span data-stu-id="76855-220">No issues</span></span>|  
|<span data-ttu-id="76855-221">.resources ファイル</span><span class="sxs-lookup"><span data-stu-id="76855-221">.resources file</span></span>|<span data-ttu-id="76855-222">変換は、ファイルに文字列以外のリソース (ファイル リンクを含む) が含まれている場合は失敗します</span><span class="sxs-lookup"><span data-stu-id="76855-222">Conversion fails if file contains non-string resources (including file links)</span></span>|<span data-ttu-id="76855-223">問題なし</span><span class="sxs-lookup"><span data-stu-id="76855-223">No issues</span></span>|<span data-ttu-id="76855-224">サポートなし</span><span class="sxs-lookup"><span data-stu-id="76855-224">Not supported</span></span>|--|  
|<span data-ttu-id="76855-225">.exe または .dll アセンブリ</span><span class="sxs-lookup"><span data-stu-id="76855-225">.exe or .dll assembly</span></span>|<span data-ttu-id="76855-226">サポートされていません</span><span class="sxs-lookup"><span data-stu-id="76855-226">Not supported</span></span>|<span data-ttu-id="76855-227">サポートなし</span><span class="sxs-lookup"><span data-stu-id="76855-227">Not supported</span></span>|<span data-ttu-id="76855-228">文字列リソース (パス名を含む) だけがリソースとして認識されます。</span><span class="sxs-lookup"><span data-stu-id="76855-228">Only string resources (including path names) are recognized as resources</span></span>|<span data-ttu-id="76855-229">サポートなし</span><span class="sxs-lookup"><span data-stu-id="76855-229">Not supported</span></span>|  
  
## <a name="performing-specific-resgenexe-tasks"></a><span data-ttu-id="76855-230">特定の Resgen.exe タスクの実行</span><span class="sxs-lookup"><span data-stu-id="76855-230">Performing Specific Resgen.exe Tasks</span></span>  

 <span data-ttu-id="76855-231">さまざまな方法で Resgen.exe を使用できます。テキストベースまたは XML ベースのリソース ファイルをバイナリ ファイルにコンパイルすることや、リソース ファイル形式を別のリソース ファイル形式に変換することや、<xref:System.Resources.ResourceManager> 機能をラップしてリソースへのアクセスを提供するクラスを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="76855-231">You can use Resgen.exe in diverse ways: to compile a text-based or XML-based resource file into a binary file, to convert between resource file formats, and to generate a class that wraps <xref:System.Resources.ResourceManager> functionality and provides access to resources.</span></span> <span data-ttu-id="76855-232">このセクションには、各タスクに関する詳細な情報があります。</span><span class="sxs-lookup"><span data-stu-id="76855-232">This section provides detailed information about each task:</span></span>  
  
- [<span data-ttu-id="76855-233">リソースのバイナリ ファイルへのコンパイル</span><span class="sxs-lookup"><span data-stu-id="76855-233">Compiling Resources into a Binary File</span></span>](resgen-exe-resource-file-generator.md#Compiling)  
  
- [<span data-ttu-id="76855-234">リソース ファイルの種類間の変換</span><span class="sxs-lookup"><span data-stu-id="76855-234">Converting Between Resource File Types</span></span>](resgen-exe-resource-file-generator.md#Convert)  
  
- [<span data-ttu-id="76855-235">複数のファイルのコンパイルまたは変換</span><span class="sxs-lookup"><span data-stu-id="76855-235">Compiling or Converting Multiple Files</span></span>](resgen-exe-resource-file-generator.md#Multiple)  
  
- [<span data-ttu-id="76855-236">.resw ファイルへのリソースのエクスポート</span><span class="sxs-lookup"><span data-stu-id="76855-236">Exporting Resources to a .resw File</span></span>](resgen-exe-resource-file-generator.md#Exporting)  
  
- [<span data-ttu-id="76855-237">リソースの条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="76855-237">Conditionally Compiling Resources</span></span>](resgen-exe-resource-file-generator.md#Conditional)  
  
- [<span data-ttu-id="76855-238">厳密に型指定されたリソース クラスの生成</span><span class="sxs-lookup"><span data-stu-id="76855-238">Generating a Strongly Typed Resource Class</span></span>](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>

### <a name="compiling-resources-into-a-binary-file"></a><span data-ttu-id="76855-239">リソースのバイナリ ファイルへのコンパイル</span><span class="sxs-lookup"><span data-stu-id="76855-239">Compiling Resources into a Binary File</span></span>  

 <span data-ttu-id="76855-240">Resgen.exe の最も一般的な用途は、テキスト ベースのリソース ファイル (.txt または .restext ファイル) または XML ベースのリソース ファイル (.resx ファイル) をバイナリ .resources ファイルにコンパイルすることです。</span><span class="sxs-lookup"><span data-stu-id="76855-240">The most common use of Resgen.exe is to compile a text-based resource file (a .txt or .restext file) or an XML-based resource file (a .resx file) into a binary .resources file.</span></span> <span data-ttu-id="76855-241">次に、出力ファイルは、言語コンパイラを使用してメインのアセンブリに、または[アセンブリ リンカー (AL.exe)](al-exe-assembly-linker.md) を使用してサテライト アセンブリに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="76855-241">The output file then can be embedded in a main assembly by a language compiler or in a satellite assembly by [Assembly Linker (AL.exe)](al-exe-assembly-linker.md).</span></span>  
  
 <span data-ttu-id="76855-242">リソース ファイルをコンパイルする構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76855-242">The syntax to compile a resource file is:</span></span>  
  
```console  
resgen inputFilename [outputFilename]
```  
  
 <span data-ttu-id="76855-243">パラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76855-243">where the parameters are:</span></span>  
  
 `inputFilename`  
 <span data-ttu-id="76855-244">コンパイルするリソース ファイルの拡張子を含むファイル名。</span><span class="sxs-lookup"><span data-stu-id="76855-244">The file name, including the extension, of the resource file to compile.</span></span> <span data-ttu-id="76855-245">Resgen.exe は、拡張子 .txt、.restext、または .resx を持つファイルだけをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="76855-245">Resgen.exe only compiles files with extensions of .txt, .restext, or .resx.</span></span>  
  
 `outputFilename`  
 <span data-ttu-id="76855-246">出力ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="76855-246">The name of the output file.</span></span> <span data-ttu-id="76855-247">`outputFilename` を省略した場合は、Resgen.exe が `inputFilename` と同じディレクトリに `inputFilename` のルート ファイル名の .resources ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="76855-247">If you omit `outputFilename`, Resgen.exe creates a .resources file with the root file name of `inputFilename` in the same directory as `inputFilename`.</span></span> <span data-ttu-id="76855-248">`outputFilename` でディレクトリ パスが示されている場合、ディレクトリが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-248">If `outputFilename` includes a directory path, the directory must exist.</span></span>  
  
 <span data-ttu-id="76855-249">ファイル名を指定し、それをピリオドでルート ファイル名から区切ることで、.resources ファイルの完全修飾名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="76855-249">You provide a fully qualified namespace for the .resources file by specifying it in the file name and separating it from the root file name by a period.</span></span> <span data-ttu-id="76855-250">たとえば、`outputFilename` が `MyCompany.Libraries.Strings.resources` の場合、その名前空間は MyCompany.Libraries になります。</span><span class="sxs-lookup"><span data-stu-id="76855-250">For example, if `outputFilename` is `MyCompany.Libraries.Strings.resources`, the namespace is MyCompany.Libraries.</span></span>  
  
 <span data-ttu-id="76855-251">Resources.txt に含まれる名前と値のペアを読み取り、Resources.resources という名前のバイナリ .resources ファイルを書き込むコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="76855-251">The following command reads the name/value pairs in Resources.txt and writes a binary .resources file named Resources.resources.</span></span> <span data-ttu-id="76855-252">出力ファイル名は明示的に指定されていないため、入力ファイルと同じ名前を既定で受け取ります。</span><span class="sxs-lookup"><span data-stu-id="76855-252">Because the output file name is not specified explicitly, it receives the same name as the input file by default.</span></span>  
  
```console  
resgen Resources.txt
```  
  
 <span data-ttu-id="76855-253">Resources.restext に含まれる名前と値のペアを読み取り、StringResources.resources という名前のバイナリ リソース ファイルを書き込むコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="76855-253">The following command reads the name/value pairs in Resources.restext and writes a binary resources file named StringResources.resources.</span></span>  
  
```console  
resgen Resources.restext StringResources.resources  
```  
  
 <span data-ttu-id="76855-254">XML ベースの入力ファイル Resources.resx を読み取り、Resources.resources という名前のバイナリ .resources ファイルを書き込むコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="76855-254">The following command reads an XML-based input file named Resources.resx and writes a binary .resources file named Resources.resources.</span></span>  
  
```console  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>

### <a name="converting-between-resource-file-types"></a><span data-ttu-id="76855-255">リソース ファイルの種類間の変換</span><span class="sxs-lookup"><span data-stu-id="76855-255">Converting Between Resource File Types</span></span>  

 <span data-ttu-id="76855-256">テキストベースか XML ベースのリソース ファイルをバイナリ .resources ファイルにコンパイルすることに加えて、Resgen.exe は、任意のサポートされるファイルの種類を他のサポートされるファイルの種類に変換できます。</span><span class="sxs-lookup"><span data-stu-id="76855-256">In addition to compiling text-based or XML-based resource files into binary .resources files, Resgen.exe can convert any supported file type to any other supported file type.</span></span> <span data-ttu-id="76855-257">これによって、次の変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="76855-257">This means that it can perform the following conversions:</span></span>  
  
- <span data-ttu-id="76855-258">.txt および .restext ファイルから .resx ファイル。</span><span class="sxs-lookup"><span data-stu-id="76855-258">.txt and .restext files to .resx files.</span></span>  
  
- <span data-ttu-id="76855-259">.resx ファイルから .txt および .restext ファイル。</span><span class="sxs-lookup"><span data-stu-id="76855-259">.resx files to .txt and .restext files.</span></span>  
  
- <span data-ttu-id="76855-260">.resources ファイルから .txt および .restext ファイル。</span><span class="sxs-lookup"><span data-stu-id="76855-260">.resources files to .txt and .restext files.</span></span>  
  
- <span data-ttu-id="76855-261">.resources ファイルから .resx ファイル。</span><span class="sxs-lookup"><span data-stu-id="76855-261">.resources files to .resx files.</span></span>  
  
 <span data-ttu-id="76855-262">構文は、前のセクションの構文と同じです。</span><span class="sxs-lookup"><span data-stu-id="76855-262">The syntax is the same as that shown in the previous section.</span></span>  
  
 <span data-ttu-id="76855-263">また、Resgen.exe を使用して、.NET Framework アセンブリへの埋め込みリソースを Windows 8.x Store アプリケーション対応 .resw ファイルに変換できます。</span><span class="sxs-lookup"><span data-stu-id="76855-263">In addition, you can use Resgen.exe to convert embedded resources in a .NET Framework assembly to a .resw file tor Windows 8.x Store apps.</span></span>  
  
 <span data-ttu-id="76855-264">バイナリ リソース ファイル Resources.resources を読み取り、Resources.resx という名前の XML ベースの出力ファイルを書き込むコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="76855-264">The following command reads a binary resources file Resources.resources and writes an XML-based output file named Resources.resx.</span></span>  
  
```console  
resgen Resources.resources Resources.resx  
```  
  
 <span data-ttu-id="76855-265">次のコマンドは、StringResources.txt という名前のテキスト ベースのリソース ファイルを読み取り、LibraryResources.resx という名前の XML ベースのリソース ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="76855-265">The following command reads a text-based resources file named StringResources.txt and writes an XML-based resources file named LibraryResources.resx.</span></span> <span data-ttu-id="76855-266">文字列リソースを含むことに加えて、.resx ファイルは、文字列以外のリソースを保存するのにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="76855-266">In addition to containing string resources, the .resx file could also be used to store non-string resources.</span></span>  
  
```console  
resgen StringResources.txt LibraryResources.resx  
```  
  
 <span data-ttu-id="76855-267">次の 2 つのコマンドは、Resources.resx という名前の XML ベースのリソース ファイルを読み取り、Resources.txt および Resources.restext という名前のテキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="76855-267">The following two commands read an XML-based resources file named Resources.resx and write text files named Resources.txt and Resources.restext.</span></span> <span data-ttu-id="76855-268">.resx ファイルに埋め込みオブジェクトが含まれている場合は、テキスト ファイルに正しく変換されません。</span><span class="sxs-lookup"><span data-stu-id="76855-268">Note that if the .resx file contains any embedded objects, they will not be accurately converted into the text files.</span></span>  
  
```console  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>

### <a name="compiling-or-converting-multiple-files"></a><span data-ttu-id="76855-269">複数のファイルのコンパイルまたは変換</span><span class="sxs-lookup"><span data-stu-id="76855-269">Compiling or Converting Multiple Files</span></span>  

 <span data-ttu-id="76855-270">`/compile` スイッチを使用すると、1 回の操作でリソース ファイルの一覧を別の形式に変換できます。</span><span class="sxs-lookup"><span data-stu-id="76855-270">You can use the `/compile` switch to convert a list of resource files from one format to another in a single operation.</span></span> <span data-ttu-id="76855-271">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76855-271">The syntax is:</span></span>  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 <span data-ttu-id="76855-272">次のコマンドは、3 つのファイル、StringResources.resources、TableResources.resources、ImageResources.resources を StringResources.txt、TableResources.resw、ImageResources.resw という名前の別の .resources ファイルにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="76855-272">The following command compiles three files, StringResources.txt, TableResources.resw, and ImageResources.resw, into separate .resources files named StringResources.resources, TableResources.resources, and ImageResources.resources.</span></span>  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>

### <a name="exporting-resources-to-a-resw-file"></a><span data-ttu-id="76855-273">.resw ファイルへのリソースのエクスポート</span><span class="sxs-lookup"><span data-stu-id="76855-273">Exporting Resources to a .resw File</span></span>  

 <span data-ttu-id="76855-274">Windows 8.x Store アプリケーションを開発する場合は、既存のデスクトップ アプリケーションのリソースを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="76855-274">If you're developing a Windows 8.x Store app, you may want to use resources from an existing desktop app.</span></span> <span data-ttu-id="76855-275">ただし、2 つの種類のアプリケーションは、異なるファイル形式をサポートします。</span><span class="sxs-lookup"><span data-stu-id="76855-275">However, the two kinds of applications support different file formats.</span></span> <span data-ttu-id="76855-276">デスクトップ アプリケーションでは、テキストのリソース (.txt または .restext) または .resx ファイルはバイナリ .resources ファイルにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="76855-276">In desktop apps, resources in text (.txt or .restext) or .resx files are compiled into binary .resources files.</span></span> <span data-ttu-id="76855-277">Windows 8.x Store アプリケーションでは、.resw ファイルはバイナリ パッケージ リソース インデックス (PRI) ファイルにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="76855-277">In Windows 8.x Store apps, .resw files are compiled into binary package resource index (PRI) files.</span></span> <span data-ttu-id="76855-278">Resgen.exe を使用して、このギャップを埋めることができます。これを行うには、実行可能ファイルまたはサテライト アセンブリからリソースを抽出して、Windows 8.x Store アプリケーションの開発時に使用できる 1 つ以上の .resw ファイルを記述します。</span><span class="sxs-lookup"><span data-stu-id="76855-278">You can use Resgen.exe to bridge this gap by extracting resources from an executable or a satellite assembly and writing them to one or more .resw files that can be used when developing a Windows 8.x Store app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="76855-279">Visual Studio は、ポータブル ライブラリ内のリソースを Windows 8.x Store アプリに組み込むために必要なすべての変換を自動的に処理します。</span><span class="sxs-lookup"><span data-stu-id="76855-279">Visual Studio automatically handles all conversions necessary for incorporating the resources in a portable library into a Windows 8.x Store app.</span></span> <span data-ttu-id="76855-280">アセンブリ内でリソースを .resw ファイル形式に変換するために Resgen.exe を直接使用する方法は、Visual Studio 外で Windows 8.x Store アプリを開発する開発者にのみ関連します。</span><span class="sxs-lookup"><span data-stu-id="76855-280">Using Resgen.exe directly to convert the resources in an assembly to .resw file format is of interest only to developers who want to develop a Windows 8.x Store app outside of Visual Studio.</span></span>  
  
 <span data-ttu-id="76855-281">アセンブリから .resw ファイルを生成する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76855-281">The syntax to generate .resw files from an assembly is:</span></span>  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 <span data-ttu-id="76855-282">パラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76855-282">where the parameters are:</span></span>  
  
 `filename.extension`  
 <span data-ttu-id="76855-283">.NET Framework アセンブリ (実行可能ファイルまたは .DLL) の名前。</span><span class="sxs-lookup"><span data-stu-id="76855-283">The name of a .NET Framework assembly (an executable or .DLL).</span></span> <span data-ttu-id="76855-284">ファイルにリソースが含まれていない場合、Resgen.exe でファイルは作成されません。</span><span class="sxs-lookup"><span data-stu-id="76855-284">If the file contains no resources, Resgen.exe does not create any files.</span></span>  
  
 `outputDirectory`  
 <span data-ttu-id="76855-285">.resw ファイルを記述する既存のディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="76855-285">The existing directory to which to write the .resw files.</span></span> <span data-ttu-id="76855-286">`outputDirectory` を省略すると、.resw ファイルは現在のディレクトリに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="76855-286">If `outputDirectory` is omitted, .resw files are written to the current directory.</span></span> <span data-ttu-id="76855-287">Resgen.exe は、アセンブリ内の .resources ファイルごとに 1 つの .resw ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="76855-287">Resgen.exe creates one .resw file for each .resources file in the assembly.</span></span> <span data-ttu-id="76855-288">.resw ファイルのルート ファイル名は .resources ファイルのルート名と同じです。</span><span class="sxs-lookup"><span data-stu-id="76855-288">The root file name of the .resw file is the same as the root name of the .resources file.</span></span>  
  
 <span data-ttu-id="76855-289">次のコマンドは、MyApp.exe に埋め込まれた各 .resources ファイルに対し、Win8Resources ディレクトリに .resw ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="76855-289">The following command creates a .resw file in the Win8Resources directory for each .resources file embedded in MyApp.exe:</span></span>  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>

### <a name="conditionally-compiling-resources"></a><span data-ttu-id="76855-290">リソースの条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="76855-290">Conditionally Compiling Resources</span></span>  

 <span data-ttu-id="76855-291">.NET Framework 4.5 以降、Resgen.exe では、テキスト (.txt および .restext) ファイル内の文字列リソースの条件付きコンパイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="76855-291">Starting with the .NET Framework 4.5, Resgen.exe supports conditional compilation of string resources in text (.txt and .restext) files.</span></span> <span data-ttu-id="76855-292">これによって、複数のビルド構成で 1 つのテキスト ベースのリソース ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="76855-292">This enables you to use a single text-based resource file in multiple build configurations.</span></span>  
  
 <span data-ttu-id="76855-293">.txt または .restext ファイルで、シンボルが定義されている場合は、`#ifdef` … `#endif`</span><span class="sxs-lookup"><span data-stu-id="76855-293">In a .txt or .restext file, you use the `#ifdef`…`#endif`</span></span> <span data-ttu-id="76855-294">コンストラクトを使って、バイナリ .resources ファイルにリソースを含めます。また、シンボルが定義されていない場合は、`#if !` ... `#endif` コンストラクトを使ってリソースを含めます。</span><span class="sxs-lookup"><span data-stu-id="76855-294">construct to include a resource in the binary .resources file if a symbol is defined, and you use the `#if !`... `#endif` construct to include a resource if a symbol is not defined.</span></span> <span data-ttu-id="76855-295">コンパイル時に、シンボルのコンマ区切りリストが続く `/define:` オプションを使用して、シンボルを定義します。</span><span class="sxs-lookup"><span data-stu-id="76855-295">At compile time, you then define symbols by using the `/define:` option followed by a comma-delimited list of symbols.</span></span> <span data-ttu-id="76855-296">比較では、大文字と小文字が区別されます。つまり、`/define` によって定義されたシンボルとコンパイルされるテキスト ファイルのシンボルの大文字と小文字が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-296">The comparison is cased-sensitive; the case of symbols defined by `/define` must match the case of symbols in the text files to be compiled.</span></span>  
  
 <span data-ttu-id="76855-297">たとえば、UIResources.rext という名前の次のファイルには、`AppTitle`、`PRODUCTION`、または `CONSULT` のどの名前のシンボルが定義されているかに応じて 3 つの値からいずれか 1 つの値を取得できる `RETAIL` という名前の文字列リソースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="76855-297">For example, the following file named UIResources.rext includes a string resource named `AppTitle` that can take one of three values, depending on whether symbols named `PRODUCTION`, `CONSULT`, or `RETAIL` are defined.</span></span>  
  
```text
#ifdef PRODUCTION  
AppTitle=My Software Company Project Manager
#endif  
#ifdef CONSULT  
AppTitle=My Consulting Company Project Manager  
#endif  
#ifdef RETAIL  
AppTitle=My Retail Store Project Manager  
#endif  
FileMenuName=File  
```  
  
 <span data-ttu-id="76855-298">ファイルは、次のコマンドを使用してバイナリ .resources ファイルにコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="76855-298">The file can then be compiled into a binary .resources file with the following command:</span></span>  
  
```console  
resgen /define:CONSULT UIResources.restext  
```  
  
 <span data-ttu-id="76855-299">これによって、2 つの文字列リソースを含む .resources ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="76855-299">This produces a .resources file that contains two string resources.</span></span> <span data-ttu-id="76855-300">`AppTitle` リソースの値は "My Consulting Company Project Manager" です。</span><span class="sxs-lookup"><span data-stu-id="76855-300">The value of the `AppTitle` resource is "My Consulting Company Project Manager".</span></span>  
  
<a name="Strong"></a>

### <a name="generating-a-strongly-typed-resource-class"></a><span data-ttu-id="76855-301">厳密に型指定されたリソース クラスを生成しています</span><span class="sxs-lookup"><span data-stu-id="76855-301">Generating a Strongly Typed Resource Class</span></span>  

 <span data-ttu-id="76855-302">Resgen.exe は厳密に型指定されたリソースをサポートします。このサポートでは、静的な読み取り専用プロパティを持つクラスを作成して、リソースへのアクセスをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="76855-302">Resgen.exe supports strongly typed resources, which encapsulates access to resources by creating classes that contain a set of static read-only properties.</span></span> <span data-ttu-id="76855-303">これによって、リソースを取得するために <xref:System.Resources.ResourceManager> クラスのメソッドを直接呼び出す方法の代替手段が可能になります。</span><span class="sxs-lookup"><span data-stu-id="76855-303">This provides an alternative to calling the methods of the <xref:System.Resources.ResourceManager> class directly to retrieve resources.</span></span> <span data-ttu-id="76855-304">`/str` クラスの機能をラップする、Resgen.exe の <xref:System.Resources.Tools.StronglyTypedResourceBuilder> オプションを使用して、厳密に型指定されたリソース サポートを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="76855-304">You can enable strongly typed resource support by using the `/str` option in Resgen.exe, which wraps the functionality of the <xref:System.Resources.Tools.StronglyTypedResourceBuilder> class.</span></span> <span data-ttu-id="76855-305">`/str` オプションを指定した場合の Resgen.exe の出力は、入力パラメーターで参照されるリソースと一致する厳密に型指定されたプロパティを含むクラスです。</span><span class="sxs-lookup"><span data-stu-id="76855-305">When you specify the `/str` option, the output of Resgen.exe is a class that contains strongly typed properties that match the resources that are referenced in the input parameter.</span></span> <span data-ttu-id="76855-306">このクラスは、処理されたファイルで使用できるリソースに対する、厳密に型指定された読み取り専用アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="76855-306">This class provides strongly typed read-only access to the resources that are available in the file processed.</span></span>  
  
 <span data-ttu-id="76855-307">厳密に型指定されたリソースを作成する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76855-307">The syntax to create a strongly typed resource is:</span></span>  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 <span data-ttu-id="76855-308">パラメーターとスイッチ:</span><span class="sxs-lookup"><span data-stu-id="76855-308">The parameters and switches are:</span></span>  
  
 `inputFilename`  
 <span data-ttu-id="76855-309">厳密に型指定されたリソース クラスを生成するためのリソース ファイルのファイル名 (拡張子を含む)。</span><span class="sxs-lookup"><span data-stu-id="76855-309">The file name, including the extension, of the resource file for which to generate a strongly typed resource class.</span></span> <span data-ttu-id="76855-310">ファイルは、テキスト ベース、XML ベース、または .resources バイナリ ファイルです。 .txt、.restext、.resw、または .resources 拡張子を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="76855-310">The file can be a text-based, XML-based, or binary .resources file; it can have an extension of .txt, .restext, .resw, or .resources.</span></span>  
  
 `outputFilename`  
 <span data-ttu-id="76855-311">出力ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="76855-311">The name of the output file.</span></span> <span data-ttu-id="76855-312">`outputFilename` でディレクトリ パスが示されている場合、ディレクトリが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-312">If `outputFilename` includes a directory path, the directory must exist.</span></span> <span data-ttu-id="76855-313">`outputFilename` を省略した場合は、Resgen.exe が `inputFilename` と同じディレクトリに `inputFilename` のルート ファイル名の .resources ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="76855-313">If you omit `outputFilename`, Resgen.exe creates a .resources file with the root file name of `inputFilename` in the same directory as `inputFilename`.</span></span>  
  
 <span data-ttu-id="76855-314">`outputFilename` は、テキスト ベース、XML ベース、またはバイナリ .resources ファイルです。</span><span class="sxs-lookup"><span data-stu-id="76855-314">`outputFilename` can be a text-based, XML-based, or binary .resources file.</span></span> <span data-ttu-id="76855-315">`outputFilename` の拡張子が `inputFilename` のファイル拡張子と異なる場合は、Resgen.exe でファイル変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="76855-315">If the file extension of `outputFilename` is different from the file extension of `inputFilename`, Resgen.exe performs the file conversion.</span></span>  
  
 <span data-ttu-id="76855-316">`inputFilename` が .resources ファイルで、`outputFilename` も .resources ファイルである場合は、Resgen.exe で .resources ファイルがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="76855-316">If `inputFilename` is a .resources file, Resgen.exe copies the .resources file if `outputFilename` is also a .resources file.</span></span> <span data-ttu-id="76855-317">`outputFilename` を省略すると、Resgen.exe で `inputFilename` が同一の .resources ファイルで上書きされます。</span><span class="sxs-lookup"><span data-stu-id="76855-317">If `outputFilename` is omitted, Resgen.exe overwrites `inputFilename` with an identical .resources file.</span></span>  
  
 <span data-ttu-id="76855-318">*language*</span><span class="sxs-lookup"><span data-stu-id="76855-318">*language*</span></span>  
 <span data-ttu-id="76855-319">厳密な型のリソース クラスのソース コードの生成に使用する言語。</span><span class="sxs-lookup"><span data-stu-id="76855-319">The language in which to generate source code for the strongly typed resource class.</span></span> <span data-ttu-id="76855-320">指定できる値は、C# コードの場合は `cs`、`C#`、`csharp`、Visual Basic コードの場合は `vb`、`visualbasic`、VBScript コードの場合は `vbs`、`vbscript`、C++ コードの場合は `c++`、`mc`、`cpp` です。</span><span class="sxs-lookup"><span data-stu-id="76855-320">Possible values are `cs`, `C#`, and `csharp` for C# code, `vb` and `visualbasic` for Visual Basic code, `vbs` and `vbscript` for VBScript code, and `c++`, `mc`, and `cpp` for C++ code.</span></span>  
  
 <span data-ttu-id="76855-321">*namespace*</span><span class="sxs-lookup"><span data-stu-id="76855-321">*namespace*</span></span>  
 <span data-ttu-id="76855-322">厳密に型指定したクラスを含む名前空間。</span><span class="sxs-lookup"><span data-stu-id="76855-322">The namespace that contains the strongly typed resource class.</span></span> <span data-ttu-id="76855-323">.resources ファイルおよびリソース クラスは、同じ名前空間を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-323">The .resources file and the resource class should have the same namespace.</span></span> <span data-ttu-id="76855-324">`outputFilename` で名前空間を指定する場合については、「[リソースのバイナリ ファイルへのコンパイル](resgen-exe-resource-file-generator.md#Compiling)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76855-324">For information about specifying the namespace in the `outputFilename`, see [Compiling Resources into a Binary File](resgen-exe-resource-file-generator.md#Compiling).</span></span> <span data-ttu-id="76855-325">*namespace* を省略すると、リソース クラスは、名前空間に含まれなくなります。</span><span class="sxs-lookup"><span data-stu-id="76855-325">If *namespace* is omitted, the resource class is not contained in a namespace.</span></span>  
  
 <span data-ttu-id="76855-326">*classname*</span><span class="sxs-lookup"><span data-stu-id="76855-326">*classname*</span></span>  
 <span data-ttu-id="76855-327">厳密な型のリソース クラスの名前。</span><span class="sxs-lookup"><span data-stu-id="76855-327">The name of the strongly typed resource class.</span></span> <span data-ttu-id="76855-328">これは、.resources ファイルのルート名に対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-328">This should correspond to the root name of the .resources file.</span></span> <span data-ttu-id="76855-329">たとえば、Resgen.exe で MyCompany.Libraries.Strings.resources という名前の .resources ファイルが生成される場合、厳密に型指定されたリソース クラスの名前は Strings になります。</span><span class="sxs-lookup"><span data-stu-id="76855-329">For example, if Resgen.exe generates a .resources file named MyCompany.Libraries.Strings.resources, the name of the strongly typed resource class is Strings.</span></span> <span data-ttu-id="76855-330">If *classname* を省略すると、生成されるクラスは `outputFilename` のルート名から派生します。</span><span class="sxs-lookup"><span data-stu-id="76855-330">If *classname* is omitted, the generated class is derived from the root name of `outputFilename`.</span></span> <span data-ttu-id="76855-331">If `outputFilename` を省略すると、生成されるクラスは `inputFilename` のルート名から派生します。</span><span class="sxs-lookup"><span data-stu-id="76855-331">If `outputFilename` is omitted, the generated class is derived from the root name of `inputFilename`.</span></span>  
  
 <span data-ttu-id="76855-332">*classname* には、埋め込まれた空白などの無効な文字を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="76855-332">*classname* cannot contain invalid characters such as embedded spaces.</span></span> <span data-ttu-id="76855-333">*classname* に空白が埋め込まれている場合、または *classname* が *inputFilename* から既定で生成されて、*inputFilename* に空白が埋め込まれている場合、Resgen.exe によって無効な文字がすべてアンダースコア (\_) に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="76855-333">If *classname* contains embedded spaces, or if *classname* is generated by default from *inputFilename*, and *inputFilename* contains embedded spaces, Resgen.exe replaces all invalid characters with an underscore (\_).</span></span>  
  
 <span data-ttu-id="76855-334">*ファイル名*</span><span class="sxs-lookup"><span data-stu-id="76855-334">*filename*</span></span>  
 <span data-ttu-id="76855-335">クラス ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="76855-335">The name of the class file.</span></span>  
  
 `/publicclass`  
 <span data-ttu-id="76855-336">厳密に型指定されたリソース クラスを `internal` (C# の場合) または `Friend` (Visual Basic) ではなくパブリックにします。</span><span class="sxs-lookup"><span data-stu-id="76855-336">Makes the strongly typed resource class public rather than `internal` (in C#) or `Friend` (in Visual Basic).</span></span> <span data-ttu-id="76855-337">これにより、リソースには、それ自体が埋め込まれているアセンブリの外部からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="76855-337">This allows the resources to be accessed from outside the assembly in which they are embedded.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="76855-338">厳密に型指定されたリソース クラスを作成するときは、生成されたコードの名前空間とクラス名に .resources ファイルの名前を合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="76855-338">When you create a strongly typed resource class, the name of your .resources file must match the namespace and class name of the generated code.</span></span> <span data-ttu-id="76855-339">ただし、Resgen.exe では、互換性のない名前の .resources ファイルを生成するオプションを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="76855-339">However, Resgen.exe allows you to specify options that produce a .resources file that has an incompatible name.</span></span> <span data-ttu-id="76855-340">この動作を回避するには、出力ファイルの生成後にその名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="76855-340">To work around this behavior, rename the output file after it has been generated.</span></span>  
  
 <span data-ttu-id="76855-341">厳密に型指定されたリソース クラスには、次のメンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="76855-341">The strongly typed resource class has the following members:</span></span>  
  
- <span data-ttu-id="76855-342">厳密に入力されたリソース クラスをインスタンス化するために使用できる、パラメーターなしのコンストラクター。</span><span class="sxs-lookup"><span data-stu-id="76855-342">A parameterless constructor, which can be used to instantiate the strongly typed resource class.</span></span>  
  
- <span data-ttu-id="76855-343">`static` (C#) または `Shared` (Visual Basic)、および厳密に入力されたリソースを管理する `ResourceManager` のインスタンスを返す読み取り専用 <xref:System.Resources.ResourceManager> プロパティ。</span><span class="sxs-lookup"><span data-stu-id="76855-343">A `static` (C#) or `Shared` (Visual Basic) and read-only `ResourceManager` property, which returns the <xref:System.Resources.ResourceManager> instance that manages the strongly typed resource.</span></span>  
  
- <span data-ttu-id="76855-344">リソース検索に使用するカルチャを設定する `Culture` 静的プロパティ。</span><span class="sxs-lookup"><span data-stu-id="76855-344">A static `Culture` property, which allows you to set the culture used for resource retrieval.</span></span> <span data-ttu-id="76855-345">既定値は `null` です。したがって、現在の UI カルチャが使用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="76855-345">By default, its value is `null`, which means that the current UI culture is used.</span></span>  
  
- <span data-ttu-id="76855-346">1 つの `static` (C#) または `Shared` (Visual Basic)、および .resources ファイルのリソースごとの読み取り専用プロパティ。</span><span class="sxs-lookup"><span data-stu-id="76855-346">One `static` (C#) or `Shared` (Visual Basic) and read-only property for each resource in the .resources file.</span></span> <span data-ttu-id="76855-347">プロパティの名前はリソースの名前です。</span><span class="sxs-lookup"><span data-stu-id="76855-347">The name of the property is the name of the resource.-</span></span>  
  
 <span data-ttu-id="76855-348">たとえば、次のコマンドでは、StringResources.txt という名前のリソース ファイルを StringResources.resources にコンパイルし、リソース マネージャーへのアクセスに使用できる StringResources.vb という名前の Visual Basic ソース コード ファイルに `StringResources` という名前のクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="76855-348">For example, the following command compiles a resource file named StringResources.txt into StringResources.resources and generates a class named `StringResources` in a Visual Basic source code file named StringResources.vb that can be used to access the Resource Manager.</span></span>  
  
```console  
resgen StringResources.txt /str:vb,,StringResources
```  
  
## <a name="see-also"></a><span data-ttu-id="76855-349">関連項目</span><span class="sxs-lookup"><span data-stu-id="76855-349">See also</span></span>

- [<span data-ttu-id="76855-350">ツール</span><span class="sxs-lookup"><span data-stu-id="76855-350">Tools</span></span>](index.md)
- [<span data-ttu-id="76855-351">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="76855-351">Resources in Desktop Apps</span></span>](../resources/index.md)
- [<span data-ttu-id="76855-352">リソース ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="76855-352">Creating Resource Files</span></span>](../resources/creating-resource-files-for-desktop-apps.md)
- [<span data-ttu-id="76855-353">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="76855-353">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="76855-354">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="76855-354">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
