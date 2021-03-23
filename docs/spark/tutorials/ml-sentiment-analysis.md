---
title: .NET for Apache Spark と ML.NET での感情分析のチュートリアル
description: このチュートリアルでは、感情分析に ML.NET と .NET for Apache Spark を使用する方法について説明します。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: a21b92f910d82cbddd2976adeb292cea5f7bc78b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876865"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="af5dd-103">チュートリアル: .NET for Apache Spark と ML.NET での感情分析</span><span class="sxs-lookup"><span data-stu-id="af5dd-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="af5dd-104">このチュートリアルでは、ML.NET と .NET for Apache Spark を使用してオンライン レビューの感情分析を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="af5dd-105">[ML.NET](http://dot.net/ml) は、クロスプラットフォームでオープンソースの機械学習フレームワークであり無料です。</span><span class="sxs-lookup"><span data-stu-id="af5dd-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="af5dd-106">ML.NET と .NET for Apache Spark を使用して、機械学習アルゴリズムのトレーニングと予測をスケーリングできます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="af5dd-107">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="af5dd-108">Visual Studio で ML.NET モデル ビルダー を使用して感情分析モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="af5dd-109">.NET for Apache Spark コンソール アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="af5dd-110">ユーザー定義関数を記述して実装します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="af5dd-111">.NET for Apache Spark コンソール アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af5dd-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="af5dd-112">Prerequisites</span></span>

* <span data-ttu-id="af5dd-113">これまでに .NET for Apache Spark アプリケーションを開発したことがない場合は、最初に[概要のチュートリアル](get-started.md)に関する記事を読んで、基本についての理解を深めてください。</span><span class="sxs-lookup"><span data-stu-id="af5dd-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="af5dd-114">このチュートリアルを続ける前に、概要チュートリアルのすべての前提条件を満たしてください。</span><span class="sxs-lookup"><span data-stu-id="af5dd-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="af5dd-115">このチュートリアルでは、Visual Studio で使用できるビジュアル インターフェイスである ML.NET モデル ビルダー (プレビュー) を使用します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="af5dd-116">Visual Studio がない場合は、無料で [Visual Studio の Community バージョンをダウンロードする](https://visualstudio.microsoft.com/downloads/)ことができます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="af5dd-117">ML.NET モデル ビルダー (プレビュー) を[ダウンロードしてインストール](https://marketplace.visualstudio.com/items?itemName=MLNET.07)します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="af5dd-118">Yelp レビュー データセットの [yelptest.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) と [yelptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="af5dd-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="af5dd-119">データを確認する</span><span class="sxs-lookup"><span data-stu-id="af5dd-119">Review the data</span></span>

<span data-ttu-id="af5dd-120">Yelp レビュー データセットには、さまざまなサービスに関するオンライン Yelp レビューが含まれています。</span><span class="sxs-lookup"><span data-stu-id="af5dd-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="af5dd-121">[yelptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) を開き、データの構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="af5dd-122">1 番目の列にはレビュー テキストが含まれ、2 番目の列にはセンチメントのスコアが含まれます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="af5dd-123">センチメント スコアが 1 の場合、レビューは肯定的になり、センチメント スコアが 0 の場合、レビューは否定的になります。</span><span class="sxs-lookup"><span data-stu-id="af5dd-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="af5dd-124">サンプル データを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-124">The following table contains sample data:</span></span>

|<span data-ttu-id="af5dd-125">ReviewText</span><span class="sxs-lookup"><span data-stu-id="af5dd-125">ReviewText</span></span>|<span data-ttu-id="af5dd-126">Sentiment</span><span class="sxs-lookup"><span data-stu-id="af5dd-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="af5dd-127">Wow...Loved this place.</span><span class="sxs-lookup"><span data-stu-id="af5dd-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="af5dd-128">1</span><span class="sxs-lookup"><span data-stu-id="af5dd-128">1</span></span>|
|<span data-ttu-id="af5dd-129">Crust is not good.</span><span class="sxs-lookup"><span data-stu-id="af5dd-129">Crust is not good.</span></span>|    <span data-ttu-id="af5dd-130">0</span><span class="sxs-lookup"><span data-stu-id="af5dd-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="af5dd-131">機械学習モデルを構築する</span><span class="sxs-lookup"><span data-stu-id="af5dd-131">Build your machine learning model</span></span>

1. <span data-ttu-id="af5dd-132">Visual Studio を開き、新しい C# コンソール アプリ (.NET Core) を作成します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="af5dd-133">プロジェクトには「*MLSparkModel*」という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="af5dd-134">**ソリューション エクスプローラー** で、*MLSparkModel* プロジェクトを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="af5dd-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="af5dd-135">次に、 **[追加] > [機械学習]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="af5dd-136">ML.NET モデル ビルダーで、 **[Sentiment Analysis]\(感情分析\)** シナリオ タイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="af5dd-137">**[Add data]\(データの追加\)** ページで、*yelptrain.csv* データセットをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="af5dd-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="af5dd-138">**[Columns to Predict]\(予測する列\)** ドロップダウンから *[Sentiment]\(感情\)* を選択します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="af5dd-139">**[Train]\(トレーニング\)** ページで、トレーニング時間を "*60 秒*" に設定し、 **[Start training]\(トレーニングの開始\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="af5dd-140">**[Progress]\(進行状況\)** の下にトレーニングの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="af5dd-141">モデル ビルダーのトレーニングが完了したら、トレーニングの結果を **[Evaluate]\(評価\)** します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="af5dd-142">**[Try your model]\(モデルを試す\)** の下のテキスト ボックスに語句を入力して **[Predict]\(予測\)** を選択し、出力を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="af5dd-143">**[Code]\(コード\)** を選択してから **[Projects]\(プロジェクトの追加\)** を選択して、ML モデルをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="af5dd-144">ソリューションに次の 2 つのプロジェクトが追加されることに注意してください: **MLSparkModelML.ConsoleApp** と **MLSparkModelML.Model**。</span><span class="sxs-lookup"><span data-stu-id="af5dd-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="af5dd-145">*MLSpark* C# プロジェクトをダブルクリックして、次のプロジェクト参照が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="af5dd-146">コンソール アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="af5dd-146">Create a console app</span></span>

<span data-ttu-id="af5dd-147">モデル ビルダーによってコンソール アプリが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="af5dd-148">ソリューション エクスプローラーで **MLSparkModelML.Console** を右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="af5dd-149">**Microsoft.Spark** を検索し、パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="af5dd-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="af5dd-150">**Microsoft.ML** は、モデル ビルダーによって自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="af5dd-151">SparkSession を作成する</span><span class="sxs-lookup"><span data-stu-id="af5dd-151">Create a SparkSession</span></span>

1. <span data-ttu-id="af5dd-152">**MLSparkModelML.ConsoleApp** の *Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="af5dd-153">このファイルは、モデル ビルダーによって自動生成されたものです。</span><span class="sxs-lookup"><span data-stu-id="af5dd-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="af5dd-154">`using` ステートメント、Main() メソッドの内容、および `CreateSingleDataSample` 領域を削除します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="af5dd-155">次に示す別の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="af5dd-156">`DATA_FILEPATH` を実際の *yelptest.csv* のパスに変更します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="af5dd-157">新しい `SparkSession` を作成するために、次のコードを `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="af5dd-158">Spark セッションは、Dataset API と DataFrame API を使用して Spark をプログラミングするためのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="af5dd-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="af5dd-159">上で作成した *spark* オブジェクトを呼び出すことで、プログラムの至るところで Spark と DataFrame の機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="af5dd-160">DataFrame を作成してコンソールに出力する</span><span class="sxs-lookup"><span data-stu-id="af5dd-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="af5dd-161">`DataFrame` として、*yelptest.csv* ファイルから Yelp レビュー データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="af5dd-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="af5dd-162">`header` オプションと `inferSchema` オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="af5dd-163">`header` オプションを指定すると、*yelptest.csv* の最初の行が、データではなく列名として読み取られます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="af5dd-164">`inferSchema` オプションを指定すると、データに基づいて列の型が推測されます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="af5dd-165">ユーザー定義関数を登録する</span><span class="sxs-lookup"><span data-stu-id="af5dd-165">Register a user-defined function</span></span>

<span data-ttu-id="af5dd-166">Spark アプリケーションで UDF ("*ユーザー定義関数*") を使用して、データの計算と分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="af5dd-167">このチュートリアルでは、ML.NET と UDF を使用して、各 Yelp レビューを評価します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="af5dd-168">`MLudf` という名前の UDF を登録するために、次のコードを `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="af5dd-169">この UDF は、入力として Yelp レビュー文字列を受け取り、肯定的または否定的な感情に対して、それぞれ true または false を出力します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="af5dd-170">後のステップで定義する *predict()* メソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="af5dd-171">Spark SQL を使用して UDF を呼び出す</span><span class="sxs-lookup"><span data-stu-id="af5dd-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="af5dd-172">データを読み取り、ML を組み込んだので、Spark SQL を使用して、DataFrame の各行に対して感情分析を実行する UDF を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="af5dd-173">次のコードを `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-173">Add the following code to your `Main` method:</span></span>

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a><span data-ttu-id="af5dd-174">predict() メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="af5dd-174">Create predict() method</span></span>

<span data-ttu-id="af5dd-175">`Main()` メソッドの前に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="af5dd-176">このコードは、モデル ビルダーによって *ConsumeModel.cs* に生成されるものと似ています。</span><span class="sxs-lookup"><span data-stu-id="af5dd-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="af5dd-177">このメソッドをコンソールに移動すると、アプリを実行するたびにモデルが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="af5dd-178">コンソール アプリにモデルを追加する</span><span class="sxs-lookup"><span data-stu-id="af5dd-178">Add the model to your console app</span></span>

<span data-ttu-id="af5dd-179">ソリューション エクスプローラーで、**MLSparkModelML.Model** プロジェクトから *MLModel.zip* ファイルをコピーし、**MLSparkModelML.ConsoleApp** プロジェクトにそれを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="af5dd-180">*MLSparkModelML.ConsoleApp.csproj* に参照が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="af5dd-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="af5dd-181">コードを実行する</span><span class="sxs-lookup"><span data-stu-id="af5dd-181">Run your code</span></span>

<span data-ttu-id="af5dd-182">`spark-submit` を使用してコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="af5dd-183">コマンド プロンプトを使用してコンソール アプリのルート フォルダーに移動し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="af5dd-184">最初に、アプリをクリーンにして発行します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="af5dd-185">次に、コンソール アプリの発行フォルダーに移動して、次の `spark-submit` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="af5dd-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="af5dd-186">忘れずに、実際の Microsoft Spark jar ファイルのパスで、コマンドを更新してください。</span><span class="sxs-lookup"><span data-stu-id="af5dd-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2-4_2.11-1.0.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="af5dd-187">コードを取得する</span><span class="sxs-lookup"><span data-stu-id="af5dd-187">Get the code</span></span>

<span data-ttu-id="af5dd-188">このチュートリアルは、「[ビッグ データでの感情分析](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)」の例のコードに似ています。</span><span class="sxs-lookup"><span data-stu-id="af5dd-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="af5dd-189">次の手順</span><span class="sxs-lookup"><span data-stu-id="af5dd-189">Next steps</span></span>

<span data-ttu-id="af5dd-190">次の記事に進み、.NET for Apache Spark で構造化ストリーミングを行う方法を学習してください。</span><span class="sxs-lookup"><span data-stu-id="af5dd-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="af5dd-191">チュートリアル: .NET for Apache Spark を使用した構造化ストリーミング</span><span class="sxs-lookup"><span data-stu-id="af5dd-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
