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
# <a name="how-to-choose-an-mlnet-algorithm"></a>ML.NET アルゴリズムの選び方

[ML.NET タスク](resources/tasks.md) ごとに選択できるトレーニング アルゴリズムは複数あります。 どれを選択するかは、解決しようとしている問題、データの特性、利用できるコンピューティング リソースとストレージ リソースによって変わります。 機械学習モデルのトレーニングは反復処理である点に注意することが重要です。 場合によっては、最適なものを見つけるために複数のアルゴリズムを試す必要があります。

アルゴリズムは **特徴** に対して動作します。 特徴は、入力データから計算された数値です。 それらは機械学習アルゴリズムに最適な入力です。 生の入力データを 1 つ以上の[データ変換](resources/transforms.md)を使用して特徴に変換します。 たとえば、テキスト データは、単語数と単語の組み合わせ数のセットに変換されます。 データ変換を使用して生のデータの種類から特徴が抽出されると、**特徴付けされた** と呼ばれます。 たとえば、特徴付けされたテキスト、特徴付けされた画像データなどです。

## <a name="trainer--algorithm--task"></a>トレーナー = アルゴリズム + タスク

アルゴリズムは、**モデル** を生成するために実行される数学です。 アルゴリズムが異なると、特性が異なるモデルが生成されます。

ML.NET では、同じアルゴリズムを異なるタスクに適用できます。 たとえば、確率的双対座標上昇法は、二項分類、多クラス分類、回帰に使用できます。 違いは、タスクに合わせてアルゴリズムの出力が解釈される方法にあります。

ML.NET には、各アルゴリズムとタスクの組み合わせに対して、トレーニング アルゴリズムを実行し、解釈するコンポーネントが用意されています。 これらのコンポーネントはトレーナーと呼ばれます。 たとえば、<xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> には、**回帰** タスクに適用される **StochasticDualCoordinatedAscent** アルゴリズムが使用されます。

## <a name="linear-algorithms"></a>線形アルゴリズム

線形アルゴリズムでは、入力データと一連の **重み** の線形結合から **スコア** を計算するモデルが生成されます。 重みは、トレーニング中に推定されるモデルのパラメーターです。

線形アルゴリズムは、[線形分離可能](https://en.wikipedia.org/wiki/Linear_separability)である特徴の場合に適しています。

線形アルゴリズムでトレーニングする前に、特徴を正規化しておくことをお勧めします。 こうすることで、ある特徴が他の特徴よりも結果に大きな影響を及ぼすことを防ぎます。

一般に、線形アルゴリズムはスケーラブルで高速であり、トレーニング コストが低コストで、予測も低コストです。 これらは、特徴の数と、おおよそのトレーニング データ セットのサイズによってスケールします。

線形アルゴリズムは、トレーニング データに対して複数回実行されます。 データセットがメモリに収まる場合は、トレーナーを追加する前に ML.NET パイプラインに[キャッシュ チェックポイント](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A)を追加すると、トレーニングが高速になります。

### <a name="averaged-perceptron"></a>Averaged perceptron (平均化パーセプトロン)

テキスト分類に最適です。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|二項分類|はい|

### <a name="stochastic-dual-coordinated-ascent"></a>確率的双対座標上昇法

既定のパフォーマンスが適切な場合、調整は不要です。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>|二項分類|はい|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>|二項分類|はい|
|<xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>|多クラス分類|はい|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>|多クラス分類|はい|
|<xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|回帰|はい|

### <a name="l-bfgs"></a>L-BFGS

特徴数が多い場合に使用します。 ロジスティック回帰トレーニング統計を生成しますが、AveragedPerceptronTrainer ほどスケーリングしません

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>|二項分類|はい|
|<xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>|多クラス分類|はい|
|<xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|回帰|はい|

### <a name="symbolic-stochastic-gradient-descent"></a>Symbolic stochastic gradient descent (シンボリック確率的勾配降下法)

最も高速で最も正確な線形二項分類トレーナー。 プロセッサの数に合わせてスケーリングします。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|二項分類|はい|

### <a name="online-gradient-descent"></a>オンライン勾配降下

選択した損失関数と、時間の経過と共に表示されるベクターの平均を使用して重みベクトルを更新するオプションを使用して、標準 (非バッチ) 確率的勾配降下法を実装します。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>|回帰|はい|

## <a name="decision-tree-algorithms"></a>デシジョン ツリー アルゴリズム

デシジョン ツリー アルゴリズムは、一連の決定を含むモデルを作成します。事実上、データ値を通るフロー チャートです。

この種類のアルゴリズムを使用するために、特徴が線形に分離可能である必要はありません。 また、特徴ベクター内の個々の値は決定プロセスで独立して使用されるため、特徴を正規化する必要はありません。

一般的に、デシジョン ツリー アルゴリズムは非常に正確です。

Generalized Additive Model (一般化加法モデル、GAM) を除き、特徴の数が多いと、説明可能性のないツリー モデルになる可能性があります。

デシジョン ツリー アルゴリズムに消費されるリソースは多く、線形アルゴリズムほどスケールしません。 メモリに収まるようなデータセットに対しては適切に動作します。

Boosted decision trees (ブースト デシジョン ツリー) は小さなツリーの集合であり、各ツリーで入力データにスコアが付けられ、そのスコアは次のツリーに渡され、より良いスコアが生成されるという処理が繰り返されます。集合内の各ツリーは、前のツリーに基づいて改善されます。

### <a name="light-gradient-boosted-machine"></a>Light gradient boosted machine (軽勾配ブースト マシン)

最も高速で最も正確な二項分類ツリー トレーナー。 高度に調整可能。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>|二項分類|はい|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>|多クラス分類|はい|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>|回帰|はい|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|順位付け|いいえ|

### <a name="fast-tree"></a>Fast tree (高速ツリー)

特徴付けされた画像データに使用します。 不均衡なデータに対応できます。 高度に調整可能。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>|二項分類|はい|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>|回帰|はい|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>|回帰|はい|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|順位付け|いいえ|

### <a name="fast-forest"></a>Fast forest (高速フォレスト)

ノイズの多いデータに適しています。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>|二項分類|はい|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|回帰|はい|

### <a name="generalized-additive-model-gam"></a>Generalized Additive Model (一般化加法モデル、GAM)

ツリー アルゴリズムに適した問題で、説明可能性が優先される場合に最適です。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>|二項分類|いいえ|
|<xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|回帰|いいえ|

## <a name="matrix-factorization"></a>行列因子分解

### <a name="matrix-factorization"></a>行列因子分解

レコメンデーションでの[協調フィルター処理](https://en.wikipedia.org/wiki/Collaborative_filtering)に使用されます。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>|推奨|いいえ|

### <a name="field-aware-factorization-machine"></a>Field Aware Factorization Machine

 データセットが大規模で、カテゴリ別のスパース データに最適です。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|二項分類|いいえ|

## <a name="meta-algorithms"></a>メタ アルゴリズム

これらのトレーナーでは、二項トレーナーから多クラストレーナーを作成します。 <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>、<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>、<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>、<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>、<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>、<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>、<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> と共に使用します。

### <a name="one-versus-all"></a>One versus all (1 対すべて)

この多クラス分類子では、クラスごとに 1 つの二項分類子がトレーニングされます。これにより、そのクラスは他のすべてのクラスと区別されます。 分類するクラスの数によってスケールが制限されます。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OneVersusAllTrainer>|多クラス分類|はい|

### <a name="pairwise-coupling"></a>Pairwise coupling (ペアワイズ結合)

この多クラス分類子では、クラスの各ペアに対して二項分類アルゴリズムがトレーニングされます。 2 つのクラスの各組み合わせをトレーニングする必要があるので、クラスの数によってスケールが制限されます。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>|多クラス分類|いいえ|

## <a name="k-means"></a>K-Means

クラスタリングに使用されます。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.KMeansTrainer>|クラスタリング|はい|

## <a name="principal-component-analysis"></a>主成分分析

異常検出に使用されます。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|異常検出|いいえ|

## <a name="naive-bayes"></a>Naive Bayes

特徴が独立しており、トレーニング データセットが小さい場合は、この多クラス分類アルゴリズムを使用します。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|多クラス分類|はい|

## <a name="prior-trainer"></a>以前のトレーナー

他のトレーナーのパフォーマンスを基準にするには、この二項分類アルゴリズムを使用します。 他のトレーナーのメトリックは以前のトレーナーよりも効果の点で優れています。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PriorTrainer>|二項分類|はい|

## <a name="support-vector-machines"></a>サポート ベクター マシン

サポート ベクター マシン (SVM) は非常に人気があり、よく研究されているクラスの教師あり学習モデルで、線形と非線形の分類タスクで使用できます。

最近の研究では、より大規模なトレーニング セットに合わせて効率的に拡大できるようにこれらのモデルを最適化する方法に重点が置かれています。

### <a name="linear-svm"></a>リニア SVM

ブール値のラベル付きデータに対してトレーニングされた線形二項分類モデルを使用して、ターゲットを予測します。 確率的勾配降下法ステップと射影ステップを交互に切り替えます。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LinearSvmTrainer>|二項分類|はい|

### <a name="local-deep-svm"></a>ローカル ディープ SVM

非線形二項分類モデルを使用してターゲットを予測します。 予測時間のコストを削減します。予測コストは、線形ではなくトレーニング セットのサイズに応じて対数的に増加し、分類精度の低下は許容可能です。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LdSvmTrainer>|二項分類|はい|

## <a name="ordinary-least-squares"></a>最小二乗法

最小二乗法 (OLS) は、線形回帰で最も一般的に使用される技術です。

通常の最小二乗法は、実績値から予測された線までの距離の平方の合計として誤差を計算し、二乗エラーを最小限にすることでモデルを適合させる損失関数を示します。 このメソッドは、入力と従属変数との間の強力な線形関係を前提とします。

|Trainer|タスク|ONNX エクスポート可能|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OlsTrainer>|回帰|はい|
