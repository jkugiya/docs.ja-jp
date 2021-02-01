---
title: メソッド - C# プログラミング ガイド
description: C# のメソッドは、一連のステートメントが含まれているコード ブロックです。 メソッドを呼び出して引数を指定すると、プログラムによってステートメントが実行されます。
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 879e57cfbce82f1aa77f8810e23d6a61a6ea5bc8
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899452"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="b980c-104">メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b980c-104">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="b980c-105">メソッドは、一連のステートメントが含まれているコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="b980c-105">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="b980c-106">必要なメソッド引数を指定してプログラムからメソッドを呼び出すと、メソッド内のステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-106">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="b980c-107">C# では、実行されるすべての命令がメソッドのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-107">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="b980c-108">`Main` メソッドは、すべての C# アプリケーションのエントリ ポイントです。プログラムが開始されると、このメソッドが共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-108">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="b980c-109">この記事では、名前付きメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b980c-109">This article discusses named methods.</span></span> <span data-ttu-id="b980c-110">匿名関数については、「[匿名関数](../statements-expressions-operators/anonymous-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b980c-110">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="b980c-111">メソッド シグネチャ</span><span class="sxs-lookup"><span data-stu-id="b980c-111">Method signatures</span></span>

<span data-ttu-id="b980c-112">メソッドは、[クラス](../../language-reference/keywords/class.md)、[構造体](../../language-reference/builtin-types/struct.md)、または[インターフェイス](../interfaces/index.md)内で、アクセス レベル (`public` や `private` など)、オプションの修飾子 (`abstract` や `sealed` など)、戻り値、メソッドの名前、およびメソッド パラメーターを指定して宣言されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-112">Methods are declared in a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../interfaces/index.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="b980c-113">これらのまとまりがメソッドのシグネチャとなります。</span><span class="sxs-lookup"><span data-stu-id="b980c-113">These parts together are the signature of the method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b980c-114">メソッドのオーバーロードを可能にするために、メソッドの戻り値の型はメソッドのシグネチャには含まれません。</span><span class="sxs-lookup"><span data-stu-id="b980c-114">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="b980c-115">ただし、デリゲートとそれが指すメソッドの互換性を決定する場合には、メソッドのシグネチャの一部となります。</span><span class="sxs-lookup"><span data-stu-id="b980c-115">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="b980c-116">メソッド パラメーターはかっこで囲み、各パラメーターをコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="b980c-116">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="b980c-117">かっこ内を空にすると、メソッドでパラメーターが不要なことを意味します。</span><span class="sxs-lookup"><span data-stu-id="b980c-117">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="b980c-118">このクラスには次の 4 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b980c-118">This class contains four methods:</span></span>

[!code-csharp[DifferentModifiersOnMethods#1](snippets/methods/Program.cs#1)]

## <a name="method-access"></a><span data-ttu-id="b980c-119">メソッド アクセス</span><span class="sxs-lookup"><span data-stu-id="b980c-119">Method access</span></span>

<span data-ttu-id="b980c-120">オブジェクトでメソッドを呼び出すのは、フィールドにアクセスするのと似ています。</span><span class="sxs-lookup"><span data-stu-id="b980c-120">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="b980c-121">オブジェクト名の後に、ピリオド、メソッド名、かっこを追加します。</span><span class="sxs-lookup"><span data-stu-id="b980c-121">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="b980c-122">引数はかっこの中に記述し、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="b980c-122">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="b980c-123">`Motorcycle` クラスのメソッドの呼び出し例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b980c-123">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[CallingMethods#2](snippets/methods/Program.cs#2)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="b980c-124">メソッドのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="b980c-124">Method parameters vs. arguments</span></span>

<span data-ttu-id="b980c-125">メソッド定義には、必要なパラメーターの名前と型を指定します。</span><span class="sxs-lookup"><span data-stu-id="b980c-125">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="b980c-126">呼び出し元のコードからメソッドを呼び出すときに、各パラメーターに引数と呼ばれる具体的な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b980c-126">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="b980c-127">引数にはパラメーター型との互換性が必要ですが、呼び出し元のコードで引数名を使用する場合、引数名がメソッドで定義されるパラメーター名と同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b980c-127">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="b980c-128">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b980c-128">For example:</span></span>

[!code-csharp[MethodExamples#3](snippets/methods/Program.cs#3)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="b980c-129">参照渡しと値渡し</span><span class="sxs-lookup"><span data-stu-id="b980c-129">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="b980c-130">既定では、[値の型](../../language-reference/builtin-types/value-types.md)のインスタンスがメソッドに渡されるときは、インスタンス自体ではなく、そのコピーが渡されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-130">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="b980c-131">したがって、引数に加えた変更は、呼び出し元のメソッドにある元のインスタンスには影響しません。</span><span class="sxs-lookup"><span data-stu-id="b980c-131">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="b980c-132">値の型インスタンスを参照で渡すには、`ref` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="b980c-132">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="b980c-133">詳細については、「[値型パラメーターの引き渡し](./passing-value-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b980c-133">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="b980c-134">参照型のオブジェクトがメソッドに渡されると、オブジェクトへの参照が渡されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-134">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="b980c-135">つまり、メソッドは、オブジェクト自体ではなく、オブジェクトの場所を示す引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b980c-135">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="b980c-136">この参照を使用してオブジェクトのメンバーを変更した場合は、オブジェクトを値で渡しても、呼び出し元のメソッドの引数に変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-136">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="b980c-137">`class` キーワードを使用して参照型を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b980c-137">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[SampleRefTypeClass#4](snippets/methods/Program.cs#4)]

<span data-ttu-id="b980c-138">この型に基づくオブジェクトをメソッドに渡す場合は、オブジェクトへの参照が渡されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-138">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="b980c-139">次の例では、`SampleRefType` 型のオブジェクトをメソッド `ModifyObject`に渡します。</span><span class="sxs-lookup"><span data-stu-id="b980c-139">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[PassingAReferenceType#5](snippets/methods/Program.cs#5)]

<span data-ttu-id="b980c-140">この例は、基本的に前の例と同様に、引数を値でメソッドに渡しています。</span><span class="sxs-lookup"><span data-stu-id="b980c-140">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="b980c-141">しかし、参照型を使用しているため、結果は異なります。</span><span class="sxs-lookup"><span data-stu-id="b980c-141">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="b980c-142">`ModifyObject` のパラメーター `value` の `obj`フィールドで行われた変更によって、 `value` メソッドの引数 `rt`の `TestRefType` フィールドも変更されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-142">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="b980c-143">`TestRefType` メソッドは出力として 33 を表示します。</span><span class="sxs-lookup"><span data-stu-id="b980c-143">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="b980c-144">参照型を参照渡しまたは値渡しで渡す方法の詳細については、「[参照型パラメーターの引き渡し](./passing-reference-type-parameters.md)」と「[参照型](../../language-reference/keywords/reference-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b980c-144">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="b980c-145">戻り値</span><span class="sxs-lookup"><span data-stu-id="b980c-145">Return values</span></span>

<span data-ttu-id="b980c-146">メソッドは、呼び出し元に値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="b980c-146">Methods can return a value to the caller.</span></span> <span data-ttu-id="b980c-147">戻り値の型 (メソッド名の前に記述されている型) が `void`でない場合、メソッドは、 `return` キーワードを使用して値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="b980c-147">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="b980c-148">`return` キーワードに続いて戻り値の型に一致する値が記述されたステートメントは、その値をメソッドの呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="b980c-148">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="b980c-149">値を呼び出し元に返す方法には、値によって返す方法と、C# 7.0 以降の[参照](ref-returns.md)によって返す方法があります。</span><span class="sxs-lookup"><span data-stu-id="b980c-149">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="b980c-150">値が参照によって呼び出し元に返されるのは、`ref` キーワードがメソッド シグネチャで使用されていて、そのキーワードが各 `return` キーワードの後に続いている場合です。</span><span class="sxs-lookup"><span data-stu-id="b980c-150">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="b980c-151">たとえば、次のメソッド シグネチャと return ステートメントは、メソッドが変数名 `estDistance` を参照によって呼び出し元に返すことを示しています。</span><span class="sxs-lookup"><span data-stu-id="b980c-151">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="b980c-152">また、 `return` キーワードは、メソッドの実行を中止します。</span><span class="sxs-lookup"><span data-stu-id="b980c-152">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="b980c-153">戻り値の型が `void`の場合、値を持たない `return` ステートメントは、メソッドの実行を中止するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b980c-153">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="b980c-154">`return` キーワードを使用しない場合、メソッドは、コード ブロックの最後に到達したときに実行を中止します。</span><span class="sxs-lookup"><span data-stu-id="b980c-154">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="b980c-155">戻り値の型が void 以外のメソッドで値を返すには、 `return` キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b980c-155">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="b980c-156">たとえば、次の 2 つのメソッドは、 `return` キーワードを使用して整数を返します。</span><span class="sxs-lookup"><span data-stu-id="b980c-156">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[SimpleMathClass#6](snippets/methods/Program.cs#6)]

<span data-ttu-id="b980c-157">メソッドから返された値を使用する場合、呼び出し元のメソッド内で同じ型の値を使用している場所では、メソッド呼び出し自体を値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="b980c-157">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="b980c-158">戻り値は、変数に代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="b980c-158">You can also assign the return value to a variable.</span></span> <span data-ttu-id="b980c-159">たとえば、次の 2 つのコードでは、同様の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="b980c-159">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[SquareANumberWithAddTwoNumbersUsingLocalVariable#7](snippets/methods/Program.cs#7)]

[!code-csharp[SquareANumberWithAddTwoNumbersInTheSameLine#8](snippets/methods/Program.cs#8)]

<span data-ttu-id="b980c-160">この場合、ローカル変数 `result`を使用して値を格納する手順はオプションです。</span><span class="sxs-lookup"><span data-stu-id="b980c-160">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="b980c-161">このローカル変数によってコードの読みやすさが向上することがあります。また、引数の元の値をメソッドのスコープ全体で保持する場合に必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b980c-161">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="b980c-162">メソッドから参照によって返された値を使用する場合、値を変更するには、[ref ローカル](ref-returns.md#ref-locals)変数を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b980c-162">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="b980c-163">たとえば、`Planet.GetEstimatedDistance` メソッドが <xref:System.Double> の値を参照によって返す場合は、次のようなコードを使用して、その値を ref ローカル変数として定義できます。</span><span class="sxs-lookup"><span data-stu-id="b980c-163">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="b980c-164">呼び出し元の関数から、配列の内容を変更するメソッド `M` に配列が渡された場合、`M` から多次元配列を返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b980c-164">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="b980c-165">値の適切なスタイルまたは機能フローのために `M` から結果の配列を返すことはできますが、必須ではありません。変更された配列を返す必要がないのは、C# ではすべての参照型が値で渡され、配列参照の値がその配列へのポインターになるためです。</span><span class="sxs-lookup"><span data-stu-id="b980c-165">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="b980c-166">メソッド `M` では、次の例に示すように、配列の内容に対する変更は、配列への参照を含むコードによって監視できます。</span><span class="sxs-lookup"><span data-stu-id="b980c-166">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

<span data-ttu-id="b980c-167">詳細については、「 [return](../../language-reference/keywords/return.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b980c-167">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="b980c-168">非同期メソッド</span><span class="sxs-lookup"><span data-stu-id="b980c-168">Async methods</span></span>

<span data-ttu-id="b980c-169">非同期機能を使用することによって、明示的なコールバックを使用せずに、または複数のメソッドやラムダ式にわたって手動でコードを分割することなく、非同期メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b980c-169">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="b980c-170">メソッドに [async](../../language-reference/keywords/async.md) 修飾子を付けると、そのメソッドで [await](../../language-reference/operators/await.md) 演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b980c-170">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="b980c-171">コントロールが非同期メソッドの await 式に到達すると、コントロールは呼び出し元に戻り、待機中のタスクが完了するまでメソッドの進行状況は中断されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-171">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="b980c-172">タスクが完了すると、メソッドで実行を再開できます。</span><span class="sxs-lookup"><span data-stu-id="b980c-172">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="b980c-173">非同期メソッドは、まだ完了していない待機中の最初のオブジェクトに達するか、または非同期メソッドの最後に達すると、呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="b980c-173">An async method returns to the caller when either it encounters the first awaited object that's not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="b980c-174">非同期メソッドの戻り値の型としては、 <xref:System.Threading.Tasks.Task%601>、 <xref:System.Threading.Tasks.Task>、または void を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b980c-174">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="b980c-175">戻り値の型 void は主として、void の戻り値の型が必要なイベント ハンドラーの定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-175">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="b980c-176">void を返す非同期メソッドは待機できません。void を返すメソッドの呼び出し元は、このメソッドがスローする例外をキャッチできません。</span><span class="sxs-lookup"><span data-stu-id="b980c-176">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="b980c-177">次の例で、 `DelayAsync` は戻り値の型が <xref:System.Threading.Tasks.Task%601>である非同期メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b980c-177">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b980c-178">`DelayAsync` には、整数を返す `return` ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="b980c-178">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="b980c-179">そのため、メソッド宣言 `DelayAsync` では、戻り値の型を `Task<int>`とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b980c-179">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="b980c-180">戻り値の型が `Task<int>`であるため、ステートメント `await` に示すように、 `DoSomethingAsync` 内の `int result = await delayTask`式を評価すると整数が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-180">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="b980c-181">`Main` メソッドは、戻り値の型が <xref:System.Threading.Tasks.Task> の非同期メソッドの例です。</span><span class="sxs-lookup"><span data-stu-id="b980c-181">The `Main` method is an example of an async method that has a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="b980c-182">これは `DoSomethingAsync` メソッドに進みます。1 行で表現されるため、キーワードの `async` と `await` を省略できます。</span><span class="sxs-lookup"><span data-stu-id="b980c-182">It goes to the `DoSomethingAsync` method, and because it is expressed with a single line, it can omit the `async` and `await` keywords.</span></span> <span data-ttu-id="b980c-183">`DoSomethingAsync` が非同期メソッドであるため、 `DoSomethingAsync` を呼び出すタスクは、ステートメント `await DoSomethingAsync();`に示すように待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b980c-183">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span>

:::code language="csharp" source="snippets/classes-and-structs/methods/Program.cs":::

<span data-ttu-id="b980c-184">非同期メソッドで [ref](../../language-reference/keywords/ref.md) パラメーターまたは [out](../../language-reference/keywords/out-parameter-modifier.md) パラメーターを宣言することはできませんが、これらのパラメーターを持つメソッドを呼び出すことはできます。</span><span class="sxs-lookup"><span data-stu-id="b980c-184">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="b980c-185">非同期メソッドの詳細については、「[async および await を使用した非同期プログラミング](../concepts/async/index.md)」と[非同期の戻り値の型](../concepts/async/async-return-types.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b980c-185">For more information about async methods, see [Asynchronous programming with async and await](../concepts/async/index.md) and [Async return types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="b980c-186">式本体の定義</span><span class="sxs-lookup"><span data-stu-id="b980c-186">Expression body definitions</span></span>

<span data-ttu-id="b980c-187">メソッドの定義としては、式の結果を即座に返すか、またはメソッドの本文として 1 つのステートメントを含むものが一般的です。</span><span class="sxs-lookup"><span data-stu-id="b980c-187">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="b980c-188">`=>`を使用してこのようなメソッドを定義するための構文ショートカットがあります。</span><span class="sxs-lookup"><span data-stu-id="b980c-188">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="b980c-189">メソッドが `void` を返すか、非同期メソッドである場合は、メソッドの本文を (ラムダの場合と同様に) ステートメント式にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b980c-189">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="b980c-190">プロパティとインデクサーは読み取り専用にする必要があるため、 `get` アクセサー キーワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b980c-190">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="b980c-191">Iterators</span><span class="sxs-lookup"><span data-stu-id="b980c-191">Iterators</span></span>

<span data-ttu-id="b980c-192">反復子は、リストや配列など、コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="b980c-192">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="b980c-193">反復子は、 [yield return](../../language-reference/keywords/yield.md) ステートメントを使用して、各要素を 1 回に1 つ返します。</span><span class="sxs-lookup"><span data-stu-id="b980c-193">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="b980c-194">[yield return](../../language-reference/keywords/yield.md) ステートメントに達すると、コードの現在の場所が記憶されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-194">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="b980c-195">反復子が次回呼び出されたとき、この場所から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="b980c-195">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="b980c-196">[foreach](../../language-reference/keywords/foreach-in.md) ステートメントを使用して、クライアント コードから反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b980c-196">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="b980c-197">反復子の戻り値の型には、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b980c-197">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="b980c-198">詳細については、「 [反復子](../concepts/iterators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b980c-198">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b980c-199">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="b980c-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b980c-200">関連項目</span><span class="sxs-lookup"><span data-stu-id="b980c-200">See also</span></span>

- [<span data-ttu-id="b980c-201">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b980c-201">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b980c-202">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="b980c-202">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="b980c-203">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="b980c-203">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="b980c-204">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="b980c-204">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="b980c-205">継承</span><span class="sxs-lookup"><span data-stu-id="b980c-205">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="b980c-206">抽象クラスとシール クラス、およびクラス メンバー</span><span class="sxs-lookup"><span data-stu-id="b980c-206">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="b980c-207">params</span><span class="sxs-lookup"><span data-stu-id="b980c-207">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="b980c-208">return</span><span class="sxs-lookup"><span data-stu-id="b980c-208">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="b980c-209">out</span><span class="sxs-lookup"><span data-stu-id="b980c-209">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="b980c-210">ref</span><span class="sxs-lookup"><span data-stu-id="b980c-210">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="b980c-211">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="b980c-211">Passing Parameters</span></span>](passing-parameters.md)
