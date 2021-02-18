---
title: "NETSDK1045: 現在の .NET SDK では、ターゲットとして '新しいバージョン' がサポートされていません。"
description: .NET SDK エラー NETSDK1045 について説明します。これは、要求されたバージョンの .NET SDK をビルド ツールで見つけられない場合に発生します。
ms.topic: error-reference
ms.date: 02/12/2021
f1_keywords:
- NETSDK1045
ms.openlocfilehash: 900402ae01f945b1096170ea4fc79d00ea789b62
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488206"
---
# <a name="netsdk1045-the-current-net-sdk-does-not-support-newer-version-as-a-target"></a><span data-ttu-id="38bbe-103">NETSDK1045: 現在の .NET SDK では、ターゲットとして '新しいバージョン' がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="38bbe-103">NETSDK1045: The current .NET SDK does not support 'newer version' as a target.</span></span>

<span data-ttu-id="38bbe-104">**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="38bbe-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="38bbe-105">このエラーは、プロジェクトのビルドに必要な .NET SDK のバージョンをビルド ツールで見つけられない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="38bbe-105">This error occurs when the build tools can't find the version of the .NET SDK that's needed to build a project.</span></span> <span data-ttu-id="38bbe-106">これは通常、.NET Core SDK のインストールまたは構成の問題が原因です。</span><span class="sxs-lookup"><span data-stu-id="38bbe-106">This is typically due to a .NET Core SDK installation or configuration issue.</span></span> <span data-ttu-id="38bbe-107">完全なエラー メッセージは、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="38bbe-107">The full error message is similar to the following example:</span></span>

> <span data-ttu-id="38bbe-108">NETSDK1045: 現在の .NET SDK では、ターゲットとして '新しいバージョン' がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="38bbe-108">NETSDK1045: The current .NET SDK does not support 'newer version' as a target.</span></span> <span data-ttu-id="38bbe-109">'古いバージョン' 以下をターゲットにするか、'新しいバージョン' をサポートする .NET SDK バージョンを使用してください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-109">Either target 'older version' or lower, or use a .NET SDK version that supports 'newer version'.</span></span>

<span data-ttu-id="38bbe-110">次のセクションでは、このエラーの考えられる原因についていくつか説明します。</span><span class="sxs-lookup"><span data-stu-id="38bbe-110">The following sections describe some of the possible reasons for this error.</span></span> <span data-ttu-id="38bbe-111">それぞれを調べ、どれが自分に該当するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="38bbe-111">Check each one and see which one applies to you.</span></span> <span data-ttu-id="38bbe-112">環境または構成ファイルに変更を加える際には、場合によってはコマンド ウィンドウを再起動するか、Visual Studio を再起動するか、コンピューターを再起動して変更を有効にする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-112">Keep in mind that when making changes to the environment or the configuration files, you might have to restart command windows, restart Visual Studio, or reboot your machine, for your changes to take effect.</span></span>

## <a name="net-sdk-version"></a><span data-ttu-id="38bbe-113">.NET SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="38bbe-113">.NET SDK version</span></span>

<span data-ttu-id="38bbe-114">プロジェクト ファイル (.csproj、.vbproj、または .fsproj) を開き、ターゲット フレームワークを確認します。</span><span class="sxs-lookup"><span data-stu-id="38bbe-114">Open the project file (.csproj, .vbproj, or .fsproj) and check the target framework.</span></span> <span data-ttu-id="38bbe-115">これは、アプリで使用しようとしているフレームワークのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="38bbe-115">This is the version of the framework that your app is trying to use.</span></span>

```xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

<span data-ttu-id="38bbe-116">一覧表示されている .NET のバージョンがコンピューターにインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-116">Make sure that the version of .NET listed is installed on the machine.</span></span> <span data-ttu-id="38bbe-117">次のコマンドを使用して、インストールされているバージョンを一覧表示できます (開発者コマンド プロンプトを開いて、このコマンドを実行する)。</span><span class="sxs-lookup"><span data-stu-id="38bbe-117">You can list the installed versions by using the following command (open a Developer Command Prompt and run this command):</span></span>

```dotnetcli
dotnet --list-sdks
```

### <a name="x86-or-x64-architecture"></a><span data-ttu-id="38bbe-118">x86 または x64 のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="38bbe-118">x86 or x64 architecture</span></span>

<span data-ttu-id="38bbe-119">.NET SDK の各バージョンは、x86 と x64 の両方のアーキテクチャで使用できます。</span><span class="sxs-lookup"><span data-stu-id="38bbe-119">Each version of the .NET SDK is available in both x86 and x64 architecture.</span></span> <span data-ttu-id="38bbe-120">プロジェクトで間違ったアーキテクチャ用の .NET SDK を検索しようしているか、プロジェクトに必要なアーキテクチャ用の .NET SDK がインストールされていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38bbe-120">The project might be trying to find the .NET SDK for the wrong architecture, or the .NET SDK for the architecture your project needs might not be installed.</span></span> <span data-ttu-id="38bbe-121">インストール フォルダーに必要なアーキテクチャがあるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-121">Check the installation folders for the architecture you need.</span></span> <span data-ttu-id="38bbe-122">たとえば、Windows では、.NET SDK の x86 バージョンが *C:\Program Files (x86)\dotnet* にインストールされ、x64 バージョンが *C:\Program Files\dotnet* にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="38bbe-122">For example, on Windows, the x86 version of the .NET SDK is installed in *C:\Program Files (x86)\dotnet* and the x64 version is installed in *C:\Program Files\dotnet*.</span></span> <span data-ttu-id="38bbe-123">「[.NET が既にインストールされていることを確認する方法](../../install/how-to-detect-installed-versions.md)」を参照し、ご利用のオペレーティング システムを選択して、コンピューターにインストールされているものを検出する方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-123">See [How to check that .NET is already installed](../../install/how-to-detect-installed-versions.md) and choose your operating system to find out how to detect what's installed on your machine.</span></span>

<span data-ttu-id="38bbe-124">必要なバージョンがインストールされていない場合は、[こちら](https://dotnet.microsoft.com/download/dotnet-core)からダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-124">If the version you need is not installed, download it from [here](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

## <a name="preview-not-enabled"></a><span data-ttu-id="38bbe-125">プレビューが有効になっていない</span><span class="sxs-lookup"><span data-stu-id="38bbe-125">Preview not enabled</span></span>

<span data-ttu-id="38bbe-126">要求された .NET SDK バージョンのプレビューがインストールされている場合は、Visual Studio でプレビューを有効にするオプションも設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38bbe-126">If you have a preview installed of the requested .NET SDK version, you also need to set the option to enable previews in Visual Studio.</span></span> <span data-ttu-id="38bbe-127">**[ツール]**  >  **[オプション]**  >  **[環境]**  >  **[プレビュー機能]** の順に移動し、 **[プレビューの .NET Core SDK を使用]** がオンになっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-127">Go to **Tools** > **Options** > **Environment** > **Preview Features**, and make sure that **Use previews of the .NET Core SDK** is checked.</span></span>

## <a name="visual-studio-version"></a><span data-ttu-id="38bbe-128">Visual Studio のバージョン</span><span class="sxs-lookup"><span data-stu-id="38bbe-128">Visual Studio version</span></span>

<span data-ttu-id="38bbe-129">たとえば、.NET Core 3.0 以降では Visual Studio 2019 が必要です。</span><span class="sxs-lookup"><span data-stu-id="38bbe-129">For example, .NET Core 3.0 and later require Visual Studio 2019.</span></span> <span data-ttu-id="38bbe-130">[Visual Studio 2019 バージョン 16.3](https://visualstudio.microsoft.com/downloads) 以降にアップグレードして、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="38bbe-130">Upgrade to [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads) or later to build your project.</span></span>

## <a name="path-environment-variable"></a><span data-ttu-id="38bbe-131">PATH 環境変数</span><span class="sxs-lookup"><span data-stu-id="38bbe-131">PATH environment variable</span></span>

<span data-ttu-id="38bbe-132">ビルド ツールでは、PATH 環境変数を使用して、適切なバージョンの .NET ビルド ツールを検索します。</span><span class="sxs-lookup"><span data-stu-id="38bbe-132">The build tools use the PATH environment variable to find the right version of the .NET build tools.</span></span> <span data-ttu-id="38bbe-133">PATH 環境変数に古いビルド ツールへの直接パスが含まれている場合、このエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="38bbe-133">If the PATH environment variable contains direct paths to older build tools, this error message could appear.</span></span> <span data-ttu-id="38bbe-134">PATH 環境変数内の .NET ツールへの唯一のパスが、最上位の *dotnet* フォルダー (たとえば、*C:\Program Files\dotnet*) へのものであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-134">Make sure the only path to the .NET tools in the PATH environment variable is to the top-level *dotnet* folder, for example, *C:\Program Files\dotnet*.</span></span> <span data-ttu-id="38bbe-135">不適切な PATH の例としては、*C:\Program Files\dotnet\2.1.0\sdks* のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="38bbe-135">An example of an incorrect PATH would be something like *C:\Program Files\dotnet\2.1.0\sdks*.</span></span>

## <a name="msbuildsdkpath-environment-variable"></a><span data-ttu-id="38bbe-136">MSBuildSDKPath 環境変数</span><span class="sxs-lookup"><span data-stu-id="38bbe-136">MSBuildSDKPath environment variable</span></span>

<span data-ttu-id="38bbe-137">MSBuildSDKPath 環境変数を確認します。</span><span class="sxs-lookup"><span data-stu-id="38bbe-137">Check the MSBuildSDKPath environment variable.</span></span> <span data-ttu-id="38bbe-138">この省略可能な環境変数は MSBuild によって認識され、これが設定されている場合、既定値はオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="38bbe-138">This optional environment variable is recognized by MSBuild and if set, overrides the default value.</span></span> <span data-ttu-id="38bbe-139">これは、.NET SDK の特定の古いバージョンに設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38bbe-139">It might be set to a specific older version of the .NET SDK.</span></span> <span data-ttu-id="38bbe-140">設定されている場合は、削除してプロジェクトをリビルドしてみてください。</span><span class="sxs-lookup"><span data-stu-id="38bbe-140">If it's set, try deleting it and rebuilding your project.</span></span>

## <a name="globaljson-file"></a><span data-ttu-id="38bbe-141">global.json file</span><span class="sxs-lookup"><span data-stu-id="38bbe-141">global.json file</span></span>

<span data-ttu-id="38bbe-142">フォルダー構造内の任意の場所に存在する可能性があるため、プロジェクトのルート フォルダーに *global.json* ファイルがあるかどうかを確認し、ボリュームのルートまでディレクトリ チェーンを上にたどっていきます。</span><span class="sxs-lookup"><span data-stu-id="38bbe-142">Check for a *global.json* file in the root folder in your project and up the directory chain to the root of the volume, since it can be anywhere in the folder structure.</span></span> <span data-ttu-id="38bbe-143">SDK のバージョンが含まれている場合は、`sdk` ノードとそのすべての子を削除するか、必要な新しい .NET Core バージョンに更新します。</span><span class="sxs-lookup"><span data-stu-id="38bbe-143">If it contains an SDK version, delete the `sdk` node and all its children, or update it to the desired newer .NET Core version.</span></span>

```json
{
  "sdk": {
    "version": "2.1.0"
  }
}
```

<span data-ttu-id="38bbe-144">*global.json* ファイルは必須ではありません。したがって、`sdk` ノード以外のものが含まれていない場合は、ファイル全体を削除できます。</span><span class="sxs-lookup"><span data-stu-id="38bbe-144">The *global.json* file is not required, so if it doesn't contain anything other than the `sdk` node, you can delete the whole file.</span></span>

## <a name="directorybuildprops-file"></a><span data-ttu-id="38bbe-145">Directory.build.props ファイル</span><span class="sxs-lookup"><span data-stu-id="38bbe-145">Directory.build.props file</span></span>

<span data-ttu-id="38bbe-146">*Directory.build.prop* ファイルは、グローバル プロパティを設定できる省略可能な MSBuild ファイルです。</span><span class="sxs-lookup"><span data-stu-id="38bbe-146">The *Directory.build.props* file is an optional MSBuild file that can set global properties.</span></span> <span data-ttu-id="38bbe-147">フォルダー構造内の任意の場所に存在する可能性があるため、ソリューション フォルダーにこれらのファイルがあるかどうかを確認し、ボリュームのルートまでディレクトリ チェーンを上にたどっていきます。</span><span class="sxs-lookup"><span data-stu-id="38bbe-147">Check for these files in the solution folder and up the directory chain to the root of the volume, since they can be anywhere in the folder structure.</span></span> <span data-ttu-id="38bbe-148">`TargetFramework` の要素、または目的の設定をオーバーライドできる `MSBuildSDKPath` の設定を探します。</span><span class="sxs-lookup"><span data-stu-id="38bbe-148">Look for `TargetFramework` elements, or settings of `MSBuildSDKPath` that could override your desired settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="38bbe-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="38bbe-149">See also</span></span>

- [<span data-ttu-id="38bbe-150">現在の .NET SDK は、.NET Core 3.0 のターゲットをサポートしていません – 修正</span><span class="sxs-lookup"><span data-stu-id="38bbe-150">The Current .NET SDK does not support targeting .NET Core 3.0 – Fix</span></span>](https://www.ryadel.com/current-net-sdk-not-support-net-core-3-0-fix/)
