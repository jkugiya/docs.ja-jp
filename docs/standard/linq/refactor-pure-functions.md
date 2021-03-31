---
title: 純粋関数にリファクタリングする - LINQ to XML
description: 純粋関数と、それを利用してコードをリファクタリングする方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 18418a1fc39bee9f08cbe92d42c842e3fc9e148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366014"
---
# <a name="refactor-into-pure-functions-linq-to-xml"></a><span data-ttu-id="36249-103">純粋関数にリファクタリングする (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="36249-103">Refactor into pure functions (LINQ to XML)</span></span>

<span data-ttu-id="36249-104">純粋関数型変換で重要なのは、純粋関数を使用してコードをリファクターする方法を理解することです。</span><span class="sxs-lookup"><span data-stu-id="36249-104">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

> [!NOTE]
> <span data-ttu-id="36249-105">関数型プログラミングでの命名には、一般に純粋関数を使用してプログラムをリファクターする方法が使用されます。</span><span class="sxs-lookup"><span data-stu-id="36249-105">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="36249-106">Visual Basic および C++ では、この処理がそれぞれの言語の関数を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="36249-106">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="36249-107">ただし C# では、関数がメソッドと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="36249-107">However, in C#, functions are called methods.</span></span> <span data-ttu-id="36249-108">ここでは、純粋関数が C# のメソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="36249-108">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>

<span data-ttu-id="36249-109">このセクションで既に説明したように、純粋関数には 2 つの実用的な特性があります。</span><span class="sxs-lookup"><span data-stu-id="36249-109">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="36249-110">副作用がありません。</span><span class="sxs-lookup"><span data-stu-id="36249-110">It has no side effects.</span></span> <span data-ttu-id="36249-111">この関数は、関数の外部にある変数やあらゆる型のデータを一切変更しません。</span><span class="sxs-lookup"><span data-stu-id="36249-111">The function doesn't change any variables or the data of any type outside of the function.</span></span>
- <span data-ttu-id="36249-112">一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="36249-112">It's consistent.</span></span> <span data-ttu-id="36249-113">同じ入力データを与えられると、常に同じ出力値を返します。</span><span class="sxs-lookup"><span data-stu-id="36249-113">Given the same set of input data, it will always return the same output value.</span></span>

<span data-ttu-id="36249-114">関数型プログラミングに移行するには、既存のコードをリファクターして不要な副作用や外部依存関係を排除するのが 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="36249-114">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="36249-115">この方法で、既存のコードの純粋関数バージョンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="36249-115">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="36249-116">この記事では、純粋関数の特徴とそれ以外の関数の特徴について説明します。</span><span class="sxs-lookup"><span data-stu-id="36249-116">This article discusses what a pure function is and what it's not.</span></span> <span data-ttu-id="36249-117">[WordprocessingML ドキュメント内のコンテンツの操作](xml-shape-wordprocessingml-documents.md)に関するチュートリアルでは、WordprocessingML ドキュメントの操作方法を説明し、純粋関数を使用してリファクターする方法を示す 2 つの例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="36249-117">The [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

<span data-ttu-id="36249-118">次の例に示す 2 つの非純粋関数と 1 つの純粋関数を参照して、その違いを確認してください。</span><span class="sxs-lookup"><span data-stu-id="36249-118">The following examples contrast two non-pure functions and a pure function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-static-class-member"></a><span data-ttu-id="36249-119">例: 静的クラス メンバーを変更する非純粋関数を実装する</span><span class="sxs-lookup"><span data-stu-id="36249-119">Example: Implement a non-pure function that changes a static class member</span></span>

<span data-ttu-id="36249-120">次のコードの `HyphenatedConcat` 関数は、`aMember` 静的クラス メンバーを変更するため、純粋関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="36249-120">In the following code, the `HyphenatedConcat` function isn't a pure function, because it modifies the `aMember` static class member:</span></span>

```csharp
public class Program
{
    private static string aMember = "StringOne";

    public static void HyphenatedConcat(string appendStr)
    {
        aMember += '-' + appendStr;
    }

    public static void Main()
    {
        HyphenatedConcat("StringTwo");
        Console.WriteLine(aMember);
    }
}
```

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="36249-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="36249-121">This example produces the following output:</span></span>

```output
StringOne-StringTwo
```

<span data-ttu-id="36249-122">この場合、変更されるデータに `public` アクセスと `private` アクセスのどちらがあるか、またはこのデータが `static` メンバー、`shared` メンバー、インスタンス メンバーのいずれかであるかは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="36249-122">Note that it's irrelevant whether the data being modified has `public` or `private` access, or is a `static` member, `shared` member, or instance member.</span></span> <span data-ttu-id="36249-123">純粋関数は、関数の外部にあるデータを一切変更しません。</span><span class="sxs-lookup"><span data-stu-id="36249-123">A pure function doesn't change any data outside of the function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-parameter"></a><span data-ttu-id="36249-124">例: パラメーターを変更する非純粋関数を実装する</span><span class="sxs-lookup"><span data-stu-id="36249-124">Example: Implement a non-pure function that changes a parameter</span></span>

<span data-ttu-id="36249-125">同じ関数の次のバージョンは、そのパラメーターである `sb` の内容を変更するため、純粋関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="36249-125">Furthermore, the following version of this same function isn't pure because it modifies the contents of its parameter, `sb`.</span></span>

```csharp
public class Program
{
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)
    {
        sb.Append('-' + appendStr);
    }

    public static void Main()
    {
        StringBuilder sb1 = new StringBuilder("StringOne");
        HyphenatedConcat(sb1, "StringTwo");
        Console.WriteLine(sb1);
    }
}
```

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="36249-126">このバージョンのプログラムは、最初のバージョンと同じ出力を生成します。これは、`HyphenatedConcat` 関数が <xref:System.Text.StringBuilder.Append%2A> メンバー関数を呼び出して最初のパラメーターの値 (状態) を変更したためです。</span><span class="sxs-lookup"><span data-stu-id="36249-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="36249-127">`HyphenatedConcat` はパラメーターを値で渡しますが、それでもこの変更は行われるのでご注意ください。</span><span class="sxs-lookup"><span data-stu-id="36249-127">Note that this alteration occurs despite the fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36249-128">参照型の場合、パラメーターを値で渡すと、渡されるオブジェクトへの参照がコピーされて渡されます。</span><span class="sxs-lookup"><span data-stu-id="36249-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="36249-129">このコピーは、参照変数が新しいオブジェクトに割り当てられるまで、元の参照と同じインスタンス データに関連付けられたままとなります。</span><span class="sxs-lookup"><span data-stu-id="36249-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="36249-130">パラメーターを変更する場合に、必ずしも関数に参照を渡す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="36249-130">Call-by-reference isn't necessarily required for a function to modify a parameter.</span></span>

## <a name="example-implement-a-pure-function"></a><span data-ttu-id="36249-131">例: 純粋関数の実装</span><span class="sxs-lookup"><span data-stu-id="36249-131">Example: Implement a pure function</span></span>

<span data-ttu-id="36249-132">次のバージョンのプログラムは、`HyphenatedConcat` 関数を純粋関数として実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="36249-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```csharp
class Program
{
    public static string HyphenatedConcat(string s, string appendStr)
    {
        return (s + '-' + appendStr);
    }

    public static void Main(string[] args)
    {
        string s1 = "StringOne";
        string s2 = HyphenatedConcat(s1, "StringTwo");
        Console.WriteLine(s2);
    }
}
```

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="36249-133">このバージョンも、同じ出力行 `StringOne-StringTwo` を生成します。</span><span class="sxs-lookup"><span data-stu-id="36249-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="36249-134">この連結された値を保持するために、中間変数 `s2` が使用されていることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="36249-134">Note that to retain the concatenated value, it's stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="36249-135">ローカルには純粋ではないが (つまりローカル変数を宣言して変更する)、グローバルには純粋である関数を作成すると、非常に便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="36249-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="36249-136">このような関数は、必要に応じて構成できる特性を多く備えていますが、関数型プログラミングの複雑な表現方法の一部 (単純なループによる処理を行う場合は再帰を使用する必要があるなど) が省かれています。</span><span class="sxs-lookup"><span data-stu-id="36249-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="36249-137">標準クエリ演算子</span><span class="sxs-lookup"><span data-stu-id="36249-137">Standard query operators</span></span>

<span data-ttu-id="36249-138">標準クエリ演算子の重要な特性は、純粋関数として実装される点です。</span><span class="sxs-lookup"><span data-stu-id="36249-138">An important characteristic of the standard query operators is that they're implemented as pure functions.</span></span>

<span data-ttu-id="36249-139">詳細については、「[標準クエリ演算子の概要 (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)」と「[標準クエリ演算子の概要 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36249-139">For more information, see [Standard Query Operators Overview (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) and [Standard Query Operators Overview (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36249-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="36249-140">See also</span></span>

- [<span data-ttu-id="36249-141">純粋関数型変換の概要</span><span class="sxs-lookup"><span data-stu-id="36249-141">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="36249-142">関数型プログラミングと命令型プログラミング</span><span class="sxs-lookup"><span data-stu-id="36249-142">Functional programming vs. imperative programming</span></span>](functional-vs-imperative-programming.md)
