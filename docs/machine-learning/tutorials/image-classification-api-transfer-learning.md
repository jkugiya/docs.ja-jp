---
title: 'チュートリアル: 転移学習を利用した自動ビジュアル検査'
description: このチュートリアルでは、転移学習を利用し、ML.NET で TensorFlow ディープ ラーニング モデルをトレーニングする方法を説明します。具体的には、画像検出 API を利用し、コンクリートの表面の画像をひび割れあり/ひび割れなしに分類します。
author: luisquintanilla
ms.author: luquinta
ms.date: 02/09/2021
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 71d44ca3248d497b3f46d1d93c6505adcfc42021
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873303"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="b1746-103">チュートリアル: 転移学習と ML.NET Image Classification API を利用した自動ビジュアル検査</span><span class="sxs-lookup"><span data-stu-id="b1746-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="b1746-104">転移学習、事前トレーニング済みの TensorFlow モデル、ML.NET Image Classification API を利用してカスタム ディープ ラーニング モデルをトレーニングし、コンクリートの表面の画像をひび割れあり/ひび割れなしに分類する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1746-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="b1746-105">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1746-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b1746-106">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="b1746-106">Understand the problem</span></span>
> - <span data-ttu-id="b1746-107">ML.NET Image Classification API について</span><span class="sxs-lookup"><span data-stu-id="b1746-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="b1746-108">事前トレーニング済みモデルについて</span><span class="sxs-lookup"><span data-stu-id="b1746-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="b1746-109">転移学習を利用し、カスタム TensorFlow 画像分類モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="b1746-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="b1746-110">カスタム モデルによる画像の分類</span><span class="sxs-lookup"><span data-stu-id="b1746-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1746-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b1746-111">Prerequisites</span></span>

- <span data-ttu-id="b1746-112">".NET Core クロスプラットフォーム開発" ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 以降または Visual Studio 2017 バージョン 15.6 以降。</span><span class="sxs-lookup"><span data-stu-id="b1746-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="b1746-113">画像分類の転移学習の概要</span><span class="sxs-lookup"><span data-stu-id="b1746-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="b1746-114">このサンプルは、事前トレーニング済みディープ ラーニング TensorFlow モデルを利用して画像を分類する C# .NET Core コンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="b1746-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="b1746-115">このサンプルのコードは[サンプル ブラウザー](/samples/dotnet/machinelearning-samples/mlnet-image-classification-transfer-learning/)にあります。</span><span class="sxs-lookup"><span data-stu-id="b1746-115">The code for this sample can be found on the [samples browser](/samples/dotnet/machinelearning-samples/mlnet-image-classification-transfer-learning/).</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="b1746-116">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="b1746-116">Understand the problem</span></span>

<span data-ttu-id="b1746-117">画像分類はコンピューターのビジョンの問題です。</span><span class="sxs-lookup"><span data-stu-id="b1746-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="b1746-118">画像分類では、画像を入力として受け取り、指示されたクラスにそれを分類します。</span><span class="sxs-lookup"><span data-stu-id="b1746-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="b1746-119">画像分類はたとえば次のシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b1746-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="b1746-120">顔認識</span><span class="sxs-lookup"><span data-stu-id="b1746-120">Facial recognition</span></span>
- <span data-ttu-id="b1746-121">感情検出</span><span class="sxs-lookup"><span data-stu-id="b1746-121">Emotion detection</span></span>
- <span data-ttu-id="b1746-122">医療診断</span><span class="sxs-lookup"><span data-stu-id="b1746-122">Medical diagnosis</span></span>
- <span data-ttu-id="b1746-123">陸標検出</span><span class="sxs-lookup"><span data-stu-id="b1746-123">Landmark detection</span></span>

<span data-ttu-id="b1746-124">このチュートリアルでは、カスタム画像分類モデルをトレーニングし、橋床の映像を自動検査し、ひび割れしている構造物を特定します。</span><span class="sxs-lookup"><span data-stu-id="b1746-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="b1746-125">ML.NET Image Classification API</span><span class="sxs-lookup"><span data-stu-id="b1746-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="b1746-126">ML.NET からは、画像分類を実行するさまざまな方法が与えられます。</span><span class="sxs-lookup"><span data-stu-id="b1746-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="b1746-127">このチュートリアルでは、Image Classification API を使用する転移学習を応用します。</span><span class="sxs-lookup"><span data-stu-id="b1746-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="b1746-128">Image Classification API では [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET) を利用します。これは TensorFlow C++ API 用に C# バインディングを提供する低レベル ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="b1746-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="b1746-129">転移学習とは何か</span><span class="sxs-lookup"><span data-stu-id="b1746-129">What is transfer learning?</span></span>

<span data-ttu-id="b1746-130">転移学習では、ある問題を解決することで得られた知識が関連する別の問題に応用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="b1746-131">ディープ ラーニング モデルを最初からトレーニングするには、いくつかのパラメーター、大量のラベル付きトレーニング データ、膨大な量の計算リソース (数百時間の GPU) を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1746-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="b1746-132">事前トレーニング済みモデルと転移学習を使用すると、トレーニング プロセスをショートカットできます。</span><span class="sxs-lookup"><span data-stu-id="b1746-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="b1746-133">トレーニング プロセス</span><span class="sxs-lookup"><span data-stu-id="b1746-133">Training process</span></span>

<span data-ttu-id="b1746-134">Image Classification API のトレーニング プロセスは、事前トレーニング済み TensorFlow モデルを読み込むことから始まります。</span><span class="sxs-lookup"><span data-stu-id="b1746-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="b1746-135">トレーニング プロセスは次の 2 つのステップで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="b1746-136">ボトルネック フェーズ</span><span class="sxs-lookup"><span data-stu-id="b1746-136">Bottleneck phase</span></span>
2. <span data-ttu-id="b1746-137">トレーニング フェーズ</span><span class="sxs-lookup"><span data-stu-id="b1746-137">Training phase</span></span>

![トレーニング ステップ](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="b1746-139">ボトルネック フェーズ</span><span class="sxs-lookup"><span data-stu-id="b1746-139">Bottleneck phase</span></span>

<span data-ttu-id="b1746-140">ボトルネック フェーズの間、事前トレーニング済みモデルの固定レイヤーに対して、一連のトレーニング画像が読み込まれ、ピクセル値が入力として使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="b1746-141">固定レイヤーには、非公式にボトルネック レイヤーと呼ばれている最後から 2 番目のレイヤーまでに含まれる、ニューラル ネットワーク内のあらゆるレイヤーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b1746-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="b1746-142">このようなレイヤーは、その上でトレーニングが発生せず、操作がパススルーであるため、固定と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="b1746-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="b1746-143">モデルでさまざまなクラスを区別するのに役立つ低レベル パターンが計算されるのがこの固定レイヤーです。</span><span class="sxs-lookup"><span data-stu-id="b1746-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="b1746-144">レイヤーの数が多ければ多いほど、この手順は計算処理がそれだけ激しくなります。</span><span class="sxs-lookup"><span data-stu-id="b1746-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="b1746-145">幸いなことに、これは 1 回限りの計算であるため、結果をキャッシュし、後で異なるパラメーターを使用して実験するときに利用できます。</span><span class="sxs-lookup"><span data-stu-id="b1746-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="b1746-146">トレーニング フェーズ</span><span class="sxs-lookup"><span data-stu-id="b1746-146">Training phase</span></span>

<span data-ttu-id="b1746-147">ボトルネック フェーズからの出力値が計算されると、それが入力として利用され、モデルの最終的レイヤーが保持されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="b1746-148">このプロセスは繰り返され、モデル パラメーターで指定された回数だけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="b1746-149">実行のたびに、損失と精度が評価されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="b1746-150">次に、損失を最小限に抑え、精度を最大限に高めることを目的としてモデルを改善するための適切な調整が行われます。</span><span class="sxs-lookup"><span data-stu-id="b1746-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="b1746-151">トレーニングが完了すると、2 つのモデル形式が出力されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="b1746-152">そのうちの 1 つがモデルの `.pb` バージョンであり、もう 1 つがモデルの `.zip` ML.NET シリアル化バージョンです。</span><span class="sxs-lookup"><span data-stu-id="b1746-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="b1746-153">ML.NET でサポートされる環境で作業するとき、モデルの `.zip` バージョンを使用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="b1746-154">ただし、ML.NET がサポートされない環境では、`.pb` バージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1746-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="b1746-155">事前トレーニング済みモデルについて</span><span class="sxs-lookup"><span data-stu-id="b1746-155">Understand the pretrained model</span></span>

<span data-ttu-id="b1746-156">このチュートリアルで使用される事前トレーニング済みモデルは、Residual Network (ResNet) v2 モデルの 101 レイヤー型です。</span><span class="sxs-lookup"><span data-stu-id="b1746-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="b1746-157">元のモデルは、画像を 1,000 個のカテゴリに分類する目的でトレーニングされています。</span><span class="sxs-lookup"><span data-stu-id="b1746-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="b1746-158">このモデルでは、サイズ 224 x 224 の画像を入力として受け取り、トレーニングしたクラス別にクラス確率を出力します。</span><span class="sxs-lookup"><span data-stu-id="b1746-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="b1746-159">このモデルの一部は、2 つのクラス間で予測する目的でカスタム画像を利用して新しいモデルをトレーニングするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="b1746-160">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="b1746-160">Create console application</span></span>

<span data-ttu-id="b1746-161">転移学習と Image Classification API の概要を理解できたところで、アプリケーションを構築しましょう。</span><span class="sxs-lookup"><span data-stu-id="b1746-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="b1746-162">"DeepLearning_ImageClassification_Binary" という名前の **C# .NET Core コンソール アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="b1746-163">**Microsoft.ML** NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b1746-163">Install the **Microsoft.ML** NuGet Package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. <span data-ttu-id="b1746-164">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1746-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="b1746-165">[パッケージ ソース] として [nuget.org] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1746-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="b1746-166">**[参照]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="b1746-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="b1746-167">**[プレリリースを含める]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="b1746-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="b1746-168">**Microsoft.ML** を探します。</span><span class="sxs-lookup"><span data-stu-id="b1746-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="b1746-169">**[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="b1746-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="b1746-170">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1746-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="b1746-171">**Microsoft.ML.Vision**、**SciSharp.TensorFlow.Redist**、および **Microsoft.ML.ImageAnalytics** NuGet パッケージに対して、これらの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b1746-171">Repeat these steps for the **Microsoft.ML.Vision**, **SciSharp.TensorFlow.Redist**, and **Microsoft.ML.ImageAnalytics** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="b1746-172">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="b1746-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="b1746-173">このチュートリアルのデータセットの提供元: Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018:A concrete crack image dataset for machine learning applications" (2018).</span><span class="sxs-lookup"><span data-stu-id="b1746-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="b1746-174">Browse all Datasets.</span><span class="sxs-lookup"><span data-stu-id="b1746-174">Browse all Datasets.</span></span> <span data-ttu-id="b1746-175">Paper 48.</span><span class="sxs-lookup"><span data-stu-id="b1746-175">Paper 48.</span></span> <https://digitalcommons.usu.edu/all_datasets/48>

<span data-ttu-id="b1746-176">SDNET2018 は、ひび割れあり/ひび割れなしのコンクリート構造物 (橋床、壁、歩道) に関する注釈を含む画像データセットです。</span><span class="sxs-lookup"><span data-stu-id="b1746-176">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![SDNET2018 データセットの橋床のサンプル](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="b1746-178">データは 3 つのサブディレクトリで整理されています。</span><span class="sxs-lookup"><span data-stu-id="b1746-178">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="b1746-179">D には橋床の画像が含まれています</span><span class="sxs-lookup"><span data-stu-id="b1746-179">D contains bridge deck images</span></span>
- <span data-ttu-id="b1746-180">P には歩道の画像が含まれています</span><span class="sxs-lookup"><span data-stu-id="b1746-180">P contains pavement images</span></span>
- <span data-ttu-id="b1746-181">W には壁の画像が含まれています</span><span class="sxs-lookup"><span data-stu-id="b1746-181">W contains wall images</span></span>

<span data-ttu-id="b1746-182">これらのサブディレクトリにはそれぞれ、追加のサブディレクトリが 2 つ含まれ、プレフィックスが付けられています。</span><span class="sxs-lookup"><span data-stu-id="b1746-182">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="b1746-183">C はひび割れありの表面に使用されるプレフィックスです</span><span class="sxs-lookup"><span data-stu-id="b1746-183">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="b1746-184">U はひび割れなしの表面に使用されるプレフィックスです</span><span class="sxs-lookup"><span data-stu-id="b1746-184">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="b1746-185">このチュートリアルでは、橋床の画像のみ使用します。</span><span class="sxs-lookup"><span data-stu-id="b1746-185">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="b1746-186">[データセット](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/assets.zip)をダウンロードし、解凍します。</span><span class="sxs-lookup"><span data-stu-id="b1746-186">Download the [dataset](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="b1746-187">データ セット ファイルを保存するために、プロジェクトに "assets" という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-187">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="b1746-188">先ほど解凍したディレクトリから *assets* ディレクトリに *CD* サブディレクトリと *UD* サブディレクトリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="b1746-188">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="b1746-189">入力クラスと出力クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="b1746-189">Create input and output classes</span></span>

1. <span data-ttu-id="b1746-190">*Program.cs* ファイルを開き、ファイルの先頭にある既存の `using` ステートメントを次で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b1746-190">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L1-L7)]

1. <span data-ttu-id="b1746-191">*Program.cs* の `Program` クラスの下で `ImageData` という名前のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-191">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="b1746-192">このクラスは、最初に読み込んだデータを表わすために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-192">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L137-L142)]

    <span data-ttu-id="b1746-193">`ImageData` には次のプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b1746-193">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="b1746-194">`ImagePath` は、画像が保存されている完全修飾パスです。</span><span class="sxs-lookup"><span data-stu-id="b1746-194">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="b1746-195">`Label` は、画像が属するカテゴリです。</span><span class="sxs-lookup"><span data-stu-id="b1746-195">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="b1746-196">これが予測する値です。</span><span class="sxs-lookup"><span data-stu-id="b1746-196">This is the value to predict.</span></span>

1. <span data-ttu-id="b1746-197">入力データと出力データのクラスを作成する</span><span class="sxs-lookup"><span data-stu-id="b1746-197">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="b1746-198">`ImageData` クラスの下で、`ModelInput` という名前の新しいクラスに入力データのスキーマを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1746-198">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L144-L153)]

        <span data-ttu-id="b1746-199">`ModelInput` には次のプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b1746-199">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="b1746-200">`Image` は画像の `byte[]` 表現です。</span><span class="sxs-lookup"><span data-stu-id="b1746-200">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="b1746-201">モデルでは、トレーニングのために画像データがこの種類になることが求められます。</span><span class="sxs-lookup"><span data-stu-id="b1746-201">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="b1746-202">`LabelAsKey` は `Label` の数値表現です。</span><span class="sxs-lookup"><span data-stu-id="b1746-202">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="b1746-203">`ImagePath` は、画像が保存されている完全修飾パスです。</span><span class="sxs-lookup"><span data-stu-id="b1746-203">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="b1746-204">`Label` は、画像が属するカテゴリです。</span><span class="sxs-lookup"><span data-stu-id="b1746-204">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="b1746-205">これが予測する値です。</span><span class="sxs-lookup"><span data-stu-id="b1746-205">This is the value to predict.</span></span>

        <span data-ttu-id="b1746-206">`Image` と `LabelAsKey` のみ、モデルのトレーニングと予測に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-206">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="b1746-207">`ImagePath` プロパティと `Label` プロパティは、元の画像ファイルの名前やカテゴリにアクセスするときに便利なため、維持されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-207">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="b1746-208">次に、`ModelInput` クラスの下で、`ModelOutput` という名前の新しいクラスに出力データのスキーマを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1746-208">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L155-L162)]

        <span data-ttu-id="b1746-209">`ModelOutput` には次のプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b1746-209">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="b1746-210">`ImagePath` は、画像が保存されている完全修飾パスです。</span><span class="sxs-lookup"><span data-stu-id="b1746-210">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="b1746-211">`Label` は、画像が属する元のカテゴリです。</span><span class="sxs-lookup"><span data-stu-id="b1746-211">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="b1746-212">これが予測する値です。</span><span class="sxs-lookup"><span data-stu-id="b1746-212">This is the value to predict.</span></span>
        - <span data-ttu-id="b1746-213">`PredictedLabel` はモデルで予測された値です。</span><span class="sxs-lookup"><span data-stu-id="b1746-213">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="b1746-214">`ModelInput` と同様に、予測には `PredictedLabel` のみが必要になります。モデルによる予測が含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="b1746-214">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="b1746-215">`ImagePath` プロパティと `Label` プロパティは、元の画像ファイルの名前やカテゴリにアクセスするときに便利なため、保持されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-215">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="b1746-216">ワークスペース ディレクトリを作成する</span><span class="sxs-lookup"><span data-stu-id="b1746-216">Create workspace directory</span></span>

<span data-ttu-id="b1746-217">トレーニング データと検証データが頻繁に変更されない場合は、今後の実行のために、計算されたボトルネック値をキャッシュすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b1746-217">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="b1746-218">プロジェクトで *workspace* という名前の新しいディレクトリを作成し、計算されたボトルネック値とモデルの `.pb` バージョンを格納します。</span><span class="sxs-lookup"><span data-stu-id="b1746-218">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="b1746-219">パスを定義し、変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="b1746-219">Define paths and initialize variables</span></span>

1. <span data-ttu-id="b1746-220">`Main` メソッド内で、アセットの場所、計算されたボトルネック値、モデルの `.pb` バージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1746-220">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L15-L17)]

1. <span data-ttu-id="b1746-221">[MLContext](xref:Microsoft.ML.MLContext) の新しいインスタンスを使用して `mlContext` 変数を初期化します。</span><span class="sxs-lookup"><span data-stu-id="b1746-221">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L19)]

    <span data-ttu-id="b1746-222">[MLContext](xref:Microsoft.ML.MLContext) クラスは、すべての ML.NET 操作の開始点で、mlContext を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-222">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="b1746-223">これは Entity Framework における `DbContext` と概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="b1746-223">It's similar, conceptually, to `DbContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="b1746-224">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="b1746-224">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="b1746-225">データ読み込みユーティリティ メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="b1746-225">Create data loading utility method</span></span>

<span data-ttu-id="b1746-226">イメージは 2 つのサブディレクトリに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-226">The images are stored in two subdirectories.</span></span> <span data-ttu-id="b1746-227">データを読み込む前に、`ImageData` オブジェクトの一覧に書式設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1746-227">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="b1746-228">そのためには、`LoadImagesFromDirectory` メソッドを `Main` メソッドの下で作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-228">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="b1746-229">`LoadImagesFromDirectory` 内で次のコードを追加し、サブディレクトリからすべてのファイル パスを取得します。</span><span class="sxs-lookup"><span data-stu-id="b1746-229">Inside the `LoadImagesFromDirectory`, add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L104-L105)]

1. <span data-ttu-id="b1746-230">次に、`foreach` ステートメントを利用して各ファイルを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="b1746-230">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="b1746-231">`foreach` ステートメント内で、ファイルの拡張子がサポートされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b1746-231">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="b1746-232">Image Classification API では、JPEG 形式と PNG 形式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b1746-232">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L109-L111)]

1. <span data-ttu-id="b1746-233">次に、ファイルのラベルを取得します。</span><span class="sxs-lookup"><span data-stu-id="b1746-233">Then, get the label for the file.</span></span> <span data-ttu-id="b1746-234">`useFolderNameAsLabel` パラメーターが `true` に設定されている場合、ファイルが保存されている親ディレクトリがラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-234">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="b1746-235">それ以外の場合、ラベルは、ファイルのプレフィックスか名前自体にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1746-235">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L112-L126)]

1. <span data-ttu-id="b1746-236">最後に、`ModelInput` の新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-236">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="b1746-237">データを準備する</span><span class="sxs-lookup"><span data-stu-id="b1746-237">Prepare the data</span></span>

1. <span data-ttu-id="b1746-238">`Main` メソッドに戻り、`LoadImagesFromDirectory` ユーティリティを使用し、トレーニングに使用される画像の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="b1746-238">Back in the `Main` method, use the `LoadImagesFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L22)]

1. <span data-ttu-id="b1746-239">次に、[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) メソッドを利用して [`IDataView`](xref:Microsoft.ML.IDataView) に画像を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b1746-239">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L24)]

1. <span data-ttu-id="b1746-240">データはディレクトリから読み取られた順序で読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="b1746-240">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="b1746-241">データのバランスを維持するために、[`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows%2A) メソッドを利用してシャッフルします。</span><span class="sxs-lookup"><span data-stu-id="b1746-241">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows%2A) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L26)]

1. <span data-ttu-id="b1746-242">機械学習モデルでは、数値形式で入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1746-242">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="b1746-243">そのため、トレーニングの前にデータでいくつかの処理を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1746-243">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="b1746-244">[`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) 変換と `LoadRawImageBytes` 変換から構成される [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-244">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="b1746-245">`MapValueToKey` 変換では、`Label` 列のカテゴリ値を受け取り、それを数値 `KeyType` に変換し、`LabelAsKey` という名前の新しい列に保存します。</span><span class="sxs-lookup"><span data-stu-id="b1746-245">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="b1746-246">`LoadImages` では、`imageFolder` パラメーターと共に `ImagePath` から値を取得し、トレーニングのために画像を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b1746-246">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L28-L34)]

1. <span data-ttu-id="b1746-247">データを `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) に適用する [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A) メソッドを使用し、事前処理済みのデータが含まれる [`IDataView`](xref:Microsoft.ML.IDataView) メソッドを返す [`Transform`](xref:Microsoft.ML.Data.TransformerChain%601.Transform%2A) メソッドを続けます。</span><span class="sxs-lookup"><span data-stu-id="b1746-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain%601.Transform%2A) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L36-L38)]

1. <span data-ttu-id="b1746-248">モデルをトレーニングするには、トレーニング データセットと検証データセットを用意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="b1746-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="b1746-249">モデルはトレーニング セットでトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="b1746-249">The model is trained on the training set.</span></span> <span data-ttu-id="b1746-250">初見のデータの予測精度は、検証セットに対するパフォーマンスで計測されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="b1746-251">そのパフォーマンスの結果に基づき、改善努力の中でモデルが学習したものに調整が加えられます。</span><span class="sxs-lookup"><span data-stu-id="b1746-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="b1746-252">検証セットは、元のデータセットを分割することで取得するか、この目的のために既に用意されていた別の情報源から取得します。</span><span class="sxs-lookup"><span data-stu-id="b1746-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="b1746-253">今回、事前処理済みのデータセットがトレーニング セット、検証セット、テスト セットに分割されています。</span><span class="sxs-lookup"><span data-stu-id="b1746-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L40-L41)]

    <span data-ttu-id="b1746-254">上のコード サンプルでは、2 回分割されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-254">The code sample above performs two splits.</span></span> <span data-ttu-id="b1746-255">まず、事前処理済みのデータが分割され、70% がトレーニングに使用され、残りの 30% が検証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="b1746-256">次に、30% の検証セットがさらに検証セットとテスト セットに分割され、90% が検証に使用され、10% がテストに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="b1746-257">このようなデータ分割の目的は試験を受けるようなものです。</span><span class="sxs-lookup"><span data-stu-id="b1746-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="b1746-258">試験勉強するとき、ノート、教科書、参考書で復習し、試験に出る概念をつかみます。</span><span class="sxs-lookup"><span data-stu-id="b1746-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="b1746-259">トレーニング セットがこれに相当します。</span><span class="sxs-lookup"><span data-stu-id="b1746-259">This is what the train set is for.</span></span> <span data-ttu-id="b1746-260">次に、模擬試験を受け、自分の知識を確認します。</span><span class="sxs-lookup"><span data-stu-id="b1746-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="b1746-261">ここで役立つのが検証セットです。</span><span class="sxs-lookup"><span data-stu-id="b1746-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="b1746-262">実際に試験を受ける前に概念をしっかり理解しているかを確認したくなることでしょう。</span><span class="sxs-lookup"><span data-stu-id="b1746-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="b1746-263">模擬試験の結果に基づき、間違った箇所や良く理解していなかった箇所をメモし、本番の試験に向けて復習する中、変えるべきところを組み込みます。</span><span class="sxs-lookup"><span data-stu-id="b1746-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="b1746-264">最後に、試験を受けます。</span><span class="sxs-lookup"><span data-stu-id="b1746-264">Finally, you take the exam.</span></span> <span data-ttu-id="b1746-265">テスト セットがこれに相当します。</span><span class="sxs-lookup"><span data-stu-id="b1746-265">This is what the test set is used for.</span></span> <span data-ttu-id="b1746-266">試験に出ている問題は今まで見たことがありません。トレーニングと検証から学習したことを活用し、手元の課題に自分の知識を応用します。</span><span class="sxs-lookup"><span data-stu-id="b1746-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="b1746-267">トレーニング データ、検証データ、テスト データそれぞれの値をパーティションに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b1746-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L43-L45)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="b1746-268">トレーニング パイプラインを定義する</span><span class="sxs-lookup"><span data-stu-id="b1746-268">Define the training pipeline</span></span>

<span data-ttu-id="b1746-269">モデル トレーニングはいくつかのステップから構成されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="b1746-270">まず、Image Classification API を利用し、モデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="b1746-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="b1746-271">次に、`PredictedLabel` 列のエンコード済みラベルが `MapKeyToValue` 変換により元のカテゴリ値に戻されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="b1746-272">`ImageClassificationTrainer` の必須パラメーターと省略可能なパラメーターのセットを格納するために、新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-272">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L47-L57)]

    <span data-ttu-id="b1746-273">`ImageClassificationTrainer` では、いくつかの省略可能なパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b1746-273">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="b1746-274">`FeatureColumnName` はモデルの入力として使用される列です。</span><span class="sxs-lookup"><span data-stu-id="b1746-274">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="b1746-275">`LabelColumnName` は予測する値の列です。</span><span class="sxs-lookup"><span data-stu-id="b1746-275">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="b1746-276">`ValidationSet` は検証データが含まれる [`IDataView`](xref:Microsoft.ML.IDataView) です。</span><span class="sxs-lookup"><span data-stu-id="b1746-276">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="b1746-277">`Arch` では、使用する事前トレーニング済みモデル アーキテクチャが定義されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-277">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="b1746-278">このチュートリアルでは、ResNetv2 モデルの 101 レイヤー型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-278">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="b1746-279">`MetricsCallback` では、トレーニング中に進捗状況を追跡記録する関数がバインドされます。</span><span class="sxs-lookup"><span data-stu-id="b1746-279">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="b1746-280">`TestOnTrainSet` からは、検証セットがないとき、トレーニング セットに対してパフォーマンスを検証するようにモデルに指示が出ます。</span><span class="sxs-lookup"><span data-stu-id="b1746-280">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="b1746-281">`ReuseTrainSetBottleneckCachedValues` からは、後続の実行でボトルネック フェーズからキャッシュされた値を使用するかどうかがモデルに伝えられます。</span><span class="sxs-lookup"><span data-stu-id="b1746-281">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="b1746-282">ボトルネック フェーズは、初回実行時の計算処理が激しいワンタイム パススルー計算です。</span><span class="sxs-lookup"><span data-stu-id="b1746-282">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="b1746-283">トレーニング データが変わらないとき、エポック数やバッチ サイズを変えて実験する場合、キャッシュした値を利用すると、モデルのトレーニングに必要な時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-283">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="b1746-284">`ReuseValidationSetBottleneckCachedValues` は `ReuseTrainSetBottleneckCachedValues` に似ていますが、これは検証データセット用になります。</span><span class="sxs-lookup"><span data-stu-id="b1746-284">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="b1746-285">`WorkspacePath` では、計算されたボトルネック値と `.pb` バージョンのモデルを格納するディレクトリを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1746-285">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="b1746-286">`mapLabelEstimator` と `ImageClassificationTrainer` の両方から構成される [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) トレーニング パイプラインを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1746-286">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L59-L60)]

1. <span data-ttu-id="b1746-287">[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A) メソッドを利用してモデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="b1746-287">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="b1746-288">モデルを使用する</span><span class="sxs-lookup"><span data-stu-id="b1746-288">Use the model</span></span>

<span data-ttu-id="b1746-289">モデルをトレーニングできたところで、モデルを利用して画像を分類しましょう。</span><span class="sxs-lookup"><span data-stu-id="b1746-289">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="b1746-290">`Main` メソッドの下で、コンソールに予測情報を表示する、`OutputPrediction` という名前の新しいユーティリティ メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-290">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="b1746-291">1 枚の画像を分類する</span><span class="sxs-lookup"><span data-stu-id="b1746-291">Classify a single image</span></span>

1. <span data-ttu-id="b1746-292">`Main` メソッドの下に `ClassifySingleImage` という名前の新しいメソッドを追加します。このメソッドは画像を 1 回予測し、出力します。</span><span class="sxs-lookup"><span data-stu-id="b1746-292">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="b1746-293">`ClassifySingleImage` メソッド内に [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-293">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="b1746-294">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) は、データの 1 つのインスタンスを渡してから、その予測を実行できる便利な API です。</span><span class="sxs-lookup"><span data-stu-id="b1746-294">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L73)]

1. <span data-ttu-id="b1746-295">1 つの `ModelInput` インスタンスにアクセスするには、[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) メソッドを利用して `data` [`IDataView`](xref:Microsoft.ML.IDataView) を [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) に変換し、最初の観察を取得します。</span><span class="sxs-lookup"><span data-stu-id="b1746-295">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L75)]

1. <span data-ttu-id="b1746-296">[`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) メソッドを使用し、画像を分類します。</span><span class="sxs-lookup"><span data-stu-id="b1746-296">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L77)]

1. <span data-ttu-id="b1746-297">`OutputPrediction` メソッドでコンソールに予測を出力します。</span><span class="sxs-lookup"><span data-stu-id="b1746-297">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L79-L80)]

1. <span data-ttu-id="b1746-298">`Main` メソッド内で、画像のテスト セットを利用して `ClassifySingleImage` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b1746-298">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="b1746-299">複数の画像を分類する</span><span class="sxs-lookup"><span data-stu-id="b1746-299">Classify multiple images</span></span>

1. <span data-ttu-id="b1746-300">`ClassifySingleImage` メソッドの下に `ClassifyImages` という名前の新しいメソッドを追加します。このメソッドは画像を複数回予測し、出力します。</span><span class="sxs-lookup"><span data-stu-id="b1746-300">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="b1746-301">[`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドを利用し、予測を含む [`IDataView`](xref:Microsoft.ML.IDataView) を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1746-301">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) method.</span></span> <span data-ttu-id="b1746-302">`ClassifyImages` メソッド内に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b1746-302">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L85)]

1. <span data-ttu-id="b1746-303">予測を反復処理するには、[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) メソッドを利用して `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) を [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) に変換し、最初の 10 件の観察を取得します。</span><span class="sxs-lookup"><span data-stu-id="b1746-303">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L87)]

1. <span data-ttu-id="b1746-304">予測を反復処理し、元のラベルと予測後のラベルを出力します。</span><span class="sxs-lookup"><span data-stu-id="b1746-304">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L89-L93)]

1. <span data-ttu-id="b1746-305">最後に、`Main` メソッド内で、画像のテスト セットを利用して `ClassifyImages` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b1746-305">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="b1746-306">アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="b1746-306">Run the application</span></span>

<span data-ttu-id="b1746-307">コンソール アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b1746-307">Run your console app.</span></span> <span data-ttu-id="b1746-308">出力は下の出力のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="b1746-308">The output should be similar to that below.</span></span> <span data-ttu-id="b1746-309">警告メッセージまたは処理中のメッセージが表示される場合がありますが、わかりやすくするため、これらのメッセージは結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="b1746-309">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="b1746-310">簡潔にするため、出力は要約されています。</span><span class="sxs-lookup"><span data-stu-id="b1746-310">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="b1746-311">**ボトルネック フェーズ**</span><span class="sxs-lookup"><span data-stu-id="b1746-311">**Bottleneck phase**</span></span>

<span data-ttu-id="b1746-312">画像は `byte[]` として読み込まれており、表示する画像名がないため、画像名には値が出力されません。</span><span class="sxs-lookup"><span data-stu-id="b1746-312">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="b1746-313">**トレーニング フェーズ**</span><span class="sxs-lookup"><span data-stu-id="b1746-313">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="b1746-314">**画像分類の出力**</span><span class="sxs-lookup"><span data-stu-id="b1746-314">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="b1746-315">*7001-220.jpg* 画像の検査後、実際のところ、ひび割れがないことがわかりました。</span><span class="sxs-lookup"><span data-stu-id="b1746-315">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![予測に使用された SDNET2018 データセット画像](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="b1746-317">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="b1746-317">Congratulations!</span></span> <span data-ttu-id="b1746-318">これで画像を分類するディープ ラーニング モデルが正しく作成されました。</span><span class="sxs-lookup"><span data-stu-id="b1746-318">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="b1746-319">画像を改善する</span><span class="sxs-lookup"><span data-stu-id="b1746-319">Improve the model</span></span>

<span data-ttu-id="b1746-320">モデルの結果に不満が残る場合、次の手法を試し、パフォーマンスを向上してみることができます。</span><span class="sxs-lookup"><span data-stu-id="b1746-320">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="b1746-321">**データを増やす**:モデルが学習するサンプルの数が多ければ多いほど、パフォーマンスがそれだけ上がります。</span><span class="sxs-lookup"><span data-stu-id="b1746-321">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="b1746-322">[SDNET2018 データセット](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional)を全部ダウンロードし、それを利用してトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="b1746-322">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="b1746-323">**データを拡張する**:データに変化を与える一般的な手法は、画像にさまざまな変換 (回転、裏返し、移動、トリミング) を適用してデータを強化することです。</span><span class="sxs-lookup"><span data-stu-id="b1746-323">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="b1746-324">これでモデルが学習するサンプルに変化が与えられます。</span><span class="sxs-lookup"><span data-stu-id="b1746-324">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="b1746-325">**トレーニング時間を増やす**:トレーニング時間が長ければ長いほど、モデルがそれだけ微調整されます。</span><span class="sxs-lookup"><span data-stu-id="b1746-325">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="b1746-326">エポックの数を増やすことで、モデルのパフォーマンスが上がることもあります。</span><span class="sxs-lookup"><span data-stu-id="b1746-326">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="b1746-327">**パイパーパラメーターで実験する**:このチュートリアルで使用されているパラメーターに加え、他のパラメーターを微調整するとパフォーマンスが上がることがあります。</span><span class="sxs-lookup"><span data-stu-id="b1746-327">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="b1746-328">各エポック後のモデル更新の規模を決定する学習率を変更すると、パフォーマンスが上がることがあります。</span><span class="sxs-lookup"><span data-stu-id="b1746-328">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="b1746-329">**別のモデル アーキテクチャを使用する**:目で見たときのデータによっては、その特徴を最も効果的に学習できるモデルが異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="b1746-329">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="b1746-330">モデルのパフォーマンスに不満が残る場合、アーキテクチャの変更をお試しください。</span><span class="sxs-lookup"><span data-stu-id="b1746-330">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b1746-331">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="b1746-331">Additional Resources</span></span>

- <span data-ttu-id="b1746-332">[ディープ ラーニングと機械学習](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning)</span><span class="sxs-lookup"><span data-stu-id="b1746-332">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1746-333">次の手順</span><span class="sxs-lookup"><span data-stu-id="b1746-333">Next steps</span></span>

<span data-ttu-id="b1746-334">このチュートリアルでは、転移学習、事前トレーニング済みの画像分類 TensorFlow モデル、ML.NET Image Classification API を利用してカスタム ディープ ラーニング モデルを構築し、コンクリートの表面の画像をひび割れあり/ひび割れなしに分類する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="b1746-334">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="b1746-335">さらに詳しく学習するには、次のチュートリアルに進んでください。</span><span class="sxs-lookup"><span data-stu-id="b1746-335">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b1746-336">物体検出</span><span class="sxs-lookup"><span data-stu-id="b1746-336">Object Detection</span></span>](object-detection-onnx.md)
