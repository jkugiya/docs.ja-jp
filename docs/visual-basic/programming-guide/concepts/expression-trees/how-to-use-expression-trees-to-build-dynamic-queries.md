---
title: 実行時の状態に基づくクエリの実行 (Visual Basic)
description: LINQ メソッドの呼び出し、またはこれらのメソッドに渡される式ツリーを変更することにより、コードで実行時の状態に応じて動的にクエリを実行するために使用できるさまざまな手法について説明します。
ms.date: 02/14/2021
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: c9f57950b2c26c0cca798ab632da90bf9f6c519a
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584844"
---
# <a name="querying-based-on-runtime-state-visual-basic"></a>実行時の状態に基づくクエリの実行 (Visual Basic)

データ ソースに対して <xref:System.Linq.IQueryable> または [IQueryable(Of T)](<xref:System.Linq.IQueryable%601>) が定義されているコードについて考えてみます。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Initialize":::

このコードを実行するたびに、同じクエリが実行されます。 実行時の状態に応じてさまざまなクエリを実行するコードが必要になる可能性があるため、これは多くの場合、あまり役に立ちません。 この記事では、実行時の状態に基づいて別のクエリを実行する方法について説明します。

## <a name="iqueryable--iqueryableof-t-and-expression-trees"></a>IQueryable または IQueryable(Of T) と式ツリー

基本的に、<xref:System.Linq.IQueryable> には次の 2 つのコンポーネントがあります。

* <xref:System.Linq.IQueryable.Expression> &mdash; 式ツリーの形式である、現在のクエリのコンポーネントの言語およびデータソースに依存しない表現。
* <xref:System.Linq.IQueryable.Provider> &mdash; 現在のクエリを値または値のセットに具体化する方法を認識している LINQ プロバイダーのインスタンス。

動的なクエリのコンテキストでは、通常、プロバイダーは同じままとなります。クエリの式ツリーはクエリによって異なります。

式ツリーは変更できません。別の式ツリー &mdash; したがって、別のクエリ &mdash; が必要な場合は、既存の式ツリーを新しいもの (したがって、新しい <xref:System.Linq.IQueryable>) に変換する必要があります。

次のセクションでは、実行時の状態に応じて異なる方法でクエリを実行する特定の手法について説明します。

- 式ツリー内から実行時の状態を使用する
- 追加の LINQ メソッドを呼び出す
- LINQ メソッドに渡される式ツリーを変更する
- <xref:System.Linq.Expressions.Expression> でファクトリ メソッドを使用して、[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) 式ツリー式を作成する
- <xref:System.Linq.IQueryable> の式ツリーにメソッド呼び出しノードを追加する
- 文字列を構築し、[動的 LINQ ライブラリ](https://dynamic-linq.net/)を使用する

## <a name="use-runtime-state-from-within-the-expression-tree"></a>式ツリー内から実行時の状態を使用する

LINQ プロバイダーでサポートされていると仮定した場合にクエリを動的に実行する最も簡単な方法は、次のコード例の `length` など、閉じ込められた変数を使用して、クエリ内の実行時の状態を直接参照することです。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Runtime_state_from_within_expression_tree":::

内部式ツリー &mdash;したがって、クエリ&mdash; は変更されていません。このクエリの場合は、`length` の値が変更されているため、異なる値が返されます。

## <a name="call-additional-linq-methods"></a>追加の LINQ メソッドを呼び出す

一般に、<xref:System.Linq.Queryable> の[組み込みの LINQ メソッド](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs)では、次の 2 つの手順を行います。

* メソッド呼び出しを表す <xref:System.Linq.Expressions.MethodCallExpression> で現在の式ツリーをラップする。
* ラップされた式ツリーをプロバイダーに戻し、プロバイダーの <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> メソッドを使用して値を返すか、<xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> メソッドを使用して変換されたクエリ オブジェクトを返す。

元のクエリを、[IQueryable(Of T)](xref:System.Linq.IQueryable%601) を返すメソッドの結果に置き換えて、新しいクエリを取得できます。 次の例のように、実行時の状態に基づいて条件付きでこれを行うことができます。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Added_method_calls":::

## <a name="vary-the-expression-tree-passed-into-the-linq-methods"></a>LINQ メソッドに渡される式ツリーを変更する

実行時の状態に応じて、LINQ メソッドに異なる式を渡すことができます。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Varying_expressions":::

[LinqKit](http://www.albahari.com/nutshell/linqkit.aspx) の [PredicateBuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx) などのサードパーティ製ライブラリを使用して、さまざまなサブ式を構成することもできます。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Compose_expression":::

## <a name="construct-expression-trees-and-queries-using-factory-methods"></a>ファクトリ メソッドを使用して式ツリーとクエリを構築する

この時点までのすべての例では、コンパイル時に要素型 &mdash;`String`&mdash; (したがって、クエリの型 &mdash;`IQueryable(Of String)`) がわかっています。 要素型に関係なくクエリにコンポーネントを追加したり、要素型に応じて異なるコンポーネントを追加したりすることが、必要になる場合があります。 <xref:System.Linq.Expressions.Expression?displayProperty=fullName> でファクトリ メソッドを使用して、最初から式ツリーを作成し、実行時に特定の要素型に合わせて式を調整することができます。

### <a name="constructing-an-expressionof-tdelegate"></a>[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) の構築

LINQ メソッドのいずれかに渡す式を構築する場合、実際には [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) のインスタンスを構築します。`TDelegate` は、`Func(Of String, Boolean)`、`Action`、カスタム デリゲート型などの、何らかのデリゲート型です。

[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) は、次のような完全なラムダ式を表す <xref:System.Linq.Expressions.LambdaExpression> から継承されます。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Compiler_generated":::

<xref:System.Linq.Expressions.LambdaExpression> には次の 2 つのコンポーネントがあります。

* パラメーター リスト &mdash;`(x As String)`&mdash; <xref:System.Linq.Expressions.LambdaExpression.Parameters> プロパティによって表されます
* 本文 &mdash;`x.StartsWith("a")`&mdash; <xref:System.Linq.Expressions.LambdaExpression.Body> プロパティによって表されます。

[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) を構築する基本的な手順は次のとおりです。

* <xref:System.Linq.Expressions.Expression.Parameter%2A> ファクトリ メソッドを使用して、ラムダ式内の各パラメーター (存在する場合) に <xref:System.Linq.Expressions.ParameterExpression> オブジェクトを定義する。

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_parameter":::

* 定義した <xref:System.Linq.Expressions.ParameterExpression> と、<xref:System.Linq.Expressions.Expression> のファクトリ メソッドを使用して、<xref:System.Linq.Expressions.LambdaExpression> の本体を作成します。 たとえば、`x.StartsWith("a")` を表す式はこのように構築できます。

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_body":::

* 適切な <xref:System.Linq.Expressions.Expression.Lambda%2A> ファクトリ メソッドのオーバーロードを使用して、コンパイル時に型指定される [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) にパラメーターと本文をラップします。

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_lambda":::

次のセクションでは、LINQ メソッドに渡す [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) を構築することが望ましいシナリオについて説明し、ファクトリ メソッドを使用してそれを行う方法の完全な例を示します。

### <a name="scenario"></a>シナリオ

たとえば、複数のエンティティ型があるとします。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Entities.vb":::

これらのいずれかのエンティティ型については、`string` フィールドの 1 つに特定のテキストが含まれているエンティティのみをフィルター処理して返す必要があります。 `Person` については、`FirstName` と `LastName` のプロパティを検索する必要があります。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="PersonsQry":::

しかし、`Car` については、`Model` プロパティのみを検索する必要があります。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="CarsQry":::

`IQueryable(Of Person)` 用にカスタム関数を 1 つと、`IQueryable(Of Car)` 用にもう 1 つを記述することもできますが、次の関数では、特定の要素型に関係なく、このフィルターを既存のすべてのクエリに追加します。

### <a name="example"></a>例

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_expression_of_tdelegate":::

`TextFilter` 関数は [IQueryable(Of T)](xref:System.Linq.IQueryable%601) (<xref:System.Linq.IQueryable> だけでなく) を受け取って返すため、コンパイル時に型指定されるクエリ要素をテキスト フィルターの後にさらに追加できます。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_expression_of_tdelegate_usage":::

## <a name="add-method-call-nodes-to-the-xrefsystemlinqiqueryables-expression-tree"></a><xref:System.Linq.IQueryable> の式ツリーにメソッド呼び出しノードを追加する

[IQueryable(Of T)](xref:System.Linq.IQueryable%601) の代わりに <xref:System.Linq.IQueryable> を使用する場合は、汎用 LINQ メソッドを直接呼び出すことはできません。 代替手段の 1 つは、上記のように内部式ツリーをビルドし、リフレクションを使用して、式ツリーに渡すときに適切な LINQ メソッドを呼び出すことです。

LINQ メソッドの呼び出しを表す <xref:System.Linq.Expressions.MethodCallExpression> でツリー全体をラップすることにより、LINQ メソッドの機能を複製することもできます。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_lambdaexpression":::

この場合、コンパイル時の `T` 汎用プレースホルダーがないため、コンパイル時に型情報が必要なく、[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) の代わりに <xref:System.Linq.Expressions.LambdaExpression> が生成される、<xref:System.Linq.Expressions.Expression.Lambda%2A> のオーバーロードを使用することに注意してください。

## <a name="the-dynamic-linq-library"></a>動的 LINQ ライブラリ

ファクトリ メソッドを使用した式ツリーの構築は比較的複雑です。文字列を作成する方が簡単です。 [動的 LINQ ライブラリ](https://dynamic-linq.net/)では、<xref:System.Linq.Queryable>で標準 LINQ メソッドに対応する <xref:System.Linq.IQueryable> の拡張メソッドのセットを公開し、式ツリーではなく[特殊な構文](https://dynamic-linq.net/expression-language)で文字列を受け入れます。 ライブラリで文字列から適切な式ツリーが生成され、結果として変換された <xref:System.Linq.IQueryable> を返すことができます。

たとえば、前の例 (式ツリーの構築を含む) は次のように書き換えることができます。

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Dynamic_linq":::

## <a name="see-also"></a>関連項目

- [式ツリー (Visual Basic)](index.md)
- [方法: 式ツリーを実行する (Visual Basic)](how-to-execute-expression-trees.md)
