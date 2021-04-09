---
title: '破壊的変更:Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Blazor:RequestImageFileAsync メソッドで変更されたパラメーター名'
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 61518ba246c1d390861261ecb5a9f18a5695c1fd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496983"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a><span data-ttu-id="8e207-103">Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名</span><span class="sxs-lookup"><span data-stu-id="8e207-103">Blazor: Parameter name changed in RequestImageFileAsync method</span></span>

<span data-ttu-id="8e207-104">`RequestImageFileAsync` メソッドの `maxWith` パラメーターの名前が `maxWith` から `maxWidth` に変更されました。</span><span class="sxs-lookup"><span data-stu-id="8e207-104">The `RequestImageFileAsync` method's `maxWith` parameter was renamed from `maxWith` to `maxWidth`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8e207-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8e207-105">Version introduced</span></span>

<span data-ttu-id="8e207-106">6.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e207-106">6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="8e207-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="8e207-107">Old behavior</span></span>

<span data-ttu-id="8e207-108">パラメーター名のスペルは `maxWith` です。</span><span class="sxs-lookup"><span data-stu-id="8e207-108">The parameter name is spelled `maxWith`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="8e207-109">新しい動作</span><span class="sxs-lookup"><span data-stu-id="8e207-109">New behavior</span></span>

<span data-ttu-id="8e207-110">パラメーター名のスペルは `maxWidth` です。</span><span class="sxs-lookup"><span data-stu-id="8e207-110">The parameter name is spelled `maxWidth`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8e207-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="8e207-111">Reason for change</span></span>

<span data-ttu-id="8e207-112">元のパラメーター名はタイプミスでした。</span><span class="sxs-lookup"><span data-stu-id="8e207-112">The original parameter name was a typographical error.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8e207-113">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="8e207-113">Recommended action</span></span>

<span data-ttu-id="8e207-114">`RequestImageFile` API で名前付きパラメーターを使用している場合は、`maxWith` パラメーター名を `maxWidth` に更新してください。</span><span class="sxs-lookup"><span data-stu-id="8e207-114">If you're using named parameters in the `RequestImageFile` API, update the `maxWith` parameter name to `maxWidth`.</span></span> <span data-ttu-id="8e207-115">それ以外の場合、変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8e207-115">Otherwise, no change is necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8e207-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8e207-116">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
