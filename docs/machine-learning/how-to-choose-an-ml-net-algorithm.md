---
title: ML.NET アルゴリズムの選び方
description: 機械学習モデルに適した ML.NET アルゴリズムの選び方について説明します
ms.topic: overview
ms.date: 03/31/2021
ms.openlocfilehash: c1a35f2b5b2ece2a846469f855e91b49887f0c90
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122626"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a><span data-ttu-id="09e6e-103">ML.NET アルゴリズムの選び方</span><span class="sxs-lookup"><span data-stu-id="09e6e-103">How to choose an ML.NET algorithm</span></span>

<span data-ttu-id="09e6e-104">[ML.NET タスク](resources/tasks.md) ごとに選択できるトレーニング アルゴリズムは複数あります。</span><span class="sxs-lookup"><span data-stu-id="09e6e-104">For each [ML.NET task](resources/tasks.md), there are multiple training algorithms to choose from.</span></span> <span data-ttu-id="09e6e-105">どれを選択するかは、解決しようとしている問題、データの特性、利用できるコンピューティング リソースとストレージ リソースによって変わります。</span><span class="sxs-lookup"><span data-stu-id="09e6e-105">Which one to choose depends on the problem you are trying to solve, the characteristics of your data, and the compute and storage resources you have available.</span></span> <span data-ttu-id="09e6e-106">機械学習モデルのトレーニングは反復処理である点に注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-106">It is important to note that training a machine learning model is an iterative process.</span></span> <span data-ttu-id="09e6e-107">場合によっては、最適なものを見つけるために複数のアルゴリズムを試す必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e6e-107">You might need to try multiple algorithms to find the one that works best.</span></span>

<span data-ttu-id="09e6e-108">アルゴリズムは **特徴** に対して動作します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-108">Algorithms operate on **features**.</span></span> <span data-ttu-id="09e6e-109">特徴は、入力データから計算された数値です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-109">Features are numerical values computed from your input data.</span></span> <span data-ttu-id="09e6e-110">それらは機械学習アルゴリズムに最適な入力です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-110">They are optimal inputs for machine learning algorithms.</span></span> <span data-ttu-id="09e6e-111">生の入力データを 1 つ以上の[データ変換](resources/transforms.md)を使用して特徴に変換します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-111">You transform your raw input data into features using one or more [data transforms](resources/transforms.md).</span></span> <span data-ttu-id="09e6e-112">たとえば、テキスト データは、単語数と単語の組み合わせ数のセットに変換されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-112">For example, text data is transformed into a set of word counts and word combination counts.</span></span> <span data-ttu-id="09e6e-113">データ変換を使用して生のデータの種類から特徴が抽出されると、**特徴付けされた** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-113">Once the features have been extracted from a raw data type using data transforms, they are referred to as **featurized**.</span></span> <span data-ttu-id="09e6e-114">たとえば、特徴付けされたテキスト、特徴付けされた画像データなどです。</span><span class="sxs-lookup"><span data-stu-id="09e6e-114">For example, featurized text, or featurized image data.</span></span>

## <a name="trainer--algorithm--task"></a><span data-ttu-id="09e6e-115">トレーナー = アルゴリズム + タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-115">Trainer = Algorithm + Task</span></span>

<span data-ttu-id="09e6e-116">アルゴリズムは、**モデル** を生成するために実行される数学です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-116">An algorithm is the math that executes to produce a **model**.</span></span> <span data-ttu-id="09e6e-117">アルゴリズムが異なると、特性が異なるモデルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-117">Different algorithms produce models with different characteristics.</span></span>

<span data-ttu-id="09e6e-118">ML.NET では、同じアルゴリズムを異なるタスクに適用できます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-118">With ML.NET, the same algorithm can be applied to different tasks.</span></span> <span data-ttu-id="09e6e-119">たとえば、確率的双対座標上昇法は、二項分類、多クラス分類、回帰に使用できます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-119">For example, Stochastic Dual Coordinate Ascent can be used for Binary Classification, Multiclass Classification, and Regression.</span></span> <span data-ttu-id="09e6e-120">違いは、タスクに合わせてアルゴリズムの出力が解釈される方法にあります。</span><span class="sxs-lookup"><span data-stu-id="09e6e-120">The difference is in how the output of the algorithm is interpreted to match the task.</span></span>

<span data-ttu-id="09e6e-121">ML.NET には、各アルゴリズムとタスクの組み合わせに対して、トレーニング アルゴリズムを実行し、解釈するコンポーネントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="09e6e-121">For each algorithm/task combination, ML.NET provides a component that executes the training algorithm and makes the interpretation.</span></span> <span data-ttu-id="09e6e-122">これらのコンポーネントはトレーナーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-122">These components are called trainers.</span></span> <span data-ttu-id="09e6e-123">たとえば、<xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> には、**回帰** タスクに適用される **StochasticDualCoordinatedAscent** アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-123">For example, the <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> uses the **StochasticDualCoordinatedAscent** algorithm applied to the **Regression** task.</span></span>

## <a name="linear-algorithms"></a><span data-ttu-id="09e6e-124">線形アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="09e6e-124">Linear algorithms</span></span>

<span data-ttu-id="09e6e-125">線形アルゴリズムでは、入力データと一連の **重み** の線形結合から **スコア** を計算するモデルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-125">Linear algorithms produce a model that calculates **scores** from a linear combination of the input data and a set of **weights**.</span></span> <span data-ttu-id="09e6e-126">重みは、トレーニング中に推定されるモデルのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="09e6e-126">The weights are parameters of the model estimated during training.</span></span>

<span data-ttu-id="09e6e-127">線形アルゴリズムは、[線形分離可能](https://en.wikipedia.org/wiki/Linear_separability)である特徴の場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="09e6e-127">Linear algorithms work well for features that are [linearly separable](https://en.wikipedia.org/wiki/Linear_separability).</span></span>

<span data-ttu-id="09e6e-128">線形アルゴリズムでトレーニングする前に、特徴を正規化しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="09e6e-128">Before training with a linear algorithm, the features should be normalized.</span></span> <span data-ttu-id="09e6e-129">こうすることで、ある特徴が他の特徴よりも結果に大きな影響を及ぼすことを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-129">This prevents one feature from having more influence over the result than others.</span></span>

<span data-ttu-id="09e6e-130">一般に、線形アルゴリズムはスケーラブルで高速であり、トレーニング コストが低コストで、予測も低コストです。</span><span class="sxs-lookup"><span data-stu-id="09e6e-130">In general, linear algorithms are scalable, fast, cheap to train, and cheap to predict.</span></span> <span data-ttu-id="09e6e-131">これらは、特徴の数と、おおよそのトレーニング データ セットのサイズによってスケールします。</span><span class="sxs-lookup"><span data-stu-id="09e6e-131">They scale by the number of features and approximately by the size of the training data set.</span></span>

<span data-ttu-id="09e6e-132">線形アルゴリズムは、トレーニング データに対して複数回実行されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-132">Linear algorithms make multiple passes over the training data.</span></span> <span data-ttu-id="09e6e-133">データセットがメモリに収まる場合は、トレーナーを追加する前に ML.NET パイプラインに[キャッシュ チェックポイント](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A)を追加すると、トレーニングが高速になります。</span><span class="sxs-lookup"><span data-stu-id="09e6e-133">If your dataset fits into memory, then adding a [cache checkpoint](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A) to your ML.NET pipeline before appending the trainer will make the training run faster.</span></span>

### <a name="averaged-perceptron"></a><span data-ttu-id="09e6e-134">Averaged perceptron (平均化パーセプトロン)</span><span class="sxs-lookup"><span data-stu-id="09e6e-134">Averaged perceptron</span></span>

<span data-ttu-id="09e6e-135">テキスト分類に最適です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-135">Best for text classification.</span></span>

|<span data-ttu-id="09e6e-136">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-136">Trainer</span></span>|<span data-ttu-id="09e6e-137">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-137">Task</span></span>|<span data-ttu-id="09e6e-138">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-138">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|<span data-ttu-id="09e6e-139">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-139">Binary classification</span></span>|<span data-ttu-id="09e6e-140">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-140">Yes</span></span>|

### <a name="stochastic-dual-coordinated-ascent"></a><span data-ttu-id="09e6e-141">確率的双対座標上昇法</span><span class="sxs-lookup"><span data-stu-id="09e6e-141">Stochastic dual coordinated ascent</span></span>

<span data-ttu-id="09e6e-142">既定のパフォーマンスが適切な場合、調整は不要です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-142">Tuning not needed for good default performance.</span></span>

|<span data-ttu-id="09e6e-143">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-143">Trainer</span></span>|<span data-ttu-id="09e6e-144">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-144">Task</span></span>|<span data-ttu-id="09e6e-145">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-145">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>|<span data-ttu-id="09e6e-146">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-146">Binary classification</span></span>|<span data-ttu-id="09e6e-147">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-147">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>|<span data-ttu-id="09e6e-148">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-148">Binary classification</span></span>|<span data-ttu-id="09e6e-149">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-149">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>|<span data-ttu-id="09e6e-150">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-150">Multiclass classification</span></span>|<span data-ttu-id="09e6e-151">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-151">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>|<span data-ttu-id="09e6e-152">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-152">Multiclass classification</span></span>|<span data-ttu-id="09e6e-153">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-153">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|<span data-ttu-id="09e6e-154">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-154">Regression</span></span>|<span data-ttu-id="09e6e-155">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-155">Yes</span></span>|

### <a name="l-bfgs"></a><span data-ttu-id="09e6e-156">L-BFGS</span><span class="sxs-lookup"><span data-stu-id="09e6e-156">L-BFGS</span></span>

<span data-ttu-id="09e6e-157">特徴数が多い場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-157">Use when number of features is large.</span></span> <span data-ttu-id="09e6e-158">ロジスティック回帰トレーニング統計を生成しますが、AveragedPerceptronTrainer ほどスケーリングしません</span><span class="sxs-lookup"><span data-stu-id="09e6e-158">Produces logistic regression training statistics, but doesn't scale as well as the AveragedPerceptronTrainer.</span></span>

|<span data-ttu-id="09e6e-159">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-159">Trainer</span></span>|<span data-ttu-id="09e6e-160">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-160">Task</span></span>|<span data-ttu-id="09e6e-161">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-161">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>|<span data-ttu-id="09e6e-162">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-162">Binary classification</span></span>|<span data-ttu-id="09e6e-163">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-163">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>|<span data-ttu-id="09e6e-164">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-164">Multiclass classification</span></span>|<span data-ttu-id="09e6e-165">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-165">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|<span data-ttu-id="09e6e-166">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-166">Regression</span></span>|<span data-ttu-id="09e6e-167">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-167">Yes</span></span>|

### <a name="symbolic-stochastic-gradient-descent"></a><span data-ttu-id="09e6e-168">Symbolic stochastic gradient descent (シンボリック確率的勾配降下法)</span><span class="sxs-lookup"><span data-stu-id="09e6e-168">Symbolic stochastic gradient descent</span></span>

<span data-ttu-id="09e6e-169">最も高速で最も正確な線形二項分類トレーナー。</span><span class="sxs-lookup"><span data-stu-id="09e6e-169">Fastest and most accurate linear binary classification trainer.</span></span> <span data-ttu-id="09e6e-170">プロセッサの数に合わせてスケーリングします。</span><span class="sxs-lookup"><span data-stu-id="09e6e-170">Scales well with number of processors.</span></span>

|<span data-ttu-id="09e6e-171">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-171">Trainer</span></span>|<span data-ttu-id="09e6e-172">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-172">Task</span></span>|<span data-ttu-id="09e6e-173">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-173">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|<span data-ttu-id="09e6e-174">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-174">Binary classification</span></span>|<span data-ttu-id="09e6e-175">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-175">Yes</span></span>|

### <a name="online-gradient-descent"></a><span data-ttu-id="09e6e-176">オンライン勾配降下</span><span class="sxs-lookup"><span data-stu-id="09e6e-176">Online gradient descent</span></span>

<span data-ttu-id="09e6e-177">選択した損失関数と、時間の経過と共に表示されるベクターの平均を使用して重みベクトルを更新するオプションを使用して、標準 (非バッチ) 確率的勾配降下法を実装します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-177">Implements the standard (non-batch) stochastic gradient descent, with a choice of loss functions, and an option to update the weight vector using the average of the vectors seen over time.</span></span>

|<span data-ttu-id="09e6e-178">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-178">Trainer</span></span>|<span data-ttu-id="09e6e-179">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-179">Task</span></span>|<span data-ttu-id="09e6e-180">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-180">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>|<span data-ttu-id="09e6e-181">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-181">Regression</span></span>|<span data-ttu-id="09e6e-182">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-182">Yes</span></span>|

## <a name="decision-tree-algorithms"></a><span data-ttu-id="09e6e-183">デシジョン ツリー アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="09e6e-183">Decision tree algorithms</span></span>

<span data-ttu-id="09e6e-184">デシジョン ツリー アルゴリズムは、一連の決定を含むモデルを作成します。事実上、データ値を通るフロー チャートです。</span><span class="sxs-lookup"><span data-stu-id="09e6e-184">Decision tree algorithms create a model that contains a series of decisions: effectively a flow chart through the data values.</span></span>

<span data-ttu-id="09e6e-185">この種類のアルゴリズムを使用するために、特徴が線形に分離可能である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="09e6e-185">Features do not need to be linearly separable to use this type of algorithm.</span></span> <span data-ttu-id="09e6e-186">また、特徴ベクター内の個々の値は決定プロセスで独立して使用されるため、特徴を正規化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="09e6e-186">And features do not need to be normalized, because the individual values in the feature vector are used independently in the decision process.</span></span>

<span data-ttu-id="09e6e-187">一般的に、デシジョン ツリー アルゴリズムは非常に正確です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-187">Decision tree algorithms are generally very accurate.</span></span>

<span data-ttu-id="09e6e-188">Generalized Additive Model (一般化加法モデル、GAM) を除き、特徴の数が多いと、説明可能性のないツリー モデルになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="09e6e-188">Except for Generalized Additive Models (GAMs), tree models can lack explainability when the number of features is large.</span></span>

<span data-ttu-id="09e6e-189">デシジョン ツリー アルゴリズムに消費されるリソースは多く、線形アルゴリズムほどスケールしません。</span><span class="sxs-lookup"><span data-stu-id="09e6e-189">Decision tree algorithms take more resources and do not scale as well as linear ones do.</span></span> <span data-ttu-id="09e6e-190">メモリに収まるようなデータセットに対しては適切に動作します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-190">They do perform well on datasets that can fit into memory.</span></span>

<span data-ttu-id="09e6e-191">Boosted decision trees (ブースト デシジョン ツリー) は小さなツリーの集合であり、各ツリーで入力データにスコアが付けられ、そのスコアは次のツリーに渡され、より良いスコアが生成されるという処理が繰り返されます。集合内の各ツリーは、前のツリーに基づいて改善されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-191">Boosted decision trees are an ensemble of small trees where each tree scores the input data and passes the score onto the next tree to produce a better score, and so on, where each tree in the ensemble improves on the previous.</span></span>

### <a name="light-gradient-boosted-machine"></a><span data-ttu-id="09e6e-192">Light gradient boosted machine (軽勾配ブースト マシン)</span><span class="sxs-lookup"><span data-stu-id="09e6e-192">Light gradient boosted machine</span></span>

<span data-ttu-id="09e6e-193">最も高速で最も正確な二項分類ツリー トレーナー。</span><span class="sxs-lookup"><span data-stu-id="09e6e-193">Fastest and most accurate of the binary classification tree trainers.</span></span> <span data-ttu-id="09e6e-194">高度に調整可能。</span><span class="sxs-lookup"><span data-stu-id="09e6e-194">Highly tunable.</span></span>

|<span data-ttu-id="09e6e-195">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-195">Trainer</span></span>|<span data-ttu-id="09e6e-196">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-196">Task</span></span>|<span data-ttu-id="09e6e-197">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-197">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>|<span data-ttu-id="09e6e-198">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-198">Binary classification</span></span>|<span data-ttu-id="09e6e-199">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-199">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>|<span data-ttu-id="09e6e-200">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-200">Multiclass classification</span></span>|<span data-ttu-id="09e6e-201">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-201">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>|<span data-ttu-id="09e6e-202">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-202">Regression</span></span>|<span data-ttu-id="09e6e-203">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-203">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|<span data-ttu-id="09e6e-204">順位付け</span><span class="sxs-lookup"><span data-stu-id="09e6e-204">Ranking</span></span>|<span data-ttu-id="09e6e-205">いいえ</span><span class="sxs-lookup"><span data-stu-id="09e6e-205">No</span></span>|

### <a name="fast-tree"></a><span data-ttu-id="09e6e-206">Fast tree (高速ツリー)</span><span class="sxs-lookup"><span data-stu-id="09e6e-206">Fast tree</span></span>

<span data-ttu-id="09e6e-207">特徴付けされた画像データに使用します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-207">Use for featurized image data.</span></span> <span data-ttu-id="09e6e-208">不均衡なデータに対応できます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-208">Resilient to unbalanced data.</span></span> <span data-ttu-id="09e6e-209">高度に調整可能。</span><span class="sxs-lookup"><span data-stu-id="09e6e-209">Highly tunable.</span></span>

|<span data-ttu-id="09e6e-210">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-210">Trainer</span></span>|<span data-ttu-id="09e6e-211">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-211">Task</span></span>|<span data-ttu-id="09e6e-212">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-212">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>|<span data-ttu-id="09e6e-213">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-213">Binary classification</span></span>|<span data-ttu-id="09e6e-214">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-214">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>|<span data-ttu-id="09e6e-215">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-215">Regression</span></span>|<span data-ttu-id="09e6e-216">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-216">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>|<span data-ttu-id="09e6e-217">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-217">Regression</span></span>|<span data-ttu-id="09e6e-218">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-218">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|<span data-ttu-id="09e6e-219">順位付け</span><span class="sxs-lookup"><span data-stu-id="09e6e-219">Ranking</span></span>|<span data-ttu-id="09e6e-220">いいえ</span><span class="sxs-lookup"><span data-stu-id="09e6e-220">No</span></span>|

### <a name="fast-forest"></a><span data-ttu-id="09e6e-221">Fast forest (高速フォレスト)</span><span class="sxs-lookup"><span data-stu-id="09e6e-221">Fast forest</span></span>

<span data-ttu-id="09e6e-222">ノイズの多いデータに適しています。</span><span class="sxs-lookup"><span data-stu-id="09e6e-222">Works well with noisy data.</span></span>

|<span data-ttu-id="09e6e-223">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-223">Trainer</span></span>|<span data-ttu-id="09e6e-224">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-224">Task</span></span>|<span data-ttu-id="09e6e-225">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-225">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>|<span data-ttu-id="09e6e-226">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-226">Binary classification</span></span>|<span data-ttu-id="09e6e-227">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-227">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|<span data-ttu-id="09e6e-228">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-228">Regression</span></span>|<span data-ttu-id="09e6e-229">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-229">Yes</span></span>|

### <a name="generalized-additive-model-gam"></a><span data-ttu-id="09e6e-230">Generalized Additive Model (一般化加法モデル、GAM)</span><span class="sxs-lookup"><span data-stu-id="09e6e-230">Generalized additive model (GAM)</span></span>

<span data-ttu-id="09e6e-231">ツリー アルゴリズムに適した問題で、説明可能性が優先される場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-231">Best for problems that perform well with tree algorithms but where explainability is a priority.</span></span>

|<span data-ttu-id="09e6e-232">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-232">Trainer</span></span>|<span data-ttu-id="09e6e-233">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-233">Task</span></span>|<span data-ttu-id="09e6e-234">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-234">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>|<span data-ttu-id="09e6e-235">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-235">Binary classification</span></span>|<span data-ttu-id="09e6e-236">いいえ</span><span class="sxs-lookup"><span data-stu-id="09e6e-236">No</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|<span data-ttu-id="09e6e-237">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-237">Regression</span></span>|<span data-ttu-id="09e6e-238">いいえ</span><span class="sxs-lookup"><span data-stu-id="09e6e-238">No</span></span>|

## <a name="matrix-factorization"></a><span data-ttu-id="09e6e-239">行列因子分解</span><span class="sxs-lookup"><span data-stu-id="09e6e-239">Matrix factorization</span></span>

### <a name="matrix-factorization"></a><span data-ttu-id="09e6e-240">行列因子分解</span><span class="sxs-lookup"><span data-stu-id="09e6e-240">Matrix Factorization</span></span>

<span data-ttu-id="09e6e-241">レコメンデーションでの[協調フィルター処理](https://en.wikipedia.org/wiki/Collaborative_filtering)に使用されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-241">Used for [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) in recommendation.</span></span>

|<span data-ttu-id="09e6e-242">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-242">Trainer</span></span>|<span data-ttu-id="09e6e-243">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-243">Task</span></span>|<span data-ttu-id="09e6e-244">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-244">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>|<span data-ttu-id="09e6e-245">推奨</span><span class="sxs-lookup"><span data-stu-id="09e6e-245">Recommendation</span></span>|<span data-ttu-id="09e6e-246">いいえ</span><span class="sxs-lookup"><span data-stu-id="09e6e-246">No</span></span>|

### <a name="field-aware-factorization-machine"></a><span data-ttu-id="09e6e-247">Field Aware Factorization Machine</span><span class="sxs-lookup"><span data-stu-id="09e6e-247">Field Aware Factorization Machine</span></span>

 <span data-ttu-id="09e6e-248">データセットが大規模で、カテゴリ別のスパース データに最適です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-248">Best for sparse categorical data, with large datasets.</span></span>

|<span data-ttu-id="09e6e-249">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-249">Trainer</span></span>|<span data-ttu-id="09e6e-250">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-250">Task</span></span>|<span data-ttu-id="09e6e-251">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-251">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|<span data-ttu-id="09e6e-252">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-252">Binary classification</span></span>|<span data-ttu-id="09e6e-253">いいえ</span><span class="sxs-lookup"><span data-stu-id="09e6e-253">No</span></span>|

## <a name="meta-algorithms"></a><span data-ttu-id="09e6e-254">メタ アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="09e6e-254">Meta algorithms</span></span>

<span data-ttu-id="09e6e-255">これらのトレーナーでは、二項トレーナーから多クラストレーナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-255">These trainers create a multiclass trainer from a binary trainer.</span></span> <span data-ttu-id="09e6e-256"><xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>、<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>、<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>、<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>、<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>、<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>、<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-256">Use with <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.</span></span>

### <a name="one-versus-all"></a><span data-ttu-id="09e6e-257">One versus all (1 対すべて)</span><span class="sxs-lookup"><span data-stu-id="09e6e-257">One versus all</span></span>

<span data-ttu-id="09e6e-258">この多クラス分類子では、クラスごとに 1 つの二項分類子がトレーニングされます。これにより、そのクラスは他のすべてのクラスと区別されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-258">This multiclass classifier trains one binary classifier for each class, which distinguishes that class from all other classes.</span></span> <span data-ttu-id="09e6e-259">分類するクラスの数によってスケールが制限されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-259">Is limited in scale by the number of classes to categorize.</span></span>

|<span data-ttu-id="09e6e-260">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-260">Trainer</span></span>|<span data-ttu-id="09e6e-261">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-261">Task</span></span>|<span data-ttu-id="09e6e-262">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-262">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OneVersusAllTrainer>|<span data-ttu-id="09e6e-263">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-263">Multiclass classification</span></span>|<span data-ttu-id="09e6e-264">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-264">Yes</span></span>|

### <a name="pairwise-coupling"></a><span data-ttu-id="09e6e-265">Pairwise coupling (ペアワイズ結合)</span><span class="sxs-lookup"><span data-stu-id="09e6e-265">Pairwise coupling</span></span>

<span data-ttu-id="09e6e-266">この多クラス分類子では、クラスの各ペアに対して二項分類アルゴリズムがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-266">This multiclass classifier trains a binary classification algorithm on each pair of classes.</span></span> <span data-ttu-id="09e6e-267">2 つのクラスの各組み合わせをトレーニングする必要があるので、クラスの数によってスケールが制限されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-267">Is limited in scale by the number of classes, as each combination of two classes must be trained.</span></span>

|<span data-ttu-id="09e6e-268">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-268">Trainer</span></span>|<span data-ttu-id="09e6e-269">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-269">Task</span></span>|<span data-ttu-id="09e6e-270">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-270">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>|<span data-ttu-id="09e6e-271">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-271">Multiclass classification</span></span>|<span data-ttu-id="09e6e-272">いいえ</span><span class="sxs-lookup"><span data-stu-id="09e6e-272">No</span></span>|

## <a name="k-means"></a><span data-ttu-id="09e6e-273">K-Means</span><span class="sxs-lookup"><span data-stu-id="09e6e-273">K-Means</span></span>

<span data-ttu-id="09e6e-274">クラスタリングに使用されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-274">Used for clustering.</span></span>

|<span data-ttu-id="09e6e-275">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-275">Trainer</span></span>|<span data-ttu-id="09e6e-276">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-276">Task</span></span>|<span data-ttu-id="09e6e-277">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-277">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.KMeansTrainer>|<span data-ttu-id="09e6e-278">クラスタリング</span><span class="sxs-lookup"><span data-stu-id="09e6e-278">Clustering</span></span>|<span data-ttu-id="09e6e-279">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-279">Yes</span></span>|

## <a name="principal-component-analysis"></a><span data-ttu-id="09e6e-280">主成分分析</span><span class="sxs-lookup"><span data-stu-id="09e6e-280">Principal component analysis</span></span>

<span data-ttu-id="09e6e-281">異常検出に使用されます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-281">Used for anomaly detection.</span></span>

|<span data-ttu-id="09e6e-282">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-282">Trainer</span></span>|<span data-ttu-id="09e6e-283">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-283">Task</span></span>|<span data-ttu-id="09e6e-284">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-284">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|<span data-ttu-id="09e6e-285">異常検出</span><span class="sxs-lookup"><span data-stu-id="09e6e-285">Anomaly detection</span></span>|<span data-ttu-id="09e6e-286">いいえ</span><span class="sxs-lookup"><span data-stu-id="09e6e-286">No</span></span>|

## <a name="naive-bayes"></a><span data-ttu-id="09e6e-287">Naive Bayes</span><span class="sxs-lookup"><span data-stu-id="09e6e-287">Naive Bayes</span></span>

<span data-ttu-id="09e6e-288">特徴が独立しており、トレーニング データセットが小さい場合は、この多クラス分類アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-288">Use this multi-class classification algorithm when the features are independent, and the training dataset is small.</span></span>

|<span data-ttu-id="09e6e-289">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-289">Trainer</span></span>|<span data-ttu-id="09e6e-290">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-290">Task</span></span>|<span data-ttu-id="09e6e-291">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-291">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|<span data-ttu-id="09e6e-292">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-292">Multiclass classification</span></span>|<span data-ttu-id="09e6e-293">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-293">Yes</span></span>|

## <a name="prior-trainer"></a><span data-ttu-id="09e6e-294">以前のトレーナー</span><span class="sxs-lookup"><span data-stu-id="09e6e-294">Prior Trainer</span></span>

<span data-ttu-id="09e6e-295">他のトレーナーのパフォーマンスを基準にするには、この二項分類アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-295">Use this binary classification algorithm to baseline the performance of other trainers.</span></span> <span data-ttu-id="09e6e-296">他のトレーナーのメトリックは以前のトレーナーよりも効果の点で優れています。</span><span class="sxs-lookup"><span data-stu-id="09e6e-296">To be effective, the metrics of the other trainers should be better than the prior trainer.</span></span>

|<span data-ttu-id="09e6e-297">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-297">Trainer</span></span>|<span data-ttu-id="09e6e-298">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-298">Task</span></span>|<span data-ttu-id="09e6e-299">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-299">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PriorTrainer>|<span data-ttu-id="09e6e-300">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-300">Binary classification</span></span>|<span data-ttu-id="09e6e-301">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-301">Yes</span></span>|

## <a name="support-vector-machines"></a><span data-ttu-id="09e6e-302">サポート ベクター マシン</span><span class="sxs-lookup"><span data-stu-id="09e6e-302">Support vector machines</span></span>

<span data-ttu-id="09e6e-303">サポート ベクター マシン (SVM) は非常に人気があり、よく研究されているクラスの教師あり学習モデルで、線形と非線形の分類タスクで使用できます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-303">Support vector machines (SVMs) are an extremely popular and well-researched class of supervised learning models, which can be used in linear and non-linear classification tasks.</span></span>

<span data-ttu-id="09e6e-304">最近の研究では、より大規模なトレーニング セットに合わせて効率的に拡大できるようにこれらのモデルを最適化する方法に重点が置かれています。</span><span class="sxs-lookup"><span data-stu-id="09e6e-304">Recent research has focused on ways to optimize these models to efficiently scale to larger training sets.</span></span>

### <a name="linear-svm"></a><span data-ttu-id="09e6e-305">リニア SVM</span><span class="sxs-lookup"><span data-stu-id="09e6e-305">Linear SVM</span></span>

<span data-ttu-id="09e6e-306">ブール値のラベル付きデータに対してトレーニングされた線形二項分類モデルを使用して、ターゲットを予測します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-306">Predicts a target using a linear binary classification model trained over boolean labeled data.</span></span> <span data-ttu-id="09e6e-307">確率的勾配降下法ステップと射影ステップを交互に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="09e6e-307">Alternates between stochastic gradient descent steps and projection steps.</span></span>

|<span data-ttu-id="09e6e-308">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-308">Trainer</span></span>|<span data-ttu-id="09e6e-309">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-309">Task</span></span>|<span data-ttu-id="09e6e-310">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-310">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LinearSvmTrainer>|<span data-ttu-id="09e6e-311">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-311">Binary classification</span></span>|<span data-ttu-id="09e6e-312">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-312">Yes</span></span>|

### <a name="local-deep-svm"></a><span data-ttu-id="09e6e-313">ローカル ディープ SVM</span><span class="sxs-lookup"><span data-stu-id="09e6e-313">Local Deep SVM</span></span>

<span data-ttu-id="09e6e-314">非線形二項分類モデルを使用してターゲットを予測します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-314">Predicts a target using a non-linear binary classification model.</span></span> <span data-ttu-id="09e6e-315">予測時間のコストを削減します。予測コストは、線形ではなくトレーニング セットのサイズに応じて対数的に増加し、分類精度の低下は許容可能です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-315">Reduces the prediction time cost; the prediction cost grows logarithmically with the size of the training set, rather than linearly, with a tolerable loss in classification accuracy.</span></span>

|<span data-ttu-id="09e6e-316">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-316">Trainer</span></span>|<span data-ttu-id="09e6e-317">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-317">Task</span></span>|<span data-ttu-id="09e6e-318">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-318">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LdSvmTrainer>|<span data-ttu-id="09e6e-319">二項分類</span><span class="sxs-lookup"><span data-stu-id="09e6e-319">Binary classification</span></span>|<span data-ttu-id="09e6e-320">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-320">Yes</span></span>|

## <a name="ordinary-least-squares"></a><span data-ttu-id="09e6e-321">最小二乗法</span><span class="sxs-lookup"><span data-stu-id="09e6e-321">Ordinary least squares</span></span>

<span data-ttu-id="09e6e-322">最小二乗法 (OLS) は、線形回帰で最も一般的に使用される技術です。</span><span class="sxs-lookup"><span data-stu-id="09e6e-322">Ordinary least squares (OLS) is one of the most commonly used techniques in linear regression.</span></span>

<span data-ttu-id="09e6e-323">通常の最小二乗法は、実績値から予測された線までの距離の平方の合計として誤差を計算し、二乗エラーを最小限にすることでモデルを適合させる損失関数を示します。</span><span class="sxs-lookup"><span data-stu-id="09e6e-323">Ordinary least squares refers to the loss function, which computes error as the sum of the square of distance from the actual value to the predicted line, and fits the model by minimizing the squared error.</span></span> <span data-ttu-id="09e6e-324">このメソッドは、入力と従属変数との間の強力な線形関係を前提とします。</span><span class="sxs-lookup"><span data-stu-id="09e6e-324">This method assumes a strong linear relationship between the inputs and the dependent variable.</span></span>

|<span data-ttu-id="09e6e-325">Trainer</span><span class="sxs-lookup"><span data-stu-id="09e6e-325">Trainer</span></span>|<span data-ttu-id="09e6e-326">タスク</span><span class="sxs-lookup"><span data-stu-id="09e6e-326">Task</span></span>|<span data-ttu-id="09e6e-327">ONNX エクスポート可能</span><span class="sxs-lookup"><span data-stu-id="09e6e-327">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OlsTrainer>|<span data-ttu-id="09e6e-328">回帰</span><span class="sxs-lookup"><span data-stu-id="09e6e-328">Regression</span></span>|<span data-ttu-id="09e6e-329">はい</span><span class="sxs-lookup"><span data-stu-id="09e6e-329">Yes</span></span>|
