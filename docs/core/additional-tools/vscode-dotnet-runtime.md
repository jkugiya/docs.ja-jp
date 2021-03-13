---
title: VS Code 拡張機能作成者用の .NET インストール ツール
description: 拡張機能の作成者用の .NET インストール ツールの概要 (.NET ランタイムをインストールするための Visual Studio Code 拡張機能)。
author: sfoslund
ms.date: 11/18/2020
ms.openlocfilehash: 4be931a254e4ce969f9eaf2efde7939cb54e1d5f
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605153"
---
# <a name="net-install-tool-for-extension-authors"></a>拡張機能作成者用の .NET インストール ツール

[拡張機能作成者用の .NET インストール ツール](https://github.com/dotnet/vscode-dotnet-runtime)は、VS Code 拡張機能作成者専用の .NET ランタイムを入手できる、Visual Studio Code の拡張機能です。 このツールは、.NET で記述された拡張機能での利用を目的としており、拡張機能の一部 (言語サーバーなど) を起動するために .NET を必要とします。 この拡張機能は、開発用の .NET をインストールするためにユーザーが直接使用することは意図されていません。

## <a name="getting-started-extension-authors"></a>はじめに: 拡張機能作成者

拡張機能作成者用の .NET インストール ツールがお客様のシナリオに適していることを確認するには、まず、Microsoft の GitHub ページで[この拡張機能の目標](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions)を確認してください。

> [!NOTE]
> このツールは .NET ランタイムをインストールするためにのみ使用できます。現時点では、.NET SDK をインストールすることはできません。

拡張機能作成者用の .NET インストール ツールがお客様のニーズに適していることを確認したら、[拡張機能マニフェスト](https://code.visualstudio.com/api/references/extension-manifest)でそれに対する依存関係を設定し、[VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command) で公開されているコマンドの使用を開始できます。 この拡張機能によって公開されているコマンドの一覧については、Microsoft の [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md) を参照してください。

これらの手順を実際に確認するには、こちらの[サンプル拡張機能](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample)を参照してください。

その他の例については、現在このツールが利用されている次のオープンソースの拡張機能を確認してください。

- [Visual Studio Code 用 Azure Resource Manager (ARM) ツール](https://github.com/microsoft/vscode-azurearmtools)

- [.NET Interactive Notebooks](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a>はじめに: エンド ユーザー

一般に、エンド ユーザーは、拡張機能作成者用の .NET インストール ツールを操作する必要はありません。 拡張機能に関する問題が発生した場合は、Microsoft の[トラブルシューティング ページ](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting-runtime.md)を確認するか、[GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues) でイシューを報告してください。
