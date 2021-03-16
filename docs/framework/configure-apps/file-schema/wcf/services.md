---
description: '詳細情報: <services>'
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 6e8c0c5ad5390c097db7bf1be1f0d489e1c0d624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786708"
---
# \<services>

<span data-ttu-id="03845-102">サービスは、設定ファイルの `services` セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="03845-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="03845-103">各サービスには、独自の `service` 設定セクションがあります。</span><span class="sxs-lookup"><span data-stu-id="03845-103">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="03845-104">構文</span><span class="sxs-lookup"><span data-stu-id="03845-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03845-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="03845-105">Attributes and Elements</span></span>  

 <span data-ttu-id="03845-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="03845-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03845-107">属性</span><span class="sxs-lookup"><span data-stu-id="03845-107">Attributes</span></span>  

 <span data-ttu-id="03845-108">なし</span><span class="sxs-lookup"><span data-stu-id="03845-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03845-109">子要素</span><span class="sxs-lookup"><span data-stu-id="03845-109">Child Elements</span></span>  
  
|<span data-ttu-id="03845-110">要素</span><span class="sxs-lookup"><span data-stu-id="03845-110">Element</span></span>|<span data-ttu-id="03845-111">説明</span><span class="sxs-lookup"><span data-stu-id="03845-111">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="03845-112">サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="03845-112">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03845-113">親要素</span><span class="sxs-lookup"><span data-stu-id="03845-113">Parent Elements</span></span>  
  
|<span data-ttu-id="03845-114">要素</span><span class="sxs-lookup"><span data-stu-id="03845-114">Element</span></span>|<span data-ttu-id="03845-115">説明</span><span class="sxs-lookup"><span data-stu-id="03845-115">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="03845-116">すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="03845-116">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03845-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="03845-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
