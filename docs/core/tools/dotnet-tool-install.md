---
title: dotnet tool install コマンド
description: dotnet tool install コマンドを実行すると、指定した .NET ツールがお使いのコンピューターにインストールされます。
ms.date: 02/14/2020
ms.openlocfilehash: b04e7fd24edce5d5da67cdd83fbea797118689b4
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206482"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="4a8e6-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="4a8e6-103">dotnet tool install</span></span>

<span data-ttu-id="4a8e6-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="4a8e6-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4a8e6-105">名前</span><span class="sxs-lookup"><span data-stu-id="4a8e6-105">Name</span></span>

<span data-ttu-id="4a8e6-106">`dotnet tool install` - 指定した [.NET ツール](global-tools.md)をお使いのコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-106">`dotnet tool install` - Installs the specified [.NET tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4a8e6-107">構文</span><span class="sxs-lookup"><span data-stu-id="4a8e6-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="4a8e6-108">説明</span><span class="sxs-lookup"><span data-stu-id="4a8e6-108">Description</span></span>

<span data-ttu-id="4a8e6-109">`dotnet tool install` コマンドを実行すると、.NET ツールがお使いのコンピューターにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-109">The `dotnet tool install` command provides a way for you to install .NET tools on your machine.</span></span> <span data-ttu-id="4a8e6-110">コマンドを使用するには、次のいずれかのインストール オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="4a8e6-111">既定の場所にグローバル ツールをインストールするには、`--global` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="4a8e6-112">カスタムの場所にグローバル ツールをインストールするには、`--tool-path` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="4a8e6-113">ローカル ツールをインストールするには、`--global` および `--tool-path` オプションを省略します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="4a8e6-114">**ローカル ツールは .NET Core SDK 3.0 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="4a8e6-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="4a8e6-115">グローバル ツールは、`-g` または `--global` オプションを指定した場合、既定で次のディレクトリにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="4a8e6-116">OS</span><span class="sxs-lookup"><span data-stu-id="4a8e6-116">OS</span></span>          | <span data-ttu-id="4a8e6-117">パス</span><span class="sxs-lookup"><span data-stu-id="4a8e6-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="4a8e6-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="4a8e6-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="4a8e6-119">Windows</span><span class="sxs-lookup"><span data-stu-id="4a8e6-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="4a8e6-120">ローカル ツールは、現在のディレクトリ下にある *.config* ディレクトリ内の *dotnet-tools.json* ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="4a8e6-121">マニフェスト ファイルがまだ存在しない場合は、次のコマンドを実行して作成します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="4a8e6-122">詳細については、「[ローカル ツールのインストール](global-tools.md#install-a-local-tool)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="4a8e6-123">引数</span><span class="sxs-lookup"><span data-stu-id="4a8e6-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="4a8e6-124">インストールする .NET ツールが格納されている NuGet パッケージの名前または ID。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-124">Name/ID of the NuGet package that contains the .NET tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="4a8e6-125">オプション</span><span class="sxs-lookup"><span data-stu-id="4a8e6-125">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="4a8e6-126">インストール時に使用するために追加の NuGet パッケージ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-126">Adds an additional NuGet package source to use during installation.</span></span> <span data-ttu-id="4a8e6-127">フィードは、何らかの順番ではなく、並列でアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-127">Feeds are accessed in parallel, not sequentially in some order of precedence.</span></span> <span data-ttu-id="4a8e6-128">同じパッケージとバージョンが複数のフィードに存在する場合、最も速いフィードが優先されます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-128">If the same package and version is in multiple feeds, the fastest feed wins.</span></span> <span data-ttu-id="4a8e6-129">詳細については、「[NuGet パッケージのインストールのしくみ](/nuget/concepts/package-installation-process)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-129">For more information, see [What happens when a NuGet package is installed?](/nuget/concepts/package-installation-process).</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="4a8e6-130">使用する NuGet 構成 (*nuget.config*) ファイル。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-130">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="4a8e6-131">ツールをインストールする[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-131">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="4a8e6-132">既定では、.NET SDK によって、最適なターゲット フレームワークの選択が試行されます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-132">By default, the .NET SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="4a8e6-133">ユーザー全体のインストールを指定します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-133">Specifies that the installation is user wide.</span></span> <span data-ttu-id="4a8e6-134">`--tool-path` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-134">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="4a8e6-135">`--global` と `--tool-path` の両方を省略すると、ローカル ツールのインストールが指定されます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-135">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4a8e6-136">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-136">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="4a8e6-137">グローバル ツールをインストールする場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-137">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="4a8e6-138">PATH は絶対パスでも相対パスでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-138">PATH can be absolute or relative.</span></span> <span data-ttu-id="4a8e6-139">PATH が存在しない場合、コマンドではパスの作成を試みます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-139">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="4a8e6-140">`--global` と `--tool-path` の両方を省略すると、ローカル ツールのインストールが指定されます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-140">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="4a8e6-141">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4a8e6-142">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="4a8e6-143">インストールするツールのバージョン。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-143">The version of the tool to install.</span></span> <span data-ttu-id="4a8e6-144">既定では、安定した最新バージョンのパッケージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-144">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="4a8e6-145">このオプションを使用して、プレビューまたは古いバージョンのツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-145">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="4a8e6-146">使用例</span><span class="sxs-lookup"><span data-stu-id="4a8e6-146">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="4a8e6-147">既定の場所に [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をグローバル ツールとしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-147">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="4a8e6-148">特定の Windows ディレクトリに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をグローバル ツールとしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="4a8e6-149">特定の Linux/macOS ディレクトリに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をグローバル ツールとしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-149">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="4a8e6-150">バージョン 2.0.0 の [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をグローバル ツールとしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-150">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="4a8e6-151">現在のディレクトリに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をローカル ツールとしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="4a8e6-151">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a8e6-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a8e6-152">See also</span></span>

- [<span data-ttu-id="4a8e6-153">.NET ツール</span><span class="sxs-lookup"><span data-stu-id="4a8e6-153">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="4a8e6-154">チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="4a8e6-154">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="4a8e6-155">チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="4a8e6-155">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
