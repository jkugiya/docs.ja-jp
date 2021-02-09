---
description: "詳細情報: BC30982:ループの境界とステップの句が同じ型に変換されないため、'<variablename>' の型を推論できません"
title: ループの境界とステップの句が同じ型に変換されないため、'<variablename>' の型を推論できません
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 399e021500813127df6ecede2534783df09ac8dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641162"
---
# <a name="bc30982-type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="baf19-103">BC30982:ループの境界とステップの句が同じ型に変換されないため、'\<variablename>' の型を推論できません</span><span class="sxs-lookup"><span data-stu-id="baf19-103">BC30982: Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="baf19-104">`For...Next` ループを記述していますが、次の条件が当てはまるため、コンパイラがそのループの中でループ制御変数のデータ型を推論できません。</span><span class="sxs-lookup"><span data-stu-id="baf19-104">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="baf19-105">ループ コントロール変数のデータ型が `As` 句で指定されていません。</span><span class="sxs-lookup"><span data-stu-id="baf19-105">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="baf19-106">ループ境界とステップ変数に少なくとも 2 つのデータ型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="baf19-106">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="baf19-107">データ型の間に標準変換が存在しません。</span><span class="sxs-lookup"><span data-stu-id="baf19-107">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="baf19-108">そのため、コンパイラが、ループの制御変数のデータ型を推論できません。</span><span class="sxs-lookup"><span data-stu-id="baf19-108">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="baf19-109">次の例で、ステップ変数は文字で、ループの境界はどちらも整数です。</span><span class="sxs-lookup"><span data-stu-id="baf19-109">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="baf19-110">文字と整数の間に標準変換がないため、このエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="baf19-110">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="baf19-111">**エラー ID:** BC30982</span><span class="sxs-lookup"><span data-stu-id="baf19-111">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="baf19-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="baf19-112">To correct this error</span></span>

- <span data-ttu-id="baf19-113">必要に応じて、ループの境界とステップ変数の型を変更して、それらのうち少なくとも 1 つが、他の型の拡大変換先の型になるようにします。</span><span class="sxs-lookup"><span data-stu-id="baf19-113">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="baf19-114">前の例では、`stepVar` の型を `Integer` に変更します。</span><span class="sxs-lookup"><span data-stu-id="baf19-114">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="baf19-115">\- または -</span><span class="sxs-lookup"><span data-stu-id="baf19-115">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="baf19-116">明示的な変換関数を使用して、ループの境界とステップ変数を適切な型に変換します。</span><span class="sxs-lookup"><span data-stu-id="baf19-116">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="baf19-117">前の例では、`Val` 関数を `stepVar` に適用します。</span><span class="sxs-lookup"><span data-stu-id="baf19-117">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="baf19-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="baf19-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="baf19-119">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="baf19-119">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="baf19-120">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="baf19-120">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="baf19-121">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="baf19-121">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="baf19-122">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="baf19-122">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="baf19-123">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="baf19-123">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="baf19-124">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="baf19-124">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
