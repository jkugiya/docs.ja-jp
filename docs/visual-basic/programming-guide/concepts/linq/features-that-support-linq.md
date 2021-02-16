---
description: '詳細情報: LINQ をサポートする Visual Basic の機能'
title: LINQ をサポートする機能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 58862ac4083bcd58ee08ef1afeebf95541c53e98
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428639"
---
# <a name="visual-basic-features-that-support-linq"></a><span data-ttu-id="17fd9-103">LINQ をサポートする Visual Basic の機能</span><span class="sxs-lookup"><span data-stu-id="17fd9-103">Visual Basic Features That Support LINQ</span></span>

<span data-ttu-id="17fd9-104">統合言語クエリ (LINQ) という名前は、クエリ構文などの言語コンストラクトを言語の中で直接サポートする、Visual Basic のテクノロジをいいます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-104">The name Language-Integrated Query (LINQ) refers to technology in Visual Basic that supports query syntax and other language constructs directly in the language.</span></span> <span data-ttu-id="17fd9-105">LINQ を使用すれば、外部のデータ ソースを照会するために新しい言語を習得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="17fd9-105">With LINQ, you do not have to learn a new language to query against an external data source.</span></span> <span data-ttu-id="17fd9-106">Visual Basic を使用して、リレーショナル データベースや XML ストア、オブジェクトにデータを照会することができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-106">You can query against data in relational databases, XML stores, or objects by using Visual Basic.</span></span> <span data-ttu-id="17fd9-107">このようにクエリの機能を言語に統合することで、構文エラーやタイプ セーフのチェックをコンパイル時に行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="17fd9-107">This integration of query capabilities into the language enables compile-time checking for syntax errors and type safety.</span></span> <span data-ttu-id="17fd9-108">また、多くの場合、既にある知識だけで、豊富で多彩なクエリを Visual Basic で記述することができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-108">This integration also ensures that you already know most of what you have to know to write rich, varied queries in Visual Basic.</span></span>  
  
 <span data-ttu-id="17fd9-109">以降の各セクションでは、これから皆さんが入門ドキュメントやコード例、サンプル アプリケーションを読むために最低限必要な知識が身に付くよう、LINQ をサポートする言語コンストラクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="17fd9-109">The following sections describe the language constructs that support LINQ in enough detail to enable you to get started in reading the introductory documentation, code examples, and sample applications.</span></span> <span data-ttu-id="17fd9-110">また、リンク先のドキュメントもご覧ください。さまざまな言語機能がどのように組み合わさって統合言語クエリが実現されているかについて詳しく説明されています。</span><span class="sxs-lookup"><span data-stu-id="17fd9-110">You can also click the links to find more detailed explanations of how the language features come together to enable language-integrated query.</span></span> <span data-ttu-id="17fd9-111">まずは、「[チュートリアル: Visual Basic でのクエリの作成](walkthrough-writing-queries.md)」を読むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="17fd9-111">A good place to start is [Walkthrough: Writing Queries in Visual Basic](walkthrough-writing-queries.md).</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="17fd9-112">クエリ式</span><span class="sxs-lookup"><span data-stu-id="17fd9-112">Query Expressions</span></span>  

 <span data-ttu-id="17fd9-113">Visual Basic のクエリ式は、SQL や XQuery と同様の宣言型構文で表現することができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-113">Query expressions in Visual Basic can be expressed in a declarative syntax similar to that of SQL or XQuery.</span></span> <span data-ttu-id="17fd9-114">クエリ構文は、コンパイル時に、LINQ プロバイダーの標準クエリ演算子拡張メソッドの実装に対するメソッド呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-114">At compile time, query syntax is converted into method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="17fd9-115">アプリケーションは、`Imports` ステートメントを使用して適切な名前空間を指定することにより、スコープ内の標準クエリ演算子を制御します。</span><span class="sxs-lookup"><span data-stu-id="17fd9-115">Applications control which standard query operators are in scope by specifying the appropriate namespace with an `Imports` statement.</span></span> <span data-ttu-id="17fd9-116">次に示したのは、Visual Basic のクエリ式の構文例です。</span><span class="sxs-lookup"><span data-stu-id="17fd9-116">Syntax for a Visual Basic query expression looks like this:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="17fd9-117">詳細については、「[Visual Basic における LINQ の概要](../../language-features/linq/introduction-to-linq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17fd9-117">For more information, see [Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="implicitly-typed-variables"></a><span data-ttu-id="17fd9-118">暗黙的に型指定された変数</span><span class="sxs-lookup"><span data-stu-id="17fd9-118">Implicitly Typed Variables</span></span>  

 <span data-ttu-id="17fd9-119">変数を宣言して初期化するときに、型を明示的に指定する代わりに、コンパイラに型を推測させて代入することができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-119">Instead of explicitly specifying a type when you declare and initialize a variable, you can enable the compiler to infer and assign the type.</span></span> <span data-ttu-id="17fd9-120">これを "*ローカル型推論*" といいます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-120">This is referred to as *local type inference*.</span></span>  
  
 <span data-ttu-id="17fd9-121">明示的に型が指定される変数と同様、型が推測される変数も厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-121">Variables whose types are inferred are strongly typed, just like variables whose type you specify explicitly.</span></span> <span data-ttu-id="17fd9-122">ローカル型推論が正常に機能するのは、メソッド本体内にローカル変数を定義している場合のみです。</span><span class="sxs-lookup"><span data-stu-id="17fd9-122">Local type inference works only when you are defining a local variable inside a method body.</span></span> <span data-ttu-id="17fd9-123">詳細については、「[Option Infer ステートメント](../../../language-reference/statements/option-infer-statement.md)」と[ローカル型推論](../../language-features/variables/local-type-inference.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="17fd9-123">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="17fd9-124">ローカル型推論の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="17fd9-124">The following example illustrates local type inference.</span></span> <span data-ttu-id="17fd9-125">この例を使用するには、`Option Infer` を `On` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17fd9-125">To use this example, you must set `Option Infer` to `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="17fd9-126">LINQ クエリに必要な匿名型も、ローカル型推論で作成することができます。匿名型については、このセクションで後述します。</span><span class="sxs-lookup"><span data-stu-id="17fd9-126">Local type inference also makes it possible to create anonymous types, which are described later in this section and are necessary for LINQ queries.</span></span>  
  
 <span data-ttu-id="17fd9-127">以下の LINQ の例では、`Option Infer` が `On` または `Off` の場合に型の推定が行われます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-127">In the following LINQ example, type inference occurs if `Option Infer` is either `On` or `Off`.</span></span> <span data-ttu-id="17fd9-128">`Option Infer` が `Off` で、なおかつ `Option Strict` が `On` の場合、コンパイル時のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="17fd9-128">A compile-time error occurs if `Option Infer` is `Off` and `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a><span data-ttu-id="17fd9-129">オブジェクト初期化子</span><span class="sxs-lookup"><span data-stu-id="17fd9-129">Object Initializers</span></span>  

 <span data-ttu-id="17fd9-130">オブジェクト初期化子は、クエリ式の中で、クエリの結果を保持する匿名型を作成する必要があるときに使用します。</span><span class="sxs-lookup"><span data-stu-id="17fd9-130">Object initializers are used in query expressions when you have to create an anonymous type to hold the results of a query.</span></span> <span data-ttu-id="17fd9-131">また、名前付きの型のオブジェクトをクエリの外側で初期化する際にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-131">They also can be used to initialize objects of named types outside of queries.</span></span> <span data-ttu-id="17fd9-132">オブジェクト初期化子を使用すれば、コンストラクターを明示的に呼び出さなくても、オブジェクトを 1 行で初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-132">By using an object initializer, you can initialize an object in a single line without explicitly calling a constructor.</span></span> <span data-ttu-id="17fd9-133">`Customer` という名前のクラスがあるとしましょう。このクラスには、パブリック プロパティである `Name` と `Phone` のほか、いくつかのプロパティがあります。この場合、オブジェクト初期化子を次のように使用することができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-133">Assuming that you have a class named `Customer` that has public `Name` and `Phone` properties, along with other properties, an object initializer can be used in this manner:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 <span data-ttu-id="17fd9-134">詳細については、「[オブジェクト初期化子: 名前付きの型と匿名型](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17fd9-134">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="17fd9-135">匿名型</span><span class="sxs-lookup"><span data-stu-id="17fd9-135">Anonymous Types</span></span>  

 <span data-ttu-id="17fd9-136">クエリの結果に含めたい一連のプロパティを 1 つの要素として一時的にグループ化する場合に、匿名型は高い利便性を発揮します。</span><span class="sxs-lookup"><span data-stu-id="17fd9-136">Anonymous types provide a convenient way to temporarily group a set of properties into an element that you want to include in a query result.</span></span> <span data-ttu-id="17fd9-137">その要素に対して名前付きのデータ型を定義しなくても、選択可能なフィールドの組み合わせをクエリの中で自由に、かつ任意の順序で選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-137">This enables you to choose any combination of available fields in the query, in any order, without defining a named data type for the element.</span></span>  
  
 <span data-ttu-id="17fd9-138">"*匿名型*" は、コンパイラによって動的に構築されます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-138">An *anonymous type* is constructed dynamically by the compiler.</span></span> <span data-ttu-id="17fd9-139">型の名前はコンパイラによって割り当てられ、また、コンパイルのたびに変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17fd9-139">The name of the type is assigned by the compiler, and it might change with each new compilation.</span></span> <span data-ttu-id="17fd9-140">したがって、その名前を直接使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="17fd9-140">Therefore, the name cannot be used directly.</span></span> <span data-ttu-id="17fd9-141">匿名型の初期化方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="17fd9-141">Anonymous types are initialized in the following way:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 <span data-ttu-id="17fd9-142">詳細については、「[匿名型](../../language-features/objects-and-classes/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17fd9-142">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="17fd9-143">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="17fd9-143">Extension Methods</span></span>  

 <span data-ttu-id="17fd9-144">データ型とインターフェイスには、その定義の外側から、拡張メソッドを通じてメソッドを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-144">Extension methods enable you to add methods to a data type or interface from outside the definition.</span></span> <span data-ttu-id="17fd9-145">この機能を使用すると、既存の型を実際に変更しなくても、その型に新しいメソッドを実質的に追加できます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-145">This feature enables you to, in effect, add new methods to an existing type without actually modifying the type.</span></span> <span data-ttu-id="17fd9-146">標準クエリ演算子は、それ自体が、<xref:System.Collections.Generic.IEnumerable%601> を実装する任意の型で LINQ クエリ機能を実現する拡張メソッドのセットです。</span><span class="sxs-lookup"><span data-stu-id="17fd9-146">The standard query operators are themselves a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="17fd9-147"><xref:System.Collections.Generic.IEnumerable%601> に対する拡張機能としては、他にも <xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Union%2A>、<xref:System.Linq.Enumerable.Intersect%2A> などがあります。</span><span class="sxs-lookup"><span data-stu-id="17fd9-147">Other extensions to <xref:System.Collections.Generic.IEnumerable%601> include <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 <span data-ttu-id="17fd9-148">次の拡張メソッドは、<xref:System.String> クラスに Print メソッドを追加するものです。</span><span class="sxs-lookup"><span data-stu-id="17fd9-148">The following extension method adds a print method to the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 <span data-ttu-id="17fd9-149">このメソッドの呼び出し方は、<xref:System.String> の通常のインスタンス メソッドと同様です。</span><span class="sxs-lookup"><span data-stu-id="17fd9-149">The method is called like an ordinary instance method of <xref:System.String>:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 <span data-ttu-id="17fd9-150">詳細については、「[拡張メソッド](../../language-features/procedures/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17fd9-150">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="17fd9-151">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="17fd9-151">Lambda Expressions</span></span>  

 <span data-ttu-id="17fd9-152">ラムダ式は、単一の値を計算して返す、名前を持たない関数です。</span><span class="sxs-lookup"><span data-stu-id="17fd9-152">A lambda expression is a function without a name that calculates and returns a single value.</span></span> <span data-ttu-id="17fd9-153">名前付きの関数とは異なり、ラムダ式は、定義と実行を同時に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-153">Unlike named functions, a lambda expression can be defined and executed at the same time.</span></span> <span data-ttu-id="17fd9-154">次の例では、"4" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-154">The following example displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="17fd9-155">ラムダ式の定義を変数名に代入しておけば、その名前を使用して関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-155">You can assign the lambda expression definition to a variable name and then use the name to call the function.</span></span> <span data-ttu-id="17fd9-156">次の例でも、"4" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-156">The following example also displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 <span data-ttu-id="17fd9-157">LINQ では、ラムダ式が、多くの標準クエリ演算子の基盤となっています。</span><span class="sxs-lookup"><span data-stu-id="17fd9-157">In LINQ, lambda expressions underlie many of the standard query operators.</span></span> <span data-ttu-id="17fd9-158">基本的なクエリ メソッド (`Where`、`Select`、`Order By`、`Take While` など) で定義されている計算を取り込むためのラムダ式が、コンパイラによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-158">The compiler creates lambda expressions to capture the calculations that are defined in fundamental query methods such as `Where`, `Select`, `Order By`, `Take While`, and others.</span></span>  
  
 <span data-ttu-id="17fd9-159">たとえば、次のコードは、学生のリストからすべての最上級生を返すクエリの定義です。</span><span class="sxs-lookup"><span data-stu-id="17fd9-159">For example, the following code defines a query that returns all senior students from a list of students.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 <span data-ttu-id="17fd9-160">このクエリ定義は、次の例のようなコードにコンパイルされます。このコードでは、2 つのラムダ式を使用して `Where` と `Select` の引数が指定されています。</span><span class="sxs-lookup"><span data-stu-id="17fd9-160">The query definition is compiled into code that is similar to the following example, which uses two lambda expressions to specify the arguments for `Where` and `Select`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 <span data-ttu-id="17fd9-161">どちらのバージョンも、`For Each` ループを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="17fd9-161">Either version can be run by using a `For Each` loop:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 <span data-ttu-id="17fd9-162">詳細については、「[ラムダ式](../../language-features/procedures/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17fd9-162">For more information, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17fd9-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="17fd9-163">See also</span></span>

- [<span data-ttu-id="17fd9-164">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17fd9-164">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="17fd9-165">Visual Basic の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="17fd9-165">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="17fd9-166">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17fd9-166">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="17fd9-167">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="17fd9-167">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="17fd9-168">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="17fd9-168">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
