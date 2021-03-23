---
title: .NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする
description: .NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする方法を説明します。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0c2b7522e0e6790ded418413ef0f128aae1e0884
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875344"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="34461-103">チュートリアル: .NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする</span><span class="sxs-lookup"><span data-stu-id="34461-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="34461-104">このチュートリアルでは、.NET for Apache Spark アプリケーションを Azure HDInsight クラスターを介してクラウドにデプロイする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="34461-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="34461-105">HDInsight の Spark クラスターは Azure Storage および Azure Data Lake Storage と互換性があるため、HDInsight では、Spark クラスターの作成と構成をより簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="34461-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="34461-106">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="34461-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="34461-107">Azure Storage Explorer を使用してストレージ アカウントにアクセスする。</span><span class="sxs-lookup"><span data-stu-id="34461-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="34461-108">Azure HDInsight クラスターを作成する。</span><span class="sxs-lookup"><span data-stu-id="34461-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="34461-109">.NET for Apache Spark アプリを発行する。</span><span class="sxs-lookup"><span data-stu-id="34461-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="34461-110">HDInsight スクリプト アクションを作成する。</span><span class="sxs-lookup"><span data-stu-id="34461-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="34461-111">HDInsight クラスターで .NET for Apache Spark アプリケーションを実行する。</span><span class="sxs-lookup"><span data-stu-id="34461-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34461-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="34461-112">Prerequisites</span></span>

<span data-ttu-id="34461-113">開始する前に、以下の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="34461-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="34461-114">Azure サブスクリプションをお持ちでない場合は、[無料アカウント](https://azure.microsoft.com/free/dotnet/)を作成してください。</span><span class="sxs-lookup"><span data-stu-id="34461-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="34461-115">[Azure Portal](https://portal.azure.com/) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="34461-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="34461-116">Azure Storage Explorer を [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409)、[Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)、または [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) コンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="34461-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="34461-117">チュートリアル「[.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)」 (.NET for Apache Spark - 10 分で開始する) を完了します。</span><span class="sxs-lookup"><span data-stu-id="34461-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="34461-118">ストレージ アカウントにアクセスする</span><span class="sxs-lookup"><span data-stu-id="34461-118">Access your storage accounts</span></span>

1. <span data-ttu-id="34461-119">Azure ストレージ エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="34461-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="34461-120">左側のメニューで **[アカウントの追加]** を選択し、自分の Azure アカウントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="34461-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Storage Explorer から Azure アカウントにサインインする](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="34461-122">サインインすると、お持ちのすべてのストレージ アカウントと、それらのストレージ アカウントにアップロードしたすべてのリソースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34461-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="34461-123">HDInsight クラスターの作成</span><span class="sxs-lookup"><span data-stu-id="34461-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34461-124">HDInsight クラスターの料金は、そのクラスターを使用していない場合でも、分単位で課金されます。</span><span class="sxs-lookup"><span data-stu-id="34461-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="34461-125">使用後は、クラスターを必ず削除してください。</span><span class="sxs-lookup"><span data-stu-id="34461-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="34461-126">詳細については、この記事の「[リソースのクリーンアップ](#clean-up-resources)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="34461-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="34461-127">[Azure Portal](https://portal.azure.com) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="34461-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="34461-128">**[+ リソースの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="34461-129">次に、 **[分析]** カテゴリから **[HDInsight]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Azure portal から HDInsight リソースを作成する](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="34461-131">**[基本]** で次の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="34461-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="34461-132">プロパティ</span><span class="sxs-lookup"><span data-stu-id="34461-132">Property</span></span>  |<span data-ttu-id="34461-133">説明</span><span class="sxs-lookup"><span data-stu-id="34461-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="34461-134">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="34461-134">Subscription</span></span>  | <span data-ttu-id="34461-135">ドロップダウンから、アクティブな Azure サブスクリプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="34461-136">リソース グループ</span><span class="sxs-lookup"><span data-stu-id="34461-136">Resource group</span></span> | <span data-ttu-id="34461-137">新しいリソース グループを作成するか、既存のリソース グループを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="34461-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="34461-138">リソース グループは、Azure ソリューションの関連するリソースを保持するコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="34461-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="34461-139">クラスター名</span><span class="sxs-lookup"><span data-stu-id="34461-139">Cluster name</span></span> | <span data-ttu-id="34461-140">HDInsight Spark クラスターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="34461-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="34461-141">場所</span><span class="sxs-lookup"><span data-stu-id="34461-141">Location</span></span>   | <span data-ttu-id="34461-142">リソース グループの場所を選びます。</span><span class="sxs-lookup"><span data-stu-id="34461-142">Select a location for the resource group.</span></span> <span data-ttu-id="34461-143">テンプレートでは、この場所をクラスターの作成および既定のクラスター ストレージに使用します。</span><span class="sxs-lookup"><span data-stu-id="34461-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="34461-144">クラスターの種類</span><span class="sxs-lookup"><span data-stu-id="34461-144">Cluster type</span></span>| <span data-ttu-id="34461-145">クラスターの種類として **[Spark]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="34461-146">クラスターのバージョン</span><span class="sxs-lookup"><span data-stu-id="34461-146">Cluster version</span></span>|<span data-ttu-id="34461-147">クラスターの種類が選択されると、このフィールドに既定のバージョンが自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="34461-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="34461-148">Spark バージョン 2.3 または 2.4 を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="34461-149">クラスター ログイン ユーザー名</span><span class="sxs-lookup"><span data-stu-id="34461-149">Cluster login username</span></span>| <span data-ttu-id="34461-150">クラスターのログイン ユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="34461-150">Enter the cluster login username.</span></span>  <span data-ttu-id="34461-151">既定の名前は *admin* です。</span><span class="sxs-lookup"><span data-stu-id="34461-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="34461-152">クラスター ログイン パスワード</span><span class="sxs-lookup"><span data-stu-id="34461-152">Cluster login password</span></span>| <span data-ttu-id="34461-153">ログイン パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="34461-153">Enter any login password.</span></span> |
    |<span data-ttu-id="34461-154">Secure Shell (SSH) ユーザー名</span><span class="sxs-lookup"><span data-stu-id="34461-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="34461-155">SSH ユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="34461-155">Enter the SSH username.</span></span> <span data-ttu-id="34461-156">既定では、このアカウントは "*クラスター ログイン ユーザー名*" アカウントと同じパスワードを共有します。</span><span class="sxs-lookup"><span data-stu-id="34461-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="34461-157">**ストレージ >>** を選択して **ストレージ** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="34461-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="34461-158">**[ストレージ]** で次の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="34461-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="34461-159">プロパティ</span><span class="sxs-lookup"><span data-stu-id="34461-159">Property</span></span>  |<span data-ttu-id="34461-160">説明</span><span class="sxs-lookup"><span data-stu-id="34461-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="34461-161">プライマリ ストレージの種類</span><span class="sxs-lookup"><span data-stu-id="34461-161">Primary storage type</span></span>|<span data-ttu-id="34461-162">既定値の **[Azure Storage]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="34461-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="34461-163">メソッドの選択</span><span class="sxs-lookup"><span data-stu-id="34461-163">Selection method</span></span>|<span data-ttu-id="34461-164">既定値の **[一覧から選択する]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="34461-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="34461-165">プライマリ ストレージ アカウント</span><span class="sxs-lookup"><span data-stu-id="34461-165">Primary storage account</span></span>|<span data-ttu-id="34461-166">サブスクリプションと、そのサブスクリプション内のアクティブなストレージ アカウントの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="34461-167">コンテナー</span><span class="sxs-lookup"><span data-stu-id="34461-167">Container</span></span>|<span data-ttu-id="34461-168">このコンテナーはストレージ アカウント内の特定の BLOB コンテナーで、クラスターはこのコンテナーを検索して、クラウドでアプリケーションを実行するためのファイルを見つけます。</span><span class="sxs-lookup"><span data-stu-id="34461-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="34461-169">任意の使用可能な名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="34461-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="34461-170">**[Review + create]\(確認と作成\)** を選択し、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="34461-171">クラスターの作成には約 20 分かかります。</span><span class="sxs-lookup"><span data-stu-id="34461-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="34461-172">次のセッションに進む前に、クラスターを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34461-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="34461-173">アプリケーションの発行</span><span class="sxs-lookup"><span data-stu-id="34461-173">Publish your app</span></span>

<span data-ttu-id="34461-174">次に、チュートリアル「[.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)」 (.NET for Apache Spark - 10 分で開始する) で作成した *mySparkApp* を公開します。これにより、Spark クラスターは、アプリケーションを実行するために必要なすべてのファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="34461-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="34461-175">*mySparkApp* を公開するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="34461-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="34461-176">**Windows の場合:**</span><span class="sxs-lookup"><span data-stu-id="34461-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r win-x64
   ```

   <span data-ttu-id="34461-177">**Linux の場合:**</span><span class="sxs-lookup"><span data-stu-id="34461-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="34461-178">公開するアプリケーション ファイルを HDInsight クラスターに簡単にアップロードできるように、次のタスクを実行してファイルを圧縮します。</span><span class="sxs-lookup"><span data-stu-id="34461-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span> <span data-ttu-id="34461-179">発行フォルダーの内容 (たとえば、手順 1 の結果として作成された *publish.zip*) を圧縮します。</span><span class="sxs-lookup"><span data-stu-id="34461-179">Zip the contents of the publish folder, *publish.zip* for example, that was created as a result of Step 1.</span></span> <span data-ttu-id="34461-180">すべてのアセンブリは ZIP ファイルの最初のレイヤーにある必要があり、中間フォルダーのレイヤーに存在してはいけません。</span><span class="sxs-lookup"><span data-stu-id="34461-180">All the assemblies should be in the first layer of the ZIP file and there should be no intermediate folder layer.</span></span> <span data-ttu-id="34461-181">つまり、*publish.zip* を解凍すると、すべてのアセンブリが現在の作業ディレクトリに抽出されます。</span><span class="sxs-lookup"><span data-stu-id="34461-181">This means when you unzip *publish.zip*, all assemblies are extracted into your current working directory.</span></span>

   <span data-ttu-id="34461-182">**Windows の場合:**</span><span class="sxs-lookup"><span data-stu-id="34461-182">**On Windows:**</span></span>

   <span data-ttu-id="34461-183">7-Zip や WinZip のような抽出プログラムを使用して、発行されたすべてのバイナリを含むファイルを bin ディレクトリに抽出します。</span><span class="sxs-lookup"><span data-stu-id="34461-183">Use an extraction program, like 7-Zip or WinZip, to extract the file into the bin directory with all the published binaries.</span></span>

   <span data-ttu-id="34461-184">**Linux の場合は、次のコマンドを実行します。**</span><span class="sxs-lookup"><span data-stu-id="34461-184">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="34461-185">Azure にファイルをアップロードする</span><span class="sxs-lookup"><span data-stu-id="34461-185">Upload files to Azure</span></span>

<span data-ttu-id="34461-186">次に、Azure Storage Explorer を使用して、クラスターのストレージ用に選択した BLOB コンテナーに次の 5 つのファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="34461-186">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="34461-187">Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="34461-187">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="34461-188">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="34461-188">install-worker.sh</span></span>
* <span data-ttu-id="34461-189">publish.zip</span><span class="sxs-lookup"><span data-stu-id="34461-189">publish.zip</span></span>
* <span data-ttu-id="34461-190">microsoft-spark-2-4_2.11-1.0.0.jar</span><span class="sxs-lookup"><span data-stu-id="34461-190">microsoft-spark-2-4_2.11-1.0.0.jar</span></span>
* <span data-ttu-id="34461-191">input.txt</span><span class="sxs-lookup"><span data-stu-id="34461-191">input.txt</span></span>

1. <span data-ttu-id="34461-192">Azure Storage Explorer を開いて、左側のメニューからストレージ アカウントに移動します。</span><span class="sxs-lookup"><span data-stu-id="34461-192">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="34461-193">ストレージ アカウント内の **[BLOB コンテナー]** でクラスターの BLOB コンテナーをドリルダウンします。</span><span class="sxs-lookup"><span data-stu-id="34461-193">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="34461-194">*Microsoft.Spark.Worker* は、Apache Spark が作成されたユーザー定義関数 (UDF) などのアプリケーションを実行するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="34461-194">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="34461-195">[Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="34461-195">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span> <span data-ttu-id="34461-196">次に、Azure Storage Explorer で **[アップロード]** を選択して、worker をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="34461-196">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Azure Storage Explorer にファイルをアップロードする](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="34461-198">*install-worker.sh* は、.NET for Apache Spark 依存ファイルをクラスターのノードにコピーできるスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="34461-198">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="34461-199">ご使用のローカル コンピューターで、**install-worker.sh** という名前の新しいファイルを作成し、GitHub 上にある [install-worker.sh のコンテンツ](https://raw.githubusercontent.com/dotnet/spark/main/deployment/install-worker.sh)を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="34461-199">Create a new file named **install-worker.sh** in your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/main/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="34461-200">次に、*install-worker.sh* を BLOB コンテナーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="34461-200">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="34461-201">ご利用のクラスターには、アプリの発行済みファイルが格納されている *publish.zip* ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="34461-201">Your cluster needs the *publish.zip* file that contains your app's published files.</span></span> <span data-ttu-id="34461-202">発行済みフォルダー **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64** に移動し、**publish.zip** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="34461-202">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="34461-203">次に、BLOB コンテナーに *publish.zip* をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="34461-203">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="34461-204">jar としてパッケージ化され、[Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) nuget の一部として取り込まれ、アプリのビルド出力ディレクトリ内に併置されるアプリケーション コードが、ご利用のクラスターには必要です。</span><span class="sxs-lookup"><span data-stu-id="34461-204">Your cluster needs the application code that is packaged as a jar, included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) nuget and colocated in your app's build output directory.</span></span> <span data-ttu-id="34461-205">発行済みフォルダー **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64** に移動し、**microsoft-spark-2-4_2.11-1.0.0.jar** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="34461-205">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64**, and locate **microsoft-spark-2-4_2.11-1.0.0.jar**.</span></span> <span data-ttu-id="34461-206">次に、BLOB コンテナーに jar ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="34461-206">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="34461-207">複数の .jar ファイル (Spark のバージョン 2.3.x、2.4.x、3.0.x) が存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="34461-207">There may be multiple .jar files (for versions 2.3.x, 2.4.x and 3.0.x of Spark).</span></span> <span data-ttu-id="34461-208">クラスターの作成時に選択した Spark のバージョンと一致する .jar ファイルを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34461-208">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="34461-209">たとえば、クラスターの作成時に Spark 2.4 を選択した場合は、*microsoft-spark-2-4_2.11-1.0.0.jar* を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-209">For example, choose *microsoft-spark-2-4_2.11-1.0.0.jar* if you chose Spark 2.4 during cluster creation.</span></span>

6. <span data-ttu-id="34461-210">クラスターは、アプリケーションへの入力を必要とします。</span><span class="sxs-lookup"><span data-stu-id="34461-210">Your cluster needs the input to your app.</span></span> <span data-ttu-id="34461-211">**mySparkApp** ディレクトリに移動して、**input.txt** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="34461-211">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="34461-212">BLOB コンテナー内の **user/sshuser** ディレクトリに入力ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="34461-212">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="34461-213">ssh を使用してクラスターに接続すると、クラスターはこのフォルダーで入力を検索します。</span><span class="sxs-lookup"><span data-stu-id="34461-213">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="34461-214">特定のディレクトリにアップロードされるのは、*input.txt* ファイルのみです。</span><span class="sxs-lookup"><span data-stu-id="34461-214">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="34461-215">HDInsight スクリプト アクションを実行する</span><span class="sxs-lookup"><span data-stu-id="34461-215">Run the HDInsight script action</span></span>

<span data-ttu-id="34461-216">クラスターの実行中、ファイルを Azure にアップロードしたら、クラスターで **install-worker.sh** スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="34461-216">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="34461-217">Azure portal の HDInsight Spark クラスターに移動し、**[スクリプト アクション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-217">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="34461-218">**[+ 新規で送信]** を選択し、次の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="34461-218">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="34461-219">プロパティ</span><span class="sxs-lookup"><span data-stu-id="34461-219">Property</span></span>  |<span data-ttu-id="34461-220">説明</span><span class="sxs-lookup"><span data-stu-id="34461-220">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="34461-221">スクリプトの種類</span><span class="sxs-lookup"><span data-stu-id="34461-221">Script type</span></span> |<span data-ttu-id="34461-222">カスタム</span><span class="sxs-lookup"><span data-stu-id="34461-222">Custom</span></span>|
   | <span data-ttu-id="34461-223">名前</span><span class="sxs-lookup"><span data-stu-id="34461-223">Name</span></span> | <span data-ttu-id="34461-224">Install Worker</span><span class="sxs-lookup"><span data-stu-id="34461-224">Install Worker</span></span>|
   | <span data-ttu-id="34461-225">Bash スクリプト URI</span><span class="sxs-lookup"><span data-stu-id="34461-225">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="34461-226">この URI を確認するには、Azure Storage Explorer で install-worker.sh を右クリックして、[プロパティ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-226">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="34461-227">ノードの種類</span><span class="sxs-lookup"><span data-stu-id="34461-227">Node type(s)</span></span>| <span data-ttu-id="34461-228">ワーカー</span><span class="sxs-lookup"><span data-stu-id="34461-228">Worker</span></span>|
   | <span data-ttu-id="34461-229">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34461-229">Parameters</span></span> | <span data-ttu-id="34461-230">azure</span><span class="sxs-lookup"><span data-stu-id="34461-230">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz </br> <span data-ttu-id="34461-231">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="34461-231">/usr/local/bin</span></span>

3. <span data-ttu-id="34461-232">**[作成]** を選択して、スクリプトを送信します。</span><span class="sxs-lookup"><span data-stu-id="34461-232">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="34461-233">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="34461-233">Run your app</span></span>

1. <span data-ttu-id="34461-234">Azure portal の HDInsight Spark クラスターに移動し、**[SSH およびクラスターのログイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="34461-234">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="34461-235">ssh ログイン情報をコピーし、ログインをターミナルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="34461-235">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="34461-236">クラスターの作成時に設定したパスワードを使用してクラスターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="34461-236">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="34461-237">Ubuntu および Spark のウェルカム メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34461-237">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="34461-238">**spark-submit** コマンドを使用して、HDInsight クラスターでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="34461-238">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="34461-239">このスクリプト例の **mycontainer** と **mystorageaccount** を、実際の BLOB コンテナーの名前とストレージ アカウントに置き換えることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="34461-239">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2-4_2.11-1.0.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="34461-240">アプリケーションが実行されると、ローカル実行が開始されてからコンソールに書き込まれた文字数と同じ文字数のテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34461-240">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="34461-241">これで、初めての .NET for Apache Spark アプリケーションをクラウドで実行できました。</span><span class="sxs-lookup"><span data-stu-id="34461-241">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="34461-242">リソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="34461-242">Clean up resources</span></span>

<span data-ttu-id="34461-243">HDInsight を使用すると、データは Azure Storage に格納されるため、使用されていないクラスターを安全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="34461-243">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="34461-244">また、HDInsight クラスターは、使用していない場合でも課金されます。</span><span class="sxs-lookup"><span data-stu-id="34461-244">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="34461-245">クラスターの料金は Storage の料金の何倍にもなるため、クラスターを使用しない場合は削除するのが経済的にも合理的です。</span><span class="sxs-lookup"><span data-stu-id="34461-245">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="34461-246">リソース グループ名を選び、リソース グループ ページを開いて、 **[リソース グループの削除]** を選ぶこともできます。</span><span class="sxs-lookup"><span data-stu-id="34461-246">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="34461-247">リソース グループを削除すると、HDInsight Spark クラスターと既定のストレージ アカウントの両方が削除されます。</span><span class="sxs-lookup"><span data-stu-id="34461-247">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="34461-248">次の手順</span><span class="sxs-lookup"><span data-stu-id="34461-248">Next steps</span></span>

<span data-ttu-id="34461-249">このチュートリアルでは、.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイしました。</span><span class="sxs-lookup"><span data-stu-id="34461-249">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="34461-250">HDInsight の詳細については、Azure HDInsight のドキュメントに進んでください。</span><span class="sxs-lookup"><span data-stu-id="34461-250">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="34461-251">[Azure HDInsight 上にジョブをリモートで送信する](../how-to-guides/hdinsight-deploy-methods.md)
> [Azure HDInsight ドキュメント](/azure/hdinsight/)</span><span class="sxs-lookup"><span data-stu-id="34461-251">[Submit jobs remotely on Azure HDInsight](../how-to-guides/hdinsight-deploy-methods.md)
[Azure HDInsight Documentation](/azure/hdinsight/)</span></span>
