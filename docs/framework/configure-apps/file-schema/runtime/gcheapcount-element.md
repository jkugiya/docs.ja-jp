---
description: '詳細情報: <GCHeapCount> 要素'
title: G不正 Apcount 要素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 9e1e000d647435fe7a8c4b1a8f7549f06c2a3b38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786968"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="0697e-103">\<GCHeapCount> 要素</span><span class="sxs-lookup"><span data-stu-id="0697e-103">\<GCHeapCount> element</span></span>

<span data-ttu-id="0697e-104">サーバーのガベージコレクションに使用するヒープまたはスレッドの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0697e-104">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a><span data-ttu-id="0697e-105">構文</span><span class="sxs-lookup"><span data-stu-id="0697e-105">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0697e-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="0697e-106">Attributes and elements</span></span>

<span data-ttu-id="0697e-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0697e-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0697e-108">属性</span><span class="sxs-lookup"><span data-stu-id="0697e-108">Attributes</span></span>

|<span data-ttu-id="0697e-109">属性</span><span class="sxs-lookup"><span data-stu-id="0697e-109">Attribute</span></span>|<span data-ttu-id="0697e-110">説明</span><span class="sxs-lookup"><span data-stu-id="0697e-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0697e-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="0697e-111">Required attribute.</span></span><br /><br /><span data-ttu-id="0697e-112">サーバーのガベージコレクションに使用するヒープの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0697e-112">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="0697e-113">実際のヒープ数は、指定するヒープの数とプロセスで使用できるプロセッサの数の最小値です。</span><span class="sxs-lookup"><span data-stu-id="0697e-113">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="0697e-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="0697e-114">enabled attribute</span></span>

|<span data-ttu-id="0697e-115">値</span><span class="sxs-lookup"><span data-stu-id="0697e-115">Value</span></span>|<span data-ttu-id="0697e-116">説明</span><span class="sxs-lookup"><span data-stu-id="0697e-116">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="0697e-117">サーバー GC に使用するヒープの数。</span><span class="sxs-lookup"><span data-stu-id="0697e-117">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0697e-118">子要素</span><span class="sxs-lookup"><span data-stu-id="0697e-118">Child elements</span></span>

<span data-ttu-id="0697e-119">なし。</span><span class="sxs-lookup"><span data-stu-id="0697e-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0697e-120">親要素</span><span class="sxs-lookup"><span data-stu-id="0697e-120">Parent elements</span></span>

|<span data-ttu-id="0697e-121">要素</span><span class="sxs-lookup"><span data-stu-id="0697e-121">Element</span></span>|<span data-ttu-id="0697e-122">説明</span><span class="sxs-lookup"><span data-stu-id="0697e-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0697e-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="0697e-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0697e-124">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0697e-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0697e-125">解説</span><span class="sxs-lookup"><span data-stu-id="0697e-125">Remarks</span></span>

<span data-ttu-id="0697e-126">既定では、サーバー GC スレッドはそれぞれの CPU とハード関係があるため、1つの GC ヒープ、1つのサーバー GC スレッド、および各プロセッサにつき1つのバックグラウンドサーバー GC スレッドが存在するようになります。</span><span class="sxs-lookup"><span data-stu-id="0697e-126">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="0697e-127">.NET Framework 4.6.2 以降では、 **g Apcount** 要素を使用して、アプリケーションでサーバー GC に使用されるヒープの数を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="0697e-127">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="0697e-128">サーバー GC に使用されるヒープの数を制限することは、サーバーアプリケーションの複数のインスタンスを実行するシステムに特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0697e-128">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="0697e-129">通常は、次の2つのフラグと共に使用 **されます**。</span><span class="sxs-lookup"><span data-stu-id="0697e-129">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="0697e-130">[GCNoAffinitize](gcnoaffinitize-element.md)。サーバー GC スレッド/ヒープが cpu と関連付けられているかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="0697e-130">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="0697e-131">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)。 cpu との GC スレッド/ヒープの関係を制御します。</span><span class="sxs-lookup"><span data-stu-id="0697e-131">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="0697e-132">**GGCNoAffinitize** が設定されていて、 が無効になっている場合 (既定の設定)、 *nn* GC スレッド/ヒープと最初の *nn* プロセッサの間に関係があります。</span><span class="sxs-lookup"><span data-stu-id="0697e-132">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="0697e-133">**GCHeapAffinitizeMask** 要素を使用して、プロセスのサーバー GC ヒープによって使用されるプロセッサを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0697e-133">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="0697e-134">それ以外の場合、システムで複数のサーバープロセスが実行されていると、プロセッサの使用率が重複します。</span><span class="sxs-lookup"><span data-stu-id="0697e-134">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="0697e-135">**GGCNoAffinitize** が有効になっている場合、ガベージコレクターはサーバー gc に使用されるプロセッサの数を制限しますが、gc ヒープとプロセッサを関係付けしません。</span><span class="sxs-lookup"><span data-stu-id="0697e-135">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="0697e-136">例</span><span class="sxs-lookup"><span data-stu-id="0697e-136">Example</span></span>

<span data-ttu-id="0697e-137">次の例は、アプリケーションが10個のヒープ/スレッドを持つサーバー GC を使用することを示しています。</span><span class="sxs-lookup"><span data-stu-id="0697e-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="0697e-138">これらのヒープは、システムで実行されている他のアプリケーションのヒープと重複しないようにするため、 **GCHeapAffinitizeMask** を使用して、プロセスで cpu 0 ~ 9 を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="0697e-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="0697e-139">次の例では、サーバー GC スレッドを関係付け、GC ヒープ/スレッドの数を10に制限していません。</span><span class="sxs-lookup"><span data-stu-id="0697e-139">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0697e-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="0697e-140">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0697e-141">GCNoAffinitize 要素</span><span class="sxs-lookup"><span data-stu-id="0697e-141">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="0697e-142">GCHeapAffinitizeMask 要素</span><span class="sxs-lookup"><span data-stu-id="0697e-142">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="0697e-143">ガベージ コレクションの基礎</span><span class="sxs-lookup"><span data-stu-id="0697e-143">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="0697e-144">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="0697e-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0697e-145">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="0697e-145">Configuration File Schema</span></span>](../index.md)
