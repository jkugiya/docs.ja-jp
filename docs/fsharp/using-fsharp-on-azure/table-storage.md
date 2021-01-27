---
title: F を使用して Azure Table Storage を使ってみる#
description: Azure Table Storage または Azure Cosmos DB を使用して、構造化データをクラウドに格納します。
author: sylvanc
ms.date: 03/26/2018
ms.custom: devx-track-fsharp
ms.openlocfilehash: bc8e111636013930f7c7d4f59d1ef0720298cb9f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899283"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="126e4-103">F を使用して Azure Table Storage と Azure Cosmos DB Table API を使ってみる\#</span><span class="sxs-lookup"><span data-stu-id="126e4-103">Get started with Azure Table Storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="126e4-104">Azure Table Storage は、構造化された NoSQL データをクラウドに格納するサービスです。</span><span class="sxs-lookup"><span data-stu-id="126e4-104">Azure Table Storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="126e4-105">Table Storage は、スキーマなしの設計によるキーまたは属性ストアです。</span><span class="sxs-lookup"><span data-stu-id="126e4-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="126e4-106">Table Storage はスキーマがないため、アプリケーションの進化のニーズに合わせてデータを容易に修正できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="126e4-107">あらゆる種類のデータに、高速かつ経済的にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="126e4-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="126e4-108">Table Storage は、通常、従来の SQL と比較して、同様の容量のデータをはるかに低コストで保存できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="126e4-109">テーブル ストレージを使用すると、Web アプリケーションのユーザー データ、アドレス帳、デバイス情報、およびサービスに必要なその他の種類のメタデータなど、柔軟なデータセットを保存できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="126e4-110">ストレージ アカウントの容量の上限を超えない限り、テーブルには任意の数のエンティティを保存でき、ストレージ アカウントには任意の数のテーブルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="126e4-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="126e4-111">Azure Cosmos DB は、Azure Table Storage 向けに作成され、次のような premium 機能を必要とするアプリケーションの Table API を提供します。</span><span class="sxs-lookup"><span data-stu-id="126e4-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table Storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="126e4-112">ターンキー グローバル配信。</span><span class="sxs-lookup"><span data-stu-id="126e4-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="126e4-113">世界規模での専用スループット。</span><span class="sxs-lookup"><span data-stu-id="126e4-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="126e4-114">99 パーセンタイルで 10 ミリ秒未満の待ち時間。</span><span class="sxs-lookup"><span data-stu-id="126e4-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="126e4-115">高可用性の保証。</span><span class="sxs-lookup"><span data-stu-id="126e4-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="126e4-116">自動セカンダリ インデックス作成。</span><span class="sxs-lookup"><span data-stu-id="126e4-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="126e4-117">Azure Table Storage 用に作成されたアプリケーションは、コードを変更せずに Table API を使用して Azure Cosmos DB に移行し、premium 機能を活用できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-117">Applications written for Azure Table Storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="126e4-118">Table API には、.NET、Java、Python、および Node.js で利用可能なクライアント SDK があります。</span><span class="sxs-lookup"><span data-stu-id="126e4-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="126e4-119">詳細については、「 [Azure Cosmos DB Table API の概要](/azure/cosmos-db/table-introduction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="126e4-119">For more information, see [Introduction to Azure Cosmos DB Table API](/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="126e4-120">このチュートリアルについて</span><span class="sxs-lookup"><span data-stu-id="126e4-120">About this tutorial</span></span>

<span data-ttu-id="126e4-121">このチュートリアルでは、Azure Table Storage または Azure Cosmos DB Table API を使用して、テーブルの作成と削除、テーブルデータの挿入、更新、削除、クエリなど、いくつかの一般的なタスクを実行する F # コードを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="126e4-121">This tutorial shows how to write F# code to do some common tasks using Azure Table Storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="126e4-122">前提条件</span><span class="sxs-lookup"><span data-stu-id="126e4-122">Prerequisites</span></span>

<span data-ttu-id="126e4-123">このガイドを使用するには、最初に [Azure ストレージアカウント](/azure/storage/storage-create-storage-account) または [Azure Cosmos DB アカウント](https://azure.microsoft.com/try/cosmosdb/)を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="126e4-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="126e4-124">F # スクリプトを作成して F# インタラクティブを開始する</span><span class="sxs-lookup"><span data-stu-id="126e4-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="126e4-125">この記事のサンプルは、F # アプリケーションと F # スクリプトのどちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="126e4-126">F # スクリプトを作成するには、 `.fsx` `tables.fsx` f # 開発環境で、などの拡張子を持つファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="126e4-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="126e4-127">次に、[パケット](https://fsprojects.github.io/Paket/)や[NuGet](https://www.nuget.org/)などの[パッケージマネージャー](package-management.md)を使用して、 `WindowsAzure.Storage` ディレクティブを使用してスクリプトにパッケージと参照をインストールし `WindowsAzure.Storage.dll` `#r` ます。</span><span class="sxs-lookup"><span data-stu-id="126e4-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="126e4-128">Microsoft Azure 名前空間を取得するために、に対してもう一度実行し `Microsoft.WindowsAzure.ConfigurationManager` ます。</span><span class="sxs-lookup"><span data-stu-id="126e4-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="126e4-129">名前空間宣言の追加</span><span class="sxs-lookup"><span data-stu-id="126e4-129">Add namespace declarations</span></span>

<span data-ttu-id="126e4-130">次の `open` ステートメントを `tables.fsx` ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="126e4-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="126e4-131">Azure Storage 接続文字列を取得する</span><span class="sxs-lookup"><span data-stu-id="126e4-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="126e4-132">Azure Storage Table service に接続している場合は、このチュートリアルで使用する接続文字列が必要になります。</span><span class="sxs-lookup"><span data-stu-id="126e4-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="126e4-133">Azure portal から接続文字列をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="126e4-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="126e4-134">接続文字列の詳細については、「 [ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="126e4-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="126e4-135">Azure Cosmos DB 接続文字列を取得する</span><span class="sxs-lookup"><span data-stu-id="126e4-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="126e4-136">Azure Cosmos DB に接続している場合は、このチュートリアルで使用する接続文字列が必要になります。</span><span class="sxs-lookup"><span data-stu-id="126e4-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="126e4-137">Azure portal から接続文字列をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="126e4-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="126e4-138">Azure portal の Cosmos DB アカウントで、[**設定**  >  ] [**接続文字列**] にアクセスし、[**コピー** ] ボタンを選択してプライマリ接続文字列をコピーします。</span><span class="sxs-lookup"><span data-stu-id="126e4-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and select the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="126e4-139">このチュートリアルでは、次の例のように、スクリプトに接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="126e4-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="126e4-140">ただし、実際のプロジェクトではこの方法は **お勧めできません** 。</span><span class="sxs-lookup"><span data-stu-id="126e4-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="126e4-141">ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="126e4-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="126e4-142">ストレージ アカウント キーは常に慎重に保護してください。</span><span class="sxs-lookup"><span data-stu-id="126e4-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="126e4-143">このキーを他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーン テキスト ファイルに保存したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="126e4-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="126e4-144">侵害された可能性があると思われる場合は、Azure portal を使用してキーを再生成することができます。</span><span class="sxs-lookup"><span data-stu-id="126e4-144">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="126e4-145">実際のアプリケーションでは、ストレージ接続文字列を維持する最善の方法は構成ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="126e4-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="126e4-146">構成ファイルから接続文字列を取得するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="126e4-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="126e4-147">Azure Configuration Manager の使用はオプションです。</span><span class="sxs-lookup"><span data-stu-id="126e4-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="126e4-148">.NET Framework の型などの API を使用することもでき `ConfigurationManager` ます。</span><span class="sxs-lookup"><span data-stu-id="126e4-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="126e4-149">接続文字列を解析する</span><span class="sxs-lookup"><span data-stu-id="126e4-149">Parse the connection string</span></span>

<span data-ttu-id="126e4-150">接続文字列を解析するには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="126e4-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="126e4-151">これにより、が返さ `CloudStorageAccount` れます。</span><span class="sxs-lookup"><span data-stu-id="126e4-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="126e4-152">Table service クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="126e4-152">Create the Table service client</span></span>

<span data-ttu-id="126e4-153">クラスを使用すると、 `CloudTableClient` テーブルストレージ内のテーブルとエンティティを取得できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="126e4-154">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="126e4-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="126e4-155">これで、Table Storage に対してデータの読み取りと書き込みを実行するコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="126e4-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="126e4-156">テーブルを作成する</span><span class="sxs-lookup"><span data-stu-id="126e4-156">Create a table</span></span>

<span data-ttu-id="126e4-157">この例は、テーブルが存在しない場合に作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="126e4-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="126e4-158">エンティティをテーブルに追加する</span><span class="sxs-lookup"><span data-stu-id="126e4-158">Add an entity to a table</span></span>

<span data-ttu-id="126e4-159">エンティティは、から継承される型を持つ必要があり `TableEntity` ます。</span><span class="sxs-lookup"><span data-stu-id="126e4-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="126e4-160">は任意の `TableEntity` 方法で拡張できますが、型にはパラメーターのないコンストラクターが *必要* です。</span><span class="sxs-lookup"><span data-stu-id="126e4-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="126e4-161">との両方を持つプロパティのみ `get` `set` が Azure テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="126e4-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="126e4-162">エンティティのパーティションキーと行キーは、テーブル内のエンティティを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="126e4-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="126e4-163">同じパーティション キーを持つエンティティは、異なるパーティション キーを持つエンティティよりも迅速に照会できます。一方、多様なパーティション キーを使用すると、並列操作の拡張性が向上します。</span><span class="sxs-lookup"><span data-stu-id="126e4-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="126e4-164">をパーティションキーとして使用し、を行キーとして使用するの例を次に示し `Customer` `lastName` `firstName` ます。</span><span class="sxs-lookup"><span data-stu-id="126e4-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="126e4-165">次 `Customer` に、テーブルにを追加します。</span><span class="sxs-lookup"><span data-stu-id="126e4-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="126e4-166">これを行うには、 `TableOperation` テーブルで実行するを作成します。</span><span class="sxs-lookup"><span data-stu-id="126e4-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="126e4-167">この場合は、操作を作成し `Insert` ます。</span><span class="sxs-lookup"><span data-stu-id="126e4-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="126e4-168">エンティティのバッチを挿入する</span><span class="sxs-lookup"><span data-stu-id="126e4-168">Insert a batch of entities</span></span>

<span data-ttu-id="126e4-169">1回の書き込み操作を使用して、エンティティのバッチをテーブルに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="126e4-170">バッチ操作を使用すると、複数の操作を1回の実行にまとめることができますが、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="126e4-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="126e4-171">同じバッチ操作で、更新、削除、および挿入を実行できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="126e4-172">バッチ操作には、最大100のエンティティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="126e4-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="126e4-173">バッチ操作内のすべてのエンティティは、同じパーティションキーを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="126e4-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="126e4-174">バッチ操作でクエリを実行することはできますが、バッチ内の唯一の操作である必要があります。</span><span class="sxs-lookup"><span data-stu-id="126e4-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="126e4-175">バッチ操作に2つの挿入を結合するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="126e4-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="126e4-176">パーティション内のすべてのエンティティを取得する</span><span class="sxs-lookup"><span data-stu-id="126e4-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="126e4-177">テーブルに対してパーティション内のすべてのエンティティを照会する場合は、`TableQuery` オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="126e4-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="126e4-178">ここでは、"Smith" がパーティションキーであるエンティティをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="126e4-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="126e4-179">結果は次のように印刷されます。</span><span class="sxs-lookup"><span data-stu-id="126e4-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="126e4-180">パーティション内の一定範囲のエンティティを取得する</span><span class="sxs-lookup"><span data-stu-id="126e4-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="126e4-181">パーティション内の一部のエンティティのみを照会する場合は、パーティション キー フィルターと行キー フィルターを組み合わせて範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="126e4-182">ここでは、2つのフィルターを使用して、行キー (名) がアルファベットの "M" よりも前の文字で始まる "Smith" パーティション内のすべてのエンティティを取得します。</span><span class="sxs-lookup"><span data-stu-id="126e4-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="126e4-183">結果は次のように印刷されます。</span><span class="sxs-lookup"><span data-stu-id="126e4-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="126e4-184">単一のエンティティを取得する</span><span class="sxs-lookup"><span data-stu-id="126e4-184">Retrieve a single entity</span></span>

<span data-ttu-id="126e4-185">単一の特定のエンティティを取得するクエリを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="126e4-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="126e4-186">ここでは、を使用し `TableOperation` て、"Ben Smith" という顧客を指定します。</span><span class="sxs-lookup"><span data-stu-id="126e4-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="126e4-187">コレクションではなく、が返さ `Customer` れます。</span><span class="sxs-lookup"><span data-stu-id="126e4-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="126e4-188">クエリでパーティションキーと行キーの両方を指定することは、Table service から単一のエンティティを取得する最速の方法です。</span><span class="sxs-lookup"><span data-stu-id="126e4-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="126e4-189">結果は次のように印刷されます。</span><span class="sxs-lookup"><span data-stu-id="126e4-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="126e4-190">エンティティを置換する</span><span class="sxs-lookup"><span data-stu-id="126e4-190">Replace an entity</span></span>

<span data-ttu-id="126e4-191">エンティティを更新するには、エンティティを Table service から取得し、エンティティオブジェクトを変更した後、操作を使用して Table service に変更を保存し `Replace` ます。</span><span class="sxs-lookup"><span data-stu-id="126e4-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="126e4-192">これにより、サーバー上でエンティティが完全に置換されます。ただし、取得後にサーバー上のエンティティが変更された場合、操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="126e4-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="126e4-193">このエラーは、他のソースからの変更がアプリケーションによって誤って上書きされないようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="126e4-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="126e4-194">エンティティを挿入または置換する</span><span class="sxs-lookup"><span data-stu-id="126e4-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="126e4-195">場合によっては、テーブルにエンティティが存在するかどうかがわかりません。</span><span class="sxs-lookup"><span data-stu-id="126e4-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="126e4-196">その場合、現在格納されている値は不要になります。</span><span class="sxs-lookup"><span data-stu-id="126e4-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="126e4-197">を使用してエンティティを作成することも、 `InsertOrReplace` 状態に関係なく、エンティティが存在する場合は置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="126e4-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="126e4-198">エンティティ プロパティのサブセットを照会する</span><span class="sxs-lookup"><span data-stu-id="126e4-198">Query a subset of entity properties</span></span>

<span data-ttu-id="126e4-199">テーブルクエリでは、エンティティのすべてではなく、いくつかのプロパティのみを取得できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="126e4-200">射影と呼ばれるこの手法は、特に大規模なエンティティの場合に、クエリのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="126e4-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="126e4-201">ここでは、とを使用して電子メールアドレスのみを返し `DynamicTableEntity` `EntityResolver` ます。</span><span class="sxs-lookup"><span data-stu-id="126e4-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="126e4-202">プロジェクションはローカルストレージエミュレーターではサポートされていないため、このコードは Table service でアカウントを使用している場合にのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="126e4-202">Projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="126e4-203">ページ内のエンティティを非同期的に取得する</span><span class="sxs-lookup"><span data-stu-id="126e4-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="126e4-204">多数のエンティティを読み取っているときに、すべてのエンティティが返されるのを待機するのではなく、取得時に処理する場合は、セグメント化されたクエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="126e4-205">ここでは、非同期ワークフローを使用してページ内の結果を返し、多数の結果が返されるのを待機している間に実行がブロックされないようにします。</span><span class="sxs-lookup"><span data-stu-id="126e4-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="126e4-206">ここで、この計算を同期的に実行します。</span><span class="sxs-lookup"><span data-stu-id="126e4-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="126e4-207">エンティティを削除する</span><span class="sxs-lookup"><span data-stu-id="126e4-207">Delete an entity</span></span>

<span data-ttu-id="126e4-208">エンティティは、取得後に削除できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="126e4-209">エンティティの更新と同様に、エンティティを取得した後にエンティティが変更された場合、これは失敗します。</span><span class="sxs-lookup"><span data-stu-id="126e4-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="126e4-210">テーブルを削除する</span><span class="sxs-lookup"><span data-stu-id="126e4-210">Delete a table</span></span>

<span data-ttu-id="126e4-211">ストレージアカウントからテーブルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="126e4-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="126e4-212">削除されたテーブルは、削除後の一定期間は再作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="126e4-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="126e4-213">次のステップ</span><span class="sxs-lookup"><span data-stu-id="126e4-213">Next steps</span></span>

<span data-ttu-id="126e4-214">これで、Table storage の基本を学習できました。さらに複雑なストレージタスクと Azure Cosmos DB Table API については、次のリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="126e4-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="126e4-215">Azure Cosmos DB Table API の概要</span><span class="sxs-lookup"><span data-stu-id="126e4-215">Introduction to Azure Cosmos DB Table API</span></span>](/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="126e4-216">.NET 用ストレージ クライアント ライブラリ リファレンス</span><span class="sxs-lookup"><span data-stu-id="126e4-216">Storage Client Library for .NET reference</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="126e4-217">Azure Storage 型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="126e4-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="126e4-218">Azure Storage Team Blog</span><span class="sxs-lookup"><span data-stu-id="126e4-218">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="126e4-219">接続文字列の構成</span><span class="sxs-lookup"><span data-stu-id="126e4-219">Configuring Connection Strings</span></span>](/azure/storage/common/storage-configure-connection-string)
