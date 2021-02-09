---
description: '詳細情報: Imports ステートメント (.NET 名前空間および型)'
title: Imports ステートメント - .NET 名前空間および型
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 28b7608e250fdba9c39f0209154d5a3d8f725eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768975"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="2d433-103">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="2d433-103">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="2d433-104">名前空間の修飾なしで型名を参照できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-104">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d433-105">構文</span><span class="sxs-lookup"><span data-stu-id="2d433-105">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="2d433-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="2d433-106">Parts</span></span>

|<span data-ttu-id="2d433-107">用語</span><span class="sxs-lookup"><span data-stu-id="2d433-107">Term</span></span>|<span data-ttu-id="2d433-108">定義</span><span class="sxs-lookup"><span data-stu-id="2d433-108">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="2d433-109">任意。</span><span class="sxs-lookup"><span data-stu-id="2d433-109">Optional.</span></span> <span data-ttu-id="2d433-110">コードで完全修飾文字列の代わりに `namespace` を参照できる *インポート エイリアス* または名前。</span><span class="sxs-lookup"><span data-stu-id="2d433-110">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="2d433-111">「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d433-111">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="2d433-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="2d433-112">Required.</span></span> <span data-ttu-id="2d433-113">インポートする名前空間の完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="2d433-113">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="2d433-114">任意のレベルに入れ子になった名前空間の文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-114">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="2d433-115">任意。</span><span class="sxs-lookup"><span data-stu-id="2d433-115">Optional.</span></span> <span data-ttu-id="2d433-116">名前空間に宣言されているプログラミング要素の名前。</span><span class="sxs-lookup"><span data-stu-id="2d433-116">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="2d433-117">任意のコンテナー要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-117">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2d433-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="2d433-118">Remarks</span></span>

<span data-ttu-id="2d433-119">`Imports` ステートメントを使用すると、特定の名前空間に含まれている型を直接参照できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-119">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="2d433-120">1 つの名前空間名または入れ子になった名前空間の文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-120">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="2d433-121">次の例に示すように、入れ子になった各名前空間は、ピリオド (`.`) で次の上位の名前空間と区別します。</span><span class="sxs-lookup"><span data-stu-id="2d433-121">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="2d433-122">各ソース ファイルには、任意の数の `Imports` ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2d433-122">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="2d433-123">これらは、`Option Strict` ステートメントなど、任意のオプションの宣言の後に続く必要があり、`Module` や `Class` ステートメントなどのプログラミング要素の宣言の前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d433-123">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="2d433-124">`Imports` は、ファイル レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-124">You can use `Imports` only at file level.</span></span> <span data-ttu-id="2d433-125">つまり、インポートの宣言コンテキストはソース ファイルである必要があり、名前空間、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックでは宣言できません。</span><span class="sxs-lookup"><span data-stu-id="2d433-125">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="2d433-126">`Imports` ステートメントによって、他のプロジェクトおよびアセンブリの要素をプロジェクトで使用できなくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2d433-126">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="2d433-127">インポートは、参照の設定の代わりになりません。</span><span class="sxs-lookup"><span data-stu-id="2d433-127">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="2d433-128">これにより、プロジェクトで既に使用可能な名前を修飾する必要がなくなるだけです。</span><span class="sxs-lookup"><span data-stu-id="2d433-128">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="2d433-129">詳細については、「[宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の "コンテナー要素のインポート" に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d433-129">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2d433-130">暗黙的な `Imports` ステートメントを定義するには、「[[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d433-130">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="2d433-131">詳細については、[方法:インポートした名前空間を追加または削除する (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d433-131">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="2d433-132">インポート エイリアス</span><span class="sxs-lookup"><span data-stu-id="2d433-132">Import Aliases</span></span>

<span data-ttu-id="2d433-133">*インポート エイリアス* では、名前空間または型のエイリアスを定義します。</span><span class="sxs-lookup"><span data-stu-id="2d433-133">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="2d433-134">インポート エイリアスは、1 つまたは複数の名前空間で宣言されている、同じ名前の項目を使用する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="2d433-134">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="2d433-135">詳細と例については、「[宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の「要素名を修飾する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d433-135">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="2d433-136">モジュール レベルで `aliasname` と同じ名前のメンバーを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d433-136">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="2d433-137">そうすると、Visual Basic コンパイラでは、宣言されたメンバーに対してのみ `aliasname` が使用され、それをインポート エイリアスとして認識されなくなります。</span><span class="sxs-lookup"><span data-stu-id="2d433-137">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="2d433-138">インポート エイリアスの宣言に使用される構文は、XML 名前空間プレフィックスのインポートに使用されるものと似ていますが、結果は異なります。</span><span class="sxs-lookup"><span data-stu-id="2d433-138">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="2d433-139">インポート エイリアスは、コードで式として使用できますが、XML 名前空間プレフィックスは、XML リテラルまたは XML 軸プロパティで、修飾される要素名または属性名のプレフィックスとしてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-139">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="2d433-140">要素の名前</span><span class="sxs-lookup"><span data-stu-id="2d433-140">Element Names</span></span>

<span data-ttu-id="2d433-141">`element` を指定する場合、*コンテナー要素*、つまり他の要素を含むことができるプログラミング要素を表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d433-141">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="2d433-142">コンテナー要素には、クラス、構造体、モジュール、インターフェイス、および列挙が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d433-142">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="2d433-143">`Imports` ステートメントで使用できる要素のスコープは、`element`を指定したかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="2d433-143">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="2d433-144">`namespace` だけを指定する場合、その名前空間の一意の名前を持つすべてのメンバーと、その名前空間内のコンテナー要素のメンバーは、修飾なしで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-144">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="2d433-145">`namespace` と `element` の両方を指定すると、その要素のメンバーだけが修飾なしで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d433-145">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="2d433-146">例</span><span class="sxs-lookup"><span data-stu-id="2d433-146">Example</span></span>

<span data-ttu-id="2d433-147">次の例では、<xref:System.IO.DirectoryInfo> クラスを使用して、*C:\\* ディレクトリにあるすべてのフォルダーを返しています。</span><span class="sxs-lookup"><span data-stu-id="2d433-147">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="2d433-148">コードでは、ファイルの先頭に `Imports` ステートメントがありません。</span><span class="sxs-lookup"><span data-stu-id="2d433-148">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="2d433-149">そのため、<xref:System.IO.DirectoryInfo>、<xref:System.Text.StringBuilder>、および <xref:Microsoft.VisualBasic.ControlChars.CrLf> 参照はすべて、名前空間で完全修飾されています。</span><span class="sxs-lookup"><span data-stu-id="2d433-149">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="2d433-150">例</span><span class="sxs-lookup"><span data-stu-id="2d433-150">Example</span></span>

<span data-ttu-id="2d433-151">次の例には、参照先の名前空間の `Imports` ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d433-151">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="2d433-152">そのため、型は名前空間で完全修飾されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2d433-152">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="2d433-153">例</span><span class="sxs-lookup"><span data-stu-id="2d433-153">Example</span></span>

<span data-ttu-id="2d433-154">次の例には、参照先の名前空間のエイリアスを作成する `Imports` ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d433-154">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="2d433-155">型はエイリアスで修飾されています。</span><span class="sxs-lookup"><span data-stu-id="2d433-155">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="2d433-156">例</span><span class="sxs-lookup"><span data-stu-id="2d433-156">Example</span></span>

<span data-ttu-id="2d433-157">次の例には、参照先の型のエイリアスを作成する `Imports` ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d433-157">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="2d433-158">エイリアスは、型を指定するために使用されています。</span><span class="sxs-lookup"><span data-stu-id="2d433-158">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="2d433-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d433-159">See also</span></span>

- [<span data-ttu-id="2d433-160">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="2d433-160">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="2d433-161">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="2d433-161">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="2d433-162">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="2d433-162">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="2d433-163">Imports ステートメント (XML 名前空間)</span><span class="sxs-lookup"><span data-stu-id="2d433-163">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="2d433-164">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="2d433-164">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
