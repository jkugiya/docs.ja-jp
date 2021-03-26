---
title: Installutil.exe (インストーラー ツール)
description: Installutil.exe (インストーラー ツール) を使用します。 このツールを使用すると、指定したアセンブリのインストーラ コンポーネントを実行することによって、サーバー リソースのインストールとアンインストールを実行できます。
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
ms.openlocfilehash: 31420f21cdcbac65f5fc565dbf6db7a8d892fb9e
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654051"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="0af93-104">Installutil.exe (インストーラー ツール)</span><span class="sxs-lookup"><span data-stu-id="0af93-104">Installutil.exe (Installer Tool)</span></span>

<span data-ttu-id="0af93-105">インストーラー ツールは、指定したアセンブリ内のインストーラー コンポーネントを実行することによってサーバー リソースのインストールとアンインストールを実行できるコマンド ライン ユーティリティです。</span><span class="sxs-lookup"><span data-stu-id="0af93-105">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="0af93-106">このツールは、<xref:System.Configuration.Install> 名前空間のクラスと組み合わせることによって動作します。</span><span class="sxs-lookup"><span data-stu-id="0af93-106">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>

<span data-ttu-id="0af93-107">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0af93-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="0af93-108">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="0af93-108">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

<span data-ttu-id="0af93-109">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="0af93-109">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="0af93-110">構文</span><span class="sxs-lookup"><span data-stu-id="0af93-110">Syntax</span></span>

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a><span data-ttu-id="0af93-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0af93-111">Parameters</span></span>

|<span data-ttu-id="0af93-112">引数</span><span class="sxs-lookup"><span data-stu-id="0af93-112">Argument</span></span>|<span data-ttu-id="0af93-113">説明</span><span class="sxs-lookup"><span data-stu-id="0af93-113">Description</span></span>|
|--------------|-----------------|
|`assembly`|<span data-ttu-id="0af93-114">インストーラー コンポーネントを実行するアセンブリのファイル名。</span><span class="sxs-lookup"><span data-stu-id="0af93-114">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="0af93-115">`/AssemblyName` オプションを使用してアセンブリの厳密な名前を指定する場合は、このパラメーターを省略します。</span><span class="sxs-lookup"><span data-stu-id="0af93-115">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|

<a name="options"></a>

## <a name="options"></a><span data-ttu-id="0af93-116">Options</span><span class="sxs-lookup"><span data-stu-id="0af93-116">Options</span></span>

|<span data-ttu-id="0af93-117">オプション</span><span class="sxs-lookup"><span data-stu-id="0af93-117">Option</span></span>|<span data-ttu-id="0af93-118">説明</span><span class="sxs-lookup"><span data-stu-id="0af93-118">Description</span></span>|
|------------|-----------------|
|`/h[elp]`<br /><br /> <span data-ttu-id="0af93-119">\- または -</span><span class="sxs-lookup"><span data-stu-id="0af93-119">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="0af93-120">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-120">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="0af93-121">`/help` *assembly*</span><span class="sxs-lookup"><span data-stu-id="0af93-121">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="0af93-122">\- または -</span><span class="sxs-lookup"><span data-stu-id="0af93-122">-or-</span></span><br /><br /> <span data-ttu-id="0af93-123">`/?` *assembly*</span><span class="sxs-lookup"><span data-stu-id="0af93-123">`/?` *assembly*</span></span>|<span data-ttu-id="0af93-124">InstallUtil.exe のコマンド構文とオプションと共に、指定したアセンブリ内でそれぞれのインストーラーによって認識される追加オプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-124">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="0af93-125">このオプションを指定すると、各インストーラー コンポーネントの <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> プロパティによって返されるテキストが InstallUtil.exe のヘルプ テキストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-125">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|
|<span data-ttu-id="0af93-126">`/AssemblyName` "*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="0af93-126">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="0af93-127">,Version=*major.minor.build.revision*</span><span class="sxs-lookup"><span data-stu-id="0af93-127">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="0af93-128">,Culture=*locale*</span><span class="sxs-lookup"><span data-stu-id="0af93-128">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="0af93-129">,PublicKeyToken=*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="0af93-129">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="0af93-130">グローバル アセンブリ キャッシュに登録されている必要があるアセンブリの厳密な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0af93-130">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="0af93-131">アセンブリ名は、バージョン、カルチャ、およびアセンブリの公開キー トークンによって完全修飾にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0af93-131">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="0af93-132">完全修飾名は、引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="0af93-132">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="0af93-133">たとえば、"myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" は、完全修飾のアセンブリ名です。</span><span class="sxs-lookup"><span data-stu-id="0af93-133">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|
|<span data-ttu-id="0af93-134">`/InstallStateDir=[` *directoryName* `]`</span><span class="sxs-lookup"><span data-stu-id="0af93-134">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="0af93-135">アセンブリをアンインストールするために使用されるデータを格納する .InstallState ファイルのディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="0af93-135">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="0af93-136">既定のディレクトリは、アセンブリを格納しているディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="0af93-136">The default is the directory that contains the assembly.</span></span>|
|<span data-ttu-id="0af93-137">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="0af93-137">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="0af93-138">インストールの進行状況を記録するログ ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0af93-138">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="0af93-139">既定では、`/LogFile` オプションを省略した場合は、*assemblyname*.InstallLog という名前のログ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-139">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="0af93-140">*filename* を省略した場合、ログ ファイルは生成されません。</span><span class="sxs-lookup"><span data-stu-id="0af93-140">If *filename* is omitted, no log file is generated.</span></span>|
|<span data-ttu-id="0af93-141">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="0af93-141">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="0af93-142">`true` の場合は出力がコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-142">If `true`, displays output to the console.</span></span> <span data-ttu-id="0af93-143">`false` (既定値) の場合はコンソールへの出力が中止されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-143">If `false` (the default), suppresses output to the console.</span></span>|
|`/ShowCallStack`|<span data-ttu-id="0af93-144">インストール中に例外が発生した場合、コール スタックがログ ファイルに出力されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-144">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|
|<span data-ttu-id="0af93-145">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="0af93-145">`/u`[`ninstall`]</span></span>|<span data-ttu-id="0af93-146">指定されたアセンブリをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="0af93-146">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="0af93-147">他のオプションとは異なり、コマンド ラインのどこにオプションを指定するかとは無関係に、`/u` はすべてのアセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-147">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a><span data-ttu-id="0af93-148">その他のインストーラー オプション</span><span class="sxs-lookup"><span data-stu-id="0af93-148">Additional Installer Options</span></span>

<span data-ttu-id="0af93-149">アセンブリ内で使用されるそれぞれのインストーラーでは、「[オプション](#options)」で示したオプション以外のオプションも認識される場合があります。</span><span class="sxs-lookup"><span data-stu-id="0af93-149">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="0af93-150">これらのオプションを確認するには、コマンド ラインで `/?` オプションまたは `/help` オプションと共にアセンブリのパスを指定して InstallUtil.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="0af93-150">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="0af93-151">これらのオプションを指定するには、InstallUtil.exe で認識されるオプションと共にそれらのオプションをコマンド ラインに含めます。</span><span class="sxs-lookup"><span data-stu-id="0af93-151">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="0af93-152">個々のインストーラー コンポーネントでサポートされるオプションのヘルプ テキストは、<xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> プロパティによって返されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-152">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0af93-153">コマンド ラインで入力された個々のオプションには、<xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> プロパティからプログラムでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0af93-153">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="0af93-154">オプションとコマンド ライン パラメーターはすべてインストール ログ ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="0af93-154">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="0af93-155">ただし、一部のインストーラー コンポーネントで認識される `/Password` パラメーターを使用する場合、パスワード情報は 8 つのアスタリスク (\*) に置き換えられ、ログ ファイルに表示されません。</span><span class="sxs-lookup"><span data-stu-id="0af93-155">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0af93-156">インストーラーに渡されるパラメーターには機密情報または個人を特定できる情報が含まれる場合があり、既定ではプレーンテキスト ログ ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="0af93-156">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="0af93-157">この動作を回避するには、コマンド ラインで Installutil.exe の後に (*filename* 引数を指定せずに) `/LogFile=` を指定して、ログ ファイルが生成されないようにします。</span><span class="sxs-lookup"><span data-stu-id="0af93-157">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="0af93-158">Remarks</span><span class="sxs-lookup"><span data-stu-id="0af93-158">Remarks</span></span>

<span data-ttu-id="0af93-159">.NET Framework アプリケーションは、従来のプログラム ファイルと関連リソースで構成されます。関連リソースには、メッセージ キュー、イベント ログ、パフォーマンス カウンターなどがあり、アプリケーションを配置するときにこれらのリソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0af93-159">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="0af93-160">アセンブリのインストーラー コンポーネントを使用すると、アプリケーションのインストール時にこれらのリソースを作成したり、アプリケーションのアンインストール時に削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="0af93-160">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="0af93-161">Installutil.exe は、これらのインストーラー コンポーネントを検出して実行します。</span><span class="sxs-lookup"><span data-stu-id="0af93-161">Installutil.exe detects and executes these installer components.</span></span>

<span data-ttu-id="0af93-162">同じコマンド行に複数のアセンブリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0af93-162">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="0af93-163">アセンブリ名の前に指定したオプションは、そのアセンブリのインストールに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-163">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="0af93-164">`/u` と `/AssemblyName` 以外のオプションは、累積されますがオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="0af93-164">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="0af93-165">つまり、あるアセンブリに指定したオプションは、そのオプションを新しい値と共に指定しない限り、後続のすべてのアセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-165">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>

<span data-ttu-id="0af93-166">オプションを指定せずにアセンブリに対して Installutil.exe を実行すると、次の 3 つのファイルがアセンブリのディレクトリ内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-166">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>

- <span data-ttu-id="0af93-167">InstallUtil.InstallLog - インストールの進行状況に関する一般的な説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0af93-167">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>

- <span data-ttu-id="0af93-168">*assemblyname*.InstallLog - インストール プロセスのコミット フェーズに固有の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0af93-168">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="0af93-169">コミット フェーズの詳細については、「<xref:System.Configuration.Install.Installer.Commit%2A> メソッド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0af93-169">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>

- <span data-ttu-id="0af93-170">*assemblyname*.InstallState - アセンブリをアンインストールするために使用されるデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0af93-170">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>

<span data-ttu-id="0af93-171">Installutil.exe は、リフレクションを使用して指定されたアセンブリを調査し、<xref:System.Configuration.Install.Installer> 属性が <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> に設定されたすべての `true` タイプを検索します。</span><span class="sxs-lookup"><span data-stu-id="0af93-171">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="0af93-172">次に、<xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> タイプの各インスタンスについて、<xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Configuration.Install.Installer> メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0af93-172">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="0af93-173">Installutil.exe は、トランザクション的な方法でインストールを実行します。つまり、いずれかのアセンブリのインストールに失敗した場合には、他のすべてのアセンブリのインストールをロールバックします。</span><span class="sxs-lookup"><span data-stu-id="0af93-173">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="0af93-174">アンインストールはトランザクション的な方法では実行されません。</span><span class="sxs-lookup"><span data-stu-id="0af93-174">Uninstall is not transactional.</span></span>

<span data-ttu-id="0af93-175">Installutil.exe では、遅延署名されたアセンブリのインストールおよびアンインストールはできませんが、厳密な名前付きアセンブリのインストールおよびアンインストールはできます。</span><span class="sxs-lookup"><span data-stu-id="0af93-175">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>

<span data-ttu-id="0af93-176">.NET Framework Version 2.0 から、32 ビット バージョンの共通言語ランタイム (CLR) は 32 ビット バージョンのインストーラー ツールにのみ付属し、64 ビット バージョンの CLR は 32 ビットおよび 64 ビットの両方のバージョンのインストーラー ツールに付属するようになりました。</span><span class="sxs-lookup"><span data-stu-id="0af93-176">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="0af93-177">64 ビットの CLR を使用しているときは、32 ビットのアセンブリをインストールするには 32 ビットのインストーラーを使用し、64 ビットおよび Microsoft Intermediate Language (MSIL) のアセンブリをインストールするには 64 ビットのインストーラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="0af93-177">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="0af93-178">どちらのバージョンのインストーラー ツールも同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="0af93-178">Both versions of the Installer tool behave the same.</span></span>

<span data-ttu-id="0af93-179">C++ を使用して作成した Windows サービスを Installutil.exe で配置することはできません。Installutil.exe は、C++ コンパイラで作成される埋め込みのネイティブ コードを認識できません。</span><span class="sxs-lookup"><span data-stu-id="0af93-179">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="0af93-180">C++ Windows サービスを Installutil.exe で配置しようとすると、<xref:System.BadImageFormatException> などの例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0af93-180">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="0af93-181">これを行うには、サービス コードを C++ モジュールに移行し、インストーラー オブジェクトを C# または Visual Basic で記述します。</span><span class="sxs-lookup"><span data-stu-id="0af93-181">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>

## <a name="examples"></a><span data-ttu-id="0af93-182">使用例</span><span class="sxs-lookup"><span data-stu-id="0af93-182">Examples</span></span>

<span data-ttu-id="0af93-183">InstallUtil.exe のコマンド構文とオプションの説明を表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>

```console
installutil /?
```

<span data-ttu-id="0af93-184">InstallUtil.exe のコマンド構文とオプションの説明を表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-184">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="0af93-185">インストーラーの <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> プロパティにヘルプ テキストが割り当てられている場合は、`myAssembly.exe` のインストーラー コンポーネントでサポートされるオプションの説明とリストも表示されます。</span><span class="sxs-lookup"><span data-stu-id="0af93-185">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>

```console
installutil /? myAssembly.exe
```

<span data-ttu-id="0af93-186">アセンブリ `myAssembly.exe` 内のインストーラー コンポーネントを実行するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-186">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>

```console
installutil myAssembly.exe
```

<span data-ttu-id="0af93-187">`/AssemblyName` スイッチと完全修飾名を使用してアセンブリのインストーラー コンポーネントを実行するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-187">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="0af93-188">ファイル名で指定されたアセンブリと厳密な名前で指定されたアセンブリのインストーラー コンポーネントを実行するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-188">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="0af93-189">`/AssemblyName` オプションはオーバーライドできないので、コマンド ラインではファイル名で指定するすべてのアセンブリを厳密な名前で指定するアセンブリよりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0af93-189">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="0af93-190">アセンブリ `myAssembly.exe` 内のアンインストーラー コンポーネントを実行するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-190">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>

```console
installutil /u myAssembly.exe
```

<span data-ttu-id="0af93-191">`myAssembly1.exe` アセンブリと `myAssembly2.exe` アセンブリ内のアンインストーラー コンポーネントを実行するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-191">The following command executes the uninstaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

<span data-ttu-id="0af93-192">コマンド ラインでの `/u` オプションの位置は重要ではないので、これは次のコマンドと同等です。</span><span class="sxs-lookup"><span data-stu-id="0af93-192">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

<span data-ttu-id="0af93-193">アセンブリ `myAssembly.exe` 内のインストーラーを実行し、進行状況に関する情報を `myLog.InstallLog` に書き込むように指定するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-193">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

<span data-ttu-id="0af93-194">アセンブリ `myAssembly.exe` 内のインストーラーを実行し、進行状況に関する情報を `myLog.InstallLog` に書き込むように指定し、インストーラーのカスタム オプション `/reg` を使用してシステム レジストリを更新するように指定するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-194">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

<span data-ttu-id="0af93-195">アセンブリ `myAssembly.exe` 内のインストーラーを実行し、インストーラーのカスタム オプション `/email` を使用してユーザーの電子メール アドレスを指定し、ログ ファイルに出力しないようにするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-195">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

<span data-ttu-id="0af93-196">`myAssembly.exe` に関するインストールの進行状況を `myLog.InstallLog` に書き込み、`myTestAssembly.exe` に関する進行状況を `myTestLog.InstallLog` に書き込むコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0af93-196">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a><span data-ttu-id="0af93-197">関連項目</span><span class="sxs-lookup"><span data-stu-id="0af93-197">See also</span></span>

- <xref:System.Configuration.Install>
- [<span data-ttu-id="0af93-198">ツール</span><span class="sxs-lookup"><span data-stu-id="0af93-198">Tools</span></span>](index.md)
- [<span data-ttu-id="0af93-199">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="0af93-199">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
