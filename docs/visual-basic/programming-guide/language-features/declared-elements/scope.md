---
description: '詳細情報: Visual Basic におけるスコープ'
title: スコープ
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 5b5412f5743162bb91fc3651d08f5c7ff9ba8abd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480207"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="54722-103">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="54722-103">Scope in Visual Basic</span></span>

<span data-ttu-id="54722-104">宣言された要素の *スコープ* は、その名前を修飾したり、[Imports ステートメント (.NET 名前空間および型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) から使用できるようにしたりしなくても、それを参照できるすべてのコードのセットです。</span><span class="sxs-lookup"><span data-stu-id="54722-104">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="54722-105">要素には、次のいずれかのレベルのスコープを設定できます。</span><span class="sxs-lookup"><span data-stu-id="54722-105">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="54722-106">レベル</span><span class="sxs-lookup"><span data-stu-id="54722-106">Level</span></span>|<span data-ttu-id="54722-107">説明</span><span class="sxs-lookup"><span data-stu-id="54722-107">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="54722-108">ブロック スコープ</span><span class="sxs-lookup"><span data-stu-id="54722-108">Block scope</span></span>|<span data-ttu-id="54722-109">それが宣言されているコード ブロック内でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="54722-109">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="54722-110">プロシージャ スコープ</span><span class="sxs-lookup"><span data-stu-id="54722-110">Procedure scope</span></span>|<span data-ttu-id="54722-111">それが宣言されているプロシージャ内のすべてのコードで使用可能</span><span class="sxs-lookup"><span data-stu-id="54722-111">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="54722-112">モジュール スコープ</span><span class="sxs-lookup"><span data-stu-id="54722-112">Module scope</span></span>|<span data-ttu-id="54722-113">それが宣言されているモジュール、クラス、または構造体内のすべてのコードで使用可能</span><span class="sxs-lookup"><span data-stu-id="54722-113">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="54722-114">名前空間スコープ</span><span class="sxs-lookup"><span data-stu-id="54722-114">Namespace scope</span></span>|<span data-ttu-id="54722-115">それが宣言されている名前空間内のすべてのコードで使用可能</span><span class="sxs-lookup"><span data-stu-id="54722-115">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="54722-116">これらのスコープのレベルは、最も狭い (ブロック) から最も広い (名前空間) まで進展します。ここで、*最も狭いスコープ* とは、修飾せずに要素を参照できる最小限のコードのセットを意味します。</span><span class="sxs-lookup"><span data-stu-id="54722-116">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="54722-117">詳細については、このページの「スコープのレベル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54722-117">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="54722-118">スコープの指定と変数の定義</span><span class="sxs-lookup"><span data-stu-id="54722-118">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="54722-119">要素のスコープは、それを宣言するときに指定します。</span><span class="sxs-lookup"><span data-stu-id="54722-119">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="54722-120">スコープは、次の要因によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="54722-120">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="54722-121">要素を宣言する領域 (ブロック、プロシージャ、モジュール、クラス、または構造体)</span><span class="sxs-lookup"><span data-stu-id="54722-121">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="54722-122">要素の宣言を含む名前空間</span><span class="sxs-lookup"><span data-stu-id="54722-122">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="54722-123">要素に対して宣言するアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="54722-123">The access level you declare for the element</span></span>

<span data-ttu-id="54722-124">同じ名前だがスコープが異なる変数を定義する場合は、それによって予期しない結果につながる可能性があるため、注意してください。</span><span class="sxs-lookup"><span data-stu-id="54722-124">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="54722-125">詳細については、「 [References to Declared Elements](references-to-declared-elements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54722-125">For more information, see [References to Declared Elements](references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="54722-126">スコープのレベル</span><span class="sxs-lookup"><span data-stu-id="54722-126">Levels of Scope</span></span>

<span data-ttu-id="54722-127">プログラミング要素は、それを宣言する領域全体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="54722-127">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="54722-128">同じリージョン内のすべてのコードでは、その名前を修飾せずに要素を参照できます。</span><span class="sxs-lookup"><span data-stu-id="54722-128">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="54722-129">ブロック スコープ</span><span class="sxs-lookup"><span data-stu-id="54722-129">Block Scope</span></span>

<span data-ttu-id="54722-130">ブロックは、次のように、開始と終了の宣言ステートメントに囲まれた一連のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="54722-130">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="54722-131">`Do` および `Loop`</span><span class="sxs-lookup"><span data-stu-id="54722-131">`Do` and `Loop`</span></span>

- <span data-ttu-id="54722-132">`For` [`Each`] および `Next`</span><span class="sxs-lookup"><span data-stu-id="54722-132">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="54722-133">`If` および `End If`</span><span class="sxs-lookup"><span data-stu-id="54722-133">`If` and `End If`</span></span>

- <span data-ttu-id="54722-134">`Select` および `End Select`</span><span class="sxs-lookup"><span data-stu-id="54722-134">`Select` and `End Select`</span></span>

- <span data-ttu-id="54722-135">`SyncLock` および `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="54722-135">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="54722-136">`Try` および `End Try`</span><span class="sxs-lookup"><span data-stu-id="54722-136">`Try` and `End Try`</span></span>

- <span data-ttu-id="54722-137">`While` および `End While`</span><span class="sxs-lookup"><span data-stu-id="54722-137">`While` and `End While`</span></span>

- <span data-ttu-id="54722-138">`With` および `End With`</span><span class="sxs-lookup"><span data-stu-id="54722-138">`With` and `End With`</span></span>

<span data-ttu-id="54722-139">ブロック内で変数を宣言すると、そのブロック内でのみそれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="54722-139">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="54722-140">次の例で、整数変数 `cube` のスコープは `If` と `End If` の間のブロックであるため、実行がブロックから出ると、`cube` を参照できなくなります。</span><span class="sxs-lookup"><span data-stu-id="54722-140">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="54722-141">変数のスコープがブロックに制限されている場合でも、その有効期間はプロシージャ全体の有効期間になります。</span><span class="sxs-lookup"><span data-stu-id="54722-141">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="54722-142">プロシージャの実行中にブロックに複数回入る場合、各ブロック変数で前の値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="54722-142">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="54722-143">そのような場合に予期しない結果を避けるには、ブロックの先頭でブロック変数を初期化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="54722-143">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="54722-144">プロシージャ スコープ</span><span class="sxs-lookup"><span data-stu-id="54722-144">Procedure Scope</span></span>

<span data-ttu-id="54722-145">プロシージャ内で宣言された要素は、そのプロシージャの外部で使用できません。</span><span class="sxs-lookup"><span data-stu-id="54722-145">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="54722-146">宣言を含むプロシージャだけがそれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="54722-146">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="54722-147">このレベルの変数は、*ローカル変数* とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="54722-147">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="54722-148">それらは、[Dim ステートメント](../../../language-reference/statements/dim-statement.md)で、[Static](../../../language-reference/modifiers/static.md) キーワードを付けるか、または付けないで、宣言します。</span><span class="sxs-lookup"><span data-stu-id="54722-148">You declare them with the [Dim Statement](../../../language-reference/statements/dim-statement.md), with or without the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="54722-149">プロシージャとブロックのスコープは密接に関連しています。</span><span class="sxs-lookup"><span data-stu-id="54722-149">Procedure and block scope are closely related.</span></span> <span data-ttu-id="54722-150">プロシージャ内の、ただしそのプロシージャ内のいずれかのブロックの外部で変数を宣言した場合、その変数はブロック スコープを持つと考えることができます。その場合ブロックはプロシージャ全体になります。</span><span class="sxs-lookup"><span data-stu-id="54722-150">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="54722-151">すべてのローカル要素は、`Static` 変数であっても、それらが存在するプロシージャに対してプライベートです。</span><span class="sxs-lookup"><span data-stu-id="54722-151">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="54722-152">プロシージャ内で [Public](../../../language-reference/modifiers/public.md) キーワードを使用して要素を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="54722-152">You cannot declare any element using the [Public](../../../language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="54722-153">モジュール スコープ</span><span class="sxs-lookup"><span data-stu-id="54722-153">Module Scope</span></span>

<span data-ttu-id="54722-154">便宜上、*モジュール レベル* という 1 つの用語は、モジュール、クラス、および構造体に等しく適用されます。</span><span class="sxs-lookup"><span data-stu-id="54722-154">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="54722-155">このレベルで要素を宣言するには、宣言ステートメントをプロシージャまたはブロックの外部で、ただしモジュール、クラス、または構造体内に配置します。</span><span class="sxs-lookup"><span data-stu-id="54722-155">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="54722-156">モジュール レベルで宣言を行うと、選択したアクセス レベルによってスコープが決まります。</span><span class="sxs-lookup"><span data-stu-id="54722-156">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="54722-157">モジュール、クラス、または構造体を含む名前空間もスコープに影響します。</span><span class="sxs-lookup"><span data-stu-id="54722-157">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="54722-158">[Private](../../../language-reference/modifiers/private.md) アクセス レベルを宣言した要素は、そのモジュール内のすべてのプロシージャで使用できますが、別のモジュール内のコードでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="54722-158">Elements for which you declare [Private](../../../language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="54722-159">アクセス レベル キーワードを使用しない場合、モジュール レベルの `Dim` ステートメントは既定で `Private` になります。</span><span class="sxs-lookup"><span data-stu-id="54722-159">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="54722-160">ただし、`Dim` ステートメントで `Private` キーワードを使用することで、スコープとアクセス レベルをより明確にすることができます。</span><span class="sxs-lookup"><span data-stu-id="54722-160">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="54722-161">次の例では、モジュールに定義されているすべてのプロシージャで、文字列変数 `strMsg` を参照できます。</span><span class="sxs-lookup"><span data-stu-id="54722-161">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="54722-162">2 番目のプロシージャを呼び出すと、ダイアログ ボックスに `strMsg` 文字列変数の内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="54722-162">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a><span data-ttu-id="54722-163">名前空間スコープ</span><span class="sxs-lookup"><span data-stu-id="54722-163">Namespace Scope</span></span>

<span data-ttu-id="54722-164">[Friend](../../../language-reference/modifiers/friend.md) または [Public](../../../language-reference/modifiers/public.md) キーワードを使用して、要素をモジュール レベルで宣言すると、その要素が宣言されている名前空間全体のすべてのプロシージャで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="54722-164">If you declare an element at module level using the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="54722-165">前の例を次のように変更すると、文字列変数 `strMsg` は、宣言の名前空間内の任意の場所でコードによって参照できます。</span><span class="sxs-lookup"><span data-stu-id="54722-165">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="54722-166">名前空間スコープには、入れ子になった名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="54722-166">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="54722-167">名前空間内から使用できる要素は、その名前空間内に入れ子になっているすべての名前空間内からも使用できます。</span><span class="sxs-lookup"><span data-stu-id="54722-167">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="54722-168">プロジェクトに [Namespace ステートメント](../../../language-reference/statements/namespace-statement.md) が含まれていない場合、プロジェクトのすべてのものが同じ名前空間内にあります。</span><span class="sxs-lookup"><span data-stu-id="54722-168">If your project does not contain any [Namespace Statement](../../../language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="54722-169">この場合、名前空間スコープはプロジェクト スコープと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="54722-169">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="54722-170">モジュール、クラス、または構造体内の `Public` 要素は、そのプロジェクトを参照するすべてのプロジェクトでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="54722-170">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="54722-171">スコープの選択</span><span class="sxs-lookup"><span data-stu-id="54722-171">Choice of Scope</span></span>

<span data-ttu-id="54722-172">変数を宣言する場合、そのスコープを選択するときに、次の点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54722-172">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="54722-173">ローカル変数の利点</span><span class="sxs-lookup"><span data-stu-id="54722-173">Advantages of Local Variables</span></span>

<span data-ttu-id="54722-174">ローカル変数は、次の理由で、あらゆる種類の一時的な計算に適しています。</span><span class="sxs-lookup"><span data-stu-id="54722-174">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="54722-175">**名前の競合の回避。**</span><span class="sxs-lookup"><span data-stu-id="54722-175">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="54722-176">ローカル変数名は競合する可能性がありません。</span><span class="sxs-lookup"><span data-stu-id="54722-176">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="54722-177">たとえば、`intTemp` という変数を含む複数の異なるプロシージャを作成できます。</span><span class="sxs-lookup"><span data-stu-id="54722-177">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="54722-178">各 `intTemp` がローカル変数として宣言されている限り、各プロシージャではその独自のバージョンの `intTemp` のみが認識されます。</span><span class="sxs-lookup"><span data-stu-id="54722-178">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="54722-179">他のプロシージャの `intTemp` 変数に影響を与えることなく、あるプロシージャで、そのローカル `intTemp` の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="54722-179">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="54722-180">**メモリの使用量。**</span><span class="sxs-lookup"><span data-stu-id="54722-180">**Memory Consumption.**</span></span> <span data-ttu-id="54722-181">ローカル変数は、プロシージャの実行中にのみメモリを消費します。</span><span class="sxs-lookup"><span data-stu-id="54722-181">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="54722-182">それらのメモリは、プロシージャが呼び出し元のコードに戻ったときに解放されます。</span><span class="sxs-lookup"><span data-stu-id="54722-182">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="54722-183">これに対し、[Shared](../../../language-reference/modifiers/shared.md) 変数と [Static](../../../language-reference/modifiers/static.md) 変数では、アプリケーションが実行を停止するまでメモリ リソースが消費されるため、必要な場合にのみそれらを使用してください。</span><span class="sxs-lookup"><span data-stu-id="54722-183">By contrast, [Shared](../../../language-reference/modifiers/shared.md) and [Static](../../../language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="54722-184">*インスタンス変数* では、それらのインスタンスが存在し続ける間メモリが消費されるので、ローカル変数よりも非効率的ですが、`Shared` または `Static` 変数よりも効率的である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="54722-184">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="54722-185">スコープの最小化</span><span class="sxs-lookup"><span data-stu-id="54722-185">Minimizing Scope</span></span>

<span data-ttu-id="54722-186">一般に、変数または定数を宣言するときは、スコープを可能な限り狭くすることをお勧めします (ブロック スコープが最も狭い)。</span><span class="sxs-lookup"><span data-stu-id="54722-186">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="54722-187">これにより、メモリを節約し、コードで間違った変数を誤って参照する可能性が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="54722-187">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="54722-188">同様に、プロシージャ呼び出しの間でその値を保持する必要がある場合にのみ、変数を [Static](../../../language-reference/modifiers/static.md) として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54722-188">Similarly, you should declare a variable to be [Static](../../../language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="54722-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="54722-189">See also</span></span>

- [<span data-ttu-id="54722-190">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="54722-190">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="54722-191">方法: 変数のスコープを制御する</span><span class="sxs-lookup"><span data-stu-id="54722-191">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="54722-192">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="54722-192">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="54722-193">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="54722-193">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="54722-194">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="54722-194">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="54722-195">変数宣言</span><span class="sxs-lookup"><span data-stu-id="54722-195">Variable Declaration</span></span>](../variables/variable-declaration.md)
