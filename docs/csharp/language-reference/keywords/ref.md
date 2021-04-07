---
description: ref キーワード - C# リファレンス
title: ref キーワード - C# リファレンス
ms.date: 03/29/2021
f1_keywords:
- ref_CSharpKeyword
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 3392e560eaf0bac39cf4e9707574fd2bb3d96057
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079441"
---
# <a name="ref-c-reference"></a><span data-ttu-id="26e8f-103">ref (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="26e8f-103">ref (C# Reference)</span></span>

<span data-ttu-id="26e8f-104">`ref` キーワードは、値が参照渡しで渡されることを示します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-104">The `ref` keyword indicates that a value is passed by reference.</span></span> <span data-ttu-id="26e8f-105">このキーワードは、4 つの異なるコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-105">It is used in four different contexts:</span></span>

- <span data-ttu-id="26e8f-106">メソッド シグネチャとメソッドの呼び出しで、参照によってメソッドに引数を渡します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-106">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="26e8f-107">詳細については、「[参照渡しで引数を渡す](#passing-an-argument-by-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-107">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="26e8f-108">メソッド シグネチャで、参照渡しで呼び出し元に値を返します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-108">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="26e8f-109">詳細については、[参照戻り値](#reference-return-values)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-109">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="26e8f-110">メンバーの本文で、参照戻り値が、呼び出し元によって変更される参照としてローカルに格納されることを示します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-110">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="26e8f-111">または、ローカル変数から別の値へのアクセスが参照渡しで行われることを示します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-111">Or to indicate that a local variable accesses another value by reference.</span></span> <span data-ttu-id="26e8f-112">詳細については、「[ref ローカル変数](#ref-locals)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-112">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="26e8f-113">`struct` の宣言で、`ref struct` または `readonly ref struct` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-113">In a `struct` declaration, to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="26e8f-114">詳細については、「[構造体型](../builtin-types/struct.md)」の記事の「[`ref` 構造体](../builtin-types/struct.md#ref-struct)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-114">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="26e8f-115">参照渡しで引数を渡す</span><span class="sxs-lookup"><span data-stu-id="26e8f-115">Passing an argument by reference</span></span>

<span data-ttu-id="26e8f-116">メソッドのパラメーター リストで使用した場合、`ref` キーワードは、引数を値ではなく、参照によって渡すことを示します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-116">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="26e8f-117">`ref` キーワードは、仮パラメーターを引数 (変数にする必要があります) の別名にします。</span><span class="sxs-lookup"><span data-stu-id="26e8f-117">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="26e8f-118">つまり、パラメーターに対するすべての操作は引数に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-118">In other words, any operation on the parameter is made on the argument.</span></span>

<span data-ttu-id="26e8f-119">たとえば、呼び出し元からローカル変数式または配列要素のアクセス式が渡されるとします。</span><span class="sxs-lookup"><span data-stu-id="26e8f-119">For example, suppose the caller passes a local variable expression or an array element access expression.</span></span> <span data-ttu-id="26e8f-120">また、呼び出されるメソッドでは、ref パラメーターが参照するオブジェクトを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-120">The called method can then replace the object to which the ref parameter refers.</span></span> <span data-ttu-id="26e8f-121">その場合は、メソッドから制御が戻ったとき、呼び出し元のローカル変数または配列要素によって参照されるのは、新しいオブジェクトとなります。</span><span class="sxs-lookup"><span data-stu-id="26e8f-121">In that case, the caller's local variable or the array element refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="26e8f-122">参照渡しで渡すという概念と参照型の概念とを混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-122">Don't confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="26e8f-123">2 つの概念は同じではありません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-123">The two concepts are not the same.</span></span> <span data-ttu-id="26e8f-124">メソッドのパラメーターは、値型か参照型かどうかに関係なく、`ref` によって変更できます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-124">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="26e8f-125">参照渡しで渡される場合、値型はボックス化されません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-125">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="26e8f-126">`ref` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方が、次の例に示すように `ref` キーワードを明示的に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26e8f-126">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span> <span data-ttu-id="26e8f-127">(例外として、COM 呼び出しを行う場合は、呼び出し元のメソッドで `ref` を省略できます)。</span><span class="sxs-lookup"><span data-stu-id="26e8f-127">(Except that the calling method can omit `ref` when making a COM call.)</span></span>

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="26e8f-128">`ref` または `in` パラメーターに渡す引数は、渡す前に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26e8f-128">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="26e8f-129">この要件は、引数を渡す前に明示的に初期化する必要がない [out](out-parameter-modifier.md) パラメーターの場合とは異なります。</span><span class="sxs-lookup"><span data-stu-id="26e8f-129">This requirement differs from [out](out-parameter-modifier.md) parameters, whose arguments don't have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="26e8f-130">クラスのメンバーは、`ref`、`in`、または `out` のみが異なるシグネチャを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-130">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="26e8f-131">1 つの型の 2 つのメンバー間の唯一の違いが、1 つには `ref` パラメーターが存在し、もう 1 つには `out` または `in` パラメーターが存在することである場合、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-131">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="26e8f-132">たとえば、次のコードはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-132">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="26e8f-133">ただし、次の例に示すように、1 つのメソッドに `ref`、`in` または `out` パラメーターがあり、もう 1 つには値渡しされるパラメーターがある場合、メソッドをオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-133">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a parameter that is passed by value, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="26e8f-134">非表示やオーバーライドなど、シグネチャの一致が必要な他の状況では、`in`、`ref`、`out` はシグネチャの一部であり、互いに一致しません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-134">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="26e8f-135">プロパティは変数ではありません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-135">Properties are not variables.</span></span> <span data-ttu-id="26e8f-136">それらはメソッドであり、`ref` パラメーターに渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-136">They're methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="26e8f-137">次の種類のメソッドには、`ref`、`in`、`out` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-137">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="26e8f-138">[async](async.md) 修飾子を使用して定義した Async メソッド。</span><span class="sxs-lookup"><span data-stu-id="26e8f-138">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="26e8f-139">[yield return](yield.md) または `yield break` ステートメントを含む Iterator メソッド。</span><span class="sxs-lookup"><span data-stu-id="26e8f-139">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="26e8f-140">[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)には、これらのキーワードの使用に関する制限もあります。</span><span class="sxs-lookup"><span data-stu-id="26e8f-140">[extension methods](../../programming-guide/classes-and-structs/extension-methods.md) also have restrictions on the use of these keywords:</span></span>

- <span data-ttu-id="26e8f-141">拡張メソッドの最初の引数では、`out` キーワードを使用できません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-141">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="26e8f-142">拡張メソッドの最初の引数が構造体ではない場合、または構造体として制約されていないジェネリック型である場合、その引数で `ref` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-142">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="26e8f-143">最初の引数が構造体である場合を除き、`in` キーワードは使用できません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-143">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="26e8f-144">ジェネリック型では、構造体として制約されている場合であっても、`in` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-144">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="26e8f-145">参照渡しで引数を渡す:使用例</span><span class="sxs-lookup"><span data-stu-id="26e8f-145">Passing an argument by reference: An example</span></span>

<span data-ttu-id="26e8f-146">前の例は、参照によって値型を渡す例でした。</span><span class="sxs-lookup"><span data-stu-id="26e8f-146">The previous examples pass value types by reference.</span></span> <span data-ttu-id="26e8f-147">`ref` キーワードを使用して、参照渡しで参照型を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-147">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="26e8f-148">参照型を参照渡しで渡すと、呼び出されたメソッドは、参照パラメーターが呼び出し元で参照するオブジェクトに置換できます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-148">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="26e8f-149">オブジェクトの格納場所は、参照パラメーターの値としてメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-149">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="26e8f-150">パラメーターの格納場所の値を変更する場合は (新しいオブジェクトをポイント)、呼び出し元が参照する格納場所を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-150">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="26e8f-151">次の例では、参照型のインスタンスを `ref` パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-151">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="26e8f-152">参照型を値渡しまたは参照渡しで渡す方法の詳細については、「[参照型パラメーターの引き渡し](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-152">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="26e8f-153">参照戻り値</span><span class="sxs-lookup"><span data-stu-id="26e8f-153">Reference return values</span></span>

<span data-ttu-id="26e8f-154">参照戻り値 (または ref 戻り値) は、メソッドから呼び出し元に参照渡しで返される値です。</span><span class="sxs-lookup"><span data-stu-id="26e8f-154">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="26e8f-155">つまり、呼び出し元はメソッドによって返される値を変更することができ、呼び出し元メソッド内のオブジェクトの状態にその変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-155">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="26e8f-156">参照戻り値は `ref` キーワードを使用して以下に定義されます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-156">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="26e8f-157">メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="26e8f-157">In the method signature.</span></span> <span data-ttu-id="26e8f-158">たとえば、次のメソッド シグネチャは、`GetCurrentPrice` メソッドが参照渡しで <xref:System.Decimal> 値を返すことを示しています。</span><span class="sxs-lookup"><span data-stu-id="26e8f-158">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="26e8f-159">メソッドの `return` ステートメントで返される変数と `return` トークンの間。</span><span class="sxs-lookup"><span data-stu-id="26e8f-159">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="26e8f-160">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-160">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="26e8f-161">呼び出し元がオブジェクトの状態を変更するには、[ref ローカル変数](#ref-locals)として明示的に定義した変数に参照戻り値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26e8f-161">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="26e8f-162">次に、メソッド シグネチャとメソッド本体の両方を示す、より完全な ref 戻り値の例を示します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-162">Here's a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="26e8f-163">呼び出されるメソッドでは、値が参照渡しで値が返されるように戻り値を `ref readonly` として宣言し、返された値を呼び出し元のコードで変更できないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-163">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code can't modify the returned value.</span></span> <span data-ttu-id="26e8f-164">呼び出し元のメソッドでは、ローカルの [ref readonly](#ref-readonly-locals) 変数に値を格納することで、返された値のコピーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-164">The calling method can avoid copying the returned value by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="26e8f-165">例については、「[ref 戻り値と ref ローカル変数の使用例](#a-ref-returns-and-ref-locals-example)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-165">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="26e8f-166">ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="26e8f-166">Ref locals</span></span>

<span data-ttu-id="26e8f-167">ref ローカル変数は、`return ref` を使用して返された値を参照するために使用します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-167">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="26e8f-168">ref ローカル変数は、初期化して ref 戻り値以外の値にすることができません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-168">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="26e8f-169">言い換えると、初期化の右側は参照にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="26e8f-169">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="26e8f-170">ref ローカル変数の値に変更を加えると、参照渡しの値を返すメソッドのオブジェクトの状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-170">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="26e8f-171">次の 2 つの場所で `ref` キーワードを使用して、ref ローカルを定義します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-171">You define a ref local by using the `ref` keyword in two places:</span></span>

- <span data-ttu-id="26e8f-172">変数宣言の前。</span><span class="sxs-lookup"><span data-stu-id="26e8f-172">Before the variable declaration.</span></span>
- <span data-ttu-id="26e8f-173">参照渡しで値を返すメソッドの呼び出しの直前。</span><span class="sxs-lookup"><span data-stu-id="26e8f-173">Immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="26e8f-174">たとえば、次のステートメントは、`GetEstimatedValue` という名前のメソッドによって返される ref ローカル変数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="26e8f-174">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="26e8f-175">同じ方法で、参照渡しの値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-175">You can access a value by reference in the same way.</span></span> <span data-ttu-id="26e8f-176">場合によっては、参照渡しの値へのアクセスによって負荷がかかる可能性があるコピー操作が回避され、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="26e8f-176">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="26e8f-177">たとえば、次のステートメントは、値の参照に使用される ref ローカル値をどのように定義するかを示しています。</span><span class="sxs-lookup"><span data-stu-id="26e8f-177">For example, the following statement shows how to define a ref local variable that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="26e8f-178">どちらの例も、`ref` キーワードは両方の位置で使用する必要があります。そうしないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-178">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="26e8f-179">C# 7.3 以降、`foreach` ステートメントの反復変数を ref ローカルまたは ref readonly ローカル変数にすることができます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-179">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be a ref local or ref readonly local variable.</span></span> <span data-ttu-id="26e8f-180">詳細については、[foreach ステートメント](foreach-in.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-180">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="26e8f-181">また、C# 7.3 以降では、[ref 代入演算子](../operators/assignment-operator.md#ref-assignment-operator)を使用して、ref ローカルまたは ref readonly ローカル変数を再割り当てできます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-181">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="26e8f-182">ref readonly ローカル</span><span class="sxs-lookup"><span data-stu-id="26e8f-182">Ref readonly locals</span></span>

<span data-ttu-id="26e8f-183">ref readonly ローカルは、署名に `ref readonly` が含まれていて `return ref` を使用するメソッドまたはプロパティにより返される値を参照する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-183">A ref readonly local is used to refer to values returned by a method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="26e8f-184">`ref readonly` 変数は `ref` ローカル変数のプロパティと `readonly` 変数の組み合わせです。それに割り当てられたストレージのエイリアスであり、変更できません。</span><span class="sxs-lookup"><span data-stu-id="26e8f-184">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it's an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="26e8f-185">ref 戻り値と ref ローカル変数の使用例</span><span class="sxs-lookup"><span data-stu-id="26e8f-185">A ref returns and ref locals example</span></span>

<span data-ttu-id="26e8f-186">次の例は、`Title` と `Author` という 2 つの <xref:System.String> フィールドを持つ `Book` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="26e8f-186">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="26e8f-187">また、`Book` オブジェクトのプライベート配列を含む `BookCollection` クラスも定義しています。</span><span class="sxs-lookup"><span data-stu-id="26e8f-187">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="26e8f-188">個々のブック オブジェクトは、`GetBookByTitle` メソッドを呼び出すことによって参照渡しで返されます。</span><span class="sxs-lookup"><span data-stu-id="26e8f-188">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="26e8f-189">呼び出し元が `GetBookByTitle` によって返される値を ref ローカル変数として格納する場合、呼び出し元が戻り値に加えた変更が `BookCollection` オブジェクトに反映されます。次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e8f-189">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="26e8f-190">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="26e8f-190">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26e8f-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="26e8f-191">See also</span></span>

- [<span data-ttu-id="26e8f-192">安全で効率的なコードを記述する</span><span class="sxs-lookup"><span data-stu-id="26e8f-192">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="26e8f-193">ref 戻り値と ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="26e8f-193">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="26e8f-194">ref 条件式</span><span class="sxs-lookup"><span data-stu-id="26e8f-194">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="26e8f-195">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="26e8f-195">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="26e8f-196">メソッド パラメーター</span><span class="sxs-lookup"><span data-stu-id="26e8f-196">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="26e8f-197">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="26e8f-197">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="26e8f-198">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="26e8f-198">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="26e8f-199">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="26e8f-199">C# Keywords</span></span>](index.md)
