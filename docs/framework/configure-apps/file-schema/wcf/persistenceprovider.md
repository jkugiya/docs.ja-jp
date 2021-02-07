---
description: '詳細情報: <persistenceProvider>'
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 60ddaf9f26f496bd7d79ccab84f84135e46963d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683555"
---
# \<persistenceProvider>

<span data-ttu-id="f06af-102">使用する永続化プロバイダーの実装の型と、永続化操作に使用するタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="f06af-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="f06af-103">構文</span><span class="sxs-lookup"><span data-stu-id="f06af-103">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f06af-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f06af-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f06af-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06af-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f06af-106">属性</span><span class="sxs-lookup"><span data-stu-id="f06af-106">Attributes</span></span>  
  
|<span data-ttu-id="f06af-107">属性</span><span class="sxs-lookup"><span data-stu-id="f06af-107">Attribute</span></span>|<span data-ttu-id="f06af-108">説明</span><span class="sxs-lookup"><span data-stu-id="f06af-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f06af-109">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="f06af-109">persistenceOperationTimeout</span></span>|<span data-ttu-id="f06af-110">永続化動作に使用するタイムアウトを指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="f06af-110">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="f06af-111">既定値は "00:00:30" です。</span><span class="sxs-lookup"><span data-stu-id="f06af-111">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="f06af-112">type</span><span class="sxs-lookup"><span data-stu-id="f06af-112">type</span></span>|<span data-ttu-id="f06af-113">使用する永続化プロバイダー ファクトリの型を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="f06af-113">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f06af-114">子要素</span><span class="sxs-lookup"><span data-stu-id="f06af-114">Child Elements</span></span>  

 <span data-ttu-id="f06af-115">なし。</span><span class="sxs-lookup"><span data-stu-id="f06af-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f06af-116">親要素</span><span class="sxs-lookup"><span data-stu-id="f06af-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f06af-117">要素</span><span class="sxs-lookup"><span data-stu-id="f06af-117">Element</span></span>|<span data-ttu-id="f06af-118">説明</span><span class="sxs-lookup"><span data-stu-id="f06af-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f06af-119">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="f06af-119">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f06af-120">解説</span><span class="sxs-lookup"><span data-stu-id="f06af-120">Remarks</span></span>  

 <span data-ttu-id="f06af-121">この要素は、WCF サービスの状態をシリアル化するために使用される永続化プロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="f06af-121">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="f06af-122">HTTP ヘッダーに状態情報を渡す `wsHttpContextBinding` と一緒に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f06af-122">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f06af-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f06af-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
