---
description: '詳細情報: Visual Basic における有効期間'
title: 有効期間
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 7c95358209c61b42862f4e995d02a97dfb6e8487
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471462"
---
# <a name="lifetime-in-visual-basic"></a><span data-ttu-id="50def-103">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="50def-103">Lifetime in Visual Basic</span></span>

<span data-ttu-id="50def-104">宣言された要素の *有効期間* は、それを使用できる期間です。</span><span class="sxs-lookup"><span data-stu-id="50def-104">The *lifetime* of a declared element is the period of time during which it is available for use.</span></span> <span data-ttu-id="50def-105">変数は、有効期間がある唯一の要素です。</span><span class="sxs-lookup"><span data-stu-id="50def-105">Variables are the only elements that have lifetime.</span></span> <span data-ttu-id="50def-106">このため、コンパイラでは、プロシージャのパラメーターと関数の戻り値が変数の特殊なケースとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="50def-106">For this purpose, the compiler treats procedure parameters and function returns as special cases of variables.</span></span> <span data-ttu-id="50def-107">変数の有効期間は、それが値を保持できる期間を表します。</span><span class="sxs-lookup"><span data-stu-id="50def-107">The lifetime of a variable represents the period of time during which it can hold a value.</span></span> <span data-ttu-id="50def-108">その値は有効期間を通じて変更される可能性がありますが、常に何らかの値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="50def-108">Its value can change over its lifetime, but it always holds some value.</span></span>  
  
## <a name="different-lifetimes"></a><span data-ttu-id="50def-109">さまざまな有効期間</span><span class="sxs-lookup"><span data-stu-id="50def-109">Different Lifetimes</span></span>  

 <span data-ttu-id="50def-110">*メンバー変数* (モジュールレベルで、プロシージャの外部で宣言) には、通常、それが宣言されている要素と同じ有効期間があります。</span><span class="sxs-lookup"><span data-stu-id="50def-110">A *member variable* (declared at module level, outside any procedure) typically has the same lifetime as the element in which it is declared.</span></span> <span data-ttu-id="50def-111">クラスまたは構造体に宣言された非共有変数は、それが宣言されているクラスまたは構造体のインスタンスごとに個別のコピーとして存在します。</span><span class="sxs-lookup"><span data-stu-id="50def-111">A nonshared variable declared in a class or structure exists as a separate copy for each instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="50def-112">各変数には、そのインスタンスと同じ有効期間があります。</span><span class="sxs-lookup"><span data-stu-id="50def-112">Each such variable has the same lifetime as its instance.</span></span> <span data-ttu-id="50def-113">ただし、`Shared` 変数の有効期間は 1 つだけであり、アプリケーションが実行中の間ずっと存続します。</span><span class="sxs-lookup"><span data-stu-id="50def-113">However, a `Shared` variable has only a single lifetime, which lasts for the entire time your application is running.</span></span>  
  
 <span data-ttu-id="50def-114">*ローカル変数* (プロシージャ内で宣言) は、それが宣言されているプロシージャが実行されている間のみ存在します。</span><span class="sxs-lookup"><span data-stu-id="50def-114">A *local variable* (declared inside a procedure) exists only while the procedure in which it is declared is running.</span></span> <span data-ttu-id="50def-115">これは、そのプロシージャのパラメーターと関数の戻り値にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="50def-115">This applies also to that procedure's parameters and to any function return.</span></span> <span data-ttu-id="50def-116">ただし、そのプロシージャで、他のプロシージャを呼び出している場合、呼び出されたプロシージャが実行されている間、ローカル変数の値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="50def-116">However, if that procedure calls other procedures, the local variables retain their values while the called procedures are running.</span></span>  
  
## <a name="beginning-of-lifetime"></a><span data-ttu-id="50def-117">有効期間の開始</span><span class="sxs-lookup"><span data-stu-id="50def-117">Beginning of Lifetime</span></span>  

 <span data-ttu-id="50def-118">ローカル変数の有効期間は、それが宣言されているプロシージャの制御が始まったときに開始されます。</span><span class="sxs-lookup"><span data-stu-id="50def-118">A local variable's lifetime begins when control enters the procedure in which it is declared.</span></span> <span data-ttu-id="50def-119">すべてのローカル変数は、プロシージャの実行が開始されるとすぐに、そのデータ型の既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="50def-119">Every local variable is initialized to the default value for its data type as soon as the procedure begins running.</span></span> <span data-ttu-id="50def-120">プロシージャで、初期値を指定した `Dim` ステートメントが検出されると、コードで他の値を既に代入していた場合でも、それらの変数にそれらの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="50def-120">When the procedure encounters a `Dim` statement that specifies initial values, it sets those variables to those values, even if your code had already assigned other values to them.</span></span>  
  
 <span data-ttu-id="50def-121">構造体変数の各メンバーは、個別の変数であるかのように初期化されます。</span><span class="sxs-lookup"><span data-stu-id="50def-121">Each member of a structure variable is initialized as if it were a separate variable.</span></span> <span data-ttu-id="50def-122">同様に、配列変数の各要素は個別に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="50def-122">Similarly, each element of an array variable is initialized individually.</span></span>  
  
 <span data-ttu-id="50def-123">プロシージャ内のブロック内で宣言された変数 (`For` ループなど) は、プロシージャに入ったときに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="50def-123">Variables declared within a block inside a procedure (such as a `For` loop) are initialized on entry to the procedure.</span></span> <span data-ttu-id="50def-124">これらの初期化は、コードでブロックが実行されたかどうかにかかわらず有効になります。</span><span class="sxs-lookup"><span data-stu-id="50def-124">These initializations take effect whether or not your code ever executes the block.</span></span>  
  
## <a name="end-of-lifetime"></a><span data-ttu-id="50def-125">有効期間の終了</span><span class="sxs-lookup"><span data-stu-id="50def-125">End of Lifetime</span></span>  

 <span data-ttu-id="50def-126">プロシージャが終了すると、そのローカル変数の値は保持されず、Visual Basic によってそれらのメモリが解放されます。</span><span class="sxs-lookup"><span data-stu-id="50def-126">When a procedure terminates, the values of its local variables are not preserved, and Visual Basic reclaims their memory.</span></span> <span data-ttu-id="50def-127">次回にプロシージャを呼び出すと、そのすべてのローカル変数が新しく作成され、再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="50def-127">The next time you call the procedure, all its local variables are created afresh and reinitialized.</span></span>  
  
 <span data-ttu-id="50def-128">クラスまたは構造体のインスタンスが終了すると、その非共有変数では、それらのメモリと値が失われます。</span><span class="sxs-lookup"><span data-stu-id="50def-128">When an instance of a class or structure terminates, its nonshared variables lose their memory and their values.</span></span> <span data-ttu-id="50def-129">クラスまたは構造体の新しい各インスタンスで、その非共有変数が作成され、再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="50def-129">Each new instance of the class or structure creates and reinitializes its nonshared variables.</span></span> <span data-ttu-id="50def-130">ただし、`Shared` 変数は、アプリケーションが実行を停止するまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="50def-130">However, `Shared` variables are preserved until your application stops running.</span></span>  
  
## <a name="extension-of-lifetime"></a><span data-ttu-id="50def-131">有効期間の延長</span><span class="sxs-lookup"><span data-stu-id="50def-131">Extension of Lifetime</span></span>  

 <span data-ttu-id="50def-132">`Static` キーワードでローカル変数を宣言する場合、その有効期間は、そのプロシージャの実行時間よりも長くなります。</span><span class="sxs-lookup"><span data-stu-id="50def-132">If you declare a local variable with the `Static` keyword, its lifetime is longer than the execution time of its procedure.</span></span> <span data-ttu-id="50def-133">次の表は、プロシージャの宣言によって、`Static` 変数が存在する期間がどのように決まるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="50def-133">The following table shows how the procedure declaration determines how long a `Static` variable exists.</span></span>  
  
|<span data-ttu-id="50def-134">プロシージャの場所と共有</span><span class="sxs-lookup"><span data-stu-id="50def-134">Procedure location and sharing</span></span>|<span data-ttu-id="50def-135">静的変数の有効期間の開始</span><span class="sxs-lookup"><span data-stu-id="50def-135">Static variable lifetime begins</span></span>|<span data-ttu-id="50def-136">静的変数の有効期間の終了</span><span class="sxs-lookup"><span data-stu-id="50def-136">Static variable lifetime ends</span></span>|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|<span data-ttu-id="50def-137">モジュール内 (既定で共有される)</span><span class="sxs-lookup"><span data-stu-id="50def-137">In a module (shared by default)</span></span>|<span data-ttu-id="50def-138">プロシージャが初めて呼び出されたとき</span><span class="sxs-lookup"><span data-stu-id="50def-138">The first time the procedure is called</span></span>|<span data-ttu-id="50def-139">アプリケーションの実行が停止したとき</span><span class="sxs-lookup"><span data-stu-id="50def-139">When your application stops running</span></span>|  
|<span data-ttu-id="50def-140">クラス内、`Shared` (プロシージャはインスタンス メンバーではない)</span><span class="sxs-lookup"><span data-stu-id="50def-140">In a class, `Shared` (procedure is not an instance member)</span></span>|<span data-ttu-id="50def-141">特定のインスタンスか、またはクラスや構造体名自体で、プロシージャが初めて呼び出されたとき</span><span class="sxs-lookup"><span data-stu-id="50def-141">The first time the procedure is called either on a specific instance or on the class or structure name itself</span></span>|<span data-ttu-id="50def-142">アプリケーションの実行が停止したとき</span><span class="sxs-lookup"><span data-stu-id="50def-142">When your application stops running</span></span>|  
|<span data-ttu-id="50def-143">クラスのインスタンス内、`Shared` ではない (プロシージャはインスタンス メンバーである)</span><span class="sxs-lookup"><span data-stu-id="50def-143">In an instance of a class, not `Shared` (procedure is an instance member)</span></span>|<span data-ttu-id="50def-144">特定のインスタンスでプロシージャが初めて呼び出されたとき</span><span class="sxs-lookup"><span data-stu-id="50def-144">The first time the procedure is called on the specific instance</span></span>|<span data-ttu-id="50def-145">ガベージ コレクション (GC) のためにインスタンスが解放されたとき</span><span class="sxs-lookup"><span data-stu-id="50def-145">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="static-variables-of-the-same-name"></a><span data-ttu-id="50def-146">同じ名前の静的変数</span><span class="sxs-lookup"><span data-stu-id="50def-146">Static Variables of the Same Name</span></span>  

 <span data-ttu-id="50def-147">複数のプロシージャで、同じ名前の静的変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="50def-147">You can declare static variables with the same name in more than one procedure.</span></span> <span data-ttu-id="50def-148">この場合、Visual Basic コンパイラでは、このような各変数が個別の要素と見なされます。</span><span class="sxs-lookup"><span data-stu-id="50def-148">If you do this, the Visual Basic compiler considers each such variable to be a separate element.</span></span> <span data-ttu-id="50def-149">これらの変数のいずれかを初期化しても、他の値には影響しません。</span><span class="sxs-lookup"><span data-stu-id="50def-149">The initialization of one of these variables does not affect the values of the others.</span></span> <span data-ttu-id="50def-150">一連のオーバーロードでプロシージャを定義し、各オーバーロードで同じ名前の静的変数を宣言する場合も同じことが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="50def-150">The same applies if you define a procedure with a set of overloads and declare a static variable with the same name in each overload.</span></span>  
  
## <a name="containing-elements-for-static-variables"></a><span data-ttu-id="50def-151">静的変数の含んでいる要素</span><span class="sxs-lookup"><span data-stu-id="50def-151">Containing Elements for Static Variables</span></span>  

 <span data-ttu-id="50def-152">静的ローカル変数は、クラス内、つまりそのクラスのプロシージャ内で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="50def-152">You can declare a static local variable within a class, that is, inside a procedure in that class.</span></span> <span data-ttu-id="50def-153">ただし、静的ローカル変数は、構造体内で、構造体のメンバーとして、またはその構造内のプロシージャのローカル変数として宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="50def-153">However, you cannot declare a static local variable within a structure, either as a structure member or as a local variable of a procedure within that structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50def-154">例</span><span class="sxs-lookup"><span data-stu-id="50def-154">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="50def-155">説明</span><span class="sxs-lookup"><span data-stu-id="50def-155">Description</span></span>  

 <span data-ttu-id="50def-156">次の例では、[Static](../../../language-reference/modifiers/static.md) キーワードで変数を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="50def-156">The following example declares a variable with the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span> <span data-ttu-id="50def-157">([Dim ステートメント](../../../language-reference/statements/dim-statement.md)で `Static` などの修飾子を使用している場合は、`Dim` キーワードが不要です。)</span><span class="sxs-lookup"><span data-stu-id="50def-157">(Note that you do not need the `Dim` keyword when the [Dim Statement](../../../language-reference/statements/dim-statement.md) uses a modifier such as `Static`.)</span></span>  
  
### <a name="code"></a><span data-ttu-id="50def-158">コード</span><span class="sxs-lookup"><span data-stu-id="50def-158">Code</span></span>  

 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a><span data-ttu-id="50def-159">コメント</span><span class="sxs-lookup"><span data-stu-id="50def-159">Comments</span></span>  

 <span data-ttu-id="50def-160">前の例では、プロシージャ `runningTotal` が呼び出し元のコードに戻った後も、変数 `applesSold` が存在し続けます。</span><span class="sxs-lookup"><span data-stu-id="50def-160">In the preceding example, the variable `applesSold` continues to exist after the procedure `runningTotal` returns to the calling code.</span></span> <span data-ttu-id="50def-161">次回に `runningTotal` が呼び出されたときに、`applesSold` には以前に計算された値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="50def-161">The next time `runningTotal` is called, `applesSold` retains its previously calculated value.</span></span>  
  
 <span data-ttu-id="50def-162">`Static` を使用せずに `applesSold` を宣言している場合、以前に累積された値は `runningTotal` の呼び出し間で保持されません。</span><span class="sxs-lookup"><span data-stu-id="50def-162">If `applesSold` had been declared without using `Static`, the previous accumulated values would not be preserved across calls to `runningTotal`.</span></span> <span data-ttu-id="50def-163">次回に `runningTotal` が呼び出されたときに、`applesSold` が再作成されて、0 に初期化され、`runningTotal` では、単にそれが呼び出されたときと同じ値が返されます。</span><span class="sxs-lookup"><span data-stu-id="50def-163">The next time `runningTotal` was called, `applesSold` would have been recreated and initialized to 0, and `runningTotal` would have simply returned the same value with which it was called.</span></span>  
  
### <a name="compile-the-code"></a><span data-ttu-id="50def-164">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="50def-164">Compile the code</span></span>  

 <span data-ttu-id="50def-165">静的ローカル変数の値は、その宣言の一部として初期化できます。</span><span class="sxs-lookup"><span data-stu-id="50def-165">You can initialize the value of a static local variable as part of its declaration.</span></span> <span data-ttu-id="50def-166">配列を `Static` として宣言する場合は、その順位 (次元の数)、各次元の長さ、および個々の要素の値を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="50def-166">If you declare an array to be `Static`, you can initialize its rank (number of dimensions), the length of each dimension, and the values of the individual elements.</span></span>  
  
### <a name="security"></a><span data-ttu-id="50def-167">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="50def-167">Security</span></span>  

 <span data-ttu-id="50def-168">前の例では、モジュール レベルで `applesSold` を宣言することで、同じ有効期間を生成できます。</span><span class="sxs-lookup"><span data-stu-id="50def-168">In the preceding example, you can produce the same lifetime by declaring `applesSold` at module level.</span></span> <span data-ttu-id="50def-169">ただし、このように変数のスコープを変更した場合、プロシージャでそれに排他的にアクセスしなくなります。</span><span class="sxs-lookup"><span data-stu-id="50def-169">If you changed the scope of a variable this way, however, the procedure would no longer have exclusive access to it.</span></span> <span data-ttu-id="50def-170">他のプロシージャによって `applesSold` にアクセスしてその値が変更される可能性があるため、累計は信頼できず、コードの保守が困難になることがあります。</span><span class="sxs-lookup"><span data-stu-id="50def-170">Because other procedures could access `applesSold` and change its value, the running total could be unreliable and the code could be more difficult to maintain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50def-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="50def-171">See also</span></span>

- [<span data-ttu-id="50def-172">Shared</span><span class="sxs-lookup"><span data-stu-id="50def-172">Shared</span></span>](../../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="50def-173">Nothing</span><span class="sxs-lookup"><span data-stu-id="50def-173">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="50def-174">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="50def-174">Declared Element Names</span></span>](declared-element-names.md)
- [<span data-ttu-id="50def-175">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="50def-175">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="50def-176">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="50def-176">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="50def-177">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="50def-177">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="50def-178">変数</span><span class="sxs-lookup"><span data-stu-id="50def-178">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="50def-179">変数宣言</span><span class="sxs-lookup"><span data-stu-id="50def-179">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="50def-180">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="50def-180">Troubleshooting Data Types</span></span>](../data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="50def-181">Static</span><span class="sxs-lookup"><span data-stu-id="50def-181">Static</span></span>](../../../language-reference/modifiers/static.md)
