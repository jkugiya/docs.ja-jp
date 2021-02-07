---
description: 詳細については <add> 、 <namespaceTable>
title: <add> の <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: b7804bdec4a1fb2199c81ba0dde031b80b451d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750261"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="ab643-103">\<add> の \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="ab643-103">\<add> of \<namespaceTable></span></span>

<span data-ttu-id="ab643-104">名前空間とプレフィックスのマッピングを含む構成要素を表します。これは、ルーティングの XPath フィルターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ab643-104">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ab643-105">構文</span><span class="sxs-lookup"><span data-stu-id="ab643-105">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab643-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ab643-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ab643-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab643-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab643-108">属性</span><span class="sxs-lookup"><span data-stu-id="ab643-108">Attributes</span></span>  
  
|<span data-ttu-id="ab643-109">属性</span><span class="sxs-lookup"><span data-stu-id="ab643-109">Attribute</span></span>|<span data-ttu-id="ab643-110">説明</span><span class="sxs-lookup"><span data-stu-id="ab643-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab643-111">namespace</span><span class="sxs-lookup"><span data-stu-id="ab643-111">namespace</span></span>|<span data-ttu-id="ab643-112">名前空間を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="ab643-112">A string containing the namespace.</span></span>|  
|<span data-ttu-id="ab643-113">prefix</span><span class="sxs-lookup"><span data-stu-id="ab643-113">prefix</span></span>|<span data-ttu-id="ab643-114">この名前空間のプレフィックスを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="ab643-114">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab643-115">子要素</span><span class="sxs-lookup"><span data-stu-id="ab643-115">Child Elements</span></span>  

 <span data-ttu-id="ab643-116">なし。</span><span class="sxs-lookup"><span data-stu-id="ab643-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab643-117">親要素</span><span class="sxs-lookup"><span data-stu-id="ab643-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ab643-118">要素</span><span class="sxs-lookup"><span data-stu-id="ab643-118">Element</span></span>|<span data-ttu-id="ab643-119">説明</span><span class="sxs-lookup"><span data-stu-id="ab643-119">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="ab643-120">名前空間とプレフィックスのマッピングを含む要素セットを定義する構成セクションを表します。これは、ルーティングの XPath フィルターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ab643-120">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab643-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab643-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
