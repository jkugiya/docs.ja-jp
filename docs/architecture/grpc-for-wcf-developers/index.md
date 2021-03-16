---
title: WCF 開発者向け ASP.NET Core gRPC - WCF 開発者向け gRPC
description: WCF 開発者向け ASP.NET Core 5.0 で gRPC サービスを構築する方法の概要
ms.date: 01/06/2021
ms.openlocfilehash: 26cce6bb784c08a5b59623ff5882fcf2fbb9e9ac
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970194"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="8b782-103">WCF 開発者向け ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="8b782-103">ASP.NET Core gRPC for WCF Developers</span></span>

![カバーの画像](./media/cover.png)

<span data-ttu-id="8b782-105">エディション v1.0.1 - ASP.NET Core 5.0 に更新されました</span><span class="sxs-lookup"><span data-stu-id="8b782-105">EDITION v1.0.1 - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="8b782-106">書籍の更新とコミュニティへの投稿については、「[changelog](https://aka.ms/grpc-ebook-changelog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b782-106">Refer [changelog](https://aka.ms/grpc-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="8b782-107">発行者</span><span class="sxs-lookup"><span data-stu-id="8b782-107">PUBLISHED BY</span></span>

<span data-ttu-id="8b782-108">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="8b782-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="8b782-109">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8b782-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="8b782-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="8b782-110">One Microsoft Way</span></span>

<span data-ttu-id="8b782-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="8b782-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="8b782-112">Copyright © 2021 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8b782-112">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="8b782-113">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="8b782-113">All rights reserved.</span></span> <span data-ttu-id="8b782-114">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="8b782-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="8b782-115">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="8b782-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="8b782-116">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8b782-116">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="8b782-117">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="8b782-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="8b782-118">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="8b782-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="8b782-119"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="8b782-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="8b782-120">Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。</span><span class="sxs-lookup"><span data-stu-id="8b782-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="8b782-121">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="8b782-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="8b782-122">作成者:</span><span class="sxs-lookup"><span data-stu-id="8b782-122">Authors:</span></span>

> <span data-ttu-id="8b782-123">**Mark Rendle** - 技術部門最高責任者 - [Visual ReCode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="8b782-123">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="8b782-124">**Miranda Steiner** - 技術文書作成者</span><span class="sxs-lookup"><span data-stu-id="8b782-124">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="8b782-125">エディター:</span><span class="sxs-lookup"><span data-stu-id="8b782-125">Editor:</span></span>

> <span data-ttu-id="8b782-126">**Maira Wenzel** - シニア コンテンツ開発者 - Microsoft</span><span class="sxs-lookup"><span data-stu-id="8b782-126">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="8b782-127">はじめに</span><span class="sxs-lookup"><span data-stu-id="8b782-127">Introduction</span></span>

<span data-ttu-id="8b782-128">gRPC とは、ネットワーク接続されたサービスと分散型アプリケーションを構築するための最新のフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="8b782-128">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="8b782-129">SOAP のクロスプラットフォーム相互運用性と組み合わせた、Windows Communication Foundation (WCF) NetTCP バインドのパフォーマンスを想像してください。</span><span class="sxs-lookup"><span data-stu-id="8b782-129">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="8b782-130">gRPC は、アプリケーションとサービス間のハイ パフォーマンスで低帯域幅の通信を実現できるように、HTTP/2 および Protobuf メッセージエンコード プロトコルに基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="8b782-130">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="8b782-131">.NET、Java、Python、Node.js、Go、C++ など、最も一般的なプログラミング言語およびプラットフォームにわたって、サーバー コードおよびクライアント コードの生成がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8b782-131">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="8b782-132">ASP.NET Core 5.0 での gRPC 用の最上級のサポートと共に、.NET Framework 4.x 用の既存の gRPC ツールとライブラリを利用できることから、.NET を組織で採用することを検討している開発チームにとって、これは WCF に替わる優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="8b782-132">With the first-class support for gRPC in ASP.NET Core 5.0, alongside the existing gRPC tools and libraries for .NET Framework 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="8b782-133">対象読者</span><span class="sxs-lookup"><span data-stu-id="8b782-133">Who should use this guide</span></span>

<span data-ttu-id="8b782-134">このガイドは、.NET Framework または .NET で作業している開発者の中でも、以前に WCF を使用したことがある方々、使用しているアプリケーションを .NET Core 3.0 以降のバージョン用の最新の RPC 環境に移行しようとしている方々向けに作成されています。</span><span class="sxs-lookup"><span data-stu-id="8b782-134">This guide was written for developers working in .NET Framework or .NET who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="8b782-135">より一般的に、このガイドは、NET 5 へのアップグレードを実施または検討していて、組み込みの gRPC ツールを使用する場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8b782-135">More generally, if you are upgrading, or considering upgrading, to .NET 5, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="8b782-136">このガイドを使用する方法</span><span class="sxs-lookup"><span data-stu-id="8b782-136">How you can use this guide</span></span>

<span data-ttu-id="8b782-137">ここでは、ASP.NET Core 5.0 で gRPC サービスを構築する方法について簡単に説明します。特に、類似のプラットフォームとして WCF について説明します。</span><span class="sxs-lookup"><span data-stu-id="8b782-137">This is a short introduction to building gRPC Services in ASP.NET Core 5.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="8b782-138">gRPC の原則について説明しており、各概念をそれに相当する WCF の機能に関連付けています。また、既存の WCF アプリケーションを gRPC に移行する方法を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="8b782-138">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="8b782-139">WCF の経験があり、新しいサービスを構築する目的で gRPC の知識を求めている開発者にとっても役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8b782-139">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="8b782-140">独自のプロジェクトのためのテンプレートまたは参照としてサンプル アプリケーションを利用できます。本書やそのサンプルのコードは自由にコピーしたり、再利用したりしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="8b782-140">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="8b782-141">これらの考慮事項と営業案件の共通理解を確保するために、チームにこのガイドを自由に転送してください。</span><span class="sxs-lookup"><span data-stu-id="8b782-141">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="8b782-142">用語の共通セットと基本原則を理解して全員が作業すると、アーキテクチャのパターンと実践方法を一貫して適用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8b782-142">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="8b782-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b782-143">References</span></span>

- <span data-ttu-id="8b782-144">**gRPC の Web サイト**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="8b782-144">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="8b782-145">**サーバー アプリ用の .NET 5 と .NET Framework のどちらかを選択する**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="8b782-145">**Choosing between .NET 5 and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="8b782-146">次へ</span><span class="sxs-lookup"><span data-stu-id="8b782-146">Next</span></span>](introduction.md)
