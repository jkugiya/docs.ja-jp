---
description: '詳細情報: <extensions> セクション'
title: <extensions> 下
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 65b1de76155b1e3fbd8e5f14a5f4a1cb8c180ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664692"
---
# <a name="extensions-section"></a><span data-ttu-id="13058-103">\<extensions> 下</span><span class="sxs-lookup"><span data-stu-id="13058-103">\<extensions> section</span></span>

<span data-ttu-id="13058-104">この構成セクションには、拡張のコレクションが含まれています。この拡張のコレクションによってユーザーは、ユーザー定義のバインディング、動作、およびその他の拡張機能を作成できます。</span><span class="sxs-lookup"><span data-stu-id="13058-104">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="13058-105">構文</span><span class="sxs-lookup"><span data-stu-id="13058-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13058-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="13058-106">Attributes and Elements</span></span>  

 <span data-ttu-id="13058-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="13058-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13058-108">属性</span><span class="sxs-lookup"><span data-stu-id="13058-108">Attributes</span></span>  

 <span data-ttu-id="13058-109">なし。</span><span class="sxs-lookup"><span data-stu-id="13058-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="13058-110">子要素</span><span class="sxs-lookup"><span data-stu-id="13058-110">Child Elements</span></span>  
  
|<span data-ttu-id="13058-111">要素</span><span class="sxs-lookup"><span data-stu-id="13058-111">Element</span></span>|<span data-ttu-id="13058-112">説明</span><span class="sxs-lookup"><span data-stu-id="13058-112">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="13058-113">このセクションには、動作拡張を指定する子要素が含まれています。この動作拡張により、ユーザーはサービスまたはエンドポイントの動作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="13058-113">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="13058-114">このセクションは、コンピューターまたはアプリケーションの構成ファイルからカスタム バインディング要素を使用できます。</span><span class="sxs-lookup"><span data-stu-id="13058-114">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="13058-115">このセクションには、バインディング拡張を指定する子要素が含まれています。このバインディング拡張によって、ユーザーはバインディングをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="13058-115">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="13058-116">このセクションには、標準エンドポイントを登録する子要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="13058-116">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13058-117">親要素</span><span class="sxs-lookup"><span data-stu-id="13058-117">Parent Elements</span></span>  
  
|<span data-ttu-id="13058-118">要素</span><span class="sxs-lookup"><span data-stu-id="13058-118">Element</span></span>|<span data-ttu-id="13058-119">説明</span><span class="sxs-lookup"><span data-stu-id="13058-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13058-120">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="13058-120">system.ServiceModel</span></span>|<span data-ttu-id="13058-121">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="13058-121">The root element of all WCF configuration elements.</span></span>|
