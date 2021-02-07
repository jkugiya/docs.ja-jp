---
title: ASP.NET Web Forms 開発者向け Blazor
description: Blazor と .NET Core を使用し、使い慣れた簡単な方法で、.NET によるフルスタック Web アプリを構築する方法について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 02/02/2021
ms.openlocfilehash: 267f7222865c5a92d20faaae41b052da08c284a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653473"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a><span data-ttu-id="cb024-103">ASP.NET Web Forms 開発者向け Blazor</span><span class="sxs-lookup"><span data-stu-id="cb024-103">Blazor for ASP.NET Web Forms Developers</span></span>

![サーバーレス アプリの e-book のカバーを示すスクリーン ショット。](./media/index/blazor-for-aspnet-web-forms-developers.png)

> <span data-ttu-id="cb024-105">次の場所でダウンロードできます: <https://aka.ms/blazor-ebook></span><span class="sxs-lookup"><span data-stu-id="cb024-105">DOWNLOAD available at: <https://aka.ms/blazor-ebook></span></span>

<span data-ttu-id="cb024-106">**エディション v1.0**</span><span class="sxs-lookup"><span data-stu-id="cb024-106">**EDITION v1.0**</span></span>

<span data-ttu-id="cb024-107">書籍の更新とコミュニティへの投稿については、「[changelog](https://aka.ms/blazor-ebook-changelog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb024-107">Refer [changelog](https://aka.ms/blazor-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="cb024-108">発行者</span><span class="sxs-lookup"><span data-stu-id="cb024-108">PUBLISHED BY</span></span>

<span data-ttu-id="cb024-109">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="cb024-109">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="cb024-110">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="cb024-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="cb024-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="cb024-111">One Microsoft Way</span></span>

<span data-ttu-id="cb024-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="cb024-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="cb024-113">Copyright © 2021 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="cb024-113">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="cb024-114">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="cb024-114">All rights reserved.</span></span> <span data-ttu-id="cb024-115">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="cb024-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="cb024-116">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="cb024-116">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="cb024-117">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="cb024-117">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="cb024-118">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="cb024-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="cb024-119">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="cb024-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="cb024-120"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="cb024-120">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="cb024-121">Mac および macOS は Apple Inc. の商標です。</span><span class="sxs-lookup"><span data-stu-id="cb024-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="cb024-122">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="cb024-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="cb024-123">作成者:</span><span class="sxs-lookup"><span data-stu-id="cb024-123">Authors:</span></span>

> <span data-ttu-id="cb024-124">**[Daniel Roth](https://github.com/danroth27)** 、Microsoft Corporation のプリンシパル プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="cb024-124">**[Daniel Roth](https://github.com/danroth27)**, Principal Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="cb024-125">**[Jeff Fritz](https://github.com/csharpfritz)** 、Microsoft Corporation のシニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="cb024-125">**[Jeff Fritz](https://github.com/csharpfritz)**, Senior Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="cb024-126">**[Taylor Southwick](https://github.com/twsouthwick)** 、Microsoft Corporation のシニア ソフトウェア エンジニア</span><span class="sxs-lookup"><span data-stu-id="cb024-126">**[Taylor Southwick](https://github.com/twsouthwick)**, Senior Software Engineer, Microsoft Corp.</span></span>

> <span data-ttu-id="cb024-127">**[Scott Addie](https://github.com/scottaddie)** 、Microsoft Corporation のシニア コンテンツ開発者</span><span class="sxs-lookup"><span data-stu-id="cb024-127">**[Scott Addie](https://github.com/scottaddie)**, Senior Content Developer, Microsoft Corp.</span></span>

> <span data-ttu-id="cb024-128">**[Steve "ardalis" Smith](https://ardalis.com)** 、ソフトウェア アーキテクトおよびトレーナー - Ardalis Services LLC</span><span class="sxs-lookup"><span data-stu-id="cb024-128">**[Steve "ardalis" Smith](https://ardalis.com)**, Software Architect and Trainer, Ardalis Services LLC</span></span>

## <a name="introduction"></a><span data-ttu-id="cb024-129">はじめに</span><span class="sxs-lookup"><span data-stu-id="cb024-129">Introduction</span></span>

<span data-ttu-id="cb024-130">.NET では、あらゆる種類の Web アプリを構築するためのフレームワークとツールの包括的セットである ASP.NET を利用した Web アプリの開発を長期にわたりサポートしてきました。</span><span class="sxs-lookup"><span data-stu-id="cb024-130">.NET has long supported web app development through ASP.NET, a comprehensive set of frameworks and tools for building any kind of web app.</span></span> <span data-ttu-id="cb024-131">ASP.NET には独自の系列の Web フレームワークとテクノロジがあり、その原点は代表的な Active Server Pages (ASP) までさかのぼります。</span><span class="sxs-lookup"><span data-stu-id="cb024-131">ASP.NET has its own lineage of web frameworks and technologies starting all the way back with classic Active Server Pages (ASP).</span></span> <span data-ttu-id="cb024-132">ASP.NET Web Forms、ASP.NET MVC、ASP.NET Web Pages、最近の ASP.NET Core などのフレームワークでは、*サーバーでレンダリングする* Web アプリを生産的かつ強力な方法で構築できます。サーバーでレンダリングする Web アプリでは、HTTP 要求に応答し、UI コンテンツがサーバー上で動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="cb024-132">Frameworks like ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web Pages, and more recently ASP.NET Core, provide a productive and powerful way to build *server-rendered* web apps, where UI content is dynamically generated on the server in response to HTTP requests.</span></span> <span data-ttu-id="cb024-133">各 ASP.NET framework は異なる対象ユーザーとアプリ構築方針に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb024-133">Each ASP.NET framework caters to a different audience and app building philosophy.</span></span> <span data-ttu-id="cb024-134">ASP.NET Web Forms は .NET Framework の初回リリースに付属しました。再利用可能な UI コントロールと単純なイベント処理など、デスクトップ開発者にとっておなじみのパターンを多く利用する Web 開発を可能にしました。</span><span class="sxs-lookup"><span data-stu-id="cb024-134">ASP.NET Web Forms shipped with the original release of the .NET Framework and enabled web development using many of the patterns familiar to desktop developers, like reusable UI controls with simple event handling.</span></span> <span data-ttu-id="cb024-135">しかしながら、どの ASP.NET サービスでも、ユーザーのブラウザーで実行されるコードを実行する方法がありません。</span><span class="sxs-lookup"><span data-stu-id="cb024-135">However, none of the ASP.NET offerings provide a way to run code that executed in the user's browser.</span></span> <span data-ttu-id="cb024-136">それを行うには、JavaScript を記述し、jQuery、Knockout、Angular、React など、ここ数年、人気が上がったり下がったりしているさまざまな JavaScript フレームワーク/ツールのいずれかを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb024-136">To do that requires writing JavaScript and using any of the many JavaScript frameworks and tools that have phased in and out of popularity over the years: jQuery, Knockout, Angular, React, and so on.</span></span>

<span data-ttu-id="cb024-137">[Blazor](https://blazor.net) は、.NET で Web アプリを構築したときにできることを変える、新しい Web フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="cb024-137">[Blazor](https://blazor.net) is a new web framework that changes what is possible when building web apps with .NET.</span></span> <span data-ttu-id="cb024-138">Blazor は、JavaScript ではなく、C# を基盤とするクライアント側の Web UI フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="cb024-138">Blazor is a client-side web UI framework based on C# instead of JavaScript.</span></span> <span data-ttu-id="cb024-139">Blazor を利用すると、クライアント側のロジックと UI コンポーネントを C# で記述し、通常の .NET アセンブリにコンパイルしたら、WebAssembly という名前の新しいオープン Web 標準を利用し、ブラウザーで直接実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb024-139">With Blazor you can write your client-side logic and UI components in C#, compile them into normal .NET assemblies, and then run them directly in the browser using a new open web standard called WebAssembly.</span></span> <span data-ttu-id="cb024-140">あるいは、サーバー上で .NET UI コンポーネントを実行し、ブラウザーとのリアルタイム接続ですべての UI インタラクションを流動的に処理することが Blazor で可能です。</span><span class="sxs-lookup"><span data-stu-id="cb024-140">Or alternatively, Blazor can run your .NET UI components on the server and handle all UI interactions fluidly over a real-time connection with the browser.</span></span> <span data-ttu-id="cb024-141">サーバー上で実行されている .NET とペアリングした場合、Blazor では .NET によるフルスタックの Web 開発が可能になります。</span><span class="sxs-lookup"><span data-stu-id="cb024-141">When paired with .NET running on the server, Blazor enables full-stack web development with .NET.</span></span> <span data-ttu-id="cb024-142">再利用可能なコンポーネント モデルやユーザー イベントを処理する簡単な方法など、Blazor には ASP.NET Web Forms との間にさまざまな共通点があります。また、最新かつ高パフォーマンスな Web 開発エクスペリエンスを提供するために .NET に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="cb024-142">While Blazor shares many commonalities with ASP.NET Web Forms, like having a reusable component model and a simple way to handle user events, it also builds on the foundations of .NET to provide a modern and high-performance web development experience.</span></span>

<span data-ttu-id="cb024-143">本書をお読みいただくと、ASP.NET Web Forms の開発者は慣れた便利な方法で Blazor を導入できます。</span><span class="sxs-lookup"><span data-stu-id="cb024-143">This book introduces ASP.NET Web Forms developers to Blazor in a way that is familiar and convenient.</span></span> <span data-ttu-id="cb024-144">本書では Blazor の概念を ASP.NET Web Forms における類似の概念と一緒に紹介し、さらに、あまり知られていないかもしれない新しい概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb024-144">It introduces Blazor concepts in parallel with analogous concepts in ASP.NET Web Forms while also explaining new concepts that may be less familiar.</span></span> <span data-ttu-id="cb024-145">コンポーネントの作成、ルーティング、レイアウト、構成、セキュリティなど、さまざまなトピックと懸念事項を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="cb024-145">It covers a broad range of topics and concerns including component authoring, routing, layout, configuration, and security.</span></span> <span data-ttu-id="cb024-146">また、本書の内容は新しい開発を可能にすることを第一としていますが、既存のアプリを最新式にするときのために、既存の ASP.NET Web Forms を Blazor に移行するためのガイドラインと方策についても取り上げます。</span><span class="sxs-lookup"><span data-stu-id="cb024-146">And while the content of this book is primarily for enabling new development, it also covers guidelines and strategies for migrating existing ASP.NET Web Forms to Blazor for when you want to modernize an existing app.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="cb024-147">対象読者</span><span class="sxs-lookup"><span data-stu-id="cb024-147">Who should use the book</span></span>

<span data-ttu-id="cb024-148">本書は、既存の知識や技能に関連付けて Blazor を説明してくれる文章を探している ASP.NET Web Forms 開発者向けとなっています。</span><span class="sxs-lookup"><span data-stu-id="cb024-148">This book is for ASP.NET Web Forms developers looking for an introduction to Blazor that relates to their existing knowledge and skills.</span></span> <span data-ttu-id="cb024-149">本書は Blazor を基盤とする新しいプロジェクトを短期間で始める際や、既存の ASP.NET Web Forms アプリケーションを最新式にするための計画を立てる際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cb024-149">This book can help with quickly getting started on a new Blazor-based project or to help chart a roadmap for modernizing an existing ASP.NET Web Forms application.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="cb024-150">本書の使用方法</span><span class="sxs-lookup"><span data-stu-id="cb024-150">How to use the book</span></span>

<span data-ttu-id="cb024-151">本書の最初の部分では、Blazor の概要を取り上げ、ASP.NET Web Forms による Web アプリ開発と比較します。</span><span class="sxs-lookup"><span data-stu-id="cb024-151">The first part of this book covers what Blazor is and compares it to web app development with ASP.NET Web Forms.</span></span> <span data-ttu-id="cb024-152">次に、章ごとに Blazor に関するさまざまなトピックを取り上げ、Blazor の概念を ASP.NET Web Forms においてそれに対応する概念に関連付けます。あるいは、まったく新しい概念であれば、それについて十分に説明します。</span><span class="sxs-lookup"><span data-stu-id="cb024-152">The book then covers a variety of Blazor topics, chapter by chapter, and relates each Blazor concept to the corresponding concept in ASP.NET Web Forms, or explains fully any completely new concepts.</span></span> <span data-ttu-id="cb024-153">また、本書では、Blazor の機能の実演や ASP.NET Web Forms から Blazor に移行する際の見本として、ASP.NET Web Forms と Blazor の両方で実装されている完全なサンプル アプリがたびたび取り上げられます。</span><span class="sxs-lookup"><span data-stu-id="cb024-153">The book also refers regularly to a complete sample app implemented in both ASP.NET Web Forms and Blazor to demonstrate Blazor features and to provide a case study for migrating from ASP.NET Web Forms to Blazor.</span></span> <span data-ttu-id="cb024-154">[GitHub](https://github.com/dotnet-architecture/eshoponblazor) には、サンプル アプリの両方の実装 (ASP.NET Web Forms 版と Blazor 版) があります。</span><span class="sxs-lookup"><span data-stu-id="cb024-154">You can find both implementations of the sample app (ASP.NET Web Forms and Blazor versions) on [GitHub](https://github.com/dotnet-architecture/eshoponblazor).</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="cb024-155">本書で取り上げないもの</span><span class="sxs-lookup"><span data-stu-id="cb024-155">What this book doesn't cover</span></span>

<span data-ttu-id="cb024-156">本書は Blazor の紹介文であり、包括的な移行ガイドではありません。</span><span class="sxs-lookup"><span data-stu-id="cb024-156">This book is an introduction to Blazor, not a comprehensive migration guide.</span></span> <span data-ttu-id="cb024-157">ASP.NET Web Forms から Blazor にプロジェクトを移行する方法に関するガイダンスが含まれていますが、微妙な違いや詳細をあらゆる点で説明する試みはありません。</span><span class="sxs-lookup"><span data-stu-id="cb024-157">While it does include guidance on how to approach migrating a project from ASP.NET Web Forms to Blazor, it does not attempt to cover every nuance and detail.</span></span> <span data-ttu-id="cb024-158">ASP.NET から ASP.NET Core に移行する一般的な手順については、ASP.NET Core ドキュメントの[移行ガイダンス](/aspnet/core/migration/proper-to-2x/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb024-158">For more general guidance on migrating from ASP.NET to ASP.NET Core, refer to the [migration guidance](/aspnet/core/migration/proper-to-2x/) in the ASP.NET Core documentation.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="cb024-159">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="cb024-159">Additional resources</span></span>

<span data-ttu-id="cb024-160">Blazor の公式ホーム ページとドキュメントは <https://blazor.net> にあります。</span><span class="sxs-lookup"><span data-stu-id="cb024-160">You can find the official Blazor home page and documentation at <https://blazor.net>.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="cb024-161">フィードバックの送信</span><span class="sxs-lookup"><span data-stu-id="cb024-161">Send your feedback</span></span>

<span data-ttu-id="cb024-162">本書と関連サンプルは継続的に更新されるので、お客様のフィードバックを歓迎しています。</span><span class="sxs-lookup"><span data-stu-id="cb024-162">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="cb024-163">本書を改善する方法についてコメントがある場合、[GitHub の問題](https://github.com/dotnet/docs/issues)に関して作成されたあらゆるページの下部にあるフィードバック セクションをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="cb024-163">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="cb024-164">次へ</span><span class="sxs-lookup"><span data-stu-id="cb024-164">Next</span></span>](introduction.md)
