---
title: 'チュートリアル: 自転車レンタル需要の予測 - 時系列'
description: このチュートリアルでは、一変量時系列解析と ML.NET を使用して、自転車レンタル サービスの需要を予測する方法について説明します。
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: aea264036ab4766696699980f464cca3d8229499
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875591"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="74e5b-103">チュートリアル: 時系列解析と ML.NET を使用して自転車レンタル サービスの需要を予測する</span><span class="sxs-lookup"><span data-stu-id="74e5b-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="74e5b-104">ML.NET を使用して SQL Server データベースに格納されているデータに対して、一変量時系列解析を使用して自転車レンタル サービスの需要を予測する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="74e5b-105">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="74e5b-106">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="74e5b-106">Understand the problem</span></span>
> * <span data-ttu-id="74e5b-107">データベースからデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="74e5b-107">Load data from a database</span></span>
> * <span data-ttu-id="74e5b-108">予測モデルを作成する</span><span class="sxs-lookup"><span data-stu-id="74e5b-108">Create a forecasting model</span></span>
> * <span data-ttu-id="74e5b-109">予測モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="74e5b-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="74e5b-110">予測モデルを保存する</span><span class="sxs-lookup"><span data-stu-id="74e5b-110">Save a forecasting model</span></span>
> * <span data-ttu-id="74e5b-111">予測モデルを使用する</span><span class="sxs-lookup"><span data-stu-id="74e5b-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74e5b-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="74e5b-112">Prerequisites</span></span>

- <span data-ttu-id="74e5b-113">".NET Core クロスプラットフォーム開発" ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 以降または Visual Studio 2017 バージョン 15.6 以降。</span><span class="sxs-lookup"><span data-stu-id="74e5b-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="74e5b-114">時系列予測のサンプルの概要</span><span class="sxs-lookup"><span data-stu-id="74e5b-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="74e5b-115">このサンプルは、特異スペクトル解析 (Singular Spectrum Analysis) と呼ばれる一変量時系列解析アルゴリズムを使用して、自転車のレンタルの需要を予測する、**C# .NET Core コンソール アプリケーション** です。</span><span class="sxs-lookup"><span data-stu-id="74e5b-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Singular Spectrum Analysis.</span></span> <span data-ttu-id="74e5b-116">このサンプルのコードについては、GitHub の [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand) リポジトリで見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="74e5b-117">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="74e5b-117">Understand the problem</span></span>

<span data-ttu-id="74e5b-118">効率的に事業を運営するには、在庫管理が重要な役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="74e5b-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="74e5b-119">製品の在庫が多すぎるということは、製品が棚に置かれたままで販売されず、何の収益も生み出さないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="74e5b-120">製品が少なすぎると、販売機会の損失や顧客が競合他社から購入することにつながります。</span><span class="sxs-lookup"><span data-stu-id="74e5b-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="74e5b-121">そのため、在庫を維持するための最適な量はどのくらいかということを常に問いかけます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="74e5b-122">時系列解析では、履歴データ、パターンの識別、およびこの情報を使用して、将来の値を予測することで、この質問に対する回答を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="74e5b-123">このチュートリアルで使用されているデータを解析するための手法は、一変量時系列解析です。</span><span class="sxs-lookup"><span data-stu-id="74e5b-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="74e5b-124">一変量時系列解析では、月単位の売上など、特定の間隔で一定の期間にわたって 1 つの数値の観測を調べます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="74e5b-125">このチュートリアルで使用されているアルゴリズムは、[特異スペクトル解析 (SSA: Singular Spectrum Analysis)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf) です。</span><span class="sxs-lookup"><span data-stu-id="74e5b-125">The algorithm used in this tutorial is [Singular Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="74e5b-126">SSA は、時系列を一連のプリンシパル コンポーネントに分解することによって機能します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="74e5b-127">これらのコンポーネントは、傾向、ノイズ、季節性、およびその他の多くの要因に対応するシグナルの部分として解釈することができます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="74e5b-128">その後、これらのコンポーネントは再構築され、将来の値の予測に使用されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="74e5b-129">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="74e5b-129">Create console application</span></span>

1. <span data-ttu-id="74e5b-130">"BikeDemandForecasting" という名前の新しい **C# .NET Core コンソール アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="74e5b-131">**Microsoft.ML** バージョン NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="74e5b-131">Install **Microsoft.ML** version NuGet package</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. <span data-ttu-id="74e5b-132">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="74e5b-133">[パッケージ ソース] として "nuget.org" を選択し、 **[参照]** タブを選択し、"**Microsoft.ML**" を検索します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="74e5b-134">**[プレリリースを含める]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="74e5b-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="74e5b-135">**[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="74e5b-136">**[変更のプレビュー]** ダイアログで **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、[ライセンスの同意] ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="74e5b-137">**System.Data.SqlClient** と **Microsoft.ML.TimeSeries** に対して、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-137">Repeat these steps for **System.Data.SqlClient** and **Microsoft.ML.TimeSeries**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="74e5b-138">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="74e5b-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="74e5b-139">*Data* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="74e5b-140">[*DailyDemand.mdf* データベース ファイル](https://github.com/dotnet/machinelearning-samples/raw/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf)をダウンロードし、*Data* ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="74e5b-141">このチュートリアルで使用されているデータは、[UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset) から取得したものです。</span><span class="sxs-lookup"><span data-stu-id="74e5b-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="74e5b-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web リンク](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3)。</span><span class="sxs-lookup"><span data-stu-id="74e5b-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="74e5b-143">元のデータセットには、季節性と天気に対応する複数の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="74e5b-144">簡潔にするため、またこのチュートリアルで使用されているアルゴリズムには 1 つの数値列の値しか必要ないため、元のデータセットは次の列のみが含まれるように圧縮されています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="74e5b-145">**dteday**:観察の日付。</span><span class="sxs-lookup"><span data-stu-id="74e5b-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="74e5b-146">**year**:観察のエンコードされた年 (0 = 2011、1 = 2012)。</span><span class="sxs-lookup"><span data-stu-id="74e5b-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="74e5b-147">**cnt**:その日にレンタルされた自転車の合計数。</span><span class="sxs-lookup"><span data-stu-id="74e5b-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="74e5b-148">元のデータセットは、SQL Server データベースの次のスキーマを持つデータベース テーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```sql
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="74e5b-149">データのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="74e5b-150">RentalDate</span><span class="sxs-lookup"><span data-stu-id="74e5b-150">RentalDate</span></span> | <span data-ttu-id="74e5b-151">Year</span><span class="sxs-lookup"><span data-stu-id="74e5b-151">Year</span></span> | <span data-ttu-id="74e5b-152">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="74e5b-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="74e5b-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="74e5b-153">1/1/2011</span></span>|<span data-ttu-id="74e5b-154">0</span><span class="sxs-lookup"><span data-stu-id="74e5b-154">0</span></span>|<span data-ttu-id="74e5b-155">985</span><span class="sxs-lookup"><span data-stu-id="74e5b-155">985</span></span>|
|<span data-ttu-id="74e5b-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="74e5b-156">1/2/2011</span></span>|<span data-ttu-id="74e5b-157">0</span><span class="sxs-lookup"><span data-stu-id="74e5b-157">0</span></span>|<span data-ttu-id="74e5b-158">801</span><span class="sxs-lookup"><span data-stu-id="74e5b-158">801</span></span>|
|<span data-ttu-id="74e5b-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="74e5b-159">1/3/2011</span></span>|<span data-ttu-id="74e5b-160">0</span><span class="sxs-lookup"><span data-stu-id="74e5b-160">0</span></span>|<span data-ttu-id="74e5b-161">1349</span><span class="sxs-lookup"><span data-stu-id="74e5b-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="74e5b-162">入力クラスと出力クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="74e5b-162">Create input and output classes</span></span>

1. <span data-ttu-id="74e5b-163">*Program.cs* ファイルを開き、既存の `using` ステートメントを次のステートメントに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="74e5b-164">`ModelInput` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-164">Create `ModelInput` class.</span></span> <span data-ttu-id="74e5b-165">`Program` クラスの下に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="74e5b-166">`ModelInput` クラスには、次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="74e5b-167">**RentalDate**:観察の日付。</span><span class="sxs-lookup"><span data-stu-id="74e5b-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="74e5b-168">**Year**:観察のエンコードされた年 (0 = 2011、1 = 2012)。</span><span class="sxs-lookup"><span data-stu-id="74e5b-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="74e5b-169">**TotalRentals**:その日にレンタルされた自転車の合計数。</span><span class="sxs-lookup"><span data-stu-id="74e5b-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="74e5b-170">新しく作成された `ModelInput` クラスの下に `ModelOutput` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="74e5b-171">`ModelOutput` クラスには、次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="74e5b-172">**ForecastedRentals**:予測期間の予測値。</span><span class="sxs-lookup"><span data-stu-id="74e5b-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="74e5b-173">**LowerBoundRentals**:予測期間の予測される最小値。</span><span class="sxs-lookup"><span data-stu-id="74e5b-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="74e5b-174">**UpperBoundRentals**:予測期間の予測される最大値。</span><span class="sxs-lookup"><span data-stu-id="74e5b-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="74e5b-175">パスを定義し、変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="74e5b-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="74e5b-176">`Main` メソッド内で、データの場所、接続文字列、およびトレーニング済みのモデルを保存する場所を格納する変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="74e5b-177">`Main` メソッドに次の行を追加して、[`MLContext`](xref:Microsoft.ML.MLContext) の新しいインスタンスで `mlContext` 変数を初期化します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="74e5b-178">[`MLContext`](xref:Microsoft.ML.MLContext) クラスは、すべての ML.NET 操作の開始点で、mlContext を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="74e5b-179">これは Entity Framework における `DBContext` と概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="74e5b-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="74e5b-180">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="74e5b-180">Load the data</span></span>

1. <span data-ttu-id="74e5b-181">`ModelInput` 型のレコードを読み込む `DatabaseLoader` を作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="74e5b-182">データベースからデータを読み込むクエリを定義します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="74e5b-183">ML.NET アルゴリズムでは、データが [`Single`](xref:System.Single) 型であることが想定されています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="74e5b-184">このため、データベースから取得された、[`Real`](xref:System.Data.SqlDbType) 型の単精度浮動小数点値ではない数値は [`Real`](xref:System.Data.SqlDbType) に変換される必要があります。</span><span class="sxs-lookup"><span data-stu-id="74e5b-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="74e5b-185">`Year` 列と `TotalRental` 列はどちらもデータベース内では整数型です。</span><span class="sxs-lookup"><span data-stu-id="74e5b-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="74e5b-186">`CAST` 組み込み関数を使用すると、どちらも `Real` にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="74e5b-187">データベースに接続してクエリを実行する `DatabaseSource` を作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="74e5b-188">`IDataView` にデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="74e5b-189">このデータセットには 2 年分のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="74e5b-190">トレーニングに使用されるのは 1 年目のデータのみで、2 年目のデータは、モデルによって生成された予測と実際の値を比較するために保持されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="74e5b-191">[`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) 変換を使用してデータをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="74e5b-192">1 年目に対しては、`upperBound` パラメーターを 1 に設定することによって、`Year` 列の 1 未満の値のみが選択されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="74e5b-193">反対に、2 年目に対しては、`lowerBound` パラメーターを 1 に設定することによって、1 以上の値が選択されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="74e5b-194">時系列解析パイプラインを定義する</span><span class="sxs-lookup"><span data-stu-id="74e5b-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="74e5b-195">[SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) を使用して時系列データセット内の値を予測するパイプラインを定義します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="74e5b-196">`forecastingPipeline` では、1 年目用の 365 のデータ ポイントとサンプルを取得するか、`seriesLength` パラメーターで指定された 30 日 (月単位) 間隔に時系列データセットを分割します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="74e5b-197">これらの各サンプルは、毎週または 7 日間の期間で解析されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="74e5b-198">次の期間の予測値がどのようになるかを判断する際には、前の 7 日間の値を使用して予測が行われます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="74e5b-199">モデルは、`horizon` パラメーターで定義されているように、7 つの期間を将来まで予測するように設定されています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="74e5b-200">予測は情報に基づいた推測であるため、100% 正確であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="74e5b-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="74e5b-201">したがって、上限と下限によって定義される最善のシナリオと最悪のシナリオにおける値の範囲を把握しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="74e5b-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="74e5b-202">この場合、下限と上限の信頼レベルは 95% に設定されています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="74e5b-203">信頼レベルは、状況に応じて増減できます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="74e5b-204">値が大きいほど、望ましい信頼レベルを達成するために上限と下限の範囲が広くなります。</span><span class="sxs-lookup"><span data-stu-id="74e5b-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="74e5b-205">[`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit%2A) メソッドを使用して、モデルをトレーニングし、以前に定義した `forecastingPipeline` にデータを適合させます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit%2A) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="74e5b-206">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="74e5b-206">Evaluate the model</span></span>

<span data-ttu-id="74e5b-207">来年のデータを予測し、それを実際の値と比較することによって、モデルのパフォーマンスを評価します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="74e5b-208">`Main` メソッドの下に、`Evaluate` という新しいユーティリティ メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="74e5b-209">`Evaluate` メソッド内で、トレーニング済みのモデルで [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドを使用して、2 年目のデータを予測します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="74e5b-210">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) メソッドを使用して、データから実際の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="74e5b-211">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) メソッドを使用して、予測値を取得します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="74e5b-212">実際の値と予測値の差を計算します (一般的にエラーと呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="74e5b-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="74e5b-213">平均絶対誤差値と二乗平均平方根誤差値を計算して、パフォーマンスを測定します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="74e5b-214">パフォーマンスを評価するため、次のメトリックが使用されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="74e5b-215">**平均絶対誤差**:予測が実際の値にどれだけ近いかを測定します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="74e5b-216">この値の範囲は 0 から無限大です。</span><span class="sxs-lookup"><span data-stu-id="74e5b-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="74e5b-217">0 に近いほど、モデルの品質が高くなります。</span><span class="sxs-lookup"><span data-stu-id="74e5b-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="74e5b-218">**二乗平均平方根誤差**:モデル内のエラーを集約します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="74e5b-219">この値の範囲は 0 から無限大です。</span><span class="sxs-lookup"><span data-stu-id="74e5b-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="74e5b-220">0 に近いほど、モデルの品質が高くなります。</span><span class="sxs-lookup"><span data-stu-id="74e5b-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="74e5b-221">メトリックをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="74e5b-222">`Main` メソッド内で `Evaluate` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="74e5b-223">モデルを保存する</span><span class="sxs-lookup"><span data-stu-id="74e5b-223">Save the model</span></span>

<span data-ttu-id="74e5b-224">モデルに問題がなければ、後で他のアプリケーションで使用できるように保存します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="74e5b-225">`Main` メソッドで、[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) を作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="74e5b-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) は、単一の予測を行うための便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="74e5b-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="74e5b-227">以前に定義した `modelPath` 変数によって指定された `MLModel.zip` という名前のファイルにモデルを保存します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="74e5b-228">[`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint%2A) メソッドを使用してモデルを保存します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint%2A) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="74e5b-229">モデルを使用して需要を予測する</span><span class="sxs-lookup"><span data-stu-id="74e5b-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="74e5b-230">`Evaluate` メソッドの下に、`Forecast` という新しいユーティリティ メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="74e5b-231">`Forecast` メソッド内で、[`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict%2A) メソッドを使用して、次の 7 日間のレンタルを予測します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict%2A) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="74e5b-232">7 つの期間の実際の値と予測値を合わせます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="74e5b-233">予測出力を反復処理し、コンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="74e5b-234">アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="74e5b-234">Run the application</span></span>

1. <span data-ttu-id="74e5b-235">`Main` メソッド内で、`Forecast` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="74e5b-236">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="74e5b-236">Run the application.</span></span> <span data-ttu-id="74e5b-237">次のような出力がコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="74e5b-238">簡潔にするため、出力は要約されています。</span><span class="sxs-lookup"><span data-stu-id="74e5b-238">For brevity, the output has been condensed.</span></span>

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

<span data-ttu-id="74e5b-239">実際の値と予測値を検査すると、次のリレーションシップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="74e5b-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![実際の値と予測値の比較](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="74e5b-241">予測値は、レンタルの正確な数を予測するものではありませんが、より絞り込んだ値の範囲が提供されるため、リソースの使用を最適化した事業が可能になります。</span><span class="sxs-lookup"><span data-stu-id="74e5b-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="74e5b-242">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="74e5b-242">Congratulations!</span></span> <span data-ttu-id="74e5b-243">これで、自転車のレンタル需要を予測するための時系列の機械学習モデルが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="74e5b-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="74e5b-244">このチュートリアルのソース コードは、[dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand) リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="74e5b-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="74e5b-245">次の手順</span><span class="sxs-lookup"><span data-stu-id="74e5b-245">Next steps</span></span>

- [<span data-ttu-id="74e5b-246">ML.NET での機械学習のタスク</span><span class="sxs-lookup"><span data-stu-id="74e5b-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="74e5b-247">モデルの正確度を改善する</span><span class="sxs-lookup"><span data-stu-id="74e5b-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
