---
title: 'チュートリアル: 回帰を使用して価格を予測する'
description: このチュートリアルでは、ML.NET を使用して、料金 (具体的にはニューヨーク市のタクシー運賃) を予測する回帰モデルを構築する方法を示します。
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: f8f7146241368edaca31afd970af54a098d1aafa
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874642"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="00a49-103">チュートリアル: ML.NET で回帰を使用して価格を予測する</span><span class="sxs-lookup"><span data-stu-id="00a49-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="00a49-104">このチュートリアルでは、ML.NET を使用して、料金 (具体的にはニューヨーク市のタクシー運賃) を予測する[回帰モデル](../resources/glossary.md#regression)を構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="00a49-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="00a49-105">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="00a49-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="00a49-106">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="00a49-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="00a49-107">データを読み込んで変換する</span><span class="sxs-lookup"><span data-stu-id="00a49-107">Load and transform the data</span></span>
> * <span data-ttu-id="00a49-108">学習アルゴリズムを選択する</span><span class="sxs-lookup"><span data-stu-id="00a49-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="00a49-109">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="00a49-109">Train the model</span></span>
> * <span data-ttu-id="00a49-110">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="00a49-110">Evaluate the model</span></span>
> * <span data-ttu-id="00a49-111">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="00a49-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00a49-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="00a49-112">Prerequisites</span></span>

* <span data-ttu-id="00a49-113">".NET Core クロスプラットフォーム開発" ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 以降または Visual Studio 2017 バージョン 15.6 以降。</span><span class="sxs-lookup"><span data-stu-id="00a49-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="00a49-114">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="00a49-114">Create a console application</span></span>

1. <span data-ttu-id="00a49-115">"TaxiFarePrediction" という名前の **.NET Core コンソール アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="00a49-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="00a49-116">プロジェクトに *Data* という名前のディレクトリを作成して、データ セットとモデルのファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="00a49-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="00a49-117">**Microsoft.ML** と **Microsoft.ML.FastTree** NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="00a49-117">Install the **Microsoft.ML** and **Microsoft.ML.FastTree** NuGet Package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="00a49-118">**ソリューション エクスプローラー** で、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="00a49-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="00a49-119">[パッケージ ソース] として [nuget.org] を選択します。 **[参照]** タブを選択し、「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、 **[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="00a49-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="00a49-120">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="00a49-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="00a49-121">**Microsoft.ML.FastTree** NuGet パッケージに対して同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="00a49-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="00a49-122">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="00a49-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="00a49-123">[taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/main/test/data/taxi-fare-train.csv) データ セットと [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/main/test/data/taxi-fare-test.csv) データ セットをダウンロードして、前の手順で作成済みの *Data* フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="00a49-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/main/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/main/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="00a49-124">これらのデータ セットを使用して、機械学習モデルをトレーニングし、モデルの正確度を評価します。</span><span class="sxs-lookup"><span data-stu-id="00a49-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="00a49-125">これらのデータ セットは、[NYC TLC Taxi Trip データ セット](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)から取得したものです。</span><span class="sxs-lookup"><span data-stu-id="00a49-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="00a49-126">**ソリューション エクスプローラー** で、各 \*.csv ファイルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="00a49-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="00a49-127">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="00a49-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="00a49-128">**taxi-fare-train.csv** データ セットを開き、最初の行の列ヘッダーを確認します。</span><span class="sxs-lookup"><span data-stu-id="00a49-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="00a49-129">各列を確認してください。</span><span class="sxs-lookup"><span data-stu-id="00a49-129">Take a look at each of the columns.</span></span> <span data-ttu-id="00a49-130">データについて把握し、どの列が **特徴** で、どの列が **ラベル** であるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="00a49-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="00a49-131">`label` は予測する列です。</span><span class="sxs-lookup"><span data-stu-id="00a49-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="00a49-132">識別された `Features` は、`Label` を予測するためにモデルを指定する入力です。</span><span class="sxs-lookup"><span data-stu-id="00a49-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="00a49-133">提供されているデータ セットには、次の列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="00a49-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="00a49-134">**vendor_id:** タクシー会社の ID は特徴です。</span><span class="sxs-lookup"><span data-stu-id="00a49-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="00a49-135">**rate_code:** タクシー旅行のレートの種類は特徴です。</span><span class="sxs-lookup"><span data-stu-id="00a49-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="00a49-136">**passenger_count:** 旅行の乗客数は特徴です。</span><span class="sxs-lookup"><span data-stu-id="00a49-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="00a49-137">**trip_time_in_secs:** 旅行の所要時間です。</span><span class="sxs-lookup"><span data-stu-id="00a49-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="00a49-138">旅行が終わる前に、旅行の運賃を予測したいと考えます。</span><span class="sxs-lookup"><span data-stu-id="00a49-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="00a49-139">その時点では、旅行の所要時間はわかりません。</span><span class="sxs-lookup"><span data-stu-id="00a49-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="00a49-140">したがって、旅行の所要時間は特徴ではなく、この列はモデルから除外します。</span><span class="sxs-lookup"><span data-stu-id="00a49-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="00a49-141">**trip_distance:** 旅行距離は特徴です。</span><span class="sxs-lookup"><span data-stu-id="00a49-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="00a49-142">**payment_type:** 支払い方法 (現金またはクレジット カード) は特徴です。</span><span class="sxs-lookup"><span data-stu-id="00a49-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="00a49-143">**fare_amount:** 支払った合計タクシー運賃はラベルです。</span><span class="sxs-lookup"><span data-stu-id="00a49-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="00a49-144">データ クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="00a49-144">Create data classes</span></span>

<span data-ttu-id="00a49-145">入力データと予測のためのクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="00a49-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="00a49-146">**ソリューション エクスプローラー** で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="00a49-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="00a49-147">**[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを *TaxiTrip.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="00a49-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="00a49-148">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="00a49-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="00a49-149">以下の `using` ディレクティブを新しいファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](./snippets/predict-prices/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="00a49-150">既存のクラス定義を削除し、2 つのクラス `TaxiTrip` と `TaxiTripFarePrediction` を含む次のコードを *TaxiTrip.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](./snippets/predict-prices/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="00a49-151">`TaxiTrip` は入力データ クラスであり、各データ セット列の定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="00a49-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="00a49-152"><xref:Microsoft.ML.Data.LoadColumnAttribute> 属性を使用して、データ セット内のソース列のインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="00a49-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="00a49-153">`TaxiTripFarePrediction` クラスは予測結果を表します。</span><span class="sxs-lookup"><span data-stu-id="00a49-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="00a49-154">このクラスには、`Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> 属性が適用された 1 つの浮動小数点型フィールド `FareAmount` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="00a49-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="00a49-155">回帰タスクの場合、**Score** 列には、予測ラベル値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="00a49-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="00a49-156">入力データと予測データのクラス内の浮動小数点値を表すには、`float` 型を使います。</span><span class="sxs-lookup"><span data-stu-id="00a49-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="00a49-157">データおよびモデルのパスを定義する</span><span class="sxs-lookup"><span data-stu-id="00a49-157">Define data and model paths</span></span>

<span data-ttu-id="00a49-158">次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](./snippets/predict-prices/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="00a49-159">データ セットを含むファイルのパスとモデルを保存するファイルのパスを保持するための 3 つのフィールドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00a49-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="00a49-160">`_trainDataPath` には、モデルのトレーニングに使用するデータ セットがあるファイルへのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="00a49-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="00a49-161">`_testDataPath` には、モデルの評価に使用するデータ セットがあるファイルへのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="00a49-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="00a49-162">`_modelPath` には、トレーニング済みモデルが格納されるファイルへのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="00a49-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="00a49-163">`Main` メソッドのすぐ上に次のコードを追加して、それらのパスと `_textLoader` 変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="00a49-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](./snippets/predict-prices/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="00a49-164">すべての ML.NET 操作は、[MLContext クラス](xref:Microsoft.ML.MLContext)で始まります。</span><span class="sxs-lookup"><span data-stu-id="00a49-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="00a49-165">`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="00a49-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="00a49-166">これは Entity Framework における `DBContext` と概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="00a49-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="00a49-167">Main で変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="00a49-167">Initialize variables in Main</span></span>

<span data-ttu-id="00a49-168">`Main` メソッド内の `Console.WriteLine("Hello World!")` の行は、`mlContext` 変数を宣言して初期化する次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="00a49-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](./snippets/predict-prices/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="00a49-169">`Main` メソッドに次のコード行を追加して、`Train` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="00a49-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](./snippets/predict-prices/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="00a49-170">`Train()` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00a49-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="00a49-171">データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="00a49-171">Loads the data.</span></span>
* <span data-ttu-id="00a49-172">データを抽出して変換します。</span><span class="sxs-lookup"><span data-stu-id="00a49-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="00a49-173">モデルをトレーニングする。</span><span class="sxs-lookup"><span data-stu-id="00a49-173">Trains the model.</span></span>
* <span data-ttu-id="00a49-174">モデルを返します。</span><span class="sxs-lookup"><span data-stu-id="00a49-174">Returns the model.</span></span>

<span data-ttu-id="00a49-175">`Train` メソッドは、モデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="00a49-175">The `Train` method trains the model.</span></span> <span data-ttu-id="00a49-176">次のコードを使用して、`Main` の直下にそのメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="00a49-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="00a49-177">データを読み込んで変換する</span><span class="sxs-lookup"><span data-stu-id="00a49-177">Load and transform data</span></span>

<span data-ttu-id="00a49-178">ML.NET では、数値またはテキストの表形式データを記述する柔軟で効率的な方法として、[IDataView クラス](xref:Microsoft.ML.IDataView)を使います。</span><span class="sxs-lookup"><span data-stu-id="00a49-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="00a49-179">`IDataView` は、テキスト ファイルを読み込むか、またはリアルタイムで読み込むことができます (たとえば、SQL データベースまたはログ ファイル)。</span><span class="sxs-lookup"><span data-stu-id="00a49-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="00a49-180">`Train()` メソッドの最初の行として、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](./snippets/predict-prices/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="00a49-181">タクシー運賃を予測したいので、`FareAmount` 列は、予測する `Label` です (モデルの出力)。</span><span class="sxs-lookup"><span data-stu-id="00a49-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="00a49-182">`CopyColumnsEstimator` 変換クラスを使って `FareAmount` をコピーし、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](./snippets/predict-prices/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="00a49-183">モデルをトレーニングするアルゴリズムには、**数値** の特徴が必要であるため、カテゴリ データ (`VendorId`、`RateCode`、および `PaymentType`) の値を数値 (`VendorIdEncoded`、`RateCodeEncoded`、および`PaymentTypeEncoded`) に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00a49-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="00a49-184">それを行うには、異なる数値キーの値を各列内の異なる値に割り当てる [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) 変換クラスを使用し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](./snippets/predict-prices/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="00a49-185">データの準備の最後の手順では、`mlContext.Transforms.Concatenate` 変換クラスを使用して、すべての特徴列を **Features** 列に結合します。</span><span class="sxs-lookup"><span data-stu-id="00a49-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="00a49-186">既定では、学習アルゴリズムは **Features** 列の特徴のみを処理します。</span><span class="sxs-lookup"><span data-stu-id="00a49-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="00a49-187">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](./snippets/predict-prices/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="00a49-188">学習アルゴリズムを選択する</span><span class="sxs-lookup"><span data-stu-id="00a49-188">Choose a learning algorithm</span></span>

<span data-ttu-id="00a49-189">この問題の中心となるのは、ニューヨーク市のタクシー運賃の予測です。</span><span class="sxs-lookup"><span data-stu-id="00a49-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="00a49-190">一見すると、単に乗車距離に依存すると思われるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="00a49-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="00a49-191">しかし、ニューヨークのタクシー会社は追加の乗客数や現金でなくクレジット カードによる支払いなど、その他の要因によって請求額を変えます。</span><span class="sxs-lookup"><span data-stu-id="00a49-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="00a49-192">データ セット内の他の要因に基づき、実際の値である価格値を予測します。</span><span class="sxs-lookup"><span data-stu-id="00a49-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="00a49-193">それを行うには、[回帰](../resources/glossary.md#regression)機械学習タスクを選択します。</span><span class="sxs-lookup"><span data-stu-id="00a49-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="00a49-194">`Train()` 内に次のコード行として以下を追加することで、データ変換定義に [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) 機械学習タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](./snippets/predict-prices/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="00a49-195">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="00a49-195">Train the model</span></span>

<span data-ttu-id="00a49-196">`Train()` メソッドに次のコード行を追加して、モデルをトレーニング `dataview` に適合させ、トレーニング済みモデルを返します。</span><span class="sxs-lookup"><span data-stu-id="00a49-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](./snippets/predict-prices/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="00a49-197">[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) メソッドでは、データセットを変換して、トレーニングを適用することにより、モデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="00a49-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="00a49-198">`Train()` メソッドで次のコード行を使用して、トレーニング済みモデルを返します。</span><span class="sxs-lookup"><span data-stu-id="00a49-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](./snippets/predict-prices/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="00a49-199">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="00a49-199">Evaluate the model</span></span>

<span data-ttu-id="00a49-200">次に、品質保証と検証のためのテスト データを使って、モデルのパフォーマンスを評価します。</span><span class="sxs-lookup"><span data-stu-id="00a49-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="00a49-201">次のコードを利用して、`Train()` の直後に `Evaluate()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="00a49-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="00a49-202">`Evaluate` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00a49-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="00a49-203">テスト データ セットを読み込む。</span><span class="sxs-lookup"><span data-stu-id="00a49-203">Loads the test dataset.</span></span>
* <span data-ttu-id="00a49-204">回帰エバリュエーターを作成する。</span><span class="sxs-lookup"><span data-stu-id="00a49-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="00a49-205">モデルを評価し、メトリックを作成する。</span><span class="sxs-lookup"><span data-stu-id="00a49-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="00a49-206">メトリックを表示する。</span><span class="sxs-lookup"><span data-stu-id="00a49-206">Displays the metrics.</span></span>

<span data-ttu-id="00a49-207">`Train` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](./snippets/predict-prices/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="00a49-208">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) メソッドを使って、テスト データセットを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="00a49-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="00a49-209">次のコードを `Evaluate` メソッドに追加することで、このデータセットを品質チェックとして使って、モデルを評価します。</span><span class="sxs-lookup"><span data-stu-id="00a49-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](./snippets/predict-prices/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="00a49-210">次に、以下のコードを `Evaluate()` に追加して、`Test` データを変換します。</span><span class="sxs-lookup"><span data-stu-id="00a49-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](./snippets/predict-prices/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="00a49-211">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドによって、テスト データセットの入力行に対する予測が行われます。</span><span class="sxs-lookup"><span data-stu-id="00a49-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="00a49-212">`RegressionContext.Evaluate` メソッドは、指定されたデータセットを使用して `PredictionModel` の品質メトリックを計算します。</span><span class="sxs-lookup"><span data-stu-id="00a49-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="00a49-213">これによって返される <xref:Microsoft.ML.Data.RegressionMetrics> オブジェクトには、回帰エバリュエーターによって計算されるメトリック全体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="00a49-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="00a49-214">これらを表示してモデルの品質を判定するには、最初にメトリックを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00a49-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="00a49-215">`Evaluate` メソッドに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](./snippets/predict-prices/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="00a49-216">予測セットができたら、[Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) メソッドがモデルを評価します。これは予測された値をテスト データセット内の実際の `Labels` と比較して、モデルのパフォーマンスのメトリックを返します。</span><span class="sxs-lookup"><span data-stu-id="00a49-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="00a49-217">次のコードを追加してモデルを評価し、評価メトリックを生成します。</span><span class="sxs-lookup"><span data-stu-id="00a49-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="00a49-218">[RSquared](../resources/glossary.md#coefficient-of-determination) は回帰モデルのもう 1 つの評価メトリックです。</span><span class="sxs-lookup"><span data-stu-id="00a49-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="00a49-219">RSquared は 0 から 1 までの値を取ります。</span><span class="sxs-lookup"><span data-stu-id="00a49-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="00a49-220">値が 1 に近づくほど、優れたモデルになります。</span><span class="sxs-lookup"><span data-stu-id="00a49-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="00a49-221">次のコードを `Evaluate` メソッドに追加して、RSquared 値を表示します。</span><span class="sxs-lookup"><span data-stu-id="00a49-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](./snippets/predict-prices/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="00a49-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) は回帰モデルの評価メトリックの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="00a49-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="00a49-223">RMS が低いほど、優れたモデルになります。</span><span class="sxs-lookup"><span data-stu-id="00a49-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="00a49-224">`Evaluate` メソッドに次のコードを追加することで、RMS 値を表示します。</span><span class="sxs-lookup"><span data-stu-id="00a49-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](./snippets/predict-prices/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="00a49-225">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="00a49-225">Use the model for predictions</span></span>

<span data-ttu-id="00a49-226">`Evaluate` メソッドの直後に、次のコードを使用して `TestSinglePrediction` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="00a49-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="00a49-227">`TestSinglePrediction` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00a49-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="00a49-228">テスト データの 1 つのコメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="00a49-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="00a49-229">テスト データに基づいて運賃合計を予測します。</span><span class="sxs-lookup"><span data-stu-id="00a49-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="00a49-230">テスト データと予測をレポート用に結合する。</span><span class="sxs-lookup"><span data-stu-id="00a49-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="00a49-231">予測された結果を表示する。</span><span class="sxs-lookup"><span data-stu-id="00a49-231">Displays the predicted results.</span></span>

<span data-ttu-id="00a49-232">`Evaluate` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](./snippets/predict-prices/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="00a49-233">次のコードを `TestSinglePrediction()` に追加することで、`PredictionEngine` を使って運賃を予測します。</span><span class="sxs-lookup"><span data-stu-id="00a49-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](./snippets/predict-prices/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="00a49-234">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) は、データの 1 つのインスタンスに対して予測を実行できる便利な API です。</span><span class="sxs-lookup"><span data-stu-id="00a49-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="00a49-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) はスレッド セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="00a49-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="00a49-236">シングル スレッド環境またはプロトタイプ環境で使用できます。</span><span class="sxs-lookup"><span data-stu-id="00a49-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="00a49-237">運用環境でパフォーマンスとスレッド セーフを向上させるには、`PredictionEnginePool` サービスを使用します。これにより、アプリケーション全体で使用するできる [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) オブジェクトの [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="00a49-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="00a49-238">[ASP.NET Core Web API で `PredictionEnginePool` を使用する](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)方法については、こちらのガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="00a49-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="00a49-239">`PredictionEnginePool` サービスの拡張機能は、現在プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="00a49-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="00a49-240">このチュートリアルでは、このクラス内の 1 つのテスト用の旅行を使用します。</span><span class="sxs-lookup"><span data-stu-id="00a49-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="00a49-241">モデルを試行するために後で他のシナリオを追加できます。</span><span class="sxs-lookup"><span data-stu-id="00a49-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="00a49-242">`TaxiTrip` のインスタンスを作成して、`TestSinglePrediction()` メソッドでコストのトレーニング済みモデルの予測をテストするために、旅行を追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](./snippets/predict-prices/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="00a49-243">次に、`TestSinglePrediction()` メソッドの次のコード行として以下を追加して、タクシー乗車データの 1 つのインスタンスに基づいて運賃を予測し、それを `PredictionEngine` に渡します。</span><span class="sxs-lookup"><span data-stu-id="00a49-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="00a49-244">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 関数では、データの 1 つのインスタンスに対して予測を行います。</span><span class="sxs-lookup"><span data-stu-id="00a49-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="00a49-245">指定された旅行の予測運賃を表示するために、次のコードを `TestSinglePrediction` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="00a49-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="00a49-246">プログラムを実行し、テスト ケースに対して予測されたタクシー運賃を確認します。</span><span class="sxs-lookup"><span data-stu-id="00a49-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="00a49-247">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="00a49-247">Congratulations!</span></span> <span data-ttu-id="00a49-248">これで、タクシー旅行運賃を予測する機械学習モデルが正常に構築され、その正確度が評価され、このモデルを使用した予測が行われました。</span><span class="sxs-lookup"><span data-stu-id="00a49-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="00a49-249">このチュートリアルのソース コードは、[dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TaxiFarePrediction) GitHub リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="00a49-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="00a49-250">次の手順</span><span class="sxs-lookup"><span data-stu-id="00a49-250">Next steps</span></span>

<span data-ttu-id="00a49-251">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="00a49-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="00a49-252">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="00a49-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="00a49-253">学習パイプラインを作成する</span><span class="sxs-lookup"><span data-stu-id="00a49-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="00a49-254">データを読み込んで変換する</span><span class="sxs-lookup"><span data-stu-id="00a49-254">Load and transform the data</span></span>
> * <span data-ttu-id="00a49-255">学習アルゴリズムを選択する</span><span class="sxs-lookup"><span data-stu-id="00a49-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="00a49-256">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="00a49-256">Train the model</span></span>
> * <span data-ttu-id="00a49-257">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="00a49-257">Evaluate the model</span></span>
> * <span data-ttu-id="00a49-258">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="00a49-258">Use the model for predictions</span></span>

<span data-ttu-id="00a49-259">さらに詳しく学習するには、次のチュートリアルに進んでください。</span><span class="sxs-lookup"><span data-stu-id="00a49-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="00a49-260">アヤメのクラスタリング</span><span class="sxs-lookup"><span data-stu-id="00a49-260">Iris clustering</span></span>](iris-clustering.md)
