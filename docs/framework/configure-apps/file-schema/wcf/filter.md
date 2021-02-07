---
description: '詳細情報: <filter>'
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 993d2265ac3a714475e8cbe9e8a2c3f93c46bde2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664679"
---
# \<filter>

<span data-ttu-id="f5ba2-102">受信メッセージを評価するときに使用する Windows Communication Foundation (WCF) の種類、 <xref:System.ServiceModel.Dispatcher.MessageFilter> およびフィルターに必要なサポートデータまたはパラメーターを決定するルーティングフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="f5ba2-103">構文</span><span class="sxs-lookup"><span data-stu-id="f5ba2-103">Syntax</span></span>  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5ba2-104">属性と要素</span><span class="sxs-lookup"><span data-stu-id="f5ba2-104">Attributes and elements</span></span>

<span data-ttu-id="f5ba2-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5ba2-106">属性</span><span class="sxs-lookup"><span data-stu-id="f5ba2-106">Attributes</span></span>

| <span data-ttu-id="f5ba2-107">属性</span><span class="sxs-lookup"><span data-stu-id="f5ba2-107">Attribute</span></span>  | <span data-ttu-id="f5ba2-108">説明</span><span class="sxs-lookup"><span data-stu-id="f5ba2-108">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="f5ba2-109">customType</span><span class="sxs-lookup"><span data-stu-id="f5ba2-109">customType</span></span> | <span data-ttu-id="f5ba2-110">フィルターとして使用されるカスタム型の完全修飾型名を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-110">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="f5ba2-111">`filterType`がに設定されている場合 `custom` 、この属性には作成するクラスの完全修飾型名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-111">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="f5ba2-112">`filterData` には、カスタム型フィルターの評価時に使用される値を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-112">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="f5ba2-113">filterData</span><span class="sxs-lookup"><span data-stu-id="f5ba2-113">filterData</span></span> | <span data-ttu-id="f5ba2-114">フィルター データを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-114">A string containing the filter data.</span></span> <span data-ttu-id="f5ba2-115">この属性を指定する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-115">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f5ba2-116">filterType</span><span class="sxs-lookup"><span data-stu-id="f5ba2-116">filterType</span></span> | <span data-ttu-id="f5ba2-117">フィルターの種類を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-117">A string containing the filter type.</span></span> <span data-ttu-id="f5ba2-118">この属性は <xref:System.ServiceModel.Routing.Configuration.FilterType> 型です。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-118">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="f5ba2-119">`filterData` 属性を使用する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-119">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f5ba2-120">name</span><span class="sxs-lookup"><span data-stu-id="f5ba2-120">name</span></span>       | <span data-ttu-id="f5ba2-121">フィルター要素の一意の名前を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-121">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f5ba2-122">子要素</span><span class="sxs-lookup"><span data-stu-id="f5ba2-122">Child elements</span></span>

<span data-ttu-id="f5ba2-123">なし。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5ba2-124">親要素</span><span class="sxs-lookup"><span data-stu-id="f5ba2-124">Parent elements</span></span>

| <span data-ttu-id="f5ba2-125">要素</span><span class="sxs-lookup"><span data-stu-id="f5ba2-125">Element</span></span> | <span data-ttu-id="f5ba2-126">説明</span><span class="sxs-lookup"><span data-stu-id="f5ba2-126">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="f5ba2-127">一連のルーティングフィルターを定義するための構成セクション <xref:System.ServiceModel.Dispatcher.MessageFilter> 。受信メッセージを評価するときに使用する Windows Communication Foundation (WCF) の種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="f5ba2-127">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f5ba2-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5ba2-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
