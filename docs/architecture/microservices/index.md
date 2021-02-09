---
title: .NET マイクロサービス。 コンテナー化された .NET アプリケーションのアーキテクチャ
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | マイクロサービスはモジュール式で独自に展開可能なサービスです。 Docker コンテナー (Linux と Windows 向け) は、サービスとその依存関係を 1 つの単位にバンドル化する (その後、分離された環境で実行される) ことで、展開とテストを簡略化します。
ms.date: 02/02/2021
ms.openlocfilehash: e9862445414dbe0bf9a1c5d36d790b57710028f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665310"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="f4447-105">.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="f4447-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![本の表紙](./media/cover-large.png)

<span data-ttu-id="f4447-107">**エディション v5.0** - ASP.NET Core 5.0 に更新されました</span><span class="sxs-lookup"><span data-stu-id="f4447-107">**EDITION v5.0** - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="f4447-108">書籍の更新とコミュニティへの投稿については、「[changelog](https://aka.ms/MicroservicesEbookChangelog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4447-108">Refer [changelog](https://aka.ms/MicroservicesEbookChangelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="f4447-109">このガイドでは、マイクロサービス ベースのアプリケーションの開発とコンテナーを使用してこれらを管理する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="f4447-109">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="f4447-110">.NET と Docker のコンテナーを使用したアーキテクチャの設計と実装アプローチについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4447-110">It discusses architectural design and implementation approaches using .NET and Docker containers.</span></span>

<span data-ttu-id="f4447-111">使用開始を容易にするため、このガイドでは、ユーザーが探究できるコンテナー化されたマイクロサービス ベースの参照アプリケーションに重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="f4447-111">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="f4447-112">参照アプリケーションは、[eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="f4447-112">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="f4447-113">アクション リンク</span><span class="sxs-lookup"><span data-stu-id="f4447-113">Action links</span></span>

- <span data-ttu-id="f4447-114">この電子書籍は、PDF 形式 (英語版のみ) で[ダウンロード](https://aka.ms/microservicesebook)することもできます</span><span class="sxs-lookup"><span data-stu-id="f4447-114">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="f4447-115">参照アプリケーションを複製/フォーク[ on GitHub の eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="f4447-115">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="f4447-116">[Channel 9 で入門ビデオ](https://aka.ms/microservices-video)を視聴</span><span class="sxs-lookup"><span data-stu-id="f4447-116">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="f4447-117">[マイクロ サービス アーキテクチャ](https://aka.ms/MicroservicesArchitecture)を今すぐ理解する</span><span class="sxs-lookup"><span data-stu-id="f4447-117">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="f4447-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="f4447-118">Introduction</span></span>

<span data-ttu-id="f4447-119">企業は、コンテナーを使用して、コストの節減、展開の問題の解決、および DevOps と製造作業の向上を実現しつつあります。</span><span class="sxs-lookup"><span data-stu-id="f4447-119">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="f4447-120">Microsoft では、Azure Kubernetes Service や Azure Service Fabric などの製品を作成したり、Docker、Mesosphere、Kubernetes などの業界リーダーと提携することで、Windows および Linux 用のコンテナーの新技術をリリースしています。</span><span class="sxs-lookup"><span data-stu-id="f4447-120">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="f4447-121">これらの製品は、企業が使用しているプラットフォームやツールに関係なく、クラウドの速度とスケールでアプリケーションを構築および展開することに役立つコンテナー ソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="f4447-121">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="f4447-122">Docker は、コンテナー業界では事実上の標準になりつつあり、Windows と Linux のエコシステムで最も重要なベンダーでサポートされています</span><span class="sxs-lookup"><span data-stu-id="f4447-122">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="f4447-123">(Microsoft は Docker をサポートする主要なクラウド ベンダーの 1 つです)。将来、Docker は、クラウドまたはオンプレミスのあらゆるデータセンターで広く使用されるようになるでしょう。</span><span class="sxs-lookup"><span data-stu-id="f4447-123">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="f4447-124">さらに、ミッション クリティカルな分散アプリケーションのための重要なアプローチとして、[マイクロサービス](https://martinfowler.com/articles/microservices.html) アーキテクチャが新たに出現しています。</span><span class="sxs-lookup"><span data-stu-id="f4447-124">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="f4447-125">マイクロサービス ベースのアーキテクチャでは、個別に開発、テスト、展開、およびバージョン管理が可能なサービスのコレクションに基づいてアプリケーションが構築されます。</span><span class="sxs-lookup"><span data-stu-id="f4447-125">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="f4447-126">このガイドについて</span><span class="sxs-lookup"><span data-stu-id="f4447-126">About this guide</span></span>

<span data-ttu-id="f4447-127">このガイドでは、マイクロサービス ベースのアプリケーションの開発とコンテナーを使用してこれらを管理する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="f4447-127">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="f4447-128">.NET と Docker のコンテナーを使用したアーキテクチャの設計と実装アプローチについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4447-128">It discusses architectural design and implementation approaches using .NET and Docker containers.</span></span> <span data-ttu-id="f4447-129">コンテナーとマイクロサービスの使用の開始を容易にするため、このガイドでは、ユーザーが探究できる参照コンテナー化されたマイクロサービス ベースのアプリケーションに重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="f4447-129">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="f4447-130">サンプル アプリケーションは、[eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="f4447-130">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="f4447-131">このガイドでは、基本的な開発とアーキテクチャに関する、主に開発環境レベルでのガイダンスが提供されます。重点は 2 つのテクノロジ:Docker と .NET に置かれます。</span><span class="sxs-lookup"><span data-stu-id="f4447-131">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET.</span></span> <span data-ttu-id="f4447-132">このガイドは、運用環境のインフラストラクチャ (クラウドまたはオンプレミス) を重視することなく、アプリケーションの設計について考慮する際にお読みいただくことを意図しています。</span><span class="sxs-lookup"><span data-stu-id="f4447-132">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="f4447-133">インフラストラクチャに関する決定は、後で実稼働可能なアプリケーションを作成するときに行います。</span><span class="sxs-lookup"><span data-stu-id="f4447-133">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="f4447-134">そのため、このガイドは、インフラストラクチャに依存しない、より開発環境中心としたものになることを意図しています。</span><span class="sxs-lookup"><span data-stu-id="f4447-134">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="f4447-135">このガイドで学習したら、次の段階は Microsoft Azure での実稼働可能なマイクロサービスについて学習することです。</span><span class="sxs-lookup"><span data-stu-id="f4447-135">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="f4447-136">バージョン</span><span class="sxs-lookup"><span data-stu-id="f4447-136">Version</span></span>

<span data-ttu-id="f4447-137">このガイドは、 **.NET 5** バージョンと、.NET 5 のリリースと同時期に更新された関連するその他の多数の同じ “相次ぐ” テクノロジ (つまり、Azure やサードパーティ製のテクノロジ) を説明するように改訂されています。</span><span class="sxs-lookup"><span data-stu-id="f4447-137">This guide has been revised to cover **.NET 5** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET 5 release.</span></span> <span data-ttu-id="f4447-138">本書がバージョン **5.0** に更新されているのはそれが理由です。</span><span class="sxs-lookup"><span data-stu-id="f4447-138">That’s why the book version has also been updated to version **5.0**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="f4447-139">このガイドに含まれないもの</span><span class="sxs-lookup"><span data-stu-id="f4447-139">What this guide does not cover</span></span>

<span data-ttu-id="f4447-140">このガイドでは、アプリケーションのライフサイクル、DevOps、CI/CD パイプライン、またはチーム作業については詳しく取り上げません。</span><span class="sxs-lookup"><span data-stu-id="f4447-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="f4447-141">これらについては、補完ガイド「[Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル](https://aka.ms/dockerlifecycleebook)」で詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="f4447-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="f4447-142">最新のガイドでも、特定のオーケストレーターに関する情報など、Azure インフラストラクチャでの実装の詳細は提供されません。</span><span class="sxs-lookup"><span data-stu-id="f4447-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4447-143">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="f4447-143">Additional resources</span></span>

- <span data-ttu-id="f4447-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル)** (ダウンロード可能な e-book)</span><span class="sxs-lookup"><span data-stu-id="f4447-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="f4447-145">対象読者</span><span class="sxs-lookup"><span data-stu-id="f4447-145">Who should use this guide</span></span>

<span data-ttu-id="f4447-146">このガイドは、Docker ベースのアプリケーションの開発とマイクロサービス ベースのアーキテクチャに詳しくない開発者およびソリューション設計者を対象にしています。</span><span class="sxs-lookup"><span data-stu-id="f4447-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="f4447-147">このガイドは、Microsoft 開発テクノロジ (特に .NET を中心とした) と Docker コンテナーを使用して、概念実証アプリケーションの設計、デザインおよび実装する方法を学習したい人向けに書かれています。</span><span class="sxs-lookup"><span data-stu-id="f4447-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET) and with Docker containers.</span></span>

<span data-ttu-id="f4447-148">新しいモダンな分散アプリケーションにどのアプローチを選択するかを決定する前に、アーキテクチャとテクノロジーの概要を必要とする、エンタープライズ アーキテクトなどの技術的意思決定者にもこのガイドは役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f4447-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="f4447-149">このガイドの使用方法</span><span class="sxs-lookup"><span data-stu-id="f4447-149">How to use this guide</span></span>

<span data-ttu-id="f4447-150">このガイドの最初の部分では、Docker コンテナーを紹介し、開発フレームワークとして .NET 5 または .NET Framework を選択する方法について説明し、マイクロサービスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="f4447-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET 5 and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="f4447-151">このコンテンツは、概要は知りたいが、コード実装の詳細について詳しく知る必要がないアーキテクトおよび技術的意思決定者向けです。</span><span class="sxs-lookup"><span data-stu-id="f4447-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="f4447-152">ガイドの 2 番目の部分は、「[Docker ベースのアプリケーションの開発プロセス](./docker-application-development-process/index.md)」セクションから始まります。</span><span class="sxs-lookup"><span data-stu-id="f4447-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="f4447-153">.NET と Docker を使用してアプリケーションを実装するための開発とマイクロサービスのパターンに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="f4447-153">It focuses on the development and microservice patterns for implementing applications using .NET and Docker.</span></span> <span data-ttu-id="f4447-154">これは、コード、パターンおよび実装の詳細を重視する開発者やアーキテクトにとって最も関心が高いセクションです。</span><span class="sxs-lookup"><span data-stu-id="f4447-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="f4447-155">関連するマイクロサービスとコンテナー ベースの参照アプリケーション: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="f4447-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="f4447-156">eShopOnContainers アプリケーションは、Docker コンテナーを使用して展開するように設計された .NET とマイクロサービスのためのオープンソースの参照アプリです。</span><span class="sxs-lookup"><span data-stu-id="f4447-156">The eShopOnContainers application is an open-source reference app for .NET and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="f4447-157">アプリケーションは、さまざまな e ストア UI フロントエンド (Web MVC アプリ、Web SPA、およびネイティブ モバイル アプリ) を含む複数のサブシステムで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f4447-157">The application consists of multiple subsystems, including several e-store UI front-ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="f4447-158">また、バック エンドのマイクロサービスと必要なサーバー側のすべての操作のためのコンテナーも含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4447-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="f4447-159">このアプリケーションの目的は、アーキテクチャのパターンを紹介することです。</span><span class="sxs-lookup"><span data-stu-id="f4447-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="f4447-160">それは、現実の世界で使用されるアプリケーションを開始するための **実稼働可能なテンプレートではありません**。</span><span class="sxs-lookup"><span data-stu-id="f4447-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="f4447-161">実際は、このアプリケーションは永久にベータ版の状態であり、新しい可能性のある興味深いテクノロジをテストするためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4447-161">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="f4447-162">フィードバックをお寄せください。</span><span class="sxs-lookup"><span data-stu-id="f4447-162">Send us your feedback!</span></span>

<span data-ttu-id="f4447-163">このガイドは、コンテナー化されたアプリケーションと .NET のマイクロサービスのアーキテクチャの理解を促進する目的で書かれています。</span><span class="sxs-lookup"><span data-stu-id="f4447-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="f4447-164">ガイドと関連する参照アプリケーションは進化していくため、お客様のフィードバックをお待ちしています。</span><span class="sxs-lookup"><span data-stu-id="f4447-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="f4447-165">このガイドを改善する方法に関するコメントがある場合は、<https://aka.ms/ebookfeedback> にフィードバックを送信してください。</span><span class="sxs-lookup"><span data-stu-id="f4447-165">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="f4447-166">謝辞</span><span class="sxs-lookup"><span data-stu-id="f4447-166">Credits</span></span>

<span data-ttu-id="f4447-167">共同作成者:</span><span class="sxs-lookup"><span data-stu-id="f4447-167">Co-Authors:</span></span>

> <span data-ttu-id="f4447-168">**Cesar de la Torre**、Microsoft Corp.、.NET 製品チーム、シニア PM</span><span class="sxs-lookup"><span data-stu-id="f4447-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="f4447-169">**Bill Wagner**、Microsoft Corp.、C+E、シニア コンテンツ開発者</span><span class="sxs-lookup"><span data-stu-id="f4447-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="f4447-170">**Mike Rousos**、Microsoft、DevDiv CAT チーム、主任ソフトウェア エンジニア</span><span class="sxs-lookup"><span data-stu-id="f4447-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="f4447-171">編集者:</span><span class="sxs-lookup"><span data-stu-id="f4447-171">Editors:</span></span>

> <span data-ttu-id="f4447-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="f4447-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="f4447-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="f4447-173">**Steve Hoag**</span></span>

<span data-ttu-id="f4447-174">参加者とレビュー担当者:</span><span class="sxs-lookup"><span data-stu-id="f4447-174">Participants and reviewers:</span></span>

> <span data-ttu-id="f4447-175">**Jeffrey Richter**、Microsoft、Azure チーム、パートナー ソフトウェア エンジニア</span><span class="sxs-lookup"><span data-stu-id="f4447-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="f4447-176">**Jimmy Bogard**、Headspring のチーフ アーキテクト</span><span class="sxs-lookup"><span data-stu-id="f4447-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="f4447-177">**Udi Dahan**、Particular Software、創設者兼最高経営責任者</span><span class="sxs-lookup"><span data-stu-id="f4447-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="f4447-178">**Jimmy Nilsson**、Factor10 の共同創始者兼最高経営責任者</span><span class="sxs-lookup"><span data-stu-id="f4447-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="f4447-179">**Glenn Condron**、ASP.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="f4447-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="f4447-180">**Mark Fussell**、Microsoft、Azure Service Fabric チーム、プリンシパル PM リーダー</span><span class="sxs-lookup"><span data-stu-id="f4447-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="f4447-181">**Diego Vega**、Microsoft、Entity Framework チーム、PM リーダー</span><span class="sxs-lookup"><span data-stu-id="f4447-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="f4447-182">**Barry Dorrans**、シニア セキュリティ プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="f4447-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="f4447-183">**Rowan Miller**、Microsoft、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="f4447-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="f4447-184">**Ankit Asthana**、Microsoft、.NET チーム、主任 PM マネージャー</span><span class="sxs-lookup"><span data-stu-id="f4447-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="f4447-185">**Scott Hunter**、Microsoft、.NET チーム、パートナー ディレクター PM</span><span class="sxs-lookup"><span data-stu-id="f4447-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="f4447-186">**Nish Anil**、Microsoft、.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="f4447-186">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="f4447-187">**Dylan Reisenberger**、Polly のアーキテクト兼開発リーダー</span><span class="sxs-lookup"><span data-stu-id="f4447-187">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="f4447-188">**Steve "ardalis" Smith** - ソフトウェア アーキテクトおよびトレーナー - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="f4447-188">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="f4447-189">**Ian Cooper**、Brighter のコーディング アーキテクト</span><span class="sxs-lookup"><span data-stu-id="f4447-189">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="f4447-190">**Unai Zorrilla**、Plain Concepts のアーキテクト兼開発リーダー</span><span class="sxs-lookup"><span data-stu-id="f4447-190">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="f4447-191">**Eduard Tomas**、Plain Concepts の開発リーダー</span><span class="sxs-lookup"><span data-stu-id="f4447-191">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="f4447-192">**Ramon Tomas**、Plain Concepts の開発者</span><span class="sxs-lookup"><span data-stu-id="f4447-192">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="f4447-193">**David Sanz**、Plain Concepts の開発者</span><span class="sxs-lookup"><span data-stu-id="f4447-193">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="f4447-194">**Javier Valero**、Grupo Solutio の最高執行責任者</span><span class="sxs-lookup"><span data-stu-id="f4447-194">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="f4447-195">**Pierre Millet**、Microsoft、シニア コンサルタント</span><span class="sxs-lookup"><span data-stu-id="f4447-195">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="f4447-196">**Michael Friis**、Docker Inc、製品マネージャー</span><span class="sxs-lookup"><span data-stu-id="f4447-196">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="f4447-197">**Charles Lowell**、Microsoft、VS CAT チーム、ソフトウェア エンジニア</span><span class="sxs-lookup"><span data-stu-id="f4447-197">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="f4447-198">**Miguel Veloso**、Plain Concepts のソフトウェア開発エンジニア</span><span class="sxs-lookup"><span data-stu-id="f4447-198">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="f4447-199">**Sumit Ghosh**、Neudesic、主席コンサルタント</span><span class="sxs-lookup"><span data-stu-id="f4447-199">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="f4447-200">Copyright</span><span class="sxs-lookup"><span data-stu-id="f4447-200">Copyright</span></span>

<span data-ttu-id="f4447-201">発行者</span><span class="sxs-lookup"><span data-stu-id="f4447-201">PUBLISHED BY</span></span>

<span data-ttu-id="f4447-202">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="f4447-202">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="f4447-203">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="f4447-203">A division of Microsoft Corporation</span></span>

<span data-ttu-id="f4447-204">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="f4447-204">One Microsoft Way</span></span>

<span data-ttu-id="f4447-205">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="f4447-205">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="f4447-206">Copyright © 2021 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="f4447-206">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="f4447-207">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="f4447-207">All rights reserved.</span></span> <span data-ttu-id="f4447-208">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="f4447-208">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="f4447-209">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="f4447-209">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="f4447-210">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f4447-210">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="f4447-211">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="f4447-211">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="f4447-212">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="f4447-212">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="f4447-213"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="f4447-213">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="f4447-214">Mac および macOS は Apple Inc. の商標です。</span><span class="sxs-lookup"><span data-stu-id="f4447-214">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="f4447-215">Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。</span><span class="sxs-lookup"><span data-stu-id="f4447-215">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="f4447-216">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="f4447-216">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="f4447-217">次へ</span><span class="sxs-lookup"><span data-stu-id="f4447-217">Next</span></span>](container-docker-introduction/index.md)
