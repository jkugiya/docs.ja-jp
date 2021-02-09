---
description: '詳細情報: Call ステートメント (Visual Basic)'
title: Call ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 70e6c109621c3710ad9476a952e9c384a142ba3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674013"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="91284-103">Call ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91284-103">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="91284-104">`Function`、`Sub`、またはダイナミックリンク ライブラリ (DLL) プロシージャに制御を渡します。</span><span class="sxs-lookup"><span data-stu-id="91284-104">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91284-105">構文</span><span class="sxs-lookup"><span data-stu-id="91284-105">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="91284-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="91284-106">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="91284-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="91284-107">Required.</span></span> <span data-ttu-id="91284-108">呼び出すプロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="91284-108">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="91284-109">任意。</span><span class="sxs-lookup"><span data-stu-id="91284-109">Optional.</span></span> <span data-ttu-id="91284-110">プロシージャの呼び出し時にプロシージャに渡す引数を表す変数または式のリスト。</span><span class="sxs-lookup"><span data-stu-id="91284-110">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="91284-111">複数の引数はコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="91284-111">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="91284-112">`argumentList` を含める場合は、かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="91284-112">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="91284-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="91284-113">Remarks</span></span>

 <span data-ttu-id="91284-114">`Call` キーワードは、プロシージャを呼び出すときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="91284-114">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="91284-115">ほとんどのプロシージャ呼び出しでは、このキーワードを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="91284-115">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="91284-116">通常、呼び出される式が識別子で始まっていない場合は、`Call` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="91284-116">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="91284-117">他の用途には `Call` キーワードを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="91284-117">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="91284-118">プロシージャが値を返す場合は、`Call` ステートメントによって値が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="91284-118">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="91284-119">例</span><span class="sxs-lookup"><span data-stu-id="91284-119">Example</span></span>

 <span data-ttu-id="91284-120">次のコードは、プロシージャを呼び出すために `Call` キーワードが必要となる 2 つの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="91284-120">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="91284-121">どちらの例も、呼び出される式は識別子で始まっていません。</span><span class="sxs-lookup"><span data-stu-id="91284-121">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="91284-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="91284-122">See also</span></span>

- [<span data-ttu-id="91284-123">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="91284-123">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="91284-124">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="91284-124">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="91284-125">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="91284-125">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="91284-126">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="91284-126">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
