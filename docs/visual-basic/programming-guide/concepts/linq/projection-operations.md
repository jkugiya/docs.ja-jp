---
description: '詳細情報: 射影操作 (Visual Basic)'
title: 射影操作
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: 5531bec915f3a9ee521e0d67941b8f1d49e90524
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466459"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="b2fbb-103">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2fbb-103">Projection Operations (Visual Basic)</span></span>

<span data-ttu-id="b2fbb-104">射影とは、オブジェクトを、必要なプロパティだけで構成された別の形式に変換する操作のことをいいます。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-104">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="b2fbb-105">射影を使用することにより、個々のオブジェクトから構築された新しい型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-105">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="b2fbb-106">プロパティを投影し、それに対して数値演算関数を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-106">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="b2fbb-107">また、元のオブジェクトを変更せずに射影することもできます。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-107">You can also project the original object without changing it.</span></span>

<span data-ttu-id="b2fbb-108">次のセクションでは、射影を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-108">The standard query operator methods that perform projection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="b2fbb-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="b2fbb-109">Methods</span></span>

|<span data-ttu-id="b2fbb-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="b2fbb-110">Method Name</span></span>|<span data-ttu-id="b2fbb-111">説明</span><span class="sxs-lookup"><span data-stu-id="b2fbb-111">Description</span></span>|<span data-ttu-id="b2fbb-112">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="b2fbb-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b2fbb-113">説明</span><span class="sxs-lookup"><span data-stu-id="b2fbb-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="b2fbb-114">選択</span><span class="sxs-lookup"><span data-stu-id="b2fbb-114">Select</span></span>|<span data-ttu-id="b2fbb-115">変換関数に基づいて値を射影します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-115">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|
|<span data-ttu-id="b2fbb-116">SelectMany</span><span class="sxs-lookup"><span data-stu-id="b2fbb-116">SelectMany</span></span>|<span data-ttu-id="b2fbb-117">変換関数に基づいて値のシーケンスを射影し、それを 1 つのシーケンスに平坦化します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-117">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="b2fbb-118">複数の `From` 句を使用</span><span class="sxs-lookup"><span data-stu-id="b2fbb-118">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="b2fbb-119">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="b2fbb-119">Query Expression Syntax Examples</span></span>

### <a name="select"></a><span data-ttu-id="b2fbb-120">選択</span><span class="sxs-lookup"><span data-stu-id="b2fbb-120">Select</span></span>

<span data-ttu-id="b2fbb-121">次の例では、`Select` 句を使って、文字列リストにある各文字列の最初の文字を射影します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-121">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>

```vb
Dim words = New List(Of String) From {"an", "apple", "a", "day"}

Dim query = From word In words
            Select word.Substring(0, 1)

Dim sb As New System.Text.StringBuilder()
For Each letter As String In query
    sb.AppendLine(letter)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' a
' a
' a
' d
```

### <a name="selectmany"></a><span data-ttu-id="b2fbb-122">SelectMany</span><span class="sxs-lookup"><span data-stu-id="b2fbb-122">SelectMany</span></span>

<span data-ttu-id="b2fbb-123">次の例では、`From` 句を複数使用して、文字列リストにある各文字列の各単語を射影します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-123">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>

```vb
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}

Dim query = From phrase In phrases
            From word In phrase.Split(" "c)
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' an
' apple
' a
' day
' the
' quick
' brown
' fox
```

## <a name="select-versus-selectmany"></a><span data-ttu-id="b2fbb-124">Select と SelectMany の比較</span><span class="sxs-lookup"><span data-stu-id="b2fbb-124">Select versus SelectMany</span></span>

<span data-ttu-id="b2fbb-125">`Select()` と `SelectMany()` の機能はどちらも、ソース値から結果値 (複数も可) を生成することです。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-125">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="b2fbb-126">`Select()` は、ソース値ごとに結果値を 1 つ生成します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-126">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="b2fbb-127">そのため、結果全体は、ソース コレクションと同じ数の要素を持つ 1 つのコレクションになります。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-127">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="b2fbb-128">これに対し、`SelectMany()` は、各ソース値から、連結されたサブコレクションを含む 1 つの総合的な結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-128">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="b2fbb-129">`SelectMany()` に引数として渡される変換関数は、ソース値ごとに列挙可能な値のシーケンスを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-129">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="b2fbb-130">この列挙可能なシーケンスは `SelectMany()` によって連結されて、1 つの大きなシーケンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-130">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>

<span data-ttu-id="b2fbb-131">これら 2 つのメソッドのアクションの概念的な違いを次の 2 つの図に示します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-131">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="b2fbb-132">どちらも、セレクター (変換) 関数が各ソース値から花の配列を選択することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-132">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>

<span data-ttu-id="b2fbb-133">次の図は、`Select()` がソース コレクションと同じ数の要素を持つコレクションを返すしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-133">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>

![Select&#40;&#41; のアクションを示すグラフィック。](./media/projection-operations/select-action-graphic.png)

<span data-ttu-id="b2fbb-135">次の図は、`SelectMany()` が中間配列シーケンスを、各中間配列の値を含む最終的な結果値に連結するしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-135">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>

![SelectMany&#40;&#41; のアクションを示すグラフィック。](./media/projection-operations/select-many-action-graphic.png )

### <a name="code-example"></a><span data-ttu-id="b2fbb-137">コード例</span><span class="sxs-lookup"><span data-stu-id="b2fbb-137">Code Example</span></span>

<span data-ttu-id="b2fbb-138">次の例は、`Select()` と `SelectMany()` の動作を比較しています。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-138">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="b2fbb-139">コードは、ソース コレクションの花の名前の各リストから最初の 2 つの項目を取って "花束" を作成します。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-139">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="b2fbb-140">この例では、変換関数 <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> が使用する "単一の値" 自体が値のコレクションになっています。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-140">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="b2fbb-141">各サブ シーケンスで各文字列を列挙するために追加の `For Each` ループを使用しています。</span><span class="sxs-lookup"><span data-stu-id="b2fbb-141">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>

```vb
Class Bouquet
    Public Flowers As List(Of String)
End Class

Sub SelectVsSelectMany()
    Dim bouquets = New List(Of Bouquet) From {
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}

    Dim output As New System.Text.StringBuilder

    ' Select()
    Dim query1 = bouquets.Select(Function(b) b.Flowers)

    output.AppendLine("Using Select():")
    For Each flowerList In query1
        For Each str As String In flowerList
            output.AppendLine(str)
        Next
    Next

    ' SelectMany()
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)

    output.AppendLine(vbCrLf & "Using SelectMany():")
    For Each str As String In query2
        output.AppendLine(str)
    Next

    ' Display the output
    MsgBox(output.ToString())

    ' This code produces the following output:
    '
    ' Using Select():
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

    ' Using SelectMany()
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

End Sub
```

## <a name="see-also"></a><span data-ttu-id="b2fbb-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2fbb-142">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b2fbb-143">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2fbb-143">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="b2fbb-144">Select 句</span><span class="sxs-lookup"><span data-stu-id="b2fbb-144">Select Clause</span></span>](../../../language-reference/queries/select-clause.md)
- [<span data-ttu-id="b2fbb-145">方法: 結合を使用したデータの結合</span><span class="sxs-lookup"><span data-stu-id="b2fbb-145">How to: Combine Data with Joins</span></span>](../../language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [<span data-ttu-id="b2fbb-146">方法: 複数のソースからオブジェクトコレクションにデータを設定する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2fbb-146">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="b2fbb-147">方法: 特定の型での LINQ クエリ結果の取得</span><span class="sxs-lookup"><span data-stu-id="b2fbb-147">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [<span data-ttu-id="b2fbb-148">方法: グループを使用してファイルを複数のファイルに分割する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2fbb-148">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
