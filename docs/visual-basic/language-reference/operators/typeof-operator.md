---
description: '詳細情報: TypeOf 演算子 (Visual Basic)'
title: TypeOf 演算子
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 59a03095b2abbaa304221b30402b9a058954db63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795236"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="00062-103">TypeOf 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00062-103">TypeOf Operator (Visual Basic)</span></span>

<span data-ttu-id="00062-104">式の結果の実行時の型に、指定された型との型互換性があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="00062-104">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="00062-105">構文</span><span class="sxs-lookup"><span data-stu-id="00062-105">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="00062-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="00062-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="00062-107">必須。</span><span class="sxs-lookup"><span data-stu-id="00062-107">Returned.</span></span> <span data-ttu-id="00062-108">`Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="00062-108">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="00062-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="00062-109">Required.</span></span> <span data-ttu-id="00062-110">参照型に評価される任意の式。</span><span class="sxs-lookup"><span data-stu-id="00062-110">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="00062-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="00062-111">Required.</span></span> <span data-ttu-id="00062-112">任意のデータ型名。</span><span class="sxs-lookup"><span data-stu-id="00062-112">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00062-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="00062-113">Remarks</span></span>  

 <span data-ttu-id="00062-114">`TypeOf` 演算子は、`objectexpression` の実行時の型が `typename` と互換性があるかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="00062-114">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="00062-115">互換性は、`typename` の型のカテゴリに依存します。</span><span class="sxs-lookup"><span data-stu-id="00062-115">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="00062-116">互換性を決定する方法を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="00062-116">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="00062-117">`typename` の型のカテゴリ</span><span class="sxs-lookup"><span data-stu-id="00062-117">Type category of `typename`</span></span>|<span data-ttu-id="00062-118">互換性の条件</span><span class="sxs-lookup"><span data-stu-id="00062-118">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="00062-119">クラス</span><span class="sxs-lookup"><span data-stu-id="00062-119">Class</span></span>|<span data-ttu-id="00062-120">`objectexpression` が `typename` 型である、または `typename` を継承する</span><span class="sxs-lookup"><span data-stu-id="00062-120">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="00062-121">構造体</span><span class="sxs-lookup"><span data-stu-id="00062-121">Structure</span></span>|<span data-ttu-id="00062-122">`objectexpression` が `typename` 型である</span><span class="sxs-lookup"><span data-stu-id="00062-122">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="00062-123">Interface</span><span class="sxs-lookup"><span data-stu-id="00062-123">Interface</span></span>|<span data-ttu-id="00062-124">`objectexpression` が `typename` を実装する、または `typename` を実装するクラスを継承する</span><span class="sxs-lookup"><span data-stu-id="00062-124">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="00062-125">`objectexpression` の実行時の型が互換性の条件を満たす場合、`result` は `True` です。</span><span class="sxs-lookup"><span data-stu-id="00062-125">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="00062-126">それ以外の場合、`result` は `False` です。</span><span class="sxs-lookup"><span data-stu-id="00062-126">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="00062-127">`objectexpression` が null の場合、`TypeOf`...`Is` は `False` を返し、...`IsNot` は `True` を返します。</span><span class="sxs-lookup"><span data-stu-id="00062-127">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="00062-128">`TypeOf` は、常に `Is` キーワードと共に `TypeOf`...`Is` 式を構築するか、または `IsNot` キーワードと共に `TypeOf`...`IsNot` 式を構築します。</span><span class="sxs-lookup"><span data-stu-id="00062-128">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00062-129">例</span><span class="sxs-lookup"><span data-stu-id="00062-129">Example</span></span>  

 <span data-ttu-id="00062-130">次の例では、`TypeOf`...`Is` 式でさまざまなデータ型を使用して、2 つのオブジェクト参照変数の型の互換性をテストしています。</span><span class="sxs-lookup"><span data-stu-id="00062-130">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="00062-131">変数 `refInteger` は、実行時の型 `Integer` を持ちます。</span><span class="sxs-lookup"><span data-stu-id="00062-131">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="00062-132">`Integer` と互換性がありますが、`Double` との互換性はありません。</span><span class="sxs-lookup"><span data-stu-id="00062-132">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="00062-133">変数 `refForm` は、実行時の型 <xref:System.Windows.Forms.Form> を持ちます。</span><span class="sxs-lookup"><span data-stu-id="00062-133">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="00062-134">この変数は、<xref:System.Windows.Forms.Form> (同じ型)、<xref:System.Windows.Forms.Control> (<xref:System.Windows.Forms.Form> は <xref:System.Windows.Forms.Control> を継承する)、および <xref:System.ComponentModel.IComponent> (<xref:System.Windows.Forms.Form> は <xref:System.ComponentModel.IComponent> を実装する <xref:System.ComponentModel.Component> を継承する) と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="00062-134">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="00062-135">ただし、`refForm` には <xref:System.Windows.Forms.Label> との互換性はありません。</span><span class="sxs-lookup"><span data-stu-id="00062-135">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00062-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="00062-136">See also</span></span>

- [<span data-ttu-id="00062-137">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="00062-137">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="00062-138">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="00062-138">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="00062-139">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="00062-139">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="00062-140">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="00062-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="00062-141">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="00062-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="00062-142">演算子および式</span><span class="sxs-lookup"><span data-stu-id="00062-142">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
