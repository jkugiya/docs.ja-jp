---
description: '詳細情報: <GCHeapAffinitizeMask> 要素'
title: GCHeapAffinitizeMask 要素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: ea6be3fa3d973f228576db69d0700b1f7ddba585
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786981"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="30b2a-103">\<GCHeapAffinitizeMask> 要素</span><span class="sxs-lookup"><span data-stu-id="30b2a-103">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="30b2a-104">GC ヒープと個々のプロセッサ間の関係を定義します。</span><span class="sxs-lookup"><span data-stu-id="30b2a-104">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="30b2a-105">構文</span><span class="sxs-lookup"><span data-stu-id="30b2a-105">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="30b2a-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="30b2a-106">Attributes and elements</span></span>

<span data-ttu-id="30b2a-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="30b2a-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="30b2a-108">属性</span><span class="sxs-lookup"><span data-stu-id="30b2a-108">Attributes</span></span>

|<span data-ttu-id="30b2a-109">属性</span><span class="sxs-lookup"><span data-stu-id="30b2a-109">Attribute</span></span>|<span data-ttu-id="30b2a-110">説明</span><span class="sxs-lookup"><span data-stu-id="30b2a-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="30b2a-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="30b2a-111">Required attribute.</span></span><br /><br /><span data-ttu-id="30b2a-112">GC ヒープと個々のプロセッサ間の関係を指定します。</span><span class="sxs-lookup"><span data-stu-id="30b2a-112">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="30b2a-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="30b2a-113">enabled attribute</span></span>

|<span data-ttu-id="30b2a-114">値</span><span class="sxs-lookup"><span data-stu-id="30b2a-114">Value</span></span>|<span data-ttu-id="30b2a-115">説明</span><span class="sxs-lookup"><span data-stu-id="30b2a-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="30b2a-116">サーバー GC ヒープと個々のプロセッサ間の関係を定義するビットマスクを形成する10進値。</span><span class="sxs-lookup"><span data-stu-id="30b2a-116">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="30b2a-117">子要素</span><span class="sxs-lookup"><span data-stu-id="30b2a-117">Child elements</span></span>

<span data-ttu-id="30b2a-118">なし。</span><span class="sxs-lookup"><span data-stu-id="30b2a-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="30b2a-119">親要素</span><span class="sxs-lookup"><span data-stu-id="30b2a-119">Parent elements</span></span>

|<span data-ttu-id="30b2a-120">要素</span><span class="sxs-lookup"><span data-stu-id="30b2a-120">Element</span></span>|<span data-ttu-id="30b2a-121">説明</span><span class="sxs-lookup"><span data-stu-id="30b2a-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="30b2a-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="30b2a-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="30b2a-123">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="30b2a-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="30b2a-124">解説</span><span class="sxs-lookup"><span data-stu-id="30b2a-124">Remarks</span></span>

<span data-ttu-id="30b2a-125">既定では、サーバー GC スレッドはそれぞれの CPU とハード関係があるため、1つの GC ヒープ、1つのサーバー GC スレッド、および各プロセッサにつき1つのバックグラウンドサーバー GC スレッドが存在するようになります。</span><span class="sxs-lookup"><span data-stu-id="30b2a-125">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="30b2a-126">4.6.2 .NET Framework 以降では、ヒープの数が **g Apcount** 要素によって制限されている場合に、 **GCHeapAffinitizeMask** 要素を使用して、サーバー GC ヒープとプロセッサ間の関係を制御できます。</span><span class="sxs-lookup"><span data-stu-id="30b2a-126">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="30b2a-127">**GCHeapAffinitizeMask** は通常、次の2つのフラグと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="30b2a-127">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="30b2a-128">[GCNoAffinitize](gcnoaffinitize-element.md)。サーバー GC スレッド/ヒープが cpu と関連付けられているかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="30b2a-128">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="30b2a-129">`enabled`GCHeapAffinitizeMask 設定を使用するには、 [GCNoAffinitize](gcnoaffinitize-element.md)要素の属性が `false` (既定値) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="30b2a-129">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="30b2a-130">"サーバー GC のプロセスで使用されるヒープの[数を制限](gcheapcount-element.md)する"。</span><span class="sxs-lookup"><span data-stu-id="30b2a-130">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="30b2a-131">既定では、プロセッサごとに1つのヒープがあります。</span><span class="sxs-lookup"><span data-stu-id="30b2a-131">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="30b2a-132">**nnnn** は、10進値として表現されるビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="30b2a-132">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="30b2a-133">バイト0のビット0はプロセッサ0を表し、バイト0のビット1はプロセッサ1を表します。</span><span class="sxs-lookup"><span data-stu-id="30b2a-133">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="30b2a-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="30b2a-134">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="30b2a-135">値1023は、0x3FF または 0011 1111 1111b です。</span><span class="sxs-lookup"><span data-stu-id="30b2a-135">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="30b2a-136">このプロセスでは、プロセッサ0からプロセッサ9までの10個のプロセッサが使用されます。</span><span class="sxs-lookup"><span data-stu-id="30b2a-136">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="30b2a-137">例</span><span class="sxs-lookup"><span data-stu-id="30b2a-137">Example</span></span>

<span data-ttu-id="30b2a-138">次の例は、アプリケーションが10個のヒープ/スレッドを持つサーバー GC を使用することを示しています。</span><span class="sxs-lookup"><span data-stu-id="30b2a-138">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="30b2a-139">これらのヒープは、システムで実行されている他のアプリケーションのヒープと重複しないようにするため、 **GCHeapAffinitizeMask** を使用して、プロセスで cpu 0 ~ 9 を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="30b2a-139">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="30b2a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="30b2a-140">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="30b2a-141">GCNoAffinitize 要素</span><span class="sxs-lookup"><span data-stu-id="30b2a-141">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="30b2a-142">G不正 Apcount 要素</span><span class="sxs-lookup"><span data-stu-id="30b2a-142">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="30b2a-143">ガベージ コレクションの基礎</span><span class="sxs-lookup"><span data-stu-id="30b2a-143">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="30b2a-144">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="30b2a-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="30b2a-145">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="30b2a-145">Configuration File Schema</span></span>](../index.md)
