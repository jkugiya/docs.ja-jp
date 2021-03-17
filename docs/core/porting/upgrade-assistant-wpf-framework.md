---
title: WPF アプリを .NET 5 にアップグレードする
description: .NET アップグレード アシスタントを使用して、既存の .NET Framework WPF アプリを .NET 5 にアップグレードします。 .NET アップグレード アシスタントは、.NET Framework から .NET 5 にアプリを移行するときに役立つ CLI ツールです。
author: ardalis
ms.date: 03/08/2021
ms.openlocfilehash: b0c9baa25be6da4e7849f28c875a1d8f5f5a5d07
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604841"
---
# <a name="upgrade-a-wpf-app-to-net-5-with-the-net-upgrade-assistant"></a><span data-ttu-id="3d86c-104">.NET アップグレード アシスタントを使用して WPF アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="3d86c-104">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>

<span data-ttu-id="3d86c-105">[.NET アップグレード アシスタント](upgrade-assistant-overview.md)は、.NET Framework WPF アプリを .NET 5 にアップグレードするときに役立つコマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="3d86c-105">The [.NET Upgrade Assistant](upgrade-assistant-overview.md) is a command-line tool that can assist with upgrading .NET Framework WPF apps to .NET 5.</span></span> <span data-ttu-id="3d86c-106">この記事では、次について説明します。</span><span class="sxs-lookup"><span data-stu-id="3d86c-106">This article provides:</span></span>

- <span data-ttu-id="3d86c-107">.NET Framework WPF アプリに対してツールを実行する方法のデモ</span><span class="sxs-lookup"><span data-stu-id="3d86c-107">A demonstration of how to run the tool against a .NET Framework WPF app</span></span>
- <span data-ttu-id="3d86c-108">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="3d86c-108">Troubleshooting tips</span></span>

## <a name="upgrade-net-framework-wpf-apps"></a><span data-ttu-id="3d86c-109">.NET Framework WPF アプリをアップグレードする</span><span class="sxs-lookup"><span data-stu-id="3d86c-109">Upgrade .NET Framework WPF apps</span></span>

<span data-ttu-id="3d86c-110">このセクションでは、.NET Framework 4.6.1 を対象として新しく作成された WPF アプリに対して .NET アップグレード アシスタントを実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3d86c-110">This section demonstrates running the .NET Upgrade Assistant against a newly created WPF app targeting .NET Framework 4.6.1.</span></span> <span data-ttu-id="3d86c-111">ツールのインストール方法の詳細については、「[.NET アップグレード アシスタントの概要](upgrade-assistant-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d86c-111">For more information on how to install the tool, see [Overview of the .NET Upgrade Assistant](upgrade-assistant-overview.md).</span></span>

### <a name="initial-demo-setup"></a><span data-ttu-id="3d86c-112">デモの初期セットアップ</span><span class="sxs-lookup"><span data-stu-id="3d86c-112">Initial demo setup</span></span>

<span data-ttu-id="3d86c-113">ご自身の .NET Framework アプリに対して .NET アップグレード アシスタントを実行する場合は、このステップを省略できます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-113">If you're running the .NET Upgrade Assistant against your own .NET Framework app, you can skip this step.</span></span> <span data-ttu-id="3d86c-114">その動作を確認するだけの場合は、このステップを見ると、使用するサンプル .NET WPF プロジェクトを設定する方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="3d86c-114">If you just want to try it out to see how it works, this step shows you how to set up a sample .NET WPF project to use.</span></span>

<span data-ttu-id="3d86c-115">Visual Studio で、.NET Framework を使用して新しい WPF アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d86c-115">Using Visual Studio, create a new WPF App using .NET Framework.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/new-project.png" alt-text="Visual Studio での新しい WPF プロジェクト":::

<span data-ttu-id="3d86c-117">プロジェクトに **WpfTest** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-117">Name the project **WpfTest**.</span></span> <span data-ttu-id="3d86c-118">**.NET Framework 4.6.1** を使用するようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="3d86c-118">Configure the project to use **.NET Framework 4.6.1**.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/configure-project.png" alt-text="Visual Studio で Windows フォーム プロジェクトを構成する":::

<span data-ttu-id="3d86c-120">作成したプロジェクトとそのファイル (特にプロジェクト ファイル) を確認します。</span><span class="sxs-lookup"><span data-stu-id="3d86c-120">Review the created project and its files, especially its project file(s).</span></span>

### <a name="run-upgrade-assistant"></a><span data-ttu-id="3d86c-121">upgrade-assistant の実行</span><span class="sxs-lookup"><span data-stu-id="3d86c-121">Run upgrade-assistant</span></span>

<span data-ttu-id="3d86c-122">ターミナルを開き、ターゲット プロジェクトまたはソリューションが配置されているフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3d86c-122">Open a terminal and navigate to the folder where the target project or solution is located.</span></span> <span data-ttu-id="3d86c-123">`upgrade-assistant` コマンドを実行します。このとき、ターゲットとするプロジェクトの名前を渡します (プロジェクト ファイルのパスが有効である限り、任意の場所からコマンドを実行できます)。</span><span class="sxs-lookup"><span data-stu-id="3d86c-123">Run the `upgrade-assistant` command, passing in the name of the project you're targeting (you can run the command from anywhere, as long as the path to the project file is valid).</span></span>

```console
upgrade-assistant .\WpfTest.csproj
```

<span data-ttu-id="3d86c-124">ツールが実行され、行われるステップの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-124">The tool runs and shows you a list of the steps it will do.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/initial-run.png" alt-text=".NET アップグレード アシスタントの初期画面":::

<span data-ttu-id="3d86c-126">各ステップが完了すると、ツールにコマンドのセットが表示されます。ユーザーはそれらを使用して、次のステップを適用またはスキップすること、詳細を確認すること、ログを構成すること、プロセスを終了することができます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-126">As each step is completed, the tool provides a set of commands allowing the user to apply or skip the next step, see more details, configure logging, or exit the process.</span></span> <span data-ttu-id="3d86c-127">あるステップで実行するアクションがないことが検出された場合は、そのステップがツールで自動的にスキップされ、実行するアクションを含む次のステップに進みます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-127">If the tool detects that a step will perform no actions, it will automatically skip that step and continue to the next step until it reaches one that will have actions to perform.</span></span> <span data-ttu-id="3d86c-128">Enter キーを押すと、他に何も選択していない場合は次のステップが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-128">Pressing enter will perform the next step if no other selection is made.</span></span>

<span data-ttu-id="3d86c-129">この例では、適用ステップを毎回選択しています。</span><span class="sxs-lookup"><span data-stu-id="3d86c-129">In this example, the apply step is chosen each time.</span></span> <span data-ttu-id="3d86c-130">最初のステップは、プロジェクトのバックアップです。</span><span class="sxs-lookup"><span data-stu-id="3d86c-130">The first step is to back up the project.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/backup-project.png" alt-text=".NET アップグレード アシスタントでのプロジェクトのバックアップ":::

<span data-ttu-id="3d86c-132">ツールにバックアップのカスタム パスを入力します。または、既定値を使用します。その場合は、`.backup` という拡張子の付いたプロジェクトのバックアップが同じフォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-132">The tool prompts for a custom path for the backup, or to use the default, which will place the project backup in the same folder with a `.backup` extension.</span></span> <span data-ttu-id="3d86c-133">ツールで実行される次のステップは、プロジェクト ファイルを SDK スタイルに変換することです。</span><span class="sxs-lookup"><span data-stu-id="3d86c-133">The next step the tool performs is to convert the project file to SDK style.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/convert-project.png" alt-text=".NET アップグレード アシスタントによるプロジェクトの SDK スタイルへの変換":::

<span data-ttu-id="3d86c-135">プロジェクトの形式が更新されたら、次のステップは、プロジェクトの TFM を更新することです。</span><span class="sxs-lookup"><span data-stu-id="3d86c-135">Once the project format has been updated, the next step is to update the TFM of the project.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-tfm.png" alt-text=".NET アップグレード アシスタントによる TFM の更新":::

<span data-ttu-id="3d86c-137">次に、ツールによってプロジェクトの NuGet パッケージが更新されます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-137">Next, the tool updates the project's NuGet packages.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-nuget-packages.png" alt-text=".NET アップグレード アシスタントによる NuGet パッケージの更新":::

<span data-ttu-id="3d86c-139">パッケージが更新されたら、次のステップは、テンプレート ファイル (存在する場合) を追加することです。</span><span class="sxs-lookup"><span data-stu-id="3d86c-139">Once the packages are updated, the next step is to add template files, if any.</span></span> <span data-ttu-id="3d86c-140">この場合、追加する必要があるテンプレート ファイルはありません。</span><span class="sxs-lookup"><span data-stu-id="3d86c-140">In this case, there are no template files that need to be added.</span></span> <span data-ttu-id="3d86c-141">このステップでは、次に示すように、アプリ構成ファイルを移行し、C# ソースを更新して修正プログラムを適用します。</span><span class="sxs-lookup"><span data-stu-id="3d86c-141">This step continues and migrates app config files and updates C# source to apply fixes, as shown below.</span></span> <span data-ttu-id="3d86c-142">このプロジェクトの構成ファイルまたはソース コードを変更する必要はなかったため、これらの手順は自動的に行われました。</span><span class="sxs-lookup"><span data-stu-id="3d86c-142">This project didn't need any config file or source code changes, so these steps proceeded automatically.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/add-template-files.png" alt-text=".NET アップグレード アシスタントによってテンプレート ファイルが追加され、構成が移行される":::

<span data-ttu-id="3d86c-144">これは最後のプロジェクトであるため、次のステップ "Move to next project" では、ソリューション全体の移行プロセスを完了するように求められます。</span><span class="sxs-lookup"><span data-stu-id="3d86c-144">Since this is the last project, the next step, "Move to next project", prompts to complete the process of migrating the entire solution.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/complete-solution.png" alt-text=".NET アップグレード アシスタントでのソリューションの完了":::

<span data-ttu-id="3d86c-146">このプロセスが完了すると、移行された WPF プロジェクトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3d86c-146">Once this process has completed, the migrated WPF project will look something like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0-windows</TargetFramework>
    <OutputType>WinExe</OutputType>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <UseWPF>true</UseWPF>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
    <PackageReference Include="Microsoft.DotNet.UpgradeAssistant.Extensions.Default.Analyzers" Version="0.2.211942">
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="5.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="3d86c-147">.NET アップグレード アシスタントにより、アップグレード プロセスを続けるのに役立つアナライザーもプロジェクトに追加されることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="3d86c-147">Notice that the .NET Upgrade Assistant also adds analyzers to the project that assist with continuing the upgrade process.</span></span>

## <a name="troubleshooting-tips"></a><span data-ttu-id="3d86c-148">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="3d86c-148">Troubleshooting tips</span></span>

<span data-ttu-id="3d86c-149">.NET アップグレード アシスタントの使用時に発生するおそれがある既知の問題がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="3d86c-149">There are several known problems that can occur when using the .NET Upgrade Assistant.</span></span> <span data-ttu-id="3d86c-150">場合によっては、.NET アップグレード アシスタントで内部的に使用される [try-convert ツール](https://github.com/dotnet/try-convert)に問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="3d86c-150">In some cases, these are problems with the [try-convert tool](https://github.com/dotnet/try-convert) that the .NET Upgrade Assistant uses internally.</span></span> <span data-ttu-id="3d86c-151">このツールは、より多くのシナリオに対応するように頻繁に更新されるため、最新のバージョンを使用していることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="3d86c-151">This tool is being frequently updated to address more scenarios, so make sure you're using a recent version.</span></span>

- <span data-ttu-id="3d86c-152">try-convert ツールをインストールして、少なくともバージョン _0.7.21201_ に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d86c-152">The try-convert tool must be installed and updated to at least version _0.7.21201_.</span></span>
- <span data-ttu-id="3d86c-153">以前のバージョンの try-convert ツールでは、カスタムのターゲットまたは props ファイルがサポートされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="3d86c-153">Earlier versions of the try-convert tool didn't support custom target or props files.</span></span> <span data-ttu-id="3d86c-154">最新バージョンにアップグレードできない場合は、これらの問題に手動で対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d86c-154">If you can't upgrade to the latest version, you may need to manually address these issues.</span></span> <span data-ttu-id="3d86c-155">ターゲット プロジェクト ファイルにカスタムのターゲットまたは props ファイルへの参照が含まれている場合、.NET アップグレード アシスタントを実行する前に、それらの参照をファイルから手動で削除しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d86c-155">If the target project file includes references to custom targets or props files, these references may need to be manually deleted from the file before the .NET Upgrade Assistant is run against it.</span></span>

<span data-ttu-id="3d86c-156">その他のトラブルシューティングのヒントと既知の問題については、[ツールの GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d86c-156">[The tool's GitHub repository](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) has more troubleshooting tips and known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d86c-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d86c-157">See also</span></span>

- [<span data-ttu-id="3d86c-158">.NET アップグレード アシスタントを使用して Windows フォーム アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="3d86c-158">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="3d86c-159">.NET アップグレード アシスタントを使用して ASP.NET MVC アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="3d86c-159">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-aspnetmvc.md)
- [<span data-ttu-id="3d86c-160">.NET アップグレード アシスタントの概要</span><span class="sxs-lookup"><span data-stu-id="3d86c-160">Overview of the .NET Upgrade Assistant</span></span>](upgrade-assistant-overview.md)
- [<span data-ttu-id="3d86c-161">.NET アップグレード アシスタントの GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="3d86c-161">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
