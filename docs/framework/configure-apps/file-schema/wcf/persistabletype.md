---
description: '詳細情報: <persistableType>'
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: eadbb951d751dd88ce974edc8d5b343a1469b758
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683633"
---
# \<persistableType>

<span data-ttu-id="afd94-102">すべての永続型を指定します。</span><span class="sxs-lookup"><span data-stu-id="afd94-102">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="afd94-103">構文</span><span class="sxs-lookup"><span data-stu-id="afd94-103">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="afd94-104">Type</span><span class="sxs-lookup"><span data-stu-id="afd94-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afd94-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="afd94-105">Attributes and Elements</span></span>  

 <span data-ttu-id="afd94-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="afd94-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afd94-107">属性</span><span class="sxs-lookup"><span data-stu-id="afd94-107">Attributes</span></span>  
  
|<span data-ttu-id="afd94-108">属性</span><span class="sxs-lookup"><span data-stu-id="afd94-108">Attribute</span></span>|<span data-ttu-id="afd94-109">説明</span><span class="sxs-lookup"><span data-stu-id="afd94-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afd94-110">id</span><span class="sxs-lookup"><span data-stu-id="afd94-110">id</span></span>|<span data-ttu-id="afd94-111">永続型の一意の ID を指定する文字列を含む必須属性。</span><span class="sxs-lookup"><span data-stu-id="afd94-111">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="afd94-112">name</span><span class="sxs-lookup"><span data-stu-id="afd94-112">name</span></span>|<span data-ttu-id="afd94-113">永続型の名前を指定する文字列を含む省略可能な属性。</span><span class="sxs-lookup"><span data-stu-id="afd94-113">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afd94-114">子要素</span><span class="sxs-lookup"><span data-stu-id="afd94-114">Child Elements</span></span>  

 <span data-ttu-id="afd94-115">なし</span><span class="sxs-lookup"><span data-stu-id="afd94-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afd94-116">親要素</span><span class="sxs-lookup"><span data-stu-id="afd94-116">Parent Elements</span></span>  
  
|<span data-ttu-id="afd94-117">要素</span><span class="sxs-lookup"><span data-stu-id="afd94-117">Element</span></span>|<span data-ttu-id="afd94-118">説明</span><span class="sxs-lookup"><span data-stu-id="afd94-118">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="afd94-119">`persistableType` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="afd94-119">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afd94-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="afd94-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="afd94-121">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="afd94-121">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="afd94-122">方法: COM+ サービス設定を構成する</span><span class="sxs-lookup"><span data-stu-id="afd94-122">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
