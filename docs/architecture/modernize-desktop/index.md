---
title: .NET 5 を使用した Windows 10 でのデスクトップ アプリの最新化
description: .NET 5 を使用して既存のデスクトップ アプリを最新化する方法
ms.date: 01/06/2021
ms.openlocfilehash: de8a451b0598b5eabd99028d377c161dace61623
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615706"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-5"></a><span data-ttu-id="42708-103">.NET 5 を使用した Windows 10 でのデスクトップ アプリの最新化</span><span class="sxs-lookup"><span data-stu-id="42708-103">Modernizing Desktop Apps on Windows 10 with .NET 5</span></span>

![最新デスクトップ アプリに関する電子ブックのカバーを示すスクリーンショット。](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="42708-105">**エディション v1.0.1** - .NET 5 に更新</span><span class="sxs-lookup"><span data-stu-id="42708-105">**EDITION v1.0.1** - Updated to .NET 5</span></span>

<span data-ttu-id="42708-106">書籍の更新とコミュニティへの投稿については、「[changelog](https://aka.ms/desktop-ebook-changelog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42708-106">Refer [changelog](https://aka.ms/desktop-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="42708-107">発行者</span><span class="sxs-lookup"><span data-stu-id="42708-107">PUBLISHED BY</span></span>

<span data-ttu-id="42708-108">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="42708-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="42708-109">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="42708-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="42708-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="42708-110">One Microsoft Way</span></span>

<span data-ttu-id="42708-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="42708-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="42708-112">Copyright © 2021 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="42708-112">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="42708-113">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="42708-113">All rights reserved.</span></span> <span data-ttu-id="42708-114">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="42708-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="42708-115">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="42708-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="42708-116">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="42708-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="42708-117">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="42708-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="42708-118">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="42708-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="42708-119"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="42708-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="42708-120">Mac および macOS は Apple Inc. の商標です。</span><span class="sxs-lookup"><span data-stu-id="42708-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="42708-121">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="42708-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="42708-122">共同作成者:</span><span class="sxs-lookup"><span data-stu-id="42708-122">Co-Authors:</span></span>

> <span data-ttu-id="42708-123">**Olia Gavrysh**、Microsoft、.NET チーム、プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="42708-123">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="42708-124">**Miguel Angel Castejón Dominguez**、Kabel、イノベーション アーキテクト</span><span class="sxs-lookup"><span data-stu-id="42708-124">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="42708-125">参加者とレビュー担当者:</span><span class="sxs-lookup"><span data-stu-id="42708-125">Participants and reviewers:</span></span>

> <span data-ttu-id="42708-126">**Maira Wenzel**、Microsoft、.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="42708-126">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="42708-127">**Andy De Gorge**、Microsoft、.NET Docs チーム、シニア コンテンツ開発者</span><span class="sxs-lookup"><span data-stu-id="42708-127">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="42708-128">**Miguel Ramos**、Microsoft、Windows 開発者プラットフォーム チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="42708-128">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="42708-129">**Adam Braden**、Microsoft、Windows 開発者プラットフォーム チーム、プリンシパル プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="42708-129">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="42708-130">**Ricardo Minguez Pablos**、Microsoft、Azure IoT チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="42708-130">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="42708-131">**Nish Anil**、Microsoft、.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="42708-131">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="42708-132">**Beth Massi**、Microsoft、シニア製品マーケティング マネージャー</span><span class="sxs-lookup"><span data-stu-id="42708-132">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="42708-133">**Scott Hunter**、Microsoft、.NET チーム、パートナー ディレクター プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="42708-133">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="42708-134">**Marta Fuentes Lara**、Kabel</span><span class="sxs-lookup"><span data-stu-id="42708-134">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="42708-135">**Raúl Fernández de Córdoba**、Kabel</span><span class="sxs-lookup"><span data-stu-id="42708-135">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="42708-136">**Antonio Manuel Fernández Cantos**、Kabel</span><span class="sxs-lookup"><span data-stu-id="42708-136">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="42708-137">はじめに</span><span class="sxs-lookup"><span data-stu-id="42708-137">Introduction</span></span>

<span data-ttu-id="42708-138">本書では、最新化のパスを使用して既存のデスクトップ アプリケーションを移動させて、最新のランタイム、言語、プラットフォームの機能を組み込むための戦略について説明しています。</span><span class="sxs-lookup"><span data-stu-id="42708-138">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="42708-139">アプリケーションがそれぞれ異なり、同様にユーザーの要件や設定もそれぞれ異なるため、独自のレシピが存在しないことはわかるでしょう。</span><span class="sxs-lookup"><span data-stu-id="42708-139">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="42708-140">良い点としては、アプリケーションに新しい機能を追加する場合に、一般的なアプローチを適用できることです。</span><span class="sxs-lookup"><span data-stu-id="42708-140">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="42708-141">一部のアプローチでは、コードを大幅に変更する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="42708-141">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="42708-142">本書では、それらすべての機能のバックグラウンドでの動作を明らかにして、実装のしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="42708-142">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="42708-143">また、プロジェクトを進化させるためのインスピレーションを得ることができるように、既存のデスクトップ アプリケーションを最新化するための一般的なシナリオをいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="42708-143">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="42708-144">Microsoft では、既存のアプリケーションを最新化するためのアプローチとして、カスタマイズされた独自のパスを柔軟に作成できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="42708-144">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="42708-145">本書で説明されている最新化戦略はすべて、大部分が独立しています。</span><span class="sxs-lookup"><span data-stu-id="42708-145">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="42708-146">ご利用のアプリケーションに関連する戦略を選択し、重要ではない他の戦略はスキップすることができます。</span><span class="sxs-lookup"><span data-stu-id="42708-146">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="42708-147">つまり、戦略を組み合わせて、最良の方法でアプリケーションのニーズに対応することができます。</span><span class="sxs-lookup"><span data-stu-id="42708-147">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="42708-148">対象読者</span><span class="sxs-lookup"><span data-stu-id="42708-148">Who should use the book</span></span>

<span data-ttu-id="42708-149">本書は、既存の Windows フォームと WPF デスクトップ アプリケーションを最新化して .NET と Windows 10 のメリットを活用したい開発者やソリューション アーキテクト向けです。</span><span class="sxs-lookup"><span data-stu-id="42708-149">This book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET and Windows 10.</span></span>

<span data-ttu-id="42708-150">また、既存のデスクトップ アプリケーションを最新化することで得られるメリットの概要を知りたいエンタープライズ アーキテクトや開発担当者などの技術的な意思決定者の場合にも、本書は役立つでしょう。</span><span class="sxs-lookup"><span data-stu-id="42708-150">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="42708-151">本書の使用方法</span><span class="sxs-lookup"><span data-stu-id="42708-151">How to use the book</span></span>

<span data-ttu-id="42708-152">本書では、既存のアプリケーションを最新化する必要がある "理由"、および NET と MSIX を使用してデスクトップ アプリを最新化することで得られる具体的なメリットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="42708-152">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="42708-153">本書の内容は、概要は知りたいが、実装や技術的なステップバイステップの詳細は必要のないアーキテクトおよび技術的意思決定者向けに考案されています。</span><span class="sxs-lookup"><span data-stu-id="42708-153">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="42708-154">各章には、サンプルの実装コード スニペットとスクリーンショットを記載しています。また、第 5 章では、サンプル アプリケーションの完全な移行プロセスを説明します。</span><span class="sxs-lookup"><span data-stu-id="42708-154">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="42708-155">本書で取り上げないもの</span><span class="sxs-lookup"><span data-stu-id="42708-155">What this book doesn't cover</span></span>

<span data-ttu-id="42708-156">本書では、リフトアンドシフト シナリオに重点を置いたシナリオの特定のサブセットを紹介し、コードを書き直すことなく最新化のメリットを得るための方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="42708-156">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="42708-157">本書では、.NET を使用して最新のアプリケーションをゼロから開発することについて、および Windows フォームと WPF の概要については説明しません。</span><span class="sxs-lookup"><span data-stu-id="42708-157">This book isn't about developing modern applications with .NET from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="42708-158">ここでは、デスクトップ開発のための最新テクノロジを使用した既存のデスクトップ アプリケーションの更新方法について重点的に説明します。</span><span class="sxs-lookup"><span data-stu-id="42708-158">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="42708-159">本書で使用するサンプル</span><span class="sxs-lookup"><span data-stu-id="42708-159">Samples used in this book</span></span>

<span data-ttu-id="42708-160">最新化の実行に必要な手順を強調するために、`eShopModernizing` と呼ばれるサンプル アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="42708-160">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="42708-161">このアプリケーションには、Windows フォームと WPF という 2 種類のフレーバーがあります。これらの両方で .NET に対して最新化を実行する方法について、ステップバイステップのプロセスを説明します。</span><span class="sxs-lookup"><span data-stu-id="42708-161">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET.</span></span>

<span data-ttu-id="42708-162">また、本書の GitHub リポジトリには、プロセスの結果が表示されます。ステップバイステップのチュートリアルに従う場合は、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="42708-162">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="42708-163">フィードバックの送信</span><span class="sxs-lookup"><span data-stu-id="42708-163">Send your feedback</span></span>

<span data-ttu-id="42708-164">本書と関連サンプルは継続的に更新されるので、お客様のフィードバックを歓迎しています。</span><span class="sxs-lookup"><span data-stu-id="42708-164">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="42708-165">本書を改善する方法についてコメントがある場合、[GitHub の問題](https://github.com/dotnet/docs/issues)に関して作成されたあらゆるページの下部にあるフィードバック セクションをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="42708-165">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="42708-166">次へ</span><span class="sxs-lookup"><span data-stu-id="42708-166">Next</span></span>](why-modern-applications.md)
