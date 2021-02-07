---
description: '詳細情報: <parameter>'
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: fb04cfb5bf451cdb99c23ae41ea8fafeb13f0d11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683815"
---
# \<parameter>

<span data-ttu-id="589f6-102">宣言された型がジェネリック型である場合、ジェネリック パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="589f6-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="589f6-103">構文</span><span class="sxs-lookup"><span data-stu-id="589f6-103">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="589f6-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="589f6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="589f6-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="589f6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="589f6-106">属性</span><span class="sxs-lookup"><span data-stu-id="589f6-106">Attributes</span></span>  
  
|<span data-ttu-id="589f6-107">属性</span><span class="sxs-lookup"><span data-stu-id="589f6-107">Attribute</span></span>|<span data-ttu-id="589f6-108">説明</span><span class="sxs-lookup"><span data-stu-id="589f6-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="589f6-109">インデックス</span><span class="sxs-lookup"><span data-stu-id="589f6-109">index</span></span>|<span data-ttu-id="589f6-110">宣言された型がジェネリック型である場合、既知の型を返すジェネリック パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="589f6-110">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="589f6-111">type</span><span class="sxs-lookup"><span data-stu-id="589f6-111">type</span></span>|<span data-ttu-id="589f6-112">シリアル化と逆シリアル化で使用される既知の型を説明する文字列。</span><span class="sxs-lookup"><span data-stu-id="589f6-112">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="589f6-113">index 属性</span><span class="sxs-lookup"><span data-stu-id="589f6-113">index Attribute</span></span>  
  
|<span data-ttu-id="589f6-114">値</span><span class="sxs-lookup"><span data-stu-id="589f6-114">Value</span></span>|<span data-ttu-id="589f6-115">説明</span><span class="sxs-lookup"><span data-stu-id="589f6-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="589f6-116">"0"</span><span class="sxs-lookup"><span data-stu-id="589f6-116">"0"</span></span>|<span data-ttu-id="589f6-117">ジェネリック型の最初のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="589f6-117">The first parameter in the generic type.</span></span> <span data-ttu-id="589f6-118">たとえば、<xref:System.Collections.Generic.List%601> にはパラメーターが 1 つだけあります。</span><span class="sxs-lookup"><span data-stu-id="589f6-118">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="589f6-119">宣言型として使用される場合、index は "0" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="589f6-119">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="589f6-120">"1"</span><span class="sxs-lookup"><span data-stu-id="589f6-120">"1"</span></span>|<span data-ttu-id="589f6-121">ジェネリック型の 2 番目のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="589f6-121">The second parameter in a generic type.</span></span> <span data-ttu-id="589f6-122">たとえば、<xref:System.Collections.Generic.Dictionary%602> には 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="589f6-122">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="589f6-123">2 番目のパラメーターによって既知の型が返される場合は、index 属性を "1" に設定します。</span><span class="sxs-lookup"><span data-stu-id="589f6-123">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="589f6-124">子要素</span><span class="sxs-lookup"><span data-stu-id="589f6-124">Child Elements</span></span>  

 <span data-ttu-id="589f6-125">なし。</span><span class="sxs-lookup"><span data-stu-id="589f6-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="589f6-126">親要素</span><span class="sxs-lookup"><span data-stu-id="589f6-126">Parent Elements</span></span>  
  
|<span data-ttu-id="589f6-127">要素</span><span class="sxs-lookup"><span data-stu-id="589f6-127">Element</span></span>|<span data-ttu-id="589f6-128">説明</span><span class="sxs-lookup"><span data-stu-id="589f6-128">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="589f6-129">宣言型のフィールドまたはプロパティによって返される既知の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="589f6-129">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="589f6-130">解説</span><span class="sxs-lookup"><span data-stu-id="589f6-130">Remarks</span></span>  

 <span data-ttu-id="589f6-131">既知の型の詳細については、「 [データコントラクトの既知の型](../../../wcf/feature-details/data-contract-known-types.md) 」と「」を参照してください <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="589f6-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="589f6-132">[\<dataContractSerializer>](datacontractserializer-element.md)この要素の使用例については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="589f6-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="589f6-133">この構成要素に、両方の属性を同時に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="589f6-133">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="589f6-134">両方の属性が設定された場合、<xref:System.Configuration.ConfigurationErrorsException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="589f6-134">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="589f6-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="589f6-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="589f6-136">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="589f6-136">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
