---
description: '詳細情報: Partial (Visual Basic)'
title: Partial
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: bf2d8b06b83f4a90ec2f4edd52405b58695c26e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701015"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="4274b-103">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4274b-103">Partial (Visual Basic)</span></span>

<span data-ttu-id="4274b-104">型宣言が、型の部分定義であることを示します。</span><span class="sxs-lookup"><span data-stu-id="4274b-104">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="4274b-105">`Partial` キーワードを使用して、型の定義を複数の宣言に分割できます。</span><span class="sxs-lookup"><span data-stu-id="4274b-105">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="4274b-106">部分宣言は必要に応じていくつでも使用でき、複数のソース ファイルとして作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4274b-106">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="4274b-107">ただし、すべての宣言は同じアセンブリおよび同じ名前空間にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="4274b-107">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4274b-108">Visual Basic では、*部分メソッド* をサポートしています。このメソッドは通常、部分クラスに実装されています。</span><span class="sxs-lookup"><span data-stu-id="4274b-108">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="4274b-109">詳細については、「[部分メソッド](../../programming-guide/language-features/procedures/partial-methods.md)」および「[Sub ステートメント](../statements/sub-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-109">For more information, see [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4274b-110">構文</span><span class="sxs-lookup"><span data-stu-id="4274b-110">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="4274b-111">指定項目</span><span class="sxs-lookup"><span data-stu-id="4274b-111">Parts</span></span>  
  
|<span data-ttu-id="4274b-112">用語</span><span class="sxs-lookup"><span data-stu-id="4274b-112">Term</span></span>|<span data-ttu-id="4274b-113">定義</span><span class="sxs-lookup"><span data-stu-id="4274b-113">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="4274b-114">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-114">Optional.</span></span> <span data-ttu-id="4274b-115">この型に適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="4274b-115">List of attributes that apply to this type.</span></span> <span data-ttu-id="4274b-116">[属性リスト](../statements/attribute-list.md)は山かっこ (`< >`) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="4274b-116">You must enclose the [Attribute List](../statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="4274b-117">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-117">Optional.</span></span> <span data-ttu-id="4274b-118">どのようなコードから型にアクセスできるのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4274b-118">Specifies what code can access this type.</span></span> <span data-ttu-id="4274b-119">「 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-119">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="4274b-120">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-120">Optional.</span></span> <span data-ttu-id="4274b-121">「[Shadows](shadows.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-121">See [Shadows](shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="4274b-122">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-122">Optional.</span></span> <span data-ttu-id="4274b-123">「[MustInherit](mustinherit.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-123">See [MustInherit](mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="4274b-124">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-124">Optional.</span></span> <span data-ttu-id="4274b-125">「[NotInheritable](notinheritable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-125">See [NotInheritable](notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="4274b-126">必須です。</span><span class="sxs-lookup"><span data-stu-id="4274b-126">Required.</span></span> <span data-ttu-id="4274b-127">この型の名前です。</span><span class="sxs-lookup"><span data-stu-id="4274b-127">Name of this type.</span></span> <span data-ttu-id="4274b-128">同じ型の他のすべての部分宣言で定義されている名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4274b-128">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="4274b-129">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-129">Optional.</span></span> <span data-ttu-id="4274b-130">これがジェネリック型であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="4274b-130">Specifies that this is a generic type.</span></span> <span data-ttu-id="4274b-131">「[Visual Basic におけるジェネリック型](../../programming-guide/language-features/data-types/generic-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-131">See [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="4274b-132">[Of](../statements/of-clause.md) を使用する場合は必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="4274b-132">Required if you use [Of](../statements/of-clause.md).</span></span> <span data-ttu-id="4274b-133">「[型リスト](../statements/type-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-133">See [Type List](../statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="4274b-134">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-134">Optional.</span></span> <span data-ttu-id="4274b-135">「[Inherits ステートメント](../statements/inherits-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-135">See [Inherits Statement](../statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="4274b-136">`Inherits` を使用する場合は必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="4274b-136">Required if you use `Inherits`.</span></span> <span data-ttu-id="4274b-137">このクラスの派生元のクラスまたはインターフェイスの名前です。</span><span class="sxs-lookup"><span data-stu-id="4274b-137">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="4274b-138">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-138">Optional.</span></span> <span data-ttu-id="4274b-139">「[Implements ステートメント](../statements/implements-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-139">See [Implements Statement](../statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="4274b-140">`Implements` を使用する場合は必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="4274b-140">Required if you use `Implements`.</span></span> <span data-ttu-id="4274b-141">この型が実装するインターフェイスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4274b-141">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="4274b-142">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-142">Optional.</span></span> <span data-ttu-id="4274b-143">この型の追加の変数やイベントを宣言するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4274b-143">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="4274b-144">任意。</span><span class="sxs-lookup"><span data-stu-id="4274b-144">Optional.</span></span> <span data-ttu-id="4274b-145">この型の追加のプロシージャを宣言および定義するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4274b-145">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="4274b-146">`End Class` または `End Structure`</span><span class="sxs-lookup"><span data-stu-id="4274b-146">`End Class` or `End Structure`</span></span>|<span data-ttu-id="4274b-147">この `Class` または `Structure` の部分定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="4274b-147">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4274b-148">Remarks</span><span class="sxs-lookup"><span data-stu-id="4274b-148">Remarks</span></span>  

 <span data-ttu-id="4274b-149">Visual Basic では、部分クラス定義を使用して、生成されたコードとユーザーが作成したコードとを別々のソース ファイルに分離します。</span><span class="sxs-lookup"><span data-stu-id="4274b-149">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="4274b-150">たとえば、**Windows フォーム デザイナー** では、<xref:System.Windows.Forms.Form> などのコントロールに部分クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="4274b-150">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="4274b-151">これらのコントロールでは、生成されたコードを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="4274b-151">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="4274b-152">部分型を作成する際、クラス、構造体、インターフェイス、およびモジュールの作成に関するすべての規則 (修飾子の利用法や継承に関する規則など) が適用されます。</span><span class="sxs-lookup"><span data-stu-id="4274b-152">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="4274b-153">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="4274b-153">Best Practices</span></span>  
  
- <span data-ttu-id="4274b-154">通常の状況では、1 つの型の開発を複数の宣言に分割しないようにします。</span><span class="sxs-lookup"><span data-stu-id="4274b-154">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="4274b-155">したがって、ほとんどの場合は、`Partial` キーワードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4274b-155">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="4274b-156">読みやすくするために、型の部分宣言にはすべて、`Partial` キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="4274b-156">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="4274b-157">コンパイラでは、最大 1 つの部分宣言でキーワードを省略できますが、複数の部分宣言で省略するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="4274b-157">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4274b-158">動作</span><span class="sxs-lookup"><span data-stu-id="4274b-158">Behavior</span></span>  
  
- <span data-ttu-id="4274b-159">**宣言の共用体。**</span><span class="sxs-lookup"><span data-stu-id="4274b-159">**Union of Declarations.**</span></span> <span data-ttu-id="4274b-160">コンパイラは型を、すべての部分宣言の共用体として扱います。</span><span class="sxs-lookup"><span data-stu-id="4274b-160">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="4274b-161">すべての部分定義で使用されているすべての修飾子は、型全体に適用され、すべての部分定義のすべてのメンバーは、型全体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="4274b-161">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="4274b-162">**モジュール内の部分型は上位変換できません。**</span><span class="sxs-lookup"><span data-stu-id="4274b-162">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="4274b-163">部分定義がモジュール内にある場合、その型の上位変換は自動的に失敗します。</span><span class="sxs-lookup"><span data-stu-id="4274b-163">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="4274b-164">この場合、一連の部分定義によって、予期しない結果になったり、場合によってはコンパイラ エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="4274b-164">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="4274b-165">詳細については、「[型の上位変換](../../programming-guide/language-features/declared-elements/type-promotion.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4274b-165">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="4274b-166">コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。</span><span class="sxs-lookup"><span data-stu-id="4274b-166">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="4274b-167">キーワード `Partial` は次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4274b-167">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="4274b-168">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="4274b-168">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="4274b-169">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="4274b-169">Structure Statement</span></span>](../statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="4274b-170">例</span><span class="sxs-lookup"><span data-stu-id="4274b-170">Example</span></span>  

 <span data-ttu-id="4274b-171">次の例では、クラス `sampleClass` の定義を 2 つの宣言に分割し、それぞれ別の `Sub` プロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="4274b-171">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="4274b-172">この例にある 2 つの部分定義は、同じソース ファイル内にあっても、別々のソース ファイル内にあってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4274b-172">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4274b-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="4274b-173">See also</span></span>

- [<span data-ttu-id="4274b-174">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="4274b-174">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="4274b-175">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="4274b-175">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="4274b-176">型の上位変換</span><span class="sxs-lookup"><span data-stu-id="4274b-176">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="4274b-177">Shadows</span><span class="sxs-lookup"><span data-stu-id="4274b-177">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="4274b-178">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4274b-178">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="4274b-179">部分メソッド</span><span class="sxs-lookup"><span data-stu-id="4274b-179">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
