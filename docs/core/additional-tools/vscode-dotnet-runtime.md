---
title: VS Code 拡張機能作成者用の .NET インストール ツール
description: 拡張機能の作成者用の .NET インストール ツールの概要 (.NET ランタイムをインストールするための Visual Studio Code 拡張機能)。
author: sfoslund
ms.date: 11/18/2020
ms.openlocfilehash: a372d0cc728956920d013dac9bc0da1bcd3edc0b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872991"
---
# <a name="net-install-tool-for-extension-authors"></a><span data-ttu-id="141d7-103">拡張機能作成者用の .NET インストール ツール</span><span class="sxs-lookup"><span data-stu-id="141d7-103">.NET install tool for extension authors</span></span>

<span data-ttu-id="141d7-104">[拡張機能作成者用の .NET インストール ツール](https://github.com/dotnet/vscode-dotnet-runtime)は、VS Code 拡張機能作成者専用の .NET ランタイムを入手できる、Visual Studio Code の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="141d7-104">The [.NET install tool for extension authors](https://github.com/dotnet/vscode-dotnet-runtime) is a Visual Studio Code extension that allows acquisition of the .NET runtime specifically for VS Code extension authors.</span></span> <span data-ttu-id="141d7-105">このツールは、.NET で記述された拡張機能での利用を目的としており、拡張機能の一部 (言語サーバーなど) を起動するために .NET を必要とします。</span><span class="sxs-lookup"><span data-stu-id="141d7-105">This tool is intended to be leveraged in extensions that are written in .NET and require .NET to boot pieces of the extension (for example, a language server).</span></span> <span data-ttu-id="141d7-106">この拡張機能は、開発用の .NET をインストールするためにユーザーが直接使用することは意図されていません。</span><span class="sxs-lookup"><span data-stu-id="141d7-106">The extension is not intended to be used directly by users to install .NET for development.</span></span>

## <a name="getting-started-extension-authors"></a><span data-ttu-id="141d7-107">はじめに: 拡張機能作成者</span><span class="sxs-lookup"><span data-stu-id="141d7-107">Getting started: extension authors</span></span>

<span data-ttu-id="141d7-108">拡張機能作成者用の .NET インストール ツールがお客様のシナリオに適していることを確認するには、まず、Microsoft の GitHub ページで[この拡張機能の目標](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="141d7-108">To ensure that the .NET install tool for extension authors is the right fit for your scenario, start by reviewing the [goals of this extension](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) on our GitHub page.</span></span>

> [!NOTE]
> <span data-ttu-id="141d7-109">このツールは .NET ランタイムをインストールするためにのみ使用できます。現時点では、.NET SDK をインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="141d7-109">This tool can be used to install the .NET runtime only, it currently does not have the capability to install the .NET SDK.</span></span>

<span data-ttu-id="141d7-110">拡張機能作成者用の .NET インストール ツールがお客様のニーズに適していることを確認したら、[拡張機能マニフェスト](https://code.visualstudio.com/api/references/extension-manifest)でそれに対する依存関係を設定し、[VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command) で公開されているコマンドの使用を開始できます。</span><span class="sxs-lookup"><span data-stu-id="141d7-110">Once you have verified that the .NET install tool for extension authors fits your needs, you can take a dependency on it in your [extension manifest](https://code.visualstudio.com/api/references/extension-manifest) and begin using the commands we expose with the [VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command).</span></span> <span data-ttu-id="141d7-111">この拡張機能によって公開されているコマンドの一覧については、Microsoft の [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/main/Documentation/commands.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="141d7-111">You can find the list of commands this extension exposes on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/main/Documentation/commands.md).</span></span>

<span data-ttu-id="141d7-112">これらの手順を実際に確認するには、こちらの[サンプル拡張機能](https://github.com/dotnet/vscode-dotnet-runtime/tree/main/sample)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="141d7-112">Check out this [sample extension](https://github.com/dotnet/vscode-dotnet-runtime/tree/main/sample) to see these steps in action.</span></span>

<span data-ttu-id="141d7-113">その他の例については、現在このツールが利用されている次のオープンソースの拡張機能を確認してください。</span><span class="sxs-lookup"><span data-stu-id="141d7-113">For more examples, check out these open source extensions that currently leverage this tool:</span></span>

- [<span data-ttu-id="141d7-114">Visual Studio Code 用 Azure Resource Manager (ARM) ツール</span><span class="sxs-lookup"><span data-stu-id="141d7-114">Azure Resource Manager (ARM) Tools for Visual Studio Code</span></span>](https://github.com/microsoft/vscode-azurearmtools)

- [<span data-ttu-id="141d7-115">.NET Interactive Notebooks</span><span class="sxs-lookup"><span data-stu-id="141d7-115">.NET Interactive Notebooks</span></span>](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a><span data-ttu-id="141d7-116">はじめに: エンド ユーザー</span><span class="sxs-lookup"><span data-stu-id="141d7-116">Getting started: end users</span></span>

<span data-ttu-id="141d7-117">一般に、エンド ユーザーは、拡張機能作成者用の .NET インストール ツールを操作する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="141d7-117">In general, the end user should not need to interact with the .NET install tool for extension authors at all.</span></span> <span data-ttu-id="141d7-118">拡張機能に関する問題が発生した場合は、Microsoft の[トラブルシューティング ページ](https://github.com/dotnet/vscode-dotnet-runtime/blob/main/Documentation/troubleshooting-runtime.md)を確認するか、[GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues) でイシューを報告してください。</span><span class="sxs-lookup"><span data-stu-id="141d7-118">If you are having problems with the extension, check out our [troubleshooting page](https://github.com/dotnet/vscode-dotnet-runtime/blob/main/Documentation/troubleshooting-runtime.md) or file an issue on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues).</span></span>
