---
description: '詳細情報: Object Data Type'
title: Object Data Type
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: b1f169e4e590335a0879f5ecd9b68507a3fa2ccb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792155"
---
# <a name="object-data-type"></a><span data-ttu-id="14b37-103">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="14b37-103">Object Data Type</span></span>

<span data-ttu-id="14b37-104">オブジェクトを参照するアドレスを保持します。</span><span class="sxs-lookup"><span data-stu-id="14b37-104">Holds addresses that refer to objects.</span></span> <span data-ttu-id="14b37-105">任意の参照型 (文字列、配列、クラス、またはインターフェイス) を `Object` 変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="14b37-105">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="14b37-106">`Object` 変数は、任意の値の型 (数値、`Boolean`、`Char`、`Date`、構造体、または列挙型) のデータを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="14b37-106">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>

## <a name="remarks"></a><span data-ttu-id="14b37-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="14b37-107">Remarks</span></span>

<span data-ttu-id="14b37-108">`Object` データ型は、アプリケーションで認識されるオブジェクト インスタンスなどの任意のデータ型のデータを指すことができます。</span><span class="sxs-lookup"><span data-stu-id="14b37-108">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="14b37-109">コンパイル時に変数が指す可能性のあるデータ型がわからない場合は、`Object` を使用します。</span><span class="sxs-lookup"><span data-stu-id="14b37-109">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>

<span data-ttu-id="14b37-110">`Object` の既定値は `Nothing` (null 参照) です。</span><span class="sxs-lookup"><span data-stu-id="14b37-110">The default value of `Object` is `Nothing` (a null reference).</span></span>

## <a name="data-types"></a><span data-ttu-id="14b37-111">データの種類</span><span class="sxs-lookup"><span data-stu-id="14b37-111">Data Types</span></span>

<span data-ttu-id="14b37-112">任意のデータ型の変数、定数、または式を `Object` 変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="14b37-112">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="14b37-113">`Object` 変数で現在参照されているデータ型を特定するには、<xref:System.Type?displayProperty=nameWithType> クラスの <xref:System.Type.GetTypeCode%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="14b37-113">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="14b37-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="14b37-114">The following example illustrates this.</span></span>

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

<span data-ttu-id="14b37-115">`Object` データ型は参照型です。</span><span class="sxs-lookup"><span data-stu-id="14b37-115">The `Object` data type is a reference type.</span></span> <span data-ttu-id="14b37-116">ただし、Visual Basic では、値の型のデータを参照するときに、`Object` 変数が値型として扱われます。</span><span class="sxs-lookup"><span data-stu-id="14b37-116">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>

## <a name="storage"></a><span data-ttu-id="14b37-117">記憶域</span><span class="sxs-lookup"><span data-stu-id="14b37-117">Storage</span></span>

<span data-ttu-id="14b37-118">参照先のデータ型にかかわらず、`Object` 変数にはデータ値自体は含まれませんが、値へのポインターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="14b37-118">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="14b37-119">コンピューターのメモリでは常に 4 バイトが使用されますが、変数の値を表すデータの記憶域は含まれません。</span><span class="sxs-lookup"><span data-stu-id="14b37-119">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="14b37-120">コードではポインターを使用してデータが検索されるため、値の型を保持する `Object` 変数は、明示的に型指定された変数よりもアクセスが多少遅くなります。</span><span class="sxs-lookup"><span data-stu-id="14b37-120">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="14b37-121">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="14b37-121">Programming Tips</span></span>

- <span data-ttu-id="14b37-122">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="14b37-122">**Interop Considerations.**</span></span> <span data-ttu-id="14b37-123">オートメーション オブジェクトや COM オブジェクトのように、.NET Framework 向けに作成されていないコンポーネントとやり取りする場合、他の環境のポインター型は Visual Basic の `Object` 型と互換性がないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="14b37-123">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>

- <span data-ttu-id="14b37-124">**パフォーマンス。**</span><span class="sxs-lookup"><span data-stu-id="14b37-124">**Performance.**</span></span> <span data-ttu-id="14b37-125">`Object` 型で宣言する変数は、任意のオブジェクトへの参照を格納するのに十分な柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="14b37-125">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="14b37-126">ただし、このような変数に対してメソッドまたはプロパティを呼び出すと、常に *遅延バインディング* が発生します (実行時)。</span><span class="sxs-lookup"><span data-stu-id="14b37-126">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="14b37-127">(コンパイル時の) *事前バインディング* を強制し、パフォーマンスを向上させるには、特定のクラス名を持つ変数を宣言するか、その変数を特定のデータ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="14b37-127">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>

  <span data-ttu-id="14b37-128">オブジェクト変数を宣言するときは、一般化された `Object` 型ではなく、<xref:System.OperatingSystem> などの特定のクラス型を使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="14b37-128">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="14b37-129">また、<xref:System.Windows.Forms.Control> ではなく <xref:System.Windows.Forms.TextBox> など、使用可能な最も具体的なクラスを使用して、そのプロパティとメソッドにアクセスできるようにする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="14b37-129">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="14b37-130">通常、使用可能なクラス名を見つけるには、**オブジェクト ブラウザー** の **[クラス]** の一覧を使用できます。</span><span class="sxs-lookup"><span data-stu-id="14b37-130">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>

- <span data-ttu-id="14b37-131">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="14b37-131">**Widening.**</span></span> <span data-ttu-id="14b37-132">すべてのデータ型とすべての参照型は、`Object` データ型に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="14b37-132">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="14b37-133">これは、<xref:System.OverflowException?displayProperty=nameWithType> エラーを発生させることなく、任意の型を `Object` に変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="14b37-133">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

  <span data-ttu-id="14b37-134">ただし、値の型と `Object` の間で変換を行う場合、Visual Basic では *ボックス化* と *ボックス化解除* という操作が実行され、これにより実行速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="14b37-134">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>

- <span data-ttu-id="14b37-135">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="14b37-135">**Type Characters.**</span></span> <span data-ttu-id="14b37-136">`Object` には、リテラルの型文字も識別子の型文字も含まれません。</span><span class="sxs-lookup"><span data-stu-id="14b37-136">`Object` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="14b37-137">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="14b37-137">**Framework Type.**</span></span> <span data-ttu-id="14b37-138">.NET Framework において対応する型は、<xref:System.Object?displayProperty=nameWithType> クラスです。</span><span class="sxs-lookup"><span data-stu-id="14b37-138">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>

## <a name="example"></a><span data-ttu-id="14b37-139">例</span><span class="sxs-lookup"><span data-stu-id="14b37-139">Example</span></span>

<span data-ttu-id="14b37-140">次の例は、オブジェクト インスタンスを指す `Object` 変数を示しています。</span><span class="sxs-lookup"><span data-stu-id="14b37-140">The following example illustrates an `Object` variable pointing to an object instance.</span></span>

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a><span data-ttu-id="14b37-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="14b37-141">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="14b37-142">データの種類</span><span class="sxs-lookup"><span data-stu-id="14b37-142">Data Types</span></span>](index.md)
- [<span data-ttu-id="14b37-143">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="14b37-143">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="14b37-144">変換の概要</span><span class="sxs-lookup"><span data-stu-id="14b37-144">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="14b37-145">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="14b37-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="14b37-146">方法: 2 つのオブジェクトが関連しているかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="14b37-146">How to: Determine Whether Two Objects Are Related</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="14b37-147">方法: 2 つのオブジェクトが同一であるかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="14b37-147">How to: Determine Whether Two Objects Are Identical</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
