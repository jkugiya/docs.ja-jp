---
title: Ildasm.exe (IL 逆アセンブラー)
description: Ildasm.exe (IL Disassembler) を使用します。中間言語 (IL) コードを含む移植可能な実行可能 (PE) ファイルを利用して、Ilasm.exe に対するテキスト ファイルが作成されます。
ms.date: 03/30/2017
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
ms.openlocfilehash: 128257e8b1879ef712dd5c33239784fd03de31e2
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654116"
---
# <a name="ildasmexe-il-disassembler"></a><span data-ttu-id="be1f7-103">Ildasm.exe (IL 逆アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="be1f7-103">Ildasm.exe (IL Disassembler)</span></span>

<span data-ttu-id="be1f7-104">IL 逆アセンブラーは、IL アセンブラー (*Ilasm.exe*) と対をなすツールです。</span><span class="sxs-lookup"><span data-stu-id="be1f7-104">The IL Disassembler is a companion tool to the IL Assembler (*Ilasm.exe*).</span></span> <span data-ttu-id="be1f7-105">*Ildasm.exe* は、中間言語 (IL: Intermediate Language) コードを含む、ポータブル実行可能 (PE) ファイルを使用して、*Ilasm.exe* に対する入力として適したテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-105">*Ildasm.exe* takes a portable executable (PE) file that contains intermediate language (IL) code and creates a text file suitable as input to *Ilasm.exe*.</span></span>

<span data-ttu-id="be1f7-106">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="be1f7-107">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

<span data-ttu-id="be1f7-108">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="be1f7-109">構文</span><span class="sxs-lookup"><span data-stu-id="be1f7-109">Syntax</span></span>

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a><span data-ttu-id="be1f7-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be1f7-110">Parameters</span></span>

<span data-ttu-id="be1f7-111">*.exe*、 *.dll*、 *.obj*、 *.lib*、および *.winmd* の各ファイルについて、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-111">The following options are available for *.exe*, *.dll*, *.obj*, *.lib*, and *.winmd* files.</span></span>

| <span data-ttu-id="be1f7-112">オプション</span><span class="sxs-lookup"><span data-stu-id="be1f7-112">Option</span></span> | <span data-ttu-id="be1f7-113">説明</span><span class="sxs-lookup"><span data-stu-id="be1f7-113">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="be1f7-114">**/out=** `filename`</span><span class="sxs-lookup"><span data-stu-id="be1f7-114">**/out=** `filename`</span></span>|<span data-ttu-id="be1f7-115">結果をグラフィカル ユーザー インターフェイスに表示せずに、指定した `filename` を持つ出力ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-115">Creates an output file with the specified `filename`, rather than displaying the results in a graphical user interface.</span></span>|
|<span data-ttu-id="be1f7-116">**/rtf**</span><span class="sxs-lookup"><span data-stu-id="be1f7-116">**/rtf**</span></span>|<span data-ttu-id="be1f7-117">出力をリッチ テキスト形式で生成します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-117">Produces output in rich text format.</span></span> <span data-ttu-id="be1f7-118">**/text** オプションと共に使用すると無効になります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-118">Invalid with the **/text** option.</span></span>|
|<span data-ttu-id="be1f7-119">**/text**</span><span class="sxs-lookup"><span data-stu-id="be1f7-119">**/text**</span></span>|<span data-ttu-id="be1f7-120">結果をグラフィカル ユーザー インターフェイスまたは出力ファイルに出力せずに、コンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-120">Displays the results to the console window, rather than in a graphical user interface or as an output file.</span></span>|
|<span data-ttu-id="be1f7-121">**/html**</span><span class="sxs-lookup"><span data-stu-id="be1f7-121">**/html**</span></span>|<span data-ttu-id="be1f7-122">出力を HTML 形式で生成します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-122">Produces output in HTML format.</span></span> <span data-ttu-id="be1f7-123">**/output** オプションと共に使用する場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-123">Valid with the **/output** option only.</span></span>|
|<span data-ttu-id="be1f7-124">**/?**</span><span class="sxs-lookup"><span data-stu-id="be1f7-124">**/?**</span></span>|<span data-ttu-id="be1f7-125">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-125">Displays the command syntax and options for the tool.</span></span>|

<span data-ttu-id="be1f7-126">*.exe* ファイル、 *.dll* ファイル、および *.winmd* ファイルについては、次のオプションも利用できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-126">The following additional options are available for *.exe*, *.dll*, and *.winmd* files.</span></span>

| <span data-ttu-id="be1f7-127">オプション</span><span class="sxs-lookup"><span data-stu-id="be1f7-127">Option</span></span> | <span data-ttu-id="be1f7-128">説明</span><span class="sxs-lookup"><span data-stu-id="be1f7-128">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="be1f7-129">**/bytes**</span><span class="sxs-lookup"><span data-stu-id="be1f7-129">**/bytes**</span></span>|<span data-ttu-id="be1f7-130">実際のバイトを 16 進形式の命令コメントとして表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-130">Shows actual bytes, in hexadecimal format, as instruction comments.</span></span>|
|<span data-ttu-id="be1f7-131">**/caverbal**</span><span class="sxs-lookup"><span data-stu-id="be1f7-131">**/caverbal**</span></span>|<span data-ttu-id="be1f7-132">カスタム属性の BLOB を Verbal 形式で生成します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-132">Produces custom attribute blobs in verbal form.</span></span> <span data-ttu-id="be1f7-133">既定はバイナリ形式です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-133">The default is binary form.</span></span>|
|<span data-ttu-id="be1f7-134">**/linenum**</span><span class="sxs-lookup"><span data-stu-id="be1f7-134">**/linenum**</span></span>|<span data-ttu-id="be1f7-135">元のソース行への参照を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-135">Includes references to original source lines.</span></span>|
|<span data-ttu-id="be1f7-136">**/nobar**</span><span class="sxs-lookup"><span data-stu-id="be1f7-136">**/nobar**</span></span>|<span data-ttu-id="be1f7-137">逆アセンブルのプログレス インジケーター ポップアップ ウィンドウの表示を中止します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-137">Suppresses the disassembly progress indicator pop-up window.</span></span>|
|<span data-ttu-id="be1f7-138">**/noca**</span><span class="sxs-lookup"><span data-stu-id="be1f7-138">**/noca**</span></span>|<span data-ttu-id="be1f7-139">カスタム属性の出力を抑止します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-139">Suppresses the output of custom attributes.</span></span>|
|<span data-ttu-id="be1f7-140">**/project**</span><span class="sxs-lookup"><span data-stu-id="be1f7-140">**/project**</span></span>|<span data-ttu-id="be1f7-141">ネイティブ Windows ランタイムに表示される方法ではなく、マネージド コードに表示される方法でメタデータを示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-141">Displays metadata the way it appears to managed code, instead of the way it appears in the native Windows Runtime.</span></span> <span data-ttu-id="be1f7-142">`PEfilename` が Windows メタデータ ( *.winmd*) ファイルではない場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-142">If `PEfilename` is not a Windows metadata (*.winmd*) file, this option has no effect.</span></span> <span data-ttu-id="be1f7-143">「[Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../cross-platform/support-for-windows-store-apps-and-windows-runtime.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be1f7-143">See [.NET Framework Support for Windows Store Apps and Windows Runtime](../cross-platform/support-for-windows-store-apps-and-windows-runtime.md).</span></span>|
|<span data-ttu-id="be1f7-144">**/pubonly**</span><span class="sxs-lookup"><span data-stu-id="be1f7-144">**/pubonly**</span></span>|<span data-ttu-id="be1f7-145">パブリックな型とメンバーだけを逆アセンブルします。</span><span class="sxs-lookup"><span data-stu-id="be1f7-145">Disassembles only public types and members.</span></span> <span data-ttu-id="be1f7-146">**/visibility:PUB** と等価です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-146">Equivalent to **/visibility:PUB**.</span></span>|
|<span data-ttu-id="be1f7-147">**/quoteallnames**</span><span class="sxs-lookup"><span data-stu-id="be1f7-147">**/quoteallnames**</span></span>|<span data-ttu-id="be1f7-148">すべての名前を単一引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-148">Includes all names in single quotes.</span></span>|
|<span data-ttu-id="be1f7-149">**/raweh**</span><span class="sxs-lookup"><span data-stu-id="be1f7-149">**/raweh**</span></span>|<span data-ttu-id="be1f7-150">例外処理句を生の形式で表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-150">Shows exception handling clauses in raw form.</span></span>|
|<span data-ttu-id="be1f7-151">**/source**</span><span class="sxs-lookup"><span data-stu-id="be1f7-151">**/source**</span></span>|<span data-ttu-id="be1f7-152">元のソース行をコメントとして表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-152">Shows original source lines as comments.</span></span>|
|<span data-ttu-id="be1f7-153">**/tokens**</span><span class="sxs-lookup"><span data-stu-id="be1f7-153">**/tokens**</span></span>|<span data-ttu-id="be1f7-154">クラスとメンバーのメタデータ トークンを表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-154">Shows metadata tokens of classes and members.</span></span>|
|<span data-ttu-id="be1f7-155">**/visibility:** `vis`[+`vis`...]</span><span class="sxs-lookup"><span data-stu-id="be1f7-155">**/visibility:** `vis`[+`vis`...]</span></span>|<span data-ttu-id="be1f7-156">指定した参照可能範囲を持つ型またはメンバーだけを逆アセンブルします。</span><span class="sxs-lookup"><span data-stu-id="be1f7-156">Disassembles only types or members with the specified visibility.</span></span> <span data-ttu-id="be1f7-157">`vis` の有効な値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-157">The following are valid values for `vis`:</span></span><br /><br /> <span data-ttu-id="be1f7-158">**PUB** — Public</span><span class="sxs-lookup"><span data-stu-id="be1f7-158">**PUB** — Public</span></span><br /><br /> <span data-ttu-id="be1f7-159">**PRI** — Private</span><span class="sxs-lookup"><span data-stu-id="be1f7-159">**PRI** — Private</span></span><br /><br /> <span data-ttu-id="be1f7-160">**FAM** — Family</span><span class="sxs-lookup"><span data-stu-id="be1f7-160">**FAM** — Family</span></span><br /><br /> <span data-ttu-id="be1f7-161">**ASM** — Assembly</span><span class="sxs-lookup"><span data-stu-id="be1f7-161">**ASM** — Assembly</span></span><br /><br /> <span data-ttu-id="be1f7-162">**FAA** — Family および Assembly</span><span class="sxs-lookup"><span data-stu-id="be1f7-162">**FAA** — Family and Assembly</span></span><br /><br /> <span data-ttu-id="be1f7-163">**FOA** — Family または Assembly</span><span class="sxs-lookup"><span data-stu-id="be1f7-163">**FOA** — Family or Assembly</span></span><br /><br /> <span data-ttu-id="be1f7-164">**PSC** — Private Scope</span><span class="sxs-lookup"><span data-stu-id="be1f7-164">**PSC** — Private Scope</span></span><br /><br /> <span data-ttu-id="be1f7-165">以上の可視性修飾子の定義については、「<xref:System.Reflection.MethodAttributes>」と「<xref:System.Reflection.TypeAttributes>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be1f7-165">For definitions of these visibility modifiers, see <xref:System.Reflection.MethodAttributes> and <xref:System.Reflection.TypeAttributes>.</span></span>|

<span data-ttu-id="be1f7-166">次のオプションは、 *.exe* ファイル、 *.dll* ファイル、および *.winmd* ファイルをファイル出力またはコンソール出力する場合にだけ有効です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-166">The following options are valid for *.exe*, *.dll*, and *.winmd* files for file or console output only.</span></span>

| <span data-ttu-id="be1f7-167">オプション</span><span class="sxs-lookup"><span data-stu-id="be1f7-167">Option</span></span> | <span data-ttu-id="be1f7-168">説明</span><span class="sxs-lookup"><span data-stu-id="be1f7-168">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="be1f7-169">**/all**</span><span class="sxs-lookup"><span data-stu-id="be1f7-169">**/all**</span></span>|<span data-ttu-id="be1f7-170">**/header**、 **/bytes**、 **/stats**、 **/classlist**、 **/tokens** の各オプションの組み合わせを指定します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-170">Specifies a combination of the **/header**, **/bytes**, **/stats**, **/classlist**, and **/tokens** options.</span></span>|
|<span data-ttu-id="be1f7-171">**/classlist**</span><span class="sxs-lookup"><span data-stu-id="be1f7-171">**/classlist**</span></span>|<span data-ttu-id="be1f7-172">モジュールで定義されているクラスの一覧を含めます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-172">Includes a list of classes defined in the module.</span></span>|
|<span data-ttu-id="be1f7-173">**/forward**</span><span class="sxs-lookup"><span data-stu-id="be1f7-173">**/forward**</span></span>|<span data-ttu-id="be1f7-174">事前のクラス宣言を使用します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-174">Uses forward class declaration.</span></span>|
|<span data-ttu-id="be1f7-175">**/headers**</span><span class="sxs-lookup"><span data-stu-id="be1f7-175">**/headers**</span></span>|<span data-ttu-id="be1f7-176">出力にファイル ヘッダー情報を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-176">Includes file header information in the output.</span></span>|
|<span data-ttu-id="be1f7-177">**/item:** `class`[ **::** `member`[`(sig`]]</span><span class="sxs-lookup"><span data-stu-id="be1f7-177">**/item:** `class`[**::** `member`[`(sig`]]</span></span>|<span data-ttu-id="be1f7-178">指定した引数に応じて、次の要素を逆アセンブルします。</span><span class="sxs-lookup"><span data-stu-id="be1f7-178">Disassembles the following depending upon the argument supplied:</span></span><br /><br /> <span data-ttu-id="be1f7-179">-   指定した `class` を逆アセンブルします。</span><span class="sxs-lookup"><span data-stu-id="be1f7-179">-   Disassembles the specified `class`.</span></span><br /><span data-ttu-id="be1f7-180">-   指定した `class` の `member` を逆アセンブルします。</span><span class="sxs-lookup"><span data-stu-id="be1f7-180">-   Disassembles the specified `member` of the `class`.</span></span><br /><span data-ttu-id="be1f7-181">-   指定したシグネチャ `sig` を持つ `class` の `member` を逆アセンブルします。</span><span class="sxs-lookup"><span data-stu-id="be1f7-181">-   Disassembles the `member` of the `class` with the specified signature `sig`.</span></span> <span data-ttu-id="be1f7-182">`sig` の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="be1f7-182">The format of `sig` is:</span></span><br />     <span data-ttu-id="be1f7-183">[`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)</span><span class="sxs-lookup"><span data-stu-id="be1f7-183">[`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)</span></span><br />     <span data-ttu-id="be1f7-184">**注** .NET Framework Version 1.0 および 1.1 では、`(sig)` のように、`sig` の後に閉じかっこを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-184">**Note** In the .NET Framework versions 1.0 and 1.1, `sig` must be followed by a closing parenthesis: `(sig)`.</span></span> <span data-ttu-id="be1f7-185">.NET Framework 2.0 以降では、閉じかっこを省略して `(sig` とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-185">Starting with the Net Framework 2.0 the closing parenthesis must be omitted: `(sig`.</span></span>|
|<span data-ttu-id="be1f7-186">**/noil**</span><span class="sxs-lookup"><span data-stu-id="be1f7-186">**/noil**</span></span>|<span data-ttu-id="be1f7-187">IL アセンブリ コードが出力されなくなります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-187">Suppresses IL assembly code output.</span></span>|
|<span data-ttu-id="be1f7-188">**/stats**</span><span class="sxs-lookup"><span data-stu-id="be1f7-188">**/stats**</span></span>|<span data-ttu-id="be1f7-189">イメージの統計情報を含めます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-189">Includes statistics on the image.</span></span>|
|<span data-ttu-id="be1f7-190">**/typelist**</span><span class="sxs-lookup"><span data-stu-id="be1f7-190">**/typelist**</span></span>|<span data-ttu-id="be1f7-191">ラウンド トリップの型の順序を保存するために、型の完全な一覧を生成します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-191">Produces the full list of types, to preserve type ordering in a round trip.</span></span>|
|<span data-ttu-id="be1f7-192">**/unicode**</span><span class="sxs-lookup"><span data-stu-id="be1f7-192">**/unicode**</span></span>|<span data-ttu-id="be1f7-193">出力に Unicode エンコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-193">Uses Unicode encoding for the output.</span></span>|
|<span data-ttu-id="be1f7-194">**/utf8**</span><span class="sxs-lookup"><span data-stu-id="be1f7-194">**/utf8**</span></span>|<span data-ttu-id="be1f7-195">出力に UTF-8 エンコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-195">Uses UTF-8 encoding for the output.</span></span> <span data-ttu-id="be1f7-196">既定値は ANSI です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-196">ANSI is the default.</span></span>|

<span data-ttu-id="be1f7-197">次のオプションは、 *.exe*、 *.dll*、 *.obj*、 *.lib*、および *.winmd* の各ファイルをファイル出力またはコンソール出力する場合にだけ有効です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-197">The following options are valid for *.exe*, *.dll*, *.obj*, *.lib*, and *.winmd* files for file or console output only.</span></span>

| <span data-ttu-id="be1f7-198">オプション</span><span class="sxs-lookup"><span data-stu-id="be1f7-198">Option</span></span> | <span data-ttu-id="be1f7-199">説明</span><span class="sxs-lookup"><span data-stu-id="be1f7-199">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="be1f7-200">**/metadata**[=`specifier`]</span><span class="sxs-lookup"><span data-stu-id="be1f7-200">**/metadata**[=`specifier`]</span></span>|<span data-ttu-id="be1f7-201">メタデータを表示します。ここで、`specifier` は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="be1f7-201">Shows metadata, where `specifier` is:</span></span><br /><br /> <span data-ttu-id="be1f7-202">**MDHEADER** — メタデータのヘッダー情報とサイズを表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-202">**MDHEADER** — Show the metadata header information and sizes.</span></span><br /><br /> <span data-ttu-id="be1f7-203">**HEX** — ワードおよび 16 進で情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-203">**HEX** — Show information in hex as well as in words.</span></span><br /><br /> <span data-ttu-id="be1f7-204">**CSV** — レコード数およびヒープ サイズを表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-204">**CSV** — Show the record counts and heap sizes.</span></span><br /><br /> <span data-ttu-id="be1f7-205">**UNREX** — 未解決の外部項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-205">**UNREX** — Show unresolved externals.</span></span><br /><br /> <span data-ttu-id="be1f7-206">**SCHEMA** — メタデータ ヘッダーおよびスキーマ情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-206">**SCHEMA** — Show the metadata header and schema information.</span></span><br /><br /> <span data-ttu-id="be1f7-207">**RAW** — 未処理のメタデータ テーブルを表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-207">**RAW** — Show the raw metadata tables.</span></span><br /><br /> <span data-ttu-id="be1f7-208">**HEAPS** — 未処理のヒープを表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-208">**HEAPS** — Show the raw heaps.</span></span><br /><br /> <span data-ttu-id="be1f7-209">**VALIDATE** — メタデータの一貫性を検証します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-209">**VALIDATE** — Validate the consistency of the metadata.</span></span><br /><br /> <span data-ttu-id="be1f7-210">**/metadata** を複数回指定し、`specifier`に異なる値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-210">You can specify **/metadata** multiple times, with different values for `specifier`.</span></span>|

<span data-ttu-id="be1f7-211">次のオプションは、 *.lib* ファイルをファイル出力またはコンソール出力する場合にだけ有効です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-211">The following options are valid for *.lib* files for file or console output only.</span></span>

| <span data-ttu-id="be1f7-212">オプション</span><span class="sxs-lookup"><span data-stu-id="be1f7-212">Option</span></span> | <span data-ttu-id="be1f7-213">説明</span><span class="sxs-lookup"><span data-stu-id="be1f7-213">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="be1f7-214">**/objectfile**=`filename`</span><span class="sxs-lookup"><span data-stu-id="be1f7-214">**/objectfile**=`filename`</span></span>|<span data-ttu-id="be1f7-215">指定したライブラリ内の単一のオブジェクト ファイルのメタデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-215">Shows the metadata of a single object file in the specified library.</span></span>|

> [!NOTE]
> <span data-ttu-id="be1f7-216">*Ildasm.exe* に関するすべてのオプションでは大文字と小文字が区別されず、先頭の 3 文字で認識されます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-216">All options for *Ildasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="be1f7-217">たとえば、 **/quo** は **/quoteallnames** と等価です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-217">For example, **/quo** is equivalent to **/quoteallnames**.</span></span> <span data-ttu-id="be1f7-218">引数を伴うオプションの場合は、オプションと引数の間に区切り記号としてコロン (:) または等号 (=) を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-218">Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="be1f7-219">たとえば、 **/output:** *filename* は **/output=** *filename* と同等です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-219">For example, **/output:** *filename* is equivalent to **/output=** *filename*.</span></span>

## <a name="remarks"></a><span data-ttu-id="be1f7-220">Remarks</span><span class="sxs-lookup"><span data-stu-id="be1f7-220">Remarks</span></span>

<span data-ttu-id="be1f7-221">*Ildasm.exe* はディスク上のファイルについてだけ動作します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-221">*Ildasm.exe* only operates on PE files on disk.</span></span> <span data-ttu-id="be1f7-222">グローバル アセンブリ キャッシュ内にインストールされたファイルについては動作しません。</span><span class="sxs-lookup"><span data-stu-id="be1f7-222">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="be1f7-223">*Ildasm.exe* で生成されるテキスト ファイルを IL アセンブラー (*Ilasm.exe*) に対する入力として使用できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-223">The text file produced by *Ildasm.exe* can be used as input to the IL Assembler (*Ilasm.exe*).</span></span> <span data-ttu-id="be1f7-224">これは、必ずしもランタイム メタデータ属性のすべてをサポートしないプログラミング言語で記述されたコードをコンパイルするときなどに便利です。</span><span class="sxs-lookup"><span data-stu-id="be1f7-224">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="be1f7-225">コードをコンパイルし、その出力を *Ildasm.exe* で実行した後、生成された IL テキスト ファイルを手作業で編集して足りない属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-225">After compiling the code and running its output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="be1f7-226">このテキスト ファイルを IL アセンブラーで実行すると、最終的な実行可能ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-226">You can then run this text file through the IL Assembler to produce a final executable file.</span></span>

> [!NOTE]
> <span data-ttu-id="be1f7-227">現時点では、埋め込みのネイティブ コード (たとえば Visual C++ で生成された PE ファイル) を含む PE ファイルについては、この手法を使用できません。</span><span class="sxs-lookup"><span data-stu-id="be1f7-227">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>  

<span data-ttu-id="be1f7-228">IL 逆アセンブラーで既定の GUI を使用すると、既存のどの PE ファイルのメタデータおよび逆アセンブルしたコードでも、階層ツリー ビューで表示できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-228">You can use the default GUI in the IL Disassembler to view the metadata and disassembled code of any existing PE file in a hierarchical tree view.</span></span> <span data-ttu-id="be1f7-229">GUI を使用するには、引数 *PEfilename* またはその他のオプションを指定せずに、コマンド行で「**ildasm**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-229">To use the GUI, type **ildasm** at the command line without supplying the *PEfilename* argument or any options.</span></span> <span data-ttu-id="be1f7-230">**[ファイル]** メニューで、*Ildasm.exe* に読み込む PE ファイルまで移動できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-230">From the **File** menu, you can navigate to the PE file that you want to load into *Ildasm.exe*.</span></span> <span data-ttu-id="be1f7-231">選択した PE ファイルについて表示されたメタデータおよび逆アセンブルしたコードを保存するには、 **[ファイル]** メニューの **[ダンプ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be1f7-231">To save the metadata and disassembled code displayed for the selected PE, select the **Dump** command from the **File** menu.</span></span> <span data-ttu-id="be1f7-232">階層ツリー ビューだけを保存するには、 **[ファイル]** メニューの **[ツリービューをダンプ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be1f7-232">To save the hierarchical tree view only, select the **Dump Treeview** command from the **File** menu.</span></span> <span data-ttu-id="be1f7-233">*Ildasm.exe* へのファイルの読み込みとその出力の解釈について詳しくは、Windows SDK に付属している Samples フォルダー内にある、*Ildasm.exe* のチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="be1f7-233">For a detailed guide to loading a file into *Ildasm.exe* and interpreting the output, see the *Ildasm.exe* Tutorial, located in the Samples folder that ships with the Windows SDK.</span></span>

<span data-ttu-id="be1f7-234">*Ildasm.exe* に対して、埋め込みリソースを含む引数 *PEfilename* を指定した場合は、複数の出力ファイルが生成されます。生成されるファイルは、IL コードを含む 1 つのテキスト ファイルと、埋め込みマネージド リソースごとにリソース名を使用してメタデータから生成した .resources ファイルです。</span><span class="sxs-lookup"><span data-stu-id="be1f7-234">If you provide *Ildasm.exe* with a *PEfilename* argument that contains embedded resources, the tool produces multiple output files: a text file that contains IL code and, for each embedded managed resource, a .resources file produced using the resource's name from metadata.</span></span> <span data-ttu-id="be1f7-235">アンマネージ リソースが *PEfilename* の中に埋め込まれている場合は、IL 出力に対して **/output** オプションで指定されたファイル名を使用して、.res ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-235">If an unmanaged resource is embedded in *PEfilename*, a .res file is produced using the filename specified for IL output by the **/output** option.</span></span>

> [!NOTE]
> <span data-ttu-id="be1f7-236">*Ildasm.exe* では、入力ファイルの *.obj* と *.lib* についてはメタデータの説明だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-236">*Ildasm.exe* shows only metadata descriptions for *.obj* and *.lib* input files.</span></span> <span data-ttu-id="be1f7-237">これらの種類のファイルの場合、IL コードは逆アセンブルされません。</span><span class="sxs-lookup"><span data-stu-id="be1f7-237">IL code for these file types is not disassembled.</span></span>

<span data-ttu-id="be1f7-238">*Ildasm.exe* を .exe ファイルまたは *.dll* ファイルに対して実行し、ファイルが管理されているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-238">You can run *Ildasm.exe* over an.exe or *.dll* file to determine whether the file is managed.</span></span> <span data-ttu-id="be1f7-239">ファイルが管理されていない場合は、そのファイルに有効な共通言語ランタイム ヘッダーがないため、逆アセンブルできないことを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-239">If the file is not managed, the tool displays a message stating that the file has no valid common language runtime header and cannot be disassembled.</span></span> <span data-ttu-id="be1f7-240">ファイルが管理されている場合は、処理が正常に行われます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-240">If the file is managed, the tool runs successfully.</span></span>

## <a name="version-information"></a><span data-ttu-id="be1f7-241">バージョン情報</span><span class="sxs-lookup"><span data-stu-id="be1f7-241">Version Information</span></span>

<span data-ttu-id="be1f7-242">.NET Framework 4.5 以降、未処理のバイナリ コンテンツを表示することで、認識できないマーシャリング BLOB (バイナリ ラージ オブジェクト) が *Ildasm.exe* によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-242">Starting with the .NET Framework 4.5, *Ildasm.exe* handles an unrecognized marshal BLOB (binary large object) by displaying the raw binary content.</span></span> <span data-ttu-id="be1f7-243">たとえば、C# プログラムで生成されたマーシャル BLOB の表示方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-243">For example, the following code shows how a marshal BLOB generated by a C# program is displayed:</span></span>

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

<span data-ttu-id="be1f7-244">次の *Ildasm.exe* の出力からの抜粋に示すように、.NET Framework 4.5 以降、*Ildasm.exe* ではインターフェイス実装に適用される属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-244">Starting with the .NET Framework 4.5, *Ildasm.exe* displays attributes that are applied to interface implementations, as shown in the following excerpt from *Ildasm.exe* output:</span></span>

```il
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

## <a name="examples"></a><span data-ttu-id="be1f7-245">使用例</span><span class="sxs-lookup"><span data-stu-id="be1f7-245">Examples</span></span>

<span data-ttu-id="be1f7-246">PE ファイル `MyHello.exe` のメタデータと逆アセンブルしたコードを、*Ildasm.exe* の既定の GUI で表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-246">The following command causes the metadata and disassembled code for the PE file `MyHello.exe` to display in the *Ildasm.exe* default GUI.</span></span>

```console
ildasm myHello.exe
```

<span data-ttu-id="be1f7-247">ファイル `MyFile.exe` を逆アセンブルし、生成される IL アセンブラー テキストをファイル *MyFile.il* に格納するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-247">The following command disassembles the file `MyFile.exe` and stores the resulting IL Assembler text in the file *MyFile.il*.</span></span>

```console
ildasm MyFile.exe /output:MyFile.il
```

<span data-ttu-id="be1f7-248">ファイル `MyFile.exe` を逆アセンブルし、生成される IL アセンブラーをコンソール ウィンドウに表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-248">The following command disassembles the file `MyFile.exe` and displays the resulting IL Assembler text to the console window.</span></span>

```console
ildasm MyFile.exe /text
```

<span data-ttu-id="be1f7-249">`MyApp.exe` ファイルに埋め込みのマネージド リソースとアンマネージド リソースが含まれる場合、次のコマンドを実行すると 4 つのファイル (*MyApp.il*、*MyApp.res*、*Icons.resources*、*Message.resources*) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be1f7-249">If the file `MyApp.exe` contains embedded managed and unmanaged resources, the following command produces four files: *MyApp.il*, *MyApp.res*, *Icons.resources*, and *Message.resources*:</span></span>

```console
ildasm MyApp.exe /output:MyApp.il
```

<span data-ttu-id="be1f7-250">`MyFile.exe` 内のクラス `MyClass` に属するメソッド `MyMethod` を逆アセンブルし、その出力をコンソール ウィンドウに表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-250">The following command disassembles the method `MyMethod` within the class `MyClass` in `MyFile.exe` and displays the output to the console window.</span></span>

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

<span data-ttu-id="be1f7-251">上の例では、異なるシグネチャを持つ `MyMethod` という名前のメソッドが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-251">In the previous example, there could be several methods named `MyMethod` with different signatures.</span></span> <span data-ttu-id="be1f7-252">戻り値の型 **void**、およびパラメーターの型 **int32** と **string** を指定してインスタンス メソッド `MyMethod` を逆アセンブルするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-252">The following command disassembles the instance method `MyMethod` with the return type of **void** and the parameter types **int32** and **string**.</span></span>

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> <span data-ttu-id="be1f7-253">.NET Framework Version 1.0 および 1.1 では、メソッド名の後にある左かっことシグネチャの後にある右かっこの数が一致するように `MyMethod(instance void(int32))` とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-253">In the .NET Framework versions 1.0 and 1.1, the left parenthesis that follows the method name must be balanced by a right parenthesis after the signature: `MyMethod(instance void(int32))`.</span></span> <span data-ttu-id="be1f7-254">.NET Framework Version 2.0 以降では、閉じかっこを省略して `MyMethod(instance void(int32)` とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-254">Starting with the .NET Framework 2.0 the closing parenthesis must be omitted: `MyMethod(instance void(int32)`.</span></span>

<span data-ttu-id="be1f7-255">`static` メソッド (Visual Basic の `Shared` メソッド) を取得するには、キーワード `instance` を省略します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-255">To retrieve a `static` method (`Shared` method in Visual Basic), omit the keyword `instance`.</span></span> <span data-ttu-id="be1f7-256">`int32` や `string` のようなプリミティブ型でないクラス型には名前空間を含め、キーワード `class` を前に付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-256">Class types that are not primitive types like `int32` and `string` must include the namespace and must be preceded by the keyword `class`.</span></span> <span data-ttu-id="be1f7-257">外部の型には、角かっこで囲んだライブラリ名を前に付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-257">External types must be preceded by the library name in square brackets.</span></span> <span data-ttu-id="be1f7-258">`MyMethod` 型の 1 つのパラメーターと <xref:System.AppDomain> 型の戻り値を持つ、<xref:System.AppDomain> という名前の静的メソッドを逆アセンブルするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-258">The following command disassembles a static method named `MyMethod` that has one parameter of type <xref:System.AppDomain> and has a return type of <xref:System.AppDomain>.</span></span>

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

<span data-ttu-id="be1f7-259">入れ子になった型は、クラスを前に付けてスラッシュで区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="be1f7-259">A nested type must be preceded by its containing class, delimited by a forward slash.</span></span> <span data-ttu-id="be1f7-260">たとえば、`MyNamespace.MyClass` クラスに `NestedClass` という名前の入れ子になったクラスが含まれている場合は、`class MyNamespace.MyClass/NestedClass` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="be1f7-260">For example, if the `MyNamespace.MyClass` class contains a nested class named `NestedClass`, the nested class is identified as follows: `class MyNamespace.MyClass/NestedClass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="be1f7-261">関連項目</span><span class="sxs-lookup"><span data-stu-id="be1f7-261">See also</span></span>

- [<span data-ttu-id="be1f7-262">ツール</span><span class="sxs-lookup"><span data-stu-id="be1f7-262">Tools</span></span>](index.md)
- [<span data-ttu-id="be1f7-263">Ilasm.exe (IL アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="be1f7-263">Ilasm.exe (IL Assembler)</span></span>](ilasm-exe-il-assembler.md)
- [<span data-ttu-id="be1f7-264">マネージド実行プロセス</span><span class="sxs-lookup"><span data-stu-id="be1f7-264">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="be1f7-265">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="be1f7-265">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
