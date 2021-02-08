---
description: '詳細情報: <declaredTypes>'
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: e5f60209dd556edc7cf47b01b1a58c1f17d74eac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803933"
---
# \<declaredTypes>

<span data-ttu-id="0fff8-102">逆シリアル化時に <xref:System.Runtime.Serialization.DataContractSerializer> が使用する既知の型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0fff8-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="0fff8-103">データコントラクトと既知の型の詳細については、「 [データコントラクトの既知の型](../../../wcf/feature-details/data-contract-known-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fff8-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="0fff8-104">構文</span><span class="sxs-lookup"><span data-stu-id="0fff8-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fff8-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0fff8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0fff8-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0fff8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fff8-107">属性</span><span class="sxs-lookup"><span data-stu-id="0fff8-107">Attributes</span></span>  

 <span data-ttu-id="0fff8-108">なし。</span><span class="sxs-lookup"><span data-stu-id="0fff8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fff8-109">子要素</span><span class="sxs-lookup"><span data-stu-id="0fff8-109">Child Elements</span></span>  
  
|<span data-ttu-id="0fff8-110">要素</span><span class="sxs-lookup"><span data-stu-id="0fff8-110">Element</span></span>|<span data-ttu-id="0fff8-111">説明</span><span class="sxs-lookup"><span data-stu-id="0fff8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="0fff8-112">既知の型を必要とする型を追加します。</span><span class="sxs-lookup"><span data-stu-id="0fff8-112">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fff8-113">親要素</span><span class="sxs-lookup"><span data-stu-id="0fff8-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0fff8-114">要素</span><span class="sxs-lookup"><span data-stu-id="0fff8-114">Element</span></span>|<span data-ttu-id="0fff8-115">説明</span><span class="sxs-lookup"><span data-stu-id="0fff8-115">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="0fff8-116"><xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0fff8-116">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fff8-117">解説</span><span class="sxs-lookup"><span data-stu-id="0fff8-117">Remarks</span></span>  

 <span data-ttu-id="0fff8-118">既知の型の詳細については、「 [データコントラクトの既知の型](../../../wcf/feature-details/data-contract-known-types.md) 」と「」を参照してください <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="0fff8-118">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fff8-119">例</span><span class="sxs-lookup"><span data-stu-id="0fff8-119">Example</span></span>  

 <span data-ttu-id="0fff8-120">次の XML コードは、要素に追加された宣言型と既知の型を示して `DataContractSerializer` います。</span><span class="sxs-lookup"><span data-stu-id="0fff8-120">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="0fff8-121">この例は、追加された 3 つの型を示しています。</span><span class="sxs-lookup"><span data-stu-id="0fff8-121">The example shows three types being added.</span></span> <span data-ttu-id="0fff8-122">最初の型は、"Item" という既知の型を使用する "Orders" という名前のカスタム型です。</span><span class="sxs-lookup"><span data-stu-id="0fff8-122">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="0fff8-123">2 つ目の宣言型は、既知の型として <xref:System.Collections.Generic.List%601> を使用する `Item` です。</span><span class="sxs-lookup"><span data-stu-id="0fff8-123">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="0fff8-124">最後の 3 つ目の宣言型は、<xref:System.Collections.Generic.Dictionary%602> です。</span><span class="sxs-lookup"><span data-stu-id="0fff8-124">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="0fff8-125"><xref:System.Collections.Generic.Dictionary%602> クラスの型は、2 種類のパラメーターを持つジェネリック型です。</span><span class="sxs-lookup"><span data-stu-id="0fff8-125">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="0fff8-126">最初のパラメーターはキーを表し、2 番目のパラメーターは値を表します。</span><span class="sxs-lookup"><span data-stu-id="0fff8-126">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="0fff8-127">次の例は、2 番目の型 (値) の <xref:System.Collections.Generic.List%601> を既知の型の一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="0fff8-127">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="0fff8-128">`index` 属性を使用して、既知の型で使用する型パラメーターを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fff8-128">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="0fff8-129">この場合には、"1" に設定された index 属性 (コレクションは 0 から始まる) によって値型が示されます。</span><span class="sxs-lookup"><span data-stu-id="0fff8-129">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="0fff8-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fff8-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="0fff8-131">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="0fff8-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
