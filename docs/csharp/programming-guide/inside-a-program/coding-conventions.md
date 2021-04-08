---
title: C# のコーディング規則 - C# プログラミング ガイド
description: C# のコーディング規則について説明します。 コーディング規則によってコードの外観に一貫性がもたらされ、コードのコピー、変更、保守が容易になります。
ms.date: 03/31/2021
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.openlocfilehash: 019bf02ea3cdfec2c4ae0d73b5b375781c5fcd9a
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231324"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="3c77e-104">C# のコーディング規則 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3c77e-104">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="3c77e-105">コーディング規則には、次の目的があります。</span><span class="sxs-lookup"><span data-stu-id="3c77e-105">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="3c77e-106">コードの見た目が統一されるため、コードを読むときに、レイアウトではなく内容に重点を置くことができます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="3c77e-107">これにより、経験に基づいて推測することで、コードをより迅速に理解することができます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="3c77e-108">コードのコピー、変更、および保守が容易になります。</span><span class="sxs-lookup"><span data-stu-id="3c77e-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="3c77e-109">コーディング規約により、C# のベスト プラクティスがわかります。</span><span class="sxs-lookup"><span data-stu-id="3c77e-109">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="3c77e-110">この記事のガイドラインは、サンプルおよびドキュメントを開発するために Microsoft によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-110">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="3c77e-111">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="3c77e-111">Naming conventions</span></span>  
  
- <span data-ttu-id="3c77e-112">[using ディレクティブ](../../language-reference/keywords/using-directive.md)が含まれていない簡単な例では、名前空間の修飾を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-112">In short examples that don't include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="3c77e-113">プロジェクトに名前空間が既定でインポートされていることがわかっている場合は、その名前空間の各名前を完全修飾する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3c77e-113">If you know that a namespace is imported by default in a project, you don't have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="3c77e-114">次の例に示すように、修飾名が長すぎて 1 行に収まらない場合は、ドット (.) の後で改行できます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-114">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet1":::

- <span data-ttu-id="3c77e-115">他のガイドラインに合わせて、Visual Studio デザイナーのツールを使用して作成されたオブジェクトの名前を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3c77e-115">You don't have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="3c77e-116">レイアウト規則</span><span class="sxs-lookup"><span data-stu-id="3c77e-116">Layout conventions</span></span>  

<span data-ttu-id="3c77e-117">コードの構造を強調する書式が使用され、コードが読みやすくなっているのが、優れたレイアウトです。</span><span class="sxs-lookup"><span data-stu-id="3c77e-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="3c77e-118">マイクロソフトの例とサンプルは、次の規則に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="3c77e-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="3c77e-119">コード エディターの既定の設定 (スマート インデント、4 文字インデント、タブを空白として保存) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="3c77e-120">詳細については、「[[オプション]、[テキスト エディター]、[C#]、[書式設定]](/visualstudio/ide/reference/options-text-editor-csharp-formatting)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="3c77e-121">1 つの行には 1 つのステートメントのみを記述します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-121">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="3c77e-122">1 つの行には 1 つの宣言のみを記述します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-122">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="3c77e-123">継続行にインデントが自動的に設定されない場合は、1 タブ ストップ (4 つの空白) 分のインデントを設定します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="3c77e-124">メソッド定義とプロパティ定義の間に少なくとも 1 行の空白行を追加します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="3c77e-125">次のコードに示すように、式に句を作成するときはかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet2":::

## <a name="commenting-conventions"></a><span data-ttu-id="3c77e-126">コメント規則</span><span class="sxs-lookup"><span data-stu-id="3c77e-126">Commenting conventions</span></span>  
  
- <span data-ttu-id="3c77e-127">コメントは、コード行の末尾ではなく別の行に記述します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-127">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="3c77e-128">コメントのテキストは大文字で開始します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-128">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="3c77e-129">コメントのテキストはピリオドで終了します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-129">End comment text with a period.</span></span>  
  
- <span data-ttu-id="3c77e-130">次の例に示すように、コメント デリミター (//) とコメント テキストの間に空白を 1 つ挿入します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-130">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet3":::

- <span data-ttu-id="3c77e-131">アスタリスクを整形したブロックでコメントを囲まないようにします。</span><span class="sxs-lookup"><span data-stu-id="3c77e-131">Don't create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="3c77e-132">言語ガイドライン</span><span class="sxs-lookup"><span data-stu-id="3c77e-132">Language guidelines</span></span>  

<span data-ttu-id="3c77e-133">以降のセクションでは、コード例とサンプルを準備する際に C# チームが従っている方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-133">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="3c77e-134">文字列データ型</span><span class="sxs-lookup"><span data-stu-id="3c77e-134">String data type</span></span>  
  
- <span data-ttu-id="3c77e-135">次のコードに示すように、短い文字列を連結するときは[文字列補間](../../language-reference/tokens/interpolated.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-135">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet6":::

- <span data-ttu-id="3c77e-136">ループ内で文字列を追加する場合 (特に大量のテキストを処理する場合) は、<xref:System.Text.StringBuilder> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-136">To append strings in loops, especially when you're working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="3c77e-137">暗黙的に型指定されたローカル変数</span><span class="sxs-lookup"><span data-stu-id="3c77e-137">Implicitly typed local variables</span></span>  
  
- <span data-ttu-id="3c77e-138">変数の型が割り当ての右側から明らかである場合、または厳密な型が重要でない場合は、ローカル変数の[暗黙の型指定](../classes-and-structs/implicitly-typed-local-variables.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-138">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet8":::
  
- <span data-ttu-id="3c77e-139">割り当ての右側から型が明らかではない場合、[var](../../language-reference/keywords/var.md) を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-139">Don't use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span> <span data-ttu-id="3c77e-140">メソッド名から型が明らかであると想定しないでください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-140">Don't assume the type is clear from a method name.</span></span> <span data-ttu-id="3c77e-141">変数の型は、`new` 演算子または明示的なキャストの場合に明らかであると見なされます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-141">A variable type is considered clear if it's a `new` operator or an explicit cast.</span></span>
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet9":::

- <span data-ttu-id="3c77e-142">変数の型を指定するときに変数名に頼らないでください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-142">Don't rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="3c77e-143">変数名が正しくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c77e-143">It might not be correct.</span></span> <span data-ttu-id="3c77e-144">次の例で、変数名 `inputInt` は誤解を招きます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-144">In the following example, the variable name `inputInt` is misleading.</span></span> <span data-ttu-id="3c77e-145">文字列です。</span><span class="sxs-lookup"><span data-stu-id="3c77e-145">It's a string.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet10":::

- <span data-ttu-id="3c77e-146">[dynamic](../../language-reference/builtin-types/reference-types.md) の代わりに `var` を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-146">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span> <span data-ttu-id="3c77e-147">`dynamic` は、実行時の型の推定が必要な場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-147">Use `dynamic` when you want run-time type inference.</span></span> <span data-ttu-id="3c77e-148">詳細については、「[dynamic 型の使用 (C# プログラミングガイド)](../types/using-type-dynamic.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-148">For more information, see [Using type dynamic (C# Programming Guide)](../types/using-type-dynamic.md).</span></span>
  
- <span data-ttu-id="3c77e-149">[for](../../language-reference/keywords/for.md) ループでループ変数の型を決定するときは、暗黙の型指定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-149">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
  <span data-ttu-id="3c77e-150">次の例では、`for` ステートメントで暗黙の型指定を使用しています。</span><span class="sxs-lookup"><span data-stu-id="3c77e-150">The following example uses implicit typing in a `for` statement.</span></span>  

    :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

- <span data-ttu-id="3c77e-151">[foreach](../../language-reference/keywords/foreach-in.md) ループでループ変数の型を決定するときは、暗黙の型指定は使用されません。</span><span class="sxs-lookup"><span data-stu-id="3c77e-151">Don't use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

  <span data-ttu-id="3c77e-152">次の例では、`foreach` ステートメントで暗黙の型指定が使用されています。</span><span class="sxs-lookup"><span data-stu-id="3c77e-152">The following example uses explicit typing in a `foreach` statement.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet12":::

  > [!NOTE]
  > <span data-ttu-id="3c77e-153">反復可能コレクションの要素の型を誤って変更しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-153">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="3c77e-154">たとえば、`foreach` ステートメントで <xref:System.Linq.IQueryable?displayProperty=nameWithType> から <xref:System.Collections.IEnumerable?displayProperty=nameWithType> に切り替えるのは簡単ですが、これを行うとクエリの結果が変更されます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-154">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-types"></a><span data-ttu-id="3c77e-155">unsigned データ型</span><span class="sxs-lookup"><span data-stu-id="3c77e-155">Unsigned data types</span></span>  
  
<span data-ttu-id="3c77e-156">通常は、unsigned 型ではなく `int` を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-156">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="3c77e-157">C# では `int` を使用するのが一般的です。`int` を使用すると、他のライブラリと対話しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="3c77e-157">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="3c77e-158">配列</span><span class="sxs-lookup"><span data-stu-id="3c77e-158">Arrays</span></span>  
  
<span data-ttu-id="3c77e-159">宣言行で配列を初期化するときは簡潔な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-159">Use the concise syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="3c77e-160">次の例では、`string[]` の代わりに `var` を使用できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-160">In the following example, note that you can't use `var` instead of `string[]`.</span></span>  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13a":::

<span data-ttu-id="3c77e-161">明示的なインスタンス化を使用する場合は、`var` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-161">If you use explicit instantiation, you can use `var`.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13b":::

<span data-ttu-id="3c77e-162">配列のサイズを指定する場合は、1 つずつ要素を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c77e-162">If you specify an array size, you have to initialize the elements one at a time.</span></span>
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13c":::
  
### <a name="delegates"></a><span data-ttu-id="3c77e-163">代理人</span><span class="sxs-lookup"><span data-stu-id="3c77e-163">Delegates</span></span>  
  
<span data-ttu-id="3c77e-164">デリゲート型を定義する代わりに [`Func<>` と `Action<>`](../../../standard/delegates-lambdas.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-164">Use [`Func<>` and `Action<>`](../../../standard/delegates-lambdas.md) instead of defining delegate types.</span></span> <span data-ttu-id="3c77e-165">クラスで、デリゲート メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-165">In a class, define the delegate method.</span></span>  

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14a":::

<span data-ttu-id="3c77e-166">`Func<>` または `Action<>` デリゲートで定義されているシグネチャを使用してメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-166">Call the method using the signature defined by the `Func<>` or `Action<>` delegate.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15a":::

<span data-ttu-id="3c77e-167">デリゲート型のインスタンスを作成する場合、簡潔な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-167">If you create instances of a delegate type, use the concise syntax.</span></span> <span data-ttu-id="3c77e-168">クラスで、デリゲート型および一致するシグネチャを持つメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-168">In a class, define the delegate type and a method that has a matching signature.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14b":::

<span data-ttu-id="3c77e-169">デリゲート型のインスタンスを作成し、それを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-169">Create an instance of the delegate type and call it.</span></span> <span data-ttu-id="3c77e-170">次の宣言は、短縮した構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="3c77e-170">The following declaration shows the condensed syntax.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15b":::

<span data-ttu-id="3c77e-171">次の宣言は、完全な構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="3c77e-171">The following declaration uses the full syntax.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15c":::

### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="3c77e-172">例外処理での `try`-`catch` および `using` ステートメント</span><span class="sxs-lookup"><span data-stu-id="3c77e-172">`try`-`catch` and `using` statements in exception handling</span></span>  
  
- <span data-ttu-id="3c77e-173">ほとんどの例外処理には、[try-catch](../../language-reference/keywords/try-catch.md) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-173">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet16":::

- <span data-ttu-id="3c77e-174">C# の [using ステートメント](../../language-reference/keywords/using-statement.md)を使用して、コードを簡潔にします。</span><span class="sxs-lookup"><span data-stu-id="3c77e-174">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="3c77e-175">[try-finally](../../language-reference/keywords/try-finally.md) ステートメントを使用するときに `finally` ブロックのコードが <xref:System.IDisposable.Dispose%2A> メソッドの呼び出しだけである場合は、`using` ステートメントを代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-175">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>

  <span data-ttu-id="3c77e-176">次の例で、`try`-`finally` ステートメントは `finally` ブロックでのみ `Dispose` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-176">In the following example, the `try`-`finally` statement only calls `Dispose` in the `finally` block.</span></span>
  
   :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17a":::

  <span data-ttu-id="3c77e-177">`using` ステートメントを使用して同じことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-177">You can do the same thing with a `using` statement.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17b":::

  <span data-ttu-id="3c77e-178">C# 8 以降のバージョンでは、中かっこを必要としない新しい [`using` 構文](../../language-reference/keywords/using-statement.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-178">In C# 8 and later versions, use the new [`using` syntax](../../language-reference/keywords/using-statement.md) that doesn't require braces:</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17c":::

### <a name="-and--operators"></a><span data-ttu-id="3c77e-179">`&&` 演算子と `||` 演算子</span><span class="sxs-lookup"><span data-stu-id="3c77e-179">`&&` and `||` operators</span></span>  
  
<span data-ttu-id="3c77e-180">例外を回避し、不要な比較をスキップしてパフォーマンスを向上させるには、比較を実行する場合、次の例に示すように [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) の代わりに [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) を、[`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) の代わりに [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-180">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet18":::

<span data-ttu-id="3c77e-181">除数が 0 の場合、`if` ステートメント内の 2 番目の句によって実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-181">If the divisor is 0, the second clause in the `if` statement would cause a run-time error.</span></span> <span data-ttu-id="3c77e-182">ただし、最初の式が false の場合、&& 演算子はショートサーキットされます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-182">But the && operator short-circuits when the first expression is false.</span></span> <span data-ttu-id="3c77e-183">つまり、2 番目の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="3c77e-183">That is, it doesn't evaluate the second expression.</span></span> <span data-ttu-id="3c77e-184">& 演算子は両方を評価し、`divisor` が 0 の場合は実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-184">The & operator would evaluate both, resulting in a run-time error when `divisor` is 0.</span></span>
  
### <a name="new-operator"></a><span data-ttu-id="3c77e-185">`new` 演算子</span><span class="sxs-lookup"><span data-stu-id="3c77e-185">`new` operator</span></span>  
  
- <span data-ttu-id="3c77e-186">次の宣言に示すように、オブジェクトのインスタンス化の簡潔な形式のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-186">Use one of the concise forms of object instantiation, as shown in the following declarations.</span></span> <span data-ttu-id="3c77e-187">2 番目の例は、C# 9 以降で使用できる構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="3c77e-187">The second example shows syntax that is available starting in C# 9.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet19":::
  
  ```csharp
  ExampleClass instance2 = new();
  ```
  
  <span data-ttu-id="3c77e-188">上記の宣言は次の宣言と同等です。</span><span class="sxs-lookup"><span data-stu-id="3c77e-188">The preceding declarations are equivalent to the following declaration.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet20":::

- <span data-ttu-id="3c77e-189">次の例に示すように、オブジェクト初期化子を使用してオブジェクトの作成を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-189">Use object initializers to simplify object creation, as shown in the following example.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21a":::

  <span data-ttu-id="3c77e-190">次の例では、前の例と同じプロパティを設定しますが、初期化子を使用しません。</span><span class="sxs-lookup"><span data-stu-id="3c77e-190">The following example sets the same properties as the preceding example but doesn't use initializers.</span></span>
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21b":::

### <a name="event-handling"></a><span data-ttu-id="3c77e-191">イベント処理</span><span class="sxs-lookup"><span data-stu-id="3c77e-191">Event handling</span></span>  
  
<span data-ttu-id="3c77e-192">後で削除する必要のないイベント ハンドラーを定義する場合は、ラムダ式を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-192">If you're defining an event handler that you don't need to remove later, use a lambda expression.</span></span>  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet22":::

<span data-ttu-id="3c77e-193">ラムダ式では、次の従来の定義を短縮します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-193">The lambda expression shortens the following traditional definition.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet23":::

### <a name="static-members"></a><span data-ttu-id="3c77e-194">静的メンバー</span><span class="sxs-lookup"><span data-stu-id="3c77e-194">Static members</span></span>  
  
<span data-ttu-id="3c77e-195">[静的](../../language-reference/keywords/static.md)メンバーは、クラス名 *ClassName.StaticMember* を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-195">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="3c77e-196">こうすることで、静的アクセスが明確になり、コードがよりわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="3c77e-196">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="3c77e-197">派生クラスの名前を持つ基本クラスに定義された静的メンバーを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-197">Don't qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="3c77e-198">このコードをコンパイルすると、コードが読みやすくなくなり、派生クラスに同じ名前の静的メンバーを追加すると、将来的にコードが中断する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c77e-198">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="3c77e-199">LINQ クエリ</span><span class="sxs-lookup"><span data-stu-id="3c77e-199">LINQ queries</span></span>  
  
- <span data-ttu-id="3c77e-200">クエリ変数にはわかりやすい名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-200">Use meaningful names for query variables.</span></span> <span data-ttu-id="3c77e-201">次の例では、シアトル在住の顧客に `seattleCustomers` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="3c77e-201">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- <span data-ttu-id="3c77e-202">エイリアスを使用して、匿名型のプロパティ名の大文字と小文字の使用が正しい Pascal 形式になるようにします。</span><span class="sxs-lookup"><span data-stu-id="3c77e-202">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet26":::

- <span data-ttu-id="3c77e-203">結果のプロパティ名があいまいになる場合は、プロパティ名を変更します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-203">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="3c77e-204">たとえば、クエリで顧客名と販売店 ID を返す場合、クエリ結果で `Name` と `ID` をそのまま使用するのではなく、これらの名前を変更し、`Name` が顧客の名前であり、`ID` が販売店の ID であることを明確にします。</span><span class="sxs-lookup"><span data-stu-id="3c77e-204">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet27":::

- <span data-ttu-id="3c77e-205">クエリ変数と範囲変数の宣言で暗黙の型指定を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-205">Use implicit typing in the declaration of query variables and range variables.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- <span data-ttu-id="3c77e-206">前の例に示すように、クエリ句を [from](../../language-reference/keywords/from-clause.md) 句の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-206">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  

- <span data-ttu-id="3c77e-207">[where](../../language-reference/keywords/where-clause.md) 句を他のクエリ句より先に使用し、それ以降のクエリ句では、フィルター化されたデータセットが処理されるようにします。</span><span class="sxs-lookup"><span data-stu-id="3c77e-207">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet29":::

- <span data-ttu-id="3c77e-208">内部コレクションにアクセスするには、[join](../../language-reference/keywords/join-clause.md) 句ではなく複数の `from` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c77e-208">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="3c77e-209">たとえば、`Student` オブジェクトのコレクションがあり、各オブジェクトに試験の点数のコレクションが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="3c77e-209">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="3c77e-210">次のクエリを実行すると、90 点より高い点数とその点数を取った学生の姓が返されます。</span><span class="sxs-lookup"><span data-stu-id="3c77e-210">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet30":::

## <a name="security"></a><span data-ttu-id="3c77e-211">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3c77e-211">Security</span></span>  

<span data-ttu-id="3c77e-212">「[安全なコーディングのガイドライン](../../../standard/security/secure-coding-guidelines.md)」のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="3c77e-212">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c77e-213">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c77e-213">See also</span></span>

- [<span data-ttu-id="3c77e-214">.NET ランタイム コーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3c77e-214">.NET runtime coding guidelines</span></span>](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
- [<span data-ttu-id="3c77e-215">Visual Basic のコーディング規則</span><span class="sxs-lookup"><span data-stu-id="3c77e-215">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="3c77e-216">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3c77e-216">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
