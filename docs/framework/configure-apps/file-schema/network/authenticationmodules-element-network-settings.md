---
description: '詳細情報: <authenticationModules> 要素 (ネットワーク設定)'
title: <authenticationModules> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 2c2dc3c6a3d8fc064bb24c3d86a4441c269e43f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698611"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="7f668-103">\<authenticationModules> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="7f668-103">\<authenticationModules> Element (Network Settings)</span></span>

<span data-ttu-id="7f668-104">ネットワーク要求を認証するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f668-104">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="7f668-105">構文</span><span class="sxs-lookup"><span data-stu-id="7f668-105">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f668-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7f668-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7f668-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f668-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f668-108">属性</span><span class="sxs-lookup"><span data-stu-id="7f668-108">Attributes</span></span>  

 <span data-ttu-id="7f668-109">なし。</span><span class="sxs-lookup"><span data-stu-id="7f668-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f668-110">子要素</span><span class="sxs-lookup"><span data-stu-id="7f668-110">Child Elements</span></span>  
  
|<span data-ttu-id="7f668-111">**要素**</span><span class="sxs-lookup"><span data-stu-id="7f668-111">**Element**</span></span>|<span data-ttu-id="7f668-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="7f668-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7f668-113">add</span><span class="sxs-lookup"><span data-stu-id="7f668-113">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="7f668-114">アプリケーションに認証モジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="7f668-114">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="7f668-115">オフ</span><span class="sxs-lookup"><span data-stu-id="7f668-115">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="7f668-116">アプリケーションからすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="7f668-116">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="7f668-117">remove</span><span class="sxs-lookup"><span data-stu-id="7f668-117">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="7f668-118">アプリケーションから認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="7f668-118">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f668-119">親要素</span><span class="sxs-lookup"><span data-stu-id="7f668-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7f668-120">**要素**</span><span class="sxs-lookup"><span data-stu-id="7f668-120">**Element**</span></span>|<span data-ttu-id="7f668-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="7f668-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7f668-122">system.net</span><span class="sxs-lookup"><span data-stu-id="7f668-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="7f668-123">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f668-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f668-124">解説</span><span class="sxs-lookup"><span data-stu-id="7f668-124">Remarks</span></span>  

 <span data-ttu-id="7f668-125">要素は、 `authenticationModule` サーバーとの認証プロセスを実行する認証モジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f668-125">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="7f668-126">認証モジュールは、インターフェイスを実装する必要があり <xref:System.Net.IAuthenticationModule> ます。</span><span class="sxs-lookup"><span data-stu-id="7f668-126">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7f668-127">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="7f668-127">Configuration Files</span></span>  

 <span data-ttu-id="7f668-128">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f668-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f668-129">例</span><span class="sxs-lookup"><span data-stu-id="7f668-129">Example</span></span>  

 <span data-ttu-id="7f668-130">次の例では、認証モジュールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7f668-130">The following example enables an authentication module.</span></span> <span data-ttu-id="7f668-131">Version および PublicKeyToken の値は、指定されたモジュールの正しい値に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f668-131">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f668-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f668-132">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="7f668-133">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="7f668-133">Network Settings Schema</span></span>](index.md)
