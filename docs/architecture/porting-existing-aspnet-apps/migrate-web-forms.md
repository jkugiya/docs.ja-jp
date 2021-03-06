---
title: ASP.NET Web Forms アプリを移行するための戦略
description: チームは ASP.NET Web フォームアプリを .NET Core に移行するためにどのような戦略を使用できますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0b37a37f047de50c347313be14a2228838da6995
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401282"
---
# <a name="strategies-for-migrating-aspnet-web-forms-apps"></a><span data-ttu-id="56517-103">ASP.NET Web Forms アプリを移行するための戦略</span><span class="sxs-lookup"><span data-stu-id="56517-103">Strategies for migrating ASP.NET Web Forms apps</span></span>

<span data-ttu-id="56517-104">この書籍では、大規模な ASP.NET MVC と Web API アプリを .NET Core に移行するためのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="56517-104">This book offers guidance for migrating large ASP.NET MVC and Web API apps to .NET Core.</span></span> <span data-ttu-id="56517-105">これらの ASP.NET アプリには、対処する必要がある Web フォーム (*.aspx*) ページも含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="56517-105">Some of these ASP.NET apps may also include Web Forms (*.aspx*) pages that must be addressed.</span></span> <span data-ttu-id="56517-106">ASP.NET Web フォームは .NET Core ではサポートされていません (ASP.NET Web ページ)。</span><span class="sxs-lookup"><span data-stu-id="56517-106">ASP.NET Web Forms isn't supported in .NET Core (nor are ASP.NET Web Pages).</span></span> <span data-ttu-id="56517-107">通常は、ASP.NET Core に移植するときに、これらのページの機能を書き直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="56517-107">Typically, the functionality of these pages must be rewritten when porting to ASP.NET Core.</span></span> <span data-ttu-id="56517-108">ただし、このような移行の前または実行中に適用できるいくつかの戦略によって、必要な全体的な作業量を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="56517-108">There are, however, some strategies you can apply before or during such migration to help reduce the overall effort required.</span></span>

<span data-ttu-id="56517-109">Web フォームは、かなりの時間にわたり引き続きサポートされます。</span><span class="sxs-lookup"><span data-stu-id="56517-109">Web Forms will continue to be supported for quite some time.</span></span> <span data-ttu-id="56517-110">1つのオプションとして、この機能を ASP.NET 4.x アプリで保持することができます。</span><span class="sxs-lookup"><span data-stu-id="56517-110">One option may be to keep this functionality in an ASP.NET 4.x app.</span></span>

## <a name="separate-business-logic-and-other-concerns"></a><span data-ttu-id="56517-111">ビジネスロジックとその他の懸念事項の分離</span><span class="sxs-lookup"><span data-stu-id="56517-111">Separate business logic and other concerns</span></span>

<span data-ttu-id="56517-112">ASP.NET の Web フォームページのコードが少ないほど、改善されます。</span><span class="sxs-lookup"><span data-stu-id="56517-112">The less code in your ASP.NET Web Forms pages, the better.</span></span> <span data-ttu-id="56517-113">可能であれば、ビジネスロジックや、データアクセスなどの他の懸念事項を別のクラスに保持し、理想的には別のクラスライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="56517-113">When possible, keep business logic and other concerns like data access in separate classes, ideally in separate class libraries.</span></span> <span data-ttu-id="56517-114">これらのクラスライブラリは、任意の ASP.NET Core アプリによって .NET Standard および使用されるように移植できます。</span><span class="sxs-lookup"><span data-stu-id="56517-114">These class libraries can be ported to .NET Standard and consumed by any ASP.NET Core app.</span></span>

## <a name="implement-client-behavior-and-web-apis"></a><span data-ttu-id="56517-115">クライアント動作と web Api を実装する</span><span class="sxs-lookup"><span data-stu-id="56517-115">Implement client behavior and web APIs</span></span>

<span data-ttu-id="56517-116">API 呼び出しを使用して、Web フォームまたはブラウザーでロジックを実装するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="56517-116">Consider the choice between implementing logic in Web Forms or in the browser with the help of API calls.</span></span> <span data-ttu-id="56517-117">後者を優先します。</span><span class="sxs-lookup"><span data-stu-id="56517-117">Favor the latter.</span></span> <span data-ttu-id="56517-118">Api の ASP.NET Core への移行はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="56517-118">Migrating APIs to ASP.NET Core is supported.</span></span> <span data-ttu-id="56517-119">クライアント側の動作は、アプリが使用しているサーバー側のスタックから独立している必要があります。</span><span class="sxs-lookup"><span data-stu-id="56517-119">Client-side behavior should be independent of the server-side stack your app is using.</span></span> <span data-ttu-id="56517-120">このアプローチを使用すると、より応答性に優れたユーザーエクスペリエンスを提供するという利点があります。</span><span class="sxs-lookup"><span data-stu-id="56517-120">Using this approach has the added benefit of providing a more responsive user experience.</span></span>

## <a name="consider-blazor"></a><span data-ttu-id="56517-121">Blazor を検討する</span><span class="sxs-lookup"><span data-stu-id="56517-121">Consider Blazor</span></span>

<span data-ttu-id="56517-122">Blazor を使用すると、JavaScript の代わりに、C# で対話型の web Ui を作成できます。</span><span class="sxs-lookup"><span data-stu-id="56517-122">Blazor lets you build interactive web UIs with C# instead of JavaScript.</span></span> <span data-ttu-id="56517-123">サーバーまたはブラウザーで、WebAssembly 使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="56517-123">It can run on the server or in the browser using WebAssembly.</span></span> <span data-ttu-id="56517-124">ASP.NET Web Forms アプリをページごとに Blazor アプリに移植できます。</span><span class="sxs-lookup"><span data-stu-id="56517-124">ASP.NET Web Forms apps may be ported page-by-page to Blazor apps.</span></span> <span data-ttu-id="56517-125">Web フォームアプリを Blazor に移植する方法の詳細については、「 [Blazor for ASP.NET Web Forms デベロッパー](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56517-125">For more information on porting Web Forms apps to Blazor, see [Blazor for ASP.NET Web Forms Developers](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/).</span></span> <span data-ttu-id="56517-126">また、多くの Web フォームコントロールは、オープンソースのコミュニティプロジェクトの一部として Blazor に移植されています。 [Blazor Web フォームコンポーネント](https://fritzandfriends.github.io/BlazorWebFormsComponents/)。</span><span class="sxs-lookup"><span data-stu-id="56517-126">In addition, many Web Forms controls have been ported to Blazor as part of an open-source community project, [Blazor Web Forms Components](https://fritzandfriends.github.io/BlazorWebFormsComponents/).</span></span> <span data-ttu-id="56517-127">これらのコンポーネントを使用すると、組み込みの Web フォームコントロールを使用している場合でも、Web フォームページを Blazor に簡単に移植できます。</span><span class="sxs-lookup"><span data-stu-id="56517-127">With these components, you can more easily port Web Forms pages to Blazor even if they use the built-in Web Forms controls.</span></span>

## <a name="summary"></a><span data-ttu-id="56517-128">まとめ</span><span class="sxs-lookup"><span data-stu-id="56517-128">Summary</span></span>

<span data-ttu-id="56517-129">ASP.NET Web フォームから ASP.NET Core への直接移行はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="56517-129">Migrating directly from ASP.NET Web Forms to ASP.NET Core isn't supported.</span></span> <span data-ttu-id="56517-130">ただし、ASP.NET Core を簡単に移行できるようにするための戦略があります。</span><span class="sxs-lookup"><span data-stu-id="56517-130">However, there are strategies to make moving to ASP.NET Core easier.</span></span> <span data-ttu-id="56517-131">次の方法で、Web フォーム機能を ASP.NET Core に正常に移行できます。</span><span class="sxs-lookup"><span data-stu-id="56517-131">You can migrate your Web Forms functionality to ASP.NET Core successfully by:</span></span>

* <span data-ttu-id="56517-132">プロジェクトから非 web 機能を維持します。</span><span class="sxs-lookup"><span data-stu-id="56517-132">Keeping non-web functionality out of your projects.</span></span>
* <span data-ttu-id="56517-133">可能な限り、web Api を使用します。</span><span class="sxs-lookup"><span data-stu-id="56517-133">Using web APIs wherever possible.</span></span>
* <span data-ttu-id="56517-134">より新しい UI のオプションとして Blazor を検討しています。</span><span class="sxs-lookup"><span data-stu-id="56517-134">Considering Blazor as an option for a more modern UI.</span></span>

## <a name="references"></a><span data-ttu-id="56517-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="56517-135">References</span></span>

- [<span data-ttu-id="56517-136">無料の電子書籍: ASP.NET Web Forms 開発者向けの Blazor</span><span class="sxs-lookup"><span data-stu-id="56517-136">Free e-book: Blazor for ASP.NET Web Forms Developers</span></span>](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)
- [<span data-ttu-id="56517-137">Blazor Web フォームコンポーネント (コミュニティプロジェクト)</span><span class="sxs-lookup"><span data-stu-id="56517-137">Blazor Web Forms Components (Community Project)</span></span>](https://fritzandfriends.github.io/BlazorWebFormsComponents/)

>[!div class="step-by-step"]
><span data-ttu-id="56517-138">[前へ](incremental-migration-strategies.md)
>[次へ](deployment-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="56517-138">[Previous](incremental-migration-strategies.md)
[Next](deployment-strategies.md)</span></span>
