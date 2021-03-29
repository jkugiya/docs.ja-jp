---
title: 'チュートリアル: モデル ビルダーで回帰を使用して価格を予測する'
description: このチュートリアルでは、ML.NET モデル ビルダーを使用して、価格 (具体的にはニューヨーク市のタクシー運賃) を予測する回帰モデルを構築する方法を示します。
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: c34586014b5617f7712a4b708cb2e4a4814da684
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874759"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="68441-103">チュートリアル: モデル ビルダーで回帰を使用して価格を予測する</span><span class="sxs-lookup"><span data-stu-id="68441-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="68441-104">ML.NET モデル ビルダーを使用して、価格を予測する回帰モデルを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="68441-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="68441-105">このチュートリアルで開発する .NET コンソール アプリでは、過去のニューヨーク市のタクシー運賃データに基づいてタクシー運賃を予測します。</span><span class="sxs-lookup"><span data-stu-id="68441-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="68441-106">モデル ビルダーの価格予測テンプレートは、数値による予測値を必要とするすべてのシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="68441-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="68441-107">シナリオの例には、住宅価格の予測、需要予測、売上予測などがあります。</span><span class="sxs-lookup"><span data-stu-id="68441-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="68441-108">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="68441-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="68441-109">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="68441-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="68441-110">シナリオを選択する</span><span class="sxs-lookup"><span data-stu-id="68441-110">Choose a scenario</span></span>
> - <span data-ttu-id="68441-111">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="68441-111">Load the data</span></span>
> - <span data-ttu-id="68441-112">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="68441-112">Train the model</span></span>
> - <span data-ttu-id="68441-113">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="68441-113">Evaluate the model</span></span>
> - <span data-ttu-id="68441-114">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="68441-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="68441-115">モデル ビルダーは現在のところ、プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="68441-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="68441-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="68441-116">Pre-requisites</span></span>

<span data-ttu-id="68441-117">前提条件の一覧とインストール手順は、[モデル ビルダーのインストール ガイド](../how-to-guides/install-model-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68441-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="68441-118">コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="68441-118">Create a console application</span></span>

1. <span data-ttu-id="68441-119">"TaxiFarePrediction" という名前の **C# .NET Core コンソール アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="68441-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="68441-120">**[ソリューションとプロジェクトを同じディレクトリに配置する]** を **オフ** (VS 2019) にします。または、 **[ソリューションのディレクトリの作成]** を **オン** にします (VS 2017)。</span><span class="sxs-lookup"><span data-stu-id="68441-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="68441-121">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="68441-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="68441-122">プロジェクトに *Data* という名前のディレクトリを作成して、データ セットのファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="68441-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="68441-123">機械学習モデルのトレーニングと評価に使用するデータ セットは、NYC TLC Taxi Trip データ セットから取得したものです。</span><span class="sxs-lookup"><span data-stu-id="68441-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="68441-124">このデータ セットをダウンロードするには、[taxi-fare-train.csv のダウンロード リンク](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/taxi-fare-train.csv)に移動します。</span><span class="sxs-lookup"><span data-stu-id="68441-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="68441-125">ページが読み込まれたら、ページ上の任意の場所を右クリックして、**[名前を付けて保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68441-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="68441-126">**[名前を付けて保存] ダイアログ** を使って、前の手順で作成した *Data* フォルダーにファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="68441-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="68441-127">**ソリューション エクスプローラー** で、*[taxi-fare-train.csv]* ファイルを右クリックし、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68441-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="68441-128">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="68441-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="68441-129">`taxi-fare-train.csv` データ セットの各行に、タクシーの移動の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="68441-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="68441-130">**taxi-fare-train.csv** データ セットを開きます</span><span class="sxs-lookup"><span data-stu-id="68441-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="68441-131">提供されているデータ セットには、次の列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="68441-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="68441-132">**vendor_id:** タクシー会社の ID は特徴です。</span><span class="sxs-lookup"><span data-stu-id="68441-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="68441-133">**rate_code:** タクシー旅行のレートの種類は特徴です。</span><span class="sxs-lookup"><span data-stu-id="68441-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="68441-134">**passenger_count:** 旅行の乗客数は特徴です。</span><span class="sxs-lookup"><span data-stu-id="68441-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="68441-135">**trip_time_in_secs:** 旅行の所要時間です。</span><span class="sxs-lookup"><span data-stu-id="68441-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="68441-136">旅行が終わる前に、旅行の運賃を予測したいと考えます。</span><span class="sxs-lookup"><span data-stu-id="68441-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="68441-137">その時点では、旅行の所要時間はわかりません。</span><span class="sxs-lookup"><span data-stu-id="68441-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="68441-138">したがって、旅行の所要時間は特徴ではなく、この列はモデルから除外します。</span><span class="sxs-lookup"><span data-stu-id="68441-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="68441-139">**trip_distance:** 旅行距離は特徴です。</span><span class="sxs-lookup"><span data-stu-id="68441-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="68441-140">**payment_type:** 支払い方法 (現金またはクレジット カード) は特徴です。</span><span class="sxs-lookup"><span data-stu-id="68441-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="68441-141">**fare_amount:** 支払った合計タクシー運賃はラベルです。</span><span class="sxs-lookup"><span data-stu-id="68441-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="68441-142">`label` は予測する列です。</span><span class="sxs-lookup"><span data-stu-id="68441-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="68441-143">回帰タスクを実行する場合の目標は、数値を予測することです。</span><span class="sxs-lookup"><span data-stu-id="68441-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="68441-144">この価格予測シナリオでは、タクシーの乗車のコストが予測されています。</span><span class="sxs-lookup"><span data-stu-id="68441-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="68441-145">したがって、**fare_amount** がラベルです。</span><span class="sxs-lookup"><span data-stu-id="68441-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="68441-146">識別された `features` は、`label` を予測するためにモデルを指定する入力です。</span><span class="sxs-lookup"><span data-stu-id="68441-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="68441-147">この場合、**trip_time_in_secs** を除く残りの列は、料金の合計を予測する特徴または入力として使用されます。</span><span class="sxs-lookup"><span data-stu-id="68441-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="68441-148">シナリオを選択する</span><span class="sxs-lookup"><span data-stu-id="68441-148">Choose a scenario</span></span>

<span data-ttu-id="68441-149">モデルをトレーニングするには、モデル ビルダーによって提供される機械学習シナリオの一覧から選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68441-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="68441-150">この場合、シナリオは `Price Prediction` です。</span><span class="sxs-lookup"><span data-stu-id="68441-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="68441-151">**ソリューション エクスプローラー** で、*[TaxiFarePrediction]* プロジェクトを右クリックし、**[追加]** > **[機械学習]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68441-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="68441-152">モデル ビルダー ツールのシナリオの手順で、*価格の予測* のシナリオを選択します。</span><span class="sxs-lookup"><span data-stu-id="68441-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="68441-153">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="68441-153">Load the data</span></span>

<span data-ttu-id="68441-154">モデル ビルダーは、SQL Server データベースか、csv または tsv 形式のローカル ファイルという 2 つのソースからデータを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="68441-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="68441-155">モデル ビルダー ツールのデータの手順で、データ ソースのドロップダウンから *[ファイル]* を選択します。</span><span class="sxs-lookup"><span data-stu-id="68441-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="68441-156">*[ファイルの選択]* テキスト ボックスの横にあるボタンを選択し、ファイル エクスプローラーを使用して *Data* ディレクトリにある *[taxi-fare-test.csv]* を参照し、選択します</span><span class="sxs-lookup"><span data-stu-id="68441-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="68441-157">*[Column to Predict (Label)]\(予測する列 (ラベル)\)* ドロップダウンで *[fare_amount]* を選択します。</span><span class="sxs-lookup"><span data-stu-id="68441-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="68441-158">*[Input Columns (Features)]\(入力列 (特徴)\)* ドロップダウンを展開し、*[trip_time_in_secs]* 列をオフにして、トレーニング時の特徴から除外します。</span><span class="sxs-lookup"><span data-stu-id="68441-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="68441-159">Model Builder ツールのトレーニング ステップに移動します。</span><span class="sxs-lookup"><span data-stu-id="68441-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="68441-160">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="68441-160">Train the model</span></span>

<span data-ttu-id="68441-161">このチュートリアルで、価格予測モデルのトレーニングに使用する機械学習のタスクは、回帰です。</span><span class="sxs-lookup"><span data-stu-id="68441-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="68441-162">モデルのトレーニング プロセス中、モデル ビルダーは、さまざまな回帰アルゴリズムと設定を使用して、データセットで最も良いパフォーマンスのモデルを見つける個別のモデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="68441-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="68441-163">モデルのトレーニングに必要な時間は、データの量に比例します。</span><span class="sxs-lookup"><span data-stu-id="68441-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="68441-164">モデル ビルダーにより、 **[Time to train (seconds)]\(トレーニング時間 (秒)\)** の既定値が、データ ソースのサイズに基づいて自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="68441-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="68441-165">より長い時間トレーニングする場合を除き、*[Time to train (seconds)]\(トレーニング時間 (秒)\)* は既定値のままとします。</span><span class="sxs-lookup"><span data-stu-id="68441-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="68441-166">*[Start Training]\(トレーニング開始\)* を選択します。</span><span class="sxs-lookup"><span data-stu-id="68441-166">Select *Start Training*.</span></span>

<span data-ttu-id="68441-167">トレーニング プロセスを通して、進捗データがトレーニングの手順の `Progress` セクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="68441-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="68441-168">状態には、トレーニング プロセスの完了ステータスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="68441-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="68441-169">[Best accuracy]\(最良の精度\) には、これまでにモデル ビルダーで見つかった最良のパフォーマンスのモデルの精度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="68441-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="68441-170">精度が高くなるほど、テスト データでモデルが正確に予測されたことになります。</span><span class="sxs-lookup"><span data-stu-id="68441-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="68441-171">[Best algorithm]\(最良のアルゴリズム\) には、これまでにモデル ビルダーで見つかった最良のパフォーマンスのアルゴリズムの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="68441-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="68441-172">[Last algorithm]\(最後のアルゴリズム\) には、モデル ビルダーがモデルのトレーニングに最近使用したアルゴリズムの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="68441-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="68441-173">トレーニングが完了したら、評価の手順に移動します。</span><span class="sxs-lookup"><span data-stu-id="68441-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="68441-174">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="68441-174">Evaluate the model</span></span>

<span data-ttu-id="68441-175">トレーニングの手順の結果が、最良のパフォーマンスだった 1 つのモデルになります。</span><span class="sxs-lookup"><span data-stu-id="68441-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="68441-176">モデル ビルダー ツールの評価の手順の出力セクションには、*[Best Model]\(最良のモデル\)* エントリの最良のパフォーマンスのモデルで使用されたアルゴリズムと、*[Best Model Quality (RSquared)]\(最良のモデル品質 (RSquared)\)* のメトリックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="68441-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="68441-177">また、概要テーブルには上位 5 つのモデルとそのメトリックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="68441-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="68441-178">精度のメトリックに不満がある場合、モデルのトレーニング時間を増やすか、さらに多くのデータを使用すると、モデルの精度を簡単に高めることができます。</span><span class="sxs-lookup"><span data-stu-id="68441-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="68441-179">そうでない場合は、コードの手順に移動します。</span><span class="sxs-lookup"><span data-stu-id="68441-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="68441-180">予測を行うコードを追加する</span><span class="sxs-lookup"><span data-stu-id="68441-180">Add the code to make predictions</span></span>

<span data-ttu-id="68441-181">トレーニング プロセスの結果として 2 つのプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="68441-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="68441-182">TaxiFarePredictionML.ConsoleApp: モデルのトレーニングとサンプルの使用に関するコードが含まれている .NET Core コンソール アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="68441-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="68441-183">TaxiFarePredictionML.Model: 入力および出力モデル データのスキーマを定義するデータ モデル、トレーニング中に最も高速であったモデルの保存されたバージョン、予測を行うために `ConsumeModel` を呼び出したヘルパー クラスが含まれている .NET Standard クラス ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="68441-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="68441-184">モデル ビルダー ツールのコードの手順で、 **[プロジェクトの追加]** を選択して、自動生成されたプロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="68441-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="68441-185">*[TaxiFarePrediction]* プロジェクトの *[Program.cs]* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="68441-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="68441-186">*TaxiFarePredictionML.Model* プロジェクトを参照する次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="68441-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="68441-187">新しいデータに対してモデルを使用して予測を行うには、アプリケーションの `ModelInput` メソッド内に `Main` クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="68441-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="68441-188">運賃額が入力に含まれていないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="68441-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="68441-189">これは、モデルによってその予測が生成されるためです。</span><span class="sxs-lookup"><span data-stu-id="68441-189">This is because the model will generate the prediction for it.</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. <span data-ttu-id="68441-190">`ConsumeModel` クラスの `Predict` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="68441-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="68441-191">`Predict` メソッドでは、トレーニング済みモデルを読み込み、モデルに対して [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) を作成し、新しいデータに対してそれを使用して予測を行います。</span><span class="sxs-lookup"><span data-stu-id="68441-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="68441-192">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="68441-192">Run the application.</span></span>

    <span data-ttu-id="68441-193">プログラムによって生成される出力は次のスニペットのようになります。</span><span class="sxs-lookup"><span data-stu-id="68441-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="68441-194">別のソリューション内で後で生成されたプロジェクトを参照する必要がある場合は、`C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` ディレクトリを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="68441-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="68441-195">次の手順</span><span class="sxs-lookup"><span data-stu-id="68441-195">Next Steps</span></span>

<span data-ttu-id="68441-196">このチュートリアルでは、以下の内容を学習しました。</span><span class="sxs-lookup"><span data-stu-id="68441-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="68441-197">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="68441-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="68441-198">シナリオを選択する</span><span class="sxs-lookup"><span data-stu-id="68441-198">Choose a scenario</span></span>
> - <span data-ttu-id="68441-199">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="68441-199">Load the data</span></span>
> - <span data-ttu-id="68441-200">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="68441-200">Train the model</span></span>
> - <span data-ttu-id="68441-201">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="68441-201">Evaluate the model</span></span>
> - <span data-ttu-id="68441-202">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="68441-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="68441-203">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="68441-203">Additional Resources</span></span>

<span data-ttu-id="68441-204">このチュートリアルで説明しているトピックについて詳しくは、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="68441-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="68441-205">モデル ビルダーのシナリオ</span><span class="sxs-lookup"><span data-stu-id="68441-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- <span data-ttu-id="68441-206">[Regression](../resources/glossary.md#regression) (回帰)</span><span class="sxs-lookup"><span data-stu-id="68441-206">[Regression](../resources/glossary.md#regression)</span></span>
- [<span data-ttu-id="68441-207">回帰モデルのメトリック</span><span class="sxs-lookup"><span data-stu-id="68441-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="68441-208">NYC TLC Taxi Trip データ セット</span><span class="sxs-lookup"><span data-stu-id="68441-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
