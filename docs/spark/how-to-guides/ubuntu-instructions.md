---
title: Ubuntu で .NET for Apache Spark アプリケーションをビルドする
description: Ubuntu で .NET for Apache Spark アプリケーションをビルドする方法を学習する
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: ae5e0e24ef53b74bd34a2c0100c30a375d8bd71f
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103921"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="9cef2-103">Ubuntu で .NET for Apache Spark アプリケーションをビルドする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="9cef2-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="9cef2-104">この記事では、Ubuntu で .NET for Apache Spark アプリケーションをビルドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9cef2-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="9cef2-105">Prerequisites</span></span>

<span data-ttu-id="9cef2-106">以下の必須コンポーネントがすべて揃っている場合は、「[ビルド](#build)」の手順に進んでください。</span><span class="sxs-lookup"><span data-stu-id="9cef2-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="9cef2-107">**[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet/3.1)** をダウンロードしてインストールする - SDK をインストールすると、`dotnet` ツールチェーンがパスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9cef2-107">Download and install **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="9cef2-108">.NET Core 2.1、2.2、および 3.1 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9cef2-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="9cef2-109">**[OpenJDK 8](https://openjdk.java.net/install/)** をインストールする。</span><span class="sxs-lookup"><span data-stu-id="9cef2-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span>

   - <span data-ttu-id="9cef2-110">次のコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cef2-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="9cef2-111">コマンド ラインから `java` を実行できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-111">Verify you are able to run `java` from your command-line.</span></span>

      <span data-ttu-id="9cef2-112">java -version の出力サンプル:</span><span class="sxs-lookup"><span data-stu-id="9cef2-112">Sample java -version output:</span></span>

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="9cef2-113">既に複数の OpenJDK バージョンをインストールしていて、OpenJDK 8 を選択したい場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="9cef2-114">**[Apache Maven 3.6.0 以降](https://maven.apache.org/download.cgi)** をインストールする。</span><span class="sxs-lookup"><span data-stu-id="9cef2-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="9cef2-115">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-115">Run the following command:</span></span>

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       <span data-ttu-id="9cef2-116">これらの環境変数は、ターミナルを閉じると失われることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9cef2-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="9cef2-117">変更を永続させたい場合は、`~/.bashrc` ファイルに `export` の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="9cef2-118">コマンド ラインから `mvn` を実行できることを確認します</span><span class="sxs-lookup"><span data-stu-id="9cef2-118">Verify you are able to run `mvn` from your command-line</span></span>

       <span data-ttu-id="9cef2-119">mvn -version の出力サンプル:</span><span class="sxs-lookup"><span data-stu-id="9cef2-119">Sample mvn -version output:</span></span>

       ```output
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="9cef2-120">**[Apache Spark 2.3 以降](https://spark.apache.org/downloads.html)** をインストールする。</span><span class="sxs-lookup"><span data-stu-id="9cef2-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="9cef2-121">[Apache Spark 2.3 以降](https://spark.apache.org/downloads.html)をダウンロードし、ローカル フォルダーに抽出します (`~/bin/spark-3.0.1-bin-hadoop2.7` など)。</span><span class="sxs-lookup"><span data-stu-id="9cef2-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-3.0.1-bin-hadoop2.7`).</span></span> <span data-ttu-id="9cef2-122">(サポートされている Spark のバージョンは 2.3.\*、2.4.0、2.4.1、2.4.3、2.4.4、2.4.5、2.4.6、2.4.7、3.0.0、3.0.1 です)</span><span class="sxs-lookup"><span data-stu-id="9cef2-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 and 3.0.1)</span></span>

   ```bash
   tar -xvzf /path/to/spark-3.0.1-bin-hadoop2.7.tgz -C ~/bin/spark-3.0.1-bin-hadoop2.7
   ```

   * <span data-ttu-id="9cef2-123">必要な[環境変数](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (`~/bin/spark-3.0.1-bin-hadoop2.7/` など) と `PATH` (`$SPARK_HOME/bin:$PATH` など) を追加します</span><span class="sxs-lookup"><span data-stu-id="9cef2-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-3.0.1-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-3.0.1-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      <span data-ttu-id="9cef2-124">これらの環境変数は、ターミナルを閉じると失われることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9cef2-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="9cef2-125">変更を永続させたい場合は、`~/.bashrc` ファイルに `export` の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="9cef2-126">コマンド ラインから `spark-shell` を実行できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="9cef2-127">コンソール出力の例:</span><span class="sxs-lookup"><span data-stu-id="9cef2-127">Sample console output:</span></span>

      ```
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

<span data-ttu-id="9cef2-128">次のセクションに進む前に、コマンド ラインから `dotnet`、`java`、`mvn`、`spark-shell` を実行できることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9cef2-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="9cef2-129">もっと良い方法があると思いますか。</span><span class="sxs-lookup"><span data-stu-id="9cef2-129">Feel there is a better way?</span></span> <span data-ttu-id="9cef2-130">[イシューを作成](https://github.com/dotnet/spark/issues)して、お気軽にご投稿ください。</span><span class="sxs-lookup"><span data-stu-id="9cef2-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="9cef2-131">Build</span><span class="sxs-lookup"><span data-stu-id="9cef2-131">Build</span></span>

<span data-ttu-id="9cef2-132">このガイドの残りの部分では、.NET for Apache Spark リポジトリをご自分のコンピューターにクローンしておく必要があります (`~/dotnet.spark/` など)。</span><span class="sxs-lookup"><span data-stu-id="9cef2-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="9cef2-133">.NET for Spark の Scala 拡張機能レイヤーをビルドする</span><span class="sxs-lookup"><span data-stu-id="9cef2-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="9cef2-134">.NET アプリケーションを送信したとき、.NET for Apache Spark には、要求の処理方法を Apache Spark に伝える、Scala で記述された必要なロジックが含まれています (たとえば、新しい Spark セッションを作成する要求や、.NET 側から JVM 側にデータを転送する要求など)。</span><span class="sxs-lookup"><span data-stu-id="9cef2-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="9cef2-135">このロジックは、[.NET for Apache Spark の Scala ソース コード](https://github.com/dotnet/spark/tree/master/src/scala)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="9cef2-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="9cef2-136">次の手順は、.NET for Apache Spark の Scala 拡張機能レイヤーをビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="9cef2-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package
```

<span data-ttu-id="9cef2-137">サポートされている Spark バージョンに対して作成された JAR を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cef2-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2-3\target\microsoft-spark-2-3_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-2-4\target\microsoft-spark-2-4_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-3-0\target\microsoft-spark-3-0_2.12-<spark-dotnet-version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="9cef2-138">.NET Core CLI を使用して .NET サンプル アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="9cef2-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="9cef2-139">このセクションでは、.NET for Apache Spark の[サンプル アプリケーション](https://github.com/dotnet/spark/tree/master/examples)をビルドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="9cef2-140">これらの手順は、あらゆる .NET for Spark アプリケーションのビルド プロセス全体を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9cef2-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="9cef2-141">ワーカーをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9cef2-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="9cef2-142">コンソール出力の例:</span><span class="sxs-lookup"><span data-stu-id="9cef2-142">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.1/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/
   ```

2. <span data-ttu-id="9cef2-143">サンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9cef2-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="9cef2-144">コンソール出力の例:</span><span class="sxs-lookup"><span data-stu-id="9cef2-144">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.1/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="9cef2-145">.NET for Spark のサンプル アプリケーションを実行する</span><span class="sxs-lookup"><span data-stu-id="9cef2-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="9cef2-146">サンプルをビルドしたら、`spark-submit` を使用して .NET Core アプリを送信できます。</span><span class="sxs-lookup"><span data-stu-id="9cef2-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="9cef2-147">[必須コンポーネント](#prerequisites)のセクションに従っていることと、Apache Spark がインストール済みであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9cef2-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="9cef2-148">`DOTNET_WORKER_DIR` または `PATH` 環境変数を設定して、`Microsoft.Spark.Worker` バイナリが生成されたパスが含まれるようにします (`~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish` など)。</span><span class="sxs-lookup"><span data-stu-id="9cef2-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="9cef2-149">ターミナルを開き、アプリのバイナリが生成されたディレクトリに移動します (`~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish` など)。</span><span class="sxs-lookup"><span data-stu-id="9cef2-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="9cef2-150">次の基本構造に従ってアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="9cef2-151">実行できるいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9cef2-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="9cef2-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="9cef2-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="9cef2-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="9cef2-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="9cef2-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (Maven アクセス可能)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="9cef2-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="9cef2-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jar 提供)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="9cef2-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
