---
description: '詳細情報: Visual Basic におけるシャドウ'
title: シャドウ
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 468ad72808d689016cacb8d2be56fa9f9fcd1eec
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434824"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="95eb7-103">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="95eb7-103">Shadowing in Visual Basic</span></span>

<span data-ttu-id="95eb7-104">2 つのプログラミング要素が同じ名前を共有している場合、それらのうちの 1 つで他方を非表示にしたり、*シャドウ* したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-104">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="95eb7-105">このような状況では、シャドウされた要素を参照することはできません。代わりに、コードで要素名を使用すると、Visual Basic コンパイラによって、それがシャドウする要素に解決されます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-105">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="95eb7-106">目的</span><span class="sxs-lookup"><span data-stu-id="95eb7-106">Purpose</span></span>  

 <span data-ttu-id="95eb7-107">シャドウの主な目的は、クラス メンバーの定義を保護することです。</span><span class="sxs-lookup"><span data-stu-id="95eb7-107">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="95eb7-108">基底クラスには、既に定義されているものと同じ名前の要素を作成する変更が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="95eb7-108">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="95eb7-109">この場合、`Shadows` 修飾子は、クラスによる参照が、新しい基底クラス要素ではなく定義したメンバーに強制的に解決されるようにします。</span><span class="sxs-lookup"><span data-stu-id="95eb7-109">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="95eb7-110">シャドウの種類</span><span class="sxs-lookup"><span data-stu-id="95eb7-110">Types of Shadowing</span></span>  

 <span data-ttu-id="95eb7-111">要素では、2 つの異なる方法で別の要素をシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-111">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="95eb7-112">シャドウする要素は、シャドウされる要素を含む領域のサブ領域内で宣言できます。この場合、シャドウは *スコープによって* 実現されます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-112">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="95eb7-113">または、派生クラスで、基底クラスのメンバーを再定義できます。この場合、シャドウは *継承によって* 行われます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-113">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="95eb7-114">スコープによるシャドウ</span><span class="sxs-lookup"><span data-stu-id="95eb7-114">Shadowing Through Scope</span></span>  

 <span data-ttu-id="95eb7-115">同じモジュール、クラス、または構造体内のプログラミング要素で、同じ名前で、異なるスコープを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-115">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="95eb7-116">2 つの要素がこのように宣言されていて、コードでそれらが共有する名前を参照する場合、スコープが狭い方の要素によって、他方の要素がシャドウされます (ブロック スコープが最も狭い)。</span><span class="sxs-lookup"><span data-stu-id="95eb7-116">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="95eb7-117">たとえば、モジュールで `temp` という名前の `Public` 変数を定義でき、モジュール内のプロシージャでも、`temp` という名前のローカル変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-117">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="95eb7-118">プロシージャ内から `temp` への参照ではローカル変数にアクセスしますが、プロシージャの外部から `temp` への参照では `Public` 変数にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="95eb7-118">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="95eb7-119">この場合、プロシージャ変数 `temp` によって、モジュール変数 `temp` がシャドウされます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-119">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="95eb7-120">次の図は、どちらも `temp` という名前の 2 つの変数を示します。</span><span class="sxs-lookup"><span data-stu-id="95eb7-120">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="95eb7-121">ローカル変数 `temp` は、それ自身のプロシージャ `p` 内からアクセスされるときに、メンバー変数 `temp` をシャドウします。</span><span class="sxs-lookup"><span data-stu-id="95eb7-121">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="95eb7-122">ただし、`MyClass` キーワードによって、シャドウをバイパスし、メンバー変数にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-122">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![スコープによるシャドウを示すグラフィック。](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="95eb7-124">スコープによるシャドウの例については、「[方法:自分で宣言した変数と同じ名前の変数を隠す](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95eb7-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="95eb7-125">継承によるシャドウ</span><span class="sxs-lookup"><span data-stu-id="95eb7-125">Shadowing Through Inheritance</span></span>  

 <span data-ttu-id="95eb7-126">派生クラスで、基底クラスから継承されたプログラミング要素を再定義する場合、再定義する要素によって、元の要素がシャドウされます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="95eb7-127">任意の型の宣言された要素、またはオーバーロードされた要素のセットを、他の型でシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="95eb7-128">たとえば、`Integer` 変数によって、`Function` プロシージャをシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="95eb7-129">別のプロシージャでプロシージャをシャドウする場合、別のパラメーター リストと別の戻り値の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="95eb7-130">次の図は、基底クラス `b` と、`b` から継承する派生クラス `d` を示しています。</span><span class="sxs-lookup"><span data-stu-id="95eb7-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="95eb7-131">基底クラスで `proc` という名前のプロシージャを定義しており、派生クラスでは、同じ名前の別のプロシージャでそれをシャドウします。</span><span class="sxs-lookup"><span data-stu-id="95eb7-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="95eb7-132">最初の `Call` ステートメントで、派生クラスのシャドウする `proc` にアクセスしています。</span><span class="sxs-lookup"><span data-stu-id="95eb7-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="95eb7-133">ただし、`MyBase` キーワードによって、シャドウをバイパスし、基底クラスのシャドウされたプロシージャにアクセスしています。</span><span class="sxs-lookup"><span data-stu-id="95eb7-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![継承によるシャドウのグラフィック ダイアグラム](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="95eb7-135">継承によるシャドウの例については、「[方法:自分で宣言した変数と同じ名前の変数を隠す](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)」と「[方法:継承された変数を隠す](how-to-hide-an-inherited-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95eb7-135">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="95eb7-136">シャドウとアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="95eb7-136">Shadowing and Access Level</span></span>  

 <span data-ttu-id="95eb7-137">シャドウする要素には、常に派生クラスを使用して、コードからアクセスできるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="95eb7-137">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="95eb7-138">たとえば、それが `Private` として宣言されているとします。</span><span class="sxs-lookup"><span data-stu-id="95eb7-138">For example, it might be declared `Private`.</span></span> <span data-ttu-id="95eb7-139">そのような場合、シャドウが無効化され、コンパイラによって、同じ要素への参照が、シャドウがなかった場合のように解決されます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-139">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="95eb7-140">この要素は、シャドウするクラスからさかのぼって最も少ない派生ステップでアクセス可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="95eb7-140">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="95eb7-141">シャドウされた要素がプロシージャの場合は、同じ名前、パラメーター リスト、および戻り値の型を持つ、最も近いアクセス可能なバージョンに解決されます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-141">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="95eb7-142">次の例に、3 つのクラスの継承階層を示します。</span><span class="sxs-lookup"><span data-stu-id="95eb7-142">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="95eb7-143">各クラスで `Sub` プロシージャ`display` を定義し、各派生クラスで、その基底クラスの `display` プロシージャをシャドウしています。</span><span class="sxs-lookup"><span data-stu-id="95eb7-143">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="95eb7-144">前の例では、派生クラス `secondClass` で、`Private` プロシージャによって `display` をシャドウしています。</span><span class="sxs-lookup"><span data-stu-id="95eb7-144">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="95eb7-145">モジュール `callDisplay` で `secondClass` の `display` が呼び出されたときに、呼び出し元のコードは `secondClass` の外部にあるため、プライベートの `display` プロシージャにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="95eb7-145">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="95eb7-146">シャドウが無効化され、コンパイラによって、参照が基底クラスの `display` プロシージャに解決されます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-146">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="95eb7-147">ただし、さらに派生したクラス `thirdClass` では `display` を `Public` として宣言しているため、`callDisplay` のコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-147">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="95eb7-148">シャドウとオーバーライド</span><span class="sxs-lookup"><span data-stu-id="95eb7-148">Shadowing and Overriding</span></span>  

 <span data-ttu-id="95eb7-149">シャドウとオーバーライドを混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="95eb7-149">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="95eb7-150">どちらも派生クラスが基底クラスから継承されるときに使用し、どちらも一方の宣言された要素を他方の要素で再定義します。</span><span class="sxs-lookup"><span data-stu-id="95eb7-150">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="95eb7-151">しかし、この 2 つには、大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="95eb7-151">But there are significant differences between the two.</span></span> <span data-ttu-id="95eb7-152">比較については、「[シャドウとオーバーライドの違い](differences-between-shadowing-and-overriding.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95eb7-152">For a comparison, see [Differences Between Shadowing and Overriding](differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="95eb7-153">シャドウとオーバーロード</span><span class="sxs-lookup"><span data-stu-id="95eb7-153">Shadowing and Overloading</span></span>  

 <span data-ttu-id="95eb7-154">派生クラス内で、複数の要素で同じ基底クラス要素をシャドウする場合、シャドウする要素は、その要素のオーバーロードされたバージョンになります。</span><span class="sxs-lookup"><span data-stu-id="95eb7-154">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="95eb7-155">詳細については、「 [Procedure Overloading](../procedures/procedure-overloading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95eb7-155">For more information, see [Procedure Overloading](../procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="95eb7-156">シャドウされた要素へのアクセス</span><span class="sxs-lookup"><span data-stu-id="95eb7-156">Accessing a Shadowed Element</span></span>  

 <span data-ttu-id="95eb7-157">派生クラスから要素にアクセスする場合、通常、その派生クラスの現在のインスタンスから行いますが、要素名を `Me` キーワードで修飾します。</span><span class="sxs-lookup"><span data-stu-id="95eb7-157">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="95eb7-158">派生クラスで基底クラスの要素をシャドウする場合は、`MyBase` キーワードで修飾することで、基底クラスの要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-158">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="95eb7-159">シャドウされた要素にアクセスする例については、「[方法:派生クラスによって非表示になっている変数にアクセスする](how-to-access-a-variable-hidden-by-a-derived-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95eb7-159">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="95eb7-160">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="95eb7-160">Declaration of the Object Variable</span></span>  

 <span data-ttu-id="95eb7-161">オブジェクト変数を作成する方法は、派生クラスがシャドウする要素またはシャドウされた要素にアクセスするかどうかにも影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="95eb7-161">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="95eb7-162">次の例では、派生クラスから 2 つのオブジェクトを作成していますが、一方のオブジェクトは基底クラスとして、他方を派生クラスとして宣言しています。</span><span class="sxs-lookup"><span data-stu-id="95eb7-162">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="95eb7-163">前の例では、変数 `basObj` が基底クラスとして宣言されています。</span><span class="sxs-lookup"><span data-stu-id="95eb7-163">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="95eb7-164">`dervCls` オブジェクトをそれに割り当てることは、拡大変換になるため、有効です。</span><span class="sxs-lookup"><span data-stu-id="95eb7-164">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="95eb7-165">ただし、基底クラスでは派生クラス内の変数 `z` のシャドウするバージョンにアクセスできないため、コンパイラによって `basObj.z` が元の基底クラスの値に解決されます。</span><span class="sxs-lookup"><span data-stu-id="95eb7-165">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95eb7-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="95eb7-166">See also</span></span>

- [<span data-ttu-id="95eb7-167">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="95eb7-167">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="95eb7-168">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="95eb7-168">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="95eb7-169">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="95eb7-169">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="95eb7-170">Shadows</span><span class="sxs-lookup"><span data-stu-id="95eb7-170">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="95eb7-171">Overrides</span><span class="sxs-lookup"><span data-stu-id="95eb7-171">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="95eb7-172">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="95eb7-172">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="95eb7-173">継承の基本</span><span class="sxs-lookup"><span data-stu-id="95eb7-173">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
