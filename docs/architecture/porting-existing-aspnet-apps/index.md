---
title: .NET Core への既存の ASP.NET アプリの移植
description: ASP.NET MVC および Web API アプリを ASP.NET Core に変換するための無料ガイドです。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 36c0cdbe03fb97ae82336d53e15be2108e9c6367
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462986"
---
# <a name="porting-existing-aspnet-apps-to-net-core"></a><span data-ttu-id="5be34-103">.NET Core への既存の ASP.NET アプリの移植</span><span class="sxs-lookup"><span data-stu-id="5be34-103">Porting Existing ASP.NET Apps to .NET Core</span></span>

![カバーの画像](./media/index/porting-existing-aspnet-apps.png)

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5be34-105">発行者</span><span class="sxs-lookup"><span data-stu-id="5be34-105">PUBLISHED BY</span></span>

<span data-ttu-id="5be34-106">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="5be34-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="5be34-107">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5be34-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="5be34-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="5be34-108">One Microsoft Way</span></span>

<span data-ttu-id="5be34-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="5be34-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="5be34-110">Copyright &copy; 2020 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5be34-110">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="5be34-111">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="5be34-111">All rights reserved.</span></span> <span data-ttu-id="5be34-112">本書の内容のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="5be34-112">No part of this book's contents may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="5be34-113">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="5be34-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="5be34-114">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="5be34-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="5be34-115">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="5be34-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="5be34-116">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="5be34-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="5be34-117"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="5be34-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="5be34-118">Mac および macOS は Apple Inc. の商標です。</span><span class="sxs-lookup"><span data-stu-id="5be34-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="5be34-119">Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。</span><span class="sxs-lookup"><span data-stu-id="5be34-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="5be34-120">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="5be34-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="5be34-121">作成者:</span><span class="sxs-lookup"><span data-stu-id="5be34-121">Authors:</span></span>

> <span data-ttu-id="5be34-122">**Steve "ardalis" Smith**、ソフトウェア アーキテクトおよびトレーナー - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="5be34-122">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="5be34-123">参加者とレビュー担当者:</span><span class="sxs-lookup"><span data-stu-id="5be34-123">Participants and Reviewers:</span></span>

> <span data-ttu-id="5be34-124">**Nish Anil**、Microsoft、.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="5be34-124">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="5be34-125">**Mike Rousos**、Microsoft、.NET チーム、主任ソフトウェア エンジニア</span><span class="sxs-lookup"><span data-stu-id="5be34-125">**Mike Rousos**, Principal Software Engineer, .NET team, Microsoft</span></span>

> <span data-ttu-id="5be34-126">**Scott Addie**、Microsoft、.NET チーム、シニア コンテンツ開発者</span><span class="sxs-lookup"><span data-stu-id="5be34-126">**Scott Addie**, Senior Content Developer, .NET team, Microsoft</span></span>

> <span data-ttu-id="5be34-127">**David Pine**、Microsoft、.NET チーム、シニア コンテンツ開発者</span><span class="sxs-lookup"><span data-stu-id="5be34-127">**David Pine**, Senior Content Developer, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="5be34-128">バージョン</span><span class="sxs-lookup"><span data-stu-id="5be34-128">Version</span></span>

<span data-ttu-id="5be34-129">このガイドでは、 **.NET Core 3.1** と、.NET Core 3.1 リリースと同時期の同じテクノロジの "流れ" (つまり、Azure やその他のサードパーティ製テクノロジ) に関連する更新プログラムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5be34-129">This guide covers **.NET Core 3.1** and updates related to the same technology "wave" (that is, Azure and other third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="5be34-130">.NET Core 3.1 から .NET 5.0 (次のバージョン) への更新は比較的わかりやすく、.NET Framework から .NET Core への移植よりも必要な作業量がかなり少なくなります。</span><span class="sxs-lookup"><span data-stu-id="5be34-130">Updating from .NET Core 3.1 to .NET 5.0 (the next version) is relatively straightforward and certainly will require substantially less effort than porting from .NET Framework to .NET Core.</span></span> <span data-ttu-id="5be34-131">.NET Framework 4.x から .NET 5.0 への移行は、.NET Core 3.1 への移行に似ています。</span><span class="sxs-lookup"><span data-stu-id="5be34-131">Migrating from .NET Framework 4.x to .NET 5.0 will be similar to migrating to .NET Core 3.1.</span></span> <span data-ttu-id="5be34-132">詳細については、[適切な .NET Core バージョンの選択](choose-net-core-version.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5be34-132">For more information, see [choosing the right .NET Core version](choose-net-core-version.md).</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="5be34-133">対象読者</span><span class="sxs-lookup"><span data-stu-id="5be34-133">Who should use this guide</span></span>

<span data-ttu-id="5be34-134">このガイドの対象読者は、ASP.NET MVC および Web API (.NET Framework 4.x) 用に作成された既存のアプリを .NET Core に移行することに関心をお持ちの開発者、開発リーダー、およびアーキテクトです。</span><span class="sxs-lookup"><span data-stu-id="5be34-134">This guide's audience is developers, development leads, and architects who are interested in migrating their existing apps written for ASP.NET MVC and Web API (.NET Framework 4.x) to .NET Core.</span></span> <span data-ttu-id="5be34-135">ASP.NET Web Forms の開発者はこのガイドを活用できますが、電子書籍『[ASP.NET Web Forms 開発者向け Blazor](https://docs.microsoft.com/dotnet/architecture/blazor-for-web-forms-developers/)』も併せてご覧いただく必要があります。</span><span class="sxs-lookup"><span data-stu-id="5be34-135">ASP.NET Web Forms developers will benefit from this guide but should also read the [Blazor for ASP.NET Web Forms Developers](https://docs.microsoft.com/dotnet/architecture/blazor-for-web-forms-developers/) e-book.</span></span>

<span data-ttu-id="5be34-136">第 2 の対象読者は、アプリを .NET Core に移行するタイミングを計画している技術的な意思決定者です。</span><span class="sxs-lookup"><span data-stu-id="5be34-136">A secondary audience is technical decision-makers planning when to move their apps to .NET Core.</span></span>

<span data-ttu-id="5be34-137">この書籍の対象読者は、ASP.NET MVC および Web API で実行する既存の大規模なアプリをお持ちの .NET 開発者です。</span><span class="sxs-lookup"><span data-stu-id="5be34-137">The target audience for this book is .NET developers with large, existing apps that run on ASP.NET MVC and Web API.</span></span> <span data-ttu-id="5be34-138">ASP.NET Web Forms 上に構築されたアプリはこの書籍の対象範囲外ですが、.NET Framework と .NET Core を比較する情報の多くは関連している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5be34-138">Apps built on ASP.NET Web Forms are outside of the focus of this book, though much of the information comparing .NET Framework and .NET Core may still be relevant.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="5be34-139">このガイドを使用する方法</span><span class="sxs-lookup"><span data-stu-id="5be34-139">How you can use this guide</span></span>

<span data-ttu-id="5be34-140">この書籍は、多くの読者がそうするように、はじめから終わりまで読んでいくことが可能です。</span><span class="sxs-lookup"><span data-stu-id="5be34-140">You can read this book straight through, as we expect many readers to do.</span></span> <span data-ttu-id="5be34-141">この書籍ではまず、そもそも自分のアプリを移植する必要があるかどうかについての考慮事項が説明されます。</span><span class="sxs-lookup"><span data-stu-id="5be34-141">This book will provide you first with considerations for whether you should port your app at all.</span></span> <span data-ttu-id="5be34-142">その内容の次に、.NET Framework と .NET Core のアーキテクチャの相違点が示されます。</span><span class="sxs-lookup"><span data-stu-id="5be34-142">That content is followed by architectural differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="5be34-143">そこから、大規模なソリューションを徐々に移行していくための戦略と、実際のアプリを移植する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="5be34-143">From there, you'll learn strategies for migrating a large solution over time and how to port a real app.</span></span> <span data-ttu-id="5be34-144">書籍では次に、異なるアプリを、ユーザーに対しては 1 つのアプリのように見せながら実行する必要性に対応する展開シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5be34-144">Next, the book includes deployment scenarios that address the need to run different apps while appearing as a single app to users.</span></span> <span data-ttu-id="5be34-145">最後に、ASP.NET MVC から ASP.NET Core に移行された実際のアプリについて説明する 2 つのケース スタディで書籍は締めくくられます。</span><span class="sxs-lookup"><span data-stu-id="5be34-145">The book concludes with two case studies describing real apps that have migrated from ASP.NET MVC to ASP.NET Core.</span></span>

<span data-ttu-id="5be34-146">第 1 章から開始するかどうかにかかわらず、これらのいずれかの章を参照して特定の概念について学習することができます。</span><span class="sxs-lookup"><span data-stu-id="5be34-146">Whether or not you choose to start from the first chapter, you can reference any of these chapters to learn about specific concepts:</span></span>

- [<span data-ttu-id="5be34-147">アーキテクチャの相違点</span><span class="sxs-lookup"><span data-stu-id="5be34-147">Architectural differences</span></span>](architectural-differences.md)
- [<span data-ttu-id="5be34-148">大規模なソリューションの移行</span><span class="sxs-lookup"><span data-stu-id="5be34-148">Migrate large solutions</span></span>](migrate-large-solutions.md)
- [<span data-ttu-id="5be34-149">移行の例</span><span class="sxs-lookup"><span data-stu-id="5be34-149">Sample migration</span></span>](example-migration-eshop.md)
- [<span data-ttu-id="5be34-150">展開シナリオ</span><span class="sxs-lookup"><span data-stu-id="5be34-150">Deployment scenarios</span></span>](deployment-scenarios.md)

<span data-ttu-id="5be34-151">このガイドは [PDF 形式](https://aka.ms/aspnet-porting-ebook)とオンラインの両方で利用できます。</span><span class="sxs-lookup"><span data-stu-id="5be34-151">This guide is available both in [PDF form](https://aka.ms/aspnet-porting-ebook) and online.</span></span> <span data-ttu-id="5be34-152">本書やそのオンライン版のリンクをご自由にチームに転送し、これらの概念の共通理解に役立ててください。</span><span class="sxs-lookup"><span data-stu-id="5be34-152">Feel free to forward this document or links to its online version to your team to ensure a common understanding of these concepts.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="5be34-153">フィードバックの送信</span><span class="sxs-lookup"><span data-stu-id="5be34-153">Send your feedback</span></span>

<span data-ttu-id="5be34-154">本書と関連サンプルは継続的に更新されるので、お客様のフィードバックを歓迎しています。</span><span class="sxs-lookup"><span data-stu-id="5be34-154">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="5be34-155">本書を改善する方法についてコメントがある場合、[GitHub の問題](https://github.com/dotnet/docs/issues)に関して作成されたあらゆるページの下部にあるフィードバック セクションをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="5be34-155">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="5be34-156">次へ</span><span class="sxs-lookup"><span data-stu-id="5be34-156">Next</span></span>](introduction.md)
