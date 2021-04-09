---
title: '破壊的変更: Blazor: WebEventDescriptor.EventArgsType プロパティが置き換えられました'
description: WebEventDescriptor.EventArgsType プロパティが EventName プロパティに置き換えられた ASP.NET Core 6.0 の破壊的変更について説明します。
ms.author: scaddie
ms.date: 02/24/2021
no-loc:
- Blazor
ms.openlocfilehash: c9e866813707114f912ffe83309b0f95c2c9a0f2
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497009"
---
# <a name="blazor-no-loc-textwebeventdescriptoreventargstype-property-replaced"></a><span data-ttu-id="34829-103">Blazor: :::no-loc text="WebEventDescriptor.EventArgsType"::: プロパティが置き換えられました</span><span class="sxs-lookup"><span data-stu-id="34829-103">Blazor: :::no-loc text="WebEventDescriptor.EventArgsType"::: property replaced</span></span>

<span data-ttu-id="34829-104"><xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor> クラスは、JavaScript から .NET にイベントをやり取りするための Blazor の内部プロトコルの一部です。</span><span class="sxs-lookup"><span data-stu-id="34829-104">The <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor> class is part of Blazor's internal protocol for communicating events from JavaScript into .NET.</span></span> <span data-ttu-id="34829-105">通常、このクラスは、アプリ コードではなく、プラットフォームの作成者によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="34829-105">This class isn't typically used by app code, but rather by platform authors.</span></span>

<span data-ttu-id="34829-106">ASP.NET Core 6.0 以降、`WebEventDescriptor` の <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> プロパティは新しい `EventName` プロパティに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="34829-106">Starting in ASP.NET Core 6.0, the <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> property on `WebEventDescriptor` is being replaced by a new `EventName` property.</span></span> <span data-ttu-id="34829-107">この変更は低レベルのプラットフォーム実装の詳細であるため、アプリ コードに影響する可能性はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="34829-107">This change is unlikely to affect any app code, as it's a low-level platform implementation detail.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="34829-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="34829-108">Version introduced</span></span>

<span data-ttu-id="34829-109">6.0</span><span class="sxs-lookup"><span data-stu-id="34829-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="34829-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="34829-110">Old behavior</span></span>

<span data-ttu-id="34829-111">ASP.NET Core 5.0 以前の場合、プロパティ `EventArgsType` には、DOM イベントの種類のグループに対して非標準の Blazor 固有のカテゴリ名を記述します。</span><span class="sxs-lookup"><span data-stu-id="34829-111">In ASP.NET Core 5.0 and earlier, the property `EventArgsType` describes a nonstandard, Blazor-specific category name for groups of DOM event types.</span></span> <span data-ttu-id="34829-112">たとえば、`click` と `mousedown` のイベントはいずれも `mouse` の `EventArgsType` 値 にマップされていました。</span><span class="sxs-lookup"><span data-stu-id="34829-112">For example, the `click` and `mousedown` events were both mapped to an `EventArgsType` value of `mouse`.</span></span> <span data-ttu-id="34829-113">同様に、`cut`、`copy`、および `paste` のイベントは、`clipboard` の `EventArgsType` 値にマップされます。</span><span class="sxs-lookup"><span data-stu-id="34829-113">Similarly, `cut`, `copy`, and `paste` events are mapped to an `EventArgsType` value of `clipboard`.</span></span> <span data-ttu-id="34829-114">これらのカテゴリ名は、受信イベントの引数データを逆シリアル化する際に使用される .NET 型を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="34829-114">These category names are used to determine the .NET type to use for deserializing the incoming event arguments data.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="34829-115">新しい動作</span><span class="sxs-lookup"><span data-stu-id="34829-115">New behavior</span></span>

<span data-ttu-id="34829-116">ASP.NET Core 6.0 以降、新しいプロパティ `EventName` には元のイベントの名前のみを指定します。</span><span class="sxs-lookup"><span data-stu-id="34829-116">Starting in ASP.NET Core 6.0, the new property `EventName` only specifies the original event's name.</span></span> <span data-ttu-id="34829-117">たとえば、`click`、`mousedown`、`cut`、`copy`、`paste` などです。</span><span class="sxs-lookup"><span data-stu-id="34829-117">For example, `click`, `mousedown`, `cut`, `copy`, or `paste`.</span></span> <span data-ttu-id="34829-118">Blazor 固有のカテゴリ名を指定する必要はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="34829-118">There's no longer a need to supply a Blazor-specific category name.</span></span> <span data-ttu-id="34829-119">そのため、以前のプロパティ `EventArgsType` は削除されました。</span><span class="sxs-lookup"><span data-stu-id="34829-119">For that reason, the old property `EventArgsType` is removed.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="34829-120">変更理由</span><span class="sxs-lookup"><span data-stu-id="34829-120">Reason for change</span></span>

<span data-ttu-id="34829-121">プル要求 [dotnet/aspnetcore#29993](https://github.com/dotnet/aspnetcore/pull/29993) で、カスタムのイベント引数クラスのサポートが導入されました。</span><span class="sxs-lookup"><span data-stu-id="34829-121">In pull request [dotnet/aspnetcore#29993](https://github.com/dotnet/aspnetcore/pull/29993), support for custom event arguments classes was introduced.</span></span> <span data-ttu-id="34829-122">このサポートの一部として、フレームワークは、事前に定義されたカテゴリのセットに適合するすべてのイベントに依存しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="34829-122">As part of this support, the framework no longer relies on all events fitting into a predefined set of categories.</span></span> <span data-ttu-id="34829-123">フレームワークに必要な情報は元のイベント名のみになりました。</span><span class="sxs-lookup"><span data-stu-id="34829-123">The framework now only needs to know the original event name.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="34829-124">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="34829-124">Recommended action</span></span>

<span data-ttu-id="34829-125">アプリ コードは影響を受けないため、変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="34829-125">App code should be unaffected and doesn't need to change.</span></span>

<span data-ttu-id="34829-126">カスタムの Blazor レンダリング プラットフォームを構築する場合は、必要に応じてイベントを `Renderer` にディスパッチするためのメカニズムを更新します。</span><span class="sxs-lookup"><span data-stu-id="34829-126">If building a custom Blazor rendering platform, you may need to update the mechanism for dispatching events into the `Renderer`.</span></span> <span data-ttu-id="34829-127">イベント カテゴリに関するハードコーディングされたルールを、元の生のイベント名を指定する場合よりも簡単なロジックに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="34829-127">Replace any hardcoded rules about event categories with simpler logic that supplies the original, raw event name.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="34829-128">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="34829-128">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`P:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType`

-->
