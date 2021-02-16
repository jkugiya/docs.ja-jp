---
description: '詳細情報: 方法:プロシージャ引数の値が変更されないように保護する (Visual Basic)'
title: '方法: プロシージャ引数の値が変化しないようにする'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 2e47a584632f124a001617770aeae5104ef20abe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476216"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="bf2a2-103">方法: プロシージャ引数の値が変更されないように保護する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf2a2-103">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>

<span data-ttu-id="bf2a2-104">Visual Basic では、プロシージャでパラメーターが [ByRef](../../../language-reference/modifiers/byref.md) として宣言されている場合、引数の基になる呼び出し元のコードのプログラミング要素への直接参照がプロシージャ コードに渡されます。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-104">If a procedure declares a parameter as [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="bf2a2-105">これにより、プロシージャは引数の基になる呼び出し元のコードの値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-105">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="bf2a2-106">呼び出し元のコードで、そのような変更から保護することが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-106">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="bf2a2-107">プロシージャで対応するパラメーターを [ByVal](../../../language-reference/modifiers/byval.md) として宣言することで、引数を変更から常に保護できます。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-107">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="bf2a2-108">特定の引数を一部のケースでは変更できるようにし、他のケースでは変更できないようにする場合は、その引数を `ByRef` として宣言し、呼び出し元のコードが呼び出しごとに引渡し方法を決定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-108">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="bf2a2-109">これを行うには、対応する引数をかっこで囲んで値渡しにするか、かっこで囲まずに参照渡しにします。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-109">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="bf2a2-110">詳細については、[方法: 引数の値渡しを強制する](./how-to-force-an-argument-to-be-passed-by-value.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-110">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf2a2-111">例</span><span class="sxs-lookup"><span data-stu-id="bf2a2-111">Example</span></span>  

 <span data-ttu-id="bf2a2-112">次の例は、配列変数を受け取り、その要素を操作する 2 つのプロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-112">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="bf2a2-113">`increase` プロシージャは、各要素に 1 を加算するだけです。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-113">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="bf2a2-114">`replace` プロシージャは、`a()` パラメーターに新しい配列を割り当ててから、各要素に 1 を加算します。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-114">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="bf2a2-115">ただし、再割り当ては、呼び出し元のコードの基になる配列変数には影響しません。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-115">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="bf2a2-116">最初の `MsgBox` 呼び出しでは、"After increase(n): 11, 21, 31, 41" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-116">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="bf2a2-117">配列 `n` は参照型であるため、引渡し方法が `ByVal` であっても、`increase` はそのメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-117">Because the array `n` is a reference type, `increase` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="bf2a2-118">2 番目の `MsgBox` 呼び出しでは、"After replace(n): 11, 21, 31, 41" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-118">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="bf2a2-119">`n` は `ByVal` で渡されるため、`replace` は呼び出し元のコードの変数 `n` に新しい配列を割り当てて変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-119">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="bf2a2-120">`replace` が新しい配列インスタンス `k` を作成し、ローカル変数 `a` に割り当てると、呼び出し元のコードによって渡された `n` への参照は失われます。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-120">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="bf2a2-121">`a` のメンバーを変更すると、ローカル配列 `k` だけが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-121">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="bf2a2-122">したがって、`replace` は呼び出し元のコードの配列 `n` の値をインクリメントしません。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-122">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="bf2a2-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bf2a2-123">Compile the code</span></span>  

 <span data-ttu-id="bf2a2-124">Visual Basic の既定では、引数は値渡しになります。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-124">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="bf2a2-125">ただし、宣言されるすべてのパラメーターに、[ByVal](../../../language-reference/modifiers/byval.md) または [ByRef](../../../language-reference/modifiers/byref.md) キーワードを含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-125">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="bf2a2-126">これにより、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bf2a2-126">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf2a2-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf2a2-127">See also</span></span>

- [<span data-ttu-id="bf2a2-128">手順</span><span class="sxs-lookup"><span data-stu-id="bf2a2-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bf2a2-129">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="bf2a2-129">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bf2a2-130">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="bf2a2-130">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="bf2a2-131">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="bf2a2-131">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="bf2a2-132">変更できる引数と変更できない引数の違い</span><span class="sxs-lookup"><span data-stu-id="bf2a2-132">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="bf2a2-133">引数の値渡しと参照渡しの違い</span><span class="sxs-lookup"><span data-stu-id="bf2a2-133">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="bf2a2-134">方法: プロシージャ引数の値を変更する</span><span class="sxs-lookup"><span data-stu-id="bf2a2-134">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="bf2a2-135">方法: 引数の値渡しを強制する</span><span class="sxs-lookup"><span data-stu-id="bf2a2-135">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="bf2a2-136">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="bf2a2-136">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="bf2a2-137">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="bf2a2-137">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
