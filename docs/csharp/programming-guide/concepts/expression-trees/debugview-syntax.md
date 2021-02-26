---
title: DebugView プロパティで使用される構文 (C#)
description: 式ツリーを文字列で表現する目的で DebugView プロパティにより使用される特別な構文について説明します。
author: zspitz
ms.author: wiwagn
ms.date: 02/14/2021
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 278fc66f9f8cf7671b956126cec10c4464a5b81c
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639390"
---
# <a name="debugview-syntax"></a><span data-ttu-id="53b11-103">**DebugView** の構文</span><span class="sxs-lookup"><span data-stu-id="53b11-103">**DebugView** syntax</span></span>

<span data-ttu-id="53b11-104">**DebugView** プロパティ (デバッグ時にのみ利用可能) を指定すると、式ツリーが文字列でレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="53b11-104">The **DebugView** property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="53b11-105">構文の大部分はかなりわかりやすいです。特別なケースについて以降のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="53b11-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="53b11-106">各例の後に、**DebugView** を含むブロック コメントが示されています。</span><span class="sxs-lookup"><span data-stu-id="53b11-106">Each example is followed by a block comment, containing the **DebugView**.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="53b11-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="53b11-107">ParameterExpression</span></span>

<span data-ttu-id="53b11-108"><xref:System.Linq.Expressions.ParameterExpression> 変数名は、先頭に記号 `$` を付けて表示されます。</span><span class="sxs-lookup"><span data-stu-id="53b11-108"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="53b11-109">パラメーターに名前がない場合、`$var1` や `$var2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="53b11-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="53b11-110">使用例</span><span class="sxs-lookup"><span data-stu-id="53b11-110">Examples</span></span>

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a><span data-ttu-id="53b11-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="53b11-111">ConstantExpression</span></span>

<span data-ttu-id="53b11-112">整数値、文字列、および `null` を表す <xref:System.Linq.Expressions.ConstantExpression> オブジェクトの場合、定数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="53b11-112">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="53b11-113">C# リテラルとしての標準のサフィックスを持つ数値型の場合、サフィックスが値に追加されます。</span><span class="sxs-lookup"><span data-stu-id="53b11-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="53b11-114">さまざまな数値型に関連するサフィックスを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="53b11-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="53b11-115">種類</span><span class="sxs-lookup"><span data-stu-id="53b11-115">Type</span></span> | <span data-ttu-id="53b11-116">キーワード</span><span class="sxs-lookup"><span data-stu-id="53b11-116">Keyword</span></span> | <span data-ttu-id="53b11-117">サフィックス</span><span class="sxs-lookup"><span data-stu-id="53b11-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="53b11-118">uint</span><span class="sxs-lookup"><span data-stu-id="53b11-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="53b11-119">U</span><span class="sxs-lookup"><span data-stu-id="53b11-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="53b11-120">long</span><span class="sxs-lookup"><span data-stu-id="53b11-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="53b11-121">L</span><span class="sxs-lookup"><span data-stu-id="53b11-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="53b11-122">ulong</span><span class="sxs-lookup"><span data-stu-id="53b11-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="53b11-123">UL</span><span class="sxs-lookup"><span data-stu-id="53b11-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="53b11-124">double</span><span class="sxs-lookup"><span data-stu-id="53b11-124">double</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="53b11-125">D</span><span class="sxs-lookup"><span data-stu-id="53b11-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="53b11-126">float</span><span class="sxs-lookup"><span data-stu-id="53b11-126">float</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="53b11-127">F</span><span class="sxs-lookup"><span data-stu-id="53b11-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="53b11-128">decimal</span><span class="sxs-lookup"><span data-stu-id="53b11-128">decimal</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="53b11-129">M</span><span class="sxs-lookup"><span data-stu-id="53b11-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="53b11-130">使用例</span><span class="sxs-lookup"><span data-stu-id="53b11-130">Examples</span></span>

```csharp
int num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a><span data-ttu-id="53b11-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="53b11-131">BlockExpression</span></span>

<span data-ttu-id="53b11-132"><xref:System.Linq.Expressions.BlockExpression> オブジェクトの型がブロック内の最後の式の型と異なる場合、その型が山かっこ (`<` と `>`) 内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="53b11-132">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="53b11-133">それ以外の場合、<xref:System.Linq.Expressions.BlockExpression> オブジェクトの型は表示されません。</span><span class="sxs-lookup"><span data-stu-id="53b11-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="53b11-134">使用例</span><span class="sxs-lookup"><span data-stu-id="53b11-134">Examples</span></span>

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a><span data-ttu-id="53b11-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="53b11-135">LambdaExpression</span></span>

<span data-ttu-id="53b11-136"><xref:System.Linq.Expressions.LambdaExpression> オブジェクトは、デリゲート型と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="53b11-136"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="53b11-137">ラムダ式に名前がない場合、`#Lambda1` や `#Lambda2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="53b11-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="53b11-138">使用例</span><span class="sxs-lookup"><span data-stu-id="53b11-138">Examples</span></span>

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```

## <a name="labelexpression"></a><span data-ttu-id="53b11-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="53b11-139">LabelExpression</span></span>

<span data-ttu-id="53b11-140"><xref:System.Linq.Expressions.LabelExpression> オブジェクトの既定値を指定した場合、その値が <xref:System.Linq.Expressions.LabelTarget> オブジェクトの前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="53b11-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="53b11-141">`.Label` トークンは、ラベルの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="53b11-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="53b11-142">`.LabelTarget` トークンは、ジャンプ先のターゲットを示します。</span><span class="sxs-lookup"><span data-stu-id="53b11-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="53b11-143">ラベルに名前がない場合、`#Label1` や `#Label2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="53b11-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="53b11-144">使用例</span><span class="sxs-lookup"><span data-stu-id="53b11-144">Examples</span></span>

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```

## <a name="checked-operators"></a><span data-ttu-id="53b11-145">checked 演算子</span><span class="sxs-lookup"><span data-stu-id="53b11-145">Checked Operators</span></span>

<span data-ttu-id="53b11-146">checked 演算子は、演算子の前に `#` 記号が付く形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="53b11-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="53b11-147">たとえば、checked 加算演算子は `#+` と表示されます。</span><span class="sxs-lookup"><span data-stu-id="53b11-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="53b11-148">使用例</span><span class="sxs-lookup"><span data-stu-id="53b11-148">Examples</span></span>

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```
