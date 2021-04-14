---
title: '破壊的変更:Kestrel: 変更されたログ メッセージ属性'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Kestrel: 変更されたログ メッセージ属性'
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: daeb9ae418f343a00e9563ef3e2b5090a7f016a9
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255169"
---
# <a name="kestrel-log-message-attributes-changed"></a><span data-ttu-id="bee21-103">Kestrel: 変更されたログ メッセージ属性</span><span class="sxs-lookup"><span data-stu-id="bee21-103">Kestrel: Log message attributes changed</span></span>

<span data-ttu-id="bee21-104">Kestrel ログ メッセージには ID と名前が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="bee21-104">Kestrel log messages have associated IDs and names.</span></span> <span data-ttu-id="bee21-105">これらの属性により、さまざまな種類のログ メッセージが一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="bee21-105">These attributes uniquely identify different kinds of log messages.</span></span> <span data-ttu-id="bee21-106">それらの ID と名前の一部が誤って重複していました。</span><span class="sxs-lookup"><span data-stu-id="bee21-106">Some of those IDs and names were incorrectly duplicated.</span></span> <span data-ttu-id="bee21-107">この重複の問題は、ASP.NET Core 6.0 で修正されています。</span><span class="sxs-lookup"><span data-stu-id="bee21-107">This duplication problem is fixed in ASP.NET Core 6.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bee21-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="bee21-108">Version introduced</span></span>

<span data-ttu-id="bee21-109">ASP.NET Core 6.0</span><span class="sxs-lookup"><span data-stu-id="bee21-109">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="bee21-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="bee21-110">Old behavior</span></span>

<span data-ttu-id="bee21-111">ASP.NET Core 6.0 より前の、影響を受けたログ メッセージの状態を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bee21-111">The following table shows the state of the affected log messages before ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="bee21-112">メッセージの説明</span><span class="sxs-lookup"><span data-stu-id="bee21-112">Message description</span></span>                   | <span data-ttu-id="bee21-113">名前</span><span class="sxs-lookup"><span data-stu-id="bee21-113">Name</span></span>                    | <span data-ttu-id="bee21-114">id</span><span class="sxs-lookup"><span data-stu-id="bee21-114">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="bee21-115">閉じられた HTTP/2 接続に関するログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="bee21-115">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="bee21-116">36</span><span class="sxs-lookup"><span data-stu-id="bee21-116">36</span></span> |
| <span data-ttu-id="bee21-117">HTTP/2 フレームの送信に関するログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="bee21-117">HTTP/2 frame sending log messages</span></span>     | `Http2FrameReceived`    | <span data-ttu-id="bee21-118">37</span><span class="sxs-lookup"><span data-stu-id="bee21-118">37</span></span> |

## <a name="new-behavior"></a><span data-ttu-id="bee21-119">新しい動作</span><span class="sxs-lookup"><span data-stu-id="bee21-119">New behavior</span></span>

<span data-ttu-id="bee21-120">ASP.NET Core 6.0 の、影響を受けたログ メッセージの状態を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bee21-120">The following table shows the state of the affected log messages in ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="bee21-121">メッセージの説明</span><span class="sxs-lookup"><span data-stu-id="bee21-121">Message description</span></span>                   | <span data-ttu-id="bee21-122">名前</span><span class="sxs-lookup"><span data-stu-id="bee21-122">Name</span></span>                    | <span data-ttu-id="bee21-123">id</span><span class="sxs-lookup"><span data-stu-id="bee21-123">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="bee21-124">閉じられた HTTP/2 接続に関するログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="bee21-124">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="bee21-125">48</span><span class="sxs-lookup"><span data-stu-id="bee21-125">48</span></span> |
| <span data-ttu-id="bee21-126">HTTP/2 フレームの送信に関するログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="bee21-126">HTTP/2 frame sending log messages</span></span>     | `Http2FrameSending`     | <span data-ttu-id="bee21-127">49</span><span class="sxs-lookup"><span data-stu-id="bee21-127">49</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="bee21-128">変更理由</span><span class="sxs-lookup"><span data-stu-id="bee21-128">Reason for change</span></span>

<span data-ttu-id="bee21-129">さまざまなメッセージの種類を識別できるように、ログの ID と名前は一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bee21-129">Log IDs and names should be unique so different message types can be identified.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bee21-130">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="bee21-130">Recommended action</span></span>

<span data-ttu-id="bee21-131">古い ID と名前を参照するコードまたは構成がある場合は、新しい ID と名前を使用するようにそれらの参照を更新してください。</span><span class="sxs-lookup"><span data-stu-id="bee21-131">If you have code or configuration that references the old IDs and names, update those references to use the new IDs and names.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
