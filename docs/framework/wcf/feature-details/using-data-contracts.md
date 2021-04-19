---
title: データ コントラクトの使用
description: 各パラメーターまたは戻り値の型に対して、WCF クライアントとサーバー間で交換するためにシリアル化されるデータを定義するデータ コントラクトについて説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 97d234d094abf7666a341493f6b394c73513fa70
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289868"
---
# <a name="using-data-contracts"></a><span data-ttu-id="5b32f-103">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="5b32f-103">Using Data Contracts</span></span>

<span data-ttu-id="5b32f-104">*データ コントラクト* は、サービスとクライアントの間の正式な取り決めであり、交換されるデータが抽象的に記述されています。</span><span class="sxs-lookup"><span data-stu-id="5b32f-104">A *data contract* is a formal agreement between a service and a client that abstractly describes the data to be exchanged.</span></span> <span data-ttu-id="5b32f-105">つまり、クライアントとサービスが通信するために必要なのは同じデータ コントラクトだけで、同じ型を共有する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5b32f-105">That is, to communicate, the client and the service do not have to share the same types, only the same data contracts.</span></span> <span data-ttu-id="5b32f-106">データ コントラクトは、パラメーターまたは戻り値の型ごとに、交換するためにシリアル化する (XML に変換する) 必要があるデータを正確に定義します。</span><span class="sxs-lookup"><span data-stu-id="5b32f-106">A data contract precisely defines, for each parameter or return type, what data is serialized (turned into XML) to be exchanged.</span></span>  
  
## <a name="data-contract-basics"></a><span data-ttu-id="5b32f-107">データ コントラクトの基本</span><span class="sxs-lookup"><span data-stu-id="5b32f-107">Data Contract Basics</span></span>  

 <span data-ttu-id="5b32f-108">Windows Communication Foundation (WCF) により、データ コントラクト シリアライザーと呼ばれるシリアル化エンジンが既定で使用されて、データのシリアル化と逆シリアル化 (データと XML の間の変換) が行われます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-108">Windows Communication Foundation (WCF) uses a serialization engine called the Data Contract Serializer by default to serialize and deserialize data (convert it to and from XML).</span></span> <span data-ttu-id="5b32f-109">すべての .NET Framework プリミティブ型 (整数や文字列など) およびプリミティブ型として扱われる特定の型 (<xref:System.DateTime> や <xref:System.Xml.XmlElement>など) は、準備なしでシリアル化できるため、既定のデータ コントラクトを持つと見なされます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-109">All .NET Framework primitive types, such as integers and strings, as well as certain types treated as primitives, such as <xref:System.DateTime> and <xref:System.Xml.XmlElement>, can be serialized with no other preparation and are considered as having default data contracts.</span></span> <span data-ttu-id="5b32f-110">多くの .NET Framework 型にも、既存のデータ コントラクトがあります。</span><span class="sxs-lookup"><span data-stu-id="5b32f-110">Many .NET Framework types also have existing data contracts.</span></span> <span data-ttu-id="5b32f-111">シリアル化できるすべての型の一覧については、「 [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b32f-111">For a full list of serializable types, see [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="5b32f-112">新しい複合型を作成したら、シリアル化できるように、データ コントラクトを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b32f-112">New complex types that you create must have a data contract defined for them to be serializable.</span></span> <span data-ttu-id="5b32f-113">既定では、 <xref:System.Runtime.Serialization.DataContractSerializer> はデータ コントラクトを推測し、公開されている型をすべてシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="5b32f-113">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> infers the data contract and serializes all publicly visible types.</span></span> <span data-ttu-id="5b32f-114">その型の読み書き可能なパブリック プロパティおよびパブリック フィールドは、すべてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-114">All public read/write properties and fields of the type are serialized.</span></span> <span data-ttu-id="5b32f-115"><xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>を使用することにより、メンバーがシリアル化されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-115">You can opt out members from serialization by using the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>.</span></span> <span data-ttu-id="5b32f-116">また、 <xref:System.Runtime.Serialization.DataContractAttribute> 属性および <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を使用して、データ コントラクトを明示的に作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-116">You can also explicitly create a data contract by using <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="5b32f-117">これを行うには、通常、その型に <xref:System.Runtime.Serialization.DataContractAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="5b32f-117">This is normally done by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="5b32f-118">この属性は、クラス、構造体、および列挙体に適用できます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-118">This attribute can be applied to classes, structures, and enumerations.</span></span> <span data-ttu-id="5b32f-119">次に、データ コントラクト型の各メンバーに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用して、それが *データ メンバー* であること、つまり、シリアル化する必要があることを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b32f-119">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute must then be applied to each member of the data contract type to indicate that it is a *data member*, that is, it should be serialized.</span></span> <span data-ttu-id="5b32f-120">詳細については、「[シリアル化可能な型](serializable-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b32f-120">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="5b32f-121">例</span><span class="sxs-lookup"><span data-stu-id="5b32f-121">Example</span></span>  

 <span data-ttu-id="5b32f-122"><xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性が明示的に適用されたサービス コントラクト (インターフェイス) の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5b32f-122">The following example shows a service contract (an interface) to which the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes have been explicitly applied.</span></span> <span data-ttu-id="5b32f-123">この例は、プリミティブ型はデータ コントラクトを必要としないのに対し、複合型は必要とすることを示しています。</span><span class="sxs-lookup"><span data-stu-id="5b32f-123">The example shows that primitive types do not require a data contract, while a complex type does.</span></span>  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 <span data-ttu-id="5b32f-124">次の例では、 `MyTypes.PurchaseOrder` 型のデータ コントラクトが作成され、 <xref:System.Runtime.Serialization.DataContractAttribute> と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性がクラスとそのメンバーに適用されるかを示します。</span><span class="sxs-lookup"><span data-stu-id="5b32f-124">The following example shows how a data contract for the `MyTypes.PurchaseOrder` type is created by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a><span data-ttu-id="5b32f-125">Notes</span><span class="sxs-lookup"><span data-stu-id="5b32f-125">Notes</span></span>  

 <span data-ttu-id="5b32f-126">以下に、データ コントラクトを作成する際に考慮する必要がある項目を示します。</span><span class="sxs-lookup"><span data-stu-id="5b32f-126">The following notes provide items to consider when creating data contracts:</span></span>  
  
- <span data-ttu-id="5b32f-127"><xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 属性は、マークされていない型で使用した場合にのみ受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-127">The <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute is only honored when used with unmarked types.</span></span> <span data-ttu-id="5b32f-128">これには、 <xref:System.Runtime.Serialization.DataContractAttribute>、 <xref:System.SerializableAttribute>、 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>、 <xref:System.Runtime.Serialization.EnumMemberAttribute> のいずれかの属性でマークされていない型、または他の方法 ( <xref:System.Xml.Serialization.IXmlSerializable>など) でシリアル化可能としてマークされた型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-128">This includes types that are not marked with one of the <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, or <xref:System.Runtime.Serialization.EnumMemberAttribute> attributes, or marked as serializable by any other means (such as <xref:System.Xml.Serialization.IXmlSerializable>).</span></span>  
  
- <span data-ttu-id="5b32f-129"><xref:System.Runtime.Serialization.DataMemberAttribute> 属性は、フィールドおよびプロパティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-129">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to fields, and properties.</span></span>  
  
- <span data-ttu-id="5b32f-130">メンバーのアクセシビリティ レベル (内部、プライベート、保護、またはパブリック) は、データ コントラクトに影響しません。</span><span class="sxs-lookup"><span data-stu-id="5b32f-130">Member accessibility levels (internal, private, protected, or public) do not affect the data contract in any way.</span></span>  
  
- <span data-ttu-id="5b32f-131"><xref:System.Runtime.Serialization.DataMemberAttribute> 属性が静的メンバーに適用されている場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-131">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is ignored if it is applied to static members.</span></span>  
  
- <span data-ttu-id="5b32f-132">シリアル化中には、プロパティのデータ メンバーがシリアル化対象のプロパティの値を取得できるように、プロパティ取得コードが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-132">During serialization, property-get code is called for property data members to get the value of the properties to be serialized.</span></span>  
  
- <span data-ttu-id="5b32f-133">逆シリアル化中には、まず初期化されていないオブジェクトが、その型のコンストラクターを呼び出さずに作成されます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-133">During deserialization, an uninitialized object is first created, without calling any constructors on the type.</span></span> <span data-ttu-id="5b32f-134">次に、すべてのデータ メンバーが逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-134">Then all data members are deserialized.</span></span>  
  
- <span data-ttu-id="5b32f-135">逆シリアル化中には、プロパティのデータ メンバーが、プロパティを逆シリアル化されている値に設定できるように、プロパティ設定コードが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-135">During deserialization, property-set code is called for property data members to set the properties to the value being deserialized.</span></span>  
  
- <span data-ttu-id="5b32f-136">データ コントラクトが有効であるためには、すべてのデータ メンバーをシリアル化できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b32f-136">For a data contract to be valid, it must be possible to serialize all of its data members.</span></span> <span data-ttu-id="5b32f-137">シリアル化できるすべての型の一覧については、「 [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b32f-137">For a full list of serializable types, see [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).</span></span>  
  
     <span data-ttu-id="5b32f-138">ジェネリック型は、非ジェネリック型とまったく同じように処理されます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-138">Generic types are handled in exactly the same way as non-generic types.</span></span> <span data-ttu-id="5b32f-139">ジェネリック パラメーターに対する特別な要件はありません。</span><span class="sxs-lookup"><span data-stu-id="5b32f-139">There are no special requirements for generic parameters.</span></span> <span data-ttu-id="5b32f-140">たとえば、次の型について考えます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-140">For example, consider the following type.</span></span>  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 <span data-ttu-id="5b32f-141">この型は、ジェネリック型パラメーター (`T`) に使用される型をシリアル化できるかどうかに関係なくシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="5b32f-141">This type is serializable whether the type used for the generic type parameter (`T`) is serializable or not.</span></span> <span data-ttu-id="5b32f-142">すべてのデータ メンバーをシリアル化できる必要があるため、次の型をシリアル化できるのは、ジェネリック型パラメーターもシリアル化できる場合だけです。次のコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b32f-142">Because it must be possible to serialize all data members, the following type is serializable only if the generic type parameter is also serializable, as shown in the following code.</span></span>  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 <span data-ttu-id="5b32f-143">データ コントラクトを定義する WCF サービスのコード サンプル全体については、「 [Basic Data Contract](../samples/basic-data-contract.md) 」のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b32f-143">For a complete code sample of a WCF service that defines a data contract see the [Basic Data Contract](../samples/basic-data-contract.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b32f-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b32f-144">See also</span></span>

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="5b32f-145">シリアル化可能な型</span><span class="sxs-lookup"><span data-stu-id="5b32f-145">Serializable Types</span></span>](serializable-types.md)
- [<span data-ttu-id="5b32f-146">データ コントラクト名</span><span class="sxs-lookup"><span data-stu-id="5b32f-146">Data Contract Names</span></span>](data-contract-names.md)
- [<span data-ttu-id="5b32f-147">データ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="5b32f-147">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="5b32f-148">データ メンバーの順序</span><span class="sxs-lookup"><span data-stu-id="5b32f-148">Data Member Order</span></span>](data-member-order.md)
- [<span data-ttu-id="5b32f-149">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="5b32f-149">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="5b32f-150">上位互換性のあるデータ コントラクト</span><span class="sxs-lookup"><span data-stu-id="5b32f-150">Forward-Compatible Data Contracts</span></span>](forward-compatible-data-contracts.md)
- [<span data-ttu-id="5b32f-151">データ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="5b32f-151">Data Contract Versioning</span></span>](data-contract-versioning.md)
- [<span data-ttu-id="5b32f-152">バージョン トレラントなシリアル化コールバック</span><span class="sxs-lookup"><span data-stu-id="5b32f-152">Version-Tolerant Serialization Callbacks</span></span>](version-tolerant-serialization-callbacks.md)
- [<span data-ttu-id="5b32f-153">データ メンバーの既定値</span><span class="sxs-lookup"><span data-stu-id="5b32f-153">Data Member Default Values</span></span>](data-member-default-values.md)
- [<span data-ttu-id="5b32f-154">データ コントラクト シリアライザーでサポートされる型</span><span class="sxs-lookup"><span data-stu-id="5b32f-154">Types Supported by the Data Contract Serializer</span></span>](types-supported-by-the-data-contract-serializer.md)
- [<span data-ttu-id="5b32f-155">方法: クラスまたは構造体に基本的なデータ コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="5b32f-155">How to: Create a Basic Data Contract for a Class or Structure</span></span>](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
