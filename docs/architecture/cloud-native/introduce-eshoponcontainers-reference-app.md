---
title: EShopOnContainers reference アプリの概要
description: ASP.NET Core と Azure 用の eShopOnContainers Cloud ネイティブマイクロサービスリファレンスアプリの概要。
ms.date: 01/19/2021
ms.openlocfilehash: 35aa92794d8488c3de60f42af52654c4c26aad82
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505675"
---
# <a name="introducing-eshoponcontainers-reference-app"></a><span data-ttu-id="9e4b0-103">EShopOnContainers reference アプリの概要</span><span class="sxs-lookup"><span data-stu-id="9e4b0-103">Introducing eShopOnContainers reference app</span></span>

<span data-ttu-id="9e4b0-104">Microsoft は、一流のコミュニティエキスパートと提携して、完全な機能を備えたクラウドネイティブマイクロサービス参照アプリケーションである eShopOnContainers を生み出しました。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-104">Microsoft, in partnership with leading community experts, has produced a full-featured cloud-native microservices reference application, eShopOnContainers.</span></span> <span data-ttu-id="9e4b0-105">このアプリケーションは、.NET と Docker、および必要に応じて Azure、Kubernetes、および Visual Studio を使用してオンラインショップを構築するために構築されています。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-105">This application is built to showcase using .NET and Docker, and optionally Azure, Kubernetes, and Visual Studio, to build an online storefront.</span></span>

![eShopOnContainers サンプルアプリのスクリーンショット。](./media/eshoponcontainers-sample-app-screenshot.png)

<span data-ttu-id="9e4b0-107">**(図 2-1)** 。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-107">**Figure 2-1**.</span></span> <span data-ttu-id="9e4b0-108">eShopOnContainers サンプルアプリのスクリーンショット。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-108">eShopOnContainers Sample App Screenshot.</span></span>

<span data-ttu-id="9e4b0-109">この章を開始する前に、 [eShopOnContainers reference アプリケーション](https://github.com/dotnet-architecture/eShopOnContainers)をダウンロードすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-109">Before starting this chapter, we recommend that you download the [eShopOnContainers reference application](https://github.com/dotnet-architecture/eShopOnContainers).</span></span> <span data-ttu-id="9e4b0-110">これを行うと、表示される情報と一緒に操作しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-110">If you do so, it should be easier for you to follow along with the information presented.</span></span>

## <a name="features-and-requirements"></a><span data-ttu-id="9e4b0-111">機能と要件</span><span class="sxs-lookup"><span data-stu-id="9e4b0-111">Features and requirements</span></span>

<span data-ttu-id="9e4b0-112">まず、アプリケーションの機能と要件について確認します。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-112">Let's start with a review of the application's features and requirements.</span></span> <span data-ttu-id="9e4b0-113">EShopOnContainers アプリケーションは、t シャツやコーヒーカップなどのさまざまな物理製品を販売するオンラインストアを表します。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-113">The eShopOnContainers application represents an online store that sells various physical products like t-shirts and coffee mugs.</span></span> <span data-ttu-id="9e4b0-114">これまでにオンラインで購入したものがある場合、そのストアの使用経験は比較的なじみがあるはずです。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-114">If you've bought anything online before, the experience of using the store should be relatively familiar.</span></span> <span data-ttu-id="9e4b0-115">ストアが実装する基本的な機能の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-115">Here are some of the basic features the store implements:</span></span>

- <span data-ttu-id="9e4b0-116">カタログ項目のリスト</span><span class="sxs-lookup"><span data-stu-id="9e4b0-116">List catalog items</span></span>
- <span data-ttu-id="9e4b0-117">項目を種類でフィルター処理</span><span class="sxs-lookup"><span data-stu-id="9e4b0-117">Filter items by type</span></span>
- <span data-ttu-id="9e4b0-118">ブランド別に項目をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="9e4b0-118">Filter items by brand</span></span>
- <span data-ttu-id="9e4b0-119">買い物かごに商品を追加する</span><span class="sxs-lookup"><span data-stu-id="9e4b0-119">Add items to the shopping basket</span></span>
- <span data-ttu-id="9e4b0-120">バスケットの項目を編集または削除する</span><span class="sxs-lookup"><span data-stu-id="9e4b0-120">Edit or remove items from the basket</span></span>
- <span data-ttu-id="9e4b0-121">チェックアウト</span><span class="sxs-lookup"><span data-stu-id="9e4b0-121">Checkout</span></span>
- <span data-ttu-id="9e4b0-122">アカウントを登録する</span><span class="sxs-lookup"><span data-stu-id="9e4b0-122">Register an account</span></span>
- <span data-ttu-id="9e4b0-123">サインイン</span><span class="sxs-lookup"><span data-stu-id="9e4b0-123">Sign in</span></span>
- <span data-ttu-id="9e4b0-124">サインアウト</span><span class="sxs-lookup"><span data-stu-id="9e4b0-124">Sign out</span></span>
- <span data-ttu-id="9e4b0-125">注文の確認</span><span class="sxs-lookup"><span data-stu-id="9e4b0-125">Review orders</span></span>

<span data-ttu-id="9e4b0-126">このアプリケーションには、次の非機能的な要件もあります。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-126">The application also has the following non-functional requirements:</span></span>

- <span data-ttu-id="9e4b0-127">高可用性が必要であり、トラフィックの増加に対応するために自動的に拡張する必要があります (さらに、トラフィックのサブサイドを一度スケールダウンする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-127">It needs to be highly available and it must scale automatically to meet increased traffic (and scale back down once traffic subsides).</span></span>
- <span data-ttu-id="9e4b0-128">正常性と診断のログを使用して、問題のトラブルシューティングに役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-128">It should provide easy-to-use monitoring of its health and diagnostic logs to help troubleshoot any issues it encounters.</span></span>
- <span data-ttu-id="9e4b0-129">継続的インテグレーションとデプロイ (CI/CD) のサポートなど、アジャイル開発プロセスをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-129">It should support an agile development process, including support for continuous integration and deployment (CI/CD).</span></span>
- <span data-ttu-id="9e4b0-130">アプリケーションでは、2つの web フロントエンド (従来のアプリケーションとシングルページアプリケーション) に加えて、さまざまな種類のオペレーティングシステムを実行しているモバイルクライアントアプリもサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-130">In addition to the two web front ends (traditional and Single Page Application), the application must also support mobile client apps running different kinds of operating systems.</span></span>
- <span data-ttu-id="9e4b0-131">クロスプラットフォームのホストとクロスプラットフォームの開発をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-131">It should support cross-platform hosting and cross-platform development.</span></span>

![eShopOnContainers リファレンスアプリケーション開発アーキテクチャ。](./media/eshoponcontainers-development-architecture.png)

<span data-ttu-id="9e4b0-133">**図 2-2**.</span><span class="sxs-lookup"><span data-stu-id="9e4b0-133">**Figure 2-2**.</span></span> <span data-ttu-id="9e4b0-134">eShopOnContainers リファレンスアプリケーション開発アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-134">eShopOnContainers reference application development architecture.</span></span>

<span data-ttu-id="9e4b0-135">EShopOnContainers アプリケーションには、ASP.NET Core MVC サーバーアプリケーションまたは適切な API ゲートウェイを対象とする HTTPS 経由でアプリケーションにアクセスする web またはモバイルクライアントからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-135">The eShopOnContainers application is accessible from web or mobile clients that access the application over HTTPS targeting either the ASP.NET Core MVC server application or an appropriate API Gateway.</span></span> <span data-ttu-id="9e4b0-136">API ゲートウェイには、個々のフロントエンドクライアントからバックエンドサービスを切り離し、より優れたセキュリティを提供するなど、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-136">API Gateways offer several advantages, such as decoupling back-end services from individual front-end clients and providing better security.</span></span> <span data-ttu-id="9e4b0-137">また、アプリケーションでは、フロントエンドクライアントごとに個別の API ゲートウェイを作成することを推奨するフロントエンド (BFF) と呼ばれる関連パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-137">The application also makes use of a related pattern known as Backends-for-Frontends (BFF), which recommends creating separate API gateways for each front-end client.</span></span> <span data-ttu-id="9e4b0-138">参照アーキテクチャは、要求が web またはモバイルクライアントから送信されているかどうかに基づいて API ゲートウェイを分割する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-138">The reference architecture demonstrates breaking up the API gateways based on whether the request is coming from a web or mobile client.</span></span>

<span data-ttu-id="9e4b0-139">アプリケーションの機能は、多くの異なるマイクロサービスに分割されます。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-139">The application's functionality is broken up into many distinct microservices.</span></span> <span data-ttu-id="9e4b0-140">認証と id、製品カタログからのアイテムの一覧表示、ユーザーの買い物かごの管理、注文の配置を担当するサービスがあります。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-140">There are services responsible for authentication and identity, listing items from the product catalog, managing users' shopping baskets, and  placing orders.</span></span> <span data-ttu-id="9e4b0-141">これらの各サービスには、独自の永続的なストレージがあります。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-141">Each of these separate services has its own persistent storage.</span></span> <span data-ttu-id="9e4b0-142">すべてのサービスがやり取りする単一のマスター データ ストアは存在しません。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-142">There's no single master data store with which all services interact.</span></span> <span data-ttu-id="9e4b0-143">代わりに、サービス間の調整と通信は、必要に応じて、メッセージバスを使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-143">Instead, coordination and communication between the services is done on an as-needed basis and by using a message bus.</span></span>

<span data-ttu-id="9e4b0-144">各マイクロサービスは、個々の要件に基づいて異なる方法で設計されています。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-144">Each of the different microservices is designed differently, based on their individual requirements.</span></span> <span data-ttu-id="9e4b0-145">この側面は、テクノロジスタックが異なる可能性があることを意味しますが、これらはすべて .NET を使用して構築され、クラウド向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-145">This aspect means their technology stack may differ, although they're all built using .NET and designed for the cloud.</span></span> <span data-ttu-id="9e4b0-146">より単純なサービスは、基になるデータストアへの基本的な作成、読み取り、更新、削除 (CRUD) アクセスを提供します。さらに高度なサービスでは Domain-Driven 設計アプローチとパターンを使用して、ビジネスの複雑さを管理します。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-146">Simpler services provide basic Create-Read-Update-Delete (CRUD) access to the underlying data stores, while more advanced services use Domain-Driven Design approaches and patterns to manage business complexity.</span></span>

![さまざまな種類のマイクロサービス](./media/different-kinds-of-microservices.png)

<span data-ttu-id="9e4b0-148">**図 2-3**.</span><span class="sxs-lookup"><span data-stu-id="9e4b0-148">**Figure 2-3**.</span></span> <span data-ttu-id="9e4b0-149">さまざまな種類のマイクロサービス。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-149">Different kinds of microservices.</span></span>

## <a name="overview-of-the-code"></a><span data-ttu-id="9e4b0-150">コードの概要</span><span class="sxs-lookup"><span data-stu-id="9e4b0-150">Overview of the code</span></span>

<span data-ttu-id="9e4b0-151">マイクロサービスを使用するため、eShopOnContainers アプリには、GitHub リポジトリに多数の独立したプロジェクトとソリューションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-151">Because it uses microservices, the eShopOnContainers app includes quite a few separate projects and solutions in its GitHub repository.</span></span> <span data-ttu-id="9e4b0-152">ソリューションと実行可能ファイルを分離するだけでなく、さまざまなサービスは独自のコンテナー内で実行するように設計されています。これは、ローカルでの開発時と運用時の両方で実行できます。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-152">In addition to separate solutions and executable files, the various services are designed to run inside their own containers, both during local development and at runtime in production.</span></span> <span data-ttu-id="9e4b0-153">図2-4 は、さまざまなプロジェクトが編成されている Visual Studio の完全なソリューションを示しています。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-153">Figure 2-4 shows the full Visual Studio solution, in which the various different projects are organized.</span></span>

![Visual Studio ソリューション内のプロジェクト。](./media/projects-in-visual-studio-solution.png)

<span data-ttu-id="9e4b0-155">**図 2-4**</span><span class="sxs-lookup"><span data-stu-id="9e4b0-155">**Figure 2-4**.</span></span> <span data-ttu-id="9e4b0-156">Visual Studio ソリューション内のプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-156">Projects in Visual Studio solution.</span></span>

<span data-ttu-id="9e4b0-157">コードはさまざまなマイクロサービスをサポートするように編成されており、各マイクロサービス内では、コードがドメインロジック、インフラストラクチャの問題、およびユーザーインターフェイスまたはサービスエンドポイントに分割されます。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-157">The code is organized to support the different microservices, and within each microservice, the code is broken up into domain logic, infrastructure concerns, and user interface or service endpoint.</span></span> <span data-ttu-id="9e4b0-158">多くの場合、各サービスの依存関係は、運用環境の Azure サービスと、ローカル開発のための別のオプションによって満たされます。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-158">In many cases, each service's dependencies can be fulfilled by Azure services in production, and alternative options for local development.</span></span> <span data-ttu-id="9e4b0-159">アプリケーションの要件が Azure サービスにどのように対応しているかを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-159">Let's examine how the application's requirements map to Azure services.</span></span>

## <a name="understanding-microservices"></a><span data-ttu-id="9e4b0-160">マイクロサービスについて</span><span class="sxs-lookup"><span data-stu-id="9e4b0-160">Understanding microservices</span></span>

<span data-ttu-id="9e4b0-161">この本は、Azure テクノロジを使用して構築されたクラウドネイティブアプリケーションに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-161">This book focuses on cloud-native applications built using Azure technology.</span></span> <span data-ttu-id="9e4b0-162">マイクロサービスのベストプラクティスと、マイクロサービスベースのアプリケーションを設計する方法の詳細については、「 [.Net マイクロサービス: コンテナー化された .Net アプリケーションのアーキテクチャ](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e4b0-162">To learn more about microservices best practices and how to architect microservice-based applications, read the companion book, [.NET Microservices: Architecture for Containerized .NET Applications](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9e4b0-163">[前へ](candidate-apps.md)
>[次へ](map-eshoponcontainers-azure-services.md)</span><span class="sxs-lookup"><span data-stu-id="9e4b0-163">[Previous](candidate-apps.md)
[Next](map-eshoponcontainers-azure-services.md)</span></span>
