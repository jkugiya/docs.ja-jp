---
description: '詳細情報: Static (Visual Basic)'
title: Static
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 03c2e3f64ac9052a0c604b8bc34782af16edbf34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700742"
---
# <a name="static-visual-basic"></a><span data-ttu-id="a32bd-103">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a32bd-103">Static (Visual Basic)</span></span>

<span data-ttu-id="a32bd-104">1 つ以上の宣言されているローカル変数が存在し続け、それらが宣言されているプロシージャの終了後もその最新の値が保持されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="a32bd-104">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a32bd-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="a32bd-105">Remarks</span></span>  

 <span data-ttu-id="a32bd-106">通常、プロシージャ内のローカル変数は、プロシージャが停止するとすぐに存在しなくなります。</span><span class="sxs-lookup"><span data-stu-id="a32bd-106">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="a32bd-107">静的変数は存在し続け、その最新の値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="a32bd-107">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="a32bd-108">次回にコードでプロシージャを呼び出したときに、変数は再初期化されず、それに代入された最新の値も保持されます。</span><span class="sxs-lookup"><span data-stu-id="a32bd-108">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="a32bd-109">静的変数は、それが定義されているクラスまたはモジュールの有効期間にわたって存在し続けます。</span><span class="sxs-lookup"><span data-stu-id="a32bd-109">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a32bd-110">ルール</span><span class="sxs-lookup"><span data-stu-id="a32bd-110">Rules</span></span>  
  
- <span data-ttu-id="a32bd-111">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="a32bd-111">**Declaration Context.**</span></span> <span data-ttu-id="a32bd-112">`Static` は、ローカル変数にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a32bd-112">You can use `Static` only on local variables.</span></span> <span data-ttu-id="a32bd-113">つまり、`Static` 変数の宣言コンテキストは、プロシージャまたはプロシージャ内のブロックにする必要があり、ソース ファイル、名前空間、クラス、構造体、またはモジュールにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a32bd-113">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="a32bd-114">構造体プロシージャ内で `Static` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a32bd-114">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="a32bd-115">`Static` ローカル変数のデータ型は推論できません。</span><span class="sxs-lookup"><span data-stu-id="a32bd-115">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="a32bd-116">詳細については、「[ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a32bd-116">For more information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="a32bd-117">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="a32bd-117">**Combined Modifiers.**</span></span> <span data-ttu-id="a32bd-118">同じ宣言内で `Static` を `ReadOnly`、`Shadows`、または `Shared` と共に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a32bd-118">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a32bd-119">動作</span><span class="sxs-lookup"><span data-stu-id="a32bd-119">Behavior</span></span>  

 <span data-ttu-id="a32bd-120">`Shared` プロシージャで静的変数を宣言する場合、アプリケーション全体で使用できる静的変数のコピーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="a32bd-120">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="a32bd-121">クラスのインスタンスを指す変数ではなく、クラス名を使用して `Shared` プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a32bd-121">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="a32bd-122">`Shared` ではないプロシージャで静的変数を宣言すると、クラスの各インスタンスで使用できる変数のコピーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="a32bd-122">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="a32bd-123">非共有プロシージャを呼び出すには、クラスの特定のインスタンスを指す変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="a32bd-123">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a32bd-124">例</span><span class="sxs-lookup"><span data-stu-id="a32bd-124">Example</span></span>  

 <span data-ttu-id="a32bd-125">次の例は、`Static` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="a32bd-125">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="a32bd-126">`Static` 変数の `totalSales` は、1 回だけ 0 に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="a32bd-126">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="a32bd-127">`updateSales` を入力するたびに、`totalSales` には、それに対して計算した最新の値が引き続き含まれます。</span><span class="sxs-lookup"><span data-stu-id="a32bd-127">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="a32bd-128">`Static` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a32bd-128">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="a32bd-129">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="a32bd-129">Dim Statement</span></span>](../statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a32bd-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a32bd-130">See also</span></span>

- [<span data-ttu-id="a32bd-131">Shadows</span><span class="sxs-lookup"><span data-stu-id="a32bd-131">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="a32bd-132">Shared</span><span class="sxs-lookup"><span data-stu-id="a32bd-132">Shared</span></span>](shared.md)
- [<span data-ttu-id="a32bd-133">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="a32bd-133">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="a32bd-134">変数宣言</span><span class="sxs-lookup"><span data-stu-id="a32bd-134">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="a32bd-135">構造体</span><span class="sxs-lookup"><span data-stu-id="a32bd-135">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a32bd-136">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="a32bd-136">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="a32bd-137">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="a32bd-137">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
