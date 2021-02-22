---
title: dotnet new コマンド
description: dotnet new コマンドを実行すると、指定したテンプレートに基づいて、新しい .NET プロジェクトが作成されます。
no-loc:
- Blazor
- WebAssembly
ms.date: 09/04/2020
ms.openlocfilehash: acaaf025555c46f720452b8c9d4f875b8656125a
ms.sourcegitcommit: b924ade6426cf61a4604c4e2ee54cb3592c29317
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/18/2021
ms.locfileid: "101096810"
---
# <a name="dotnet-new"></a><span data-ttu-id="8d758-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8d758-103">dotnet new</span></span>

<span data-ttu-id="8d758-104">**この記事の対象:** ✔️ .NET Core 2.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8d758-105">名前</span><span class="sxs-lookup"><span data-stu-id="8d758-105">Name</span></span>

<span data-ttu-id="8d758-106">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d758-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8d758-107">構文</span><span class="sxs-lookup"><span data-stu-id="8d758-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="8d758-108">説明</span><span class="sxs-lookup"><span data-stu-id="8d758-108">Description</span></span>

<span data-ttu-id="8d758-109">`dotnet new` コマンドを実行すると、テンプレートに基づいて、.NET プロジェクトまたはその他の成果物が作成されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-109">The `dotnet new` command creates a .NET project or other artifacts based on a template.</span></span>

<span data-ttu-id="8d758-110">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="8d758-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="8d758-111">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="8d758-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="8d758-112">引数</span><span class="sxs-lookup"><span data-stu-id="8d758-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="8d758-113">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="8d758-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="8d758-114">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d758-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="8d758-115">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d758-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="8d758-116">`dotnet new --list` または `dotnet new -l` を実行すると、インストールされているすべてのテンプレートの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="8d758-117">`TEMPLATE` の値が返されたテーブルの「**テンプレート**」列または「**短い形式の名前**」列のテキストと完全に一致しない場合、それら 2 つの列で部分文字列一致が実行されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="8d758-118">.NET Core 3.0 SDK 以降では、次の条件で `dotnet new` コマンドを呼び出すと、CLI によって NuGet.org 内のテンプレートが検索されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="8d758-119">`dotnet new` の呼び出し時に、CLI でテンプレートの一致を (部分的にも) 検出できない場合。</span><span class="sxs-lookup"><span data-stu-id="8d758-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="8d758-120">テンプレートの新しいバージョンが利用可能な場合。</span><span class="sxs-lookup"><span data-stu-id="8d758-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="8d758-121">この場合、プロジェクトまたは成果物が作成されますが、更新されたバージョンのテンプレートについて、CLI によって警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="8d758-122">次の表は、.NET SDK にプレインストールされているテンプレートを示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-122">The following table shows the templates that come pre-installed with the .NET SDK.</span></span> <span data-ttu-id="8d758-123">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="8d758-124">短い名前のリンクをクリックすると、特定のテンプレート オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="8d758-125">テンプレート</span><span class="sxs-lookup"><span data-stu-id="8d758-125">Templates</span></span>                                    | <span data-ttu-id="8d758-126">短い名前</span><span class="sxs-lookup"><span data-stu-id="8d758-126">Short name</span></span>                        | <span data-ttu-id="8d758-127">言語</span><span class="sxs-lookup"><span data-stu-id="8d758-127">Language</span></span>     | <span data-ttu-id="8d758-128">Tags</span><span class="sxs-lookup"><span data-stu-id="8d758-128">Tags</span></span>                                  | <span data-ttu-id="8d758-129">導入時期</span><span class="sxs-lookup"><span data-stu-id="8d758-129">Introduced</span></span> |
|----------------------------------------------|-----------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="8d758-130">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="8d758-130">Console Application</span></span>                          | [`console`](#console)             | <span data-ttu-id="8d758-131">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d758-131">[C#], F#, VB</span></span> | <span data-ttu-id="8d758-132">Common/Console</span><span class="sxs-lookup"><span data-stu-id="8d758-132">Common/Console</span></span>                        | <span data-ttu-id="8d758-133">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-133">1.0</span></span>        |
| <span data-ttu-id="8d758-134">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8d758-134">Class library</span></span>                                | [`classlib`](#classlib)           | <span data-ttu-id="8d758-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d758-135">[C#], F#, VB</span></span> | <span data-ttu-id="8d758-136">Common/Library</span><span class="sxs-lookup"><span data-stu-id="8d758-136">Common/Library</span></span>                        | <span data-ttu-id="8d758-137">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-137">1.0</span></span>        |
| <span data-ttu-id="8d758-138">WPF アプリケーション</span><span class="sxs-lookup"><span data-stu-id="8d758-138">WPF Application</span></span>                              | [`wpf`](#wpf)                     | <span data-ttu-id="8d758-139">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="8d758-139">[C#], VB</span></span>     | <span data-ttu-id="8d758-140">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="8d758-140">Common/WPF</span></span>                            | <span data-ttu-id="8d758-141">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="8d758-141">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8d758-142">WPF クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8d758-142">WPF Class library</span></span>                            | [`wpflib`](#wpf)                  | <span data-ttu-id="8d758-143">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="8d758-143">[C#], VB</span></span>     | <span data-ttu-id="8d758-144">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="8d758-144">Common/WPF</span></span>                            | <span data-ttu-id="8d758-145">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="8d758-145">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8d758-146">WPF カスタム コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8d758-146">WPF Custom Control Library</span></span>                   | [`wpfcustomcontrollib`](#wpf)     | <span data-ttu-id="8d758-147">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="8d758-147">[C#], VB</span></span>     | <span data-ttu-id="8d758-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="8d758-148">Common/WPF</span></span>                            | <span data-ttu-id="8d758-149">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="8d758-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8d758-150">WPF ユーザー コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8d758-150">WPF User Control Library</span></span>                     | [`wpfusercontrollib`](#wpf)       | <span data-ttu-id="8d758-151">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="8d758-151">[C#], VB</span></span>     | <span data-ttu-id="8d758-152">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="8d758-152">Common/WPF</span></span>                            | <span data-ttu-id="8d758-153">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="8d758-153">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8d758-154">Windows フォーム (WinForms) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="8d758-154">Windows Forms (WinForms) Application</span></span>         | [`winforms`](#winforms)           | <span data-ttu-id="8d758-155">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="8d758-155">[C#], VB</span></span>     | <span data-ttu-id="8d758-156">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="8d758-156">Common/WinForms</span></span>                       | <span data-ttu-id="8d758-157">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="8d758-157">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8d758-158">Windows フォーム (WinForms) クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8d758-158">Windows Forms (WinForms) Class library</span></span>       | [`winformslib`](#winforms)        | <span data-ttu-id="8d758-159">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="8d758-159">[C#], VB</span></span>     | <span data-ttu-id="8d758-160">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="8d758-160">Common/WinForms</span></span>                       | <span data-ttu-id="8d758-161">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="8d758-161">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8d758-162">Worker Service</span><span class="sxs-lookup"><span data-stu-id="8d758-162">Worker Service</span></span>                               | [`worker`](#web-others)           | <span data-ttu-id="8d758-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-163">[C#]</span></span>         | <span data-ttu-id="8d758-164">Common/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="8d758-164">Common/Worker/Web</span></span>                     | <span data-ttu-id="8d758-165">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-165">3.0</span></span>        |
| <span data-ttu-id="8d758-166">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8d758-166">Unit Test Project</span></span>                            | [`mstest`](#test)                 | <span data-ttu-id="8d758-167">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d758-167">[C#], F#, VB</span></span> | <span data-ttu-id="8d758-168">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="8d758-168">Test/MSTest</span></span>                           | <span data-ttu-id="8d758-169">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-169">1.0</span></span>        |
| <span data-ttu-id="8d758-170">NUnit 3 テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8d758-170">NUnit 3 Test Project</span></span>                         | [`nunit`](#nunit)                 | <span data-ttu-id="8d758-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d758-171">[C#], F#, VB</span></span> | <span data-ttu-id="8d758-172">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="8d758-172">Test/NUnit</span></span>                            | <span data-ttu-id="8d758-173">2.1.400</span><span class="sxs-lookup"><span data-stu-id="8d758-173">2.1.400</span></span>    |
| <span data-ttu-id="8d758-174">NUnit 3 テスト項目</span><span class="sxs-lookup"><span data-stu-id="8d758-174">NUnit 3 Test Item</span></span>                            | `nunit-test`                      | <span data-ttu-id="8d758-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d758-175">[C#], F#, VB</span></span> | <span data-ttu-id="8d758-176">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="8d758-176">Test/NUnit</span></span>                            | <span data-ttu-id="8d758-177">2.2</span><span class="sxs-lookup"><span data-stu-id="8d758-177">2.2</span></span>        |
| <span data-ttu-id="8d758-178">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8d758-178">xUnit Test Project</span></span>                           | [`xunit`](#test)                  | <span data-ttu-id="8d758-179">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8d758-179">[C#], F#, VB</span></span> | <span data-ttu-id="8d758-180">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="8d758-180">Test/xUnit</span></span>                            | <span data-ttu-id="8d758-181">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-181">1.0</span></span>        |
| <span data-ttu-id="8d758-182">Razor コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8d758-182">Razor Component</span></span>                              | `razorcomponent`                  | <span data-ttu-id="8d758-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-183">[C#]</span></span>         | <span data-ttu-id="8d758-184">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8d758-184">Web/ASP.NET</span></span>                           | <span data-ttu-id="8d758-185">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-185">3.0</span></span>        |
| <span data-ttu-id="8d758-186">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="8d758-186">Razor Page</span></span>                                   | [`page`](#page)                   | <span data-ttu-id="8d758-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-187">[C#]</span></span>         | <span data-ttu-id="8d758-188">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8d758-188">Web/ASP.NET</span></span>                           | <span data-ttu-id="8d758-189">2.0</span><span class="sxs-lookup"><span data-stu-id="8d758-189">2.0</span></span>        |
| <span data-ttu-id="8d758-190">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="8d758-190">MVC ViewImports</span></span>                              | [`viewimports`](#namespace)       | <span data-ttu-id="8d758-191">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-191">[C#]</span></span>         | <span data-ttu-id="8d758-192">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8d758-192">Web/ASP.NET</span></span>                           | <span data-ttu-id="8d758-193">2.0</span><span class="sxs-lookup"><span data-stu-id="8d758-193">2.0</span></span>        |
| <span data-ttu-id="8d758-194">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="8d758-194">MVC ViewStart</span></span>                                | `viewstart`                       | <span data-ttu-id="8d758-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-195">[C#]</span></span>         | <span data-ttu-id="8d758-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8d758-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="8d758-197">2.0</span><span class="sxs-lookup"><span data-stu-id="8d758-197">2.0</span></span>        |
| <span data-ttu-id="8d758-198">Blazor サーバー アプリ</span><span class="sxs-lookup"><span data-stu-id="8d758-198">Blazor Server App</span></span>                            | [`blazorserver`](#blazorserver)   | <span data-ttu-id="8d758-199">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-199">[C#]</span></span>         | <span data-ttu-id="8d758-200">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="8d758-200">Web/Blazor</span></span>                            | <span data-ttu-id="8d758-201">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-201">3.0</span></span>        |
| <span data-ttu-id="8d758-202">Blazor WebAssembly アプリ</span><span class="sxs-lookup"><span data-stu-id="8d758-202">Blazor WebAssembly App</span></span>                       | [`blazorwasm`](#blazorwasm)       | <span data-ttu-id="8d758-203">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-203">[C#]</span></span>         | <span data-ttu-id="8d758-204">Web/Blazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="8d758-204">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="8d758-205">3.1.300</span><span class="sxs-lookup"><span data-stu-id="8d758-205">3.1.300</span></span>    |
| <span data-ttu-id="8d758-206">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="8d758-206">ASP.NET Core Empty</span></span>                           | [`web`](#web)                     | <span data-ttu-id="8d758-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8d758-207">[C#], F#</span></span>     | <span data-ttu-id="8d758-208">Web/Empty</span><span class="sxs-lookup"><span data-stu-id="8d758-208">Web/Empty</span></span>                             | <span data-ttu-id="8d758-209">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-209">1.0</span></span>        |
| <span data-ttu-id="8d758-210">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="8d758-210">ASP.NET Core Web App (Model-View-Controller)</span></span> | [`mvc`](#web-options)             | <span data-ttu-id="8d758-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8d758-211">[C#], F#</span></span>     | <span data-ttu-id="8d758-212">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="8d758-212">Web/MVC</span></span>                               | <span data-ttu-id="8d758-213">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-213">1.0</span></span>        |
| <span data-ttu-id="8d758-214">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="8d758-214">ASP.NET Core Web App</span></span>                         | [`webapp, razor`](#web-options)   | <span data-ttu-id="8d758-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-215">[C#]</span></span>         | <span data-ttu-id="8d758-216">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="8d758-216">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="8d758-217">2.2、2.0</span><span class="sxs-lookup"><span data-stu-id="8d758-217">2.2, 2.0</span></span>   |
| <span data-ttu-id="8d758-218">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d758-218">ASP.NET Core with Angular</span></span>                    | [`angular`](#spa)                 | <span data-ttu-id="8d758-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-219">[C#]</span></span>         | <span data-ttu-id="8d758-220">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="8d758-220">Web/MVC/SPA</span></span>                           | <span data-ttu-id="8d758-221">2.0</span><span class="sxs-lookup"><span data-stu-id="8d758-221">2.0</span></span>        |
| <span data-ttu-id="8d758-222">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d758-222">ASP.NET Core with React.js</span></span>                   | [`react`](#spa)                   | <span data-ttu-id="8d758-223">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-223">[C#]</span></span>         | <span data-ttu-id="8d758-224">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="8d758-224">Web/MVC/SPA</span></span>                           | <span data-ttu-id="8d758-225">2.0</span><span class="sxs-lookup"><span data-stu-id="8d758-225">2.0</span></span>        |
| <span data-ttu-id="8d758-226">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d758-226">ASP.NET Core with React.js and Redux</span></span>         | [`reactredux`](#reactredux)       | <span data-ttu-id="8d758-227">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-227">[C#]</span></span>         | <span data-ttu-id="8d758-228">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="8d758-228">Web/MVC/SPA</span></span>                           | <span data-ttu-id="8d758-229">2.0</span><span class="sxs-lookup"><span data-stu-id="8d758-229">2.0</span></span>        |
| <span data-ttu-id="8d758-230">Razor クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8d758-230">Razor Class Library</span></span>                          | [`razorclasslib`](#razorclasslib) | <span data-ttu-id="8d758-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-231">[C#]</span></span>         | <span data-ttu-id="8d758-232">Web/Razor/Library/Razor Class Library</span><span class="sxs-lookup"><span data-stu-id="8d758-232">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="8d758-233">2.1</span><span class="sxs-lookup"><span data-stu-id="8d758-233">2.1</span></span>        |
| <span data-ttu-id="8d758-234">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="8d758-234">ASP.NET Core Web API</span></span>                         | [`webapi`](#webapi)               | <span data-ttu-id="8d758-235">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8d758-235">[C#], F#</span></span>     | <span data-ttu-id="8d758-236">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="8d758-236">Web/WebAPI</span></span>                            | <span data-ttu-id="8d758-237">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-237">1.0</span></span>        |
| <span data-ttu-id="8d758-238">ASP.NET Core gRPC サービス</span><span class="sxs-lookup"><span data-stu-id="8d758-238">ASP.NET Core gRPC Service</span></span>                    | [`grpc`](#web-others)             | <span data-ttu-id="8d758-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="8d758-239">[C#]</span></span>         | <span data-ttu-id="8d758-240">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="8d758-240">Web/gRPC</span></span>                              | <span data-ttu-id="8d758-241">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-241">3.0</span></span>        |
| <span data-ttu-id="8d758-242">dotnet gitignore ファイル</span><span class="sxs-lookup"><span data-stu-id="8d758-242">dotnet gitignore file</span></span>                        | `gitignore`                       |              | <span data-ttu-id="8d758-243">構成</span><span class="sxs-lookup"><span data-stu-id="8d758-243">Config</span></span>                                | <span data-ttu-id="8d758-244">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-244">3.0</span></span>        |
| <span data-ttu-id="8d758-245">global.json file</span><span class="sxs-lookup"><span data-stu-id="8d758-245">global.json file</span></span>                             | [`globaljson`](#globaljson)       |              | <span data-ttu-id="8d758-246">構成</span><span class="sxs-lookup"><span data-stu-id="8d758-246">Config</span></span>                                | <span data-ttu-id="8d758-247">2.0</span><span class="sxs-lookup"><span data-stu-id="8d758-247">2.0</span></span>        |
| <span data-ttu-id="8d758-248">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="8d758-248">NuGet Config</span></span>                                 | `nugetconfig`                     |              | <span data-ttu-id="8d758-249">構成</span><span class="sxs-lookup"><span data-stu-id="8d758-249">Config</span></span>                                | <span data-ttu-id="8d758-250">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-250">1.0</span></span>        |
| <span data-ttu-id="8d758-251">dotnet ローカル ツール マニフェスト ファイル</span><span class="sxs-lookup"><span data-stu-id="8d758-251">Dotnet local tool manifest file</span></span>              | `tool-manifest`                   |              | <span data-ttu-id="8d758-252">構成</span><span class="sxs-lookup"><span data-stu-id="8d758-252">Config</span></span>                                | <span data-ttu-id="8d758-253">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-253">3.0</span></span>        |
| <span data-ttu-id="8d758-254">Web 構成</span><span class="sxs-lookup"><span data-stu-id="8d758-254">Web Config</span></span>                                   | `webconfig`                       |              | <span data-ttu-id="8d758-255">構成</span><span class="sxs-lookup"><span data-stu-id="8d758-255">Config</span></span>                                | <span data-ttu-id="8d758-256">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-256">1.0</span></span>        |
| <span data-ttu-id="8d758-257">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="8d758-257">Solution File</span></span>                                | `sln`                             |              | <span data-ttu-id="8d758-258">ソリューション</span><span class="sxs-lookup"><span data-stu-id="8d758-258">Solution</span></span>                              | <span data-ttu-id="8d758-259">1.0</span><span class="sxs-lookup"><span data-stu-id="8d758-259">1.0</span></span>        |
| <span data-ttu-id="8d758-260">プロトコル バッファー ファイル</span><span class="sxs-lookup"><span data-stu-id="8d758-260">Protocol Buffer File</span></span>                         | [`proto`](#namespace)             |              | <span data-ttu-id="8d758-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="8d758-261">Web/gRPC</span></span>                              | <span data-ttu-id="8d758-262">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-262">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="8d758-263">オプション</span><span class="sxs-lookup"><span data-stu-id="8d758-263">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="8d758-264">指定されたコマンドが実行されてテンプレートが作成された場合に起きることの概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-264">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="8d758-265">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-265">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="8d758-266">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-266">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8d758-267">これは、選択されたテンプレートによって出力ディレクトリ内の既存のファイルがオーバーライドされる場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="8d758-267">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8d758-268">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="8d758-268">Prints out help for the command.</span></span> <span data-ttu-id="8d758-269">`dotnet new` コマンド自体、または任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8d758-269">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="8d758-270">たとえば、`dotnet new mvc --help` のようにします。</span><span class="sxs-lookup"><span data-stu-id="8d758-270">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="8d758-271">指定された `PATH` または `NUGET_ID` からテンプレート パックがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8d758-271">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8d758-272">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d758-272">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="8d758-273">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="8d758-273">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="8d758-274">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d758-274">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="8d758-275">このコマンドの実行時にテンプレートのバージョンが既にインストールされていたら、テンプレートは指定されたバージョンか、最新の安定したバージョン (バージョンが指定されていない場合) に更新されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-275">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="8d758-276">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d758-276">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="8d758-277">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8d758-277">Lists templates containing the specified name.</span></span> <span data-ttu-id="8d758-278">名前が指定されていない場合、すべてのテンプレートが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-278">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="8d758-279">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="8d758-279">The language of the template to create.</span></span> <span data-ttu-id="8d758-280">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8d758-280">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8d758-281">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="8d758-281">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8d758-282">一部のシェルは `#` を特殊文字として解釈します。</span><span class="sxs-lookup"><span data-stu-id="8d758-282">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="8d758-283">そのような場合は、言語パラメーター値を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="8d758-283">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="8d758-284">たとえば、`dotnet new console -lang "F#"` のようにします。</span><span class="sxs-lookup"><span data-stu-id="8d758-284">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="8d758-285">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="8d758-285">The name for the created output.</span></span> <span data-ttu-id="8d758-286">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-286">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="8d758-287">インストール中に使用する NuGet ソースを 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="8d758-287">Specifies a NuGet source to use during install.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="8d758-288">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="8d758-288">Location to place the generated output.</span></span> <span data-ttu-id="8d758-289">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="8d758-289">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="8d758-290">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="8d758-290">Filters templates based on available types.</span></span> <span data-ttu-id="8d758-291">事前定義されている値は `project` および `item` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-291">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="8d758-292">指定された `PATH` または `NUGET_ID` でテンプレート パックがアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8d758-292">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8d758-293">`<PATH|NUGET_ID>` 値が指定されないと、現在インストールされているすべてのテンプレート パックとそれらに関連付けられているテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-293">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="8d758-294">`NUGET_ID` を指定した場合、バージョン番号は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="8d758-294">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="8d758-295">このオプションにパラメーターを指定しないと、コマンドによって、インストールされたテンプレートとそれらに関する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-295">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8d758-296">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d758-296">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8d758-297">たとえば、*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、 *./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="8d758-297">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="8d758-298">テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="8d758-298">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="8d758-299">現在インストールされているテンプレート パックに利用できる更新プログラムがあるかどうか確認され、それらがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8d758-299">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="8d758-300">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-300">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="8d758-301">現在インストールされているテンプレート パックに利用できる更新プログラムがあるかどうか確認されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-301">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="8d758-302">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-302">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="8d758-303">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="8d758-303">Template options</span></span>

<span data-ttu-id="8d758-304">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d758-304">Each project template may have additional options available.</span></span> <span data-ttu-id="8d758-305">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="8d758-305">The core templates have the following additional options:</span></span>

### `console`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-306">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-306">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-307">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-307">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="8d758-308">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-308">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-309">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-309">SDK version</span></span> | <span data-ttu-id="8d758-310">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-310">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-311">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-311">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-312">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-312">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8d758-313">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-313">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="8d758-314">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-314">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="8d758-315">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="8d758-315">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="8d758-316">F# に対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8d758-316">Not supported for F#.</span></span> <span data-ttu-id="8d758-317">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-317">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8d758-318">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d758-318">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-319">指定した場合、プロジェクトの作成中には暗黙的な復元が実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-319">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="8d758-320">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-320">Available since .NET Core 2.2 SDK.</span></span>

***

### `classlib`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-321">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-321">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-322">値: .NET クラス ライブラリを作成するには `net5.0` または `netcoreapp<version>`、.NET Standard クラス ライブラリを作成するには `netstandard<version>`。</span><span class="sxs-lookup"><span data-stu-id="8d758-322">Values: `net5.0` or `netcoreapp<version>` to create a .NET Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8d758-323">.NET 5.0 SDK の既定値は `net5.0` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-323">The default value for .NET 5.0 SDK is `net5.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="8d758-324">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-324">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="8d758-325">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="8d758-325">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="8d758-326">F# に対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8d758-326">Not supported for F#.</span></span> <span data-ttu-id="8d758-327">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-327">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8d758-328">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d758-328">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-329">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-329">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="8d758-330">`wpf`, `wpflib`, `wpfcustomcontrollib`, `wpfusercontrollib`</span><span class="sxs-lookup"><span data-stu-id="8d758-330">`wpf`, `wpflib`, `wpfcustomcontrollib`, `wpfusercontrollib`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-331">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-332">既定値は `net5.0` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-332">The default value is `net5.0`.</span></span> <span data-ttu-id="8d758-333">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-333">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="8d758-334">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-334">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="8d758-335">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="8d758-335">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="8d758-336">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d758-336">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-337">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-337">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="8d758-338">`winforms`, `winformslib`</span><span class="sxs-lookup"><span data-stu-id="8d758-338">`winforms`, `winformslib`</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="8d758-339">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="8d758-340">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="8d758-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="8d758-341">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d758-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-342">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-342">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="8d758-343">`worker`, `grpc`</span><span class="sxs-lookup"><span data-stu-id="8d758-343">`worker`, `grpc`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-344">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-344">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-345">既定値は `netcoreapp3.1` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-345">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="8d758-346">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-346">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8d758-347">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-347">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-348">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-348">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="8d758-349">`mstest`, `xunit`</span><span class="sxs-lookup"><span data-stu-id="8d758-349">`mstest`, `xunit`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-350">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-350">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-351">.NET Core 3.0 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="8d758-351">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="8d758-352">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-352">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-353">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-353">SDK version</span></span> | <span data-ttu-id="8d758-354">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-354">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-355">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-355">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-356">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-356">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8d758-357">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-357">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="8d758-358">[dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化が有効化されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-358">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-359">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-359">Doesn't execute an implicit restore during project creation.</span></span>

***

### `nunit`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-360">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-360">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="8d758-361">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-361">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-362">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-362">SDK version</span></span> | <span data-ttu-id="8d758-363">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-363">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-364">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-364">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-365">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-365">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8d758-366">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-366">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8d758-367">2.2</span><span class="sxs-lookup"><span data-stu-id="8d758-367">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="8d758-368">2.1</span><span class="sxs-lookup"><span data-stu-id="8d758-368">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="8d758-369">[dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化が有効化されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-369">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-370">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### `page`

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="8d758-371">生成されるコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="8d758-371">Namespace for the generated code.</span></span> <span data-ttu-id="8d758-372">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-372">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="8d758-373">PageModel なしでページが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-373">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="8d758-374">`viewimports`, `proto`</span><span class="sxs-lookup"><span data-stu-id="8d758-374">`viewimports`, `proto`</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="8d758-375">生成されるコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="8d758-375">Namespace for the generated code.</span></span> <span data-ttu-id="8d758-376">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-376">The default value is `MyApp.Namespace`.</span></span>

***

### `blazorserver`

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="8d758-377">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8d758-377">The type of authentication to use.</span></span> <span data-ttu-id="8d758-378">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-378">The possible values are:</span></span>

  - <span data-ttu-id="8d758-379">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="8d758-379">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8d758-380">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="8d758-380">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="8d758-381">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-381">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="8d758-382">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-382">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="8d758-383">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="8d758-383">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="8d758-384">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-384">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="8d758-385">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8d758-385">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8d758-386">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-386">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-387">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-387">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="8d758-388">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-388">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8d758-389">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-389">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="8d758-390">このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-390">The reset password policy ID for this project.</span></span> <span data-ttu-id="8d758-391">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-391">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="8d758-392">このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-392">The edit profile policy ID for this project.</span></span> <span data-ttu-id="8d758-393">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-393">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="8d758-394">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="8d758-394">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8d758-395">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-395">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8d758-396">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-396">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="8d758-397">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-397">The Client ID for this project.</span></span> <span data-ttu-id="8d758-398">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-398">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8d758-399">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-399">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="8d758-400">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="8d758-400">The domain for the directory tenant.</span></span> <span data-ttu-id="8d758-401">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-401">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-402">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-402">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="8d758-403">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-403">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8d758-404">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-404">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d758-405">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-405">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="8d758-406">リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="8d758-406">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8d758-407">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-407">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-408">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-408">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="8d758-409">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="8d758-409">Allows this application read-access to the directory.</span></span> <span data-ttu-id="8d758-410">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-410">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8d758-411">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-411">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="8d758-412">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="8d758-412">Turns off HTTPS.</span></span> <span data-ttu-id="8d758-413">このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が `--auth` 用に使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-413">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8d758-414">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-414">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d758-415">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-415">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-416">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-416">Doesn't execute an implicit restore during project creation.</span></span>

***

### `blazorwasm`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-417">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-417">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="8d758-418">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-418">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-419">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-419">SDK version</span></span> | <span data-ttu-id="8d758-420">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-420">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-421">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-421">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-422">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-422">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="8d758-423">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-423">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="8d758-424">Blazor WebAssembly アプリ用の ASP.NET Core ホストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8d758-424">Includes an ASP.NET Core host for the Blazor WebAssembly app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="8d758-425">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8d758-425">The type of authentication to use.</span></span> <span data-ttu-id="8d758-426">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-426">The possible values are:</span></span>

  - <span data-ttu-id="8d758-427">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="8d758-427">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8d758-428">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="8d758-428">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="8d758-429">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-429">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="8d758-430">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-430">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="8d758-431">OIDC プロバイダーの機関。</span><span class="sxs-lookup"><span data-stu-id="8d758-431">The authority of the OIDC provider.</span></span> <span data-ttu-id="8d758-432">`Individual` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-432">Use with `Individual` authentication.</span></span> <span data-ttu-id="8d758-433">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-433">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="8d758-434">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8d758-434">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8d758-435">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-435">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-436">既定値は `https://aadB2CInstance.b2clogin.com/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-436">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="8d758-437">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-437">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8d758-438">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-438">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="8d758-439">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="8d758-439">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8d758-440">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d758-441">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-441">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="8d758-442">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-442">The Client ID for this project.</span></span> <span data-ttu-id="8d758-443">スタンドアロンのシナリオで、`IndividualB2C`、`SingleOrg`、または `Individual` 認証と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-443">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="8d758-444">既定値は `33333333-3333-3333-33333333333333333` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-444">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="8d758-445">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="8d758-445">The domain for the directory tenant.</span></span> <span data-ttu-id="8d758-446">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-446">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-447">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-447">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="8d758-448">呼び出すサーバー API のアプリ ID URI。</span><span class="sxs-lookup"><span data-stu-id="8d758-448">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="8d758-449">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-449">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-450">既定値は `api.id.uri` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-450">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="8d758-451">サーバーでホストされる API のクライアント ID。</span><span class="sxs-lookup"><span data-stu-id="8d758-451">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="8d758-452">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-452">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-453">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-453">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="8d758-454">アクセス トークンをプロビジョニングするためにクライアントが要求する必要のある API スコープ。</span><span class="sxs-lookup"><span data-stu-id="8d758-454">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="8d758-455">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-455">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-456">既定値は `user_impersonation` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-456">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="8d758-457">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-457">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8d758-458">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-458">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d758-459">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-459">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="8d758-460">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="8d758-460">Allows this application read-access to the directory.</span></span> <span data-ttu-id="8d758-461">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-461">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8d758-462">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-462">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="8d758-463">インストールとオフライン使用をサポートするプログレッシブ Web アプリケーション (PWA) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-463">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="8d758-464">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="8d758-464">Turns off HTTPS.</span></span> <span data-ttu-id="8d758-465">このオプションは、`Individual`、`IndividualB2C`、または `SingleOrg` が `--auth` 用に使用されていない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-465">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8d758-466">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-466">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d758-467">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-467">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="8d758-468">Web アプリから呼び出すための API の URL。</span><span class="sxs-lookup"><span data-stu-id="8d758-468">URL of the API to call from the web app.</span></span> <span data-ttu-id="8d758-469">ASP.NET Core ホストが指定されていない `SingleOrg` または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-469">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="8d758-470">既定値は `https://graph.microsoft.com/v1.0/me` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-470">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="8d758-471">Web アプリによって Microsoft Graph が呼び出されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8d758-471">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="8d758-472">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-472">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="8d758-473">Web アプリから API を呼び出すように要求するスコープ。</span><span class="sxs-lookup"><span data-stu-id="8d758-473">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="8d758-474">ASP.NET Core ホストが指定されていない `SingleOrg` または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-474">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="8d758-475">既定値は、`user.read` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-475">The default is `user.read`.</span></span>

***

### `web`

- **`--exclude-launch-settings`**

  <span data-ttu-id="8d758-476">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-476">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-477">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-477">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-478">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8d758-478">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8d758-479">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-479">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-480">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-480">SDK version</span></span> | <span data-ttu-id="8d758-481">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-481">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-482">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-482">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-483">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-483">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8d758-484">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-484">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8d758-485">2.1</span><span class="sxs-lookup"><span data-stu-id="8d758-485">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="8d758-486">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-486">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="8d758-487">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="8d758-487">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="8d758-488">`mvc`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="8d758-488">`mvc`, `webapp`</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="8d758-489">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8d758-489">The type of authentication to use.</span></span> <span data-ttu-id="8d758-490">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-490">The possible values are:</span></span>

  - <span data-ttu-id="8d758-491">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="8d758-491">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8d758-492">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="8d758-492">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="8d758-493">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-493">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="8d758-494">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-494">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="8d758-495">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="8d758-495">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="8d758-496">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-496">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="8d758-497">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8d758-497">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8d758-498">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-498">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-499">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-499">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="8d758-500">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-500">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8d758-501">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-501">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="8d758-502">このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-502">The reset password policy ID for this project.</span></span> <span data-ttu-id="8d758-503">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-503">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="8d758-504">このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-504">The edit profile policy ID for this project.</span></span> <span data-ttu-id="8d758-505">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-505">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="8d758-506">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="8d758-506">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8d758-507">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-507">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8d758-508">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-508">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="8d758-509">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-509">The Client ID for this project.</span></span> <span data-ttu-id="8d758-510">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-510">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8d758-511">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-511">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="8d758-512">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="8d758-512">The domain for the directory tenant.</span></span> <span data-ttu-id="8d758-513">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-513">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-514">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-514">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="8d758-515">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-515">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8d758-516">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-516">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d758-517">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-517">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="8d758-518">リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="8d758-518">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8d758-519">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-520">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-520">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="8d758-521">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="8d758-521">Allows this application read-access to the directory.</span></span> <span data-ttu-id="8d758-522">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-522">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8d758-523">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-523">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="8d758-524">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="8d758-524">Turns off HTTPS.</span></span> <span data-ttu-id="8d758-525">このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-525">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8d758-526">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-526">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d758-527">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-527">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-528">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-529">.NET Core 3.0 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="8d758-529">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="8d758-530">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-531">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-531">SDK version</span></span> | <span data-ttu-id="8d758-532">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-533">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-533">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-534">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8d758-535">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-535">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="8d758-536">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="8d758-537">プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="8d758-537">Includes BrowserLink in the project.</span></span> <span data-ttu-id="8d758-538">.NET Core 2.2 および 3.1 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8d758-538">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="8d758-539">デバッグ ビルドで [Razor ランタイム コンパイル](/aspnet/core/mvc/views/view-compilation#runtime-compilation)を使用するようにプロジェクトが構成されているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="8d758-539">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="8d758-540">.NET Core 3.1.201 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="8d758-540">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="8d758-541">`angular`, `react`</span><span class="sxs-lookup"><span data-stu-id="8d758-541">`angular`, `react`</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="8d758-542">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8d758-542">The type of authentication to use.</span></span> <span data-ttu-id="8d758-543">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-543">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="8d758-544">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-544">The possible values are:</span></span>

  - <span data-ttu-id="8d758-545">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="8d758-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8d758-546">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="8d758-546">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8d758-547">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-547">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d758-548">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-548">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="8d758-549">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="8d758-549">Turns off HTTPS.</span></span> <span data-ttu-id="8d758-550">このオプションは、認証が `None` の場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-550">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8d758-551">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-551">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d758-552">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-552">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-553">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-553">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-554">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-554">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-555">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8d758-555">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8d758-556">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-556">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-557">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-557">SDK version</span></span> | <span data-ttu-id="8d758-558">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-558">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-559">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-559">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-560">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-560">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8d758-561">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-561">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8d758-562">2.1</span><span class="sxs-lookup"><span data-stu-id="8d758-562">2.1</span></span>         | `netcoreapp2.0` |

***

### `reactredux`

- **`--exclude-launch-settings`**

  <span data-ttu-id="8d758-563">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-563">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-564">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-564">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-565">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8d758-565">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8d758-566">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-566">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-567">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-567">SDK version</span></span> | <span data-ttu-id="8d758-568">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-568">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-569">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-569">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-570">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-570">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8d758-571">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-571">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8d758-572">2.1</span><span class="sxs-lookup"><span data-stu-id="8d758-572">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="8d758-573">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-573">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="8d758-574">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="8d758-574">Turns off HTTPS.</span></span>

***

### `razorclasslib`

- **`--no-restore`**

  <span data-ttu-id="8d758-575">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-575">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="8d758-576">このライブラリへのコンポーネントに加え、従来の Razor ページとビューの追加がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8d758-576">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="8d758-577">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-577">Available since .NET Core 3.0 SDK.</span></span>

***
  
### `webapi`

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="8d758-578">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8d758-578">The type of authentication to use.</span></span> <span data-ttu-id="8d758-579">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8d758-579">The possible values are:</span></span>

  - <span data-ttu-id="8d758-580">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="8d758-580">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8d758-581">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-581">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="8d758-582">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-582">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="8d758-583">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="8d758-583">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="8d758-584">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8d758-584">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8d758-585">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-585">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8d758-586">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-586">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="8d758-587">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-587">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8d758-588">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-588">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="8d758-589">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="8d758-589">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8d758-590">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-590">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d758-591">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-591">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="8d758-592">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-592">The Client ID for this project.</span></span> <span data-ttu-id="8d758-593">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-593">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8d758-594">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-594">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="8d758-595">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="8d758-595">The domain for the directory tenant.</span></span> <span data-ttu-id="8d758-596">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-596">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8d758-597">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-597">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="8d758-598">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="8d758-598">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8d758-599">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8d758-599">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8d758-600">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="8d758-600">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="8d758-601">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="8d758-601">Allows this application read-access to the directory.</span></span> <span data-ttu-id="8d758-602">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-602">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8d758-603">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="8d758-604">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="8d758-604">Turns off HTTPS.</span></span> <span data-ttu-id="8d758-605">`app.UseHsts` と `app.UseHttpsRedirection` は `Startup.Configure` に追加されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-605">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="8d758-606">このオプションは、`IndividualB2C` または `SingleOrg` が認証用に使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-606">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8d758-607">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8d758-608">`IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-608">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d758-609">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-609">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8d758-610">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8d758-610">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8d758-611">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d758-611">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8d758-612">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="8d758-612">SDK version</span></span> | <span data-ttu-id="8d758-613">既定値</span><span class="sxs-lookup"><span data-stu-id="8d758-613">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8d758-614">5.0</span><span class="sxs-lookup"><span data-stu-id="8d758-614">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="8d758-615">3.1</span><span class="sxs-lookup"><span data-stu-id="8d758-615">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8d758-616">3.0</span><span class="sxs-lookup"><span data-stu-id="8d758-616">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8d758-617">2.1</span><span class="sxs-lookup"><span data-stu-id="8d758-617">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="8d758-618">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8d758-618">Doesn't execute an implicit restore during project creation.</span></span>

***

### `globaljson`

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="8d758-619">*global.json* ファイル内で使用する .NET SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="8d758-619">Specifies the version of the .NET SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="8d758-620">使用例</span><span class="sxs-lookup"><span data-stu-id="8d758-620">Examples</span></span>

- <span data-ttu-id="8d758-621">テンプレート名を指定することによって、C# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d758-621">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="8d758-622">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d758-622">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="8d758-623">指定されたディレクトリ内に .NET Standard クラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-623">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="8d758-624">認証なしで、現在のディレクトリに新しい ASP.NET Core C# MVC プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d758-624">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="8d758-625">新しい xUnit プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d758-625">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="8d758-626">シングル ページ アプリケーション (SPA) テンプレートに使用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8d758-626">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="8d758-627">部分文字列 *we* に一致するすべてのテンプレートの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="8d758-627">List all templates matching the *we* substring.</span></span> <span data-ttu-id="8d758-628">完全一致が見つからないので、短い名前と名前の両方の列に対して部分文字列一致が実行されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-628">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="8d758-629">*ng* に一致するテンプレートの呼び出しを試みます。</span><span class="sxs-lookup"><span data-stu-id="8d758-629">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="8d758-630">一致が 1 つだけでない場合、部分的に一致するテンプレートの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="8d758-630">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="8d758-631">ASP.NET Core 用の SPA テンプレートのバージョン 2.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8d758-631">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="8d758-632">インストールされているテンプレートとそれらに関する詳細や、それらのアンインストール方法を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8d758-632">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="8d758-633">現在のディレクトリに *global.json* が作成され、SDK バージョンが 3.1.101 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d758-633">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="8d758-634">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d758-634">See also</span></span>

- [<span data-ttu-id="8d758-635">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="8d758-635">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="8d758-636">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="8d758-636">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="8d758-637">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="8d758-637">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="8d758-638">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="8d758-638">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
