---
title: Azure での F# の使用
description: F# での Azure サービスの使用に関するガイド
author: sylvanc
ms.date: 07/29/2020
ms.custom: devx-track-fsharp
ms.openlocfilehash: 16599aa48776acee05edf8201cdd148a87507cdb
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899412"
---
# <a name="using-f-on-azure"></a><span data-ttu-id="6fbf1-103">Azure での F# の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-103">Using F# on Azure</span></span>

<span data-ttu-id="6fbf1-104">F# は卓越したクラウド プログラミング言語であり、Web アプリケーション、クラウド サービス、クラウドでホストされるマイクロ サービスの作成、および拡張性の高いデータの処理に頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-104">F# is a superb language for cloud programming and is frequently used to write web applications, cloud services, cloud-hosted microservices, and for scalable data processing.</span></span>

<span data-ttu-id="6fbf1-105">次のセクションでは、広範囲の Azure サービスで F# を使用する方法に関するリソースを紹介します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-105">In the following sections, you will find resources on how to use a range of Azure services with F#.</span></span>

> [!NOTE]
> <span data-ttu-id="6fbf1-106">特定の Azure サービスがこのドキュメント セットに記載されていない場合、そのサービスの Azure Functions または .NET のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-106">If a particular Azure service isn't in this documentation set, please consult either the Azure Functions or .NET documentation for that service.</span></span> <span data-ttu-id="6fbf1-107">言語に依存しない言語固有のドキュメントを必要としない一部の Azure サービスはここに記載されていません。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-107">Some Azure services are language-independent and require no language-specific documentation and are not listed here.</span></span>

## <a name="using-azure-virtual-machines-with-f"></a><span data-ttu-id="6fbf1-108">F\# での Azure Virtual Machines の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-108">Using Azure Virtual Machines with F\#</span></span>

<span data-ttu-id="6fbf1-109">Azure では、さまざまな仮想マシン (VM) の構成をサポートします。[Linux および Windows の仮想マシン](https://azure.microsoft.com/services/virtual-machines/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-109">Azure supports a wide range of virtual machine (VM) configurations, see [Linux and Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/).</span></span>

<span data-ttu-id="6fbf1-110">実行、コンパイル、スクリプト作成のために F# を仮想マシンにインストールするには、「[Using F# on Linux](https://fsharp.org/use/linux)」(Linux での F# の使用) および「[Using F# on Windows](https://fsharp.org/use/windows)」(Windows での F# の使用) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-110">To install F# on a virtual machine for execution, compilation and/or scripting see [Using F# on Linux](https://fsharp.org/use/linux) and [Using F# on Windows](https://fsharp.org/use/windows).</span></span>

## <a name="using-azure-functions-with-f"></a><span data-ttu-id="6fbf1-111">F\#での Azure Functions の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-111">Using Azure Functions with F\#</span></span>

<span data-ttu-id="6fbf1-112">[Azure Functions](https://azure.microsoft.com/services/functions/) を使用すると、クラウドで小さなコードの集まりまたは "関数" を簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-112">[Azure Functions](https://azure.microsoft.com/services/functions/) is a solution for easily running small pieces of code, or "functions," in the cloud.</span></span> <span data-ttu-id="6fbf1-113">問題を解決するために必要なコードのみを手元で作成することができます。アプリケーション全体またはコードを実行するためのインフラストラクチャについて心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-113">You can write just the code you need for the problem at hand, without worrying about a whole application or the infrastructure to run it.</span></span> <span data-ttu-id="6fbf1-114">関数は、Azure ストレージおよびその他のクラウドでホストされるリソースでイベントに接続されます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-114">Your functions are connected to events in Azure storage and other cloud-hosted resources.</span></span> <span data-ttu-id="6fbf1-115">データは、関数の引数を使用して F# 関数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-115">Data flows into your F# functions via function arguments.</span></span> <span data-ttu-id="6fbf1-116">必要に応じて任意の開発言語を使用し、スケールを Azure に任せることができます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-116">You can use your development language of choice, trusting Azure to scale as needed.</span></span>

<span data-ttu-id="6fbf1-117">Azure Functions は、F# を第一級の言語としてサポートし、F# コードを効率と拡張性に優れた方法で事後対応型で実行します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-117">Azure Functions support F# as a first-class language with efficient, reactive, scalable execution of F# code.</span></span> <span data-ttu-id="6fbf1-118">Azure Functions で F# を使用する方法のリファレンス ドキュメントについては、「[Azure Functions F# 開発者向けリファレンス](/azure/azure-functions/functions-reference-fsharp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-118">See the [Azure Functions F# Developer Reference](/azure/azure-functions/functions-reference-fsharp) for reference documentation on how to use F# with Azure Functions.</span></span>

<span data-ttu-id="6fbf1-119">Azure Functions と F# の使用に関する他のリソース:</span><span class="sxs-lookup"><span data-stu-id="6fbf1-119">Other resources for using Azure Functions and F#:</span></span>

* [<span data-ttu-id="6fbf1-120">Suave を使用した F# での Azure Functions のスケールアップ</span><span class="sxs-lookup"><span data-stu-id="6fbf1-120">Scale Up Azure Functions in F# Using Suave</span></span>](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [<span data-ttu-id="6fbf1-121">F# で Azure 関数を作成する方法</span><span class="sxs-lookup"><span data-stu-id="6fbf1-121">How to create Azure function in F#</span></span>](https://www.mnie.me/azurefunctions)
* [<span data-ttu-id="6fbf1-122">Azure Functions での Azure 型プロバイダーの使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-122">Using the Azure Type Provider with Azure Functions</span></span>](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a><span data-ttu-id="6fbf1-123">F\#での Azure Storage の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-123">Using Azure Storage with F\#</span></span>

<span data-ttu-id="6fbf1-124">Azure Storage は、顧客のニーズに合う耐久性、可用性、スケーラビリティを必要とする最新のアプリケーション向けのストレージ サービスの基本階層です。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-124">Azure Storage is a base layer of storage services for modern applications that rely on durability, availability, and scalability to meet the needs of customers.</span></span> <span data-ttu-id="6fbf1-125">F# プログラムは、次の記事で説明されている方法を使用して、Azure Storage サービスと直接やり取りできます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-125">F# programs can interact directly with Azure storage services, using the techniques described in the following articles.</span></span>

* [<span data-ttu-id="6fbf1-126">F# を使用した Azure Blob Storage の概要</span><span class="sxs-lookup"><span data-stu-id="6fbf1-126">Get started with Azure Blob Storage using F#</span></span>](blob-storage.md)
* [<span data-ttu-id="6fbf1-127">F# を使用した Azure File Storage の概要</span><span class="sxs-lookup"><span data-stu-id="6fbf1-127">Get started with Azure File Storage using F#</span></span>](file-storage.md)
* [<span data-ttu-id="6fbf1-128">F# を使用した Azure Queue Storage の概要</span><span class="sxs-lookup"><span data-stu-id="6fbf1-128">Get started with Azure Queue Storage using F#</span></span>](queue-storage.md)
* [<span data-ttu-id="6fbf1-129">F# を使用した Azure Table Storage の概要</span><span class="sxs-lookup"><span data-stu-id="6fbf1-129">Get started with Azure Table Storage using F#</span></span>](table-storage.md)

<span data-ttu-id="6fbf1-130">Azure Storage は、明示的な API 呼び出しではなく、宣言型の構成を使って Azure Functions と組み合わせても使用できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-130">Azure Storage can also be used in conjunction with Azure Functions through declarative configuration rather than explicit API calls.</span></span> <span data-ttu-id="6fbf1-131">F# の例を含む「[Azure Functions における Storage BLOB のバインド](/azure/azure-functions/functions-bindings-storage)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-131">See [Azure Functions triggers and bindings for Azure Storage](/azure/azure-functions/functions-bindings-storage) which includes F# examples.</span></span>

## <a name="using-azure-app-service-with-f"></a><span data-ttu-id="6fbf1-132">F\#での Azure App Service の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-132">Using Azure App Service with F\#</span></span>

<span data-ttu-id="6fbf1-133">[Azure App Service](https://azure.microsoft.com/services/app-service/) は、クラウドまたはオンプレミスでどこにでもデータに接続する強力な Web アプリおよびモバイル アプリをビルドするためのクラウド プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-133">[Azure App Service](https://azure.microsoft.com/services/app-service/) is a cloud platform to build powerful web and mobile apps that connect to data anywhere, in the cloud or on-premises.</span></span>

* [<span data-ttu-id="6fbf1-134">F# Azure Web API の例</span><span class="sxs-lookup"><span data-stu-id="6fbf1-134">F# Azure Web API example</span></span>](https://github.com/fsprojects/azure-webapi-example)
* [<span data-ttu-id="6fbf1-135">Azure 上の web アプリケーションでの F# のホスト</span><span class="sxs-lookup"><span data-stu-id="6fbf1-135">Hosting F# in a web application on Azure</span></span>](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-on-azure-hdinsight-or-azure-databricks"></a><span data-ttu-id="6fbf1-136">Azure HDInsight または Azure Databricks での F# での Apache Spark の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-136">Using Apache Spark with F# on Azure HDInsight or Azure Databricks</span></span>

<span data-ttu-id="6fbf1-137">[Apache Spark for Azure HDInsight](/azure/hdinsight/spark/apache-spark-overview) は、大規模なデータ分析アプリケーションを実行するオープン ソースの処理のフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-137">[Apache Spark for Azure HDInsight](/azure/hdinsight/spark/apache-spark-overview) is an open source processing framework that runs large-scale data analytics applications.</span></span> <span data-ttu-id="6fbf1-138">[Azure Databricks](/azure/databricks/scenarios/what-is-azure-databricks) は、Microsoft Azure クラウド サービス プラットフォーム用に最適化された Apache Spark ベースの分析プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-138">[Azure Databricks](/azure/databricks/scenarios/what-is-azure-databricks) is an Apache Spark-based analytics platform optimized for the Microsoft Azure cloud services platform.</span></span> <span data-ttu-id="6fbf1-139">Azure では、Apache Spark は簡単かつ低コストで展開できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-139">Azure makes Apache Spark easy and cost effective to deploy.</span></span> <span data-ttu-id="6fbf1-140">Apache Spark に対する .Net の一連のバインドである [.NET for Apache Spark](../../spark/what-is-apache-spark-dotnet.md) を使用して、ご自分の Spark アプリケーションを F# で開発できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-140">Develop your Spark application in F# using [.NET for Apache Spark](../../spark/what-is-apache-spark-dotnet.md), a set of .NET bindings for Apache Spark.</span></span>

* [<span data-ttu-id="6fbf1-141">.NET for Apache Spark の F# のサンプル</span><span class="sxs-lookup"><span data-stu-id="6fbf1-141">.NET for Apache Spark F# samples</span></span>](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.FSharp.Examples)
* [<span data-ttu-id="6fbf1-142">Azure HDInsight に .NET Interactive Jupyter ノートブックをインストールする</span><span class="sxs-lookup"><span data-stu-id="6fbf1-142">Install .NET Interactive Jupyter notebooks in Azure HDInsight</span></span>](../../spark/how-to-guides/hdinsight-notebook-installation.md)
* [<span data-ttu-id="6fbf1-143">Azure HDInsight に Apache Spark ジョブの送信する</span><span class="sxs-lookup"><span data-stu-id="6fbf1-143">Submit Apache Spark jobs to Azure HDInsight</span></span>](../../spark/how-to-guides/hdinsight-deploy-methods.md)
* [<span data-ttu-id="6fbf1-144">Azure Databricks に Apache Spark ジョブの送信する</span><span class="sxs-lookup"><span data-stu-id="6fbf1-144">Submit Apache Spark jobs to Azure Databricks</span></span>](../../spark/how-to-guides/databricks-deploy-methods.md)

## <a name="using-azure-cosmos-db-with-f"></a><span data-ttu-id="6fbf1-145">F\# での Azure Cosmos DB の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-145">Using Azure Cosmos DB with F\#</span></span>

<span data-ttu-id="6fbf1-146">[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) は、可用性が高く世界各地に分散されたアプリ向けの NoSQL サービスです。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-146">[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) is a NoSQL service for highly available, globally distributed apps.</span></span>

<span data-ttu-id="6fbf1-147">Azure Cosmos DB は、2 つの方法で F# で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-147">Azure Cosmos DB can be used with F# in two ways:</span></span>

1. <span data-ttu-id="6fbf1-148">Azure Cosmos DB コレクションに対する変更に反応するか変更を発生させる F# Azure Functions を作成する。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-148">Through the creation of F# Azure Functions which react to or cause changes to Azure Cosmos DB collections.</span></span> <span data-ttu-id="6fbf1-149">「[Azure Functions の Azure Cosmos DB バインド](/azure/azure-functions/functions-bindings-cosmosdb)」を参照してください。または</span><span class="sxs-lookup"><span data-stu-id="6fbf1-149">See [Azure Cosmos DB bindings for Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb), or</span></span>
2. <span data-ttu-id="6fbf1-150">[Azure Cosmos DB .NET SDK for SQL API](/azure/cosmos-db/sql-api-sdk-dotnet) を使用する。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-150">By using the [Azure Cosmos DB .NET SDK for SQL API](/azure/cosmos-db/sql-api-sdk-dotnet).</span></span> <span data-ttu-id="6fbf1-151">関連するサンプルが C# であります。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-151">The related samples are in C#.</span></span>

## <a name="using-azure-event-hubs-with-f"></a><span data-ttu-id="6fbf1-152">F\# での Azure Event Hubs の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-152">Using Azure Event Hubs with F\#</span></span>

<span data-ttu-id="6fbf1-153">[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) は、Web サイト、アプリケーション、およびデバイスからのクラウド スケール テレメトリの取り込みを提供します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-153">[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) provide cloud-scale telemetry ingestion from websites, apps, and devices.</span></span>

<span data-ttu-id="6fbf1-154">Azure Event Hubs は、2 つの方法で F# で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-154">Azure Event Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="6fbf1-155">イベントによってトリガーされる F# Azure Functions を作成します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-155">Through the creation of F# Azure Functions which are triggered by events.</span></span> <span data-ttu-id="6fbf1-156">「[Azure Functions における Event Hub のバインド](/azure/azure-functions/functions-bindings-event-hubs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-156">See [Azure Function triggers for Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), or</span></span>
2. <span data-ttu-id="6fbf1-157">または、[.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted) を使用します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-157">By using the [.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted).</span></span> <span data-ttu-id="6fbf1-158">これらの例は C# であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-158">Note these examples are in C#.</span></span>

## <a name="using-azure-notification-hubs-with-f"></a><span data-ttu-id="6fbf1-159">F\# での Azure Notification Hubs の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-159">Using Azure Notification Hubs with F\#</span></span>

<span data-ttu-id="6fbf1-160">[Azure Notification Hubs](/azure/notification-hubs/) は、任意のバックエンド (クラウドまたはオンプレミス) から任意のモバイル プラットフォームにモバイル プッシュ通知を送信するためのマルチプラット フォームに対応するスケール アウト プッシュ インフラストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-160">[Azure Notification Hubs](/azure/notification-hubs/) are multiplatform, scaled-out push infrastructure that enable you to send mobile push notifications from any backend (in the cloud or on-premises) to any mobile platform.</span></span>

<span data-ttu-id="6fbf1-161">Azure Notification Hubs は、2 つの方法で F# で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-161">Azure Notification Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="6fbf1-162">通知ハブに結果を送信する F# Azure Functions を作成します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-162">Through the creation of F# Azure Functions which send results to a notification hub.</span></span> <span data-ttu-id="6fbf1-163">「[Azure Functions における通知ハブの出力バインド](/azure/azure-functions/functions-bindings-notification-hubs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-163">See [Azure Function output triggers for Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), or</span></span>
2. <span data-ttu-id="6fbf1-164">または、[.NET SDK for Azure](/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend) を使用します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-164">By using the [.NET SDK for Azure](/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend).</span></span> <span data-ttu-id="6fbf1-165">これらの例は C# であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-165">Note these examples are in C#.</span></span>

## <a name="implementing-webhooks-on-azure-with-f"></a><span data-ttu-id="6fbf1-166">Azure と F\# での Webhook の実装</span><span class="sxs-lookup"><span data-stu-id="6fbf1-166">Implementing WebHooks on Azure with F\#</span></span>

<span data-ttu-id="6fbf1-167">[Webhook](https://en.wikipedia.org/wiki/Webhook)は、Web 要求によってトリガーされるコールバックです。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-167">A [Webhook](https://en.wikipedia.org/wiki/Webhook) is a callback triggered via a web request.</span></span> <span data-ttu-id="6fbf1-168">Webhook は、GitHub などのサイトでイベントを通知するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-168">Webhooks are used by sites such as GitHub to signal events.</span></span>

<span data-ttu-id="6fbf1-169">[Azure Function F# と Webhook バインド](/azure/azure-functions/functions-bindings-http-webhook)を使用して、Webhook を F# で実装し、Azure でホストすることができます。します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-169">Webhooks can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Webhook Binding](/azure/azure-functions/functions-bindings-http-webhook).</span></span>

## <a name="using-webjobs-with-f"></a><span data-ttu-id="6fbf1-170">F\# での Webjobs の使用</span><span class="sxs-lookup"><span data-stu-id="6fbf1-170">Using Webjobs with F\#</span></span>

<span data-ttu-id="6fbf1-171">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) は、オンデマンド、継続的、またはスケジュール指定の 3 つの方法で App Service Web アプリで実行できるプログラムです。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-171">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) are programs you can run in your App Service web app in three ways: on demand, continuously, or on a schedule.</span></span>

[<span data-ttu-id="6fbf1-172">F# Webjob の例</span><span class="sxs-lookup"><span data-stu-id="6fbf1-172">Example F# Webjob</span></span>](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a><span data-ttu-id="6fbf1-173">Azure と F\# でのタイマーの実装</span><span class="sxs-lookup"><span data-stu-id="6fbf1-173">Implementing Timers on Azure with F\#</span></span>

<span data-ttu-id="6fbf1-174">タイマーは、スケジュールに従って、1 回または定期的に呼び出し関数をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-174">Timer triggers call functions based on a schedule, one time or recurring.</span></span>

<span data-ttu-id="6fbf1-175">[Azure Function F# とタイマー トリガー](/azure/azure-functions/functions-bindings-timer)を使用して、タイマーを F# で実装し、Azure でホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-175">Timers can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Timer Trigger](/azure/azure-functions/functions-bindings-timer).</span></span>

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a><span data-ttu-id="6fbf1-176">F# スクリプトを使用した Azure リソースの展開と管理</span><span class="sxs-lookup"><span data-stu-id="6fbf1-176">Deploying and Managing Azure Resources with F# Scripts</span></span>

<span data-ttu-id="6fbf1-177">Azure VM はプログラムで展開し、Microsoft.Azure.Management パッケージと API を使用して、F# スクリプトから管理します。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-177">Azure VMs may be programmatically deployed and managed from F# scripts by using the Microsoft.Azure.Management packages and APIs.</span></span> <span data-ttu-id="6fbf1-178">例については、「[.NET の管理ライブラリの概要](/previous-versions/azure/dn722415(v=azure.100))」と[Azure Resource Manager の使用](/azure/azure-resource-manager/resource-manager-deployment-model)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-178">For example, see [Get Started with the Management Libraries for .NET](/previous-versions/azure/dn722415(v=azure.100)) and [Using Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).</span></span>

<span data-ttu-id="6fbf1-179">同様に、他の Azure リソースも同じコンポーネントを使用して、F# スクリプトから展開および管理できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-179">Likewise, other Azure resources may also be deployed and managed from F# scripts using the same components.</span></span> <span data-ttu-id="6fbf1-180">たとえば、F# スクリプトからプログラム的に、ストレージ アカウントの作成、Azure Cloud Services のデプロイ、Azure Cosmos DB インスタンスの作成、Azure Notification Hubs の管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-180">For example, you can create storage accounts, deploy Azure Cloud Services, create Azure Cosmos DB instances and manage Azure Notification Hubs programmatically from F# scripts.</span></span>

<span data-ttu-id="6fbf1-181">F# スクリプトを使用したリソースの展開および管理は、通常必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-181">Using F# scripts to deploy and manage resources is not normally necessary.</span></span> <span data-ttu-id="6fbf1-182">たとえば、Azure リソースは JSON テンプレートの説明から直接デプロイすることもでき、これをパラメーター化できます。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-182">For example, Azure resources may also be deployed directly from JSON template descriptions, which can be parameterized.</span></span> <span data-ttu-id="6fbf1-183">[Azure クイック スタート テンプレート](https://azure.microsoft.com/resources/templates/)などの例を含む[Azure Resource Manager テンプレート](/azure/azure-resource-manager/resource-manager-template-best-practices)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbf1-183">See [Azure Resource Manager Templates](/azure/azure-resource-manager/resource-manager-template-best-practices) including examples such as the [Azure Quickstart Templates](https://azure.microsoft.com/resources/templates/).</span></span>

## <a name="other-resources"></a><span data-ttu-id="6fbf1-184">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="6fbf1-184">Other resources</span></span>

* [<span data-ttu-id="6fbf1-185">すべての Azure サービスのドキュメント</span><span class="sxs-lookup"><span data-stu-id="6fbf1-185">Full documentation on all Azure services</span></span>](/azure/)
