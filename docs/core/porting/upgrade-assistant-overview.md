---
title: .NET アップグレード アシスタントの概要
description: .NET Framework からの移行と .NET 5 へのプロジェクトのアップグレードに役立つ .NET アップグレード アシスタント ツールについて紹介します。
author: ardalis
ms.date: 03/08/2021
ms.openlocfilehash: c667cfce40d4f740bc23606826eb2a058643b7be
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604776"
---
# <a name="overview-of-the-net-upgrade-assistant"></a>.NET アップグレード アシスタントの概要

お客様は、現在 .NET Framework 上で実行されているアプリを .NET 5 に移植することに関心があるとします。 .NET アップグレード アシスタント ツールを使用すれば、このプロセスを容易に行うことができます。 この記事では、次について説明します。

- .NET アップグレード アシスタントの概要。
- .NET アップグレード アシスタントをインストールする方法。

## <a name="what-is-the-net-upgrade-assistant"></a>.NET アップグレード アシスタントとは

.NET アップグレード アシスタントは、さまざまな種類の .NET Framework アプリに対して実行できるコマンドライン ツールです。 これは、.NET Framework アプリの .NET 5 へのアップグレードを支援するように設計されています。 このツールを実行した後、**ほとんどの場合、アプリでは移行を完遂するためにより多くの作業が必要になります**。 このツールには、移行を完遂するのを支援するアナライザーのインストールが含まれています。

現在、このツールでは次の種類の .NET Framework アプリがサポートされています。

- .NET Framework Windows フォーム アプリ
- .NET Framework WPF アプリ
- .NET Framework ASP.NET MVC アプリ
- .NET Framework コンソール アプリ
- .NET Framework クラス ライブラリ

.NET アップグレード アシスタントは現在プレリリースされていて、頻繁に更新されています。 このツールの使用時に問題が見つかった場合は、このツールの [GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant)でそれらをご報告ください。

## <a name="how-to-install-the-net-upgrade-assistant"></a>.NET アップグレード アシスタントをインストールする方法

.NET アップグレード アシスタントをインストールして使用する方法については、[入門チュートリアル](https://aka.ms/dotnet-upgrade-assistant-install)に関するページを参照してください。

### <a name="prerequisites"></a>[前提条件]

1. このツールでは、プロジェクト ファイルの操作に MSBuild が使用されます。 最新バージョンの MSBuild がインストールされていることをご確認ください。 [Visual Studio 2019 をインストール](https://visualstudio.microsoft.com/downloads/)すれば、それを簡単に行うことができます。
1. このツールは [try-convert](https://github.com/dotnet/try-convert) に依存しています。 このツールを正しく動作させるには、プロジェクト ファイルを新しい SDK スタイルに変換するための try-convert ツールをインストールする必要があります。 **try-convert** が既にインストールされている場合は、代わりにそれを更新することが必要になることがあります (**upgrade-assistant** がバージョン _0.7.212201_ 以降に依存しているためです)
    1. try-convert をインストールするには: `dotnet tool install -g try-convert`
    1. try-convert を更新するには: `dotnet tool update -g try-convert`

### <a name="installation-steps"></a>インストール手順

このツールは、次を実行することで .NET CLI ツールとしてインストールできます:

```dotnet
dotnet tool install -g upgrade-assistant
```

同様に、.NET アップグレード アシスタントは .NET CLI ツールとしてインストールされるため、次を実行することで簡単に更新できます:

```dotnet
dotnet tool update -g upgrade-assistant
```

インストールの手順の詳細については、プロジェクトの [README](https://github.com/dotnet/upgrade-assistant) を参照してください。

## <a name="see-also"></a>関連項目

- [.NET アップグレード アシスタントを使用して WPF アプリを .NET 5 にアップグレードする](upgrade-assistant-wpf-framework.md)
- [.NET アップグレード アシスタントを使用して Windows フォーム アプリを .NET 5 にアップグレードする](upgrade-assistant-winforms-framework.md)
- [.NET アップグレード アシスタントを使用して ASP.NET MVC アプリを .NET 5 にアップグレードする](upgrade-assistant-aspnetmvc.md)
- [.NET アップグレード アシスタントの GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant)
