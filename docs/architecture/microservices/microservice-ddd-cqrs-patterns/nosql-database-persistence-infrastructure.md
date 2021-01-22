---
title: 永続インフラストラクチャとして NoSQL データベースを使用する
description: 永続性実装のオプションとしての NoSql データベースの一般的な使用と、特に Azure Cosmos DB の使用について理解します。
ms.date: 01/13/2021
ms.openlocfilehash: 32f32a3fd247f49ac54deaf33605bcc2ac7b55dc
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188830"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="7504b-103">永続インフラストラクチャとして NoSQL データベースを使用する</span><span class="sxs-lookup"><span data-stu-id="7504b-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="7504b-104">インフラストラクチャ データ層に NoSQL データベースを使用する場合、通常は Entity Framework Core のような ORM は使用しません。</span><span class="sxs-lookup"><span data-stu-id="7504b-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="7504b-105">代わりに、Azure Cosmos DB、MongoDB、Cassandra、RavenDB、CouchDB、または Azure Storage Table などの NoSQL エンジンによって提供される API を使用します。</span><span class="sxs-lookup"><span data-stu-id="7504b-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="7504b-106">ただし、NoSQL データベース、特にドキュメント指向データベース (Azure Cosmos DB、CouchDB、RavenDB など) を使用する場合、集約ルート、子エンティティ クラス、および値オブジェクト クラスに関しては、DDD 集約を使用してモデルを設計する方法は、EF Core での方法と部分的に似ています。</span><span class="sxs-lookup"><span data-stu-id="7504b-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="7504b-107">しかし、最終的には、データベースの選択が設計に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="7504b-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="7504b-108">ドキュメント指向データベースを使用する場合は、JSON または別の形式でシリアル化された 1 つのドキュメントとして集約を実装します。</span><span class="sxs-lookup"><span data-stu-id="7504b-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="7504b-109">ただし、データベースの使用は、ドメイン モデルのコードの観点からは透過的です。</span><span class="sxs-lookup"><span data-stu-id="7504b-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="7504b-110">NoSQL データベースを使用する場合も、エンティティ クラスと集約ルート クラスを引き続き使用しますが、永続化がリレーショナルではないため、EF Core を使用するときよりも高い柔軟性が得られます。</span><span class="sxs-lookup"><span data-stu-id="7504b-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="7504b-111">違いは、そのモデルを永続化する方法にあります。</span><span class="sxs-lookup"><span data-stu-id="7504b-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="7504b-112">インフラストラクチャの永続性に依存しない、POCO エンティティ クラスに基づいてドメイン モデルを実装した場合、リレーショナルから NoSQL に移行しても、別の永続化インフラストラクチャに移行したように見える場合があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="7504b-113">しかし、これを目標とはしないでください。</span><span class="sxs-lookup"><span data-stu-id="7504b-113">However, that should not be your goal.</span></span> <span data-ttu-id="7504b-114">各種のデータベース技術には常に制約や妥協があり、リレーショナルまたは NoSQL データベースに同じモデルを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="7504b-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="7504b-115">永続化モデルの変更は、トランザクションと永続化の操作がかなり異なるため、簡単な作業ではありません。</span><span class="sxs-lookup"><span data-stu-id="7504b-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="7504b-116">たとえば、ドキュメント指向のデータベースでは、複数の子コレクション プロパティを持つためにルートを集約することができます。</span><span class="sxs-lookup"><span data-stu-id="7504b-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="7504b-117">リレーショナル データベースでは、複数の子コレクション プロパティへのクエリ実行は簡単に最適化されません。UNION ALL SQL ステートメントが EF から返されるためです。</span><span class="sxs-lookup"><span data-stu-id="7504b-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="7504b-118">リレーショナル データベースと NoSQL データベースに対して同じドメイン モデルを持つのは単純なことではないので、行わないでください。</span><span class="sxs-lookup"><span data-stu-id="7504b-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="7504b-119">データがそれぞれ特定のデータベースでどのように使用されるかを理解したうえで、モデルを設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="7504b-120">NoSQL データベースを使用する場合の利点は、エンティティがより非正規化されるため、テーブル マッピングを設定しなくてもよい点です。</span><span class="sxs-lookup"><span data-stu-id="7504b-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="7504b-121">リレーショナル データベースを使用するときよりも、ドメイン モデルに柔軟性を持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="7504b-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="7504b-122">集約に基づいてドメイン モデルを設計すると、NoSQL とドキュメント指向データベースへの移行が、リレーショナル データベースを使用するよりもさらに簡単になる場合があります。これは、設計する集約が、ドキュメント指向データベース内のシリアル化されたドキュメントと似ているからです。</span><span class="sxs-lookup"><span data-stu-id="7504b-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="7504b-123">その後、これらの "バッグ" にその集約に必要なすべての情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7504b-123">Then you can include in those "bags" all the information you might need for that aggregate.</span></span>

<span data-ttu-id="7504b-124">たとえば、次の JSON コードは、ドキュメント指向データベースを使用するときの、注文集約のサンプル実装です。</span><span class="sxs-lookup"><span data-stu-id="7504b-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="7504b-125">これは、eShopOnContainers サンプルで実装した注文集約と似ていますが、下に EF Core を使用していません。</span><span class="sxs-lookup"><span data-stu-id="7504b-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="7504b-126">Azure Cosmos DB とネイティブ Cosmos DB API の概要</span><span class="sxs-lookup"><span data-stu-id="7504b-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="7504b-127">[Azure Cosmos DB](/azure/cosmos-db/introduction) は、ミッション クリティカルなアプリケーションのために、世界各地に分散された Microsoft のデータベース サービスです。</span><span class="sxs-lookup"><span data-stu-id="7504b-127">[Azure Cosmos DB](/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="7504b-128">Azure Cosmos DB では、[ターン キー グローバル配布](/azure/cosmos-db/distribute-data-globally)、世界規模での[スループットとストレージのエラスティック スケーリング](/azure/cosmos-db/partition-data)、99 パーセンタイルで 10 ミリ秒未満の待機時間、[5 つの明確に定義された整合性レベル](/azure/cosmos-db/consistency-levels)、および保証された高可用性を提供しており、これらすべてが[業界トップの SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/) でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7504b-128">Azure Cosmos DB provides [turn-key global distribution](/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="7504b-129">Azure Cosmos DB により、[データが自動的にインデックス付けされる](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf)ため、スキーマとインデックスの管理に対処する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="7504b-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="7504b-130">これはマルチモデルで、ドキュメント、キー値、グラフ、および列指向データ モデルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="7504b-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![Azure Cosmos DB のグローバル配布を示す図。](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

<span data-ttu-id="7504b-132">**図 7-19**</span><span class="sxs-lookup"><span data-stu-id="7504b-132">**Figure 7-19**.</span></span> <span data-ttu-id="7504b-133">Azure Cosmos DB のグローバル配布</span><span class="sxs-lookup"><span data-stu-id="7504b-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="7504b-134">C\# モデルを使用して Azure Cosmos DB API で使用される集約を実装すると、集約が EF Core で使用される C\# POCO クラスと同じようになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="7504b-135">違いは、次のコードのように、それらをアプリケーション層とインフラストラクチャ層から使用する方法にあります。</span><span class="sxs-lookup"><span data-stu-id="7504b-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// **_ Domain Model Code _*_
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot's methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
// _*_ End of Domain Model Code _*_

// _*_ Infrastructure Code using Cosmos DB Client API _*_
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="7504b-136">ドメイン モデルを操作する方法が、インフラストラクチャが EF のときにドメイン モデル レイヤーで使用するのと同様の方法になる可能性があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="7504b-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="7504b-137">集約内の整合性、インバリアント、および検証を確認するため、同じ集約ルート メソッドを引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="7504b-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="7504b-138">ただし、モデルを NoSQL データベースに永続化する場合は、EF Core コードやリレーショナル データベースに関連するその他のコードと比べて、コードと API は劇的に変わります。</span><span class="sxs-lookup"><span data-stu-id="7504b-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="7504b-139">MongoDB と Azure Cosmos DB をターゲットとする .NET コードを実装する</span><span class="sxs-lookup"><span data-stu-id="7504b-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="7504b-140">.NET コンテナーから Azure Cosmos DB を使用する</span><span class="sxs-lookup"><span data-stu-id="7504b-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="7504b-141">他の .NET アプリケーションからアクセスする場合と同じように、コンテナーで実行されている .NET コードから Azure Cosmos DB データベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7504b-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="7504b-142">たとえば、eShopOnContainers の Locations.API と Marketing.API のマイクロサービスは、Azure Cosmos DB データベースを使用できるように実装されています。</span><span class="sxs-lookup"><span data-stu-id="7504b-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="7504b-143">ただし、Docker 開発環境の観点から、Azure Cosmos DB には制限があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="7504b-144">ローカルの開発用コンピューターで実行できるオンプレミスの [Azure Cosmos DB エミュレーター](/azure/cosmos-db/local-emulator)がある場合でも、Windows のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7504b-144">Even though there’s an on-premises [Azure Cosmos DB Emulator](/azure/cosmos-db/local-emulator) that can run in a local development machine, it only supports Windows.</span></span> <span data-ttu-id="7504b-145">Linux と macOS はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7504b-145">Linux and macOS aren't supported.</span></span>

<span data-ttu-id="7504b-146">このエミュレーターを Docker で実行する可能性もありますが、可能性があるのは Windows コンテナーのみであり、Linux コンテナーではありません。</span><span class="sxs-lookup"><span data-stu-id="7504b-146">There's also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="7504b-147">現在、Docker for Windows に Linux コンテナーと Windows コンテナーを同時に展開することはできないため、アプリケーションを Linux コンテナーとして展開する場合、これが開発環境にとって最初のハンディキャップとなります。</span><span class="sxs-lookup"><span data-stu-id="7504b-147">That's an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you can't deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="7504b-148">展開されるすべてのコンテナーは、Linux または Windows 用のどちらかにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-148">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="7504b-149">開発およびテスト ソリューションにとって理想的でより簡単な展開は、開発およびテスト環境に常に整合性を持たせるために、データベース システムをカスタム コンテナーと共にコンテナーとして展開できることです。</span><span class="sxs-lookup"><span data-stu-id="7504b-149">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="7504b-150">Linux/Windows コンテナーと Azure Cosmos DB のローカル開発/テストに MongoDB API を使用する</span><span class="sxs-lookup"><span data-stu-id="7504b-150">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="7504b-151">Cosmos DB データベースでは、.NET とネイティブ MongoDB ワイヤ プロトコルのために MongoDB API をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7504b-151">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="7504b-152">つまり、既存のドライバーを使用することで、図 7-20 に示すように、MongoDB 用に記述されたアプリケーションで Cosmos DB と通信し、MongoDB データベースの代わりに Cosmos DB データベースを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7504b-152">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Cosmos DB で .NET と MongoDB のワイヤ プロトコルをサポートしていることを示す図。](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

<span data-ttu-id="7504b-154">図 7-20。</span><span class="sxs-lookup"><span data-stu-id="7504b-154">_\*Figure 7-20\*\*.</span></span> <span data-ttu-id="7504b-155">MongoDB API とプロトコルを使用して Azure Cosmos DB にアクセスする</span><span class="sxs-lookup"><span data-stu-id="7504b-155">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="7504b-156">[MongoDB Docker イメージ](https://hub.docker.com/r/_/mongo/)は、Docker Linux コンテナーと Docker Windows コンテナーをサポートするマルチアーキテクチャ イメージなので、これは Linux コンテナーを使用する Docker 環境での概念実証にとって非常に便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="7504b-156">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="7504b-157">次の画像に示すように、MongoDB API を使用することで、eShopOnContainers でローカル開発環境に対して MongoDB Linux コンテナーと Windows コンテナーの両方がサポートされますが、その後、[MongoDB の接続文字列を Azure Cosmos DB をポイントするように変更](/azure/cosmos-db/connect-mongodb-account)するだけで、Azure Cosmos DB と同じようなスケーラブルな PaaS クラウド ソリューションに移行できます。</span><span class="sxs-lookup"><span data-stu-id="7504b-157">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](/azure/cosmos-db/connect-mongodb-account).</span></span>

![eShopOnContainers の Location マイクロサービスで Cosmos DB または Mongo DB を使用できることを示す図。](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

<span data-ttu-id="7504b-159">**図 7-21**</span><span class="sxs-lookup"><span data-stu-id="7504b-159">**Figure 7-21**.</span></span> <span data-ttu-id="7504b-160">開発環境に MongoDB コンテナーまたは運用に Azure Cosmos DB を使用する eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="7504b-160">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="7504b-161">運用環境の Azure Cosmos DB は、PaaS およびスケーラブルなサービスとして Azure のクラウドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="7504b-161">The production Azure Cosmos DB would be running in Azure's cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="7504b-162">.NET のカスタム コンテナーは、(Windows 10 コンピューターで Docker for Windows を使用して) ローカルの Docker の開発用ホストで実行することも、Azure AKS または Azure Service Fabric での Kubernetes のように、運用環境に展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="7504b-162">Your custom .NET containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="7504b-163">この 2 つ目の環境では、運用中のデータの処理にクラウド内の Azure Cosmos DB を使用しているため、.NET のカスタム コンテナーのみが展開され、MongoDB コンテナーは展開されません。</span><span class="sxs-lookup"><span data-stu-id="7504b-163">In this second environment, you would deploy only the .NET custom containers but not the MongoDB container since you'd be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="7504b-164">MongoDB API を使用することの明らかな利点は、MongoDB と Azure Cosmos DB の両方のデータベース エンジンでソリューションを実行できるため、異なる環境への移行が容易になることです。</span><span class="sxs-lookup"><span data-stu-id="7504b-164">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="7504b-165">ただし、特定のデータベース エンジンの機能をフル活用するために、ネイティブ API (ネイティブ Cosmos DB API) を使用することには意義がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-165">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="7504b-166">単純に MongoDB を使用することとクラウドでの Cosmos DB との詳しい比較については、[Azure Cosmos DB を使用する利点に関するページ](/azure/cosmos-db/mongodb-introduction)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7504b-166">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="7504b-167">実稼働アプリケーションのアプローチを分析する:MongoDB API とCosmos DB API</span><span class="sxs-lookup"><span data-stu-id="7504b-167">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="7504b-168">Microsoft では、根本的に、Azure Cosmos DB でも動作する NoSQL データベースを使用して一貫性のある開発/テスト環境を持つことを優先したため、eShopOnContainers では MongoDB API を使用しています。</span><span class="sxs-lookup"><span data-stu-id="7504b-168">In eShopOnContainers, we're using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="7504b-169">ただし、MongoDB API を使用して実稼働アプリケーションの Azure で Azure Cosmos DB にアクセスすることを計画している場合は、Azure Cosmos DB データベースにアクセスするために MongoDB API を使用した場合とネイティブ Azure Cosmos DB API を使用した場合とを比較して、機能とパフォーマンスの違いを分析する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-169">However, if you are planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="7504b-170">同様の場合は、MongoDB API を使用でき、同時に 2 つの NoSQL データベース エンジンをサポートするという利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="7504b-170">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="7504b-171">また、[MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service) を使用して、MongoDB クラスターを Azure のクラウドで運用データベースとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="7504b-171">You could also use MongoDB clusters as the production database in Azure's cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="7504b-172">ただしこれは、Microsoft が提供している PaaS サービスではありません。</span><span class="sxs-lookup"><span data-stu-id="7504b-172">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="7504b-173">このケースでは、Azure は MongoDB からのそのソリューションをホスティングしているだけです。</span><span class="sxs-lookup"><span data-stu-id="7504b-173">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="7504b-174">基本的に、これは、Linux コンテナーには便利な選択だったため、eShopOnContainers では MongoDB API を使用しましたが、Azure Cosmos DB に対して MongoDB API を常に使用すべきではないことを言明する免責事項にすぎません。</span><span class="sxs-lookup"><span data-stu-id="7504b-174">Basically, this is just a disclaimer stating that you shouldn't always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="7504b-175">決定は、特定のニーズと、実稼働アプリケーションに対して行う必要があるテストに基づいて行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-175">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-applications"></a><span data-ttu-id="7504b-176">コード:.NET アプリケーションで MongoDB API を使用する</span><span class="sxs-lookup"><span data-stu-id="7504b-176">The code: Use MongoDB API in .NET applications</span></span>

<span data-ttu-id="7504b-177">.NET 用の MongoDB API は、次の図に示されている Locations.API プロジェクトのような、プロジェクトに追加する必要のある NuGet パッケージに基づいています。</span><span class="sxs-lookup"><span data-stu-id="7504b-177">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![MongoDB NuGet パッケージの依存関係のスクリーンショット。](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

<span data-ttu-id="7504b-179">**図 7-22**。</span><span class="sxs-lookup"><span data-stu-id="7504b-179">**Figure 7-22**.</span></span> <span data-ttu-id="7504b-180">.NET プロジェクト内の MongoDB API NuGet パッケージの参照</span><span class="sxs-lookup"><span data-stu-id="7504b-180">MongoDB API NuGet packages references in a .NET project</span></span>

<span data-ttu-id="7504b-181">次のセクションでは、コードを調査しましょう。</span><span class="sxs-lookup"><span data-stu-id="7504b-181">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="7504b-182">MongoDB API によって使用されるモデル</span><span class="sxs-lookup"><span data-stu-id="7504b-182">A Model used by MongoDB API</span></span>

<span data-ttu-id="7504b-183">最初に、データベースから取得したデータをアプリケーションのメモリ領域で保持するモデルを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-183">First, you need to define a model that will hold the data coming from the database in your application's memory space.</span></span> <span data-ttu-id="7504b-184">eShopOnContainers で Locations に使用するモデルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7504b-184">Here's an example of the model used for Locations at eShopOnContainers.</span></span>

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList)
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

<span data-ttu-id="7504b-185">MongoDB NuGet パッケージから取得されるいくつかの属性と型があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="7504b-185">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="7504b-186">NoSQL データベースは、通常、非リレーショナルの階層データを操作するのに非常に適しています。</span><span class="sxs-lookup"><span data-stu-id="7504b-186">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="7504b-187">この例では、`GeoJson2DGeographicCoordinates` のように、特に地理上の位置のために作成された MongoDB 型を使用しています。</span><span class="sxs-lookup"><span data-stu-id="7504b-187">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="7504b-188">データベースとコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="7504b-188">Retrieve the database and the collection</span></span>

<span data-ttu-id="7504b-189">eShopOnContainers では、次のコードのように、コードを実装してデータベースと MongoCollections を取得する、カスタムのデータベース コンテキストを作成しました。</span><span class="sxs-lookup"><span data-stu-id="7504b-189">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }
}
```

#### <a name="retrieve-the-data"></a><span data-ttu-id="7504b-190">データを取得する</span><span class="sxs-lookup"><span data-stu-id="7504b-190">Retrieve the data</span></span>

<span data-ttu-id="7504b-191">C# コードでは、Web API コントローラーやカスタム リポジトリの実装のように、MongoDB API からクエリを実行するときに、次のようなコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="7504b-191">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="7504b-192">`_context` オブジェクトは以前の `LocationsContext` クラスのインスタンスであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7504b-192">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="7504b-193">MongoDB の接続文字列に対して docker-compose.override.yml ファイル内の環境変数を使用する</span><span class="sxs-lookup"><span data-stu-id="7504b-193">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="7504b-194">MongoClient オブジェクトを作成するときには、正確に適切なデータベースをポイントしている `ConnectionString` パラメーターと同じ、基本的なパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="7504b-194">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="7504b-195">eShopOnContainers の場合、接続文字列はローカル MongoDB Docker コンテナーまたは "運用中の" Azure Cosmos DB データベースをポイントすることができます。</span><span class="sxs-lookup"><span data-stu-id="7504b-195">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a "production" Azure Cosmos DB database.</span></span>  <span data-ttu-id="7504b-196">次の yml コードにあるように、その接続文字列は、docker-compose または Visual Studio を使用して展開するときに使用される、`docker-compose.override.yml` ファイルで定義されている環境変数から取得されます。</span><span class="sxs-lookup"><span data-stu-id="7504b-196">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations-api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}

```

<span data-ttu-id="7504b-197">`ConnectionString` 環境変数はこの方法で解決されます:`ESHOP_AZURE_COSMOSDB` グローバル変数が Azure Cosmos DB 接続文字列を使用して `.env` ファイルで定義されている場合、そのグローバル変数を使用してクラウド内の Azure Cosmos DB データベースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7504b-197">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="7504b-198">定義されていない場合は `mongodb://nosqldata` 値が取得され、開発 MongoDB コンテナーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7504b-198">If it’s not defined, it will take the `mongodb://nosqldata` value and use the development MongoDB container.</span></span>

<span data-ttu-id="7504b-199">次のコードは、eShopOnContainers に実装されているように、Azure Cosmos DB グローバル環境変数を持つ `.env` ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="7504b-199">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

<span data-ttu-id="7504b-200">「[Azure Cosmos DB への MongoDB アプリケーションの接続](/azure/cosmos-db/connect-mongodb-account)」で説明したように、ESHOP_AZURE_COSMOSDB 行をコメント解除し、Azure portal から取得した Azure Cosmos DB 接続文字列を使用してそれを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7504b-200">Uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="7504b-201">`ESHOP_AZURE_COSMOSDB` グローバル変数が空の場合 (つまり、`.env` ファイルでコメントアウトされている場合)、コンテナーでは既定の MongoDB 接続文字列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7504b-201">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning it's commented out in the `.env` file, then the container uses a default MongoDB connection string.</span></span> <span data-ttu-id="7504b-202">この接続文字列は、次の .yml コードに示すように、`nosqldata` という名前の eShopOnContainers に配置されたローカル MongoDB コンテナーをポイントし、docker-compose ファイルに定義されていました。</span><span class="sxs-lookup"><span data-stu-id="7504b-202">This connection string points to the local MongoDB container deployed in eShopOnContainers that is named `nosqldata` and was defined at the docker-compose file, as shown in the following .yml code:</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="7504b-203">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="7504b-203">Additional resources</span></span>

- <span data-ttu-id="7504b-204">**NoSQL データベースのドキュメント データのモデリング** </span><span class="sxs-lookup"><span data-stu-id="7504b-204">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="7504b-205">**Vaughn Vernon。理想的なドメイン駆動設計集約ストアとは?**</span><span class="sxs-lookup"><span data-stu-id="7504b-205">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="7504b-206">**Azure Cosmos DB の概要:MongoDB の API**  </span><span class="sxs-lookup"><span data-stu-id="7504b-206">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="7504b-207">**Azure Cosmos DB:.NET および Azure portal を使用して MongoDB API の Web アプリを構築する**  </span><span class="sxs-lookup"><span data-stu-id="7504b-207">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="7504b-208">**ローカルの開発とテストでの Azure Cosmos DB Emulator の使用**  </span><span class="sxs-lookup"><span data-stu-id="7504b-208">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="7504b-209">**Azure Cosmos DB への MongoDB アプリケーションの接続**  </span><span class="sxs-lookup"><span data-stu-id="7504b-209">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="7504b-210">**Cosmos DB エミュレーターの Docker イメージ (Windows コンテナー)**   </span><span class="sxs-lookup"><span data-stu-id="7504b-210">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="7504b-211">**MongoDB Docker イメージ (Linux と Windows コンテナー)**   </span><span class="sxs-lookup"><span data-stu-id="7504b-211">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="7504b-212">**Azure Cosmos DB:MongoDB API アカウントでの Studio 3T の使用**  </span><span class="sxs-lookup"><span data-stu-id="7504b-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="7504b-213">[前へ](infrastructure-persistence-layer-implementation-entity-framework-core.md)
>[次へ](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="7504b-213">[Previous](infrastructure-persistence-layer-implementation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
