---
title: .NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする
description: .NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする方法を説明します。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a0904b5b692e1c32ba12a685f2c3a3f7d86c2c58
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874057"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="620ad-103">.NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする</span><span class="sxs-lookup"><span data-stu-id="620ad-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="620ad-104">このチュートリアルでは、.NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="620ad-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="620ad-105">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) は、AWS でのビッグ データ フレームワークの実行を簡略化する、マネージド クラスター プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="620ad-105">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

<span data-ttu-id="620ad-106">このチュートリアルでは、以下の内容を学習します。</span><span class="sxs-lookup"><span data-stu-id="620ad-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="620ad-107">Microsoft.Spark.Worker を準備する</span><span class="sxs-lookup"><span data-stu-id="620ad-107">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="620ad-108">Spark .NET アプリを発行する</span><span class="sxs-lookup"><span data-stu-id="620ad-108">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="620ad-109">アプリを Amazon EMR Spark にデプロイする</span><span class="sxs-lookup"><span data-stu-id="620ad-109">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="620ad-110">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="620ad-110">Run your app</span></span>

> [!Note]
> <span data-ttu-id="620ad-111">AWS EMR Spark は Linux ベースです。</span><span class="sxs-lookup"><span data-stu-id="620ad-111">AWS EMR Spark is Linux-based.</span></span> <span data-ttu-id="620ad-112">そのため、AWS EMR Spark へのアプリのデプロイに関心がある場合は、アプリが .NET Standard と互換性があることと、アプリのコンパイルに .NET Core コンパイラを使用していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="620ad-112">Therefore, if you are interested in deploying your app to AWS EMR Spark, make sure your app is .NET Standard compatible and that you use .NET Core compiler to compile your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="620ad-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="620ad-113">Prerequisites</span></span>

<span data-ttu-id="620ad-114">開始する前に、以下を行います。</span><span class="sxs-lookup"><span data-stu-id="620ad-114">Before you start, do the following:</span></span>

* <span data-ttu-id="620ad-115">[AWS CLI](https://aws.amazon.com/cli/) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="620ad-115">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="620ad-116">[install-worker.sh](https://github.com/dotnet/spark/blob/main/deployment/install-worker.sh) をお使いのローカル コンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="620ad-116">Download [install-worker.sh](https://github.com/dotnet/spark/blob/main/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="620ad-117">これは、後で .NET for Apache Spark の依存ファイルを Spark クラスターのワーカー ノードにコピーするために使用するヘルパー スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="620ad-117">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="620ad-118">ワーカーの依存関係を準備する</span><span class="sxs-lookup"><span data-stu-id="620ad-118">Prepare worker dependencies</span></span>

<span data-ttu-id="620ad-119">**Microsoft.Spark.Worker** は、Spark クラスターの個々のワーカー ノードに存在するバックエンド コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="620ad-119">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="620ad-120">C# UDF (ユーザー定義関数) を実行する場合、.NET CLR を起動して UDF を実行する方法が Spark で認識されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="620ad-120">When you want to execute a C# UDF (User-Defined Function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="620ad-121">**Microsoft.Spark.Worker** により、この機能を有効にするクラスのコレクションが Spark に提供されます。</span><span class="sxs-lookup"><span data-stu-id="620ad-121">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="620ad-122">お使いのクラスターにデプロイされる [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp リリースを選択します。</span><span class="sxs-lookup"><span data-stu-id="620ad-122">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="620ad-123">たとえば、`netcoreapp3.1` を使用する `.NET for Apache Spark v1.0.0` が必要な場合は、[Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="620ad-123">For example, if you want `.NET for Apache Spark v1.0.0` using `netcoreapp3.1`, you'd download [Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span>

2. <span data-ttu-id="620ad-124">クラスターからアクセスできる分散ファイル システム (S3 など) に、`Microsoft.Spark.Worker.<release>.tar.gz` と [install-worker.sh](https://github.com/dotnet/spark/blob/main/deployment/install-worker.sh) をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="620ad-124">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/main/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="620ad-125">.NET for Apache Spark アプリを準備する</span><span class="sxs-lookup"><span data-stu-id="620ad-125">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="620ad-126">[入門](get-started.md)チュートリアルに従ってアプリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="620ad-126">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="620ad-127">Spark .NET アプリを自己完結型として発行します。</span><span class="sxs-lookup"><span data-stu-id="620ad-127">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="620ad-128">Linux で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="620ad-128">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="620ad-129">発行されたファイル用に `<your app>.zip` を生成します。</span><span class="sxs-lookup"><span data-stu-id="620ad-129">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="620ad-130">`zip` を使用して Linux で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="620ad-130">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="620ad-131">クラスターからアクセスできる分散ファイル システム (S3 など) に、次の項目をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="620ad-131">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="620ad-132">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: この jar は、[Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージの一部として含まれており、アプリのビルド出力ディレクトリに併置されています。</span><span class="sxs-lookup"><span data-stu-id="620ad-132">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="620ad-133">各 Executor の作業ディレクトリ内に配置されるファイル (依存関係ファイルや、すべてのワーカーからアクセスできる共通データなど) またはアセンブリ (アプリが依存しているユーザー定義関数またはライブラリを含む DLL など)。</span><span class="sxs-lookup"><span data-stu-id="620ad-133">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="620ad-134">Amazon EMR Spark にデプロイする</span><span class="sxs-lookup"><span data-stu-id="620ad-134">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="620ad-135">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) は、AWS でのビッグ データ フレームワークの実行を簡略化する、マネージド クラスター プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="620ad-135">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="620ad-136">Amazon EMR Spark は Linux ベースです。</span><span class="sxs-lookup"><span data-stu-id="620ad-136">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="620ad-137">そのため、Amazon EMR Spark へのアプリのデプロイに関心がある場合は、アプリが .NET Standard と互換性があることと、アプリのコンパイルに [.NET Core コンパイラ](https://dotnet.microsoft.com/download)を使用していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="620ad-137">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="620ad-138">Microsoft.Spark.Worker をデプロイする</span><span class="sxs-lookup"><span data-stu-id="620ad-138">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="620ad-139">この手順は、クラスターの作成時にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="620ad-139">This step is only required at cluster creation.</span></span>

<span data-ttu-id="620ad-140">[ブートストラップ アクション](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)を使用してクラスターの作成中に、`install-worker.sh` を実行します。</span><span class="sxs-lookup"><span data-stu-id="620ad-140">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="620ad-141">AWS CLI を使用して Linux で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="620ad-141">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a><span data-ttu-id="620ad-142">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="620ad-142">Run your app</span></span>

<span data-ttu-id="620ad-143">Amazon EMR Spark でアプリを実行するには、spark submit ステップと Amazon EMR ステップの 2 通りの方法があります。</span><span class="sxs-lookup"><span data-stu-id="620ad-143">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="620ad-144">spark-submit を使用する</span><span class="sxs-lookup"><span data-stu-id="620ad-144">Use spark-submit</span></span>

<span data-ttu-id="620ad-145">[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) コマンドを使用して、.NET for Apache Spark ジョブを Amazon EMR Spark に送信できます。</span><span class="sxs-lookup"><span data-stu-id="620ad-145">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="620ad-146">クラスター内のいずれかのノードに `ssh` で接続します。</span><span class="sxs-lookup"><span data-stu-id="620ad-146">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="620ad-147">`spark-submit` を実行します。</span><span class="sxs-lookup"><span data-stu-id="620ad-147">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="620ad-148">Amazon EMR ステップを使用する</span><span class="sxs-lookup"><span data-stu-id="620ad-148">Use Amazon EMR Steps</span></span>

<span data-ttu-id="620ad-149">[Amazon EMR ステップ](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html)を使用して、EMR クラスターにインストールされている Spark フレームワークにジョブを送信できます。</span><span class="sxs-lookup"><span data-stu-id="620ad-149">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="620ad-150">AWS CLI を使用して Linux で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="620ad-150">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="620ad-151">次のステップ</span><span class="sxs-lookup"><span data-stu-id="620ad-151">Next steps</span></span>

<span data-ttu-id="620ad-152">このチュートリアルでは、.NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイしました。</span><span class="sxs-lookup"><span data-stu-id="620ad-152">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="620ad-153">.NET for Apache Spark のプロジェクト例については、GitHub に進んでください。</span><span class="sxs-lookup"><span data-stu-id="620ad-153">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="620ad-154">.NET for Apache Spark サンプル</span><span class="sxs-lookup"><span data-stu-id="620ad-154">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/main/examples)
