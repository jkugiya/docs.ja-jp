---
description: '詳細情報: <settings> 要素 (ネットワーク設定)'
title: <settings> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: e6ed242e68ac9a9e2c20067d66681bbcd51fcc50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712975"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="974d0-103">\<settings> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="974d0-103">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="974d0-104"><xref:System.Net?displayProperty=nameWithType> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="974d0-104">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="974d0-105">構文</span><span class="sxs-lookup"><span data-stu-id="974d0-105">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="974d0-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="974d0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="974d0-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="974d0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="974d0-108">属性</span><span class="sxs-lookup"><span data-stu-id="974d0-108">Attributes</span></span>  

 <span data-ttu-id="974d0-109">なし。</span><span class="sxs-lookup"><span data-stu-id="974d0-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="974d0-110">子要素</span><span class="sxs-lookup"><span data-stu-id="974d0-110">Child Elements</span></span>  
  
|<span data-ttu-id="974d0-111">要素</span><span class="sxs-lookup"><span data-stu-id="974d0-111">Element</span></span>|<span data-ttu-id="974d0-112">説明</span><span class="sxs-lookup"><span data-stu-id="974d0-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="974d0-113">httpListener</span><span class="sxs-lookup"><span data-stu-id="974d0-113">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="974d0-114">クラスによって使用されるパラメーターをカスタマイズ <xref:System.Net.HttpListener> します。</span><span class="sxs-lookup"><span data-stu-id="974d0-114">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="974d0-115">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="974d0-115">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="974d0-116">Web 要求パラメーターをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="974d0-116">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="974d0-117">ipv6</span><span class="sxs-lookup"><span data-stu-id="974d0-117">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="974d0-118">インターネットプロトコルバージョン 6 (IPv6) のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="974d0-118">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="974d0-119">\<performanceCounter> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="974d0-119">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="974d0-120">ネットワークパフォーマンスカウンターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="974d0-120">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="974d0-121">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="974d0-121">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="974d0-122">ネットワークリソースへの接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="974d0-122">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="974d0-123">socket</span><span class="sxs-lookup"><span data-stu-id="974d0-123">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="974d0-124">ソケット操作が完了ポートを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="974d0-124">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="974d0-125">\<webProxyScript> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="974d0-125">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="974d0-126">Web プロキシを検出するために使用するスクリプトの特性を構成します。</span><span class="sxs-lookup"><span data-stu-id="974d0-126">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="974d0-127">親要素</span><span class="sxs-lookup"><span data-stu-id="974d0-127">Parent Elements</span></span>  
  
|<span data-ttu-id="974d0-128">要素</span><span class="sxs-lookup"><span data-stu-id="974d0-128">Element</span></span>|<span data-ttu-id="974d0-129">説明</span><span class="sxs-lookup"><span data-stu-id="974d0-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="974d0-130">system.net</span><span class="sxs-lookup"><span data-stu-id="974d0-130">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="974d0-131">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="974d0-131">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="974d0-132">解説</span><span class="sxs-lookup"><span data-stu-id="974d0-132">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="974d0-133">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="974d0-133">Configuration Files</span></span>  

 <span data-ttu-id="974d0-134">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="974d0-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974d0-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="974d0-135">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="974d0-136">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="974d0-136">Network Settings Schema</span></span>](index.md)
