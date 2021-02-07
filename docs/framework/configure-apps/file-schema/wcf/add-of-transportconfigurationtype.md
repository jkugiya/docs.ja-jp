---
description: 詳細については <add> 、 <transportConfigurationType>
title: <add> の <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 4a4a68e1f70bcb2ec7d55d5d6c3b530e71ddc55d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750014"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="ef212-103">\<add> の \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="ef212-103">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="ef212-104">この要素は、特定のトランスポートの種類を識別するキーと値のペアです。</span><span class="sxs-lookup"><span data-stu-id="ef212-104">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ef212-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef212-105">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef212-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ef212-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ef212-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef212-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef212-108">属性</span><span class="sxs-lookup"><span data-stu-id="ef212-108">Attributes</span></span>  
  
|<span data-ttu-id="ef212-109">属性</span><span class="sxs-lookup"><span data-stu-id="ef212-109">Attribute</span></span>|<span data-ttu-id="ef212-110">説明</span><span class="sxs-lookup"><span data-stu-id="ef212-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef212-111">name</span><span class="sxs-lookup"><span data-stu-id="ef212-111">name</span></span>|<span data-ttu-id="ef212-112">必須の文字列属性です。</span><span class="sxs-lookup"><span data-stu-id="ef212-112">Required String attribute.</span></span><br /><br /> <span data-ttu-id="ef212-113">トランスポートの種類を一意に識別するユーザー定義キーを含みます。</span><span class="sxs-lookup"><span data-stu-id="ef212-113">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="ef212-114">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="ef212-114">transportConfigurationType</span></span>|<span data-ttu-id="ef212-115">特定のトランスポートを実装する種類を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="ef212-115">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef212-116">子要素</span><span class="sxs-lookup"><span data-stu-id="ef212-116">Child Elements</span></span>  

 <span data-ttu-id="ef212-117">なし</span><span class="sxs-lookup"><span data-stu-id="ef212-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef212-118">親要素</span><span class="sxs-lookup"><span data-stu-id="ef212-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ef212-119">要素</span><span class="sxs-lookup"><span data-stu-id="ef212-119">Element</span></span>|<span data-ttu-id="ef212-120">説明</span><span class="sxs-lookup"><span data-stu-id="ef212-120">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="ef212-121">特定のトランスポートを実装する型のコレクション。</span><span class="sxs-lookup"><span data-stu-id="ef212-121">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef212-122">例</span><span class="sxs-lookup"><span data-stu-id="ef212-122">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="ef212-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef212-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="ef212-124">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ef212-124">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
