---
description: '詳細情報: <forcePerformanceCounterUniqueSharedMemoryReads> 要素'
title: <forcePerformanceCounterUniqueSharedMemoryReads> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 63fe695cc993faa851a9ea3196294397d2992c45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787033"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="bc32a-103">\<forcePerformanceCounterUniqueSharedMemoryReads> 要素</span><span class="sxs-lookup"><span data-stu-id="bc32a-103">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>

<span data-ttu-id="bc32a-104">PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。</span><span class="sxs-lookup"><span data-stu-id="bc32a-104">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="bc32a-105">構文</span><span class="sxs-lookup"><span data-stu-id="bc32a-105">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc32a-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bc32a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="bc32a-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc32a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc32a-108">属性</span><span class="sxs-lookup"><span data-stu-id="bc32a-108">Attributes</span></span>  
  
|<span data-ttu-id="bc32a-109">属性</span><span class="sxs-lookup"><span data-stu-id="bc32a-109">Attribute</span></span>|<span data-ttu-id="bc32a-110">説明</span><span class="sxs-lookup"><span data-stu-id="bc32a-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bc32a-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="bc32a-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="bc32a-112">PerfCounter.dll が category Options レジストリ設定を使用して、カテゴリ固有の共有メモリまたはグローバルメモリのパフォーマンスカウンターデータを読み込むかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bc32a-112">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bc32a-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="bc32a-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="bc32a-114">値</span><span class="sxs-lookup"><span data-stu-id="bc32a-114">Value</span></span>|<span data-ttu-id="bc32a-115">説明</span><span class="sxs-lookup"><span data-stu-id="bc32a-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bc32a-116">PerfCounter.dll では、[カテゴリオプション] レジストリ設定を使用しません。これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="bc32a-116">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="bc32a-117">PerfCounter.dll では、[カテゴリオプション] レジストリ設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc32a-117">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc32a-118">子要素</span><span class="sxs-lookup"><span data-stu-id="bc32a-118">Child Elements</span></span>  

 <span data-ttu-id="bc32a-119">なし。</span><span class="sxs-lookup"><span data-stu-id="bc32a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc32a-120">親要素</span><span class="sxs-lookup"><span data-stu-id="bc32a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bc32a-121">要素</span><span class="sxs-lookup"><span data-stu-id="bc32a-121">Element</span></span>|<span data-ttu-id="bc32a-122">説明</span><span class="sxs-lookup"><span data-stu-id="bc32a-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bc32a-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="bc32a-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bc32a-124">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc32a-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc32a-125">解説</span><span class="sxs-lookup"><span data-stu-id="bc32a-125">Remarks</span></span>  

 <span data-ttu-id="bc32a-126">.NET Framework 4 より前の .NET Framework のバージョンでは、読み込まれた PerfCounter.dll のバージョンは、プロセスに読み込まれたランタイムにこれされています。</span><span class="sxs-lookup"><span data-stu-id="bc32a-126">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="bc32a-127">コンピューターに .NET Framework バージョン1.1 と .NET Framework 2.0 の両方がインストールされている場合、.NET Framework 1.1 アプリケーションは .NET Framework 1.1 バージョンの PerfCounter.dll を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="bc32a-127">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="bc32a-128">.NET Framework 4 以降では、インストールされている PerfCounter.dll の最新バージョンが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="bc32a-128">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="bc32a-129">これは、コンピューターに .NET Framework 4 がインストールされている場合に、.NET Framework 1.1 アプリケーションによって .NET Framework 4 バージョンの PerfCounter.dll が読み込まれることを意味します。</span><span class="sxs-lookup"><span data-stu-id="bc32a-129">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="bc32a-130">.NET Framework 4 以降では、パフォーマンスカウンターを使用する場合、PerfCounter.dll は各プロバイダーの [カテゴリオプション] レジストリエントリを確認して、カテゴリ固有の共有メモリまたはグローバル共有メモリから読み取るかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="bc32a-130">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="bc32a-131">.NET Framework 1.1 PerfCounter.dll は、カテゴリ固有の共有メモリを認識しないため、そのレジストリエントリを読み取りません。常に、グローバルな共有メモリから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="bc32a-131">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="bc32a-132">旧バージョンとの互換性のために、.NET Framework 4 PerfCounter.dll は .NET Framework 1.1 アプリケーションで実行されているときに、カテゴリオプションのレジストリエントリをチェックしません。</span><span class="sxs-lookup"><span data-stu-id="bc32a-132">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="bc32a-133">.NET Framework 1.1 PerfCounter.dll と同様に、グローバルな共有メモリを使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="bc32a-133">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="bc32a-134">ただし、要素を有効にすることで、レジストリ設定を確認するように .NET Framework 4 PerfCounter.dll に指示でき `<forcePerformanceCounterUniqueSharedMemoryReads>` ます。</span><span class="sxs-lookup"><span data-stu-id="bc32a-134">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc32a-135">要素を有効 `<forcePerformanceCounterUniqueSharedMemoryReads>` にしても、カテゴリ固有の共有メモリが使用されることは保証されません。</span><span class="sxs-lookup"><span data-stu-id="bc32a-135">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="bc32a-136">を有効に設定する `true` と、PerfCounter.dll がカテゴリオプションのレジストリ設定を参照するだけになります。</span><span class="sxs-lookup"><span data-stu-id="bc32a-136">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="bc32a-137">カテゴリのオプションの既定の設定では、カテゴリ固有の共有メモリを使用します。ただし、カテゴリのオプションを変更して、グローバルな共有メモリを使用する必要があることを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="bc32a-137">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="bc32a-138">[カテゴリオプション] の設定を含むレジストリキーは、<の HKEY_LOCAL_MACHINE\System\CurrentControlSet\Servicesの \\ 区分 \> \ パフォーマンスです。</span><span class="sxs-lookup"><span data-stu-id="bc32a-138">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="bc32a-139">既定では、カテゴリのオプションは3に設定されています。これは、PerfCounter.dll がカテゴリ固有の共有メモリを使用するように指示します。</span><span class="sxs-lookup"><span data-stu-id="bc32a-139">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="bc32a-140">[カテゴリ] オプションが0に設定されている場合、PerfCounter.dll はグローバル共有メモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc32a-140">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="bc32a-141">インスタンスデータが再利用されるのは、作成されるインスタンスの名前が再利用されるインスタンスと同一である場合だけです。</span><span class="sxs-lookup"><span data-stu-id="bc32a-141">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="bc32a-142">すべてのバージョンがカテゴリに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bc32a-142">All versions will be able to write to the category.</span></span> <span data-ttu-id="bc32a-143">Category オプションが1に設定されている場合、グローバル共有メモリが使用されますが、カテゴリ名が再利用されるカテゴリと同じ長さの場合は、インスタンスデータを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="bc32a-143">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="bc32a-144">設定0および1を使用すると、メモリリークが発生し、パフォーマンスカウンターのメモリがいっぱいになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bc32a-144">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc32a-145">例</span><span class="sxs-lookup"><span data-stu-id="bc32a-145">Example</span></span>  

 <span data-ttu-id="bc32a-146">次の例は、カテゴリ固有の共有メモリを使用する必要があるかどうかを判断するために、PerfCounter.dll が category Options レジストリエントリを参照するように指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc32a-146">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc32a-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc32a-147">See also</span></span>

- [<span data-ttu-id="bc32a-148">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bc32a-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bc32a-149">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="bc32a-149">Configuration File Schema</span></span>](../index.md)
