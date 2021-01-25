---
title: dotnet test コマンド
description: dotnet test コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。
ms.date: 04/29/2020
ms.openlocfilehash: 2671cbe6f610cfa8aa98e63e67f3240a1650cd6b
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757877"
---
# <a name="dotnet-test"></a><span data-ttu-id="bbc2e-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bbc2e-103">dotnet test</span></span>

<span data-ttu-id="bbc2e-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bbc2e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bbc2e-105">名前</span><span class="sxs-lookup"><span data-stu-id="bbc2e-105">Name</span></span>

<span data-ttu-id="bbc2e-106">`dotnet test` - 単体テストを実行するために使用される .NET テスト ドライバー。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bbc2e-107">構文</span><span class="sxs-lookup"><span data-stu-id="bbc2e-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="bbc2e-108">説明</span><span class="sxs-lookup"><span data-stu-id="bbc2e-108">Description</span></span>

<span data-ttu-id="bbc2e-109">`dotnet test` コマンドは、指定されたソリューションで単体テストを実行する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="bbc2e-110">`dotnet test` コマンドを実行すると、ソリューションがビルドされ、ソリューション内の各テスト プロジェクトのテスト ホスト アプリケーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="bbc2e-111">テスト ホストは、指定されたプロジェクトで、テスト フレームワークを使用してテストを実行します。たとえば、MSTest、NUnit、xUnit などです。そして、各テストの成功または失敗を報告します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="bbc2e-112">すべてのテストが成功した場合、テスト ランナーは 0 の終了コードを返します。それ以外の、いずれかのテストに失敗した場合は、1 を返します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="bbc2e-113">複数の対象を持つプロジェクトでは、対象となる各フレームワークに対してテストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="bbc2e-114">テスト ホストと単体テスト フレームワークは、NuGet パッケージとしてパッケージ化され、プロジェクトの通常の依存関係として復元されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="bbc2e-115">テスト プロジェクトでは、通常の `<PackageReference>` 要素を使用してテスト ランナーを指定します。次のサンプル プロジェクト ファイルのようになります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="bbc2e-116">`Microsoft.NET.Test.Sdk` がテスト ホストの場合、`xunit` はテスト フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="bbc2e-117">また、`xunit.runner.visualstudio` はテスト アダプターであり、xUnit フレームワークはテスト ホストと連携できます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="bbc2e-118">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="bbc2e-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="bbc2e-119">引数</span><span class="sxs-lookup"><span data-stu-id="bbc2e-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="bbc2e-120">テスト プロジェクトへのパス。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-120">Path to the test project.</span></span>
  - <span data-ttu-id="bbc2e-121">ソリューションへのパス。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-121">Path to the solution.</span></span>
  - <span data-ttu-id="bbc2e-122">プロジェクトまたはソリューションを含むディレクトリへのパス。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="bbc2e-123">テスト プロジェクト " *.dll*" ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="bbc2e-124">指定されていない場合、プロジェクトまたはソリューションが現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="bbc2e-125">オプション</span><span class="sxs-lookup"><span data-stu-id="bbc2e-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="bbc2e-126">追加のテスト アダプターを検索するディレクトリへのパス。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="bbc2e-127">サフィックス `.TestAdapter.dll` を持つ " *.dll*" ファイルのみが検査されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="bbc2e-128">指定しない場合、テスト " *.dll*" のディレクトリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="bbc2e-129">変更履歴モードでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="bbc2e-130">このオプションは、テスト ホストがクラッシュする原因となる問題のあるテストを分離するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="bbc2e-131">クラッシュが検出されると、クラッシュ前に実行されたテストの順序をキャプチャするシーケンス ファイルが `TestResults/<Guid>/<Guid>_Sequence.xml` に作成されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="bbc2e-132">**`--blame-crash`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="bbc2e-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="bbc2e-133">テスト ホストが予期せずに終了した場合に、変更履歴モードでテストを実行して、クラッシュ ダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="bbc2e-134">このオプションは、使用されている .NET のバージョン、エラーの種類、およびオペレーティング システムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-134">This option depends on the version of .NET used, the type of error, and the operating system.</span></span>
  
  <span data-ttu-id="bbc2e-135">マネージド コードでの例外の場合、ダンプは .NET 5.0 以降のバージョンで自動的に収集されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-135">For exceptions in managed code, a dump will be automatically collected on .NET 5.0 and later versions.</span></span> <span data-ttu-id="bbc2e-136">testhost や、やはり .NET 5.0 で実行されてクラッシュした子プロセスのダンプが生成されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-136">It will generate a dump for testhost or any child process that also ran on .NET 5.0 and crashed.</span></span> <span data-ttu-id="bbc2e-137">ネイティブ コードでのクラッシュの場合、ダンプは生成されません。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-137">Crashes in native code will not generate a dump.</span></span> <span data-ttu-id="bbc2e-138">このオプションは、Windows、macOS、Linux で動作します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-138">This option works on Windows, macOS, and Linux.</span></span>
  
  <span data-ttu-id="bbc2e-139">ネイティブ コードでのクラッシュ ダンプ、または .NET Core 3.1 以前のバージョンを使用しているときのクラッシュ ダンプは、Windows 上でのみ、Procdump を使用して収集できます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-139">Crash dumps in native code, or when using .NET Core 3.1 or earlier versions, can only be collected on Windows, by using Procdump.</span></span> <span data-ttu-id="bbc2e-140">*procdump.exe* および *procdump64.exe* を含むディレクトリが、PATH または PROCDUMP_PATH 環境変数に指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-140">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="bbc2e-141">[ツールをダウンロード](/sysinternals/downloads/procdump)します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-141">[Download the tools](/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="bbc2e-142">`--blame` を意味します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-142">Implies `--blame`.</span></span>
  
  <span data-ttu-id="bbc2e-143">.NET 5.0 以降で実行されているネイティブ アプリケーションからクラッシュ ダンプを収集するには、`VSTEST_DUMP_FORCEPROCDUMP` 環境変数を `1` に設定することで、Procdump を強制的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-143">To collect a crash dump from a native application running on .NET 5.0 or later, the usage of Procdump can be forced by setting the `VSTEST_DUMP_FORCEPROCDUMP` environment variable to `1`.</span></span>

- <span data-ttu-id="bbc2e-144">**`--blame-crash-dump-type <DUMP_TYPE>`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="bbc2e-144">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="bbc2e-145">収集されるクラッシュ ダンプの種類。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-145">The type of crash dump to be collected.</span></span> <span data-ttu-id="bbc2e-146">`--blame-crash` を意味します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-146">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="bbc2e-147">**`--blame-crash-collect-always`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="bbc2e-147">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="bbc2e-148">予期しないテスト ホストの終了だけでなく、予期されていたものに対しても、クラッシュ ダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-148">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="bbc2e-149">**`--blame-hang`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="bbc2e-149">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="bbc2e-150">変更履歴モードでテストを実行し、テストが指定のタイムアウトを超えたときにハング ダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-150">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="bbc2e-151">**`--blame-hang-dump-type <DUMP_TYPE>`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="bbc2e-151">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="bbc2e-152">収集されるクラッシュ ダンプの種類。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-152">The type of crash dump to be collected.</span></span> <span data-ttu-id="bbc2e-153">必ず、`full`、`mini`、または `none` になります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-153">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="bbc2e-154">`none` が指定されている場合、タイムアウト時にテスト ホストが終了されますが、ダンプは収集されません。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-154">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="bbc2e-155">`--blame-hang` を意味します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-155">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="bbc2e-156">**`--blame-hang-timeout <TIMESPAN>`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="bbc2e-156">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="bbc2e-157">テストごとのタイムアウト。それが過ぎると、ハング ダンプがトリガーされ、テスト ホスト プロセスとそのすべての子プロセスは、ダンプされて終了されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-157">Per-test timeout, after which a hang dump is triggered and the test host process and all of its child processes are dumped and terminated.</span></span> <span data-ttu-id="bbc2e-158">タイムアウト値は、次のいずれかの形式で指定されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-158">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="bbc2e-159">1.5h、1.5hour、1.5hours</span><span class="sxs-lookup"><span data-stu-id="bbc2e-159">1.5h, 1.5hour, 1.5hours</span></span>
  - <span data-ttu-id="bbc2e-160">90m、90min、90minute、90minutes</span><span class="sxs-lookup"><span data-stu-id="bbc2e-160">90m, 90min, 90minute, 90minutes</span></span>
  - <span data-ttu-id="bbc2e-161">5400s、5400sec、5400second、5400seconds</span><span class="sxs-lookup"><span data-stu-id="bbc2e-161">5400s, 5400sec, 5400second, 5400seconds</span></span>
  - <span data-ttu-id="bbc2e-162">5400000ms、5400000mil、5400000millisecond、5400000milliseconds</span><span class="sxs-lookup"><span data-stu-id="bbc2e-162">5400000ms, 5400000mil, 5400000millisecond, 5400000milliseconds</span></span>

  <span data-ttu-id="bbc2e-163">単位が使用されていない場合 (例: 5400000)、値はミリ秒単位であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-163">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="bbc2e-164">データ ドリブン テストと共に使用すると、タイムアウトの動作は、利用するテスト アダプターに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-164">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="bbc2e-165">xUnit および NUnit の場合、タイムアウトはテスト ケースの後に毎回更新されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-165">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="bbc2e-166">MSTest の場合、すべてのテスト ケースにこのタイムアウトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-166">For MSTest, the timeout is used for all test cases.</span></span> <span data-ttu-id="bbc2e-167">このオプションは、netcoreapp 2.1 以降がインストールされている Windows、netcoreapp 3.1 以降がインストールされている Linux、net5.0 以降がインストールされている macOS でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-167">This option is supported on Windows with netcoreapp2.1 and later, on Linux with netcoreapp3.1 and later, and on macOS with net5.0 or later.</span></span> <span data-ttu-id="bbc2e-168">`--blame` と `--blame-hang` を意味します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-168">Implies `--blame` and `--blame-hang`.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="bbc2e-169">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-169">Defines the build configuration.</span></span> <span data-ttu-id="bbc2e-170">既定値は `Debug` ですが、プロジェクトの構成がこの既定の SDK 設定をオーバーライドする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-170">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="bbc2e-171">テストの実行のためのデータ コレクターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-171">Enables data collector for the test run.</span></span> <span data-ttu-id="bbc2e-172">詳細については、[「Monitor and analyze test run」](https://aka.ms/vstest-collect) (テストの実行のモニターと分析) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-172">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="bbc2e-173">.NET Core でサポートされている任意のプラットフォーム上のコード カバレッジを収集するには、[Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) をインストールし、`--collect:"XPlat Code Coverage"` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-173">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="bbc2e-174">Windows では、`--collect "Code Coverage"` オプションを使用してコード カバレッジを収集できます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-174">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="bbc2e-175">このオプションを選択すると、 *.coverage* ファイルが生成されます。このファイルは、Visual Studio 2019 Enterprise で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-175">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="bbc2e-176">詳細については、[コード カバレッジの使用](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested)に関するページと「[コード カバレッジ分析のカスタマイズ](/visualstudio/test/customizing-code-coverage-analysis)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-176">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="bbc2e-177">テスト プラットフォームの診断モードを有効にし、指定したファイルとそれ以降のファイルに診断メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-177">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="bbc2e-178">メッセージをログに記録するプロセスによって、テスト ホスト ログの `*.host_<date>.txt` やデータ コレクター ログの `*.datacollector_<date>.txt` などの、作成されるファイルが決まります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-178">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bbc2e-179">テスト バイナリに `dotnet` または .NET Framework テスト ホストを強制的に使用します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-179">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="bbc2e-180">このオプションでは、使用するホストの種類のみが決定されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-180">This option only determines which type of host to use.</span></span> <span data-ttu-id="bbc2e-181">実際に使用されるフレームワークのバージョンは、テスト プロジェクトの "*runtimeconfig. json*" によって決まります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-181">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="bbc2e-182">指定しない場合、[TargetFramework アセンブリ属性](/dotnet/api/system.runtime.versioning.targetframeworkattribute) を使用してホストの種類が決定されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-182">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="bbc2e-183">その属性が " *.dll*" から削除されると、.NET Framework ホストが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-183">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="bbc2e-184">指定された式を使用して、現在のプロジェクト内のテストを除外します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-184">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="bbc2e-185">詳細については、「[フィルター オプションの詳細](#filter-option-details)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-185">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="bbc2e-186">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[選択的単体テストの実行](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-186">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="bbc2e-187">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-187">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="bbc2e-188">コマンドを停止して、ユーザーの入力または操作のために待機させることができます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-188">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="bbc2e-189">たとえば、認証を完了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-189">For example, to complete authentication.</span></span> <span data-ttu-id="bbc2e-190">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-190">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="bbc2e-191">テスト結果のロガーを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-191">Specifies a logger for test results.</span></span> <span data-ttu-id="bbc2e-192">MSBuild とは異なり、dotnet テストでは省略形は受け入れられません。`-l "console;v=d"` ではなく `-l "console;verbosity=detailed"` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-192">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span> <span data-ttu-id="bbc2e-193">複数のロガーを有効にするには、パラメーターを複数回指定します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-193">Specify the parameter multiple times to enable multiple loggers.</span></span>

- **`--no-build`**

  <span data-ttu-id="bbc2e-194">実行前にテスト プロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-194">Doesn't build the test project before running it.</span></span> <span data-ttu-id="bbc2e-195">また、- `--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-195">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="bbc2e-196">Microsoft TestPlatform バナーを表示せずにテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-196">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="bbc2e-197">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-197">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bbc2e-198">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-198">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="bbc2e-199">実行するバイナリを検索するディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-199">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="bbc2e-200">指定しない場合、既定のパスは `./bin/<configuration>/<framework>/` になります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-200">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="bbc2e-201">(`TargetFrameworks` プロパティを使用した) ターゲット フレームワークが複数あるプロジェクトの場合は、このオプションを指定するときに `--framework` も定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-201">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="bbc2e-202">`dotnet test` では常に、出力ディレクトリからテストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-202">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="bbc2e-203"><xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> を使用して、出力ディレクトリ内のテスト資産を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-203">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="bbc2e-204">テスト結果が配置されるディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-204">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="bbc2e-205">指定されたディレクトリが存在しない場合は、作成されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-205">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="bbc2e-206">既定値は、プロジェクト ファイルが含まれるディレクトリの `TestResults` です。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-206">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="bbc2e-207">テスト対象のターゲット ランタイム。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-207">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="bbc2e-208">テストの実行に使用する `.runsettings` ファイルです。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-208">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="bbc2e-209">`TargetPlatform` 要素 (x86|x64) は `dotnet test` には影響しません。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-209">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="bbc2e-210">x86 を対象とするテストを実行するには、x86 バージョンの .NET Core をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-210">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="bbc2e-211">パスにある *dotnet.exe* のビットは、テストを実行するために使用されるものです。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-211">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="bbc2e-212">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-212">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="bbc2e-213">`.runsettings` ファイルを使用して単体テストを構成します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-213">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="bbc2e-214">テスト実行を構成する</span><span class="sxs-lookup"><span data-stu-id="bbc2e-214">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="bbc2e-215">テストを実行する代わりに、検出されたテストを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-215">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bbc2e-216">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-216">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bbc2e-217">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-217">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="bbc2e-218">既定値は、`minimal` です。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-218">The default is `minimal`.</span></span> <span data-ttu-id="bbc2e-219">詳細については、「<xref:Microsoft.Build.Framework.LoggerVerbosity>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-219">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="bbc2e-220">**`RunSettings`** 引数</span><span class="sxs-lookup"><span data-stu-id="bbc2e-220">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="bbc2e-221">インラインの `RunSettings` は、コマンド ラインの最後の引数として "-- " の後に渡されます (-- の後のスペースに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-221">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="bbc2e-222">インラインの `RunSettings` は `[name]=[value]` のペアとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-222">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="bbc2e-223">複数の `[name]=[value]` のペアを区切るにはスペースを使用します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-223">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="bbc2e-224">例 : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="bbc2e-224">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="bbc2e-225">詳しくは、「[コマンド ラインで RunSettings 引数を渡す](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-225">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="bbc2e-226">使用例</span><span class="sxs-lookup"><span data-stu-id="bbc2e-226">Examples</span></span>

- <span data-ttu-id="bbc2e-227">現在のディレクトリのプロジェクトでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-227">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="bbc2e-228">`test1` プロジェクトでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-228">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="bbc2e-229">現在のディレクトリでプロジェクトのテストを実行し、trx 形式でテスト結果ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-229">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="bbc2e-230">現在のディレクトリでプロジェクトのテストを実行し、([Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) コレクター統合をインストールした後) コード カバレッジ ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-230">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="bbc2e-231">現在のディレクトリでプロジェクトのテストを実行し、コード カバレッジ ファイルを生成します (Windows のみ)。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-231">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="bbc2e-232">現在のディレクトリでプロジェクトのテストを実行し、詳細をコンソールに記録します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-232">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="bbc2e-233">現在のディレクトリのプロジェクトでテストを実行し、テスト ホストがクラッシュしたときに実行されていたテストを報告します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-233">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="bbc2e-234">フィルター オプションの詳細</span><span class="sxs-lookup"><span data-stu-id="bbc2e-234">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="bbc2e-235">`<Expression>` の形式は `<property><operator><value>[|&<Expression>]` です。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-235">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="bbc2e-236">`<property>` は `Test Case` の属性です。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-236">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="bbc2e-237">よく利用される単体テスト フレームワークでサポートされるプロパティは以下の通りです。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-237">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="bbc2e-238">テスト フレームワーク</span><span class="sxs-lookup"><span data-stu-id="bbc2e-238">Test Framework</span></span> | <span data-ttu-id="bbc2e-239">サポートされるプロパティ</span><span class="sxs-lookup"><span data-stu-id="bbc2e-239">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="bbc2e-240">MSTest</span><span class="sxs-lookup"><span data-stu-id="bbc2e-240">MSTest</span></span>         | <ul><li><span data-ttu-id="bbc2e-241">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="bbc2e-241">FullyQualifiedName</span></span></li><li><span data-ttu-id="bbc2e-242">名前</span><span class="sxs-lookup"><span data-stu-id="bbc2e-242">Name</span></span></li><li><span data-ttu-id="bbc2e-243">ClassName</span><span class="sxs-lookup"><span data-stu-id="bbc2e-243">ClassName</span></span></li><li><span data-ttu-id="bbc2e-244">優先度</span><span class="sxs-lookup"><span data-stu-id="bbc2e-244">Priority</span></span></li><li><span data-ttu-id="bbc2e-245">TestCategory</span><span class="sxs-lookup"><span data-stu-id="bbc2e-245">TestCategory</span></span></li></ul> |
| <span data-ttu-id="bbc2e-246">xUnit</span><span class="sxs-lookup"><span data-stu-id="bbc2e-246">xUnit</span></span>          | <ul><li><span data-ttu-id="bbc2e-247">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="bbc2e-247">FullyQualifiedName</span></span></li><li><span data-ttu-id="bbc2e-248">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bbc2e-248">DisplayName</span></span></li><li><span data-ttu-id="bbc2e-249">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="bbc2e-249">Category</span></span></li></ul>                                 |
| <span data-ttu-id="bbc2e-250">NUnit</span><span class="sxs-lookup"><span data-stu-id="bbc2e-250">NUnit</span></span>          | <ul><li><span data-ttu-id="bbc2e-251">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="bbc2e-251">FullyQualifiedName</span></span></li><li><span data-ttu-id="bbc2e-252">名前</span><span class="sxs-lookup"><span data-stu-id="bbc2e-252">Name</span></span></li><li><span data-ttu-id="bbc2e-253">TestCategory</span><span class="sxs-lookup"><span data-stu-id="bbc2e-253">TestCategory</span></span></li><li><span data-ttu-id="bbc2e-254">優先度</span><span class="sxs-lookup"><span data-stu-id="bbc2e-254">Priority</span></span></li></ul>                                   |

<span data-ttu-id="bbc2e-255">`<operator>` は、プロパティと値の関係を示します。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-255">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="bbc2e-256">演算子</span><span class="sxs-lookup"><span data-stu-id="bbc2e-256">Operator</span></span> | <span data-ttu-id="bbc2e-257">関数</span><span class="sxs-lookup"><span data-stu-id="bbc2e-257">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="bbc2e-258">完全一致</span><span class="sxs-lookup"><span data-stu-id="bbc2e-258">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="bbc2e-259">完全一致ではない</span><span class="sxs-lookup"><span data-stu-id="bbc2e-259">Not exact match</span></span> |
| `~`      | <span data-ttu-id="bbc2e-260">内容</span><span class="sxs-lookup"><span data-stu-id="bbc2e-260">Contains</span></span>        |
| `!~`     | <span data-ttu-id="bbc2e-261">含まない</span><span class="sxs-lookup"><span data-stu-id="bbc2e-261">Not contains</span></span>    |

<span data-ttu-id="bbc2e-262">`<value>` は文字列です。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-262">`<value>` is a string.</span></span> <span data-ttu-id="bbc2e-263">すべての参照で大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-263">All the lookups are case insensitive.</span></span>

<span data-ttu-id="bbc2e-264">`<operator>` を含まない式は、自動的に `FullyQualifiedName` プロパティの `contains` とみなされます (たとえば、`dotnet test --filter xyz` は `dotnet test --filter FullyQualifiedName~xyz` と同じです)。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-264">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="bbc2e-265">式は条件演算子を使用して結合できます。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-265">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="bbc2e-266">演算子</span><span class="sxs-lookup"><span data-stu-id="bbc2e-266">Operator</span></span>            | <span data-ttu-id="bbc2e-267">関数</span><span class="sxs-lookup"><span data-stu-id="bbc2e-267">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="bbc2e-268">OR</span><span class="sxs-lookup"><span data-stu-id="bbc2e-268">OR</span></span>       |
| `&`                 | <span data-ttu-id="bbc2e-269">AND</span><span class="sxs-lookup"><span data-stu-id="bbc2e-269">AND</span></span>      |

<span data-ttu-id="bbc2e-270">条件演算子を使用する場合は、式をかっこで囲みます (例: `(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-270">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="bbc2e-271">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[選択的単体テストの実行](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bbc2e-271">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bbc2e-272">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbc2e-272">See also</span></span>

- [<span data-ttu-id="bbc2e-273">フレームワークとターゲット</span><span class="sxs-lookup"><span data-stu-id="bbc2e-273">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="bbc2e-274">.NET Runtime Identifier (RID) カタログ</span><span class="sxs-lookup"><span data-stu-id="bbc2e-274">.NET Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="bbc2e-275">コマンドラインを使用して runsettings 引数を渡す</span><span class="sxs-lookup"><span data-stu-id="bbc2e-275">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
