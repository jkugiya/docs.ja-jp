---
title: .NET CLI を使用してアプリを公開する
description: .NET CLI コマンドを使用して .NET アプリケーションを公開する方法について説明します。
author: adegeo
ms.author: adegeo
ms.date: 02/05/2021
dev_langs:
- csharp
- vb
ms.openlocfilehash: 65c9c4929d9ed8ab4005677fbcb0a3745ed14190
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874304"
---
# <a name="publish-net-apps-with-the-net-cli"></a><span data-ttu-id="7250d-103">.NET CLI を使用した .NET アプリの発行</span><span class="sxs-lookup"><span data-stu-id="7250d-103">Publish .NET apps with the .NET CLI</span></span>

<span data-ttu-id="7250d-104">この記事では、コマンド ラインから .NET アプリケーションを公開する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="7250d-104">This article demonstrates how you can publish your .NET application from the command line.</span></span> <span data-ttu-id="7250d-105">.NET には、アプリケーションを公開する方法が 3 つ用意されています。</span><span class="sxs-lookup"><span data-stu-id="7250d-105">.NET provides three ways to publish your applications.</span></span> <span data-ttu-id="7250d-106">フレームワークに依存する展開を使用すると、ローカル環境にインストールされている .NET ランタイムを使用するクロスプラットフォームの .dll ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-106">Framework-dependent deployment produces a cross-platform .dll file that uses the locally installed .NET runtime.</span></span> <span data-ttu-id="7250d-107">フレームワークに依存する実行可能ファイルを使用すると、ローカル環境にインストールされている .NET ランタイムを使用するプラットフォーム固有の実行可能ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-107">Framework-dependent executable produces a platform-specific executable that uses the locally installed .NET runtime.</span></span> <span data-ttu-id="7250d-108">自己完結型の実行可能ファイルを使用すると、プラットフォーム固有の実行可能ファイルが生成されて、.NET ランタイムのローカル コピーが組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7250d-108">Self-contained executable produces a platform-specific executable and includes a local copy of the .NET runtime.</span></span>

<span data-ttu-id="7250d-109">これらの公開モードの概要については、[.NET アプリケーションの展開](index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7250d-109">For an overview of these publishing modes, see [.NET Application Deployment](index.md).</span></span>

<span data-ttu-id="7250d-110">CLI の使用方法について簡単にわかるヘルプをお探しですか。</span><span class="sxs-lookup"><span data-stu-id="7250d-110">Looking for some quick help on using the CLI?</span></span> <span data-ttu-id="7250d-111">次の表では、アプリの公開方法についての例を示します。</span><span class="sxs-lookup"><span data-stu-id="7250d-111">The following table shows some examples of how to publish your app.</span></span> <span data-ttu-id="7250d-112">ターゲット フレームワークは、`-f <TFM>` パラメーターを使用するか、プロジェクト ファイルを編集して、指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7250d-112">You can specify the target framework with the `-f <TFM>` parameter or by editing the project file.</span></span> <span data-ttu-id="7250d-113">詳細については、「[公開の基礎](#publishing-basics)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7250d-113">For more information, see [Publishing basics](#publishing-basics).</span></span>

| <span data-ttu-id="7250d-114">公開モード</span><span class="sxs-lookup"><span data-stu-id="7250d-114">Publish Mode</span></span>                   | <span data-ttu-id="7250d-115">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="7250d-115">SDK Version</span></span> | <span data-ttu-id="7250d-116">command</span><span class="sxs-lookup"><span data-stu-id="7250d-116">Command</span></span>                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| [<span data-ttu-id="7250d-117">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="7250d-117">Framework-dependent deployment</span></span>](#framework-dependent-deployment) | <span data-ttu-id="7250d-118">2.1</span><span class="sxs-lookup"><span data-stu-id="7250d-118">2.1</span></span>         | `dotnet publish -c Release`                                 |
|                                | <span data-ttu-id="7250d-119">3.1</span><span class="sxs-lookup"><span data-stu-id="7250d-119">3.1</span></span>         | `dotnet publish -c Release -p:UseAppHost=false`             |
|                                | <span data-ttu-id="7250d-120">5.0</span><span class="sxs-lookup"><span data-stu-id="7250d-120">5.0</span></span>         | `dotnet publish -c Release -p:UseAppHost=false`             |
| [<span data-ttu-id="7250d-121">フレームワークに依存する実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="7250d-121">Framework-dependent executable</span></span>](#framework-dependent-executable) | <span data-ttu-id="7250d-122">3.1</span><span class="sxs-lookup"><span data-stu-id="7250d-122">3.1</span></span>         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
|                                | <span data-ttu-id="7250d-123">5.0</span><span class="sxs-lookup"><span data-stu-id="7250d-123">5.0</span></span>         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
| [<span data-ttu-id="7250d-124">自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="7250d-124">Self-contained deployment</span></span>](#self-contained-deployment)      | <span data-ttu-id="7250d-125">2.1</span><span class="sxs-lookup"><span data-stu-id="7250d-125">2.1</span></span>         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | <span data-ttu-id="7250d-126">3.1</span><span class="sxs-lookup"><span data-stu-id="7250d-126">3.1</span></span>         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | <span data-ttu-id="7250d-127">5.0</span><span class="sxs-lookup"><span data-stu-id="7250d-127">5.0</span></span>         | `dotnet publish -c Release -r <RID> --self-contained true`  |

<span data-ttu-id="7250d-128">\* **SDK バージョン 3.1** 以降を使用する場合、基本的な `dotnet publish` コマンドを実行するときの既定の公開モードは、フレームワークに依存する実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="7250d-128">\* When using **SDK version 3.1** or higher, framework-dependent executable is the default publishing mode when running the basic `dotnet publish` command.</span></span>

> [!NOTE]
> <span data-ttu-id="7250d-129">`-c Release` パラメーターは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="7250d-129">The `-c Release` parameter isn't required.</span></span> <span data-ttu-id="7250d-130">アプリの **リリース** ビルドを公開することを明示するために提供されています。</span><span class="sxs-lookup"><span data-stu-id="7250d-130">It's provided as a reminder to publish the **Release** build of your app.</span></span>

## <a name="publishing-basics"></a><span data-ttu-id="7250d-131">公開の基礎</span><span class="sxs-lookup"><span data-stu-id="7250d-131">Publishing basics</span></span>

<span data-ttu-id="7250d-132">アプリを公開するときは、プロジェクト ファイルの設定 `<TargetFramework>` で既定のターゲット フレームワークを指定します。</span><span class="sxs-lookup"><span data-stu-id="7250d-132">The `<TargetFramework>` setting of the project file specifies the default target framework when you publish your app.</span></span> <span data-ttu-id="7250d-133">任意の有効な[ターゲット フレームワーク モニカー (TFM)](../../standard/frameworks.md) にターゲット フレームワークを変更できます。</span><span class="sxs-lookup"><span data-stu-id="7250d-133">You can change the target framework to any valid [Target Framework Moniker (TFM)](../../standard/frameworks.md).</span></span> <span data-ttu-id="7250d-134">たとえば、プロジェクトで `<TargetFramework>netcoreapp2.1</TargetFramework>` を使用している場合は、.NET Core 2.1 をターゲットとするバイナリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-134">For example, if your project uses `<TargetFramework>netcoreapp2.1</TargetFramework>`, a binary that targets .NET Core 2.1 is created.</span></span> <span data-ttu-id="7250d-135">この設定で指定されている TFM が、[`dotnet publish`](../tools/dotnet-publish.md) コマンドで使用される既定のターゲットになります。</span><span class="sxs-lookup"><span data-stu-id="7250d-135">The TFM specified in this setting is the default target used by the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="7250d-136">複数のフレームワークをターゲットにしたい場合は、セミコロンで区切ることにより、`<TargetFrameworks>` の設定で複数の TFM 値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7250d-136">If you want to target more than one framework, you can set the `<TargetFrameworks>` setting to multiple TFM values, separated by a semicolon.</span></span> <span data-ttu-id="7250d-137">アプリをビルドするときは、ターゲット フレームワークごとにビルドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-137">When you build your app, a build is produced for each target framework.</span></span> <span data-ttu-id="7250d-138">ただし、アプリを公開するときは、`dotnet publish -f <TFM>` コマンドでターゲット フレームワークを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-138">However, when you publish your app, you must specify the target framework with the `dotnet publish -f <TFM>` command.</span></span>

<span data-ttu-id="7250d-139">他の値を設定しない限り、[`dotnet publish`](../tools/dotnet-publish.md) コマンドの出力ディレクトリは `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` です。</span><span class="sxs-lookup"><span data-stu-id="7250d-139">Unless otherwise set, the output directory of the [`dotnet publish`](../tools/dotnet-publish.md) command is `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`.</span></span> <span data-ttu-id="7250d-140">`-c` パラメーターで変更しない限り、**BUILD-CONFIGURATION** の既定のモードは **Debug** です。</span><span class="sxs-lookup"><span data-stu-id="7250d-140">The default **BUILD-CONFIGURATION** mode is **Debug** unless changed with the `-c` parameter.</span></span> <span data-ttu-id="7250d-141">たとえば、`dotnet publish -c Release -f netcoreapp2.1` と指定すると、`./bin/Release/netcoreapp2.1/publish/` に公開されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-141">For example, `dotnet publish -c Release -f netcoreapp2.1` publishes to `./bin/Release/netcoreapp2.1/publish/`.</span></span>

<span data-ttu-id="7250d-142">.NET Core SDK 3.1 以降を使用している場合、既定の公開モードはフレームワークに依存する "_実行可能ファイル_" です。</span><span class="sxs-lookup"><span data-stu-id="7250d-142">If you use .NET Core SDK 3.1 or later, the default publish mode is framework-dependent _executable_.</span></span>

<span data-ttu-id="7250d-143">.NET Core SDK 2.1 を使用している場合、既定の公開モードはフレームワークに依存する "_展開_" です。</span><span class="sxs-lookup"><span data-stu-id="7250d-143">If you use .NET Core SDK 2.1, the default publish mode is framework-dependent _deployment_.</span></span>

### <a name="native-dependencies"></a><span data-ttu-id="7250d-144">ネイティブの依存関係</span><span class="sxs-lookup"><span data-stu-id="7250d-144">Native dependencies</span></span>

<span data-ttu-id="7250d-145">アプリにネイティブの依存関係がある場合、別のオペレーティング システムではアプリが実行されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-145">If your app has native dependencies, it may not run on a different operating system.</span></span> <span data-ttu-id="7250d-146">たとえば、ネイティブの Windows API を使用しているアプリは、macOS または Linux では実行されません。</span><span class="sxs-lookup"><span data-stu-id="7250d-146">For example, if your app uses the native Windows API, it won't run on macOS or Linux.</span></span> <span data-ttu-id="7250d-147">プラットフォーム固有のコードを提供し、プラットフォームごとに実行可能ファイルをコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-147">You would need to provide platform-specific code and compile an executable for each platform.</span></span>

<span data-ttu-id="7250d-148">また、参照しているライブラリにネイティブの依存関係がある場合、すべてのプラットフォームではアプリを実行できない可能性があることも考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7250d-148">Consider also, if a library you referenced has a native dependency, your app may not run on every platform.</span></span> <span data-ttu-id="7250d-149">ただし、参照している NuGet パッケージには、必要なネイティブの依存関係を処理するためにプラットフォーム固有のバージョンが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-149">However, it's possible a NuGet package you're referencing has included platform-specific versions to handle the required native dependencies for you.</span></span>

<span data-ttu-id="7250d-150">ネイティブの依存関係があるアプリを配布するときは、`dotnet publish -r <RID>` スイッチを使用して、公開対象のターゲット プラットフォームを指定することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-150">When distributing an app with native dependencies, you may need to use the `dotnet publish -r <RID>` switch to specify the target platform you want to publish for.</span></span> <span data-ttu-id="7250d-151">ランタイム識別子の一覧については、[ランタイム識別子 (RID) のカタログ](../rid-catalog.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7250d-151">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

<span data-ttu-id="7250d-152">プラットフォーム固有のバイナリの詳細については、「[フレームワークに依存する実行可能ファイル](#framework-dependent-executable)」および「[自己完結型の展開](#self-contained-deployment)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7250d-152">More information about platform-specific binaries is covered in the [Framework-dependent executable](#framework-dependent-executable) and [Self-contained deployment](#self-contained-deployment) sections.</span></span>

## <a name="sample-app"></a><span data-ttu-id="7250d-153">サンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="7250d-153">Sample app</span></span>

<span data-ttu-id="7250d-154">次のアプリを使用して、公開コマンドを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7250d-154">You can use the following app to explore the publishing commands.</span></span> <span data-ttu-id="7250d-155">ターミナルで次のコマンドを実行すると、アプリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-155">The app is created by running the following commands in your terminal:</span></span>

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

<span data-ttu-id="7250d-156">コンソール テンプレートによって生成される `Program.cs` または `Program.vb` ファイルを、次のように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-156">The `Program.cs` or `Program.vb` file that is generated by the console template needs to be changed to the following:</span></span>

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

<span data-ttu-id="7250d-157">アプリを実行すると ([`dotnet run`](../tools/dotnet-run.md))、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-157">When you run the app ([`dotnet run`](../tools/dotnet-run.md)), the following output is displayed:</span></span>

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a><span data-ttu-id="7250d-158">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="7250d-158">Framework-dependent deployment</span></span>

<span data-ttu-id="7250d-159">.NET Core 2.1 SDK の CLI の場合、フレームワークに依存する展開 (FDD) が、基本的な `dotnet publish` コマンドの既定のモードです。</span><span class="sxs-lookup"><span data-stu-id="7250d-159">For the .NET Core 2.1 SDK CLI, framework-dependent deployment (FDD) is the default mode for the basic `dotnet publish` command.</span></span> <span data-ttu-id="7250d-160">それより新しい SDK では、[フレームワークに依存する実行可能ファイル](#framework-dependent-executable)が既定値です。</span><span class="sxs-lookup"><span data-stu-id="7250d-160">In newer SDKs, [Framework-dependent executable](#framework-dependent-executable) is the default.</span></span>

<span data-ttu-id="7250d-161">FDD としてアプリを公開すると、`./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` フォルダーに`<PROJECT-NAME>.dll` ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-161">When you publish your app as an FDD, a `<PROJECT-NAME>.dll` file is created in the `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` folder.</span></span> <span data-ttu-id="7250d-162">アプリを実行するには、出力フォルダーに移動して、`dotnet <PROJECT-NAME>.dll` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7250d-162">To run your app, navigate to the output folder and use the `dotnet <PROJECT-NAME>.dll` command.</span></span>

<span data-ttu-id="7250d-163">アプリは、特定のバージョンの .NET をターゲットにするように構成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-163">Your app is configured to target a specific version of .NET.</span></span> <span data-ttu-id="7250d-164">アプリが実行されるすべてのコンピューターには、そのターゲットの .NET ランタイムが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-164">That targeted .NET runtime is required to be on any machine where your app runs.</span></span> <span data-ttu-id="7250d-165">たとえば、アプリのターゲットが .NET Core 3.1 である場合、アプリを実行するコンピューターには、.NET Core 3.1 ランタイムがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-165">For example, if your app targets .NET Core 3.1, any machine that your app runs on must have the .NET Core 3.1 runtime installed.</span></span> <span data-ttu-id="7250d-166">「[公開の基礎](#publishing-basics)」セクションで説明したように、プロジェクト ファイルを編集することで、既定のターゲット フレームワークを変更したり、複数のフレームワークをターゲットにしたりできます。</span><span class="sxs-lookup"><span data-stu-id="7250d-166">As stated in the [Publishing basics](#publishing-basics) section, you can edit your project file to change the default target framework or to target more than one framework.</span></span>

<span data-ttu-id="7250d-167">FDD を公開すると、アプリが実行されるシステムで使用できる最新の .NET セキュリティ更新プログラムまで自動的にロールフォワードするアプリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-167">Publishing an FDD creates an app that automatically rolls-forward to the latest .NET security patch available on the system that runs the app.</span></span> <span data-ttu-id="7250d-168">コンパイル時のバージョンのバインドの詳細については、「[使用する .NET のバージョンを選択する](../versions/selection.md#framework-dependent-apps-roll-forward)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7250d-168">For more information on version binding at compile time, see [Select the .NET version to use](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

| <span data-ttu-id="7250d-169">公開モード</span><span class="sxs-lookup"><span data-stu-id="7250d-169">Publish Mode</span></span>                   | <span data-ttu-id="7250d-170">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="7250d-170">SDK Version</span></span> | <span data-ttu-id="7250d-171">コマンド</span><span class="sxs-lookup"><span data-stu-id="7250d-171">Command</span></span>                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| <span data-ttu-id="7250d-172">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="7250d-172">Framework-dependent deployment</span></span> | <span data-ttu-id="7250d-173">2.1</span><span class="sxs-lookup"><span data-stu-id="7250d-173">2.1</span></span>         | `dotnet publish -c Release`                                 |
|                                | <span data-ttu-id="7250d-174">3.1</span><span class="sxs-lookup"><span data-stu-id="7250d-174">3.1</span></span>         | `dotnet publish -c Release -p:UseAppHost=false`             |
|                                | <span data-ttu-id="7250d-175">5.0</span><span class="sxs-lookup"><span data-stu-id="7250d-175">5.0</span></span>         | `dotnet publish -c Release -p:UseAppHost=false`             |

## <a name="framework-dependent-executable"></a><span data-ttu-id="7250d-176">フレームワークに依存する実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="7250d-176">Framework-dependent executable</span></span>

<span data-ttu-id="7250d-177">.NET 5 (および .NET Core 3.1) SDK の CLI の場合は、フレームワークに依存する実行可能ファイル (FDE) が、基本的な `dotnet publish` コマンドの既定のモードです。</span><span class="sxs-lookup"><span data-stu-id="7250d-177">For the .NET 5 (and .NET Core 3.1) SDK CLI, framework-dependent executable (FDE) is the default mode for the basic `dotnet publish` command.</span></span> <span data-ttu-id="7250d-178">現在のオペレーティング システムをターゲットにする限り、他のパラメーターを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7250d-178">You don't need to specify any other parameters, as long as you want to target the current operating system.</span></span>

<span data-ttu-id="7250d-179">このモードでは、クロスプラットフォーム アプリをホストするために、プラットフォームに固有の実行可能なホストが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-179">In this mode, a platform-specific executable host is created to host your cross-platform app.</span></span> <span data-ttu-id="7250d-180">FDD では `dotnet` コマンドの形式でホストを要求するので、このモードは FDD と似ています。</span><span class="sxs-lookup"><span data-stu-id="7250d-180">This mode is similar to FDD, as FDD requires a host in the form of the `dotnet` command.</span></span> <span data-ttu-id="7250d-181">ホストの実行可能ファイル名はプラットフォームごとに異なり、`<PROJECT-FILE>.exe` のような名前になります。</span><span class="sxs-lookup"><span data-stu-id="7250d-181">The host executable filename varies per platform and is named something similar to `<PROJECT-FILE>.exe`.</span></span> <span data-ttu-id="7250d-182">この実行可能ファイルは、`dotnet <PROJECT-FILE>.dll` を呼び出す (アプリの実行手段として引き続き使用可能) 代わりに、直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="7250d-182">You can run this executable directly instead of calling `dotnet <PROJECT-FILE>.dll`, which is still an acceptable way to run the app.</span></span>

<span data-ttu-id="7250d-183">アプリは、特定のバージョンの .NET をターゲットにするように構成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-183">Your app is configured to target a specific version of .NET.</span></span> <span data-ttu-id="7250d-184">アプリが実行されるすべてのコンピューターには、そのターゲットの .NET ランタイムが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-184">That targeted .NET runtime is required to be on any machine where your app runs.</span></span> <span data-ttu-id="7250d-185">たとえば、アプリのターゲットが .NET Core 3.1 である場合、アプリを実行するコンピューターには、.NET Core 3.1 ランタイムがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-185">For example, if your app targets .NET Core 3.1, any machine that your app runs on must have the .NET Core 3.1 runtime installed.</span></span> <span data-ttu-id="7250d-186">「[公開の基礎](#publishing-basics)」セクションで説明したように、プロジェクト ファイルを編集することで、既定のターゲット フレームワークを変更したり、複数のフレームワークをターゲットにしたりできます。</span><span class="sxs-lookup"><span data-stu-id="7250d-186">As stated in the [Publishing basics](#publishing-basics) section, you can edit your project file to change the default target framework or to target more than one framework.</span></span>

<span data-ttu-id="7250d-187">FDE を公開すると、アプリが実行されるシステムで使用できる最新の .NET セキュリティ更新プログラムまで自動的にロールフォワードするアプリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-187">Publishing an FDE creates an app that automatically rolls-forward to the latest .NET security patch available on the system that runs the app.</span></span> <span data-ttu-id="7250d-188">コンパイル時のバージョンのバインドの詳細については、「[使用する .NET のバージョンを選択する](../versions/selection.md#framework-dependent-apps-roll-forward)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7250d-188">For more information on version binding at compile time, see [Select the .NET version to use](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

<span data-ttu-id="7250d-189">.NET 2.1 の場合は、`dotnet publish` コマンドで次のスイッチを使用して、FDE を公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-189">For .NET 2.1, you must use the following switches with the `dotnet publish` command to publish an FDE:</span></span>

- <span data-ttu-id="7250d-190">`-r <RID>` このスイッチでは、識別子 (RID) を使用してターゲット プラットフォームを指定します。</span><span class="sxs-lookup"><span data-stu-id="7250d-190">`-r <RID>` This switch uses an identifier (RID) to specify the target platform.</span></span> <span data-ttu-id="7250d-191">ランタイム識別子の一覧については、[ランタイム識別子 (RID) のカタログ](../rid-catalog.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7250d-191">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

- <span data-ttu-id="7250d-192">`--self-contained false` このスイッチは、自己完結型の展開 (SCD) を作成する `-r` スイッチの既定の動作を無効にします。</span><span class="sxs-lookup"><span data-stu-id="7250d-192">`--self-contained false` This switch disables the default behavior of the `-r` switch, which is to create a self-contained deployment (SCD).</span></span> <span data-ttu-id="7250d-193">このスイッチは、FDE を作成します。</span><span class="sxs-lookup"><span data-stu-id="7250d-193">This switch creates an FDE.</span></span>

| <span data-ttu-id="7250d-194">公開モード</span><span class="sxs-lookup"><span data-stu-id="7250d-194">Publish Mode</span></span>                   | <span data-ttu-id="7250d-195">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="7250d-195">SDK Version</span></span> | <span data-ttu-id="7250d-196">コマンド</span><span class="sxs-lookup"><span data-stu-id="7250d-196">Command</span></span>                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| <span data-ttu-id="7250d-197">フレームワークに依存する実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="7250d-197">Framework-dependent executable</span></span> | <span data-ttu-id="7250d-198">3.1</span><span class="sxs-lookup"><span data-stu-id="7250d-198">3.1</span></span>         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
|                                | <span data-ttu-id="7250d-199">5.0</span><span class="sxs-lookup"><span data-stu-id="7250d-199">5.0</span></span>         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |

<span data-ttu-id="7250d-200">`-r` スイッチを使用すると常に、出力フォルダーのパスが `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/` に変わります</span><span class="sxs-lookup"><span data-stu-id="7250d-200">Whenever you use the `-r` switch, the output folder path changes to: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`</span></span>

<span data-ttu-id="7250d-201">[アプリの例](#sample-app)を使用する場合は、`dotnet publish -f net5.0 -r win10-x64 --self-contained false` を実行します。</span><span class="sxs-lookup"><span data-stu-id="7250d-201">If you use the [example app](#sample-app), run `dotnet publish -f net5.0 -r win10-x64 --self-contained false`.</span></span> <span data-ttu-id="7250d-202">このコマンドでは、実行可能ファイル `./bin/Debug/net5.0/win10-x64/publish/apptest1.exe` が作成されます</span><span class="sxs-lookup"><span data-stu-id="7250d-202">This command creates the following executable: `./bin/Debug/net5.0/win10-x64/publish/apptest1.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="7250d-203">**グローバリゼーション インバリアント モード** を有効にすることで、展開の合計サイズを小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="7250d-203">You can reduce the total size of your deployment by enabling **globalization invariant mode**.</span></span> <span data-ttu-id="7250d-204">このモードは、全世界を意識するものではなく、[インバリアント カルチャ](xref:System.Globalization.CultureInfo.InvariantCulture)の書式設定規則、大文字/小文字の区別規則、文字列比較、並べ替え順序を使用できるアプリケーションにとって便利です。</span><span class="sxs-lookup"><span data-stu-id="7250d-204">This mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span> <span data-ttu-id="7250d-205">**グローバリゼーション インバリアント モード** の詳細と、それを有効にする方法については、[.NET のグローバリゼーション インバリアント モード](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7250d-205">For more information about **globalization invariant mode** and how to enable it, see [.NET Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).</span></span>

## <a name="self-contained-deployment"></a><span data-ttu-id="7250d-206">自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="7250d-206">Self-contained deployment</span></span>

<span data-ttu-id="7250d-207">自己完結型の展開 (SCD) を公開すると、.NET SDK によってプラットフォーム固有の実行可能ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-207">When you publish a self-contained deployment (SCD), the .NET SDK creates a platform-specific executable.</span></span> <span data-ttu-id="7250d-208">SCD の公開には、アプリの実行に必要なすべての .NET ファイルが含まれますが、[.NET のネイティブの依存関係](https://github.com/dotnet/core/blob/main/Documentation/prereqs.md)は含まれません。</span><span class="sxs-lookup"><span data-stu-id="7250d-208">Publishing an SCD includes all required .NET files to run your app but it doesn't include the [native dependencies of .NET](https://github.com/dotnet/core/blob/main/Documentation/prereqs.md).</span></span> <span data-ttu-id="7250d-209">これらの依存関係は、アプリを実行する前に、システムに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-209">These dependencies must be present on the system before the app runs.</span></span>

<span data-ttu-id="7250d-210">SCD の公開で作成されるアプリでは、使用可能な最新の .NET セキュリティ更新プログラムへのロールフォワードは行われません。</span><span class="sxs-lookup"><span data-stu-id="7250d-210">Publishing an SCD creates an app that doesn't roll forward to the latest available .NET security patch.</span></span> <span data-ttu-id="7250d-211">コンパイル時のバージョンのバインドの詳細については、「[使用する .NET のバージョンを選択する](../versions/selection.md#self-contained-deployments-include-the-selected-runtime)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7250d-211">For more information on version binding at compile time, see [Select the .NET version to use](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).</span></span>

<span data-ttu-id="7250d-212">`dotnet publish` コマンドで次のスイッチを使用して、SCD を公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7250d-212">You must use the following switches with the `dotnet publish` command to publish an SCD:</span></span>

- <span data-ttu-id="7250d-213">`-r <RID>` このスイッチでは、識別子 (RID) を使用してターゲット プラットフォームを指定します。</span><span class="sxs-lookup"><span data-stu-id="7250d-213">`-r <RID>` This switch uses an identifier (RID) to specify the target platform.</span></span> <span data-ttu-id="7250d-214">ランタイム識別子の一覧については、[ランタイム識別子 (RID) のカタログ](../rid-catalog.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7250d-214">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

- <span data-ttu-id="7250d-215">`--self-contained true` このスイッチでは、SCD として実行可能ファイルを作成するよう .NET Core SDK に指示されます。</span><span class="sxs-lookup"><span data-stu-id="7250d-215">`--self-contained true` This switch tells the .NET Core SDK to create an executable as an SCD.</span></span>

| <span data-ttu-id="7250d-216">公開モード</span><span class="sxs-lookup"><span data-stu-id="7250d-216">Publish Mode</span></span>                   | <span data-ttu-id="7250d-217">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="7250d-217">SDK Version</span></span> | <span data-ttu-id="7250d-218">コマンド</span><span class="sxs-lookup"><span data-stu-id="7250d-218">Command</span></span>                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| <span data-ttu-id="7250d-219">自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="7250d-219">Self-contained deployment</span></span>      | <span data-ttu-id="7250d-220">2.1</span><span class="sxs-lookup"><span data-stu-id="7250d-220">2.1</span></span>         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | <span data-ttu-id="7250d-221">3.1</span><span class="sxs-lookup"><span data-stu-id="7250d-221">3.1</span></span>         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | <span data-ttu-id="7250d-222">5.0</span><span class="sxs-lookup"><span data-stu-id="7250d-222">5.0</span></span>         | `dotnet publish -c Release -r <RID> --self-contained true`  |

> [!NOTE]
> <span data-ttu-id="7250d-223">**グローバリゼーション インバリアント モード** を有効にすることで、展開の合計サイズを小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="7250d-223">You can reduce the total size of your deployment by enabling **globalization invariant mode**.</span></span> <span data-ttu-id="7250d-224">このモードは、全世界を意識するものではなく、[インバリアント カルチャ](xref:System.Globalization.CultureInfo.InvariantCulture)の書式設定規則、大文字/小文字の区別規則、文字列比較、並べ替え順序を使用できるアプリケーションにとって便利です。</span><span class="sxs-lookup"><span data-stu-id="7250d-224">This mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span> <span data-ttu-id="7250d-225">**グローバリゼーション インバリアント モード** の詳細と、それを有効にする方法については、「[.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md)」(.NET Core のグローバリゼーション インバリアント モード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7250d-225">For more information about **globalization invariant mode** and how to enable it, see [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7250d-226">関連項目</span><span class="sxs-lookup"><span data-stu-id="7250d-226">See also</span></span>

- [<span data-ttu-id="7250d-227">.NET アプリケーションの展開の概要</span><span class="sxs-lookup"><span data-stu-id="7250d-227">.NET Application Deployment Overview</span></span>](index.md)
- [<span data-ttu-id="7250d-228">.NET ランタイム識別子 (RID) カタログ</span><span class="sxs-lookup"><span data-stu-id="7250d-228">.NET Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
