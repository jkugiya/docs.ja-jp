---
description: '詳細情報: <gcServer> 要素'
title: gcServer 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: bed347699786682421292392a8d2449b7aac61d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754538"
---
# <a name="gcserver-element"></a><span data-ttu-id="09734-103">\<gcServer> 要素</span><span class="sxs-lookup"><span data-stu-id="09734-103">\<gcServer> element</span></span>

<span data-ttu-id="09734-104">共通言語ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="09734-104">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="09734-105">構文</span><span class="sxs-lookup"><span data-stu-id="09734-105">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09734-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="09734-106">Attributes and elements</span></span>

<span data-ttu-id="09734-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="09734-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="09734-108">属性</span><span class="sxs-lookup"><span data-stu-id="09734-108">Attributes</span></span>

|<span data-ttu-id="09734-109">属性</span><span class="sxs-lookup"><span data-stu-id="09734-109">Attribute</span></span>|<span data-ttu-id="09734-110">説明</span><span class="sxs-lookup"><span data-stu-id="09734-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="09734-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="09734-111">Required attribute.</span></span><br /><br /><span data-ttu-id="09734-112">ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="09734-112">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="09734-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="09734-113">enabled attribute</span></span>

|<span data-ttu-id="09734-114">値</span><span class="sxs-lookup"><span data-stu-id="09734-114">Value</span></span>|<span data-ttu-id="09734-115">説明</span><span class="sxs-lookup"><span data-stu-id="09734-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="09734-116">サーバーのガベージ コレクションを実行しません。</span><span class="sxs-lookup"><span data-stu-id="09734-116">Does not run server garbage collection.</span></span> <span data-ttu-id="09734-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="09734-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="09734-118">サーバーのガベージ コレクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="09734-118">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="09734-119">子要素</span><span class="sxs-lookup"><span data-stu-id="09734-119">Child elements</span></span>

<span data-ttu-id="09734-120">なし。</span><span class="sxs-lookup"><span data-stu-id="09734-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="09734-121">親要素</span><span class="sxs-lookup"><span data-stu-id="09734-121">Parent elements</span></span>

|<span data-ttu-id="09734-122">要素</span><span class="sxs-lookup"><span data-stu-id="09734-122">Element</span></span>|<span data-ttu-id="09734-123">説明</span><span class="sxs-lookup"><span data-stu-id="09734-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="09734-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="09734-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="09734-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="09734-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09734-126">解説</span><span class="sxs-lookup"><span data-stu-id="09734-126">Remarks</span></span>

<span data-ttu-id="09734-127">共通言語ランタイム (CLR) は、2 種類のガベージ コレクションをサポートしています。1 つはワークステーション ガベージ コレクションで、すべてのシステムで使用できるものです。もう 1 つはサーバー ガベージ コレクションで、マルチプロセッサ システムで使用できるものです。</span><span class="sxs-lookup"><span data-stu-id="09734-127">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="09734-128">CLR が実行するガベージコレクションの種類を制御するには、 **gcServer** 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="09734-128">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="09734-129"><xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> プロパティを使用して、サーバー ガベージ コレクションが有効かどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="09734-129">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="09734-130">シングル プロセッサ コンピューターの場合、既定のワークステーション ガベージ コレクションが催促のオプションです。</span><span class="sxs-lookup"><span data-stu-id="09734-130">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="09734-131">2 つのプロセッサを搭載するコンピューターで、ワークステーションかサーバーのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="09734-131">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="09734-132">3 つ以上のプロセッサでは、サーバー ガベージ コレクションが最速のオプションです。</span><span class="sxs-lookup"><span data-stu-id="09734-132">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="09734-133">ほとんどの場合、マルチプロセッササーバーシステムはサーバー GC を無効にし、サーバーアプリの多くのインスタンスが同じコンピューターで実行されるときに、ワークステーション GC を使用します。</span><span class="sxs-lookup"><span data-stu-id="09734-133">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="09734-134">この要素は、アプリケーション構成ファイルでのみ使用できます。要素がマシン構成ファイルにある場合には無視されます。</span><span class="sxs-lookup"><span data-stu-id="09734-134">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="09734-135">.NET Framework 4 以前のバージョンでは、サーバー ガベージ コレクションを有効にすると同時実行ガベージ コレクションが使用できません。</span><span class="sxs-lookup"><span data-stu-id="09734-135">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="09734-136">.NET Framework 4.5 以降では、サーバーのガベージコレクションは同時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="09734-136">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="09734-137">非同時サーバーガベージコレクションを使用するには、 **gcServer** 要素をに設定し、 `true` [gcConcurrent 要素](gcconcurrent-element.md) をに設定し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="09734-137">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="09734-138">.NET Framework 4.6.2 以降では、次の要素を使用してサーバー GC を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="09734-138">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="09734-139">[GCNoAffinitize](gcnoaffinitize-element.md)。サーバー GC ヒープとプロセッサの間にアフィニティがあるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="09734-139">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="09734-140">既定では、プロセッサごとに1つのサーバー GC ヒープがあります。</span><span class="sxs-lookup"><span data-stu-id="09734-140">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="09734-141">"プロセスで使用されるヒープの[数を制限](gcheapcount-element.md)する"。</span><span class="sxs-lookup"><span data-stu-id="09734-141">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="09734-142">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)は、使用可能なサーバー GC ヒープと個々のプロセッサ間の関係を定義します。</span><span class="sxs-lookup"><span data-stu-id="09734-142">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="09734-143">例</span><span class="sxs-lookup"><span data-stu-id="09734-143">Example</span></span>

<span data-ttu-id="09734-144">次の例では、サーバーのガベージコレクションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="09734-144">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="09734-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="09734-145">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="09734-146">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="09734-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="09734-147">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="09734-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="09734-148">同時実行ガベージコレクションを無効にするには</span><span class="sxs-lookup"><span data-stu-id="09734-148">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
