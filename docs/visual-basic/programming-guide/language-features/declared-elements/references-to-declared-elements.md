---
description: '詳細情報: 宣言された要素の参照 (Visual Basic)'
title: 宣言された要素の参照
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 75cc05381f01af00ac75995739647810fb7ff1d7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471436"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="c5f32-103">宣言された要素の参照 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5f32-103">References to Declared Elements (Visual Basic)</span></span>

<span data-ttu-id="c5f32-104">コードが宣言された要素を参照すると、Visual Basic コンパイラは、参照内の名前と、その名前の適切な宣言を照合します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-104">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="c5f32-105">同じ名前の複数の要素が宣言されている場合は、その名前を *修飾* することで、それらの要素のうちどれが参照されるかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-105">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="c5f32-106">コンパイラは、名前宣言への名前参照を *最も狭いスコープ* と照合しようとします。</span><span class="sxs-lookup"><span data-stu-id="c5f32-106">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="c5f32-107">これは、参照を行うコードから始まり、コンテナー要素のレベルの外側に向かって機能することを意味します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-107">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="c5f32-108">次の例では、同じ名前を持つ 2 つの変数への参照を示します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-108">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="c5f32-109">この例では、それぞれが `totalCount` という名前の 2 つの変数を、モジュール `container` の異なるレベルのスコープで宣言しています。</span><span class="sxs-lookup"><span data-stu-id="c5f32-109">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="c5f32-110">プロシージャ `showCount` により `totalCount` が修飾なしで表示される場合、Visual Basic コンパイラは、参照を最も狭いスコープ (つまり、`showCount` 内のローカル宣言) に解決します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-110">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="c5f32-111">含まれているモジュール `container` で `totalCount` を修飾すると、コンパイラは、参照をより広いスコープの宣言に解決します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-111">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="c5f32-112">要素名の修飾</span><span class="sxs-lookup"><span data-stu-id="c5f32-112">Qualifying an Element Name</span></span>  

 <span data-ttu-id="c5f32-113">この検索プロセスをオーバーライドし、より広いスコープで宣言された名前を指定する場合は、より広いスコープのコンテナー要素で名前を *修飾* する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-113">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="c5f32-114">場合によっては、コンテナー要素を修飾する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-114">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="c5f32-115">名前の修飾は、ターゲット要素が定義されている場所を識別する情報を、ソース ステートメント内で先に記述することを意味します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-115">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="c5f32-116">この情報は、*修飾文字列* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-116">This information is called a *qualification string*.</span></span> <span data-ttu-id="c5f32-117">1 つ以上の名前空間と、1 つのモジュール、クラス、または構造体を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-117">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="c5f32-118">修飾文字列では、ターゲット要素を含むモジュール、クラス、または構造体を明確に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-118">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="c5f32-119">コンテナーは、別のコンテナー要素 (通常は名前空間) に配置される場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-119">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="c5f32-120">修飾文字列に複数のコンテナー要素を含めることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-120">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="c5f32-121">名前を修飾することで宣言された要素にアクセスするには</span><span class="sxs-lookup"><span data-stu-id="c5f32-121">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="c5f32-122">要素が定義されている場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-122">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="c5f32-123">これには、名前空間、または名前空間の階層が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-123">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="c5f32-124">最下位レベルの名前空間内では、要素はモジュール、クラス、または構造体に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-124">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. <span data-ttu-id="c5f32-125">ターゲット要素の場所に基づいて、修飾パスを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-125">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="c5f32-126">最上位レベルの名前空間から開始し、最下位レベルの名前空間に進み、ターゲット要素が含まれているモジュール、クラス、または構造体で終了します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-126">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="c5f32-127">パス内の各要素には、その後に続く要素が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-127">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="c5f32-128">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="c5f32-128">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="c5f32-129">ターゲット要素の修飾文字列を準備します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-129">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="c5f32-130">パス内のすべての要素の後にピリオド (`.`) を配置します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-130">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="c5f32-131">アプリケーションは、修飾文字列内のすべての要素にアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-131">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="c5f32-132">通常の方法で、ターゲット要素を参照する式または代入ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-132">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="c5f32-133">ターゲット要素名の前に修飾文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-133">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="c5f32-134">名前は、要素が含まれているモジュール、クラス、または構造体の後のピリオド (`.`) の直後に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-134">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="c5f32-135">コンパイラは、修飾文字列を使用して、ターゲット要素参照と照合できる、明確で、あいまいでない宣言を検索します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-135">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="c5f32-136">また、アプリケーションが同じ名前を持つ複数のプログラミング要素にアクセスできる場合は、名前参照の修飾が必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-136">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="c5f32-137">たとえば、<xref:System.Windows.Forms> と <xref:System.Web.UI.WebControls> の名前空間のどちらにも、`Label` クラス (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> および <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5f32-137">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="c5f32-138">アプリケーションで両方を使用する場合、または独自の `Label` クラスを定義する場合は、異なる `Label` オブジェクトを区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-138">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="c5f32-139">変数宣言に、名前空間またはインポートの別名を含めます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-139">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="c5f32-140">次の例では、インポートの別名を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-140">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="c5f32-141">他のコンテナー要素のメンバー</span><span class="sxs-lookup"><span data-stu-id="c5f32-141">Members of Other Containing Elements</span></span>  

 <span data-ttu-id="c5f32-142">別のクラスまたは構造体の非共有メンバーを使用する場合は、まず、クラスまたは構造体のインスタンスを指す変数または式を使用して、メンバー名を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-142">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="c5f32-143">次の例では、`demoClass` は `class1` という名前のクラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="c5f32-143">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="c5f32-144">[Shared](../../../language-reference/modifiers/shared.md) ではないメンバーを修飾するために、クラス名自体を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c5f32-144">You cannot use the class name itself to qualify a member that is not [Shared](../../../language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="c5f32-145">まず、オブジェクト変数にインスタンスを作成してから (この場合は `demoClass`)、変数名によって参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-145">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="c5f32-146">クラスまたは構造体に `Shared` メンバーが含まれている場合は、クラスまたは構造体の名前を使用して、またはインスタンスを指す変数または式を使用して、そのメンバーを修飾できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-146">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="c5f32-147">モジュールには個別のインスタンスはなく、そのすべてのメンバーは既定で `Shared` です。</span><span class="sxs-lookup"><span data-stu-id="c5f32-147">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="c5f32-148">そのため、モジュール名を持つモジュール メンバーを修飾します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-148">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="c5f32-149">次の例では、モジュール メンバー プロシージャへの修飾参照を示します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-149">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="c5f32-150">この例では、プロジェクト内の異なるモジュールに、両方とも `perform` という名前の 2 つの `Sub` プロシージャを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="c5f32-150">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="c5f32-151">それぞれをその独自のモジュール内に修飾なしで指定できますが、他の場所から参照されている場合は修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-151">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="c5f32-152">`module3` の最後の参照は `perform` を修飾しないため、コンパイラはその参照を解決できません。</span><span class="sxs-lookup"><span data-stu-id="c5f32-152">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="c5f32-153">プロジェクトへの参照</span><span class="sxs-lookup"><span data-stu-id="c5f32-153">References to Projects</span></span>  

 <span data-ttu-id="c5f32-154">別のプロジェクトで定義されている [Public](../../../language-reference/modifiers/public.md) 要素を使用するには、まず、そのプロジェクトのアセンブリまたは型ライブラリへの *参照* を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-154">To use [Public](../../../language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="c5f32-155">参照を設定するには、 **[プロジェクト]** メニューで **[参照の追加]** をクリックするか、[-reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) コマンドライン コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-155">To set a reference, click **Add Reference** on the **Project** menu, or use the [-reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="c5f32-156">たとえば、.NET Framework の XML オブジェクト モデルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-156">For example, you can use the XML object model of the .NET Framework.</span></span> <span data-ttu-id="c5f32-157"><xref:System.Xml> 名前空間への参照を設定する場合は、<xref:System.Xml.XmlDocument> など、そのクラスのいずれかを宣言して使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-157">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="c5f32-158"><xref:System.Xml.XmlDocument> の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-158">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="c5f32-159">コンテナー要素のインポート</span><span class="sxs-lookup"><span data-stu-id="c5f32-159">Importing Containing Elements</span></span>  

 <span data-ttu-id="c5f32-160">[Imports ステートメント (.NET 名前空間と型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) を使用すると、使用するモジュールまたはクラスを含む名前空間を *インポート* できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-160">You can use the [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="c5f32-161">これにより、インポートされた名前空間で定義されている要素を、その名前を完全修飾せずに参照できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-161">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="c5f32-162">次の例では、前の例を記述し直して、<xref:System.Xml> 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="c5f32-162">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="c5f32-163">さらに、`Imports` ステートメントでは、インポートされた名前空間ごとに *インポートの別名* を定義できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-163">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="c5f32-164">これにより、ソース コードを短くして、読みやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-164">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="c5f32-165">次の例では、前の例を記述し直して、`xD` 名前空間の別名として <xref:System.Xml> を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5f32-165">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="c5f32-166">`Imports` ステートメントによって、他のプロジェクトの要素をアプリケーションで使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-166">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="c5f32-167">つまり、参照の設定の代わりになりません。</span><span class="sxs-lookup"><span data-stu-id="c5f32-167">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="c5f32-168">名前空間をインポートすると、その名前空間で定義されている名前を修飾する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-168">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="c5f32-169">また、`Imports` ステートメントを使用して、モジュール、クラス、構造体、および列挙型をインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-169">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="c5f32-170">その後、このようなインポートされた要素のメンバーを修飾なしで使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-170">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="c5f32-171">ただし、クラスや構造体の非共有メンバーは、常に、クラスまたは構造体のインスタンスに評価される変数または式を使用して修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-171">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="c5f32-172">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c5f32-172">Naming Guidelines</span></span>  

 <span data-ttu-id="c5f32-173">同じ名前を持つ複数のプログラミング要素を定義すると、コンパイラがその名前への参照を解決しようとしたときに、*名前のあいまいさ* が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-173">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="c5f32-174">スコープ内に複数の定義が含まれている場合、またはスコープ内に定義が存在しない場合、参照は解決不可能です。</span><span class="sxs-lookup"><span data-stu-id="c5f32-174">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="c5f32-175">例については、このヘルプ ページの「修飾参照の例」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5f32-175">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="c5f32-176">すべての要素に一意の名前を付けることで、名前のあいまいさを回避できます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-176">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="c5f32-177">その後、名前を名前空間、モジュール、またはクラスで修飾しなくても、任意の要素を参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c5f32-177">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="c5f32-178">また、間違った要素が誤って参照される可能性を低くすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-178">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="c5f32-179">シャドウ</span><span class="sxs-lookup"><span data-stu-id="c5f32-179">Shadowing</span></span>  

 <span data-ttu-id="c5f32-180">2 つのプログラミング要素が同じ名前を共有している場合、それらのうちの 1 つで他方を非表示にしたり、*シャドウ* したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-180">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="c5f32-181">シャドウされた要素を参照することはできません。代わりに、シャドウされた要素名を使用するコードでは、Visual Basic コンパイラによってシャドウ要素に解決されます。</span><span class="sxs-lookup"><span data-stu-id="c5f32-181">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="c5f32-182">例の詳細については、「[Visual Basic におけるシャドウ](shadowing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5f32-182">For a more detailed explanation with examples, see [Shadowing in Visual Basic](shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f32-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5f32-183">See also</span></span>

- [<span data-ttu-id="c5f32-184">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="c5f32-184">Declared Element Names</span></span>](declared-element-names.md)
- [<span data-ttu-id="c5f32-185">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="c5f32-185">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="c5f32-186">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="c5f32-186">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="c5f32-187">変数</span><span class="sxs-lookup"><span data-stu-id="c5f32-187">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="c5f32-188">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="c5f32-188">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c5f32-189">New 演算子</span><span class="sxs-lookup"><span data-stu-id="c5f32-189">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="c5f32-190">Public</span><span class="sxs-lookup"><span data-stu-id="c5f32-190">Public</span></span>](../../../language-reference/modifiers/public.md)
