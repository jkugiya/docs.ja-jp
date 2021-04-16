---
title: ASP.NET Web Forms と Blazor のアーキテクチャの比較
description: ASP.NET Web Forms と Blazor のアーキテクチャの比較について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: afb5d4025b81c2ddef782c462c94d32edc872a21
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509729"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a><span data-ttu-id="8da08-103">ASP.NET Web Forms と Blazor のアーキテクチャの比較</span><span class="sxs-lookup"><span data-stu-id="8da08-103">Architecture comparison of ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="8da08-104">ASP.NET Web Forms と Blazor には多くの類似した概念がありますが、そのしくみには違いがあります。</span><span class="sxs-lookup"><span data-stu-id="8da08-104">While ASP.NET Web Forms and Blazor have many similar concepts, there are differences in how they work.</span></span> <span data-ttu-id="8da08-105">この章では、ASP.NET Web Forms と Blazor の内部動作とアーキテクチャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8da08-105">This chapter examines the inner workings and architectures of ASP.NET Web Forms and Blazor.</span></span>

## <a name="aspnet-web-forms"></a><span data-ttu-id="8da08-106">ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="8da08-106">ASP.NET Web Forms</span></span>

<span data-ttu-id="8da08-107">ASP.NET Web Forms フレームワークは、ページ中心のアーキテクチャに基づいています。</span><span class="sxs-lookup"><span data-stu-id="8da08-107">The ASP.NET Web Forms framework is based on a page-centric architecture.</span></span> <span data-ttu-id="8da08-108">アプリ内の場所に対する HTTP 要求はそれぞれ別個のページであり、ASP.NET ではそれを応答に使用します。</span><span class="sxs-lookup"><span data-stu-id="8da08-108">Each HTTP request for a location in the app is a separate page with which ASP.NET responds.</span></span> <span data-ttu-id="8da08-109">ページが要求されると、ブラウザーの内容は、要求されたページの結果に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="8da08-109">As pages are requested, the contents of the browser are replaced with the results of the page requested.</span></span>

<span data-ttu-id="8da08-110">ページは、次のコンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="8da08-110">Pages consist of the following components:</span></span>

- <span data-ttu-id="8da08-111">HTML マークアップ</span><span class="sxs-lookup"><span data-stu-id="8da08-111">HTML markup</span></span>
- <span data-ttu-id="8da08-112">C# または Visual Basic コード</span><span class="sxs-lookup"><span data-stu-id="8da08-112">C# or Visual Basic code</span></span>
- <span data-ttu-id="8da08-113">ロジックおよびイベント処理機能を含む分離コード クラス</span><span class="sxs-lookup"><span data-stu-id="8da08-113">A code-behind class containing logic and event-handling capabilities</span></span>
- <span data-ttu-id="8da08-114">コントロール</span><span class="sxs-lookup"><span data-stu-id="8da08-114">Controls</span></span>

<span data-ttu-id="8da08-115">コントロールは、ページ上でプログラムによって配置および操作できる再利用可能な Web UI ユニットです。</span><span class="sxs-lookup"><span data-stu-id="8da08-115">Controls are reusable units of web UI that can be programmatically placed and interacted with on a page.</span></span> <span data-ttu-id="8da08-116">ページは、マークアップ、コントロール、および何らかのコードを含む、 *.aspx* で終わるファイルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="8da08-116">Pages are composed of files that end with *.aspx* containing markup, controls, and some code.</span></span> <span data-ttu-id="8da08-117">分離コード クラスは同じベース名のファイルに置かれ、使用するプログラミング言語に応じて拡張子が *.aspx.cs* または *.aspx.vb* になります。</span><span class="sxs-lookup"><span data-stu-id="8da08-117">The code-behind classes are in files with the same base name and an *.aspx.cs* or *.aspx.vb* extension, depending on the programming language used.</span></span> <span data-ttu-id="8da08-118">興味深いことに、Web サーバーが *.aspx* ファイルの内容を解釈し、変更されるたびにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="8da08-118">Interestingly, the web server interprets contents of the *.aspx* files and compiles them whenever they change.</span></span> <span data-ttu-id="8da08-119">この再コンパイルは、Web サーバーが既に実行されている場合でも発生します。</span><span class="sxs-lookup"><span data-stu-id="8da08-119">This recompilation occurs even if the web server is already running.</span></span>

<span data-ttu-id="8da08-120">コントロールは、マークアップを使用して作成し、ユーザー コントロールとして提供できます。</span><span class="sxs-lookup"><span data-stu-id="8da08-120">Controls can be built with markup and delivered as user controls.</span></span> <span data-ttu-id="8da08-121">ユーザー コントロールは `UserControl` クラスから派生し、ページと同様の構造を持ちます。</span><span class="sxs-lookup"><span data-stu-id="8da08-121">A user control derives from the `UserControl` class and has a similar structure to the Page.</span></span> <span data-ttu-id="8da08-122">ユーザー コントロールのマークアップは *.ascx* ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8da08-122">Markup for user controls is stored in an *.ascx* file.</span></span> <span data-ttu-id="8da08-123">付随する分離コード クラスは、 *.ascx.cs* または *.ascx.vb* ファイルに置かれます。</span><span class="sxs-lookup"><span data-stu-id="8da08-123">An accompanying code-behind class resides in an *.ascx.cs* or *.ascx.vb* file.</span></span> <span data-ttu-id="8da08-124">コントロールは、`WebControl` または `CompositeControl` 基本クラスから継承することにより、完全にコードで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8da08-124">Controls can also be built completely with code, by inheriting from either the `WebControl` or `CompositeControl` base class.</span></span>

<span data-ttu-id="8da08-125">ページには、広範なイベント ライフサイクルもあります。</span><span class="sxs-lookup"><span data-stu-id="8da08-125">Pages also have an extensive event lifecycle.</span></span> <span data-ttu-id="8da08-126">各ページでは、ASP.NET ランタイムによって各要求のページのコードが実行されるときに発生する、初期化、ロード、プリレンダリング、およびアンロードの各イベントに対してイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="8da08-126">Each page raises events for the initialization, load, prerender, and unload events that occur as the ASP.NET runtime executes the page's code for each request.</span></span>

<span data-ttu-id="8da08-127">通常、ページ上のコントロールは、コントロールが表示されていた同じページにポストバックされ、`ViewState` という名前の隠しフォーム フィールドからのペイロードを一緒に運びます。</span><span class="sxs-lookup"><span data-stu-id="8da08-127">Controls on a Page typically post-back to the same page that presented the control, and carry along with them a payload from a hidden form field called `ViewState`.</span></span> <span data-ttu-id="8da08-128">`ViewState` フィールドには、コントロールがレンダリングされてページに表示された時点のコントロールの状態に関する情報が含まれています。これにより、ASP.NET ランタイムでは、サーバーに送信された内容を比較して変更を特定できます。</span><span class="sxs-lookup"><span data-stu-id="8da08-128">The `ViewState` field contains information about the state of the controls at the time they were rendered and presented on the page, allowing the ASP.NET runtime to compare and identify changes in the content submitted to the server.</span></span>

## Blazor

<span data-ttu-id="8da08-129">Blazor は、クライアント側の Web UI フレームワークであり、Angular や React などの JavaScript フロントエンド フレームワークに性質が似ています。</span><span class="sxs-lookup"><span data-stu-id="8da08-129">Blazor is a client-side web UI framework similar in nature to JavaScript front-end frameworks like Angular or React.</span></span> <span data-ttu-id="8da08-130">Blazor では、ユーザー操作が処理され、必要な UI の更新がレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="8da08-130">Blazor handles user interactions and renders the necessary UI updates.</span></span> <span data-ttu-id="8da08-131">Blazor は、要求/応答モデルに基づいて *いません*。</span><span class="sxs-lookup"><span data-stu-id="8da08-131">Blazor *isn't* based on a request-reply model.</span></span> <span data-ttu-id="8da08-132">ユーザー操作は、特定の HTTP 要求のコンテキストには含まれないイベントとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="8da08-132">User interactions are handled as events that aren't in the context of any particular HTTP request.</span></span>

<span data-ttu-id="8da08-133">Blazor アプリは、HTML ページ上にレンダリングされる 1 つ以上のルート コンポーネントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="8da08-133">Blazor apps consist of one or more root components that are rendered on an HTML page.</span></span>

![HTML 内の Blazor コンポーネント](./media/architecture-comparison/blazor-components-in-html.png)

<span data-ttu-id="8da08-135">コンポーネントをレンダリングする場所をユーザーが指定する方法と、ユーザー操作に対してコンポーネントを関連付ける方法は、[ホスティング モデル](hosting-models.md)に固有となります。</span><span class="sxs-lookup"><span data-stu-id="8da08-135">How the user specifies where components should render and how the components are then wired up for user interactions is [hosting model](hosting-models.md) specific.</span></span>

<span data-ttu-id="8da08-136">Blazor [コンポーネント](components.md)は、再利用可能な UI を表す .NET クラスです。</span><span class="sxs-lookup"><span data-stu-id="8da08-136">Blazor [components](components.md) are .NET classes that represent a reusable piece of UI.</span></span> <span data-ttu-id="8da08-137">各コンポーネントは、自身の状態を保持し、自身のレンダリング ロジックを指定します。これには、他のコンポーネントのレンダリングを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8da08-137">Each component maintains its own state and specifies its own rendering logic, which can include rendering other components.</span></span> <span data-ttu-id="8da08-138">コンポーネントは、コンポーネントの状態を更新するために、特定のユーザー操作のイベント ハンドラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="8da08-138">Components specify event handlers for specific user interactions to update the component's state.</span></span>

<span data-ttu-id="8da08-139">コンポーネントでイベントが処理された後、Blazor によってコンポーネントがレンダリングされ、レンダリングされた出力の変更内容が追跡されます。</span><span class="sxs-lookup"><span data-stu-id="8da08-139">After a component handles an event, Blazor renders the component and keeps track of what changed in the rendered output.</span></span> <span data-ttu-id="8da08-140">コンポーネントは、ドキュメント オブジェクト モデル (DOM) に直接はレンダリングされません。</span><span class="sxs-lookup"><span data-stu-id="8da08-140">Components don't render directly to the Document Object Model (DOM).</span></span> <span data-ttu-id="8da08-141">代わりに、Blazor で変更を追跡できるように、`RenderTree` と呼ばれる DOM のメモリ内表現にレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="8da08-141">They instead render to an in-memory representation of the DOM called a `RenderTree` so that Blazor can track the changes.</span></span> <span data-ttu-id="8da08-142">Blazor では、新しくレンダリングされた出力を前の出力と比較して UI の相違を計算してから、それを DOM に効率よく適用します。</span><span class="sxs-lookup"><span data-stu-id="8da08-142">Blazor compares the newly rendered output with the previous output to calculate a UI diff that it then applies efficiently to the DOM.</span></span>

![Blazor DOM の相互作用](./media/architecture-comparison/blazor-dom-interaction.png)

<span data-ttu-id="8da08-144">また、コンポーネントでは、その状態が通常の UI イベントの外部で変更された場合に、レンダリングが必要であることを手動で示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="8da08-144">Components can also manually indicate that they should be rendered if their state changes outside of a normal UI event.</span></span> <span data-ttu-id="8da08-145">Blazor では、`SynchronizationContext` を使用して、1 つの論理スレッドを強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="8da08-145">Blazor uses a `SynchronizationContext` to enforce a single logical thread of execution.</span></span> <span data-ttu-id="8da08-146">コンポーネントの ライフサイクル メソッドと Blazor によって発生するイベント コールバックは、この `SynchronizationContext` で実行されます。</span><span class="sxs-lookup"><span data-stu-id="8da08-146">A component's lifecycle methods and any event callbacks that are raised by Blazor are executed on this `SynchronizationContext`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8da08-147">[前へ](introduction.md)
>[次へ](hosting-models.md)</span><span class="sxs-lookup"><span data-stu-id="8da08-147">[Previous](introduction.md)
[Next](hosting-models.md)</span></span>
