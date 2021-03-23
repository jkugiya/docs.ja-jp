---
title: .NET for Apache Spark ジョブを Databricks に送信する
description: spark-submit と Set Jar を使用して、.NET for Apache Spark ジョブを Databricks に送信する方法について説明します。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 39be961ad67da3f8593cb98e1bad8df354f28893
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875578"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="adc65-103">.NET for Apache Spark ジョブを Databricks に送信する</span><span class="sxs-lookup"><span data-stu-id="adc65-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="adc65-104">.NET for Apache Spark ジョブを Databricks クラスター上で実行できますが、すぐに行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="adc65-104">You can run your .NET for Apache Spark jobs on Databricks clusters, but it is not available out-of-the-box.</span></span> <span data-ttu-id="adc65-105">.NET for Apache Spark ジョブの Databricks へのデプロイには、`spark-submit` と Set Jar の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="adc65-105">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="adc65-106">spark-submit を使用して展開する</span><span class="sxs-lookup"><span data-stu-id="adc65-106">Deploy using spark-submit</span></span>

<span data-ttu-id="adc65-107">[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) コマンドを使用して、.NET for Apache Spark ジョブを Databricks に送信できます。</span><span class="sxs-lookup"><span data-stu-id="adc65-107">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="adc65-108">`spark-submit` を使用すると、オンデマンドで作成されたクラスターにのみ送信できます。</span><span class="sxs-lookup"><span data-stu-id="adc65-108">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="adc65-109">Databricks ワークスペースに移動して新しいジョブを作成します。</span><span class="sxs-lookup"><span data-stu-id="adc65-109">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="adc65-110">ジョブのタイトルを選択し、 **[Configure spark-submit]\(spark-submit の構成\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="adc65-110">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="adc65-111">次のパラメーターをジョブ構成に貼り付け、 **[確認]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="adc65-111">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="adc65-112">使用する特定のファイルと構成に基づいて、上記のパラメーターの内容を更新します。</span><span class="sxs-lookup"><span data-stu-id="adc65-112">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="adc65-113">たとえば、DBFS にアップロードした Microsoft Spark jar ファイルのバージョンを参照し、アプリの適切な名前と発行済みのアプリの zip ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="adc65-113">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="adc65-114">ジョブに移動し、 **[編集]** を選択して、ジョブのクラスターを構成します。</span><span class="sxs-lookup"><span data-stu-id="adc65-114">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="adc65-115">デプロイで使用する Apache Spark のバージョンに基づいて、Databricks Runtime のバージョンを設定します。</span><span class="sxs-lookup"><span data-stu-id="adc65-115">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="adc65-116">次に、 **[詳細オプション] > [Init スクリプト]** を選択し、Init スクリプトのパスを `dbfs:/spark-dotnet/db-init.sh` に設定します。</span><span class="sxs-lookup"><span data-stu-id="adc65-116">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="adc65-117">**[確認]** を選択して、クラスターの設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="adc65-117">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="adc65-118">ジョブに移動し、 **[今すぐ実行]** を選択して、新しく構成した Spark クラスターでジョブを実行します。</span><span class="sxs-lookup"><span data-stu-id="adc65-118">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="adc65-119">ジョブのクラスターが作成されるまで数分かかります。</span><span class="sxs-lookup"><span data-stu-id="adc65-119">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="adc65-120">作成されると、ジョブが送信されます。</span><span class="sxs-lookup"><span data-stu-id="adc65-120">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="adc65-121">出力を表示するには、Databricks ワークスペースの左側のメニューから **[クラスター]** を選択し、 **[Driver Logs]\(ドライバーのログ\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="adc65-121">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="adc65-122">Set Jar を使用してデプロイする</span><span class="sxs-lookup"><span data-stu-id="adc65-122">Deploy using Set Jar</span></span>

<span data-ttu-id="adc65-123">別の方法として、Databricks ワークスペースで [Set Jar](/azure/databricks/jobs#--create-a-job) を使用して、.NET for Apache Spark ジョブを Databricks に送信できます。</span><span class="sxs-lookup"><span data-stu-id="adc65-123">Alternatively, you can use [Set Jar](/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="adc65-124">*Set Jar* を使用すると、既存のアクティブなクラスターにジョブを送信できます。</span><span class="sxs-lookup"><span data-stu-id="adc65-124">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="adc65-125">1 回限りのセットアップ</span><span class="sxs-lookup"><span data-stu-id="adc65-125">One-time setup</span></span>

1. <span data-ttu-id="adc65-126">Databricks クラスターに移動し、左側のメニューから **[ジョブ]** を選択し、 **[Set JAR]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="adc65-126">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="adc65-127">適切な `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="adc65-127">Upload the appropriate `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`.</span></span>

3. <span data-ttu-id="adc65-128">`<your-app-name>` の代わりに発行済みの実行可能ファイルの正しい名前が含まれるように、次のパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="adc65-128">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="adc65-129">Init スクリプトが既に設定されている既存のクラスターを指すようにクラスターを構成します。</span><span class="sxs-lookup"><span data-stu-id="adc65-129">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="adc65-130">アプリを発行して実行する</span><span class="sxs-lookup"><span data-stu-id="adc65-130">Publish and run your app</span></span>

1. <span data-ttu-id="adc65-131">アプリを発行したこと、およびアプリケーション コードで `SparkSession.Stop()` が使用されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="adc65-131">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="adc65-132">[Databricks CLI](/azure/databricks/dev-tools/databricks-cli) を使用して、アプリケーションを Databricks クラスターにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="adc65-132">Use [Databricks CLI](/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="adc65-133">たとえば、発行済みのアプリをクラスターにアップロードするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="adc65-133">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="adc65-134">アプリにユーザー定義関数が含まれている場合は、アプリ アセンブリ (ユーザー定義関数とそれらの依存関係を含む DLL など) を各 *Microsoft.Spark.Worker* の作業ディレクトリに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adc65-134">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="adc65-135">アプリケーション アセンブリを Databricks クラスターにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="adc65-135">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="adc65-136">[db-init.sh](https://github.com/dotnet/spark/blob/main/deployment/db-init.sh) 内のアプリの依存関係セクションをコメント解除して、アプリの依存関係パスをポイントするように変更します。</span><span class="sxs-lookup"><span data-stu-id="adc65-136">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/main/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="adc65-137">次に、更新された *db-init.sh* をクラスターにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="adc65-137">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="adc65-138">**[Databricks クラスター] > [ジョブ] > <ジョブ名> > [今すぐ実行]** を選択して、ジョブを実行します。</span><span class="sxs-lookup"><span data-stu-id="adc65-138">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="adc65-139">次の手順</span><span class="sxs-lookup"><span data-stu-id="adc65-139">Next steps</span></span>

* [<span data-ttu-id="adc65-140">.NET for Apache Spark の概要</span><span class="sxs-lookup"><span data-stu-id="adc65-140">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="adc65-141">.NET for Apache Spark アプリケーションを Databricks にデプロイする</span><span class="sxs-lookup"><span data-stu-id="adc65-141">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="adc65-142">Azure Databricks のドキュメント</span><span class="sxs-lookup"><span data-stu-id="adc65-142">Azure Databricks Documentation</span></span>](/azure/azure-databricks/)
