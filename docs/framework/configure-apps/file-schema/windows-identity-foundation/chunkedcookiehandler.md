---
description: '詳細情報: <chunkedCookieHandler>'
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b0090706d3d7a9f62e17ae63ec16e4b3a869a812
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664289"
---
# \<chunkedCookieHandler>

<span data-ttu-id="7201c-102">を構成 <xref:System.IdentityModel.Services.ChunkedCookieHandler> します。</span><span class="sxs-lookup"><span data-stu-id="7201c-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="7201c-103">この要素は `mode` 、要素の属性 `<cookieHandler>` が "Default" または "Chunked" の場合にのみ存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7201c-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="7201c-104">構文</span><span class="sxs-lookup"><span data-stu-id="7201c-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7201c-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7201c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7201c-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7201c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7201c-107">属性</span><span class="sxs-lookup"><span data-stu-id="7201c-107">Attributes</span></span>  
  
|<span data-ttu-id="7201c-108">属性</span><span class="sxs-lookup"><span data-stu-id="7201c-108">Attribute</span></span>|<span data-ttu-id="7201c-109">説明</span><span class="sxs-lookup"><span data-stu-id="7201c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7201c-110">chunkSize</span><span class="sxs-lookup"><span data-stu-id="7201c-110">chunkSize</span></span>|<span data-ttu-id="7201c-111">1つの HTTP クッキーの HTTP クッキーデータの最大サイズ (文字数)。</span><span class="sxs-lookup"><span data-stu-id="7201c-111">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="7201c-112">チャンクサイズを調整する場合は注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="7201c-112">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="7201c-113">Web ブラウザーでは、cookie のサイズとドメインごとに許可される数の制限が異なります。</span><span class="sxs-lookup"><span data-stu-id="7201c-113">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="7201c-114">たとえば、元の Netscape 仕様では、これらの制限が規定されています。これは、cookie の合計数は300クッキー、cookie ヘッダーあたりは4096バイト (cookie の値だけでなく、メタデータを含む)、ドメインごとに20の cookie です。</span><span class="sxs-lookup"><span data-stu-id="7201c-114">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="7201c-115">既定値は 2000 です。</span><span class="sxs-lookup"><span data-stu-id="7201c-115">The default is 2000.</span></span> <span data-ttu-id="7201c-116">必須。</span><span class="sxs-lookup"><span data-stu-id="7201c-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7201c-117">子要素</span><span class="sxs-lookup"><span data-stu-id="7201c-117">Child Elements</span></span>  

 <span data-ttu-id="7201c-118">なし</span><span class="sxs-lookup"><span data-stu-id="7201c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7201c-119">親要素</span><span class="sxs-lookup"><span data-stu-id="7201c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7201c-120">要素</span><span class="sxs-lookup"><span data-stu-id="7201c-120">Element</span></span>|<span data-ttu-id="7201c-121">説明</span><span class="sxs-lookup"><span data-stu-id="7201c-121">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="7201c-122"><xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) が cookie の読み取りと書き込みに使用するを構成します。</span><span class="sxs-lookup"><span data-stu-id="7201c-122">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7201c-123">解説</span><span class="sxs-lookup"><span data-stu-id="7201c-123">Remarks</span></span>  

 <span data-ttu-id="7201c-124"><xref:System.IdentityModel.Services.ChunkedCookieHandler> `mode` 要素の属性を `<cookieHandler>` "Default" または "Chunked" に設定してを指定した場合、子要素を追加し、その属性を設定することにより、cookie ハンドラーが cookie の読み書きに使用するチャンクサイズを指定でき `<chunkedCookieHandler>` `chunkSize` ます。</span><span class="sxs-lookup"><span data-stu-id="7201c-124">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="7201c-125">`<chunkedCookieHandler>`要素が存在しない場合は、既定のチャンクサイズである2000バイトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7201c-125">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="7201c-126">`mode`属性が "Custom" に設定されている場合、この要素を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="7201c-126">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="7201c-127">`<chunkedCookieHandler>`要素は、クラスによって表され <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> ます。</span><span class="sxs-lookup"><span data-stu-id="7201c-127">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7201c-128">例</span><span class="sxs-lookup"><span data-stu-id="7201c-128">Example</span></span>  

 <span data-ttu-id="7201c-129">次の例では、3000バイトのチャンク単位でクッキーを書き込むチャンク cookie ハンドラーを構成します。</span><span class="sxs-lookup"><span data-stu-id="7201c-129">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7201c-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="7201c-130">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
