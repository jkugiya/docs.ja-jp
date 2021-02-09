---
description: '詳細情報: IsNot 演算子 (Visual Basic)'
title: IsNot 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ac3e127676dfa57d14e07838152022de62fc336b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665667"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="7b727-103">IsNot 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b727-103">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="7b727-104">2 つのオブジェクト参照変数を比較します。</span><span class="sxs-lookup"><span data-stu-id="7b727-104">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="7b727-105">構文</span><span class="sxs-lookup"><span data-stu-id="7b727-105">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="7b727-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="7b727-106">Parts</span></span>

- `result`

  <span data-ttu-id="7b727-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="7b727-107">Required.</span></span> <span data-ttu-id="7b727-108">`Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="7b727-108">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="7b727-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="7b727-109">Required.</span></span> <span data-ttu-id="7b727-110">任意の `Object` 変数または式。</span><span class="sxs-lookup"><span data-stu-id="7b727-110">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="7b727-111">必須。</span><span class="sxs-lookup"><span data-stu-id="7b727-111">Required.</span></span> <span data-ttu-id="7b727-112">任意の `Object` 変数または式。</span><span class="sxs-lookup"><span data-stu-id="7b727-112">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b727-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="7b727-113">Remarks</span></span>

<span data-ttu-id="7b727-114">`IsNot` 演算子は、2 つのオブジェクト参照が別のオブジェクトを参照しているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7b727-114">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="7b727-115">ただし、値は比較されません。</span><span class="sxs-lookup"><span data-stu-id="7b727-115">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="7b727-116">`object1` と `object2` の両方がまったく同じオブジェクト インスタンスを参照している場合、`result` は `False` です。そうでない場合、`result` は `True` です。</span><span class="sxs-lookup"><span data-stu-id="7b727-116">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="7b727-117">`IsNot` は `Is` 演算子の逆です。</span><span class="sxs-lookup"><span data-stu-id="7b727-117">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="7b727-118">`IsNot` の利点は、`Not` と `Is` を使用することで読みにくくなる可能性がある洗練されていない構文を回避できることです。</span><span class="sxs-lookup"><span data-stu-id="7b727-118">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="7b727-119">`Is` と `IsNot` の演算子を使用すると、事前バインディング オブジェクトと遅延バインディング オブジェクトの両方をテストできます。</span><span class="sxs-lookup"><span data-stu-id="7b727-119">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="7b727-120">例</span><span class="sxs-lookup"><span data-stu-id="7b727-120">Example</span></span>

<span data-ttu-id="7b727-121">次のコード例では、`Is` 演算子と `IsNot` 演算子の両方を使用して、同じ比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="7b727-121">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="7b727-122">TypeOf 演算子と IsNot 演算子を使用する</span><span class="sxs-lookup"><span data-stu-id="7b727-122">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="7b727-123">Visual Basic 14 以降、`TypeOf` 演算子と `IsNot` 演算子を一緒に使用し、オブジェクトとデータ型の間に互換性が "*ない*" かどうかをテストできます。</span><span class="sxs-lookup"><span data-stu-id="7b727-123">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="7b727-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7b727-124">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="7b727-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b727-125">See also</span></span>

- [<span data-ttu-id="7b727-126">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="7b727-126">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="7b727-127">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="7b727-127">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="7b727-128">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="7b727-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="7b727-129">方法: 2 つのオブジェクトが等しいかどうかをテストする</span><span class="sxs-lookup"><span data-stu-id="7b727-129">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
