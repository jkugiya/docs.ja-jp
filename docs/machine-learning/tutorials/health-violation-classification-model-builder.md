---
title: 'チュートリアル: モデル ビルダーを使用して保健衛生違反を分類する'
description: このチュートリアルでは、サンフランシスコでのレストランの保健衛生違反の重大度を分類するために、ML.NET モデル ビルダーを使用して多クラス分類モデルを構築する方法について説明します。
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 468d09510cb55971d25877e40b7c54aae479ac84
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875617"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a><span data-ttu-id="3043a-103">チュートリアル: モデル ビルダーを使用してレストランの保健衛生違反の重大度を分類する</span><span class="sxs-lookup"><span data-stu-id="3043a-103">Tutorial: Classify the severity of restaurant health violations with Model Builder</span></span>

<span data-ttu-id="3043a-104">保健衛生検査中に検出されたレストラン違反のリスク レベルを分類するために、モデル ビルダーを使用して多クラス分類モデルを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3043a-104">Learn how to build a multiclass classification model using Model Builder to categorize the risk level of restaurant violations found during health inspections.</span></span>

<span data-ttu-id="3043a-105">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3043a-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="3043a-106">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="3043a-106">Prepare and understand the data</span></span>
> - <span data-ttu-id="3043a-107">シナリオを選択する</span><span class="sxs-lookup"><span data-stu-id="3043a-107">Choose a scenario</span></span>
> - <span data-ttu-id="3043a-108">データベースからデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="3043a-108">Load data from a database</span></span>
> - <span data-ttu-id="3043a-109">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="3043a-109">Train the model</span></span>
> - <span data-ttu-id="3043a-110">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="3043a-110">Evaluate the model</span></span>
> - <span data-ttu-id="3043a-111">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="3043a-111">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="3043a-112">モデル ビルダーは現在のところ、プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="3043a-112">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3043a-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="3043a-113">Prerequisites</span></span>

<span data-ttu-id="3043a-114">前提条件の一覧とインストール手順は、[モデル ビルダーのインストール ガイド](../how-to-guides/install-model-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3043a-114">For a list of prerequisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="model-builder-multiclass-classification-overview"></a><span data-ttu-id="3043a-115">モデル ビルダー多クラス分類の概要</span><span class="sxs-lookup"><span data-stu-id="3043a-115">Model Builder multiclass classification overview</span></span>

<span data-ttu-id="3043a-116">このサンプルでは、モデル ビルダーでビルドされた機械学習モデルを使用して、保健衛生違反のリスクを分類する C# .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3043a-116">This sample creates a C# .NET Core console application that categorizes the risk of health violations using a machine learning model built with Model Builder.</span></span> <span data-ttu-id="3043a-117">このチュートリアルのソース コードは、[dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="3043a-117">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub repository.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="3043a-118">コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="3043a-118">Create a console application</span></span>

1. <span data-ttu-id="3043a-119">"RestaurantViolations" という名前の **C# .NET Core コンソール アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="3043a-119">Create a **C# .NET Core console application** called "RestaurantViolations".</span></span> <span data-ttu-id="3043a-120">**[ソリューションとプロジェクトを同じディレクトリに配置する]** を **オフ** (VS 2019) にします。または、 **[ソリューションのディレクトリの作成]** を **オン** にします (VS 2017)。</span><span class="sxs-lookup"><span data-stu-id="3043a-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="3043a-121">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="3043a-121">Prepare and understand the data</span></span>

> <span data-ttu-id="3043a-122">機械学習モデルのトレーニングと評価に使用するデータ セットは、[サンフランシスコ公衆衛生局の安全性スコア](https://www.sfdph.org/dph/EH/Food/score/default.asp) から取得したものです。</span><span class="sxs-lookup"><span data-stu-id="3043a-122">The data set used to train and evaluate the machine learning model is originally from the [San Francisco Department of Public Health Restaurant Safety Scores](https://www.sfdph.org/dph/EH/Food/score/default.asp).</span></span> <span data-ttu-id="3043a-123">便宜上、データ セットは、モデルのトレーニングと予測の作成に関連する列のみを含むように圧縮されています。</span><span class="sxs-lookup"><span data-stu-id="3043a-123">For convenience, the dataset has been condensed to only include the columns relevant to train the model and make predictions.</span></span> <span data-ttu-id="3043a-124">[データセット](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)の詳細については、次の Web サイトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3043a-124">Visit the following website to learn more about the [dataset](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).</span></span>

<span data-ttu-id="3043a-125">[Restaurant Safety Scores データセット](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip)をダウンロードして解凍します。</span><span class="sxs-lookup"><span data-stu-id="3043a-125">[Download the Restaurant Safety Scores dataset](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) and unzip it.</span></span>

<span data-ttu-id="3043a-126">データセットの各行には、保健局の検査中に観察された違反に関する情報と、それらの違反が公衆衛生と安全性に与える脅威のリスク評価が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3043a-126">Each row in the dataset contains information regarding violations observed during an inspection from the Health Department and a risk assessment of the threat those violations present to public health and safety.</span></span>

| <span data-ttu-id="3043a-127">InspectionType</span><span class="sxs-lookup"><span data-stu-id="3043a-127">InspectionType</span></span> | <span data-ttu-id="3043a-128">ViolationDescription</span><span class="sxs-lookup"><span data-stu-id="3043a-128">ViolationDescription</span></span> | <span data-ttu-id="3043a-129">RiskCategory</span><span class="sxs-lookup"><span data-stu-id="3043a-129">RiskCategory</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3043a-130">定期 - スケジュールなし</span><span class="sxs-lookup"><span data-stu-id="3043a-130">Routine - Unscheduled</span></span> | <span data-ttu-id="3043a-131">食品接触面の洗浄または衛生状態が不適切</span><span class="sxs-lookup"><span data-stu-id="3043a-131">Inadequately cleaned or sanitized food contact surfaces</span></span> | <span data-ttu-id="3043a-132">リスク - 中</span><span class="sxs-lookup"><span data-stu-id="3043a-132">Moderate Risk</span></span> |
| <span data-ttu-id="3043a-133">新しい所有権</span><span class="sxs-lookup"><span data-stu-id="3043a-133">New Ownership</span></span> | <span data-ttu-id="3043a-134">リスクの高い害虫の侵入</span><span class="sxs-lookup"><span data-stu-id="3043a-134">High risk vermin infestation</span></span> | <span data-ttu-id="3043a-135">リスク - 高</span><span class="sxs-lookup"><span data-stu-id="3043a-135">High Risk</span></span> |
| <span data-ttu-id="3043a-136">定期 - スケジュールなし</span><span class="sxs-lookup"><span data-stu-id="3043a-136">Routine - Unscheduled</span></span> | <span data-ttu-id="3043a-137">清潔でない、適切に保管されていない、または消毒が十分でない布巾</span><span class="sxs-lookup"><span data-stu-id="3043a-137">Wiping cloths not clean or properly stored or inadequate sanitizer</span></span> | <span data-ttu-id="3043a-138">リスク - 低</span><span class="sxs-lookup"><span data-stu-id="3043a-138">Low Risk</span></span> |

- <span data-ttu-id="3043a-139">**InspectionType**: 検査の種類。</span><span class="sxs-lookup"><span data-stu-id="3043a-139">**InspectionType**: the type of inspection.</span></span> <span data-ttu-id="3043a-140">これは、新しい施設の最初の検査、定期検査、苦情検査など、さまざまな種類の検査とすることができます。</span><span class="sxs-lookup"><span data-stu-id="3043a-140">This can either be a first-time inspection for a new establishment, a routine inspection, a complaint inspection, and many other types.</span></span>
- <span data-ttu-id="3043a-141">**ViolationDescription**: 検査中に検出された違反の説明。</span><span class="sxs-lookup"><span data-stu-id="3043a-141">**ViolationDescription**: a description of the violation found during inspection.</span></span>
- <span data-ttu-id="3043a-142">**RiskCategory**: 違反が公衆衛生と安全性に及ぼすリスクの重大度。</span><span class="sxs-lookup"><span data-stu-id="3043a-142">**RiskCategory**: the risk severity a violation poses to public health and safety.</span></span>

<span data-ttu-id="3043a-143">`label` は予測する列です。</span><span class="sxs-lookup"><span data-stu-id="3043a-143">The `label` is the column you want to predict.</span></span> <span data-ttu-id="3043a-144">分類タスクを実行する場合の目標は、カテゴリ (テキストまたは数値) を割り当てることです。</span><span class="sxs-lookup"><span data-stu-id="3043a-144">When performing a classification task, the goal is to assign a category (text or numerical).</span></span> <span data-ttu-id="3043a-145">この分類シナリオで、違反の重大度として割り当てられる値は、リスク - 低、リスク - 中、またはリスク - 高です。</span><span class="sxs-lookup"><span data-stu-id="3043a-145">In this classification scenario, the severity of the violation is assigned the value of low, moderate, or high risk.</span></span> <span data-ttu-id="3043a-146">したがって、**RiskCategory** はラベルです。</span><span class="sxs-lookup"><span data-stu-id="3043a-146">Therefore, the **RiskCategory** is the label.</span></span> <span data-ttu-id="3043a-147">`features` は、`label` を予測するためのモデルを指定する入力です。</span><span class="sxs-lookup"><span data-stu-id="3043a-147">The `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="3043a-148">この場合は、**RiskCategory** を予測するための機能または入力として **InspectionType** および **ViolationDescription** を使用します。</span><span class="sxs-lookup"><span data-stu-id="3043a-148">In this case, the **InspectionType** and **ViolationDescription** are used as features or inputs to predict the **RiskCategory**.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="3043a-149">シナリオを選択する</span><span class="sxs-lookup"><span data-stu-id="3043a-149">Choose a scenario</span></span>

![Visual Studio のモデル ビルダー ウィザード](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="3043a-151">モデルをトレーニングするには、モデル ビルダーによって提供される機械学習シナリオの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-151">To train your model, select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="3043a-152">この場合、シナリオは "*問題の分類*" です。</span><span class="sxs-lookup"><span data-stu-id="3043a-152">In this case, the scenario is *Issue Classification*.</span></span>

1. <span data-ttu-id="3043a-153">**ソリューション エクスプローラー** で、*[RestaurantViolations]* プロジェクトを右クリックし、**[追加]** > **[機械学習]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-153">In **Solution Explorer**, right-click the *RestaurantViolations* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="3043a-154">このサンプルでは、シナリオは多クラス分類です。</span><span class="sxs-lookup"><span data-stu-id="3043a-154">For this sample, the scenario is multiclass classification.</span></span> <span data-ttu-id="3043a-155">モデル ビルダーの "*シナリオ*" の手順で、**[問題の分類]** シナリオを選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-155">In the *Scenario* step of Model Builder, select the **Issue Classification** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="3043a-156">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="3043a-156">Load the data</span></span>

<span data-ttu-id="3043a-157">モデル ビルダーは、SQL Server データベースから、あるいは `csv` 形式または `tsv` 形式のローカル ファイルからデータを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3043a-157">Model Builder accepts data from a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="3043a-158">モデル ビルダー ツールのデータの手順で、データ ソースのドロップダウンから **[SQL Server]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-158">In the data step of the Model Builder tool, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="3043a-159">**[SQL Server データベースに接続]** テキスト ボックスの横にあるボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-159">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="3043a-160">**[データの選択]** ダイアログで、**[Microsoft SQL Server データベース ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-160">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="3043a-161">**[常にこれを選択する]** チェックボックスをオフにして、 **[続行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-161">Uncheck the **Always use this selection** checkbox and select **Continue**.</span></span>
    1. <span data-ttu-id="3043a-162">**[接続プロパティ]** ダイアログで、**[参照]** を選択し、ダウンロードした *RestaurantScores.mdf* ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-162">In the **Connection Properties** dialog, select **Browse** and select the downloaded *RestaurantScores.mdf* file.</span></span>
    1. <span data-ttu-id="3043a-163">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-163">Select **OK**.</span></span>
1. <span data-ttu-id="3043a-164">**[テーブル名]** ドロップダウンから **[違反]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-164">Choose **Violations** from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="3043a-165">**[予測する列 (ラベル)]** ドロップダウンで **[RiskCategory]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-165">Choose **RiskCategory** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="3043a-166">**[入力列 (機能)]** ドロップダウンで選択されている既定の列の選択 (**[InspectionType]** および **[ViolationDescription]**) をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="3043a-166">Leave the default column selections, **InspectionType** and **ViolationDescription**, checked in the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="3043a-167">**[トレーニング]** リンクを選択して、モデル ビルダーの次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="3043a-167">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="3043a-168">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="3043a-168">Train the model</span></span>

<span data-ttu-id="3043a-169">このチュートリアルで、問題の分類モデルをトレーニングするのに使用する機械学習のタスクは、多クラス分類です。</span><span class="sxs-lookup"><span data-stu-id="3043a-169">The machine learning task used to train the issue classification model in this tutorial is multiclass classification.</span></span> <span data-ttu-id="3043a-170">モデルのトレーニング プロセス中、モデル ビルダーは、データセットに対して最もパフォーマンスの優れたモデルを見つけるために、さまざまな多クラス分類アルゴリズムと設定を使用して個々のモデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="3043a-170">During the model training process, Model Builder trains separate models using different multiclass classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="3043a-171">モデルのトレーニングに必要な時間は、データの量に比例します。</span><span class="sxs-lookup"><span data-stu-id="3043a-171">The time required for the model to train is proportional to the amount of data.</span></span> <span data-ttu-id="3043a-172">モデル ビルダーにより、 **[Time to train (seconds)]\(トレーニング時間 (秒)\)** の既定値が、データ ソースのサイズに基づいて自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="3043a-172">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="3043a-173">モデル ビルダーによって **[トレーニング時間 (秒)]** の値が 10 秒に設定しますが、30 秒に増加します。</span><span class="sxs-lookup"><span data-stu-id="3043a-173">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="3043a-174">トレーニング時間が長いほど、モデル ビルダーは最良のモデルの検索の中で、より多くのアルゴリズムやパラメーターの組み合わせを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="3043a-174">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="3043a-175">**[Start Training]\(トレーニング開始\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3043a-175">Select **Start Training**.</span></span>

    <span data-ttu-id="3043a-176">トレーニング プロセスを通して、進捗データがトレーニングの手順の `Progress` セクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3043a-176">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="3043a-177">**[状態]** には、トレーニング プロセスの完了ステータスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3043a-177">**Status** displays the completion status of the training process.</span></span>
    - <span data-ttu-id="3043a-178">**[Best accuracy]\(最良の精度\)**   には、これまでにモデル ビルダーで見つかった最良のパフォーマンスのモデルの精度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3043a-178">**Best accuracy** displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="3043a-179">精度が高くなるほど、テスト データでモデルが正確に予測されたことになります。</span><span class="sxs-lookup"><span data-stu-id="3043a-179">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="3043a-180">**[Best algorithm]\(最良のアルゴリズム\)**   には、これまでにモデル ビルダーで見つかった最良のパフォーマンスのアルゴリズムの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3043a-180">**Best algorithm** displays the name of the best-performing algorithm found by Model Builder so far.</span></span>
    - <span data-ttu-id="3043a-181">**[Last algorithm]\(最後のアルゴリズム\)**   には、モデル ビルダーがモデルのトレーニングに最近使用したアルゴリズムの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3043a-181">**Last algorithm** displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="3043a-182">トレーニングが完了したら、 **[評価]** リンクを選択して、次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="3043a-182">Once training is complete, select the **Evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="3043a-183">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="3043a-183">Evaluate the model</span></span>

<span data-ttu-id="3043a-184">トレーニングの手順の結果は、最良のパフォーマンスを示した 1 つのモデルになります。</span><span class="sxs-lookup"><span data-stu-id="3043a-184">The result of the training step is the one model that had the best performance.</span></span> <span data-ttu-id="3043a-185">モデル ビルダーの評価の手順の出力セクションには、**[Best Model]\(最良のモデル\)** エントリの最良のパフォーマンスのモデルで使用されたアルゴリズムと、**[Best Model Accuracy]\(最良のモデル精度\)** のメトリックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3043a-185">In the evaluate step of Model Builder, the output section contains the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="3043a-186">さらに、探索された最大 5 つのモデルとそのメトリックが含まれている概要テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3043a-186">Additionally, a summary table containing up to five models that were explored and their metrics is displayed.</span></span>

<span data-ttu-id="3043a-187">精度のメトリックに不満がある場合、モデルのトレーニング時間を増やすか、さらに多くのデータを使用すると、モデルの精度を簡単に高めることができます。</span><span class="sxs-lookup"><span data-stu-id="3043a-187">If you're not satisfied with your accuracy metrics, some easy ways to try to improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="3043a-188">それ以外の場合、**[コード]** リンクを選択して、モデル ビルダーの最後の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="3043a-188">Otherwise, select the **code** link to move to the final step in Model Builder.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="3043a-189">予測を行うコードを追加する</span><span class="sxs-lookup"><span data-stu-id="3043a-189">Add the code to make predictions</span></span>

<span data-ttu-id="3043a-190">トレーニング プロセスの結果として 2 つのプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3043a-190">Two projects are created as a result of the training process.</span></span>

- <span data-ttu-id="3043a-191">RestaurantViolationsML.ConsoleApp: モデルのトレーニングとサンプルの使用に関するコードが含まれている C# .NET Core コンソール アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="3043a-191">RestaurantViolationsML.ConsoleApp: A C# .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="3043a-192">RestaurantViolationsML.Model: 入力および出力モデル データのスキーマを定義するデータ モデル、トレーニング中に最も高速であったモデルの保存されたバージョン、予測を行うために `ConsumeModel` を呼び出したヘルパー クラスが含まれている .NET Standard クラス ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="3043a-192">RestaurantViolationsML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training, and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="3043a-193">モデル ビルダーのコードの手順で、**[プロジェクトの追加]** を選択して、自動生成されたプロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3043a-193">In the code step of Model Builder, select **Add Projects** to add the autogenerated projects to the solution.</span></span>
1. <span data-ttu-id="3043a-194">*RestaurantViolations* プロジェクトで *Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3043a-194">Open the *Program.cs* file in the *RestaurantViolations* project.</span></span>
1. <span data-ttu-id="3043a-195">*RestaurantViolationsML.Model* プロジェクトを参照する次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="3043a-195">Add the following using statement to reference the *RestaurantViolationsML.Model* project:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. <span data-ttu-id="3043a-196">新しいデータに対してモデルを使用して予測を行うには、アプリケーションの `ModelInput` メソッド内に `Main` クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3043a-196">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="3043a-197">リスク カテゴリが入力に含まれていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3043a-197">Notice that the risk category is not part of the input.</span></span> <span data-ttu-id="3043a-198">これは、モデルによってその予測が生成されるためです。</span><span class="sxs-lookup"><span data-stu-id="3043a-198">This is because the model generates the prediction for it.</span></span>

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. <span data-ttu-id="3043a-199">`ConsumeModel` クラスの `Predict` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3043a-199">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="3043a-200">`Predict` メソッドでは、トレーニング済みモデルを読み込み、モデルに対して [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) を作成し、新しいデータに対してそれを使用して予測を行います。</span><span class="sxs-lookup"><span data-stu-id="3043a-200">The `Predict` method loads the trained model, creates a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model, and uses it to make predictions on new data.</span></span>

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. <span data-ttu-id="3043a-201">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3043a-201">Run the application.</span></span>

    <span data-ttu-id="3043a-202">プログラムによって生成される出力は次のスニペットのようになります。</span><span class="sxs-lookup"><span data-stu-id="3043a-202">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

<span data-ttu-id="3043a-203">別のソリューション内で後で生成されたプロジェクトを参照する必要がある場合は、`C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` ディレクトリを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="3043a-203">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

<span data-ttu-id="3043a-204">おめでとうございます。</span><span class="sxs-lookup"><span data-stu-id="3043a-204">Congratulations!</span></span> <span data-ttu-id="3043a-205">これで、モデル ビルダーを使用して保健衛生違反のリスクを分類するための機械学習モデルを正常に作成できました。</span><span class="sxs-lookup"><span data-stu-id="3043a-205">You've successfully built a machine learning model to categorize the risk of health violations using Model Builder.</span></span> <span data-ttu-id="3043a-206">このチュートリアルのソース コードは、[dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="3043a-206">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub repository.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3043a-207">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="3043a-207">Additional resources</span></span>

<span data-ttu-id="3043a-208">このチュートリアルで説明しているトピックについて詳しくは、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3043a-208">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="3043a-209">モデル ビルダーのシナリオ</span><span class="sxs-lookup"><span data-stu-id="3043a-209">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="3043a-210">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="3043a-210">Multiclass Classification</span></span>](../resources/glossary.md#multiclass-classification)
- [<span data-ttu-id="3043a-211">多クラス分類モデル メトリック</span><span class="sxs-lookup"><span data-stu-id="3043a-211">Multiclass Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
