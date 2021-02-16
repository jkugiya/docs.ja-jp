---
description: '詳細情報: データのフィルター処理 (Visual Basic)'
title: データのフィルター処理
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 2e259209df35a89eb4730f79ffccfee7cb64b9e9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428598"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="04dfb-103">データのフィルター処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04dfb-103">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="04dfb-104">フィルター処理とは、特定の条件を満たす要素のみが含まれるように結果セットを限定する操作のことです。</span><span class="sxs-lookup"><span data-stu-id="04dfb-104">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="04dfb-105">選択とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-105">It is also known as selection.</span></span>

<span data-ttu-id="04dfb-106">次の図は、文字のシーケンスをフィルター処理した結果を示したものです。</span><span class="sxs-lookup"><span data-stu-id="04dfb-106">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="04dfb-107">フィルター処理操作の述語では、文字が "A" でなければならないことが指定されています。</span><span class="sxs-lookup"><span data-stu-id="04dfb-107">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![LINQ のフィルター操作を示す図。](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="04dfb-109">次のセクションでは、選択を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-109">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="04dfb-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="04dfb-110">Methods</span></span>

|<span data-ttu-id="04dfb-111">メソッド名</span><span class="sxs-lookup"><span data-stu-id="04dfb-111">Method Name</span></span>|<span data-ttu-id="04dfb-112">説明</span><span class="sxs-lookup"><span data-stu-id="04dfb-112">Description</span></span>|<span data-ttu-id="04dfb-113">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="04dfb-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="04dfb-114">説明</span><span class="sxs-lookup"><span data-stu-id="04dfb-114">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="04dfb-115">OfType</span><span class="sxs-lookup"><span data-stu-id="04dfb-115">OfType</span></span>|<span data-ttu-id="04dfb-116">指定した型にキャストできるかどうかにより、値を選択します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-116">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="04dfb-117">該当なし。</span><span class="sxs-lookup"><span data-stu-id="04dfb-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="04dfb-118">Where</span><span class="sxs-lookup"><span data-stu-id="04dfb-118">Where</span></span>|<span data-ttu-id="04dfb-119">述語関数に基づいて値を選択します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-119">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="04dfb-120">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="04dfb-120">Query Expression Syntax Example</span></span>

<span data-ttu-id="04dfb-121">次の例では、`Where` を使って、配列から特定の長さを持つ文字列をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-121">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a><span data-ttu-id="04dfb-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="04dfb-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="04dfb-123">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04dfb-123">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="04dfb-124">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="04dfb-124">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="04dfb-125">方法: クエリ結果をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="04dfb-125">How to: Filter Query Results</span></span>](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="04dfb-126">方法: リフレクションを使用してアセンブリのメタデータにクエリを実行する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04dfb-126">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="04dfb-127">方法: 指定された属性または名前のファイルを照会する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04dfb-127">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="04dfb-128">方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04dfb-128">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
