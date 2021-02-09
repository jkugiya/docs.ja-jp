---
description: '詳細情報: CType 関数 (Visual Basic)'
title: CType Function
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 9732f52b40e5f762769ba5dc340c000e7e1ba17a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701262"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="55649-103">CType 関数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55649-103">CType Function (Visual Basic)</span></span>

<span data-ttu-id="55649-104">任意の式を、指定されたデータ型、オブジェクト、構造体、クラス、またはインターフェイスに明示的に変換し、その結果を返します。</span><span class="sxs-lookup"><span data-stu-id="55649-104">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="55649-105">構文</span><span class="sxs-lookup"><span data-stu-id="55649-105">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="55649-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="55649-106">Parts</span></span>

<span data-ttu-id="55649-107">`expression` 任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="55649-107">`expression` Any valid expression.</span></span> <span data-ttu-id="55649-108">`expression` の値が `typename` で許可されている範囲内でない場合、Visual Basic が例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="55649-108">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="55649-109">`typename` `Dim` ステートメントの `As` 句内の有効な任意の式。つまり、任意のデータ型、オブジェクト、構造体、クラス、またはインターフェイスの名前。</span><span class="sxs-lookup"><span data-stu-id="55649-109">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="55649-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="55649-110">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="55649-111">次の関数を使用して型変換を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="55649-111">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="55649-112">特定のデータ型への変換を実行する、`CByte`、`CDbl`、`CInt` などの型変換関数。</span><span class="sxs-lookup"><span data-stu-id="55649-112">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="55649-113">詳細については、「 [データ型変換関数](type-conversion-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55649-113">For more information, see [Type Conversion Functions](type-conversion-functions.md).</span></span>
> - <span data-ttu-id="55649-114">[DirectCast 演算子](../operators/directcast-operator.md)または [TryCast 演算子](../operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="55649-114">[DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md).</span></span> <span data-ttu-id="55649-115">これらの演算子では、一方の型が他方の型を継承または実装している必要があります。</span><span class="sxs-lookup"><span data-stu-id="55649-115">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="55649-116">これらの場合は、`CType` データ型との間で変換を行うときに、`Object` よりもいくらかパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="55649-116">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="55649-117">`CType` は、インラインでコンパイルされます。つまり、変換コードは、式を評価するコードに含まれます。</span><span class="sxs-lookup"><span data-stu-id="55649-117">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="55649-118">場合によっては、変換を実行するプロシージャが呼び出されないため、コードの実行速度が速くなります。</span><span class="sxs-lookup"><span data-stu-id="55649-118">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="55649-119">`expression` から `typename` など、`Integer` から `Date` への変換が定義されていない場合、Visual Basic はコンパイル時のエラー メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="55649-119">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="55649-120">実行時に変換が失敗すると、適切な例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="55649-120">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="55649-121">縮小変換が失敗した場合、最もよくスローされるのは <xref:System.OverflowException> です。</span><span class="sxs-lookup"><span data-stu-id="55649-121">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="55649-122">変換が定義されていない場合、<xref:System.InvalidCastException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="55649-122">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="55649-123">たとえば、これは、`expression` が `Object` 型で、実行時の型が `typename` への変換を持たない場合に起こります。</span><span class="sxs-lookup"><span data-stu-id="55649-123">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="55649-124">`expression` または `typename` のデータ型が、定義したクラスまたは構造体の場合、そのクラスまたは構造体に `CType` を変換演算子として定義できます。</span><span class="sxs-lookup"><span data-stu-id="55649-124">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="55649-125">これにより、`CType` は *オーバーロードされた演算子* として機能します。</span><span class="sxs-lookup"><span data-stu-id="55649-125">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="55649-126">この方法を利用する場合、定義したクラスまたは構造体からの変換、またはこのクラスまたは構造体への変換の動作 (スローする例外など) を制御できます。</span><span class="sxs-lookup"><span data-stu-id="55649-126">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="55649-127">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="55649-127">Overloading</span></span>

<span data-ttu-id="55649-128">`CType` 演算子も、コードの外部で定義されたクラスまたは構造体でオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="55649-128">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="55649-129">このようなクラスまたは構造体からの変換、またはこのクラスまたは構造体への変換を行う場合は、その `CType` 演算子の動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="55649-129">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="55649-130">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55649-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="55649-131">動的オブジェクトの変換</span><span class="sxs-lookup"><span data-stu-id="55649-131">Converting Dynamic Objects</span></span>

<span data-ttu-id="55649-132">動的オブジェクトの型変換は、<xref:System.Dynamic.DynamicObject.TryConvert%2A> メソッドまたは <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> メソッドを使用するユーザー定義の動的変換によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="55649-132">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="55649-133">動的オブジェクトを使用する場合は、<xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> メソッドを使用して動的オブジェクトを変換します。</span><span class="sxs-lookup"><span data-stu-id="55649-133">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="55649-134">例</span><span class="sxs-lookup"><span data-stu-id="55649-134">Example</span></span>

<span data-ttu-id="55649-135">`CType` 関数を使用して任意の式を `Single` データ型に変換する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55649-135">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="55649-136">その他の例については、「[暗黙的な変換と明示的な変換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55649-136">For additional examples, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55649-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="55649-137">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="55649-138">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="55649-138">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="55649-139">変換関数</span><span class="sxs-lookup"><span data-stu-id="55649-139">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="55649-140">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="55649-140">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="55649-141">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="55649-141">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="55649-142">.NET Framework における型変換</span><span class="sxs-lookup"><span data-stu-id="55649-142">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
