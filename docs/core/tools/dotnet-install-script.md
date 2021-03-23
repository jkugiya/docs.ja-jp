---
title: dotnet-install スクリプト
description: .NET SDK と共有ランタイムをインストールするための dotnet-install スクリプトについて説明します。
ms.date: 09/22/2020
ms.openlocfilehash: 45b5a15bdbaa3f3167dd434e2600e33b69dc9b85
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875162"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="cd8c4-103">dotnet-install スクリプト リファレンス</span><span class="sxs-lookup"><span data-stu-id="cd8c4-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="cd8c4-104">名前</span><span class="sxs-lookup"><span data-stu-id="cd8c4-104">Name</span></span>

<span data-ttu-id="cd8c4-105">`dotnet-install.ps1` | `dotnet-install.sh` - .NET SDK と共有ランタイムをインストールするために使用するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cd8c4-106">構文</span><span class="sxs-lookup"><span data-stu-id="cd8c4-106">Synopsis</span></span>

<span data-ttu-id="cd8c4-107">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress] [-ProxyBypassList <LIST_OF_URLS>]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

<span data-ttu-id="cd8c4-108">Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

<span data-ttu-id="cd8c4-109">bash スクリプトは PowerShell のスイッチも読み取るので、Linux/macOS システムのスクリプトで PowerShell のスイッチを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-109">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

## <a name="description"></a><span data-ttu-id="cd8c4-110">説明</span><span class="sxs-lookup"><span data-stu-id="cd8c4-110">Description</span></span>

<span data-ttu-id="cd8c4-111">`dotnet-install` スクリプトによって、.NET CLI や共有ランタイムを含む .NET SDK の非管理者インストールが実行されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-111">The `dotnet-install` scripts perform a non-admin installation of the .NET SDK, which includes the .NET CLI and the shared runtime.</span></span> <span data-ttu-id="cd8c4-112">次の 2 つのスクリプトがあります。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-112">There are two scripts:</span></span>

* <span data-ttu-id="cd8c4-113">Windows 上で動作する PowerShell スクリプト。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-113">A PowerShell script that works on Windows.</span></span>
* <span data-ttu-id="cd8c4-114">Linux/macOS で動作する bash スクリプト。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-114">A bash script that works on Linux/macOS.</span></span>

> [!NOTE]
> <span data-ttu-id="cd8c4-115">.NET によって利用統計情報が収集されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-115">.NET collects telemetry data.</span></span> <span data-ttu-id="cd8c4-116">詳細とオプトアウトの方法については、「[.NET SDK 製品利用統計情報](telemetry.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-116">To learn more and how to opt out, see [.NET SDK telemetry](telemetry.md).</span></span>

### <a name="purpose"></a><span data-ttu-id="cd8c4-117">目的</span><span class="sxs-lookup"><span data-stu-id="cd8c4-117">Purpose</span></span>

 <span data-ttu-id="cd8c4-118">このスクリプトの用途は本来、次のような継続的インテグレーション (CI) シナリオ向けとして意図されています。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-118">The intended use of the scripts is for Continuous Integration (CI) scenarios, where:</span></span>

* <span data-ttu-id="cd8c4-119">ユーザーの操作と管理者権限なしで SDK をインストールする必要がある。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-119">The SDK needs to be installed without user interaction and without admin rights.</span></span>
* <span data-ttu-id="cd8c4-120">SDK インストールを複数の CI 実行間で保持する必要がない。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-120">The SDK installation doesn't need to persist across multiple CI runs.</span></span>

  <span data-ttu-id="cd8c4-121">イベントの一般的なシーケンス:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-121">The typical sequence of events:</span></span>
  * <span data-ttu-id="cd8c4-122">CI がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-122">CI is triggered.</span></span>
  * <span data-ttu-id="cd8c4-123">CI により、これらのスクリプトの 1 つを利用して SDK がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-123">CI installs the SDK using one of these scripts.</span></span>
  * <span data-ttu-id="cd8c4-124">CI でその作業が完了し、SDK インストールを含む、一時的なデータが消去されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-124">CI finishes its work and clears temporary data including the SDK installation.</span></span>

<span data-ttu-id="cd8c4-125">開発環境を設定するか、アプリを実行するには、これらのスクリプトではなく、インストーラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-125">To set up a development environment or to run apps, use the installers rather than these scripts.</span></span>

### <a name="recommended-version"></a><span data-ttu-id="cd8c4-126">推奨されるバージョン</span><span class="sxs-lookup"><span data-stu-id="cd8c4-126">Recommended version</span></span>

<span data-ttu-id="cd8c4-127">安定したバージョンのスクリプトを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-127">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="cd8c4-128">Bash (Linux、macOS): <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="cd8c4-128">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="cd8c4-129">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="cd8c4-129">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

### <a name="script-behavior"></a><span data-ttu-id="cd8c4-130">スクリプトの動作</span><span class="sxs-lookup"><span data-stu-id="cd8c4-130">Script behavior</span></span>

<span data-ttu-id="cd8c4-131">スクリプトの動作は両方とも同じです。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-131">Both scripts have the same behavior.</span></span> <span data-ttu-id="cd8c4-132">CLI ビルド ドロップから ZIP/tarball ファイルをダウンロードし、既定の場所または `-InstallDir|--install-dir` で指定された場所へのインストールに進みます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-132">They download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span>

<span data-ttu-id="cd8c4-133">既定では、インストール スクリプトは SDK をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-133">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="cd8c4-134">共有ランタイムの取得だけを行いたい場合は、`-Runtime|--runtime` 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-134">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="cd8c4-135">既定では、スクリプトはインストールの場所を現在のセッションの $PATH に追加します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-135">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="cd8c4-136">`-NoPath|--no-path` 引数を指定することによってこの既定の動作をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-136">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span> <span data-ttu-id="cd8c4-137">スクリプトでは、`DOTNET_ROOT` 環境変数は設定されません。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-137">The script doesn't set the `DOTNET_ROOT` environment variable.</span></span>

<span data-ttu-id="cd8c4-138">スクリプトを実行する前に、必要な[依存関係](../install/windows.md#dependencies)をすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-138">Before running the script, install the required [dependencies](../install/windows.md#dependencies).</span></span>

<span data-ttu-id="cd8c4-139">`-Version|--version` 引数を使用して、特定のバージョンをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-139">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="cd8c4-140">バージョンには 3 つの部分からなるバージョン番号 (`2.1.0` など) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-140">The version must be specified as a three-part version number, such as `2.1.0`.</span></span> <span data-ttu-id="cd8c4-141">バージョンが指定されていない場合、スクリプトでは `latest` バージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-141">If the version isn't specified, the script installs the `latest` version.</span></span>

<span data-ttu-id="cd8c4-142">インストール スクリプトでは、Windows 上のレジストリは更新されません。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-142">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="cd8c4-143">zip 形式のバイナリがダウンロードされて、フォルダーにコピーされるだけです。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-143">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="cd8c4-144">レジストリ キーの値を更新する必要がある場合は、.NET インストーラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-144">If you want registry key values to be updated, use the .NET installers.</span></span>

## <a name="options"></a><span data-ttu-id="cd8c4-145">オプション</span><span class="sxs-lookup"><span data-stu-id="cd8c4-145">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="cd8c4-146">インストールする .NET バイナリのアーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-146">Architecture of the .NET binaries to install.</span></span> <span data-ttu-id="cd8c4-147">指定できる値は、`<auto>`、`amd64`、`x64`、`x86`、`arm64`、および `arm` です。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-147">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="cd8c4-148">既定値は `<auto>` です。これは実行中の OS アーキテクチャを示します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-148">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="cd8c4-149">Azure フィードの URL をインストーラーに指定します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-149">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="cd8c4-150">この値は変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-150">We recommended that you don't change this value.</span></span> <span data-ttu-id="cd8c4-151">既定値は `https://dotnetcli.azureedge.net/dotnet` です。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-151">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="cd8c4-152">インストールのソース チャネルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-152">Specifies the source channel for the installation.</span></span> <span data-ttu-id="cd8c4-153">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-153">The possible values are:</span></span>

  - <span data-ttu-id="cd8c4-154">`Current` - 最新リリース。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-154">`Current` - Most current release.</span></span>
  - <span data-ttu-id="cd8c4-155">`LTS` - 長期的なサポート チャネル (サポートされている最新リリース)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-155">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="cd8c4-156">特定のリリースを表す X.Y 形式の 2 部構成のバージョン (たとえば、`2.1` または `3.0`)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-156">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="cd8c4-157">ブランチ名: たとえば、`release/3.1.1xx` または `master` (夜間リリース用)</span><span class="sxs-lookup"><span data-stu-id="cd8c4-157">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="cd8c4-158">プレビュー チャネルからバージョンをインストールするには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-158">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="cd8c4-159">「[インストーラーとバイナリ](https://github.com/dotnet/core-sdk#installers-and-binaries)」に記載されているチャネルの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-159">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="cd8c4-160">既定値は `LTS` です。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-160">The default value is `LTS`.</span></span> <span data-ttu-id="cd8c4-161">.NET のサポート チャネルの詳細については、「[.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」(.NET のサポート ポリシー) ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-161">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="cd8c4-162">設定すると、スクリプトでインストールは実行されません。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-162">If set, the script won't perform the installation.</span></span> <span data-ttu-id="cd8c4-163">代わりに、現在要求されているバージョンの .NET CLI を一貫してインストールするために使用するコマンド ラインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-163">Instead, it displays what command line to use to consistently install the currently requested version of the .NET CLI.</span></span> <span data-ttu-id="cd8c4-164">たとえば、バージョン `latest` を指定すると、そのバージョンのリンクが表示されるので、ビルド スクリプトで確定的にこのコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-164">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="cd8c4-165">また、自分でインストールまたはダウンロードしたい場合、バイナリの場所も表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-165">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="cd8c4-166">Azure フィードに付加するクエリ文字列として使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-166">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="cd8c4-167">非公開の BLOB ストレージ アカウントを使用するように URL を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-167">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="cd8c4-168">スクリプトのヘルプを出力します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-168">Prints out help for the script.</span></span> <span data-ttu-id="cd8c4-169">bash スクリプトのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-169">Applies only to bash script.</span></span> <span data-ttu-id="cd8c4-170">PowerShell の場合、`Get-Help ./dotnet-install.ps1` を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-170">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="cd8c4-171">インストール パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-171">Specifies the installation path.</span></span> <span data-ttu-id="cd8c4-172">存在しない場合は、ディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-172">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="cd8c4-173">既定値は、 *%LocalAppData%\Microsoft\dotnet* (Windows) または */usr/share/dotnet* (Linux と macOS) です。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-173">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="cd8c4-174">バイナリは、このディレクトリに直接配置されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-174">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="cd8c4-175">SDK バージョンを決定するために使用される [global.json](global-json.md) ファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-175">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="cd8c4-176">*global.json* ファイルには `sdk:version` の値が必要です。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-176">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="cd8c4-177">[Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) からのダウンロードを無効にし、キャッシュされていないフィードを直接使用します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-177">Disables downloading from the [Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="cd8c4-178">設定すると、インストール フォルダーは現在のセッションのパスにはエクスポートされません。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-178">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="cd8c4-179">既定では、スクリプトによって PATH が変更されます。これにより、インストール後すぐに .NET CLI を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-179">By default, the script modifies the PATH, which makes the .NET CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="cd8c4-180">設定すると、インストーラーで Web 要求を行うときにプロキシが使われます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-180">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="cd8c4-181">(Windows でのみ有効)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-181">(Only valid for Windows.)</span></span>

- **`-ProxyBypassList <LIST_OF_URLS>`**

  <span data-ttu-id="cd8c4-182">`ProxyAddress` で設定されている場合、プロキシをバイパスする URL をコンマ区切りの一覧で提供します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-182">If set with `ProxyAddress`, provides a list of comma-separated urls that will bypass the proxy.</span></span> <span data-ttu-id="cd8c4-183">(Windows でのみ有効)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-183">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="cd8c4-184">設定すると、プロキシ アドレスの使用時に、インストーラーでは現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-184">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="cd8c4-185">(Windows でのみ有効)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-185">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="cd8c4-186">SDK 全体ではなく共有ランタイムのみがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-186">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="cd8c4-187">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-187">The possible values are:</span></span>

  - <span data-ttu-id="cd8c4-188">`dotnet` - `Microsoft.NETCore.App` 共有ランタイム。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-188">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="cd8c4-189">`aspnetcore` - `Microsoft.AspNetCore.App` 共有ランタイム。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-189">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="cd8c4-190">`windowsdesktop` - `Microsoft.WindowsDesktop.App` 共有ランタイム。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-190">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- <span data-ttu-id="cd8c4-191">**`--runtime-id <RID>` [非推奨]**</span><span class="sxs-lookup"><span data-stu-id="cd8c4-191">**`--runtime-id <RID>` [Deprecated]**</span></span>

  <span data-ttu-id="cd8c4-192">ツールのインストール先の[ランタイム識別子](../rid-catalog.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-192">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="cd8c4-193">Portable Linux には `linux-x64` を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-193">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="cd8c4-194">(Linux または macOS の場合、および .NET Core 2.1 より前のバージョンの場合にのみ有効)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-194">(Only valid for Linux/macOS and for versions earlier than .NET Core 2.1.)</span></span>

  **`--os <OPERATING_SYSTEM>`**

  <span data-ttu-id="cd8c4-195">ツールのインストール先のオペレーティング システムを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-195">Specifies the operating system for which the tools are being installed.</span></span> <span data-ttu-id="cd8c4-196">指定できる値は、`osx`、`linux`、`linux-musl`、`freebsd`、`rhel.6` です。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-196">Possible values are: `osx`, `linux`, `linux-musl`, `freebsd`, `rhel.6`.</span></span> <span data-ttu-id="cd8c4-197">(.NET Core 2.1 以降の場合に有効)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-197">(Valid for .NET Core 2.1 and later.)</span></span>

  <span data-ttu-id="cd8c4-198">パラメーターは省略可能です。スクリプトによって検出されたオペレーティング システムをオーバーライドする必要がある場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-198">The parameter is optional and should only be used when it's required to override the operating system that is detected by the script.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="cd8c4-199">このパラメーターは非推奨であり、今後のバージョンのスクリプトでは削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-199">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="cd8c4-200">別の方法として、`-Runtime|--runtime` オプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-200">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="cd8c4-201">SDK 全体ではなく共有ランタイム ビットのみがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-201">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="cd8c4-202">このオプションは、`-Runtime|--runtime dotnet` を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-202">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="cd8c4-203">*dotnet.exe* など、バージョン管理されていないファイルが既に存在する場合は、そのインストールをスキップします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-203">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="cd8c4-204">このインストーラーで使用されている、キャッシュされていないフィードの URL を変更することを許可します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-204">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="cd8c4-205">この値は変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-205">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="cd8c4-206">診断情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-206">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="cd8c4-207">特定のビルド バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-207">Represents a specific build version.</span></span> <span data-ttu-id="cd8c4-208">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-208">The possible values are:</span></span>

  - <span data-ttu-id="cd8c4-209">`latest` - チャネルの最新ビルド (`-Channel` オプションで使用)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-209">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="cd8c4-210">特定のビルド バージョンを表す X.Y.Z 形式の 3 部構成のバージョン。`-Channel` オプションよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-210">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="cd8c4-211">たとえば、`2.0.0-preview2-006120` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-211">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="cd8c4-212">指定しない場合、`-Version` の既定値は `latest` です。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-212">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="cd8c4-213">使用例</span><span class="sxs-lookup"><span data-stu-id="cd8c4-213">Examples</span></span>

- <span data-ttu-id="cd8c4-214">最新の長期サポート (LST) バージョンを既定の場所にインストールします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-214">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="cd8c4-215">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-215">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="cd8c4-216">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-216">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="cd8c4-217">3\.1 チャネルから、最新バージョンを指定した場所にインストールします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-217">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="cd8c4-218">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-218">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="cd8c4-219">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-219">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="cd8c4-220">共有ランタイムの 3.0.0 バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-220">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="cd8c4-221">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-221">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="cd8c4-222">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-222">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="cd8c4-223">スクリプトを入手し、会社のプロキシの背後に 2.1.2 バージョンをインストールします (Windows のみ)。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-223">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="cd8c4-224">スクリプトを入手し、.NET CLI の 1 行コードのサンプルをインストールします。</span><span class="sxs-lookup"><span data-stu-id="cd8c4-224">Obtain script and install .NET CLI one-liner examples:</span></span>

  <span data-ttu-id="cd8c4-225">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-225">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="cd8c4-226">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="cd8c4-226">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="cd8c4-227">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd8c4-227">See also</span></span>

- [<span data-ttu-id="cd8c4-228">.NET のリリース</span><span class="sxs-lookup"><span data-stu-id="cd8c4-228">.NET releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="cd8c4-229">.NET ランタイムと SDK ダウンロード アーカイブ</span><span class="sxs-lookup"><span data-stu-id="cd8c4-229">.NET Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/main/release-notes/download-archive.md)
