---
description: '詳細情報: 反復子 (Visual Basic)'
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 7a3329ba23a3f2487343b332f3bb9c4b19c36496
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730526"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="f8111-103">反復子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8111-103">Iterator (Visual Basic)</span></span>

<span data-ttu-id="f8111-104">関数または `Get` アクセサーが反復子であることを示します。</span><span class="sxs-lookup"><span data-stu-id="f8111-104">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8111-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8111-105">Remarks</span></span>  

 <span data-ttu-id="f8111-106">*反復子* は、コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8111-106">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="f8111-107">反復子は、[Yield](../statements/yield-statement.md) ステートメントを使用して、コレクションの各要素を 1 回に 1 つ返します。</span><span class="sxs-lookup"><span data-stu-id="f8111-107">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="f8111-108">`Yield` ステートメントに達すると、コードの現在の場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="f8111-108">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="f8111-109">次回、Iterator 関数が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="f8111-109">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="f8111-110">反復子は、関数として実装することも、プロパティ定義の `Get` アクセサーとして実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="f8111-110">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="f8111-111">`Iterator` 修飾子は、Iterator 関数または `Get` アクセサーの宣言に記述されます。</span><span class="sxs-lookup"><span data-stu-id="f8111-111">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="f8111-112">[For Each...Next ステートメント](../statements/for-each-next-statement.md)を使用して、クライアント コードから反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f8111-112">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="f8111-113">Iterator 関数または `Get` アクセサーの戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> となります。</span><span class="sxs-lookup"><span data-stu-id="f8111-113">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="f8111-114">反復子に `ByRef` パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f8111-114">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="f8111-115">反復子を、イベント、インスタンス コンストラクター、静的コンストラクター、静的デストラクターで指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f8111-115">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="f8111-116">反復子は、匿名関数にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f8111-116">An iterator can be an anonymous function.</span></span> <span data-ttu-id="f8111-117">詳細については、「 [反復子](../../programming-guide/concepts/iterators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8111-117">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f8111-118">使用方法</span><span class="sxs-lookup"><span data-stu-id="f8111-118">Usage</span></span>  

 <span data-ttu-id="f8111-119">`Iterator` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f8111-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="f8111-120">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="f8111-120">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="f8111-121">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="f8111-121">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="f8111-122">例</span><span class="sxs-lookup"><span data-stu-id="f8111-122">Example</span></span>  

 <span data-ttu-id="f8111-123">次の例では、Iterator 関数を示します。</span><span class="sxs-lookup"><span data-stu-id="f8111-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="f8111-124">Iterator 関数には、[For…Next](../statements/for-next-statement.md) ループ内に `Yield` ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="f8111-124">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="f8111-125">`Main` 内の [For Each](../statements/for-each-next-statement.md) ステートメント本体の各反復処理では、`Power` Iterator 関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f8111-125">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="f8111-126">Iterator 関数を呼び出すごとに、`Yield` ステートメントの次の実行に進みます。これは、`For…Next` ループの次の反復処理で行われます。</span><span class="sxs-lookup"><span data-stu-id="f8111-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="f8111-127">例</span><span class="sxs-lookup"><span data-stu-id="f8111-127">Example</span></span>  

 <span data-ttu-id="f8111-128">次の例は、反復子である `Get` アクセサーを示しています。</span><span class="sxs-lookup"><span data-stu-id="f8111-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="f8111-129">`Iterator` 修飾子は、プロパティ宣言にあります。</span><span class="sxs-lookup"><span data-stu-id="f8111-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="f8111-130">その他の例については、「[反復子](../../programming-guide/concepts/iterators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8111-130">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8111-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8111-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="f8111-132">反復子</span><span class="sxs-lookup"><span data-stu-id="f8111-132">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="f8111-133">Yield ステートメント</span><span class="sxs-lookup"><span data-stu-id="f8111-133">Yield Statement</span></span>](../statements/yield-statement.md)
