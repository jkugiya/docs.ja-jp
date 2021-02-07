---
description: '詳細情報: <GCNoAffinitize> 要素'
title: GCNoAffinitize 要素
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 139c0fd9e1ec829a3569b77a85e6526bec765e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754551"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="2f423-103">\<GCNoAffinitize> 要素</span><span class="sxs-lookup"><span data-stu-id="2f423-103">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="2f423-104">Cpu を使用してサーバー GC スレッドを関係付けするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f423-104">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="2f423-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f423-105">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f423-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="2f423-106">Attributes and elements</span></span>

<span data-ttu-id="2f423-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f423-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f423-108">属性</span><span class="sxs-lookup"><span data-stu-id="2f423-108">Attributes</span></span>

|<span data-ttu-id="2f423-109">属性</span><span class="sxs-lookup"><span data-stu-id="2f423-109">Attribute</span></span>|<span data-ttu-id="2f423-110">説明</span><span class="sxs-lookup"><span data-stu-id="2f423-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2f423-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="2f423-111">Required attribute.</span></span><br /><br /><span data-ttu-id="2f423-112">サーバー GC スレッド/ヒープをコンピューターで使用可能なプロセッサと関連付けるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f423-112">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="2f423-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="2f423-113">enabled attribute</span></span>

|<span data-ttu-id="2f423-114">値</span><span class="sxs-lookup"><span data-stu-id="2f423-114">Value</span></span>|<span data-ttu-id="2f423-115">説明</span><span class="sxs-lookup"><span data-stu-id="2f423-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="2f423-116">アフィニティ化する server GC スレッドと Cpu。</span><span class="sxs-lookup"><span data-stu-id="2f423-116">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="2f423-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="2f423-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="2f423-118">では、Cpu を使用してサーバー GC スレッドを関係付けません。</span><span class="sxs-lookup"><span data-stu-id="2f423-118">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2f423-119">子要素</span><span class="sxs-lookup"><span data-stu-id="2f423-119">Child elements</span></span>

<span data-ttu-id="2f423-120">なし。</span><span class="sxs-lookup"><span data-stu-id="2f423-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2f423-121">親要素</span><span class="sxs-lookup"><span data-stu-id="2f423-121">Parent elements</span></span>

|<span data-ttu-id="2f423-122">要素</span><span class="sxs-lookup"><span data-stu-id="2f423-122">Element</span></span>|<span data-ttu-id="2f423-123">説明</span><span class="sxs-lookup"><span data-stu-id="2f423-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2f423-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="2f423-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2f423-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2f423-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2f423-126">解説</span><span class="sxs-lookup"><span data-stu-id="2f423-126">Remarks</span></span>

<span data-ttu-id="2f423-127">既定では、サーバー GC スレッドはそれぞれの Cpu とハード関係があります。</span><span class="sxs-lookup"><span data-stu-id="2f423-127">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="2f423-128">システムの使用可能な各プロセッサには、独自の GC ヒープとスレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="2f423-128">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="2f423-129">これは、キャッシュの使用を最適化するため、通常は推奨される設定です。</span><span class="sxs-lookup"><span data-stu-id="2f423-129">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="2f423-130">4.6.2 .NET Framework 以降では、 **GCNoAffinitize** 要素の属性をに設定することにより、 `enabled` `true` サーバー GC スレッドと cpu を密に結合しないように指定できます。</span><span class="sxs-lookup"><span data-stu-id="2f423-130">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="2f423-131">Cpu を使用してサーバー GC スレッドを関係付けしないように、 **GCNoAffinitize** 構成要素のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2f423-131">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="2f423-132">また、アプリケーションで使用される GC ヒープとスレッドの数を制御するために、この要素を [Gの Apcount](gcheapcount-element.md) 要素と共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f423-132">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="2f423-133">`enabled` **GCNoAffinitize** 要素の属性が `false` (既定値) の場合は、 [g apcount](gcheapcount-element.md)要素を使用して gc スレッドとヒープの数を指定することもできます。また、 [GCHEAPAFFINITIZEMASK](gcheapaffinitizemask-element.md)要素を使用して、gc スレッドとヒープが関連付けられているプロセッサを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f423-133">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="2f423-134">例</span><span class="sxs-lookup"><span data-stu-id="2f423-134">Example</span></span>

<span data-ttu-id="2f423-135">次の例では、サーバー GC スレッドをハード関係付けしていません。</span><span class="sxs-lookup"><span data-stu-id="2f423-135">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="2f423-136">次の例では、サーバー GC スレッドを関係付けせず、GC ヒープ/スレッドの数を10に制限しています。</span><span class="sxs-lookup"><span data-stu-id="2f423-136">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2f423-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f423-137">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2f423-138">GCHeapAffinitizeMask 要素</span><span class="sxs-lookup"><span data-stu-id="2f423-138">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="2f423-139">G不正 Apcount 要素</span><span class="sxs-lookup"><span data-stu-id="2f423-139">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="2f423-140">ガベージ コレクションの基礎</span><span class="sxs-lookup"><span data-stu-id="2f423-140">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="2f423-141">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="2f423-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2f423-142">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="2f423-142">Configuration File Schema</span></span>](../index.md)
