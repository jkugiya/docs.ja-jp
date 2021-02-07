---
description: '詳細情報: <clear> authenticationModules の要素 (ネットワーク設定)'
title: authenticationModules の <clear> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: ccfc9f53ef53268cdb1155673fc47a862a63419c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698571"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="2e8fa-103">authenticationModules の \<clear> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="2e8fa-103">\<clear> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="2e8fa-104">アプリケーションからすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-104">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="2e8fa-105">構文</span><span class="sxs-lookup"><span data-stu-id="2e8fa-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e8fa-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2e8fa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2e8fa-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e8fa-108">属性</span><span class="sxs-lookup"><span data-stu-id="2e8fa-108">Attributes</span></span>  

 <span data-ttu-id="2e8fa-109">なし。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e8fa-110">子要素</span><span class="sxs-lookup"><span data-stu-id="2e8fa-110">Child Elements</span></span>  

 <span data-ttu-id="2e8fa-111">なし。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e8fa-112">親要素</span><span class="sxs-lookup"><span data-stu-id="2e8fa-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2e8fa-113">**要素**</span><span class="sxs-lookup"><span data-stu-id="2e8fa-113">**Element**</span></span>|<span data-ttu-id="2e8fa-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="2e8fa-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2e8fa-115">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="2e8fa-115">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="2e8fa-116">ネットワーク要求を認証するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-116">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e8fa-117">解説</span><span class="sxs-lookup"><span data-stu-id="2e8fa-117">Remarks</span></span>  

 <span data-ttu-id="2e8fa-118">要素は、構成 `clear` ファイルまたは構成階層内の上位レベルで定義されたすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-118">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2e8fa-119">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2e8fa-119">Configuration Files</span></span>  

 <span data-ttu-id="2e8fa-120">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e8fa-121">例</span><span class="sxs-lookup"><span data-stu-id="2e8fa-121">Example</span></span>  

 <span data-ttu-id="2e8fa-122">次の例では、構成されているすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-122">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e8fa-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e8fa-123">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="2e8fa-124">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="2e8fa-124">Network Settings Schema</span></span>](index.md)
