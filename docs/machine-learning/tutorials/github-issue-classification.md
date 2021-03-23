---
title: 'チュートリアル: サポートの問題の分類 - 多クラス分類'
description: GitHub の問題を分類し、それを特定の領域に割り当てるための多クラス分類シナリオで、ML.NET を使用する方法について説明します。
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: dfc007f72fcd67f31139bc7fcbad93dde39d88fb
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875630"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="e9d87-103">チュートリアル: ML.NET での多クラス分類を使用したサポートの問題の分類</span><span class="sxs-lookup"><span data-stu-id="e9d87-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="e9d87-104">このサンプル チュートリアルでは ML.NET を使用して GitHub の問題の分類子を作成し、Visual Studio で C# を使用する .NET Core コンソール アプリケーションから GitHub の問題に対する区分ラベルを分類して予測するモデルをトレーニングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="e9d87-105">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="e9d87-106">データを準備する</span><span class="sxs-lookup"><span data-stu-id="e9d87-106">Prepare your data</span></span>
> * <span data-ttu-id="e9d87-107">データを変換する</span><span class="sxs-lookup"><span data-stu-id="e9d87-107">Transform the data</span></span>
> * <span data-ttu-id="e9d87-108">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="e9d87-108">Train the model</span></span>
> * <span data-ttu-id="e9d87-109">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="e9d87-109">Evaluate the model</span></span>
> * <span data-ttu-id="e9d87-110">トレーニング済みモデルを使用して予測する</span><span class="sxs-lookup"><span data-stu-id="e9d87-110">Predict with the trained model</span></span>
> * <span data-ttu-id="e9d87-111">読み込み済みのモデルを使用して配置および予測する</span><span class="sxs-lookup"><span data-stu-id="e9d87-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="e9d87-112">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/GitHubIssueClassification) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e9d87-113">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e9d87-113">Prerequisites</span></span>

* <span data-ttu-id="e9d87-114">".NET Core クロスプラットフォーム開発" ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 以降または Visual Studio 2017 バージョン 15.6 以降。</span><span class="sxs-lookup"><span data-stu-id="e9d87-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* <span data-ttu-id="e9d87-115">[GitHub の問題のタブ区切りのファイル (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv)。</span><span class="sxs-lookup"><span data-stu-id="e9d87-115">The [GitHub issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="e9d87-116">[GitHub の問題のテスト タブ区切りのファイル (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv)。</span><span class="sxs-lookup"><span data-stu-id="e9d87-116">The [GitHub issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e9d87-117">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="e9d87-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="e9d87-118">プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="e9d87-118">Create a project</span></span>

1. <span data-ttu-id="e9d87-119">Visual Studio 2017 を開きます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="e9d87-120">**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** をメニュー バーから選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="e9d87-121">**[新しいプロジェクト]** ダイアログで、 **[Visual C#]** ノードを選択し、 **[.NET Core]** ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="e9d87-122">次に、 **[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="e9d87-123">**[名前]** テキスト ボックスに「GitHubIssueClassification」と入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="e9d87-124">プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="e9d87-125">**ソリューション エクスプローラー** で、プロジェクトを右クリックし、 **[追加]**  >  **[新しいフォルダー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="e9d87-126">「Data」と入力して Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="e9d87-127">プロジェクトに *Models* という名前のディレクトリを作成して、モデルを保存します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="e9d87-128">**ソリューション エクスプローラー** で、プロジェクトを右クリックし、 **[追加]**  >  **[新しいフォルダー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="e9d87-129">「Models」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="e9d87-130">**Microsoft.ML NuGet パッケージ** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="e9d87-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="e9d87-131">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="e9d87-132">[パッケージ ソース] として [nuget.org] を選択します。[参照] タブを選択し、「**Microsoft.ML**」を検索し、 **[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="e9d87-133">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="e9d87-134">データを準備する</span><span class="sxs-lookup"><span data-stu-id="e9d87-134">Prepare your data</span></span>

1. <span data-ttu-id="e9d87-135">[issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) データ セットと [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) データ セットをダウンロードして、それらを作成済みの *Data* フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="e9d87-136">1 番目のデータ セットでは機械学習モデルをトレーニングし、2 番目のデータ セットはモデルの精度を評価するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="e9d87-137">ソリューション エクスプローラーで、各 \*.tsv ファイルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="e9d87-138">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="e9d87-139">クラスを作成してパスを定義する</span><span class="sxs-lookup"><span data-stu-id="e9d87-139">Create classes and define paths</span></span>

<span data-ttu-id="e9d87-140">次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](./snippets/github-issue-classification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="e9d87-141">最近ダウンロードしたファイルのパスを保持する 3 つのグローバル フィールドと、`MLContext`、`DataView`、および `PredictionEngine` のためのグローバル変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="e9d87-142">`_trainDataPath` には、モデルのトレーニングに使用するデータ セットのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="e9d87-143">`_testDataPath` には、モデルの評価に使用するデータ セットのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="e9d87-144">`_modelPath` には、トレーニング済みのモデルを保存するパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="e9d87-145">`_mlContext` は処理コンテキストを提供する <xref:Microsoft.ML.MLContext> です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="e9d87-146">`_trainingDataView` は、トレーニング データセットを処理するために使用される <xref:Microsoft.ML.IDataView> です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="e9d87-147">`_predEngine` は、1 つの予測に使用される <xref:Microsoft.ML.PredictionEngine%602> です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="e9d87-148">`Main` メソッドのすぐ上にある行に次のコードを追加して、それらのパスとその他の変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-148">Add the following code to the line directly above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](./snippets/github-issue-classification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="e9d87-149">入力データと予測のために、いくつかのクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="e9d87-150">プロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="e9d87-151">**ソリューション エクスプローラー** で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="e9d87-152">**[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを「*GitHubIssueData.cs*」に変更します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="e9d87-153">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="e9d87-154">コード エディターで *GitHubIssueData.cs* ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="e9d87-155">*GitHubIssueData.cs* の先頭に次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](./snippets/github-issue-classification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="e9d87-156">既存のクラス定義を削除し、`GitHubIssue` と `IssuePrediction` の 2 つのクラスを含む次のコードを *GitHubIssueData.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](./snippets/github-issue-classification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="e9d87-157">`label` は予測する列です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="e9d87-158">識別された `Features` は、ラベルを予測するためにモデルを指定する入力です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="e9d87-159">データ セット内のソース列のインデックスを指定するには、[LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) を使用します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="e9d87-160">`GitHubIssue` は、入力データセット クラスで、次の <xref:System.String> フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="e9d87-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="e9d87-161">最初の列 `ID` (GitHub 問題 ID)</span><span class="sxs-lookup"><span data-stu-id="e9d87-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="e9d87-162">2 番目の列 `Area` (トレーニングの予測)</span><span class="sxs-lookup"><span data-stu-id="e9d87-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="e9d87-163">3 番目の列 `Title` (GitHub の問題のタイトル) は、`Area` の予測に使用される最初の `feature` です</span><span class="sxs-lookup"><span data-stu-id="e9d87-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="e9d87-164">第 4 列 `Description` は、`Area` の予測に使用される 2 番目の `feature` です</span><span class="sxs-lookup"><span data-stu-id="e9d87-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="e9d87-165">`IssuePrediction` は、モデルがトレーニングされた後に、予測に使用されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="e9d87-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="e9d87-166">これには、1 つの `string` (`Area`) と、`PredictedLabel` `ColumnName` 属性があります。</span><span class="sxs-lookup"><span data-stu-id="e9d87-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="e9d87-167">`PredictedLabel` は予測と評価の際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="e9d87-168">評価では、トレーニング データを含む入力、予測された値、およびモデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="e9d87-169">すべての ML.NET 操作は、[MLContext ](xref:Microsoft.ML.MLContext)クラスで始まります。</span><span class="sxs-lookup"><span data-stu-id="e9d87-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="e9d87-170">`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="e9d87-171">`Entity Framework` における `DBContext` と、概念的にはほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="e9d87-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="e9d87-172">Main で変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="e9d87-172">Initialize variables in Main</span></span>

<span data-ttu-id="e9d87-173">複数のトレーニング間で反復可能な決定論的結果を得るために、`_mlContext` グローバル変数をランダム シード (`seed: 0`) を使用して `MLContext` の新しいインスタンスで初期化します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="e9d87-174">`Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](./snippets/github-issue-classification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="e9d87-175">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="e9d87-175">Load the data</span></span>

<span data-ttu-id="e9d87-176">ML.NET では、数値またはテキストの表形式データを記述する柔軟で効率的な方法として、[IDataView クラス](xref:Microsoft.ML.IDataView)を使います。</span><span class="sxs-lookup"><span data-stu-id="e9d87-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="e9d87-177">`IDataView` は、テキスト ファイルを読み込むか、またはリアルタイムで読み込むことができます (たとえば、SQL データベースまたはログ ファイル)。</span><span class="sxs-lookup"><span data-stu-id="e9d87-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="e9d87-178">パイプラインで利用するために `_trainingDataView` グローバル変数を初期化して読み込むには、`mlContext` 初期化の後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](./snippets/github-issue-classification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="e9d87-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) は、データ スキーマを定義し、ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e9d87-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="e9d87-180">データ パス変数を取得して、`IDataView` を返します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="e9d87-181">`Main` メソッドに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](./snippets/github-issue-classification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="e9d87-182">`ProcessData` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="e9d87-183">データを抽出して変換します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="e9d87-184">処理パイプラインを返します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="e9d87-185">`Main` メソッドの直後に、次のコードを使用して `ProcessData` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="e9d87-186">特徴を抽出してデータを変換する</span><span class="sxs-lookup"><span data-stu-id="e9d87-186">Extract Features and transform the data</span></span>

<span data-ttu-id="e9d87-187">`GitHubIssue` に対する GitHub の区分ラベルを予測する場合、[MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) メソッドを使用して `Area` 列を数値キー型の `Label` 列 (分類アルゴリズムによって許可される形式) に変換し、それを新しいデータセット列として追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](./snippets/github-issue-classification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="e9d87-188">次に、テキスト (`Title` および `Description`) 列をそれぞれ `TitleFeaturized` および `DescriptionFeaturized` と呼ばれる数値ベクターに変換する `mlContext.Transforms.Text.FeaturizeText` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-188">Next, call `mlContext.Transforms.Text.FeaturizeText`, which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="e9d87-189">次のコードを使用して、両列の特徴付けをパイプラインに追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](./snippets/github-issue-classification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="e9d87-190">データ準備の最後の手順では、[Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) メソッドを使用して、すべての特徴列を **Features** 列に結合します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="e9d87-191">既定では、学習アルゴリズムは **Features** 列の特徴のみを処理します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="e9d87-192">次のコードを使用してパイプラインに、この変換を追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](./snippets/github-issue-classification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="e9d87-193">次に、DataView をキャッシュするために <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> を追加します。つまり、次のコードでキャッシュを使用してデータが複数回反復されると、パフォーマンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e9d87-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](./snippets/github-issue-classification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="e9d87-194">小/中規模のデータセットの場合は、AppendCacheCheckpoint を使用して、トレーニング時間を短くします。</span><span class="sxs-lookup"><span data-stu-id="e9d87-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="e9d87-195">非常に大きいデータセットを処理するときは、使用しないでください (.AppendCacheCheckpoint() を削除します)。</span><span class="sxs-lookup"><span data-stu-id="e9d87-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="e9d87-196">`ProcessData` メソッドの最後で、パイプラインが返されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](./snippets/github-issue-classification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="e9d87-197">この手順で前処理と特徴付けが処理されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="e9d87-198">ML.NET に用意されているその他のコンポーネントを使用すると、モデルでより良い結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="e9d87-199">モデルを構築してトレーニングする</span><span class="sxs-lookup"><span data-stu-id="e9d87-199">Build and train the model</span></span>

<span data-ttu-id="e9d87-200">`Main` メソッドの次のコード行として、`BuildAndTrainModel` メソッドに次の呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](./snippets/github-issue-classification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="e9d87-201">`BuildAndTrainModel` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="e9d87-202">トレーニング アルゴリズムのクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="e9d87-203">モデルをトレーニングする。</span><span class="sxs-lookup"><span data-stu-id="e9d87-203">Trains the model.</span></span>
* <span data-ttu-id="e9d87-204">トレーニング データに基づいて区分を予測します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="e9d87-205">モデルを返します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-205">Returns the model.</span></span>

<span data-ttu-id="e9d87-206">`Main` メソッドの直後に、次のコードを使用して `BuildAndTrainModel` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="e9d87-207">分類タスクについて</span><span class="sxs-lookup"><span data-stu-id="e9d87-207">About the classification task</span></span>

<span data-ttu-id="e9d87-208">分類とは、データを使用して項目またはデータ行のカテゴリ、型、クラスを **判断** する機械学習タスクであり、多くの場合、次のいずれかの種類になります。</span><span class="sxs-lookup"><span data-stu-id="e9d87-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="e9d87-209">バイナリ: A か B のいずれかである。</span><span class="sxs-lookup"><span data-stu-id="e9d87-209">Binary: either A or B.</span></span>
* <span data-ttu-id="e9d87-210">多クラス: 1 つのモデルを使用して予測できるカテゴリが多数ある。</span><span class="sxs-lookup"><span data-stu-id="e9d87-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="e9d87-211">この種の問題では、問題カテゴリの予測が 2 つだけ (バイナリ) ではなく複数のカテゴリの 1 つ (多クラス) なので、多クラス分類学習アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="e9d87-212">`BuildAndTrainModel()` 内に最初のコード行として以下を付加することで、データ変換定義に機械学習アルゴリズムを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](./snippets/github-issue-classification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="e9d87-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) は、マルチクラス分類のトレーニング アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="e9d87-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="e9d87-214">これは `pipeline` に付加され、特徴付けされた `Title` と `Description` (`Features`) および `Label` 入力パラメータ―を受け入れて、履歴データから学習します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="e9d87-215">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="e9d87-215">Train the model</span></span>

<span data-ttu-id="e9d87-216">`BuildAndTrainModel()` メソッドの次のコード行として以下を追加して、モデルを `splitTrainSet` データに適合させ、トレーニング済みモデルを返します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](./snippets/github-issue-classification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="e9d87-217">`Fit()` メソッドでは、データセットを変換してトレーニングを適用することで、モデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="e9d87-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="e9d87-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) は、データの 1 つのインスタンスを渡してから、その予測を実行できる便利な API です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="e9d87-219">`BuildAndTrainModel()` メソッドに次の行として以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](./snippets/github-issue-classification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="e9d87-220">トレーニング済みモデルを使用して予測する</span><span class="sxs-lookup"><span data-stu-id="e9d87-220">Predict with the trained model</span></span>

<span data-ttu-id="e9d87-221">GitHub の問題を追加して、`Predict` メソッドでトレーニングされたモデルの予測をテストします。これには `GitHubIssue` のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](./snippets/github-issue-classification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="e9d87-222">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 関数を使用して、データの 1 つの行に対して予測を行います。</span><span class="sxs-lookup"><span data-stu-id="e9d87-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](./snippets/github-issue-classification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="e9d87-223">モデルの使用: 予測結果</span><span class="sxs-lookup"><span data-stu-id="e9d87-223">Using the model: prediction results</span></span>

<span data-ttu-id="e9d87-224">結果を共有し、それに応じたアクションを実行するために、`GitHubIssue` および対応する `Area` ラベル予測を表示します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="e9d87-225">次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果の表示を作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](./snippets/github-issue-classification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="e9d87-226">評価に使用する、トレーニング済みのモデルを返す</span><span class="sxs-lookup"><span data-stu-id="e9d87-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="e9d87-227">`BuildAndTrainModel` メソッドの最後で、モデルを返します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](./snippets/github-issue-classification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="e9d87-228">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="e9d87-228">Evaluate the model</span></span>

<span data-ttu-id="e9d87-229">これでモデルの作成とトレーニングが完了したので、品質保証と検証のために、別のデータ セットを使用してモデルを評価します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="e9d87-230">`Evaluate` メソッドでは、`BuildAndTrainModel` で作成されたモデルが渡されて評価されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="e9d87-231">`BuildAndTrainModel` の直後に、次のコードに示すように `Evaluate` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="e9d87-232">`Evaluate` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="e9d87-233">テスト データ セットを読み込む。</span><span class="sxs-lookup"><span data-stu-id="e9d87-233">Loads the test dataset.</span></span>
* <span data-ttu-id="e9d87-234">多クラス評価器を作成する。</span><span class="sxs-lookup"><span data-stu-id="e9d87-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="e9d87-235">モデルを評価し、メトリックを作成する。</span><span class="sxs-lookup"><span data-stu-id="e9d87-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="e9d87-236">メトリックを表示する。</span><span class="sxs-lookup"><span data-stu-id="e9d87-236">Displays the metrics.</span></span>

<span data-ttu-id="e9d87-237">`BuildAndTrainModel` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](./snippets/github-issue-classification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="e9d87-238">トレーニング データセットで以前にも行ったように、次のコードを `Evaluate` メソッドに追加することで、テスト データセットを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](./snippets/github-issue-classification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="e9d87-239">[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) メソッドは、指定されたデータセットを使用して、モデルに対する品質メトリックを計算します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="e9d87-240">これによって返される <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> オブジェクトには、多クラス分類評価器によって計算されるメトリック全体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="e9d87-241">メトリックを表示してモデルの品質を判定するには、最初にメトリックを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9d87-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="e9d87-242">特徴を入力して予測を返すために、機械学習の `_trainedModel` グローバル変数 ([ITransformer](xref:Microsoft.ML.ITransformer)) の [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドを使用していることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="e9d87-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="e9d87-243">`Evaluate` メソッドに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](./snippets/github-issue-classification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="e9d87-244">多クラス分類では、次のメトリックが評価されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="e9d87-245">マイクロ精度: すべてのサンプルとクラスのペアが、精度メトリックに均等に作用します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="e9d87-246">マイクロ精度は可能な限り 1 に近づけます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="e9d87-247">マクロ精度: すべてのクラスが、精度メトリックに均等に作用します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="e9d87-248">少数派のクラスは、大規模なクラスと同じ重みが与えられています。</span><span class="sxs-lookup"><span data-stu-id="e9d87-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="e9d87-249">マクロ精度は可能な限り 1 に近づけます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="e9d87-250">対数損失: [対数損失](../resources/glossary.md#log-loss)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9d87-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="e9d87-251">対数損失は可能な限り 1 に近づけます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="e9d87-252">対数損失還元: 範囲は [-inf, 1.00] です。ここで、1.00 は完璧な予測で、0 は平均の予測です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="e9d87-253">対数損失還元は可能な限り 1 に近づけます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="e9d87-254">モデル検証のためのメトリックを表示する</span><span class="sxs-lookup"><span data-stu-id="e9d87-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="e9d87-255">次のコードを使用してメトリックを表示し、結果を共有し、それに対してアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](./snippets/github-issue-classification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="e9d87-256">モデルをファイルに保存する</span><span class="sxs-lookup"><span data-stu-id="e9d87-256">Save the model to a file</span></span>

<span data-ttu-id="e9d87-257">モデルに問題がなければ、後で、または別のアプリケーションで予測を行うために、そのモデルをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="e9d87-258">`Evaluate` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="e9d87-259">`Evaluate` メソッドの下に `SaveModelAsFile` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="e9d87-260">次のコードを `SaveModelAsFile` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="e9d87-261">このコードでは [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save%2A) メソッドを使用して、トレーニング済みのモデルを zip ファイルとしてシリアル化し、格納します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save%2A) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="e9d87-262">モデルによるデプロイと予測</span><span class="sxs-lookup"><span data-stu-id="e9d87-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="e9d87-263">`Evaluate` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](./snippets/github-issue-classification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="e9d87-264">`Evaluate` メソッドの直後 (および `SaveModelAsFile` メソッドの直前) に、次のコードを使用して `PredictIssue` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="e9d87-265">`PredictIssue` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="e9d87-266">保存されたモデルを読み込む</span><span class="sxs-lookup"><span data-stu-id="e9d87-266">Loads the saved model</span></span>
* <span data-ttu-id="e9d87-267">テスト データの問題を 1 つ作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="e9d87-268">テスト データに基づいて区分を予測します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="e9d87-269">テスト データと予測をレポート用に結合する。</span><span class="sxs-lookup"><span data-stu-id="e9d87-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="e9d87-270">予測された結果を表示する。</span><span class="sxs-lookup"><span data-stu-id="e9d87-270">Displays the predicted results.</span></span>

<span data-ttu-id="e9d87-271">`PredictIssue` メソッドに次のコードを追加して、保存されたモデルをアプリケーションに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="e9d87-272">GitHub の問題を追加して、`Predict` メソッドでトレーニングされたモデルの予測をテストします。これには `GitHubIssue` のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](./snippets/github-issue-classification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="e9d87-273">以前に行ったように、次のコードを使って `PredictionEngine` インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](./snippets/github-issue-classification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="e9d87-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) は、データの 1 つのインスタンスに対して予測を実行できる便利な API です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="e9d87-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) はスレッド セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="e9d87-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="e9d87-276">シングル スレッド環境またはプロトタイプ環境で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="e9d87-277">運用環境でパフォーマンスとスレッド セーフを向上させるには、`PredictionEnginePool` サービスを使用します。これにより、アプリケーション全体で使用するできる [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) オブジェクトの [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="e9d87-278">[ASP.NET Core Web API で `PredictionEnginePool` を使用する](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)方法については、こちらのガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9d87-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="e9d87-279">`PredictionEnginePool` サービスの拡張機能は、現在プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="e9d87-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="e9d87-280">`PredictionEngine` を使用して、予測のための `PredictIssue` メソッドに次のコードを追加して、GitHub の区分ラベルを予測します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](./snippets/github-issue-classification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="e9d87-281">予測のために読み込み済みのモデルを使用する</span><span class="sxs-lookup"><span data-stu-id="e9d87-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="e9d87-282">問題を分類し、それに応じて処理するために `Area` を表示します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="e9d87-283">次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果の表示を作成します。</span><span class="sxs-lookup"><span data-stu-id="e9d87-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](./snippets/github-issue-classification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="e9d87-284">結果</span><span class="sxs-lookup"><span data-stu-id="e9d87-284">Results</span></span>

<span data-ttu-id="e9d87-285">結果は以下のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="e9d87-285">Your results should be similar to the following.</span></span> <span data-ttu-id="e9d87-286">パイプラインが処理されると、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="e9d87-287">警告または処理メッセージが表示されることがありますが、</span><span class="sxs-lookup"><span data-stu-id="e9d87-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="e9d87-288">わかりやすくするために、これらのメッセージは次の結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="e9d87-288">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="e9d87-289">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="e9d87-289">Congratulations!</span></span> <span data-ttu-id="e9d87-290">これで、GitHub の問題用の区分ラベルを分類および予測するための機械学習モデルをビルドできました。</span><span class="sxs-lookup"><span data-stu-id="e9d87-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="e9d87-291">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/GitHubIssueClassification) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="e9d87-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e9d87-292">次の手順</span><span class="sxs-lookup"><span data-stu-id="e9d87-292">Next steps</span></span>

<span data-ttu-id="e9d87-293">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="e9d87-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="e9d87-294">データを準備する</span><span class="sxs-lookup"><span data-stu-id="e9d87-294">Prepare your data</span></span>
> * <span data-ttu-id="e9d87-295">データを変換する</span><span class="sxs-lookup"><span data-stu-id="e9d87-295">Transform the data</span></span>
> * <span data-ttu-id="e9d87-296">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="e9d87-296">Train the model</span></span>
> * <span data-ttu-id="e9d87-297">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="e9d87-297">Evaluate the model</span></span>
> * <span data-ttu-id="e9d87-298">トレーニング済みモデルを使用して予測する</span><span class="sxs-lookup"><span data-stu-id="e9d87-298">Predict with the trained model</span></span>
> * <span data-ttu-id="e9d87-299">読み込み済みのモデルを使用して配置および予測する</span><span class="sxs-lookup"><span data-stu-id="e9d87-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="e9d87-300">さらに詳しく学習するには、次のチュートリアルに進んでください。</span><span class="sxs-lookup"><span data-stu-id="e9d87-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e9d87-301">タクシー代予測</span><span class="sxs-lookup"><span data-stu-id="e9d87-301">Taxi Fare Predictor</span></span>](predict-prices.md)
