---
title: 移行に関するその他の情報
description: チームが .NET Framework アプリを .NET Core に移植する際に役立つリソースはどこで見つけることができますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: c6563f4791d133606cb1818a088bff17a315b1f6
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102401459"
---
# <a name="additional-migration-resources"></a>移行に関するその他の情報

ASP.NET MVC や Web API からの移行を計画して実行する際には、このブックを超えて使用できるリソースがいくつかあります。 ASP.NET Core。 これらの情報を書き留めておき、移行の過程で発生した障害を克服するのに役立ちます。

## <a name="official-documentation"></a>公式ドキュメント

公式のドキュメント web サイトである [docs.microsoft.com](https://docs.microsoft.com/)には、バージョン、フレームワーク、互換性に影響する変更、およびサポートオプションに関する最新情報が記載されています。 この書籍には、docs 記事へのリンクが多数掲載されていますが、直面している問題については、少なくともドキュメントをすばやく検索して、問題についての情報があるかどうかを確認し、解決策または回避策を提供することをお勧めします。

## <a name="github"></a>GitHub

.NET Core はオープンソースプロジェクトであるため、GitHub で多くの問題が検出、報告、議論、修正されています。 Microsoft には、役に立つ可能性のあるリポジトリを見つけることができる GitHub 組織がいくつかあります。 これらの組織の一覧とパブリックリポジトリの一部を次に示します。

- [Microsoft](https://github.com/microsoft)
  - [ASP.NET API のバージョン管理](https://github.com/microsoft/aspnet-api-versioning)
- [dotnet](https://github.com/dotnet)
  - [ASP.NET Core](https://github.com/dotnet/aspnetcore)
  - [.NET ランタイム](https://github.com/dotnet/runtime)
  - [Entity Framework Core](https://github.com/dotnet/efcore)
  - [C# 言語](https://github.com/dotnet/csharplang)
  - [Docs](https://github.com/dotnet/docs)
  - [ドキュメントのサンプル](https://github.com/dotnet/samples)
  - [変換を試す](https://github.com/dotnet/try-convert)
  - [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)
- [.NET アーキテクチャリファレンスアプリ](https://github.com/dotnet-architecture)
  - [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing)
  - [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb)
  - [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)

移行時に問題が発生した場合は、これらの GitHub リポジトリをレポートすることをお勧めします。 製品チームは問題を監視し、通常はバグレポートに迅速に対応します (ただし、"how to" の質問は、Stack Overflow により適切に指示される可能性があります)。

## <a name="stack-overflow"></a>Stack Overflow

[Stack Overflow](https://stackoverflow.com/) には、前述の質問と回答の形式の豊富な情報が記載されています。最も役に立つ回答が最初に記載されており、問題を解決した場合はマークが付けられています。 発生する可能性のある問題に対する既存の解決策を探すだけでなく、もちろん質問をして、.NET コミュニティからの回答を得ることもできます。 タグを使用して検索を絞り込むことができることを忘れないでください。質問をする際には、質問に対して必要なエクスペリエンスを最大限に活用するために、適切なタグを使用するようにしてください。

## <a name="youtube-channels"></a>YouTube チャンネル

YouTube には、.NET と .NET Core のビデオコンテンツが大量に含まれています。これには、発生する可能性のあるシナリオについて説明する便利なチュートリアルやチュートリアルが含まれている場合があります。 オンラインヘルプを検索する他の作業が短い場合は、個別に検索することを検討してください。 開始するには、次のような場所があります。

- [dotnet](https://www.youtube.com/dotnet)
- [Visual Studio](https://www.youtube.com/visualstudio)

## <a name="twitter-gitter-slack-and-other-community-channels"></a>Twitter、Gitter、余裕、およびその他のコミュニティチャネル

.Net の開発者に接続する他の多くの方法については、 [.net のコミュニティページ](https://dotnet.microsoft.com/platform/community)を参照してください。 [Dotnetevolution Discord サーバー](https://aka.ms/dotnet-discord)に参加することもできます。 さらに、多くの製品チームとチームメンバーは、Twitter だけでなく、他のさまざまなコミュニティにも存在します。 [Twitter でも、この本の執筆者](https://twitter.com/ardalis)と連絡を取ることができます。

## <a name="references"></a>関連項目

- [.NET Framework から .NET Core への移植の概要](../../core/porting/index.md)
- [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)
- [ASP.NET から ASP.NET Core への移行](../../core/porting/index.md)
- [.NET コミュニティリソース](https://dotnet.microsoft.com/platform/community)

>[!div class="step-by-step"]
>[前へ](deployment-strategies.md)
>[次へ](architectural-differences.md)
