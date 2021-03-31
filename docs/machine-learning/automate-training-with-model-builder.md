---
title: モデル ビルダーの概要としくみ
description: ML.NET モデル ビルダーを使用し、機械学習モデルを自動的にトレーニングする方法
ms.date: 06/01/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: d7566a03f83eb76999d995a39aaae408405db2e1
ms.sourcegitcommit: b27645cb378d4e8137a267e5467ff31409acf6c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2021
ms.locfileid: "103231421"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="f4e90-103">モデル ビルダーの概要としくみ</span><span class="sxs-lookup"><span data-stu-id="f4e90-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="f4e90-104">ML.NET モデル ビルダーは、直観的なグラフィックスでカスタムの機械学習モデルを構築、トレーニング、展開できる Visual Studio 拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="f4e90-105">モデル ビルダーでは自動化された機械学習 (AutoML) を利用してさまざまな機械学習のアルゴリズムや設定を見つけます。自分のシナリオに最適なものを見つけるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="f4e90-106">モデル ビルダーは機械学習の専門知識がなくても使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="f4e90-107">必要なものはいくつかのデータと解決すべき問題です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="f4e90-108">モデル ビルダーでは、.NET アプリケーションにモデルを追加するコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![モデル ビルダー Visual Studio 拡張機能のユーザー インターフェイスのアニメーション](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="f4e90-110">モデル ビルダーは現在のところ、プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="f4e90-111">シナリオ</span><span class="sxs-lookup"><span data-stu-id="f4e90-111">Scenario</span></span>

<span data-ttu-id="f4e90-112">さまざまなシナリオをモデル ビルダーに取り込み、自分のアプリケーションのための機械学習モデルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="f4e90-113">シナリオは、自分のデータを使用して行う予測の種類を説明するものです。</span><span class="sxs-lookup"><span data-stu-id="f4e90-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="f4e90-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-114">For example:</span></span>

- <span data-ttu-id="f4e90-115">過去の販売データに基づいて今後の製品売上高を予測する</span><span class="sxs-lookup"><span data-stu-id="f4e90-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="f4e90-116">顧客のレビューに基づいてセンチメントを肯定的と否定的に分類する</span><span class="sxs-lookup"><span data-stu-id="f4e90-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="f4e90-117">銀行取引が詐欺かどうかを検出する</span><span class="sxs-lookup"><span data-stu-id="f4e90-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="f4e90-118">顧客がフィードバックした問題を社内の該当チームに送信する</span><span class="sxs-lookup"><span data-stu-id="f4e90-118">route customer feedback issues to the correct team in your company</span></span>

<span data-ttu-id="f4e90-119">各シナリオは、次を含む、異なる Machine Learning タスクにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-119">Each scenario maps to a different Machine Learning Task which include:</span></span>

- <span data-ttu-id="f4e90-120">二項分類</span><span class="sxs-lookup"><span data-stu-id="f4e90-120">Binary classification</span></span>
- <span data-ttu-id="f4e90-121">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="f4e90-121">Multiclass classification</span></span>
- <span data-ttu-id="f4e90-122">回帰</span><span class="sxs-lookup"><span data-stu-id="f4e90-122">Regression</span></span>
- <span data-ttu-id="f4e90-123">クラスタリング</span><span class="sxs-lookup"><span data-stu-id="f4e90-123">Clustering</span></span>
- <span data-ttu-id="f4e90-124">異常検出</span><span class="sxs-lookup"><span data-stu-id="f4e90-124">Anomaly detection</span></span>
- <span data-ttu-id="f4e90-125">順位付け</span><span class="sxs-lookup"><span data-stu-id="f4e90-125">Ranking</span></span>
- <span data-ttu-id="f4e90-126">推奨</span><span class="sxs-lookup"><span data-stu-id="f4e90-126">Recommendation</span></span>
- <span data-ttu-id="f4e90-127">予測</span><span class="sxs-lookup"><span data-stu-id="f4e90-127">Forecasting</span></span>

<span data-ttu-id="f4e90-128">たとえば、センチメントをポジティブまたはネガティブとして分類するシナリオは、二項分類タスクに該当します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-128">For example, the scenario of classifying sentiments as positive or negative would fall under the binary classification task.</span></span>

<span data-ttu-id="f4e90-129">ML.NET でサポートされているさまざまな ML タスクに関する詳細については、「[ML.NET での機械学習のタスク](resources/tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4e90-129">For more information about the different ML Tasks supported by ML.NET see [Machine learning tasks in ML.NET](resources/tasks.md).</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="f4e90-130">自分に最適な機械学習シナリオとは?</span><span class="sxs-lookup"><span data-stu-id="f4e90-130">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="f4e90-131">モデル ビルダーでは、シナリオを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-131">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="f4e90-132">シナリオの種類は、行おうとしている予測の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-132">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="f4e90-133">テキスト分類</span><span class="sxs-lookup"><span data-stu-id="f4e90-133">Text classification</span></span>

<span data-ttu-id="f4e90-134">分類は、データをカテゴリに分類するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-134">Classification is used to categorize data into categories.</span></span>

![不正検出、リスク軽減、アプリケーション スクリーニングなど、二項分類の例を示す図](media/binary-classification-examples.png)

![ドキュメントと製品の分類、サポート チケットのルーティング、顧客の問題の優先度設定など、多クラス分類の例](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="f4e90-137">値の予測</span><span class="sxs-lookup"><span data-stu-id="f4e90-137">Value prediction</span></span>

<span data-ttu-id="f4e90-138">回帰タスクに属する値の予測は、数字の予測に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-138">Value prediction, which falls under the regression task, is used to predict numbers.</span></span>

![価格予測、売上予測、予測メンテナンスなどの回帰の例を示す図](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="f4e90-140">イメージ分類</span><span class="sxs-lookup"><span data-stu-id="f4e90-140">Image classification</span></span>

<span data-ttu-id="f4e90-141">イメージ分類は、さまざまなカテゴリのイメージ特定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-141">Image classification is used to identify images of different categories.</span></span> <span data-ttu-id="f4e90-142">これには、さまざまな種類の地形、動物、製造上の不具合などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-142">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="f4e90-143">一連のイメージがあり、イメージをさまざまなカテゴリに分類したいときは、イメージ分類シナリオを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-143">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="object-detection"></a><span data-ttu-id="f4e90-144">オブジェクトの検出</span><span class="sxs-lookup"><span data-stu-id="f4e90-144">Object detection</span></span>

<span data-ttu-id="f4e90-145">オブジェクト検出は、画像内のエンティティの特定と分類に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-145">Object detection is used to locate and categorize entities within images.</span></span>  <span data-ttu-id="f4e90-146">画像に含まれる車や人を見つけ、識別します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-146">For example, locating and identifying cars and people in an image.</span></span>

<span data-ttu-id="f4e90-147">オブジェクト検出は、画像に異なる種類のオブジェクトが複数含まれる場合に利用できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-147">You can use object detection when images contain multiple objects of different types.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="f4e90-148">推奨事項</span><span class="sxs-lookup"><span data-stu-id="f4e90-148">Recommendation</span></span>

<span data-ttu-id="f4e90-149">推奨事項シナリオでは、他のユーザーとの好きや嫌いの類似度に基づいて、特定のユーザーに対する提案項目の一覧が予測されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-149">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="f4e90-150">ユーザーのセットと、"製品" のセット (購入する品目、映画、本、テレビ番組など)、およびそれらの製品に対するユーザーの "評価" のセットがある場合は、推奨事項シナリオを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-150">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="f4e90-151">環境</span><span class="sxs-lookup"><span data-stu-id="f4e90-151">Environment</span></span>

<span data-ttu-id="f4e90-152">シナリオに基づき、お使いのコンピューター上のローカル環境で、または Azure 上のクラウドで、機械学習モデルをトレーニングできます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-152">You can train your machine learning model locally on your machine or in the cloud on Azure, depending on the scenario.</span></span>

<span data-ttu-id="f4e90-153">ローカル環境でトレーニングする場合は、コンピューター リソース (CPU、メモリ、ディスク) の制約内で作業します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-153">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="f4e90-154">クラウドでトレーニングする場合は、シナリオのニーズに合わせて、リソースをスケールアップできます (特に大規模なデータセット)。</span><span class="sxs-lookup"><span data-stu-id="f4e90-154">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="f4e90-155">オブジェクト検出を除くあらゆるシナリオでローカル CPU トレーニングがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f4e90-155">Local CPU training is supported for all scenarios except Object Detection.</span></span>

<span data-ttu-id="f4e90-156">ローカル GPU トレーニングは、イメージ分類でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f4e90-156">Local GPU training is supported for Image Classification.</span></span>

<span data-ttu-id="f4e90-157">Azure トレーニングは、イメージ分類とオブジェクト検出でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f4e90-157">Azure training is supported for Image Classification and Object Detection.</span></span>

## <a name="data"></a><span data-ttu-id="f4e90-158">データ</span><span class="sxs-lookup"><span data-stu-id="f4e90-158">Data</span></span>

<span data-ttu-id="f4e90-159">シナリオを選択すると、モデル ビルダーからデータセットを提供するように求められます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-159">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="f4e90-160">このデータはモデルをトレーニングし、評価し、シナリオに最適なモデルを選択するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-160">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![モデル ビルダーの手順を示す図](media/model-builder-steps.png)

<span data-ttu-id="f4e90-162">モデル ビルダーは、.tsv、.csv、.txt 形式のデータセットと、SQL データベース形式をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f4e90-162">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="f4e90-163">.txt ファイルがある場合、列は `,`、`;`、または `/t` で区切る必要があり、ファイルにはヘッダー行が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-163">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="f4e90-164">データセットがイメージで構成されている場合、サポートされているファイルの種類は `.jpg` と `.png`です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-164">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="f4e90-165">詳細については、「[モデル ビルダーにトレーニング データを読み込む](how-to-guides/load-data-model-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4e90-165">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="f4e90-166">予測する出力を選択します (ラベル)</span><span class="sxs-lookup"><span data-stu-id="f4e90-166">Choose the output to predict (label)</span></span>

<span data-ttu-id="f4e90-167">データセットは、トレーニング サンプルの行と属性の列からなるテーブルです。</span><span class="sxs-lookup"><span data-stu-id="f4e90-167">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="f4e90-168">各行の内容:</span><span class="sxs-lookup"><span data-stu-id="f4e90-168">Each row has:</span></span>

- <span data-ttu-id="f4e90-169">**ラベル** (予測する属性)</span><span class="sxs-lookup"><span data-stu-id="f4e90-169">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="f4e90-170">**特徴** (ラベルを予測するための入力として使用される属性)。</span><span class="sxs-lookup"><span data-stu-id="f4e90-170">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="f4e90-171">家の価格予測シナリオの場合、特徴は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-171">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="f4e90-172">家の面積</span><span class="sxs-lookup"><span data-stu-id="f4e90-172">the square footage of the house</span></span>
- <span data-ttu-id="f4e90-173">寝室と浴室の数</span><span class="sxs-lookup"><span data-stu-id="f4e90-173">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="f4e90-174">郵便番号</span><span class="sxs-lookup"><span data-stu-id="f4e90-174">the zip code</span></span>

<span data-ttu-id="f4e90-175">ラベルは、面積、寝室数、浴室数、郵便番号からなるその行の過去の住宅価格です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-175">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![サイズ、部屋数、郵便番号、価格ラベルから構成される特徴を持つ住宅価格データからなる行と列を示す表](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="f4e90-177">データセットの例</span><span class="sxs-lookup"><span data-stu-id="f4e90-177">Example datasets</span></span>

<span data-ttu-id="f4e90-178">独自のデータをまだ用意していない場合、次のいずれかのデータセットをお試しください。</span><span class="sxs-lookup"><span data-stu-id="f4e90-178">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="f4e90-179">シナリオ</span><span class="sxs-lookup"><span data-stu-id="f4e90-179">Scenario</span></span>|<span data-ttu-id="f4e90-180">例</span><span class="sxs-lookup"><span data-stu-id="f4e90-180">Example</span></span>|<span data-ttu-id="f4e90-181">データ</span><span class="sxs-lookup"><span data-stu-id="f4e90-181">Data</span></span>|<span data-ttu-id="f4e90-182">ラベル</span><span class="sxs-lookup"><span data-stu-id="f4e90-182">Label</span></span>|<span data-ttu-id="f4e90-183">フィーチャー</span><span class="sxs-lookup"><span data-stu-id="f4e90-183">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="f4e90-184">分類</span><span class="sxs-lookup"><span data-stu-id="f4e90-184">Classification</span></span>|<span data-ttu-id="f4e90-185">売上の異常を予測する</span><span class="sxs-lookup"><span data-stu-id="f4e90-185">Predict sales anomalies</span></span>|[<span data-ttu-id="f4e90-186">製品の売上データ</span><span class="sxs-lookup"><span data-stu-id="f4e90-186">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="f4e90-187">製品の売上</span><span class="sxs-lookup"><span data-stu-id="f4e90-187">Product Sales</span></span>|<span data-ttu-id="f4e90-188">月</span><span class="sxs-lookup"><span data-stu-id="f4e90-188">Month</span></span>|
||<span data-ttu-id="f4e90-189">Web サイトのコメントのセンチメントを予測する</span><span class="sxs-lookup"><span data-stu-id="f4e90-189">Predict sentiment of website comments</span></span>|[<span data-ttu-id="f4e90-190">Web サイトのコメント データ</span><span class="sxs-lookup"><span data-stu-id="f4e90-190">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="f4e90-191">ラベル (否定的なセンチメントのときは 0、肯定的なセンチメントのときは 1)</span><span class="sxs-lookup"><span data-stu-id="f4e90-191">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="f4e90-192">コメント、年度</span><span class="sxs-lookup"><span data-stu-id="f4e90-192">Comment, Year</span></span>|
||<span data-ttu-id="f4e90-193">クレジット カード取引の詐欺を予測する</span><span class="sxs-lookup"><span data-stu-id="f4e90-193">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="f4e90-194">クレジット カードのデータ</span><span class="sxs-lookup"><span data-stu-id="f4e90-194">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CCFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="f4e90-195">クラス (詐欺の場合は 1、それ以外の場合 0)</span><span class="sxs-lookup"><span data-stu-id="f4e90-195">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="f4e90-196">金額、V1-V28 (匿名化された特徴)</span><span class="sxs-lookup"><span data-stu-id="f4e90-196">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="f4e90-197">GitHub リポジトリでのイシューの種類を予測する</span><span class="sxs-lookup"><span data-stu-id="f4e90-197">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="f4e90-198">GitHub 問題のデータ</span><span class="sxs-lookup"><span data-stu-id="f4e90-198">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="f4e90-199">区分</span><span class="sxs-lookup"><span data-stu-id="f4e90-199">Area</span></span>|<span data-ttu-id="f4e90-200">タイトル、説明</span><span class="sxs-lookup"><span data-stu-id="f4e90-200">Title, Description</span></span>|
|<span data-ttu-id="f4e90-201">値の予測</span><span class="sxs-lookup"><span data-stu-id="f4e90-201">Value prediction</span></span>|<span data-ttu-id="f4e90-202">タクシー料金を予測する</span><span class="sxs-lookup"><span data-stu-id="f4e90-202">Predict taxi fare price</span></span>|[<span data-ttu-id="f4e90-203">タクシーの料金データ</span><span class="sxs-lookup"><span data-stu-id="f4e90-203">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="f4e90-204">料金</span><span class="sxs-lookup"><span data-stu-id="f4e90-204">Fare</span></span>|<span data-ttu-id="f4e90-205">乗車時間、距離</span><span class="sxs-lookup"><span data-stu-id="f4e90-205">Trip time, distance</span></span>|
|<span data-ttu-id="f4e90-206">イメージ分類</span><span class="sxs-lookup"><span data-stu-id="f4e90-206">Image classification</span></span>|<span data-ttu-id="f4e90-207">花の種類を予測する</span><span class="sxs-lookup"><span data-stu-id="f4e90-207">Predict the category of a flower</span></span> |[<span data-ttu-id="f4e90-208">花の画像</span><span class="sxs-lookup"><span data-stu-id="f4e90-208">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="f4e90-209">花の種類: デイジー、タンポポ、バラ、ヒマワリ、チューリップ</span><span class="sxs-lookup"><span data-stu-id="f4e90-209">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="f4e90-210">イメージ データ自体</span><span class="sxs-lookup"><span data-stu-id="f4e90-210">The image data itself</span></span>|
|<span data-ttu-id="f4e90-211">推奨事項</span><span class="sxs-lookup"><span data-stu-id="f4e90-211">Recommendation</span></span>|<span data-ttu-id="f4e90-212">好きな映画を予測する</span><span class="sxs-lookup"><span data-stu-id="f4e90-212">Predict movies that someone will like</span></span>|[<span data-ttu-id="f4e90-213">映画の評価</span><span class="sxs-lookup"><span data-stu-id="f4e90-213">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="f4e90-214">ユーザー、映画</span><span class="sxs-lookup"><span data-stu-id="f4e90-214">Users, Movies</span></span>|<span data-ttu-id="f4e90-215">評価</span><span class="sxs-lookup"><span data-stu-id="f4e90-215">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="f4e90-216">トレーニング</span><span class="sxs-lookup"><span data-stu-id="f4e90-216">Train</span></span>

<span data-ttu-id="f4e90-217">シナリオ、環境、データ、ラベルを選択すると、モデル ビルダーによってモデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-217">Once you select your scenario, environment, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="f4e90-218">トレーニングとは何か?</span><span class="sxs-lookup"><span data-stu-id="f4e90-218">What is training?</span></span>

<span data-ttu-id="f4e90-219">トレーニングとは、モデル ビルダーがシナリオの質問に対する回答方法をモデルに教える自動プロセスです。</span><span class="sxs-lookup"><span data-stu-id="f4e90-219">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="f4e90-220">トレーニングが終わると、モデルは以前に見たことがない入力データで予測できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-220">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="f4e90-221">たとえば、住宅価格を予測しているなら、新しい住宅が市場に出たとき、その販売価格を予測できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-221">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="f4e90-222">モデル ビルダーで使用される機械学習は自動化されているため (AutoML)、トレーニング中に、ユーザーが入力したり、調整したりする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="f4e90-222">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="f4e90-223">どのくらいの時間、トレーニングしますか?</span><span class="sxs-lookup"><span data-stu-id="f4e90-223">How long should I train for?</span></span>

<span data-ttu-id="f4e90-224">モデル ビルダーは、AutoML を使用して複数のモデルを探索し、最適なパフォーマンスを発揮するモデルを見つけます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-224">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="f4e90-225">トレーニング期間を長くすると、AutoML はより広い設定範囲でさらに多くのモデルを探索できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-225">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="f4e90-226">以下の表は、ローカル コンピューターにある一連のサンプル データセットで、優れたパフォーマンスを得るのに要した平均時間を示しています。</span><span class="sxs-lookup"><span data-stu-id="f4e90-226">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="f4e90-227">データセットのサイズ</span><span class="sxs-lookup"><span data-stu-id="f4e90-227">Dataset size</span></span>|<span data-ttu-id="f4e90-228">トレーニングの平均時間</span><span class="sxs-lookup"><span data-stu-id="f4e90-228">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="f4e90-229">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="f4e90-229">0 - 10 MB</span></span>|<span data-ttu-id="f4e90-230">10 秒</span><span class="sxs-lookup"><span data-stu-id="f4e90-230">10 sec</span></span>|
|<span data-ttu-id="f4e90-231">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="f4e90-231">10 - 100 MB</span></span>|<span data-ttu-id="f4e90-232">10 分</span><span class="sxs-lookup"><span data-stu-id="f4e90-232">10 min</span></span>|
|<span data-ttu-id="f4e90-233">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="f4e90-233">100 - 500 MB</span></span>|<span data-ttu-id="f4e90-234">30 分</span><span class="sxs-lookup"><span data-stu-id="f4e90-234">30 min</span></span>|
|<span data-ttu-id="f4e90-235">500 MB - 1 GB</span><span class="sxs-lookup"><span data-stu-id="f4e90-235">500 - 1 GB</span></span>|<span data-ttu-id="f4e90-236">60 分</span><span class="sxs-lookup"><span data-stu-id="f4e90-236">60 min</span></span>|
|<span data-ttu-id="f4e90-237">1 GB 超</span><span class="sxs-lookup"><span data-stu-id="f4e90-237">1 GB+</span></span>|<span data-ttu-id="f4e90-238">3 時間超</span><span class="sxs-lookup"><span data-stu-id="f4e90-238">3+ hours</span></span>|

<span data-ttu-id="f4e90-239">これらは参考用の数字に過ぎません。</span><span class="sxs-lookup"><span data-stu-id="f4e90-239">These numbers are a guide only.</span></span> <span data-ttu-id="f4e90-240">トレーニングの正確な長さは、次の条件によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-240">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="f4e90-241">モデルへの入力として使用されている特徴 (列) の数</span><span class="sxs-lookup"><span data-stu-id="f4e90-241">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="f4e90-242">列の種類</span><span class="sxs-lookup"><span data-stu-id="f4e90-242">the type of columns</span></span>
- <span data-ttu-id="f4e90-243">ML タスク</span><span class="sxs-lookup"><span data-stu-id="f4e90-243">the ML task</span></span>
- <span data-ttu-id="f4e90-244">トレーニングに使用されるマシンの CPU、ディスク、およびメモリのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="f4e90-244">the CPU, disk, and memory performance of the machine used for training</span></span>

<span data-ttu-id="f4e90-245">通常は、データセットとして 100 行より多くの行を使用することをお勧めします。それ以下では、何も結果が生成されない場合や、トレーニングにかなりの時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-245">It's generally advised that you use more than 100 rows as datasets with less than that may not produce any results and may take a significantly longer time to train.</span></span>

## <a name="evaluate"></a><span data-ttu-id="f4e90-246">評価</span><span class="sxs-lookup"><span data-stu-id="f4e90-246">Evaluate</span></span>

<span data-ttu-id="f4e90-247">評価は、モデルがどのくらい適切かを測定するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f4e90-247">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="f4e90-248">モデル ビルダーは、トレーニングしたモデルを使用して新しいテスト データで予測し、予測の精度を測定します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-248">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="f4e90-249">モデル ビルダーでは、トレーニング セットとテスト セットにトレーニング データが分割されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-249">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="f4e90-250">トレーニング データ (80%) はモデルのトレーニングに使用されます。テスト データ (20%) はモデルの評価のための控えとなります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-250">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="f4e90-251">モデルのパフォーマンスを把握するには</span><span class="sxs-lookup"><span data-stu-id="f4e90-251">How do I understand my model performance?</span></span>

<span data-ttu-id="f4e90-252">シナリオが機械学習タスクにマップされます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-252">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="f4e90-253">各 ML タスクには、独自の評価メトリック セットがあります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-253">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="f4e90-254">値の予測</span><span class="sxs-lookup"><span data-stu-id="f4e90-254">Value prediction</span></span>

<span data-ttu-id="f4e90-255">値の予測問題の既定のメトリックは RSquared で、RSquared の値の範囲は 0 から 1 です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-255">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="f4e90-256">最適な値は 1 です。つまり、RSquared の値が 1 に近いほど、モデルのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-256">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="f4e90-257">絶対損失、二乗損失、RMS 損失など、報告されるその他のメトリックは追加メトリックで、モデルのパフォーマンスを理解し、それを他の値の予測モデルと比較する目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-257">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="f4e90-258">分類 (2 つのカテゴリ)</span><span class="sxs-lookup"><span data-stu-id="f4e90-258">Classification (2 categories)</span></span>

<span data-ttu-id="f4e90-259">分類問題の既定のメトリックは正確度です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-259">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="f4e90-260">正確度は、テスト データセットに基づいてモデルが正しく予測する比率を定めるものです。</span><span class="sxs-lookup"><span data-stu-id="f4e90-260">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="f4e90-261">100%、つまり 1.0 に近ければ近いほど、良いということになります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-261">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="f4e90-262">真陽性率と擬陽性率を測定する AUC (曲線下面積) など、報告されるその他のメトリックは 0.50 以上であれば、モデルは許容されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-262">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="f4e90-263">F1 スコアなどの追加メトリックを使用すると、精度と再現率のバランスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-263">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="f4e90-264">分類 (3 つ以上のカテゴリ)</span><span class="sxs-lookup"><span data-stu-id="f4e90-264">Classification (3+ categories)</span></span>

<span data-ttu-id="f4e90-265">多クラス分類の既定のメトリックはマイクロ正確度です。</span><span class="sxs-lookup"><span data-stu-id="f4e90-265">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="f4e90-266">マイクロ正確度が 100%、つまり 1.0 に近ければ近いほど、良いということになります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-266">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="f4e90-267">多クラス分類のもう 1 つの重要なメトリックはマクロ正確度です。マイクロ正確度と同様、1.0 に近いほど良いことになります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-267">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="f4e90-268">これらの 2 種類の正確度は次のように考えるとよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="f4e90-268">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="f4e90-269">マイクロ正確度: 受信チケットが、どのくらいの頻度で適切なチームに分類されるか。</span><span class="sxs-lookup"><span data-stu-id="f4e90-269">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="f4e90-270">マクロ正確度: 平均的なチームが受け取るチケットが、そのチームにとって適切である頻度はどのくらいか。</span><span class="sxs-lookup"><span data-stu-id="f4e90-270">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="f4e90-271">評価メトリックの詳細</span><span class="sxs-lookup"><span data-stu-id="f4e90-271">More information on evaluation metrics</span></span>

<span data-ttu-id="f4e90-272">詳しくは、[モデルの評価メトリック](resources/metrics.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f4e90-272">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="f4e90-273">改善</span><span class="sxs-lookup"><span data-stu-id="f4e90-273">Improve</span></span>

<span data-ttu-id="f4e90-274">モデルのパフォーマンス スコアが予想ほど良くない場合、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-274">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="f4e90-275">トレーニングの時間を長くします。</span><span class="sxs-lookup"><span data-stu-id="f4e90-275">Train for a longer period of time.</span></span> <span data-ttu-id="f4e90-276">時間を増やせば、自動化された機械学習エンジンによって実験されるアルゴリズムや設定が増えます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-276">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="f4e90-277">データを追加します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-277">Add more data.</span></span> <span data-ttu-id="f4e90-278">高品質の機械学習モデルをトレーニングするにはデータ量が十分ではないことがあります。データセットの例の数が少ない場合は特にこれが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-278">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.This is especially true with datasets that have a small number of examples.</span></span>

- <span data-ttu-id="f4e90-279">データのバランスを調整します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-279">Balance your data.</span></span> <span data-ttu-id="f4e90-280">分類タスクの場合、カテゴリ全体でトレーニング セットのバランスが取れていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f4e90-280">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="f4e90-281">たとえば、100 のトレーニング例に対してクラスが 4 つあるとき、90 個のレコードに最初の 2 つのクラス (tag1 と tag2) を使用するが、残りの 2 つ (tag3 と tag4) は残りの 10 個のレコードでのみ使用する場合、データにバランスが欠け、tag3 か tag4 を正しく予測することがモデルにとって難しくなります。</span><span class="sxs-lookup"><span data-stu-id="f4e90-281">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="f4e90-282">コード</span><span class="sxs-lookup"><span data-stu-id="f4e90-282">Code</span></span>

<span data-ttu-id="f4e90-283">評価フェーズ後、モデル ビルダーからモデル ファイルとコードが出力されます。このコードを使用し、モデルをアプリケーションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-283">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="f4e90-284">ML.NET モデルは zip ファイルで保存されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-284">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="f4e90-285">モデルを読み込み、使用するためのコードがソリューションに新しいプロジェクトとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-285">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="f4e90-286">モデル ビルダーからはサンプル コンソール アプリも追加されます。これを実行すると、実際に動作するモデルを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-286">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="f4e90-287">さらに、モデル ビルダーからはモデルを生成したコードが出力されます。モデルの生成に使用された手順を理解できます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-287">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="f4e90-288">モデル トレーニング コードを使用し、モデルを新しいデータで再トレーニングすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f4e90-288">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="f4e90-289">次の内容</span><span class="sxs-lookup"><span data-stu-id="f4e90-289">What's next?</span></span>

<span data-ttu-id="f4e90-290">モデル ビルダーの Visual Studio 拡張機能の[インストール](how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="f4e90-290">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="f4e90-291">[価格予測または回帰のシナリオ](tutorials/predict-prices-with-model-builder.md)をお試しください。</span><span class="sxs-lookup"><span data-stu-id="f4e90-291">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
