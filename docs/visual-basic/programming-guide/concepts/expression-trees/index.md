---
description: '詳細情報: 式ツリー (Visual Basic)'
title: 式ツリー
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: 7fa4f36334a5a951cbe86c6db80af77db40e245a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462257"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="ff97e-103">式ツリー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff97e-103">Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="ff97e-104">式ツリーでは、コードがツリー状のデータ構造で表示されます。各ノードは 1 つの式に対応しています。たとえば、メソッドの呼び出しや `x < y` のような二項演算などです。</span><span class="sxs-lookup"><span data-stu-id="ff97e-104">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="ff97e-105">式ツリーで表されるコードはコンパイルおよび実行できます。</span><span class="sxs-lookup"><span data-stu-id="ff97e-105">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="ff97e-106">これによって、実行可能なコードの動的な変更、さまざまなデータベースでの LINQ クエリの実行、および動的クエリの作成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="ff97e-106">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="ff97e-107">LINQ の式ツリーの詳細については、「[方法: 式ツリーを使用して動的クエリをビルドする (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff97e-107">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="ff97e-108">また、式ツリーを動的言語ランタイム (DLR) に使用することで、動的言語と .NET Framework 間の相互運用性が実現し、コンパイラ ライターで Microsoft Intermediate language (MSIL) ではなく式ツリーを出力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff97e-108">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="ff97e-109">DLR の詳細については、「[動的言語ランタイムの概要](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff97e-109">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="ff97e-110">匿名のラムダ式に基づいて、C# と Visual Basic コンパイラで式ツリーを作成できます。または、<xref:System.Linq.Expressions> 名前空間を使用して手動で式ツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ff97e-110">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="ff97e-111">ラムダ式からの式ツリーの作成</span><span class="sxs-lookup"><span data-stu-id="ff97e-111">Creating Expression Trees from Lambda Expressions</span></span>  

 <span data-ttu-id="ff97e-112">ラムダ式が <xref:System.Linq.Expressions.Expression%601> 型の変数に割り当てられている場合、コンパイラはラムダ式を表す式ツリーを構築するコードを出力します。</span><span class="sxs-lookup"><span data-stu-id="ff97e-112">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="ff97e-113">Visual Basic コンパイラは、式形式のラムダ (つまり単一行のラムダ) からのみ式ツリーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ff97e-113">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="ff97e-114">ステートメント形式のラムダ (つまり複数行のラムダ) は解析できません。</span><span class="sxs-lookup"><span data-stu-id="ff97e-114">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="ff97e-115">Visual Basic のラムダ式の詳細については、「[ラムダ式](../../language-features/procedures/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff97e-115">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="ff97e-116">次のコード例は、ラムダ式 `Function(num) num < 5` を表す式ツリーを Visual Basic コンパイラで作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff97e-116">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="ff97e-117">API を使用した式ツリーの作成</span><span class="sxs-lookup"><span data-stu-id="ff97e-117">Creating Expression Trees by Using the API</span></span>  

 <span data-ttu-id="ff97e-118">API を使用して式ツリーを作成するには、<xref:System.Linq.Expressions.Expression> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ff97e-118">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="ff97e-119">このクラスには、特定の型を持つ式ツリー ノードを作成する静的ファクトリ メソッドが含まれます。たとえば、変数またはパラメーターを表す <xref:System.Linq.Expressions.ParameterExpression> や、メソッドの呼び出しを表す <xref:System.Linq.Expressions.MethodCallExpression> などです。</span><span class="sxs-lookup"><span data-stu-id="ff97e-119">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="ff97e-120"><xref:System.Linq.Expressions.ParameterExpression>、<xref:System.Linq.Expressions.MethodCallExpression> などの式固有の型も、<xref:System.Linq.Expressions> 名前空間で定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff97e-120"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="ff97e-121">これらの型は、<xref:System.Linq.Expressions.Expression> 抽象型から派生したものです。</span><span class="sxs-lookup"><span data-stu-id="ff97e-121">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="ff97e-122">次のコード例は、API を使用して、ラムダ式 `Function(num) num < 5` を表す式ツリーを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff97e-122">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="ff97e-123">.NET Framework 4 以降の式ツリー API は、割り当て式、制御フロー式 (ループ、条件ブロック)、および `try-catch` ブロックもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ff97e-123">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="ff97e-124">API を使用すると、Visual Basic コンパイラのラムダ式から作成できる式ツリーよりも複雑な式ツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ff97e-124">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="ff97e-125">次の例は、数値の階乗を計算する式ツリーを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff97e-125">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="ff97e-126">詳細については、「[Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/) (Visual Studio 2010 での式ツリーによる動的メソッドの生成)」を参照し、Visual Studio 2010 以降のバージョンについても同じ方法を適用してください。</span><span class="sxs-lookup"><span data-stu-id="ff97e-126">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="ff97e-127">式ツリーの解析</span><span class="sxs-lookup"><span data-stu-id="ff97e-127">Parsing Expression Trees</span></span>  

 <span data-ttu-id="ff97e-128">次のコード例は、ラムダ式 `Function(num) num < 5` を表す式ツリーを各部分に分解する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff97e-128">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="ff97e-129">式ツリーの不変性</span><span class="sxs-lookup"><span data-stu-id="ff97e-129">Immutability of Expression Trees</span></span>  

 <span data-ttu-id="ff97e-130">式ツリーは変更できません。</span><span class="sxs-lookup"><span data-stu-id="ff97e-130">Expression trees should be immutable.</span></span> <span data-ttu-id="ff97e-131">つまり、式ツリーを変更するには、既存の式ツリーをコピーしてツリー内のノードを置き換えることで、新しい式ツリーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff97e-131">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="ff97e-132">式ツリー ビジターを使用して、既存の式ツリーを走査することができます。</span><span class="sxs-lookup"><span data-stu-id="ff97e-132">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="ff97e-133">詳細については、「[方法:式ツリーを変更する (Visual Basic)](how-to-modify-expression-trees.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff97e-133">For more information, see [How to: Modify Expression Trees (Visual Basic)](how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="ff97e-134">式ツリーのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ff97e-134">Compiling Expression Trees</span></span>  

 <span data-ttu-id="ff97e-135"><xref:System.Linq.Expressions.Expression%601> 型に含まれる <xref:System.Linq.Expressions.Expression%601.Compile%2A> メソッドにより、式ツリーが表すコードを実行可能なデリゲートにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ff97e-135">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="ff97e-136">次のコード例は、式ツリーをコンパイルして結果のコードを実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff97e-136">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="ff97e-137">詳細については、「[方法:式ツリーを実行する (Visual Basic)](how-to-execute-expression-trees.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff97e-137">For more information, see [How to: Execute Expression Trees (Visual Basic)](how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff97e-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff97e-138">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="ff97e-139">方法: 式ツリーを実行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff97e-139">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
- [<span data-ttu-id="ff97e-140">方法: 式ツリーを変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff97e-140">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
- [<span data-ttu-id="ff97e-141">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="ff97e-141">Lambda Expressions</span></span>](../../language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="ff97e-142">動的言語ランタイムの概要</span><span class="sxs-lookup"><span data-stu-id="ff97e-142">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="ff97e-143">プログラミングの概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff97e-143">Programming Concepts (Visual Basic)</span></span>](../index.md)
