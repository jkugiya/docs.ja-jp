---
description: '詳細情報: Throw ステートメント (Visual Basic)'
title: Throw ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: b7fa4183b5997e5dac8045502a8eed1afe66fc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740939"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="94781-103">Throw ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94781-103">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="94781-104">プロシージャ内で例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="94781-104">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="94781-105">構文</span><span class="sxs-lookup"><span data-stu-id="94781-105">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="94781-106">パーツ</span><span class="sxs-lookup"><span data-stu-id="94781-106">Part</span></span>

`expression`\
<span data-ttu-id="94781-107">スローされる例外に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="94781-107">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="94781-108">`Catch` ステートメント内に存在する場合は省略可能で、それ以外の場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="94781-108">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="94781-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="94781-109">Remarks</span></span>

<span data-ttu-id="94781-110">`Throw` ステートメントでは、構造化例外処理コード (`Try`...`Catch`...`Finally`) または非構造化例外処理コード (`On Error GoTo`) で処理できる例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="94781-110">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="94781-111">`Throw` ステートメントを使用して、コード内でエラーをトラップできます。Visual Basic によって、適切な例外処理コードが見つかるまで呼び出し履歴が上に移動するためです。</span><span class="sxs-lookup"><span data-stu-id="94781-111">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="94781-112">式が指定されていない `Throw` ステートメントは、`Catch` ステートメントでのみ使用できます。この場合、ステートメントでは、現在 `Catch` ステートメントによって処理されている例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="94781-112">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="94781-113">`Throw` ステートメントによって、`expression` 例外の呼び出し履歴がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="94781-113">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="94781-114">`expression` が指定されていない場合、呼び出し履歴は変更されません。</span><span class="sxs-lookup"><span data-stu-id="94781-114">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="94781-115"><xref:System.Exception.StackTrace%2A> プロパティによって、例外の呼び出し履歴にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="94781-115">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="94781-116">例</span><span class="sxs-lookup"><span data-stu-id="94781-116">Example</span></span>

<span data-ttu-id="94781-117">次のコードでは、`Throw` ステートメントを使用して、例外をスローしています。</span><span class="sxs-lookup"><span data-stu-id="94781-117">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="94781-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="94781-118">See also</span></span>

- [<span data-ttu-id="94781-119">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="94781-119">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="94781-120">On Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="94781-120">On Error Statement</span></span>](on-error-statement.md)
