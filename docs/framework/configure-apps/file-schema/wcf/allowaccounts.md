---
description: '詳細情報: <allowAccounts>'
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 5211d694e5318faf0cfc31b404764acb405bd096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749988"
---
# \<allowAccounts>

<span data-ttu-id="6de24-102">Windows Communication Foundation (WCF) サービスをホストするプロセスのユーザーアカウントを指定する構成要素のコレクションが含まれており、共有サービスへの接続アクセスが許可されます。</span><span class="sxs-lookup"><span data-stu-id="6de24-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="6de24-103">構文</span><span class="sxs-lookup"><span data-stu-id="6de24-103">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6de24-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6de24-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6de24-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6de24-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6de24-106">属性</span><span class="sxs-lookup"><span data-stu-id="6de24-106">Attributes</span></span>  

 <span data-ttu-id="6de24-107">なし。</span><span class="sxs-lookup"><span data-stu-id="6de24-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6de24-108">子要素</span><span class="sxs-lookup"><span data-stu-id="6de24-108">Child Elements</span></span>  
  
|<span data-ttu-id="6de24-109">属性</span><span class="sxs-lookup"><span data-stu-id="6de24-109">Attribute</span></span>|<span data-ttu-id="6de24-110">説明</span><span class="sxs-lookup"><span data-stu-id="6de24-110">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="6de24-111">WCF サービスをホストし、共有サービスへの接続アクセスが付与されているプロセスのユーザーアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="6de24-111">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6de24-112">親要素</span><span class="sxs-lookup"><span data-stu-id="6de24-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6de24-113">要素</span><span class="sxs-lookup"><span data-stu-id="6de24-113">Element</span></span>|<span data-ttu-id="6de24-114">説明</span><span class="sxs-lookup"><span data-stu-id="6de24-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6de24-115">[\<net.pipe>](net-pipe.md) または [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="6de24-115">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="6de24-116">Net Pipe または TCP 共有サービスの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="6de24-116">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6de24-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6de24-117">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
