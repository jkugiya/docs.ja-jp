---
title: ASP.NET MVC アプリを .NET 5 にアップグレードする
description: .NET アップグレード アシスタントを使用して、既存の .NET Framework ASP.NET MVC アプリを .NET 5 にアップグレードします。 .NET アップグレード アシスタントは、.NET Framework から .NET 5 にアプリを移行するときに役立つ CLI ツールです。
author: ardalis
ms.date: 03/08/2021
ms.openlocfilehash: 421d8ce16bc1800451ee39c20c4746ea321fafd0
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604958"
---
# <a name="upgrade-an-aspnet-mvc-app-to-net-5-with-the-net-upgrade-assistant"></a><span data-ttu-id="cd696-104">.NET アップグレード アシスタントを使用して ASP.NET MVC アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="cd696-104">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>

<span data-ttu-id="cd696-105">[.NET アップグレード アシスタント](upgrade-assistant-overview.md)は、.NET Framework ASP.NET MVC アプリを .NET 5 にアップグレードするときに役立つコマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="cd696-105">The [.NET Upgrade Assistant](upgrade-assistant-overview.md) is a command-line tool that can assist with upgrading .NET Framework ASP.NET MVC apps to .NET 5.</span></span> <span data-ttu-id="cd696-106">この記事では、次について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd696-106">This article provides:</span></span>

- <span data-ttu-id="cd696-107">.NET Framework ASP.NET MVC アプリに対してツールを実行する方法のデモ</span><span class="sxs-lookup"><span data-stu-id="cd696-107">A demonstration of how to run the tool against a .NET Framework ASP.NET MVC app</span></span>
- <span data-ttu-id="cd696-108">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="cd696-108">Troubleshooting tips</span></span>

## <a name="upgrade-net-framework-aspnet-mvc-apps"></a><span data-ttu-id="cd696-109">.NET Framework ASP.NET MVC アプリのアップグレード</span><span class="sxs-lookup"><span data-stu-id="cd696-109">Upgrade .NET Framework ASP.NET MVC apps</span></span>

<span data-ttu-id="cd696-110">このセクションでは、.NET Framework 4.6.1 を対象として新しく作成した ASP.NET MVC アプリに対して .NET アップグレード アシスタントを実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="cd696-110">This section demonstrates running the .NET Upgrade Assistant against a newly created ASP.NET MVC app targeting .NET Framework 4.6.1.</span></span> <span data-ttu-id="cd696-111">ツールのインストール方法の詳細については、「[.NET アップグレード アシスタントの概要](upgrade-assistant-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd696-111">For more information on how to install the tool, see [Overview of the .NET Upgrade Assistant](upgrade-assistant-overview.md).</span></span>

### <a name="initial-demo-setup"></a><span data-ttu-id="cd696-112">デモの初期セットアップ</span><span class="sxs-lookup"><span data-stu-id="cd696-112">Initial demo setup</span></span>

<span data-ttu-id="cd696-113">ご自身の .NET Framework アプリに対して .NET アップグレード アシスタントを実行する場合は、このステップを省略できます。</span><span class="sxs-lookup"><span data-stu-id="cd696-113">If you're running the .NET Upgrade Assistant against your own .NET Framework app, you can skip this step.</span></span> <span data-ttu-id="cd696-114">このステップでは、動作を確認するために試してみたい方のために、使用するサンプルの ASP.NET MVC と Web API (.NET Framework) プロジェクトを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cd696-114">If you just want to try it out to see how it works, this step shows you how to set up a sample ASP.NET MVC and Web API (.NET Framework) project to use.</span></span>

<span data-ttu-id="cd696-115">Visual Studio を使用して、.NET Framework を使用した新しい ASP.NET Web アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd696-115">Using Visual Studio, create a new ASP.NET Web Application project using .NET Framework.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/new-project.png" alt-text="Visual Studio の新しい ASP.NET Web アプリケーション プロジェクト":::

<span data-ttu-id="cd696-117">プロジェクトに **AspNetMvcTest** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="cd696-117">Name the project **AspNetMvcTest**.</span></span> <span data-ttu-id="cd696-118">**.NET Framework 4.6.1** を使用するようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="cd696-118">Configure the project to use **.NET Framework 4.6.1**.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/configure-project.png" alt-text="Visual Studio で ASP.NET プロジェクトを構成する":::

<span data-ttu-id="cd696-120">次のダイアログで、**MVC** アプリケーションを選択し、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd696-120">In the next dialog, choose **MVC** application, then select **Create**.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/create-mvc-webapi.png" alt-text="Visual Studio で ASP.NET MVC プロジェクトを作成する":::

<span data-ttu-id="cd696-122">作成したプロジェクトとそのファイル (特にプロジェクト ファイル) を確認します。</span><span class="sxs-lookup"><span data-stu-id="cd696-122">Review the created project and its files, especially its project file(s).</span></span>

### <a name="run-upgrade-assistant"></a><span data-ttu-id="cd696-123">upgrade-assistant の実行</span><span class="sxs-lookup"><span data-stu-id="cd696-123">Run upgrade-assistant</span></span>

<span data-ttu-id="cd696-124">ターミナルを開き、ターゲット プロジェクトまたはソリューションが配置されているフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="cd696-124">Open a terminal and navigate to the folder where the target project or solution is located.</span></span> <span data-ttu-id="cd696-125">`upgrade-assistant` コマンドを実行します。このとき、ターゲットとするプロジェクトの名前を渡します (プロジェクト ファイルのパスが有効である限り、任意の場所からコマンドを実行できます)。</span><span class="sxs-lookup"><span data-stu-id="cd696-125">Run the `upgrade-assistant` command, passing in the name of the project you're targeting (you can run the command from anywhere, as long as the path to the project file is valid).</span></span>

```console
upgrade-assistant .\AspNetMvcTest.csproj
```

<span data-ttu-id="cd696-126">ツールが実行され、行われるステップの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-126">The tool runs and shows you a list of the steps it will do.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/initial-run.png" alt-text=".NET アップグレード アシスタントの初期画面":::

<span data-ttu-id="cd696-128">各ステップが完了すると、ツールにコマンドのセットが表示されます。ユーザーはそれらを使用して、次のステップを適用またはスキップすること、詳細を確認すること、ログを構成すること、プロセスを終了することができます。</span><span class="sxs-lookup"><span data-stu-id="cd696-128">As each step is completed, the tool provides a set of commands allowing the user to apply or skip the next step, see more details, configure logging, or exit the process.</span></span> <span data-ttu-id="cd696-129">あるステップで実行するアクションがないことが検出された場合は、そのステップがツールで自動的にスキップされ、実行するアクションを含む次のステップに進みます。</span><span class="sxs-lookup"><span data-stu-id="cd696-129">If the tool detects that a step will perform no actions, it automatically skips that step and continues to the next step until it reaches one that has actions to perform.</span></span> <span data-ttu-id="cd696-130"><kbd>Enter</kbd> キーを押すと、他に何も選択していない場合は次のステップが実行されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-130">Pressing <kbd>Enter</kbd> will perform the next step if no other selection is made.</span></span>

<span data-ttu-id="cd696-131">この例では、適用ステップを毎回選択しています。</span><span class="sxs-lookup"><span data-stu-id="cd696-131">In this example, the apply step is chosen each time.</span></span> <span data-ttu-id="cd696-132">最初のステップは、プロジェクトのバックアップです。</span><span class="sxs-lookup"><span data-stu-id="cd696-132">The first step is to back up the project.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/backup-project.png" alt-text=".NET アップグレード アシスタントでのプロジェクトのバックアップ":::

<span data-ttu-id="cd696-134">ツールにバックアップのカスタム パスを入力します。または、既定値を使用します。その場合は、`.backup` という拡張子の付いたプロジェクトのバックアップが同じフォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-134">The tool prompts for a custom path for the backup, or to use the default, which will place the project backup in the same folder with a `.backup` extension.</span></span> <span data-ttu-id="cd696-135">ツールで実行される次のステップは、プロジェクト ファイルを SDK スタイルに変換することです。</span><span class="sxs-lookup"><span data-stu-id="cd696-135">The next step the tool does is to convert the project file to SDK style.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/convert-project.png" alt-text=".NET アップグレード アシスタントによるプロジェクトの SDK スタイルへの変換":::

<span data-ttu-id="cd696-137">プロジェクトの形式が更新されたら、次のステップは、プロジェクトの TFM を更新することです。</span><span class="sxs-lookup"><span data-stu-id="cd696-137">Once the project format has been updated, the next step is to update the TFM of the project.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-tfm.png" alt-text=".NET アップグレード アシスタントによる TFM の更新":::

<span data-ttu-id="cd696-139">次に、ツールによってプロジェクトの NuGet パッケージが更新されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-139">Next, the tool updates the project's NuGet packages.</span></span> <span data-ttu-id="cd696-140">複数のパッケージに更新が必要です。さらに、新しいアナライザー パッケージが追加されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-140">Several packages need updates, and a new analyzer package is added.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-nuget-packages.png" alt-text=".NET アップグレード アシスタントによる NuGet パッケージの更新":::

<span data-ttu-id="cd696-142">パッケージが更新されたら、次のステップは、テンプレート ファイル (存在する場合) を追加することです。</span><span class="sxs-lookup"><span data-stu-id="cd696-142">Once the packages are updated, the next step is to add template files, if any.</span></span> <span data-ttu-id="cd696-143">必要な 4 つのテンプレート項目がツールに表示され、そして追加されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-143">The tool notes there are four expected template items that must be added, and then adds them.</span></span> <span data-ttu-id="cd696-144">次のファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd696-144">These include the following files:</span></span>

- `Program.cs`
- `Startup.cs`
- `appsettings.json`
- `appsettings.Development.json`

<span data-ttu-id="cd696-145">これらのファイルは、[アプリの起動](/aspnet/core/fundamentals/startup)と[構成](/aspnet/core/fundamentals/configuration)のために ASP.NET Core によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-145">These files are used by ASP.NET Core for [app startup](/aspnet/core/fundamentals/startup) and [configuration](/aspnet/core/fundamentals/configuration).</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/add-template-files.png" alt-text=".NET アップグレード アシスタントによるテンプレート ファイルの追加":::

<span data-ttu-id="cd696-147">次に、このツールで構成ファイルを移行します。</span><span class="sxs-lookup"><span data-stu-id="cd696-147">Next, the tool migrates config files.</span></span> <span data-ttu-id="cd696-148">ツールでアプリの設定が識別され、サポートされていない構成セクションが無効化されてから、`appSettings` 構成の値が移行されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-148">The tool identifies app settings and disables unsupported configuration sections, then migrates the `appSettings` configuration values.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config.png" alt-text=".NET アップグレード アシスタントによる構成の移行":::

<span data-ttu-id="cd696-150">`system.web.webPages.razor/pages/namespaces` が移行されて、ツールによる構成ファイルの移行が完了します。</span><span class="sxs-lookup"><span data-stu-id="cd696-150">The tool completes the migration of config files by migrating `system.web.webPages.razor/pages/namespaces`.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config2.png" alt-text=".NET アップグレード アシスタントによる構成の移行が完了しました":::

<span data-ttu-id="cd696-152">ツールによって既知の修正プログラムが適用され、C# の参照が新しい対応するものに移行されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-152">The tool applies known fixes to migrate C# references to their new counterparts.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-csharp.png" alt-text=".NET アップグレード アシスタントによる C# ソースの更新":::

<span data-ttu-id="cd696-154">これは最後のプロジェクトであるため、次のステップ "Move to next project" では、ソリューション全体の移行プロセスを完了するように求められます。</span><span class="sxs-lookup"><span data-stu-id="cd696-154">Since this is the last project, the next step, "Move to next project", prompts to complete the process of migrating the entire solution.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/complete-solution.png" alt-text=".NET アップグレード アシスタントでのソリューションの完了":::

<span data-ttu-id="cd696-156">このプロセスが完了したら、プロジェクト ファイルを開いて確認します。</span><span class="sxs-lookup"><span data-stu-id="cd696-156">Once this process has completed, open the project file and review it.</span></span> <span data-ttu-id="cd696-157">次のような静的ファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="cd696-157">Look for static files like these:</span></span>

```xml
  <ItemGroup>
    <Content Include="fonts\glyphicons-halflings-regular.woff2" />
    <Content Include="fonts\glyphicons-halflings-regular.woff" />
    <Content Include="fonts\glyphicons-halflings-regular.ttf" />
    <Content Include="fonts\glyphicons-halflings-regular.eot" />
    <Content Include="Content\bootstrap.min.css.map" />
    <Content Include="Content\bootstrap.css.map" />
    <Content Include="Content\bootstrap-theme.min.css.map" />
    <Content Include="Content\bootstrap-theme.css.map" />
    <Content Include="Scripts\jquery-3.4.1.slim.min.map" />
    <Content Include="Scripts\jquery-3.4.1.min.map" />
  </ItemGroup>
```

<span data-ttu-id="cd696-158">Web サーバーによって提供される静的ファイルは、`wwwroot` というルート レベルのフォルダー内の適切なフォルダーに移動される必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd696-158">Static files that should be served by the web server should be moved to an appropriate folder within a root level folder named `wwwroot`.</span></span> <span data-ttu-id="cd696-159">詳細については、「[ASP.NET Core の静的ファイル](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0&preserve-view=true)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd696-159">See [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0&preserve-view=true) for details.</span></span> <span data-ttu-id="cd696-160">ファイルが移動されたら、プロジェクト ファイル内にある、これらのファイルに対応する `<Content>` 要素を削除できます。</span><span class="sxs-lookup"><span data-stu-id="cd696-160">Once the files have been moved, the `<Content>` elements in the project file corresponding to these files can be deleted.</span></span> <span data-ttu-id="cd696-161">実際、すべての `<Content>` 要素と、それらが含まれるグループを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="cd696-161">In fact, all `<Content>` elements and their containing groups can be removed.</span></span> <span data-ttu-id="cd696-162">また、`bootstrap` や `jQuery` のようなクライアント側ライブラリへの `<PackageReference>`があれば、削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd696-162">Also, any `<PackageReference>` to a client-side library like `bootstrap` or `jQuery` should be removed.</span></span>

<span data-ttu-id="cd696-163">既定では、プロジェクトはクラス ライブラリとして変換されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-163">By default, the project will be converted as a class library.</span></span> <span data-ttu-id="cd696-164">1 行目の `Sdk` 属性を `Microsoft.NET.Sdk.Web` に変更し、`<TargetFramework>` を `net5.0` に設定します。</span><span class="sxs-lookup"><span data-stu-id="cd696-164">Change the first line's `Sdk` attribute to `Microsoft.NET.Sdk.Web` and set the `<TargetFramework>` to `net5.0`.</span></span> <span data-ttu-id="cd696-165">プロジェクトをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="cd696-165">Compile the project.</span></span> <span data-ttu-id="cd696-166">この時点では、エラーの数はかなり少ないはずです。</span><span class="sxs-lookup"><span data-stu-id="cd696-166">At this point, the number of errors should be fairly small.</span></span> <span data-ttu-id="cd696-167">新しい ASP.NET 4.6.1 MVC プロジェクトを移植する場合は、残りのエラーで `App_Start` フォルダー内のファイルが参照されます。</span><span class="sxs-lookup"><span data-stu-id="cd696-167">When porting a new ASP.NET 4.6.1 MVC project, the remaining errors refer to files in the `App_Start` folder:</span></span>

- <span data-ttu-id="cd696-168">BundleConfig.cs</span><span class="sxs-lookup"><span data-stu-id="cd696-168">BundleConfig.cs</span></span>
- <span data-ttu-id="cd696-169">FilterConfig.cs</span><span class="sxs-lookup"><span data-stu-id="cd696-169">FilterConfig.cs</span></span>
- <span data-ttu-id="cd696-170">RouteConfig.cs</span><span class="sxs-lookup"><span data-stu-id="cd696-170">RouteConfig.cs</span></span>

<span data-ttu-id="cd696-171">これらのファイル、および `App_Start` フォルダー全体を削除できます。</span><span class="sxs-lookup"><span data-stu-id="cd696-171">These files - and the entire `App_Start` folder - can be deleted.</span></span> <span data-ttu-id="cd696-172">同様に、`Global.asax` および `Global.asax.cs` ファイルも削除できます。</span><span class="sxs-lookup"><span data-stu-id="cd696-172">Likewise, the `Global.asax` and `Global.asax.cs` files can be removed.</span></span>

<span data-ttu-id="cd696-173">この時点で残っているエラーは、バンドルに関連するものだけです。</span><span class="sxs-lookup"><span data-stu-id="cd696-173">At this point the only errors that remain are related to bundling.</span></span> <span data-ttu-id="cd696-174">[ASP.NET Core でバンドルと縮小を構成するには、いくつかの方法](/aspnet/core/migration/mvc?view=aspnetcore-5.0&preserve-view=true#configure-bundling-and-minification)があります。</span><span class="sxs-lookup"><span data-stu-id="cd696-174">There are [several ways to configure bundling and minification in ASP.NET Core](/aspnet/core/migration/mvc?view=aspnetcore-5.0&preserve-view=true#configure-bundling-and-minification).</span></span> <span data-ttu-id="cd696-175">プロジェクトに最も適したものを選択してください。</span><span class="sxs-lookup"><span data-stu-id="cd696-175">Choose whatever makes the most sense for your project.</span></span>

## <a name="troubleshooting-tips"></a><span data-ttu-id="cd696-176">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="cd696-176">Troubleshooting tips</span></span>

<span data-ttu-id="cd696-177">.NET アップグレード アシスタントの使用時に発生するおそれがある既知の問題がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="cd696-177">There are several known problems that can occur when using the .NET Upgrade Assistant.</span></span> <span data-ttu-id="cd696-178">場合によっては、.NET アップグレード アシスタントで内部的に使用される [try-convert ツール](https://github.com/dotnet/try-convert)に問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="cd696-178">In some cases, these are problems with the [try-convert tool](https://github.com/dotnet/try-convert) that the .NET Upgrade Assistant uses internally.</span></span> <span data-ttu-id="cd696-179">このツールは、より多くのシナリオに対応するように頻繁に更新されるため、最新のバージョンを使用していることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cd696-179">This tool is being frequently updated to address more scenarios, so make sure you're using a recent version.</span></span>

- <span data-ttu-id="cd696-180">**try-convert** ツールをインストールして、少なくともバージョン _0.7.212201_ に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd696-180">The **try-convert** tool must be installed and updated to at least version _0.7.212201_.</span></span>
- <span data-ttu-id="cd696-181">以前のバージョンの **try-convert** ツールでは、カスタムのターゲットまたは props ファイルがサポートされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="cd696-181">Earlier versions of the **try-convert** tool didn't support custom target or props files.</span></span> <span data-ttu-id="cd696-182">最新バージョンにアップグレードできない場合は、これらの問題に手動で対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd696-182">If you can't upgrade to the latest version, you may need to manually address these issues.</span></span> <span data-ttu-id="cd696-183">ターゲット プロジェクト ファイルにカスタムのターゲットまたは props ファイルへの参照が含まれている場合、.NET アップグレード アシスタントを実行する前に、それらの参照をファイルから手動で削除しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="cd696-183">If the target project file includes references to custom targets or props files, these references may need to be manually deleted from the file before the .NET Upgrade Assistant is run against it.</span></span>

```xml
<Import Project="packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props" Condition="Exists('packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props')" />
```

<span data-ttu-id="cd696-184">その他のトラブルシューティングのヒントと既知の問題については、[ツールの GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd696-184">[The tool's GitHub repository](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) has more troubleshooting tips and known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd696-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd696-185">See also</span></span>

- [<span data-ttu-id="cd696-186">.NET アップグレード アシスタントを使用して WPF アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="cd696-186">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-wpf-framework.md)
- [<span data-ttu-id="cd696-187">.NET アップグレード アシスタントを使用して Windows フォーム アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="cd696-187">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="cd696-188">.NET アップグレード アシスタントの概要</span><span class="sxs-lookup"><span data-stu-id="cd696-188">Overview of the .NET Upgrade Assistant</span></span>](upgrade-assistant-overview.md)
- [<span data-ttu-id="cd696-189">.NET アップグレード アシスタントの GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="cd696-189">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
