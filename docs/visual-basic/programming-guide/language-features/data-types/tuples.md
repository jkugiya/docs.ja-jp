---
description: '詳細情報: タプル (Visual Basic)'
title: タプル
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: f598facb446b7d50864c0cf9151195cfcde158bb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454457"
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="88ad7-103">タプル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88ad7-103">Tuples (Visual Basic)</span></span>

<span data-ttu-id="88ad7-104">Visual Basic 2017 以降、Visual Basic 言語ではタプルの組み込みサポートが提供されています。これによって、タプルの作成とタプルの要素へのアクセスが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-104">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="88ad7-105">タプルは、特定の数とシーケンスの値が含まれる軽量なデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-105">A tuple is a lightweight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="88ad7-106">タプルをインスタンス化するときは、各値 (または要素) の数とデータ型を定義します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-106">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="88ad7-107">たとえば、2 タプル (つまりペア) には 2 つの要素があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-107">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="88ad7-108">1 つ目を `Boolean` 値、2つ目を `String` にすることができます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-108">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="88ad7-109">タプルを使用すると複数の値を 1 つのオブジェクトに簡単に格納できるので、多くの場合、メソッドから複数の値を返すための軽量な方法として使用されます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-109">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88ad7-110">タプルのサポートには <xref:System.ValueTuple> 型が必要です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-110">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="88ad7-111">.NET Framework 4.7 がインストールされていない場合は、NuGet ギャラリーから入手できる NuGet パッケージ `System.ValueTuple` を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-111">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="88ad7-112">このパッケージがないと、"定義済みの型 'ValueTuple(Of,,,)' は定義またはインポートされていません" のようなコンパイル エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-112">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="88ad7-113">タプルのインスタンス化と使用</span><span class="sxs-lookup"><span data-stu-id="88ad7-113">Instantiating and using a tuple</span></span>

<span data-ttu-id="88ad7-114">タプルをインスタンス化するには、コンマ区切り値をかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-114">You instantiate a tuple by enclosing its comma-delimited values in parentheses.</span></span> <span data-ttu-id="88ad7-115">これらの値のそれぞれがタプルのフィールドになります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-115">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="88ad7-116">たとえば、次のコードではトリプル (つまり 3 タプル) が定義されており、`Date` が 1 つ目の値、`String` が 2 つ目の値、`Boolean` が 3 つ目の値です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-116">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="88ad7-117">既定では、タプルの各フィールドの名前は、文字列 `Item` と、タプル内のフィールドの位置を示す 1 から始まる数字で構成されます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-117">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="88ad7-118">この 3 タプルでは、`Date` フィールドが `Item1`、`String` フィールドが `Item2`、`Boolean` フィールドが `Item3` です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-118">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="88ad7-119">次の例では、前のコード行でインスタンス化されたタプルのフィールドの値を表示します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-119">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="88ad7-120">Visual Basic タプルのフィールドは読み取り/書き込み可能です。タプルをインスタンス化すると、その値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-120">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="88ad7-121">次の例では、前の例で作成したタプルの 3 つのフィールドのうち 2 つを変更し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-121">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="88ad7-122">名前付きタプルのインスタンス化と使用</span><span class="sxs-lookup"><span data-stu-id="88ad7-122">Instantiating and using a named tuple</span></span>

<span data-ttu-id="88ad7-123">タプルのフィールドに既定の名前を使用するのではなく、独自の名前をタプルの要素に割り当てることによって、"*名前付きタプル*" をインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-123">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="88ad7-124">その後、タプルのフィールドに、割り当てられた名前 "*または*" 既定の名前でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-124">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="88ad7-125">次の例では、前と同じ 3 タプルをインスタンス化していますが、1 つ目のフィールド `EventDate`、2 つ目 `Name`、3 つ目 `IsHoliday` を明示的に指定する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-125">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="88ad7-126">次に、フィールド値を表示し、変更してから、フィールドの値を再度表示します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-126">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="88ad7-127">推論されたタプル要素の名前</span><span class="sxs-lookup"><span data-stu-id="88ad7-127">Inferred tuple element names</span></span>

<span data-ttu-id="88ad7-128">Visual Basic 15.3 以降では、Visual Basic がタプル要素の名前を推定できます。明示的に割り当てる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="88ad7-128">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="88ad7-129">推定タプル名は、一連の変数からタプルを初期化するときに、タプル要素名を変数名と同じにする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-129">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span>

<span data-ttu-id="88ad7-130">次の例では、明示的に指定された3つの要素、`state`、`stateName`、および `capital` を含む `stateInfo` タプルを作成します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-130">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="88ad7-131">要素の名前を付けるとき、タプルの初期化ステートメントにより、名前が付けられる要素に同じ名前の変数の値が単に代入されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="88ad7-131">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]

<span data-ttu-id="88ad7-132">要素と変数の名前が同じであるため、次の例に示すように、Visual Basic コンパイラがフィールドの名前を推定できます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-132">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="88ad7-133">推定タプル要素名を有効にするには、Visual Basic プロジェクト (\*.vbproj) ファイルに使用する Visual Basic コンパイラのバージョンを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-133">To enable inferred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.3</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="88ad7-134">バージョン番号として、15.3 以降の任意の Visual Basic コンパイラ バージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-134">The version number can be any version of the Visual Basic compiler starting with 15.3.</span></span> <span data-ttu-id="88ad7-135">特定のコンパイラ バージョンをハードコーディングする代わりに、`LangVersion` の値として "Latest" を指定すると、システムにインストールされている最新バージョンの Visual Basic コンパイラでコンパイルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-135">Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.</span></span>

<span data-ttu-id="88ad7-136">詳細については、[Visual Basic 言語バージョンの設定](../../../language-reference/configure-language-version.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="88ad7-136">For more information, see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="88ad7-137">場合によっては、Visual Basic コンパイラが候補名からタプル要素名を推定できないことがあり、`Item1`、`Item2` などの既定名を使用しないとタプル フィールドを参照できません。次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-137">In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:</span></span>

- <span data-ttu-id="88ad7-138">候補名が、タプル メンバーの名前と同じです (`Item3`、`Rest`、`ToString` など)。</span><span class="sxs-lookup"><span data-stu-id="88ad7-138">The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.</span></span>

- <span data-ttu-id="88ad7-139">候補名がタプル内で重複しています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-139">The candidate name is duplicated in the tuple.</span></span>

<span data-ttu-id="88ad7-140">フィールド名の推定に失敗しても、Visual Basic はコンパイラ エラーを生成せず、実行時に例外がスローされることもありません。</span><span class="sxs-lookup"><span data-stu-id="88ad7-140">When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime.</span></span> <span data-ttu-id="88ad7-141">代わりに、`Item1` や `Item2` など、定義済みの名前でタプル フィールドを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-141">Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`.</span></span>

## <a name="tuples-versus-structures"></a><span data-ttu-id="88ad7-142">タプルと構造体</span><span class="sxs-lookup"><span data-stu-id="88ad7-142">Tuples versus structures</span></span>

<span data-ttu-id="88ad7-143">Visual Basic のタプルは、**System.ValueTuple** ジェネリック型の 1 つのインスタンスである値型です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-143">A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types.</span></span> <span data-ttu-id="88ad7-144">たとえば、前の例で定義されている `holiday` タプルは、<xref:System.ValueTuple%603> 構造体のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="88ad7-144">For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure.</span></span> <span data-ttu-id="88ad7-145">これは、データの軽量コンテナーとして設計されています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-145">It is designed to be a lightweight container for data.</span></span> <span data-ttu-id="88ad7-146">タプルは、複数のデータ項目を含むオブジェクトを簡単に作成することを目的としているため、カスタム構造体であれば備えている機能の一部が欠落しています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-146">Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have.</span></span> <span data-ttu-id="88ad7-147">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-147">These include:</span></span>

- <span data-ttu-id="88ad7-148">カスタム メンバー。</span><span class="sxs-lookup"><span data-stu-id="88ad7-148">Custom members.</span></span> <span data-ttu-id="88ad7-149">タプルに対して独自のプロパティ、メソッド、またはイベントを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="88ad7-149">You cannot define your own properties, methods, or events for a tuple.</span></span>

- <span data-ttu-id="88ad7-150">検証。</span><span class="sxs-lookup"><span data-stu-id="88ad7-150">Validation.</span></span> <span data-ttu-id="88ad7-151">フィールドに代入されたデータを検証することはできません。</span><span class="sxs-lookup"><span data-stu-id="88ad7-151">You cannot validate the data assigned to fields.</span></span>

- <span data-ttu-id="88ad7-152">不変性。</span><span class="sxs-lookup"><span data-stu-id="88ad7-152">Immutability.</span></span> <span data-ttu-id="88ad7-153">Visual Basic のタプルは変更可能です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-153">Visual Basic tuples are mutable.</span></span> <span data-ttu-id="88ad7-154">対照的に、カスタム構造体では、インスタンスを変更可能にするかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-154">In contrast, a custom structure allows you to control whether an instance is mutable or immutable.</span></span>

<span data-ttu-id="88ad7-155">カスタム メンバー、プロパティとフィールドの検証、または不変性が重要な場合は、Visual Basic の [Structure](../../../language-reference/statements/structure-statement.md) ステートメントを使用してカスタム値型を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-155">If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.</span></span>

<span data-ttu-id="88ad7-156">Visual Basic のタプルは、**ValueTuple** 型のメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-156">A Visual Basic tuple does inherit the members of its **ValueTuple** type.</span></span> <span data-ttu-id="88ad7-157">フィールドに加えて、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-157">In addition to its fields, these include the following methods:</span></span>

| <span data-ttu-id="88ad7-158">Method</span><span class="sxs-lookup"><span data-stu-id="88ad7-158">Method</span></span> | <span data-ttu-id="88ad7-159">説明</span><span class="sxs-lookup"><span data-stu-id="88ad7-159">Description</span></span> |
| ---|---|
| <span data-ttu-id="88ad7-160">CompareTo</span><span class="sxs-lookup"><span data-stu-id="88ad7-160">CompareTo</span></span> | <span data-ttu-id="88ad7-161">現在のタプルを、同じ数の要素を持つ別のタプルと比較します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-161">Compares the current tuple to another tuple with the same number of elements.</span></span> |
| <span data-ttu-id="88ad7-162">次の値に等しい</span><span class="sxs-lookup"><span data-stu-id="88ad7-162">Equals</span></span> | <span data-ttu-id="88ad7-163">現在のタプルが別のタプルまたはオブジェクトと等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-163">Determines whether the current tuple is equal to another tuple or object.</span></span> |
| <span data-ttu-id="88ad7-164">GetHashCode</span><span class="sxs-lookup"><span data-stu-id="88ad7-164">GetHashCode</span></span> | <span data-ttu-id="88ad7-165">現在のインスタンスのハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-165">Calculates the hash code for the current instance.</span></span> |
| <span data-ttu-id="88ad7-166">ToString</span><span class="sxs-lookup"><span data-stu-id="88ad7-166">ToString</span></span> | <span data-ttu-id="88ad7-167">`(Item1, Item2...)` という形式で、このタプルの文字列表現を返します。`Item1` と `Item2` はタプルのフィールドの値を表しています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-167">Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields.</span></span> |

<span data-ttu-id="88ad7-168">さらに、**ValueTuple** 型は <xref:System.Collections.IStructuralComparable> および <xref:System.Collections.IStructuralEquatable> インターフェイスを実装し、これらによってカスタム比較演算子を定義できます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-168">In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define custom comparers.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="88ad7-169">割り当てとタプル</span><span class="sxs-lookup"><span data-stu-id="88ad7-169">Assignment and tuples</span></span>

<span data-ttu-id="88ad7-170">Visual Basic では、同じ数のフィールドを含むタプル型の間の代入がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-170">Visual Basic supports assignment between tuple types that have the same number of fields.</span></span> <span data-ttu-id="88ad7-171">次のいずれかに該当する場合は、フィールドの型を変換できます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-171">The field types can be converted if one of the following is true:</span></span>

- <span data-ttu-id="88ad7-172">代入元と代入先のフィールドの型が同じです。</span><span class="sxs-lookup"><span data-stu-id="88ad7-172">The source and target field are of the same type.</span></span>

- <span data-ttu-id="88ad7-173">代入元の型から代入先の型への拡大 (つまり暗黙) の変換が定義されています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-173">A widening (or implicit) conversion of the source type to the target type is defined.</span></span>

- <span data-ttu-id="88ad7-174">`Option Strict` が `On` になっており、代入元の型から代入先の型への縮小 (つまり明示的) の変換が定義されています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-174">`Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined.</span></span> <span data-ttu-id="88ad7-175">代入元の値が代入先の型の範囲外の場合、この変換によって例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-175">This conversion can throw an exception if the source value is outside the range of the target type.</span></span>

<span data-ttu-id="88ad7-176">他の変換は、割り当てでは考慮されません。</span><span class="sxs-lookup"><span data-stu-id="88ad7-176">Other conversions are not considered for assignments.</span></span> <span data-ttu-id="88ad7-177">タプル型間で許可されている割り当ての種類を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="88ad7-177">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="88ad7-178">以降の例で使用されている変数について考えます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-178">Consider these variables used in the following examples:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

<span data-ttu-id="88ad7-179">最初の 2 つの変数 `unnamed` および `anonymous` では、フィールドにセマンティック名が割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="88ad7-179">The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields.</span></span> <span data-ttu-id="88ad7-180">フィールド名は、既定の `Item1` と `Item2` です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-180">Their field names are the default `Item1` and `Item2`.</span></span> <span data-ttu-id="88ad7-181">最後の 2 つの変数 `named` および `differentName` には、セマンティック フィールド名が付けられています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-181">The last two variables, `named` and `differentName` have semantic field names.</span></span> <span data-ttu-id="88ad7-182">この 2 つのタプルでは、フィールド名が異なっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="88ad7-182">Note that these two tuples have different names for the fields.</span></span>

<span data-ttu-id="88ad7-183">この 4 つのタプルに含まれているフィールドの数 ("アリティ" と呼ばれます) とフィールドの型は同じです。</span><span class="sxs-lookup"><span data-stu-id="88ad7-183">All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical.</span></span> <span data-ttu-id="88ad7-184">このため、これらの割り当てはすべて機能します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-184">Therefore, all of these assignments work:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

<span data-ttu-id="88ad7-185">タプルの名前が割り当てられていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="88ad7-185">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="88ad7-186">フィールドの値は、タプルのフィールドの順序に従って割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-186">The values of the fields are assigned following the order of the fields in the tuple.</span></span>

<span data-ttu-id="88ad7-187">最終的に、`named` の 1 つ目のフィールドが `Integer` で、`Long` の 1 つ目のフィールドが `conversion` でも、`named` タプルを `conversion` タプルに代入できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="88ad7-187">Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`.</span></span> <span data-ttu-id="88ad7-188">この代入が成功するのは、`Integer` から `Long` への変換が拡大変換であるためです。</span><span class="sxs-lookup"><span data-stu-id="88ad7-188">This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

<span data-ttu-id="88ad7-189">フィールドの数が異なるタプルは代入できません。</span><span class="sxs-lookup"><span data-stu-id="88ad7-189">Tuples with different numbers of fields are not assignable:</span></span>

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="88ad7-190">メソッドの戻り値としてのタプル</span><span class="sxs-lookup"><span data-stu-id="88ad7-190">Tuples as method return values</span></span>

<span data-ttu-id="88ad7-191">1 つのメソッドで返すことができる値は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="88ad7-191">A method can return only a single value.</span></span> <span data-ttu-id="88ad7-192">しかし、1 回のメソッド呼び出しで複数の値を返すことが望ましい場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-192">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="88ad7-193">この制限を回避するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-193">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="88ad7-194">カスタム クラスまたは構造体を作成して、そのプロパティまたはフィールドがメソッドによって返される値を表すようにできます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-194">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="88ad7-195">これは、重量ソリューションです。メソッド呼び出しの値を取得するためだけにカスタム型を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-195">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="88ad7-196">メソッドから 1 つの値を返し、メソッドの参照によって残りの値を渡して返すことができます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-196">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="88ad7-197">これは、変数をインスタンス化する際のオーバーヘッドが発生し、参照によって渡す変数の値が誤って上書きされるリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-197">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="88ad7-198">複数の戻り値を取得するための軽量ソリューションを提供するタプルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-198">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="88ad7-199">たとえば、.NET の **TryParse** メソッドは、解析操作が成功したかどうかを示す `Boolean` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-199">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="88ad7-200">解析操作の結果は、メソッドへの参照によって渡される変数で返されます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-200">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="88ad7-201">通常、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType> などの解析メソッドを呼び出すと、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-201">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="88ad7-202"><xref:System.Int32.TryParse%2A?displayProperty=nameWithType> メソッドへの呼び出しを独自のメソッドでラップすると、解析操作からタプルを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-202">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="88ad7-203">次の例では、`NumericLibrary.ParseInteger` が <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> メソッドを呼び出し、2 つの要素を含む名前付きタプルを返します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-203">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="88ad7-204">さらに、次のコードを使用してメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-204">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="88ad7-205">Visual Basic のタプルと .NET Framework のタプル</span><span class="sxs-lookup"><span data-stu-id="88ad7-205">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="88ad7-206">Visual Basic のタプルは、.NET Framework 4.7 に導入された **System.ValueTuple** ジェネリック型の 1 つのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="88ad7-206">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="88ad7-207">.NET Framework には、一連のジェネリック **System.Tuple** クラスも含まれています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-207">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="88ad7-208">ただし、これらのクラスは、Visual Basic のタプルや **System.ValueTuple** ジェネリック型とはいくつかの点で異なっています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-208">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="88ad7-209">**Tuple** クラスの要素は、`Item1`、`Item2` などと名前が付けられるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="88ad7-209">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="88ad7-210">Visual Basic のタプルと **ValueTuple** 型では、タプルの要素はフィールドです。</span><span class="sxs-lookup"><span data-stu-id="88ad7-210">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="88ad7-211">**Tuple** インスタンスまたは **ValueTuple** インスタンスの要素には、わかりやすい名前を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="88ad7-211">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="88ad7-212">Visual Basic では、フィールドの意味を伝える名前を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="88ad7-212">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="88ad7-213">**Tuple** インスタンスのプロパティは読み取り専用です。つまり、タプルは変更不可能です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-213">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="88ad7-214">Visual Basic のタプルと **ValueTuple** 型では、タプルのフィールドは読み取り/書き込み可能です。つまり、タプルは変更可能です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-214">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="88ad7-215">ジェネリック **Tuple** 型は参照型です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-215">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="88ad7-216">これらの **Tuple** 型の使用は、オブジェクトの割り当てを意味します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-216">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="88ad7-217">ホット パスでは、これがアプリケーションのパフォーマンスに大きな影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-217">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="88ad7-218">Visual Basic のタプルと **ValueTuple** 型は値型です。</span><span class="sxs-lookup"><span data-stu-id="88ad7-218">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="88ad7-219"><xref:System.TupleExtensions> クラスの拡張メソッドを使用すると、Visual Basic のタプルと .NET **Tuple** オブジェクトの変換が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="88ad7-219">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="88ad7-220">**ToTuple** メソッドは Visual Basic のタプルを .NET **Tuple** オブジェクトに変換し、**ToValueTuple** メソッドは .NET **Tuple** オブジェクトを Visual Basic のタプルに変換します。</span><span class="sxs-lookup"><span data-stu-id="88ad7-220">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="88ad7-221">次の例では、タプルを作成し、それを .NET **Tuple** オブジェクトに変換してから、再び Visual Basic のタプルに変換しています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-221">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="88ad7-222">例は、その後、このタプルと最初のタプルを比較して、等しいことを確認しています。</span><span class="sxs-lookup"><span data-stu-id="88ad7-222">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="88ad7-223">関連項目</span><span class="sxs-lookup"><span data-stu-id="88ad7-223">See also</span></span>

- [<span data-ttu-id="88ad7-224">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="88ad7-224">Visual Basic Language Reference</span></span>](index.md)
