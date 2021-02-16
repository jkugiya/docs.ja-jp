---
description: '詳細情報: 方法:新しい変数を作成する (Visual Basic)'
title: '方法: 新しい変数を作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: b473a247bc5b4d9c1d65f4721ecba3621b232e27
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481962"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="65c90-103">方法: 新しい変数を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65c90-103">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="65c90-104">[Dim ステートメント](../../../language-reference/statements/dim-statement.md)を使用して変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="65c90-104">You create a variable with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="65c90-105">新しい変数を作成するには</span><span class="sxs-lookup"><span data-stu-id="65c90-105">To create a new variable</span></span>

1. <span data-ttu-id="65c90-106">`Dim` ステートメントで変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="65c90-106">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="65c90-107">[Private](../../../language-reference/modifiers/private.md)、[Static](../../../language-reference/modifiers/static.md)、[Shadows](../../../language-reference/modifiers/shadows.md)、[WithEvents](../../../language-reference/modifiers/withevents.md) など、変数の特性の指定を含めます。</span><span class="sxs-lookup"><span data-stu-id="65c90-107">Include specifications for the variable's characteristics, such as [Private](../../../language-reference/modifiers/private.md), [Static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md), or [WithEvents](../../../language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="65c90-108">詳細については、「[宣言された要素の特性](../declared-elements/declared-element-characteristics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65c90-108">For more information, see [Declared Element Characteristics](../declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="65c90-109">宣言で他のキーワードを使用する場合、`Dim` キーワードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="65c90-109">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="65c90-110">指定の後ろに変数の名前を指定します。これは Visual Basic のルールおよび規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="65c90-110">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="65c90-111">詳細については、「[宣言された要素の名前](../declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65c90-111">For more information, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="65c90-112">名前の後ろに [As](../../../language-reference/statements/as-clause.md) 句を指定して、変数のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="65c90-112">Follow the name with the [As](../../../language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="65c90-113">データ型を指定しない場合、既定値の `Object` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="65c90-113">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="65c90-114">`As` 句の後ろに等号 (`=`) を指定し、等号の後ろに変数の初期値を指定します。</span><span class="sxs-lookup"><span data-stu-id="65c90-114">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="65c90-115">Visual Basic により、`Dim` ステートメントが実行されるたびに、指定した値が変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="65c90-115">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="65c90-116">初期値を指定しない場合、Visual Basic では、`Dim` ステートメントを含むコードに初めて入ったときに、その変数のデータ型の既定の初期値が代入されます。</span><span class="sxs-lookup"><span data-stu-id="65c90-116">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="65c90-117">変数が参照型である場合は、[New 演算子](../../../language-reference/operators/new-operator.md) キーワードを `As` 句に含めると、そのクラスのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="65c90-117">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="65c90-118">`New` を使用しない場合、変数の初期値は [Nothing](../../../language-reference/nothing.md) です。</span><span class="sxs-lookup"><span data-stu-id="65c90-118">If you do not use `New`, the initial value of the variable is [Nothing](../../../language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="65c90-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="65c90-119">See also</span></span>

- [<span data-ttu-id="65c90-120">変数</span><span class="sxs-lookup"><span data-stu-id="65c90-120">Variables</span></span>](index.md)
- [<span data-ttu-id="65c90-121">変数宣言</span><span class="sxs-lookup"><span data-stu-id="65c90-121">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="65c90-122">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="65c90-122">Declared Element Names</span></span>](../declared-elements/declared-element-names.md)
- [<span data-ttu-id="65c90-123">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="65c90-123">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="65c90-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="65c90-124">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="65c90-125">ステートメント</span><span class="sxs-lookup"><span data-stu-id="65c90-125">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="65c90-126">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="65c90-126">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="65c90-127">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="65c90-127">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
