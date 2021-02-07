---
description: '詳細情報: ログクラス'
title: Logging クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 1ae3079ab21502ee3f5bf71db57f0695da9a8571
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726209"
---
# <a name="logging-class"></a><span data-ttu-id="0a431-103">Logging クラス</span><span class="sxs-lookup"><span data-stu-id="0a431-103">Logging class</span></span>

<span data-ttu-id="0a431-104">トレースログ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="0a431-104">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="0a431-105">このクラスは内部的なものであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="0a431-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0a431-106">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0a431-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="0a431-107">関連付け方法</span><span class="sxs-lookup"><span data-stu-id="0a431-107">Associate method</span></span>

<span data-ttu-id="0a431-108">2つのオブジェクトが互いに関連付けられていることをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="0a431-108">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="0a431-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-109">Parameters</span></span>

- <span data-ttu-id="0a431-110">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-110">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-111">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-111">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-112">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-112">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-113">関連付けるオブジェクト `objB` 。</span><span class="sxs-lookup"><span data-stu-id="0a431-113">The object to associate with `objB`.</span></span>

- <span data-ttu-id="0a431-114">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-114">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-115">関連付けるオブジェクト `objA` 。</span><span class="sxs-lookup"><span data-stu-id="0a431-115">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="0a431-116">Enter (TraceSource、object、string、string) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-116">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="0a431-117">メソッドへの入り口をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="0a431-117">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="0a431-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-118">Parameters</span></span>

- <span data-ttu-id="0a431-119">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-119">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-120">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-120">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-121">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-121">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-122">メソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-122">The object that the method was called on.</span></span>

- <span data-ttu-id="0a431-123">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-123">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-124">入力されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-124">The method that is being entered.</span></span>

- <span data-ttu-id="0a431-125">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-125">`param` <xref:System.String></span></span>

  <span data-ttu-id="0a431-126">メソッドに渡されたパラメーター。</span><span class="sxs-lookup"><span data-stu-id="0a431-126">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="0a431-127">Enter (TraceSource、object、string、object) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-127">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="0a431-128">メソッドへの入り口をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="0a431-128">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="0a431-129">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-129">Parameters</span></span>

- <span data-ttu-id="0a431-130">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-130">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-131">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-131">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-132">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-132">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-133">メソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-133">The object that the method was called on.</span></span>

- <span data-ttu-id="0a431-134">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-134">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-135">入力されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-135">The method that is being entered.</span></span>

- <span data-ttu-id="0a431-136">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-136">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-137">メソッドに渡されたパラメーター。</span><span class="sxs-lookup"><span data-stu-id="0a431-137">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="0a431-138">Enter (TraceSource、string、string、string) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-138">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="0a431-139">メソッドへの入り口をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="0a431-139">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="0a431-140">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-140">Parameters</span></span>

- <span data-ttu-id="0a431-141">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-141">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-142">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-142">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-143">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-143">`obj` <xref:System.String></span></span>

  <span data-ttu-id="0a431-144">メソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-144">The object that the method was called on.</span></span>

- <span data-ttu-id="0a431-145">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-145">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-146">入力されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-146">The method that is being entered.</span></span>

- <span data-ttu-id="0a431-147">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-147">`param` <xref:System.String></span></span>

  <span data-ttu-id="0a431-148">メソッドに渡されたパラメーター。</span><span class="sxs-lookup"><span data-stu-id="0a431-148">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="0a431-149">Enter (TraceSource、string、string、object) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-149">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="0a431-150">メソッドへの入り口をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="0a431-150">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="0a431-151">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-151">Parameters</span></span>

- <span data-ttu-id="0a431-152">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-152">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-153">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-153">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-154">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-154">`obj` <xref:System.String></span></span>

  <span data-ttu-id="0a431-155">メソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-155">The object that the method was called on.</span></span>

- <span data-ttu-id="0a431-156">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-156">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-157">入力されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-157">The method that is being entered.</span></span>

- <span data-ttu-id="0a431-158">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-158">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-159">メソッドに渡されたパラメーター。</span><span class="sxs-lookup"><span data-stu-id="0a431-159">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="0a431-160">Enter (TraceSource, string, string) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-160">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="0a431-161">メソッドへの入り口をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="0a431-161">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="0a431-162">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-162">Parameters</span></span>

- <span data-ttu-id="0a431-163">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-163">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-164">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-164">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-165">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-165">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-166">入力されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-166">The method that is being entered.</span></span>

- <span data-ttu-id="0a431-167">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-167">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="0a431-168">メソッドに渡されたパラメーター。</span><span class="sxs-lookup"><span data-stu-id="0a431-168">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="0a431-169">Enter (TraceSource, string) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-169">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="0a431-170">メソッドへの入り口をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="0a431-170">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="0a431-171">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-171">Parameters</span></span>

- <span data-ttu-id="0a431-172">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-172">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-173">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-173">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-174">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-174">`msg` <xref:System.String></span></span>

  <span data-ttu-id="0a431-175">トレースソースにログを記録するための開始メッセージ。</span><span class="sxs-lookup"><span data-stu-id="0a431-175">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="0a431-176">Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-176">Exception method</span></span>

<span data-ttu-id="0a431-177">例外をログに記録し、インデントを復元します。</span><span class="sxs-lookup"><span data-stu-id="0a431-177">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="0a431-178">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-178">Parameters</span></span>

- <span data-ttu-id="0a431-179">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-179">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-180">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-180">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-181">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-181">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-182">例外をスローしたメソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-182">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="0a431-183">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-183">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-184">例外をスローしたメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-184">The method that threw the exception.</span></span>

- <span data-ttu-id="0a431-185">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="0a431-185">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="0a431-186">スローされた例外。</span><span class="sxs-lookup"><span data-stu-id="0a431-186">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="0a431-187">Exit (TraceSource、object、string、object) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-187">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="0a431-188">ログは関数から終了します。</span><span class="sxs-lookup"><span data-stu-id="0a431-188">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="0a431-189">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-189">Parameters</span></span>

- <span data-ttu-id="0a431-190">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-190">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-191">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-191">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-192">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-192">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-193">メソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-193">The object that the method was called on.</span></span>

- <span data-ttu-id="0a431-194">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-194">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-195">終了されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-195">The method that is being exited.</span></span>

- <span data-ttu-id="0a431-196">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-196">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-197">メソッドによって返される値。</span><span class="sxs-lookup"><span data-stu-id="0a431-197">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="0a431-198">Exit (TraceSource、string、string、object) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-198">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="0a431-199">ログは関数から終了します。</span><span class="sxs-lookup"><span data-stu-id="0a431-199">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="0a431-200">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-200">Parameters</span></span>

- <span data-ttu-id="0a431-201">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-201">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-202">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-202">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-203">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-203">`obj` <xref:System.String></span></span>

  <span data-ttu-id="0a431-204">メソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-204">The object that the method was called on.</span></span>

- <span data-ttu-id="0a431-205">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-205">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-206">終了されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-206">The method that is being exited.</span></span>

- <span data-ttu-id="0a431-207">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-207">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-208">メソッドによって返される値。</span><span class="sxs-lookup"><span data-stu-id="0a431-208">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="0a431-209">Exit (TraceSource、object、string、string) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-209">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="0a431-210">ログは関数から終了します。</span><span class="sxs-lookup"><span data-stu-id="0a431-210">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="0a431-211">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-211">Parameters</span></span>

- <span data-ttu-id="0a431-212">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-212">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-213">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-213">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-214">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0a431-214">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="0a431-215">メソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-215">The object that the method was called on.</span></span>

- <span data-ttu-id="0a431-216">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-216">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-217">終了されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-217">The method that is being exited.</span></span>

- <span data-ttu-id="0a431-218">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-218">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="0a431-219">メソッドによって返される値。</span><span class="sxs-lookup"><span data-stu-id="0a431-219">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="0a431-220">Exit (TraceSource、string、string、string) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-220">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="0a431-221">ログは関数から終了します。</span><span class="sxs-lookup"><span data-stu-id="0a431-221">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="0a431-222">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-222">Parameters</span></span>

- <span data-ttu-id="0a431-223">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-223">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-224">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-224">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-225">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-225">`obj` <xref:System.String></span></span>

  <span data-ttu-id="0a431-226">メソッドが呼び出されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0a431-226">The object that the method was called on.</span></span>

- <span data-ttu-id="0a431-227">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-227">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-228">終了されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-228">The method that is being exited.</span></span>

- <span data-ttu-id="0a431-229">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-229">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="0a431-230">メソッドによって返される値。</span><span class="sxs-lookup"><span data-stu-id="0a431-230">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="0a431-231">Exit (TraceSource, string, string) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-231">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="0a431-232">ログは関数から終了します。</span><span class="sxs-lookup"><span data-stu-id="0a431-232">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="0a431-233">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-233">Parameters</span></span>

- <span data-ttu-id="0a431-234">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-234">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-235">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-235">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-236">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-236">`method` <xref:System.String></span></span>

  <span data-ttu-id="0a431-237">終了されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="0a431-237">The method that is being exited.</span></span>

- <span data-ttu-id="0a431-238">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-238">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="0a431-239">終了されるメソッドに渡されたパラメーター。</span><span class="sxs-lookup"><span data-stu-id="0a431-239">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="0a431-240">Exit (TraceSource, string) メソッド</span><span class="sxs-lookup"><span data-stu-id="0a431-240">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="0a431-241">ログは関数から終了します。</span><span class="sxs-lookup"><span data-stu-id="0a431-241">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="0a431-242">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a431-242">Parameters</span></span>

- <span data-ttu-id="0a431-243">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a431-243">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="0a431-244">イベントのログを記録するトレースソース。</span><span class="sxs-lookup"><span data-stu-id="0a431-244">The trace source to log the event to.</span></span>

- <span data-ttu-id="0a431-245">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0a431-245">`msg` <xref:System.String></span></span>

  <span data-ttu-id="0a431-246">トレースソースに記録する終了メッセージ。</span><span class="sxs-lookup"><span data-stu-id="0a431-246">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="0a431-247">Http プロパティ</span><span class="sxs-lookup"><span data-stu-id="0a431-247">Http property</span></span>

<span data-ttu-id="0a431-248">"System .Net. Http" のトレースソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a431-248">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="0a431-249">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="0a431-249">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="0a431-250">"System .Net. Http" のトレースソース `null` 。ログ記録が有効になっていない場合は。</span><span class="sxs-lookup"><span data-stu-id="0a431-250">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="0a431-251">On プロパティ</span><span class="sxs-lookup"><span data-stu-id="0a431-251">On property</span></span>

<span data-ttu-id="0a431-252">ログが有効になっているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a431-252">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="0a431-253">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="0a431-253">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="0a431-254">ログが可能な場合は `true`、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="0a431-254">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a431-255">必要条件</span><span class="sxs-lookup"><span data-stu-id="0a431-255">Requirements</span></span>

<span data-ttu-id="0a431-256">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="0a431-256">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="0a431-257">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="0a431-257">**Assembly:** System (in System.dll)</span></span>
