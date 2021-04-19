---
title: 既知のデータ コントラクト型
description: データ コントラクト モデルで、KnownTypeAttribute クラスを使用して、WCF での逆シリアル化中に含める型を指定する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 124083d86c220451c55a9290c2edf996b50d8d28
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286683"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="f6925-103">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="f6925-103">Data Contract Known Types</span></span>

<span data-ttu-id="f6925-104"><xref:System.Runtime.Serialization.KnownTypeAttribute> クラスを使用すると、逆シリアル化において考慮する必要のある型を事前に指定できます。</span><span class="sxs-lookup"><span data-stu-id="f6925-104">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="f6925-105">実施例については、「 [Known Types](../samples/known-types.md) 」の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6925-105">For a working example, see the [Known Types](../samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="f6925-106">通常は、クライアントとサービス間でパラメーターを渡したり、値を返したりするときに、転送するデータのデータ コントラクトのすべてが両方のエンドポイントで共有されます。</span><span class="sxs-lookup"><span data-stu-id="f6925-106">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="f6925-107">ただし、次の場合はこれが該当しません。</span><span class="sxs-lookup"><span data-stu-id="f6925-107">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="f6925-108">送信データ コントラクトが、予想データ コントラクトから派生する場合。</span><span class="sxs-lookup"><span data-stu-id="f6925-108">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="f6925-109">詳細については、「[データ コントラクトの等価性](data-contract-equivalence.md)」の継承に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6925-109">For more information, see the section about inheritance in [Data Contract Equivalence](data-contract-equivalence.md)).</span></span> <span data-ttu-id="f6925-110">この場合、送信されるデータには、受信エンドポイントで予想しているデータ コントラクトが含まれません。</span><span class="sxs-lookup"><span data-stu-id="f6925-110">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="f6925-111">クラス、構造体、または列挙とは対照的に、送信される情報の宣言型がインターフェイスである場合。</span><span class="sxs-lookup"><span data-stu-id="f6925-111">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="f6925-112">したがって、インターフェイスを実装するどの型が実際に送信されるかを事前に知ることができないため、受信エンドポイントでは送信されるデータのデータ コントラクトを事前に確認することができません。</span><span class="sxs-lookup"><span data-stu-id="f6925-112">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="f6925-113">送信される情報の宣言型が <xref:System.Object>である場合。</span><span class="sxs-lookup"><span data-stu-id="f6925-113">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="f6925-114">すべての型が <xref:System.Object>から継承され、どの型が実際に送信されるかを事前に知ることができないため、受信エンドポイントでは送信されるデータのデータ コントラクトを事前に確認することができません。</span><span class="sxs-lookup"><span data-stu-id="f6925-114">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="f6925-115">これは最初の項目についての特殊なケースです。すべてのデータ コントラクトは既定で、 <xref:System.Object>に対して生成された空のデータ コントラクトから派生します。</span><span class="sxs-lookup"><span data-stu-id="f6925-115">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="f6925-116">.NET Framework 型を含む一部の型に、前述した 3 つのカテゴリの 1 つに分類されるメンバーが含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="f6925-116">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="f6925-117">たとえば、 <xref:System.Collections.Hashtable> は <xref:System.Object> を使用して、ハッシュ テーブルに実際のオブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="f6925-117">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="f6925-118">これらの型をシリアル化する場合、受信側ではこれらのメンバーのデータ コントラクトを事前に確認することができません。</span><span class="sxs-lookup"><span data-stu-id="f6925-118">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="f6925-119">KnownTypeAttribute クラス</span><span class="sxs-lookup"><span data-stu-id="f6925-119">The KnownTypeAttribute Class</span></span>  

 <span data-ttu-id="f6925-120">データが受信エンドポイントに到着すると、WCF ランタイムにより、共通言語ランタイム (CLR: Common Language Runtime) 型のインスタンスへのデータの逆シリアル化が試行されます。</span><span class="sxs-lookup"><span data-stu-id="f6925-120">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="f6925-121">逆シリアル化するためにインスタンス化される型は、まず受信メッセージを調べてメッセージの内容が従うデータ コントラクトを特定することで選択されます。</span><span class="sxs-lookup"><span data-stu-id="f6925-121">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="f6925-122">次に逆シリアル化エンジンは、メッセージの内容と互換性のあるデータ コントラクトを実装する CLR 型を探します。</span><span class="sxs-lookup"><span data-stu-id="f6925-122">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="f6925-123">逆シリアル化エンジンによってこの処理中に逆シリアル化の候補の型として許可される一連の型は、逆シリアル化の "既知の型" のセットと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f6925-123">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="f6925-124">逆シリアル化エンジンに型の情報を知らせる方法として、 <xref:System.Runtime.Serialization.KnownTypeAttribute>を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="f6925-124">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="f6925-125">この属性は、データ コントラクト型全体に適用できるだけで、個々のデータ メンバーには適用できません。</span><span class="sxs-lookup"><span data-stu-id="f6925-125">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="f6925-126">この属性は、クラスまたは構造体にすることが可能な *外部型* に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f6925-126">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="f6925-127">最も簡単な使用方法は、属性を適用するときに "既知の型" として型を指定することです。</span><span class="sxs-lookup"><span data-stu-id="f6925-127">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="f6925-128">これによって、外部型のオブジェクトまたはメンバーを通して参照される任意のオブジェクトが逆シリアル化されるときに、必ず、その既知の型が既知の型のセットに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f6925-128">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="f6925-129">複数の <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性を同じ型に適用することができます。</span><span class="sxs-lookup"><span data-stu-id="f6925-129">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="f6925-130">既知の型とプリミティブ</span><span class="sxs-lookup"><span data-stu-id="f6925-130">Known Types and Primitives</span></span>  

 <span data-ttu-id="f6925-131">プリミティブとして扱われる特定の型 ( <xref:System.DateTime> 、 <xref:System.Xml.XmlElement>など) と同様に、プリミティブ型は、常に "既知" であり、このメカニズムを通して追加する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="f6925-131">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="f6925-132">ただし、プリミティブ型の配列は明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6925-132">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="f6925-133">ほとんどのコレクションは、配列と同等に扱われます。</span><span class="sxs-lookup"><span data-stu-id="f6925-133">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="f6925-134">(非ジェネリック コレクションは、 <xref:System.Object>の配列と同等に扱われます)。</span><span class="sxs-lookup"><span data-stu-id="f6925-134">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="f6925-135">プリミティブ、プリミティブ配列、およびプリミティブ コレクションの使用例については、例 4 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6925-135">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6925-136">他のプリミティブ型とは異なり、 <xref:System.DateTimeOffset> 構造は、既定では既知の型ではないため、既知の型のリストに手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6925-136">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f6925-137">例</span><span class="sxs-lookup"><span data-stu-id="f6925-137">Examples</span></span>  

 <span data-ttu-id="f6925-138"><xref:System.Runtime.Serialization.KnownTypeAttribute> クラスの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6925-138">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="f6925-139">例 1</span><span class="sxs-lookup"><span data-stu-id="f6925-139">Example 1</span></span>  

 <span data-ttu-id="f6925-140">継承関係にある 3 つのクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="f6925-140">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="f6925-141">次の `CompanyLogo` クラスはシリアル化できますが、 `ShapeOfLogo` メンバーが `CircleType` オブジェクトと `TriangleType` オブジェクトのどちらかに設定されている場合は、逆シリアル化エンジンが "Circle" や "Triangle" という名前のデータ コントラクト型を認識しないため、逆シリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="f6925-141">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="f6925-142">`CompanyLogo` 型の正しいコードの記述方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f6925-142">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="f6925-143">外部型の `CompanyLogo2` が逆シリアル化されるときは、必ず、逆シリアル化エンジンが `CircleType` と `TriangleType` を認識するため、"Circle" データ コントラクトおよび "Triangle" データ コントラクトと一致する型を検出できます。</span><span class="sxs-lookup"><span data-stu-id="f6925-143">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="f6925-144">例 2</span><span class="sxs-lookup"><span data-stu-id="f6925-144">Example 2</span></span>  

 <span data-ttu-id="f6925-145">次の例では、 `CustomerTypeA` と `CustomerTypeB` の両方が `Customer` データ コントラクトを持っている場合でも、逆シリアル化エンジンは `CustomerTypeB` だけを認識するため、 `PurchaseOrder` が逆シリアル化されるときは必ず `CustomerTypeB` のインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f6925-145">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="f6925-146">例 3</span><span class="sxs-lookup"><span data-stu-id="f6925-146">Example 3</span></span>  

 <span data-ttu-id="f6925-147">次の例では、 <xref:System.Collections.Hashtable> が <xref:System.Object>として内部的にその内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="f6925-147">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="f6925-148">ハッシュ テーブルを正常に逆シリアル化するには、逆シリアル化エンジンがそのテーブルに現れる可能性のある型のセットを認識している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6925-148">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="f6925-149">この場合は、 `Book` オブジェクトと `Magazine` オブジェクトだけが `Catalog`に保存されているため、この 2 つが <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性を使用して追加されることが事前にわかっています。</span><span class="sxs-lookup"><span data-stu-id="f6925-149">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="f6925-150">例 4</span><span class="sxs-lookup"><span data-stu-id="f6925-150">Example 4</span></span>  

 <span data-ttu-id="f6925-151">次の例では、データ コントラクトには数値と、その数値に基づいて実行する演算が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f6925-151">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="f6925-152">`Numbers` データ メンバーは、整数、整数の配列、または整数を含む <xref:System.Collections.Generic.List%601> にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f6925-152">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f6925-153">この例は、WCF プロキシを生成するために SVCUTIL.EXE が使用されている場合にのみ、クライアント側で機能します。</span><span class="sxs-lookup"><span data-stu-id="f6925-153">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="f6925-154">SVCUTIL.EXE は、サービスからメタデータ (任意の既知の型を含む) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f6925-154">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="f6925-155">この情報がない場合、クライアントは型を逆シリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="f6925-155">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="f6925-156">アプリケーション コードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f6925-156">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="f6925-157">既知の型、継承、およびインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6925-157">Known Types, Inheritance, and Interfaces</span></span>  

 <span data-ttu-id="f6925-158">`KnownTypeAttribute` 属性を使用して既知の型を特定の型に関連付けると、その既知の型がその特定の型から派生したすべての型に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f6925-158">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="f6925-159">たとえば、次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6925-159">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="f6925-160">`DoubleDrawing` クラスは、 `KnownTypeAttribute` フィールドで `Square` と `Circle` を使用するために `AdditionalShape` 属性を必要としません。これは、既に基本クラス (`Drawing`) にこれらの属性が適用されているためです。</span><span class="sxs-lookup"><span data-stu-id="f6925-160">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="f6925-161">既知の型は、クラスと構造体にのみ関連付けることができます。インターフェイスに関連付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="f6925-161">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="f6925-162">オープン ジェネリック メソッドを使用する既知の型</span><span class="sxs-lookup"><span data-stu-id="f6925-162">Known Types Using Open Generic Methods</span></span>  

 <span data-ttu-id="f6925-163">既知の型としてジェネリック型の追加が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="f6925-163">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="f6925-164">ただし、オープン ジェネリック型をパラメーターとして `KnownTypeAttribute` 属性に渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="f6925-164">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="f6925-165">この問題は、型の一覧を返すメソッドを作成して既知の型のコレクションに追加するという代替機構を使用することで解決できます。</span><span class="sxs-lookup"><span data-stu-id="f6925-165">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="f6925-166">次に、いくつかの制限事項があるため、このメソッドの名前を `KnownTypeAttribute` 属性への文字列引数として指定します。</span><span class="sxs-lookup"><span data-stu-id="f6925-166">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="f6925-167">このメソッドは、 `KnownTypeAttribute` 属性を適用する型上に存在し、静的で、パラメーターを必要とせず、 <xref:System.Collections.IEnumerable> の <xref:System.Type>に代入可能なオブジェクトを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6925-167">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="f6925-168">同じ型上で、メソッド名を持つ `KnownTypeAttribute` 属性と実際の型を持つ `KnownTypeAttribute` 属性を組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="f6925-168">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="f6925-169">また、メソッド名が同じ複数の `KnownTypeAttribute` を同じ型に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f6925-169">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="f6925-170">次のクラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6925-170">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="f6925-171">`theDrawing` フィールドには、 `ColorDrawing` ジェネリック クラスおよび `BlackAndWhiteDrawing`ジェネリック クラスのインスタンスを格納でき、これらのクラスは両方とも `Drawing`ジェネリック クラスから継承されています。</span><span class="sxs-lookup"><span data-stu-id="f6925-171">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="f6925-172">通常、両クラスとも既知の型に追加する必要がありますが、次の属性の構文は無効です。</span><span class="sxs-lookup"><span data-stu-id="f6925-172">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="f6925-173">したがって、これらの型を返すメソッドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6925-173">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="f6925-174">この型の正しいコードの記述方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f6925-174">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="f6925-175">既知の型を追加するその他の方法</span><span class="sxs-lookup"><span data-stu-id="f6925-175">Additional Ways to Add Known Types</span></span>  

 <span data-ttu-id="f6925-176">また、既知の型は、構成ファイルを使用して追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="f6925-176">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="f6925-177">この方法は、Windows Communication Foundation (WCF) でサードパーティ製の型ライブラリを使用する場合のように、適切な逆シリアル化のために既知の型を必要とする型を制御できない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="f6925-177">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="f6925-178">構成ファイルで既知の型を指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6925-178">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="f6925-179">前の構成ファイルでは、 `MyCompany.Library.Shape` というコントラクト型が `MyCompany.Library.Circle` を既知の型として持つと宣言されています。</span><span class="sxs-lookup"><span data-stu-id="f6925-179">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6925-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6925-180">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="f6925-181">既知の型</span><span class="sxs-lookup"><span data-stu-id="f6925-181">Known Types</span></span>](../samples/known-types.md)
- [<span data-ttu-id="f6925-182">データ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="f6925-182">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="f6925-183">サービス コントラクトの設計</span><span class="sxs-lookup"><span data-stu-id="f6925-183">Designing Service Contracts</span></span>](../designing-service-contracts.md)
