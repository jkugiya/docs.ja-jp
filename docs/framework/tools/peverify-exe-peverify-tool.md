---
title: Peverify.exe (PEVerify ツール)
description: Peverify.exe (移植できる実行可能ファイルの検証) を使用し、Microsoft Intermediate Language (MSIL) のコードとメタデータが .NET のタイプ セーフ標準を満たすかどうかを判断します。
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
ms.openlocfilehash: ba8b4cd7f398eee9129d24d25d8fdb754c89a3ee
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653297"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="15413-103">Peverify.exe (PEVerify ツール)</span><span class="sxs-lookup"><span data-stu-id="15413-103">Peverify.exe (PEVerify tool)</span></span>

<span data-ttu-id="15413-104">PEVerify ツールは、Microsoft Intermediate Language (MSIL) を生成する開発者 (コンパイラの作成者やスクリプト エンジンの開発者など) が、生成する MSIL コードと関連メタデータがタイプ セーフ要件を満たしているかどうかを確認する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="15413-104">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers and script engine developers) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="15413-105">一部のコンパイラでは、特定の言語構成を使用しなかった場合にだけ、検査可能でタイプ セーフなコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="15413-105">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="15413-106">このようなコンパイラを使用している場合、コードのタイプ セーフ性が損なわれていないかを確認することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="15413-106">If you're using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="15413-107">ファイルに対して PEVerify ツールを実行し、MSIL とメタデータを検査できます。</span><span class="sxs-lookup"><span data-stu-id="15413-107">You can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="15413-108">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="15413-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="15413-109">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="15413-109">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>
  
## <a name="syntax"></a><span data-ttu-id="15413-110">構文</span><span class="sxs-lookup"><span data-stu-id="15413-110">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="15413-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="15413-111">Parameters</span></span>  
  
|<span data-ttu-id="15413-112">引数</span><span class="sxs-lookup"><span data-stu-id="15413-112">Argument</span></span>|<span data-ttu-id="15413-113">説明</span><span class="sxs-lookup"><span data-stu-id="15413-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="15413-114">*ファイル名*</span><span class="sxs-lookup"><span data-stu-id="15413-114">*filename*</span></span>|<span data-ttu-id="15413-115">MSIL とメタデータを検査する対象のポータブル実行可能 (PE) ファイル。</span><span class="sxs-lookup"><span data-stu-id="15413-115">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="15413-116">オプション</span><span class="sxs-lookup"><span data-stu-id="15413-116">Option</span></span>|<span data-ttu-id="15413-117">説明</span><span class="sxs-lookup"><span data-stu-id="15413-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="15413-118">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="15413-118">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="15413-119">*maxErrorCount* エラーが発生した後で検査を中止します。</span><span class="sxs-lookup"><span data-stu-id="15413-119">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="15413-120">このパラメーターは、.NET Framework Version 2.0 以降ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="15413-120">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="15413-121">**/clock**</span><span class="sxs-lookup"><span data-stu-id="15413-121">**/clock**</span></span>|<span data-ttu-id="15413-122">次の検査時間をミリ秒単位で計測して報告します。</span><span class="sxs-lookup"><span data-stu-id="15413-122">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="15413-123">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="15413-123">**MD Val. cycle**</span></span><br /> <span data-ttu-id="15413-124">メタデータ検証サイクル</span><span class="sxs-lookup"><span data-stu-id="15413-124">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="15413-125">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="15413-125">**MD Val. pure**</span></span><br /> <span data-ttu-id="15413-126">メタデータ検証のみ</span><span class="sxs-lookup"><span data-stu-id="15413-126">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="15413-127">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="15413-127">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="15413-128">Microsoft Intermediate Language (MSIL) 検証サイクル</span><span class="sxs-lookup"><span data-stu-id="15413-128">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="15413-129">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="15413-129">**IL Ver pure**</span></span><br /> <span data-ttu-id="15413-130">MSIL 検証のみ</span><span class="sxs-lookup"><span data-stu-id="15413-130">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="15413-131">**MD Val. cycle** 時間および **IL Ver. cycle** 時間には、必要なスタートアップ手順およびシャットダウン手順を実行するために必要な時間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="15413-131">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="15413-132">**MD Val. pure** 時間および **IL Ver pure** 時間は、検査または検証だけを行うために要する時間を反映します。</span><span class="sxs-lookup"><span data-stu-id="15413-132">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="15413-133">**/help**</span><span class="sxs-lookup"><span data-stu-id="15413-133">**/help**</span></span>|<span data-ttu-id="15413-134">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="15413-134">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="15413-135">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="15413-135">**/hresult**</span></span>|<span data-ttu-id="15413-136">エラーコードを 16 進形式で表示します。</span><span class="sxs-lookup"><span data-stu-id="15413-136">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="15413-137">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="15413-137">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="15413-138">指定したエラー コードを無視します。</span><span class="sxs-lookup"><span data-stu-id="15413-138">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="15413-139">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="15413-139">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="15413-140">指定した応答ファイル内に一覧表示されているエラー コードを無視します。</span><span class="sxs-lookup"><span data-stu-id="15413-140">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="15413-141">**/il**</span><span class="sxs-lookup"><span data-stu-id="15413-141">**/il**</span></span>|<span data-ttu-id="15413-142">*filename* で指定したアセンブリに実装されているメソッドに対して、MSIL がタイプ セーフかどうかを検査します。</span><span class="sxs-lookup"><span data-stu-id="15413-142">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="15413-143">**/quiet** オプションを指定した場合を除き、検出された問題ごとに詳細な説明が返されます。</span><span class="sxs-lookup"><span data-stu-id="15413-143">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="15413-144">**/md**</span><span class="sxs-lookup"><span data-stu-id="15413-144">**/md**</span></span>|<span data-ttu-id="15413-145">*filename* で指定したアセンブリに対して、メタデータを検証します。</span><span class="sxs-lookup"><span data-stu-id="15413-145">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="15413-146">このオプションでは、ファイル内のすべてのメタデータ構造が検証され、検出された問題がすべて報告されます。</span><span class="sxs-lookup"><span data-stu-id="15413-146">This option walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="15413-147">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="15413-147">**/nologo**</span></span>|<span data-ttu-id="15413-148">製品バージョンと著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="15413-148">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="15413-149">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="15413-149">**/nosymbols**</span></span>|<span data-ttu-id="15413-150">.NET Framework Version 2.0 で、後方互換性のために行番号を表示しません。</span><span class="sxs-lookup"><span data-stu-id="15413-150">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="15413-151">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="15413-151">**/quiet**</span></span>|<span data-ttu-id="15413-152">クワイエット モードを指定します。このモードでは、検査により検出された問題の報告が簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="15413-152">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="15413-153">ファイルがタイプ セーフかどうかは報告されますが、タイプ セーフでない場合に、その問題に関する情報は報告されません。</span><span class="sxs-lookup"><span data-stu-id="15413-153">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="15413-154">透過的なメソッドのみを検証します。</span><span class="sxs-lookup"><span data-stu-id="15413-154">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="15413-155">**/unique**</span><span class="sxs-lookup"><span data-stu-id="15413-155">**/unique**</span></span>|<span data-ttu-id="15413-156">繰り返し発生するエラー コードを無視します。</span><span class="sxs-lookup"><span data-stu-id="15413-156">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="15413-157">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="15413-157">**/verbose**</span></span>|<span data-ttu-id="15413-158">.NET Framework Version 2.0 で、MSIL 検証メッセージに追加情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="15413-158">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="15413-159">**/?**</span><span class="sxs-lookup"><span data-stu-id="15413-159">**/?**</span></span>|<span data-ttu-id="15413-160">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="15413-160">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15413-161">Remarks</span><span class="sxs-lookup"><span data-stu-id="15413-161">Remarks</span></span>  

 <span data-ttu-id="15413-162">共通言語ランタイムは、セキュリティ機構や分離機構の実施を簡単にするために、アプリケーション コードがタイプ セーフに実行されることに依存しています。</span><span class="sxs-lookup"><span data-stu-id="15413-162">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="15413-163">通常、[検査可能でタイプ セーフ](../../standard/security/key-security-concepts.md#type-safety-and-security)なコード以外のコードは実行できません。しかし、信頼できるが検査を実行できないコードを実行可能にするセキュリティ ポリシーを設定することはできます。</span><span class="sxs-lookup"><span data-stu-id="15413-163">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="15413-164">**/md** と **/il** のいずれのオプションも指定しない場合は、両方の種類の検査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="15413-164">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="15413-165">まず、 **/md** オプションによる検査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="15413-165">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="15413-166">エラーが検出されない場合は、 **/il** オプションによる検査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="15413-166">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="15413-167">**/md** と **/il** の両方のオプションを指定した場合は、メタデータの検査でエラーが検出された場合でも、 **/il** オプションによる検査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="15413-167">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="15413-168">つまり、メタデータの検査でエラーが検出されないときは、**peverify** *filename* は **peverify** *filename* **/md** **/il** と同等です。</span><span class="sxs-lookup"><span data-stu-id="15413-168">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="15413-169">Peverify.exe は、データ フローの分析と、メタデータの有効性に関する多数の規則のリストに基づいて、MSIL に対する包括的な検査を実行します。</span><span class="sxs-lookup"><span data-stu-id="15413-169">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="15413-170">Peverify.exe によって実行される検査の詳細については、Windows SDK の Tools Developers Guide フォルダー内にある "Metadata Validation Specification" (メタデータ検証仕様) と "MSIL Instruction Set Specification" (MSIL 命令セット仕様) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15413-170">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
<span data-ttu-id="15413-171">.NET Framework Version 2.0 以降では、`dup`、`ldsflda`、`ldflda`、`ldelema`、`call`、`unbox` の各 MSIL 命令を使用して指定する検証可能な `byref` 戻り値をサポートします。</span><span class="sxs-lookup"><span data-stu-id="15413-171">.NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call`, and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="15413-172">使用例</span><span class="sxs-lookup"><span data-stu-id="15413-172">Examples</span></span>  

 <span data-ttu-id="15413-173">アセンブリ `myAssembly.exe` に実装されているメソッドに対して、メタデータの有効性および MSIL がタイプ セーフかどうかについて検査するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="15413-173">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="15413-174">上記の要求が正常に終了した場合は、次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="15413-174">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="15413-175">アセンブリ `myAssembly.exe` に実装されているメソッドに対して、メタデータの有効性および MSIL がタイプ セーフかどうかについて検査するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="15413-175">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="15413-176">このツールは、これらの検査に要する時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="15413-176">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="15413-177">上記の要求が正常に終了した場合は、次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="15413-177">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="15413-178">アセンブリ `myAssembly.exe` に実装されているメソッドに対して、メタデータの有効性および MSIL がタイプ セーフかどうかについて検査するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="15413-178">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="15413-179">しかし、Peverify.exe は、最大エラー カウントである 100 に達すると、停止します。</span><span class="sxs-lookup"><span data-stu-id="15413-179">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="15413-180">このツールは、指定されたエラー コードも無視します。</span><span class="sxs-lookup"><span data-stu-id="15413-180">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="15413-181">上記の例と結果は同じですが、無視するエラー コードを応答ファイル `ignoreErrors.rsp` に指定するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="15413-181">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="15413-182">この応答ファイルには、エラー コードの一覧をコンマで区切って指定できます。</span><span class="sxs-lookup"><span data-stu-id="15413-182">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="15413-183">また、エラー コードを 1 行に 1 つという形式で指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="15413-183">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="15413-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="15413-184">See also</span></span>

- [<span data-ttu-id="15413-185">ツール</span><span class="sxs-lookup"><span data-stu-id="15413-185">Tools</span></span>](index.md)
- [<span data-ttu-id="15413-186">検証可能なタイプ セーフ コードの作成</span><span class="sxs-lookup"><span data-stu-id="15413-186">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="15413-187">タイプ セーフとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="15413-187">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="15413-188">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="15413-188">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
