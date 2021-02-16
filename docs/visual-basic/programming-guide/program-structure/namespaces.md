---
description: '詳細情報: Visual Basic における名前空間'
title: 名前空間
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: 2f7c0bfd29bf6fe104252aa125b4ddff1259b50a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460749"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="240f0-103">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="240f0-103">Namespaces in Visual Basic</span></span>

<span data-ttu-id="240f0-104">アセンブリ内で定義されているオブジェクトは、名前空間によって編成されています。</span><span class="sxs-lookup"><span data-stu-id="240f0-104">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="240f0-105">アセンブリには複数の名前空間を含めることができます。さらに、名前空間の中に他の名前空間を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="240f0-105">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="240f0-106">名前空間を使用するとあいまいさがなくなるため、クラス ライブラリを使用する場合など、多数のオブジェクトを使用する場合に参照が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="240f0-106">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="240f0-107">たとえば、.NET Framework では、<xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間に <xref:System.Windows.Forms.ListBox> クラスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="240f0-107">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="240f0-108">次のコードは、このクラスの完全修飾名を使用して変数を宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-108">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="240f0-109">名前の競合の回避</span><span class="sxs-lookup"><span data-stu-id="240f0-109">Avoiding Name Collisions</span></span>  

 <span data-ttu-id="240f0-110">.NET Framework の名前空間は、別のライブラリで似た名前が使用されている場合にクラス ライブラリの開発者が遭遇する、"*名前空間の汚染*" と呼ばれる問題に対処しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-110">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="240f0-111">このような既存コンポーネントとの競合は、 *名前の競合* とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="240f0-111">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="240f0-112">たとえば、 `ListBox`という名前の新しいクラスを作成した場合、プロジェクト内ではこのクラスを修飾子を付けずに使用できます。</span><span class="sxs-lookup"><span data-stu-id="240f0-112">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="240f0-113">ただし、同じプロジェクトで .NET Framework の <xref:System.Windows.Forms.ListBox> クラスを使用する場合は、完全修飾参照を使用して参照を一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="240f0-113">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="240f0-114">参照が一意でない場合、Visual Basic では名前があいまいであることを示すエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="240f0-114">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="240f0-115">次のコード例では、これらのオブジェクトを宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-115">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="240f0-116">次の図は、どちらも `ListBox` いう名前のオブジェクトを含む、2 つの名前空間階層を示しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-116">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![2 つの名前空間階層を示すスクリーンショット](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="240f0-118">既定では、Visual Basic で作成するすべての実行可能ファイルには、プロジェクトと同じ名前の名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="240f0-118">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="240f0-119">たとえば、 `ListBoxProject`という名前のプロジェクト内でオブジェクトを定義した場合、実行可能ファイル ListBoxProject.exe には `ListBoxProject`という名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="240f0-119">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="240f0-120">複数のアセンブリで同じ名前空間を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="240f0-120">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="240f0-121">Visual Basic では、これらは 1 つの名前セットとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="240f0-121">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="240f0-122">たとえば、 `SomeNameSpace` というアセンブリの `Assemb1`という名前空間のクラスを定義した後に、 `Assemb2`というアセンブリの同じ名前空間のクラスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="240f0-122">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="240f0-123">完全修飾名</span><span class="sxs-lookup"><span data-stu-id="240f0-123">Fully Qualified Names</span></span>  

 <span data-ttu-id="240f0-124">完全修飾名は、オブジェクトが定義されている名前空間の名前で始まるオブジェクト参照です。</span><span class="sxs-lookup"><span data-stu-id="240f0-124">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="240f0-125">他のプロジェクトで定義されているオブジェクトを使用するには、 **[プロジェクト]** メニューの **[参照の追加]** をクリックしてそのクラスへの参照を作成し、コード内でそのオブジェクトの完全修飾名を使用します。</span><span class="sxs-lookup"><span data-stu-id="240f0-125">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="240f0-126">次のコードは、別のプロジェクトの名前空間のオブジェクトを使用して完全修飾名を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-126">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="240f0-127">完全修飾名を使用すると、どのオブジェクトを使用するかをコンパイラが認識できるため、名前の競合を防止できます。</span><span class="sxs-lookup"><span data-stu-id="240f0-127">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="240f0-128">ただし、名前自体が長くなるため、使いにくくなります。</span><span class="sxs-lookup"><span data-stu-id="240f0-128">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="240f0-129">この問題を回避するには、 `Imports` ステートメントを使って *エイリアス* を定義します。エイリアスとは、完全修飾名の代わりに使用できる短い名前です。</span><span class="sxs-lookup"><span data-stu-id="240f0-129">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="240f0-130">たとえば、次のコード例では、2 つの完全修飾名に対してエイリアスを作成し、作成したエイリアスを使って 2 つのオブジェクトを定義しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-130">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="240f0-131">エイリアスを指定せずに `Imports` ステートメントを使用すると、インポートした名前空間のすべての名前を修飾子を付けずに使用できます。ただし、それらの名前がプロジェクト内で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="240f0-131">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="240f0-132">プロジェクトに、同じ名前の複数の項目を持つ名前空間をインポートする `Imports` ステートメントがある場合は、それらの名前を使用するときに完全修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="240f0-132">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="240f0-133">たとえば、プロジェクトに次の 2 つの `Imports` ステートメントがあるとします。</span><span class="sxs-lookup"><span data-stu-id="240f0-133">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="240f0-134">`Class1` を完全修飾せずに使用しようとすると、`Class1` という名前があいまいであることを示すエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="240f0-134">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="240f0-135">名前空間レベルのステートメント</span><span class="sxs-lookup"><span data-stu-id="240f0-135">Namespace Level Statements</span></span>  

 <span data-ttu-id="240f0-136">名前空間内では、モジュール、インターフェイス、クラス、デリゲート、列挙体、構造体、他の名前空間などの項目を定義できます。</span><span class="sxs-lookup"><span data-stu-id="240f0-136">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="240f0-137">プロパティ、プロシージャ、変数、イベントなどの項目を名前空間のレベルで定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="240f0-137">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="240f0-138">これらの項目は、モジュール、構造体、クラスなどのコンテナー内で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="240f0-138">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="240f0-139">完全修飾名の Global キーワード</span><span class="sxs-lookup"><span data-stu-id="240f0-139">Global Keyword in Fully Qualified Names</span></span>  

 <span data-ttu-id="240f0-140">入れ子になった階層構造の名前空間を定義すると、その階層構造の内部にあるコードが .NET Framework の <xref:System?displayProperty=nameWithType> 名前空間にアクセスできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="240f0-140">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="240f0-141">次の例は、 `SpecialSpace.System` 名前空間から <xref:System?displayProperty=nameWithType>にアクセスできない階層構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-141">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="240f0-142">この場合、 <xref:System.Int32?displayProperty=nameWithType>に `SpecialSpace.System` が定義されていないため、Visual Basic コンパイラは `Int32`への参照を正しく解決できません。</span><span class="sxs-lookup"><span data-stu-id="240f0-142">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="240f0-143">`Global` キーワードを使用すると、修飾チェーンを .NET Framework クラス ライブラリの最も外側のレベルで開始できます。</span><span class="sxs-lookup"><span data-stu-id="240f0-143">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="240f0-144">これにより、クラス ライブラリの <xref:System?displayProperty=nameWithType> 名前空間や、その他のあらゆる名前空間を指定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="240f0-144">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="240f0-145">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="240f0-145">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="240f0-146">`Global` を使用して、 <xref:Microsoft.VisualBasic?displayProperty=nameWithType>などの他のルート レベルの名前空間、およびプロジェクトに関連する任意の名前空間にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="240f0-146">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="240f0-147">名前空間のステートメントでの Global キーワード</span><span class="sxs-lookup"><span data-stu-id="240f0-147">Global Keyword in Namespace Statements</span></span>  

 <span data-ttu-id="240f0-148">[Namespace ステートメント](../../language-reference/statements/namespace-statement.md)で `Global` キーワードを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="240f0-148">You can also use the `Global` keyword in a [Namespace Statement](../../language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="240f0-149">これにより、プロジェクトのルート名前空間から名前空間を定義できます。</span><span class="sxs-lookup"><span data-stu-id="240f0-149">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="240f0-150">プロジェクト内のすべての名前空間は、プロジェクトのルート名前空間に基づいています。</span><span class="sxs-lookup"><span data-stu-id="240f0-150">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="240f0-151">Visual Studio では、プロジェクト内のすべてのコードで、既定のルート名前空間としてプロジェクト名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="240f0-151">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="240f0-152">たとえば、プロジェクト名が `ConsoleApplication1`である場合、そのプログラミング要素は `ConsoleApplication1`名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="240f0-152">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="240f0-153">`Namespace Magnetosphere`を宣言すると、プロジェクトの `Magnetosphere` への参照は `ConsoleApplication1.Magnetosphere`にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="240f0-153">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="240f0-154">次の例では、プロジェクトのルート名前空間から名前空間を宣言するために `Global` キーワードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-154">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="240f0-155">名前空間宣言では、 `Global` を別の名前空間に入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="240f0-155">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="240f0-156">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) を使用して、プロジェクトの **ルート名前空間** を表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="240f0-156">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="240f0-157">新しいプロジェクトの場合、 **ルート名前空間** の既定値は、プロジェクト名です。</span><span class="sxs-lookup"><span data-stu-id="240f0-157">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="240f0-158">`Global` を最上位レベルの名前空間にするには、 **ルート名前空間** のエントリを消去して、ボックスを空にします。</span><span class="sxs-lookup"><span data-stu-id="240f0-158">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="240f0-159">**ルート名前空間** を消去すると、名前空間の宣言で `Global` キーワードの必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="240f0-159">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="240f0-160">`Namespace` ステートメントで .NET framework の名前空間にもなっている名前を宣言する場合、 `Global` キーワードが完全修飾名で使用されていない場合、.NET Framework 名前空間は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="240f0-160">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="240f0-161">`Global` キーワードを使用せずに、.NET Framework 名前空間へのアクセスを有効にするには、 `Global` キーワードを `Namespace` ステートメントに含めます。</span><span class="sxs-lookup"><span data-stu-id="240f0-161">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="240f0-162">次の例では、 `Global` 名前空間の宣言で、 `System.Text` キーワードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="240f0-162">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="240f0-163">名前空間の宣言に `Global` キーワードが含まれていない場合、 <xref:System.Text.StringBuilder> にアクセスするには、 `Global.System.Text.StringBuilder`を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="240f0-163">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="240f0-164">`ConsoleApplication1`という名前のプロジェクトで、 `System.Text` キーワードが使用されていない場合、 `ConsoleApplication1.System.Text` を参照すると、 `Global` にアクセスすることになります。</span><span class="sxs-lookup"><span data-stu-id="240f0-164">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="240f0-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="240f0-165">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="240f0-166">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="240f0-166">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="240f0-167">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="240f0-167">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="240f0-168">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="240f0-168">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="240f0-169">Writing Code in Office Solutions</span><span class="sxs-lookup"><span data-stu-id="240f0-169">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
