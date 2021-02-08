---
description: 詳細については <add> 、 <defaultPorts>
title: <add> の <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 9db7afa5183b185eb842530b051d98236e7fa381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803959"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="582e6-103">\<add> の \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="582e6-103">\<add> of \<defaultPorts></span></span>

<span data-ttu-id="582e6-104">クライアント アプリケーションがリッスンする既定の通信エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="582e6-104">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="582e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="582e6-105">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="582e6-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="582e6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="582e6-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="582e6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="582e6-108">属性</span><span class="sxs-lookup"><span data-stu-id="582e6-108">Attributes</span></span>  
  
|<span data-ttu-id="582e6-109">属性</span><span class="sxs-lookup"><span data-stu-id="582e6-109">Attribute</span></span>|<span data-ttu-id="582e6-110">説明</span><span class="sxs-lookup"><span data-stu-id="582e6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="582e6-111">port</span><span class="sxs-lookup"><span data-stu-id="582e6-111">port</span></span>|<span data-ttu-id="582e6-112">既定の通信ポート番号を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="582e6-112">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="582e6-113">scheme</span><span class="sxs-lookup"><span data-stu-id="582e6-113">scheme</span></span>|<span data-ttu-id="582e6-114">通信ポートに関連付けられているプロトコル設定のグループを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="582e6-114">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="582e6-115">子要素</span><span class="sxs-lookup"><span data-stu-id="582e6-115">Child Elements</span></span>  

 <span data-ttu-id="582e6-116">なし。</span><span class="sxs-lookup"><span data-stu-id="582e6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="582e6-117">親要素</span><span class="sxs-lookup"><span data-stu-id="582e6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="582e6-118">要素</span><span class="sxs-lookup"><span data-stu-id="582e6-118">Element</span></span>|<span data-ttu-id="582e6-119">説明</span><span class="sxs-lookup"><span data-stu-id="582e6-119">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="582e6-120">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="582e6-120">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="582e6-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="582e6-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
