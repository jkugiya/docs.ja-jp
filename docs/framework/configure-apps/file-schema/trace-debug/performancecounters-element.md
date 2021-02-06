---
description: '詳細情報: <performanceCounters> 要素'
title: <performanceCounters> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: 3a9a6c42575be3fc7fb5c5d80ffecd940894e164
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639576"
---
# <a name="performancecounters-element"></a><span data-ttu-id="0e0eb-103">\<performanceCounters> 要素</span><span class="sxs-lookup"><span data-stu-id="0e0eb-103">\<performanceCounters> Element</span></span>

<span data-ttu-id="0e0eb-104">パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-104">Specifies the size of the global memory shared by performance counters.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a><span data-ttu-id="0e0eb-105">構文</span><span class="sxs-lookup"><span data-stu-id="0e0eb-105">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e0eb-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0e0eb-106">Attributes and Elements</span></span>

<span data-ttu-id="0e0eb-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e0eb-108">属性</span><span class="sxs-lookup"><span data-stu-id="0e0eb-108">Attributes</span></span>

|<span data-ttu-id="0e0eb-109">属性</span><span class="sxs-lookup"><span data-stu-id="0e0eb-109">Attribute</span></span>|<span data-ttu-id="0e0eb-110">説明</span><span class="sxs-lookup"><span data-stu-id="0e0eb-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="0e0eb-111">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="0e0eb-111">filemappingsize</span></span>|<span data-ttu-id="0e0eb-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="0e0eb-113">パフォーマンス カウンターが共有するグローバル メモリのサイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-113">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="0e0eb-114">既定値は 524288 です。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-114">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0e0eb-115">子要素</span><span class="sxs-lookup"><span data-stu-id="0e0eb-115">Child Elements</span></span>

<span data-ttu-id="0e0eb-116">なし。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0e0eb-117">親要素</span><span class="sxs-lookup"><span data-stu-id="0e0eb-117">Parent Elements</span></span>

|<span data-ttu-id="0e0eb-118">要素</span><span class="sxs-lookup"><span data-stu-id="0e0eb-118">Element</span></span>|<span data-ttu-id="0e0eb-119">説明</span><span class="sxs-lookup"><span data-stu-id="0e0eb-119">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="0e0eb-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="0e0eb-121">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-121">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0e0eb-122">解説</span><span class="sxs-lookup"><span data-stu-id="0e0eb-122">Remarks</span></span>

<span data-ttu-id="0e0eb-123">パフォーマンスカウンターは、メモリマップトファイルまたは共有メモリを使用して、パフォーマンスデータをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-123">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="0e0eb-124">共有メモリのサイズによって、一度に使用できるインスタンスの数が決まります。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-124">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="0e0eb-125">共有メモリには、グローバル共有メモリと個別の共有メモリの2種類があります。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-125">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="0e0eb-126">グローバル共有メモリは、.NET Framework バージョン1.0 または1.1 と共にインストールされたすべてのパフォーマンスカウンターカテゴリによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-126">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="0e0eb-127">.NET Framework バージョン2.0 と共にインストールされるパフォーマンスカウンターカテゴリには、個別の共有メモリが使用されます。各パフォーマンスカウンターカテゴリには独自のメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-127">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="0e0eb-128">グローバル共有メモリのサイズは、構成ファイルでのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-128">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="0e0eb-129">既定のサイズは 524288 byes、最大サイズは33554432バイト、最小サイズは32768バイトです。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-129">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="0e0eb-130">グローバル共有メモリはすべてのプロセスとカテゴリによって共有されるため、最初の作成者はサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-130">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="0e0eb-131">アプリケーション構成ファイルでサイズを定義する場合、そのサイズは、アプリケーションがパフォーマンスカウンターを実行する最初のアプリケーションである場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-131">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="0e0eb-132">そのため、値を指定する正しい場所 `filemappingsize` は Machine.config ファイルです。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-132">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="0e0eb-133">グローバル共有メモリ内のメモリは、個々のパフォーマンスカウンターによって解放されることはないため、異なる名前を持つ多数のパフォーマンスカウンターインスタンスが作成されると、最終的にグローバル共有メモリが使い果たされます。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-133">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="0e0eb-134">個別の共有メモリのサイズについては、レジストリキー HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Performance の DWORD FileMappingSize 値 \\ *\<category name>* が最初に参照され、次に構成ファイル内のグローバル共有メモリに指定された値が続きます。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-134">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="0e0eb-135">[FileMappingSize] の値が存在しない場合は、構成ファイルのグローバル設定の1つ目の共有メモリサイズが4番目 (1/4) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0e0eb-135">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e0eb-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e0eb-136">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
