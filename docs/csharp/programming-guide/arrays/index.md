---
title: 配列 - C# プログラミング ガイド
description: C# の配列データ構造に、同じ型の複数の変数を格納します。 配列を宣言するには、型を指定するか、任意の型を格納する場合は Object を指定します。
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794765"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="fa748-104">配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="fa748-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="fa748-105">配列データ構造体には、同じ型の複数の変数を格納できます。</span><span class="sxs-lookup"><span data-stu-id="fa748-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="fa748-106">配列は、要素の型を指定することで宣言します。</span><span class="sxs-lookup"><span data-stu-id="fa748-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="fa748-107">配列に任意の型の要素を格納する場合は、その型として `object` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fa748-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="fa748-108">C# の統一型システムでは、すべての型 (定義済み、ユーザー定義、参照型、および値の型) が、直接または間接的に <xref:System.Object> を継承します。</span><span class="sxs-lookup"><span data-stu-id="fa748-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="fa748-109">例</span><span class="sxs-lookup"><span data-stu-id="fa748-109">Example</span></span>

<span data-ttu-id="fa748-110">次の例では、1 次元配列、多次元配列、およびジャグ配列を作成しています。</span><span class="sxs-lookup"><span data-stu-id="fa748-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="fa748-111">配列の概要</span><span class="sxs-lookup"><span data-stu-id="fa748-111">Array overview</span></span>

<span data-ttu-id="fa748-112">配列には、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="fa748-112">An array has the following properties:</span></span>

- <span data-ttu-id="fa748-113">配列は、[1 次元](single-dimensional-arrays.md)、[多次元](multidimensional-arrays.md)、または[ジャグ](jagged-arrays.md)のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="fa748-113">An array can be [single-dimensional](single-dimensional-arrays.md), [multidimensional](multidimensional-arrays.md) or [jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="fa748-114">次元数と各次元の長さは、配列インスタンスの作成時に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fa748-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="fa748-115">インスタンスの有効期間中にこれらの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa748-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="fa748-116">数値配列要素の既定値はゼロに設定され、参照要素は null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fa748-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="fa748-117">ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="fa748-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="fa748-118">配列には、ゼロから始まるインデックスが付けられます。`n` 個の要素を含む配列には、`0` から `n-1` までのインデックスが付けられます。</span><span class="sxs-lookup"><span data-stu-id="fa748-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="fa748-119">配列の要素および配列型は、どのような型でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="fa748-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="fa748-120">配列型は、抽象基本型 <xref:System.Array> から派生した[参照型](../../language-reference/keywords/reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="fa748-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="fa748-121">この型は <xref:System.Collections.IEnumerable> と <xref:System.Collections.Generic.IEnumerable%601> を実装するので、C# のすべての配列で [foreach](../../language-reference/keywords/foreach-in.md) 反復処理を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fa748-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

### <a name="arrays-as-objects"></a><span data-ttu-id="fa748-122">オブジェクトとしての配列</span><span class="sxs-lookup"><span data-stu-id="fa748-122">Arrays as Objects</span></span>

<span data-ttu-id="fa748-123">C# の配列は、実際はオブジェクトです。C や C++ の場合のように、単なるアドレス指定可能な連続メモリ領域ではありません。</span><span class="sxs-lookup"><span data-stu-id="fa748-123">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="fa748-124"><xref:System.Array> はすべての配列型の抽象基本データ型で、</span><span class="sxs-lookup"><span data-stu-id="fa748-124"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="fa748-125"><xref:System.Array> のプロパティとその他のクラス メンバーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fa748-125">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="fa748-126">この例としては、<xref:System.Array.Length%2A> プロパティを使用して、配列の長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="fa748-126">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="fa748-127">`numbers` 配列の長さ `5` を `lengthOfNumbers` という変数に代入するコードは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fa748-127">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="fa748-128"><xref:System.Array> クラスには、配列の並べ替え、検索、コピーを行うための便利なメソッドやプロパティが他にも多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="fa748-128">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span> <span data-ttu-id="fa748-129">次の例では、<xref:System.Array.Rank%2A> プロパティを使用して、配列の次元数を表示します。</span><span class="sxs-lookup"><span data-stu-id="fa748-129">The following example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="fa748-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa748-130">See also</span></span>

- [<span data-ttu-id="fa748-131">1 次元配列の使用方法</span><span class="sxs-lookup"><span data-stu-id="fa748-131">How to use single-dimensional arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="fa748-132">多次元配列の使用方法</span><span class="sxs-lookup"><span data-stu-id="fa748-132">How to use multi-dimensional arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="fa748-133">ジャグ配列の使用方法</span><span class="sxs-lookup"><span data-stu-id="fa748-133">How to use jagged arrays</span></span>](jagged-arrays.md)
- [<span data-ttu-id="fa748-134">配列での foreach の使用</span><span class="sxs-lookup"><span data-stu-id="fa748-134">Using foreach with arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="fa748-135">引数としての配列の受け渡し</span><span class="sxs-lookup"><span data-stu-id="fa748-135">Passing arrays as arguments</span></span>](passing-arrays-as-arguments.md)
- [<span data-ttu-id="fa748-136">暗黙的に型指定される配列</span><span class="sxs-lookup"><span data-stu-id="fa748-136">Implicitly typed arrays</span></span>](implicitly-typed-arrays.md)
- [<span data-ttu-id="fa748-137">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fa748-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fa748-138">コレクション</span><span class="sxs-lookup"><span data-stu-id="fa748-138">Collections</span></span>](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
