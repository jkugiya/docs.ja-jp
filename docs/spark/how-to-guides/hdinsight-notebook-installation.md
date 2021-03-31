---
title: Azure HDInsight Spark クラスター上の Jupyter Notebook に .NET for Apache Spark をインストールする
description: Azure HDInsight の Jupyter Notebook に .NET for Apache Spark をインストールする方法について説明します。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: b84d61c29d2b2aa7a9fee20a8af9f3eee23f7e8b
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605478"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="87cf6-103">Azure HDInsight Spark クラスター上の Jupyter Notebook に .NET for Apache Spark をインストールする</span><span class="sxs-lookup"><span data-stu-id="87cf6-103">Install .NET for Apache Spark on Jupyter Notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="87cf6-104">この記事では、Azure HDInsight Spark クラスター上の Jupyter Notebook に .NET for Apache Spark をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-104">This article teaches you how to install .NET for Apache Spark on Jupyter Notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="87cf6-105">コマンド ラインと Azure portal を組み合わせて、Azure HDInsight クラスターに .NET for Apache Spark をデプロイすることができます (詳しくは [Azure HDInsight に .NET for Apache Spark アプリケーションをデプロイする方法](../tutorials/hdinsight-deployment.md)に関する記事を参照)。ただし、ノートブックにはより対話的で反復的なエクスペリエンスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="87cf6-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="87cf6-106">Azure HDInsight クラスターには既に Jupyter Notebook が付属しているため、.NET for Apache Spark を実行するように Jupyter Notebook を構成するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="87cf6-106">Azure HDInsight clusters already come with Jupyter Notebooks, so all you have to do is configure the Jupyter Notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="87cf6-107">Jupyter Notebook で .NET for Apache Spark を使用する場合、C# コードを 1 行ずつ実行し、必要に応じて実行状態を維持するために、C# REPL が必要です。</span><span class="sxs-lookup"><span data-stu-id="87cf6-107">To use .NET for Apache Spark in your Jupyter Notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="87cf6-108">[Try .NET](https://github.com/dotnet/try) は、公式の .NET REPL として統合されています。</span><span class="sxs-lookup"><span data-stu-id="87cf6-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="87cf6-109">Jupyter Notebook のエクスペリエンスを通じて .NET for Apache Spark を有効にするには、[Ambari](/azure/hdinsight/hdinsight-hadoop-manage-ambari) を使用したいくつかの手動の手順に従い、HDInsight Spark クラスターで[スクリプト アクション](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="87cf6-110">この機能は "*試験段階*" であり、HDInsight Spark チームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="87cf6-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="87cf6-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="87cf6-111">Prerequisites</span></span>

<span data-ttu-id="87cf6-112">まだお持ちでない場合は、[Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) クラスターを作成します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-112">If you don't already have one, create an [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="87cf6-113">[Azure portal](https://portal.azure.com) にアクセスし、 **[+ リソースの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="87cf6-114">新しい Azure HDInsight クラスターのリソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="87cf6-115">クラスターの作成中に、**Spark 2.4** と **HDI 4.0** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="87cf6-116">.NET for Apache Spark のインストール</span><span class="sxs-lookup"><span data-stu-id="87cf6-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="87cf6-117">Azure portal で、前の手順で作成した **HDInsight Spark クラスター** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="87cf6-118">Livy サーバーを停止する</span><span class="sxs-lookup"><span data-stu-id="87cf6-118">Stop the Livy server</span></span>

1. <span data-ttu-id="87cf6-119">ポータルで **[概要]** を選択した後、 **[Ambari ホーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="87cf6-120">入力を求められたら、クラスターのログイン資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![クラスター ダッシュボードで [Ambari ホーム] を選択する](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="87cf6-122">左側のナビゲーション メニューから **[Spark2]** を選択し、 **[LIVY FOR SPARK2 SERVER]\(Spark2 の Livy サーバー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![[LIVY FOR SPARK2 SERVER] を選択する](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="87cf6-124">**hn0 で始まるホスト** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-124">Select **hn0... host**.</span></span>

   !["hno..." が示されているホストが選択されている](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="87cf6-126">**[Livy for Spark2 Server]\(Spark2 の Livy サーバー\)** の横にある省略記号を選択し、 **[停止]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="87cf6-127">メッセージが表示されたら、 **[OK]** を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="87cf6-128">Spark2 の Livy サーバーを停止します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="87cf6-129">![省略記号、[停止] の順に選択する](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="87cf6-129">![Select the ellipsis and then Stop](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="87cf6-130">**hn1 で始まるホスト** に対して前の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="87cf6-131">HDInsight スクリプト アクションを送信する</span><span class="sxs-lookup"><span data-stu-id="87cf6-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="87cf6-132">`install-interactive-notebook.sh` は、.NET for Apache Spark をインストールし、Apache Livy と sparkmagic に変更を加えるスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="87cf6-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="87cf6-133">スクリプト アクションを HDInsight に送信する前に、`install-interactive-notebook.sh` を作成してアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="87cf6-134">ご自分のローカル コンピューターに **install-interactive-notebook.sh** という名前の新しいファイルを作成し、[install-interactive-notebook.sh の内容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="87cf6-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="87cf6-135">このスクリプトを、HDInsight クラスターからアクセスできる [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="87cf6-135">Upload the script to a [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="87cf6-136">たとえば、`https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh` のようにします。</span><span class="sxs-lookup"><span data-stu-id="87cf6-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="87cf6-137">[HDInsight スクリプト アクション](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)を使用して、クラスターで `install-interactive-notebook.sh` を実行します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="87cf6-138">Azure portal で HDI クラスターに戻り、左側のオプションから **[スクリプト アクション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="87cf6-139">HDInsight Spark クラスターに .NET for Apache Spark の REPL をデプロイするためのスクリプト アクションを 1 つ送信します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="87cf6-140">次の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-140">Use the following settings:</span></span>

   |<span data-ttu-id="87cf6-141">プロパティ</span><span class="sxs-lookup"><span data-stu-id="87cf6-141">Property</span></span>  |<span data-ttu-id="87cf6-142">説明</span><span class="sxs-lookup"><span data-stu-id="87cf6-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="87cf6-143">スクリプトの種類</span><span class="sxs-lookup"><span data-stu-id="87cf6-143">Script type</span></span> | <span data-ttu-id="87cf6-144">カスタム</span><span class="sxs-lookup"><span data-stu-id="87cf6-144">Custom</span></span> |
   | <span data-ttu-id="87cf6-145">名前</span><span class="sxs-lookup"><span data-stu-id="87cf6-145">Name</span></span> | <span data-ttu-id="87cf6-146">" *.NET for Apache Spark 対話型 Notebook エクスペリエンスをインストールする*"</span><span class="sxs-lookup"><span data-stu-id="87cf6-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="87cf6-147">Bash スクリプト URI</span><span class="sxs-lookup"><span data-stu-id="87cf6-147">Bash script URI</span></span> | <span data-ttu-id="87cf6-148">`install-interactive-notebook.sh` のアップロード先の URI。</span><span class="sxs-lookup"><span data-stu-id="87cf6-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="87cf6-149">ノードの種類</span><span class="sxs-lookup"><span data-stu-id="87cf6-149">Node type(s)</span></span>| <span data-ttu-id="87cf6-150">ヘッド、ワーカー</span><span class="sxs-lookup"><span data-stu-id="87cf6-150">Head and Worker</span></span> |
   | <span data-ttu-id="87cf6-151">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87cf6-151">Parameters</span></span> | <span data-ttu-id="87cf6-152">.NET for Apache Spark のバージョン。</span><span class="sxs-lookup"><span data-stu-id="87cf6-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="87cf6-153">[.NET for Apache Spark のリリース](https://github.com/dotnet/spark/releases)を確認できます。</span><span class="sxs-lookup"><span data-stu-id="87cf6-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="87cf6-154">たとえば、Sparkdotnet バージョン 1.0.0 をインストールする場合は、`1.0.0` とします。</span><span class="sxs-lookup"><span data-stu-id="87cf6-154">For example, if you want to install Sparkdotnet version 1.0.0 then it would be `1.0.0`.</span></span>

   <span data-ttu-id="87cf6-155">スクリプト アクションの状態の横に緑色のチェックマークが表示されたら、次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="87cf6-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="87cf6-156">Livy サーバーを起動する</span><span class="sxs-lookup"><span data-stu-id="87cf6-156">Start the Livy server</span></span>

<span data-ttu-id="87cf6-157">「[Livy サーバーを停止する](#stop-the-livy-server)」セクションの手順に従って、ホスト **hn0** と **hn1** に対して Spark2 の Livy サーバーを **[開始]** ( **[停止]** ではなく) します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="87cf6-158">Spark の既定の構成を設定する</span><span class="sxs-lookup"><span data-stu-id="87cf6-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="87cf6-159">ポータルで **[概要]** を選択した後、 **[Ambari ホーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="87cf6-160">入力を求められたら、クラスターのログイン資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="87cf6-161">**[Spark2]** 、 **[CONFIGS]\(構成\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="87cf6-162">次に、 **[Custom spark2-defaults]\(カスタム Spark2 既定値\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Ambari の [構成] タブ](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="87cf6-164">**[プロパティの追加]** を選択して、Spark の既定の設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-164">Select **Add Property** to add Spark default settings.</span></span>

   ![プロパティの追加](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="87cf6-166">個別のプロパティが 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-166">There are three individual properties.</span></span> <span data-ttu-id="87cf6-167">単一プロパティの追加モードで、**TEXT** プロパティの型を使用して、一度に 1 つずつ追加します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="87cf6-168">いずれのキーまたは値の前後にも、余分なスペースがないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="87cf6-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="87cf6-169">**プロパティ 1**</span><span class="sxs-lookup"><span data-stu-id="87cf6-169">**Property 1**</span></span>
       * <span data-ttu-id="87cf6-170">キー: &ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="87cf6-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="87cf6-171">値: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="87cf6-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="87cf6-172">**プロパティ 2** 前のスクリプト アクションに含めた .NET for Apache Spark のバージョンを使用してください。</span><span class="sxs-lookup"><span data-stu-id="87cf6-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="87cf6-173">キー: &ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="87cf6-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="87cf6-174">値: `["nuget: Microsoft.Spark, 1.0.0", "nuget: Microsoft.Spark.Extensions.Delta, 1.0.0"]`</span><span class="sxs-lookup"><span data-stu-id="87cf6-174">Value: `["nuget: Microsoft.Spark, 1.0.0", "nuget: Microsoft.Spark.Extensions.Delta, 1.0.0"]`</span></span>

   * <span data-ttu-id="87cf6-175">**プロパティ 3**</span><span class="sxs-lookup"><span data-stu-id="87cf6-175">**Property 3**</span></span>
       * <span data-ttu-id="87cf6-176">キー: &ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="87cf6-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="87cf6-177">値: `try`</span><span class="sxs-lookup"><span data-stu-id="87cf6-177">Value: `try`</span></span>

   <span data-ttu-id="87cf6-178">たとえば、次の画像は、プロパティ 1 を追加するための設定をキャプチャしたものです。</span><span class="sxs-lookup"><span data-stu-id="87cf6-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Text プロパティの追加](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="87cf6-180">3 つのプロパティを追加したら、 **[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="87cf6-181">構成の推奨事項に関する警告画面が表示された場合は、 **[PROCEED ANYWAY]\(警告を無視して続行\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="87cf6-182">影響を受けたコンポーネントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-182">Restart affected components.</span></span>

   <span data-ttu-id="87cf6-183">新しいプロパティを追加したら、その変更の影響を受けたコンポーネントを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="87cf6-184">上部にある **[再起動]** を選択して、ドロップダウンから **[影響を受けるものをすべて再起動する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![[再起動] > [影響を受けるものをすべて再起動する] が強調表示された [構成] タブ](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="87cf6-186">メッセージが表示されたら、 **[CONFIRM RESTART ALL]\(すべて再起動\)** を選択して続行し、 **[OK]** をクリックして完了します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="87cf6-187">Jupyter Notebook を使用してジョブを送信する</span><span class="sxs-lookup"><span data-stu-id="87cf6-187">Submit jobs through a Jupyter Notebook</span></span>

<span data-ttu-id="87cf6-188">前の手順を完了したら、Jupyter Notebook を使用して .NET for Apache Spark ジョブを送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter Notebooks.</span></span>

1. <span data-ttu-id="87cf6-189">新しい .NET for Apache Spark ノートブックを作成します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="87cf6-190">Azure portal で、HDI クラスターから Jupyter Notebook を起動します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-190">Launch a Jupyter Notebook from your HDI cluster in the Azure portal.</span></span>

   ![Jupyter Notebook を起動する](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="87cf6-192">次に、 **[新規]**  >  **[.NET Spark (C#)]** の順に選択して、ノートブックを作成します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="87cf6-194">.NET for Apache Spark を使用してジョブを送信します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="87cf6-195">次のコード スニペットを使用して、データフレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![コマンドの実行を示すデータフレームを作成する](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="87cf6-197">次のコード スニペットを使用して、ユーザー定義関数 (UDF) を登録し、データフレームを指定してその UDF を使用します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![UDF を登録して使用する](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="87cf6-199">次の手順</span><span class="sxs-lookup"><span data-stu-id="87cf6-199">Next steps</span></span>

* [<span data-ttu-id="87cf6-200">.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする</span><span class="sxs-lookup"><span data-stu-id="87cf6-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="87cf6-201">HDInsight のドキュメント</span><span class="sxs-lookup"><span data-stu-id="87cf6-201">HDInsight Documentation</span></span>](/azure/hdinsight/)
