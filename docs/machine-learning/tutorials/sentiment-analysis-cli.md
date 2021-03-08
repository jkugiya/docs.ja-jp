---
title: ML.NET CLI を使用してセンチメントを分析する
description: サンプル データセットから ML モデルと関連する C# コードを自動的に生成する
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 47c38bb0b66a6fc08dd319583847dd83baedcd1e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103700"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="ad3a0-103">ML.NET CLI を使用してセンチメントを分析する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="ad3a0-104">ML.NET CLI を使用して ML.NET モデルと基礎となる C# コードを自動生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="ad3a0-105">データセットと実装する機械学習タスクを指定すると、CLI では、AutoML エンジンを使用してモデルの生成と展開のソース コードと、分類モデルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the classification model.</span></span>

<span data-ttu-id="ad3a0-106">このチュートリアルでは、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ad3a0-107">選択した機械学習タスク用にデータを準備する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="ad3a0-108">CLI から "mlnet classification" コマンドを実行する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-108">Run the 'mlnet classification' command from the CLI</span></span>
> - <span data-ttu-id="ad3a0-109">品質メトリックの結果を確認する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-109">Review the quality metric results</span></span>
> - <span data-ttu-id="ad3a0-110">アプリケーションでモデルを使用するために生成された C# コードを理解する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="ad3a0-111">モデルのトレーニングに使用された生成済み C# コードを調べる</span><span class="sxs-lookup"><span data-stu-id="ad3a0-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="ad3a0-112">このトピックは、現在プレビュー段階の ML.NET CLI ツールについて述べており、内容が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ad3a0-113">詳細については、[ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="ad3a0-114">ML.NET CLI は ML.NET の一部であり、その主な目的は、ML.NET を学習する .NET 開発者のために ML.NET を "民主化" することなので、始めるときにゼロからコードを書く必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="ad3a0-115">ML.NET CLI は任意のコマンドプロンプト (Windows、Mac、または Linux) で実行して、指定するトレーニング データセットに基づいて高品質の ML.NET モデルとソース コードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="ad3a0-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="ad3a0-116">Pre-requisites</span></span>

- <span data-ttu-id="ad3a0-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet/3.1) 以降</span><span class="sxs-lookup"><span data-stu-id="ad3a0-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet/3.1) or later</span></span>
- <span data-ttu-id="ad3a0-118">(省略可能) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="ad3a0-118">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="ad3a0-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="ad3a0-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="ad3a0-120">生成された C# コード プロジェクトは、Visual Studio から、または `dotnet run` (.NET Core CLI) を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="ad3a0-121">データを準備する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-121">Prepare your data</span></span>

<span data-ttu-id="ad3a0-122">ここでは、二項分類機械学習タスクである "感情分析" シナリオに使用されている既存のデータセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="ad3a0-123">お持ちのデータセットを同様の方法で使用して、モデルとコードを自動的に生成することができます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="ad3a0-124">[UCI Sentiment Labeled Sentences データセット zip ファイル (次の注の引用を参照してください)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) をダウンロードし、任意のフォルダーに展開します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ad3a0-125">このチュートリアルで使用されるデータセットでは、「From Group to Individual Labels using Deep Features」 (Kotzias 他</span><span class="sxs-lookup"><span data-stu-id="ad3a0-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="ad3a0-126">KDD 2015) のものであり、UCI 機械学習リポジトリ (Dua, D. and Karra Taniskidou, E.(2017)) でホストされています。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="ad3a0-127">UCI 機械学習リポジトリ [http://archive.ics.uci.edu/ml ]。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="ad3a0-128">カリフォルニア州アーバイン: カリフォルニア大学情報コンピュータサイエンス学部。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="ad3a0-129">`yelp_labelled.txt` ファイルを以前に作成した任意のフォルダー (`/cli-test` など) にコピーします。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="ad3a0-130">任意のコマンド プロンプトを開き、データセット ファイルをコピーしたフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="ad3a0-131">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="ad3a0-132">Visual Studio Code などの任意のテキスト エディターを使用して、`yelp_labelled.txt` データセット ファイルを開き、調べることができます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="ad3a0-133">次のような構造であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="ad3a0-134">このファイルにヘッダーはありません。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-134">The file has no header.</span></span> <span data-ttu-id="ad3a0-135">列のインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-135">You will use the column's index.</span></span>

    - <span data-ttu-id="ad3a0-136">列は 2 つしかありません。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-136">There are just two columns:</span></span>

        | <span data-ttu-id="ad3a0-137">テキスト (列インデックス 0)</span><span class="sxs-lookup"><span data-stu-id="ad3a0-137">Text (Column index 0)</span></span> | <span data-ttu-id="ad3a0-138">ラベル (列インデックス 1)</span><span class="sxs-lookup"><span data-stu-id="ad3a0-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="ad3a0-139">Wow...Loved this place.</span><span class="sxs-lookup"><span data-stu-id="ad3a0-139">Wow... Loved this place.</span></span> | <span data-ttu-id="ad3a0-140">1</span><span class="sxs-lookup"><span data-stu-id="ad3a0-140">1</span></span> |
        | <span data-ttu-id="ad3a0-141">Crust is not good.</span><span class="sxs-lookup"><span data-stu-id="ad3a0-141">Crust is not good.</span></span> | <span data-ttu-id="ad3a0-142">0</span><span class="sxs-lookup"><span data-stu-id="ad3a0-142">0</span></span> |
        | <span data-ttu-id="ad3a0-143">Not tasty and the texture was just nasty.</span><span class="sxs-lookup"><span data-stu-id="ad3a0-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="ad3a0-144">0</span><span class="sxs-lookup"><span data-stu-id="ad3a0-144">0</span></span> |
        | <span data-ttu-id="ad3a0-145">...その他のテキスト行...</span><span class="sxs-lookup"><span data-stu-id="ad3a0-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="ad3a0-146">...(1 または 0)...</span><span class="sxs-lookup"><span data-stu-id="ad3a0-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="ad3a0-147">データセット ファイルはエディターから必ず閉じてください。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="ad3a0-148">これで、この "感情分析" シナリオに CLI を使用する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ad3a0-149">このチュートリアルを完了した後は、現在 ML.NET CLI プレビューでサポートされているいずれかの ML タスク ( *"二項分類"、"分類"、"回帰"* 、 *"レコメンデーション"* ) に使用する準備ができていれば、お持ちのデータセットで試すこともできます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Classification', 'Regression',* and *'Recommendation'*.</span></span>

## <a name="run-the-mlnet-classification-command"></a><span data-ttu-id="ad3a0-150">"mlnet classification" コマンドを実行する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-150">Run the 'mlnet classification' command</span></span>

1. <span data-ttu-id="ad3a0-151">次の ML.NET CLI コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    <span data-ttu-id="ad3a0-152">このコマンドによって **`mlnet classification` コマンド** が次のように実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-152">This command runs the **`mlnet classification` command**:</span></span>
    - <span data-ttu-id="ad3a0-153">"*classification*" の **ML タスク** に対して</span><span class="sxs-lookup"><span data-stu-id="ad3a0-153">for the **ML task** of *classification*</span></span>
    - <span data-ttu-id="ad3a0-154">**データセット ファイル `yelp_labelled.txt`** をトレーニングおよびテスト データセットとして使用します (内部的には、CLI によってクロス検証が使用されるか、トレーニング用に 1 つとテスト用に 1 つという 2 つのデータセットに分割されます)。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="ad3a0-155">この予測する **目的列/ターゲット列** (一般的に **"ラベル"** と呼ばれます) は、**インデックス 1 の列** です (インデックスは 0 ベースなので、これは 2 列目です)。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="ad3a0-156">この特定のデータセット ファイルにはヘッダーがないため、列名を含む **ファイル ヘッダーは使用しません**。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="ad3a0-157">実験の **目標探索およびトレーニング時間** は **10 秒** です</span><span class="sxs-lookup"><span data-stu-id="ad3a0-157">the **targeted exploration/train time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="ad3a0-158">CLI からの出力が次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-158">You will see output from the CLI, similar to:</span></span>

    ![PowerShell での ML.NET CLI 分類](./media/mlnet-cli/mlnet-classification-powershell.gif)

    <span data-ttu-id="ad3a0-160">この特定のケースでは、CLI ツールでは、わずか 10 秒の間に指定した小さなデータセットに対してかなりの回数の反復処理を実行できました。つまり、内部データ変換とアルゴリズムのハイパーパラメーターが異なるさまざまなアルゴリズム/構成の組み合わせに基づいて、複数回のトレーニングを行いました。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-160">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="ad3a0-161">最後に、10 秒間で検出された "最高品質" のモデルは、何らかの特定の構成を持つ特定のトレーナー/アルゴリズムを使用するモデルです。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-161">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="ad3a0-162">探索時間によっては、コマンドから異なる結果が生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-162">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="ad3a0-163">選択は、`Accuracy` など、表示されている複数のメトリックに基づいています。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-163">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="ad3a0-164">**モデルの品質メトリックを理解する**</span><span class="sxs-lookup"><span data-stu-id="ad3a0-164">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="ad3a0-165">二項分類モデルを評価する最初で最も簡単なメトリックは正確度です。これは簡単に理解できます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-165">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="ad3a0-166">"正確度は、テスト データ セットでの正しい予測の割合です"。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-166">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="ad3a0-167">100% (1.00) に近いほど優れています。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-167">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="ad3a0-168">ただし、正確度メトリックを使用して測定するだけでは不十分な場合があります。特に、テスト データセットでラベル (この場合は 0 と 1) のバランスが取れていない場合です。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-168">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="ad3a0-169">追加のメトリックや、さまざまなモデルの評価に使用される **メトリックに関するより詳細な情報** (正確度、AUC、AUCPR、F1 スコアなど) については、[ML.NET のメトリックの概要](../resources/metrics.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-169">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ad3a0-170">これと同じデータセットを試し、`--max-exploration-time` に数分間 (たとえば 180 秒を指定するので 3 分間) を指定すると、このデータセット (かなり小規模で 1,000 行) に対して、トレーニング パイプライン構成が異なる優れた "最適なモデル" が自動的に検出されます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-170">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="ad3a0-171">大規模なデータセットを対象とした "運用環境対応モデル" である "最高/高品質" なモデルを見つけるには、通常、データセットのサイズに応じて、はるかに長い探索時間を指定して、CLI を使用した実験を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-171">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="ad3a0-172">実際のところ、多くの場合、特に行と列のデータセットが大きいと、数時間の探索時間が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-172">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="ad3a0-173">前のコマンド実行により、以下の資産が生成されました。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-173">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="ad3a0-174">すぐに使用できるシリアル化されたモデル .zip ("最適なモデル")。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-174">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="ad3a0-175">その生成されたモデルを実行/スコア付けする C# コード (そのモデルを使用してエンドユーザー アプリで予測を行うため)。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-175">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="ad3a0-176">そのモデルを生成に使用される C# トレーニング コード (学習目的)。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-176">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="ad3a0-177">ハイパーパラメーターとデータ変換の組み合わせを使用して各アルゴリズムに関する具体的な詳細情報を試し、すべての反復処理が探索されたログ ファイル。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-177">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="ad3a0-178">最初の 2 つの資産 (.ZIP ファイル モデルと、そのモデルを実行する C# コード) は、その生成された ML モデルを使用して予測を行うために、エンドユーザー アプリ (ASP.NET Core Web アプリ、サービス、デスクトップ アプリなど) で直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-178">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="ad3a0-179">3 つ目の資産のトレーニング コードは、生成されたモデルをトレーニングするために CLI によって使用された ML.NET API コードを示しています。そのため、CLI によって選択された特定のトレーナー/アルゴリズムとハイパーパラメーターを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-179">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="ad3a0-180">これらの列挙した資産については、チュートリアルの次の手順で説明します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-180">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="ad3a0-181">生成された C# コードを調べて予測するモデルの実行に使用する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-181">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="ad3a0-182">Visual Studio (2017 または 2019) で、元の保存先フォルダー内の `SampleClassification` という名前のフォルダーに生成されたソリューションを開きます (このチュートリアルでは `/cli-test` という名前でした)。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-182">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="ad3a0-183">次のようなソリューションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-183">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="ad3a0-184">このチュートリアルでは Visual Studio を使用することをお勧めしますが、生成された C# コード (2 つのプロジェクト) を任意のテキスト エディターで調べ、生成されたコンソール アプリを macOS、Linux または Windows マシン上で `dotnet CLI` を使用して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-184">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![CLI によって生成された VS ソリューション](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - <span data-ttu-id="ad3a0-186">シリアル化された ML モデル (.zip ファイル) とデータ クラス (データ モデル) を含む、生成された **クラス ライブラリ** は、エンドユーザー アプリケーションで直接使用できます。さらに、そのクラス ライブラリを直接参照する (または必要に応じてコードを移動する) こともできます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-186">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="ad3a0-187">生成された **コンソール アプリ** には、確認する必要がある実行コードが含まれているので、通常、単純なコード (わずか数行) を予測を行うエンドユーザー アプリケーションに移動することで、"スコア付けコード" (予測する ML モデルを実行するコード) を再利用します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-187">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="ad3a0-188">クラス ライブラリ プロジェクト内の **ModelInput.cs** および **ModelOutput.cs** クラス ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-188">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="ad3a0-189">これらのクラスは、データの保持に使用される "データ クラス" つまり POCO クラスであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-189">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="ad3a0-190">これは "定型コード" ですが、データセットに数十列から数百列がある場合に生成すると便利です。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-190">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="ad3a0-191">`ModelInput` クラスはデータセットからデータを読み取るときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-191">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="ad3a0-192">`ModelOutput` クラスは、予測結果 (予測データ) を取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-192">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="ad3a0-193">Program.cs ファイルを開き、コードを調べます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-193">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="ad3a0-194">わずか数行で、モデルを実行し、サンプル予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-194">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - 最初のコード行では、この場合は予測に使用するデータセットの最初の行に基づいて "*単一のサンプル データ*" が作成されます。 <span data-ttu-id="ad3a0-196">コードを更新し、独自の "ハードコーディングされたデータ" を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-196">You can also create you own 'hard-coded' data by updating the code:</span></span>

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - <span data-ttu-id="ad3a0-197">次のコード行では、指定の入力データ上で `ConsumeModel.Predict()` メソッドを使用して予測を行い、(ModelOutput.cs スキーマに基づいて) 結果を返します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-197">The next line of code uses the `ConsumeModel.Predict()` method on the specified input data to make a prediction and return the results (based on the ModelOutput.cs schema).</span></span>
    - <span data-ttu-id="ad3a0-198">最後のコード行では、サンプル データのプロパティに加え、Sentiment 予測と、肯定的なセンチメントの場合は (1)、否定的なセンチメントの場合は (2) という対応スコアが出力されます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-198">The last lines of code print out the properties of the sample data (in this case the Comment) as well as the Sentiment prediction and corresponding Scores for positive sentiment (1) and negative sentiment (2).</span></span>

1. <span data-ttu-id="ad3a0-199">プロジェクトを実行するには、データセットの最初の行から読み込まれた元のサンプル データを使用するか、ハードコーディングされた独自のカスタム サンプル データを指定します。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-199">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="ad3a0-200">次のような予測が得られます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-200">You should get a prediction comparable to:</span></span>

![ML.NET CLI で Visual Studio からアプリを実行する](./media/mlnet-cli/mlnet-cli-console-app.png)<span data-ttu-id="ad3a0-202">)</span><span class="sxs-lookup"><span data-stu-id="ad3a0-202">)</span></span>

1. <span data-ttu-id="ad3a0-203">ハードコーディングされたサンプル データをセンチメントが異なる他の文に変更して、モデルがどのように肯定的センチメントまたは否定的センチメントを予測するかを確認してみてください。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-203">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="ad3a0-204">エンドユーザー アプリケーションに ML モデルの予測を組み込む</span><span class="sxs-lookup"><span data-stu-id="ad3a0-204">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="ad3a0-205">同様の "ML モデル スコア付けコード" を使用して、エンドユーザー アプリケーションでモデルを実行し、予測することができます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-205">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="ad3a0-206">たとえば、そのコードを **WPF** や **WinForms** などの任意の Windows デスクトップ アプリケーションに直接移動して、コンソール アプリで実行したときと同じ方法でモデルを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-206">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="ad3a0-207">ただし、ML モデルを実行するこれらのコード行を実装する方法は、最適化して (つまり、モデルの .zip ファイルをキャッシュし、読み込みが 1 回になるようにして)、要求ごとに作成するのではなくシングルトン オブジェクトを持つようにします。次のセクションで説明するように、Web アプリケーションや分散サービスなど、アプリケーションをスケーラブルにする必要がある場合は特にそうです。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-207">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="ad3a0-208">スケーラブルな ASP.NET Core Web アプリケーションおよびサービス (マルチスレッド アプリ) で ML.NET モデルを実行する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-208">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="ad3a0-209">モデル オブジェクト (モデルの .zip ファイルから読み込まれた `ITransformer`) と `PredictionEngine` オブジェクトの作成は、最適化するようにします。特に、スケーラブルな Web アプリと分散サービスに対して実行する場合は特にそうです。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-209">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="ad3a0-210">最初のケースでは、モデル オブジェクト (`ITransformer`) の最適化は簡単です。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-210">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="ad3a0-211">`ITransformer` オブジェクトはスレッドセーフなので、オブジェクトをシングルトン オブジェクトまたは静的オブジェクトとしてキャッシュして、モデルの読み込みを 1 回にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-211">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="ad3a0-212">2 つ目のオブジェクトの `PredictionEngine` オブジェクトはそれほど簡単ではありません。`PredictionEngine` オブジェクトはスレッドセーフではないので、ASP.NET Core アプリでこのオブジェクトをシングルトン オブジェクトまたは静的オブジェクトとしてインスタンス化することができないからです。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-212">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="ad3a0-213">このスレッド セーフとスケーラビリティの問題については、この[ブログ記事](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)で詳しく説明されています。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-213">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="ad3a0-214">ただし、状況はこのブログ記事で説明されているよりもはるかに簡単になりました。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-214">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="ad3a0-215">Microsoft はより簡単なアプローチに取り組み、優れた **".NET Core 統合パッケージ"** を作成しました。アプリケーションの DI サービス (Dependency Injection サービス) に登録することで ASP.NET Core アプリおよびサービスで簡単に使用できます。また、その後はコードから直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-215">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="ad3a0-216">その実行方法については、次のチュートリアルと例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-216">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="ad3a0-217">チュートリアル: スケーラブルな ASP.NET Core Web アプリと WebAPI 上の ML.NET モデルの実行</span><span class="sxs-lookup"><span data-stu-id="ad3a0-217">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
- [<span data-ttu-id="ad3a0-218">サンプル: ASP.NET Core WebAPI 上のスケーラブルな ML.NET モデル</span><span class="sxs-lookup"><span data-stu-id="ad3a0-218">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="ad3a0-219">"最高品質" のモデルのトレーニングに使用された生成済み C# コードを調べる</span><span class="sxs-lookup"><span data-stu-id="ad3a0-219">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="ad3a0-220">より高度な学習目的のために、生成済みモデルのトレーニングに CLI ツールによって使用された生成済み C# コードを調べることもできます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-220">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="ad3a0-221">その "トレーニング モデル コード" は、現在、`ModelBuilder` という名前で生成されたカスタム クラスに生成されているので、そのトレーニング コードを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-221">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="ad3a0-222">さらに重要な点は、この特定のシナリオ (感情分析モデル) の場合、その生成済みトレーニング コードを次のチュートリアルで説明されているコードと比較することもできることです。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-222">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="ad3a0-223">比較:[チュートリアル: センチメント分析のバイナリ分類のシナリオで ML.NET を使用する](sentiment-analysis.md)</span><span class="sxs-lookup"><span data-stu-id="ad3a0-223">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="ad3a0-224">チュートリアルで選択したアルゴリズムとパイプラインの構成を CLI ツールによって生成されたコードと比較するのは興味深いことです。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-224">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="ad3a0-225">より良いモデルのために反復処理と検索に使う時間に応じて、選択されるアルゴリズムと、その特定のハイパーパラメーターとパイプラインの構成は変わることがあります。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-225">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="ad3a0-226">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="ad3a0-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ad3a0-227">選択した ML タスク (解決する問題) 用のデータを準備する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-227">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="ad3a0-228">CLI ツールで "mlnet classification" コマンドを実行する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-228">Run the 'mlnet classification' command in the CLI tool</span></span>
> - <span data-ttu-id="ad3a0-229">品質メトリックの結果を確認する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-229">Review the quality metric results</span></span>
> - <span data-ttu-id="ad3a0-230">モデルを実行するために生成された C# コード (エンドユーザー アプリで使用するコード) を理解する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-230">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="ad3a0-231">"最高品質" のモデルのトレーニングに使用された生成済み C# コードを調べる (学習目的)</span><span class="sxs-lookup"><span data-stu-id="ad3a0-231">Explore the generated C# code that was used to train the "best quality" model (earning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="ad3a0-232">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad3a0-232">See also</span></span>

- [<span data-ttu-id="ad3a0-233">ML.NET CLI を使用してモデルのトレーニングを自動化する</span><span class="sxs-lookup"><span data-stu-id="ad3a0-233">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="ad3a0-234">チュートリアル: スケーラブルな ASP.NET Core Web アプリと WebAPI 上の ML.NET モデルの実行</span><span class="sxs-lookup"><span data-stu-id="ad3a0-234">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
- [<span data-ttu-id="ad3a0-235">サンプル: ASP.NET Core WebAPI 上のスケーラブルな ML.NET モデル</span><span class="sxs-lookup"><span data-stu-id="ad3a0-235">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="ad3a0-236">ML.NET CLI auto-train コマンド リファレンス ガイド</span><span class="sxs-lookup"><span data-stu-id="ad3a0-236">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="ad3a0-237">ML.NET CLI のテレメトリ</span><span class="sxs-lookup"><span data-stu-id="ad3a0-237">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
