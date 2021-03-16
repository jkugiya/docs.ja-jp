---
description: '詳細情報: <transportConfigurationTypes>'
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: d6ef92cf3bdd10fdc9b374f10aaa748cf4300529
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749273"
---
# \<transportConfigurationTypes>

<span data-ttu-id="30b8a-102">特定のトランスポートの型を識別する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="30b8a-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="30b8a-103">これはカスタム WAS プロトコルの追加に使用できます。</span><span class="sxs-lookup"><span data-stu-id="30b8a-103">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="30b8a-104">構文</span><span class="sxs-lookup"><span data-stu-id="30b8a-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30b8a-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="30b8a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="30b8a-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="30b8a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30b8a-107">属性</span><span class="sxs-lookup"><span data-stu-id="30b8a-107">Attributes</span></span>  
  
|<span data-ttu-id="30b8a-108">属性</span><span class="sxs-lookup"><span data-stu-id="30b8a-108">Attribute</span></span>|<span data-ttu-id="30b8a-109">説明</span><span class="sxs-lookup"><span data-stu-id="30b8a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30b8a-110">name</span><span class="sxs-lookup"><span data-stu-id="30b8a-110">name</span></span>|<span data-ttu-id="30b8a-111">トランスポートの名前</span><span class="sxs-lookup"><span data-stu-id="30b8a-111">The name of the transport</span></span>|  
|<span data-ttu-id="30b8a-112">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="30b8a-112">transportConfigurationType</span></span>|<span data-ttu-id="30b8a-113">トランスポートを実装する型</span><span class="sxs-lookup"><span data-stu-id="30b8a-113">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30b8a-114">子要素</span><span class="sxs-lookup"><span data-stu-id="30b8a-114">Child Elements</span></span>  
  
|<span data-ttu-id="30b8a-115">要素</span><span class="sxs-lookup"><span data-stu-id="30b8a-115">Element</span></span>|<span data-ttu-id="30b8a-116">説明</span><span class="sxs-lookup"><span data-stu-id="30b8a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="30b8a-117">特定のトランスポートの型を識別する構成要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="30b8a-117">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30b8a-118">親要素</span><span class="sxs-lookup"><span data-stu-id="30b8a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="30b8a-119">要素</span><span class="sxs-lookup"><span data-stu-id="30b8a-119">Element</span></span>|<span data-ttu-id="30b8a-120">説明</span><span class="sxs-lookup"><span data-stu-id="30b8a-120">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="30b8a-121">環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="30b8a-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30b8a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="30b8a-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="30b8a-123">ホスティング</span><span class="sxs-lookup"><span data-stu-id="30b8a-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
