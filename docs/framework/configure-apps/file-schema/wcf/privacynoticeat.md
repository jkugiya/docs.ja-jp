---
description: '詳細情報: <privacyNoticeAt>'
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2e38d43becd783cc50afba5a029d3ab9905ec15a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683503"
---
# \<privacyNoticeAt>

<span data-ttu-id="49f17-102">`wsFederationHttp` バインディングで使用されるプライバシーに関する声明を指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="49f17-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="49f17-103">構文</span><span class="sxs-lookup"><span data-stu-id="49f17-103">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="49f17-104">種類</span><span class="sxs-lookup"><span data-stu-id="49f17-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49f17-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="49f17-105">Attributes and Elements</span></span>  

 <span data-ttu-id="49f17-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="49f17-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49f17-107">属性</span><span class="sxs-lookup"><span data-stu-id="49f17-107">Attributes</span></span>  
  
|<span data-ttu-id="49f17-108">属性</span><span class="sxs-lookup"><span data-stu-id="49f17-108">Attribute</span></span>|<span data-ttu-id="49f17-109">説明</span><span class="sxs-lookup"><span data-stu-id="49f17-109">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="49f17-110">プライバシーに関する声明の場所を示す URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="49f17-110">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="49f17-111">このプライバシーに関する声明のバージョンを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="49f17-111">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49f17-112">子要素</span><span class="sxs-lookup"><span data-stu-id="49f17-112">Child Elements</span></span>  

 <span data-ttu-id="49f17-113">なし。</span><span class="sxs-lookup"><span data-stu-id="49f17-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49f17-114">親要素</span><span class="sxs-lookup"><span data-stu-id="49f17-114">Parent Elements</span></span>  
  
|<span data-ttu-id="49f17-115">要素</span><span class="sxs-lookup"><span data-stu-id="49f17-115">Element</span></span>|<span data-ttu-id="49f17-116">説明</span><span class="sxs-lookup"><span data-stu-id="49f17-116">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="49f17-117">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="49f17-117">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49f17-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="49f17-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="49f17-119">バインド</span><span class="sxs-lookup"><span data-stu-id="49f17-119">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="49f17-120">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="49f17-120">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="49f17-121">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="49f17-121">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
