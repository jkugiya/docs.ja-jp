---
title: 型システム ランタイム イベント
description: TypeLoadStart や Typeloadstart など、.NET 型システムに固有の診断情報を収集する .NET ランタイム イベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594037"
---
# <a name="net-runtime-type-events"></a><span data-ttu-id="72224-103">.NET ランタイム型イベント</span><span class="sxs-lookup"><span data-stu-id="72224-103">.NET runtime type events</span></span>

<span data-ttu-id="72224-104">これらのイベントは、型の読み込みに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="72224-104">These events collect information relating to loading types.</span></span> <span data-ttu-id="72224-105">診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="72224-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="typeloadstart-event"></a><span data-ttu-id="72224-106">TypeLoadStart イベント</span><span class="sxs-lookup"><span data-stu-id="72224-106">TypeLoadStart Event</span></span>

|<span data-ttu-id="72224-107">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="72224-107">Keyword for raising the event</span></span>|<span data-ttu-id="72224-108">Event</span><span class="sxs-lookup"><span data-stu-id="72224-108">Event</span></span>|<span data-ttu-id="72224-109">Level</span><span class="sxs-lookup"><span data-stu-id="72224-109">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="72224-110">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="72224-110">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="72224-111">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="72224-111">Informational (4)</span></span>|  

|<span data-ttu-id="72224-112">Event</span><span class="sxs-lookup"><span data-stu-id="72224-112">Event</span></span>|<span data-ttu-id="72224-113">イベント ID</span><span class="sxs-lookup"><span data-stu-id="72224-113">Event ID</span></span>|<span data-ttu-id="72224-114">説明</span><span class="sxs-lookup"><span data-stu-id="72224-114">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|<span data-ttu-id="72224-115">73</span><span class="sxs-lookup"><span data-stu-id="72224-115">73</span></span>|<span data-ttu-id="72224-116">型の読み込みが開始されました。</span><span class="sxs-lookup"><span data-stu-id="72224-116">A type load has started.</span></span>|

|<span data-ttu-id="72224-117">フィールド名</span><span class="sxs-lookup"><span data-stu-id="72224-117">Field name</span></span>|<span data-ttu-id="72224-118">データ型</span><span class="sxs-lookup"><span data-stu-id="72224-118">Data type</span></span>|<span data-ttu-id="72224-119">説明</span><span class="sxs-lookup"><span data-stu-id="72224-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="72224-120">型の読み込み操作の ID。</span><span class="sxs-lookup"><span data-stu-id="72224-120">ID for the type load operation.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="72224-121">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="72224-121">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="typeloadstop-event"></a><span data-ttu-id="72224-122">TypeLoadStop イベント</span><span class="sxs-lookup"><span data-stu-id="72224-122">TypeLoadStop Event</span></span>

|<span data-ttu-id="72224-123">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="72224-123">Keyword for raising the event</span></span>|<span data-ttu-id="72224-124">Level</span><span class="sxs-lookup"><span data-stu-id="72224-124">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="72224-125">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="72224-125">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="72224-126">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="72224-126">Informational (4)</span></span>|  

|<span data-ttu-id="72224-127">Event</span><span class="sxs-lookup"><span data-stu-id="72224-127">Event</span></span>|<span data-ttu-id="72224-128">イベント ID</span><span class="sxs-lookup"><span data-stu-id="72224-128">Event ID</span></span>|<span data-ttu-id="72224-129">説明</span><span class="sxs-lookup"><span data-stu-id="72224-129">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|<span data-ttu-id="72224-130">74</span><span class="sxs-lookup"><span data-stu-id="72224-130">74</span></span>|<span data-ttu-id="72224-131">型の読み込みが完了しました。</span><span class="sxs-lookup"><span data-stu-id="72224-131">A type load is finished.</span></span>|

|<span data-ttu-id="72224-132">フィールド名</span><span class="sxs-lookup"><span data-stu-id="72224-132">Field name</span></span>|<span data-ttu-id="72224-133">データ型</span><span class="sxs-lookup"><span data-stu-id="72224-133">Data type</span></span>|<span data-ttu-id="72224-134">説明</span><span class="sxs-lookup"><span data-stu-id="72224-134">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="72224-135">型の読み込み操作の ID (対応する TypeLoadStart イベントの TypeLoadStartID と一致します)。</span><span class="sxs-lookup"><span data-stu-id="72224-135">ID for the type load operation (matches the corresponding TypeLoadStart event's TypeLoadStartID).</span></span>|
|`LoadLevel`|`win:UInt16`|<span data-ttu-id="72224-136">型の読み込みレベル。</span><span class="sxs-lookup"><span data-stu-id="72224-136">Type load level.</span></span>|
|`TypeID`|`win:UInt64`|<span data-ttu-id="72224-137">型ハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="72224-137">Pointer to the type handle.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="72224-138">型の名前。</span><span class="sxs-lookup"><span data-stu-id="72224-138">Name of the type.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="72224-139">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="72224-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
