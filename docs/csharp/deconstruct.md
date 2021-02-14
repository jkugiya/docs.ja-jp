---
title: タプルとその他の型の分解
description: タプルとその他の型を分解する方法について説明します。
ms.technology: csharp-fundamentals
ms.date: 11/23/2017
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 5aaf7157b87de4f67f6e4beba18794a6dd13b6d0
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585352"
---
# <a name="deconstructing-tuples-and-other-types"></a><span data-ttu-id="03e86-103">タプルとその他の型の分解</span><span class="sxs-lookup"><span data-stu-id="03e86-103">Deconstructing tuples and other types</span></span>

<span data-ttu-id="03e86-104">タプルでは、軽量な処理でメソッドの呼び出しから複数の値を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="03e86-104">A tuple provides a lightweight way to retrieve multiple values from a method call.</span></span> <span data-ttu-id="03e86-105">ただし、タプルを取得した場合は、その個々の要素を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03e86-105">But once you retrieve the tuple, you have to handle its individual elements.</span></span> <span data-ttu-id="03e86-106">このような処理を要素ごとに行うことは手間がかかります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="03e86-106">Doing this on an element-by-element basis is cumbersome, as the following example shows.</span></span> <span data-ttu-id="03e86-107">`QueryCityData` メソッドは 3 つのタプルを返し、その各要素は別の操作の変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="03e86-107">The `QueryCityData` method returns a 3-tuple, and each of its elements is assigned to a variable in a separate operation.</span></span>

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

<span data-ttu-id="03e86-108">1 つのオブジェクトから複数のフィールドとプロパティの値を取得する処理も同様に煩雑です。メンバーごとにフィールドまたはプロパティの値を変数に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="03e86-108">Retrieving multiple field and property values from an object can be equally cumbersome: you have to assign a field or property value to a variable on a member-by-member basis.</span></span>

<span data-ttu-id="03e86-109">C# 7.0 以降、単一の *分解* 操作で、タプルから複数の要素を取得したり、オブジェクトから複数のフィールド、プロパティ、および計算値を取得したりできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="03e86-109">Starting with C# 7.0, you can retrieve multiple elements from a tuple or retrieve multiple field, property, and computed values from an object in a single *deconstruct* operation.</span></span> <span data-ttu-id="03e86-110">タプルを分解するときに、その要素を個々の変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03e86-110">When you deconstruct a tuple, you assign its elements to individual variables.</span></span> <span data-ttu-id="03e86-111">オブジェクトを分解するときに、選択した値を個々の変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03e86-111">When you deconstruct an object, you assign selected values to individual variables.</span></span>

## <a name="deconstructing-a-tuple"></a><span data-ttu-id="03e86-112">タプルの分解</span><span class="sxs-lookup"><span data-stu-id="03e86-112">Deconstructing a tuple</span></span>

<span data-ttu-id="03e86-113">C# には、タプルの分解を組み込みでサポートしているという特長があり、単一操作でタプル内のすべての項目を展開することができます。</span><span class="sxs-lookup"><span data-stu-id="03e86-113">C# features built-in support for deconstructing tuples, which lets you unpackage all the items in a tuple in a single operation.</span></span> <span data-ttu-id="03e86-114">タプルを分解する一般的な構文は、タプルを定義する構文と似ています。代入ステートメントの左側で変数をかっこで囲み、その各要素に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="03e86-114">The general syntax for deconstructing a tuple is similar to the syntax for defining one: you enclose the variables to which each element is to be assigned in parentheses in the left side of an assignment statement.</span></span> <span data-ttu-id="03e86-115">たとえば、次のステートメントは、4 タプルの要素を 4 つの別の変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03e86-115">For example, the following statement assigns the elements of a 4-tuple to four separate variables:</span></span>

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

<span data-ttu-id="03e86-116">タプルの分解には 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="03e86-116">There are three ways to deconstruct a tuple:</span></span>

- <span data-ttu-id="03e86-117">かっこ内の各フィールドの型を明示的に宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="03e86-117">You can explicitly declare the type of each field inside parentheses.</span></span> <span data-ttu-id="03e86-118">次の例では、この方法を使用して、`QueryCityData` メソッドから返される 3 タプルを分解します。</span><span class="sxs-lookup"><span data-stu-id="03e86-118">The following example uses this approach to deconstruct the 3-tuple returned by the `QueryCityData` method.</span></span>

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- <span data-ttu-id="03e86-119">C# で各変数の型を推定するには、`var` キーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="03e86-119">You can use the `var` keyword so that C# infers the type of each variable.</span></span> <span data-ttu-id="03e86-120">`var` キーワードはかっこの外に配置します。</span><span class="sxs-lookup"><span data-stu-id="03e86-120">You place the `var` keyword outside of the parentheses.</span></span> <span data-ttu-id="03e86-121">次の例では、`QueryCityData` メソッドから返される 3 タプルを分解するときに型の推定を使用します。</span><span class="sxs-lookup"><span data-stu-id="03e86-121">The following example uses type inference when deconstructing the 3-tuple returned by the `QueryCityData` method.</span></span>

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    <span data-ttu-id="03e86-122">また、かっこ内の変数宣言のいずれかまたはすべてについて、個々に `var` キーワードを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="03e86-122">You can also use the `var` keyword individually with any or all of the variable declarations inside the parentheses.</span></span>

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    <span data-ttu-id="03e86-123">ただし、この処理は煩雑なため推奨されません。</span><span class="sxs-lookup"><span data-stu-id="03e86-123">This is cumbersome and is not recommended.</span></span>

- <span data-ttu-id="03e86-124">最後に、既に宣言されている変数にタプルを分解することができます。</span><span class="sxs-lookup"><span data-stu-id="03e86-124">Lastly, you may deconstruct the tuple into variables that have already been declared.</span></span>

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

<span data-ttu-id="03e86-125">タプル内のフィールドすべての型が同じでも、かっこ外では指定できない型があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="03e86-125">Note that you cannot specify a specific type outside the parentheses even if every field in the tuple has the same type.</span></span> <span data-ttu-id="03e86-126">この場合、コンパイル エラー CS8136 "分解 `変数 (...)` フォームは特定の種類の '変数' を許可しません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="03e86-126">This generates compiler error CS8136, "Deconstruction 'var (...)' form disallows a specific type for 'var'.".</span></span>

<span data-ttu-id="03e86-127">また、タプルの各要素も変数に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="03e86-127">Note that you must also assign each element of the tuple to a variable.</span></span> <span data-ttu-id="03e86-128">いずれかの要素を省略すると、コンパイラでエラー CS8132 " 'x' 要素のタプルを 'y' 変数に分解することはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="03e86-128">If you omit any elements, the compiler generates error CS8132, "Cannot deconstruct a tuple of 'x' elements into 'y' variables."</span></span>

<span data-ttu-id="03e86-129">分解の左側にある既存の変数に宣言と割り当てを混在させることはできません。</span><span class="sxs-lookup"><span data-stu-id="03e86-129">Note that you cannot mix declarations and assignments to existing variables on the left-hand side of a deconstruction.</span></span> <span data-ttu-id="03e86-130">メンバーに新しく宣言された変数と既存の変数が含まれる場合、コンパイラでエラー CS8184 "分解の左側で宣言と式を混用できません"</span><span class="sxs-lookup"><span data-stu-id="03e86-130">The compiler generates error CS8184, "a deconstruction cannot mix declarations and expressions on the left-hand-side."</span></span> <span data-ttu-id="03e86-131">が生成されます。</span><span class="sxs-lookup"><span data-stu-id="03e86-131">when the members include newly declared and existing variables.</span></span>

## <a name="deconstructing-tuple-elements-with-discards"></a><span data-ttu-id="03e86-132">破棄によるタプル要素の分解</span><span class="sxs-lookup"><span data-stu-id="03e86-132">Deconstructing tuple elements with discards</span></span>

<span data-ttu-id="03e86-133">タプルを分解する場合、一部の要素の値のみが必要なことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="03e86-133">Often when deconstructing a tuple, you're interested in the values of only some elements.</span></span> <span data-ttu-id="03e86-134">C# 7.0 以降、C# の *破棄* のサポートを利用できるようになりました。破棄は、無視対象と選択した値が指定された書き込み専用の変数です。</span><span class="sxs-lookup"><span data-stu-id="03e86-134">Starting with C# 7.0, you can take advantage of C#'s support for *discards*, which are write-only variables whose values you've chosen to ignore.</span></span> <span data-ttu-id="03e86-135">破棄を指定するには、割り当て内でアンダースコア文字 ("\_") を使用します。</span><span class="sxs-lookup"><span data-stu-id="03e86-135">A discard is designated by an underscore character ("\_") in an assignment.</span></span> <span data-ttu-id="03e86-136">必要に応じて任意の数の値を破棄できます。そのため、すべての値を 1 つの破棄 `_` で表すことができます。</span><span class="sxs-lookup"><span data-stu-id="03e86-136">You can discard as many values as you like; all are represented by the single discard, `_`.</span></span>

<span data-ttu-id="03e86-137">破棄を含むタプルの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="03e86-137">The following example illustrates the use of tuples with discards.</span></span> <span data-ttu-id="03e86-138">`QueryCityDataForYears` メソッドは、市区町村名、その地域、年、市区町村のその年の人口、2 つ目の年、市区町村のその 2 つ目の年の人口という 6 つのタプルを返します。</span><span class="sxs-lookup"><span data-stu-id="03e86-138">The `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="03e86-139">この例は、2 つの年の間に変化した人口数を示しています。</span><span class="sxs-lookup"><span data-stu-id="03e86-139">The example shows the change in population between those two years.</span></span> <span data-ttu-id="03e86-140">タプルから使用できるデータのうち、市区町村の地域は使用しません。また、指定時に市区町村名と 2 つの日付はわかっています。</span><span class="sxs-lookup"><span data-stu-id="03e86-140">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="03e86-141">そのため、タプルに格納されている 2 つの人口値のみが必要であり、残りの値は破棄対象として処理できます。</span><span class="sxs-lookup"><span data-stu-id="03e86-141">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a><span data-ttu-id="03e86-142">ユーザー定義型の分解</span><span class="sxs-lookup"><span data-stu-id="03e86-142">Deconstructing user-defined types</span></span>

<span data-ttu-id="03e86-143">C# には、非タプル型を分解するためのサポートが組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="03e86-143">C# does not offer built-in support for deconstructing non-tuple types.</span></span> <span data-ttu-id="03e86-144">ただし、クラス、構造体、またはインターフェイスの作成者であれば、1 つまたは複数の `Deconstruct` メソッドを実装することで、型のインスタンスを分解することができます。</span><span class="sxs-lookup"><span data-stu-id="03e86-144">However, as the author of a class, a struct, or an interface, you can allow instances of the type to be deconstructed by implementing one or more `Deconstruct` methods.</span></span> <span data-ttu-id="03e86-145">このメソッドからは void が返され、分解される各値はメソッド シグネチャの [out](language-reference/keywords/out-parameter-modifier.md) パラメーターで示されます。</span><span class="sxs-lookup"><span data-stu-id="03e86-145">The method returns void, and each value to be deconstructed is indicated by an [out](language-reference/keywords/out-parameter-modifier.md) parameter in the method signature.</span></span> <span data-ttu-id="03e86-146">たとえば、`Person` クラスの次の `Deconstruct` メソッドは、名、ミドル ネーム、姓を返します。</span><span class="sxs-lookup"><span data-stu-id="03e86-146">For example, the following `Deconstruct` method of a `Person` class returns the first, middle, and last name:</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

<span data-ttu-id="03e86-147">この場合、`p` という `Person` クラスのインスタンスは、次のような割り当てで分解できます。</span><span class="sxs-lookup"><span data-stu-id="03e86-147">You can then deconstruct an instance of the `Person` class named `p` with an assignment like the following:</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

<span data-ttu-id="03e86-148">次の例では、`Deconstruct` メソッドをオーバーロードし、`Person` オブジェクトの多様な組み合わせのプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="03e86-148">The following example overloads the `Deconstruct` method to return various combinations of properties of a `Person` object.</span></span> <span data-ttu-id="03e86-149">各オーバーロードから以下が返されます。</span><span class="sxs-lookup"><span data-stu-id="03e86-149">Individual overloads return:</span></span>

- <span data-ttu-id="03e86-150">名と姓。</span><span class="sxs-lookup"><span data-stu-id="03e86-150">A first and last name.</span></span>
- <span data-ttu-id="03e86-151">名、ミドルネーム、姓。</span><span class="sxs-lookup"><span data-stu-id="03e86-151">A first, middle, and last name.</span></span>
- <span data-ttu-id="03e86-152">名、姓、市区町村名、州名。</span><span class="sxs-lookup"><span data-stu-id="03e86-152">A first name, a last name, a city name, and a state name.</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

<span data-ttu-id="03e86-153">パラメーター数が同じ `Deconstruct` メソッドが複数あると、あいまいになります。</span><span class="sxs-lookup"><span data-stu-id="03e86-153">Multiple `Deconstruct` methods having the same number of parameters are ambiguous.</span></span> <span data-ttu-id="03e86-154">異なる数のパラメーター、つまり "アリティ" を持つ `Deconstruct` メソッドを定義するように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03e86-154">You must be careful to define `Deconstruct` methods with different numbers of parameters, or "arity".</span></span> <span data-ttu-id="03e86-155">オーバーロードの解決時に、パラメーター数が同じ `Deconstruct` メソッドを区別できません。</span><span class="sxs-lookup"><span data-stu-id="03e86-155">`Deconstruct` methods with the same number of parameters cannot be distinguished during overload resolution.</span></span>

## <a name="deconstructing-a-user-defined-type-with-discards"></a><span data-ttu-id="03e86-156">破棄によるユーザー定義型の分解</span><span class="sxs-lookup"><span data-stu-id="03e86-156">Deconstructing a user-defined type with discards</span></span>

<span data-ttu-id="03e86-157">[タプル](#deconstructing-tuple-elements-with-discards)の場合と同様に、破棄を使用して、`Deconstruct` メソッドから返される項目のうち、選択した項目を無視できます。</span><span class="sxs-lookup"><span data-stu-id="03e86-157">Just as you do with [tuples](#deconstructing-tuple-elements-with-discards), you can use discards to ignore selected items returned by a `Deconstruct` method.</span></span> <span data-ttu-id="03e86-158">各破棄は "\_" という変数で定義されます。また、1 つの破棄操作に複数の破棄を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="03e86-158">Each discard is defined by a variable named "\_", and a single deconstruction operation can include multiple discards.</span></span>

<span data-ttu-id="03e86-159">`Person` オブジェクトを 4 つの文字列 (名、姓、市区町村、州) に分解し、姓と州を破棄する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="03e86-159">The following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state) but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a><span data-ttu-id="03e86-160">拡張メソッドによるユーザー定義型の分解</span><span class="sxs-lookup"><span data-stu-id="03e86-160">Deconstructing a user-defined type with an extension method</span></span>

<span data-ttu-id="03e86-161">クラス、構造体、またはインターフェイスを作成していない場合でも、目的の値を返す `Deconstruct` [拡張メソッド](programming-guide/classes-and-structs/extension-methods.md)を 1 つまたは複数実装することで、このようなオブジェクトを分解することができます。</span><span class="sxs-lookup"><span data-stu-id="03e86-161">If you didn't author a class, struct, or interface, you can still deconstruct objects of that type by implementing one or more `Deconstruct` [extension methods](programming-guide/classes-and-structs/extension-methods.md) to return the values in which you're interested.</span></span>

<span data-ttu-id="03e86-162"><xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> クラスの `Deconstruct` 拡張メソッドを 2 つ定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="03e86-162">The following example defines two `Deconstruct` extension methods for the <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="03e86-163">1 つ目の拡張メソッドは、型、静的かインスタンスか、読み取り専用かどうか、インデックスが作成されているかどうかなど、プロパティの特徴を示す値のセットを返します。</span><span class="sxs-lookup"><span data-stu-id="03e86-163">The first returns a set of values that indicate the characteristics of the property, including its type, whether it's static or instance, whether it's read-only, and whether it's indexed.</span></span> <span data-ttu-id="03e86-164">2 つ目の拡張メソッドは、プロパティのアクセシビリティを示します。</span><span class="sxs-lookup"><span data-stu-id="03e86-164">The second indicates the property's accessibility.</span></span> <span data-ttu-id="03e86-165">get アクセサーと set アクセサーのアクセシビリティは異なる可能性があるため、ブール値は、プロパティの get アクセサーと set アクセサーが異なるかどうか、また異なる場合はアクセシビリティが同じかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="03e86-165">Because the accessibility of get and set accessors can differ, Boolean values indicate whether the property has separate get and set accessors and, if it does, whether they have the same accessibility.</span></span> <span data-ttu-id="03e86-166">アクセサーが 1 つのみの場合、または get アクセサーと set アクセサーのアクセシビリティが同じ場合、`access` 変数は、全体としてそのアクセシビリティのプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="03e86-166">If there is only one accessor or both the get and the set accessor have the same accessibility, the `access` variable indicates the accessibility of the property as a whole.</span></span> <span data-ttu-id="03e86-167">それ以外の場合、get アクセサーと set アクセサーのアクセシビリティは `getAccess` 変数と `setAccess` 変数で示されます。</span><span class="sxs-lookup"><span data-stu-id="03e86-167">Otherwise, the accessibility of the get and set accessors are indicated by the `getAccess` and `setAccess` variables.</span></span>

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a><span data-ttu-id="03e86-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="03e86-168">See also</span></span>

- [<span data-ttu-id="03e86-169">破棄</span><span class="sxs-lookup"><span data-stu-id="03e86-169">Discards</span></span>](discards.md)
- [<span data-ttu-id="03e86-170">タプル型</span><span class="sxs-lookup"><span data-stu-id="03e86-170">Tuple types</span></span>](language-reference/builtin-types/value-tuples.md)
