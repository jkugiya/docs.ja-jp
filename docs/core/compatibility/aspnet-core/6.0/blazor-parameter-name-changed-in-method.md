---
title: '破壊的変更: Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Blazor :RequestImageFileAsync メソッドで変更されたパラメーター名'
no-loc:
- Blazor
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 06fe2b0cff17630e09da3f80c506684f1b26e9d4
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292276"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a><span data-ttu-id="c3a83-103">Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名</span><span class="sxs-lookup"><span data-stu-id="c3a83-103">Blazor: Parameter name changed in RequestImageFileAsync method</span></span>

<span data-ttu-id="c3a83-104">`RequestImageFileAsync` メソッドの `maxWith` パラメーターの名前が `maxWith` から `maxWidth` に変更されました。</span><span class="sxs-lookup"><span data-stu-id="c3a83-104">The `RequestImageFileAsync` method's `maxWith` parameter was renamed from `maxWith` to `maxWidth`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c3a83-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="c3a83-105">Version introduced</span></span>

<span data-ttu-id="c3a83-106">ASP.NET Core 6.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="c3a83-106">ASP.NET Core 6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c3a83-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="c3a83-107">Old behavior</span></span>

<span data-ttu-id="c3a83-108">パラメーター名のスペルは `maxWith` です。</span><span class="sxs-lookup"><span data-stu-id="c3a83-108">The parameter name is spelled `maxWith`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="c3a83-109">新しい動作</span><span class="sxs-lookup"><span data-stu-id="c3a83-109">New behavior</span></span>

<span data-ttu-id="c3a83-110">パラメーター名のスペルは `maxWidth` です。</span><span class="sxs-lookup"><span data-stu-id="c3a83-110">The parameter name is spelled `maxWidth`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c3a83-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="c3a83-111">Reason for change</span></span>

<span data-ttu-id="c3a83-112">元のパラメーター名はタイプミスでした。</span><span class="sxs-lookup"><span data-stu-id="c3a83-112">The original parameter name was a typographical error.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c3a83-113">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="c3a83-113">Recommended action</span></span>

<span data-ttu-id="c3a83-114">`RequestImageFile` API で名前付きパラメーターを使用している場合は、`maxWith` パラメーター名を `maxWidth` に更新してください。</span><span class="sxs-lookup"><span data-stu-id="c3a83-114">If you're using named parameters in the `RequestImageFile` API, update the `maxWith` parameter name to `maxWidth`.</span></span> <span data-ttu-id="c3a83-115">それ以外の場合、変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c3a83-115">Otherwise, no change is necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c3a83-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="c3a83-116">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
