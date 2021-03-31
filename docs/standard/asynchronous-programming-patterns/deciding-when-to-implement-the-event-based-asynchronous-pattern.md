---
description: '詳細情報: イベントベースでの非同期パターンの実装時期を決定する'
title: イベントベースの非同期パターンの実装時期を決定する
ms.date: 03/30/2017
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- AsyncOperationManager class
- threading [.NET], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
ms.openlocfilehash: 463a39c398c9920d7873203f193898461171cdda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703095"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a><span data-ttu-id="20f8f-103">イベントベースの非同期パターンの実装時期を決定する</span><span class="sxs-lookup"><span data-stu-id="20f8f-103">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="20f8f-104">イベント ベースの非同期パターンは、クラスの非同期動作を公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-104">The Event-based Asynchronous Pattern provides a pattern for exposing the asynchronous behavior of a class.</span></span> <span data-ttu-id="20f8f-105">このパターンの導入に伴い、.NET では、非同期動作を公開する 2 つのパターンとして、<xref:System.IAsyncResult?displayProperty=nameWithType> インターフェイスに基づく非同期パターンとイベント ベースのパターンが定義されています。</span><span class="sxs-lookup"><span data-stu-id="20f8f-105">With the introduction of this pattern, .NET defines two patterns for exposing asynchronous behavior: the Asynchronous Pattern based on the <xref:System.IAsyncResult?displayProperty=nameWithType> interface, and the event-based pattern.</span></span> <span data-ttu-id="20f8f-106">この記事では、両方のパターンをどのような状況で実装するべきか説明します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-106">This article describes when it's appropriate for you to implement both patterns.</span></span>

<span data-ttu-id="20f8f-107"><xref:System.IAsyncResult> インターフェイスによる非同期プログラミングについて詳しくは、「[非同期プログラミング モデル (APM)](asynchronous-programming-model-apm.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="20f8f-107">For more information about asynchronous programming with the <xref:System.IAsyncResult> interface, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>

## <a name="general-principles"></a><span data-ttu-id="20f8f-108">一般原則</span><span class="sxs-lookup"><span data-stu-id="20f8f-108">General Principles</span></span>

<span data-ttu-id="20f8f-109">一般的に、可能であれば、イベント ベースの非同期パターンを利用して非同期機能を公開してください。</span><span class="sxs-lookup"><span data-stu-id="20f8f-109">In general, you should expose asynchronous features using the Event-based Asynchronous Pattern whenever possible.</span></span> <span data-ttu-id="20f8f-110">ただし、イベント ベースのパターンでは満たせない要件もあります。</span><span class="sxs-lookup"><span data-stu-id="20f8f-110">However, there are some requirements that the event-based pattern cannot meet.</span></span> <span data-ttu-id="20f8f-111">そのようなとき、場合によっては、イベント ベースのパターンに加え、<xref:System.IAsyncResult> パターンも実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20f8f-111">In those cases, you may need to implement the <xref:System.IAsyncResult> pattern in addition to the event-based pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="20f8f-112">イベント ベースのパターンを実装せずに <xref:System.IAsyncResult> パターンのみを実装することはまれです。</span><span class="sxs-lookup"><span data-stu-id="20f8f-112">It is rare for the <xref:System.IAsyncResult> pattern to be implemented without the event-based pattern also being implemented.</span></span>

## <a name="guidelines"></a><span data-ttu-id="20f8f-113">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="20f8f-113">Guidelines</span></span>

<span data-ttu-id="20f8f-114">次の一覧は、イベント ベースの非同期パターンを実装するときのガイドラインをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="20f8f-114">The following list describes the guidelines for when you should implement Event-based Asynchronous Pattern:</span></span>

- <span data-ttu-id="20f8f-115">既定の API としてイベント ベースのパターンを使用し、クラスの非同期動作を公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-115">Use the event-based pattern as the default API to expose asynchronous behavior for your class.</span></span>

- <span data-ttu-id="20f8f-116">クラスが主に、Windows フォームなど、クライアント アプリケーションで使用されるとき、<xref:System.IAsyncResult> パターンを公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="20f8f-116">Do not expose the <xref:System.IAsyncResult> pattern when your class is primarily used in a client application, for example Windows Forms.</span></span>

- <span data-ttu-id="20f8f-117">要件を満たすために必要なときにのみ、<xref:System.IAsyncResult> パターンを公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-117">Only expose the <xref:System.IAsyncResult> pattern when it is necessary for meeting your requirements.</span></span> <span data-ttu-id="20f8f-118">たとえば、既存の API との互換性を得るために <xref:System.IAsyncResult> パターンを公開する必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="20f8f-118">For example, compatibility with an existing API may require you to expose the <xref:System.IAsyncResult> pattern.</span></span>

- <span data-ttu-id="20f8f-119"><xref:System.IAsyncResult> パターンを公開するときは、イベント ベースのパターンも公開してください。</span><span class="sxs-lookup"><span data-stu-id="20f8f-119">Do not expose the <xref:System.IAsyncResult> pattern without also exposing the event-based pattern.</span></span>

- <span data-ttu-id="20f8f-120"><xref:System.IAsyncResult> パターンを公開する必要がある場合、詳細設定のオプションとしてそれを行います。</span><span class="sxs-lookup"><span data-stu-id="20f8f-120">If you must expose the <xref:System.IAsyncResult> pattern, do so as an advanced option.</span></span> <span data-ttu-id="20f8f-121">たとえば、プロキシ オブジェクトを生成する場合、既定でイベント ベースのパターンを生成し、<xref:System.IAsyncResult> パターンを生成するオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-121">For example, if you generate a proxy object, generate the event-based pattern by default, with an option to generate the <xref:System.IAsyncResult> pattern.</span></span>

- <span data-ttu-id="20f8f-122"><xref:System.IAsyncResult> パターンの実装を基盤にしてイベント ベースのパターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-122">Build your event-based pattern implementation on your <xref:System.IAsyncResult> pattern implementation.</span></span>

- <span data-ttu-id="20f8f-123">同じクラスでイベント ベースのパターンと <xref:System.IAsyncResult> パターンの両方を公開することは避けます。</span><span class="sxs-lookup"><span data-stu-id="20f8f-123">Avoid exposing both the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class.</span></span> <span data-ttu-id="20f8f-124">イベント ベースのパターンを "上位" クラスで公開し、<xref:System.IAsyncResult> パターンを "下位" クラスで公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-124">Expose the event-based pattern on "higher level" classes and the <xref:System.IAsyncResult> pattern on "lower level" classes.</span></span> <span data-ttu-id="20f8f-125">たとえば、<xref:System.Net.WebClient> コンポーネントのイベント ベースのパターンと <xref:System.Web.HttpRequest> クラスの <xref:System.IAsyncResult> パターンを比較します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-125">For example, compare the event-based pattern on the <xref:System.Net.WebClient> component with the <xref:System.IAsyncResult> pattern on the <xref:System.Web.HttpRequest> class.</span></span>

  - <span data-ttu-id="20f8f-126">互換性のために必要なとき、イベント ベースのパターンと <xref:System.IAsyncResult> パターンを同じクラスで公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-126">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class when compatibility requires it.</span></span> <span data-ttu-id="20f8f-127">たとえば、<xref:System.IAsyncResult> パターンを使用する API を既に公開している場合、後方互換性のために <xref:System.IAsyncResult> パターンを維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20f8f-127">For example, if you have already released an API that uses the <xref:System.IAsyncResult> pattern, you would need to retain the <xref:System.IAsyncResult> pattern for backward compatibility.</span></span>

  - <span data-ttu-id="20f8f-128">最終的なオブジェクト モデルが複雑すぎて実装を分ける意味がなくなってしまう場合、イベント ベースのパターンと <xref:System.IAsyncResult> パターンを同じクラスで公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-128">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class if the resulting object model complexity outweighs the benefit of separating the implementations.</span></span> <span data-ttu-id="20f8f-129">イベント ベースのパターンを公開することを避けるより、1 つのクラスで両方のパターンを公開するほうが得策です。</span><span class="sxs-lookup"><span data-stu-id="20f8f-129">It is better to expose both patterns on a single class than to avoid exposing the event-based pattern.</span></span>

  - <span data-ttu-id="20f8f-130">イベント ベースのパターンと <xref:System.IAsyncResult> パターンを 1 つのクラスで公開する必要がある場合、<xref:System.ComponentModel.EditorBrowsableState.Advanced> に設定された <xref:System.ComponentModel.EditorBrowsableAttribute> を使用し、<xref:System.IAsyncResult> パターンの実装を高度な機能として設定します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-130">If you must expose both the event-based pattern and <xref:System.IAsyncResult> pattern on a single class, use <xref:System.ComponentModel.EditorBrowsableAttribute> set to <xref:System.ComponentModel.EditorBrowsableState.Advanced> to mark the <xref:System.IAsyncResult> pattern implementation as an advanced feature.</span></span> <span data-ttu-id="20f8f-131">これで Visual Studio IntelliSense のようなデザイン環境に、<xref:System.IAsyncResult> のプロパティやメソッドを表示しないように指示されます。</span><span class="sxs-lookup"><span data-stu-id="20f8f-131">This indicates to design environments, such as Visual Studio IntelliSense, not to display the <xref:System.IAsyncResult> properties and methods.</span></span> <span data-ttu-id="20f8f-132">これらのプロパティとメソッドには完全な有用性がまだ与えられていませんが、IntelliSense で開発している開発者は API を詳しく理解できます。</span><span class="sxs-lookup"><span data-stu-id="20f8f-132">These properties and methods are still fully usable, but the developer working through IntelliSense has a clearer view of the API.</span></span>

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a><span data-ttu-id="20f8f-133">イベント ベースのパターンに加え、IAsyncResult パターンを公開する基準</span><span class="sxs-lookup"><span data-stu-id="20f8f-133">Criteria for Exposing the IAsyncResult Pattern in Addition to the Event-based Pattern</span></span>

<span data-ttu-id="20f8f-134">前述のシナリオではイベント ベースの非同期パターンにさまざまな長所がありましたが、短所もあります。パフォーマンスが最も重要な要件であれば、その短所も考慮してください。</span><span class="sxs-lookup"><span data-stu-id="20f8f-134">While the Event-based Asynchronous Pattern has many benefits under the previously mentioned scenarios, it does have some drawbacks, which you should be aware of if performance is your most important requirement.</span></span>

<span data-ttu-id="20f8f-135">イベント ベースのパターンで <xref:System.IAsyncResult> パターンも対処されないシナリオが 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="20f8f-135">There are three scenarios that the event-based pattern does not address as well as the <xref:System.IAsyncResult> pattern:</span></span>

- <span data-ttu-id="20f8f-136">1 つの <xref:System.IAsyncResult> に対する待機をブロックする</span><span class="sxs-lookup"><span data-stu-id="20f8f-136">Blocking wait on one <xref:System.IAsyncResult></span></span>

- <span data-ttu-id="20f8f-137">たくさんの <xref:System.IAsyncResult> オブジェクトに対する待機をブロックする</span><span class="sxs-lookup"><span data-stu-id="20f8f-137">Blocking wait on many <xref:System.IAsyncResult> objects</span></span>

- <span data-ttu-id="20f8f-138"><xref:System.IAsyncResult> の完了に対するポーリング</span><span class="sxs-lookup"><span data-stu-id="20f8f-138">Polling for completion on the <xref:System.IAsyncResult></span></span>

<span data-ttu-id="20f8f-139">以上のシナリオには、イベント ベースのパターンで対処できますが、<xref:System.IAsyncResult> パターンを使用する場合より面倒になります。</span><span class="sxs-lookup"><span data-stu-id="20f8f-139">You can address these scenarios by using the event-based pattern, but doing so is more cumbersome than using the <xref:System.IAsyncResult> pattern.</span></span>

<span data-ttu-id="20f8f-140">開発者は多くの場合、一般的にパフォーマンス要件が非常に高いサービスに <xref:System.IAsyncResult> パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-140">Developers often use the <xref:System.IAsyncResult> pattern for services that typically have very high performance requirements.</span></span> <span data-ttu-id="20f8f-141">たとえば、完了のポーリング シナリオに該当するのが高性能サーバーを利用するときです。</span><span class="sxs-lookup"><span data-stu-id="20f8f-141">For example, the polling for completion scenario is a high-performance server technique.</span></span>

<span data-ttu-id="20f8f-142">また、イベント ベースのパターンは <xref:System.IAsyncResult> パターンと比べて効率性が劣ります。作成されるオブジェクトが多く (特に <xref:System.EventArgs>)、スレッド間で同期がとられるためです。</span><span class="sxs-lookup"><span data-stu-id="20f8f-142">Additionally, the event-based pattern is less efficient than the <xref:System.IAsyncResult> pattern because it creates more objects, especially <xref:System.EventArgs>, and because it synchronizes across threads.</span></span>

<span data-ttu-id="20f8f-143">次の一覧は、<xref:System.IAsyncResult> パターンを使用する場合の推奨事項をいくつか取り上げたものです。</span><span class="sxs-lookup"><span data-stu-id="20f8f-143">The following list shows some recommendations to follow if you decide to use the <xref:System.IAsyncResult> pattern:</span></span>

- <span data-ttu-id="20f8f-144"><xref:System.Threading.WaitHandle> または <xref:System.IAsyncResult> オブジェクトのサポートが厳密に必要な場合にのみ <xref:System.IAsyncResult> パターンを公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-144">Only expose the <xref:System.IAsyncResult> pattern when you specifically require support for <xref:System.Threading.WaitHandle> or <xref:System.IAsyncResult> objects.</span></span>

- <span data-ttu-id="20f8f-145">既存の API で <xref:System.IAsyncResult> パターンを使用している場合にのみ <xref:System.IAsyncResult> パターンを公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-145">Only expose the <xref:System.IAsyncResult> pattern when you have an existing API that uses the <xref:System.IAsyncResult> pattern.</span></span>

- <span data-ttu-id="20f8f-146">既存の API が <xref:System.IAsyncResult> パターンに基づく場合、次のリリースでイベント ベースのパターンも公開することを検討します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-146">If you have an existing API based on the <xref:System.IAsyncResult> pattern, consider also exposing the event-based pattern in your next release.</span></span>

- <span data-ttu-id="20f8f-147">検証済みの高いパフォーマンス要件がイベント ベースのパターンでは満たせないが、<xref:System.IAsyncResult> パターンでは満たせる場合にのみ、<xref:System.IAsyncResult> パターンを公開します。</span><span class="sxs-lookup"><span data-stu-id="20f8f-147">Only expose <xref:System.IAsyncResult> pattern if you have high performance requirements which you have verified cannot be met by the event-based pattern but can be met by the <xref:System.IAsyncResult> pattern.</span></span>

## <a name="see-also"></a><span data-ttu-id="20f8f-148">参照</span><span class="sxs-lookup"><span data-stu-id="20f8f-148">See also</span></span>

- [<span data-ttu-id="20f8f-149">方法: イベントベースの非同期パターンをサポートするコンポーネントを実装する</span><span class="sxs-lookup"><span data-stu-id="20f8f-149">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="20f8f-150">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="20f8f-150">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="20f8f-151">イベントベースの非同期パターンの実装</span><span class="sxs-lookup"><span data-stu-id="20f8f-151">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="20f8f-152">イベントベースの非同期パターンを実装するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="20f8f-152">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="20f8f-153">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="20f8f-153">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
