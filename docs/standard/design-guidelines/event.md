---
description: '詳細情報: イベントのデザイン'
title: イベントのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: d64bfb13792aa9d646560de844acddd9b7e188c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642202"
---
# <a name="event-design"></a><span data-ttu-id="212dd-103">イベントのデザイン</span><span class="sxs-lookup"><span data-stu-id="212dd-103">Event Design</span></span>

<span data-ttu-id="212dd-104">イベントは、最も一般的に使用されるコールバック (フレームワークからユーザー コードを呼び出すことができるようにするコンストラクト) の形式です。</span><span class="sxs-lookup"><span data-stu-id="212dd-104">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="212dd-105">他のコールバック メカニズムとしては、デリゲートを受け取るメンバー、仮想メンバー、インターフェイス ベースのプラグインがあります。使いやすさに関する調査のデータからは、開発者の大半が、他のコールバック メカニズムを使用するよりイベントの方が使いやすいと感じていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="212dd-105">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="212dd-106">イベントは、Visual Studio や多くの言語と問題なく統合されます。</span><span class="sxs-lookup"><span data-stu-id="212dd-106">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="212dd-107">イベントには 2 つのグループがあることに注意してください。つまり、システムの状態が変化する前に発生するイベント (プリイベントと呼ばれます) と、状態が変化した後で発生するイベント (ポストイベントと呼ばれます) です。</span><span class="sxs-lookup"><span data-stu-id="212dd-107">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="212dd-108">プリイベントの例である `Form.Closing` は、フォームが閉じられる前に発生します。</span><span class="sxs-lookup"><span data-stu-id="212dd-108">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="212dd-109">ポストイベントの例である `Form.Closed` は、フォームが閉じられた後で発生します。</span><span class="sxs-lookup"><span data-stu-id="212dd-109">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="212dd-110">✔️ イベントの場合は、"起動 (fire)" や "トリガー (trigger)" ではなく、"発生 (raise)" という用語を使用します。</span><span class="sxs-lookup"><span data-stu-id="212dd-110">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="212dd-111">✔️ イベント ハンドラーとして使用する新しいデリゲートを手動で作成するのではなく、<xref:System.EventHandler%601?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="212dd-111">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="212dd-112">✔️ イベント引数としては <xref:System.EventArgs> のサブクラスを使用することを検討します。ただし、イベントでイベント処理メソッドにデータを渡す必要がないことが確実であるときは例外で、その場合は `EventArgs` 型を直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="212dd-112">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="212dd-113">`EventArgs` を直接使用する API を出荷した場合、互換性を損なうことなく、イベントで渡されるデータを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="212dd-113">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="212dd-114">サブクラスを使用した場合は、最初は完全に空であっても、必要に応じてサブクラスにプロパティを追加できます。</span><span class="sxs-lookup"><span data-stu-id="212dd-114">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="212dd-115">✔️ 各イベントを発生させるには、保護された仮想メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="212dd-115">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="212dd-116">これは、アンシールド クラスでの非静的イベントにのみ適用され、構造体、シールド クラス、または静的イベントには適用されません。</span><span class="sxs-lookup"><span data-stu-id="212dd-116">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="212dd-117">メソッドの目的は、派生クラスでオーバーライドを使用してイベントを処理する方法を提供することです。</span><span class="sxs-lookup"><span data-stu-id="212dd-117">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="212dd-118">オーバーライドは、派生クラスで基底クラスのイベントを処理するための、より柔軟かつ高速で、いっそう自然な方法です。</span><span class="sxs-lookup"><span data-stu-id="212dd-118">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="212dd-119">慣例として、メソッドの名前は、"On" で始まり、その後にイベントの名前を付けたものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="212dd-119">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="212dd-120">派生クラスでは、オーバーライドの中でメソッドの基底の実装を呼び出さないことを選択できます。</span><span class="sxs-lookup"><span data-stu-id="212dd-120">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="212dd-121">そのためには、基底クラスが正常に動作するために必要な処理をメソッドに含めないでください。</span><span class="sxs-lookup"><span data-stu-id="212dd-121">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="212dd-122">✔️ イベントを発生させる保護されたメソッドに 1 つのパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="212dd-122">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="212dd-123">パラメーターには `e` という名前を付け、イベント引数クラスとして型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="212dd-123">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="212dd-124">❌ 非静的イベントを発生させるときは、センダーとして null を渡さないでください。</span><span class="sxs-lookup"><span data-stu-id="212dd-124">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="212dd-125">✔️ 静的イベントを発生させるときは、センダーとして null を渡します。</span><span class="sxs-lookup"><span data-stu-id="212dd-125">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="212dd-126">❌ イベントを発生させるときは、イベント データ パラメーターとして null を渡さないでください。</span><span class="sxs-lookup"><span data-stu-id="212dd-126">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="212dd-127">イベント処理メソッドにデータを何も渡したくない場合は、`EventArgs.Empty` を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="212dd-127">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="212dd-128">開発者は、このパラメーターは null ではないものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="212dd-128">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="212dd-129">✔️ エンド ユーザーがキャンセルできるイベントを発生させることを検討します。</span><span class="sxs-lookup"><span data-stu-id="212dd-129">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="212dd-130">これはプリイベントにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="212dd-130">This only applies to pre-events.</span></span>

 <span data-ttu-id="212dd-131">エンド ユーザーがイベントをキャンセルできるようにするには、<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> またはそのサブクラスをイベント引数として使用します。</span><span class="sxs-lookup"><span data-stu-id="212dd-131">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="212dd-132">カスタム イベント ハンドラーの設計</span><span class="sxs-lookup"><span data-stu-id="212dd-132">Custom Event Handler Design</span></span>

 <span data-ttu-id="212dd-133">ジェネリックがサポートされていなかった古いバージョンの CLR をフレームワークで使用する必要がある場合など、`EventHandler<T>` を使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="212dd-133">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="212dd-134">そのような場合は、カスタム イベント ハンドラーのデリゲートの設計と開発が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="212dd-134">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="212dd-135">✔️ イベント ハンドラーの戻り値の型には void を使用します。</span><span class="sxs-lookup"><span data-stu-id="212dd-135">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="212dd-136">イベント ハンドラーでは、複数のイベント処理メソッドを、場合によっては複数のオブジェクトで、呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="212dd-136">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="212dd-137">イベント処理メソッドで値を返すことが許可された場合、イベントの呼び出しごとに複数の戻り値が返されます。</span><span class="sxs-lookup"><span data-stu-id="212dd-137">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="212dd-138">✔️ イベント ハンドラーの 1 番目のパラメーターは、型として `object` を使用し、名前を `sender` にします。</span><span class="sxs-lookup"><span data-stu-id="212dd-138">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="212dd-139">✔️ イベント ハンドラーの 2 番目のパラメーターは、型として <xref:System.EventArgs?displayProperty=nameWithType> またはそのサブクラスを使用し、名前を `e` にします。</span><span class="sxs-lookup"><span data-stu-id="212dd-139">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="212dd-140">❌ イベント ハンドラーで 3 つ以上のパラメーターを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="212dd-140">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="212dd-141">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="212dd-141">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="212dd-142">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="212dd-142">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="212dd-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="212dd-143">See also</span></span>

- [<span data-ttu-id="212dd-144">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="212dd-144">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="212dd-145">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="212dd-145">Framework Design Guidelines</span></span>](index.md)
