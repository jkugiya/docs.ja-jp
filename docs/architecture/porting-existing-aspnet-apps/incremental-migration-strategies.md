---
title: 段階的に移行するための戦略
description: チームがどのような戦略を採用していても、ASP.NET MVC から .NET Core に大規模なアプリを段階的に移行することができますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: dc500fa71188c472f78ef4df95d79434208552c3
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102401462"
---
# <a name="strategies-for-migrating-incrementally"></a>段階的に移行するための戦略

大規模なアプリの移行における最大の課題は、プロセスを小さなタスクに分割する方法を決定することです。 この目的に適用できるいくつかの方法があります。たとえば、UI、データアクセス、ビジネスロジックなどの水平方向の層にアプリを分割したり、アプリを別の小さなアプリに分割したりすることができます。 もう1つの方法は、最新の .NET Core リリースに対して、アプリの一部またはすべてを別のフレームワークバージョンにアップグレードすることです。 使用できる1つの方法は、一度に1つの水平方向のレイヤーを移行するのではなく、アプリの [垂直スライス](https://deviq.com/practices/vertical-slices) を移行することです。 これらのさまざまなアプローチについて考えてみましょう。

Large ASP.NET 4.5 アプリの移行の課題を考慮してください。 1つの方法は、アプリ全体を .NET Framework 4.5 から .NET Core 3.1 に直接移行することです。 ただし、この方法では、2つのフレームワークとバージョン間のすべての重大な変更を考慮する必要があります。

## <a name="migrating-layer-by-layer"></a>レイヤーによるレイヤーの移行

.NET エコシステムに加えて、さまざまな .NET framework 間の相互運用性を向上させるために、 [.NET Standard](https://dotnet.microsoft.com/platform/dotnet-standard)ます。 .NET Standard では、承認された一連の共通 Api に対してライブラリを構築できるため、どの .NET アプリでも使用できます。 .NET Standard 2.0 は、ほとんどの .NET Framework および .NET Core アプリで使用されるほとんどの基本クラスライブラリ機能に対応しているため、注目してください。 残念ながら、.NET Standard 2.0 がサポートされている .NET の最も古いバージョンは .NET Framework 4.6.1 であり、.NET Framework 4.8 には、初期アップグレードのための魅力的な選択肢となっている多くの更新プログラムがあります。

.NET Framework 4.5 システムレイヤーを段階的にアップグレードする方法の1つは、最初にクラスライブラリの依存関係を .NET Framework 4.8 に更新することです。 次に、これらのライブラリを .NET Standard クラスライブラリに変更します。 必要に応じて、マルチターゲットと条件付きコンパイルを使用します。 この手順は、アプリの依存関係が .NET Framework を必要とし、.NET Standard や .NET Core を使用するために直接移植できないシナリオで役に立ちます。 .NET Framework ライブラリは ASP.NET Core 2.1 アプリで使用できるため、次の手順は、アプリの一部またはすべての web 機能を ASP.NET Core 2.1 に移行することです ( [前の章](choose-net-core-version.md)を参照)。 これは、下位レベルのクラスライブラリの依存関係と web アプリのエントリポイントまでの作業を開始する "ボトムアップ" アプローチです。

アプリが ASP.NET Core 2.1 で実行されている場合、分離された ASP.NET Core 3.1 に移行するのは比較的簡単です。 この手順で最も可能性の高い課題は、互換性のない依存関係を更新して、.NET Core をサポートし、場合によっては最新バージョンの .NET Standard をサポートすることです。 .NET Framework のみのライブラリに問題のある依存関係がないアプリの場合、ASP.NET Core 2.1 にアップグレードする理由はほとんどありません。 ASP.NET Core 3.1 に直接移植すると、よりわかりやすくなり、手間がかかります。

アプリが .NET Core 3.1 で実行されている間、現在の .NET 5 リリースへの移行は比較的簡単です。 このプロセスでは、主にプロジェクトファイルのターゲットフレームワークとそれに関連付けられている NuGet パッケージの依存関係を更新する必要があります。 [考慮すべき](../../core/compatibility/5.0.md)重大な変更がいくつかありますが、ほとんどのアプリでは .net Core 3.1 から .net 5 に移行するために大幅な変更は必要ありません。 [.Net Core 3.1 と .net 5 を選択する際の主な決定要因は、サポートされている可能性が](choose-net-core-version.md)あります。

別の方法としては、"ボトムアップ" アプローチの代わりに、web アプリ (またはソリューション全体) から開始し、自動ツールを使用してアップグレードを支援することもできます。 [.Net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)を使用すると、.NET Framework アプリを .net Core/.net 5 にアップグレードできます。 これにより、プロジェクトファイル形式の変更、適切なターゲットフレームワークの設定、NuGet 依存関係の更新など、アプリのアップグレードに関連する一般的なタスクの多くが自動化されます。

別の方法としては、"ボトムアップ" アプローチの代わりに、web アプリ (またはソリューション全体) から開始し、自動ツールを使用してアップグレードを支援することもできます。 [.Net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)を使用すると、.NET Framework アプリを .net Core/.net 5 にアップグレードできます。 これにより、プロジェクトファイル形式の変更、適切なターゲットフレームワークの設定、NuGet 依存関係の更新など、アプリのアップグレードに関連する一般的なタスクの多くが自動化されます。

## <a name="migrating-slice-by-slice"></a>スライスによるスライスの移行

移行の別の方法として、機能の垂直スライスを識別し、ターゲットプラットフォームに1つずつ移行します。 最初の手順として、新しい ASP.NET Core 3.1 または5のアプリを作成します。 次に、最初に移行される個々のページまたは API エンドポイントを特定します。 ASP.NET Core アプリでこの1つのルートをサポートするために必要な機能だけを構築します。 次に、HTTP リライトまたはリバースプロキシを使用して、これらのページまたはエンドポイントに対する要求を、ASP.NET アプリではなく新しいアプリに送信します。

IIS を使用してこの戦略を実行する方法についての特定のガイダンスについては [、「5つの展開シナリオ](deployment-scenarios.md)」で説明されています。

## <a name="references"></a>関連項目

- [.NET Standard とは何でしょうか。](https://dotnet.microsoft.com/platform/dotnet-standard)
- [.NET 5 の概要](https://devblogs.microsoft.com/dotnet/introducing-net-5/)
- [ASP.NET Core 3.1 から5.0 への移行](/aspnet/core/migration/31-to-50)
- [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)

>[!div class="step-by-step"]
>[前へ](choose-net-core-version.md)
>[次へ](migrate-web-forms.md)
