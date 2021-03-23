---
title: .NET for Apache Spark を使用した構造化ストリーミングのチュートリアル
description: このチュートリアルでは、Spark 構造化ストリーミング用の .NET for Apache Spark の使用方法について説明します。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 29f90c43ece1f2655a15f759b473f723e712bda8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873173"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="8d07a-103">チュートリアル: .NET for Apache Spark を使用した構造化ストリーミング</span><span class="sxs-lookup"><span data-stu-id="8d07a-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="8d07a-104">このチュートリアルでは、.NET for Apache Spark を使用して Spark 構造化ストリーミングを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="8d07a-105">Spark 構造化ストリーミングは、リアルタイム データ ストリームを処理するための Apache Spark のサポートです。</span><span class="sxs-lookup"><span data-stu-id="8d07a-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="8d07a-106">ストリーム処理とは、ライブ データの生成中にそれを分析することを意味します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="8d07a-107">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="8d07a-108">.NET for Apache Spark アプリケーションを作成して実行する</span><span class="sxs-lookup"><span data-stu-id="8d07a-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="8d07a-109">netcat を使用してデータ ストリームを作成する</span><span class="sxs-lookup"><span data-stu-id="8d07a-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="8d07a-110">ユーザー定義関数と SparkSQL を使用してストリーミング データを分析する</span><span class="sxs-lookup"><span data-stu-id="8d07a-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d07a-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="8d07a-111">Prerequisites</span></span>

<span data-ttu-id="8d07a-112">これが初めての .NET for Apache Spark アプリケーションである場合は、基本について理解を深めるために、[概要のチュートリアル](get-started.md)に関する記事から始めてください。</span><span class="sxs-lookup"><span data-stu-id="8d07a-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="8d07a-113">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="8d07a-113">Create a console application</span></span>

1. <span data-ttu-id="8d07a-114">コマンド プロンプトで、次のコマンドを実行して、新しいコンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="8d07a-115">`dotnet` コマンドで、種類が `console` の `new` アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="8d07a-116">`-o` パラメーターによって、*mySparkStreamingApp* という名前のディレクトリが作成され、そこにアプリに必要なファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="8d07a-117">`cd mySparkStreamingApp` コマンドで、ディレクトリを、先ほど作成したアプリ ディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="8d07a-118">アプリで .NET for Apache Spark を使用するには、Microsoft.Spark パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8d07a-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="8d07a-119">コンソールで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="8d07a-120">データ ストリームを確立して接続する</span><span class="sxs-lookup"><span data-stu-id="8d07a-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="8d07a-121">ストリーム処理をテストする一般的な方法の 1 つとして、**netcat** を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="8d07a-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="8d07a-122">netcat (*nc* とも呼ばれます) を使用すると、ネットワーク接続に対する読み取りと書き込みを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="8d07a-123">netcat とのネットワーク接続を確立するには、ターミナル ウィンドウを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="8d07a-124">netcat を使用してデータ ストリームを作成する</span><span class="sxs-lookup"><span data-stu-id="8d07a-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="8d07a-125">[netcat をダウンロードします](https://sourceforge.net/projects/nc110/files/)。</span><span class="sxs-lookup"><span data-stu-id="8d07a-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="8d07a-126">次に、zip ダウンロードからファイルを抽出し、抽出したディレクトリを "PATH" 環境変数に追加します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="8d07a-127">新しい接続を開始するには、新しいコンソールを開き、localhost にポート 9999 で接続する次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="8d07a-128">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="8d07a-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="8d07a-129">Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="8d07a-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="8d07a-130">Spark プログラムでは、このコマンド プロンプトに入力する入力がリッスンされます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="8d07a-131">SparkSession を作成する</span><span class="sxs-lookup"><span data-stu-id="8d07a-131">Create a SparkSession</span></span>

1. <span data-ttu-id="8d07a-132">次の追加の `using` ステートメントを、*mySparkStreamingApp* の *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="8d07a-133">新しい `SparkSession` を作成するために、次のコードを `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="8d07a-134">Spark セッションは、Dataset API と DataFrame API を使用して Spark をプログラミングするためのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="8d07a-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="8d07a-135">上で作成した *spark* オブジェクトを呼び出すことで、プログラムの至るところで Spark と DataFrame の機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="8d07a-136">ReadStream () を使用してストリームに接続する</span><span class="sxs-lookup"><span data-stu-id="8d07a-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="8d07a-137">`ReadStream()` メソッドによって、ストリーミング データを `DataFrame` として読み取るために使用できる `DataStreamReader` が返されます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="8d07a-138">ストリーミング データを予期する場所を Spark アプリに通知する、ホストとポートの情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8d07a-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="8d07a-139">ユーザー定義関数を登録する</span><span class="sxs-lookup"><span data-stu-id="8d07a-139">Register a user-defined function</span></span>

<span data-ttu-id="8d07a-140">Spark アプリケーションで UDF ("*ユーザー定義関数*") を使用して、データの計算と分析を実行できます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="8d07a-141">`udfArray` という名前の UDF を登録するために、次のコードを `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="8d07a-142">この UDF によって、netcat ターミナルから受け取った各文字列を処理して、元の文字列 (*str* に含まれています) と、その後ろに元の文字列の長さに連結された元の文字列が続く配列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="8d07a-143">たとえば、netcat ターミナルに *Hello world* と入力すると、次のような配列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="8d07a-144">array\[0] = Hello world</span><span class="sxs-lookup"><span data-stu-id="8d07a-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="8d07a-145">array\[1] = Hello world 11</span><span class="sxs-lookup"><span data-stu-id="8d07a-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="8d07a-146">SparkSQL を使用する</span><span class="sxs-lookup"><span data-stu-id="8d07a-146">Use SparkSQL</span></span>

<span data-ttu-id="8d07a-147">SparkSQL を使用して、DataFrame に格納されているデータに対してさまざまな関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="8d07a-148">DataFrame の各行に対して 1 つの UDF を適用するために、複数の UDF と SparkSQL を組み合わせるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="8d07a-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="8d07a-149">このコード スニペットでは、*udfArray* を DataFrame 内の各値に適用します。値は、netcat ターミナルから読み取られた各文字列を表します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="8d07a-150">SparkSQL メソッド <xref:Microsoft.Spark.Sql.Functions.Explode%2A> を適用して、配列の各エントリを各行に配置します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="8d07a-151">最後に、<xref:Microsoft.Spark.Sql.DataFrame.Select%2A> を使用して、生成された列を新しい DataFrame *arrayDF* に配置します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="8d07a-152">ストリームを表示する</span><span class="sxs-lookup"><span data-stu-id="8d07a-152">Display your stream</span></span>

<span data-ttu-id="8d07a-153"><xref:Microsoft.Spark.Sql.DataFrame.WriteStream> を使用して、出力の特性を確立します (コンソールへの結果の出力や、最新の出力のみの表示など)。</span><span class="sxs-lookup"><span data-stu-id="8d07a-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="8d07a-154">コードを実行する</span><span class="sxs-lookup"><span data-stu-id="8d07a-154">Run your code</span></span>

<span data-ttu-id="8d07a-155">Spark の構造化ストリーミングでは、一連の小さな **バッチ** を通してデータが処理されます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="8d07a-156">プログラムを実行すると、netcat 接続を確立するコマンド プロンプトで入力を開始できます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="8d07a-157">そのコマンド プロンプトでデータを入力して Enter キーを押すたびに、Spark によって入力がバッチとみなされ、UDF が実行されます。</span><span class="sxs-lookup"><span data-stu-id="8d07a-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="8d07a-158">spark-submit を使用してアプリを実行する</span><span class="sxs-lookup"><span data-stu-id="8d07a-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="8d07a-159">新しい netcat セッションを開始した後、新しいターミナルを開き、次のコマンドのように `spark-submit` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8d07a-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="8d07a-160">必ず上記のコマンドを実際の Microsoft Spark jar ファイルへのパスに更新してください。</span><span class="sxs-lookup"><span data-stu-id="8d07a-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="8d07a-161">上記のコマンドでは、netcat サーバーが localhost ポート 9999 で実行されていることも前提としています。</span><span class="sxs-lookup"><span data-stu-id="8d07a-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="8d07a-162">コードの入手</span><span class="sxs-lookup"><span data-stu-id="8d07a-162">Get the code</span></span>

<span data-ttu-id="8d07a-163">このチュートリアルでは [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) の例を使用していますが、GitHub には、他に次の 3 つの完全なストリームの処理例があります。</span><span class="sxs-lookup"><span data-stu-id="8d07a-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="8d07a-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): 任意のソースからストリーミングされたデータのワード カウント</span><span class="sxs-lookup"><span data-stu-id="8d07a-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="8d07a-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): ウィンドウ ロジックを使用したデータのワード カウント</span><span class="sxs-lookup"><span data-stu-id="8d07a-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="8d07a-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): Kafka からストリーミングされたデータのワード カウント</span><span class="sxs-lookup"><span data-stu-id="8d07a-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="8d07a-167">次のステップ</span><span class="sxs-lookup"><span data-stu-id="8d07a-167">Next steps</span></span>

<span data-ttu-id="8d07a-168">次の記事に進んで、.NET for Apache Spark アプリケーションを Databricks にデプロイする方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="8d07a-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8d07a-169">チュートリアル: .NET for Apache Spark アプリケーションを Databricks にデプロイする</span><span class="sxs-lookup"><span data-stu-id="8d07a-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
