---
title: .NET Core 3.1 の新機能
description: .NET Core 3.1 の新機能について説明します。
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 8d086c5c595197894e01a347f82b2c6341263fc5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104966"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="85371-103">.NET Core 3.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="85371-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="85371-104">この記事では、.NET Core 3.1 の新機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="85371-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="85371-105">このリリースには、小規模であるが重要な修正に重点を置いた .NET Core 3.0 のマイナー機能強化が含まれています。</span><span class="sxs-lookup"><span data-stu-id="85371-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="85371-106">.NET Core 3.1 に関する最も重要な機能は、[長期的なサポート (LTS)](#long-term-support) リリースであるということです。</span><span class="sxs-lookup"><span data-stu-id="85371-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="85371-107">Visual Studio 2019 を使用している場合は、.NET Core 3.1 プロジェクトで使用できるように [Visual Studio 2019 バージョン 16.4 以降](https://visualstudio.microsoft.com/downloads/) に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85371-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="85371-108">Visual Studio 16.4 の新機能の詳細については、[Visual Studio 2019 バージョン 16.4 の新機能](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="85371-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="85371-109">Visual Studio for Mac でも .NET Core 3.1 がサポートされており、Visual Studio for Mac 8.4 に含まれています。</span><span class="sxs-lookup"><span data-stu-id="85371-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="85371-110">リリースの詳細については、「[.NET Core 3.1 についてのお知らせ](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85371-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="85371-111">Windows、macOS、または Linux 上に [.NET Core 3.1 をダウンロードして使い始めましょう](https://dotnet.microsoft.com/download/dotnet/3.1)。</span><span class="sxs-lookup"><span data-stu-id="85371-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="85371-112">長期的なサポート</span><span class="sxs-lookup"><span data-stu-id="85371-112">Long-term support</span></span>

<span data-ttu-id="85371-113">.NET Core 3.1 は、次の 3 年間にわたって Microsoft のサポートが提供される LTS リリースです。</span><span class="sxs-lookup"><span data-stu-id="85371-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="85371-114">アプリを .NET Core 3.1 に移行することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="85371-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="85371-115">他のメジャー リリースの現在のライフサイクルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="85371-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="85371-116">リリース</span><span class="sxs-lookup"><span data-stu-id="85371-116">Release</span></span> | <span data-ttu-id="85371-117">メモ</span><span class="sxs-lookup"><span data-stu-id="85371-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="85371-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="85371-118">.NET Core 3.0</span></span> | <span data-ttu-id="85371-119">2020 年 3 月 3 日にサポートが終了します。</span><span class="sxs-lookup"><span data-stu-id="85371-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="85371-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="85371-120">.NET Core 2.2</span></span> | <span data-ttu-id="85371-121">2019 年 12 月 23 日にサポートが終了します。</span><span class="sxs-lookup"><span data-stu-id="85371-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="85371-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="85371-122">.NET Core 2.1</span></span> | <span data-ttu-id="85371-123">2021 年 8 月 21 日にサポートが終了します。</span><span class="sxs-lookup"><span data-stu-id="85371-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="85371-124">詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="85371-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="85371-125">macOS appHost と公証</span><span class="sxs-lookup"><span data-stu-id="85371-125">macOS appHost and notarization</span></span>

<span data-ttu-id="85371-126">*macOS のみ*</span><span class="sxs-lookup"><span data-stu-id="85371-126">*macOS only*</span></span>

<span data-ttu-id="85371-127">macOS の公証を受けた .NET Core SDK 3.1 以降では、appHost の設定は既定で無効です。</span><span class="sxs-lookup"><span data-stu-id="85371-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="85371-128">詳細については、「[macOS Catalina の公証と .NET Core のダウンロードとプロジェクトへの影響](../install/macos-notarization-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85371-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="85371-129">appHost 設定が有効な場合、ビルド時または発行時に .NET Core によってネイティブの Mach-O 実行可能ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="85371-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="85371-130">`dotnet run` コマンドを使用してソース コードから実行するか、Mach-O 実行可能ファイルを直接起動すると、アプリは appHost のコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="85371-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="85371-131">appHost を使用しない場合、ユーザーが[フレームワークに依存する](../deploying/index.md#publish-framework-dependent)アプリを起動できる唯一の方法は、`dotnet <filename.dll>` コマンドを使用することです。</span><span class="sxs-lookup"><span data-stu-id="85371-131">Without the appHost, the only way a user can start a [framework-dependent](../deploying/index.md#publish-framework-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="85371-132">[自己完結型](../deploying/index.md#publish-self-contained)のアプリを発行すると、常に appHost が作成されます。</span><span class="sxs-lookup"><span data-stu-id="85371-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="85371-133">プロジェクト レベルで appHost を構成するか、`-p:UseAppHost` パラメーターを使用して特定の `dotnet` コマンドの appHost を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="85371-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="85371-134">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="85371-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="85371-135">コマンド ライン パラメーター</span><span class="sxs-lookup"><span data-stu-id="85371-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="85371-136">`UseAppHost` 設定の詳細については、[Microsoft.NET.Sdk の MSBuild プロパティ](../project-sdk/msbuild-props.md#useapphost)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85371-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="85371-137">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="85371-137">Windows Forms</span></span>

<span data-ttu-id="85371-138">*Windows のみ*</span><span class="sxs-lookup"><span data-stu-id="85371-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="85371-139">Windows フォームで破壊的変更が行われています。</span><span class="sxs-lookup"><span data-stu-id="85371-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="85371-140">Windows フォームには、Visual Studio Designer Toolbox でしばらくの間利用できなくなっているレガシ コントロールが含まれていました。</span><span class="sxs-lookup"><span data-stu-id="85371-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="85371-141">これらは、.NET Framework 2.0 の新しいコントロールに置き換えられていました。</span><span class="sxs-lookup"><span data-stu-id="85371-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="85371-142">これらは、Desktop SDK for .NET Core 3.1. から削除されています。</span><span class="sxs-lookup"><span data-stu-id="85371-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="85371-143">削除されたコントロール</span><span class="sxs-lookup"><span data-stu-id="85371-143">Removed control</span></span> | <span data-ttu-id="85371-144">推奨代替</span><span class="sxs-lookup"><span data-stu-id="85371-144">Recommended replacement</span></span> | <span data-ttu-id="85371-145">削除された関連 API</span><span class="sxs-lookup"><span data-stu-id="85371-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="85371-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="85371-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="85371-147">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="85371-147">DataGridCell</span></span><br/><span data-ttu-id="85371-148">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="85371-148">DataGridRow</span></span><br/><span data-ttu-id="85371-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="85371-149">DataGridTableCollection</span></span><br/><span data-ttu-id="85371-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="85371-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="85371-151">DataGridTableStyle</span><span class="sxs-lookup"><span data-stu-id="85371-151">DataGridTableStyle</span></span><br/><span data-ttu-id="85371-152">DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="85371-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="85371-153">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="85371-153">DataGridLineStyle</span></span><br/><span data-ttu-id="85371-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="85371-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="85371-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="85371-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="85371-156">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="85371-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="85371-157">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="85371-157">DataGridTextBox</span></span><br/><span data-ttu-id="85371-158">GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="85371-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="85371-159">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="85371-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="85371-160">HitTestType</span><span class="sxs-lookup"><span data-stu-id="85371-160">HitTestType</span></span> |
| <span data-ttu-id="85371-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="85371-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="85371-162">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="85371-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="85371-163">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="85371-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="85371-164">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="85371-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="85371-165">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="85371-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="85371-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="85371-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="85371-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="85371-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="85371-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="85371-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="85371-169">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="85371-169">MenuItemCollection</span></span> |
| <span data-ttu-id="85371-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="85371-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="85371-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="85371-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="85371-172">アプリケーションを .NET Core 3.1 に更新し、コントロールの置き換えを行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="85371-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="85371-173">コントロールの置き換えは、基本的には型の "検索と置換" という単純なプロセスです。</span><span class="sxs-lookup"><span data-stu-id="85371-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="85371-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="85371-174">C++/CLI</span></span>

<span data-ttu-id="85371-175">*Windows のみ*</span><span class="sxs-lookup"><span data-stu-id="85371-175">*Windows only*</span></span>

<span data-ttu-id="85371-176">C++/CLI (別名 "マネージド C++") プロジェクトを作成するためのサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="85371-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="85371-177">これらのプロジェクトから生成されるバイナリは、.NET Core 3.0 以降のバージョンと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="85371-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="85371-178">Visual Studio 2019 バージョン 16.4 に C++/CLI のサポートを追加するには、[C++ ワークロードを使用するデスクトップ開発](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="85371-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="85371-179">このワークロードによって、次の 2 つのテンプレートが Visual Studio に追加されます。</span><span class="sxs-lookup"><span data-stu-id="85371-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="85371-180">CLR クラス ライブラリ (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="85371-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="85371-181">CLR 空のプロジェクト (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="85371-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="85371-182">次の手順</span><span class="sxs-lookup"><span data-stu-id="85371-182">Next steps</span></span>

- [<span data-ttu-id="85371-183">.NET Core 3.0 と 3.1 の間の破壊的変更を確認する</span><span class="sxs-lookup"><span data-stu-id="85371-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.1.md)
- [<span data-ttu-id="85371-184">Windows フォーム アプリ用の .NET Core 3.1 における破壊的変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="85371-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
