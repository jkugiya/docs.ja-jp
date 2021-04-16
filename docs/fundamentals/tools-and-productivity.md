---
title: .NET でのツールと診断
author: IEvangelist
description: .NET 開発者が使用できる開発ツールと診断ツールについて説明します。
ms.author: dapine
ms.date: 10/21/2020
ms.topic: overview
ms.openlocfilehash: 07c1a161a0bb429403db6852fe77749d83c19ec0
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96593833"
---
# <a name="tools-and-diagnostics-in-net"></a><span data-ttu-id="c8f83-103">.NET でのツールと診断</span><span class="sxs-lookup"><span data-stu-id="c8f83-103">Tools and diagnostics in .NET</span></span>

<span data-ttu-id="c8f83-104">この記事では、.NET 開発者が使用できるさまざまなツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c8f83-104">In this article, you'll learn about the various tools available to .NET developers.</span></span> <span data-ttu-id="c8f83-105">.NET には、コマンドライン インターフェイス (CLI) を備えた堅牢なソフトウェア開発キット (SDK) があります。</span><span class="sxs-lookup"><span data-stu-id="c8f83-105">With .NET, you have a robust software development kit (SDK) that includes a command-line interface (CLI).</span></span> <span data-ttu-id="c8f83-106">.NET CLI では、.NET 対応の統合開発環境 (IDE) 全体で多くの機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="c8f83-106">The .NET CLI enables many of the features throughout the .NET-ready integrated development environments (IDEs).</span></span> <span data-ttu-id="c8f83-107">この記事では、パフォーマンスの問題、メモリ リーク、高 CPU、デッドロックを診断するための NET CLI ツール、コード分析のためのツール サポートなどの生産性機能に関するリソースも提供します。</span><span class="sxs-lookup"><span data-stu-id="c8f83-107">This article also provides resources to productivity capabilities, such as .NET CLI tools for diagnosing performance issues, memory leaks, high CPU, deadlocks, and tooling support for code analysis.</span></span>

## <a name="net-sdk"></a><span data-ttu-id="c8f83-108">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="c8f83-108">.NET SDK</span></span>

<span data-ttu-id="c8f83-109">.NET SDK には、.NET ランタイムと .NET CLI の両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c8f83-109">The .NET SDK includes both the .NET Runtime and the .NET CLI.</span></span> <span data-ttu-id="c8f83-110">Windows、Linux、macOS、または Docker 用の [.NET SDK](https://dotnet.microsoft.com/download) をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="c8f83-110">You can download the [.NET SDK](https://dotnet.microsoft.com/download) for Windows, Linux, macOS, or Docker.</span></span> <span data-ttu-id="c8f83-111">詳細については、[.NET SDK の概要](../core/sdk.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f83-111">For more information, see [.NET SDK overview](../core/sdk.md).</span></span>

## <a name="net-cli"></a><span data-ttu-id="c8f83-112">.NET CLI</span><span class="sxs-lookup"><span data-stu-id="c8f83-112">.NET CLI</span></span>

<span data-ttu-id="c8f83-113">.NET CLI は、.NET アプリケーションを開発、ビルド、実行、発行するためのクロスプラットフォーム ツールチェーンです。</span><span class="sxs-lookup"><span data-stu-id="c8f83-113">The .NET CLI is a cross-platform toolchain for developing, building, running, and publishing .NET applications.</span></span> <span data-ttu-id="c8f83-114">.NET CLI は、.NET SDK に含まれています。</span><span class="sxs-lookup"><span data-stu-id="c8f83-114">The .NET CLI is included with the .NET SDK.</span></span> <span data-ttu-id="c8f83-115">詳細については、[.NET CLI の概要](../core/tools/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f83-115">For more information, see [.NET CLI overview](../core/tools/index.md).</span></span>

## <a name="ides"></a><span data-ttu-id="c8f83-116">IDE</span><span class="sxs-lookup"><span data-stu-id="c8f83-116">IDEs</span></span>

<span data-ttu-id="c8f83-117">.NET アプリケーションは、[Visual Studio Code](https://code.visualstudio.com/docs)、 [Visual Studio](/visualstudio/windows)、または [Visual Studio for Mac](/visualstudio/mac) で作成できます。</span><span class="sxs-lookup"><span data-stu-id="c8f83-117">You can write .NET applications in [Visual Studio Code](https://code.visualstudio.com/docs), [Visual Studio](/visualstudio/windows), or [Visual Studio for Mac](/visualstudio/mac).</span></span> <span data-ttu-id="c8f83-118">クラウドを利用した開発環境の詳細については、[Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f83-118">For information on cloud-powered development environments, see [Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline).</span></span>

## <a name="additional-tools"></a><span data-ttu-id="c8f83-119">その他のツール</span><span class="sxs-lookup"><span data-stu-id="c8f83-119">Additional tools</span></span>

<span data-ttu-id="c8f83-120">.NET では、より一般的なツールだけでなく、特定のシナリオ用のツールも用意されています。</span><span class="sxs-lookup"><span data-stu-id="c8f83-120">In addition to the more common tools, .NET also provides tools for specific scenarios.</span></span> <span data-ttu-id="c8f83-121">ユース ケースの一部には、.NET SDK または .NET ランタイムのアンインストール、Windows Communication Foundation (WCF) メタデータの取得、プロキシ ソース コードの生成、XML のシリアル化などがあります。</span><span class="sxs-lookup"><span data-stu-id="c8f83-121">Some of the use cases include uninstalling the .NET SDK or the .NET Runtime, retrieving Windows Communication Foundation (WCF) metadata, generating proxy source code, and serializing XML.</span></span> <span data-ttu-id="c8f83-122">詳細については、「[.NET の追加ツールの概要](../core/additional-tools/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f83-122">For more information, see [.NET additional tools overview](../core/additional-tools/index.md).</span></span>

## <a name="diagnostics-and-instrumentation"></a><span data-ttu-id="c8f83-123">診断とインストルメンテーション</span><span class="sxs-lookup"><span data-stu-id="c8f83-123">Diagnostics and instrumentation</span></span>

<span data-ttu-id="c8f83-124">.NET 開発者は、一般的なパフォーマンス診断ツールを利用して、アプリのパフォーマンスの監視、トレースによるアプリのプロファイリング、パフォーマンス メトリックの収集、およびダンプ ファイルの分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c8f83-124">As a .NET developer, you can make use of common performance diagnostic tools to monitor app performance, profile apps with tracing, collect performance metrics, and analyze dump files.</span></span> <span data-ttu-id="c8f83-125">イベント カウンターを使用してパフォーマンス メトリックを収集し、プロファイリング ツールを使用して、アプリの動作についての分析情報を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="c8f83-125">You collect performance metrics with event counters, and use profiling tools to gain insights into how apps perform.</span></span> <span data-ttu-id="c8f83-126">詳細については、[.NET 診断ツール](../core/diagnostics/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f83-126">For more information, see [.NET diagnostics tools](../core/diagnostics/index.md).</span></span>

## <a name="code-analysis"></a><span data-ttu-id="c8f83-127">コード分析</span><span class="sxs-lookup"><span data-stu-id="c8f83-127">Code analysis</span></span>

<span data-ttu-id="c8f83-128">.NET のコンパイラ プラットフォーム (Roslyn) アナライザーでは、お使いの C# または Visual Basic コードについて、コード品質やコード スタイルに関する問題を検査できます。</span><span class="sxs-lookup"><span data-stu-id="c8f83-128">The .NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and code style issues.</span></span> <span data-ttu-id="c8f83-129">詳細については、「[.NET ソース コード分析の概要](code-analysis/overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f83-129">For more information, see [.NET source code analysis overview](code-analysis/overview.md).</span></span>
