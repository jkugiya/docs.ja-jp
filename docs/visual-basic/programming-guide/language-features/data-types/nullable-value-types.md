---
description: '詳細情報: null 許容値型 (Visual Basic)'
title: null 許容値型
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: acc91d98a3ed288a9bf0bcf6abbd3d8a516bd699
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483886"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="9daf8-103">null 許容値型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9daf8-103">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="9daf8-104">場合によっては、特定の状況で値が定義されていない値型を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-104">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="9daf8-105">たとえば、データベースのフィールドでは、意味のある値が割り当てられている場合と、値が割り当てられていない場合を、区別することが必要なときがあります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-105">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="9daf8-106">値型は、通常の値または null 値を受け取るように拡張できます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-106">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="9daf8-107">このような拡張機能は "*null 許容型*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-107">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="9daf8-108">各 null 許容値型は、ジェネリック構造体 <xref:System.Nullable%601> から作成されます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-108">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="9daf8-109">作業関連のアクティビティを追跡するデータベースについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-109">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="9daf8-110">次の例では、null 許容 `Boolean` 型が作成され、その型の変数が宣言されます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-110">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="9daf8-111">宣言は、次の 3 つの方法で記述できます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-111">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="9daf8-112">変数 `ridesBusToWork` では、`True` の値または `False` の値を保持するか、または値をまったく保持しないことができます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-112">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="9daf8-113">既定の初期値は値なしです。この場合は、このユーザーに対して情報がまだ取得されていないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="9daf8-113">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="9daf8-114">これに対し、`False` は情報が取得されていて、ユーザーが通勤にバスを利用しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="9daf8-114">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="9daf8-115">null 許容値型を使用して変数とプロパティを宣言したり、null 許容値型の要素を含む配列を宣言したりできます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-115">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="9daf8-116">パラメーターが null 許容値型であるプロシージャを宣言したり、`Function` プロシージャから null 許容値型を返したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-116">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="9daf8-117">配列、`String`、クラスなどの参照型では、null 許容型を作成できません。</span><span class="sxs-lookup"><span data-stu-id="9daf8-117">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="9daf8-118">基になる型は、値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-118">The underlying type must be a value type.</span></span> <span data-ttu-id="9daf8-119">詳細については、「 [Value Types and Reference Types](value-types-and-reference-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9daf8-119">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="9daf8-120">null 許容型変数の使用</span><span class="sxs-lookup"><span data-stu-id="9daf8-120">Using a Nullable Type Variable</span></span>

<span data-ttu-id="9daf8-121">null 許容値型の最も重要なメンバーは、<xref:System.Nullable%601.HasValue%2A> プロパティと <xref:System.Nullable%601.Value%2A> プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9daf8-121">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="9daf8-122">null 許容値型の変数の場合、<xref:System.Nullable%601.HasValue%2A> により、変数に定義済みの値が含まれているかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-122">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="9daf8-123"><xref:System.Nullable%601.HasValue%2A> が `True` の場合は、<xref:System.Nullable%601.Value%2A> から値を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-123">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="9daf8-124"><xref:System.Nullable%601.HasValue%2A> と <xref:System.Nullable%601.Value%2A> はどちらも `ReadOnly` プロパティであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9daf8-124">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="9daf8-125">既定値</span><span class="sxs-lookup"><span data-stu-id="9daf8-125">Default Values</span></span>

<span data-ttu-id="9daf8-126">null 許容値型の変数を宣言すると、その <xref:System.Nullable%601.HasValue%2A> プロパティには既定値の `False` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-126">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="9daf8-127">これは、既定では、変数には、基になる値型の既定値が設定されるのではなく、定義された値がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="9daf8-127">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="9daf8-128">次の例では、`Integer` 型の既定値が 0 であっても、変数 `numberOfChildren` の初期状態には定義された値がありません。</span><span class="sxs-lookup"><span data-stu-id="9daf8-128">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="9daf8-129">null 値は、未定義の値または不明な値を示すのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-129">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="9daf8-130">`numberOfChildren` が `Integer` として宣言されている場合、情報が現在使用できないことを示す値は存在しません。</span><span class="sxs-lookup"><span data-stu-id="9daf8-130">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="9daf8-131">値の格納</span><span class="sxs-lookup"><span data-stu-id="9daf8-131">Storing Values</span></span>

<span data-ttu-id="9daf8-132">null 許容値型の変数またはプロパティへの値の格納は、通常の方法で行います。</span><span class="sxs-lookup"><span data-stu-id="9daf8-132">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="9daf8-133">次の例では、前の例で宣言した `numberOfChildren` 変数に値を代入しています。</span><span class="sxs-lookup"><span data-stu-id="9daf8-133">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="9daf8-134">null 許容値型の変数またはプロパティに定義された値が含まれている場合は、値が割り当てられていない初期状態に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-134">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="9daf8-135">これを行うには、次の例に示すように、変数またはプロパティに `Nothing` を設定します。</span><span class="sxs-lookup"><span data-stu-id="9daf8-135">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="9daf8-136">null 許容値型の変数に `Nothing` を割り当てることはできますが、等号を使用して `Nothing` かどうかをテストすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9daf8-136">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="9daf8-137">等号を使用する比較 (`someVar = Nothing`) は、常に `Nothing` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-137">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="9daf8-138">変数の <xref:System.Nullable%601.HasValue%2A> プロパティが `False` かどうかをテストすることや、`Is` または `IsNot` 演算子を使用してテストすることはできます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-138">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="9daf8-139">値の取得</span><span class="sxs-lookup"><span data-stu-id="9daf8-139">Retrieving Values</span></span>

<span data-ttu-id="9daf8-140">null 許容値型の変数の値を取得するには、最初にその <xref:System.Nullable%601.HasValue%2A> プロパティをテストして、値があることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-140">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="9daf8-141"><xref:System.Nullable%601.HasValue%2A> が `False` のときに値を読み込もうとすると、Visual Basic で <xref:System.InvalidOperationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-141">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="9daf8-142">次の例では、前の例の変数 `numberOfChildren` を読み取るための推奨される方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9daf8-142">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="9daf8-143">null 許容型の比較</span><span class="sxs-lookup"><span data-stu-id="9daf8-143">Comparing Nullable Types</span></span>

<span data-ttu-id="9daf8-144">Null 許容の `Boolean` 変数をブール式で使用すると、結果は `True`、`False`、または `Nothing` になります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-144">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="9daf8-145">`And` と `Or` の真理値表を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9daf8-145">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="9daf8-146">`b1` と `b2` が持つことのできる値は 3 つなので、評価する組み合わせは 9 つです。</span><span class="sxs-lookup"><span data-stu-id="9daf8-146">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="9daf8-147">b1</span><span class="sxs-lookup"><span data-stu-id="9daf8-147">b1</span></span>|<span data-ttu-id="9daf8-148">b2</span><span class="sxs-lookup"><span data-stu-id="9daf8-148">b2</span></span>|<span data-ttu-id="9daf8-149">b1 And b2</span><span class="sxs-lookup"><span data-stu-id="9daf8-149">b1 And b2</span></span>|<span data-ttu-id="9daf8-150">b1 Or b2</span><span class="sxs-lookup"><span data-stu-id="9daf8-150">b1 Or b2</span></span>|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

<span data-ttu-id="9daf8-151">ブール型の変数または式の値が `Nothing` の場合は、`true` でも `false` でもありません。</span><span class="sxs-lookup"><span data-stu-id="9daf8-151">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="9daf8-152">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9daf8-152">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="9daf8-153">この例では、`b1 And b2` は `Nothing` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-153">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="9daf8-154">その結果、各 `If` ステートメントでは `Else` 句が実行され、出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-154">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="9daf8-155">ショートサーキット評価を使用する `AndAlso` および `OrElse` では、最初が `Nothing` と評価されたときに、2 番目のオペランドを評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-155">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="9daf8-156">伝達</span><span class="sxs-lookup"><span data-stu-id="9daf8-156">Propagation</span></span>

<span data-ttu-id="9daf8-157">算術、比較、シフト、または型の演算の一方または両方のオペランドが null 許容値型である場合は、演算の結果も null 許容値型になります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-157">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="9daf8-158">両方のオペランドの値が `Nothing` ではない場合、演算は、どちらも null 許容値型でない場合と同じように、オペランドの基になる値に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="9daf8-158">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="9daf8-159">次の例では、変数 `compare1` と `sum1` は暗黙的に型指定されています。</span><span class="sxs-lookup"><span data-stu-id="9daf8-159">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="9daf8-160">これらをマウスでポイントすると、どちらもコンパイラによって null 許容値型と推論されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-160">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="9daf8-161">一方または両方のオペランドの値が `Nothing` の場合、結果は `Nothing` になります。</span><span class="sxs-lookup"><span data-stu-id="9daf8-161">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="9daf8-162">データでの null 許容型の使用</span><span class="sxs-lookup"><span data-stu-id="9daf8-162">Using Nullable Types with Data</span></span>

<span data-ttu-id="9daf8-163">データベースは、null 許容値型を使用する最も重要な場所の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="9daf8-163">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="9daf8-164">現在は、すべてのデータベース オブジェクトで null 許容値型がサポートされているわけではありませんが、デザイナーで生成されたテーブル アダプターではサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9daf8-164">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="9daf8-165">「[TableAdapter での Null 許容型のサポート](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9daf8-165">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="9daf8-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="9daf8-166">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="9daf8-167">データの種類</span><span class="sxs-lookup"><span data-stu-id="9daf8-167">Data Types</span></span>](index.md)
- [<span data-ttu-id="9daf8-168">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="9daf8-168">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="9daf8-169">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="9daf8-169">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="9daf8-170">TableAdapters を使用してデータセットを入力する</span><span class="sxs-lookup"><span data-stu-id="9daf8-170">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="9daf8-171">If 演算子</span><span class="sxs-lookup"><span data-stu-id="9daf8-171">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="9daf8-172">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="9daf8-172">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="9daf8-173">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="9daf8-173">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="9daf8-174">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="9daf8-174">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="9daf8-175">null 許容値型 (C#)</span><span class="sxs-lookup"><span data-stu-id="9daf8-175">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
