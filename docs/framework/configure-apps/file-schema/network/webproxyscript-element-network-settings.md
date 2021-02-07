---
description: '詳細情報: <webProxyScript> 要素 (ネットワーク設定)'
title: <webProxyScript> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 1627b6650582202f3f1a4c1fdebf2d183e4a894b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740107"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="cd3c6-103">\<webProxyScript> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="cd3c6-103">\<webProxyScript> Element (Network Settings)</span></span>

<span data-ttu-id="cd3c6-104">Web プロキシを検出するために使用するスクリプトの特性を構成します。</span><span class="sxs-lookup"><span data-stu-id="cd3c6-104">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="cd3c6-105">構文</span><span class="sxs-lookup"><span data-stu-id="cd3c6-105">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd3c6-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cd3c6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cd3c6-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd3c6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd3c6-108">属性</span><span class="sxs-lookup"><span data-stu-id="cd3c6-108">Attributes</span></span>  
  
|<span data-ttu-id="cd3c6-109">属性</span><span class="sxs-lookup"><span data-stu-id="cd3c6-109">Attribute</span></span>|<span data-ttu-id="cd3c6-110">説明</span><span class="sxs-lookup"><span data-stu-id="cd3c6-110">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="cd3c6-111">スクリプトをダウンロードする最長時間を、時間、分、および秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="cd3c6-111">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="cd3c6-112">既定値は1分です。</span><span class="sxs-lookup"><span data-stu-id="cd3c6-112">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd3c6-113">子要素</span><span class="sxs-lookup"><span data-stu-id="cd3c6-113">Child Elements</span></span>  

 <span data-ttu-id="cd3c6-114">なし。</span><span class="sxs-lookup"><span data-stu-id="cd3c6-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd3c6-115">親要素</span><span class="sxs-lookup"><span data-stu-id="cd3c6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="cd3c6-116">要素</span><span class="sxs-lookup"><span data-stu-id="cd3c6-116">Element</span></span>|<span data-ttu-id="cd3c6-117">説明</span><span class="sxs-lookup"><span data-stu-id="cd3c6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd3c6-118">設定</span><span class="sxs-lookup"><span data-stu-id="cd3c6-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="cd3c6-119"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="cd3c6-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd3c6-120">解説</span><span class="sxs-lookup"><span data-stu-id="cd3c6-120">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cd3c6-121">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="cd3c6-121">Configuration Files</span></span>  

 <span data-ttu-id="cd3c6-122">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="cd3c6-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3c6-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd3c6-123">See also</span></span>

- [<span data-ttu-id="cd3c6-124">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="cd3c6-124">Network Settings Schema</span></span>](index.md)
