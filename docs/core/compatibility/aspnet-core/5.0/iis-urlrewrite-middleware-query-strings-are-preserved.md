---
title: 破壊的変更:IIS:UrlRewrite ミドルウェア クエリ文字列は保持されます
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: IIS:UrlRewrite ミドルウェア クエリ文字列は保持されます'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: e4d1ecba62f9e43e7377aba1138968f15f8895d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759330"
---
# <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="76425-103">IIS:UrlRewrite ミドルウェア クエリ文字列は保持されます</span><span class="sxs-lookup"><span data-stu-id="76425-103">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="76425-104">IIS UrlRewrite ミドルウェアの不具合により、クエリ文字列は書き換えルールに保持されませんでした。</span><span class="sxs-lookup"><span data-stu-id="76425-104">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="76425-105">IIS UrlRewrite モジュールの動作との一貫性を維持するため、この不具合が修正されました。</span><span class="sxs-lookup"><span data-stu-id="76425-105">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="76425-106">ディスカッションについては、イシュー [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76425-106">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="76425-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="76425-107">Version introduced</span></span>

<span data-ttu-id="76425-108">ASP.NET Core 5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="76425-108">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="76425-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="76425-109">Old behavior</span></span>

<span data-ttu-id="76425-110">次の書き換えルールについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="76425-110">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="76425-111">上記のルールでは、クエリ文字列は追加されません。</span><span class="sxs-lookup"><span data-stu-id="76425-111">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="76425-112">`/about?id=1` のような URI は、`/contact?id=1` ではなく、`/contact` にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="76425-112">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="76425-113">`appendQueryString` 属性は既定で `true` にもなります。</span><span class="sxs-lookup"><span data-stu-id="76425-113">The `appendQueryString` attribute defaults to `true` as well.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="76425-114">新しい動作</span><span class="sxs-lookup"><span data-stu-id="76425-114">New behavior</span></span>

<span data-ttu-id="76425-115">クエリ文字列は保持されます。</span><span class="sxs-lookup"><span data-stu-id="76425-115">The query string is preserved.</span></span> <span data-ttu-id="76425-116">[以前の動作](#old-behavior)の例からの URI は `/contact?id=1` になります。</span><span class="sxs-lookup"><span data-stu-id="76425-116">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="76425-117">変更理由</span><span class="sxs-lookup"><span data-stu-id="76425-117">Reason for change</span></span>

<span data-ttu-id="76425-118">以前の動作は、IIS UrlRewrite モジュールの動作と一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="76425-118">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="76425-119">ミドルウェアとモジュールの間で移植をサポートするため、目標は一貫性のある動作を維持することになります。</span><span class="sxs-lookup"><span data-stu-id="76425-119">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="76425-120">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="76425-120">Recommended action</span></span>

<span data-ttu-id="76425-121">クエリ文字列を削除する動作を優先する場合、`action` 要素を `appendQueryString="false"` に設定します。</span><span class="sxs-lookup"><span data-stu-id="76425-121">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="76425-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="76425-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->