---
description: '詳細情報: 演算子のオーバーロード'
title: 演算子のオーバーロード
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: e6552f35081afa542e4dc14239206a63c7c1bd59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713326"
---
# <a name="operator-overloads"></a><span data-ttu-id="3e04b-103">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="3e04b-103">Operator Overloads</span></span>

<span data-ttu-id="3e04b-104">演算子のオーバーロードを使用すると、フレームワークの型を組み込みの言語プリミティブのように使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3e04b-104">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="3e04b-105">状況によっては許可され、役に立つこともありますが、演算子のオーバーロードは慎重に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e04b-105">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="3e04b-106">フレームワーク デザイナーが簡単なメソッドにする必要がある操作に対して演算子を使い始めた場合など、演算子のオーバーロードの使用方法が正しくない多くのケースがあります。</span><span class="sxs-lookup"><span data-stu-id="3e04b-106">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="3e04b-107">以下のガイドラインは、演算子のオーバーロードを使用するタイミングと方法を決定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3e04b-107">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="3e04b-108">❌ プリミティブ (組み込み) 型のように感じられるようにする必要がある型以外には、演算子のオーバーロードを定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e04b-108">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="3e04b-109">✔️ プリミティブ型のように感じられるようにする必要がある型には、演算子のオーバーロードを定義することを検討します。</span><span class="sxs-lookup"><span data-stu-id="3e04b-109">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="3e04b-110">たとえば、<xref:System.String?displayProperty=nameWithType> には `operator==` と `operator!=` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="3e04b-110">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="3e04b-111">✔️ 数値を表す構造体で演算子のオーバーロードを定義します (<xref:System.Decimal?displayProperty=nameWithType> など)。</span><span class="sxs-lookup"><span data-stu-id="3e04b-111">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="3e04b-112">❌ 凝った演算子のオーバーロードを定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e04b-112">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="3e04b-113">演算子のオーバーロードは、演算の結果がすぐにわかる場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3e04b-113">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="3e04b-114">たとえば、ある <xref:System.DateTime> を別の `DateTime` から減算して <xref:System.TimeSpan> を取得できるようにするのは理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="3e04b-114">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="3e04b-115">一方、2 つのデータベース クエリの和集合を求めるために論理和演算子を使用をしたり、ストリームに書き込むためにシフト演算子を使用したりするのは適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="3e04b-115">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="3e04b-116">❌ 少なくとも 1 つのオペランドがオーバーロードを定義する型でない限り、演算子のオーバーロードを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e04b-116">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="3e04b-117">✔️ 演算子のオーバーロードは対称的になるようにします。</span><span class="sxs-lookup"><span data-stu-id="3e04b-117">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="3e04b-118">たとえば、`operator==` をオーバーロードする場合は、`operator!=` もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e04b-118">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="3e04b-119">同様に、`operator<` をオーバーロードする場合は、`operator>` もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e04b-119">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="3e04b-120">✔️ メソッドには、オーバーロードされる各演算子に対応するフレンドリ名を付けることを検討します。</span><span class="sxs-lookup"><span data-stu-id="3e04b-120">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="3e04b-121">多くの言語では、演算子のオーバーロードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3e04b-121">Many languages do not support operator overloading.</span></span> <span data-ttu-id="3e04b-122">このため、オーバーロード演算子には、同等の機能を提供するドメイン固有の適切な名前を持つ二次的なメソッドを含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3e04b-122">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="3e04b-123">次の表では、演算子とそれに対応するわかりやすいメソッド名の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="3e04b-123">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="3e04b-124">C# の演算子シンボル</span><span class="sxs-lookup"><span data-stu-id="3e04b-124">C# Operator Symbol</span></span>|<span data-ttu-id="3e04b-125">メタデータ名</span><span class="sxs-lookup"><span data-stu-id="3e04b-125">Metadata Name</span></span>|<span data-ttu-id="3e04b-126">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="3e04b-126">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="3e04b-127">operator == のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="3e04b-127">Overloading Operator ==</span></span>

 <span data-ttu-id="3e04b-128">`operator ==` のオーバーロードは非常に複雑です。</span><span class="sxs-lookup"><span data-stu-id="3e04b-128">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="3e04b-129">演算子のセマンティクスは、<xref:System.Object.Equals%2A?displayProperty=nameWithType> など、他のいくつかのメンバーと互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e04b-129">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="3e04b-130">変換演算子</span><span class="sxs-lookup"><span data-stu-id="3e04b-130">Conversion Operators</span></span>

 <span data-ttu-id="3e04b-131">変換演算子は、ある型から別の型に変換できる単項演算子です。</span><span class="sxs-lookup"><span data-stu-id="3e04b-131">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="3e04b-132">演算子は、オペランドまたは戻り値の型のいずれかで静的メンバーとして定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e04b-132">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="3e04b-133">変換演算子には、暗黙と明示の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="3e04b-133">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="3e04b-134">❌ エンド ユーザーがそのような変換を明確に想定していない場合は、変換演算子を提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e04b-134">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="3e04b-135">❌ 型のドメインの外部で変換演算子を定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e04b-135">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="3e04b-136">たとえば、<xref:System.Int32>、<xref:System.Double>、<xref:System.Decimal> はすべて数値型ですが、<xref:System.DateTime> はそうではありません。</span><span class="sxs-lookup"><span data-stu-id="3e04b-136">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="3e04b-137">したがって、`Double(long)` を `DateTime` に変換する変換演算子は定義しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e04b-137">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="3e04b-138">このような場合は、コンストラクターを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3e04b-138">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="3e04b-139">❌ 変換で損失が発生する可能性がある場合は、暗黙的な変換演算子を提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e04b-139">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="3e04b-140">たとえば、`Double` の方が `Int32` より範囲が広いので、`Double` から `Int32` への暗黙的な変換を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="3e04b-140">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="3e04b-141">変換で損失が発生する可能性がある場合でも、明示的な変換演算子は提供できます。</span><span class="sxs-lookup"><span data-stu-id="3e04b-141">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="3e04b-142">❌ 暗黙のキャストから例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="3e04b-142">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="3e04b-143">変換が行われていることがわからない可能性があるため、エンド ユーザーにとって起きていることを理解するのは非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="3e04b-143">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="3e04b-144">✔️ キャスト演算子の呼び出しによって損失を伴う変換が発生し、演算子のコントラクトでは損失を伴う変換が許可されていない場合は、<xref:System.InvalidCastException?displayProperty=nameWithType> をスローします。</span><span class="sxs-lookup"><span data-stu-id="3e04b-144">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="3e04b-145">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="3e04b-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3e04b-146">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="3e04b-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3e04b-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e04b-147">See also</span></span>

- [<span data-ttu-id="3e04b-148">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3e04b-148">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="3e04b-149">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3e04b-149">Framework Design Guidelines</span></span>](index.md)
