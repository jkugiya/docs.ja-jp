---
description: '詳細情報: 方法:プロシージャを作成する (Visual Basic)'
title: '方法: プロシージャを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: bca5ad24e845600642429273f6053787dd290b88
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472541"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="8134f-103">方法: プロシージャを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8134f-103">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="8134f-104">プロシージャは、開始宣言ステートメント (`Sub` または `Function`) と終了宣言ステートメント (`End Sub` または `End Function`) で囲みます。</span><span class="sxs-lookup"><span data-stu-id="8134f-104">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="8134f-105">プロシージャのコードはすべて、これらのステートメントの間にあります。</span><span class="sxs-lookup"><span data-stu-id="8134f-105">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="8134f-106">あるプロシージャに別のプロシージャを含めることはできないため、その開始と終了のステートメントは他のプロシージャの外部にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="8134f-106">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="8134f-107">異なる場所で同じタスクを実行するコードがある場合は、そのタスクをプロシージャとして一度記述してから、コード内の異なる場所から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8134f-107">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="8134f-108">値を返さないプロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="8134f-108">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="8134f-109">他のプロシージャの外部で、`Sub` ステートメントを使用し、その後に `End Sub` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8134f-109">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="8134f-110">`Sub` ステートメントで、`Sub` キーワードの後にプロシージャの名前を指定してから、かっこで囲んだパラメーター リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="8134f-110">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="8134f-111">`Sub` および `End Sub` ステートメントの間に、プロシージャのコード ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="8134f-111">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="8134f-112">値を返すプロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="8134f-112">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="8134f-113">他のプロシージャの外部で、`Function` ステートメントを使用し、その後に `End Function` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8134f-113">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="8134f-114">`Function` ステートメントで、`Function` キーワードの後にプロシージャの名前を指定します。次に、かっこで囲んだパラメーター リストを指定し、戻り値のデータ型を指定する `As` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="8134f-114">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="8134f-115">`Function` および `End Function` ステートメントの間に、プロシージャのコード ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="8134f-115">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="8134f-116">`Return` ステートメントを使用して、呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="8134f-116">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="8134f-117">新しいプロシージャを古い繰り返しコード ブロックに接続するには</span><span class="sxs-lookup"><span data-stu-id="8134f-117">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="8134f-118">古いコードでアクセスできる場所に新しいプロシージャを定義していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8134f-118">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="8134f-119">古い繰り返しコード ブロックで、繰り返しタスクを実行するステートメントを、`Sub` または `Function` プロシージャを呼び出す単一のステートメントに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8134f-119">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="8134f-120">プロシージャが、値を返す `Function` である場合は、呼び出し元のステートメントで確実に戻り値を持つアクション (変数に格納するなど) を実行するようにしてください。そうしないと、値が失われます。</span><span class="sxs-lookup"><span data-stu-id="8134f-120">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="8134f-121">例</span><span class="sxs-lookup"><span data-stu-id="8134f-121">Example</span></span>

 <span data-ttu-id="8134f-122">次の `Function` プロシージャでは、他の 2 つの辺の値を指定して、直角三角形の最も長い辺 (斜辺) を計算します。</span><span class="sxs-lookup"><span data-stu-id="8134f-122">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="8134f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8134f-123">See also</span></span>

- [<span data-ttu-id="8134f-124">手順</span><span class="sxs-lookup"><span data-stu-id="8134f-124">Procedures</span></span>](index.md)
- [<span data-ttu-id="8134f-125">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="8134f-125">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="8134f-126">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="8134f-126">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="8134f-127">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="8134f-127">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="8134f-128">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="8134f-128">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="8134f-129">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="8134f-129">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8134f-130">再帰プロシージャ</span><span class="sxs-lookup"><span data-stu-id="8134f-130">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="8134f-131">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="8134f-131">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="8134f-132">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="8134f-132">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="8134f-133">オブジェクト指向プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8134f-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
