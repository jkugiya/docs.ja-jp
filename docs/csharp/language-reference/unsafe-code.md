---
title: アンセーフ コード、データへのポインター、および関数ポインター
description: アンセーフ コード、ポインター、および関数ポインターについて説明します。 C# では、これらの機能を使用してメモリまたは関数ポインターを直接操作するために、unsafe コンテキストを宣言する必要があります。
ms.date: 04/01/2021
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 9c55fc48b5805ba38dcf289cb5e03626cf3e96ec
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498579"
---
# <a name="unsafe-code-and-pointer-types"></a><span data-ttu-id="2034a-104">アンセーフ コードとポインター型</span><span class="sxs-lookup"><span data-stu-id="2034a-104">Unsafe code and pointer types</span></span>

<span data-ttu-id="2034a-105">記述する C# コードのほとんどは、"検証可能なセーフ コード" です。</span><span class="sxs-lookup"><span data-stu-id="2034a-105">Most of the C# code you write is "verifiably safe code."</span></span> <span data-ttu-id="2034a-106">"*検証可能なセーフ コード*" は、コードが安全であることを .NET ツールが検証できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2034a-106">*Verifiably safe code* means .NET tools can verify that the code is safe.</span></span> <span data-ttu-id="2034a-107">一般に、セーフ コードはポインターを使用してメモリに直接アクセスしません。</span><span class="sxs-lookup"><span data-stu-id="2034a-107">In general, safe code doesn't directly access memory using pointers.</span></span> <span data-ttu-id="2034a-108">また、生のメモリも割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="2034a-108">It also doesn't allocate raw memory.</span></span> <span data-ttu-id="2034a-109">代わりに、マネージド オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2034a-109">It creates managed objects instead.</span></span>

<span data-ttu-id="2034a-110">C# では、"*検証不可能*" なコードを記述できる [`unsafe`](keywords/unsafe.md) コンテキストがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2034a-110">C# supports an [`unsafe`](keywords/unsafe.md) context, in which you may write *unverifiable* code.</span></span> <span data-ttu-id="2034a-111">`unsafe` コンテキストでは、コードがポインターの使用、メモリ ブロックの割り当てと解放、関数ポインターを使用したメソッドの呼び出しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-111">In an `unsafe` context, code may use pointers, allocate and free blocks of memory, and call methods using function pointers.</span></span> <span data-ttu-id="2034a-112">C# のアンセーフ コードは、必ずしも危険ではありません。ただ、安全性を確認できないコードであるというだけです。</span><span class="sxs-lookup"><span data-stu-id="2034a-112">Unsafe code in C# isn't necessarily dangerous; it's just code whose safety cannot be verified.</span></span>

<span data-ttu-id="2034a-113">アンセーフ コードには次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-113">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="2034a-114">メソッド、型、およびコード ブロックをアンセーフとして定義できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-114">Methods, types, and code blocks can be defined as unsafe.</span></span>
- <span data-ttu-id="2034a-115">アンセーフ コードでアプリケーションのパフォーマンスが向上することがあります。これは、配列のバインド チェックが削除されるためです。</span><span class="sxs-lookup"><span data-stu-id="2034a-115">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>
- <span data-ttu-id="2034a-116">アンセーフ コードは、ポインターを必要とするネイティブ関数を呼び出すときに必要です。</span><span class="sxs-lookup"><span data-stu-id="2034a-116">Unsafe code is required when you call native functions that require pointers.</span></span>
- <span data-ttu-id="2034a-117">アンセーフ コードを使用すると、セキュリティと安定性の面でリスクが生じます。</span><span class="sxs-lookup"><span data-stu-id="2034a-117">Using unsafe code introduces security and stability risks.</span></span>
- <span data-ttu-id="2034a-118">unsafe ブロックを含むコードは、[**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) コンパイラ オプションを使ってコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-118">The code that contains unsafe blocks must be compiled with the [**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) compiler option.</span></span>

## <a name="pointer-types"></a><span data-ttu-id="2034a-119">ポインター型</span><span class="sxs-lookup"><span data-stu-id="2034a-119">Pointer types</span></span>

<span data-ttu-id="2034a-120">unsafe コンテキストの型には、値の型に加えてポインター型、または参照型を設定できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-120">In an unsafe context, a type may be a pointer type, in addition to a value type, or a reference type.</span></span> <span data-ttu-id="2034a-121">ポインター型の宣言は、次のいずれかの形式になります。</span><span class="sxs-lookup"><span data-stu-id="2034a-121">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="2034a-122">ポインター型の `*` の前に指定された型は、**参照型** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2034a-122">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="2034a-123">参照型にできるのは[アンマネージド型](builtin-types/unmanaged-types.md)だけです。</span><span class="sxs-lookup"><span data-stu-id="2034a-123">Only an [unmanaged type](builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="2034a-124">ポインター型は [object](builtin-types/reference-types.md) を継承せず、ポインター型と `object` の間で変換を行う方法はありません。</span><span class="sxs-lookup"><span data-stu-id="2034a-124">Pointer types don't inherit from [object](builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="2034a-125">また、ボックス化とボックス化解除もポインターをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="2034a-125">Also, boxing and unboxing don't support pointers.</span></span> <span data-ttu-id="2034a-126">ただし、異なるポインター型の間で変換したり、ポインター型と整数型の間で変換したりすることはできます。</span><span class="sxs-lookup"><span data-stu-id="2034a-126">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="2034a-127">同じ宣言で複数のポインターを宣言する場合、アスタリスク (`*`) は基底の型のみと一緒に記述します。</span><span class="sxs-lookup"><span data-stu-id="2034a-127">When you declare multiple pointers in the same declaration, you write the asterisk (`*`) together with the underlying type only.</span></span> <span data-ttu-id="2034a-128">各ポインター名のプレフィックスとしては使用されません。</span><span class="sxs-lookup"><span data-stu-id="2034a-128">It isn't used as a prefix to each pointer name.</span></span> <span data-ttu-id="2034a-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2034a-129">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="2034a-130">オブジェクト参照は、それを指すポインターがあってもガベージ コレクションされる可能性があるため、ポインターによって参照や、参照を含む [struct](builtin-types/struct.md) を指すことはできません。</span><span class="sxs-lookup"><span data-stu-id="2034a-130">A pointer can't point to a reference or to a [struct](builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="2034a-131">ガベージ コレクターは、オブジェクトを指すポインター型があるかどうかを追跡しません。</span><span class="sxs-lookup"><span data-stu-id="2034a-131">The garbage collector doesn't keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="2034a-132">`MyType*` 型のポインター変数の値は、`MyType` 型の変数のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="2034a-132">The value of the pointer variable of type `MyType*` is the address of a variable of type `MyType`.</span></span> <span data-ttu-id="2034a-133">ポインター型の宣言の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2034a-133">The following are examples of pointer type declarations:</span></span>

- <span data-ttu-id="2034a-134">`int* p`: `p` は、整数へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="2034a-134">`int* p`: `p` is a pointer to an integer.</span></span>
- <span data-ttu-id="2034a-135">`int** p`: `p` は、整数へのポインターのポインターです。</span><span class="sxs-lookup"><span data-stu-id="2034a-135">`int** p`: `p` is a pointer to a pointer to an integer.</span></span>
- <span data-ttu-id="2034a-136">`int*[] p`: `p` は、整数へのポインターの 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="2034a-136">`int*[] p`: `p` is a single-dimensional array of pointers to integers.</span></span>
- <span data-ttu-id="2034a-137">`char* p`: `p` は、char へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="2034a-137">`char* p`: `p` is a pointer to a char.</span></span>
- <span data-ttu-id="2034a-138">`void* p`: `p` は、未知の型へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="2034a-138">`void* p`: `p` is a pointer to an unknown type.</span></span>

<span data-ttu-id="2034a-139">ポインター間接参照演算子 `*` を使用すると、ポインター変数が指す位置にあるコンテンツにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2034a-139">The pointer indirection operator `*` can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="2034a-140">たとえば、次のような宣言があるとします。</span><span class="sxs-lookup"><span data-stu-id="2034a-140">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="2034a-141">この例の式 `*myVariable` は、`int` に含まれているアドレスの位置にある `myVariable` 変数を示しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-141">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="2034a-142">[`fixed` ステートメント](keywords/fixed-statement.md)の記事に、いくつかのポインターの例があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-142">There are several examples of pointers in the articles on the [`fixed` statement](keywords/fixed-statement.md).</span></span> <span data-ttu-id="2034a-143">次の例は、`unsafe` キーワードと `fixed` ステートメントの使用例と、内部ポインターのインクリメント方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-143">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="2034a-144">このコードは、コンソール アプリケーションの Main 関数に貼り付けて実行することができます</span><span class="sxs-lookup"><span data-stu-id="2034a-144">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="2034a-145">これらの例は、[**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) コンパイラ オプションを設定してコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-145">These examples must be compiled with the [**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) compiler option set.</span></span>

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="5":::

<span data-ttu-id="2034a-146">間接参照演算子は、`void*` 型のポインターに適用できません。</span><span class="sxs-lookup"><span data-stu-id="2034a-146">You can't apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="2034a-147">ただし、void ポインターと他のポインター型はキャストを使用して相互に変換できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-147">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="2034a-148">ポインターは、`null` にできます。</span><span class="sxs-lookup"><span data-stu-id="2034a-148">A pointer can be `null`.</span></span> <span data-ttu-id="2034a-149">null ポインターに間接演算子を適用すると、実装で定義されている動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="2034a-149">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="2034a-150">ポインターをメソッド間で引き渡すと、未定義の動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-150">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="2034a-151">たとえば、`in`、`out` または `ref` パラメーターを介してポインターをローカル変数に返したり、関数の結果として返したりするメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="2034a-151">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="2034a-152">ポインターが固定ブロックに設定されていた場合は、そのポインターが指す変数が既に固定されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-152">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="2034a-153">次の表は、unsafe コンテキストでポインターに使用できる演算子とステートメントの一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-153">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="2034a-154">演算子/ステートメント</span><span class="sxs-lookup"><span data-stu-id="2034a-154">Operator/Statement</span></span>|<span data-ttu-id="2034a-155">使用</span><span class="sxs-lookup"><span data-stu-id="2034a-155">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="2034a-156">ポインターの間接参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="2034a-156">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="2034a-157">ポインター経由で構造体のメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2034a-157">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="2034a-158">ポインターにインデックスを付けます。</span><span class="sxs-lookup"><span data-stu-id="2034a-158">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="2034a-159">変数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2034a-159">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="2034a-160">`++` および `--`</span><span class="sxs-lookup"><span data-stu-id="2034a-160">`++` and `--`</span></span>|<span data-ttu-id="2034a-161">ポインターをインクリメントおよびデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="2034a-161">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="2034a-162">`+` および `-`</span><span class="sxs-lookup"><span data-stu-id="2034a-162">`+` and `-`</span></span>|<span data-ttu-id="2034a-163">ポインター演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="2034a-163">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="2034a-164">`==`、`!=`、`<`、`>`、`<=`、`>=`</span><span class="sxs-lookup"><span data-stu-id="2034a-164">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="2034a-165">ポインターを比較します。</span><span class="sxs-lookup"><span data-stu-id="2034a-165">Compares pointers.</span></span>|
|[`stackalloc`](operators/stackalloc.md)|<span data-ttu-id="2034a-166">スタックにメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2034a-166">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="2034a-167">`fixed` ステートメント</span><span class="sxs-lookup"><span data-stu-id="2034a-167">`fixed` statement</span></span>](keywords/fixed-statement.md)|<span data-ttu-id="2034a-168">変数を一時的に固定して、そのアドレスを取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2034a-168">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="2034a-169">ポインター関連の演算子について詳しくは、「[ポインターに関連する演算子](operators/pointer-related-operators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2034a-169">For more information about pointer-related operators, see [Pointer-related operators](operators/pointer-related-operators.md).</span></span>

<span data-ttu-id="2034a-170">どのポインター型も、暗黙的に `void*` 型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-170">Any pointer type can be implicitly converted to a `void*` type.</span></span> <span data-ttu-id="2034a-171">どのポインター型にも、値 `null` を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-171">Any pointer type can be assigned the value `null`.</span></span> <span data-ttu-id="2034a-172">どのポインター型も、キャスト式を使用して、他のポインター型に明示的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-172">Any pointer type can be explicitly converted to any other pointer type using a cast expression.</span></span> <span data-ttu-id="2034a-173">また、任意の整数型をポインター型に、または任意のポインター型を整数型に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="2034a-173">You can also convert any integral type to a pointer type, or any pointer type to an integral type.</span></span> <span data-ttu-id="2034a-174">これらの変換には、明示的なキャストが必要です。</span><span class="sxs-lookup"><span data-stu-id="2034a-174">These conversions require an explicit cast.</span></span>

<span data-ttu-id="2034a-175">次の例では、`int*` を `byte*` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-175">The following example converts an `int*` to a `byte*`.</span></span> <span data-ttu-id="2034a-176">ポインターは、変数の最下位バイト アドレスを指すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2034a-176">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="2034a-177">`int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-177">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>

:::code language="csharp" source="snippets/unsafe-code/Conversions.cs" ID="Conversion":::

## <a name="fixed-size-buffers"></a><span data-ttu-id="2034a-178">固定サイズ バッファー</span><span class="sxs-lookup"><span data-stu-id="2034a-178">Fixed-size buffers</span></span>

<span data-ttu-id="2034a-179">C# では、[fixed](keywords/fixed-statement.md) ステートメントを使って、データの構造体に固定サイズの配列を持ったバッファーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-179">In C#, you can use the [fixed](keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="2034a-180">固定サイズのバッファーは、他の言語またはプラットフォームのデータ ソースと相互運用するメソッドを作成するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="2034a-180">Fixed size buffers are useful when you write methods that interoperate with data sources from other languages or platforms.</span></span> <span data-ttu-id="2034a-181">この固定配列には、標準的な構造体メンバーで許容されている属性または修飾子であれば、何でも適用することができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-181">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="2034a-182">ただし配列の型は `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float`、`double` のいずれかに該当する必要があり、それが唯一の制限となります。</span><span class="sxs-lookup"><span data-stu-id="2034a-182">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

<span data-ttu-id="2034a-183">セーフ コードでは、配列を含む C# 構造体に配列要素が含まれません。</span><span class="sxs-lookup"><span data-stu-id="2034a-183">In safe code, a C# struct that contains an array doesn't contain the array elements.</span></span> <span data-ttu-id="2034a-184">代わりに、構造体には、要素の参照が格納されます。</span><span class="sxs-lookup"><span data-stu-id="2034a-184">The struct contains a reference to the elements instead.</span></span> <span data-ttu-id="2034a-185">[unsafe](keywords/unsafe.md) のコード ブロックで使われている [struct](builtin-types/struct.md) に、固定サイズの配列を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-185">You can embed an array of fixed size in a [struct](builtin-types/struct.md) when it's used in an [unsafe](keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="2034a-186">`pathName` が参照であるため、次の `struct` のサイズは配列内の要素の数に依存しません。</span><span class="sxs-lookup"><span data-stu-id="2034a-186">The size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="6":::

<span data-ttu-id="2034a-187">アンセーフ コードでは、`struct` に埋め込み配列を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-187">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="2034a-188">以下の例の `fixedBuffer` 配列は固定サイズです。</span><span class="sxs-lookup"><span data-stu-id="2034a-188">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="2034a-189">`fixed` ステートメントを使用して、先頭要素へのポインターを確立します。</span><span class="sxs-lookup"><span data-stu-id="2034a-189">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="2034a-190">このポインターを使用して配列の要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2034a-190">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="2034a-191">`fixed` ステートメントによって、`fixedBuffer` インスタンス フィールドがメモリ内の特定の位置に固定されます。</span><span class="sxs-lookup"><span data-stu-id="2034a-191">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="7":::

<span data-ttu-id="2034a-192">要素数 128 の `char` 配列のサイズは 256 バイトです。</span><span class="sxs-lookup"><span data-stu-id="2034a-192">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="2034a-193">固定サイズの [char](builtin-types/char.md) バッファーは、エンコーディングに関係なく常に、1 文字あたり 2 バイトを消費します。</span><span class="sxs-lookup"><span data-stu-id="2034a-193">Fixed size [char](builtin-types/char.md) buffers always take 2 bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="2034a-194">この配列サイズは、char のバッファーが、`CharSet = CharSet.Auto` または `CharSet = CharSet.Ansi` で API メソッドや構造体にマーシャリングされたときにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="2034a-194">This array size is the same even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="2034a-195">詳細については、「<xref:System.Runtime.InteropServices.CharSet>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2034a-195">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="2034a-196">上記の例は、固定せずに `fixed` フィールドにアクセスする方法を示しています。この方法は C# 7.3 以降から使用できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-196">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="2034a-197">一般的な固定サイズの配列としては、他にも [bool](builtin-types/bool.md) 配列があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-197">Another common fixed-size array is the [bool](builtin-types/bool.md) array.</span></span> <span data-ttu-id="2034a-198">`bool` 配列内の要素のサイズは常に 1 バイトです。</span><span class="sxs-lookup"><span data-stu-id="2034a-198">The elements in a `bool` array are always 1 byte in size.</span></span> <span data-ttu-id="2034a-199">`bool` 配列は、ビット配列やバッファーの作成には適していません。</span><span class="sxs-lookup"><span data-stu-id="2034a-199">`bool` arrays aren't appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="2034a-200">固定サイズ バッファーは <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>を使用してコンパイルされます。これにより、オーバーフローする可能性があるアンマネージド配列が型に含まれていることが共通言語ランタイム (CLR) に指示されます。</span><span class="sxs-lookup"><span data-stu-id="2034a-200">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="2034a-201">[Stackalloc](operators/stackalloc.md) を使用して割り当てられたメモリによって、CLR のバッファー オーバーラン検出機能も自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="2034a-201">Memory allocated using [stackalloc](operators/stackalloc.md) also automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="2034a-202">前の例では、`unsafe struct` に固定サイズ バッファーがどのようにして存在できるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-202">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="2034a-203">`Buffer` 用にコンパイラで生成された C# は、次のように属性が付けられます。</span><span class="sxs-lookup"><span data-stu-id="2034a-203">The compiler-generated C# for `Buffer` is attributed as follows:</span></span>

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

<span data-ttu-id="2034a-204">固定サイズ バッファーは、次の点で通常の配列とは異なります。</span><span class="sxs-lookup"><span data-stu-id="2034a-204">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="2034a-205">`unsafe` のコンテキストでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-205">May only be used in an `unsafe` context.</span></span>
- <span data-ttu-id="2034a-206">構造体のインスタンス フィールドのみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-206">May only be instance fields of structs.</span></span>
- <span data-ttu-id="2034a-207">これらは常にベクター (1 次元配列) です。</span><span class="sxs-lookup"><span data-stu-id="2034a-207">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="2034a-208">宣言には、`fixed char id[8]` などの長さを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-208">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="2034a-209">`fixed char id[]` は使用できません。</span><span class="sxs-lookup"><span data-stu-id="2034a-209">You can't use `fixed char id[]`.</span></span>

## <a name="how-to-use-pointers-to-copy-an-array-of-bytes"></a><span data-ttu-id="2034a-210">ポインターを使用してバイトの配列をコピーする方法</span><span class="sxs-lookup"><span data-stu-id="2034a-210">How to use pointers to copy an array of bytes</span></span>

<span data-ttu-id="2034a-211">次の例では、ポインターを使って 1 つの配列から別の配列にバイトをコピーします。</span><span class="sxs-lookup"><span data-stu-id="2034a-211">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="2034a-212">この例では、[unsafe](keywords/unsafe.md) キーワードを使います。このキーワードは、`Copy` メソッドでのポインターの使用を可能にします。</span><span class="sxs-lookup"><span data-stu-id="2034a-212">This example uses the [unsafe](keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="2034a-213">[fixed](keywords/fixed-statement.md) ステートメントを使って、コピー元とコピー先の配列へのポインターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="2034a-213">The [fixed](keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="2034a-214">`fixed` ステートメントを使って、コピー元配列とコピー先配列のメモリ内での位置を "*固定*" し、ガベージ コレクションによって移動されないようにします。</span><span class="sxs-lookup"><span data-stu-id="2034a-214">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="2034a-215">`fixed` ブロックが完了すると、これらの配列のメモリ ブロックは固定解除されます。</span><span class="sxs-lookup"><span data-stu-id="2034a-215">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="2034a-216">この例の `Copy` メソッドは `unsafe` キーワードを使っているので、[**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) コンパイラ オプションを指定してコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-216">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) compiler option.</span></span>

<span data-ttu-id="2034a-217">この例では、2 番目のアンマネージド ポインターではなくインデックスを使って、両方の配列の要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2034a-217">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="2034a-218">`pSource` と `pTarget` のポインターの宣言を使って配列を固定します。</span><span class="sxs-lookup"><span data-stu-id="2034a-218">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="2034a-219">この機能は、C# 7.3 以降から使用できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-219">This feature is available starting with C# 7.3.</span></span>

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="8":::

## <a name="function-pointers"></a><span data-ttu-id="2034a-220">関数ポインター</span><span class="sxs-lookup"><span data-stu-id="2034a-220">Function pointers</span></span>

<span data-ttu-id="2034a-221">C# には、安全な関数ポインター オブジェクトを定義するための [`delegate`](builtin-types/reference-types.md#the-delegate-type) 型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2034a-221">C# provides [`delegate`](builtin-types/reference-types.md#the-delegate-type) types to define safe function pointer objects.</span></span> <span data-ttu-id="2034a-222">デリゲートを呼び出すには、<xref:System.Delegate?displayProperty=nameWithType> から派生した型をインスタンス化し、その `Invoke` メソッドへの仮想メソッド呼び出しを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="2034a-222">Invoking a delegate involves instantiating a type derived from <xref:System.Delegate?displayProperty=nameWithType> and making a virtual method call to its `Invoke` method.</span></span> <span data-ttu-id="2034a-223">この仮想呼び出しでは、`callvirt` IL 命令が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2034a-223">This virtual call uses the `callvirt` IL instruction.</span></span> <span data-ttu-id="2034a-224">パフォーマンスを重視するコード パスでは、`calli` IL 命令を使用する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="2034a-224">In performance critical code paths, using the `calli` IL instruction is more efficient.</span></span>

<span data-ttu-id="2034a-225">関数ポインターは、`delegate*` 構文を使用して定義できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-225">You can define a function pointer using the `delegate*` syntax.</span></span> <span data-ttu-id="2034a-226">コンパイラは、`delegate` オブジェクトをインスタンス化して `Invoke` を呼び出すのではなく、`calli` 命令を使用して関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2034a-226">The compiler will call the function using the `calli` instruction rather than instantiating a `delegate` object and calling `Invoke`.</span></span> <span data-ttu-id="2034a-227">次のコードでは、`delegate` または `delegate*` を使用する 2 つのメソッドを宣言して、同じ型の 2 つのオブジェクトを結合しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-227">The following code declares two methods that use a `delegate` or a `delegate*` to combine two objects of the same type.</span></span> <span data-ttu-id="2034a-228">最初のメソッドは、<xref:System.Func%603?displayProperty=nameWithType> デリゲート型を使用します。</span><span class="sxs-lookup"><span data-stu-id="2034a-228">The first method uses a <xref:System.Func%603?displayProperty=nameWithType> delegate type.</span></span> <span data-ttu-id="2034a-229">2 番目のメソッドは、同じパラメーターと戻り値の型を持つ `delegate*` 宣言を使用します。</span><span class="sxs-lookup"><span data-stu-id="2034a-229">The second method uses a `delegate*` declaration with the same parameters and return type:</span></span>

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="UseDelegateOrPointer":::

<span data-ttu-id="2034a-230">次のコードは、静的ローカル関数を宣言し、そのローカル関数へのポインターを使用して `UnsafeCombine` メソッドを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-230">The following code shows how you would declare a static local function and invoke the `UnsafeCombine` method using a pointer to that local function:</span></span>

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="InvokeViaFunctionPointer":::

<span data-ttu-id="2034a-231">上記のコードは、関数ポインターとしてアクセスされる関数に対するいくつかの規則を示しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-231">The preceding code illustrates several of the rules on the function accessed as a function pointer:</span></span>

- <span data-ttu-id="2034a-232">関数ポインターは、`unsafe` コンテキスト内でのみ宣言できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-232">Function pointers can only be declared in an `unsafe` context.</span></span>
- <span data-ttu-id="2034a-233">`delegate*` を受け取る (または `delegate*` を返す) メソッドは、`unsafe` コンテキストでのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-233">Methods that take a `delegate*` (or return a `delegate*`) can only be called in an `unsafe` context.</span></span>
- <span data-ttu-id="2034a-234">関数のアドレスを取得する `&` 演算子は、`static` 関数でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-234">The `&` operator to obtain the address of a function is allowed only on `static` functions.</span></span> <span data-ttu-id="2034a-235">(この規則は、メンバー関数とローカル関数の両方に適用されます)。</span><span class="sxs-lookup"><span data-stu-id="2034a-235">(This rule applies to both member functions and local functions).</span></span>

<span data-ttu-id="2034a-236">この構文は、`delegate` 型を宣言し、ポインターを使用する場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="2034a-236">The syntax has parallels with declaring `delegate` types and using pointers.</span></span> <span data-ttu-id="2034a-237">`delegate` の `*` サフィックスは、宣言が "*関数ポインター*" であることを示します。</span><span class="sxs-lookup"><span data-stu-id="2034a-237">The `*` suffix on `delegate` indicates the declaration is a *function pointer*.</span></span> <span data-ttu-id="2034a-238">メソッド グループを関数ポインターに割り当てるときの `&` は演算がメソッドのアドレスを受け取ることを示します。</span><span class="sxs-lookup"><span data-stu-id="2034a-238">The `&` when assigning a method group to a function pointer indicates the operation takes the address of the method.</span></span>

<span data-ttu-id="2034a-239">`delegate*` の呼び出し規則はキーワード `managed` と `unmanaged` を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="2034a-239">You can specify the calling convention for a `delegate*` using the keywords `managed` and `unmanaged`.</span></span> <span data-ttu-id="2034a-240">また、`unmanaged` 関数ポインターにも、呼び出し規則を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2034a-240">In addition, for `unmanaged` function pointers, you can specify the calling convention.</span></span> <span data-ttu-id="2034a-241">次の宣言は、それぞれの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-241">The following declarations show examples of each.</span></span> <span data-ttu-id="2034a-242">最初の宣言では、既定の `managed` の呼び出し規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2034a-242">The first declaration uses the `managed` calling convention, which is the default.</span></span> <span data-ttu-id="2034a-243">次の 3 つでは、`unmanaged` の呼び出し規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2034a-243">The next three use an `unmanaged` calling convention.</span></span> <span data-ttu-id="2034a-244">それぞれ、ECMA 335 呼び出し規則のいずれか (`Cdecl`、`Stdcall`、`Fastcall`、または `Thiscall`) を指定しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-244">Each specifies one of the ECMA 335 calling conventions: `Cdecl`, `Stdcall`, `Fastcall`, or `Thiscall`.</span></span> <span data-ttu-id="2034a-245">最後の宣言では、`unmanaged` の呼び出し規則を使用して、プラットフォームの既定の呼び出し規則を選択するように CLR に指示しています。</span><span class="sxs-lookup"><span data-stu-id="2034a-245">The last declarations uses the `unmanaged` calling convention, instructing the CLR to pick the default calling convention for the platform.</span></span> <span data-ttu-id="2034a-246">CLR は、実行時に呼び出し規則を選択します。</span><span class="sxs-lookup"><span data-stu-id="2034a-246">The CLR will choose the calling convention at run time.</span></span>

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="UnmanagedFunctionPointers":::

<span data-ttu-id="2034a-247">関数ポインターの詳細については、C# 9.0 の[関数ポインター](~/_csharplang/proposals/csharp-9.0/function-pointers.md)に関する提案を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2034a-247">You can learn more about function pointers in the [Function pointer](~/_csharplang/proposals/csharp-9.0/function-pointers.md) proposal for C# 9.0.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2034a-248">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="2034a-248">C# language specification</span></span>

<span data-ttu-id="2034a-249">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の[アンセーフ コード](~/_csharplang/spec/unsafe-code.md)に関する章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2034a-249">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
