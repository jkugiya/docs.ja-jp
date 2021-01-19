---
title: Jupyter Notebook を使用する
titleSuffix: .NET for Apache Spark
description: Jupyter Notebook、Jupyter Lab、Visual Studio Code (VS Code) などの対話型環境で .NET for Apache Spark を使用する
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: 9c0e713731b5e2ad742bdd257a99f9029f244363
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536113"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a><span data-ttu-id="4ec88-103">.NET for Apache Spark を Jupyter Notebook で使用する</span><span class="sxs-lookup"><span data-stu-id="4ec88-103">Use .NET for Apache Spark in Jupyter Notebooks</span></span>

<span data-ttu-id="4ec88-104">この記事では、NET Interactive を使用して .NET for Apache Spark ジョブを Jupyter Notebook と Visual Studio Code (VS Code) で対話的に実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-104">In this article, you learn how to run .NET for Apache Spark jobs interactively in Jupyter Notebook and Visual Studio Code (VS Code) with .NET Interactive.</span></span>

## <a name="about-jupyter"></a><span data-ttu-id="4ec88-105">Jupyter について</span><span class="sxs-lookup"><span data-stu-id="4ec88-105">About Jupyter</span></span>

<span data-ttu-id="4ec88-106">[Jupyter](https://jupyter.org/) は、オープンソースのクロスプラットフォーム コンピューティング環境で、アプリケーションのプロトタイプ作成と開発を対話的に行う方法がユーザーに提供されます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-106">[Jupyter](https://jupyter.org/) is an open-source, cross-platform computing environment that provides a way for users to prototype and develop applications interactively.</span></span> <span data-ttu-id="4ec88-107">Jupyter Notebook、Jupyter Lab、VS Code などのさまざまなインターフェイスを介して、Jupyter と対話することができます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-107">You can interact with Jupyter through a wide variety of interfaces such as Jupyter Notebook, Jupyter Lab, and VS Code.</span></span>

<span data-ttu-id="4ec88-108">.NET のコンテキストでは、.NET Core グローバル ツールである [.NET Interactive](https://github.com/dotnet/interactive) によって、Jupyter Notebook などの対話型コンピューティング環境に .NET コード (C# または F#) を記述するためのカーネルが提供されます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-108">In the context of .NET, [.NET Interactive](https://github.com/dotnet/interactive), a .NET Core global tool, provides a kernel for writing .NET code (C#/F#) in interactive computing environments such as Jupyter Notebook.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ec88-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="4ec88-109">Prerequisites</span></span>

- [<span data-ttu-id="4ec88-110">.NET Core 3.1 SDK</span><span class="sxs-lookup"><span data-stu-id="4ec88-110">.NET Core 3.1 SDK</span></span>](../../core/install/index.yml)
- [<span data-ttu-id="4ec88-111">Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec88-111">Apache Spark</span></span>](https://spark.apache.org/downloads.html)
- [<span data-ttu-id="4ec88-112">Apache Spark .NET Worker</span><span class="sxs-lookup"><span data-stu-id="4ec88-112">Apache Spark .NET Worker</span></span>](https://github.com/dotnet/spark/releases)

<span data-ttu-id="4ec88-113">.NET for Apache Spark 環境用に設定する方法の詳細については、[入門チュートリアル](../tutorials/get-started.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ec88-113">See the [getting started tutorial](../tutorials/get-started.md) for more information on setting up your .NET for Apache Spark environment.</span></span>

## <a name="prepare-environment"></a><span data-ttu-id="4ec88-114">環境を準備する</span><span class="sxs-lookup"><span data-stu-id="4ec88-114">Prepare environment</span></span>

<span data-ttu-id="4ec88-115">Jupyter Notebook を使用するには、2 つのことが必要です。</span><span class="sxs-lookup"><span data-stu-id="4ec88-115">To work with Jupyter Notebooks, you'll need two things.</span></span>

1. <span data-ttu-id="4ec88-116">[.NET Interactive グローバル .NET ツール](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)をインストールします</span><span class="sxs-lookup"><span data-stu-id="4ec88-116">Install the [.NET Interactive global .NET tool](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)</span></span>
1. <span data-ttu-id="4ec88-117">`Microsoft.Spark` NuGet パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4ec88-117">Download the `Microsoft.Spark` NuGet package.</span></span>
    1. <span data-ttu-id="4ec88-118">[Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージ ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-118">Navigate to the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package page.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="4ec88-119">既定では、最新バージョンのパッケージがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-119">By default, the latest version of the package is downloaded.</span></span> <span data-ttu-id="4ec88-120">**ダウンロードしたバージョンがご使用の Apache Spark .NET Worker と同じであることを確認します。**</span><span class="sxs-lookup"><span data-stu-id="4ec88-120">**Make sure that the version you download is the same as your Apache Spark .NET Worker.**</span></span>

    1. <span data-ttu-id="4ec88-121">**[情報]** ウィンドウで、 **[パッケージのダウンロード]** を選択してパッケージの最新バージョンをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4ec88-121">In the **Info** pane, select **Download package** to download the latest version of the package.</span></span> <span data-ttu-id="4ec88-122">パッケージの名前は、"*microsoft.spark.[パッケージのバージョン].nupkg*" のようなものになります。</span><span class="sxs-lookup"><span data-stu-id="4ec88-122">The name of the package is similar to  *microsoft.spark.[PACKAGE-VERSION].nupkg*.</span></span>
    1. <span data-ttu-id="4ec88-123">ダウンロードしたパッケージを解凍します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-123">Unzip the downloaded package.</span></span> <span data-ttu-id="4ec88-124">解凍されたディレクトリには *jar* という名前のサブディレクトリが含まれているはずです。</span><span class="sxs-lookup"><span data-stu-id="4ec88-124">The unzipped directory should contain a subdirectory called *jars*.</span></span> <span data-ttu-id="4ec88-125">パスは後で使用するため、メモしておいてください。</span><span class="sxs-lookup"><span data-stu-id="4ec88-125">Take note of the path since it's used at a later time.</span></span>

## <a name="start-net-for-apache-spark"></a><span data-ttu-id="4ec88-126">.NET for Apache Spark を開始する</span><span class="sxs-lookup"><span data-stu-id="4ec88-126">Start .NET for Apache Spark</span></span>

<span data-ttu-id="4ec88-127">次のコマンドを実行して、デバッグ モードで .NET for Apache Spark を開始します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-127">Run the following command to start .NET for Apache Spark in debug mode.</span></span> <span data-ttu-id="4ec88-128">この `spark-submit` コマンドはプロセスを開始し、[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) からの接続を待機します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-128">This `spark-submit` command starts a process and waits for connections from a [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span> <span data-ttu-id="4ec88-129">使用している .NET for Apache Spark に対応するバージョンの `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` へのパスを必ず指定してください。</span><span class="sxs-lookup"><span data-stu-id="4ec88-129">Make sure to provide the path to the `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` for the respective version of .NET for Apache Spark you're using.</span></span>

<span data-ttu-id="4ec88-130">**Ubuntu**</span><span class="sxs-lookup"><span data-stu-id="4ec88-130">**Ubuntu**</span></span>

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

<span data-ttu-id="4ec88-131">**Windows**</span><span class="sxs-lookup"><span data-stu-id="4ec88-131">**Windows**</span></span>

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a><span data-ttu-id="4ec88-132">ノートブックを作成する</span><span class="sxs-lookup"><span data-stu-id="4ec88-132">Create a notebook</span></span>

<span data-ttu-id="4ec88-133">さまざまなインターフェイスを使用して、Jupyter とやり取りできます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-133">You can use different interfaces to interact with Jupyter.</span></span> <span data-ttu-id="4ec88-134">ブラウザーベースのインターフェイスの場合は、Jupyter Notebook または Jupyter Lab を使用します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-134">For a browser-based interface, use Jupyter Notebooks or Jupyter Lab.</span></span> <span data-ttu-id="4ec88-135">ローカル エディターを使用する場合は、VS Code を使用します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-135">For a local editor experience, use VS Code.</span></span>

### <a name="jupyter-notebooks--jupyter-lab"></a><span data-ttu-id="4ec88-136">Jupyter Notebooks と Jupyter Lab</span><span class="sxs-lookup"><span data-stu-id="4ec88-136">Jupyter Notebooks & Jupyter Lab</span></span>

1. <span data-ttu-id="4ec88-137">別のコマンド プロンプトで、次のいずれかのコマンドを使用して Jupyter Notebook または Jupyter Lab を開始します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-137">In another command prompt, start Jupyter Notebook or Jupyter Lab using one of the commands below:</span></span>

    <span data-ttu-id="4ec88-138">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="4ec88-138">**Jupyter Notebook**</span></span>

    ```bash
    jupyter notebook
    ```

    <span data-ttu-id="4ec88-139">**Jupyter Lab**</span><span class="sxs-lookup"><span data-stu-id="4ec88-139">**Jupyter Lab**</span></span>

    ```bash
    jupyter lab
    ```

    <span data-ttu-id="4ec88-140">これらのコマンドにより、Jupyter Notebook または Jupyter Lab インターフェイスを使用したブラウザー ウィンドウが起動されます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-140">These commands launch a browser window with the Jupyter Notebook or Jupyter Lab interface.</span></span>

1. <span data-ttu-id="4ec88-141">ブラウザーで、新しいノートブックを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-141">In the browser, create a new notebook.</span></span>

    <span data-ttu-id="4ec88-142">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="4ec88-142">**Jupyter Notebook**</span></span>

    <span data-ttu-id="4ec88-143">**[新規] > [.NET (C#)]** または **[新規] > [.NET (F#)]** を選択します</span><span class="sxs-lookup"><span data-stu-id="4ec88-143">Select **New > .NET (C#)** or **New > .NET (F#)**</span></span>

    <span data-ttu-id="4ec88-144">**Jupyter Lab**</span><span class="sxs-lookup"><span data-stu-id="4ec88-144">**Jupyter Lab**</span></span>

    <span data-ttu-id="4ec88-145">ランチャー ウィンドウで、 **[.NET (C#)]** または **[.NET (F#)]** を選択します</span><span class="sxs-lookup"><span data-stu-id="4ec88-145">In the Launcher window, select **.NET (C#)** or **.NET (F#)**</span></span>

### <a name="visual-studio-code-preview"></a><span data-ttu-id="4ec88-146">Visual Studio Code (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="4ec88-146">Visual Studio Code (preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4ec88-147">VS Code で Jupyter Notebook を使用するには、次のものをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ec88-147">To use Jupyter Notebooks in VS Code, you have to install:</span></span>
>
>- [<span data-ttu-id="4ec88-148">VS Code Insiders</span><span class="sxs-lookup"><span data-stu-id="4ec88-148">VS Code Insiders</span></span>](https://code.visualstudio.com/insiders/)
>- [<span data-ttu-id="4ec88-149">.NET Interactive Notebooks 拡張機能</span><span class="sxs-lookup"><span data-stu-id="4ec88-149">.NET Interactive Notebooks extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. <span data-ttu-id="4ec88-150">VS Code を開きます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-150">Open VS Code.</span></span>
1. <span data-ttu-id="4ec88-151">**[表示] > [コマンド パレット]** でコマンド パレットを開きます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-151">Open the command palette **View > Command Palette**.</span></span>

    <span data-ttu-id="4ec88-152">コマンド パレットが表示されたら、次のコマンドを入力して、新しい .NET Interactive ノートブックを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-152">When the command palette appears, enter the following command to create a new .NET Interactive notebook:</span></span>

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    <span data-ttu-id="4ec88-153">または、 *.ipynb* 拡張機能を使用して既存の .NET Interactive ノートブックを開く場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-153">Alternatively, if you want to open an existing .NET Interactive notebook with the *.ipynb* extension, use the following command:</span></span>

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a><span data-ttu-id="4ec88-154">Spark セッションを初期化する</span><span class="sxs-lookup"><span data-stu-id="4ec88-154">Initialize a Spark Session</span></span>

1. <span data-ttu-id="4ec88-155">ノートブックが開いたら、`Microsoft.Spark` NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4ec88-155">When the notebook opens, install the `Microsoft.Spark` NuGet package.</span></span> <span data-ttu-id="4ec88-156">インストールするバージョンが .NET Worker と同じであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-156">Make sure the version you install is the same as the .NET Worker.</span></span>

    ```text
    #r "nuget:Microsoft.Spark, 1.0.0"
    ```

1. <span data-ttu-id="4ec88-157">次の using ステートメントをノートブックに追加します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-157">Add the following using statement to the notebook.</span></span>

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. <span data-ttu-id="4ec88-158">ご自分の [SparkSession](xref:Microsoft.Spark.Sql.SparkSession) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="4ec88-158">Initialize your [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span>

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

<span data-ttu-id="4ec88-159">ノートブックは次の図のようなものになります。</span><span class="sxs-lookup"><span data-stu-id="4ec88-159">The notebook should look similar to the one in the following image.</span></span> <span data-ttu-id="4ec88-160">この例では VS Code を使用していますが、Jupyter Notebook と Jupyter Lab でも同じように見えます。</span><span class="sxs-lookup"><span data-stu-id="4ec88-160">This example uses VS Code, but Jupyter Notebook and Jupyter Lab should look about the same.</span></span>

> [!div class="mx-imgBorder"]
<span data-ttu-id="4ec88-161">![.NET for Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span><span class="sxs-lookup"><span data-stu-id="4ec88-161">![.NET for Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span></span>

## <a name="next-steps"></a><span data-ttu-id="4ec88-162">次の手順</span><span class="sxs-lookup"><span data-stu-id="4ec88-162">Next Steps</span></span>

- [<span data-ttu-id="4ec88-163">.NET for Apache Spark の概要</span><span class="sxs-lookup"><span data-stu-id="4ec88-163">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
- [<span data-ttu-id="4ec88-164">.NET for Apache Spark と ML.NET を使用してセンチメントを予測する</span><span class="sxs-lookup"><span data-stu-id="4ec88-164">Predict sentiment using .NET for Apache Spark and ML.NET</span></span>](../tutorials/ml-sentiment-analysis.md)
- <span data-ttu-id="4ec88-165">.NET Interactive の詳細については、[.NET Interactive に関するドキュメント](https://github.com/dotnet/interactive/blob/main/docs/README.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ec88-165">For more information on .NET Interactive, see the [.NET Interactive documentation](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span></span>
