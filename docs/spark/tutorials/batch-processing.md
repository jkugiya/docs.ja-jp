---
title: .NET for Apache Spark を使用したバッチ処理のチュートリアル
description: .NET for Apache Spark を使用してバッチ処理を実行する方法について説明します。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 28674c583466bb4873581c9d233b9a508019b045
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876943"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="ba647-103">チュートリアル: .NET for Apache Spark を使用してバッチ処理を実行する</span><span class="sxs-lookup"><span data-stu-id="ba647-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="ba647-104">このチュートリアルでは、.NET for Apache Spark を使用してバッチ処理を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba647-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="ba647-105">バッチ処理とは、保存データの変換のことです。これは、ソース データが既にデータ ストレージに読み込まれていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ba647-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="ba647-106">バッチ処理は、通常、さらに詳しい分析を行うために準備する必要がある大規模なフラット データセットに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="ba647-107">ログの処理とデータ ウェアハウスは、一般的なバッチ処理のシナリオです。</span><span class="sxs-lookup"><span data-stu-id="ba647-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="ba647-108">このシナリオでは、さまざまなプロジェクトがフォークされた回数や最近のプロジェクトがどのように更新されたかなど、GitHub プロジェクトに関する情報を分析します。</span><span class="sxs-lookup"><span data-stu-id="ba647-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="ba647-109">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba647-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="ba647-110">.NET for Apache Spark アプリケーションを作成して実行する</span><span class="sxs-lookup"><span data-stu-id="ba647-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="ba647-111">データを DataFrame に読み込み、分析を行うために準備する</span><span class="sxs-lookup"><span data-stu-id="ba647-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="ba647-112">Spark SQL を使用してデータを処理する</span><span class="sxs-lookup"><span data-stu-id="ba647-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba647-113">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ba647-113">Prerequisites</span></span>

<span data-ttu-id="ba647-114">.NET for Apache Spark を初めて使用する場合は、「[.NET for Apache Spark の概要](get-started.md)」チュートリアルをチェックし、環境を準備して最初の .NET for Apache Spark アプリケーションを実行する方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ba647-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="ba647-115">サンプル データをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="ba647-115">Download the sample data</span></span>

<span data-ttu-id="ba647-116">[GHTorrent](http://ghtorrent.org/) は、プロジェクト、コミット、およびウォッチャーに関する情報などのすべてのパブリック GitHub イベントを監視し、イベントとその構造をデータベースに格納します。</span><span class="sxs-lookup"><span data-stu-id="ba647-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="ba647-117">さまざまな期間にわたって収集されたデータは、ダウンロード可能なアーカイブとして入手できます。</span><span class="sxs-lookup"><span data-stu-id="ba647-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="ba647-118">ダンプ ファイルは非常に大きいため、このガイドでは、GitHub からダウンロードできる、[ダンプ ファイルの切り詰められたバージョン](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv)を使用します。</span><span class="sxs-lookup"><span data-stu-id="ba647-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="ba647-119">GHTorrent データセットは、デュアル ライセンス スキーム ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)) で配布されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="ba647-120">商用以外の用途 (教育、研究、個人的使用などを含みますが、これらに限定されません) では、データセットは [CC-BY-SA ライセンス](https://creativecommons.org/licenses/by-sa/4.0/)に基づいて配布されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ba647-121">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="ba647-121">Create a console application</span></span>

1. <span data-ttu-id="ba647-122">コマンド プロンプトで、次のコマンドを実行して、新しいコンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba647-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="ba647-123">`dotnet` コマンドで、種類が `console` の `new` アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba647-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="ba647-124">`-o` パラメーターは、アプリが格納される *mySparkApp* というディレクトリを作成して、必要なファイルを取り込みます。</span><span class="sxs-lookup"><span data-stu-id="ba647-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="ba647-125">`cd mySparkBatchApp` コマンドで、ディレクトリを、先ほど作成したアプリ ディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="ba647-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="ba647-126">アプリで .NET for Apache Spark を使用するには、Microsoft.Spark パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ba647-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="ba647-127">コンソールで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ba647-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="ba647-128">SparkSession を作成する</span><span class="sxs-lookup"><span data-stu-id="ba647-128">Create a SparkSession</span></span>

1. <span data-ttu-id="ba647-129">次の追加の `using` ステートメントを *mySparkBatchApp* 内の *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="ba647-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="ba647-130">次のコードをプロジェクトの名前空間に追加します。</span><span class="sxs-lookup"><span data-stu-id="ba647-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="ba647-131">*s_referenceData* は、後で日付に基づいてフィルター処理を行うためにプログラムで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="ba647-132">次のコードを Main メソッド内に追加して、新しい SparkSession を確立します。</span><span class="sxs-lookup"><span data-stu-id="ba647-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="ba647-133">SparkSession は、Dataset と DataFrame API を使用して Spark をプログラミングするためのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="ba647-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="ba647-134">`spark` オブジェクトを呼び出すことにより、プログラム全体で Spark および DataFrame の機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ba647-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="ba647-135">データを準備する</span><span class="sxs-lookup"><span data-stu-id="ba647-135">Prepare the data</span></span>

1. <span data-ttu-id="ba647-136">入力ファイルを `DataFrame` に読み込みます。これは、名前付きの列に編成されたデータの分散コレクションです。</span><span class="sxs-lookup"><span data-stu-id="ba647-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="ba647-137"><xref:Microsoft.Spark.Sql.DataFrame.Schema%2A> を使用して、データの列を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ba647-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="ba647-138"><xref:Microsoft.Spark.Sql.DataFrame.Show%2A> メソッドを使用して、DataFrame 内のデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="ba647-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="ba647-139">ダウンロードした GitHub データの場所を指すように、CSV ファイルのパスを必ず更新してください。</span><span class="sxs-lookup"><span data-stu-id="ba647-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. <span data-ttu-id="ba647-140"><xref:Microsoft.Spark.Sql.DataFrame.Na%2A> メソッドを使用して、NA (null) 値を持つ行をドロップし、<xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> メソッドを使用してデータから特定の列を削除します。</span><span class="sxs-lookup"><span data-stu-id="ba647-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="ba647-141">これにより、最終的な分析に関連しない null データまたは列を分析しようとした場合のエラーを回避することができます。</span><span class="sxs-lookup"><span data-stu-id="ba647-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="ba647-142">データを分析する</span><span class="sxs-lookup"><span data-stu-id="ba647-142">Analyze the data</span></span>

<span data-ttu-id="ba647-143">Spark SQL を使用すると、データに対して SQL 呼び出しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ba647-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="ba647-144">ユーザー定義関数と Spark SQL を組み合わせて、ユーザー定義関数を DataFrame のすべての行に適用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="ba647-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="ba647-145">明示的に `spark.Sql` を呼び出して、他の種類のアプリで見られる標準的な SQL 呼び出しを模倣することができます。</span><span class="sxs-lookup"><span data-stu-id="ba647-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="ba647-146">また、<xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> や <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> などのメソッドを呼び出して、データの計算を明示的に結合、フィルター処理、および実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="ba647-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="ba647-147">このアプリの目的は、GitHub プロジェクトのデータに関する分析情報を得ることです。</span><span class="sxs-lookup"><span data-stu-id="ba647-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="ba647-148">次のコード スニペットをプログラムに追加してデータを分析します。</span><span class="sxs-lookup"><span data-stu-id="ba647-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="ba647-149">次のコード ブロックを追加すると、各言語がフォークされた回数が検出されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="ba647-150">まず、データが言語別にグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-150">First, the data is grouped by language.</span></span> <span data-ttu-id="ba647-151">次に、各言語からのフォークの平均回数が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="ba647-152">次のコード ブロックを追加して、フォークの平均回数を降順に並べ替え、どの言語が最も多くフォークされているかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba647-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="ba647-153">つまり、フォークの回数が最も多いものが最初に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="ba647-154">次のコード ブロックは、最近のプロジェクトがどのように更新されたかを示します。</span><span class="sxs-lookup"><span data-stu-id="ba647-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="ba647-155">*MyUDF* という名前の新しいユーザー定義関数を登録し、それを、チュートリアルの冒頭で宣言した日付 (*s_referenceDate*) と比較します。</span><span class="sxs-lookup"><span data-stu-id="ba647-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="ba647-156">各プロジェクトの日付がこの参照日付と比較されます。</span><span class="sxs-lookup"><span data-stu-id="ba647-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="ba647-157">次に、Spark SQL を使用してデータの各行で UDF を呼び出し、データセット内の各プロジェクトを分析します。</span><span class="sxs-lookup"><span data-stu-id="ba647-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);
   cleanedProjects.CreateOrReplaceTempView("dateView");

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. <span data-ttu-id="ba647-158">`spark.Stop()` を呼び出して SparkSession を終了します。</span><span class="sxs-lookup"><span data-stu-id="ba647-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="ba647-159">spark-submit を使用してアプリを実行する</span><span class="sxs-lookup"><span data-stu-id="ba647-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="ba647-160">次のコマンドを使用して .NET アプリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ba647-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="ba647-161">`spark-submit` を使用してアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ba647-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="ba647-162">次のコマンドは、必ず Microsoft Spark jar ファイルの実際のパスを使って更新してください。</span><span class="sxs-lookup"><span data-stu-id="ba647-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar dotnet /<path>/to/netcoreapp<version>/mySparkBatchApp.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="ba647-163">コードを取得する</span><span class="sxs-lookup"><span data-stu-id="ba647-163">Get the code</span></span>

<span data-ttu-id="ba647-164">[完全なソリューション](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs)は、GitHub で確認できます。</span><span class="sxs-lookup"><span data-stu-id="ba647-164">You can see the [full solution](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ba647-165">次の手順</span><span class="sxs-lookup"><span data-stu-id="ba647-165">Next steps</span></span>

<span data-ttu-id="ba647-166">次の記事に進み、.NET for Apache Spark でストリーミング データを処理する方法を学習してください。</span><span class="sxs-lookup"><span data-stu-id="ba647-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ba647-167">チュートリアル: .NET for Apache Spark を使用した構造化ストリーミング</span><span class="sxs-lookup"><span data-stu-id="ba647-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
