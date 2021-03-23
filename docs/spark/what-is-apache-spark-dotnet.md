---
title: .NET for Apache Spark とは
description: .NET for Apache Spark について説明します。これは、.NET コードが記述されたすべての場所で Spark を使用する、無料でオープンソースのクロスプラットフォームなビッグ データ分析フレームワークです。
author: mamccrea
ms.topic: overview
ms.date: 10/09/2020
ms.openlocfilehash: 1fa3ae16334176f0e3e888087078d5b98de9d869
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873199"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="d1c8b-103">.NET for Apache Spark とは</span><span class="sxs-lookup"><span data-stu-id="d1c8b-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="d1c8b-104">[Apache Spark](what-is-spark.md) は、大規模なデータ セット (一般的にテラバイトまたはペタバイト規模のデータ) の分析に使用される汎用の分散処理エンジンです。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="d1c8b-105">.NET for Apache Spark は、人気のあるオープンソースのビッグ データ分析フレームワークのための、[オープンソース](https://github.com/dotnet/spark)でクロスプラットフォームの無料の .NET サポートです。既に知っている言語を使用して、Apache Spark の機能をビッグ データ アプリケーションに追加できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-105">With .NET for Apache Spark, the free, [open-source](https://github.com/dotnet/spark), and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="d1c8b-106">.NET for Apache Spark を選択する理由</span><span class="sxs-lookup"><span data-stu-id="d1c8b-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="d1c8b-107">.NET for Apache Spark は、.NET の経験あるいはコード ベースを持つ開発者が、ビッグ データ分析の世界へ参入できるように支援します。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="d1c8b-108">.NET for Apache Spark は、C# および F# から Spark を使用するためのハイ パフォーマンスの API を提供します。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="d1c8b-109">C# および F# では、次にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="d1c8b-110">構造化データを操作するためのデータフレームおよび SparkSQL。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="d1c8b-111">ストリーミング データを操作するための Spark Structured Streaming。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="d1c8b-112">SQL 構文を使用してクエリを作成するための Spark SQL。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="d1c8b-113">トレーニングと予測を高速化するための機械学習の統合 (つまり、[ML.NET](https://dot.net/ml) と共に .NET for Apache Spark を使用します)。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="d1c8b-114">.NET for Apache Spark は、.NET Standard (.NET 実装全体で共通した .NET API の標準仕様) に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="d1c8b-115">つまり、.NET コードが記述されたすべての場所で Apache Spark を使用できることで、.NET 開発者として既に持っているすべての知識、スキル、コード、およびライブラリを再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="d1c8b-116">.NET for Apache Spark は、.NET Core を使用して Windows、Linux、macOS で実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="d1c8b-117">Windows では、.NET Framework を使用して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="d1c8b-118">Azure HDInsight Spark、Amazon EMR Spark、Azure Databricks、AWS 上の Databricks など、主要なすべてのクラウド プロバイダーにアプリケーションをデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="d1c8b-119">.NET for Apache Spark のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="d1c8b-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="d1c8b-120">Spark への C# および F# の言語バインドは、拡張を簡単にする新しい Spark 相互運用レイヤーに記述されています。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="d1c8b-121">この新しい Spark 相互運用レイヤーは、言語拡張のベスト プラクティスを使用して記述され、相互運用とパフォーマンスのために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="d1c8b-122">長期的には、この拡張機能を使用して、Spark に他の言語のサポートを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="d1c8b-123">![.NET for Apache Spark のアーキテクチャ](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="d1c8b-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="d1c8b-124">Spark 言語拡張機能の相互運用のサポートについては[提案](https://issues.apache.org/jira/browse/SPARK-26257)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="d1c8b-125">.NET for Apache Spark のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="d1c8b-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="d1c8b-126">[TPC-H ベンチマーク](http://www.tpc.org/tpch/)を使用して Python および Scala と比較した場合、.NET for Apache Spark はほとんどの場合で優れた成績を収め、ユーザー定義関数のパフォーマンスが重要な場合は Python よりも 2 倍高速に実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="d1c8b-127">パフォーマンスを改善してベンチマークを行うための継続的な取り組みがなされています。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="d1c8b-128">独自のベンチマークを実行するには、[.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/main/benchmark) で利用可能なベンチマークを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/main/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="d1c8b-129">.NET for Apache Spark のロードマップ</span><span class="sxs-lookup"><span data-stu-id="d1c8b-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="d1c8b-130">正規の [.NET for Apache Spark のロードマップ](https://github.com/dotnet/spark/blob/main/ROADMAP.md)から短期および長期の計画について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/main/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="d1c8b-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="d1c8b-131">.NET Foundation</span></span>

<span data-ttu-id="d1c8b-132">.NET for Apache Spark プロジェクトは、[.NET Foundation](https://www.dotnetfoundation.org/) の一部です。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="d1c8b-133">投稿</span><span class="sxs-lookup"><span data-stu-id="d1c8b-133">Contributions</span></span>

<span data-ttu-id="d1c8b-134">.NET for Apache Spark チームでは、GitHub イシューとプル要求の両方での投稿を推奨しています。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="d1c8b-135">まず、[既存のイシュー](https://github.com/dotnet/spark/issues)を探します。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="d1c8b-136">既存のイシューが見つからない場合は、[新しいイシューを開始](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+)します。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d1c8b-137">次の手順</span><span class="sxs-lookup"><span data-stu-id="d1c8b-137">Next steps</span></span>

<span data-ttu-id="d1c8b-138">.NET for Apache Spark を試す。</span><span class="sxs-lookup"><span data-stu-id="d1c8b-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d1c8b-139">チュートリアル: .NET for Apache Spark の概要</span><span class="sxs-lookup"><span data-stu-id="d1c8b-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
