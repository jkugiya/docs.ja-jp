---
description: '詳細情報: <remove> webRequestModules の要素 (ネットワーク設定)'
title: webRequestModules の <remove> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: db65c91417af2538e27b65e0ae28d06a6bfcde0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713001"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="35512-103">webRequestModules の \<remove> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="35512-103">\<remove> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="35512-104">アプリケーションからカスタム Web 要求モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="35512-104">Removes a custom Web request module from the application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**
  
## <a name="syntax"></a><span data-ttu-id="35512-105">構文</span><span class="sxs-lookup"><span data-stu-id="35512-105">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35512-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="35512-106">Attributes and Elements</span></span>  

 <span data-ttu-id="35512-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="35512-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35512-108">属性</span><span class="sxs-lookup"><span data-stu-id="35512-108">Attributes</span></span>  
  
|<span data-ttu-id="35512-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="35512-109">**Attribute**</span></span>|<span data-ttu-id="35512-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="35512-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="35512-111">この Web 要求モジュールによって処理される要求の URI プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="35512-111">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35512-112">子要素</span><span class="sxs-lookup"><span data-stu-id="35512-112">Child Elements</span></span>  

 <span data-ttu-id="35512-113">なし。</span><span class="sxs-lookup"><span data-stu-id="35512-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35512-114">親要素</span><span class="sxs-lookup"><span data-stu-id="35512-114">Parent Elements</span></span>  
  
|<span data-ttu-id="35512-115">**要素**</span><span class="sxs-lookup"><span data-stu-id="35512-115">**Element**</span></span>|<span data-ttu-id="35512-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="35512-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="35512-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="35512-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="35512-118">ネットワークホストから情報を要求するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="35512-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35512-119">解説</span><span class="sxs-lookup"><span data-stu-id="35512-119">Remarks</span></span>  

 <span data-ttu-id="35512-120">要素は、 `remove` 指定された URI プレフィックスの登録済み Web 要求モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="35512-120">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="35512-121">属性の値は、 `prefix` 有効な URI の先頭の文字 (""、"" など) にする必要があり `http` `http://www.contoso.com` ます。</span><span class="sxs-lookup"><span data-stu-id="35512-121">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="35512-122">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="35512-122">Configuration Files</span></span>  

 <span data-ttu-id="35512-123">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="35512-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35512-124">例</span><span class="sxs-lookup"><span data-stu-id="35512-124">Example</span></span>  

<span data-ttu-id="35512-125">次の例では、HTTP 用の既存の Web 要求モジュールを削除し、HTTP 要求用の新しいカスタム Web 要求モジュールをに登録し `www.contoso.com` ます。</span><span class="sxs-lookup"><span data-stu-id="35512-125">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35512-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="35512-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="35512-127">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="35512-127">Network Settings Schema</span></span>](index.md)
