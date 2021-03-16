---
title: Ilasm.exe (IL アセンブラー)
description: Ilasm.exe (IL アセンブラー) を使用して作業を開始します。 このツールによって、中間言語 (IL) アセンブリからポータブル実行可能 (PE) ファイルが生成されます。
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: be654c27af2b3e0e281c734069f2de469b901446
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258040"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="3a32f-104">Ilasm.exe (IL アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="3a32f-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="3a32f-105">IL アセンブラーにより、中間言語 (IL) アセンブリからポータブル実行可能 (PE) ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL) assembly.</span></span> <span data-ttu-id="3a32f-106">(IL の詳細については、「[マネージド実行プロセス](../../standard/managed-execution-process.md)」を参照してください)。IL と必要なメタデータを含む実行可能ファイルを実行すると、IL が予測どおりに動作するかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="3a32f-107">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="3a32f-108">ツールを実行するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-108">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

<span data-ttu-id="3a32f-109">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-109">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="3a32f-110">構文</span><span class="sxs-lookup"><span data-stu-id="3a32f-110">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="3a32f-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3a32f-111">Parameters</span></span>

| <span data-ttu-id="3a32f-112">引数</span><span class="sxs-lookup"><span data-stu-id="3a32f-112">Argument</span></span> | <span data-ttu-id="3a32f-113">説明</span><span class="sxs-lookup"><span data-stu-id="3a32f-113">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="3a32f-114">.il ソース ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="3a32f-114">The name of the .il source file.</span></span> <span data-ttu-id="3a32f-115">このファイルは、メタデータ宣言ディレクティブとシンボリック IL 命令で構成されます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-115">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="3a32f-116">複数のソース ファイル引数を指定すると、*Ilasm.exe* で 1 つの PE ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-116">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="3a32f-117">**注:** .il ソース ファイルのコードの最後の行に、後続の空白または行末文字のいずれかがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3a32f-117">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="3a32f-118">オプション</span><span class="sxs-lookup"><span data-stu-id="3a32f-118">Option</span></span> | <span data-ttu-id="3a32f-119">説明</span><span class="sxs-lookup"><span data-stu-id="3a32f-119">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="3a32f-120">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="3a32f-120">**/32bitpreferred**</span></span>|<span data-ttu-id="3a32f-121">32 ビット優先イメージ (PE32) を作成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-121">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="3a32f-122">**/alignment:** `integer`</span><span class="sxs-lookup"><span data-stu-id="3a32f-122">**/alignment:** `integer`</span></span>|<span data-ttu-id="3a32f-123">NT オプション ヘッダーの FileAlignment を `integer` で指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-123">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="3a32f-124">このオプションは、ファイル指定されている .alignment IL ディレクティブをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3a32f-124">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="3a32f-125">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="3a32f-125">**/appcontainer**</span></span>|<span data-ttu-id="3a32f-126">出力として、Windows アプリ コンテナー内で実行する *.dll* ファイルまたは *.exe* ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-126">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="3a32f-127">**/arm**</span><span class="sxs-lookup"><span data-stu-id="3a32f-127">**/arm**</span></span>|<span data-ttu-id="3a32f-128">ターゲット プロセッサとして Advanced RISC Machine (ARM) を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-128">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="3a32f-129">イメージのビット数を指定しない場合、既定は **/32bitpreferred** です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-129">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="3a32f-130">**/base:** `integer`</span><span class="sxs-lookup"><span data-stu-id="3a32f-130">**/base:** `integer`</span></span>|<span data-ttu-id="3a32f-131">NT オプション ヘッダーの ImageBase を `integer` で指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-131">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="3a32f-132">このオプションは、ファイルに指定されている .imagebase IL ディレクティブをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3a32f-132">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="3a32f-133">**/clock**</span><span class="sxs-lookup"><span data-stu-id="3a32f-133">**/clock**</span></span>|<span data-ttu-id="3a32f-134">指定した .il ソース ファイルのコンパイル時間を計測して報告します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-134">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="3a32f-135">**Total Run**: 後に続く特定の操作の実行に要した合計時間。</span><span class="sxs-lookup"><span data-stu-id="3a32f-135">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="3a32f-136">**Startup**: ファイルを読み込み、開く。</span><span class="sxs-lookup"><span data-stu-id="3a32f-136">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="3a32f-137">**Emitting MD**:メタデータの出力。</span><span class="sxs-lookup"><span data-stu-id="3a32f-137">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="3a32f-138">**Ref to Def Resolution**: ファイルの定義への参照の解決。</span><span class="sxs-lookup"><span data-stu-id="3a32f-138">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="3a32f-139">**CEE File Generation**: メモリ内のファイル イメージの生成。</span><span class="sxs-lookup"><span data-stu-id="3a32f-139">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="3a32f-140">**PE File Writing**: PE へのイメージの書き込み。</span><span class="sxs-lookup"><span data-stu-id="3a32f-140">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="3a32f-141">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="3a32f-141">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="3a32f-142">デバッグ情報 (ローカル変数と引数名、および行番号) を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-142">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="3a32f-143">PDB ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-143">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="3a32f-144">**/debug** に値を追加しなければ、JIT の最適化が無効になり、PDB ファイルのシーケンス ポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-144">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="3a32f-145">**IMPL** を指定すると、JIT 最適化が無効になり、暗黙のシーケンス ポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-145">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="3a32f-146">**OPT** を指定すると、JIT 最適化が有効になり、暗黙のシーケンス ポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-146">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="3a32f-147">**/dll**</span><span class="sxs-lookup"><span data-stu-id="3a32f-147">**/dll**</span></span>|<span data-ttu-id="3a32f-148">出力として *.dll* ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-148">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="3a32f-149">**/enc:** `file`</span><span class="sxs-lookup"><span data-stu-id="3a32f-149">**/enc:** `file`</span></span>|<span data-ttu-id="3a32f-150">指定されたソース ファイルからエディット コンティニュ デルタを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-150">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="3a32f-151">この引数は教育機関専用のため、商業目的の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-151">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="3a32f-152">**/exe**</span><span class="sxs-lookup"><span data-stu-id="3a32f-152">**/exe**</span></span>|<span data-ttu-id="3a32f-153">出力として実行可能ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-153">Produces an executable file as output.</span></span> <span data-ttu-id="3a32f-154">既定値です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-154">This is the default.</span></span>|
|<span data-ttu-id="3a32f-155">**/flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="3a32f-155">**/flags:** `integer`</span></span>|<span data-ttu-id="3a32f-156">共通言語ランタイム ヘッダーの ImageFlags を `integer` で指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-156">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="3a32f-157">このオプションは、ファイルに指定されている .corflags IL ディレクティブをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3a32f-157">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="3a32f-158">有効な *integer* の値の一覧については、CorHdr.h で COMIMAGE_FLAGS を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a32f-158">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="3a32f-159">**/fold**</span><span class="sxs-lookup"><span data-stu-id="3a32f-159">**/fold**</span></span>|<span data-ttu-id="3a32f-160">複数の同じメソッド本体を 1 つに折りたたみます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-160">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="3a32f-161">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="3a32f-161">/**highentropyva**</span></span>|<span data-ttu-id="3a32f-162">高エントロピ ASLR (Address Space Layout Randomization) をサポートする出力実行可能プログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-162">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="3a32f-163">(既定では **/appcontainer**)。</span><span class="sxs-lookup"><span data-stu-id="3a32f-163">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="3a32f-164">**/include:** `includePath`</span><span class="sxs-lookup"><span data-stu-id="3a32f-164">**/include:** `includePath`</span></span>|<span data-ttu-id="3a32f-165">`#include`によってインクルードされるファイルの検索パスを設定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-165">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="3a32f-166">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="3a32f-166">**/itanium**</span></span>|<span data-ttu-id="3a32f-167">ターゲット プロセッサとして Intel Itanium を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-167">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="3a32f-168">イメージのビット数を指定しない場合、既定は **/pe64** です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-168">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="3a32f-169">**/key:** `keyFile`</span><span class="sxs-lookup"><span data-stu-id="3a32f-169">**/key:** `keyFile`</span></span>|<span data-ttu-id="3a32f-170">`filename` に含まれる秘密キーを使って、厳密な署名を持つ `keyFile` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3a32f-170">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="3a32f-171">**/key:**  @`keySource`</span><span class="sxs-lookup"><span data-stu-id="3a32f-171">**/key:** @`keySource`</span></span>|<span data-ttu-id="3a32f-172">`filename` で生成された秘密キーを使って、厳密な署名を持つ `keySource` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3a32f-172">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="3a32f-173">**/listing**</span><span class="sxs-lookup"><span data-stu-id="3a32f-173">**/listing**</span></span>|<span data-ttu-id="3a32f-174">標準出力にリスティング ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-174">Produces a listing file on the standard output.</span></span> <span data-ttu-id="3a32f-175">このオプションを省略すると、リスティング ファイルは生成されません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-175">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="3a32f-176">このパラメーターは、.NET Framework 2.0 以降ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-176">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="3a32f-177">**/mdv:** `versionString`</span><span class="sxs-lookup"><span data-stu-id="3a32f-177">**/mdv:** `versionString`</span></span>|<span data-ttu-id="3a32f-178">メタデータのバージョン文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-178">Sets the metadata version string.</span></span>|
|<span data-ttu-id="3a32f-179">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="3a32f-179">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="3a32f-180">メタデータのストリーム バージョンを設定します。ここで、 `major` と `minor` は整数です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-180">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="3a32f-181">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="3a32f-181">**/noautoinherit**</span></span>|<span data-ttu-id="3a32f-182">基底クラスが指定されていない場合、 <xref:System.Object> からの既定の継承を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3a32f-182">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="3a32f-183">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="3a32f-183">**/nocorstub**</span></span>|<span data-ttu-id="3a32f-184">CORExeMain スタブの生成を抑止します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-184">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="3a32f-185">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="3a32f-185">**/nologo**</span></span>|<span data-ttu-id="3a32f-186">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-186">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="3a32f-187">**/output:** `file.ext`</span><span class="sxs-lookup"><span data-stu-id="3a32f-187">**/output:** `file.ext`</span></span>|<span data-ttu-id="3a32f-188">出力ファイルの名前と拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-188">Specifies the output file name and extension.</span></span> <span data-ttu-id="3a32f-189">既定では、出力ファイルの名前は最初のソース ファイルの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="3a32f-189">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="3a32f-190">既定の拡張子は *.exe* です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-190">The default extension is *.exe*.</span></span> <span data-ttu-id="3a32f-191">**/dll** オプションを指定した場合の既定の拡張子は *.dll* です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-191">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="3a32f-192">**注:** **/output** :myfile.dll と指定しても **/dll** オプションは設定されません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-192">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="3a32f-193">**/dll** を指定しないと、*myfile.dll* という名前の実行可能ファイルになります。</span><span class="sxs-lookup"><span data-stu-id="3a32f-193">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="3a32f-194">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="3a32f-194">**/optimize**</span></span>|<span data-ttu-id="3a32f-195">長いインストラクションを短く最適化します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-195">Optimizes long instructions to short.</span></span> <span data-ttu-id="3a32f-196">たとえば `br` を `br.s`にします。</span><span class="sxs-lookup"><span data-stu-id="3a32f-196">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="3a32f-197">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="3a32f-197">**/pe64**</span></span>|<span data-ttu-id="3a32f-198">64 ビットのイメージ (PE32+) を作成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-198">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="3a32f-199">ターゲット プロセッサを指定しない場合、既定は `/itanium`です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-199">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="3a32f-200">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="3a32f-200">**/pdb**</span></span>|<span data-ttu-id="3a32f-201">デバッグ情報の追跡を有効にせずに PDB ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-201">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="3a32f-202">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="3a32f-202">**/quiet**</span></span>|<span data-ttu-id="3a32f-203">クワイエット モードを指定します。アセンブリの進行状況はレポートされません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-203">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="3a32f-204">**/resource:** `file.res`</span><span class="sxs-lookup"><span data-stu-id="3a32f-204">**/resource:** `file.res`</span></span>|<span data-ttu-id="3a32f-205">指定した \*.res 形式のリソース ファイルを生成される *.exe* ファイルまたは *.dll* ファイルに組み込みます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-205">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="3a32f-206">**/resource** オプションで指定できる .res ファイルは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="3a32f-206">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="3a32f-207">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="3a32f-207">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="3a32f-208">NT オプション ヘッダーのサブシステム バージョン番号を設定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-208">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="3a32f-209">**/appcontainer** および **/arm** では、最小バージョン番号は 6.02 です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-209">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="3a32f-210">**/stack:** `stackSize`</span><span class="sxs-lookup"><span data-stu-id="3a32f-210">**/stack:** `stackSize`</span></span>|<span data-ttu-id="3a32f-211">NT Optional ヘッダーの SizeOfStackReserve 値を `stackSize`に設定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-211">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="3a32f-212">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="3a32f-212">**/stripreloc**</span></span>|<span data-ttu-id="3a32f-213">ベースの再配置が不要であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-213">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="3a32f-214">**/subsystem:** `integer`</span><span class="sxs-lookup"><span data-stu-id="3a32f-214">**/subsystem:** `integer`</span></span>|<span data-ttu-id="3a32f-215">NT オプション ヘッダーのサブシステムを `integer` で指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-215">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="3a32f-216">このコマンドは、ファイルに指定されている .subsystem IL ディレクティブをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3a32f-216">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="3a32f-217">有効な `integer` の値の一覧については、winnt.h で IMAGE_SUBSYSTEM を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a32f-217">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="3a32f-218">**/x64**</span><span class="sxs-lookup"><span data-stu-id="3a32f-218">**/x64**</span></span>|<span data-ttu-id="3a32f-219">ターゲット プロセッサとして 64 ビットの AMD プロセッサを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-219">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="3a32f-220">イメージのビット数を指定しない場合、既定は **/pe64** です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-220">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="3a32f-221">**/?**</span><span class="sxs-lookup"><span data-stu-id="3a32f-221">**/?**</span></span>|<span data-ttu-id="3a32f-222">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-222">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="3a32f-223">*Ilasm.exe* に関するすべてのオプションでは大文字と小文字が区別されず、先頭の 3 文字で認識されます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-223">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="3a32f-224">たとえば、 **/lis** は **/listing** と等価であり、 **/res:** myresfile.res は **/resource:** myresfile.res と等価です。引数を伴うオプションの場合は、オプションと引数の間に区切り記号としてコロン (:) または等号 (=) を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-224">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="3a32f-225">たとえば、 **/output**:*file.ext* は **/output**=*file.ext* と等価です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-225">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a32f-226">Remarks</span><span class="sxs-lookup"><span data-stu-id="3a32f-226">Remarks</span></span>

<span data-ttu-id="3a32f-227">IL アセンブラーは、IL ジェネレーターを設計および実装するツールの販売元を支援します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-227">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="3a32f-228">ツールとコンパイラの開発者は、*Ilasm.exe* を使用することで、PE ファイル形式での IL の出力にかかわることなく、IL とメタデータの生成に集中できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-228">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="3a32f-229">C# および Visual Basic など、ランタイムを対象とした他のコンパイラと同様に、*Ilasm.exe* も中間オブジェクト ファイルを生成しません。このため、PE ファイルを形成するためのリンク ステージが必要ありません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-229">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="3a32f-230">IL アセンブラーは、すべての既存メタデータ、およびランタイムを対象としたプログラミング言語の IL 機能を表現できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-230">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="3a32f-231">このため、このようなプログラミング言語で記述されたマネージド コードを IL アセンブラーで適切に表現し、*Ilasm.exe* でコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-231">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="3a32f-232">.il ソース ファイルのコードの最後の行に、後続の空白または行末文字がない場合、コンパイルに失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="3a32f-232">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="3a32f-233">*Ilasm.exe* と、その対をなすツール [*Ildasm.exe*](ildasm-exe-il-disassembler.md) を併用できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-233">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="3a32f-234">*Ildasm.exe* は、IL コードを含む PE ファイルを使用して、*Ilasm.exe* への入力として適したテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-234">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="3a32f-235">これは、必ずしもランタイム メタデータ属性のすべてをサポートしないプログラミング言語で記述されたコードをコンパイルするときなどに便利です。</span><span class="sxs-lookup"><span data-stu-id="3a32f-235">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="3a32f-236">コードをコンパイルし、その出力を *Ildasm.exe* で実行した後、生成された IL テキスト ファイルを手作業で編集して足りない属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-236">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="3a32f-237">このテキスト ファイルを *Ilasm.exe* で実行すると、最終的な実行可能ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-237">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="3a32f-238">この方法を使用して、異なるコンパイラによって生成された複数の PE ファイルから 1 つの PE ファイルを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-238">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="3a32f-239">現時点では、埋め込みのネイティブ コード (たとえば Visual C++ で生成された PE ファイル) を含む PE ファイルについては、この手法を使用できません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-239">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="3a32f-240">この *Ildasm.exe* と *Ilasm.exe* の組み合わせをできる限り正確に使用するため、アセンブラーは、既定では、IL ソース内に記述されている可能性がある (または別のコンパイラによって出力される可能性がある) 長いエンコーディングを短いエンコーディングに置換しません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-240">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="3a32f-241">可能な場合は、常に **/optimize** オプションを使用して、短いエンコーディングを置換します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-241">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="3a32f-242">*Ildasm.exe* はディスク上のファイルについてだけ動作します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-242">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="3a32f-243">グローバル アセンブリ キャッシュ内にインストールされたファイルについては動作しません。</span><span class="sxs-lookup"><span data-stu-id="3a32f-243">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="3a32f-244">IL の文法の詳細については、Windows SDK の asmparse.grammar ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a32f-244">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="3a32f-245">バージョン情報</span><span class="sxs-lookup"><span data-stu-id="3a32f-245">Version Information</span></span>

<span data-ttu-id="3a32f-246">.NET Framework 4.5 以降では、次に類似するコードを使用することで、インターフェイス実装にカスタム属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-246">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="3a32f-247">.NET Framework 4.5 以降では、次のコードに示すように、未処理のバイナリ表現を使用することで、任意のマーシャリング BLOB (バイナリ ラージ オブジェクト) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-247">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="3a32f-248">IL の文法の詳細については、Windows SDK の asmparse.grammar ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a32f-248">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="3a32f-249">使用例</span><span class="sxs-lookup"><span data-stu-id="3a32f-249">Examples</span></span>

<span data-ttu-id="3a32f-250">IL ファイル *myTestFile.il* をアセンブルして実行可能ファイル *myTestFile.exe* を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-250">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="3a32f-251">IL ファイル *myTestFile.il* をアセンブルして *.dll* ファイル *myTestFile.dll* を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="3a32f-252">IL ファイル *myTestFile.il* をアセンブルして *.dll* ファイル *myNewTestFile.dll* を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3a32f-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="3a32f-253">コンソールに "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3a32f-253">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="3a32f-254">記述するだけです。</span><span class="sxs-lookup"><span data-stu-id="3a32f-254">to the console.</span></span> <span data-ttu-id="3a32f-255">このコードのコンパイル後に [*Ildasm.exe*](ildasm-exe-il-disassembler.md) ツールを使用して、IL ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-255">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="3a32f-256">次の IL コードの例は、前の C# のコード例に対応しています。</span><span class="sxs-lookup"><span data-stu-id="3a32f-256">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="3a32f-257">IL アセンブラー ツールを使うと、このコードをアセンブリにコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="3a32f-257">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="3a32f-258">IL コードと C# コードの例は、どちらもコンソールに "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3a32f-258">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="3a32f-259">記述するだけです。</span><span class="sxs-lookup"><span data-stu-id="3a32f-259">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="3a32f-260">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a32f-260">See also</span></span>

- [<span data-ttu-id="3a32f-261">ツール</span><span class="sxs-lookup"><span data-stu-id="3a32f-261">Tools</span></span>](index.md)
- [<span data-ttu-id="3a32f-262">*Ildasm.exe* (IL 逆アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="3a32f-262">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="3a32f-263">マネージド実行プロセス</span><span class="sxs-lookup"><span data-stu-id="3a32f-263">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="3a32f-264">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="3a32f-264">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
