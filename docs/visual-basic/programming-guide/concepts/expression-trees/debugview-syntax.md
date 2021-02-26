---
title: DebugView プロパティで使用される構文
description: 式ツリーを文字列で表現する目的で DebugView プロパティにより使用される特別な構文について説明します。
author: zspitz
ms.author: wiwagn
ms.date: 02/14/2021
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 1b6d117bb1ce0cb13344c72be3b55742c443448f
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639190"
---
# <a name="debugview-syntax"></a><span data-ttu-id="1df82-103">**DebugView** の構文</span><span class="sxs-lookup"><span data-stu-id="1df82-103">**DebugView** syntax</span></span>

<span data-ttu-id="1df82-104">**DebugView** プロパティ (デバッグ時にのみ利用可能) を指定すると、式ツリーが文字列でレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="1df82-104">The **DebugView** property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="1df82-105">構文の大部分はかなりわかりやすいです。特別なケースについて以降のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="1df82-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="1df82-106">各例の後に、**DebugView** を含むコメント ブロックが示されています。</span><span class="sxs-lookup"><span data-stu-id="1df82-106">Each example is followed by a comment block containing the **DebugView**.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="1df82-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="1df82-107">ParameterExpression</span></span>

<span data-ttu-id="1df82-108"><xref:System.Linq.Expressions.ParameterExpression> 変数名は、先頭に記号 "$" を付けて表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df82-108"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="1df82-109">パラメーターに名前がない場合、`$var1` や `$var2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1df82-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="1df82-110">使用例</span><span class="sxs-lookup"><span data-stu-id="1df82-110">Examples</span></span>

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a><span data-ttu-id="1df82-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="1df82-111">ConstantExpressions</span></span>

<span data-ttu-id="1df82-112">整数値、文字列、および `null` を表す <xref:System.Linq.Expressions.ConstantExpression> オブジェクトの場合、定数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df82-112">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="1df82-113">一部の数値型では、値にサフィックスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="1df82-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="1df82-114">種類</span><span class="sxs-lookup"><span data-stu-id="1df82-114">Type</span></span> | <span data-ttu-id="1df82-115">キーワード</span><span class="sxs-lookup"><span data-stu-id="1df82-115">Keyword</span></span> | <span data-ttu-id="1df82-116">サフィックス</span><span class="sxs-lookup"><span data-stu-id="1df82-116">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="1df82-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="1df82-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="1df82-118">U</span><span class="sxs-lookup"><span data-stu-id="1df82-118">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="1df82-119">Long</span><span class="sxs-lookup"><span data-stu-id="1df82-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="1df82-120">L</span><span class="sxs-lookup"><span data-stu-id="1df82-120">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="1df82-121">ULong</span><span class="sxs-lookup"><span data-stu-id="1df82-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="1df82-122">UL</span><span class="sxs-lookup"><span data-stu-id="1df82-122">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="1df82-123">Double</span><span class="sxs-lookup"><span data-stu-id="1df82-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="1df82-124">D</span><span class="sxs-lookup"><span data-stu-id="1df82-124">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="1df82-125">Single</span><span class="sxs-lookup"><span data-stu-id="1df82-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="1df82-126">F</span><span class="sxs-lookup"><span data-stu-id="1df82-126">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="1df82-127">Decimal</span><span class="sxs-lookup"><span data-stu-id="1df82-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="1df82-128">M</span><span class="sxs-lookup"><span data-stu-id="1df82-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="1df82-129">使用例</span><span class="sxs-lookup"><span data-stu-id="1df82-129">Examples</span></span>

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a><span data-ttu-id="1df82-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="1df82-130">BlockExpression</span></span>

<span data-ttu-id="1df82-131"><xref:System.Linq.Expressions.BlockExpression> オブジェクトの型がブロック内の最後の式の型と異なる場合、その型が山かっこ (`<` と `>`) 内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df82-131">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="1df82-132">それ以外の場合、<xref:System.Linq.Expressions.BlockExpression> オブジェクトの型は表示されません。</span><span class="sxs-lookup"><span data-stu-id="1df82-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="1df82-133">使用例</span><span class="sxs-lookup"><span data-stu-id="1df82-133">Examples</span></span>

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object),
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a><span data-ttu-id="1df82-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="1df82-134">LambdaExpression</span></span>

<span data-ttu-id="1df82-135"><xref:System.Linq.Expressions.LambdaExpression> オブジェクトは、デリゲート型と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df82-135"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="1df82-136">ラムダ式に名前がない場合、`#Lambda1` や `#Lambda2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1df82-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="1df82-137">使用例</span><span class="sxs-lookup"><span data-stu-id="1df82-137">Examples</span></span>

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a><span data-ttu-id="1df82-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="1df82-138">LabelExpression</span></span>

<span data-ttu-id="1df82-139"><xref:System.Linq.Expressions.LabelExpression> オブジェクトの既定値を指定した場合、その値が <xref:System.Linq.Expressions.LabelTarget> オブジェクトの前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df82-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="1df82-140">`.Label` トークンは、ラベルの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="1df82-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="1df82-141">`.LabelTarget` トークンは、ジャンプ先のターゲットを示します。</span><span class="sxs-lookup"><span data-stu-id="1df82-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="1df82-142">ラベルに名前がない場合、`#Label1` や `#Label2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1df82-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="1df82-143">使用例</span><span class="sxs-lookup"><span data-stu-id="1df82-143">Examples</span></span>

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a><span data-ttu-id="1df82-144">checked 演算子</span><span class="sxs-lookup"><span data-stu-id="1df82-144">Checked Operators</span></span>

<span data-ttu-id="1df82-145">checked 演算子は、演算子の前に `#` 記号が付く形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df82-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="1df82-146">たとえば、checked 加算演算子は `#+` と表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df82-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="1df82-147">使用例</span><span class="sxs-lookup"><span data-stu-id="1df82-147">Examples</span></span>

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```
