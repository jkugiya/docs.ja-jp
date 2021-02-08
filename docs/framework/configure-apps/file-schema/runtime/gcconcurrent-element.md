---
description: '詳細情報: <gcConcurrent> 要素'
title: gcConcurrent 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: dff8b073977c007a132cfbd685724a02ba37684b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787007"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="34103-103">\<gcConcurrent> 要素</span><span class="sxs-lookup"><span data-stu-id="34103-103">\<gcConcurrent> element</span></span>

<span data-ttu-id="34103-104">共通言語ランタイムがガベージ コレクションを別のスレッドで実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="34103-104">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="34103-105">構文</span><span class="sxs-lookup"><span data-stu-id="34103-105">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34103-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="34103-106">Attributes and elements</span></span>

<span data-ttu-id="34103-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="34103-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="34103-108">属性</span><span class="sxs-lookup"><span data-stu-id="34103-108">Attributes</span></span>

|<span data-ttu-id="34103-109">属性</span><span class="sxs-lookup"><span data-stu-id="34103-109">Attribute</span></span>|<span data-ttu-id="34103-110">説明</span><span class="sxs-lookup"><span data-stu-id="34103-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="34103-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="34103-111">Required attribute.</span></span><br /><br /><span data-ttu-id="34103-112">ランタイムがガベージ コレクションを並列に実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="34103-112">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="34103-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="34103-113">enabled attribute</span></span>

|<span data-ttu-id="34103-114">値</span><span class="sxs-lookup"><span data-stu-id="34103-114">Value</span></span>|<span data-ttu-id="34103-115">説明</span><span class="sxs-lookup"><span data-stu-id="34103-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="34103-116">ガベージコレクションを同時に実行しません。</span><span class="sxs-lookup"><span data-stu-id="34103-116">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="34103-117">ガベージ コレクションを並列に実行します。</span><span class="sxs-lookup"><span data-stu-id="34103-117">Runs garbage collection concurrently.</span></span> <span data-ttu-id="34103-118">既定値です。</span><span class="sxs-lookup"><span data-stu-id="34103-118">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="34103-119">子要素</span><span class="sxs-lookup"><span data-stu-id="34103-119">Child elements</span></span>

<span data-ttu-id="34103-120">なし。</span><span class="sxs-lookup"><span data-stu-id="34103-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34103-121">親要素</span><span class="sxs-lookup"><span data-stu-id="34103-121">Parent elements</span></span>

|<span data-ttu-id="34103-122">要素</span><span class="sxs-lookup"><span data-stu-id="34103-122">Element</span></span>|<span data-ttu-id="34103-123">説明</span><span class="sxs-lookup"><span data-stu-id="34103-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="34103-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="34103-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="34103-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="34103-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="34103-126">解説</span><span class="sxs-lookup"><span data-stu-id="34103-126">Remarks</span></span>

<span data-ttu-id="34103-127">.NET Framework 4 より前では、ワークステーションのガベージコレクションは同時実行ガベージコレクションをサポートしていました。これにより、別のスレッドでバックグラウンドでガベージコレクションが実行されました。</span><span class="sxs-lookup"><span data-stu-id="34103-127">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="34103-128">.NET Framework 4 では、同時実行ガベージコレクションがバックグラウンド GC に置き換えられました。これにより、別のスレッドでバックグラウンドでガベージコレクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="34103-128">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="34103-129">.NET Framework 4.5 以降では、サーバーのガベージコレクションでバックグラウンドコレクションを使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="34103-129">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="34103-130">**GcConcurrent** 要素は、ランタイムが同時実行ガベージコレクションとバックグラウンドガベージコレクションのどちらを実行するか、またはフォアグラウンドでガベージコレクションを実行するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="34103-130">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="34103-131">バックグラウンドガベージコレクションを無効にするには</span><span class="sxs-lookup"><span data-stu-id="34103-131">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="34103-132">.NET Framework 4 以降では、同時実行ガベージコレクションはバックグラウンドガベージコレクションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="34103-132">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="34103-133">.NET Framework のドキュメントでは、 *同時実行* と *背景* という用語が同じ意味で使用されます。</span><span class="sxs-lookup"><span data-stu-id="34103-133">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="34103-134">バックグラウンドガベージコレクションを無効にするには、この記事で説明されているように、 **gcConcurrent** 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="34103-134">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="34103-135">既定では、ランタイムは同時実行ガベージ コレクションまたはバックグラウンド ガベージ コレクションを使用します。これは待機時間について最適化されています。</span><span class="sxs-lookup"><span data-stu-id="34103-135">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="34103-136">アプリケーションでユーザーとのやり取りが多い場合は、同時実行ガベージ コレクションを有効にして、ガベージ コレクションを実行するためのアプリケーションの停止時間を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="34103-136">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="34103-137">`enabled` **GcConcurrent** 要素の属性をに設定すると `false` 、ランタイムは非同時実行ガベージコレクションを使用します。これは、スループットのために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="34103-137">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="34103-138">次の構成ファイルは、バックグラウンドガベージコレクションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="34103-138">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="34103-139">マシン構成ファイルに **gcConcurrentSetting** 設定がある場合は、すべての .NET Framework アプリケーションの既定値が定義されます。</span><span class="sxs-lookup"><span data-stu-id="34103-139">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="34103-140">マシン構成ファイルの設定は、アプリケーション構成ファイルの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="34103-140">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="34103-141">同時実行ガベージコレクションとバックグラウンドガベージコレクションの詳細については、「 [バックグラウンドガベージコレクション](../../../../standard/garbage-collection/background-gc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34103-141">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="34103-142">例</span><span class="sxs-lookup"><span data-stu-id="34103-142">Example</span></span>

<span data-ttu-id="34103-143">次の例では、バックグラウンドガベージコレクションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="34103-143">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="34103-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="34103-144">See also</span></span>

- [<span data-ttu-id="34103-145">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="34103-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="34103-146">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="34103-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="34103-147">ガベージ コレクションの基礎</span><span class="sxs-lookup"><span data-stu-id="34103-147">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
