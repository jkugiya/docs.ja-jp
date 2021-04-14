---
title: 状態管理
description: ASP.NET Web Forms と Blazor で状態を管理するためのさまざまなアプローチについて説明します。
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: 2ca811f886c6a245ac16c2bd66a68ff16e5bfc44
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "88267725"
---
# <a name="state-management"></a><span data-ttu-id="c6371-103">状態管理</span><span class="sxs-lookup"><span data-stu-id="c6371-103">State management</span></span>

<span data-ttu-id="c6371-104">状態管理は Web Forms アプリケーションのカギを握る概念であり、ビュー状態、セッション状態、アプリケーション状態、およびポストバックの機能を使用することで容易になります。</span><span class="sxs-lookup"><span data-stu-id="c6371-104">State management is a key concept of Web Forms applications, facilitated through View State, Session State, Application State, and Postback features.</span></span> <span data-ttu-id="c6371-105">このフレームワークのステートフル機能は、アプリケーションに必要な状態管理を隠し、アプリケーション開発者が機能の提供に専念できるようにするために役立ちました。</span><span class="sxs-lookup"><span data-stu-id="c6371-105">These stateful features of the framework helped to hide the state management required for an application and allow application developers to focus on delivering their functionality.</span></span> <span data-ttu-id="c6371-106">ASP.NET Core と Blazor を使用する場合、これらの機能の一部は再配置され、一部は完全に削除されました。</span><span class="sxs-lookup"><span data-stu-id="c6371-106">With ASP.NET Core and Blazor, some of these features have been relocated and some have been removed altogether.</span></span> <span data-ttu-id="c6371-107">この章では、Blazor の新機能を使用して、状態を維持し、同じ機能を提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6371-107">This chapter reviews how to maintain state and deliver the same functionality with the new features in Blazor.</span></span>

## <a name="request-state-management-with-viewstate"></a><span data-ttu-id="c6371-108">ViewState を使用した要求の状態管理</span><span class="sxs-lookup"><span data-stu-id="c6371-108">Request state management with ViewState</span></span>

<span data-ttu-id="c6371-109">Web Forms アプリケーションでの状態管理を説明する際には、多くの開発者がすぐに ViewState のことを考えます。</span><span class="sxs-lookup"><span data-stu-id="c6371-109">When discussing state management in Web Forms application, many developers will immediately think of ViewState.</span></span> <span data-ttu-id="c6371-110">Web Forms では、ViewState によって HTTP 要求間のコンテンツの状態が管理されます。それには、大きなエンコードされたテキストのブロックがブラウザーとの間で送受信されます。</span><span class="sxs-lookup"><span data-stu-id="c6371-110">In Web Forms, ViewState manages the state of the content between HTTP requests by sending a large encoded block of text back and forth to the browser.</span></span> <span data-ttu-id="c6371-111">ViewState フィールドは、多くの要素を含むページからのコンテンツでいっぱいになり、サイズが数メガバイトにまで拡大する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c6371-111">The ViewState field could be overwhelmed with content from a page containing many elements, potentially expanding to several megabytes in size.</span></span>

<span data-ttu-id="c6371-112">Blazor Server では、アプリによってサーバーとの継続的な接続が維持されます。</span><span class="sxs-lookup"><span data-stu-id="c6371-112">With Blazor Server, the app maintains an ongoing connection with the server.</span></span> <span data-ttu-id="c6371-113">接続がアクティブと見なされている間、アプリの状態 ("*回線*" と呼ばれます) はサーバー メモリに保持されます。</span><span class="sxs-lookup"><span data-stu-id="c6371-113">The app's state, called a *circuit*, is held in server memory while the connection is considered active.</span></span> <span data-ttu-id="c6371-114">状態は、ユーザーがアプリやアプリ内の特定のページから移動したときにのみ破棄されます。</span><span class="sxs-lookup"><span data-stu-id="c6371-114">State will only be disposed when the user navigates away from the app or a particular page in the app.</span></span> <span data-ttu-id="c6371-115">アクティブなコンポーネントのすべてのメンバーは、サーバーとの各対話の間で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c6371-115">All members of the active components are available between interactions with the server.</span></span>

<span data-ttu-id="c6371-116">この機能にはいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="c6371-116">There are several advantages of this feature:</span></span>

- <span data-ttu-id="c6371-117">コンポーネントの状態はいつでも使用でき、対話間で再構築されることはありません。</span><span class="sxs-lookup"><span data-stu-id="c6371-117">Component state is readily available and not rebuilt between interactions.</span></span>
- <span data-ttu-id="c6371-118">状態はブラウザーに送信されません。</span><span class="sxs-lookup"><span data-stu-id="c6371-118">State isn't transmitted to the browser.</span></span>

<span data-ttu-id="c6371-119">ただし、メモリ内のコンポーネント状態の永続化には、注意すべきいくつかの欠点があります。</span><span class="sxs-lookup"><span data-stu-id="c6371-119">However, there are some disadvantages to in-memory component state persistence to be aware of:</span></span>

- <span data-ttu-id="c6371-120">要求の間でサーバーが再起動した場合、状態は失われます。</span><span class="sxs-lookup"><span data-stu-id="c6371-120">If the server restarts between request, state is lost.</span></span>
- <span data-ttu-id="c6371-121">アプリケーション Web サーバーの負荷分散ソリューションには、同じブラウザーからのすべての要求が同じサーバーに返されるようにするために、スティッキー セッションが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6371-121">Your application web server load-balancing solution must include sticky sessions to ensure that all requests from the same browser return to the same server.</span></span> <span data-ttu-id="c6371-122">要求が別のサーバーに送信されると、状態は失われます。</span><span class="sxs-lookup"><span data-stu-id="c6371-122">If a request goes to a different server, state will be lost.</span></span>
- <span data-ttu-id="c6371-123">サーバー上でのコンポーネント状態の永続化は、Web サーバーのメモリ負荷につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c6371-123">Persistence of component state on the server can lead to memory pressure on the web server.</span></span>

<span data-ttu-id="c6371-124">上記の理由から、サーバー上のメモリ内に存在するコンポーネントの状態のみに依存することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="c6371-124">For the preceding reasons, don't rely on just the state of the component to reside in-memory on the server.</span></span> <span data-ttu-id="c6371-125">アプリケーションには、要求間のデータ用にバッキング データ ストアも含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6371-125">Your application should also include some backing data store for data between requests.</span></span> <span data-ttu-id="c6371-126">この戦略のシンプルな例をいくつか次に示します。</span><span class="sxs-lookup"><span data-stu-id="c6371-126">Some simple examples of this strategy:</span></span>

- <span data-ttu-id="c6371-127">ショッピング カート アプリケーションで、カートに追加された新しいアイテムの内容をデータベース レコードに保持します。</span><span class="sxs-lookup"><span data-stu-id="c6371-127">In a shopping cart application, persist the content of new items added to the cart in a database record.</span></span> <span data-ttu-id="c6371-128">サーバー上にある状態が失われた場合は、データベース レコードから再構築できます。</span><span class="sxs-lookup"><span data-stu-id="c6371-128">If the state on the server is lost, you can reconstitute it from the database records.</span></span>
- <span data-ttu-id="c6371-129">マルチパート Web フォームでは、ユーザーは、各要求の間にアプリケーションによって値が記憶されることを期待します。</span><span class="sxs-lookup"><span data-stu-id="c6371-129">In a multi-part web form, your users will expect your application to remember values between each request.</span></span> <span data-ttu-id="c6371-130">ユーザーの各投稿の間でデータ ストアにデータを書き込み、マルチパート フォームが完了したときに、そのデータをフェッチして最終的なフォーム応答構造にまとめられるようにします。</span><span class="sxs-lookup"><span data-stu-id="c6371-130">Write the data between each of your user's posts to a data store so that they can be fetched and assembled into the final form response structure when the multi-part form is completed.</span></span>

<span data-ttu-id="c6371-131">Blazor アプリでの状態管理の詳細については、「[ASP.NET Core Blazor の状態管理](/aspnet/core/blazor/state-management)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6371-131">For additional details on managing state in Blazor apps, see [ASP.NET Core Blazor state management](/aspnet/core/blazor/state-management).</span></span>

## <a name="maintain-state-with-session"></a><span data-ttu-id="c6371-132">セッションで状態を維持する</span><span class="sxs-lookup"><span data-stu-id="c6371-132">Maintain state with Session</span></span>

<span data-ttu-id="c6371-133">Web Forms 開発者は、<xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> ディクショナリ オブジェクトを使用して、現在操作しているユーザーに関する情報を保持できます。</span><span class="sxs-lookup"><span data-stu-id="c6371-133">Web Forms developers could maintain information about the currently acting user with the <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> dictionary object.</span></span> <span data-ttu-id="c6371-134">文字列キーを使用して `Session` にオブジェクトを追加するのはとても簡単です。そのオブジェクトは、その後ユーザーがアプリケーションと対話している間に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c6371-134">It's easy enough to add an object with a string key to the `Session`, and that object would be available at a later time during the user's interactions with the application.</span></span> <span data-ttu-id="c6371-135">HTTP との対話の管理を回避しようとする際には、`Session` オブジェクトによって状態が管理しやすくなりました。</span><span class="sxs-lookup"><span data-stu-id="c6371-135">In an attempt to eliminate managing interacting with HTTP, the `Session` object made it easy to maintain state.</span></span>

<span data-ttu-id="c6371-136">.NET Framework `Session` オブジェクトのシグネチャは、ASP.NET Core `Session` オブジェクトと同じではありません。</span><span class="sxs-lookup"><span data-stu-id="c6371-136">The signature of the .NET Framework `Session` object isn't the same as the ASP.NET Core `Session` object.</span></span> <span data-ttu-id="c6371-137">移行して新しいセッション状態機能を使用することを決定する前に、[新しい ASP.NET Core セッションのドキュメント](/dotnet/api/microsoft.aspnetcore.http.isession)を検討してください。</span><span class="sxs-lookup"><span data-stu-id="c6371-137">Consider [the documentation for the new ASP.NET Core Session](/dotnet/api/microsoft.aspnetcore.http.isession) before deciding to migrate and use the new session state feature.</span></span>

<span data-ttu-id="c6371-138">セッションは ASP.NET Core と Blazor Server で使用できますが、データを適切にデータ リポジトリに格納することが推奨されるため、使用はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="c6371-138">Session is available in ASP.NET Core and Blazor Server, but is discouraged from use in favor of storing data in a data repository appropriately.</span></span> <span data-ttu-id="c6371-139">また、訪問者がプライバシーの懸念からアプリケーションでの HTTP Cookie の使用を拒否した場合も、セッション状態は機能しません。</span><span class="sxs-lookup"><span data-stu-id="c6371-139">Session state is also not functional if visitors decline the use HTTP cookies in your application due to privacy concerns.</span></span>

<span data-ttu-id="c6371-140">ASP.NET Core とセッション状態の構成については、[「ASP.NET Core でのセッションと状態の管理」の記事](/aspnet/core/fundamentals/app-state#session-state)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6371-140">Configuration for ASP.NET Core and Session state is available in the [Session and state management in ASP.NET Core article](/aspnet/core/fundamentals/app-state#session-state).</span></span>

## <a name="application-state"></a><span data-ttu-id="c6371-141">アプリケーションの状態</span><span class="sxs-lookup"><span data-stu-id="c6371-141">Application state</span></span>

<span data-ttu-id="c6371-142">Web Forms フレームワークの `Application` オブジェクトには、アプリケーション スコープの構成および状態と対話するための、大規模なクロス要求リポジトリが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c6371-142">The `Application` object in the Web Forms framework provides a massive, cross-request repository for interacting with application-scope configuration and state.</span></span> <span data-ttu-id="c6371-143">アプリケーション状態は、要求を行うユーザーに関係なく、すべての要求で参照される、さまざまなアプリケーション構成プロパティを格納するための理想的な場所でした。</span><span class="sxs-lookup"><span data-stu-id="c6371-143">Application state was an ideal place to store various application configuration properties that would be referenced by all requests, regardless of the user making the request.</span></span> <span data-ttu-id="c6371-144">`Application` オブジェクトの問題は、データが複数のサーバーにわたって保持されないということでした。</span><span class="sxs-lookup"><span data-stu-id="c6371-144">The problem with the `Application` object was that data didn't persist across multiple servers.</span></span> <span data-ttu-id="c6371-145">アプリケーション オブジェクトの状態は、再起動の間に失われました。</span><span class="sxs-lookup"><span data-stu-id="c6371-145">The state of the application object was lost between restarts.</span></span>

<span data-ttu-id="c6371-146">`Session` と同様に、複数のサーバー インスタンスからアクセスできる永続的なバッキング ストアにデータを移動することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6371-146">As with `Session`, it's recommended that data move to a persistent backing store that could be accessed by multiple server instances.</span></span> <span data-ttu-id="c6371-147">複数の要求およびユーザー間でアクセスできるようにしたい揮発性のデータがある場合は、シングルトン サービスに簡単に格納して、それをこの情報または対話を必要とするコンポーネントに挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="c6371-147">If there is volatile data that you would like to be able to access across requests and users, you could easily store it in a singleton service that can be injected into components that require this information or interaction.</span></span>

<span data-ttu-id="c6371-148">アプリケーション状態を維持するためのオブジェクトの構築とその使用は、次の実装のようになります。</span><span class="sxs-lookup"><span data-stu-id="c6371-148">The construction of an object to maintain application state and its consumption could resemble the following implementation:</span></span>

```csharp
public class MyApplicationState
{
    public int VisitorCounter { get; private set; } = 0;

    public void IncrementCounter() => VisitorCounter += 1;
}
```

```csharp
app.AddSingleton<MyApplicationState>();
```

```razor
@inject MyApplicationState AppState

<label>Total Visitors: @AppState.VisitorCounter</label>
```

<span data-ttu-id="c6371-149">`MyApplicationState` オブジェクトはサーバーで 1 回だけ作成され、値 `VisitorCounter` がフェッチされて、コンポーネントのラベルに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c6371-149">The `MyApplicationState` object is created only once on the server, and the value `VisitorCounter` is fetched and output in the component's label.</span></span> <span data-ttu-id="c6371-150">持続性とスケーラビリティのために、`VisitorCounter` 値は永続化され、バッキング データ ストアから取得される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6371-150">The `VisitorCounter` value should be persisted and retrieved from a backing data store for durability and scalability.</span></span>

## <a name="in-the-browser"></a><span data-ttu-id="c6371-151">ブラウザー内</span><span class="sxs-lookup"><span data-stu-id="c6371-151">In the browser</span></span>

<span data-ttu-id="c6371-152">アプリケーション データは、クライアント側でユーザーのデバイスに格納し、後で使用できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c6371-152">Application data can also be stored client-side on the user's device so that is available later.</span></span> <span data-ttu-id="c6371-153">ユーザーのブラウザーの異なるスコープでデータの永続化を可能にするブラウザー機能が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="c6371-153">There are two browser features that allow for persistence of data in different scopes of the user's browser:</span></span>

- <span data-ttu-id="c6371-154">`localStorage` - スコープはユーザーのブラウザー全体です。</span><span class="sxs-lookup"><span data-stu-id="c6371-154">`localStorage` - scoped to the user's entire browser.</span></span> <span data-ttu-id="c6371-155">ページを再読み込みしたり、ブラウザーを閉じて再度開いたり、同じ URL で別のタブを開いたりすると、ブラウザーによって同じ `localStorage` が提供されます</span><span class="sxs-lookup"><span data-stu-id="c6371-155">If the page is reloaded, the browser is closed and reopened, or another tab is opened with the same URL then the same `localStorage` is provided by the browser</span></span>
- <span data-ttu-id="c6371-156">`sessionStorage` - スコープはユーザーの現在のブラウザー タブです。タブが再読み込みされた場合、状態は維持されます。</span><span class="sxs-lookup"><span data-stu-id="c6371-156">`sessionStorage` - scoped to the user's current browser tab. If the tab is reloaded, the state persists.</span></span> <span data-ttu-id="c6371-157">しかし、ユーザーが別のタブでアプリケーションを開いたり、ブラウザーを閉じてから再度開いたりすると、状態は失われます。</span><span class="sxs-lookup"><span data-stu-id="c6371-157">However, if the user opens another tab to your application or closes and reopens the browser the state is lost.</span></span>

<span data-ttu-id="c6371-158">これらの機能と対話するカスタム JavaScript コードを記述することもできますし、この機能を提供する多数の NuGet パッケージも使用可能です。</span><span class="sxs-lookup"><span data-stu-id="c6371-158">You can write some custom JavaScript code to interact with these features, or there are a number of NuGet packages that you can use that provide this functionality.</span></span> <span data-ttu-id="c6371-159">そのようなパッケージの 1 つは [Microsoft.AspNetCore.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage) です。</span><span class="sxs-lookup"><span data-stu-id="c6371-159">One such package is [Microsoft.AspNetCore.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage).</span></span>

<span data-ttu-id="c6371-160">このパッケージを使用して `localStorage` や `sessionStorage` と対話する方法については、[Blazor 状態管理](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6371-160">For instructions on utilizing this package to interact with `localStorage` and `sessionStorage`, see the [Blazor State Management](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) article.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c6371-161">[前へ](pages-routing-layouts.md)
>[次へ](forms-validation.md)</span><span class="sxs-lookup"><span data-stu-id="c6371-161">[Previous](pages-routing-layouts.md)
[Next](forms-validation.md)</span></span>
