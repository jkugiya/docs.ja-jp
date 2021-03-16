---
description: '詳細情報: <timeOuts>'
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 097569d1742f6486ddfb5fb3c3d98ba106424f45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786591"
---
# \<timeOuts>

<span data-ttu-id="ea756-102">サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="ea756-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="ea756-103">構文</span><span class="sxs-lookup"><span data-stu-id="ea756-103">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea756-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ea756-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ea756-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea756-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea756-106">属性</span><span class="sxs-lookup"><span data-stu-id="ea756-106">Attributes</span></span>  
  
|<span data-ttu-id="ea756-107">属性</span><span class="sxs-lookup"><span data-stu-id="ea756-107">Attribute</span></span>|<span data-ttu-id="ea756-108">説明</span><span class="sxs-lookup"><span data-stu-id="ea756-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="ea756-109">サービス ホストを閉じるまでに待機できる期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="ea756-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="ea756-110">サービス ホストを開くまでに待機できる期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="ea756-110">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea756-111">子要素</span><span class="sxs-lookup"><span data-stu-id="ea756-111">Child Elements</span></span>  

 <span data-ttu-id="ea756-112">なし。</span><span class="sxs-lookup"><span data-stu-id="ea756-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea756-113">親要素</span><span class="sxs-lookup"><span data-stu-id="ea756-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ea756-114">要素</span><span class="sxs-lookup"><span data-stu-id="ea756-114">Element</span></span>|<span data-ttu-id="ea756-115">説明</span><span class="sxs-lookup"><span data-stu-id="ea756-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="ea756-116">サービス ホストの設定を指定する構成要素です。</span><span class="sxs-lookup"><span data-stu-id="ea756-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea756-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea756-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="ea756-118">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ea756-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
