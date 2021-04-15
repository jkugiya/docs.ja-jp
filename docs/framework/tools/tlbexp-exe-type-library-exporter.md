---
title: Tlbexp.exe (タイプ ライブラリ エクスポーター)
description: Tlbexp.exe (タイプ ライブラリ エクスポーター) を確認します。 このツールによって、共通言語ランタイム (CLR) アセンブリで定義されている型を記述するタイプ ライブラリを生成できます。
ms.date: 03/30/2017
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
ms.openlocfilehash: 49b776781a7a61db7e90b0c1f0abec6d63f50ba0
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494650"
---
# <a name="tlbexpexe-type-library-exporter"></a><span data-ttu-id="f5878-104">Tlbexp.exe (タイプ ライブラリ エクスポーター)</span><span class="sxs-lookup"><span data-stu-id="f5878-104">Tlbexp.exe (Type Library Exporter)</span></span>

<span data-ttu-id="f5878-105">タイプ ライブラリ エクスポーターは、共通言語ランタイム アセンブリで定義されている型を記述するタイプ ライブラリを生成します。</span><span class="sxs-lookup"><span data-stu-id="f5878-105">The Type Library Exporter generates a type library that describes the types defined in a common language runtime assembly.</span></span>  
  
 <span data-ttu-id="f5878-106">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="f5878-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="f5878-107">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="f5878-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>
  
 <span data-ttu-id="f5878-108">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="f5878-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5878-109">構文</span><span class="sxs-lookup"><span data-stu-id="f5878-109">Syntax</span></span>  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5878-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5878-110">Parameters</span></span>  
  
|<span data-ttu-id="f5878-111">引数</span><span class="sxs-lookup"><span data-stu-id="f5878-111">Argument</span></span>|<span data-ttu-id="f5878-112">説明</span><span class="sxs-lookup"><span data-stu-id="f5878-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f5878-113">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="f5878-113">*assemblyName*</span></span>|<span data-ttu-id="f5878-114">タイプ ライブラリをエクスポートする対象のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="f5878-114">The assembly for which to export a type library.</span></span>|  
  
|<span data-ttu-id="f5878-115">オプション</span><span class="sxs-lookup"><span data-stu-id="f5878-115">Option</span></span>|<span data-ttu-id="f5878-116">説明</span><span class="sxs-lookup"><span data-stu-id="f5878-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f5878-117">**/asmpath:** *directory*</span><span class="sxs-lookup"><span data-stu-id="f5878-117">**/asmpath:** *directory*</span></span>|<span data-ttu-id="f5878-118">アセンブリを検索する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="f5878-118">Specifies the location to search for assemblies.</span></span> <span data-ttu-id="f5878-119">このオプションを使用する場合は、現在のディレクトリを含め、参照アセンブリの検索場所を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5878-119">If you use this option, you must explicitly specify the locations to search for referenced assemblies, including the current directory.</span></span><br /><br /> <span data-ttu-id="f5878-120">**asmpath** オプションを使用すると、タイプ ライブラリ エクスポーターは、グローバル アセンブリ キャッシュ (GAC) 内のアセンブリを検索しません。</span><span class="sxs-lookup"><span data-stu-id="f5878-120">When you use the **asmpath** option, the Type Library Exporter will not look for an assembly in the global assembly cache (GAC).</span></span>|  
|<span data-ttu-id="f5878-121">**/help**</span><span class="sxs-lookup"><span data-stu-id="f5878-121">**/help**</span></span>|<span data-ttu-id="f5878-122">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="f5878-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="f5878-123">**/names:** *filename*</span><span class="sxs-lookup"><span data-stu-id="f5878-123">**/names:** *filename*</span></span>|<span data-ttu-id="f5878-124">タイプ ライブラリにおける大文字の使用スタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5878-124">Specifies the capitalization of names in a type library.</span></span> <span data-ttu-id="f5878-125">*filename* 引数はテキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f5878-125">The *filename* argument is a text file.</span></span> <span data-ttu-id="f5878-126">このファイルには、タイプ ライブラリ内の名前に対する大文字の使用スタイルを 1 行に 1 つずつ指定します。</span><span class="sxs-lookup"><span data-stu-id="f5878-126">Each line in the file specifies the capitalization of one name in the type library.</span></span>|  
|<span data-ttu-id="f5878-127">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="f5878-127">**/nologo**</span></span>|<span data-ttu-id="f5878-128">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="f5878-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="f5878-129">**/oldnames**</span><span class="sxs-lookup"><span data-stu-id="f5878-129">**/oldnames**</span></span>|<span data-ttu-id="f5878-130">型名が競合している場合は、Tlbexp.exe は装飾された型名をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="f5878-130">Forces Tlbexp.exe to export decorated type names if there is a type name conflict.</span></span> <span data-ttu-id="f5878-131">バージョン 2.0 より以前の .NET Framework では、これが既定の動作であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f5878-131">Note that this was the default behavior in versions prior to the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="f5878-132">**/out:** *file*</span><span class="sxs-lookup"><span data-stu-id="f5878-132">**/out:** *file*</span></span>|<span data-ttu-id="f5878-133">生成するタイプ ライブラリ ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f5878-133">Specifies the name of the type library file to generate.</span></span> <span data-ttu-id="f5878-134">このオプションを省略した場合、アセンブリ名に拡張子 .tlb を付加した名前のタイプ ライブラリが生成されます。このアセンブリ名は実際のアセンブリ名ですが、アセンブリを含むファイルの名前と必ずしも同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f5878-134">If you omit this option, Tlbexp.exe generates a type library with the same name as the assembly (the actual assembly name, which might not necessarily be the same as the file containing the assembly) and a .tlb extension.</span></span>|  
|<span data-ttu-id="f5878-135">**/silence:** `warningnumber`</span><span class="sxs-lookup"><span data-stu-id="f5878-135">**/silence:** `warningnumber`</span></span>|<span data-ttu-id="f5878-136">指定された警告を表示しません。</span><span class="sxs-lookup"><span data-stu-id="f5878-136">Suppresses the display of the specified warning.</span></span> <span data-ttu-id="f5878-137">このオプションは、 **/silent** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f5878-137">This option cannot be used with **/silent**.</span></span>|  
|<span data-ttu-id="f5878-138">**/silent**</span><span class="sxs-lookup"><span data-stu-id="f5878-138">**/silent**</span></span>|<span data-ttu-id="f5878-139">成功メッセージを表示しません。</span><span class="sxs-lookup"><span data-stu-id="f5878-139">Suppresses the display of success messages.</span></span> <span data-ttu-id="f5878-140">このオプションは、 **/silence** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f5878-140">This option cannot be used with **/silence**.</span></span>|  
|<span data-ttu-id="f5878-141">**/tlbreference:** *typelibraryname*</span><span class="sxs-lookup"><span data-stu-id="f5878-141">**/tlbreference:** *typelibraryname*</span></span>|<span data-ttu-id="f5878-142">Tlbexp.exe はレジストリを参照せずに、タイプ ライブラリの参照を明示的に解決します。</span><span class="sxs-lookup"><span data-stu-id="f5878-142">Forces Tlbexp.exe to explicitly resolve type library references without consulting the registry.</span></span> <span data-ttu-id="f5878-143">たとえば、アセンブリ B がアセンブリ A を参照する場合は、レジストリで指定されているタイプ ライブラリを参照するのではなく、このオプションを使用してタイプ ライブラリの参照を明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="f5878-143">For example, if assembly B references assembly A, you can use this option to provide an explicit type library reference, rather than relying on the type library specified in the registry.</span></span> <span data-ttu-id="f5878-144">Tlbexp.exe はバージョン チェックを実行して、タイプ ライブラリとアセンブリのバージョンが同じであることを確認します。バージョンが異なる場合は、エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="f5878-144">Tlbexp.exe performs a version check to ensure that the type library version matches the assembly version; otherwise, it generates an error.</span></span><br /><br /> <span data-ttu-id="f5878-145">**tlbreference** オプションを指定しても、<xref:System.Runtime.InteropServices.ComImportAttribute> 属性の適用先のインターフェイスが別の型に実装される場合には、レジストリが参照されます。</span><span class="sxs-lookup"><span data-stu-id="f5878-145">Note that the **tlbreference** option still consults the registry in cases where the <xref:System.Runtime.InteropServices.ComImportAttribute> attribute is applied to an interface that is then implemented by another type.</span></span>|  
|<span data-ttu-id="f5878-146">**/tlbrefpath:** *path*</span><span class="sxs-lookup"><span data-stu-id="f5878-146">**/tlbrefpath:** *path*</span></span>|<span data-ttu-id="f5878-147">参照タイプ ライブラリの絶対パス。</span><span class="sxs-lookup"><span data-stu-id="f5878-147">Fully qualified path to a referenced type library.</span></span>|  
|<span data-ttu-id="f5878-148">**/win32**</span><span class="sxs-lookup"><span data-stu-id="f5878-148">**/win32**</span></span>|<span data-ttu-id="f5878-149">このオプションを指定すると、64 ビットのコンピューターでコンパイルする場合、Tlbexp.exe は 32 ビットのタイプ ライブラリを生成します。</span><span class="sxs-lookup"><span data-stu-id="f5878-149">When compiling on a 64-bit computer, this option specifies that Tlbexp.exe generates a 32-bit type library.</span></span>|  
|<span data-ttu-id="f5878-150">**/win64**</span><span class="sxs-lookup"><span data-stu-id="f5878-150">**/win64**</span></span>|<span data-ttu-id="f5878-151">このオプションを指定すると、32 ビットのコンピューターでコンパイルする場合、Tlbexp.exe は 64 ビットのタイプ ライブラリを生成します。</span><span class="sxs-lookup"><span data-stu-id="f5878-151">When compiling on a 32-bit computer, this option specifies that Tlbexp.exe generates a 64-bit type library.</span></span>|  
|<span data-ttu-id="f5878-152">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="f5878-152">**/verbose**</span></span>|<span data-ttu-id="f5878-153">詳細出力モードを指定します。このモードでは、タイプ ライブラリを生成する必要のある参照先アセンブリがある場合は、その一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="f5878-153">Specifies verbose mode; displays a list of any referenced assemblies for which a type library needs to be generated.</span></span>|  
|<span data-ttu-id="f5878-154">**/?**</span><span class="sxs-lookup"><span data-stu-id="f5878-154">**/?**</span></span>|<span data-ttu-id="f5878-155">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="f5878-155">Displays command syntax and options for the tool.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f5878-156">Tlbexp.exe のコマンド ライン オプションでは、大文字と小文字が区別されません。また、これらのオプションは任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="f5878-156">The command-line options for Tlbexp.exe are case-insensitive and can be supplied in any order.</span></span> <span data-ttu-id="f5878-157">オプションを一意に識別するために十分である場合は、オプションの一部を指定するだけでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f5878-157">You only need to specify enough of the option to uniquely identify it.</span></span> <span data-ttu-id="f5878-158">たとえば、 **/n** を指定した場合は **/nologo**、 **/o:** *outfile.tlb* と指定した場合は **/out:** *outfile.tlb* であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="f5878-158">For example, **/n** is equivalent to **/nologo**, and **/o:** *outfile.tlb* is equivalent to **/out:** *outfile.tlb*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5878-159">Remarks</span><span class="sxs-lookup"><span data-stu-id="f5878-159">Remarks</span></span>  

 <span data-ttu-id="f5878-160">Tlbexp.exe は、アセンブリで定義されている型の定義を含む、タイプ ライブラリを生成します。</span><span class="sxs-lookup"><span data-stu-id="f5878-160">Tlbexp.exe generates a type library that contains definitions of the types defined in the assembly.</span></span> <span data-ttu-id="f5878-161">Visual Basic 6.0 などのアプリケーションは、このツールで生成されたタイプ ライブラリを使用して、アセンブリ内で定義されている .NET 型にバインドできます。</span><span class="sxs-lookup"><span data-stu-id="f5878-161">Applications such as Visual Basic 6.0 can use the generated type library to bind to the .NET types defined in the assembly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f5878-162">Tlbexp.exe を使用して Windows メタデータ (.winmd) ファイルをエクスポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f5878-162">You cannot use Tlbexp.exe to export Windows metadata (.winmd) files.</span></span> <span data-ttu-id="f5878-163">Windows ランタイム アセンブリのエクスポートはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f5878-163">Exporting Windows Runtime assemblies is not supported.</span></span>  
  
 <span data-ttu-id="f5878-164">アセンブリ全体が一度に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f5878-164">The entire assembly is converted at once.</span></span> <span data-ttu-id="f5878-165">Tlbexp.exe を使用しても、アセンブリで定義されている型のサブセットに関する型情報は生成できません。</span><span class="sxs-lookup"><span data-stu-id="f5878-165">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
 <span data-ttu-id="f5878-166">Tlbexp.exe を使用して、[タイプ ライブラリ インポーター (Tlbimp.exe)](tlbimp-exe-type-library-importer.md) でインポートしたアセンブリからタイプ ライブラリを生成することもできません。</span><span class="sxs-lookup"><span data-stu-id="f5878-166">You cannot use Tlbexp.exe to produce a type library from an assembly that was imported using the [Type Library Importer (Tlbimp.exe)](tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="f5878-167">代わりに、Tlbimp.exe でインポートした元のタイプ ライブラリを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5878-167">Instead, you should refer to the original type library that was imported with Tlbimp.exe.</span></span> <span data-ttu-id="f5878-168">しかし、Tlbimp.exe でインポートしたアセンブリを参照するアセンブリから、タイプ ライブラリをエクスポートすることはできます。</span><span class="sxs-lookup"><span data-stu-id="f5878-168">You can export a type library from an assembly that references assemblies that were imported using Tlbimp.exe.</span></span> <span data-ttu-id="f5878-169">後の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5878-169">See the examples section below.</span></span>  
  
 <span data-ttu-id="f5878-170">Tlbexp.exe は、生成したタイプ ライブラリを現在のディレクトリ、または出力ファイルとして指定したディレクトリに格納します。</span><span class="sxs-lookup"><span data-stu-id="f5878-170">Tlbexp.exe places generated type libraries in the current working directory or the directory specified for the output file.</span></span> <span data-ttu-id="f5878-171">単一のアセンブリから複数のタイプ ライブラリが生成されることもあります。</span><span class="sxs-lookup"><span data-stu-id="f5878-171">A single assembly might cause several type libraries to be generated.</span></span>  
  
 <span data-ttu-id="f5878-172">Tlbexp.exe はタイプ ライブラリを生成しますが、生成したタイプ ライブラリの登録は行いません。</span><span class="sxs-lookup"><span data-stu-id="f5878-172">Tlbexp.exe generates a type library but does not register it.</span></span> <span data-ttu-id="f5878-173">これは、タイプ ライブラリの生成と登録を両方とも行う[アセンブリ登録ツール (Regasm.exe)](regasm-exe-assembly-registration-tool.md) とは対照的です。</span><span class="sxs-lookup"><span data-stu-id="f5878-173">This is in contrast to the [Assembly Registration tool (Regasm.exe)](regasm-exe-assembly-registration-tool.md), which both generates and registers a type library.</span></span> <span data-ttu-id="f5878-174">タイプ ライブラリを生成して COM に登録するには、Regasm.exe を使用します。</span><span class="sxs-lookup"><span data-stu-id="f5878-174">To generate and register a type library with COM, use Regasm.exe.</span></span>  
  
 <span data-ttu-id="f5878-175">`/win32` オプションまたは `/win64` オプションを指定しないと、Tlbexp.exe はコンパイルを実行するコンピューターのタイプ (32 ビット コンピューターまたは 64 ビット コンピューター) に応じて、32 ビットまたは 64 ビットのタイプ ライブラリを生成します。</span><span class="sxs-lookup"><span data-stu-id="f5878-175">If you do not specify either the `/win32` or `/win64` option, Tlbexp.exe generates a 32-bit or 64-bit type library that corresponds to the type of computer on which you are performing the compilation (32-bit or 64-bit computer).</span></span> <span data-ttu-id="f5878-176">クロス コンパイルを行う場合は、32 ビット コンピューター上で `/win64` オプションを使用して 64 ビットのタイプ ライブラリを生成したり、64 ビット コンピューター上で `/win32` オプションを使用して 32 ビットのタイプ ライブラリを生成したりできます。</span><span class="sxs-lookup"><span data-stu-id="f5878-176">For cross-compilation purposes, you can use the `/win64` option on a 32-bit computer to generate a 64-bit type library and you can use the `/win32` option on a 64-bit computer to generate a 32-bit type library.</span></span> <span data-ttu-id="f5878-177">32 ビットのタイプ ライブラリでは、<xref:System.Runtime.InteropServices.ComTypes.SYSKIND> 値は <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f5878-177">In 32-bit type libraries, the <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> value is set to <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>.</span></span> <span data-ttu-id="f5878-178">64 ビットのタイプ ライブラリでは、<xref:System.Runtime.InteropServices.ComTypes.SYSKIND> 値は <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f5878-178">In 64-bit type libraries, the <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> value is set to <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>.</span></span> <span data-ttu-id="f5878-179">すべてのデータ型変換 (たとえば、`IntPtr` や `UIntPtr` などのポインター-サイズ データ型) は、適切に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f5878-179">All data type transformations (for example, pointer-sized data types such as `IntPtr` and `UIntPtr`) are converted appropriately.</span></span>  
  
 <span data-ttu-id="f5878-180"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して、<xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> または `VT_UNKOWN` の `VT_DISPATCH` 値を指定すると、Tlbexp.exe は後続で使用される <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> フィールドをすべて無視します。</span><span class="sxs-lookup"><span data-stu-id="f5878-180">If you use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> value of `VT_UNKOWN` or `VT_DISPATCH`, Tlbexp.exe ignores any subsequent use of the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> field.</span></span> <span data-ttu-id="f5878-181">たとえば、次のようなシグネチャがあるとします。</span><span class="sxs-lookup"><span data-stu-id="f5878-181">For example, given the following signatures:</span></span>  
  
```csharp
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 <span data-ttu-id="f5878-182">次のタイプ ライブラリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f5878-182">the following type library is generated:</span></span>  
  
```cpp
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 <span data-ttu-id="f5878-183">Tlbexp.exe は <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> フィールドを無視することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f5878-183">Note that Tlbexp.exe ignores the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> field.</span></span>  
  
 <span data-ttu-id="f5878-184">アセンブリ内にあるすべての情報をタイプ ライブラリに含めることはできないので、エクスポート プロセス中、Tlbexp.exe によって一部のデータが破棄される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5878-184">Because type libraries cannot accommodate all the information found in assemblies, Tlbexp.exe might discard some data during the export process.</span></span> <span data-ttu-id="f5878-185">変換処理、およびタイプ ライブラリに出力される各情報のソースの識別については、「[アセンブリからタイプ ライブラリへの変換の要約](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5878-185">For an explanation of the transformation process and identification of the source of each piece of information emitted to a type library, see the [Assembly to Type Library Conversion Summary](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100)).</span></span>  
  
 <span data-ttu-id="f5878-186">タイプ ライブラリ エクスポーターは、<xref:System.TypedReference> オブジェクトがアンマネージ コードで意味を持たない場合でも、`VARIANT` パラメーターが <xref:System.TypedReference> であるメソッドをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="f5878-186">Note that the Type Library Exporter exports methods that have <xref:System.TypedReference> parameters as `VARIANT`, even though the <xref:System.TypedReference> object has no meaning in unmanaged code.</span></span> <span data-ttu-id="f5878-187"><xref:System.TypedReference> パラメーターを持つメソッドをエクスポートしても、タイプ ライブラリ エクスポーターは警告やエラーを生成しません。作成されたタイプ ライブラリを使用するアンマネージ コードは、正しく動作しません。</span><span class="sxs-lookup"><span data-stu-id="f5878-187">When you export methods that have <xref:System.TypedReference> parameters, the Type Library Exporter will not generate a warning or error and unmanaged code that uses the resulting type library will not run properly.</span></span>
  
## <a name="examples"></a><span data-ttu-id="f5878-188">使用例</span><span class="sxs-lookup"><span data-stu-id="f5878-188">Examples</span></span>  

 <span data-ttu-id="f5878-189">`myTest.dll` 内で見つかったアセンブリと同じ名前を持つタイプ ライブラリを生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f5878-189">The following command generates a type library with the same name as the assembly found in `myTest.dll`.</span></span>  
  
```console  
tlbexp myTest.dll  
```  
  
 <span data-ttu-id="f5878-190">`clipper.tlb` という名前を持つタイプ ライブラリを生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f5878-190">The following command generates a type library with the name `clipper.tlb`.</span></span>  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 <span data-ttu-id="f5878-191">Tlbexp.exe を使用してインポートしたアセンブリを参照するアセンブリから、Tlbimp.exe を使用してタイプ ライブラリをエクスポートする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f5878-191">The following example illustrates using Tlbexp.exe to export a type library from an assembly that references assemblies that were imported using Tlbimp.exe.</span></span>  
  
 <span data-ttu-id="f5878-192">まず、Tlbimp.exe を使用してタイプ ライブラリ `myLib.tlb` をインポートし、`myLib.dll` として保存します。</span><span class="sxs-lookup"><span data-stu-id="f5878-192">First use Tlbimp.exe to import the type library `myLib.tlb` and save it as `myLib.dll`.</span></span>  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 <span data-ttu-id="f5878-193">上記の例で作成した `Sample.dll,` を参照する `myLib.dll` を C# コンパイラでコンパイルするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f5878-193">The following command uses the C# compiler to compile the `Sample.dll,` which references `myLib.dll` created in the previous example.</span></span>  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 <span data-ttu-id="f5878-194">`Sample.dll` を参照する `myLib.dll` 用のタイプ ライブラリを生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f5878-194">The following command generates a type library for `Sample.dll` that references `myLib.dll`.</span></span>  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5878-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5878-195">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [<span data-ttu-id="f5878-196">ツール</span><span class="sxs-lookup"><span data-stu-id="f5878-196">Tools</span></span>](index.md)
- [<span data-ttu-id="f5878-197">Regasm.exe (アセンブリ登録ツール)</span><span class="sxs-lookup"><span data-stu-id="f5878-197">Regasm.exe (Assembly Registration Tool)</span></span>](regasm-exe-assembly-registration-tool.md)
- <span data-ttu-id="f5878-198">[アセンブリからタイプ ライブラリへの変換の要約](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f5878-198">[Assembly to Type Library Conversion Summary](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>
- [<span data-ttu-id="f5878-199">Tlbimp.exe (タイプ ライブラリ インポーター)</span><span class="sxs-lookup"><span data-stu-id="f5878-199">Tlbimp.exe (Type Library Importer)</span></span>](tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="f5878-200">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="f5878-200">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
