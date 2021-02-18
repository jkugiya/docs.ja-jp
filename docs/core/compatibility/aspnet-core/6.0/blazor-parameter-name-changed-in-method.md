---
title: '破壊的変更:Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Blazor:RequestImageFileAsync メソッドで変更されたパラメーター名'
author: scottaddie
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: bfaaa6bfe94c32fbc1a5b5b70db863d105d389b5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488242"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a><span data-ttu-id="d9c01-103">Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名</span><span class="sxs-lookup"><span data-stu-id="d9c01-103">Blazor: Parameter name changed in RequestImageFileAsync method</span></span>

<span data-ttu-id="d9c01-104">`RequestImageFileAsync` メソッドの `maxWith` パラメーターの名前が `maxWith` から `maxWidth` に変更されました。</span><span class="sxs-lookup"><span data-stu-id="d9c01-104">The `RequestImageFileAsync` method's `maxWith` parameter was renamed from `maxWith` to `maxWidth`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d9c01-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="d9c01-105">Version introduced</span></span>

<span data-ttu-id="d9c01-106">6.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="d9c01-106">6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d9c01-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="d9c01-107">Old behavior</span></span>

<span data-ttu-id="d9c01-108">パラメーター名のスペルは `maxWith` です。</span><span class="sxs-lookup"><span data-stu-id="d9c01-108">The parameter name is spelled `maxWith`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="d9c01-109">新しい動作</span><span class="sxs-lookup"><span data-stu-id="d9c01-109">New behavior</span></span>

<span data-ttu-id="d9c01-110">パラメーター名のスペルは `maxWidth` です。</span><span class="sxs-lookup"><span data-stu-id="d9c01-110">The parameter name is spelled `maxWidth`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d9c01-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="d9c01-111">Reason for change</span></span>

<span data-ttu-id="d9c01-112">元のパラメーター名はタイプミスでした。</span><span class="sxs-lookup"><span data-stu-id="d9c01-112">The original parameter name was a typographical error.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d9c01-113">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="d9c01-113">Recommended action</span></span>

<span data-ttu-id="d9c01-114">`RequestImageFile` API で名前付きパラメーターを使用している場合は、`maxWith` パラメーター名を `maxWidth` に更新してください。</span><span class="sxs-lookup"><span data-stu-id="d9c01-114">If you're using named parameters in the `RequestImageFile` API, update the `maxWith` parameter name to `maxWidth`.</span></span> <span data-ttu-id="d9c01-115">それ以外の場合、変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d9c01-115">Otherwise, no change is necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d9c01-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="d9c01-116">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
