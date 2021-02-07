---
description: '詳細情報: <add> connectionManagement の要素 (ネットワーク設定)'
title: connectionManagement の <add> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 646d9fcfb73cfd8f4f533672c1a92883274f6e39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729941"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="9d8fa-103">connectionManagement の \<add> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="9d8fa-103">\<add> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="9d8fa-104">IP アドレスまたは DNS 名を接続管理リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-104">Adds an IP address or DNS name to the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="9d8fa-105">構文</span><span class="sxs-lookup"><span data-stu-id="9d8fa-105">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d8fa-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9d8fa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9d8fa-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d8fa-108">属性</span><span class="sxs-lookup"><span data-stu-id="9d8fa-108">Attributes</span></span>  
  
|<span data-ttu-id="9d8fa-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="9d8fa-109">**Attribute**</span></span>|<span data-ttu-id="9d8fa-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="9d8fa-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="9d8fa-111">IP アドレスまたは DNS 名を記述する文字列。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-111">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="9d8fa-112">サーバーに対して許可される接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-112">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="9d8fa-113">値が指定されていない場合、既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-113">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d8fa-114">子要素</span><span class="sxs-lookup"><span data-stu-id="9d8fa-114">Child Elements</span></span>  

 <span data-ttu-id="9d8fa-115">なし。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d8fa-116">親要素</span><span class="sxs-lookup"><span data-stu-id="9d8fa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9d8fa-117">**要素**</span><span class="sxs-lookup"><span data-stu-id="9d8fa-117">**Element**</span></span>|<span data-ttu-id="9d8fa-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="9d8fa-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9d8fa-119">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="9d8fa-119">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="9d8fa-120">ネットワーク ホストへの接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-120">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d8fa-121">解説</span><span class="sxs-lookup"><span data-stu-id="9d8fa-121">Remarks</span></span>  

 <span data-ttu-id="9d8fa-122">`address` 属性の値は、すべての接続を示すアスタリスク、または形式が `<schema>://<idn_hostname>[:<port>]` の文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-122">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="9d8fa-123">HTTP API に渡される URI に Unicode が含まれる場合、punicode 文字列を返す可能性がある <xref:System.Uri.DnsSafeHost%2A> を使用して名前が内部的に変換されます (動作は現行 IDN 構成によって異なる)。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-123">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9d8fa-124">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="9d8fa-124">Configuration Files</span></span>  

 <span data-ttu-id="9d8fa-125">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d8fa-126">例</span><span class="sxs-lookup"><span data-stu-id="9d8fa-126">Example</span></span>  

 <span data-ttu-id="9d8fa-127">次の例では、サーバーへの4つの接続 `www.contoso.com` と、他のすべてのサーバーへの2つの接続を使用するようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="9d8fa-127">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d8fa-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d8fa-128">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="9d8fa-129">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="9d8fa-129">Network Settings Schema</span></span>](index.md)
