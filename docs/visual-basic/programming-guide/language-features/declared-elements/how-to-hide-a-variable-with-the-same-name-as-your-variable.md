---
description: '詳細情報: 方法:自分で宣言した変数と同じ名前の変数を隠す (Visual Basic)'
title: '方法: 自分で宣言した変数と同じ名前の変数を隠す'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: c6699abdc163c6ae1a78f6035cd08439d1b029f0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429858"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="65a8b-103">方法: 自分で宣言した変数と同じ名前の変数を隠す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65a8b-103">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="65a8b-104">変数を隠すには、それを *シャドウ* します。つまり、同じ名前の変数でそれを再定義します。</span><span class="sxs-lookup"><span data-stu-id="65a8b-104">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="65a8b-105">隠す変数は、次の 2 つの方法でシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-105">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="65a8b-106">**スコープによるシャドウ。**</span><span class="sxs-lookup"><span data-stu-id="65a8b-106">**Shadowing Through Scope.**</span></span> <span data-ttu-id="65a8b-107">スコープによってそれをシャドウするには、隠す変数が含まれている領域のサブ領域内でそれを再宣言します。</span><span class="sxs-lookup"><span data-stu-id="65a8b-107">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="65a8b-108">**継承によるシャドウ。**</span><span class="sxs-lookup"><span data-stu-id="65a8b-108">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="65a8b-109">隠す変数がクラス レベルで定義されている場合は、派生クラスで [Shadows](../../../language-reference/modifiers/shadows.md) キーワードを使用してそれを再宣言することで、継承によってそれをシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-109">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="65a8b-110">変数を隠す 2 つの方法</span><span class="sxs-lookup"><span data-stu-id="65a8b-110">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="65a8b-111">変数をスコープによってシャドウして隠すには</span><span class="sxs-lookup"><span data-stu-id="65a8b-111">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="65a8b-112">隠す変数を定義している領域を特定し、独自の変数でそれを再定義するサブ領域を決定します。</span><span class="sxs-lookup"><span data-stu-id="65a8b-112">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="65a8b-113">変数の領域</span><span class="sxs-lookup"><span data-stu-id="65a8b-113">Variable's region</span></span>|<span data-ttu-id="65a8b-114">その再定義に使用できるサブ領域</span><span class="sxs-lookup"><span data-stu-id="65a8b-114">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="65a8b-115">Module</span><span class="sxs-lookup"><span data-stu-id="65a8b-115">Module</span></span>|<span data-ttu-id="65a8b-116">モジュール内のクラス</span><span class="sxs-lookup"><span data-stu-id="65a8b-116">A class within the module</span></span>|
    |<span data-ttu-id="65a8b-117">クラス</span><span class="sxs-lookup"><span data-stu-id="65a8b-117">Class</span></span>|<span data-ttu-id="65a8b-118">クラス内のサブクラス</span><span class="sxs-lookup"><span data-stu-id="65a8b-118">A subclass within the class</span></span><br /><br /> <span data-ttu-id="65a8b-119">クラス内のプロシージャ</span><span class="sxs-lookup"><span data-stu-id="65a8b-119">A procedure within the class</span></span>|

    <span data-ttu-id="65a8b-120">そのプロシージャ内のブロック (`If`...`End If` コンストラクションや `For` ループなど) でプロシージャ変数を再定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="65a8b-120">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="65a8b-121">サブ領域がまだ存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="65a8b-121">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="65a8b-122">サブ領域内で、シャドウ変数を宣言する [Dim ステートメント](../../../language-reference/statements/dim-statement.md)を記述します。</span><span class="sxs-lookup"><span data-stu-id="65a8b-122">Within the subregion, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="65a8b-123">サブ領域内のコードで変数名を参照すると、コンパイラによって、シャドウしている変数への参照が解決されます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-123">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="65a8b-124">次の例は、スコープによるシャドウに加えて、シャドウをバイパスする参照を示しています。</span><span class="sxs-lookup"><span data-stu-id="65a8b-124">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

    ```vb
    Module shadowByScope
        ' The following statement declares num as a module-level variable.
        Public num As Integer
        Sub show()
            ' The following statement declares num as a local variable.
            Dim num As Integer
            ' The following statement sets the value of the local variable.
            num = 2
            ' The following statement displays the module-level variable.
            MsgBox(CStr(shadowByScope.num))
        End Sub
        Sub useModuleLevelNum()
            ' The following statement sets the value of the module-level variable.
            num = 1
            show()
        End Sub
    End Module
    ```

    <span data-ttu-id="65a8b-125">前の例では、モジュール レベルとプロシージャ レベル (プロシージャ `show` 内) の両方で変数 `num` を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="65a8b-125">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="65a8b-126">ローカル変数 `num` で、`show` 内のモジュールレベル変数 `num` をシャドウしているため、ローカル変数は 2 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-126">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="65a8b-127">ただし、`useModuleLevelNum` プロシージャの `num` をシャドウするローカル変数はありません。</span><span class="sxs-lookup"><span data-stu-id="65a8b-127">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="65a8b-128">そのため、`useModuleLevelNum` では、モジュールレベル変数の値が 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-128">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="65a8b-129">`show` 内の `MsgBox` 呼び出しでは、モジュール名で `num` を修飾することによって、シャドウ メカニズムがバイパスされます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-129">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="65a8b-130">そのため、ローカル変数ではなくモジュールレベルの変数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-130">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="65a8b-131">変数を継承によってシャドウして隠すには</span><span class="sxs-lookup"><span data-stu-id="65a8b-131">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="65a8b-132">隠す変数がクラス内かつクラス レベル (プロシージャの外部) で宣言されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="65a8b-132">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="65a8b-133">それ以外の場合、継承によってそれをシャドウすることはできません。</span><span class="sxs-lookup"><span data-stu-id="65a8b-133">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="65a8b-134">変数がまだ存在しない場合は、変数のクラスから派生したクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="65a8b-134">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="65a8b-135">派生クラス内で、変数を宣言する `Dim` ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="65a8b-135">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="65a8b-136">宣言に [Shadows](../../../language-reference/modifiers/shadows.md) キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-136">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="65a8b-137">派生クラスのコードで変数名を参照すると、コンパイラによって、変数への参照が解決されます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-137">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="65a8b-138">次の例に、継承によるシャドウを示しています。</span><span class="sxs-lookup"><span data-stu-id="65a8b-138">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="65a8b-139">それによって、2 つの参照が作成されます。シャドウする変数にアクセスするものと、シャドウ処理をバイパスするものです。</span><span class="sxs-lookup"><span data-stu-id="65a8b-139">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    <span data-ttu-id="65a8b-140">前の例では、基底クラスで `shadowString` 変数を宣言し、派生クラスでそれをシャドウしています。</span><span class="sxs-lookup"><span data-stu-id="65a8b-140">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="65a8b-141">派生クラスのプロシージャ `showStrings` では、名前 `shadowString` が修飾されていない場合に、文字列のシャドウしているバージョンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-141">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="65a8b-142">さらに、`shadowString` が `MyBase` キーワードで修飾されている場合は、シャドウされたバージョンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-142">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="65a8b-143">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="65a8b-143">Robust Programming</span></span>

<span data-ttu-id="65a8b-144">シャドウによって、同じ名前の変数の複数のバージョンが取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-144">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="65a8b-145">コード ステートメントで変数名を参照する場合、コンパイラによる参照の解決先のバージョンは、コード ステートメントの場所や修飾文字列の存在などの要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="65a8b-145">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="65a8b-146">これにより、シャドウされた変数の意図しないバージョンを参照するリスクが高まる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65a8b-146">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="65a8b-147">シャドウされた変数へのすべての参照を完全に修飾することで、そのリスクを軽減することができます。</span><span class="sxs-lookup"><span data-stu-id="65a8b-147">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="65a8b-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="65a8b-148">See also</span></span>

- [<span data-ttu-id="65a8b-149">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="65a8b-149">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="65a8b-150">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="65a8b-150">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="65a8b-151">シャドウとオーバーライドの違い</span><span class="sxs-lookup"><span data-stu-id="65a8b-151">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="65a8b-152">方法: 継承された変数を隠す</span><span class="sxs-lookup"><span data-stu-id="65a8b-152">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="65a8b-153">方法: 派生クラスによって非表示になっている変数にアクセスする</span><span class="sxs-lookup"><span data-stu-id="65a8b-153">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="65a8b-154">Overrides</span><span class="sxs-lookup"><span data-stu-id="65a8b-154">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="65a8b-155">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="65a8b-155">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="65a8b-156">継承の基本</span><span class="sxs-lookup"><span data-stu-id="65a8b-156">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
