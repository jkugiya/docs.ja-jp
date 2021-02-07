---
description: '詳細情報: <knownType>'
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 205f799c81263be3dd08aae9efefb975b06a0cc7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725507"
---
# \<knownType>

<span data-ttu-id="62765-102">逆シリアル化中に <xref:System.Runtime.Serialization.DataContractSerializer> によって使用される型を指定します。</span><span class="sxs-lookup"><span data-stu-id="62765-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="62765-103">この要素には、"宣言型" のフィールドまたはプロパティによって返される "既知の型" を指定します。</span><span class="sxs-lookup"><span data-stu-id="62765-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="62765-104">詳細については、「 [データコントラクトの既知の型](../../../wcf/feature-details/data-contract-known-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62765-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="62765-105">構文</span><span class="sxs-lookup"><span data-stu-id="62765-105">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="62765-106">Type</span><span class="sxs-lookup"><span data-stu-id="62765-106">Type</span></span>  

 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62765-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="62765-107">Attributes and Elements</span></span>  

 <span data-ttu-id="62765-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="62765-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62765-109">属性</span><span class="sxs-lookup"><span data-stu-id="62765-109">Attributes</span></span>  
  
|<span data-ttu-id="62765-110">属性</span><span class="sxs-lookup"><span data-stu-id="62765-110">Attribute</span></span>|<span data-ttu-id="62765-111">説明</span><span class="sxs-lookup"><span data-stu-id="62765-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62765-112">type</span><span class="sxs-lookup"><span data-stu-id="62765-112">type</span></span>|<span data-ttu-id="62765-113">型 (名前空間を含む)、アセンブリ名、バージョン、カルチャ、および公開キー トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="62765-113">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62765-114">子要素</span><span class="sxs-lookup"><span data-stu-id="62765-114">Child Elements</span></span>  
  
|<span data-ttu-id="62765-115">要素</span><span class="sxs-lookup"><span data-stu-id="62765-115">Element</span></span>|<span data-ttu-id="62765-116">説明</span><span class="sxs-lookup"><span data-stu-id="62765-116">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="62765-117">宣言型がジェネリック型である場合に、パラメーター インデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="62765-117">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62765-118">親要素</span><span class="sxs-lookup"><span data-stu-id="62765-118">Parent Elements</span></span>  
  
|<span data-ttu-id="62765-119">要素</span><span class="sxs-lookup"><span data-stu-id="62765-119">Element</span></span>|<span data-ttu-id="62765-120">説明</span><span class="sxs-lookup"><span data-stu-id="62765-120">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="62765-121">宣言されたタイプのコレクションに、宣言されたタイプを追加します。</span><span class="sxs-lookup"><span data-stu-id="62765-121">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62765-122">解説</span><span class="sxs-lookup"><span data-stu-id="62765-122">Remarks</span></span>  

 <span data-ttu-id="62765-123">既知の型の詳細については、「 [データコントラクトの既知の型](../../../wcf/feature-details/data-contract-known-types.md) 」と「」を参照してください <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="62765-123">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="62765-124">[\<dataContractSerializer>](datacontractserializer-element.md)この要素の使用例については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62765-124">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62765-125">例</span><span class="sxs-lookup"><span data-stu-id="62765-125">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="62765-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="62765-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="62765-127">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="62765-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
