---
description: ワークフローの詳細情報 <behaviors>
title: <behaviors> ワークフローの
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 5154a389aded34065cc7bdb11d1c73d71ca9f9f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698194"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="e4f9f-103">\<behaviors> ワークフローの</span><span class="sxs-lookup"><span data-stu-id="e4f9f-103">\<behaviors> of workflow</span></span>

<span data-ttu-id="e4f9f-104">この要素には、 **Servicebehaviors** コレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f9f-104">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="e4f9f-105">コレクション内の各要素は、ワークフロー サービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="e4f9f-105">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="e4f9f-106">各動作要素は、一意の **name** 属性によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="e4f9f-106">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="e4f9f-107">構文</span><span class="sxs-lookup"><span data-stu-id="e4f9f-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4f9f-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e4f9f-108">Attributes and Elements</span></span>  

 <span data-ttu-id="e4f9f-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4f9f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4f9f-110">属性</span><span class="sxs-lookup"><span data-stu-id="e4f9f-110">Attributes</span></span>  

 <span data-ttu-id="e4f9f-111">なし</span><span class="sxs-lookup"><span data-stu-id="e4f9f-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4f9f-112">子要素</span><span class="sxs-lookup"><span data-stu-id="e4f9f-112">Child Elements</span></span>  
  
|<span data-ttu-id="e4f9f-113">要素</span><span class="sxs-lookup"><span data-stu-id="e4f9f-113">Element</span></span>|<span data-ttu-id="e4f9f-114">説明</span><span class="sxs-lookup"><span data-stu-id="e4f9f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="e4f9f-115">この構成セクションは、特定のワークフロー サービスに対して定義されたすべての動作を表します。</span><span class="sxs-lookup"><span data-stu-id="e4f9f-115">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4f9f-116">親要素</span><span class="sxs-lookup"><span data-stu-id="e4f9f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e4f9f-117">要素</span><span class="sxs-lookup"><span data-stu-id="e4f9f-117">Element</span></span>|<span data-ttu-id="e4f9f-118">説明</span><span class="sxs-lookup"><span data-stu-id="e4f9f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="e4f9f-119">すべてのワークフロー構成要素のルート要素。</span><span class="sxs-lookup"><span data-stu-id="e4f9f-119">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4f9f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4f9f-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="e4f9f-121">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="e4f9f-121">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
