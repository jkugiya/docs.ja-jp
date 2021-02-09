---
description: '詳細情報: Key (Visual Basic)'
title: Key
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 5ec918da661144053824ca2a734cdec11873b0e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640798"
---
# <a name="key-visual-basic"></a><span data-ttu-id="1ce80-103">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ce80-103">Key (Visual Basic)</span></span>

<span data-ttu-id="1ce80-104">`Key` キーワードを使用すると、匿名型のプロパティの動作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-104">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="1ce80-105">キー プロパティとして指定したプロパティのみが、匿名型インスタンス間の等価性のテスト、またはハッシュ コード値の計算に関与します。</span><span class="sxs-lookup"><span data-stu-id="1ce80-105">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="1ce80-106">キー プロパティの値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="1ce80-106">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="1ce80-107">匿名型のプロパティをキー プロパティとして指定するには、初期化リストでその宣言の前にキーワード `Key` を配置します。</span><span class="sxs-lookup"><span data-stu-id="1ce80-107">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="1ce80-108">次の例では、`Airline` と `FlightNo` はキー プロパティですが、`Gate` は違います。</span><span class="sxs-lookup"><span data-stu-id="1ce80-108">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="1ce80-109">新しい匿名型を作成すると、<xref:System.Object> から直接継承されます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-109">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="1ce80-110">コンパイラによって、継承された 3 つのメンバー (<xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A>、および <xref:System.Object.ToString%2A>) がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-110">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="1ce80-111"><xref:System.Object.Equals%2A> と <xref:System.Object.GetHashCode%2A> に対して生成されるオーバーライド コードは、キー プロパティに基づきます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-111">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="1ce80-112">型にキー プロパティがない場合、<xref:System.Object.GetHashCode%2A> と <xref:System.Object.Equals%2A> はオーバーライドされません。</span><span class="sxs-lookup"><span data-stu-id="1ce80-112">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="1ce80-113">等価比較</span><span class="sxs-lookup"><span data-stu-id="1ce80-113">Equality</span></span>  

 <span data-ttu-id="1ce80-114">2 つの匿名型のインスタンスは、それらが同じ型のインスタンスであり、それらのキー プロパティの値が等しい場合に等しいとされます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-114">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="1ce80-115">次の例で、`flight2` は、前の例の `flight1` と等しくなります。それらは同じ匿名型のインスタンスであり、それらのキー プロパティで一致する値を持つためです。</span><span class="sxs-lookup"><span data-stu-id="1ce80-115">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="1ce80-116">ただし、`flight3` は、キー プロパティ `FlightNo` の値が異なるため、`flight1` と等しくありません。</span><span class="sxs-lookup"><span data-stu-id="1ce80-116">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="1ce80-117">インスタンス `flight4` は `flight1` と同じ型ではありません。それらはキー プロパティと異なるプロパティを指定しているためです。</span><span class="sxs-lookup"><span data-stu-id="1ce80-117">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="1ce80-118">2 つのインスタンスが、名前、型、順序、および値が同じで、非キー プロパティのみで宣言されている場合、2 つのインスタンスは等しくありません。</span><span class="sxs-lookup"><span data-stu-id="1ce80-118">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="1ce80-119">キー プロパティを持たないインスタンスは、それ自体とのみ等しくなります。</span><span class="sxs-lookup"><span data-stu-id="1ce80-119">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="1ce80-120">2 つの匿名型インスタンスが同じ匿名型のインスタンスである条件の詳細については、「[匿名型](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ce80-120">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="1ce80-121">ハッシュ コード計算</span><span class="sxs-lookup"><span data-stu-id="1ce80-121">Hash Code Calculation</span></span>  

 <span data-ttu-id="1ce80-122"><xref:System.Object.Equals%2A> と同様に、匿名型の <xref:System.Object.GetHashCode%2A> に定義されているハッシュ関数は、型のキー プロパティに基づきます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-122">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="1ce80-123">次の例に、キー プロパティとハッシュ コード値の間の相互作用を示します。</span><span class="sxs-lookup"><span data-stu-id="1ce80-123">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="1ce80-124">すべてのキー プロパティに同じ値を持つ匿名型のインスタンスは、同じハッシュ コード値を持ちます。非キー プロパティに一致する値がない場合でも同じです。</span><span class="sxs-lookup"><span data-stu-id="1ce80-124">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="1ce80-125">次のステートメントでは、`True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-125">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="1ce80-126">1 つ以上のキー プロパティで異なる値を持つ匿名型のインスタンスは、異なるハッシュ コード値を持ちます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-126">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="1ce80-127">次のステートメントでは、`False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-127">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="1ce80-128">キー プロパティと異なるプロパティを指定する匿名型のインスタンスは、同じ型のインスタンスではありません。</span><span class="sxs-lookup"><span data-stu-id="1ce80-128">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="1ce80-129">それらは、すべてのプロパティの名前と値が同じであっても、異なるハッシュ コード値を持ちます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-129">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="1ce80-130">次のステートメントでは、`False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-130">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="1ce80-131">読み取り専用の値</span><span class="sxs-lookup"><span data-stu-id="1ce80-131">Read-Only Values</span></span>  

 <span data-ttu-id="1ce80-132">キー プロパティの値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="1ce80-132">The values of key properties cannot be changed.</span></span> <span data-ttu-id="1ce80-133">たとえば、前の例の `flight1` では、`Airline` フィールドと `FlightNo` フィールドは読み取り専用ですが、`Gate` は変更できます。</span><span class="sxs-lookup"><span data-stu-id="1ce80-133">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="1ce80-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ce80-134">See also</span></span>

- [<span data-ttu-id="1ce80-135">匿名型の定義</span><span class="sxs-lookup"><span data-stu-id="1ce80-135">Anonymous Type Definition</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="1ce80-136">方法: 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="1ce80-136">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="1ce80-137">匿名型</span><span class="sxs-lookup"><span data-stu-id="1ce80-137">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
