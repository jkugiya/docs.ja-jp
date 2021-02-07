---
description: '詳細情報: <clear> bypasslist の要素 (ネットワーク設定)'
title: bypasslist の <clear> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 4ddb66c837c55391a19826c44c6df7a3e88c8e0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729901"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="f2a9e-103">bypasslist の \<clear> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="f2a9e-103">\<clear> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="f2a9e-104">プロキシバイパスリストをクリアします。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-104">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="f2a9e-105">構文</span><span class="sxs-lookup"><span data-stu-id="f2a9e-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2a9e-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f2a9e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f2a9e-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2a9e-108">属性</span><span class="sxs-lookup"><span data-stu-id="f2a9e-108">Attributes</span></span>  

 <span data-ttu-id="f2a9e-109">なし。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2a9e-110">子要素</span><span class="sxs-lookup"><span data-stu-id="f2a9e-110">Child Elements</span></span>  

 <span data-ttu-id="f2a9e-111">なし。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2a9e-112">親要素</span><span class="sxs-lookup"><span data-stu-id="f2a9e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f2a9e-113">**要素**</span><span class="sxs-lookup"><span data-stu-id="f2a9e-113">**Element**</span></span>|<span data-ttu-id="f2a9e-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="f2a9e-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f2a9e-115">bypasslist</span><span class="sxs-lookup"><span data-stu-id="f2a9e-115">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="f2a9e-116">プロキシを使用しないアドレスを記述する一連の正規表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-116">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2a9e-117">解説</span><span class="sxs-lookup"><span data-stu-id="f2a9e-117">Remarks</span></span>  

 <span data-ttu-id="f2a9e-118">要素は、 `clear` バイパスリストからすべてのエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-118">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f2a9e-119">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="f2a9e-119">Configuration Files</span></span>  

 <span data-ttu-id="f2a9e-120">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2a9e-121">例</span><span class="sxs-lookup"><span data-stu-id="f2a9e-121">Example</span></span>  

 <span data-ttu-id="f2a9e-122">次の例では、バイパスリストをクリアし、2つのアドレスをバイパスリストに追加します。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-122">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="f2a9e-123">最初のは、contoso.com ドメイン内のすべてのサーバーのプロキシをバイパスします。2つ目は、IP アドレスが192.168 で始まるすべてのサーバーのプロキシをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="f2a9e-123">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="f2a9e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2a9e-124">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f2a9e-125">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="f2a9e-125">Network Settings Schema</span></span>](index.md)
