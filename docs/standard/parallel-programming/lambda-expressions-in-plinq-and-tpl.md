---
description: '詳細情報: PLINQ および TPL のラムダ式'
title: PLINQ および TPL のラムダ式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 86ecfca0e9866a08b4f4bb40d15b74257ec4540e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798031"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="8621e-103">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="8621e-103">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="8621e-104">タスク並列ライブラリ (TPL) には、入力パラメーターとしてデリゲートの <xref:System.Func%601?displayProperty=nameWithType> または <xref:System.Action?displayProperty=nameWithType> ファミリのいずれかを受け取る多くのメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8621e-104">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="8621e-105">これらのデリゲートを使用して、並列ループ、タスク、またはクエリにカスタムのプログラム ロジックを渡します。</span><span class="sxs-lookup"><span data-stu-id="8621e-105">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="8621e-106">TPL と PLINQ のコード例では、ラムダ式を使用して、インライン コード ブロックとしてこれらのデリゲートのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8621e-106">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="8621e-107">このトピックでは、Func および Action について簡単に紹介し、タスク並列ライブラリと PLINQ でラムダ式を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8621e-107">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="8621e-108">一般的なデリゲートの詳細については、「[デリゲート](../../csharp/programming-guide/delegates/index.md)」と「[デリゲート](../../visual-basic/programming-guide/language-features/delegates/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8621e-108">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="8621e-109">C# と Visual Basic のラムダ式の詳細については、それぞれ「[ラムダ式](../../csharp/language-reference/operators/lambda-expressions.md)」と「[ラムダ式](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8621e-109">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/language-reference/operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="8621e-110">Func デリゲート</span><span class="sxs-lookup"><span data-stu-id="8621e-110">Func Delegate</span></span>

<span data-ttu-id="8621e-111">`Func` デリゲートは、値を返すメソッドをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="8621e-111">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="8621e-112">`Func` シグネチャでは、末尾または最も右の型パラメーターが常に戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="8621e-112">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="8621e-113">コンパイラ エラーの一般的な原因の 1 つは、2 つの入力パラメーターを <xref:System.Func%602?displayProperty=nameWithType> に渡そうとしていることです。この型は、実際には 1 つの入力パラメーターのみを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8621e-113">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="8621e-114">.NET では、17 のバージョンの `Func` が定義されています (<xref:System.Func%601?displayProperty=nameWithType>、<xref:System.Func%602?displayProperty=nameWithType>、<xref:System.Func%603?displayProperty=nameWithType> ... <xref:System.Func%6017?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="8621e-114">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="8621e-115">Action デリゲート</span><span class="sxs-lookup"><span data-stu-id="8621e-115">Action Delegate</span></span>

<span data-ttu-id="8621e-116"><xref:System.Action?displayProperty=nameWithType> デリゲートは、値を返さないメソッド (Visual Basic では Sub) をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="8621e-116">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="8621e-117">`Action` 型シグネチャでは、型パラメーターは、入力パラメーターのみを表します。</span><span class="sxs-lookup"><span data-stu-id="8621e-117">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="8621e-118">`Func` と同じように、.NET では、型パラメーターを持たないバージョンから 16 の型パラメーターを持つバージョンまでの 17 のバージョンの `Action` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="8621e-118">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="8621e-119">例</span><span class="sxs-lookup"><span data-stu-id="8621e-119">Example</span></span>

<span data-ttu-id="8621e-120"><xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> メソッドの次の例は、ラムダ式を使用して、Func および Action の両方のデリゲートを表す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8621e-120">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="8621e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8621e-121">See also</span></span>

- [<span data-ttu-id="8621e-122">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="8621e-122">Parallel Programming</span></span>](index.md)
