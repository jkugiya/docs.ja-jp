---
description: '詳細情報: <clear> webRequestModules の要素 (ネットワーク設定)'
title: webRequestModules の <clear> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: 0782bf9edeafed2d61a368c3f6a8b37ef226c990
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740419"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="85972-103">webRequestModules の \<clear> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="85972-103">\<clear> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="85972-104">アプリケーションから、登録されているすべての Web 要求モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="85972-104">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="85972-105">構文</span><span class="sxs-lookup"><span data-stu-id="85972-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85972-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="85972-106">Attributes and Elements</span></span>  

 <span data-ttu-id="85972-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="85972-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85972-108">属性</span><span class="sxs-lookup"><span data-stu-id="85972-108">Attributes</span></span>  

 <span data-ttu-id="85972-109">なし。</span><span class="sxs-lookup"><span data-stu-id="85972-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85972-110">子要素</span><span class="sxs-lookup"><span data-stu-id="85972-110">Child Elements</span></span>  

 <span data-ttu-id="85972-111">なし。</span><span class="sxs-lookup"><span data-stu-id="85972-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85972-112">親要素</span><span class="sxs-lookup"><span data-stu-id="85972-112">Parent Elements</span></span>  
  
|<span data-ttu-id="85972-113">**要素**</span><span class="sxs-lookup"><span data-stu-id="85972-113">**Element**</span></span>|<span data-ttu-id="85972-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="85972-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="85972-115">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="85972-115">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="85972-116">ネットワークホストから情報を要求するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="85972-116">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85972-117">解説</span><span class="sxs-lookup"><span data-stu-id="85972-117">Remarks</span></span>  

 <span data-ttu-id="85972-118">要素は、構成 `clear` ファイルで既に定義されている、または構成階層の上位レベルに定義されている、登録済みのすべての Web 要求モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="85972-118">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="85972-119">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="85972-119">Configuration Files</span></span>  

 <span data-ttu-id="85972-120">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="85972-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85972-121">例</span><span class="sxs-lookup"><span data-stu-id="85972-121">Example</span></span>  

 <span data-ttu-id="85972-122">次の例では、すべての Web 要求モジュールをクリアし、Web 要求モジュールを HTTP に登録します。</span><span class="sxs-lookup"><span data-stu-id="85972-122">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85972-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="85972-123">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="85972-124">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="85972-124">Network Settings Schema</span></span>](index.md)
