---
description: '詳細情報: <useManagedPresentation>'
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 9203daedcc0553c7a1308b2763b9e818ca6560c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749039"
---
# \<useManagedPresentation>

<span data-ttu-id="d739f-102">WS-Trust の CardSpace プロファイルをサポートする CardSpace セキュリティ トークン サービスとの通信に使用するバインド要素。</span><span class="sxs-lookup"><span data-stu-id="d739f-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="d739f-103">この要素には属性がなく、空のスイッチとして表されます。</span><span class="sxs-lookup"><span data-stu-id="d739f-103">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="d739f-104">構文</span><span class="sxs-lookup"><span data-stu-id="d739f-104">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d739f-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d739f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d739f-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d739f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d739f-107">属性</span><span class="sxs-lookup"><span data-stu-id="d739f-107">Attributes</span></span>  

 <span data-ttu-id="d739f-108">なし。</span><span class="sxs-lookup"><span data-stu-id="d739f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d739f-109">子要素</span><span class="sxs-lookup"><span data-stu-id="d739f-109">Child Elements</span></span>  

 <span data-ttu-id="d739f-110">なし</span><span class="sxs-lookup"><span data-stu-id="d739f-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d739f-111">親要素</span><span class="sxs-lookup"><span data-stu-id="d739f-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d739f-112">要素</span><span class="sxs-lookup"><span data-stu-id="d739f-112">Element</span></span>|<span data-ttu-id="d739f-113">説明</span><span class="sxs-lookup"><span data-stu-id="d739f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d739f-114">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="d739f-114">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d739f-115">解説</span><span class="sxs-lookup"><span data-stu-id="d739f-115">Remarks</span></span>  

 <span data-ttu-id="d739f-116">この要素は、WS-Trust の CardSpace プロファイルをサポートするという事実をポリシーで明示するために、ID プロバイダーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d739f-116">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="d739f-117">このようなポリシー アサーションを公開する ID プロバイダーは、その CardSpace プロファイルに基づくトークンを発行できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d739f-117">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d739f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d739f-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d739f-119">バインド</span><span class="sxs-lookup"><span data-stu-id="d739f-119">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d739f-120">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="d739f-120">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d739f-121">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="d739f-121">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
