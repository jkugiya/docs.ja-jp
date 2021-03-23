---
title: .NET for Apache Spark アプリケーションを Databricks にデプロイする
description: .NET for Apache Spark アプリケーションを Databricks にデプロイする方法を説明します。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e751953937279a5f9f78f777bac8a5ca510a2f87
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876969"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="3978b-103">チュートリアル: .NET for Apache Spark アプリケーションを Databricks にデプロイする</span><span class="sxs-lookup"><span data-stu-id="3978b-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="3978b-104">このチュートリアルでは、Azure Databricks を使用してクラウドにアプリをデプロイする方法について説明します。Azure Databricks は、ワンクリックでセットアップでき、ワークフローを合理化し、コラボレーションを可能にするインタラクティブなワークスペースを提供する、Apache Spark ベースの分析プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="3978b-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="3978b-105">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3978b-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="3978b-106">Azure Databricks ワークスペースを作成する。</span><span class="sxs-lookup"><span data-stu-id="3978b-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="3978b-107">.NET for Apache Spark アプリを発行する。</span><span class="sxs-lookup"><span data-stu-id="3978b-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="3978b-108">Spark ジョブと Spark クラスターを作成する。</span><span class="sxs-lookup"><span data-stu-id="3978b-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="3978b-109">Spark クラスターでアプリを実行する。</span><span class="sxs-lookup"><span data-stu-id="3978b-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3978b-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3978b-110">Prerequisites</span></span>

<span data-ttu-id="3978b-111">開始する前に、以下の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="3978b-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="3978b-112">Azure アカウントがない場合は、[無料アカウント](https://azure.microsoft.com/free/dotnet/)を作成します。</span><span class="sxs-lookup"><span data-stu-id="3978b-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="3978b-113">[Azure Portal](https://portal.azure.com/) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="3978b-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="3978b-114">「[.NET for Apache Spark - 10 分で開始する](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)」のチュートリアルを完了します。</span><span class="sxs-lookup"><span data-stu-id="3978b-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="3978b-115">Azure Databricks ワークスペースを作成する</span><span class="sxs-lookup"><span data-stu-id="3978b-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="3978b-116">**Azure 無料試用版サブスクリプション** を使用してこのチュートリアルを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="3978b-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="3978b-117">無料アカウントをお持ちの場合は、お使いのプロファイルにアクセスし、サブスクリプションを **[従量課金制]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="3978b-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="3978b-118">詳細については、[Azure 無料アカウント](https://azure.microsoft.com/free/dotnet/)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3978b-118">For more information, see [Azure free account](https://azure.microsoft.com/free/dotnet/).</span></span> <span data-ttu-id="3978b-119">次に、リージョン内の vCPU について[使用制限を削除し](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)、[クォータの増加を依頼](/azure/azure-supportability/resource-manager-core-quotas-request)します。</span><span class="sxs-lookup"><span data-stu-id="3978b-119">Then, [remove the spending limit](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="3978b-120">Azure Databricks ワークスペースを作成するときに、 **[Trial (Premium - 14-Days Free DBUs)]\(試用版 (Premium - 14 日間の無料 DBU)\)** の価格レベルを選択し、ワークスペースから 14 日間無料の Premium Azure Databricks DBU にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="3978b-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="3978b-121">このセクションでは、Azure Portal を使って Azure Databricks ワークスペースを作成します。</span><span class="sxs-lookup"><span data-stu-id="3978b-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="3978b-122">Azure portal で、 **[リソースの作成]**  >  **[分析]**  >  **[Azure Databricks]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Azure portal で Azure Databricks リソースを作成する](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="3978b-124">**[Azure Databricks サービス]** で値を指定して、Databricks ワークスペースを作成します。</span><span class="sxs-lookup"><span data-stu-id="3978b-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="3978b-125">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3978b-125">Property</span></span>  |<span data-ttu-id="3978b-126">説明</span><span class="sxs-lookup"><span data-stu-id="3978b-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="3978b-127">**ワークスペース名**</span><span class="sxs-lookup"><span data-stu-id="3978b-127">**Workspace name**</span></span>     | <span data-ttu-id="3978b-128">Databricks ワークスペースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3978b-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="3978b-129">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="3978b-129">**Subscription**</span></span>     | <span data-ttu-id="3978b-130">ドロップダウンから Azure サブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="3978b-131">**リソース グループ**</span><span class="sxs-lookup"><span data-stu-id="3978b-131">**Resource group**</span></span>     | <span data-ttu-id="3978b-132">新しいリソース グループを作成するか、既存のリソース グループを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3978b-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="3978b-133">リソース グループは、Azure ソリューションの関連するリソースを保持するコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="3978b-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="3978b-134">詳しくは、[Azure リソース グループの概要](/azure/azure-resource-manager/resource-group-overview)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3978b-134">For more information, see [Azure Resource Group overview](/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="3978b-135">**場所**</span><span class="sxs-lookup"><span data-stu-id="3978b-135">**Location**</span></span>     | <span data-ttu-id="3978b-136">優先リージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-136">Select your preferred region.</span></span> <span data-ttu-id="3978b-137">使用可能なリージョンについては、[リージョン別の利用可能な Azure サービス](https://azure.microsoft.com/regions/services/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3978b-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="3978b-138">**価格レベル**</span><span class="sxs-lookup"><span data-stu-id="3978b-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="3978b-139">**Standard**、**Premium**、**Trial** のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="3978b-140">これらのレベルの詳細については、[Databricks の価格に関するページ](https://azure.microsoft.com/pricing/details/databricks/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3978b-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="3978b-141">**Virtual Network**</span><span class="sxs-lookup"><span data-stu-id="3978b-141">**Virtual Network**</span></span>     |   <span data-ttu-id="3978b-142">いいえ</span><span class="sxs-lookup"><span data-stu-id="3978b-142">No</span></span>       |

3. <span data-ttu-id="3978b-143">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-143">Select **Create**.</span></span> <span data-ttu-id="3978b-144">ワークスペースの作成には数分かかります。</span><span class="sxs-lookup"><span data-stu-id="3978b-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="3978b-145">ワークスペースの作成中に、 **[通知]** でデプロイの状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="3978b-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="3978b-146">Azure Databricks ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="3978b-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="3978b-147">**Databricks CLI** を使用して Azure Databricks クラスターに接続し、ローカル コンピューターからそれらのクラスターにファイルをアップロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="3978b-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="3978b-148">Databricks クラスターからファイルへのアクセスは、DBFS (Databricks ファイル システム) を介して行われます。</span><span class="sxs-lookup"><span data-stu-id="3978b-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="3978b-149">Databricks CLI には、Python 3.6 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="3978b-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="3978b-150">Python を既にインストール済みである場合は、この手順をスキップできます。</span><span class="sxs-lookup"><span data-stu-id="3978b-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="3978b-151">**Windows の場合:**</span><span class="sxs-lookup"><span data-stu-id="3978b-151">**For Windows:**</span></span>

   [<span data-ttu-id="3978b-152">Windows 用 Python のダウンロード</span><span class="sxs-lookup"><span data-stu-id="3978b-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="3978b-153">**Linux の場合:** Python は、ほとんどの Linux ディストリビューションにプレインストールされています。</span><span class="sxs-lookup"><span data-stu-id="3978b-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="3978b-154">次のコマンドを実行して、どのバージョンがインストールされているかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3978b-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="3978b-155">pip を使用して Databricks CLI をインストールします。</span><span class="sxs-lookup"><span data-stu-id="3978b-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="3978b-156">Python 3.4 以降では、既定で pip が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3978b-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="3978b-157">Python 3 には pip3 を使用します。</span><span class="sxs-lookup"><span data-stu-id="3978b-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="3978b-158">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3978b-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="3978b-159">Databricks CLI をインストールしたら、新しいコマンド プロンプトを開き、`databricks` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3978b-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="3978b-160">**'databricks' が内部または外部コマンドとして認識されないエラー** が発生した場合は、新しいコマンド プロンプトを開いたことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3978b-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="3978b-161">Azure Databricks の設定</span><span class="sxs-lookup"><span data-stu-id="3978b-161">Set up Azure Databricks</span></span>

<span data-ttu-id="3978b-162">Databricks CLI がインストールされたので、認証の詳細を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3978b-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="3978b-163">Databricks CLI コマンド `databricks configure --token` を実行します。</span><span class="sxs-lookup"><span data-stu-id="3978b-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="3978b-164">構成コマンドの実行後、ホストを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="3978b-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="3978b-165">ホスト URL では、`https://<Location>.azuredatabricks.net` の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3978b-165">Your host URL uses the format: `https://<Location>.azuredatabricks.net`.</span></span> <span data-ttu-id="3978b-166">たとえば、Azure Databricks サービスの作成時に **eastus2** を選択した場合、ホストは `https://eastus2.azuredatabricks.net` となります。</span><span class="sxs-lookup"><span data-stu-id="3978b-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be `https://eastus2.azuredatabricks.net`.</span></span>

3. <span data-ttu-id="3978b-167">ホストの入力後、トークンを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="3978b-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="3978b-168">Azure portal で **[ワークスペースの起動]** を選択して、Azure Databricks ワークスペースを起動します。</span><span class="sxs-lookup"><span data-stu-id="3978b-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Azure Databricks ワークスペースを起動する](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="3978b-170">ワークスペースのホーム ページで、 **[ユーザー設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Azure Databricks ワークスペースのユーザー設定](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="3978b-172">[ユーザー設定] ページで、新しいトークンを生成できます。</span><span class="sxs-lookup"><span data-stu-id="3978b-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="3978b-173">生成されたトークンをコピーして、コマンド プロンプトに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="3978b-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Azure Databricks ワークスペースで新しいアクセス トークンを生成する](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="3978b-175">これで、作成する Azure Databricks クラスターにアクセスして、DBFS にファイルをアップロードできるようになります。</span><span class="sxs-lookup"><span data-stu-id="3978b-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="3978b-176">ワーカーの依存関係のダウンロード</span><span class="sxs-lookup"><span data-stu-id="3978b-176">Download worker dependencies</span></span>

> [!Note]
> <span data-ttu-id="3978b-177">Azure と AWS Databricks は Linux ベースです。</span><span class="sxs-lookup"><span data-stu-id="3978b-177">Azure and AWS Databricks are Linux-based.</span></span> <span data-ttu-id="3978b-178">そのため、Databricks へのアプリのデプロイに関心がある場合は、アプリが .NET Standard と互換性があることと、アプリのコンパイルに .NET Core コンパイラを使用していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3978b-178">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use .NET Core compiler to compile your app.</span></span>

1. <span data-ttu-id="3978b-179">Microsoft.Spark.Worker は、自分で作成したユーザー定義関数 (UDF) などのアプリを Apache Spark で実行するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3978b-179">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="3978b-180">[Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="3978b-180">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span>

2. <span data-ttu-id="3978b-181">*install-worker.sh* は、.NET for Apache Spark 依存ファイルをクラスターのノードにコピーできるスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="3978b-181">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="3978b-182">ご使用のローカル コンピューターで、**install-worker.sh** という名前の新しいファイルを作成し、GitHub 上にある [install-worker.sh のコンテンツ](https://raw.githubusercontent.com/dotnet/spark/main/deployment/install-worker.sh)を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="3978b-182">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/main/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="3978b-183">*db-init.sh* は、依存関係を Databricks Spark クラスターにインストールするスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="3978b-183">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="3978b-184">ご使用のローカル コンピューターで、**db-init.sh** という名前の新しいファイルを作成し、GitHub 上にある [db-init.sh のコンテンツ](https://github.com/dotnet/spark/blob/main/deployment/db-init.sh)を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="3978b-184">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/main/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="3978b-185">先ほど作成したファイルで、`DOTNET_SPARK_RELEASE` 変数を `https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz` に設定します。</span><span class="sxs-lookup"><span data-stu-id="3978b-185">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz`.</span></span> <span data-ttu-id="3978b-186">*db-init.sh* ファイルの残りの部分はそのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="3978b-186">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="3978b-187">Windows を使用している場合は、*install-worker.sh* および *db-init.sh* スクリプト内の行の終わりが Unix 形式 (LF) であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3978b-187">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="3978b-188">行の終わりは、Notepad++ や Atom などのテキスト エディターを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="3978b-188">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="3978b-189">アプリケーションの発行</span><span class="sxs-lookup"><span data-stu-id="3978b-189">Publish your app</span></span>

<span data-ttu-id="3978b-190">次に、「[.NET for Apache Spark - 10 分で開始する](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)」のチュートリアルで作成した *mySparkApp* を発行し、自分の Spark クラスターから、アプリを実行するために必要なすべてのファイルにアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3978b-190">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="3978b-191">次のコマンドを実行して、*mySparkApp* を発行します。</span><span class="sxs-lookup"><span data-stu-id="3978b-191">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="3978b-192">発行したアプリケーション ファイルを Databricks Spark クラスターに簡単にアップロードできるように、次のタスクを実行してファイルを圧縮します。</span><span class="sxs-lookup"><span data-stu-id="3978b-192">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="3978b-193">**Windows の場合:**</span><span class="sxs-lookup"><span data-stu-id="3978b-193">**On Windows:**</span></span>

   <span data-ttu-id="3978b-194">mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64 に移動します。</span><span class="sxs-lookup"><span data-stu-id="3978b-194">Navigate to mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64.</span></span> <span data-ttu-id="3978b-195">次に、**発行** フォルダーを右クリックして、 **[送信先] > [圧縮 (zip 形式) フォルダー]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-195">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="3978b-196">新しいフォルダーに **publish.zip** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="3978b-196">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="3978b-197">**Linux の場合は、次のコマンドを実行します。**</span><span class="sxs-lookup"><span data-stu-id="3978b-197">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="3978b-198">ファイルのアップロード</span><span class="sxs-lookup"><span data-stu-id="3978b-198">Upload files</span></span>

<span data-ttu-id="3978b-199">このセクションでは、DBFS に複数のファイルをアップロードして、クラウドでアプリを実行するために必要なすべてのものがクラスターに含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="3978b-199">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="3978b-200">DBFS にファイルをアップロードするときは、そのつど、ご使用のコンピューター上でそのファイルがあるディレクトリにいることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3978b-200">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="3978b-201">次のコマンドを実行して、*db-init.sh*、*install-worker.sh*、*Microsoft.Spark.Worker* を DBFS にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="3978b-201">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz dbfs:/spark-dotnet/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz
   ```

2. <span data-ttu-id="3978b-202">次のコマンドを実行して、アプリを実行するためにクラスターに必要な残りのファイル (zip 形式の発行フォルダー、*input.txt*、*microsoft-spark-2-4_2.11-1.0.0.jar*) をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="3978b-202">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2-4_2.11-1.0.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.1\ubuntu.16.04-x64 directory
   databricks fs cp publish.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2-4_2.11-1.0.0.jar dbfs:/spark-dotnet/microsoft-spark-2-4_2.11-1.0.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="3978b-203">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="3978b-203">Create a job</span></span>

<span data-ttu-id="3978b-204">アプリは、**spark-submit** を実行するジョブを介して Azure Databricks で実行されます。spark-submit は、.NET for Apache Spark ジョブを実行するために使用するコマンドです。</span><span class="sxs-lookup"><span data-stu-id="3978b-204">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="3978b-205">Azure Databricks ワークスペースで、 **[ジョブ]** アイコンを選択し、次に **[+ ジョブの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-205">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Azure Databricks ジョブを作成する](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="3978b-207">ジョブのタイトルを選択し、 **[Configure spark-submit]\(spark-submit の構成\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-207">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Databricks ジョブの spark-submit を構成する](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="3978b-209">ジョブ構成に次のパラメーターを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="3978b-209">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="3978b-210">次に、 **[確認]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-210">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2-4_2.11-1.0.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="3978b-211">クラスターの作成</span><span class="sxs-lookup"><span data-stu-id="3978b-211">Create a cluster</span></span>

1. <span data-ttu-id="3978b-212">ジョブに移動し、 **[編集]** を選択して、ジョブのクラスターを構成します。</span><span class="sxs-lookup"><span data-stu-id="3978b-212">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="3978b-213">クラスターを **Spark 2.4.1** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3978b-213">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="3978b-214">次に、 **[詳細オプション]**  >  **[Init Scripts]\(Init スクリプト\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-214">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="3978b-215">Init スクリプトのパスを `dbfs:/spark-dotnet/db-init.sh` として設定します。</span><span class="sxs-lookup"><span data-stu-id="3978b-215">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Azure Databricks で Spark クラスターを構成する](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="3978b-217">**[確認]** を選択して、クラスターの設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="3978b-217">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="3978b-218">アプリの実行</span><span class="sxs-lookup"><span data-stu-id="3978b-218">Run your app</span></span>

1. <span data-ttu-id="3978b-219">ジョブに移動し、 **[今すぐ実行]** を選択して、新しく構成した Spark クラスターでジョブを実行します。</span><span class="sxs-lookup"><span data-stu-id="3978b-219">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="3978b-220">ジョブのクラスターが作成されるまで数分かかります。</span><span class="sxs-lookup"><span data-stu-id="3978b-220">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="3978b-221">作成されると、ジョブが送信され、出力を表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3978b-221">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="3978b-222">左側のメニューから **[クラスター]** を選択し、ジョブの名前と実行を選択します。</span><span class="sxs-lookup"><span data-stu-id="3978b-222">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="3978b-223">**[Driver Logs]\(ドライバー ログ\)** を選択して、ジョブの出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="3978b-223">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="3978b-224">アプリの実行が完了すると、標準出力コンソールに書き込まれた、「開始する」のローカル実行と同じ単語件数のテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3978b-224">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure Databricks ジョブ出力のテーブル](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="3978b-226">これで、初めての .NET for Apache Spark アプリケーションを Azure Databricks で実行できました。</span><span class="sxs-lookup"><span data-stu-id="3978b-226">Congratulations, you've run your first .NET for Apache Spark application in Azure Databricks!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="3978b-227">リソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="3978b-227">Clean up resources</span></span>

<span data-ttu-id="3978b-228">Databricks ワークスペースが不要になった場合は、Azure portal で Azure Databricks リソースを削除できます。</span><span class="sxs-lookup"><span data-stu-id="3978b-228">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="3978b-229">リソース グループ名を選び、リソース グループ ページを開いて、 **[リソース グループの削除]** を選ぶこともできます。</span><span class="sxs-lookup"><span data-stu-id="3978b-229">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3978b-230">次の手順</span><span class="sxs-lookup"><span data-stu-id="3978b-230">Next steps</span></span>

<span data-ttu-id="3978b-231">このチュートリアルでは、.NET for Apache Spark アプリケーションを Databricks にデプロイしました。</span><span class="sxs-lookup"><span data-stu-id="3978b-231">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="3978b-232">Databricks の詳細については、Azure Databricks のドキュメントに進んでください。</span><span class="sxs-lookup"><span data-stu-id="3978b-232">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3978b-233">Azure Databricks のドキュメント</span><span class="sxs-lookup"><span data-stu-id="3978b-233">Azure Databricks Documentation</span></span>](/azure/azure-databricks/)
