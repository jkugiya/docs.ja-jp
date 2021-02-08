---
description: '詳細については、次を参照してください: <add> of <declaredTypes> 要素'
title: <add><declaredTypes>要素の
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 8e2be6e553ee5dc5c96bcae81d1c1c6bf609afed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803985"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="53429-103">\<add>\<declaredTypes>要素の</span><span class="sxs-lookup"><span data-stu-id="53429-103">\<add> of \<declaredTypes> Element</span></span>

<span data-ttu-id="53429-104">逆シリアル化中に、<xref:System.Runtime.Serialization.DataContractSerializer> で使用される型を追加します。</span><span class="sxs-lookup"><span data-stu-id="53429-104">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="53429-105">各宣言型は、宣言型のフィールドまたはプロパティとして返される既知の型を含みます。</span><span class="sxs-lookup"><span data-stu-id="53429-105">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="53429-106">構文</span><span class="sxs-lookup"><span data-stu-id="53429-106">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53429-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="53429-107">Attributes and Elements</span></span>  

 <span data-ttu-id="53429-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="53429-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53429-109">属性</span><span class="sxs-lookup"><span data-stu-id="53429-109">Attributes</span></span>  
  
|<span data-ttu-id="53429-110">属性</span><span class="sxs-lookup"><span data-stu-id="53429-110">Attribute</span></span>|<span data-ttu-id="53429-111">説明</span><span class="sxs-lookup"><span data-stu-id="53429-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53429-112">type</span><span class="sxs-lookup"><span data-stu-id="53429-112">type</span></span>|<span data-ttu-id="53429-113">必須の文字列属性です。</span><span class="sxs-lookup"><span data-stu-id="53429-113">Required string attribute.</span></span><br /><br /> <span data-ttu-id="53429-114">型名 (名前空間を含む)、アセンブリ名、バージョン番号、カルチャ、および公開キー トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="53429-114">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53429-115">子要素</span><span class="sxs-lookup"><span data-stu-id="53429-115">Child Elements</span></span>  
  
|<span data-ttu-id="53429-116">要素</span><span class="sxs-lookup"><span data-stu-id="53429-116">Element</span></span>|<span data-ttu-id="53429-117">説明</span><span class="sxs-lookup"><span data-stu-id="53429-117">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="53429-118">追加される宣言型の既知の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="53429-118">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="53429-119">宣言型がジェネリック型の場合は、既知の型を返すために使用されるジェネリック パラメーターを指定するために、`<knownType>` にパラメーター要素も追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53429-119">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53429-120">親要素</span><span class="sxs-lookup"><span data-stu-id="53429-120">Parent Elements</span></span>  
  
|<span data-ttu-id="53429-121">要素</span><span class="sxs-lookup"><span data-stu-id="53429-121">Element</span></span>|<span data-ttu-id="53429-122">説明</span><span class="sxs-lookup"><span data-stu-id="53429-122">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="53429-123"><xref:System.Runtime.Serialization.DataContractSerializer> による逆シリアル化中に既知のタイプを必要とするタイプが含まれています。</span><span class="sxs-lookup"><span data-stu-id="53429-123">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53429-124">解説</span><span class="sxs-lookup"><span data-stu-id="53429-124">Remarks</span></span>  

 <span data-ttu-id="53429-125">既知の型の詳細については、「 [データコントラクトの既知の型](../../../wcf/feature-details/data-contract-known-types.md) 」と「」を参照してください <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="53429-125">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="53429-126">[\<dataContractSerializer>](datacontractserializer-element.md)この要素の使用例については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53429-126">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53429-127"><xref:System.Object> 型を `<declaredType>` として追加すると、<xref:System.Configuration.ConfigurationErrorsException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="53429-127">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="53429-128">これは、構成で <xref:System.Object> 型を宣言型として使用できないためです。</span><span class="sxs-lookup"><span data-stu-id="53429-128">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53429-129">例</span><span class="sxs-lookup"><span data-stu-id="53429-129">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="53429-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="53429-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="53429-131">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="53429-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="53429-132">\<declaredTypes> の \<add></span><span class="sxs-lookup"><span data-stu-id="53429-132">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
