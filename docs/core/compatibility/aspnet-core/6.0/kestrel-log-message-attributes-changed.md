---
title: '破壊的変更:Kestrel: 変更されたログ メッセージ属性'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Kestrel: 変更されたログ メッセージ属性'
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: 09b0bc71b6c9935b9e7e4170f24869f4d45c97f6
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496879"
---
# <a name="kestrel-log-message-attributes-changed"></a><span data-ttu-id="709df-103">Kestrel: 変更されたログ メッセージ属性</span><span class="sxs-lookup"><span data-stu-id="709df-103">Kestrel: Log message attributes changed</span></span>

<span data-ttu-id="709df-104">Kestrel ログ メッセージには ID と名前が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="709df-104">Kestrel log messages have associated IDs and names.</span></span> <span data-ttu-id="709df-105">これらの属性により、さまざまな種類のログ メッセージが一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="709df-105">These attributes uniquely identify different kinds of log messages.</span></span> <span data-ttu-id="709df-106">それらの ID と名前の一部が誤って重複していました。</span><span class="sxs-lookup"><span data-stu-id="709df-106">Some of those IDs and names were incorrectly duplicated.</span></span> <span data-ttu-id="709df-107">この重複の問題は、ASP.NET Core 6.0 で修正されています。</span><span class="sxs-lookup"><span data-stu-id="709df-107">This duplication problem is fixed in ASP.NET Core 6.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="709df-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="709df-108">Version introduced</span></span>

<span data-ttu-id="709df-109">6.0</span><span class="sxs-lookup"><span data-stu-id="709df-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="709df-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="709df-110">Old behavior</span></span>

<span data-ttu-id="709df-111">ASP.NET Core 6.0 より前の、影響を受けたログ メッセージの状態を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="709df-111">The following table shows the state of the affected log messages before ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="709df-112">メッセージの説明</span><span class="sxs-lookup"><span data-stu-id="709df-112">Message description</span></span>                   | <span data-ttu-id="709df-113">名前</span><span class="sxs-lookup"><span data-stu-id="709df-113">Name</span></span>                    | <span data-ttu-id="709df-114">id</span><span class="sxs-lookup"><span data-stu-id="709df-114">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="709df-115">閉じられた HTTP/2 接続に関するログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="709df-115">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="709df-116">36</span><span class="sxs-lookup"><span data-stu-id="709df-116">36</span></span> |
| <span data-ttu-id="709df-117">HTTP/2 フレームの送信に関するログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="709df-117">HTTP/2 frame sending log messages</span></span>     | `Http2FrameReceived`    | <span data-ttu-id="709df-118">37</span><span class="sxs-lookup"><span data-stu-id="709df-118">37</span></span> |

## <a name="new-behavior"></a><span data-ttu-id="709df-119">新しい動作</span><span class="sxs-lookup"><span data-stu-id="709df-119">New behavior</span></span>

<span data-ttu-id="709df-120">ASP.NET Core 6.0 の、影響を受けたログ メッセージの状態を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="709df-120">The following table shows the state of the affected log messages in ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="709df-121">メッセージの説明</span><span class="sxs-lookup"><span data-stu-id="709df-121">Message description</span></span>                   | <span data-ttu-id="709df-122">名前</span><span class="sxs-lookup"><span data-stu-id="709df-122">Name</span></span>                    | <span data-ttu-id="709df-123">id</span><span class="sxs-lookup"><span data-stu-id="709df-123">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="709df-124">閉じられた HTTP/2 接続に関するログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="709df-124">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="709df-125">48</span><span class="sxs-lookup"><span data-stu-id="709df-125">48</span></span> |
| <span data-ttu-id="709df-126">HTTP/2 フレームの送信に関するログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="709df-126">HTTP/2 frame sending log messages</span></span>     | `Http2FrameSending`     | <span data-ttu-id="709df-127">49</span><span class="sxs-lookup"><span data-stu-id="709df-127">49</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="709df-128">変更理由</span><span class="sxs-lookup"><span data-stu-id="709df-128">Reason for change</span></span>

<span data-ttu-id="709df-129">さまざまなメッセージの種類を識別できるように、ログの ID と名前は一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="709df-129">Log IDs and names should be unique so different message types can be identified.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="709df-130">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="709df-130">Recommended action</span></span>

<span data-ttu-id="709df-131">古い ID と名前を参照するコードまたは構成がある場合は、新しい ID と名前を使用するようにそれらの参照を更新してください。</span><span class="sxs-lookup"><span data-stu-id="709df-131">If you have code or configuration that references the old IDs and names, update those references to use the new IDs and names.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
