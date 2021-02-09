---
description: '詳細情報: Continue ステートメント (Visual Basic)'
title: Continue ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: c6d67e766b2551956795803076efe639ba3c8c99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673870"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="40056-103">Continue ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40056-103">Continue Statement (Visual Basic)</span></span>

<span data-ttu-id="40056-104">ループの次の反復に直ちに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="40056-104">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40056-105">構文</span><span class="sxs-lookup"><span data-stu-id="40056-105">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="40056-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="40056-106">Remarks</span></span>  

 <span data-ttu-id="40056-107">`Do`、`For`、または `While` ループ内から、そのループの次の反復に移すことができます。</span><span class="sxs-lookup"><span data-stu-id="40056-107">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="40056-108">制御はすぐにループ条件テストに渡されます。これは、`For` または `While` ステートメントに移ったり、`Until` または `While` 句が含まれている `Do` または `Loop` ステートメントに移ったりするのと同じです。</span><span class="sxs-lookup"><span data-stu-id="40056-108">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="40056-109">`Continue` は、移動を許可するループ内の任意の場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="40056-109">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="40056-110">制御の移動を許可するルールは、[GoTo ステートメント](goto-statement.md)を使用する場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="40056-110">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="40056-111">たとえば、ループが `Try` ブロック、`Catch` ブロック、または `Finally` ブロック内に完全に含まれている場合は、`Continue` を使用してループから移動できます。</span><span class="sxs-lookup"><span data-stu-id="40056-111">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="40056-112">一方、`Try`...`End Try` 構造体がループ内に含まれている場合は、`Continue` を使用して `Finally` ブロックから制御を移すことはできません。これを使用して `Try` または `Catch` ブロックから移すことができるのは、`Try`...`End Try` 構造体から完全に移す場合のみです。</span><span class="sxs-lookup"><span data-stu-id="40056-112">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="40056-113">同じ種類のループが入れ子になっている場合 (別の `Do` ループ内の `Do` ループなど)、`Continue Do` ステートメントは、それが含まれている最も内側の `Do` ループの次の反復にスキップします。</span><span class="sxs-lookup"><span data-stu-id="40056-113">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="40056-114">`Continue` を使用して、同じ種類の含まれているループの次の反復にスキップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="40056-114">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="40056-115">さまざまな種類のループが入れ子になっている場合 (`For` ループ内の `Do` ループなど)、`Continue Do` または `Continue For` のいずれかを使用して、いずれかのループの次の反復にスキップできます。</span><span class="sxs-lookup"><span data-stu-id="40056-115">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40056-116">例</span><span class="sxs-lookup"><span data-stu-id="40056-116">Example</span></span>  

 <span data-ttu-id="40056-117">次のコード例では、除数が 0 の場合に、`Continue While` ステートメントを使用して配列の次の列にスキップします。</span><span class="sxs-lookup"><span data-stu-id="40056-117">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="40056-118">`Continue While` は `For` ループ内にあります。</span><span class="sxs-lookup"><span data-stu-id="40056-118">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="40056-119">これにより `While col < lastcol` ステートメントに移動します。これは、`For` ループが含まれている最も内側の `While` ループの次の反復です。</span><span class="sxs-lookup"><span data-stu-id="40056-119">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="40056-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="40056-120">See also</span></span>

- [<span data-ttu-id="40056-121">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="40056-121">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="40056-122">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="40056-122">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="40056-123">While...End While ステートメント</span><span class="sxs-lookup"><span data-stu-id="40056-123">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="40056-124">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="40056-124">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
