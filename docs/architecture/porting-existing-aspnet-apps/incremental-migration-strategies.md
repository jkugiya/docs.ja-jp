---
title: 段階的に移行するための戦略
description: 大規模なアプリを ASP.NET MVC から .NET Core に段階的に移行するために、チームはどのような戦略を採用できるでしょうか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 615d2a853b698bfc752c3baf36f31ab2a4f2bab8
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122886"
---
# <a name="strategies-for-migrating-incrementally"></a>段階的に移行するための戦略

大規模なアプリの移行に関する最大の課題は、プロセスを小さなタスクに分割する方法を決定することです。 この目的に適用できる戦略は複数あります。たとえば、UI、データ アクセス、ビジネス ロジックなどの水平方向のレイヤーにアプリを分割したり、アプリを複数の小規模なアプリに分割したりすることができます。 もう 1 つの戦略は、一部またはすべてのアプリを別のフレームワーク バージョンにアップグレードしてから最新の .NET Core リリースに移行することです。 そのための方法の 1 つとして、水平方向のレイヤーを一度に 1 つ移行するのではなく、アプリの[垂直スライス](https://deviq.com/practices/vertical-slices)を移行します。 このようなさまざまなアプローチについて検討してみましょう。

## <a name="migrating-slice-by-slice"></a>スライス単位の移行

移行に成功するアプローチの 1 つは、機能の垂直スライスを特定し、ターゲット プラットフォームにそれらを 1 つずつ移行することです。 最初の手順は、新しい ASP.NET Core 3.1 または 5 のアプリを作成することです。 次に、最初に移行する個々のページまたは API エンドポイントを特定します。 ASP.NET Core アプリでこの 1 つのルートをサポートするために必要な機能だけを構築してください。 続いて、HTTP の書き換えまたはリバース プロキシを使用して、これらのページまたはエンドポイントに対する要求を、ASP.NET アプリではなく新しいアプリに送信します。 このアプローチは API プロジェクトに適していますが、多くの MVC アプリに対しても機能します。

スライス単位で移行する場合、個々の API エンドポイントまたは要求されたルートのスタック全体が、新しいプロジェクトまたはソリューションで再作成されます。 一般に、このようなスライスの最初のものに対して最も多くの作業が必要になります。通常はいくつかのプロジェクトを作成し、データ アクセスとソリューションの構成に関して意思決定を行う必要があるためです。 最初のスライスの機能が既存のアプリの機能を反映したら、それを展開して、既存のアプリをそれにリダイレクトするか、単純に削除することができます。 その後、アプリ全体が新しい構造に移植されるまで、このアプローチが繰り返されます。

IIS を使用してこの戦略を実行する方法のガイダンスについては、第 5 章の[デプロイ シナリオ](deployment-scenarios.md)を参照してください。

## <a name="migrating-layer-by-layer"></a>レイヤー単位の移行

大規模な ASP.NET 4.5 アプリの移行の課題について考えてみてください。 1 つのアプローチとしては、アプリ全体を直接 .NET Framework 4.5 から .NET Core 3.1 に移行します。 ただし、このアプローチでは、2 つのフレームワークおよびバージョン間の (大幅な) 破壊的変更を考慮する必要があります。 一度に 1 つのプロジェクトに対してこの作業を実行することで、一連の足がかりが提供されるため、ソリューション全体を一度に移行する必要はありません。

さまざまな .NET フレームワーク間の相互運用性を向上させるために .NET エコシステムに最近追加されたのは [.NET Standard](https://dotnet.microsoft.com/platform/dotnet-standard) です。 .NET Standard では、合意された一連の共通 API に対してライブラリを構築できるため、任意の .NET アプリでライブラリを使用できるようになります。 .NET Standard 2.0 の注目すべき点は、ほとんどの .NET Framework および .NET Core アプリで使用される基本クラス ライブラリ機能の大部分に対応していることです。 残念ながら、.NET Standard 2.0 がサポートされている .NET の最も古いバージョンは .NET Framework 4.6.1 です。 .NET Framework 4.8 には、初期アップグレードのための魅力的な選択肢となる多数の更新プログラムが用意されています。

.NET Framework 4.5 システムをレイヤー単位で段階的にアップグレードする方法の 1 つとしては、最初にクラス ライブラリの依存関係を .NET Framework 4.8 に更新します。 次に、これらのライブラリを .NET Standard クラス ライブラリに変更します。 必要に応じて、マルチ ターゲットと条件付きコンパイルを使用します。 この手順は、アプリの依存関係が .NET Framework を必要としていて、.NET Standard や .NET Core を使用するために直接移植することが容易でないシナリオで役立ちます。 .NET Framework ライブラリは ASP.NET Core 2.1 アプリで使用できるため、次の手順は、アプリの一部またはすべての Web 機能を ASP.NET Core 2.1 に移行することです ([前の章](choose-net-core-version.md)を参照)。 これは、低レベルのクラス ライブラリの依存関係から開始して Web アプリのエントリ ポイントまで到達する "ボトムアップ" アプローチです。

ASP.NET Core 2.1 で実行されているアプリを、分離された ASP.NET Core 3.1 に移行するのは比較的簡単です。 この手順で発生する可能性が最も高い課題は、.NET Core および場合によっては新しいバージョンの .NET Standard をサポートするように互換性のない依存関係を更新することです。 .NET Framework のみのライブラリに問題のある依存関係が存在しないアプリの場合、ASP.NET Core 2.1 にアップグレードする理由はほとんどありません。 ASP.NET Core 3.1 に直接移植する方が理にかなっており、手間も少なくて済みます。

アプリが .NET Core 3.1 で実行される頃には、最新の .NET 5 リリースへの移行も比較的容易になります。 このプロセスでは主に、プロジェクト ファイルのターゲット フレームワークとそれに関連付けられている NuGet パッケージの依存関係を更新する必要があります。 [考慮すべき破壊的変更](../../core/compatibility/5.0.md)はいくつかありますが、ほとんどのアプリでは .NET Core 3.1 から .NET 5 に移行するための大幅な変更は必要ありません。 [.NET Core 3.1 と .NET 5 のどちらを選択するか](choose-net-core-version.md)の主な決定的要因はサポートである可能性があります。

"ボトムアップ" アプローチの代替手段として、Web アプリ (またはソリューション全体) から開始し、自動ツールを使用してアップグレードを支援することができます。 [.Net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)を使用すると、.NET Framework アプリを .NET Core/.NET 5 にアップグレードできます。 これは、プロジェクト ファイルの形式の変更、適切なターゲット フレームワークの設定、NuGet の依存関係の更新など、アプリのアップグレードに関連する多くの一般的なタスクを自動化します。

"ボトムアップ" アプローチの代替手段として、Web アプリ (またはソリューション全体) から開始し、自動ツールを使用してアップグレードを支援することができます。 [.Net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)を使用すると、.NET Framework アプリを .NET Core/.NET 5 にアップグレードできます。 これは、プロジェクト ファイルの形式の変更、適切なターゲット フレームワークの設定、NuGet の依存関係の更新など、アプリのアップグレードに関連する多くの一般的なタスクを自動化します。

## <a name="references"></a>References

- [.NET Standard とは何でしょうか。](https://dotnet.microsoft.com/platform/dotnet-standard)
- [.NET 5 の概要](https://devblogs.microsoft.com/dotnet/introducing-net-5/)
- [ASP.NET Core 3.1 から 5.0 への移行](/aspnet/core/migration/31-to-50)
- [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)

>[!div class="step-by-step"]
>[前へ](choose-net-core-version.md)
>[次へ](migrate-web-forms.md)
