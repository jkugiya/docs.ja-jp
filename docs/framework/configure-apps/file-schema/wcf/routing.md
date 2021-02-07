---
description: '詳細情報: <routing>'
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 62222b527a14310b66015d4fdc4503e6cff25c8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683347"
---
# \<routing>

<span data-ttu-id="bd00f-102">一連のルーティングフィルターを定義するための構成セクションを表します。これにより、受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) の種類、 <xref:System.ServiceModel.Dispatcher.MessageFilter> およびフィルターが一致したときにメッセージを送信するターゲットエンドポイントを定義するルーティングテーブルが決定されます。</span><span class="sxs-lookup"><span data-stu-id="bd00f-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="bd00f-103">構文</span><span class="sxs-lookup"><span data-stu-id="bd00f-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd00f-104">属性と要素</span><span class="sxs-lookup"><span data-stu-id="bd00f-104">Attributes and elements</span></span>

<span data-ttu-id="bd00f-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd00f-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd00f-106">属性</span><span class="sxs-lookup"><span data-stu-id="bd00f-106">Attributes</span></span>

<span data-ttu-id="bd00f-107">なし</span><span class="sxs-lookup"><span data-stu-id="bd00f-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd00f-108">子要素</span><span class="sxs-lookup"><span data-stu-id="bd00f-108">Child elements</span></span>

|     | <span data-ttu-id="bd00f-109">説明</span><span class="sxs-lookup"><span data-stu-id="bd00f-109">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="bd00f-110">受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) MessageFilter の種類を決定するルーティングフィルターのセットを格納します。</span><span class="sxs-lookup"><span data-stu-id="bd00f-110">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="bd00f-111">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納します。フィルターが一致したときにエンドポイントを指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd00f-111">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="bd00f-112">親要素</span><span class="sxs-lookup"><span data-stu-id="bd00f-112">Parent elements</span></span>

|     | <span data-ttu-id="bd00f-113">説明</span><span class="sxs-lookup"><span data-stu-id="bd00f-113">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="bd00f-114">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="bd00f-114">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="bd00f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd00f-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
