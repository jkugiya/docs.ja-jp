---
title: マイクロサービス API とコントラクトの作成、進化、バージョン管理
description: ニーズは変化するものなので、進化とバージョン管理を考慮してマイクロサービス API とコントラクトを作成します。
ms.date: 01/13/2021
ms.openlocfilehash: 84eeaa9776947abda6171949c730f8473e97b241
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189461"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a><span data-ttu-id="26784-103">マイクロサービス API とコントラクトの作成、進化、バージョン管理</span><span class="sxs-lookup"><span data-stu-id="26784-103">Creating, evolving, and versioning microservice APIs and contracts</span></span>

<span data-ttu-id="26784-104">マイクロサービス API は、サービスとそのクライアント間のコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="26784-104">A microservice API is a contract between the service and its clients.</span></span> <span data-ttu-id="26784-105">API コントラクトに違反していない場合に限り、マイクロサービスを単独で進化させることができます。そのため、コントラクトは非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="26784-105">You'll be able to evolve a microservice independently only if you do not break its API contract, which is why the contract is so important.</span></span> <span data-ttu-id="26784-106">コントラクトを変更すると、クライアント アプリケーションや API ゲートウェイに影響します。</span><span class="sxs-lookup"><span data-stu-id="26784-106">If you change the contract, it will impact your client applications or your API Gateway.</span></span>

<span data-ttu-id="26784-107">API 定義の性質は、使用しているプロトコルによって異なります。</span><span class="sxs-lookup"><span data-stu-id="26784-107">The nature of the API definition depends on which protocol you're using.</span></span> <span data-ttu-id="26784-108">たとえば、メッセージング ([AMQP](http://www.amqp.org/) など) を使用している場合、API は複数の種類のメッセージで構成されます。</span><span class="sxs-lookup"><span data-stu-id="26784-108">For instance, if you're using messaging (like [AMQP](http://www.amqp.org/)), the API consists of the message types.</span></span> <span data-ttu-id="26784-109">HTTP サービスと RESTful サービスを使用している場合、API は URL と、要求および応答の JSON 形式で構成されます。</span><span class="sxs-lookup"><span data-stu-id="26784-109">If you're using HTTP and RESTful services, the API consists of the URLs and the request and response JSON formats.</span></span>

<span data-ttu-id="26784-110">ただし、たとえ最初のコントラクトについて熟慮した場合でも、サービスの API は時間の経過と共に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26784-110">However, even if you're thoughtful about your initial contract, a service API will need to change over time.</span></span> <span data-ttu-id="26784-111">そのような状況になった場合、特に複数のクライアント アプリケーションによって使用されるパブリック API である場合は、通常、すべてのクライアントを強制的に新しい API コントラクトにアップグレードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="26784-111">When that happens—and especially if your API is a public API consumed by multiple client applications — you typically can't force all clients to upgrade to your new API contract.</span></span> <span data-ttu-id="26784-112">通常、サービス コントラクトの古いバージョンと新しいバージョンの両方が同時に実行されるように、新しいバージョンのサービスを段階的に展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26784-112">You usually need to incrementally deploy new versions of a service in a way that both old and new versions of a service contract are running simultaneously.</span></span> <span data-ttu-id="26784-113">そのため、サービスのバージョン管理戦略を用意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="26784-113">Therefore, it's important to have a strategy for your service versioning.</span></span>

<span data-ttu-id="26784-114">API の変更が少ない場合 (たとえば、API に属性やパラメーターを追加する場合など)、古い API を使用するクライアントが新しいバージョンのサービスに切り替えても、使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="26784-114">When the API changes are small, like if you add attributes or parameters to your API, clients that use an older API should switch and work with the new version of the service.</span></span> <span data-ttu-id="26784-115">必須の不足している属性がある場合は既定値を指定することができます。また、クライアントは追加された応答属性があっても無視できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26784-115">You might be able to provide default values for any missing attributes that are required, and the clients might be able to ignore any extra response attributes.</span></span>

<span data-ttu-id="26784-116">ただし、サービスの API に重大な互換性のない変更を加える必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="26784-116">However, sometimes you need to make major and incompatible changes to a service API.</span></span> <span data-ttu-id="26784-117">クライアント アプリケーションまたはサービスに対して、すぐに新しいバージョンにアップグレードすることを強制できないので、ある程度の期間、以前のバージョンの API をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="26784-117">Because you might not be able to force client applications or services to upgrade immediately to the new version, a service must support older versions of the API for some period.</span></span> <span data-ttu-id="26784-118">REST などの HTTP ベースのメカニズムを使用している場合は、API バージョン番号を URL または HTTP ヘッダーに埋め込む方法があります。</span><span class="sxs-lookup"><span data-stu-id="26784-118">If you're using an HTTP-based mechanism such as REST, one approach is to embed the API version number in the URL or into an HTTP header.</span></span> <span data-ttu-id="26784-119">次に、同じサービス インスタンス内で両方のバージョンのサービスを同時に実装するか、それぞれに 1 つのバージョンの API を処理する異なるインスタンスを展開するかを判断します。</span><span class="sxs-lookup"><span data-stu-id="26784-119">Then you can decide between implementing both versions of the service simultaneously within the same service instance, or deploying different instances that each handle a version of the API.</span></span> <span data-ttu-id="26784-120">この機能に適したアプローチは、異なる実装バージョンを独立したハンドラーに分離する [Mediator パターン](https://en.wikipedia.org/wiki/Mediator_pattern) (たとえば、[MediatR ライブラリ](https://github.com/jbogard/MediatR)など) です。</span><span class="sxs-lookup"><span data-stu-id="26784-120">A good approach for this functionality is the [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern) (for example, [MediatR library](https://github.com/jbogard/MediatR)) to decouple the different implementation versions into independent handlers.</span></span>

<span data-ttu-id="26784-121">最後に、REST アーキテクチャを使用している場合、[Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) はサービスのバージョン管理と API を進化させるために最適なソリューションです。</span><span class="sxs-lookup"><span data-stu-id="26784-121">Finally, if you're using a REST architecture, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) is the best solution for versioning your services and allowing evolvable APIs.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="26784-122">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="26784-122">Additional resources</span></span>

- <span data-ttu-id="26784-123">**Scott Hanselman。簡単になった ASP.NET Core RESTful Web API のバージョン管理** </span><span class="sxs-lookup"><span data-stu-id="26784-123">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="26784-124">**RESTful Web API のバージョン管理** </span><span class="sxs-lookup"><span data-stu-id="26784-124">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="26784-125">**Roy Fielding。バージョン管理、ハイパーメディア、REST** </span><span class="sxs-lookup"><span data-stu-id="26784-125">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
><span data-ttu-id="26784-126">[前へ](asynchronous-message-based-communication.md)
>[次へ](microservices-addressability-service-registry.md)</span><span class="sxs-lookup"><span data-stu-id="26784-126">[Previous](asynchronous-message-based-communication.md)
[Next](microservices-addressability-service-registry.md)</span></span>
