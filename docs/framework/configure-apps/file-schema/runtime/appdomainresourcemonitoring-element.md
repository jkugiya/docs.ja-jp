---
description: '詳細情報: <appDomainResourceMonitoring> 要素'
title: <appDomainResourceMonitoring> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: aee85386e6d0af2ca4fd30c0ad8fe69bae240315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719293"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="3a969-103">\<appDomainResourceMonitoring> 要素</span><span class="sxs-lookup"><span data-stu-id="3a969-103">\<appDomainResourceMonitoring> Element</span></span>

<span data-ttu-id="3a969-104">プロセスのライフサイクルにおいて、プロセスのすべてのアプリケーション ドメインの統計を収集するようにランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="3a969-104">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="3a969-105">構文</span><span class="sxs-lookup"><span data-stu-id="3a969-105">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a969-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3a969-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3a969-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3a969-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a969-108">属性</span><span class="sxs-lookup"><span data-stu-id="3a969-108">Attributes</span></span>  
  
|<span data-ttu-id="3a969-109">属性</span><span class="sxs-lookup"><span data-stu-id="3a969-109">Attribute</span></span>|<span data-ttu-id="3a969-110">説明</span><span class="sxs-lookup"><span data-stu-id="3a969-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3a969-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3a969-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="3a969-112">アプリケーションドメインのリソース監視の統計情報をランタイムが収集するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a969-112">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3a969-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="3a969-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="3a969-114">値</span><span class="sxs-lookup"><span data-stu-id="3a969-114">Value</span></span>|<span data-ttu-id="3a969-115">説明</span><span class="sxs-lookup"><span data-stu-id="3a969-115">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="3a969-116">アプリケーションドメインのリソース監視の統計情報が収集されます。</span><span class="sxs-lookup"><span data-stu-id="3a969-116">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="3a969-117">アプリケーションドメインのリソース監視の統計情報は収集されません。</span><span class="sxs-lookup"><span data-stu-id="3a969-117">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a969-118">子要素</span><span class="sxs-lookup"><span data-stu-id="3a969-118">Child Elements</span></span>  

 <span data-ttu-id="3a969-119">なし。</span><span class="sxs-lookup"><span data-stu-id="3a969-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a969-120">親要素</span><span class="sxs-lookup"><span data-stu-id="3a969-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3a969-121">要素</span><span class="sxs-lookup"><span data-stu-id="3a969-121">Element</span></span>|<span data-ttu-id="3a969-122">説明</span><span class="sxs-lookup"><span data-stu-id="3a969-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3a969-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3a969-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3a969-124">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a969-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a969-125">解説</span><span class="sxs-lookup"><span data-stu-id="3a969-125">Remarks</span></span>  

 <span data-ttu-id="3a969-126">アプリケーションドメインのリソース監視は、マネージアプリケーションドメインクラス、ホスティング [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) インターフェイス、および Windows イベントトレーシング (ETW) を介して使用できます。</span><span class="sxs-lookup"><span data-stu-id="3a969-126">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="3a969-127">監視が有効になっている場合、プロセス内のすべてのアプリケーションドメインについて、プロセスの実行中に統計が収集されます。</span><span class="sxs-lookup"><span data-stu-id="3a969-127">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="3a969-128">マネージコードからの監視を有効にするには、プロパティを使用し <xref:System.AppDomain.MonitoringIsEnabled%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="3a969-128">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="3a969-129">この構成要素は、.NET Framework 4 以降でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3a969-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a969-130">例</span><span class="sxs-lookup"><span data-stu-id="3a969-130">Example</span></span>  

 <span data-ttu-id="3a969-131">次の例は、アプリケーションドメインのリソース監視を有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3a969-131">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a969-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a969-132">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3a969-133">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="3a969-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3a969-134">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="3a969-134">Configuration File Schema</span></span>](../index.md)
