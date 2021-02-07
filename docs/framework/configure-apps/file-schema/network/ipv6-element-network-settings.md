---
description: '詳細情報: <ipv6> 要素 (ネットワーク設定)'
title: <ipv6> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: 667acaebdb290140f67ea36020bb191cd1a44f34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698649"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="eb5bf-103">\<ipv6> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="eb5bf-103">\<ipv6> Element (Network Settings)</span></span>

<span data-ttu-id="eb5bf-104">クラスの互換性のために残されているメンバーからのインターネットプロトコルバージョン 6 (IPv6) 応答を有効に <xref:System.Net.Dns> します。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-104">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="eb5bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb5bf-105">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb5bf-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="eb5bf-106">Attributes and Elements</span></span>  

 <span data-ttu-id="eb5bf-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb5bf-108">属性</span><span class="sxs-lookup"><span data-stu-id="eb5bf-108">Attributes</span></span>  
  
|<span data-ttu-id="eb5bf-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="eb5bf-109">**Attribute**</span></span>|<span data-ttu-id="eb5bf-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="eb5bf-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="eb5bf-111">クラスのメンバーが <xref:System.Net.Dns> インターネットプロトコルバージョン 6 (IPv6) アドレスを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-111">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="eb5bf-112">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb5bf-113">子要素</span><span class="sxs-lookup"><span data-stu-id="eb5bf-113">Child Elements</span></span>  

 <span data-ttu-id="eb5bf-114">なし。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb5bf-115">親要素</span><span class="sxs-lookup"><span data-stu-id="eb5bf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="eb5bf-116">**要素**</span><span class="sxs-lookup"><span data-stu-id="eb5bf-116">**Element**</span></span>|<span data-ttu-id="eb5bf-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="eb5bf-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eb5bf-118">設定</span><span class="sxs-lookup"><span data-stu-id="eb5bf-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="eb5bf-119"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb5bf-120">解説</span><span class="sxs-lookup"><span data-stu-id="eb5bf-120">Remarks</span></span>  

 <span data-ttu-id="eb5bf-121">この設定により、クラスの廃止されたメンバー (、、、、、 <xref:System.Net.Dns> <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Net.Dns.BeginResolve%2A> <xref:System.Net.Dns.EndGetHostByName%2A> <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.GetHostByName%2A> 、および <xref:System.Net.Dns.Resolve%2A> ) の IPv6 サポートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-121">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="eb5bf-122">名前空間のその他のメンバーについては <xref:System.Net?displayProperty=nameWithType> 、オペレーティングシステムで ipv6 が有効になっている場合、ipv6 アドレスが返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-122">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eb5bf-123">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="eb5bf-123">Configuration Files</span></span>  

 <span data-ttu-id="eb5bf-124">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb5bf-125">例</span><span class="sxs-lookup"><span data-stu-id="eb5bf-125">Example</span></span>  

 <span data-ttu-id="eb5bf-126">次の例では、クラスの IPv6 サポートを有効にする方法を示し <xref:System.Net.Dns> ます。</span><span class="sxs-lookup"><span data-stu-id="eb5bf-126">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb5bf-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb5bf-127">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="eb5bf-128">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="eb5bf-128">Network Settings Schema</span></span>](index.md)
