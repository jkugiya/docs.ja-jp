---
title: docker-compose.yml で複数のコンテナー アプリケーションを定義する
description: docker-compose.yml を使用して複数コンテナーのアプリケーション用にマイクロサービスの構成を指定する方法。
ms.date: 01/13/2021
ms.openlocfilehash: fa8a5736905f6bae7fec8da35638048707bb6fa1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430561"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="6ddc4-103">docker-compose.yml で複数のコンテナー アプリケーションを定義する</span><span class="sxs-lookup"><span data-stu-id="6ddc4-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="6ddc4-104">このガイドでは、[docker-compose.yml](https://docs.docker.com/compose/compose-file/) ファイルは、「[手順 4 複数のコンテナー Docker アプリケーションを構築するときに docker compose.yml で、サービスを定義します](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application)」セクションで導入されました。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="6ddc4-105">しかし、docker-compose ファイルには他の使い方もあり、さらに詳しく検討する価値があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="6ddc4-106">たとえば、マルチコンテナー アプリケーションの展開方法を、docker-compose.yml ファイルで明示的に記述することができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="6ddc4-107">必要に応じて、カスタム Docker イメージのビルド方法も記述できます</span><span class="sxs-lookup"><span data-stu-id="6ddc4-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="6ddc4-108">(カスタム Docker イメージは、Docker CLI を使用してビルドすることもできます)。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="6ddc4-109">基本的には、展開する各コンテナーを定義することに加え、各コンテナー展開に対して特定の特性も定義します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="6ddc4-110">マルチコンテナー展開の記述ファイルを作成したら、全体のソリューションを、[docker-compose up](https://docs.docker.com/compose/overview/) CLI コマンドで調整された 1 つのアクションで展開することができます。または、Visual Studio から透過的に展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="6ddc4-111">それ以外の場合は、Docker CLI を使用して、コマンドラインから `docker run` コマンドを使用して、複数の手順でコンテナーごとに展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="6ddc4-112">そのため、docker-compose.yml で定義された各サービスは、イメージまたはビルドを 1 つだけ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="6ddc4-113">その他のキーは省略可能で、その対応する `docker run` コマンド ラインと似ています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="6ddc4-114">次の YAML コードは、グローバルに使用できる定義ですが、eShopOnContainers サンプル用の 1 つの docker-compose.yml ファイルです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="6ddc4-115">このコードは eShopOnContainers からの実際の docker-compose ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-115">This code is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="6ddc4-116">むしろ、簡素化され、1 つのファイルに統合されたバージョンです。後述しますが、これは docker-compose ファイルで使用するには最善の方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
      - BasketUrl=http://basket-api
    ports:
      - "5100:80"
    depends_on:
      - catalog-api
      - ordering-api
      - basket-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=[PLACEHOLDER]
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=Services.OrderingDb;User Id=sa;Password=[PLACEHOLDER]
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  basket-api:
    image: eshop/basket-api
    environment:
      - ConnectionString=sqldata
    ports:
      - "5103:80"
    depends_on:
      - sqldata

  sqldata:
    environment:
      - SA_PASSWORD=[PLACEHOLDER]
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basketdata:
    image: redis
```

<span data-ttu-id="6ddc4-117">このファイルのルート キーはサービスです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-117">The root key in this file is services.</span></span> <span data-ttu-id="6ddc4-118">そのキーの下で、`docker-compose up` コマンドを実行するとき、またはこの docker-compose.yml ファイルを使用して Visual Studio から展開するときに、展開および実行するサービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-118">Under that key, you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="6ddc4-119">この例では、次の表に示すように、docker-compose.yml ファイルでは複数のサービスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="6ddc4-120">サービス名</span><span class="sxs-lookup"><span data-stu-id="6ddc4-120">Service name</span></span> | <span data-ttu-id="6ddc4-121">説明</span><span class="sxs-lookup"><span data-stu-id="6ddc4-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="6ddc4-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="6ddc4-122">webmvc</span></span>       | <span data-ttu-id="6ddc4-123">サーバー側 C\# からマイクロサービスを消費する ASP.NET Core MVC アプリケーションを含むコンテナー</span><span class="sxs-lookup"><span data-stu-id="6ddc4-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="6ddc4-124">catalog-api</span><span class="sxs-lookup"><span data-stu-id="6ddc4-124">catalog-api</span></span>  | <span data-ttu-id="6ddc4-125">Catalog ASP.NET Core Web API マイクロサービスを含むコンテナー</span><span class="sxs-lookup"><span data-stu-id="6ddc4-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="6ddc4-126">ordering-api</span><span class="sxs-lookup"><span data-stu-id="6ddc4-126">ordering-api</span></span> | <span data-ttu-id="6ddc4-127">Ordering ASP.NET Core Web API マイクロサービスを含むコンテナー</span><span class="sxs-lookup"><span data-stu-id="6ddc4-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="6ddc4-128">sqldata</span><span class="sxs-lookup"><span data-stu-id="6ddc4-128">sqldata</span></span>     | <span data-ttu-id="6ddc4-129">マイクロサービス データベースを保持し、SQL Server for Linux が稼働するコンテナー</span><span class="sxs-lookup"><span data-stu-id="6ddc4-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="6ddc4-130">basket-api</span><span class="sxs-lookup"><span data-stu-id="6ddc4-130">basket-api</span></span>   | <span data-ttu-id="6ddc4-131">Basket ASP.NET Core Web API マイクロサービスを使用するコンテナー</span><span class="sxs-lookup"><span data-stu-id="6ddc4-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="6ddc4-132">basketdata</span><span class="sxs-lookup"><span data-stu-id="6ddc4-132">basketdata</span></span>  | <span data-ttu-id="6ddc4-133">REDIS キャッシュ サービスが稼働し、REDIS キャッシュとしてバスケット データベースを持つコンテナー</span><span class="sxs-lookup"><span data-stu-id="6ddc4-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="6ddc4-134">単純な Web サービス API コンテナー</span><span class="sxs-lookup"><span data-stu-id="6ddc4-134">A simple Web Service API container</span></span>

<span data-ttu-id="6ddc4-135">1 つのコンテナーに集中することで、catalog.api container-microservice の定義が単純になります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-135">Focusing on a single container, the catalog-api container-microservice has a straightforward definition:</span></span>

```yml
  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=[PLACEHOLDER]
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata
```

<span data-ttu-id="6ddc4-136">このコンテナー化されたサービスには、次の基本的な構成があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="6ddc4-137">それは、カスタムの **eshop/catalog.api** イメージに基づいています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-137">It is based on the custom **eshop/catalog-api** image.</span></span> <span data-ttu-id="6ddc4-138">わかりやすくするために、ファイル内にビルドやキーの設定はありません。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-138">For simplicity's sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="6ddc4-139">つまりイメージが、(docker build を使用して) 既にビルドされているか、(docker pull コマンドを使用して) 任意の Docker レジストリからダウンロードされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="6ddc4-140">接続文字列を使用して ConnectionString という名前の環境変数を定義します。この変数は、カタログ データ モデルを含む SQL Server インスタンスにアクセスするために Entity Framework によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="6ddc4-141">この例では、同じ SQL Server コンテナーに複数のデータベースが保持されています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="6ddc4-142">そのため、Docker 用に開発用コンピューターで必要なメモリ量が減ります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="6ddc4-143">ただし、マイクロサービス データベースごとに 1 つの SQL Server のコンテナーを展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="6ddc4-144">SQL Server 名は **sqldata** で、Linux 用の SQL Server インスタンスが実行されているコンテナーで使用されているのと同じ名前です。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-144">The SQL Server name is **sqldata**, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="6ddc4-145">これは便利な方法です。この名前解決 (内部から Docker ホストへ) を使用できることで、ネットワーク アドレスが解決されるため、他のコンテナーからアクセスするコンテナーの内部 IP アドレスを知る必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don't need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="6ddc4-146">接続文字列は環境変数によって定義されるため、異なる時点で別のメカニズムを使用して、その変数を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="6ddc4-147">たとえば、最後のホストで運用に展開するときに、または Azure DevOps Services の CI/CD パイプラインから、または優先する DevOps システムから、別の接続文字列を設定できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="6ddc4-148">Docker ホスト内で **catalog-api** サービスへの内部アクセス用に、ポート 80 が公開されます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-148">It exposes port 80 for internal access to the **catalog-api** service within the Docker host.</span></span> <span data-ttu-id="6ddc4-149">ホストは、Linux の Docker イメージに基づいているため、現在は Linux VM ですが、代わりに Windows イメージ上で実行するようにコンテナーを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="6ddc4-150">コンテナー上で公開されているポート 80 を、Docker ホスト コンピューター (Linux VM) 上のポート 5101 に転送します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="6ddc4-151">Web サービスを **sqldata** サービス (コンテナーで実行されている Linux データベースの SQL Server インスタンス) にリンクします。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-151">It links the web service to the **sqldata** service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="6ddc4-152">この依存関係を指定すると、catalog-api コンテナーは、sqldata コンテナーが起動するまで起動しなくなります。この点が重要なのは、catalog-api では、SQL Server データベースが先に起動して実行されている必要があるからです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-152">When you specify this dependency, the catalog-api container will not start until the sqldata container has already started; this aspect is important because catalog-api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="6ddc4-153">ただし、このようなコンテナーの依存関係は、Docker がコンテナー レベルでしかチェックしないため、多くの場合、不十分です。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="6ddc4-154">サービス (この場合は SQL Server) がまだ準備できていない場合もあるため、クライアント マイクロサービスで指数バックオフによる再試行ロジックを実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="6ddc4-155">そうすることで、依存関係のコンテナーが少しの間、準備できない場合でも、アプリケーションが回復力を保つことができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="6ddc4-156">これは外部サーバーへのアクセスを許可するように構成されます: extra\_hosts 設定により、開発用 PC 上のローカル SQL Server インスタンスなど、Docker ホストの外 (つまり、開発用 Docker ホストである既定の Linux VM の外) にある外部のサーバーやマシンにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM, which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="6ddc4-157">より高度な他の `docker-compose.yml` 設定もあります。これについては以降のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-157">There are also other, more advanced `docker-compose.yml` settings that we'll discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="6ddc4-158">docker-compose ファイルを使用して複数の環境をターゲットにする</span><span class="sxs-lookup"><span data-stu-id="6ddc4-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="6ddc4-159">`docker-compose.*.yml` ファイルは定義ファイルで、その形式を理解する複数のインフラストラクチャで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-159">The `docker-compose.*.yml` files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="6ddc4-160">最も簡単なツールは、docker-compose コマンドです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="6ddc4-161">そのため、docker-compose コマンドを使用することで、次の主なシナリオをターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="6ddc4-162">開発環境</span><span class="sxs-lookup"><span data-stu-id="6ddc4-162">Development environments</span></span>

<span data-ttu-id="6ddc4-163">アプリケーションを開発するときには、アプリケーションを分離開発環境で実行できることが重要です。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="6ddc4-164">docker-compose CLI コマンドを使用してその環境を作成するか、Visual Studio を使用することができます。そこでは内部的に docker-compose が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-164">You can use the docker-compose CLI command to create that environment or Visual Studio, which uses docker-compose under the covers.</span></span>

<span data-ttu-id="6ddc4-165">docker-compose.yml ファイルを使用すると、アプリケーションのすべてのサービスの依存関係 (その他のサービス、キャッシュ、データベース、キューなど) を構成および文書化できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-165">The docker-compose.yml file allows you to configure and document all your application's service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="6ddc4-166">docker-compose CLI コマンドを使用すると、1 つのコマンド (docker-compose up) を使用して、依存関係ごとに 1 つ以上のコンテナーを作成して起動することができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="6ddc4-167">docker-compose.yml ファイルは、Docker エンジンによって解釈される構成ファイルですが、マルチコンテナー アプリケーションの構成に関する便利なドキュメント ファイルとしても機能します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="6ddc4-168">テスト環境</span><span class="sxs-lookup"><span data-stu-id="6ddc4-168">Testing environments</span></span>

<span data-ttu-id="6ddc4-169">継続的配置 (CD) または継続的インテグレーション (CI) プロセスの重要な部分は、単体テストと統合テストです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="6ddc4-170">これらの自動テストでは、ユーザーまたはアプリケーションのデータ内の他の変更による影響を受けないように、分離環境が必要です。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application's data.</span></span>

<span data-ttu-id="6ddc4-171">Docker Compose を使用すると、コマンド プロンプトまたはスクリプトから、次のコマンドのように、いくつかのコマンドで簡単にその分離環境を作成および破棄することができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-171">With Docker Compose, you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="6ddc4-172">運用展開</span><span class="sxs-lookup"><span data-stu-id="6ddc4-172">Production deployments</span></span>

<span data-ttu-id="6ddc4-173">Compose を使用してリモート Docker エンジンに展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="6ddc4-174">一般的なケースは、(運用 VM または [Docker マシン](https://docs.docker.com/machine/overview/)でプロビジョニングされたサーバーのように) 1 つの Docker ホスト インスタンスに展開することです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="6ddc4-175">他の任意のオーケストレーター (Azure Service Fabric、Kubernetes など) を使用している場合は、docker-compose.yml にあるようなセットアップとメタデータの構成設定を、他のオーケストレーターで必要な形式で追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="6ddc4-176">いずれの場合も、docker-compose は、開発、テスト、運用ワークフローにとって便利なツールとメタデータ形式ですが、運用ワークフローはお使いのオーケストレーターによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="6ddc4-177">複数の docker-compose ファイルを使用して複数の環境を処理する</span><span class="sxs-lookup"><span data-stu-id="6ddc4-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="6ddc4-178">さまざまな環境をターゲットとする場合は、複数の compose ファイルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="6ddc4-179">このアプローチにより、環境に応じて複数の構成バリアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-179">This approach lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="6ddc4-180">基本の docker-compose ファイルをオーバーライドする</span><span class="sxs-lookup"><span data-stu-id="6ddc4-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="6ddc4-181">前のセクションで示した簡略化された例のように、1 つの docker-compose.yml ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="6ddc4-182">ただし、これはほとんどのアプリケーションにはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="6ddc4-183">既定では、Compose は docker-compose.yml と省略可能な docker-compose.override.yml の 2 つのファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="6ddc4-184">図 6-11 に示すように、Visual Studio を使用している場合に Docker サポートを有効にすると、アプリケーションをデバッグするための docker compose.vs.debug.g.yml ファイルも Visual Studio によって追加で作成されます。このファイルは、メイン ソリューション フォルダー内の obj\\Docker\\ フォルダーで確認できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![docker compose プロジェクト内のファイル。](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

<span data-ttu-id="6ddc4-186">**図 6-11**。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-186">**Figure 6-11**.</span></span> <span data-ttu-id="6ddc4-187">Visual Studio 2019 の docker-compose ファイル</span><span class="sxs-lookup"><span data-stu-id="6ddc4-187">docker-compose files in Visual Studio 2019</span></span>

<span data-ttu-id="6ddc4-188">**docker-compose** プロジェクトのファイル構造:</span><span class="sxs-lookup"><span data-stu-id="6ddc4-188">**docker-compose** project file structure:</span></span>

- <span data-ttu-id="6ddc4-189">*.dockerignore* - ファイルを無視するために使用</span><span class="sxs-lookup"><span data-stu-id="6ddc4-189">*.dockerignore* - used to ignore files</span></span>
- <span data-ttu-id="6ddc4-190">*docker-compose.yml* - マイクロサービスを作成するために使用</span><span class="sxs-lookup"><span data-stu-id="6ddc4-190">*docker-compose.yml* - used to compose microservices</span></span>
- <span data-ttu-id="6ddc4-191">*docker-compose.override.yml* - マイクロサービス環境を構成するために使用</span><span class="sxs-lookup"><span data-stu-id="6ddc4-191">*docker-compose.override.yml* - used to configure microservices environment</span></span>

<span data-ttu-id="6ddc4-192">Visual Studio Code や Sublime などの任意のエディターを使用して docker-compose ファイルを編集し、docker-compose up コマンドを使用してアプリケーションを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-192">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="6ddc4-193">慣例により、docker-compose.yml ファイルには、基本構成とその他の静的な設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-193">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="6ddc4-194">つまり、ターゲットとしている展開環境に合わせてサービス構成を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-194">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="6ddc4-195">docker-compose.override.yml ファイルには、その名前が示すように、基本構成 (展開環境に依存する構成など) をオーバーライドする構成設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-195">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="6ddc4-196">また、複数の override ファイルを異なる名前で持つことができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-196">You can have multiple override files with different names also.</span></span> <span data-ttu-id="6ddc4-197">override ファイルには通常、アプリケーションで必要な、環境または展開に固有の追加情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-197">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="6ddc4-198">複数の環境をターゲットにする</span><span class="sxs-lookup"><span data-stu-id="6ddc4-198">Targeting multiple environments</span></span>

<span data-ttu-id="6ddc4-199">一般的なユース ケースは、運用、ステージング、CI、開発などの複数の環境をターゲットにできるように、複数の compose ファイルを定義する場合です。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-199">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="6ddc4-200">これらの相違点をサポートするため、図 6-12 に示すように、ご利用の Compose 構成を複数のファイルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-200">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![基本ファイルをオーバーライドするように設定された 3 つの docker-compose ファイルの図。](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

<span data-ttu-id="6ddc4-202">**図 6-12**。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-202">**Figure 6-12**.</span></span> <span data-ttu-id="6ddc4-203">基本の docker-compose.yml ファイル内の値をオーバーライドする複数の docker-compose ファイル</span><span class="sxs-lookup"><span data-stu-id="6ddc4-203">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="6ddc4-204">複数の docker-compose\*.yml ファイルを組み合わせて、さまざまな環境を処理することができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-204">You can combine multiple docker-compose\*.yml files to handle different environments.</span></span> <span data-ttu-id="6ddc4-205">基本の docker-compose.yml ファイルから開始します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-205">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="6ddc4-206">この基本ファイルには、環境に合わせて変更されない基本構成または静的な構成設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-206">This base file contains the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="6ddc4-207">たとえば、eShopOnContainers アプリには、基本ファイルとして次の docker-compose.yml ファイル (サービスを減らして簡略化したもの) があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-207">For example, the eShopOnContainers app has the following docker-compose.yml file (simplified with fewer services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket-api:
    image: eshop/basket-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basketdata
      - identity-api
      - rabbitmq

  catalog-api:
    image: eshop/catalog-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sqldata
      - rabbitmq

  marketing-api:
    image: eshop/marketing-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sqldata
      - nosqldata
      - identity-api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog-api
      - ordering-api
      - identity-api
      - basket-api
      - marketing-api

  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest

  nosqldata:
    image: mongo

  basketdata:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="6ddc4-208">基本の docker-compose.yml ファイル内の値は、ターゲット展開環境が異なるため、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-208">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="6ddc4-209">たとえば、webmvc サービス定義に注目すると、ターゲットとする環境が何であれ、その情報がほとんど同じであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-209">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="6ddc4-210">次の情報があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-210">You have the following information:</span></span>

- <span data-ttu-id="6ddc4-211">サービス名: webmvc</span><span class="sxs-lookup"><span data-stu-id="6ddc4-211">The service name: webmvc.</span></span>

- <span data-ttu-id="6ddc4-212">コンテナーのカスタム イメージ: eshop/webmvc</span><span class="sxs-lookup"><span data-stu-id="6ddc4-212">The container's custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="6ddc4-213">使用する Dockerfile を示す、カスタム Docker イメージをビルドするコマンド</span><span class="sxs-lookup"><span data-stu-id="6ddc4-213">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="6ddc4-214">他の依存関係コンテナーが起動されるまで、このコンテナーを起動しないようする、他のサービスへの依存関係</span><span class="sxs-lookup"><span data-stu-id="6ddc4-214">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="6ddc4-215">追加の構成を持つことはできますが、重要な点は、基本の docker-compose.yml ファイルでは、環境間で共通する情報だけを設定することです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-215">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="6ddc4-216">その後、docker-compose.override.yml または運用またはステージングの同様のファイルで、各環境に固有の構成を配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-216">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="6ddc4-217">通常、docker-compose.override.yml は、eShopOnContainers からの次の例のように、開発環境のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-217">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basketdata}
      - identityUrl=http://identity-api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=[PLACEHOLDER]}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=[PLACEHOLDER]}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity-api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog-api/hc
      - OrderingUrlHC=http://ordering-api/hc
      - IdentityUrlHC=http://identity-api/hc
      - BasketUrlHC=http://basket-api/hc
      - MarketingUrlHC=http://marketing-api/hc
      - PaymentUrlHC=http://payment-api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sqldata:
    environment:
      - SA_PASSWORD=[PLACEHOLDER]
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
  basketdata:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="6ddc4-218">この例では、開発オーバーライド構成でいくつかのポートをホストに公開し、リダイレクト URL で環境変数を定義し、開発環境への接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-218">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="6ddc4-219">これらの設定はすべて、開発環境のためだけのものです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-219">These settings are all just for the development environment.</span></span>

<span data-ttu-id="6ddc4-220">`docker-compose up` を実行 (または Visual Studio から起動) すると、コマンドは両方のオーバーライドを、2 つのファイルがマージされているかのように、自動的に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-220">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="6ddc4-221">運用環境用に、異なる構成値、ポート、または接続文字列を持つ別の Compose ファイルが必要だとします。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-221">Suppose that you want another Compose file for the production environment, with different configuration values, ports, or connection strings.</span></span> <span data-ttu-id="6ddc4-222">異なる設定と環境変数を使用して、`docker-compose.prod.yml` という名前の別の override ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-222">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="6ddc4-223">そのファイルは、別の Git リポジトリに格納したり、別のチームによって管理および保護することができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-223">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="6ddc4-224">特定の override ファイルによる展開方法</span><span class="sxs-lookup"><span data-stu-id="6ddc4-224">How to deploy with a specific override file</span></span>

<span data-ttu-id="6ddc4-225">複数の override ファイルを使用する、または異なる名前の override ファイルを使用するには、docker-compose コマンドで -f オプションを使用してファイルを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-225">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="6ddc4-226">Compose によって、コマンドラインで指定された順序でファイルがマージされます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-226">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="6ddc4-227">次の例は、override ファイルを使用した展開方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-227">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="6ddc4-228">docker-compose ファイルで環境変数を使用する</span><span class="sxs-lookup"><span data-stu-id="6ddc4-228">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="6ddc4-229">前の例に示したように、特に運用環境では、環境変数から構成情報を取得できると便利です。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-229">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="6ddc4-230">構文 ${MY\_VAR} を使用して、docker-compose ファイル内の環境変数を参照できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-230">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="6ddc4-231">docker-compose.prod.yml ファイルからの次の行は、環境変数の値の参照方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-231">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="6ddc4-232">環境変数が作成され、ホスト環境 (Linux、Windows、クラウド クラスターなど) に応じて、さまざまな方法で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-232">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="6ddc4-233">しかし、便利な方法は、.env ファイルを使用することです。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-233">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="6ddc4-234">docker-compose ファイルは、.env ファイルで既定の環境変数を宣言することをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-234">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="6ddc4-235">環境変数のこれらの値が既定値です。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-235">These values for the environment variables are the default values.</span></span> <span data-ttu-id="6ddc4-236">ただしこれらは、それぞれの環境 (ホスト OS またはクラスターからの環境変数) で定義した値によってオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-236">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="6ddc4-237">この .env ファイルを、docker-compose コマンドが実行される場所に配置します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-237">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="6ddc4-238">次の例は、eShopOnContainers アプリケーション用の [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/main/src/.env) ファイルと同様の .env ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-238">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/main/src/.env) file for the eShopOnContainers application.</span></span>

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="6ddc4-239">Docker-compose は、.env ファイル内の各行が \<variable\>=\<value\> の形式になることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-239">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="6ddc4-240">ランタイム環境で設定された値は、.env ファイル内で定義されている値を常にオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-240">The values set in the run-time environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="6ddc4-241">同様に、コマンド ライン引数を介して渡される値も、.env ファイルで設定された既定値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-241">In a similar way, values passed via command-line arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6ddc4-242">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="6ddc4-242">Additional resources</span></span>

- <span data-ttu-id="6ddc4-243">**Docker Compose の概要** </span><span class="sxs-lookup"><span data-stu-id="6ddc4-243">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="6ddc4-244">**複数の Compose ファイル** </span><span class="sxs-lookup"><span data-stu-id="6ddc4-244">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="6ddc4-245">最適化された ASP.NET Core Docker イメージをビルドする</span><span class="sxs-lookup"><span data-stu-id="6ddc4-245">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="6ddc4-246">インターネット上のソースで Docker や .NET を検索すると、ソースをコンテナーにコピーして Docker イメージを簡単にビルドする方法を示す Dockerfile が見つかります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-246">If you are exploring Docker and .NET on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="6ddc4-247">これらの例では、単純な構成を使用することで、ご利用のアプリケーションにパッケージ化された環境で Docker イメージを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-247">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="6ddc4-248">次の例は、このような単純な Dockerfile を示しています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-248">The following example shows a simple Dockerfile in this vein.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="6ddc4-249">このような Dockerfile は機能します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-249">A Dockerfile like this will work.</span></span> <span data-ttu-id="6ddc4-250">ただし、イメージ、とりわけ運用イメージは大幅に最適化できます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-250">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="6ddc4-251">コンテナーとマイクロサービス モデルでは、常にコンテナーを起動します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-251">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="6ddc4-252">コンテナーは破棄可能なため、コンテナーの一般的な使用方法では、スリープ状態のコンテナーを再起動しません。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-252">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="6ddc4-253">オーケストレーター (Kubernetes や Azure Service Fabric など) によって、イメージの新しいインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-253">Orchestrators (like Kubernetes and Azure Service Fabric) create new instances of images.</span></span> <span data-ttu-id="6ddc4-254">これは、インスタンス化のプロセスを高速化するため、アプリケーションのビルド時に、アプリケーションをプリコンパイルして最適化する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-254">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="6ddc4-255">コンテナーは起動すると、実行できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-255">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="6ddc4-256">.NET と Docker に関するブログ記事で説明されているように、`dotnet restore` および `dotnet build` CLI コマンドを使用して実行時に復元およびコンパイルしないでください。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-256">Don't restore and compile at run time using the `dotnet restore` and `dotnet build` CLI commands as you may see in blog posts about .NET and Docker.</span></span>

<span data-ttu-id="6ddc4-257">.NET チームは、.NET と ASP.NET Core をコンテナー用に最適化されたフレームワークにするための重要な作業を行っています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-257">The .NET team has been doing important work to make .NET and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="6ddc4-258">.NET は、メモリ占有領域を抑えた簡易フレームワークというだけではありません。バージョン 2.1 以降、チームでは次の 3 つの主なシナリオに合わせた Docker イメージの最適化に重点を置き、それらを *dotnet/* にある Docker Hub レジストリに発行してきました。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-258">Not only is .NET a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="6ddc4-259">**開発**: 変更の繰り返しとデバッグを迅速に行う機能が優先され、サイズは 2 番目です。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-259">**Development**: The priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="6ddc4-260">**ビルド:** アプリケーションのコンパイルが優先され、イメージにはバイナリや、バイナリを最適化するための他の依存関係が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-260">**Build**: The priority is compiling the application, and the image includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="6ddc4-261">**実稼働**: コンテナーを迅速に展開し、開始することに重点が置かれます。そのため、これらのイメージは、バイナリと、アプリケーションを稼働させるために必要なコンテンツに限定されます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-261">**Production**: The focus is fast deploying and starting of containers, so these images are limited to the binaries and content needed to run the application.</span></span>

<span data-ttu-id="6ddc4-262">.NET チームは、次の 4 つの基本的なバリエーションを [dotnet/](https://hub.docker.com/_/microsoft-dotnet/) (Docker Hub) に用意しています。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-262">The .NET team provides four basic variants in [dotnet/](https://hub.docker.com/_/microsoft-dotnet/) (at Docker Hub):</span></span>

1. <span data-ttu-id="6ddc4-263">**sdk**: 開発シナリオおよびビルド シナリオ向け</span><span class="sxs-lookup"><span data-stu-id="6ddc4-263">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="6ddc4-264">**aspnet**: ASP.NET 運用シナリオ向け</span><span class="sxs-lookup"><span data-stu-id="6ddc4-264">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="6ddc4-265">**runtime**: .NET 運用シナリオ向け</span><span class="sxs-lookup"><span data-stu-id="6ddc4-265">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="6ddc4-266">**runtime-deps**: [自己完結型アプリケーション](../../../core/deploying/index.md#publish-self-contained)の運用シナリオ向け</span><span class="sxs-lookup"><span data-stu-id="6ddc4-266">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#publish-self-contained)</span></span>

<span data-ttu-id="6ddc4-267">迅速に起動するために、ランタイム イメージでも aspnetcore\_urls にポート 80 が自動的に設定され、Ngen を使用してアセンブリのネイティブ イメージ キャッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6ddc4-267">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6ddc4-268">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="6ddc4-268">Additional resources</span></span>

- <span data-ttu-id="6ddc4-269">**ASP.NET Core を使用して最適化された Docker イメージをビルドする**
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core></span><span class="sxs-lookup"><span data-stu-id="6ddc4-269">**Building Optimized Docker Images with ASP.NET Core**
<https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core></span></span>

- <span data-ttu-id="6ddc4-270">**.NET アプリケーション用の Docker イメージのビルド**
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)</span><span class="sxs-lookup"><span data-stu-id="6ddc4-270">**Building Docker Images for .NET Applications**
[https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="6ddc4-271">[前へ](data-driven-crud-microservice.md)
> [次へ](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="6ddc4-271">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
