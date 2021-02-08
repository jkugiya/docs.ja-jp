---
description: 詳細については <filters> 、 <routing>
title: <filters> の <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 41b51453f53fca042f53ca1ee8372413b8478ecd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782053"
---
# <a name="filters-of-routing"></a><span data-ttu-id="f891a-103">\<filters> の \<routing></span><span class="sxs-lookup"><span data-stu-id="f891a-103">\<filters> of \<routing></span></span>

<span data-ttu-id="f891a-104"><xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージを評価するときに使用する Windows Communication Foundation (WCF) の種類を決定する一連のルーティングフィルターを定義するための構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="f891a-104">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="f891a-105">構文</span><span class="sxs-lookup"><span data-stu-id="f891a-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f891a-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="f891a-106">Attributes and elements</span></span>

<span data-ttu-id="f891a-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f891a-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f891a-108">属性</span><span class="sxs-lookup"><span data-stu-id="f891a-108">Attributes</span></span>

<span data-ttu-id="f891a-109">なし</span><span class="sxs-lookup"><span data-stu-id="f891a-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="f891a-110">子要素</span><span class="sxs-lookup"><span data-stu-id="f891a-110">Child elements</span></span>

|     | <span data-ttu-id="f891a-111">説明</span><span class="sxs-lookup"><span data-stu-id="f891a-111">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="f891a-112"><xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) の種類を決定するルーティングフィルターを格納します。</span><span class="sxs-lookup"><span data-stu-id="f891a-112">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="f891a-113">親要素</span><span class="sxs-lookup"><span data-stu-id="f891a-113">Parent elements</span></span>

|     | <span data-ttu-id="f891a-114">説明</span><span class="sxs-lookup"><span data-stu-id="f891a-114">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="f891a-115">一連のルーティングフィルターを定義するための構成セクションを表します。これにより、受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) の種類、 <xref:System.ServiceModel.Dispatcher.MessageFilter> およびフィルターが一致したときにメッセージを送信するターゲットエンドポイントを定義するルーティングテーブルが決定されます。</span><span class="sxs-lookup"><span data-stu-id="f891a-115">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f891a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f891a-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
