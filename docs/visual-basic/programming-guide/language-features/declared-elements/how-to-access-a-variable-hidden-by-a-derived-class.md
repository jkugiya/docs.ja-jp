---
description: '詳細情報: 方法:派生クラスによって非表示になっている変数にアクセスする (Visual Basic)'
title: '方法: 派生クラスによって非表示になっている変数にアクセスする'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 5ac1dd8afc8c32c91b748c8316d035d69468d887
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430053"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="c9f7e-103">方法: 派生クラスによって非表示になっている変数にアクセスする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9f7e-103">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="c9f7e-104">派生クラスのコードで変数にアクセスすると、コンパイラでは、通常、最も近いアクセス可能なバージョン、つまり、アクセスするクラスからさかのぼって最も少ない派生ステップでアクセス可能なバージョンに参照が解決されます。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-104">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="c9f7e-105">変数が派生クラスに定義されている場合、コードでは通常、その定義にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-105">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="c9f7e-106">派生クラス変数で基底クラスの変数をシャドウする場合、基底クラスのバージョンが隠されます。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-106">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="c9f7e-107">ただし、`MyBase` キーワードを使用して修飾することによって、基底クラスの変数にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-107">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="c9f7e-108">派生クラスによって隠された基底クラスの変数にアクセスするには</span><span class="sxs-lookup"><span data-stu-id="c9f7e-108">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="c9f7e-109">式または代入ステートメントで、変数名の前に `MyBase` キーワードとピリオド (`.`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-109">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="c9f7e-110">コンパイラでは、変数の基底クラス バージョンに参照が解決されます。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-110">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="c9f7e-111">次の例に、継承によるシャドウ処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-111">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="c9f7e-112">それによって、2 つの参照が作成されます。シャドウする変数にアクセスするものと、シャドウ処理をバイパスするものです。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-112">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="c9f7e-113">前の例では、基底クラスで `shadowString` 変数を宣言し、派生クラスでそれをシャドウしています。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-113">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="c9f7e-114">派生クラスのプロシージャ `showStrings` では、名前 `shadowString` が修飾されていない場合に、文字列のシャドウしているバージョンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-114">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="c9f7e-115">さらに、`shadowString` が `MyBase` キーワードで修飾されている場合は、シャドウされたバージョンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-115">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="c9f7e-116">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="c9f7e-116">Robust Programming</span></span>

<span data-ttu-id="c9f7e-117">シャドウされた変数の意図しないバージョンを参照するリスクを低減するために、シャドウされた変数へのすべての参照を完全修飾することができます。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-117">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="c9f7e-118">シャドウによって、同じ名前の変数の複数のバージョンが取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-118">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="c9f7e-119">コード ステートメントで変数名を参照する場合、コンパイラによる参照の解決先のバージョンは、コード ステートメントの場所や修飾文字列の存在などの要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-119">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="c9f7e-120">これにより、変数の誤ったバージョンを参照するリスクが高まる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c9f7e-120">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9f7e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9f7e-121">See also</span></span>

- [<span data-ttu-id="c9f7e-122">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="c9f7e-122">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="c9f7e-123">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="c9f7e-123">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="c9f7e-124">シャドウとオーバーライドの違い</span><span class="sxs-lookup"><span data-stu-id="c9f7e-124">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="c9f7e-125">方法: 自分で宣言した変数と同じ名前の変数を隠す</span><span class="sxs-lookup"><span data-stu-id="c9f7e-125">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="c9f7e-126">方法: 継承された変数を隠す</span><span class="sxs-lookup"><span data-stu-id="c9f7e-126">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="c9f7e-127">Shadows</span><span class="sxs-lookup"><span data-stu-id="c9f7e-127">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="c9f7e-128">Overrides</span><span class="sxs-lookup"><span data-stu-id="c9f7e-128">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="c9f7e-129">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="c9f7e-129">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="c9f7e-130">継承の基本</span><span class="sxs-lookup"><span data-stu-id="c9f7e-130">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
