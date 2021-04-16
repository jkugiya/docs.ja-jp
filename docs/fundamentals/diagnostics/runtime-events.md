---
title: ランタイム イベント
description: ETW、LTTng、または EventPipe で使用できる .NET ランタイム (CoreCLR) によって生成される診断イベントを確認します。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594049"
---
# <a name="net-runtime-events"></a><span data-ttu-id="fa5a2-103">.NET ランタイム イベント</span><span class="sxs-lookup"><span data-stu-id="fa5a2-103">.NET runtime events</span></span>

<span data-ttu-id="fa5a2-104">.NET ランタイム (CoreCLR) は、`ETW`、`LTTng`、`EventPipe` などのさまざまなメカニズムで使用できる .NET アプリケーションの問題を診断するために使用できるさまざまなイベントを生成します。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-104">The .NET runtime (CoreCLR) emits various events that can be used to diagnose issues with your .NET application that can be consumed via various mechanisms such as `ETW`, `LTTng`, and `EventPipe`.</span></span>

<span data-ttu-id="fa5a2-105">このドキュメントは、.NET Core ランタイムで発生するイベントの参考ガイドです。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-105">This document serves as a reference on the events that are fired by .NET Core runtime.</span></span>

<span data-ttu-id="fa5a2-106">.NET Framework のランタイム イベントについては、「[CLR ETW イベント](../../framework/performance/clr-etw-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-106">For runtime events in .NET Framework, see [CLR ETW Events](../../framework/performance/clr-etw-events.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fa5a2-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fa5a2-107">In this section</span></span>

<span data-ttu-id="fa5a2-108">[競合イベント](runtime-contention-events.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a2-108">[Contention Events](runtime-contention-events.md)</span></span>\
<span data-ttu-id="fa5a2-109">これらのイベントは、モニターのロック競合に関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-109">These events collect information about monitor lock contentions.</span></span>

<span data-ttu-id="fa5a2-110">[ガベージ コレクション イベント](runtime-garbage-collection-events.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a2-110">[Garbage Collection Events](runtime-garbage-collection-events.md)</span></span>\
<span data-ttu-id="fa5a2-111">これらのイベントは、ガベージ コレクションに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-111">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="fa5a2-112">ガベージ コレクションが実行された回数、ガベージ コレクションの間に解放されたメモリの量など、診断やデバッグに役立つ情報を入手できます。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-112">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc.</span></span>

<span data-ttu-id="fa5a2-113">[例外イベント](runtime-exception-events.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a2-113">[Exception Events](runtime-exception-events.md)</span></span>\
<span data-ttu-id="fa5a2-114">これらのランタイム イベントは、スローされる例外に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-114">These runtime events capture information about exceptions that are thrown.</span></span>

<span data-ttu-id="fa5a2-115">[相互運用イベント](runtime-interop-events.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a2-115">[Interop Events](runtime-interop-events.md)</span></span>\
<span data-ttu-id="fa5a2-116">これらのランタイム イベントは、共通中間言語 (CIL) のスタブ生成に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-116">These runtime events capture information about Common Intermediate Language (CIL) stub generation.</span></span>

<span data-ttu-id="fa5a2-117">[ローダーおよびバインダー イベント](runtime-loader-binder-events.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a2-117">[Loader and Binder Events](runtime-loader-binder-events.md)</span></span>\
<span data-ttu-id="fa5a2-118">これらのイベントは、アセンブリ、およびモジュールのロードとアンロードに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-118">These events collect information relating to loading and unloading assemblies and modules.</span></span>

<span data-ttu-id="fa5a2-119">[メソッド イベント](runtime-method-events.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a2-119">[Method Events](runtime-method-events.md)</span></span>\
<span data-ttu-id="fa5a2-120">これらのイベントは、メソッド固有の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-120">These events collect information that is specific to methods.</span></span> <span data-ttu-id="fa5a2-121">これらのイベントのペイロードは、シンボルの解決に必要です。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-121">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="fa5a2-122">さらに、これらのイベントは、メソッドが呼び出された回数などの有用な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-122">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="fa5a2-123">[スレッド イベント](runtime-thread-events.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a2-123">[Thread Events](runtime-thread-events.md)</span></span>\
<span data-ttu-id="fa5a2-124">これらのイベントは、ワーカー スレッドと I/O スレッドに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-124">These events collect information about worker and I/O threads.</span></span>

<span data-ttu-id="fa5a2-125">[型イベント](runtime-type-events.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a2-125">[Type Events](runtime-type-events.md)</span></span>\
<span data-ttu-id="fa5a2-126">これらのイベントは、型システムに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="fa5a2-126">These events collect information about the type system.</span></span>
