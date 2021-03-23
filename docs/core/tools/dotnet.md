---
title: dotnet コマンド
description: dotnet コマンド (.NET CLI の汎用ドライバー) とその使用方法について説明します。
ms.date: 11/11/2020
ms.openlocfilehash: 33c5f9d22166b818f5c860c4f4632d359f686919
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874538"
---
# <a name="dotnet-command"></a><span data-ttu-id="47e54-103">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-103">dotnet command</span></span>

<span data-ttu-id="47e54-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="47e54-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="47e54-105">名前</span><span class="sxs-lookup"><span data-stu-id="47e54-105">Name</span></span>

<span data-ttu-id="47e54-106">`dotnet` - .NET CLI の汎用ドライバー。</span><span class="sxs-lookup"><span data-stu-id="47e54-106">`dotnet` - The generic driver for the .NET CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="47e54-107">構文</span><span class="sxs-lookup"><span data-stu-id="47e54-107">Synopsis</span></span>

<span data-ttu-id="47e54-108">利用できるコマンドと環境に関する情報を取得するには:</span><span class="sxs-lookup"><span data-stu-id="47e54-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="47e54-109">コマンドを実行するには (SDK のインストールが必要):</span><span class="sxs-lookup"><span data-stu-id="47e54-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="47e54-110">アプリケーションを実行するには:</span><span class="sxs-lookup"><span data-stu-id="47e54-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="47e54-111">`--roll-forward` は、.NET Core 3.x 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="47e54-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="47e54-112">.NET Core 2.x には `--roll-forward-on-no-candidate-fx` を使用します。</span><span class="sxs-lookup"><span data-stu-id="47e54-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="47e54-113">説明</span><span class="sxs-lookup"><span data-stu-id="47e54-113">Description</span></span>

<span data-ttu-id="47e54-114">`dotnet` コマンドには、次の 2 つの機能があります。</span><span class="sxs-lookup"><span data-stu-id="47e54-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="47e54-115">.NET プロジェクトを操作するためのコマンドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="47e54-115">It provides commands for working with .NET projects.</span></span>

  <span data-ttu-id="47e54-116">たとえば、[`dotnet build`](dotnet-build.md) を使うと、プロジェクトをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="47e54-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="47e54-117">各コマンドには独自のオプションと引数が定義されています。</span><span class="sxs-lookup"><span data-stu-id="47e54-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="47e54-118">すべてのコマンドは、コマンドの使用方法に関する簡単なドキュメントを出力するための `--help` オプションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="47e54-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="47e54-119">.NET アプリケーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-119">It runs .NET applications.</span></span>

  <span data-ttu-id="47e54-120">アプリケーションを実行するには、アプリケーション `.dll` ファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="47e54-121">アプリケーションを実行するということは、エントリ ポイントを見つけて実行することを意味します。コンソール アプリの場合、これは `Main` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="47e54-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="47e54-122">たとえば、`dotnet myapp.dll` を使うと、`myapp` アプリケーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="47e54-123">展開オプションについては、[.NET アプリケーションの展開](../deploying/index.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-123">See [.NET application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="47e54-124">オプション</span><span class="sxs-lookup"><span data-stu-id="47e54-124">Options</span></span>

<span data-ttu-id="47e54-125">`dotnet` 単独、コマンドの実行、アプリケーションの実行にはさまざまなオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="47e54-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="47e54-126">dotnet 単独のオプション</span><span class="sxs-lookup"><span data-stu-id="47e54-126">Options for dotnet by itself</span></span>

<span data-ttu-id="47e54-127">次のオプションは、`dotnet` 単独のものです。</span><span class="sxs-lookup"><span data-stu-id="47e54-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="47e54-128">たとえば、`dotnet --info` のようにします。</span><span class="sxs-lookup"><span data-stu-id="47e54-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="47e54-129">環境に関する情報が出力されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="47e54-130">現在のオペレーティング システムや .NET バージョンのコミット SHA など、.NET のインストールとコンピューター環境に関する詳細を出力します。</span><span class="sxs-lookup"><span data-stu-id="47e54-130">Prints out detailed information about a .NET installation and the machine environment, such as the current operating system, and commit SHA of the .NET version.</span></span>

- **`--version`**

  <span data-ttu-id="47e54-131">使用中の .NET SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="47e54-131">Prints out the version of the .NET SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="47e54-132">インストールされている .NET ランタイムの一覧が出力されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-132">Prints out a list of the installed .NET runtimes.</span></span> <span data-ttu-id="47e54-133">x86 バージョンの SDK には x86 ランタイムのみが登録され、x64 バージョンの SDK には x64 ランタイムのみが登録されています。</span><span class="sxs-lookup"><span data-stu-id="47e54-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="47e54-134">インストールされている .NET SDK の一覧が出力されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-134">Prints out a list of the installed .NET SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="47e54-135">使用できるコマンドの一覧が出力されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="47e54-136">コマンドを実行するための SDK のオプション</span><span class="sxs-lookup"><span data-stu-id="47e54-136">SDK options for running a command</span></span>

<span data-ttu-id="47e54-137">次のオプションは、コマンドを指定した `dotnet` 用です。</span><span class="sxs-lookup"><span data-stu-id="47e54-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="47e54-138">たとえば、`dotnet build --help` のようにします。</span><span class="sxs-lookup"><span data-stu-id="47e54-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="47e54-139">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="47e54-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="47e54-140">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="47e54-141">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="47e54-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="47e54-142">すべてのコマンドでサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="47e54-142">Not supported in every command.</span></span> <span data-ttu-id="47e54-143">このオプションを使用できるかどうかについては、そのコマンド ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="47e54-144">`dotnet build --help` など、特定のコマンドのドキュメントを出力します。</span><span class="sxs-lookup"><span data-stu-id="47e54-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="47e54-145">各コマンドには、そのコマンドに固有のオプションが定義されています。</span><span class="sxs-lookup"><span data-stu-id="47e54-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="47e54-146">使用できるオプションの一覧については、そのコマンドのページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="47e54-147">ランタイム オプション</span><span class="sxs-lookup"><span data-stu-id="47e54-147">Runtime options</span></span>

<span data-ttu-id="47e54-148">次のオプションは、`dotnet` でアプリケーションを実行するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="47e54-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="47e54-149">たとえば、`dotnet myapp.dll --roll-forward Major` のようにします。</span><span class="sxs-lookup"><span data-stu-id="47e54-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="47e54-150">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="47e54-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="47e54-151">追加の *.deps.json* ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="47e54-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="47e54-152">*deps.json* ファイルには、依存関係、コンパイル依存関係、アセンブリ競合に対処するためのバージョン情報の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="47e54-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="47e54-153">詳細については、GitHub の「[Runtime Configuration Files](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md)」 (ランタイム構成ファイル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="47e54-154">*deps.json* ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="47e54-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="47e54-155">*deps. json* ファイルは、アプリケーションの実行に必要な依存関係に関する情報を含む構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="47e54-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="47e54-156">このファイルは、.NET SDK によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-156">This file is generated by the .NET SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="47e54-157">*runtimeconfig.json* ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="47e54-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="47e54-158">*runtimeconfig.json* ファイルは、ランタイム設定を含む構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="47e54-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="47e54-159">詳細については、[.NET ランタイム構成設定](../run-time-config/index.md#runtimeconfigjson)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-159">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="47e54-160">**`--roll-forward <SETTING>`** **.NET Core SDK 3.0 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="47e54-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="47e54-161">アプリにロール フォ ワードを適用する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="47e54-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="47e54-162">`SETTING` には次のいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="47e54-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="47e54-163">指定しない場合の既定は、`Minor` です。</span><span class="sxs-lookup"><span data-stu-id="47e54-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="47e54-164">`LatestPatch` - 最新のパッチ バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="47e54-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="47e54-165">これで、マイナー バージョンのロールフォワードが無効になります。</span><span class="sxs-lookup"><span data-stu-id="47e54-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="47e54-166">`Minor` - 要求されたマイナー バージョンが見つからない場合は、それよりも高い最小マイナー バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="47e54-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="47e54-167">要求されたマイナー バージョンが存在する場合は、LatestPatch ポリシーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="47e54-168">`Major` - 要求されたメジャー バージョンが見つからない場合は、それよりも高い最小メジャー バージョンで最小マイナー バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="47e54-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="47e54-169">要求されたメジャー バージョンが存在する場合は、Minor ポリシーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="47e54-170">`LatestMinor` - 要求されたマイナー バージョンが存在する場合でも、最上位のマイナー バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="47e54-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="47e54-171">コンポーネント ホスティング シナリオを対象としています。</span><span class="sxs-lookup"><span data-stu-id="47e54-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="47e54-172">`LatestMajor` - 要求されたメジャーが存在する場合でも、最上位のメジャー バージョンで最上位のマイナー バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="47e54-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="47e54-173">コンポーネント ホスティング シナリオを対象としています。</span><span class="sxs-lookup"><span data-stu-id="47e54-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="47e54-174">`Disable` - ロール フォワードしません。</span><span class="sxs-lookup"><span data-stu-id="47e54-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="47e54-175">指定されたバージョンにのみバインドします。</span><span class="sxs-lookup"><span data-stu-id="47e54-175">Only bind to specified version.</span></span> <span data-ttu-id="47e54-176">このポリシーは、最新のパッチにロールフォワードする機能が無効になるため、一般的な使用にはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="47e54-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="47e54-177">この値はテスト用にのみ推奨されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="47e54-178">`Disable` を除いて、すべての設定は使用できる最高のパッチ バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="47e54-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="47e54-179">ロール フォワード動作は、プロジェクト ファイル プロパティ、ランタイム構成ファイル プロパティ、および環境変数でも構成できます。</span><span class="sxs-lookup"><span data-stu-id="47e54-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="47e54-180">詳細については、「[メジャーバージョン ランタイムのロールフォワード](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="47e54-181">**`--roll-forward-on-no-candidate-fx <N>`** **.NET Core 2.x SDK で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="47e54-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="47e54-182">必要な共有フレームワークが利用できない場合の動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="47e54-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="47e54-183">`N` には以下があります。</span><span class="sxs-lookup"><span data-stu-id="47e54-183">`N` can be:</span></span>

  - <span data-ttu-id="47e54-184">`0` - マイナー バージョンのロールフォワードでも無効にします。</span><span class="sxs-lookup"><span data-stu-id="47e54-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="47e54-185">`1` - マイナー バージョンはロール フォワードしますが、メジャー バージョンはしません。</span><span class="sxs-lookup"><span data-stu-id="47e54-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="47e54-186">これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="47e54-186">This is the default behavior.</span></span>
  - <span data-ttu-id="47e54-187">`2` - マイナー バージョンとメジャー バージョンをロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="47e54-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="47e54-188">詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="47e54-189">.NET Core 3.0 以降では、このオプションは `--roll-forward` に置き換えられており、代わりにこのオプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47e54-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="47e54-190">アプリケーションを実行するために使用する .NET ランタイムのバージョン。</span><span class="sxs-lookup"><span data-stu-id="47e54-190">Version of the .NET runtime to use to run the application.</span></span>

  <span data-ttu-id="47e54-191">このオプションは、アプリケーションの `.runtimeconfig.json` ファイル内の最初のフレームワーク参照のバージョンをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="47e54-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="47e54-192">つまり、予期したとおりに動作するのは、フレームワーク参照が 1 つの場合のみです。</span><span class="sxs-lookup"><span data-stu-id="47e54-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="47e54-193">アプリケーションに複数のフレームワーク参照がある場合、このオプションを使用するとエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="47e54-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="47e54-194">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="47e54-195">全般</span><span class="sxs-lookup"><span data-stu-id="47e54-195">General</span></span>

| <span data-ttu-id="47e54-196">コマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-196">Command</span></span>                                       | <span data-ttu-id="47e54-197">関数</span><span class="sxs-lookup"><span data-stu-id="47e54-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="47e54-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="47e54-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="47e54-199">.NET アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="47e54-199">Builds a .NET application.</span></span>                                     |
| [<span data-ttu-id="47e54-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="47e54-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="47e54-201">ビルドによって起動されたサーバーとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="47e54-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="47e54-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="47e54-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="47e54-203">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="47e54-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="47e54-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="47e54-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="47e54-205">コマンドのより詳細なドキュメントをオンラインで表示します。</span><span class="sxs-lookup"><span data-stu-id="47e54-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="47e54-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="47e54-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="47e54-207">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="47e54-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="47e54-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="47e54-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="47e54-209">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="47e54-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="47e54-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="47e54-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="47e54-211">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="47e54-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="47e54-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="47e54-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="47e54-213">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="47e54-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="47e54-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="47e54-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="47e54-215">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="47e54-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="47e54-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="47e54-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="47e54-217">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="47e54-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="47e54-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="47e54-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="47e54-219">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="47e54-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="47e54-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="47e54-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="47e54-221">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="47e54-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="47e54-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="47e54-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="47e54-223">ランタイム パッケージ ストアにアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="47e54-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="47e54-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="47e54-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="47e54-225">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="47e54-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="47e54-226">プロジェクト参照</span><span class="sxs-lookup"><span data-stu-id="47e54-226">Project references</span></span>

<span data-ttu-id="47e54-227">コマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-227">Command</span></span> | <span data-ttu-id="47e54-228">関数</span><span class="sxs-lookup"><span data-stu-id="47e54-228">Function</span></span>
--- | ---
[<span data-ttu-id="47e54-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="47e54-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="47e54-230">プロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="47e54-230">Adds a project reference.</span></span>
[<span data-ttu-id="47e54-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="47e54-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="47e54-232">プロジェクト参照をリストします。</span><span class="sxs-lookup"><span data-stu-id="47e54-232">Lists project references.</span></span>
[<span data-ttu-id="47e54-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="47e54-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="47e54-234">プロジェクト参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="47e54-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="47e54-235">NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="47e54-235">NuGet packages</span></span>

<span data-ttu-id="47e54-236">コマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-236">Command</span></span> | <span data-ttu-id="47e54-237">関数</span><span class="sxs-lookup"><span data-stu-id="47e54-237">Function</span></span>
--- | ---
[<span data-ttu-id="47e54-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="47e54-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="47e54-239">NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="47e54-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="47e54-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="47e54-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="47e54-241">NuGet パッケージを削除します。</span><span class="sxs-lookup"><span data-stu-id="47e54-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="47e54-242">NuGet コマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-242">NuGet commands</span></span>

<span data-ttu-id="47e54-243">コマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-243">Command</span></span> | <span data-ttu-id="47e54-244">関数</span><span class="sxs-lookup"><span data-stu-id="47e54-244">Function</span></span>
--- | ---
[<span data-ttu-id="47e54-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="47e54-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="47e54-246">サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="47e54-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="47e54-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="47e54-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="47e54-248">パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="47e54-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="47e54-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="47e54-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="47e54-250">HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="47e54-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="47e54-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="47e54-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="47e54-252">NuGet ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="47e54-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="47e54-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="47e54-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="47e54-254">NuGet ソースを無効にします。</span><span class="sxs-lookup"><span data-stu-id="47e54-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="47e54-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="47e54-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="47e54-256">NuGet ソースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="47e54-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="47e54-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="47e54-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="47e54-258">構成されている NuGet ソースをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="47e54-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="47e54-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="47e54-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="47e54-260">NuGet ソースを削除します。</span><span class="sxs-lookup"><span data-stu-id="47e54-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="47e54-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="47e54-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="47e54-262">NuGet ソースを更新します。</span><span class="sxs-lookup"><span data-stu-id="47e54-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="47e54-263">グローバル、ツールパス、およびローカル ツールのコマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="47e54-264">ツールは、NuGet パッケージからインストールされ、コマンド プロンプトから呼び出されるコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="47e54-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="47e54-265">ツールは自分で作成することも、サードパーティによって作成されたツールをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="47e54-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="47e54-266">ツールは、グローバル ツール、ツールパス ツール、およびローカル ツールとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="47e54-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="47e54-267">詳細については、[.NET ツールの概要](global-tools.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-267">For more information, see [.NET tools overview](global-tools.md).</span></span> <span data-ttu-id="47e54-268">グローバル ツールとツールパス ツールは、.NET Core SDK 2.1 以降使用できます。</span><span class="sxs-lookup"><span data-stu-id="47e54-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="47e54-269">ローカル ツールは、.NET Core SDK 3.0 以降使用できます。</span><span class="sxs-lookup"><span data-stu-id="47e54-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="47e54-270">コマンド</span><span class="sxs-lookup"><span data-stu-id="47e54-270">Command</span></span> | <span data-ttu-id="47e54-271">関数</span><span class="sxs-lookup"><span data-stu-id="47e54-271">Function</span></span>
--- | ---
[<span data-ttu-id="47e54-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="47e54-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="47e54-273">ツールをお使いのコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="47e54-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="47e54-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="47e54-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="47e54-275">コンピューターに現在インストールされているグローバル、ツールパス、またはローカル ツールをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="47e54-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="47e54-276">dotnet tool search</span><span class="sxs-lookup"><span data-stu-id="47e54-276">dotnet tool search</span></span>](dotnet-tool-list.md) | <span data-ttu-id="47e54-277">名前またはメタデータ内に指定された検索用語が含まれるツールを NuGet.org で検索します。</span><span class="sxs-lookup"><span data-stu-id="47e54-277">Searches NuGet.org for tools that have the specified search term in their name or metadata.</span></span>
[<span data-ttu-id="47e54-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="47e54-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="47e54-279">ツールをお使いのコンピューターからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="47e54-279">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="47e54-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="47e54-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="47e54-281">コンピューターにインストールされているツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="47e54-281">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="47e54-282">その他のツール</span><span class="sxs-lookup"><span data-stu-id="47e54-282">Additional tools</span></span>

<span data-ttu-id="47e54-283">.NET Core SDK 2.1.300 以降では、`DotnetCliToolReference` を使用してプロジェクト単位でのみ入手可能であった複数のツールを .NET SDK の一部として入手できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="47e54-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET SDK.</span></span> <span data-ttu-id="47e54-284">これらのツールを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47e54-284">These tools are listed in the following table:</span></span>

| <span data-ttu-id="47e54-285">ツール</span><span class="sxs-lookup"><span data-stu-id="47e54-285">Tool</span></span>                                              | <span data-ttu-id="47e54-286">関数</span><span class="sxs-lookup"><span data-stu-id="47e54-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="47e54-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="47e54-287">dev-certs</span></span>                                         | <span data-ttu-id="47e54-288">開発証明書を作成および管理します。</span><span class="sxs-lookup"><span data-stu-id="47e54-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="47e54-289">ef</span><span class="sxs-lookup"><span data-stu-id="47e54-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="47e54-290">Entity Framework Core コマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="47e54-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="47e54-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="47e54-291">sql-cache</span></span>                                         | <span data-ttu-id="47e54-292">SQL Server キャッシュ コマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="47e54-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="47e54-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="47e54-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="47e54-294">開発ユーザーのシークレットを管理します。</span><span class="sxs-lookup"><span data-stu-id="47e54-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="47e54-295">watch</span><span class="sxs-lookup"><span data-stu-id="47e54-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="47e54-296">ファイルが変化するとコマンドを実行するファイル ウォッチャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="47e54-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="47e54-297">各ツールの詳細については、`dotnet <tool-name> --help` と入力してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-297">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="47e54-298">使用例</span><span class="sxs-lookup"><span data-stu-id="47e54-298">Examples</span></span>

<span data-ttu-id="47e54-299">新しい .NET コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="47e54-299">Create a new .NET console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="47e54-300">指定されたディレクトリにプロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="47e54-300">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="47e54-301">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="47e54-301">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="47e54-302">環境変数</span><span class="sxs-lookup"><span data-stu-id="47e54-302">Environment variables</span></span>

- <span data-ttu-id="47e54-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="47e54-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="47e54-304">.NET ランタイムが既定の場所にインストールされていない場合、その場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-304">Specifies the location of the .NET runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="47e54-305">Windows 上の既定の場所は `C:\Program Files\dotnet` です。</span><span class="sxs-lookup"><span data-stu-id="47e54-305">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="47e54-306">Linux と macOS 上の既定の場所は `/usr/share/dotnet` です。</span><span class="sxs-lookup"><span data-stu-id="47e54-306">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="47e54-307">この環境変数は、生成された実行可能ファイル (apphosts) を介してアプリを実行する場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-307">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="47e54-308">64 ビット OS 上で 32 ビット実行可能ファイルを実行する場合は、代わりに `DOTNET_ROOT(x86)` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-308">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `NUGET_PACKAGES`

  <span data-ttu-id="47e54-309">グローバル パッケージ フォルダー。</span><span class="sxs-lookup"><span data-stu-id="47e54-309">The global packages folder.</span></span> <span data-ttu-id="47e54-310">設定されていない場合は、既定で `~/.nuget/packages` (Unix の場合) または `%userprofile%\.nuget\packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="47e54-310">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="47e54-311">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-311">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="47e54-312">最初の実行時に .NET のようこそとテレメトリのメッセージを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-312">Specifies whether .NET welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="47e54-313">`true` に設定すると、これらのメッセージは表示されません (値 `true`、`1`、または `yes` が受け入れられます)。`false` に設定すると許可されます (値 `false`、`0`、または `no` が受け入れられます)。</span><span class="sxs-lookup"><span data-stu-id="47e54-313">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="47e54-314">設定しない場合、既定値は `false` であり、最初の実行時にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-314">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="47e54-315">このフラグはテレメトリには影響しません (テレメトリの送信のオプトアウトについては `DOTNET_CLI_TELEMETRY_OPTOUT` を参照)。</span><span class="sxs-lookup"><span data-stu-id="47e54-315">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="47e54-316">.NET ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-316">Specifies whether data about the .NET tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="47e54-317">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。</span><span class="sxs-lookup"><span data-stu-id="47e54-317">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="47e54-318">それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="47e54-318">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="47e54-319">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="47e54-319">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="47e54-320">.NET ランタイム、共有フレームワーク、または SDK がグローバルな場所から解決されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-320">Specifies whether .NET runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="47e54-321">設定されていない場合、既定値は 1 (論理 `true`) です。</span><span class="sxs-lookup"><span data-stu-id="47e54-321">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="47e54-322">グローバルな場所から解決せず、.NET インストールを分離するには、0 (論理 `false`) に設定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-322">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET installations.</span></span> <span data-ttu-id="47e54-323">複数レベルのルックアップの詳細については、「[Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)」 (複数レベルの SharedFX ルックアップ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-323">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="47e54-324">`DOTNET_ROLL_FORWARD` **.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="47e54-324">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="47e54-325">ロール フォワード動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-325">Determines roll forward behavior.</span></span> <span data-ttu-id="47e54-326">詳細については、この記事で前述した `--roll-forward` オプションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-326">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="47e54-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="47e54-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="47e54-328">`1` (有効) に設定した場合は、リリース バージョンからプレリリース バージョンへのロール フォワードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="47e54-328">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="47e54-329">既定 (`0` - 無効) では、.NET ランタイムのリリース バージョンが要求されるとき、インストールされているリリース バージョンのみがロール フォワードによって考慮されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-329">By default (`0` - disabled), when a release version of .NET runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="47e54-330">詳細については、「[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)」(ロールフォワード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-330">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="47e54-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **.NET Core 2.x で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="47e54-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="47e54-332">`0` に設定されている場合、マイナー バージョンのロールフォワードを無効にします。</span><span class="sxs-lookup"><span data-stu-id="47e54-332">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="47e54-333">詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-333">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="47e54-334">この設定は、.NET Core 3.0 では、`DOTNET_ROLL_FORWARD` によって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="47e54-334">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="47e54-335">代わりに、新しい設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47e54-335">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="47e54-336">`en-us` などのロケール値を使用して、CLI UI の言語を設定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-336">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="47e54-337">サポートされている値は、Visual Studio の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="47e54-337">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="47e54-338">詳細については、[Visual Studio のインストール ドキュメント](/visualstudio/install/install-visual-studio)のインストーラーの言語を変更する方法に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-338">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="47e54-339">.NET リソース マネージャーの規則が適用されるため、完全一致を選択する必要はありません。`CultureInfo` ツリーで子孫を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="47e54-339">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="47e54-340">たとえば、`fr-CA` に設定すると、CLI によって `fr` の翻訳が検索され、使用されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-340">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="47e54-341">サポートされていない言語に設定すると、CLI は英語にフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="47e54-341">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="47e54-342">GUI 対応の生成された実行可能ファイルの場合、通常は特定のクラスのエラーに対して表示されるダイアログ ポップアップが無効になります。</span><span class="sxs-lookup"><span data-stu-id="47e54-342">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="47e54-343">この場合、`stderr` にのみ書き込まれ、終了します。</span><span class="sxs-lookup"><span data-stu-id="47e54-343">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="47e54-344">CLI オプション `--additional-deps` に相当します。</span><span class="sxs-lookup"><span data-stu-id="47e54-344">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="47e54-345">検出された RID をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="47e54-345">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="47e54-346">アセンブリの解決がフォールバックする "共有ストア" の場所。</span><span class="sxs-lookup"><span data-stu-id="47e54-346">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="47e54-347">スタートアップ フックを読み込み、実行するアセンブリの一覧。</span><span class="sxs-lookup"><span data-stu-id="47e54-347">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="47e54-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="47e54-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="47e54-349">単一ファイル アプリケーションが実行前に抽出されるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="47e54-349">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="47e54-350">詳細については、「[単一ファイルの実行可能ファイル](../whats-new/dotnet-core-3-0.md#single-file-executables)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47e54-350">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="47e54-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="47e54-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="47e54-352">`dotnet.exe`、`hostfxr`、`hostpolicy` などのホスティング コンポーネントからの診断トレースを制御します。</span><span class="sxs-lookup"><span data-stu-id="47e54-352">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="47e54-353">`COREHOST_TRACE=[0/1]` - 既定値は `0` で、トレースは無効です。</span><span class="sxs-lookup"><span data-stu-id="47e54-353">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="47e54-354">`1` に設定すると、診断トレースが有効になります。</span><span class="sxs-lookup"><span data-stu-id="47e54-354">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="47e54-355">`COREHOST_TRACEFILE=<file path>` - `COREHOST_TRACE=1` によってトレースが有効になっている場合のみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-355">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="47e54-356">設定すると、指定したファイルにトレース情報が書き込まれます。それ以外の場合、トレース情報は `stderr` に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="47e54-356">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="47e54-357">**.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="47e54-357">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="47e54-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - 規定値は `4` です。</span><span class="sxs-lookup"><span data-stu-id="47e54-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="47e54-359">この設定は、`COREHOST_TRACE=1` によってトレースが有効になっている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-359">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="47e54-360">**.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="47e54-360">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="47e54-361">`4` - すべてのトレース情報が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="47e54-361">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="47e54-362">`3` - 情報、警告、およびエラー メッセージのみが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="47e54-362">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="47e54-363">`2` - 警告およびエラー メッセージのみが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="47e54-363">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="47e54-364">`1` - エラー メッセージのみが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="47e54-364">`1` - only error messages are written</span></span>

  <span data-ttu-id="47e54-365">アプリケーションの起動に関して詳しいトレース情報を取得する一般的な方法は、`COREHOST_TRACE=1` と `COREHOST_TRACEFILE=host_trace.txt` を設定してアプリケーションを実行することです。</span><span class="sxs-lookup"><span data-stu-id="47e54-365">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="47e54-366">詳細情報を含む新しいファイル `host_trace.txt` が現在のディレクトリに作成されます。</span><span class="sxs-lookup"><span data-stu-id="47e54-366">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="47e54-367">関連項目</span><span class="sxs-lookup"><span data-stu-id="47e54-367">See also</span></span>

- [<span data-ttu-id="47e54-368">ランタイム構成ファイル</span><span class="sxs-lookup"><span data-stu-id="47e54-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="47e54-369">.NET ランタイム構成設定</span><span class="sxs-lookup"><span data-stu-id="47e54-369">.NET run-time configuration settings</span></span>](../run-time-config/index.md)
