---
description: '詳細情報: <remove> connectionManagement の要素 (ネットワーク設定)'
title: connectionManagement の <remove> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 98916846fb5de93ee93a7e25530e983cbd3719ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740250"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="d307b-103">connectionManagement の \<remove> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="d307b-103">\<remove> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="d307b-104">接続管理リストから IP アドレスまたは DNS 名を削除します。</span><span class="sxs-lookup"><span data-stu-id="d307b-104">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="d307b-105">構文</span><span class="sxs-lookup"><span data-stu-id="d307b-105">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d307b-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d307b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d307b-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d307b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d307b-108">属性</span><span class="sxs-lookup"><span data-stu-id="d307b-108">Attributes</span></span>  
  
|<span data-ttu-id="d307b-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="d307b-109">**Attribute**</span></span>|<span data-ttu-id="d307b-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="d307b-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="d307b-111">IP アドレスまたは DNS 名。</span><span class="sxs-lookup"><span data-stu-id="d307b-111">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d307b-112">子要素</span><span class="sxs-lookup"><span data-stu-id="d307b-112">Child Elements</span></span>  

 <span data-ttu-id="d307b-113">なし。</span><span class="sxs-lookup"><span data-stu-id="d307b-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d307b-114">親要素</span><span class="sxs-lookup"><span data-stu-id="d307b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d307b-115">**要素**</span><span class="sxs-lookup"><span data-stu-id="d307b-115">**Element**</span></span>|<span data-ttu-id="d307b-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="d307b-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d307b-117">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="d307b-117">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="d307b-118">ネットワーク ホストへの接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d307b-118">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d307b-119">解説</span><span class="sxs-lookup"><span data-stu-id="d307b-119">Remarks</span></span>  

 <span data-ttu-id="d307b-120">要素は、 `remove` 指定されたサーバーの接続管理リストのエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="d307b-120">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="d307b-121">属性の値は、 `address` 有効な IP アドレスまたはホスト名である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d307b-121">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d307b-122">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="d307b-122">Configuration Files</span></span>  

 <span data-ttu-id="d307b-123">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d307b-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d307b-124">例</span><span class="sxs-lookup"><span data-stu-id="d307b-124">Example</span></span>  

 <span data-ttu-id="d307b-125">次の例では、サーバーに対する接続管理の一覧のエントリをすべて削除し、 `www.adventure-works.com` サーバーへの接続を4つ、 `www.contoso.com` 他のすべてのサーバーへの接続を2つ使用するようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="d307b-125">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d307b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="d307b-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="d307b-127">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="d307b-127">Network Settings Schema</span></span>](index.md)
