---
description: '詳細情報: Namespace ステートメント'
title: Namespace ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 2c315947a26f72a90e03bc1f4bf1b5f647866b33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768858"
---
# <a name="namespace-statement"></a><span data-ttu-id="d2598-103">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="d2598-103">Namespace Statement</span></span>

<span data-ttu-id="d2598-104">名前空間の名前を宣言し、宣言に続くソース コードがその名前空間内でコンパイルされるようにします。</span><span class="sxs-lookup"><span data-stu-id="d2598-104">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2598-105">構文</span><span class="sxs-lookup"><span data-stu-id="d2598-105">Syntax</span></span>  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="d2598-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="d2598-106">Parts</span></span>  

 <span data-ttu-id="d2598-107">Global</span><span class="sxs-lookup"><span data-stu-id="d2598-107">Global</span></span>  
 <span data-ttu-id="d2598-108">任意。</span><span class="sxs-lookup"><span data-stu-id="d2598-108">Optional.</span></span> <span data-ttu-id="d2598-109">これにより、プロジェクトのルート名前空間から名前空間を定義できます。</span><span class="sxs-lookup"><span data-stu-id="d2598-109">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="d2598-110">「[Visual Basic における名前空間](../../programming-guide/program-structure/namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2598-110">See [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="d2598-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="d2598-111">Required.</span></span> <span data-ttu-id="d2598-112">名前空間を識別する一意の名前。</span><span class="sxs-lookup"><span data-stu-id="d2598-112">A unique name that identifies the namespace.</span></span> <span data-ttu-id="d2598-113">有効な Visual Basic 識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2598-113">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="d2598-114">詳細については、「[宣言された要素の名前](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2598-114">For more information, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="d2598-115">任意。</span><span class="sxs-lookup"><span data-stu-id="d2598-115">Optional.</span></span> <span data-ttu-id="d2598-116">名前空間を構成する要素。</span><span class="sxs-lookup"><span data-stu-id="d2598-116">Elements that make up the namespace.</span></span> <span data-ttu-id="d2598-117">これには、列挙型、構造体、インターフェイス、クラス、モジュール、委任、その他の名前空間が含まれますが、この限りではありません。</span><span class="sxs-lookup"><span data-stu-id="d2598-117">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="d2598-118">`Namespace` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="d2598-118">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2598-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="d2598-119">Remarks</span></span>  

 <span data-ttu-id="d2598-120">名前空間は、組織的なシステムとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="d2598-120">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="d2598-121">これを使用することにより、他のプログラムおよびアプリケーションに公開されるプログラミング要素を分類して提示することができます。</span><span class="sxs-lookup"><span data-stu-id="d2598-121">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="d2598-122">名前空間は、クラスまたは構造体がそうであるという意味では、"*型*" ではないことに注意してください。つまり、名前空間のデータ型を持つプログラミング要素を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="d2598-122">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="d2598-123">`Namespace` ステートメントの後に宣言されるすべてのプログラミング要素は、その名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="d2598-123">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="d2598-124">Visual Basic は、`End Namespace` ステートメントまたは別の `Namespace` ステートメントのいずれかが検出されるまで、最後に宣言された名前空間に要素をコンパイルし続けます。</span><span class="sxs-lookup"><span data-stu-id="d2598-124">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="d2598-125">名前空間が既に定義されている場合 (ご使用のプロジェクト以外であっても)、プログラミング要素をそれに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="d2598-125">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="d2598-126">このためには、`Namespace` ステートメントを使用して、要素をその名前空間にコンパイルするように Visual Basic に指示します。</span><span class="sxs-lookup"><span data-stu-id="d2598-126">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="d2598-127">`Namespace` ステートメントは、ファイルまたは名前空間レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2598-127">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="d2598-128">つまり、名前空間の "*宣言コンテキスト*" は、ソース ファイルまたは別の名前空間である必要があり、クラス、構造体、モジュール、インターフェイス、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d2598-128">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="d2598-129">詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2598-129">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="d2598-130">ある名前空間を別の名前空間内で宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="d2598-130">You can declare one namespace within another.</span></span> <span data-ttu-id="d2598-131">宣言できる入れ子レベルに厳格な制限はありませんが、他のコードで、最も内側にある名前空間内で宣言された要素にアクセスする場合、入れ子階層内のすべての名前空間の名前を含む修飾文字列を使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d2598-131">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="d2598-132">アクセス レベル</span><span class="sxs-lookup"><span data-stu-id="d2598-132">Access Level</span></span>  

 <span data-ttu-id="d2598-133">名前空間は、アクセス レベルが `Public` であるものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="d2598-133">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="d2598-134">名前空間は、同じプロジェクト内の任意の場所にあるコード、そのプロジェクトを参照する他のプロジェクト、そのプロジェクトから構築された任意のアセンブリからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d2598-134">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="d2598-135">他の要素内部ではなく名前空間内という意味で、名前空間レベルで宣言されたプログラミング要素は、アクセス レベルを `Public` または `Friend` にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d2598-135">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="d2598-136">指定しない場合、このような要素のアクセス レベルには、既定により、`Friend` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d2598-136">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="d2598-137">名前空間レベルで宣言できる要素としては、クラス、構造体、モジュール、インターフェイス、列挙型、委任があります。</span><span class="sxs-lookup"><span data-stu-id="d2598-137">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="d2598-138">詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2598-138">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="d2598-139">ルート名前空間</span><span class="sxs-lookup"><span data-stu-id="d2598-139">Root Namespace</span></span>  

 <span data-ttu-id="d2598-140">プロジェクト内のすべての名前空間の名前は、"*ルート名前空間*" に基づきます。</span><span class="sxs-lookup"><span data-stu-id="d2598-140">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="d2598-141">Visual Studio では、プロジェクト内のすべてのコードで、既定のルート名前空間としてプロジェクト名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d2598-141">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="d2598-142">たとえば、プロジェクト名が `Payroll`である場合、そのプログラミング要素は `Payroll`名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="d2598-142">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="d2598-143">`Namespace funding` を宣言する場合、その名前空間のフル ネームは `Payroll.funding` です。</span><span class="sxs-lookup"><span data-stu-id="d2598-143">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="d2598-144">ジェネリック リスト クラスの例のように、`Namespace` で既存の名前空間を指定する場合は、ルート名前空間を null 値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="d2598-144">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="d2598-145">このためには、 **[プロジェクト]** メニューで **[プロジェクトのプロパティ]** をクリックし、 **[ルート名前空間]** エントリをクリアして、ボックスを空にします。</span><span class="sxs-lookup"><span data-stu-id="d2598-145">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="d2598-146">ジェネリック リスト クラスの例でこの操作を行わない場合、Visual Basic コンパイラは、`System.Collections.Generic` をプロジェクトの `Payroll` 内の新しい名前空間と見なし、フル ネームを `Payroll.System.Collections.Generic` にします。</span><span class="sxs-lookup"><span data-stu-id="d2598-146">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="d2598-147">または、`Global` キーワードを使用して、プロジェクトの外部で定義された名前空間の要素を参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2598-147">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="d2598-148">こうすることにより、プロジェクト名をルート名前空間として保持できます。</span><span class="sxs-lookup"><span data-stu-id="d2598-148">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="d2598-149">これにより、プログラミング要素が既存の名前空間のプログラミング要素と誤ってマージされる可能性が低減されます。</span><span class="sxs-lookup"><span data-stu-id="d2598-149">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="d2598-150">詳細については、「[Visual Basic における名前空間](../../programming-guide/program-structure/namespaces.md)」の「完全修飾名の Global キーワード」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2598-150">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="d2598-151">`Global` キーワードは、Namespace ステートメントでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2598-151">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="d2598-152">これにより、プロジェクトのルート名前空間から名前空間を定義できます。</span><span class="sxs-lookup"><span data-stu-id="d2598-152">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="d2598-153">詳細については、「[Visual Basic における名前空間](../../programming-guide/program-structure/namespaces.md)」の「名前空間のステートメントでの Global キーワード」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2598-153">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="d2598-154">**トラブルシューティング。**</span><span class="sxs-lookup"><span data-stu-id="d2598-154">**Troubleshooting.**</span></span> <span data-ttu-id="d2598-155">ルート名前空間によって、予期しない名前空間の名前の連結が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d2598-155">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="d2598-156">プロジェクトの外部で定義された名前空間を参照する場合、Visual Basic コンパイラは、それらをルート名前空間内の入れ子になった名前空間として解釈する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d2598-156">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="d2598-157">このような場合、コンパイラは、外部名前空間で既に定義されている型を認識しません。</span><span class="sxs-lookup"><span data-stu-id="d2598-157">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="d2598-158">これを回避するには、「ルート名前空間」で説明したようにルート名前空間を null 値に設定するか、`Global` キーワードを使用して外部名前空間の要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d2598-158">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="d2598-159">属性と修飾子</span><span class="sxs-lookup"><span data-stu-id="d2598-159">Attributes and Modifiers</span></span>  

 <span data-ttu-id="d2598-160">属性を名前空間に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d2598-160">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="d2598-161">属性は、アセンブリのメタデータに情報を提供します。これは、名前空間などのソース分類子にとっては意味がありません。</span><span class="sxs-lookup"><span data-stu-id="d2598-161">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="d2598-162">アクセスまたはプロシージャ修飾子やその他の修飾子を名前空間に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d2598-162">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="d2598-163">名前空間は型ではないため、これらの修飾子は意味がありません。</span><span class="sxs-lookup"><span data-stu-id="d2598-163">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2598-164">例</span><span class="sxs-lookup"><span data-stu-id="d2598-164">Example</span></span>  

 <span data-ttu-id="d2598-165">次の例では、一方が他方の入れ子になる 2 つの名前空間を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d2598-165">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a><span data-ttu-id="d2598-166">例</span><span class="sxs-lookup"><span data-stu-id="d2598-166">Example</span></span>  

 <span data-ttu-id="d2598-167">次の例では、入れ子になった複数の名前空間を 1 行で宣言します。これは、前の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="d2598-167">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="d2598-168">例</span><span class="sxs-lookup"><span data-stu-id="d2598-168">Example</span></span>  

 <span data-ttu-id="d2598-169">次の例では、前の例で定義されたクラスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d2598-169">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="d2598-170">例</span><span class="sxs-lookup"><span data-stu-id="d2598-170">Example</span></span>  

 <span data-ttu-id="d2598-171">次の例では、新しいジェネリック リスト クラスのスケルトンを定義し、それを <xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間に追加します。</span><span class="sxs-lookup"><span data-stu-id="d2598-171">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2598-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2598-172">See also</span></span>

- [<span data-ttu-id="d2598-173">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="d2598-173">Imports Statement (.NET Namespace and Type)</span></span>](imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="d2598-174">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="d2598-174">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="d2598-175">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="d2598-175">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
