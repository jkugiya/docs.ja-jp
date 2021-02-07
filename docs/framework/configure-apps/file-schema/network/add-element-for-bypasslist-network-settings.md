---
description: '詳細情報: <add> bypasslist の要素 (ネットワーク設定)'
title: bypasslist の <add> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 6bbd42cdf5d3b9bc31326b619cde96cfac0c755a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698636"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="165ea-103">bypasslist の \<add> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="165ea-103">\<add> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="165ea-104">プロキシバイパス一覧に IP アドレスまたは DNS 名を追加します。</span><span class="sxs-lookup"><span data-stu-id="165ea-104">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="165ea-105">構文</span><span class="sxs-lookup"><span data-stu-id="165ea-105">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="165ea-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="165ea-106">Attributes and Elements</span></span>  

 <span data-ttu-id="165ea-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="165ea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="165ea-108">属性</span><span class="sxs-lookup"><span data-stu-id="165ea-108">Attributes</span></span>  
  
|<span data-ttu-id="165ea-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="165ea-109">**Attribute**</span></span>|<span data-ttu-id="165ea-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="165ea-110">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="165ea-111">**address**</span><span class="sxs-lookup"><span data-stu-id="165ea-111">**address**</span></span>|<span data-ttu-id="165ea-112">IP アドレスまたは DNS 名を記述する正規表現。</span><span class="sxs-lookup"><span data-stu-id="165ea-112">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="165ea-113">子要素</span><span class="sxs-lookup"><span data-stu-id="165ea-113">Child Elements</span></span>  

 <span data-ttu-id="165ea-114">なし。</span><span class="sxs-lookup"><span data-stu-id="165ea-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="165ea-115">親要素</span><span class="sxs-lookup"><span data-stu-id="165ea-115">Parent Elements</span></span>  
  
|<span data-ttu-id="165ea-116">**要素**</span><span class="sxs-lookup"><span data-stu-id="165ea-116">**Element**</span></span>|<span data-ttu-id="165ea-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="165ea-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="165ea-118">bypasslist</span><span class="sxs-lookup"><span data-stu-id="165ea-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="165ea-119">プロキシを使用しないアドレスを記述する一連の正規表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="165ea-119">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="165ea-120">解説</span><span class="sxs-lookup"><span data-stu-id="165ea-120">Remarks</span></span>  

 <span data-ttu-id="165ea-121">要素は、 `add` IP アドレスまたは DNS サーバー名を記述する正規表現を、プロキシサーバーをバイパスするアドレスの一覧に挿入します。</span><span class="sxs-lookup"><span data-stu-id="165ea-121">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="165ea-122">属性の値は、 `address` 一連の IP アドレスまたはホスト名を表す正規表現である必要があります。</span><span class="sxs-lookup"><span data-stu-id="165ea-122">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="165ea-123">この要素に正規表現を指定する場合は、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="165ea-123">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="165ea-124">正規表現 "[a-z] + \\ . contoso \\ .com" は、contoso.com ドメイン内の任意のホストと一致しますが、contoso.com.cpandl.com ドメイン内の任意のホストとも一致します。</span><span class="sxs-lookup"><span data-stu-id="165ea-124">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="165ea-125">Contoso.com ドメイン内のホストのみを一致させるには、アンカー ("$"): "[a-z] + \\ . contoso \\ .com $" を使用します。</span><span class="sxs-lookup"><span data-stu-id="165ea-125">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="165ea-126">正規表現の詳細については、「」を参照してください。[正規表現を .NET Framework](../../../../standard/base-types/regular-expressions.md)します。</span><span class="sxs-lookup"><span data-stu-id="165ea-126">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="165ea-127">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="165ea-127">Configuration Files</span></span>  

 <span data-ttu-id="165ea-128">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="165ea-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="165ea-129">例</span><span class="sxs-lookup"><span data-stu-id="165ea-129">Example</span></span>  

 <span data-ttu-id="165ea-130">次の例では、バイパスリストに2つのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="165ea-130">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="165ea-131">最初のは、contoso.com ドメイン内のすべてのサーバーのプロキシをバイパスします。2つ目は、IP アドレスが192.168 で始まるすべてのサーバーのプロキシをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="165ea-131">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="165ea-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="165ea-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="165ea-133">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="165ea-133">Network Settings Schema</span></span>](index.md)
