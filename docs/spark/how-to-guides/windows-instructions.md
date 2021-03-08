---
title: Windows で .NET for Apache Spark アプリケーションをビルドする
description: Windows で .NET for Apache Spark アプリケーションをビルドする方法について学習します。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: d9e1721fbb13d963c3a690ded3e26885f268bc72
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106853"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="b098c-103">Windows で .NET for Apache Spark アプリケーションをビルドする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="b098c-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="b098c-104">この記事では、Windows で .NET for Apache Spark アプリケーションをビルドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b098c-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b098c-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b098c-105">Prerequisites</span></span>

<span data-ttu-id="b098c-106">以下の必須コンポーネントがすべて揃っている場合は、「[ビルド](#build)」の手順に進んでください。</span><span class="sxs-lookup"><span data-stu-id="b098c-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="b098c-107">**[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet/3.1)** をダウンロードしてインストールする - SDK をインストールすると、`dotnet` ツールチェーンがパスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b098c-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet/3.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="b098c-108">.NET Core 2.1、2.2、および 3.1 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b098c-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="b098c-109">**[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (バージョン 16.3 以降) をインストールする。</span><span class="sxs-lookup"><span data-stu-id="b098c-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="b098c-110">コミュニティ バージョンは完全に無料です。</span><span class="sxs-lookup"><span data-stu-id="b098c-110">The Community version is completely free.</span></span> <span data-ttu-id="b098c-111">インストールを構成するときは、最小でも次のコンポーネントを含めてください。</span><span class="sxs-lookup"><span data-stu-id="b098c-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="b098c-112">.NET デスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="b098c-112">.NET desktop development</span></span>
       * <span data-ttu-id="b098c-113">すべての必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b098c-113">All Required Components</span></span>
         * <span data-ttu-id="b098c-114">.NET Framework 4.6.1 開発ツール</span><span class="sxs-lookup"><span data-stu-id="b098c-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="b098c-115">.NET Core クロスプラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="b098c-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="b098c-116">すべての必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b098c-116">All Required Components</span></span>
  3. <span data-ttu-id="b098c-117">**[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** をインストールする。</span><span class="sxs-lookup"><span data-stu-id="b098c-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span>
     - <span data-ttu-id="b098c-118">ご使用のオペレーティング システムに適したバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="b098c-118">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="b098c-119">たとえば、Windows x64 コンピューターには *jdk-8u201-windows-x64.exe* を選択します。</span><span class="sxs-lookup"><span data-stu-id="b098c-119">For example, *jdk-8u201-windows-x64.exe* for Windows x64 machine.</span></span>
     - <span data-ttu-id="b098c-120">インストーラーを使ってインストールし、コマンド ラインから `java` を実行できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b098c-120">Install using the installer and verify you are able to run `java` from your command line.</span></span>
  4. <span data-ttu-id="b098c-121">**[Apache Maven 3.6.0 以降](https://maven.apache.org/download.cgi)** をインストールする。</span><span class="sxs-lookup"><span data-stu-id="b098c-121">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="b098c-122">[Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b098c-122">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span></span>
     - <span data-ttu-id="b098c-123">ローカル ディレクトリに抽出します。</span><span class="sxs-lookup"><span data-stu-id="b098c-123">Extract to a local directory.</span></span> <span data-ttu-id="b098c-124">たとえば、\*C:\bin\apache-maven-3.6.0\* です。</span><span class="sxs-lookup"><span data-stu-id="b098c-124">For example, \*C:\bin\apache-maven-3.6.0\*.</span></span>
     - <span data-ttu-id="b098c-125">Apache Maven をご自分の [PATH 環境変数](https://www.java.com/en/download/help/path.xml)に追加します。</span><span class="sxs-lookup"><span data-stu-id="b098c-125">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="b098c-126">たとえば、*C:\bin\apache-maven-3.6.0\bin* です。</span><span class="sxs-lookup"><span data-stu-id="b098c-126">For example, *C:\bin\apache-maven-3.6.0\bin*.</span></span>
     - <span data-ttu-id="b098c-127">コマンド ラインから `mvn` を実行できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b098c-127">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="b098c-128">**[Apache Spark 2.3 以降](https://spark.apache.org/downloads.html)** をインストールする。</span><span class="sxs-lookup"><span data-stu-id="b098c-128">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="b098c-129">[Apache Spark 2.3+](https://spark.apache.org/downloads.html) をダウンロードし、[7-zip](https://www.7-zip.org/) を利用してローカル フォルダー (たとえば、*C:\bin\spark-3.0.1-bin-hadoop2.7\*) に抽出します。(サポートされている Spark のバージョンは 2.3.* 、2.4.0、2.4.1、2.4.3、2.4.4、2.4.5、2.4.6、2.4.7、3.0.0、3.0.1 です)</span><span class="sxs-lookup"><span data-stu-id="b098c-129">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (for example, *C:\bin\spark-3.0.1-bin-hadoop2.7\*) using [7-zip](https://www.7-zip.org/). (The supported spark versions are 2.3.*, 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 and 3.0.1)</span></span>
     - <span data-ttu-id="b098c-130">[新しい環境変数](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` を追加します。</span><span class="sxs-lookup"><span data-stu-id="b098c-130">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span></span> <span data-ttu-id="b098c-131">たとえば、\*C:\bin\spark-3.0.1-bin-hadoop2.7\* です。</span><span class="sxs-lookup"><span data-stu-id="b098c-131">For example, \*C:\bin\spark-3.0.1-bin-hadoop2.7\*.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-3.0.1-bin-hadoop2.7\
       ```

     - <span data-ttu-id="b098c-132">Apache Spark をご自分の [PATH 環境変数](https://www.java.com/en/download/help/path.xml)に追加します。</span><span class="sxs-lookup"><span data-stu-id="b098c-132">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="b098c-133">たとえば、*C:\bin\spark-3.0.1-bin-hadoop2.7\bin* です。</span><span class="sxs-lookup"><span data-stu-id="b098c-133">For example, *C:\bin\spark-3.0.1-bin-hadoop2.7\bin*.</span></span>

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - <span data-ttu-id="b098c-134">コマンド ラインから `spark-shell` を実行できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b098c-134">Verify you are able to run `spark-shell` from your command-line.</span></span>
        <span data-ttu-id="b098c-135">コンソール出力の例:</span><span class="sxs-lookup"><span data-stu-id="b098c-135">Sample console output:</span></span>

        ```output
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 3.0.1
              /_/

        Using Scala version 2.12.10 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. <span data-ttu-id="b098c-136">**[WinUtils](https://github.com/steveloughran/winutils)** をインストールする。</span><span class="sxs-lookup"><span data-stu-id="b098c-136">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="b098c-137">[WinUtils リポジトリ](https://github.com/steveloughran/winutils)から `winutils.exe` バイナリをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b098c-137">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="b098c-138">Spark ディストリビューションをコンパイルした Hadoop のバージョンを選択してください。</span><span class="sxs-lookup"><span data-stu-id="b098c-138">You should select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="b098c-139">たとえば、Spark 3.0.1 には hadoop-2.7.1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="b098c-139">For exammple, use hadoop-2.7.1 for Spark 3.0.1.</span></span>
     - <span data-ttu-id="b098c-140">`winutils.exe` バイナリを任意のディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="b098c-140">Save `winutils.exe` binary to a directory of your choice.</span></span> <span data-ttu-id="b098c-141">たとえば、*C:\hadoop\bin* です。</span><span class="sxs-lookup"><span data-stu-id="b098c-141">For example, *C:\hadoop\bin*.</span></span>
     - <span data-ttu-id="b098c-142">winutils.exe があるディレクトリを示すように `HADOOP_HOME` を設定します (bin は含めない)。</span><span class="sxs-lookup"><span data-stu-id="b098c-142">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="b098c-143">たとえば、コマンド ラインで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="b098c-143">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="b098c-144">`%HADOOP_HOME%\bin` が含まれるように PATH 環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="b098c-144">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="b098c-145">たとえば、コマンド ラインで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="b098c-145">For instance, using command line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="b098c-146">次のセクションに進む前に、コマンド ラインから `dotnet`、`java`、`mvn`、`spark-shell` を実行できることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b098c-146">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span> <span data-ttu-id="b098c-147">もっと良い方法があると思いますか。</span><span class="sxs-lookup"><span data-stu-id="b098c-147">Feel there is a better way?</span></span> <span data-ttu-id="b098c-148">[イシューを作成](https://github.com/dotnet/spark/issues)して、お気軽にご投稿ください。</span><span class="sxs-lookup"><span data-stu-id="b098c-148">[Open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="b098c-149">環境変数が更新された場合は、コマンド ラインの新しいインスタンスが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b098c-149">A new instance of the command line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="b098c-150">ビルド</span><span class="sxs-lookup"><span data-stu-id="b098c-150">Build</span></span>

<span data-ttu-id="b098c-151">このガイドの残りの部分では、.NET for Apache Spark リポジトリをご自分のコンピューターにクローンしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b098c-151">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="b098c-152">任意の場所にリポジトリをクローンすることができます。</span><span class="sxs-lookup"><span data-stu-id="b098c-152">You can choose any location for the cloned repository.</span></span> <span data-ttu-id="b098c-153">たとえば、\*C:\github\dotnet-spark\* です。</span><span class="sxs-lookup"><span data-stu-id="b098c-153">For example, \*C:\github\dotnet-spark\*.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="b098c-154">.NET for Apache Spark の Scala 拡張機能レイヤーをビルドする</span><span class="sxs-lookup"><span data-stu-id="b098c-154">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="b098c-155">.NET アプリケーションを送信したとき、.NET for Apache Spark には、要求の処理方法を Apache Spark に伝える、Scala で記述された必要なロジックが含まれています (たとえば、新しい Spark セッションを作成する要求や、.NET 側から JVM 側にデータを転送する要求など)。</span><span class="sxs-lookup"><span data-stu-id="b098c-155">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (for example, request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="b098c-156">このロジックは、[.NET for Spark の Scala ソース コード](https://github.com/dotnet/spark/tree/master/src/scala)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b098c-156">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="b098c-157">.NET Framework、.NET Core のどちらを使用しているかにかかわらず、.NET for Apache Spark の Scala 拡張機能レイヤーをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b098c-157">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package
```

<span data-ttu-id="b098c-158">サポートされている Spark バージョンに対して作成された JAR を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b098c-158">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2-3\target\microsoft-spark-2-3_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-2-4\target\microsoft-spark-2-4_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-3-0\target\microsoft-spark-3-0_2.12-<spark-dotnet-version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="b098c-159">.NET for Spark のサンプル アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="b098c-159">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="b098c-160">このセクションでは、.NET for Apache Spark の[サンプル アプリケーション](https://github.com/dotnet/spark/tree/master/examples)をビルドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b098c-160">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="b098c-161">これらの手順は、あらゆる .NET for Spark アプリケーションのビルド プロセス全体を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b098c-161">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="b098c-162">.NET Framework 用に Visual Studio を使用する</span><span class="sxs-lookup"><span data-stu-id="b098c-162">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="b098c-163">Visual Studio で `src\csharp\Microsoft.Spark.sln` を開き、`examples` フォルダーの下に `Microsoft.Spark.CSharp.Examples` プロジェクトをビルドします (その後、これによって .NET バインドのプロジェクトもビルドされます)。</span><span class="sxs-lookup"><span data-stu-id="b098c-163">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="b098c-164">必要に応じて、`Microsoft.Spark.Examples` プロジェクトに独自のコードを記述できます (この例の "input_file.json" は、データフレームの作成に使用するデータが含まれている json ファイルです)。</span><span class="sxs-lookup"><span data-stu-id="b098c-164">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     <span data-ttu-id="b098c-165">ビルドが成功すると、出力ディレクトリに作成された適切なバイナリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b098c-165">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>
     <span data-ttu-id="b098c-166">コンソール出力の例:</span><span class="sxs-lookup"><span data-stu-id="b098c-166">Sample console output:</span></span>

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="b098c-167">.NET Core 用に .NET Core CLI を使用する</span><span class="sxs-lookup"><span data-stu-id="b098c-167">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="b098c-168">現在、Spark .NET の .NET Core ビルドを自動化する作業に取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="b098c-168">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="b098c-169">それまでは、いくつかの手順を手動で実行していただくようお願いいたします。</span><span class="sxs-lookup"><span data-stu-id="b098c-169">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="b098c-170">ワーカーをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b098c-170">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp3.1 -r win-x64
      ```

      <span data-ttu-id="b098c-171">コンソール出力の例:</span><span class="sxs-lookup"><span data-stu-id="b098c-171">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp3.1 -r win-x64
      Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.1\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish\
      ```

  2. <span data-ttu-id="b098c-172">サンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b098c-172">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp3.1 -r win-x64
      ```

      <span data-ttu-id="b098c-173">コンソール出力の例:</span><span class="sxs-lookup"><span data-stu-id="b098c-173">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp3.1 -r win-x64
      Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.1\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="b098c-174">.NET for Spark のサンプル アプリケーションを実行する</span><span class="sxs-lookup"><span data-stu-id="b098c-174">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="b098c-175">サンプルをビルドしたら、その実行には、.NET Framework、.NET Core のどちらを対象としているかにかかわらず `spark-submit` を使用します。</span><span class="sxs-lookup"><span data-stu-id="b098c-175">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="b098c-176">[必須コンポーネント](#prerequisites)のセクションに従っていることと、Apache Spark がインストール済みであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b098c-176">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="b098c-177">`DOTNET_WORKER_DIR` または `PATH` 環境変数を設定し、`Microsoft.Spark.Worker` バイナリが生成されているパスを含めます (たとえば、.NET Framework には *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* を、.NET Core には *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish* を指定します)。</span><span class="sxs-lookup"><span data-stu-id="b098c-177">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish* for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish
      ```
  
  2. <span data-ttu-id="b098c-178">PowerShell を起動し、アプリ バイナリが生成されているディレクトリに移動します (たとえば、.NET Framework の場合、*C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* に、.NET Core の場合、*C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish* に移動します)。</span><span class="sxs-lookup"><span data-stu-id="b098c-178">Open PowerShell and go to the directory where your app binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish* for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish
      ```

  3. <span data-ttu-id="b098c-179">次の基本構造に従ってアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b098c-179">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="b098c-180">実行できるいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b098c-180">Here are some examples you can run:</span></span>

     - <span data-ttu-id="b098c-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="b098c-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="b098c-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="b098c-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="b098c-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (Maven アクセス可能)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="b098c-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="b098c-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jar 提供)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="b098c-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
