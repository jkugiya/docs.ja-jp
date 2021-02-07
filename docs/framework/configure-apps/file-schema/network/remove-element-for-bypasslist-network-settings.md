---
description: '詳細情報: <remove> bypasslist の要素 (ネットワーク設定)'
title: bypasslist の <remove> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 48441f1b402b339a1bd2ea069678afb4b1d5f2e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740289"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="31704-103">bypasslist の \<remove> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="31704-103">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="31704-104">プロキシバイパスリストから IP アドレスまたは DNS 名を削除します。</span><span class="sxs-lookup"><span data-stu-id="31704-104">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="31704-105">構文</span><span class="sxs-lookup"><span data-stu-id="31704-105">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31704-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="31704-106">Attributes and Elements</span></span>

<span data-ttu-id="31704-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="31704-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="31704-108">属性</span><span class="sxs-lookup"><span data-stu-id="31704-108">Attributes</span></span>

|<span data-ttu-id="31704-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="31704-109">**Attribute**</span></span>|<span data-ttu-id="31704-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="31704-110">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="31704-111">IP アドレスまたは DNS 名を記述する正規表現。</span><span class="sxs-lookup"><span data-stu-id="31704-111">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="31704-112">子要素</span><span class="sxs-lookup"><span data-stu-id="31704-112">Child Elements</span></span>

<span data-ttu-id="31704-113">なし。</span><span class="sxs-lookup"><span data-stu-id="31704-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31704-114">親要素</span><span class="sxs-lookup"><span data-stu-id="31704-114">Parent Elements</span></span>

|<span data-ttu-id="31704-115">**要素**</span><span class="sxs-lookup"><span data-stu-id="31704-115">**Element**</span></span>|<span data-ttu-id="31704-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="31704-116">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="31704-117">bypasslist</span><span class="sxs-lookup"><span data-stu-id="31704-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="31704-118">プロキシを使用しないアドレスを記述する一連の正規表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="31704-118">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="31704-119">解説</span><span class="sxs-lookup"><span data-stu-id="31704-119">Remarks</span></span>

<span data-ttu-id="31704-120">要素は、 `remove` プロキシサーバーをバイパスするアドレスの一覧から、IP アドレスまたは DNS サーバー名を記述する正規表現を削除します。</span><span class="sxs-lookup"><span data-stu-id="31704-120">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="31704-121">これらのアドレスは、構成ファイルで既に定義されているか、構成階層の上位レベルに定義されています。</span><span class="sxs-lookup"><span data-stu-id="31704-121">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="31704-122">属性の値は、 `address` 一連の IP アドレスまたはホスト名を表す正規表現である必要があります。</span><span class="sxs-lookup"><span data-stu-id="31704-122">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="31704-123">正規表現の詳細については、「」を参照してください。[正規表現を .NET Framework](../../../../standard/base-types/regular-expressions.md)します。</span><span class="sxs-lookup"><span data-stu-id="31704-123">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="31704-124">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="31704-124">Configuration Files</span></span>

<span data-ttu-id="31704-125">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="31704-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="31704-126">例</span><span class="sxs-lookup"><span data-stu-id="31704-126">Example</span></span>

<span data-ttu-id="31704-127">次の例では、adventure-works.com ドメインの以前の定義を削除し、contoso.com ドメインをバイパスリストに追加します。</span><span class="sxs-lookup"><span data-stu-id="31704-127">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="31704-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="31704-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="31704-129">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="31704-129">Network Settings Schema</span></span>](index.md)
