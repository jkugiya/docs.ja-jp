---
description: '詳細情報: <remove> authenticationModules の要素 (ネットワーク設定)'
title: authenticationModules の <remove> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: 7c97cd20717e6e0945cf77ad6584b319120ec6a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804089"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="6ef59-103">authenticationModules の \<remove> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="6ef59-103">\<remove> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="6ef59-104">アプリケーションから認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="6ef59-104">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="6ef59-105">構文</span><span class="sxs-lookup"><span data-stu-id="6ef59-105">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ef59-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6ef59-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6ef59-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ef59-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ef59-108">属性</span><span class="sxs-lookup"><span data-stu-id="6ef59-108">Attributes</span></span>  
  
|<span data-ttu-id="6ef59-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="6ef59-109">**Attribute**</span></span>|<span data-ttu-id="6ef59-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="6ef59-110">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="6ef59-111">**type**</span><span class="sxs-lookup"><span data-stu-id="6ef59-111">**type**</span></span>|<span data-ttu-id="6ef59-112">削除する認証モジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="6ef59-112">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ef59-113">子要素</span><span class="sxs-lookup"><span data-stu-id="6ef59-113">Child Elements</span></span>  

 <span data-ttu-id="6ef59-114">なし。</span><span class="sxs-lookup"><span data-stu-id="6ef59-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ef59-115">親要素</span><span class="sxs-lookup"><span data-stu-id="6ef59-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6ef59-116">**要素**</span><span class="sxs-lookup"><span data-stu-id="6ef59-116">**Element**</span></span>|<span data-ttu-id="6ef59-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="6ef59-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6ef59-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="6ef59-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="6ef59-119">ネットワーク要求を認証するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="6ef59-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ef59-120">解説</span><span class="sxs-lookup"><span data-stu-id="6ef59-120">Remarks</span></span>  

 <span data-ttu-id="6ef59-121">要素は、構成 `remove` ファイルまたは構成階層の上位レベルで定義された認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="6ef59-121">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="6ef59-122">属性の値は、 `type` 有効なクラス名である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ef59-122">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6ef59-123">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="6ef59-123">Configuration Files</span></span>  

 <span data-ttu-id="6ef59-124">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ef59-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ef59-125">例</span><span class="sxs-lookup"><span data-stu-id="6ef59-125">Example</span></span>  

 <span data-ttu-id="6ef59-126">次の例では、認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="6ef59-126">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ef59-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ef59-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="6ef59-128">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="6ef59-128">Network Settings Schema</span></span>](index.md)
