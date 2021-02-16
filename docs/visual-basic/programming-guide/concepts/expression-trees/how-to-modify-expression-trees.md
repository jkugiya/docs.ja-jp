---
description: '詳細情報: 方法:式ツリーを変更する (Visual Basic)'
title: '方法: 式ツリーを変更する'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 13098f5588fe44be8e57c9be52a9cfe5f7cd661f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455900"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="28ed6-103">方法: 式ツリーを変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28ed6-103">How to: Modify Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="28ed6-104">このトピックでは、式ツリーを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-104">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="28ed6-105">式ツリーは変更不可であるため、直接変更を加えることができません。</span><span class="sxs-lookup"><span data-stu-id="28ed6-105">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="28ed6-106">式ツリーを変更するには、既存の式ツリーのコピーを作成する必要があります。コピーを作成する際に、必要な変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="28ed6-106">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="28ed6-107"><xref:System.Linq.Expressions.ExpressionVisitor> クラスを使用して、既存の式ツリーを走査し、走査した各ノードをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="28ed6-107">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>

## <a name="to-modify-an-expression-tree"></a><span data-ttu-id="28ed6-108">式ツリーを変更するには</span><span class="sxs-lookup"><span data-stu-id="28ed6-108">To modify an expression tree</span></span>

1. <span data-ttu-id="28ed6-109">新しい **コンソール アプリケーション** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-109">Create a new **Console Application** project.</span></span>

2. <span data-ttu-id="28ed6-110">ファイルに `System.Linq.Expressions` 名前空間の `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-110">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

3. <span data-ttu-id="28ed6-111">`AndAlsoModifier` クラスをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-111">Add the `AndAlsoModifier` class to your project.</span></span>

    ```vb
    Public Class AndAlsoModifier
        Inherits ExpressionVisitor

        Public Function Modify(ByVal expr As Expression) As Expression
            Return Visit(expr)
        End Function

        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression
            If b.NodeType = ExpressionType.AndAlso Then
                Dim left = Me.Visit(b.Left)
                Dim right = Me.Visit(b.Right)

                ' Make this binary expression an OrElse operation instead
                ' of an AndAlso operation.
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _
                                             b.IsLiftedToNull, b.Method)
            End If

            Return MyBase.VisitBinary(b)
        End Function
    End Class
    ```

    <span data-ttu-id="28ed6-112">このクラスは、`AND` 条件演算を表す式を変更するための特別なクラスで、<xref:System.Linq.Expressions.ExpressionVisitor> クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-112">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="28ed6-113">このクラスによって条件 `AND` が条件 `OR` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="28ed6-113">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="28ed6-114">そのために、クラスは基本データ型の <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> メソッドをオーバーライドします。`AND` 条件式は二項式で表されるためです。</span><span class="sxs-lookup"><span data-stu-id="28ed6-114">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="28ed6-115">`VisitBinary` メソッドでは、渡される式が `AND` 条件演算を表す場合、`AND` 条件演算子ではなく `OR` 条件演算子を含む新しい式がコードによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="28ed6-115">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="28ed6-116">`VisitBinary` に渡される式が `AND` 条件演算を表さない場合は、基底クラスの実装が延期されます。</span><span class="sxs-lookup"><span data-stu-id="28ed6-116">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="28ed6-117">基底クラスのメソッドによって、渡された式ツリーに似たノードが作成されますが、そのノードのサブツリーは、ビジターによって再帰的に作成される式ツリーに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="28ed6-117">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>

4. <span data-ttu-id="28ed6-118">ファイルに `System.Linq.Expressions` 名前空間の `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-118">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

5. <span data-ttu-id="28ed6-119">式ツリーを作成し、それをメソッドに渡して変更するコードを、Module1.vb ファイルの `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-119">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>

    ```vb
    Dim expr As Expression(Of Func(Of String, Boolean)) = _
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")

    Console.WriteLine(expr)

    Dim modifier As New AndAlsoModifier()
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))

    Console.WriteLine(modifiedExpr)

    ' This code produces the following output:
    ' name => ((name.Length > 10) && name.StartsWith("G"))
    ' name => ((name.Length > 10) || name.StartsWith("G"))
    ```

    <span data-ttu-id="28ed6-120">次のコードは、`AND` 条件演算を含む式を作成し、</span><span class="sxs-lookup"><span data-stu-id="28ed6-120">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="28ed6-121">`AndAlsoModifier` クラスのインスタンスを作成して、このクラスの `Modify` メソッドにその式を渡します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-121">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="28ed6-122">元の式ツリーと変更された式ツリーの両方が出力され、変更内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="28ed6-122">Both the original and the modified expression trees are outputted to show the change.</span></span>

6. <span data-ttu-id="28ed6-123">アプリケーションをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="28ed6-123">Compile and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="28ed6-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="28ed6-124">See also</span></span>

- [<span data-ttu-id="28ed6-125">方法: 式ツリーを実行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28ed6-125">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
- [<span data-ttu-id="28ed6-126">式ツリー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28ed6-126">Expression Trees (Visual Basic)</span></span>](index.md)
