---
title: Lc.exe (ライセンス コンパイラ)
description: Lc.exe (ライセンス コンパイラ) を使用します。 このツールは、ライセンス情報を含むテキスト ファイルを読み取り、CLR 実行可能ファイルにリソースとして埋め込むバイナリ ファイルを作成します。
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 1a9806cd71f9990d9ce70b35b3af760a22347003
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258804"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="388c1-104">Lc.exe (ライセンス コンパイラ)</span><span class="sxs-lookup"><span data-stu-id="388c1-104">Lc.exe (License Compiler)</span></span>

<span data-ttu-id="388c1-105">ライセンス コンパイラは、ライセンス情報を含むテキスト ファイルを読み込んで、バイナリ ファイルを生成します。このバイナリ ファイルは、リソースとして共通言語ランタイムの実行可能ファイルに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="388c1-105">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="388c1-106">.licx テキスト ファイルは、ライセンスされたコントロールがフォームに追加されると、Windows フォーム デザイナーによって自動的に生成または更新されます。</span><span class="sxs-lookup"><span data-stu-id="388c1-106">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="388c1-107">プロジェクト システムは、コンパイルの過程で、.licx テキスト ファイルを、.NET のコントロール ライセンス サポートを提供する .licenses バイナリのリソースに変換します。</span><span class="sxs-lookup"><span data-stu-id="388c1-107">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="388c1-108">バイナリのリソースは、その後、プロジェクト出力に埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="388c1-108">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="388c1-109">プロジェクトをビルドするときにライセンス コンパイラを使用した場合は、32 ビットと 64 ビットの間のクロス コンパイルはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="388c1-109">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="388c1-110">これは、ライセンス コンパイラはアセンブリを読み込む必要があり、32 ビット アプリケーションからの 64 ビット アセンブリの読み込みおよびその逆は、許可されないためです。</span><span class="sxs-lookup"><span data-stu-id="388c1-110">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="388c1-111">この場合は、コマンド ラインからライセンス コンパイラを使用して手動でライセンスをコンパイルし、対応するアーキテクチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="388c1-111">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="388c1-112">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="388c1-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="388c1-113">ツールを実行するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。</span><span class="sxs-lookup"><span data-stu-id="388c1-113">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="388c1-114">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="388c1-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388c1-115">構文</span><span class="sxs-lookup"><span data-stu-id="388c1-115">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="388c1-116">オプション</span><span class="sxs-lookup"><span data-stu-id="388c1-116">Option</span></span>|<span data-ttu-id="388c1-117">説明</span><span class="sxs-lookup"><span data-stu-id="388c1-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="388c1-118">**/complist:** *filename*</span><span class="sxs-lookup"><span data-stu-id="388c1-118">**/complist:** *filename*</span></span>|<span data-ttu-id="388c1-119">.licenses ファイルに組み込むライセンス付きコンポーネントの一覧を含むファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="388c1-119">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="388c1-120">各コンポーネントを参照するにはフルネームを使用し、各行にコンポーネントを 1 つだけ指定します。</span><span class="sxs-lookup"><span data-stu-id="388c1-120">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="388c1-121">コマンド行を使用する場合は、プロジェクトに属するフォームごとに個別のファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="388c1-121">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="388c1-122">Lc.exe は複数の入力ファイルを受け付けて、1 つの .licenses ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="388c1-122">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="388c1-123">**/h** **[elp]**</span><span class="sxs-lookup"><span data-stu-id="388c1-123">**/h**[**elp**]</span></span>|<span data-ttu-id="388c1-124">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="388c1-124">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="388c1-125">**/i:** *module*</span><span class="sxs-lookup"><span data-stu-id="388c1-125">**/i:** *module*</span></span>|<span data-ttu-id="388c1-126">**/complist** ファイル内に一覧表示されたコンポーネントを含むモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="388c1-126">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="388c1-127">複数のモジュールを指定するには、複数の **/i** フラグを使用します。</span><span class="sxs-lookup"><span data-stu-id="388c1-127">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="388c1-128">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="388c1-128">**/nologo**</span></span>|<span data-ttu-id="388c1-129">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="388c1-129">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="388c1-130">**/outdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="388c1-130">**/outdir:** *path*</span></span>|<span data-ttu-id="388c1-131">出力 .licenses ファイルを格納するディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="388c1-131">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="388c1-132">**/target:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="388c1-132">**/target:** *targetPE*</span></span>|<span data-ttu-id="388c1-133">.licenses ファイルを生成する実行可能ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="388c1-133">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="388c1-134">**/v**</span><span class="sxs-lookup"><span data-stu-id="388c1-134">**/v**</span></span>|<span data-ttu-id="388c1-135">詳細出力モードを指定します。コンパイルの進行状況に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="388c1-135">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="388c1-136">**@** *file*</span><span class="sxs-lookup"><span data-stu-id="388c1-136">**@** *file*</span></span>|<span data-ttu-id="388c1-137">応答 (.rsp) ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="388c1-137">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="388c1-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="388c1-138">**/?**</span></span>|<span data-ttu-id="388c1-139">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="388c1-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="388c1-140">例</span><span class="sxs-lookup"><span data-stu-id="388c1-140">Example</span></span>  
  
1. <span data-ttu-id="388c1-141">`HostApp.exe` という名前のアプリケーション内の `Samples.DLL` に格納されているライセンス付きコントロール `MyCompany.Samples.LicControl1` を使用すると *、* 次の内容を含む `HostAppLic.txt` を作成できます。</span><span class="sxs-lookup"><span data-stu-id="388c1-141">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="388c1-142">`HostApp.exe.licenses` という名前の .licenses ファイルを次のコマンドで作成します。</span><span class="sxs-lookup"><span data-stu-id="388c1-142">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="388c1-143">この .licenses ファイルをリソースとして含む  `HostApp.exe` を作成します。</span><span class="sxs-lookup"><span data-stu-id="388c1-143">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="388c1-144">C# アプリケーションを作成していた場合は、次のコマンドを使用してアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="388c1-144">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="388c1-145">`myApp.licenses`、`hostapplic.txt`、および `hostapplic2.txt` で指定されるライセンス付きコンポーネントの一覧から `hostapplic3.txt` をコンパイルするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="388c1-145">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="388c1-146">引数 `modulesList` によって、ライセンス付きコンポーネントを含むモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="388c1-146">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="388c1-147">応答ファイルの例</span><span class="sxs-lookup"><span data-stu-id="388c1-147">Response File Example</span></span>  

 <span data-ttu-id="388c1-148">次のリストは、`response.rsp` 応答ファイルの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="388c1-148">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="388c1-149">応答ファイルの詳細については、「[応答ファイル](/visualstudio/msbuild/msbuild-response-files)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="388c1-149">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="388c1-150">次のコマンドラインで、この `response.rsp` ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="388c1-150">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="388c1-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="388c1-151">See also</span></span>

- [<span data-ttu-id="388c1-152">ツール</span><span class="sxs-lookup"><span data-stu-id="388c1-152">Tools</span></span>](index.md)
- [<span data-ttu-id="388c1-153">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="388c1-153">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="388c1-154">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="388c1-154">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
