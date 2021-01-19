---
title: dotnet clean コマンド
description: dotnet clean コマンドは現在のディレクトリを消去します。
ms.date: 02/14/2020
ms.openlocfilehash: 1023f13c7662abb7dad613128631c7644ca15bb9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189604"
---
# <a name="dotnet-clean"></a><span data-ttu-id="a3f1d-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a3f1d-103">dotnet clean</span></span>

<span data-ttu-id="a3f1d-104">**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="a3f1d-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a3f1d-105">name</span><span class="sxs-lookup"><span data-stu-id="a3f1d-105">Name</span></span>

<span data-ttu-id="a3f1d-106">`dotnet clean` - プロジェクトの出力を消去します。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a3f1d-107">構文</span><span class="sxs-lookup"><span data-stu-id="a3f1d-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--interactive]
    [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]

dotnet clean -h|--help
```

## <a name="description"></a><span data-ttu-id="a3f1d-108">[説明]</span><span class="sxs-lookup"><span data-stu-id="a3f1d-108">Description</span></span>

<span data-ttu-id="a3f1d-109">`dotnet clean` コマンドは、以前のビルドの出力を消去します。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="a3f1d-110">[MSBuild ターゲット](/visualstudio/msbuild/msbuild-targets)として実装されます。そのため、コマンドの実行時にプロジェクトが評価されます。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="a3f1d-111">ビルド中に作成された出力のみが消去されます。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="a3f1d-112">中間 (*obj*) と最終出力 (*bin*) フォルダーの両方が消去されます。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="a3f1d-113">引数</span><span class="sxs-lookup"><span data-stu-id="a3f1d-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="a3f1d-114">クリーンにする MSBuild プロジェクトまたはソリューション。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="a3f1d-115">プロジェクトまたはソリューションのファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* または *sln* のどちらかで終わるファイル拡張子を持つファイルを検索して、そのファイルを使います。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="a3f1d-116">オプション</span><span class="sxs-lookup"><span data-stu-id="a3f1d-116">Options</span></span>

* **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="a3f1d-117">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-117">Defines the build configuration.</span></span> <span data-ttu-id="a3f1d-118">ほとんどのプロジェクトの既定値は `Debug` ですが、プロジェクトでビルド構成設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-118">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span> <span data-ttu-id="a3f1d-119">このオプションは、ビルド時に指定した場合にのみ、消去時にも必要です。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a3f1d-120">ビルド時に指定された[フレームワーク](../../standard/frameworks.md)です。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="a3f1d-121">フレームワークは、[プロジェクト ファイル](../project-sdk/overview.md)で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-121">The framework must be defined in the [project file](../project-sdk/overview.md).</span></span> <span data-ttu-id="a3f1d-122">ビルド時にフレームワークを指定した場合は、消去時にフレームワークを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="a3f1d-123">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="a3f1d-124">コマンドを停止して、ユーザーの入力または操作のために待機させることができます。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="a3f1d-125">たとえば、認証を完了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-125">For example, to complete authentication.</span></span> <span data-ttu-id="a3f1d-126">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="a3f1d-127">著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="a3f1d-128">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="a3f1d-129">クリーンにするビルド成果物を含むディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="a3f1d-130">プロジェクトのビルド時にフレームワークを指定した場合、出力ディレクトリ スイッチと共に `-f|--framework <FRAMEWORK>` スイッチを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="a3f1d-131">指定したランタイムの出力フォルダーをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="a3f1d-132">これは、[自己完結型の展開](../deploying/index.md#publish-self-contained)が作成された場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a3f1d-133">MSBuild の詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-133">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="a3f1d-134">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-134">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a3f1d-135">既定値は、`normal` です。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-135">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="a3f1d-136">例</span><span class="sxs-lookup"><span data-stu-id="a3f1d-136">Examples</span></span>

* <span data-ttu-id="a3f1d-137">プロジェクトの既定のビルドを消去します。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-137">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="a3f1d-138">リリース構成を使用してビルドされたプロジェクトを消去します。</span><span class="sxs-lookup"><span data-stu-id="a3f1d-138">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
