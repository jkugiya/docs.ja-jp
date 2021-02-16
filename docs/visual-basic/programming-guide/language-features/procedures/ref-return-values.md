---
description: '詳細情報: 参照戻り値のサポート (Visual Basic)'
title: 参照戻り値
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 215a647c68eb7eadd394a1a7842ceb98c46e04a5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466550"
---
# <a name="support-for-reference-return-values-visual-basic"></a><span data-ttu-id="bdd01-103">参照戻り値のサポート (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdd01-103">Support for reference return values (Visual Basic)</span></span>

<span data-ttu-id="bdd01-104">C# 7.0 以降の C# 言語では、"*参照戻り値*" がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bdd01-104">Starting with C# 7.0, the C# language supports *reference return values*.</span></span> <span data-ttu-id="bdd01-105">参照戻り値は、メソッドに参照渡しされる引数の逆と考えると理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bdd01-105">One way to understand reference return values is that they are the opposite of arguments that are passed by reference to a method.</span></span> <span data-ttu-id="bdd01-106">参照渡しされた引数が変更されると、変更は呼び出し元の変数の値に反映されます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-106">When an argument passed by reference is modified, the changes are reflected in value of the variable on the caller.</span></span> <span data-ttu-id="bdd01-107">メソッドが参照戻り値を呼び出し元に返すと、呼び出し元によって参照戻り値に加えられた変更が、呼び出されたメソッドのデータに反映されます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-107">When an method provides a reference return value to a caller, modifications made to the reference return value by the caller are reflected in the called method's data.</span></span>

<span data-ttu-id="bdd01-108">Visual Basic では、参照戻り値を使用するメソッドを作成することはできませんが、参照戻り値を使用することは可能です。</span><span class="sxs-lookup"><span data-stu-id="bdd01-108">Visual Basic does not allow you to author methods with reference return values, but it does allow you to consume reference return values.</span></span> <span data-ttu-id="bdd01-109">つまり、参照戻り値を使用してメソッドを呼び出し、その戻り値を変更できます。参照戻り値に対する変更は、呼び出されたメソッドのデータに反映されます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-109">In other words, you can call a method with a reference return value and modify that return value, and changes to the reference return value are reflected in the called method's data.</span></span>

## <a name="modifying-the-ref-return-value-directly"></a><span data-ttu-id="bdd01-110">参照戻り値を直接変更する</span><span class="sxs-lookup"><span data-stu-id="bdd01-110">Modifying the ref return value directly</span></span>

<span data-ttu-id="bdd01-111">常に成功し、`ByRef` パラメーターがないメソッドの場合、参照戻り値を直接変更できます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-111">For methods that always succeed and have no `ByRef` parameters, you can modify the reference return value directly.</span></span> <span data-ttu-id="bdd01-112">これを行うには、参照戻り値を返す式に新しい値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-112">You do this by assigning the new value to the expressions that returns the reference return value.</span></span>

<span data-ttu-id="bdd01-113">次の C# の例では、内部値をインクリメントし、それを参照戻り値として返す `NumericValue.IncrementValue` メソッドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="bdd01-113">The following C# example defines a `NumericValue.IncrementValue` method that increments an internal value and returns it as a reference return value.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

<span data-ttu-id="bdd01-114">次の Visual Basic の例では、この参照戻り値が呼び出し元によって変更されます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-114">The reference return value is then modified by the caller in the following Visual Basic example.</span></span> <span data-ttu-id="bdd01-115">`NumericValue.IncrementValue` メソッド呼び出しを含む行では、メソッドに値を割り当てていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bdd01-115">Note that the line with the `NumericValue.IncrementValue` method call does not assign a value to the method.</span></span> <span data-ttu-id="bdd01-116">代わりに、メソッドによって返される参照戻り値に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-116">Instead, it assigns a value to the reference return value returned by the method.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a><span data-ttu-id="bdd01-117">ヘルパー メソッドを使用する</span><span class="sxs-lookup"><span data-stu-id="bdd01-117">Using a helper method</span></span>

<span data-ttu-id="bdd01-118">メソッド呼び出しの参照戻り値を直接変更することが必ずしも望ましいとは限らない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bdd01-118">In other cases, modifying the reference return value of a method call directly may not always be desirable.</span></span> <span data-ttu-id="bdd01-119">たとえば、文字列を返す検索メソッドは、常に一致するものを見つけるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="bdd01-119">For example, a search method that returns a string may not always find a match.</span></span> <span data-ttu-id="bdd01-120">その場合、検索が成功した場合にのみ、参照戻り値を変更します。</span><span class="sxs-lookup"><span data-stu-id="bdd01-120">In that case, you want to modify the reference return value only if the search is successful.</span></span>

<span data-ttu-id="bdd01-121">次の C# の例はこのシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="bdd01-121">The following C# example illustrates this scenario.</span></span> <span data-ttu-id="bdd01-122">C# で記述された `Sentence` クラスを定義し、指定された部分文字列で始まる文の次の単語を検索する `FindNext` メソッドを含めます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-122">It defines a `Sentence` class written in C# includes a `FindNext` method that finds the next word in a sentence that begins with a specified substring.</span></span> <span data-ttu-id="bdd01-123">文字列は参照戻り値として返され、参照によりメソッドに渡される `Boolean` 変数は検索が成功したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="bdd01-123">The string is returned as a reference return value, and a `Boolean` variable passed by reference to the method indicates whether the search was successful.</span></span> <span data-ttu-id="bdd01-124">参照戻り値は、返された値を読み取るだけでなく、呼び出し元がそれを変更することもでき、その変更が `Sentence` クラスの内部に含まれるデータに反映されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="bdd01-124">The reference return value indicates that in addition to reading the returned value, the caller can also modify it, and that modification is reflected in the data contained internally in the `Sentence` class.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

<span data-ttu-id="bdd01-125">この例での参照戻り値の直接変更は信頼できません。メソッド呼び出しで一致するものが見つからず、文の最初の単語が返される可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="bdd01-125">Directly modifying the reference return value in this case is not reliable, since the method call may fail to find a match and return the first word in the sentence.</span></span> <span data-ttu-id="bdd01-126">その場合、呼び出し元は文の最初の単語を誤って変更することになります。</span><span class="sxs-lookup"><span data-stu-id="bdd01-126">In that case, the caller will inadvertently modify the first word of the sentence.</span></span> <span data-ttu-id="bdd01-127">これは、呼び出し元が `null` (Visual Basic では `Nothing`) を返すことによって防ぐことができる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bdd01-127">This could be prevented by the caller returning a `null` (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="bdd01-128">ただし、その場合、値が `Nothing` の文字列を変更しようとすると、<xref:System.NullReferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-128">But in that case, attempting to modify a string whose value is `Nothing` throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="bdd01-129">呼び出し元が <xref:System.String.Empty?displayProperty=nameWithType> を返すことによって防ぐことができる場合もありますが、そのためには、値が <xref:System.String.Empty?displayProperty=nameWithType> である文字列変数を呼び出し元で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd01-129">If could also be prevented by the caller returning <xref:System.String.Empty?displayProperty=nameWithType>, but this requires that the caller define a string variable whose value is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bdd01-130">呼び出し元はその文字列を変更できますが、変更された文字列は `Sentence` クラスによって格納された文の単語と関係がないため、変更自体に何の意味もありません。</span><span class="sxs-lookup"><span data-stu-id="bdd01-130">While the caller can modify that string, the modification itself serves no purpose, since the modified string has no relationship to the words in the sentence stored by the `Sentence` class.</span></span>

<span data-ttu-id="bdd01-131">このシナリオに対応する最良の方法は、ヘルパー メソッドに対して参照戻り値を参照渡しにすることです。</span><span class="sxs-lookup"><span data-stu-id="bdd01-131">The best way to handle this scenario is to pass the reference return value by reference to a helper method.</span></span> <span data-ttu-id="bdd01-132">ヘルパー メソッドには、メソッド呼び出しが成功したかどうかを判断し、成功した場合は参照戻り値を変更するロジックを含めます。</span><span class="sxs-lookup"><span data-stu-id="bdd01-132">The helper method then contains the logic to determine whether the method call succeeded and, if it did, to modify the reference return value.</span></span> <span data-ttu-id="bdd01-133">次の例は考えられる実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="bdd01-133">The following example provides a possible implementation.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a><span data-ttu-id="bdd01-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdd01-134">See also</span></span>

- [<span data-ttu-id="bdd01-135">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="bdd01-135">Passing arguments by value and by reference</span></span>](passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="bdd01-136">Visual Basic におけるプロシージャ</span><span class="sxs-lookup"><span data-stu-id="bdd01-136">Procedures in Visual Basic</span></span>](index.md)
