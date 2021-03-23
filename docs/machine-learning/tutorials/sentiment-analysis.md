---
title: 'チュートリアル: Web サイトのコメントを分析する - 二項分類'
description: このチュートリアルでは、Web サイトのコメントからセンチメントを分類して適切なアクションを実行する .NET Core コンソール アプリケーションの作成方法について説明します。 この二項センチメント分類子には、Visual Studio で C# を使用します。
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3dbcb3cbd4eea2d01638bedc7123f570ff9d64d1
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874591"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="b5bc7-104">チュートリアル: ML.NET の二項分類を使用して Web サイトのコメントのセンチメントを分析する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="b5bc7-105">このチュートリアルでは、Web サイトのコメントからセンチメントを分類して適切なアクションを実行する .NET Core コンソール アプリケーションの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="b5bc7-106">この二項センチメント分類子には、Visual Studio 2017 で C# を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="b5bc7-107">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b5bc7-108">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-108">Create a console application</span></span>
> - <span data-ttu-id="b5bc7-109">データの準備</span><span class="sxs-lookup"><span data-stu-id="b5bc7-109">Prepare data</span></span>
> - <span data-ttu-id="b5bc7-110">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="b5bc7-110">Load the data</span></span>
> - <span data-ttu-id="b5bc7-111">モデルを構築してトレーニングする</span><span class="sxs-lookup"><span data-stu-id="b5bc7-111">Build and train the model</span></span>
> - <span data-ttu-id="b5bc7-112">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-112">Evaluate the model</span></span>
> - <span data-ttu-id="b5bc7-113">モデルを使用して予測する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="b5bc7-114">結果を見る</span><span class="sxs-lookup"><span data-stu-id="b5bc7-114">See the results</span></span>

<span data-ttu-id="b5bc7-115">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5bc7-116">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b5bc7-116">Prerequisites</span></span>

- <span data-ttu-id="b5bc7-117">[Visual Studio 2017 バージョン 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)が ".NET Core クロスプラット フォーム開発" ワークロードと共にインストールされている</span><span class="sxs-lookup"><span data-stu-id="b5bc7-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="b5bc7-118">[UCI Sentiment Labeled Sentences データセット](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP ファイル)</span><span class="sxs-lookup"><span data-stu-id="b5bc7-118">[UCI Sentiment Labeled Sentences dataset](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b5bc7-119">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-119">Create a console application</span></span>

1. <span data-ttu-id="b5bc7-120">"SentimentAnalysis" という名前の **.NET Core コンソール アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="b5bc7-121">データ セット ファイルを保存するために、プロジェクトに *Data* という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="b5bc7-122">**Microsoft.ML NuGet パッケージ** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="b5bc7-123">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b5bc7-124">パッケージ ソースとして "nuget.org" を選択してから、 **[参照]** タブを選択します。**Microsoft.ML** を検索し、目的のパッケージを選択して、 **[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="b5bc7-125">選択したパッケージのライセンス条項に同意してインストールを続行します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="b5bc7-126">データを準備する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-126">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="b5bc7-127">このチュートリアルのデータセットは、「From Group to Individual Labels using Deep Features」 (Kotzias 他</span><span class="sxs-lookup"><span data-stu-id="b5bc7-127">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="b5bc7-128">著、</span><span class="sxs-lookup"><span data-stu-id="b5bc7-128">al,.</span></span> <span data-ttu-id="b5bc7-129">KDD 2015) のものであり、UCI 機械学習リポジトリ (Dua, D. and Karra Taniskidou, E.(2017)) でホストされています。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-129">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="b5bc7-130">UCI 機械学習リポジトリ [http://archive.ics.uci.edu/ml ]。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-130">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="b5bc7-131">カリフォルニア州アーバイン: カリフォルニア大学情報コンピュータサイエンス学部。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-131">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="b5bc7-132">[UCI Sentiment Labeled Sentences データセットの ZIP ファイル](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)をダウンロードし、展開します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-132">Download [UCI Sentiment Labeled Sentences dataset ZIP file](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="b5bc7-133">`yelp_labelled.txt` ファイルを、作成した *Data* ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-133">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="b5bc7-134">ソリューション エクスプローラーで、`yelp_labeled.txt` ファイルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-134">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="b5bc7-135">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-135">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="b5bc7-136">クラスを作成してパスを定義する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-136">Create classes and define paths</span></span>

1. <span data-ttu-id="b5bc7-137">次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-137">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="b5bc7-138">`Main` メソッドの直前の行に次のコードを追加して、最近ダウンロードしたデータセット ファイルのパスを保持するフィールドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-138">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](./snippets/sentiment-analysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="b5bc7-139">次に、入力データと予測のためにクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-139">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="b5bc7-140">プロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-140">Add a new class to your project:</span></span>

    - <span data-ttu-id="b5bc7-141">**ソリューション エクスプローラー** で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-141">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="b5bc7-142">**[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを *SentimentData.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-142">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="b5bc7-143">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-143">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="b5bc7-144">コード エディターで *SentimentData.cs* ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-144">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="b5bc7-145">*SentimentData.cs* の先頭に次の `using` ステートメントを 追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-145">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="b5bc7-146">既存のクラス定義を削除し、`SentimentData` と `SentimentPrediction` の 2 つのクラスを含む次のコードを *SentimentData.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-146">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/sentiment-analysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="b5bc7-147">データの準備方法</span><span class="sxs-lookup"><span data-stu-id="b5bc7-147">How the data was prepared</span></span>

<span data-ttu-id="b5bc7-148">入力データセット クラスの `SentimentData` には、ユーザー コメント用の `string` (`SentimentText`) と、センチメント用の 1 (肯定的) または 0 (否定的) のいずれかの `bool` (`Sentiment`) 値があります。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-148">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="b5bc7-149">どちらのフィールドにも [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 属性が添付され、各フィールドのデータ ファイルの順序が記述されています。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-149">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="b5bc7-150">さらに、`Sentiment` プロパティには、それを `Label` フィールドとして指定する [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) 属性があります。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-150">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="b5bc7-151">次のファイル例にはヘッダー行がなく、次のような内容です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-151">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="b5bc7-152">SentimentText</span><span class="sxs-lookup"><span data-stu-id="b5bc7-152">SentimentText</span></span>                         |<span data-ttu-id="b5bc7-153">Sentiment (ラベル)</span><span class="sxs-lookup"><span data-stu-id="b5bc7-153">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="b5bc7-154">Waitress was a little slow in service.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-154">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="b5bc7-155">0</span><span class="sxs-lookup"><span data-stu-id="b5bc7-155">0</span></span>     |
|<span data-ttu-id="b5bc7-156">Crust is not good.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-156">Crust is not good.</span></span>                    |    <span data-ttu-id="b5bc7-157">0</span><span class="sxs-lookup"><span data-stu-id="b5bc7-157">0</span></span>     |
|<span data-ttu-id="b5bc7-158">Wow...Loved this place.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-158">Wow... Loved this place.</span></span>              |    <span data-ttu-id="b5bc7-159">1</span><span class="sxs-lookup"><span data-stu-id="b5bc7-159">1</span></span>     |
|<span data-ttu-id="b5bc7-160">Service was very prompt.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-160">Service was very prompt.</span></span>              |    <span data-ttu-id="b5bc7-161">1</span><span class="sxs-lookup"><span data-stu-id="b5bc7-161">1</span></span>     |

<span data-ttu-id="b5bc7-162">`SentimentPrediction` はモデルのトレーニング後に使用される予測クラスです。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-162">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="b5bc7-163">`SentimentData` から継承されるため、入力 `SentimentText` を出力予測と共に表示することができます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-163">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="b5bc7-164">`Prediction` ブール値は、新しい入力 `SentimentText` が指定されたときにモデルで予測される値です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-164">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="b5bc7-165">出力クラス `SentimentPrediction` にはモデルによって計算されたその他の 2 つのプロパティが含まれています。1 つはモデルによって計算された生のスコアの `Score`、もう 1 つは肯定的センチメントを持つテキストの尤度に調整されたスコアの `Probability` です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-165">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="b5bc7-166">このチュートリアルで最も重要なプロパティは `Prediction` です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-166">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="b5bc7-167">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="b5bc7-167">Load the data</span></span>

<span data-ttu-id="b5bc7-168">ML.NET 内のデータは、[IDataView クラス](xref:Microsoft.ML.IDataView)として表されます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-168">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="b5bc7-169">`IDataView` は、表形式のデータ (数値とテキスト) を表すための柔軟で効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-169">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="b5bc7-170">データはテキスト ファイルから、またはリアルタイムで (SQL データベースやログ ファイルなど) `IDataView` オブジェクトに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-170">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="b5bc7-171">[MLContext クラス](xref:Microsoft.ML.MLContext)は、すべての ML.NET 操作の始点です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-171">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="b5bc7-172">`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-172">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="b5bc7-173">これは Entity Framework における `DBContext` と概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-173">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="b5bc7-174">アプリを準備してからデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-174">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="b5bc7-175">`Main` メソッドの `Console.WriteLine("Hello World!")` の行は、mlContext 変数を宣言して初期化する次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-175">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/sentiment-analysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="b5bc7-176">`Main()` メソッドに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-176">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](./snippets/sentiment-analysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="b5bc7-177">`Main()` メソッドの直後に、次のコードを使用して `LoadData()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-177">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="b5bc7-178">`LoadData()` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-178">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="b5bc7-179">データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-179">Loads the data.</span></span>
    - <span data-ttu-id="b5bc7-180">読み込んだデータセットを、トレーニングデータセットとテスト データセットに分割します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-180">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="b5bc7-181">分割されたトレーニングデータセットとテスト データセットを返します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-181">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="b5bc7-182">`LoadData()` メソッドの最初の行として、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-182">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](./snippets/sentiment-analysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="b5bc7-183">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) メソッドを使用してデータ スキーマを定義し、ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-183">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) method defines the data schema and reads in the file.</span></span> <span data-ttu-id="b5bc7-184">データ パス変数を取得して、`IDataView` を返します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-184">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="b5bc7-185">モデルのトレーニング用とテスト用にデータセットを分割する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-185">Split the dataset for model training and testing</span></span>

<span data-ttu-id="b5bc7-186">モデルを準備するときは、データセットの一部を使用してモデルをトレーニングし、データセットの一部を使用してモデルの正確度をテストします。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-186">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="b5bc7-187">読み込まれたデータを必要なデータセットに分割するには、`LoadData()` メソッドの次の行として、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-187">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](./snippets/sentiment-analysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="b5bc7-188">前のコードでは、[TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) メソッドを使用して、読み込まれたデータセットをトレーニング データセットとテスト データセットに分割し、それらを <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> クラスで返します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-188">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> class.</span></span> <span data-ttu-id="b5bc7-189">`testFraction` パラメーターを使用して、データに占めるテスト セットの割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-189">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="b5bc7-190">既定値は 10% です。この場合、より多くのデータを評価するために 20% を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-190">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="b5bc7-191">`LoadData()` メソッドの最後に、`splitDataView` が返されます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-191">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](./snippets/sentiment-analysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="b5bc7-192">モデルを構築してトレーニングする</span><span class="sxs-lookup"><span data-stu-id="b5bc7-192">Build and train the model</span></span>

1. <span data-ttu-id="b5bc7-193">`Main()` メソッドの次のコード行として、`BuildAndTrainModel` メソッドに次の呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-193">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](./snippets/sentiment-analysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="b5bc7-194">`BuildAndTrainModel()` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-194">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="b5bc7-195">データを抽出して変換します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-195">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="b5bc7-196">モデルをトレーニングする。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-196">Trains the model.</span></span>
    - <span data-ttu-id="b5bc7-197">テスト データに基づいてセンチメントを予測する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-197">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="b5bc7-198">モデルを返します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-198">Returns the model.</span></span>

2. <span data-ttu-id="b5bc7-199">`Main()` メソッドの直後に、次のコードを使用して `BuildAndTrainModel()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-199">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="b5bc7-200">データを抽出して変換する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-200">Extract and transform the data</span></span>

1. <span data-ttu-id="b5bc7-201">次のコード行として `FeaturizeText` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-201">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](./snippets/sentiment-analysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="b5bc7-202">前のコードの `FeaturizeText()` メソッドでは、テキスト列 (`SentimentText`) を機械学習アルゴリズムから使用される数値キー型の `Features` 列に変換し、それを新しいデータセット列として追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-202">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="b5bc7-203">SentimentText</span><span class="sxs-lookup"><span data-stu-id="b5bc7-203">SentimentText</span></span>                         |<span data-ttu-id="b5bc7-204">Sentiment</span><span class="sxs-lookup"><span data-stu-id="b5bc7-204">Sentiment</span></span> |<span data-ttu-id="b5bc7-205">フィーチャー</span><span class="sxs-lookup"><span data-stu-id="b5bc7-205">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="b5bc7-206">Waitress was a little slow in service.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-206">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="b5bc7-207">0</span><span class="sxs-lookup"><span data-stu-id="b5bc7-207">0</span></span>     |<span data-ttu-id="b5bc7-208">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="b5bc7-208">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="b5bc7-209">Crust is not good.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-209">Crust is not good.</span></span>                    |    <span data-ttu-id="b5bc7-210">0</span><span class="sxs-lookup"><span data-stu-id="b5bc7-210">0</span></span>     |<span data-ttu-id="b5bc7-211">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="b5bc7-211">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="b5bc7-212">Wow...Loved this place.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-212">Wow... Loved this place.</span></span>              |    <span data-ttu-id="b5bc7-213">1</span><span class="sxs-lookup"><span data-stu-id="b5bc7-213">1</span></span>     |<span data-ttu-id="b5bc7-214">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="b5bc7-214">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="b5bc7-215">Service was very prompt.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-215">Service was very prompt.</span></span>              |    <span data-ttu-id="b5bc7-216">1</span><span class="sxs-lookup"><span data-stu-id="b5bc7-216">1</span></span>     |<span data-ttu-id="b5bc7-217">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="b5bc7-217">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="b5bc7-218">学習アルゴリズムを追加する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-218">Add a learning algorithm</span></span>

<span data-ttu-id="b5bc7-219">このアプリでは、データの項目または行を分類する分類アルゴリズムを使用しています。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-219">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="b5bc7-220">このアプリでは、Web サイトのコメントが肯定的または否定的に分類されるので、二項分類タスクが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-220">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="b5bc7-221">データ変換定義に機械学習タスクを追加するには、`BuildAndTrainModel()` の次のコード行に以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-221">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](./snippets/sentiment-analysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="b5bc7-222">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) が分類トレーニング アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-222">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="b5bc7-223">これは `estimator` に追加されます。また、特徴付けされた `SentimentText` (`Features`) と `Label` 入力パラメーターを受け取って履歴データから学習します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-223">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="b5bc7-224">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="b5bc7-224">Train the model</span></span>

<span data-ttu-id="b5bc7-225">`BuildAndTrainModel()` メソッドの次のコード行として以下を追加して、モデルを `splitTrainSet` データに適合させ、トレーニング済みモデルを返します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-225">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](./snippets/sentiment-analysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="b5bc7-226">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) メソッドでは、データセットを変換して、トレーニングを適用することにより、モデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-226">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="b5bc7-227">評価に使用する、トレーニング済みのモデルを返す</span><span class="sxs-lookup"><span data-stu-id="b5bc7-227">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="b5bc7-228">`BuildAndTrainModel()` メソッドの終了時にモデルを返します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-228">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](./snippets/sentiment-analysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="b5bc7-229">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-229">Evaluate the model</span></span>

<span data-ttu-id="b5bc7-230">モデルのトレーニングが終わったら、テスト データを使用してモデルのパフォーマンスを検証します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-230">After your model is trained, use your test data to validate the model's performance.</span></span>

1. <span data-ttu-id="b5bc7-231">`BuildAndTrainModel()` の直後に、次のコードを使用して `Evaluate()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-231">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="b5bc7-232">`Evaluate()` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-232">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="b5bc7-233">テスト データ セットを読み込む。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-233">Loads the test dataset.</span></span>
    - <span data-ttu-id="b5bc7-234">BinaryClassification エバリュエーターを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-234">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="b5bc7-235">モデルを評価し、メトリックを作成する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-235">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="b5bc7-236">メトリックを表示する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-236">Displays the metrics.</span></span>

2. <span data-ttu-id="b5bc7-237">`BuildAndTrainModel()` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main()` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-237">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](./snippets/sentiment-analysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="b5bc7-238">次のコードを `Evaluate()` に追加して、`splitTestSet` データを変換します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-238">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](./snippets/sentiment-analysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="b5bc7-239">前のコードでは、[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドを使用して、テスト データセットの指定した複数の入力行に対して予測しています。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-239">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="b5bc7-240">`Evaluate()` メソッドの次のコード行として以下を追加して、モデルを評価します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-240">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](./snippets/sentiment-analysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="b5bc7-241">予測セット (`predictions`) ができると、[Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A)メソッドによってモデルが評価され、予測値とテスト データセット内の実際の `Labels` が比較され、モデルのパフォーマンスに関する [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-241">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="b5bc7-242">モデル検証のためのメトリックを表示する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-242">Displaying the metrics for model validation</span></span>

<span data-ttu-id="b5bc7-243">次のコードを使用してメトリックを表示します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-243">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](./snippets/sentiment-analysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="b5bc7-244">`Accuracy` メトリックでは、モデルの正確度が取得されます。これは、テスト セットに含まれる正しい予測の割合です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-244">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="b5bc7-245">`AreaUnderRocCurve` メトリックは、そのモデルで肯定的クラスと否定的クラスが正しく分類されている信用度を示します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-245">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="b5bc7-246">`AreaUnderRocCurve` を可能な限り 1 に近づけることが目標です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-246">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="b5bc7-247">`F1Score` メトリックでは、モデルの F1 スコアが取得されます。これは[精度](../resources/glossary.md#precision)と[再現率](../resources/glossary.md#recall)間のバランスのメジャーです。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-247">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="b5bc7-248">`F1Score` を可能な限り 1 に近づけることが目標です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-248">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="b5bc7-249">テスト データの結果を予測する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-249">Predict the test data outcome</span></span>

1. <span data-ttu-id="b5bc7-250">`Evaluate()` メソッドの直後に、次のコードを使用して `UseModelWithSingleItem()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-250">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="b5bc7-251">`UseModelWithSingleItem()` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-251">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="b5bc7-252">テスト データの 1 つのコメントを作成する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-252">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="b5bc7-253">テスト データに基づいてセンチメントを予測する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-253">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="b5bc7-254">テスト データと予測をレポート用に結合する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-254">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="b5bc7-255">予測された結果を表示する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-255">Displays the predicted results.</span></span>

2. <span data-ttu-id="b5bc7-256">`Evaluate()` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main()` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-256">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="b5bc7-257">次のコードを追加して、`UseModelWithSingleItem()` メソッドの 1 行目として作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-257">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](./snippets/sentiment-analysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="b5bc7-258">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) は、データの 1 つのインスタンスに対して予測を実行できる便利な API です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-258">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="b5bc7-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) はスレッド セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="b5bc7-260">シングル スレッド環境またはプロトタイプ環境で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-260">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="b5bc7-261">運用環境でパフォーマンスとスレッド セーフを向上させるには、`PredictionEnginePool` サービスを使用します。これにより、アプリケーション全体で使用するできる [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) オブジェクトの [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-261">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="b5bc7-262">[ASP.NET Core Web API で `PredictionEnginePool` を使用する](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)方法については、こちらのガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-262">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b5bc7-263">`PredictionEnginePool` サービスの拡張機能は、現在プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-263">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="b5bc7-264">コメントを追加して、`UseModelWithSingleItem()` メソッドでトレーニングされたモデルの予測をテストします。これには `SentimentData` のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-264">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="b5bc7-265">`UseModelWithSingleItem()` メソッドの次のコード行として以下を追加して、テスト コメント データを [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) に渡します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-265">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="b5bc7-266">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 関数では、データの 1 つの行に対して予測を行います。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="b5bc7-267">次のコードを使用して、`SentimentText` とそれに対応するセンチメント予測を表示します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](./snippets/sentiment-analysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="b5bc7-268">予測にモデルを使用する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="b5bc7-269">バッチ項目の展開と予測</span><span class="sxs-lookup"><span data-stu-id="b5bc7-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="b5bc7-270">`UseModelWithSingleItem()` メソッドの直後に、次のコードを使用して `UseModelWithBatchItems()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="b5bc7-271">`UseModelWithBatchItems()` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="b5bc7-272">バッチ テスト データを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-272">Creates batch test data.</span></span>
    - <span data-ttu-id="b5bc7-273">テスト データに基づいてセンチメントを予測する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-273">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="b5bc7-274">テスト データと予測をレポート用に結合する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-274">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="b5bc7-275">予測された結果を表示する。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="b5bc7-276">`UseModelWithSingleItem()` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="b5bc7-277">`UseModelWithBatchItems()` メソッドでトレーニングされるモデルの予測をテストするために、いくつかのコメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="b5bc7-278">コメントのセンチメントを予測する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-278">Predict comment sentiment</span></span>

<span data-ttu-id="b5bc7-279">モデルを使用し、[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドを使用してコメント データのセンチメントを予測します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="b5bc7-280">予測を組み合わせて表示する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-280">Combine and display the predictions</span></span>

<span data-ttu-id="b5bc7-281">次のコードを使用して、予測のヘッダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](./snippets/sentiment-analysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="b5bc7-282">`SentimentPrediction` は `SentimentData` から継承されているため、`Transform()` メソッドによって `SentimentText` に予測されたフィールドが設定されました。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="b5bc7-283">ML.NET プロセスが進むにつれて、各コンポーネントに列が追加されます。これで、結果が簡単に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](./snippets/sentiment-analysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="b5bc7-284">結果</span><span class="sxs-lookup"><span data-stu-id="b5bc7-284">Results</span></span>

<span data-ttu-id="b5bc7-285">結果は以下のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-285">Your results should be similar to the following.</span></span> <span data-ttu-id="b5bc7-286">処理中にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-286">During processing, messages are displayed.</span></span> <span data-ttu-id="b5bc7-287">警告または処理メッセージが表示されることがありますが、</span><span class="sxs-lookup"><span data-stu-id="b5bc7-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="b5bc7-288">わかりやすくするために、それらは次の結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-288">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="b5bc7-289">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="b5bc7-289">Congratulations!</span></span> <span data-ttu-id="b5bc7-290">これで、メッセージのセンチメントを分類および予測するための機械学習モデルをビルドできました。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="b5bc7-291">優れたモデルの構築は、反復的なプロセスです。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="b5bc7-292">このチュートリアルでは、モデルのトレーニングを短時間で実行するために小さなデータセットを使用しているため、このモデルの品質は最初は低くなっています。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="b5bc7-293">このモデルの品質に満足できなければ、大規模なトレーニング データセットを使用するか、別のトレーニング アルゴリズムとアルゴリズムごとに異なる[ハイパーパラメーター](../resources/glossary.md#hyperparameter)を選択してモデルの改良を試すことができます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="b5bc7-294">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5bc7-295">次の手順</span><span class="sxs-lookup"><span data-stu-id="b5bc7-295">Next steps</span></span>

<span data-ttu-id="b5bc7-296">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b5bc7-297">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-297">Create a console application</span></span>
> - <span data-ttu-id="b5bc7-298">データの準備</span><span class="sxs-lookup"><span data-stu-id="b5bc7-298">Prepare data</span></span>
> - <span data-ttu-id="b5bc7-299">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="b5bc7-299">Load the data</span></span>
> - <span data-ttu-id="b5bc7-300">モデルを構築してトレーニングする</span><span class="sxs-lookup"><span data-stu-id="b5bc7-300">Build and train the model</span></span>
> - <span data-ttu-id="b5bc7-301">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-301">Evaluate the model</span></span>
> - <span data-ttu-id="b5bc7-302">モデルを使用して予測する</span><span class="sxs-lookup"><span data-stu-id="b5bc7-302">Use the model to make a prediction</span></span>
> - <span data-ttu-id="b5bc7-303">結果を見る</span><span class="sxs-lookup"><span data-stu-id="b5bc7-303">See the results</span></span>

<span data-ttu-id="b5bc7-304">さらに詳しく学習するには、次のチュートリアルに進んでください。</span><span class="sxs-lookup"><span data-stu-id="b5bc7-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b5bc7-305">問題の分類</span><span class="sxs-lookup"><span data-stu-id="b5bc7-305">Issue Classification</span></span>](github-issue-classification.md)
