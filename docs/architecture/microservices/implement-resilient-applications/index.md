---
title: 回復性があるアプリケーションを実装する
description: マイクロサービスのアーキテクチャで中核となる概念である、回復性について説明します。 一時的な障害が発生したときのために、それらを適切に処理する方法を知っておく必要があります。
ms.date: 01/30/2020
ms.openlocfilehash: 3ed4474eaa1225e80f05db86965e4ba53b5d2301
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429326"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="72f1f-104">回復性があるアプリケーションを実装する</span><span class="sxs-lookup"><span data-stu-id="72f1f-104">Implement resilient applications</span></span>

<span data-ttu-id="72f1f-105">*マイクロサービスおよびクラウド ベースのアプリケーションは、最終的に確実に発生する部分的な障害を受け入れる必要があります。そのような部分的な障害に対する回復性があるようにアプリケーションを設計する必要があります。*</span><span class="sxs-lookup"><span data-stu-id="72f1f-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="72f1f-106">回復性は、障害から回復し、引き続き機能する能力です。</span><span class="sxs-lookup"><span data-stu-id="72f1f-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="72f1f-107">これは、障害を回避することではなく、障害が発生するという事実を受け入れ、ダウンタイムまたはデータの損失を回避するようにそれらに対応することです。</span><span class="sxs-lookup"><span data-stu-id="72f1f-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="72f1f-108">回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。</span><span class="sxs-lookup"><span data-stu-id="72f1f-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="72f1f-109">マイクロサービスベースのアプリケーションの設計および展開は難しい作業です。</span><span class="sxs-lookup"><span data-stu-id="72f1f-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="72f1f-110">しかし、何らかの障害が確実に発生する環境で、アプリケーションの稼働を維持する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="72f1f-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="72f1f-111">そのため、アプリケーションは、回復性を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="72f1f-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="72f1f-112">ネットワークの停止、クラウド内のノードまたは VM のクラッシュなどの部分的な障害に対処するように設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72f1f-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="72f1f-113">クラスタ内でマイクロサービス (コンテナー) を別のノードに移動するだけでも、アプリケーション内での断続的な短いエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72f1f-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="72f1f-114">アプリケーションの多くの個々のコンポーネントにも、正常性監視機能を組み込むも必要があります。</span><span class="sxs-lookup"><span data-stu-id="72f1f-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="72f1f-115">この章のガイドラインに従うと、複雑で、クラウド ベースの展開で発生する一時的なダウンタイムや定期的な障害があってもスムーズに動作するアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="72f1f-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="72f1f-116">eShopOnContainer では、リリース 3.0.0 まで、[型指定されたクライアント](./use-httpclientfactory-to-implement-resilient-http-requests.md)を使用した回復性の実装に [Polly ライブラリ](https://thepollyproject.azurewebsites.net/)を使用していました。</span><span class="sxs-lookup"><span data-stu-id="72f1f-116">eShopOnContainer had been using the [Polly library](https://thepollyproject.azurewebsites.net/) to implement resiliency using [Typed Clients](./use-httpclientfactory-to-implement-resilient-http-requests.md) up until the release 3.0.0.</span></span>
>
> <span data-ttu-id="72f1f-117">リリース 3.0.0 以降では、再試行をコード内で処理するのではなく、Kubernetes クラスター内で透過的で構成可能な方法で処理される [Linkerd のメッシュ](https://linkerd.io/)を使用した HTTP 呼び出しの回復性が実装されています。</span><span class="sxs-lookup"><span data-stu-id="72f1f-117">Starting with release 3.0.0, the HTTP calls resiliency is implemented using a [Linkerd mesh](https://linkerd.io/), that handles retries in a transparent and configurable fashion, within a Kubernetes cluster, without having to handle those concerns in the code.</span></span>
>
> <span data-ttu-id="72f1f-118">Polly ライブラリは、(特にサービスの起動時の) データベース接続に回復性を追加するためにまだ使用されています。</span><span class="sxs-lookup"><span data-stu-id="72f1f-118">The Polly library is still used to add resilience to database connections, specially while starting up the services.</span></span>

>[!WARNING]
> <span data-ttu-id="72f1f-119">このセクションのすべてのコード サンプルは、Linkerd の使用前に有効であり、現在の実際のコードを反映するようには更新されていません。</span><span class="sxs-lookup"><span data-stu-id="72f1f-119">All code samples in this section were valid before using Linkerd and are not updated to reflect the current actual code.</span></span> <span data-ttu-id="72f1f-120">つまり、このセクションのコンテキストで道理にかなうものです。</span><span class="sxs-lookup"><span data-stu-id="72f1f-120">So they make sense in the context of this section.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="72f1f-121">[前へ](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[次へ](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="72f1f-121">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
