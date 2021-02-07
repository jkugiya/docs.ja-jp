---
description: '詳細情報: <webRequestModules> 要素 (ネットワーク設定)'
title: <webRequestModules> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 851aec2bf38910239874cb5792239a48de6efb70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698428"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="dccb7-103">\<webRequestModules> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="dccb7-103">\<webRequestModules> Element (Network Settings)</span></span>

<span data-ttu-id="dccb7-104">ネットワークホストから情報を要求するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="dccb7-104">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="dccb7-105">構文</span><span class="sxs-lookup"><span data-stu-id="dccb7-105">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dccb7-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dccb7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dccb7-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dccb7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dccb7-108">属性</span><span class="sxs-lookup"><span data-stu-id="dccb7-108">Attributes</span></span>  

 <span data-ttu-id="dccb7-109">なし。</span><span class="sxs-lookup"><span data-stu-id="dccb7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dccb7-110">子要素</span><span class="sxs-lookup"><span data-stu-id="dccb7-110">Child Elements</span></span>  
  
|<span data-ttu-id="dccb7-111">**要素**</span><span class="sxs-lookup"><span data-stu-id="dccb7-111">**Element**</span></span>|<span data-ttu-id="dccb7-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="dccb7-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dccb7-113">add</span><span class="sxs-lookup"><span data-stu-id="dccb7-113">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="dccb7-114">アプリケーションにカスタム Web 要求モジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="dccb7-114">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="dccb7-115">オフ</span><span class="sxs-lookup"><span data-stu-id="dccb7-115">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="dccb7-116">アプリケーションから、登録されているすべての Web 要求モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="dccb7-116">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="dccb7-117">remove</span><span class="sxs-lookup"><span data-stu-id="dccb7-117">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="dccb7-118">アプリケーションからカスタム Web 要求モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="dccb7-118">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dccb7-119">親要素</span><span class="sxs-lookup"><span data-stu-id="dccb7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dccb7-120">**要素**</span><span class="sxs-lookup"><span data-stu-id="dccb7-120">**Element**</span></span>|<span data-ttu-id="dccb7-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="dccb7-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dccb7-122">system.net</span><span class="sxs-lookup"><span data-stu-id="dccb7-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="dccb7-123">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dccb7-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dccb7-124">解説</span><span class="sxs-lookup"><span data-stu-id="dccb7-124">Remarks</span></span>  

 <span data-ttu-id="dccb7-125">要素は、 `webRequestModules` <xref:System.Net.WebRequest> ネットワークホストに対する情報要求を処理するために、クラスの子孫を登録します。</span><span class="sxs-lookup"><span data-stu-id="dccb7-125">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="dccb7-126">Web 要求モジュールは、インターフェイスを実装する必要があり <xref:System.Net.IWebRequestCreate> ます。</span><span class="sxs-lookup"><span data-stu-id="dccb7-126">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="dccb7-127">.NET Framework には、、、およびで始まる Uri の Web 要求モジュールが含まれてい `http://` `https://` `file://` ます。</span><span class="sxs-lookup"><span data-stu-id="dccb7-127">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="dccb7-128">既定のモジュールをオーバーライドするには、構成ファイルにカスタムモジュールを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dccb7-128">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dccb7-129">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="dccb7-129">Configuration Files</span></span>  

 <span data-ttu-id="dccb7-130">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="dccb7-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dccb7-131">例</span><span class="sxs-lookup"><span data-stu-id="dccb7-131">Example</span></span>  

 <span data-ttu-id="dccb7-132">次の例では、既定の HTTP モジュールを登録します。</span><span class="sxs-lookup"><span data-stu-id="dccb7-132">The following example registers the default HTTP module.</span></span> <span data-ttu-id="dccb7-133">Version および PublicKeyToken の値は、指定されたモジュールの正しい値に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="dccb7-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dccb7-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="dccb7-134">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="dccb7-135">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="dccb7-135">Network Settings Schema</span></span>](index.md)
