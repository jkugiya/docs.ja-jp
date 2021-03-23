---
title: 'チュートリアル: TensorFlow からの ML.NET 画像分類モデル'
description: 既存の TensorFlow モデルから新しい ML.NET 画像分類モデルに知識を転移する方法について説明します。 TensorFlow モデルは、画像を 1,000 個のカテゴリに分類するためにトレーニングされました。 ML.NET モデルでは、転移学習を利用して、さらに少ない数のカテゴリに画像を分類します。
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: b3e5617979d1635248f87db6008d3e234bb3ffc5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104877034"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="d3a08-105">チュートリアル: 事前トレーニング済みの TensorFlow モデルから ML.NET 画像分類モデルを生成する</span><span class="sxs-lookup"><span data-stu-id="d3a08-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="d3a08-106">既存の TensorFlow モデルから新しい ML.NET 画像分類モデルに知識を転移する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="d3a08-107">TensorFlow モデルは、画像を 1,000 個のカテゴリに分類するためにトレーニングされました。</span><span class="sxs-lookup"><span data-stu-id="d3a08-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="d3a08-108">ML.NET モデルでは、パイプラインで TensorFlow モデルの一部を利用し、モデルをトレーニングし、画像を 3 つのカテゴリに分類しています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="d3a08-109">[画像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition)モデルを最初からトレーニングするには、数百万のパラメーター、大量のラベル付きトレーニング データ、膨大な量の計算リソース (数百時間の GPU) を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="d3a08-110">最初からカスタム モデルをトレーニングするほど効果的ではありませんが、転移学習を使用すると、何千もの画像と何百万ものラベル付き画像を使用し、カスタマイズされたモデルを短時間 (GPU が搭載されていないマシンで 1 時間以内) で構築できます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="d3a08-111">このチュートリアルでは、1 ダースのトレーニング画像のみを使用して、そのプロセスをさらにスケールダウンします。</span><span class="sxs-lookup"><span data-stu-id="d3a08-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="d3a08-112">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="d3a08-113">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="d3a08-113">Understand the problem</span></span>
> * <span data-ttu-id="d3a08-114">事前トレーニング済みの TensorFlow モデルを ML.NET パイプラインに組み込む</span><span class="sxs-lookup"><span data-stu-id="d3a08-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="d3a08-115">ML.NET モデルのトレーニングと評価</span><span class="sxs-lookup"><span data-stu-id="d3a08-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="d3a08-116">テスト画像を分類する</span><span class="sxs-lookup"><span data-stu-id="d3a08-116">Classify a test image</span></span>

<span data-ttu-id="d3a08-117">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="d3a08-118">既定では、このチュートリアルの .NET プロジェクトの構成は .NET Core 2.2 を対象としています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="d3a08-119">転移学習とは何か</span><span class="sxs-lookup"><span data-stu-id="d3a08-119">What is transfer learning?</span></span>

<span data-ttu-id="d3a08-120">転移学習は、1 つの問題を解決し、それを別の関連する問題に適用するときに得た知識を使用するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="d3a08-121">このチュートリアルでは、TensorFlow モデル (画像を 1,000 個のカテゴリに分類するようにトレーニング済み) の一部を、画像を 3 つのカテゴリに分類する ML.NET モデルで使用します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3a08-122">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d3a08-122">Prerequisites</span></span>

* <span data-ttu-id="d3a08-123">".NET Core クロスプラットフォーム開発" ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 以降または Visual Studio 2017 バージョン 15.6 以降。</span><span class="sxs-lookup"><span data-stu-id="d3a08-123">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="d3a08-124">チュートリアル資産ディレクトリの .ZIP ファイル</span><span class="sxs-lookup"><span data-stu-id="d3a08-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="d3a08-125">InceptionV1 機械学習モデル</span><span class="sxs-lookup"><span data-stu-id="d3a08-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="d3a08-126">適切な機械学習タスクを選択する</span><span class="sxs-lookup"><span data-stu-id="d3a08-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="d3a08-127">ディープ ラーニング</span><span class="sxs-lookup"><span data-stu-id="d3a08-127">Deep learning</span></span>

<span data-ttu-id="d3a08-128">[ディープ ラーニング](https://en.wikipedia.org/wiki/Deep_learning)は、Computer Vision や音声認識などの分野に革命を起こしている Machine Learning のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="d3a08-129">ディープ ラーニング モデルは、複数の学習レイヤーを含む多数の[ラベル付きデータ](https://en.wikipedia.org/wiki/Labeled_data)と[ニューラル ネットワーク](https://en.wikipedia.org/wiki/Artificial_neural_network)を使用してトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="d3a08-130">ディープ ラーニング:</span><span class="sxs-lookup"><span data-stu-id="d3a08-130">Deep learning:</span></span>

* <span data-ttu-id="d3a08-131">Computer Vision などの一部のタスクでより効果的に機能します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="d3a08-132">大量のトレーニング データが必要です。</span><span class="sxs-lookup"><span data-stu-id="d3a08-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="d3a08-133">画像分類は、画像を次のようなカテゴリに自動的に分類することができる一般的な機械学習タスクです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="d3a08-134">画像から人の顔を検出するかどうか。</span><span class="sxs-lookup"><span data-stu-id="d3a08-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="d3a08-135">猫と犬の検出。</span><span class="sxs-lookup"><span data-stu-id="d3a08-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="d3a08-136">または、次の画像のように、画像が食品、おもちゃ、または電化製品のいずれであるかを判断する場合。</span><span class="sxs-lookup"><span data-stu-id="d3a08-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="d3a08-137">![ピザの画像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![テディ ベアの画像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![トースターの画像](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="d3a08-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="d3a08-138">上の画像は Wikimedia Commons に属し、次のように属性が付けられています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="d3a08-139">"220px-Pepperoni_pizza.jpg" パブリック ドメイン、 <https://commons.wikimedia.org/w/index.php?curid=79505>、</span><span class="sxs-lookup"><span data-stu-id="d3a08-139">"220px-Pepperoni_pizza.jpg" Public Domain, <https://commons.wikimedia.org/w/index.php?curid=79505>,</span></span>
> * <span data-ttu-id="d3a08-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - 自己撮影、CC BY-SA 2.0、 <https://commons.wikimedia.org/w/index.php?curid=48166>。</span><span class="sxs-lookup"><span data-stu-id="d3a08-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, <https://commons.wikimedia.org/w/index.php?curid=48166>.</span></span>
> * <span data-ttu-id="d3a08-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - 自分の作品、CC BY-SA 3.0、 <https://commons.wikimedia.org/w/index.php?curid=27403></span><span class="sxs-lookup"><span data-stu-id="d3a08-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, <https://commons.wikimedia.org/w/index.php?curid=27403></span></span>

<span data-ttu-id="d3a08-142">`Inception model` は、画像を 1,000 個のカテゴリに分類するようにトレーニングされていますが、このチュートリアルでは、画像をより小さなカテゴリ セットにのみ分類する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="d3a08-143">`transfer learning` の `transfer` 部分を入力します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="d3a08-144">`Inception model` の画像を認識および分類する能力をカスタム画像分類器の新しい限られたカテゴリに転移ことができます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="d3a08-145">食品</span><span class="sxs-lookup"><span data-stu-id="d3a08-145">Food</span></span>
* <span data-ttu-id="d3a08-146">おもちゃ</span><span class="sxs-lookup"><span data-stu-id="d3a08-146">Toy</span></span>
* <span data-ttu-id="d3a08-147">アプライアンス</span><span class="sxs-lookup"><span data-stu-id="d3a08-147">Appliance</span></span>

<span data-ttu-id="d3a08-148">このチュートリアルでは、TensorFlow の [Inception モデル](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) ディープ ラーニング モデルを使用します。これは、`ImageNet` データセットに対してトレーニングされた、よく使われる画像認識モデルです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="d3a08-149">TensorFlow モデルでは、画像全体を "傘"、"ジャージー"、"食器洗い機" などの 1,000 個のクラスに分類します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="d3a08-150">`Inception model` は何千種類もの画像に対して事前にトレーニングされているため、画像の識別に必要な[画像の特徴](https://en.wikipedia.org/wiki/Feature_(computer_vision))が内部に含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="d3a08-151">モデルでこれらの内部画像機能を利用して、はるかに少数のクラスで新しいモデルをトレーニングすることができます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="d3a08-152">次の図に示すように、.NET Core または .NET Framework アプリケーションに ML.NET NuGet パッケージへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="d3a08-153">内部的には、既存のトレーニング済み `TensorFlow` モデル ファイルを読み込むコードを作成できるネイティブ `TensorFlow` ライブラリが ML.NET には含まれ、参照されています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![TensorFlow 変換 ML.NET Arch 図](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="d3a08-155">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="d3a08-155">Multiclass classification</span></span>

<span data-ttu-id="d3a08-156">TensorFlow Inception モデルを使用して、従来の機械学習アルゴリズムの入力に適した特徴を抽出したら、ML.NET の[多クラス分類器](../resources/tasks.md#multiclass-classification)を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="d3a08-157">この場合に使用される特定のトレーナーは、[多項ロジスティック回帰アルゴリズム](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)です。</span><span class="sxs-lookup"><span data-stu-id="d3a08-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="d3a08-158">このトレーナーに実装されているアルゴリズムは、多数の特徴を持つ問題 (画像データに対して機能するディープ ラーニング モデルのケース) に適しています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="d3a08-159">データ</span><span class="sxs-lookup"><span data-stu-id="d3a08-159">Data</span></span>

<span data-ttu-id="d3a08-160">データ ソースは 2 つあります。`.tsv` ファイルと画像ファイルです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="d3a08-161">`tags.tsv` ファイルには 2 つの列があります。最初の列は `ImagePath` と定義され、2 番目の列は画像に対応する `Label` です。</span><span class="sxs-lookup"><span data-stu-id="d3a08-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="d3a08-162">次のファイル例にはヘッダー行がなく、次のような内容です。</span><span class="sxs-lookup"><span data-stu-id="d3a08-162">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="d3a08-163">トレーニングとテストの画像は、zip ファイルでダウンロードする資産フォルダー内にあります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="d3a08-164">これらの画像は Wikimedia Commons に属します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="d3a08-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208)、無料メディア リポジトリ。*</span><span class="sxs-lookup"><span data-stu-id="d3a08-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="d3a08-166">2018 年 10 月 17 日 10:48 に以下から取得: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
> <https://commons.wikimedia.org/wiki/Teddy_bear></span><span class="sxs-lookup"><span data-stu-id="d3a08-166">Retrieved 10:48, October 17, 2018 from: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
<https://commons.wikimedia.org/wiki/Teddy_bear></span></span>

## <a name="setup"></a><span data-ttu-id="d3a08-167">セットアップ</span><span class="sxs-lookup"><span data-stu-id="d3a08-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="d3a08-168">プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="d3a08-168">Create a project</span></span>

1. <span data-ttu-id="d3a08-169">"TransferLearningTF" という **.NET Core Console アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="d3a08-170">**Microsoft.ML NuGet パッケージ** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="d3a08-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    * <span data-ttu-id="d3a08-171">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="d3a08-172">[パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択し、"**Microsoft.ML**" を検索します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="d3a08-173">**[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-173">Select the **Install** button.</span></span>
    * <span data-ttu-id="d3a08-174">**[変更のプレビュー]** ダイアログで **[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="d3a08-175">一覧表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスへの同意]** ダイアログで **[同意する]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="d3a08-176">**Microsoft.ML.ImageAnalytics**、**SciSharp.TensorFlow.Redist**、および **Microsoft.ML.TensorFlow** に対して、これらの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-176">Repeat these steps for **Microsoft.ML.ImageAnalytics**, **SciSharp.TensorFlow.Redist** and **Microsoft.ML.TensorFlow**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="d3a08-177">資産をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="d3a08-177">Download assets</span></span>

1. <span data-ttu-id="d3a08-178">[プロジェクト資産ディレクトリの zip ファイル](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)をダウンロードし、展開します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="d3a08-179">`assets` ディレクトリを *TransferLearningTF* プロジェクト ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d3a08-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="d3a08-180">このディレクトリとそのサブディレクトリには、このチュートリアルに必要なデータ ファイルとサポート ファイル (次の手順でダウンロードして追加する Inception モデルを除く) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="d3a08-181">[Inception モデル](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)をダウンロードして展開します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="d3a08-182">`inception5h` ディレクトリの内容をコピーし、*TransferLearningTF* プロジェクトの `assets/inception` ディレクトリに展開します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="d3a08-183">次の画像に示すように、このディレクトリには、このチュートリアルに必要なモデルと追加のサポート ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Inception ディレクトリの内容](./media/image-classification/inception-files.png)

1. <span data-ttu-id="d3a08-185">ソリューション エクスプローラーで、資産ディレクトリとサブディレクトリ内の各ファイルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="d3a08-186">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="d3a08-187">クラスを作成してパスを定義する</span><span class="sxs-lookup"><span data-stu-id="d3a08-187">Create classes and define paths</span></span>

1. <span data-ttu-id="d3a08-188">次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/image-classification/csharp/Program.cs#AddUsings)]

1. <span data-ttu-id="d3a08-189">`Main` メソッドのすぐ上にある行に次のコードを追加して、資産のパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](./snippets/image-classification/csharp/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="d3a08-190">入力データと予測のためにクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](./snippets/image-classification/csharp/Program.cs#DeclareImageData)]

    <span data-ttu-id="d3a08-191">`ImageData` は、入力画像データ クラスであり、次の <xref:System.String> フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="d3a08-192">`ImagePath` には、画像ファイル名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="d3a08-193">`Label` には、画像ラベルの値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="d3a08-194">`ImagePrediction` のプロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](./snippets/image-classification/csharp/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="d3a08-195">`ImagePrediction` は、画像予測クラスであり、次のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="d3a08-196">`Score` には、指定した画像分類の信頼度が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="d3a08-197">`PredictedLabelValue` には、予測された画像分類ラベルの値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3a08-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="d3a08-198">`ImagePrediction` は、モデルがトレーニングされた後に、予測に使用されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="d3a08-199">これには画像パスの `string` (`ImagePath`) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="d3a08-200">`Label` はモデルの再利用とトレーニングに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="d3a08-201">`PredictedLabelValue` は予測と評価の際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="d3a08-202">評価では、トレーニング データを含む入力、予測された値、およびモデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="d3a08-203">Main で変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="d3a08-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="d3a08-204">新しいインスタンスの `MLContext` を使用して `mlContext` 変数を初期化します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="d3a08-205">`Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](./snippets/image-classification/csharp/Program.cs#CreateMLContext)]

    <span data-ttu-id="d3a08-206">[MLContext クラス](xref:Microsoft.ML.MLContext)は、すべての ML.NET 操作の開始点で、`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d3a08-207">これは Entity Framework における `DBContext` と概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="d3a08-208">Inception モデル パラメーターの構造体を作成する</span><span class="sxs-lookup"><span data-stu-id="d3a08-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="d3a08-209">Inception モデルには、渡す必要があるパラメーターがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="d3a08-210">次のコードを使用して、`Main()` メソッドの直後に、パラメーター値をフレンドリ名にマップする構造体を作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](./snippets/image-classification/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="d3a08-211">表示ユーティリティ メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="d3a08-211">Create a display utility method</span></span>

<span data-ttu-id="d3a08-212">画像データとそれに関連する予測を複数回表示するので、画像と予測結果の表示を処理する表示ユーティリティ メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="d3a08-213">`InceptionSettings` 構造体の直後に、次のコードを使用して `DisplayResults()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="d3a08-214">`DisplayResults` メソッドの本体を入力します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](./snippets/image-classification/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="d3a08-215">.tsv ファイル ユーティリティ メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="d3a08-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="d3a08-216">`DisplayResults()` メソッドの直後に、次のコードを使用して `ReadFromTsv()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="d3a08-217">`ReadFromTsv` メソッドの本体を入力します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](./snippets/image-classification/csharp/Program.cs#ReadFromTsv)]

    <span data-ttu-id="d3a08-218">このコードでは、`tags.tsv` ファイルを解析して、ファイルパスを `ImagePath` プロパティの画像ファイル名に追加し、それと `Label` を `ImageData` オブジェクトに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="d3a08-219">予測を行うメソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="d3a08-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="d3a08-220">`DisplayResults()` メソッドの直前に、次のコードを使用して `ClassifySingleImage()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="d3a08-221">1 つの `ImagePath` の完全修飾パスと画像ファイル名を含む `ImageData` オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="d3a08-222">`ClassifySingleImage()` メソッドの次の行として、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](./snippets/image-classification/csharp/Program.cs#LoadImageData)]

1. <span data-ttu-id="d3a08-223">次のコードを `ClassifySingleImage` メソッドの次の行として追加して、1 つの予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](./snippets/image-classification/csharp/Program.cs#PredictSingle)]

    <span data-ttu-id="d3a08-224">予測を取得するには、[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="d3a08-225">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) は、データの 1 つのインスタンスに対して予測を実行できる便利な API です。</span><span class="sxs-lookup"><span data-stu-id="d3a08-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="d3a08-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) はスレッド セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="d3a08-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="d3a08-227">シングル スレッド環境またはプロトタイプ環境で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="d3a08-228">運用環境でパフォーマンスとスレッド セーフを向上させるには、`PredictionEnginePool` サービスを使用します。これにより、アプリケーション全体で使用するできる [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) オブジェクトの [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="d3a08-229">[ASP.NET Core Web API で `PredictionEnginePool` を使用する](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)方法については、こちらのガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3a08-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="d3a08-230">`PredictionEnginePool` サービスの拡張機能は、現在プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="d3a08-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="d3a08-231">`ClassifySingleImage()` メソッドの次のコード行として予測結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](./snippets/image-classification/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="d3a08-232">ML.NET モデルのパイプラインを構築する</span><span class="sxs-lookup"><span data-stu-id="d3a08-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="d3a08-233">ML.NET モデルのパイプラインは推定器のチェーンです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="d3a08-234">パイプラインの構築中に実行は発生しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d3a08-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="d3a08-235">推定器オブジェクトは作成されますが、実行されません。</span><span class="sxs-lookup"><span data-stu-id="d3a08-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="d3a08-236">モデルを生成するメソッドを追加する</span><span class="sxs-lookup"><span data-stu-id="d3a08-236">Add a method to generate the model</span></span>

    <span data-ttu-id="d3a08-237">このメソッドは、このチュートリアルの中核となるものです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="d3a08-238">モデルのパイプラインを作成し、パイプラインをトレーニングして ML.NET モデルを生成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="d3a08-239">また、未認識のテスト データに対してモデルを評価します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="d3a08-240">`InceptionSettings` 構造体の直後、かつ `DisplayResults()` メソッドの直前に、次のコードを使用して `GenerateModel()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="d3a08-241">画像データを読み込み、サイズを変更し、ピクセルを抽出する推定器を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](./snippets/image-classification/csharp/Program.cs#ImageTransforms)]

    <span data-ttu-id="d3a08-242">画像データは、TensorFlow モデルで想定されている形式に処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="d3a08-243">この場合、画像はメモリに読み込まれ、サイズが一貫したサイズに変更され、ピクセルが数値ベクターに抽出されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="d3a08-244">TensorFlow モデルを読み込み、評価する推定器を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](./snippets/image-classification/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="d3a08-245">パイプラインのこのステージでは、TensorFlow モデルをメモリに読み込み、次に TensorFlow モデル ネットワークを介してピクセル値のベクターを処理します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="d3a08-246">ディープ ラーニング モデルに入力を適用し、モデルを使用して出力を生成することは、**スコアリング** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="d3a08-247">モデル全体を使用する場合、スコアリングによって推論または予測が行われます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="d3a08-248">この場合、最後のレイヤー (推論を行うレイヤー) を除き、すべての TensorFlow モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="d3a08-249">最後から 2 番目のレイヤーの出力には、`softmax_2_preactivation` というラベルが付けられます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="d3a08-250">このレイヤーの出力は、実質的に、元の入力画像を特徴付ける特徴のベクターです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="d3a08-251">TensorFlow モデルによって生成されるこの特徴ベクターは、ML.NET トレーニング アルゴリズムへの入力として使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="d3a08-252">トレーニング データの文字列ラベルを整数キー値にマップする推定器を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](./snippets/image-classification/csharp/Program.cs#MapValueToKey)]

    <span data-ttu-id="d3a08-253">次に追加される ML.NET トレーナーでは、ラベルが任意の文字列ではなく `key` 形式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="d3a08-254">キーは、文字列値への 1 対 1 のマッピングを持つ数値です。</span><span class="sxs-lookup"><span data-stu-id="d3a08-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="d3a08-255">ML.NET トレーニング アルゴリズムを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](./snippets/image-classification/csharp/Program.cs#AddTrainer)]

1. <span data-ttu-id="d3a08-256">予測されたキー値を元の文字列にマップする推定器を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](./snippets/image-classification/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="d3a08-257">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="d3a08-257">Train the model</span></span>

1. <span data-ttu-id="d3a08-258">[LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) ラッパーを使用してトレーニング データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="d3a08-259">`GenerateModel()` メソッドに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](./snippets/image-classification/csharp/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="d3a08-260">ML.NET 内のデータは、[IDataView クラス](xref:Microsoft.ML.IDataView)として表されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d3a08-261">`IDataView` は、表形式のデータ (数値とテキスト) を表すための柔軟で効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="d3a08-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="d3a08-262">データはテキスト ファイルから、またはリアルタイムで (SQL データベースやログ ファイルなど) `IDataView` オブジェクトに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="d3a08-263">前の手順で読み込まれたデータを使用してモデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="d3a08-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](./snippets/image-classification/csharp/Program.cs#TrainModel)]

    <span data-ttu-id="d3a08-264">`Fit()` メソッドで、トレーニング データセットをパイプラインに適用してモデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="d3a08-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="d3a08-265">モデルの精度を評価する</span><span class="sxs-lookup"><span data-stu-id="d3a08-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="d3a08-266">`GenerateModel` メソッドの次の行に次のコードを追加して、テスト データを読み込んで変換します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](./snippets/image-classification/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="d3a08-267">モデルの評価に使用できるサンプル画像がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="d3a08-268">トレーニング データと同様に、モデルで変換できるように、これらを `IDataView` に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="d3a08-269">`GenerateModel()` メソッドに次のコードを追加して、モデルを評価します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](./snippets/image-classification/csharp/Program.cs#Evaluate)]

    <span data-ttu-id="d3a08-270">予測セットを作成したら、[Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="d3a08-271">モデルを評価します (予測値とテスト データセット `labels` を比較します)。</span><span class="sxs-lookup"><span data-stu-id="d3a08-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="d3a08-272">モデルのパフォーマンス メトリックを返します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="d3a08-273">モデルの精度のメトリックを表示する</span><span class="sxs-lookup"><span data-stu-id="d3a08-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="d3a08-274">次のコードを使用してメトリックを表示し、結果を共有し、それに対してアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](./snippets/image-classification/csharp/Program.cs#DisplayMetrics)]

    <span data-ttu-id="d3a08-275">画像分類では、次のメトリックが評価されます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="d3a08-276">`Log-loss` - 「[対数損失](../resources/glossary.md#log-loss)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3a08-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="d3a08-277">対数損失は可能な限り 1 に近づけます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="d3a08-278">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="d3a08-278">`Per class Log-loss`.</span></span> <span data-ttu-id="d3a08-279">クラスごとの対数損失は可能な限り 1 に近づけます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="d3a08-280">次の行としてトレーニング済みモデルを返すように次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](./snippets/image-classification/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="d3a08-281">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-281">Run the application!</span></span>

1. <span data-ttu-id="d3a08-282">MLContext クラスを作成した後、`Main` メソッドに `GenerateModel` の呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](./snippets/image-classification/csharp/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="d3a08-283">`Main` メソッドの次のコード行として、`ClassifySingleImage()` メソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a08-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](./snippets/image-classification/csharp/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="d3a08-284">コンソール アプリを実行します (Ctrl + F5 キー)。</span><span class="sxs-lookup"><span data-stu-id="d3a08-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="d3a08-285">結果は以下の出力のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="d3a08-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="d3a08-286">警告メッセージまたは処理中のメッセージが表示される場合がありますが、わかりやすくするため、これらのメッセージは結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="d3a08-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

<span data-ttu-id="d3a08-287">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="d3a08-287">Congratulations!</span></span> <span data-ttu-id="d3a08-288">これで、ML.NET で `TensorFlow` モデルに転移学習を適用して、画像分類の機械学習モデルを構築できました。</span><span class="sxs-lookup"><span data-stu-id="d3a08-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="d3a08-289">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="d3a08-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="d3a08-290">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="d3a08-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="d3a08-291">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="d3a08-291">Understand the problem</span></span>
> * <span data-ttu-id="d3a08-292">事前トレーニング済みの TensorFlow モデルを ML.NET パイプラインに組み込む</span><span class="sxs-lookup"><span data-stu-id="d3a08-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="d3a08-293">ML.NET モデルのトレーニングと評価</span><span class="sxs-lookup"><span data-stu-id="d3a08-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="d3a08-294">テスト画像を分類する</span><span class="sxs-lookup"><span data-stu-id="d3a08-294">Classify a test image</span></span>

<span data-ttu-id="d3a08-295">Machine Learning サンプルの GitHub リポジトリを確認し、拡張された画像分類サンプルを探索してください。</span><span class="sxs-lookup"><span data-stu-id="d3a08-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d3a08-296">dotnet/machinelearning-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="d3a08-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
