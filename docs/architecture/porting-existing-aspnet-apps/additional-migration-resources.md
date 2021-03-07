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
# <a name="additional-migration-resources"></a><span data-ttu-id="89c2d-103">移行に関するその他の情報</span><span class="sxs-lookup"><span data-stu-id="89c2d-103">Additional migration resources</span></span>

<span data-ttu-id="89c2d-104">ASP.NET MVC や Web API からの移行を計画して実行する際には、このブックを超えて使用できるリソースがいくつかあります。 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="89c2d-104">As you're planning and executing your migration from ASP.NET MVC and/or Web API to ASP.NET Core, there are a number of resources available to help beyond this book.</span></span> <span data-ttu-id="89c2d-105">これらの情報を書き留めておき、移行の過程で発生した障害を克服するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="89c2d-105">Make a note of these and leverage them where appropriate to help you overcome obstacles you encounter on your migration journey.</span></span>

## <a name="official-documentation"></a><span data-ttu-id="89c2d-106">公式ドキュメント</span><span class="sxs-lookup"><span data-stu-id="89c2d-106">Official documentation</span></span>

<span data-ttu-id="89c2d-107">公式のドキュメント web サイトである [docs.microsoft.com](https://docs.microsoft.com/)には、バージョン、フレームワーク、互換性に影響する変更、およびサポートオプションに関する最新情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="89c2d-107">The official documentation website, [docs.microsoft.com](https://docs.microsoft.com/), has the most up-to-date information available about versions, frameworks, breaking changes, and support options.</span></span> <span data-ttu-id="89c2d-108">この書籍には、docs 記事へのリンクが多数掲載されていますが、直面している問題については、少なくともドキュメントをすばやく検索して、問題についての情報があるかどうかを確認し、解決策または回避策を提供することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89c2d-108">You'll find many links in this book to docs articles, but for any problem you're facing it's often worth at least doing a quick search of the docs to see if there is already information covering the issue and offering a solution or workaround.</span></span>

## <a name="github"></a><span data-ttu-id="89c2d-109">GitHub</span><span class="sxs-lookup"><span data-stu-id="89c2d-109">GitHub</span></span>

<span data-ttu-id="89c2d-110">.NET Core はオープンソースプロジェクトであるため、GitHub で多くの問題が検出、報告、議論、修正されています。</span><span class="sxs-lookup"><span data-stu-id="89c2d-110">Because .NET Core is an open-source project, many issues are discovered, reported, discussed, and fixed on GitHub.</span></span> <span data-ttu-id="89c2d-111">Microsoft には、役に立つ可能性のあるリポジトリを見つけることができる GitHub 組織がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="89c2d-111">Microsoft has several GitHub organizations in which you'll find repositories that may be helpful.</span></span> <span data-ttu-id="89c2d-112">これらの組織の一覧とパブリックリポジトリの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="89c2d-112">A partial list of these organizations and some of their public repositories are listed below:</span></span>

- [<span data-ttu-id="89c2d-113">Microsoft</span><span class="sxs-lookup"><span data-stu-id="89c2d-113">Microsoft</span></span>](https://github.com/microsoft)
  - [<span data-ttu-id="89c2d-114">ASP.NET API のバージョン管理</span><span class="sxs-lookup"><span data-stu-id="89c2d-114">ASP.NET API Versioning</span></span>](https://github.com/microsoft/aspnet-api-versioning)
- [<span data-ttu-id="89c2d-115">dotnet</span><span class="sxs-lookup"><span data-stu-id="89c2d-115">dotnet</span></span>](https://github.com/dotnet)
  - [<span data-ttu-id="89c2d-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89c2d-116">ASP.NET Core</span></span>](https://github.com/dotnet/aspnetcore)
  - [<span data-ttu-id="89c2d-117">.NET ランタイム</span><span class="sxs-lookup"><span data-stu-id="89c2d-117">.NET Runtime</span></span>](https://github.com/dotnet/runtime)
  - [<span data-ttu-id="89c2d-118">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="89c2d-118">Entity Framework Core</span></span>](https://github.com/dotnet/efcore)
  - [<span data-ttu-id="89c2d-119">C# 言語</span><span class="sxs-lookup"><span data-stu-id="89c2d-119">C# Language</span></span>](https://github.com/dotnet/csharplang)
  - [<span data-ttu-id="89c2d-120">Docs</span><span class="sxs-lookup"><span data-stu-id="89c2d-120">Docs</span></span>](https://github.com/dotnet/docs)
  - [<span data-ttu-id="89c2d-121">ドキュメントのサンプル</span><span class="sxs-lookup"><span data-stu-id="89c2d-121">Docs Samples</span></span>](https://github.com/dotnet/samples)
  - [<span data-ttu-id="89c2d-122">変換を試す</span><span class="sxs-lookup"><span data-stu-id="89c2d-122">Try Convert</span></span>](https://github.com/dotnet/try-convert)
  - [<span data-ttu-id="89c2d-123">.NET Upgrade Assistant ツール</span><span class="sxs-lookup"><span data-stu-id="89c2d-123">.NET Upgrade Assistant tool</span></span>](https://aka.ms/dotnet-upgrade-assistant)
- [<span data-ttu-id="89c2d-124">.NET アーキテクチャリファレンスアプリ</span><span class="sxs-lookup"><span data-stu-id="89c2d-124">.NET Architecture Reference Apps</span></span>](https://github.com/dotnet-architecture)
  - [<span data-ttu-id="89c2d-125">eShopModernizing</span><span class="sxs-lookup"><span data-stu-id="89c2d-125">eShopModernizing</span></span>](https://github.com/dotnet-architecture/eShopModernizing)
  - [<span data-ttu-id="89c2d-126">eShopOnWeb</span><span class="sxs-lookup"><span data-stu-id="89c2d-126">eShopOnWeb</span></span>](https://github.com/dotnet-architecture/eShopOnWeb)
  - [<span data-ttu-id="89c2d-127">eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="89c2d-127">eShopOnContainers</span></span>](https://github.com/dotnet-architecture/eShopOnContainers)

<span data-ttu-id="89c2d-128">移行時に問題が発生した場合は、これらの GitHub リポジトリをレポートすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89c2d-128">If you run into problems with your migration, these GitHub repositories are a good place to report them.</span></span> <span data-ttu-id="89c2d-129">製品チームは問題を監視し、通常はバグレポートに迅速に対応します (ただし、"how to" の質問は、Stack Overflow により適切に指示される可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="89c2d-129">The product teams watch the issues and typically respond quickly to bug reports (though "how to" questions may be more appropriately directed to Stack Overflow).</span></span>

## <a name="stack-overflow"></a><span data-ttu-id="89c2d-130">Stack Overflow</span><span class="sxs-lookup"><span data-stu-id="89c2d-130">Stack Overflow</span></span>

<span data-ttu-id="89c2d-131">[Stack Overflow](https://stackoverflow.com/) には、前述の質問と回答の形式の豊富な情報が記載されています。最も役に立つ回答が最初に記載されており、問題を解決した場合はマークが付けられています。</span><span class="sxs-lookup"><span data-stu-id="89c2d-131">[Stack Overflow](https://stackoverflow.com/) has a wealth of information in the form of previous questions asked and answers given, with the most helpful answers listed first and marked if they solved the problem.</span></span> <span data-ttu-id="89c2d-132">発生する可能性のある問題に対する既存の解決策を探すだけでなく、もちろん質問をして、.NET コミュニティからの回答を得ることもできます。</span><span class="sxs-lookup"><span data-stu-id="89c2d-132">In addition to searching for an existing solution to a problem you may encounter, you can of course also ask a question yourself and hope for some response from the .NET community.</span></span> <span data-ttu-id="89c2d-133">タグを使用して検索を絞り込むことができることを忘れないでください。質問をする際には、質問に対して必要なエクスペリエンスを最大限に活用するために、適切なタグを使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="89c2d-133">Don't forget you can narrow down a search by using tags, and remember to use appropriate tags when you ask questions to maximize the chances of someone with the experience needed noticing your question.</span></span>

## <a name="youtube-channels"></a><span data-ttu-id="89c2d-134">YouTube チャンネル</span><span class="sxs-lookup"><span data-stu-id="89c2d-134">YouTube channels</span></span>

<span data-ttu-id="89c2d-135">YouTube には、.NET と .NET Core のビデオコンテンツが大量に含まれています。これには、発生する可能性のあるシナリオについて説明する便利なチュートリアルやチュートリアルが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="89c2d-135">YouTube has a huge amount of .NET and .NET Core video content, which may include useful tutorials or walkthroughs covering any scenario you may encounter.</span></span> <span data-ttu-id="89c2d-136">オンラインヘルプを検索する他の作業が短い場合は、個別に検索することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="89c2d-136">Consider searching it separately if your other efforts to find help online come up short.</span></span> <span data-ttu-id="89c2d-137">開始するには、次のような場所があります。</span><span class="sxs-lookup"><span data-stu-id="89c2d-137">Here are a few good places to get started:</span></span>

- [<span data-ttu-id="89c2d-138">dotnet</span><span class="sxs-lookup"><span data-stu-id="89c2d-138">dotnet</span></span>](https://www.youtube.com/dotnet)
- [<span data-ttu-id="89c2d-139">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89c2d-139">Visual Studio</span></span>](https://www.youtube.com/visualstudio)

## <a name="twitter-gitter-slack-and-other-community-channels"></a><span data-ttu-id="89c2d-140">Twitter、Gitter、余裕、およびその他のコミュニティチャネル</span><span class="sxs-lookup"><span data-stu-id="89c2d-140">Twitter, Gitter, Slack, and other community channels</span></span>

<span data-ttu-id="89c2d-141">.Net の開発者に接続する他の多くの方法については、 [.net のコミュニティページ](https://dotnet.microsoft.com/platform/community)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89c2d-141">You'll find many other ways to connect with .NET developers on the [.NET Community page](https://dotnet.microsoft.com/platform/community).</span></span> <span data-ttu-id="89c2d-142">[Dotnetevolution Discord サーバー](https://aka.ms/dotnet-discord)に参加することもできます。</span><span class="sxs-lookup"><span data-stu-id="89c2d-142">You can also join the [DotNetEvolution Discord server](https://aka.ms/dotnet-discord).</span></span> <span data-ttu-id="89c2d-143">さらに、多くの製品チームとチームメンバーは、Twitter だけでなく、他のさまざまなコミュニティにも存在します。</span><span class="sxs-lookup"><span data-stu-id="89c2d-143">Additionally, many product teams and team members are on Twitter as well as in various other communities.</span></span> <span data-ttu-id="89c2d-144">[Twitter でも、この本の執筆者](https://twitter.com/ardalis)と連絡を取ることができます。</span><span class="sxs-lookup"><span data-stu-id="89c2d-144">You can follow and communicate with [the author of this book on Twitter](https://twitter.com/ardalis) as well.</span></span>

## <a name="references"></a><span data-ttu-id="89c2d-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="89c2d-145">References</span></span>

- [<span data-ttu-id="89c2d-146">.NET Framework から .NET Core への移植の概要</span><span class="sxs-lookup"><span data-stu-id="89c2d-146">Overview of porting from .NET Framework to .NET Core</span></span>](../../core/porting/index.md)
- [<span data-ttu-id="89c2d-147">.NET Upgrade Assistant ツール</span><span class="sxs-lookup"><span data-stu-id="89c2d-147">.NET Upgrade Assistant tool</span></span>](https://aka.ms/dotnet-upgrade-assistant)
- [<span data-ttu-id="89c2d-148">ASP.NET から ASP.NET Core への移行</span><span class="sxs-lookup"><span data-stu-id="89c2d-148">Migrate from ASP.NET to ASP.NET Core</span></span>](../../core/porting/index.md)
- [<span data-ttu-id="89c2d-149">.NET コミュニティリソース</span><span class="sxs-lookup"><span data-stu-id="89c2d-149">.NET Community Resources</span></span>](https://dotnet.microsoft.com/platform/community)

>[!div class="step-by-step"]
><span data-ttu-id="89c2d-150">[前へ](deployment-strategies.md)
>[次へ](architectural-differences.md)</span><span class="sxs-lookup"><span data-stu-id="89c2d-150">[Previous](deployment-strategies.md)
[Next](architectural-differences.md)</span></span>
