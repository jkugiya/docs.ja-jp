---
title: ML.NET CLI を使用してモデルのトレーニングを自動化する
description: ML.NET CLI ツールを使用してコマンドラインから最適なモデルを自動的にトレーニングする方法について説明します。
ms.date: 06/03/2020
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 0b230e4a517b6493abdb1ec975776fd286b654e3
ms.sourcegitcommit: b27645cb378d4e8137a267e5467ff31409acf6c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2021
ms.locfileid: "103231408"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="86c8d-103">ML.NET CLI を使用してモデルのトレーニングを自動化する</span><span class="sxs-lookup"><span data-stu-id="86c8d-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="86c8d-104">ML.NET CLI は、.NET 開発者のためにモデル生成を自動化します。</span><span class="sxs-lookup"><span data-stu-id="86c8d-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="86c8d-105">(ML.NET AutoML CLI を使用せずに) ML.NET API を単独で使用するには、トレーナー (特定のタスクに対する機械学習アルゴリズムの実装) と、データに適用する一連のデータ変換 (特徴エンジニアリング) を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86c8d-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="86c8d-106">最適なパイプラインはデータセットごとに異なるので、すべての選択肢から最適なアルゴリズムを選択すると、複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="86c8d-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="86c8d-107">さらに、各アルゴリズムには調整が必要な一連のハイパーパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="86c8d-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="86c8d-108">そのため、特徴エンジニアリング、学習アルゴリズム、およびハイパーパラメーターの最適な組み合わせを見つけようとすると、機械学習モデルの最適化に数週間から数か月かかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86c8d-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="86c8d-109">ML.NET CLI は、このプロセスを、自動機械学習 (AutoML) を使用して簡略化します。</span><span class="sxs-lookup"><span data-stu-id="86c8d-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="86c8d-110">このトピックは、現在プレビュー段階の ML.NET **CLI** と ML.NET **AutoML** について述べており、内容が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="86c8d-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="86c8d-111">ML.NET コマンドライン インターフェイス (CLI) とは</span><span class="sxs-lookup"><span data-stu-id="86c8d-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="86c8d-112">ML.NET CLI は [.NET Core ツール](../core/tools/global-tools.md)です。</span><span class="sxs-lookup"><span data-stu-id="86c8d-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="86c8d-113">ツールをインストールしたら、機械学習タスクとトレーニング データセットを提供します。その後、ML.NET モデルと、アプリケーションでそのモデルを使用するときに実行する C# コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="86c8d-114">次の図に示すように、高品質の ML.NET モデル (シリアル化されたモデルの .zip ファイル) と、そのモデルを実行/スコア付けするサンプル C# コードを簡単に生成できます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="86c8d-115">さらに、そのモデルを作成/トレーニングする C# コードも生成されるので、その生成された "最適なモデル" に使用されるアルゴリズムと設定を調べ、反復処理することができます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

![ML.NET CLI 内で動作する AutoML エンジン](media/automate-training-with-cli/cli-high-level-process.png)

<span data-ttu-id="86c8d-117">自力でコーディングすることなく、所有しているデータセットからこうした資産を生成できるので、ML.NET について知っている場合でも生産性が向上します。</span><span class="sxs-lookup"><span data-stu-id="86c8d-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="86c8d-118">現在、ML.NET CLI でサポートされている ML タスクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="86c8d-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- <span data-ttu-id="86c8d-119">分類</span><span class="sxs-lookup"><span data-stu-id="86c8d-119">classification</span></span>
- <span data-ttu-id="86c8d-120">回帰</span><span class="sxs-lookup"><span data-stu-id="86c8d-120">regression</span></span>
- <span data-ttu-id="86c8d-121">推奨</span><span class="sxs-lookup"><span data-stu-id="86c8d-121">recommendation</span></span>
- <span data-ttu-id="86c8d-122">画像の分類</span><span class="sxs-lookup"><span data-stu-id="86c8d-122">image classification</span></span>

<span data-ttu-id="86c8d-123">使用例 (分類シナリオ):</span><span class="sxs-lookup"><span data-stu-id="86c8d-123">Example of usage (classification scenario):</span></span>

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![コマンド ラインからの ML.NET 分類](media/automate-training-with-cli/mlnet-classification-powershell.gif)

<span data-ttu-id="86c8d-125">*Windows PowerShell*、*macOS/Linux bash*、または *Windows CMD* でも同じ方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-125">You can run it the same way on *Windows PowerShell*, *macOS/Linux bash*, or *Windows CMD*.</span></span> <span data-ttu-id="86c8d-126">ただし、タブのオートコンプリート (パラメーター候補) は *Windows CMD* では機能しません。</span><span class="sxs-lookup"><span data-stu-id="86c8d-126">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="86c8d-127">生成される出力資産</span><span class="sxs-lookup"><span data-stu-id="86c8d-127">Output assets generated</span></span>

<span data-ttu-id="86c8d-128">CLI で ML タスク コマンドを使用すると、出力フォルダーに以下の資産が生成されます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-128">The ML task commands in the CLI generate the following assets in the output folder:</span></span>

- <span data-ttu-id="86c8d-129">予測を実行する準備が完了したシリアル化されたモデル .zip ("最適なモデル")。</span><span class="sxs-lookup"><span data-stu-id="86c8d-129">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="86c8d-130">C# ソリューション:</span><span class="sxs-lookup"><span data-stu-id="86c8d-130">C# solution with:</span></span>
  - <span data-ttu-id="86c8d-131">その生成されたモデルを実行/スコア付けする C# コード (そのモデルを使用してエンドユーザー アプリで予測を行うため)。</span><span class="sxs-lookup"><span data-stu-id="86c8d-131">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="86c8d-132">そのモデルの生成に使用されるトレーニング コードを含む C# コード (学習目的またはモデルの再トレーニングのため)。</span><span class="sxs-lookup"><span data-stu-id="86c8d-132">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="86c8d-133">詳細な構成/パイプラインなど、評価される複数のアルゴリズム全体にわたるすべての反復処理/スイープの情報を含むログ ファイル。</span><span class="sxs-lookup"><span data-stu-id="86c8d-133">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="86c8d-134">最初の 2 つの資産は、その生成された ML モデルを使用して予測を行うために、エンドユーザー アプリ (ASP.NET Core Web アプリ、サービス、デスクトップ アプリなど) で直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-134">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="86c8d-135">3 つ目の資産のトレーニング コードは、生成されたモデルをトレーニングするために CLI によって使用された ML.NET API コードを示しています。そのため、モデルを再トレーニングし、背後で CLI および ML.NET AutoML エンジンによって選択された特定のトレーナー/アルゴリズムとハイパーパラメーターを調べて反復処理することができます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-135">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="86c8d-136">モデルの品質を理解する</span><span class="sxs-lookup"><span data-stu-id="86c8d-136">Understanding the quality of the model</span></span>

<span data-ttu-id="86c8d-137">CLI ツールを使用して "最適なモデル" を生成すると、対象の ML タスクに適した品質メトリック (正確度、R-2 乗など) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-137">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="86c8d-138">ここでは、自動生成された "最適なモデル" の品質を理解できるように、これらのメトリックを ML タスク別にグループ化してまとめています。</span><span class="sxs-lookup"><span data-stu-id="86c8d-138">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-classification-models"></a><span data-ttu-id="86c8d-139">分類モデルのメトリック</span><span class="sxs-lookup"><span data-stu-id="86c8d-139">Metrics for Classification models</span></span>

<span data-ttu-id="86c8d-140">CLI によって検出される上位 5 つのモデルの分類メトリックの一覧を次の画像に示します。</span><span class="sxs-lookup"><span data-stu-id="86c8d-140">The following image displays the classification metrics list for the top five models found by the CLI:</span></span>

![上位 5 つのモデルの分類メトリック](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 <span data-ttu-id="86c8d-142">正確度は分類問題の一般的なメトリックですが、以下のリファレンスで説明されているように、最適なモデルを選択する場合に正確度が常に最適なメトリックとは限りません。</span><span class="sxs-lookup"><span data-stu-id="86c8d-142">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="86c8d-143">必要に応じて追加のメトリックを使用してモデルの品質を評価する場合があります。</span><span class="sxs-lookup"><span data-stu-id="86c8d-143">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="86c8d-144">CLI によって出力されるメトリックを調べて理解するには、[分類の評価メトリック](resources/metrics.md#evaluation-metrics-for-multi-class-classification)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86c8d-144">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="86c8d-145">回帰とレコメンデーション モデルのメトリック</span><span class="sxs-lookup"><span data-stu-id="86c8d-145">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="86c8d-146">観測値とモデルの予測値の差が小さく偏りがない場合、回帰モデルがデータに適しています。</span><span class="sxs-lookup"><span data-stu-id="86c8d-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="86c8d-147">回帰は特定のメトリックを使用して評価できます。</span><span class="sxs-lookup"><span data-stu-id="86c8d-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="86c8d-148">CLI で見つかる上位 5 つの品質モデルには、同様のメトリック リストが表示されます。ただしこの場合、上位 5 つは回帰 ML タスクに関連しています。</span><span class="sxs-lookup"><span data-stu-id="86c8d-148">You'll see a similar list of metrics for the top five quality models found by the CLI, except in this case, the top five are related to a regression ML task:</span></span>

![上位 5 つのモデルの回帰メトリック](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="86c8d-150">CLI によって出力されるメトリックを調べて理解するには、[回帰の評価メトリック](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)に関するトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86c8d-150">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="86c8d-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="86c8d-151">See also</span></span>

- [<span data-ttu-id="86c8d-152">ML.NET CLI ツールのインストール方法</span><span class="sxs-lookup"><span data-stu-id="86c8d-152">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="86c8d-153">チュートリアル: ML.NET CLI を使用してセンチメントを分析する</span><span class="sxs-lookup"><span data-stu-id="86c8d-153">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="86c8d-154">ML.NET CLI コマンド リファレンス</span><span class="sxs-lookup"><span data-stu-id="86c8d-154">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="86c8d-155">ML.NET CLI のテレメトリ</span><span class="sxs-lookup"><span data-stu-id="86c8d-155">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
