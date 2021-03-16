---
title: 'チュートリアル: 通話の異常を検出する'
description: 時系列データの異常検出アプリケーションを構築する方法について学習します。 このチュートリアルでは、Visual Studio 2019 の C# を使って .NET Core コンソール アプリケーションを作成します。
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7edb84ae53f1da7903cf4b3f77d215206ffbf1ef
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259825"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a><span data-ttu-id="95c29-104">チュートリアル: ML.NET で時系列の異常を検出する</span><span class="sxs-lookup"><span data-stu-id="95c29-104">Tutorial: Detect anomalies in time series with ML.NET</span></span>

<span data-ttu-id="95c29-105">時系列データの異常検出アプリケーションを構築する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="95c29-105">Learn how to build an anomaly detection application for time series data.</span></span> <span data-ttu-id="95c29-106">このチュートリアルでは、Visual Studio 2019 の C# を使って .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="95c29-106">This tutorial creates a .NET Core console application using C# in Visual Studio 2019.</span></span>

<span data-ttu-id="95c29-107">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95c29-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="95c29-108">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="95c29-108">Load the data</span></span>
> * <span data-ttu-id="95c29-109">時系列の期間を検出する</span><span class="sxs-lookup"><span data-stu-id="95c29-109">Detect period for a time series</span></span>
> * <span data-ttu-id="95c29-110">定期的な時系列の異常を検出する</span><span class="sxs-lookup"><span data-stu-id="95c29-110">Detect anomaly for a periodical time series</span></span>

<span data-ttu-id="95c29-111">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="95c29-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95c29-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="95c29-112">Prerequisites</span></span>

* <span data-ttu-id="95c29-113">[Visual Studio 2019 バージョン 16.7.8 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)が ".NET Core クロスプラットフォーム開発" ワークロードと共にインストールされている。</span><span class="sxs-lookup"><span data-stu-id="95c29-113">[Visual Studio 2019 version 16.7.8 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="95c29-114">[phone-calls.csv データセット](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv)。</span><span class="sxs-lookup"><span data-stu-id="95c29-114">[The phone-calls.csv dataset](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="95c29-115">コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="95c29-115">Create a console application</span></span>

1. <span data-ttu-id="95c29-116">"PhoneCallsAnomalyDetection" という **C# .NET Core コンソール アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="95c29-116">Create a **C# .NET Core Console Application** called "PhoneCallsAnomalyDetection".</span></span>

2. <span data-ttu-id="95c29-117">データ セット ファイルを保存するために、プロジェクトに *Data* という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="95c29-117">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="95c29-118">**Microsoft.ML NuGet パッケージ** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="95c29-118">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="95c29-119">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95c29-119">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="95c29-120">[パッケージ ソース] として [nuget.org] を選択します。[参照] タブを選択し、「**Microsoft.ML**」を検索し、 **[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="95c29-120">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="95c29-121">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95c29-121">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="95c29-122">**Microsoft.ML.TimeSeries** についてもこれらの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="95c29-122">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="95c29-123">*Program.cs* の先頭に次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="95c29-123">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="95c29-124">データをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="95c29-124">Download your data</span></span>

1. <span data-ttu-id="95c29-125">データセットをダウンロードし、以前に作成した *Data* フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="95c29-125">Download the dataset and save it to the *Data* folder you previously created:</span></span>

    <span data-ttu-id="95c29-126">[*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) を右クリックし、[名前を付けてリンク (または対象) を保存] を選択します</span><span class="sxs-lookup"><span data-stu-id="95c29-126">Right click on [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="95c29-127">\*.csv ファイルを *Data* フォルダーに保存したことを確認します。または他の場所に保存した後に、\*.csv ファイルを *Data* フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="95c29-127">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="95c29-128">ソリューション エクスプローラーで、\*.csv ファイルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95c29-128">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="95c29-129">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="95c29-129">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="95c29-130">次の表は、\*.csv ファイルのデータのプレビューです。</span><span class="sxs-lookup"><span data-stu-id="95c29-130">The following table is a data preview from your \*.csv file:</span></span>

| <span data-ttu-id="95c29-131">timestamp</span><span class="sxs-lookup"><span data-stu-id="95c29-131">timestamp</span></span>  | <span data-ttu-id="95c29-132">value</span><span class="sxs-lookup"><span data-stu-id="95c29-132">value</span></span> |
|--------|--------------|
| <span data-ttu-id="95c29-133">2018/9/3</span><span class="sxs-lookup"><span data-stu-id="95c29-133">2018/9/3</span></span>  | <span data-ttu-id="95c29-134">36.69670857</span><span class="sxs-lookup"><span data-stu-id="95c29-134">36.69670857</span></span>  |
| <span data-ttu-id="95c29-135">2018/9/4</span><span class="sxs-lookup"><span data-stu-id="95c29-135">2018/9/4</span></span>  | <span data-ttu-id="95c29-136">35.74160571</span><span class="sxs-lookup"><span data-stu-id="95c29-136">35.74160571</span></span>  |
| <span data-ttu-id="95c29-137">.....</span><span class="sxs-lookup"><span data-stu-id="95c29-137">.....</span></span>  | <span data-ttu-id="95c29-138">.....</span><span class="sxs-lookup"><span data-stu-id="95c29-138">.....</span></span>  |
| <span data-ttu-id="95c29-139">2018/10/3</span><span class="sxs-lookup"><span data-stu-id="95c29-139">2018/10/3</span></span>  | <span data-ttu-id="95c29-140">34.49893429</span><span class="sxs-lookup"><span data-stu-id="95c29-140">34.49893429</span></span>  |
| <span data-ttu-id="95c29-141">...</span><span class="sxs-lookup"><span data-stu-id="95c29-141">...</span></span>    | <span data-ttu-id="95c29-142">....</span><span class="sxs-lookup"><span data-stu-id="95c29-142">....</span></span>   |

<span data-ttu-id="95c29-143">このファイルは時系列を表します。</span><span class="sxs-lookup"><span data-stu-id="95c29-143">This file represents a time-series.</span></span> <span data-ttu-id="95c29-144">ファイルの各行はデータ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="95c29-144">Each row in the file is a data point.</span></span> <span data-ttu-id="95c29-145">各デー タポイントには、1 日の通話数を表す 2 つの属性 (つまり、`timestamp` と `value`) があります。</span><span class="sxs-lookup"><span data-stu-id="95c29-145">Each data point has two attributes, namely, `timestamp` and `value`, to represent the number of phone calls at each day.</span></span> <span data-ttu-id="95c29-146">通話数は非秘密度に変換されます。</span><span class="sxs-lookup"><span data-stu-id="95c29-146">The number of phone calls is transformed to de-sensitivity.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="95c29-147">クラスを作成してパスを定義する</span><span class="sxs-lookup"><span data-stu-id="95c29-147">Create classes and define paths</span></span>

<span data-ttu-id="95c29-148">次に、入力クラスと予測クラスのデータ構造を定義します。</span><span class="sxs-lookup"><span data-stu-id="95c29-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="95c29-149">プロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="95c29-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="95c29-150">**ソリューション エクスプローラー** で、プロジェクトを右クリックして、 **[追加]、[新しいアイテム]** の順に選びます。</span><span class="sxs-lookup"><span data-stu-id="95c29-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="95c29-151">**[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを *PhoneCallsData.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="95c29-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *PhoneCallsData.cs*.</span></span> <span data-ttu-id="95c29-152">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95c29-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="95c29-153">コード エディターで *PhoneCallsData.cs* ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="95c29-153">The *PhoneCallsData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="95c29-154">次の `using` ステートメントを *PhoneCallsData.cs* の先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="95c29-154">Add the following `using` statement to the top of *PhoneCallsData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="95c29-155">既存のクラス定義を削除し、`PhoneCallsData` と `PhoneCallsPrediction` の 2 つのクラスを含む次のコードを *PhoneCallsData.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="95c29-155">Remove the existing class definition and add the following code, which has two classes `PhoneCallsData` and `PhoneCallsPrediction`, to the *PhoneCallsData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="95c29-156">`PhoneCallsData` は入力データ クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="95c29-156">`PhoneCallsData` specifies an input data class.</span></span> <span data-ttu-id="95c29-157">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 属性は、データセット内のどの列 (列インデックス) を読み込むかを指定します。</span><span class="sxs-lookup"><span data-stu-id="95c29-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="95c29-158">これには、データ ファイル内の同じ属性に対応する `timestamp` と `value` の 2 つの属性があります。</span><span class="sxs-lookup"><span data-stu-id="95c29-158">It has two attributes `timestamp` and `value` that correspond to the same attributes in the data file.</span></span>

    <span data-ttu-id="95c29-159">`PhoneCallsPrediction` では予測データ クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="95c29-159">`PhoneCallsPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="95c29-160">SR-CNN 検出の場合、予測は指定された[検出モード](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode)によって異なります。</span><span class="sxs-lookup"><span data-stu-id="95c29-160">For SR-CNN detector, the prediction depends on the [detect mode](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) specified.</span></span> <span data-ttu-id="95c29-161">このサンプルでは、`AnomalyAndMargin` モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="95c29-161">In this sample, we select the `AnomalyAndMargin` mode.</span></span> <span data-ttu-id="95c29-162">出力には 7 つの列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="95c29-162">The output contains seven columns.</span></span> <span data-ttu-id="95c29-163">ほとんどの場合、`IsAnomaly`、`ExpectedValue`、`UpperBoundary`、`LowerBoundary` の情報で十分です。</span><span class="sxs-lookup"><span data-stu-id="95c29-163">In most cases, `IsAnomaly`, `ExpectedValue`, `UpperBoundary`, and `LowerBoundary` are informative enough.</span></span> <span data-ttu-id="95c29-164">これらを見れば、ポイントが異常であるかどうか、そのポイントの予期される値およびそのポイントの下限/上限領域がわかります。</span><span class="sxs-lookup"><span data-stu-id="95c29-164">They tell you if a point is an anomaly, the expected value of the point and the lower / upper boundary region of the point.</span></span>

5. <span data-ttu-id="95c29-165">`Main` メソッドのすぐ上にある行に次のコードを追加して、データ ファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="95c29-165">Add the following code to the line right above the `Main` method to specify the path to your data file:</span></span>

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="95c29-166">Main で変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="95c29-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="95c29-167">`Main` メソッドの `Console.WriteLine("Hello World!")` の行は、`mlContext` 変数を宣言して初期化する次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="95c29-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="95c29-168">[MLContext クラス](xref:Microsoft.ML.MLContext)は、すべての ML.NET 操作の開始点で、`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="95c29-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="95c29-169">これは Entity Framework における `DBContext` と概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="95c29-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="95c29-170">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="95c29-170">Load the data</span></span>

<span data-ttu-id="95c29-171">ML.NET 内のデータは、[IDataView クラス](xref:Microsoft.ML.IDataView)として表されます。</span><span class="sxs-lookup"><span data-stu-id="95c29-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="95c29-172">`IDataView` は、表形式のデータ (数値とテキスト) を表すための柔軟で効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="95c29-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="95c29-173">データはテキスト ファイルから、または他のソース (SQL データベースやログ ファイルなど) から `IDataView` オブジェクトに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="95c29-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="95c29-174">`Main` メソッドの次の行として次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="95c29-174">Add the following code as the next line of the `Main` method:</span></span>

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="95c29-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) は、データ スキーマを定義し、ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="95c29-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="95c29-176">データ パス変数を取得して、`IDataView` を返します。</span><span class="sxs-lookup"><span data-stu-id="95c29-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="95c29-177">時系列の異常検出</span><span class="sxs-lookup"><span data-stu-id="95c29-177">Time series anomaly detection</span></span>

<span data-ttu-id="95c29-178">時系列の異常検出は、時系列データの異常値 (指定された入力の時系列上で、動作が予期されたものではない点、つまり、"おかしい" 点) を検出するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="95c29-178">Time series anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span> <span data-ttu-id="95c29-179">これらの異常は通常、問題領域の対象のいくつかのイベントを示しています。つまり、ユーザー アカウントに対するサイバー攻撃、停電、サーバー上での RPS のバースト、メモリ リークなどです。</span><span class="sxs-lookup"><span data-stu-id="95c29-179">These anomalies are typically indicative of some events of interest in the problem domain: a cyber-attack on user accounts, power outage, bursting RPS on a server, memory leak, etc.</span></span>

<span data-ttu-id="95c29-180">時系列の異常を検出するには、まずその系列の期間を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95c29-180">To find anomaly on time series, you should first determine the period of the series.</span></span> <span data-ttu-id="95c29-181">その後、時系列を `Y = T + S + R` として複数のコンポーネントに分解できます。ここで、`Y` は元の系列、`T` は傾向コンポーネント、`S` は季節コンポーネント、`R` は系列の残りのコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="95c29-181">Then, the time series can be decomposed into several components as `Y = T + S + R`, where `Y` is the original series, `T` is the trend component, `S` is the seasonal component, and `R` is the residual component of the series.</span></span> <span data-ttu-id="95c29-182">この手順は[分解](https://en.wikipedia.org/wiki/Decomposition_of_time_series)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="95c29-182">This step is called [decomposition](https://en.wikipedia.org/wiki/Decomposition_of_time_series).</span></span> <span data-ttu-id="95c29-183">最後に、異常を見つけるために残りのコンポーネントに対して検出が行われます。</span><span class="sxs-lookup"><span data-stu-id="95c29-183">Finally, detection is performed on the residual component to find the anomalies.</span></span> <span data-ttu-id="95c29-184">ML.NET では、SR-CNN アルゴリズムは、時系列の異常を検出するための Spectral Residual (SR) および Convolutional Neural Network (CNN) に基づく高度な新しいアルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="95c29-184">In ML.NET, The SR-CNN algorithm is an advanced and novel algorithm that is based on Spectral Residual (SR) and Convolutional Neural Network(CNN) to detect anomaly on time-series.</span></span> <span data-ttu-id="95c29-185">このアルゴリズムの詳細については、「[Time-Series Anomaly Detection Service at Microsoft](https://arxiv.org/pdf/1906.03821.pdf)」(Microsoft の時系列異常検出サービス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95c29-185">For more information on this algorithm, see [Time-Series Anomaly Detection Service at Microsoft](https://arxiv.org/pdf/1906.03821.pdf).</span></span>

<span data-ttu-id="95c29-186">このチュートリアルで、2 つの関数を使用してこれらの手順を完了できることがわかります。</span><span class="sxs-lookup"><span data-stu-id="95c29-186">In this tutorial, you will see that these procedures can be completed using two functions.</span></span>

## <a name="detect-period"></a><span data-ttu-id="95c29-187">検出期間</span><span class="sxs-lookup"><span data-stu-id="95c29-187">Detect Period</span></span>

<span data-ttu-id="95c29-188">最初の手順では、`DetectSeasonality` 関数を呼び出して、系列の期間を確認します。</span><span class="sxs-lookup"><span data-stu-id="95c29-188">In the first step, we invoke the `DetectSeasonality` function to determine the period of the series.</span></span>

### <a name="create-the-detectperiod-method"></a><span data-ttu-id="95c29-189">DetectPeriod メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="95c29-189">Create the DetectPeriod method</span></span>

1. <span data-ttu-id="95c29-190">次のコードを使用して、`Main` メソッドのすぐ下に `DetectPeriod` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="95c29-190">Create the `DetectPeriod` method, just below the `Main` method, using the following code:</span></span>

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. <span data-ttu-id="95c29-191">期間を検出するには、<xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="95c29-191">Use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> function to detect period.</span></span> <span data-ttu-id="95c29-192">それを次のコードを使用して `DetectPeriod` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="95c29-192">Add it to the `DetectPeriod` method with the following code:</span></span>

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. <span data-ttu-id="95c29-193">`DetectPeriod` メソッドの次のコード行として以下を追加し、期間の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="95c29-193">Display the period value by adding the following as the next line of code in the `DetectPeriod` method:</span></span>

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. <span data-ttu-id="95c29-194">次の `DetectPeriod` メソッドに対する呼び出しを `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="95c29-194">Add the following call to the `DetectPeriod` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a><span data-ttu-id="95c29-195">期間の検出結果</span><span class="sxs-lookup"><span data-stu-id="95c29-195">Period detection results</span></span>

<span data-ttu-id="95c29-196">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="95c29-196">Run the application.</span></span> <span data-ttu-id="95c29-197">結果は以下のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="95c29-197">Your results should be similar to the following.</span></span>

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a><span data-ttu-id="95c29-198">異常を検出する</span><span class="sxs-lookup"><span data-stu-id="95c29-198">Detect Anomaly</span></span>

<span data-ttu-id="95c29-199">この手順では、<xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> メソッドを使用して異常を見つけます。</span><span class="sxs-lookup"><span data-stu-id="95c29-199">In this step, you use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> method to find anomalies.</span></span>

### <a name="create-the-detectanomaly-method"></a><span data-ttu-id="95c29-200">DetectAnomaly メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="95c29-200">Create the DetectAnomaly method</span></span>

1. <span data-ttu-id="95c29-201">次のコードを使用して、`DetectPeriod` メソッドのすぐ下に `DetectAnomaly` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="95c29-201">Create the `DetectAnomaly` method, just below the `DetectPeriod` method, using the following code:</span></span>

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. <span data-ttu-id="95c29-202">次のコードを使用して、`DetectAnomaly` メソッドに <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> を設定します。</span><span class="sxs-lookup"><span data-stu-id="95c29-202">Set up <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> in the `DetectAnomaly` method with the following code:</span></span>

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. <span data-ttu-id="95c29-203">`DetectAnomaly` メソッドに次のコード行を追加することで、SR-CNN アルゴリズムで異常を検出します。</span><span class="sxs-lookup"><span data-stu-id="95c29-203">Detect anomaly by SR-CNN algorithm by adding the following line of code in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. <span data-ttu-id="95c29-204">次のコードで [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) メソッドを使用して、表示をより簡単にするために出力データ ビューを厳密に型指定された `IEnumerable` に変換します。</span><span class="sxs-lookup"><span data-stu-id="95c29-204">Convert the output data view into a strongly typed `IEnumerable` for easier display using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. <span data-ttu-id="95c29-205">`DetectAnomaly` メソッドの次の行として次のコードを使用して、表示ヘッダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="95c29-205">Create a display header with the following code as the next line in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    <span data-ttu-id="95c29-206">変化点の検出結果には、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="95c29-206">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="95c29-207">`Index` は各点のインデックスです。</span><span class="sxs-lookup"><span data-stu-id="95c29-207">`Index` is the index of each point.</span></span>
    * <span data-ttu-id="95c29-208">`Anomaly` は、各点が異常として検出されたかどうかを示すインジケーターです。</span><span class="sxs-lookup"><span data-stu-id="95c29-208">`Anomaly` is the indicator of whether each point is detected as anomaly.</span></span>
    * <span data-ttu-id="95c29-209">`ExpectedValue` は各点の推定値です。</span><span class="sxs-lookup"><span data-stu-id="95c29-209">`ExpectedValue` is the estimated value of each point.</span></span>
    * <span data-ttu-id="95c29-210">`LowerBoundary` は、各点を異常でないと見なせる最小値です。</span><span class="sxs-lookup"><span data-stu-id="95c29-210">`LowerBoundary` is the lowest value each point can be to be not anomaly.</span></span>
    * <span data-ttu-id="95c29-211">`UpperBoundary` は、各点を異常でないと見なせる最大値です。</span><span class="sxs-lookup"><span data-stu-id="95c29-211">`UpperBoundary` is the highest value each point can be to be not anomaly.</span></span>

6. <span data-ttu-id="95c29-212">次のコードを使用して `predictions` `IEnumerable` を反復処理し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="95c29-212">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. <span data-ttu-id="95c29-213">次の `DetectAnomaly` メソッドに対する呼び出しを `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="95c29-213">Add the following call to the `DetectAnomaly` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a><span data-ttu-id="95c29-214">異常検出の結果</span><span class="sxs-lookup"><span data-stu-id="95c29-214">Anomaly detection results</span></span>

<span data-ttu-id="95c29-215">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="95c29-215">Run the application.</span></span> <span data-ttu-id="95c29-216">結果は以下のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="95c29-216">Your results should be similar to the following.</span></span> <span data-ttu-id="95c29-217">処理中にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95c29-217">During processing, messages are displayed.</span></span> <span data-ttu-id="95c29-218">警告または処理メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="95c29-218">You may see warnings or processing messages.</span></span> <span data-ttu-id="95c29-219">わかりやすくするために、一部のメッセージは次の結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="95c29-219">Some messages have been removed from the following results for clarity.</span></span>

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detected anomaly
...
```

<span data-ttu-id="95c29-220">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="95c29-220">Congratulations!</span></span> <span data-ttu-id="95c29-221">これで、定期的な系列の期間と異常を検出するための機械学習モデルが正常に構築されました。</span><span class="sxs-lookup"><span data-stu-id="95c29-221">You've now successfully built machine learning models for detecting period and anomaly on a periodical series.</span></span>

<span data-ttu-id="95c29-222">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="95c29-222">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

<span data-ttu-id="95c29-223">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="95c29-223">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="95c29-224">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="95c29-224">Load the data</span></span>
> * <span data-ttu-id="95c29-225">時系列データの期間を検出する</span><span class="sxs-lookup"><span data-stu-id="95c29-225">Detect period on the time series data</span></span>
> * <span data-ttu-id="95c29-226">時系列データの異常を検出する</span><span class="sxs-lookup"><span data-stu-id="95c29-226">Detect anomaly on the time series data</span></span>

## <a name="next-steps"></a><span data-ttu-id="95c29-227">次の手順</span><span class="sxs-lookup"><span data-stu-id="95c29-227">Next steps</span></span>

<span data-ttu-id="95c29-228">Machine Learning サンプルの GitHub リポジトリを確認し、Power Consumption Anomaly Detection サンプルを調べてください。</span><span class="sxs-lookup"><span data-stu-id="95c29-228">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="95c29-229">dotnet/machinelearning-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="95c29-229">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
