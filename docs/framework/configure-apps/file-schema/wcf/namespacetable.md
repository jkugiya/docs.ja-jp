---
description: '詳細情報: <namespaceTable>'
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 73bfac93fba3247c02c2d86d1482af2563015a76
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684088"
---
# \<namespaceTable>

<span data-ttu-id="56ac7-102">名前空間とプレフィックスのマッピングを含む要素セットを定義する構成セクションを表します。これは、ルーティングの XPath フィルターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="56ac7-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="56ac7-103">構文</span><span class="sxs-lookup"><span data-stu-id="56ac7-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56ac7-104">属性と要素</span><span class="sxs-lookup"><span data-stu-id="56ac7-104">Attributes and elements</span></span>

<span data-ttu-id="56ac7-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="56ac7-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="56ac7-106">属性</span><span class="sxs-lookup"><span data-stu-id="56ac7-106">Attributes</span></span>

<span data-ttu-id="56ac7-107">なし</span><span class="sxs-lookup"><span data-stu-id="56ac7-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="56ac7-108">子要素</span><span class="sxs-lookup"><span data-stu-id="56ac7-108">Child elements</span></span>

|     | <span data-ttu-id="56ac7-109">説明</span><span class="sxs-lookup"><span data-stu-id="56ac7-109">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="56ac7-110">XPath 式に使用される名前空間とプレフィックスのマッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="56ac7-110">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="56ac7-111">親要素</span><span class="sxs-lookup"><span data-stu-id="56ac7-111">Parent elements</span></span>

|     | <span data-ttu-id="56ac7-112">説明</span><span class="sxs-lookup"><span data-stu-id="56ac7-112">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="56ac7-113">一連のルーティングフィルターを定義するための構成セクションを表します。これにより、受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) の種類、 <xref:System.ServiceModel.Dispatcher.MessageFilter> およびフィルターが一致したときにメッセージを送信するターゲットエンドポイントを定義するルーティングテーブルが決定されます。</span><span class="sxs-lookup"><span data-stu-id="56ac7-113">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="56ac7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="56ac7-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
