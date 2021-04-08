---
title: <bypasslist> 要素 (ネットワーク設定)
description: <bypasslist> ネットワーク設定要素は、.NET Framework 内のプロキシを使用しないアドレスを記述する一連の正規表現を提供します。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 0a03b391c839b7255fdd423a305d474d0e48ad39
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259357"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="cc6ae-103">\<bypasslist> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="cc6ae-103">\<bypasslist> Element (Network Settings)</span></span>

<span data-ttu-id="cc6ae-104">プロキシを使用しないアドレスを記述する一連の正規表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-104">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="cc6ae-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc6ae-105">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc6ae-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cc6ae-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cc6ae-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc6ae-108">属性</span><span class="sxs-lookup"><span data-stu-id="cc6ae-108">Attributes</span></span>  

 <span data-ttu-id="cc6ae-109">なし。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cc6ae-110">子要素</span><span class="sxs-lookup"><span data-stu-id="cc6ae-110">Child Elements</span></span>  
  
|<span data-ttu-id="cc6ae-111">**要素**</span><span class="sxs-lookup"><span data-stu-id="cc6ae-111">**Element**</span></span>|<span data-ttu-id="cc6ae-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="cc6ae-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cc6ae-113">add</span><span class="sxs-lookup"><span data-stu-id="cc6ae-113">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="cc6ae-114">プロキシ バイパス リストに IP アドレスまたは DNS 名を追加します。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-114">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="cc6ae-115">オフ</span><span class="sxs-lookup"><span data-stu-id="cc6ae-115">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="cc6ae-116">バイパス リストをクリアします。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-116">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="cc6ae-117">remove</span><span class="sxs-lookup"><span data-stu-id="cc6ae-117">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="cc6ae-118">プロキシ バイパス リストから IP アドレスまたは DNS 名を削除します。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-118">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc6ae-119">親要素</span><span class="sxs-lookup"><span data-stu-id="cc6ae-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cc6ae-120">**要素**</span><span class="sxs-lookup"><span data-stu-id="cc6ae-120">**Element**</span></span>|<span data-ttu-id="cc6ae-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="cc6ae-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cc6ae-122">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="cc6ae-122">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="cc6ae-123">ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-123">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc6ae-124">解説</span><span class="sxs-lookup"><span data-stu-id="cc6ae-124">Remarks</span></span>  

 <span data-ttu-id="cc6ae-125">バイパス リストには、<xref:System.Net.WebRequest> インスタンスがプロキシ サーバーを経由せずに直接アクセスする URI を記述する正規表現が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-125">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="cc6ae-126">この要素に対して正規表現を指定するときには、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-126">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="cc6ae-127">正規表現 `[a-z]+\\.contoso\\.com` は contoso.com ドメイン内の任意のホストと一致しますが、contoso.com.cpandl.com ドメイン内の任意のホストとも一致します。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-127">The regular expression `[a-z]+\\.contoso\\.com` matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="cc6ae-128">contoso.com ドメイン内のホストにのみ一致させるには、アンカー (`$`): `[a-z]+\\.contoso\\.com$` を使用します。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-128">To match only a host in the contoso.com domain, use an anchor (`$`): `[a-z]+\\.contoso\\.com$`.</span></span>
  
 <span data-ttu-id="cc6ae-129">正規表現の詳細については、「[.NET Framework の正規表現](../../../../standard/base-types/regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-129">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cc6ae-130">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="cc6ae-130">Configuration Files</span></span>  

 <span data-ttu-id="cc6ae-131">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc6ae-132">例</span><span class="sxs-lookup"><span data-stu-id="cc6ae-132">Example</span></span>  

 <span data-ttu-id="cc6ae-133">次の例では、バイパス リストに 2 つのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-133">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="cc6ae-134">1 つめは、contoso.com ドメイン内のすべてのサーバーのプロキシをバイパスします。2 つめは、IP アドレスが 192.168 で始まるすべてのアドレスのプロキシをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="cc6ae-134">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc6ae-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc6ae-135">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="cc6ae-136">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="cc6ae-136">Network Settings Schema</span></span>](index.md)
