---
title: データ コントラクトの列挙型
description: データ コントラクト モデルにより、列挙型が WFC プログラミング モデルの一部としてどのように表現されるかについて説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 88bf2513435a9c00cf11a0681b32871992c8d2b2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276660"
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="dfbe7-103">データ コントラクトの列挙型</span><span class="sxs-lookup"><span data-stu-id="dfbe7-103">Enumeration Types in Data Contracts</span></span>

<span data-ttu-id="dfbe7-104">列挙はデータ コントラクト モデルで表現できます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-104">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="dfbe7-105">このトピックでは、いくつかの例を通してプログラミング モデルを説明します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-105">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="dfbe7-106">列挙の基本</span><span class="sxs-lookup"><span data-stu-id="dfbe7-106">Enumeration Basics</span></span>  

 <span data-ttu-id="dfbe7-107">データ コントラクト モデルで列挙型を使用する 1 つの方法として、<xref:System.Runtime.Serialization.DataContractAttribute> 属性を型に割り当てる方法があります。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-107">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="dfbe7-108">この場合、データ コントラクトに含める必要のある各メンバーに <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-108">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="dfbe7-109">2 つのクラスを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-109">The following example shows two classes.</span></span> <span data-ttu-id="dfbe7-110">1 つ目は列挙を使用し、2 つ目は列挙を定義します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-110">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="dfbe7-111">`Car` クラスのインスタンスは、`condition` フィールドの値が `New`、`Used`、`Rental` のいずれかに設定されている場合にのみ送受信できます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-111">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="dfbe7-112">`condition` が、`Broken` または `Stolen` の場合、<xref:System.Runtime.Serialization.SerializationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-112">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="dfbe7-113"><xref:System.Runtime.Serialization.DataContractAttribute> プロパティ (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> と <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) を、列挙データ コントラクトとして通常通り使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-113">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="dfbe7-114">列挙メンバー値</span><span class="sxs-lookup"><span data-stu-id="dfbe7-114">Enumeration Member Values</span></span>  

 <span data-ttu-id="dfbe7-115">通常、データ コントラクトには、数値ではなく列挙メンバー名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-115">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="dfbe7-116">ただし、データ コントラクト モデルを使用しているときに、受信側が WCF クライアントである場合、エクスポートされたスキーマは数値を保持します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-116">However, when using the data contract model, if the receiving side is a WCF client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="dfbe7-117">これは、「[XmlSerializer クラスの使用](using-the-xmlserializer-class.md)」使用している場合は、当てはまらないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-117">Note that this is not the case when using the [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="dfbe7-118">前の例では、`condition` が `Used` に設定され、データが XML にシリアル化されると、結果の XML は `<condition>Used</condition>` になりますが `<condition>1</condition>` にはなりません。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-118">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="dfbe7-119">したがって、次のデータ コントラクトは、`CarConditionEnum` のデータ コントラクトと同じです。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-119">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="dfbe7-120">たとえば、`CarConditionEnum` を送信側で使用し、`CarConditionWithNumbers` を受信側で使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-120">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="dfbe7-121">送信側で `Used` に値 "1" を使用し、受信側で値 "20" を使用しても、XML 表現は送信側と受信側共に `<condition>Used</condition>` です。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-121">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="dfbe7-122">データ コントラクトに含めるには、<xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-122">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="dfbe7-123">.NET Framework では、列挙に特殊な値 0 (ゼロ) を常に割り当てることができます。これはまた、すべての列挙の既定値になります。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-123">In the .NET Framework, you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="dfbe7-124">ただし、この特殊値ゼロも <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を使用してマークされない限りシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-124">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="dfbe7-125">これには、次のような 2 つの例外があります。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-125">There are two exceptions to this:</span></span>  
  
- <span data-ttu-id="dfbe7-126">フラグ列挙体 (このトピックの後で説明)</span><span class="sxs-lookup"><span data-stu-id="dfbe7-126">Flag enumerations (discussed later in this topic).</span></span>  
  
- <span data-ttu-id="dfbe7-127"><xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> プロパティが `false` に設定された列挙データ メンバー (この場合、値がゼロの列挙はシリアル化されたデータから除外される)</span><span class="sxs-lookup"><span data-stu-id="dfbe7-127">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="dfbe7-128">列挙メンバー値のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="dfbe7-128">Customizing Enumeration Member Values</span></span>  

 <span data-ttu-id="dfbe7-129">データ コントラクトの一部を形成する列挙メンバー値は、<xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> 属性の <xref:System.Runtime.Serialization.EnumMemberAttribute> プロパティを使ってカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-129">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="dfbe7-130">たとえば、次のデータ コントラクトは `CarConditionEnum` のデータ コントラクトとも等価です。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-130">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="dfbe7-131">シリアル化されると、`PreviouslyOwned` の値には XML 表現 `<condition>Used</condition>` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-131">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="dfbe7-132">単純な列挙</span><span class="sxs-lookup"><span data-stu-id="dfbe7-132">Simple Enumerations</span></span>  

 <span data-ttu-id="dfbe7-133"><xref:System.Runtime.Serialization.DataContractAttribute> 属性が割り当てられていない列挙型をシリアル化することもできます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-133">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="dfbe7-134">このような列挙型は、前の説明とまったく同じように扱われます。ただし、すべてのメンバー (<xref:System.NonSerializedAttribute> 属性は適用されていない) に <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性が適用されているかのように扱われる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-134">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="dfbe7-135">たとえば、次の列挙は、前の `CarConditionEnum` の例と同じデータ コントラクトが暗黙的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-135">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="dfbe7-136">列挙のデータ コントラクト名と名前空間、および列挙メンバー値をカスタマイズする必要がない場合に、単純な列挙を使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-136">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="dfbe7-137">単純な列挙に関するメモ</span><span class="sxs-lookup"><span data-stu-id="dfbe7-137">Notes on Simple Enumerations</span></span>  

 <span data-ttu-id="dfbe7-138"><xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を単純な列挙に適用しても効力はありません。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-138">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="dfbe7-139"><xref:System.SerializableAttribute> 属性を列挙に適用してもしなくても変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-139">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="dfbe7-140"><xref:System.Runtime.Serialization.DataContractSerializer> クラスが、列挙メンバーに適用された <xref:System.NonSerializedAttribute> 属性を受け入れるという事実は、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> と <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> の動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-140">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="dfbe7-141">この 2 つのシリアライザーは <xref:System.NonSerializedAttribute> 属性を無視します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-141">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="dfbe7-142">フラグ列挙体</span><span class="sxs-lookup"><span data-stu-id="dfbe7-142">Flag Enumerations</span></span>  

 <span data-ttu-id="dfbe7-143">列挙体に <xref:System.FlagsAttribute> 属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-143">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="dfbe7-144">この場合、ゼロ個以上の列挙値のリストを同時に送受信できます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-144">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="dfbe7-145">これを行うには、<xref:System.Runtime.Serialization.DataContractAttribute> 属性をフラグ列挙体に適用し、2 の累乗であるすべてのメンバーを、<xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を使用してマークします。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-145">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="dfbe7-146">フラグ列挙体を使用するには、数列は (1、2、4、8、16、32、64 のように) 2 の累乗の連続である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-146">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="dfbe7-147">フラグの列挙値を送信する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-147">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1. <span data-ttu-id="dfbe7-148">数値にマップする列挙メンバー (<xref:System.Runtime.Serialization.EnumMemberAttribute> 属性が適用されている) の検索を試みます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-148">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="dfbe7-149">見つかった場合、そのメンバーのみを含むリストを送信します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-149">If found, send a list that contains just that member.</span></span>  
  
2. <span data-ttu-id="dfbe7-150">合計の各部にマップされる列挙メンバー (それぞれに <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性が適用されている) が存在するような形で、数値をこの合計に分割します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-150">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="dfbe7-151">このメンバーすべてのリストを送信します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-151">Send the list of all these members.</span></span> <span data-ttu-id="dfbe7-152">このような合計を見つけるために、*最長一致アルゴリズム* が使用されることに注意してください。したがって、このような合計が存在したとしても見つかるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-152">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="dfbe7-153">この問題を回避するには、列挙メンバーの数値を必ず 2 の累乗数にします。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-153">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3. <span data-ttu-id="dfbe7-154">前の 2 つの手順が失敗し、数値がゼロ以外の場合、<xref:System.Runtime.Serialization.SerializationException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-154">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="dfbe7-155">数値がゼロの場合、空のリストを送信します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-155">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="dfbe7-156">例</span><span class="sxs-lookup"><span data-stu-id="dfbe7-156">Example</span></span>  

 <span data-ttu-id="dfbe7-157">フラグ操作で使用できる列挙の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-157">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="dfbe7-158">次の各値は、示されているようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="dfbe7-158">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="dfbe7-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfbe7-159">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="dfbe7-160">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="dfbe7-160">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="dfbe7-161">サービス コントラクトでのデータ転送の指定</span><span class="sxs-lookup"><span data-stu-id="dfbe7-161">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)
