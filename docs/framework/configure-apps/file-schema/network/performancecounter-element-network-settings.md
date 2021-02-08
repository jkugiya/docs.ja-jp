---
description: '詳細情報: <performanceCounters> 要素 (ネットワーク設定)'
title: <performanceCounters> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: a923ba2420bd15e33f4564a196854fdf9e130e12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804115"
---
# <a name="performancecounters-element-network-settings"></a><span data-ttu-id="04007-103">\<performanceCounters> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="04007-103">\<performanceCounters> Element (Network Settings)</span></span>

<span data-ttu-id="04007-104">ネットワークパフォーマンスカウンターを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="04007-104">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="04007-105">構文</span><span class="sxs-lookup"><span data-stu-id="04007-105">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04007-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="04007-106">Attributes and Elements</span></span>  

 <span data-ttu-id="04007-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="04007-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04007-108">属性</span><span class="sxs-lookup"><span data-stu-id="04007-108">Attributes</span></span>  
  
|<span data-ttu-id="04007-109">属性</span><span class="sxs-lookup"><span data-stu-id="04007-109">Attribute</span></span>|<span data-ttu-id="04007-110">説明</span><span class="sxs-lookup"><span data-stu-id="04007-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="04007-111">ネットワークパフォーマンスカウンターを有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="04007-111">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="04007-112">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="04007-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04007-113">子要素</span><span class="sxs-lookup"><span data-stu-id="04007-113">Child Elements</span></span>  

 <span data-ttu-id="04007-114">なし。</span><span class="sxs-lookup"><span data-stu-id="04007-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04007-115">親要素</span><span class="sxs-lookup"><span data-stu-id="04007-115">Parent Elements</span></span>  
  
|<span data-ttu-id="04007-116">要素</span><span class="sxs-lookup"><span data-stu-id="04007-116">Element</span></span>|<span data-ttu-id="04007-117">説明</span><span class="sxs-lookup"><span data-stu-id="04007-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04007-118">設定</span><span class="sxs-lookup"><span data-stu-id="04007-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="04007-119"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="04007-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04007-120">解説</span><span class="sxs-lookup"><span data-stu-id="04007-120">Remarks</span></span>  

 <span data-ttu-id="04007-121">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="04007-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="04007-122">ネットワーク パフォーマンス カウンターは、使用される構成ファイルで有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="04007-122">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="04007-123">すべてのネットワーク パフォーマンス カウンターは、構成ファイル内の 1 つの設定で有効または無効にされます。</span><span class="sxs-lookup"><span data-stu-id="04007-123">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="04007-124">ネットワーク パフォーマンス カウンターを個別に有効または無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="04007-124">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="04007-125">特定のネットワークパフォーマンスカウンターの詳細については、「 [ネットワークパフォーマンスカウンター](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04007-125">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="04007-126">既定値は、ネットワークパフォーマンスカウンターが無効になっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="04007-126">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="04007-127">プロパティは、 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> 適用可能 **な** 構成ファイルから enabled 属性の現在の値を取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="04007-127">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04007-128">例</span><span class="sxs-lookup"><span data-stu-id="04007-128">Example</span></span>  

 <span data-ttu-id="04007-129">次の例では、および関連する名前空間を構成して、ネットワークパフォーマンスカウンターを有効にする方法を示し <xref:System.Net> ます。</span><span class="sxs-lookup"><span data-stu-id="04007-129">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04007-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="04007-130">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="04007-131">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="04007-131">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="04007-132">ネットワークパフォーマンスカウンター</span><span class="sxs-lookup"><span data-stu-id="04007-132">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
