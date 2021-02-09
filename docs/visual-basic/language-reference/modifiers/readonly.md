---
description: '詳細情報: ReadOnly (Visual Basic)'
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: f510271531f6e6604f2b542d8331d1a1d7f64d58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700911"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="ba52e-103">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba52e-103">ReadOnly (Visual Basic)</span></span>

<span data-ttu-id="ba52e-104">変数またはプロパティを読み込めるが、書き込みはできないことを示します。</span><span class="sxs-lookup"><span data-stu-id="ba52e-104">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba52e-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="ba52e-105">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="ba52e-106">ルール</span><span class="sxs-lookup"><span data-stu-id="ba52e-106">Rules</span></span>

- <span data-ttu-id="ba52e-107">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="ba52e-107">**Declaration Context.**</span></span> <span data-ttu-id="ba52e-108">`ReadOnly` は、モジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba52e-108">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="ba52e-109">つまり、`ReadOnly` 要素の宣言コンテキストは、クラス、構造体、またはモジュールにする必要があり、ソース ファイル、名前空間、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ba52e-109">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="ba52e-110">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="ba52e-110">**Combined Modifiers.**</span></span> <span data-ttu-id="ba52e-111">同じ宣言内で `ReadOnly` を `Static` と共に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="ba52e-111">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="ba52e-112">**値の代入。**</span><span class="sxs-lookup"><span data-stu-id="ba52e-112">**Assigning a Value.**</span></span> <span data-ttu-id="ba52e-113">`ReadOnly` プロパティを使用するコードでは、その値を設定できません。</span><span class="sxs-lookup"><span data-stu-id="ba52e-113">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="ba52e-114">ただし、基になるストレージにアクセスできるコードは、いつでも値を代入したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="ba52e-114">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="ba52e-115">`ReadOnly` 変数に値を代入できるのは、その宣言内、またはそれが定義されているクラスまたは構造体のコンストラクター内でのみです。</span><span class="sxs-lookup"><span data-stu-id="ba52e-115">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="ba52e-116">ReadOnly 変数を使用するタイミング</span><span class="sxs-lookup"><span data-stu-id="ba52e-116">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="ba52e-117">定数値の宣言と割り当てに [Const ステートメント](../statements/const-statement.md) を使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba52e-117">There are situations in which you cannot use a [Const Statement](../statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="ba52e-118">たとえば、`Const` ステートメントが割り当てたいデータ型を受け入れない場合や、コンパイル時に定数式を使用して値を計算できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba52e-118">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="ba52e-119">コンパイル時に値がわからない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ba52e-119">You might not even know the value at compile time.</span></span> <span data-ttu-id="ba52e-120">このような場合は、`ReadOnly` 変数を使用して定数値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="ba52e-120">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba52e-121">変数のデータ型が配列やクラス インスタンスなどの参照型である場合は、変数自体が `ReadOnly` の場合でも、そのメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ba52e-121">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="ba52e-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ba52e-122">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="ba52e-123">初期化されると、`characterArray()` が指す配列は、"x"、"y"、および "z" を保持します。</span><span class="sxs-lookup"><span data-stu-id="ba52e-123">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="ba52e-124">変数 `characterArray` が `ReadOnly` であるため、初期化後にその値を変更することはできません。つまり、新しい配列を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="ba52e-124">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="ba52e-125">ただし、1 つまたは複数の配列メンバーの値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ba52e-125">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="ba52e-126">プロシージャ `ChangeArrayElement` の呼び出しの後、`characterArray()` が指す配列は "x"、"M"、および "z" を保持します。</span><span class="sxs-lookup"><span data-stu-id="ba52e-126">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="ba52e-127">これは、プロシージャ パラメーターを [ByVal](byval.md) として宣言するのと似ています。これにより、プロシージャは呼び出し元の引数自体を変更できなくなりますが、メンバーを変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ba52e-127">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="ba52e-128">例</span><span class="sxs-lookup"><span data-stu-id="ba52e-128">Example</span></span>

<span data-ttu-id="ba52e-129">次の例では、従業員が採用された日付の `ReadOnly` プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="ba52e-129">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="ba52e-130">クラスはプロパティ値を `Private` 変数として内部的に格納し、クラス内のコードだけがその値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ba52e-130">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="ba52e-131">ただし、プロパティは `Public` であり、クラスにアクセスできるすべてのコードでプロパティを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="ba52e-131">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="ba52e-132">`ReadOnly` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba52e-132">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="ba52e-133">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="ba52e-133">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="ba52e-134">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="ba52e-134">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="ba52e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba52e-135">See also</span></span>

- [<span data-ttu-id="ba52e-136">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="ba52e-136">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="ba52e-137">キーワード</span><span class="sxs-lookup"><span data-stu-id="ba52e-137">Keywords</span></span>](../keywords/index.md)
