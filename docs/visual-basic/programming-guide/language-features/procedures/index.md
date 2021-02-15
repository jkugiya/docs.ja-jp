---
description: '詳細情報: Visual Basic におけるプロシージャ'
title: プロシージャ
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: faff01163511d71f6dc5c6fd540b292e1dea72fb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475150"
---
# <a name="procedures-in-visual-basic"></a><span data-ttu-id="dc33f-103">Visual Basic におけるプロシージャ</span><span class="sxs-lookup"><span data-stu-id="dc33f-103">Procedures in Visual Basic</span></span>

<span data-ttu-id="dc33f-104">*プロシージャ* は、宣言ステートメント (`Function`、`Sub`、`Operator`、`Get`、`Set`) とこれに一致する `End` 宣言で囲まれた、Visual Basic ステートメントのブロックです。</span><span class="sxs-lookup"><span data-stu-id="dc33f-104">A *procedure* is a block of Visual Basic statements enclosed by a declaration statement (`Function`, `Sub`, `Operator`, `Get`, `Set`) and a matching `End` declaration.</span></span> <span data-ttu-id="dc33f-105">Visual Basic のすべての実行可能なステートメントは何らかのプロシージャに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc33f-105">All executable statements in Visual Basic must be within some procedure.</span></span>  
  
## <a name="calling-a-procedure"></a><span data-ttu-id="dc33f-106">プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="dc33f-106">Calling a Procedure</span></span>  

 <span data-ttu-id="dc33f-107">コード内の他の場所からプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="dc33f-107">You invoke a procedure from some other place in the code.</span></span> <span data-ttu-id="dc33f-108">これは、*プロシージャ コール* と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="dc33f-108">This is known as a *procedure call*.</span></span> <span data-ttu-id="dc33f-109">プロシージャの実行が終了すると、それを呼び出したコード (*呼び出しコード* と呼ばれます) に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc33f-109">When the procedure is finished running, it returns control to the code that invoked it, which is known as the *calling code*.</span></span> <span data-ttu-id="dc33f-110">呼び出しコードは、名前でプロシージャを指定して、これに制御を転送するステートメント、またはステートメント内の式です。</span><span class="sxs-lookup"><span data-stu-id="dc33f-110">The calling code is a statement, or an expression within a statement, that specifies the procedure by name and transfers control to it.</span></span>  
  
## <a name="returning-from-a-procedure"></a><span data-ttu-id="dc33f-111">プロシージャからの復帰</span><span class="sxs-lookup"><span data-stu-id="dc33f-111">Returning from a Procedure</span></span>  

 <span data-ttu-id="dc33f-112">プロシージャは、実行が終了すると、呼び出しコードに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="dc33f-112">A procedure returns control to the calling code when it has finished running.</span></span> <span data-ttu-id="dc33f-113">これを行うには、[Return ステートメント](../../../language-reference/statements/return-statement.md)、プロシージャに適した [Exit ステートメント](../../../language-reference/statements/exit-statement.md)、またはプロシージャの [End \<keyword> ステートメント](../../../language-reference/statements/end-keyword-statement.md)を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-113">To do this, it can use a [Return Statement](../../../language-reference/statements/return-statement.md), the appropriate [Exit Statement](../../../language-reference/statements/exit-statement.md) statement for the procedure, or the procedure's [End \<keyword> Statement](../../../language-reference/statements/end-keyword-statement.md) statement.</span></span> <span data-ttu-id="dc33f-114">これで、プロシージャ コールの次の時点で、制御が呼び出しコードに渡されます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-114">Control then passes to the calling code following the point of the procedure call.</span></span>  
  
- <span data-ttu-id="dc33f-115">`Return` ステートメントでは、ただちに呼び出しコードに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc33f-115">With a `Return` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="dc33f-116">`Return` ステートメントより後のステートメントは実行されません。</span><span class="sxs-lookup"><span data-stu-id="dc33f-116">Statements following the `Return` statement do not run.</span></span> <span data-ttu-id="dc33f-117">同じプロシージャ内に複数の `Return` ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-117">You can have more than one `Return` statement in the same procedure.</span></span>  
  
- <span data-ttu-id="dc33f-118">`Exit Sub` または `Exit Function` ステートメントでは、ただちに呼び出しコードに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc33f-118">With an `Exit Sub` or `Exit Function` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="dc33f-119">`Exit` ステートメントより後のステートメントは実行されません。</span><span class="sxs-lookup"><span data-stu-id="dc33f-119">Statements following the `Exit` statement do not run.</span></span> <span data-ttu-id="dc33f-120">同じプロシージャ内に複数の `Exit` ステートメントを含めることができ、さらに同じプロシージャ内に `Return` ステートメントと `Exit` ステートメントを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-120">You can have more than one `Exit` statement in the same procedure, and you can mix `Return` and `Exit` statements in the same procedure.</span></span>  
  
- <span data-ttu-id="dc33f-121">プロシージャに `Return` または `Exit` のステートメントが含まれていない場合、プロシージャ本体の最後のステートメントの後の `End Sub` または `End Function`、`End Get` または `End Set` で終了します。</span><span class="sxs-lookup"><span data-stu-id="dc33f-121">If a procedure has no `Return` or `Exit` statements, it concludes with an `End Sub` or `End Function`, `End Get`, or `End Set` statement following the last statement of the procedure body.</span></span> <span data-ttu-id="dc33f-122">`End` ステートメントはただちに呼び出しコードに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="dc33f-122">The `End` statement returns control immediately to the calling code.</span></span> <span data-ttu-id="dc33f-123">`End` ステートメントは、プロシージャ内に 1 つだけ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-123">You can have only one `End` statement in a procedure.</span></span>  
  
## <a name="parameters-and-arguments"></a><span data-ttu-id="dc33f-124">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="dc33f-124">Parameters and Arguments</span></span>  

 <span data-ttu-id="dc33f-125">プロシージャは、ほとんどの場合、呼び出すたびにデータごとに動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc33f-125">In most cases, a procedure needs to operate on different data each time you call it.</span></span> <span data-ttu-id="dc33f-126">この情報は、プロシージャ コールの一部としてプロシージャに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-126">You can pass this information to the procedure as part of the procedure call.</span></span> <span data-ttu-id="dc33f-127">プロシージャは、*パラメーター* を 0 個、またはそれ以上でも定義することができ、それぞれが渡す必要がある値を表しています。</span><span class="sxs-lookup"><span data-stu-id="dc33f-127">The procedure defines zero or more *parameters*, each of which represents a value it expects you to pass to it.</span></span> <span data-ttu-id="dc33f-128">プロシージャ定義の各パラメーターに相当するのが、プロシージャ コールの *引数* です。</span><span class="sxs-lookup"><span data-stu-id="dc33f-128">Corresponding to each parameter in the procedure definition is an *argument* in the procedure call.</span></span> <span data-ttu-id="dc33f-129">引数は、指定したプロシージャ コールの対応するパラメーターに渡される値を表しています。</span><span class="sxs-lookup"><span data-stu-id="dc33f-129">An argument represents the value you pass to the corresponding parameter in a given procedure call.</span></span>  
  
## <a name="types-of-procedures"></a><span data-ttu-id="dc33f-130">プロシージャの種類</span><span class="sxs-lookup"><span data-stu-id="dc33f-130">Types of Procedures</span></span>  

 <span data-ttu-id="dc33f-131">Visual Basic では、次のような種類のプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc33f-131">Visual Basic uses several types of procedures:</span></span>  
  
- <span data-ttu-id="dc33f-132">[Sub プロシージャ](./sub-procedures.md)はアクションを実行しますが、呼び出しコードに値を返しません。</span><span class="sxs-lookup"><span data-stu-id="dc33f-132">[Sub Procedures](./sub-procedures.md) perform actions but do not return a value to the calling code.</span></span>  
  
- <span data-ttu-id="dc33f-133">イベント処理プロシージャは、ユーザーの操作またはプログラムの起動によって発生したイベントに応答して実行される `Sub` プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="dc33f-133">Event-handling procedures are `Sub` procedures that execute in response to an event raised by user action or by an occurrence in a program.</span></span>  
  
- <span data-ttu-id="dc33f-134">[Function プロシージャ](./function-procedures.md)は、呼び出しコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="dc33f-134">[Function Procedures](./function-procedures.md) return a value to the calling code.</span></span> <span data-ttu-id="dc33f-135">返す前に他の操作を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-135">They can perform other actions before returning.</span></span>

    <span data-ttu-id="dc33f-136">C# で書かれた一部の関数は、*参照戻り値* を返します。</span><span class="sxs-lookup"><span data-stu-id="dc33f-136">Some functions written in C# return a *reference return value*.</span></span> <span data-ttu-id="dc33f-137">関数の呼び出し元は、戻り値を変更することができ、この変更は呼び出されたオブジェクトの状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-137">Function callers can modify the return value, and this modification is reflected in the state of the called object.</span></span> <span data-ttu-id="dc33f-138">Visual Basic は参照によって値を返すことはできませんが、Visual Basic 2017 から、Visual Basic のコードで参照戻り値を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="dc33f-138">Starting with Visual Basic 2017, Visual Basic code can consume reference return values, although it cannot return a value by reference.</span></span> <span data-ttu-id="dc33f-139">詳細については、[参照戻り値](ref-return-values.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc33f-139">For more information, see [Reference return values](ref-return-values.md).</span></span>
  
- <span data-ttu-id="dc33f-140">[プロパティ プロシージャ](./property-procedures.md)は、オブジェクトまたはモジュールのプロパティの値を返し、割り当てます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-140">[Property Procedures](./property-procedures.md) return and assign values of properties on objects or modules.</span></span>  
  
- <span data-ttu-id="dc33f-141">[演算子プロシージャ](./operator-procedures.md)は、オペランドの一方または両方が新しく定義されたクラスまたは構造体である場合に、標準の演算子の動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="dc33f-141">[Operator Procedures](./operator-procedures.md) define the behavior of a standard operator when one or both of the operands is a newly-defined class or structure.</span></span>  
  
- <span data-ttu-id="dc33f-142">[Visual Basic におけるジェネリック プロシージャ](../data-types/generic-procedures.md)は、標準のパラメーターだけでなく 1 つまたは複数の *型パラメーター* も定義するため、呼び出しコードが呼び出しのたびに特定のデータ型を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-142">[Generic Procedures in Visual Basic](../data-types/generic-procedures.md) define one or more *type parameters* in addition to their normal parameters, so the calling code can pass specific data types each time it makes a call.</span></span>  
  
## <a name="procedures-and-structured-code"></a><span data-ttu-id="dc33f-143">プロシージャと構造化されたコード</span><span class="sxs-lookup"><span data-stu-id="dc33f-143">Procedures and Structured Code</span></span>  

 <span data-ttu-id="dc33f-144">アプリケーションの実行可能コードのすべての行が、`Main`、 `calculate`、`Button1_Click` などの何らかのプロシージャの内部にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc33f-144">Every line of executable code in your application must be inside some procedure, such as `Main`, `calculate`, or `Button1_Click`.</span></span> <span data-ttu-id="dc33f-145">大きなプロシージャを小さなプロシージャに分割すると、アプリケーションが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="dc33f-145">If you subdivide large procedures into smaller ones, your application is more readable.</span></span>  
  
 <span data-ttu-id="dc33f-146">プロシージャは、頻繁に使用する計算、テキストやコントロールの操作、データベースの操作など、繰り返される、または共有されるタスクを実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="dc33f-146">Procedures are useful for performing repeated or shared tasks, such as frequently used calculations, text and control manipulation, and database operations.</span></span> <span data-ttu-id="dc33f-147">プロシージャはコード内のさまざまな場所から呼び出すことができるため、プロシージャをアプリケーションの文書パーツとして使用することができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-147">You can call a procedure from many different places in your code, so you can use procedures as building blocks for your application.</span></span>  
  
 <span data-ttu-id="dc33f-148">プロシージャでコードを構成すると、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="dc33f-148">Structuring your code with procedures gives you the following benefits:</span></span>  
  
- <span data-ttu-id="dc33f-149">プロシージャを使用して、プログラムを個々の論理単位に分割できます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-149">Procedures allow you to break your programs into discrete logical units.</span></span> <span data-ttu-id="dc33f-150">プロシージャを使用せずにプログラム全体をデバッグするよりも、個別の単位の方が簡単にデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-150">You can debug separate units more easily than you can debug an entire program without procedures.</span></span>  
  
- <span data-ttu-id="dc33f-151">1 つのプログラムで使用するために開発したプロシージャを、他のプログラムでも使用できます。多くの場合、プログラムをほとんどまたはまったく変更せずに使用できます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-151">After you develop procedures for use in one program, you can use them in other programs, often with little or no modification.</span></span> <span data-ttu-id="dc33f-152">これにより、コードの重複を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="dc33f-152">This helps you avoid code duplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc33f-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc33f-153">See also</span></span>

- [<span data-ttu-id="dc33f-154">方法: プロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="dc33f-154">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="dc33f-155">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="dc33f-155">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="dc33f-156">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="dc33f-156">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="dc33f-157">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="dc33f-157">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="dc33f-158">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="dc33f-158">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="dc33f-159">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="dc33f-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="dc33f-160">再帰プロシージャ</span><span class="sxs-lookup"><span data-stu-id="dc33f-160">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="dc33f-161">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="dc33f-161">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="dc33f-162">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc33f-162">Generic Procedures in Visual Basic</span></span>](../data-types/generic-procedures.md)
- [<span data-ttu-id="dc33f-163">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="dc33f-163">Objects and Classes</span></span>](../objects-and-classes/index.md)
