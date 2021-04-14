---
title: ASP.NET MVC と ASP.NET Core での Razor の使用の比較
description: ASP.NET MVC と ASP.NET Core で、Razor は どのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a9f7fa2e6b8c0c6bf61c743cf8c956b1ad09713c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401356"
---
# <a name="compare-razor-usage-in-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="d8f81-103">ASP.NET MVC と ASP.NET Core での Razor の使用の比較</span><span class="sxs-lookup"><span data-stu-id="d8f81-103">Compare Razor usage in ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="d8f81-104">Razor の基本構文は、ASP.NET MVC と ASP.NET Core で大きな変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="d8f81-104">The basic syntax of Razor hasn't changed substantially between ASP.NET MVC and ASP.NET Core.</span></span> <span data-ttu-id="d8f81-105">ただし、[タグ ヘルパー](/aspnet/core/mvc/views/tag-helpers/intro)と Razor Pages の導入など、移行時に考慮する必要があるいくつかの相違点があります。</span><span class="sxs-lookup"><span data-stu-id="d8f81-105">However, there are certain differences, such as the introduction of [Tag Helpers](/aspnet/core/mvc/views/tag-helpers/intro) and Razor Pages, that should be considered when migrating.</span></span> <span data-ttu-id="d8f81-106">アプリでカスタム Razor 機能を多用している場合は、「[ASP.NET Core の Razor 構文リファレンス](/aspnet/core/razor-pages)」を参照して、ASP.NET Core への移行時にどのような変更が必要になるかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d8f81-106">If your app makes heavy use of custom Razor functionality, refer to the [Razor syntax reference for ASP.NET Core](/aspnet/core/razor-pages) to see what changes may be required when you migrate to ASP.NET Core.</span></span>

## <a name="tag-helpers"></a><span data-ttu-id="d8f81-107">タグ ヘルパー</span><span class="sxs-lookup"><span data-stu-id="d8f81-107">Tag Helpers</span></span>

<span data-ttu-id="d8f81-108">タグ ヘルパーを使用することで、Razor ファイルでの HTML 要素の作成とレンダリングに、サーバー側コードを組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d8f81-108">Tag Helpers enable server-side code to participate in creating and rendering HTML elements in Razor files.</span></span> <span data-ttu-id="d8f81-109">これは HTML ヘルパーよりも多くの利点があるので、可能な限り HTML ヘルパーの代わりに使用してください。</span><span class="sxs-lookup"><span data-stu-id="d8f81-109">They offer many advantages over HTML Helpers and should be used in place of HTML Helpers wherever possible.</span></span> <span data-ttu-id="d8f81-110">これは標準の HTML のように見え、HTML を編集するように設計されたほとんどのツールによって無視されるので、HTML に最適な開発エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d8f81-110">They provide an HTML-friendly development experience, since they look like standard HTML and are ignored by most tooling designed to edit HTML.</span></span> <span data-ttu-id="d8f81-111">_Visual Studio_ 内では、タグ ヘルパーを使用して HTML および Razor のマークアップを作成するための機能豊富な IntelliSense がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d8f81-111">Within _Visual Studio_, there's rich IntelliSense support for creating HTML and Razor markup with Tag Helpers.</span></span> <span data-ttu-id="d8f81-112">タグ ヘルパーは、Razor ファイル内の宣言型マークアップから、単純または複雑な動作を提供できます。</span><span class="sxs-lookup"><span data-stu-id="d8f81-112">Tag Helpers can provide simple or complex behavior from declarative markup in Razor files.</span></span>

## <a name="razor-pages"></a><span data-ttu-id="d8f81-113">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="d8f81-113">Razor Pages</span></span>

<span data-ttu-id="d8f81-114">Razor Pages は、ページベース アプリとフォームベース アプリでコントローラー、アクション、ビューの代わりとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8f81-114">Razor Pages offer an alternative to controllers, actions, and views for page- and form-based apps.</span></span> <span data-ttu-id="d8f81-115">[Razor Pages と ASP.NET MVC の比較については、この章の前のほうで説明しています](./comparing-razor-pages-aspnet-mvc.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f81-115">[Razor Pages were compared to ASP.NET MVC earlier in this chapter](./comparing-razor-pages-aspnet-mvc.md).</span></span>

## <a name="references"></a><span data-ttu-id="d8f81-116">リファレンス</span><span class="sxs-lookup"><span data-stu-id="d8f81-116">References</span></span>

- [<span data-ttu-id="d8f81-117">ASP.NET MVC から ASP.NET Core MVC への移行: コントローラーとビュー</span><span class="sxs-lookup"><span data-stu-id="d8f81-117">Migrate from ASP.NET MVC to ASP.NET Core MVC: Controllers and Views</span></span>](/aspnet/core/migration/mvc#migrate-controllers-and-views)
- [<span data-ttu-id="d8f81-118">ASP.NET Core のタグ ヘルパー</span><span class="sxs-lookup"><span data-stu-id="d8f81-118">Tag Helpers in ASP.NET Core</span></span>](/aspnet/core/mvc/views/tag-helpers/intro)
- [<span data-ttu-id="d8f81-119">ASP.NET Core での Razor ページの概要</span><span class="sxs-lookup"><span data-stu-id="d8f81-119">Introduction to Razor Pages in ASP.NET Core</span></span>](/aspnet/core/razor-pages)
- [<span data-ttu-id="d8f81-120">ASP.NET Core の Razor 構文リファレンス</span><span class="sxs-lookup"><span data-stu-id="d8f81-120">Razor syntax reference for ASP.NET Core</span></span>](/aspnet/core/razor-pages)

>[!div class="step-by-step"]
><span data-ttu-id="d8f81-121">[前へ](controller-differences.md)
>[次へ](signalr-differences.md)</span><span class="sxs-lookup"><span data-stu-id="d8f81-121">[Previous](controller-differences.md)
[Next](signalr-differences.md)</span></span>
