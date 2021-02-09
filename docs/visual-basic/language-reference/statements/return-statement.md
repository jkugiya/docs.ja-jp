---
description: '詳細情報: Return ステートメント (Visual Basic)'
title: Return ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 62086090ede7e634b09d3edc3dc42feb28d15793
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741199"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="04363-103">Return ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04363-103">Return Statement (Visual Basic)</span></span>

<span data-ttu-id="04363-104">`Function`、`Sub`、`Get`、`Set`、または `Operator` プロシージャを呼び出したコードに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="04363-104">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04363-105">構文</span><span class="sxs-lookup"><span data-stu-id="04363-105">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="04363-106">パーツ</span><span class="sxs-lookup"><span data-stu-id="04363-106">Part</span></span>  

 `expression`  
 <span data-ttu-id="04363-107">`Function`、`Get`、または `Operator` プロシージャで必要です。</span><span class="sxs-lookup"><span data-stu-id="04363-107">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="04363-108">呼び出し元のコードに返される値を表す式。</span><span class="sxs-lookup"><span data-stu-id="04363-108">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04363-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="04363-109">Remarks</span></span>  

 <span data-ttu-id="04363-110">`Sub` または `Set` プロシージャでは、`Return` ステートメントは `Exit Sub` または `Exit Property` ステートメントと同じです。`expression` は指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="04363-110">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="04363-111">`Function`、`Get`、または `Operator` プロシージャでは、`Return` ステートメントに `expression` を含める必要があります。また、`expression` は、プロシージャの戻り値の型に変換可能なデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="04363-111">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="04363-112">`Function` または `Get` プロシージャでは、プロシージャ名に式を代入して戻り値として使用し、`Exit Function` または `Exit Property` ステートメントを実行する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="04363-112">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="04363-113">`Operator` プロシージャでは、`Return expression` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04363-113">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="04363-114">`Return` ステートメントは、必要に応じて同じプロシージャにいくつでも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="04363-114">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04363-115">`Finally` ブロック内のコードは、`Try` または `Catch` ブロック内で `Return` ステートメントが検出された後、その `Return` ステートメントが実行される前に実行されます。</span><span class="sxs-lookup"><span data-stu-id="04363-115">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="04363-116">`Return` ステートメントを `Finally` ブロックに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="04363-116">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04363-117">例</span><span class="sxs-lookup"><span data-stu-id="04363-117">Example</span></span>  

 <span data-ttu-id="04363-118">次の例では、`Return` ステートメントを複数回使用して、プロシージャが他の操作を行う必要がない場合に、呼び出し元のコードに戻ります。</span><span class="sxs-lookup"><span data-stu-id="04363-118">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="04363-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="04363-119">See also</span></span>

- [<span data-ttu-id="04363-120">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="04363-120">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="04363-121">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="04363-121">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="04363-122">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="04363-122">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="04363-123">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="04363-123">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="04363-124">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="04363-124">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="04363-125">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="04363-125">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="04363-126">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="04363-126">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="04363-127">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="04363-127">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
