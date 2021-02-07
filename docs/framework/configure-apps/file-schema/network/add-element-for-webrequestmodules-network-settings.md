---
description: '詳細情報: <add> webRequestModules の要素 (ネットワーク設定)'
title: webRequestModules の <add> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 1edb63a1e1095bb4b3c3d749fd389ffaad5ddf9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729895"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="0be16-103">webRequestModules の \<add> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="0be16-103">\<add> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="0be16-104">アプリケーションにカスタム Web 要求モジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="0be16-104">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="0be16-105">構文</span><span class="sxs-lookup"><span data-stu-id="0be16-105">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0be16-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0be16-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0be16-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0be16-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0be16-108">属性</span><span class="sxs-lookup"><span data-stu-id="0be16-108">Attributes</span></span>  
  
|<span data-ttu-id="0be16-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="0be16-109">**Attribute**</span></span>|<span data-ttu-id="0be16-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="0be16-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="0be16-111">この Web 要求モジュールによって処理される要求の URI プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="0be16-111">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="0be16-112"><xref:System.Type.FullName%2A> <xref:System.Reflection.Assembly.FullName%2A> この Web 要求モジュールを実装するコンマで区切られた、完全修飾型名 (プロパティによって示されます) とアセンブリ名 (プロパティによって示されます)。</span><span class="sxs-lookup"><span data-stu-id="0be16-112">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0be16-113">子要素</span><span class="sxs-lookup"><span data-stu-id="0be16-113">Child Elements</span></span>  

 <span data-ttu-id="0be16-114">なし。</span><span class="sxs-lookup"><span data-stu-id="0be16-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0be16-115">親要素</span><span class="sxs-lookup"><span data-stu-id="0be16-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0be16-116">**要素**</span><span class="sxs-lookup"><span data-stu-id="0be16-116">**Element**</span></span>|<span data-ttu-id="0be16-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="0be16-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0be16-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="0be16-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="0be16-119">ネットワークホストから情報を要求するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="0be16-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0be16-120">解説</span><span class="sxs-lookup"><span data-stu-id="0be16-120">Remarks</span></span>  

 <span data-ttu-id="0be16-121">属性は、 `prefix` 指定された Web 要求モジュールを使用する URI プレフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="0be16-121">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="0be16-122">通常、Web 要求モジュールは、HTTP や FTP などの特定のプロトコルを処理するように登録されますが、サーバー上の特定のサーバーまたはパスへの要求を処理するように登録できます。</span><span class="sxs-lookup"><span data-stu-id="0be16-122">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="0be16-123">Web 要求モジュールは、URI 照合プレフィックスがメソッドに渡されたときに作成され <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="0be16-123">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="0be16-124">属性の値は、 `prefix` 有効な URI の先頭の文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0be16-124">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="0be16-125">たとえば、`http` または `http://www.contoso.com` です。</span><span class="sxs-lookup"><span data-stu-id="0be16-125">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="0be16-126">属性の値は、 `type` 有効な型名と、それに対応するアセンブリ名をコンマで区切って指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0be16-126">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="0be16-127">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="0be16-127">Configuration Files</span></span>  

 <span data-ttu-id="0be16-128">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="0be16-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0be16-129">例</span><span class="sxs-lookup"><span data-stu-id="0be16-129">Example</span></span>  

 <span data-ttu-id="0be16-130">次の例では、HTTP 用のカスタム Web 要求モジュールを登録します。</span><span class="sxs-lookup"><span data-stu-id="0be16-130">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="0be16-131">Version および PublicKeyToken の値は、指定されたモジュールの正しい値に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="0be16-131">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0be16-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="0be16-132">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="0be16-133">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="0be16-133">Network Settings Schema</span></span>](index.md)
