---
title: マイクロサービスを基にしている複合 UI を作成する
description: マイクロサービス アーキテクチャは、バックエンド専用ではありません。 フロントエンドで使用してピーク ビューを取得します。
ms.date: 01/13/2021
ms.openlocfilehash: 3d866172cf7d15486dd2cc0d5dbb286c77693cea
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189413"
---
# <a name="creating-composite-ui-based-on-microservices"></a><span data-ttu-id="e1ad5-104">マイクロサービスを基にしている複合 UI を作成する</span><span class="sxs-lookup"><span data-stu-id="e1ad5-104">Creating composite UI based on microservices</span></span>

<span data-ttu-id="e1ad5-105">マイクロサービス アーキテクチャは多くの場合、データおよびロジックを処理するサーバー側から始まりますが、通常、UI はモノリシックとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-105">Microservices architecture often starts with the server-side handling data and logic, but, in many cases, the UI is still handled as a monolith.</span></span> <span data-ttu-id="e1ad5-106">ただし、より高度なアプローチとして ([マイクロ フロントエンド](https://martinfowler.com/articles/micro-frontends.html)と呼ばれる)、マイクロサービスに基づいたアプリケーション UI を設計する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-106">However, a more advanced approach, called [micro frontends](https://martinfowler.com/articles/micro-frontends.html), is to design your application UI based on microservices as well.</span></span> <span data-ttu-id="e1ad5-107">これは、サーバー上にマイクロサービスが置かれモノリシック クライアント アプリのみでマイクロサービスが利用されるというのでなく、マイクロサービスによって複合 UI が生成されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-107">That means having a composite UI produced by the microservices, instead of having microservices on the server and just a monolithic client app consuming the microservices.</span></span> <span data-ttu-id="e1ad5-108">このアプローチの場合、ビルドするマイクロサービスは、ロジックおよび視覚的表現の両方を備えることができます。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-108">With this approach, the microservices you build can be complete with both logic and visual representation.</span></span>

<span data-ttu-id="e1ad5-109">図 4-20 に、モノリシック クライアント アプリケーションからマイクロサービスを利用するだけの簡単なアプローチを示します。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-109">Figure 4-20 shows the simpler approach of just consuming microservices from a monolithic client application.</span></span> <span data-ttu-id="e1ad5-110">当然ながら、HTML および JavaScript の生成の間に ASP.NET MVC サービスを含めることが可能です。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-110">Of course, you could have an ASP.NET MVC service in between producing the HTML and JavaScript.</span></span> <span data-ttu-id="e1ad5-111">図は簡単なものであり、マイクロサービスを利用している単一 (モノリシック) のクライアント UI が強調表示されています。またこれらのマイクロサービスでは、UI シェイプ (HTML および JavaScript) ではなく、ロジックとデータにのみ焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-111">The figure is a simplification that highlights that you have a single (monolithic) client UI consuming the microservices, which just focus on logic and data and not on the UI shape (HTML and JavaScript).</span></span>

![マイクロサービスに接続するモノリシック UI アプリの図。](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

<span data-ttu-id="e1ad5-113">**図 4-20**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-113">**Figure 4-20**.</span></span> <span data-ttu-id="e1ad5-114">バックエンド マイクロサービスを利用するモノリシック UI アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e1ad5-114">A monolithic UI application consuming back-end microservices</span></span>

<span data-ttu-id="e1ad5-115">これに対し、複合 UI は正確に生成され、マイクロサービス自体で構成されます。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-115">In contrast, a composite UI is precisely generated and composed by the microservices themselves.</span></span> <span data-ttu-id="e1ad5-116">一部のマイクロサービスでは、UI の特定の領域のビジュアル シェイプをドライブしています。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-116">Some of the microservices drive the visual shape of specific areas of the UI.</span></span> <span data-ttu-id="e1ad5-117">その場合の主な違いは、クライアント UI コンポーネント (TypeScript クラスなど) がテンプレートに基づいており、それらのテンプレートのデータ シェイプ UI ViewModel が各マイクロサービスから取得されるということです。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-117">The key difference is that you have client UI components (TypeScript classes, for example) based on templates, and the data-shaping-UI ViewModel for those templates comes from each microservice.</span></span>

<span data-ttu-id="e1ad5-118">クライアント アプリケーションの起動時、各クライアント UI コンポーネント (TypeScript クラスなど) は、特定のシナリオで ViewModels を提供できるインフラストラクチャ マイクロサービスに自らを登録します。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-118">At client application start-up time, each of the client UI components (TypeScript classes, for example) registers itself with an infrastructure microservice capable of providing ViewModels for a given scenario.</span></span> <span data-ttu-id="e1ad5-119">マイクロサービスがシェイプを変更すると、UI も変わります。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-119">If the microservice changes the shape, the UI changes also.</span></span>

<span data-ttu-id="e1ad5-120">図 4-21 に、この複合 UI アプローチのバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-120">Figure 4-21 shows a version of this composite UI approach.</span></span> <span data-ttu-id="e1ad5-121">このアプローチは、異なる手法に基づく細分化された部分を集計する他のマイクロサービスが存在する可能性があるため、簡略化されています。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-121">This approach is simplified because you might have other microservices that are aggregating granular parts that are based on different techniques.</span></span> <span data-ttu-id="e1ad5-122">それは、従来の Web アプローチ (ASP.NET MVC) または SPA (シングル ページ アプリケーション) のどちらを構築しているかに依存します。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-122">It depends on whether you're building a traditional web approach (ASP.NET MVC) or an SPA (Single Page Application).</span></span>

![多くのビュー モデルで構成された複合 UI の図。](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

<span data-ttu-id="e1ad5-124">**図 4-21**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-124">**Figure 4-21**.</span></span> <span data-ttu-id="e1ad5-125">バックエンド マイクロサービスによって成形された複合 UI アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="e1ad5-125">Example of a composite UI application shaped by back-end microservices</span></span>

<span data-ttu-id="e1ad5-126">これらの UI コンポジション マイクロサービスのそれぞれは、小規模な API ゲートウェイに似ています。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-126">Each of those UI composition microservices would be similar to a small API Gateway.</span></span> <span data-ttu-id="e1ad5-127">ただし、この場合、それぞれが小規模な UI 領域を担当します。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-127">But in this case, each one is responsible for a small UI area.</span></span>

<span data-ttu-id="e1ad5-128">マイクロサービスによってドライブされる複合 UI アプローチは、使用する UI テクノロジに応じて、直面する困難の度合いが異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-128">A composite UI approach that's driven by microservices can be more challenging or less so, depending on what UI technologies you're using.</span></span> <span data-ttu-id="e1ad5-129">たとえば、SPA またはネイティブ モバイル アプリをビルドするために使用する技法 (Xamarin アプリを開発する場合などで、このアプローチの場合は難易度がより高くなるため) が従来の Web アプリケーションをビルドするために使用する技法と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-129">For instance, you won't use the same techniques for building a traditional web application that you use for building an SPA or for native mobile app (as when developing Xamarin apps, which can be more challenging for this approach).</span></span>

<span data-ttu-id="e1ad5-130">[eShopOnContainers](https://aka.ms/MicroservicesArchitecture) サンプル アプリケーションでは複数の理由からモノリシック UI アプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-130">The [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) sample application uses the monolithic UI approach for multiple reasons.</span></span> <span data-ttu-id="e1ad5-131">まず、マイクロサービスとコンテナーの場合です。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-131">First, it's an introduction to microservices and containers.</span></span> <span data-ttu-id="e1ad5-132">複合 UI は高度な技法であり、UI の設計および開発するときには複雑な処理も求められます。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-132">A composite UI is more advanced but also requires further complexity when designing and developing the UI.</span></span> <span data-ttu-id="e1ad5-133">次に、eShopOnContainers でも Xamarin に基づいたネイティブ モバイル アプリが実現されます。この場合は、クライアント C\# 側での処理がより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-133">Second, eShopOnContainers also provides a native mobile app based on Xamarin, which would make it more complex on the client C\# side.</span></span>

<span data-ttu-id="e1ad5-134">次の参照情報を使用してマイクロサービスに基づく複合 UI に関する知識を深めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e1ad5-134">However, we encourage you to use the following references to learn more about composite UI based on microservices.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e1ad5-135">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="e1ad5-135">Additional resources</span></span>

- <span data-ttu-id="e1ad5-136">**マイクロ フロントエンド (Martin Fowler のブログ)**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-136">**Micro Frontends (Martin Fowler's blog)**</span></span>  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- <span data-ttu-id="e1ad5-137">**マイクロフロントエンド (Michael Geers サイト)**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-137">**Micro Frontends (Michael Geers site)**</span></span>  
  <https://micro-frontends.org/>
  
- <span data-ttu-id="e1ad5-138">**ASP.NET を使用した複合 UI (特定のワークショップ)**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-138">**Composite UI using ASP.NET (Particular's Workshop)**</span></span>  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- <span data-ttu-id="e1ad5-139">**Ruben Oostinga。マイクロサービス アーキテクチャでのモノリシック フロントエンド**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-139">**Ruben Oostinga. The Monolithic Frontend in the Microservices Architecture**</span></span>  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- <span data-ttu-id="e1ad5-140">**Mauro Servienti。優れた UI コンポジションの秘密**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-140">**Mauro Servienti. The secret of better UI composition**</span></span>  
  <https://particular.net/blog/secret-of-better-ui-composition>

- <span data-ttu-id="e1ad5-141">**Viktor Farcic。フロントエンド Web コンポーネントをマイクロサービスに含める**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-141">**Viktor Farcic. Including Front-End Web Components Into Microservices**</span></span>  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- <span data-ttu-id="e1ad5-142">**マイクロサービス アーキテクチャでのフロントエンドの管理**</span><span class="sxs-lookup"><span data-stu-id="e1ad5-142">**Managing Frontend in the Microservices Architecture**</span></span>  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
><span data-ttu-id="e1ad5-143">[前へ](microservices-addressability-service-registry.md)
>[次へ](resilient-high-availability-microservices.md)</span><span class="sxs-lookup"><span data-stu-id="e1ad5-143">[Previous](microservices-addressability-service-registry.md)
[Next](resilient-high-availability-microservices.md)</span></span>
