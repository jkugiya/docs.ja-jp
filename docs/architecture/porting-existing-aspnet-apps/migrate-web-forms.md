---
title: ASP.NET Web Forms アプリを移行するための戦略
description: チームは、ASP.NET Web Forms アプリを .NET Core に移行するためにどのような戦略を使用できるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0b37a37f047de50c347313be14a2228838da6995
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401282"
---
# <a name="strategies-for-migrating-aspnet-web-forms-apps"></a><span data-ttu-id="21b23-103">ASP.NET Web Forms アプリを移行するための戦略</span><span class="sxs-lookup"><span data-stu-id="21b23-103">Strategies for migrating ASP.NET Web Forms apps</span></span>

<span data-ttu-id="21b23-104">本書では、大規模な ASP.NET MVC アプリおよび Web API アプリを .NET Core に移行するためのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="21b23-104">This book offers guidance for migrating large ASP.NET MVC and Web API apps to .NET Core.</span></span> <span data-ttu-id="21b23-105">これらの ASP.NET アプリの中には、対応が必要な Web Forms ( *.aspx*) ページを含んでいるものがあります。</span><span class="sxs-lookup"><span data-stu-id="21b23-105">Some of these ASP.NET apps may also include Web Forms (*.aspx*) pages that must be addressed.</span></span> <span data-ttu-id="21b23-106">ASP.NET Web Forms は、.NET Core (および ASP.NET Web ページ) でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="21b23-106">ASP.NET Web Forms isn't supported in .NET Core (nor are ASP.NET Web Pages).</span></span> <span data-ttu-id="21b23-107">通常は、ASP.NET Core に移植する際に、これらのページの機能を書き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="21b23-107">Typically, the functionality of these pages must be rewritten when porting to ASP.NET Core.</span></span> <span data-ttu-id="21b23-108">しかし、そのような移行の前または実行中に適用できるいくつかの戦略によって、必要な作業量を少なくすることができます。</span><span class="sxs-lookup"><span data-stu-id="21b23-108">There are, however, some strategies you can apply before or during such migration to help reduce the overall effort required.</span></span>

<span data-ttu-id="21b23-109">Web Forms は、今後もかなりの期間にわたってサポートされる予定です。</span><span class="sxs-lookup"><span data-stu-id="21b23-109">Web Forms will continue to be supported for quite some time.</span></span> <span data-ttu-id="21b23-110">1 つの選択肢は、この機能を ASP.NET 4.x アプリ内で保持することです。</span><span class="sxs-lookup"><span data-stu-id="21b23-110">One option may be to keep this functionality in an ASP.NET 4.x app.</span></span>

## <a name="separate-business-logic-and-other-concerns"></a><span data-ttu-id="21b23-111">ビジネス ロジックとその他の懸念事項を分離する</span><span class="sxs-lookup"><span data-stu-id="21b23-111">Separate business logic and other concerns</span></span>

<span data-ttu-id="21b23-112">ASP.NET Web Forms ページに含めるコードは、なるべく少なくしてください。</span><span class="sxs-lookup"><span data-stu-id="21b23-112">The less code in your ASP.NET Web Forms pages, the better.</span></span> <span data-ttu-id="21b23-113">可能な場合は、ビジネス ロジックとデータ アクセスなどのその他の懸念事項を、別のクラス内 (理想的には別のクラス ライブラリ内) で保持します。</span><span class="sxs-lookup"><span data-stu-id="21b23-113">When possible, keep business logic and other concerns like data access in separate classes, ideally in separate class libraries.</span></span> <span data-ttu-id="21b23-114">これらのクラス ライブラリを .NET Standard に移植して、任意の ASP.NET Core アプリで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="21b23-114">These class libraries can be ported to .NET Standard and consumed by any ASP.NET Core app.</span></span>

## <a name="implement-client-behavior-and-web-apis"></a><span data-ttu-id="21b23-115">クライアントの動作と Web API を実装する</span><span class="sxs-lookup"><span data-stu-id="21b23-115">Implement client behavior and web APIs</span></span>

<span data-ttu-id="21b23-116">ロジックを Web Forms に実装するか、または API 呼び出しを利用してブラウザーに実装するかを検討します。</span><span class="sxs-lookup"><span data-stu-id="21b23-116">Consider the choice between implementing logic in Web Forms or in the browser with the help of API calls.</span></span> <span data-ttu-id="21b23-117">推奨されるのは後者です。</span><span class="sxs-lookup"><span data-stu-id="21b23-117">Favor the latter.</span></span> <span data-ttu-id="21b23-118">API の ASP.NET Core への移行はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="21b23-118">Migrating APIs to ASP.NET Core is supported.</span></span> <span data-ttu-id="21b23-119">クライアント側の動作は、アプリが使用しているサーバー側のスタックから独立している必要があります。</span><span class="sxs-lookup"><span data-stu-id="21b23-119">Client-side behavior should be independent of the server-side stack your app is using.</span></span> <span data-ttu-id="21b23-120">このアプローチを使用すると、より応答性に優れたユーザー エクスペリエンスを提供できるというベネフィットも得られます。</span><span class="sxs-lookup"><span data-stu-id="21b23-120">Using this approach has the added benefit of providing a more responsive user experience.</span></span>

## <a name="consider-blazor"></a><span data-ttu-id="21b23-121">Blazor を検討する</span><span class="sxs-lookup"><span data-stu-id="21b23-121">Consider Blazor</span></span>

<span data-ttu-id="21b23-122">Blazor を使用すると、JavaScript の代わりに C# を使用して対話型の Web UI をビルドできます。</span><span class="sxs-lookup"><span data-stu-id="21b23-122">Blazor lets you build interactive web UIs with C# instead of JavaScript.</span></span> <span data-ttu-id="21b23-123">これは、サーバー上で、または WebAssembly を使用してブラウザー内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="21b23-123">It can run on the server or in the browser using WebAssembly.</span></span> <span data-ttu-id="21b23-124">ASP.NET Web Forms アプリは、ページ単位で Blazor アプリに移植できます。</span><span class="sxs-lookup"><span data-stu-id="21b23-124">ASP.NET Web Forms apps may be ported page-by-page to Blazor apps.</span></span> <span data-ttu-id="21b23-125">Web Forms アプリを Blazor に移植する方法の詳細については、「[ASP.NET Web Forms 開発者向け Blazor](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21b23-125">For more information on porting Web Forms apps to Blazor, see [Blazor for ASP.NET Web Forms Developers](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/).</span></span> <span data-ttu-id="21b23-126">また、多数の Web Forms コントロールが、オープンソース コミュニティ プロジェクト「[Blazor Web Forms コンポーネント](https://fritzandfriends.github.io/BlazorWebFormsComponents/)」の一環として Blazor に移植されています。</span><span class="sxs-lookup"><span data-stu-id="21b23-126">In addition, many Web Forms controls have been ported to Blazor as part of an open-source community project, [Blazor Web Forms Components](https://fritzandfriends.github.io/BlazorWebFormsComponents/).</span></span> <span data-ttu-id="21b23-127">これらのコンポーネントを使用すると、Web Forms ページで組み込みの Web Forms コントロールが使用されている場合でも、より簡単にページを Blazor に移植できます。</span><span class="sxs-lookup"><span data-stu-id="21b23-127">With these components, you can more easily port Web Forms pages to Blazor even if they use the built-in Web Forms controls.</span></span>

## <a name="summary"></a><span data-ttu-id="21b23-128">まとめ</span><span class="sxs-lookup"><span data-stu-id="21b23-128">Summary</span></span>

<span data-ttu-id="21b23-129">ASP.NET Web Forms から ASP.NET Core への直接の移行はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="21b23-129">Migrating directly from ASP.NET Web Forms to ASP.NET Core isn't supported.</span></span> <span data-ttu-id="21b23-130">しかし、ASP.NET Core への移行を容易にするための戦略がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="21b23-130">However, there are strategies to make moving to ASP.NET Core easier.</span></span> <span data-ttu-id="21b23-131">以下を行うことにより、Web Forms の機能を ASP.NET Core に正しく移行できます。</span><span class="sxs-lookup"><span data-stu-id="21b23-131">You can migrate your Web Forms functionality to ASP.NET Core successfully by:</span></span>

* <span data-ttu-id="21b23-132">Web 以外の機能はプロジェクトの外部で保持します。</span><span class="sxs-lookup"><span data-stu-id="21b23-132">Keeping non-web functionality out of your projects.</span></span>
* <span data-ttu-id="21b23-133">できる限り Web API を使用します。</span><span class="sxs-lookup"><span data-stu-id="21b23-133">Using web APIs wherever possible.</span></span>
* <span data-ttu-id="21b23-134">より新しい UI のためのオプションとして Blazor を検討します。</span><span class="sxs-lookup"><span data-stu-id="21b23-134">Considering Blazor as an option for a more modern UI.</span></span>

## <a name="references"></a><span data-ttu-id="21b23-135">リファレンス</span><span class="sxs-lookup"><span data-stu-id="21b23-135">References</span></span>

- [<span data-ttu-id="21b23-136">無料の電子書籍: ASP.NET Web Forms 開発者向け Blazor</span><span class="sxs-lookup"><span data-stu-id="21b23-136">Free e-book: Blazor for ASP.NET Web Forms Developers</span></span>](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)
- [<span data-ttu-id="21b23-137">Blazor Web Forms コンポーネント (コミュニティ プロジェクト)</span><span class="sxs-lookup"><span data-stu-id="21b23-137">Blazor Web Forms Components (Community Project)</span></span>](https://fritzandfriends.github.io/BlazorWebFormsComponents/)

>[!div class="step-by-step"]
><span data-ttu-id="21b23-138">[前へ](incremental-migration-strategies.md)
>[次へ](deployment-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="21b23-138">[Previous](incremental-migration-strategies.md)
[Next](deployment-strategies.md)</span></span>
