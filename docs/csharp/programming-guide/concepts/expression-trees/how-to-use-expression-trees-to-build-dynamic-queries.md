---
title: 実行時の状態に基づくクエリの実行 (C#)
description: LINQ メソッドの呼び出し、またはこれらのメソッドに渡される式ツリーを変更することにより、コードで実行時の状態に応じて動的にクエリを実行するために使用できるさまざまな手法について説明します。
ms.date: 02/11/2021
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 1a3bbe8c9ba6752c541d69502b7c4ac020fd9708
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876722"
---
# <a name="querying-based-on-runtime-state-c"></a>実行時の状態に基づくクエリの実行 (C#)

データ ソースに対して <xref:System.Linq.IQueryable> または [IQueryable\<T>](<xref:System.Linq.IQueryable%601>) を定義するコードについて考えてみます。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Initialize":::

このコードを実行するたびに、同じクエリが実行されます。 実行時の状態に応じてさまざまなクエリを実行するコードが必要になる可能性があるため、これは多くの場合、あまり役に立ちません。 この記事では、実行時の状態に基づいて別のクエリを実行する方法について説明します。

## <a name="iqueryable--iqueryablet-and-expression-trees"></a>IQueryable または IQueryable\<T> および式ツリー

基本的に、<xref:System.Linq.IQueryable> には次の 2 つのコンポーネントがあります。

* <xref:System.Linq.IQueryable.Expression> &mdash; 式ツリーの形式である、現在のクエリのコンポーネントの言語およびデータソースに依存しない表現。
* <xref:System.Linq.IQueryable.Provider> &mdash; 現在のクエリを値または値のセットに具体化する方法を認識している LINQ プロバイダーのインスタンス。

動的なクエリのコンテキストでは、通常、プロバイダーは同じままとなります。クエリの式ツリーはクエリによって異なります。

式ツリーは変更できません。別の式ツリー &mdash; したがって、別のクエリ &mdash; が必要な場合は、既存の式ツリーを新しいもの (したがって、新しい <xref:System.Linq.IQueryable>) に変換する必要があります。

次のセクションでは、実行時の状態に応じて異なる方法でクエリを実行する特定の手法について説明します。

- 式ツリー内から実行時の状態を使用する
- 追加の LINQ メソッドを呼び出す
- LINQ メソッドに渡される式ツリーを変更する
- <xref:System.Linq.Expressions.Expression> でファクトリ メソッドを使用して、[Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) 式ツリー式を構築する
- <xref:System.Linq.IQueryable> の式ツリーにメソッド呼び出しノードを追加する
- 文字列を構築し、[動的 LINQ ライブラリ](https://dynamic-linq.net/)を使用する

## <a name="use-runtime-state-from-within-the-expression-tree"></a>式ツリー内から実行時の状態を使用する

LINQ プロバイダーでサポートされていると仮定した場合にクエリを動的に実行する最も簡単な方法は、次のコード例の `length` など、閉じ込められた変数を使用して、クエリ内の実行時の状態を直接参照することです。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Runtime_state_from_within_expression_tree":::

内部式ツリー &mdash;したがって、クエリ&mdash; は変更されていません。このクエリの場合は、`length` の値が変更されているため、異なる値が返されます。

## <a name="call-additional-linq-methods"></a>追加の LINQ メソッドを呼び出す

一般に、<xref:System.Linq.Queryable> の[組み込みの LINQ メソッド](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs)では、次の 2 つの手順を行います。

* メソッド呼び出しを表す <xref:System.Linq.Expressions.MethodCallExpression> で現在の式ツリーをラップする。
* ラップされた式ツリーをプロバイダーに戻し、プロバイダーの <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> メソッドを使用して値を返すか、<xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> メソッドを使用して変換されたクエリ オブジェクトを返す。

元のクエリを、[IQueryable\<T>](xref:System.Linq.IQueryable%601) を返すメソッドの結果に置き換えて、新しいクエリを取得できます。 次の例のように、実行時の状態に基づいて条件付きでこれを行うことができます。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Added_method_calls":::

## <a name="vary-the-expression-tree-passed-into-the-linq-methods"></a>LINQ メソッドに渡される式ツリーを変更する

実行時の状態に応じて、LINQ メソッドに異なる式を渡すことができます。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Varying_expressions":::

[LinqKit](http://www.albahari.com/nutshell/linqkit.aspx) の [PredicateBuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx) などのサードパーティ製ライブラリを使用して、さまざまなサブ式を構成することもできます。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compose_expressions":::

## <a name="construct-expression-trees-and-queries-using-factory-methods"></a>ファクトリ メソッドを使用して式ツリーとクエリを構築する

この時点までのすべての例では、コンパイル時に要素型 &mdash;`string`&mdash; (したがって、クエリの型 &mdash;`IQueryable<string>`) がわかっています。 要素型に関係なくクエリにコンポーネントを追加したり、要素型に応じて異なるコンポーネントを追加したりすることが、必要になる場合があります。 <xref:System.Linq.Expressions.Expression?displayProperty=fullName> でファクトリ メソッドを使用して、最初から式ツリーを作成し、実行時に特定の要素型に合わせて式を調整することができます。

### <a name="constructing-an-expressiontdelegate"></a>[Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) の構築

LINQ メソッドのいずれかに渡す式を構築する場合、実際には [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) のインスタンスを構築することになります。ここで、`TDelegate` は `Func<string, bool>`、`Action`、カスタム デリゲート型などの何らかのデリゲート型です。

[Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) は <xref:System.Linq.Expressions.LambdaExpression> から継承されます。これは、次のような完全なラムダ式を表します。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compiler_generated_expression_tree":::

<xref:System.Linq.Expressions.LambdaExpression> には次の 2 つのコンポーネントがあります。

* パラメーター リスト &mdash;`(string x)`&mdash; <xref:System.Linq.Expressions.LambdaExpression.Parameters> プロパティによって表されます
* 本文 &mdash;`x.StartsWith("a")`&mdash; <xref:System.Linq.Expressions.LambdaExpression.Body> プロパティによって表されます。

[Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) を構築するための基本的な手順は次のとおりです。

* <xref:System.Linq.Expressions.Expression.Parameter%2A> ファクトリ メソッドを使用して、ラムダ式内の各パラメーター (存在する場合) に <xref:System.Linq.Expressions.ParameterExpression> オブジェクトを定義する。

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_parameter":::

* 定義した <xref:System.Linq.Expressions.ParameterExpression> と、<xref:System.Linq.Expressions.Expression> のファクトリ メソッドを使用して、<xref:System.Linq.Expressions.LambdaExpression> の本体を作成します。 たとえば、`x.StartsWith("a")` を表す式はこのように構築できます。

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_body":::

* 適切な <xref:System.Linq.Expressions.Expression.Lambda%2A> ファクトリ メソッドのオーバーロードを使用して、コンパイル時に型指定された [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) にパラメーターと本文をラップする。

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_lambda":::

次のセクションでは、LINQ メソッドに渡す [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) を構築することが望ましいシナリオについて説明し、ファクトリ メソッドを使用してそれを行う方法の完全な例を示します。

### <a name="scenario"></a>シナリオ

たとえば、複数のエンティティ型があるとします。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Entities":::

これらのいずれかのエンティティ型については、`string` フィールドの 1 つに特定のテキストが含まれているエンティティのみをフィルター処理して返す必要があります。 `Person` については、`FirstName` と `LastName` のプロパティを検索する必要があります。

```csharp
string term = /* ... */;
var personsQry = new List<Person>()
    .AsQueryable()
    .Where(x => x.FirstName.Contains(term) || x.LastName.Contains(term));
```

しかし、`Car` については、`Model` プロパティのみを検索する必要があります。

```csharp
string term = /* ... */;
var carsQry = new List<Car>()
    .AsQueryable()
    .Where(x => x.Model.Contains(term));
```

`IQueryable<Person>` 用にカスタム関数を 1 つと、`IQueryable<Car>` 用にもう 1 つを記述することもできますが、次の関数では、特定の要素型に関係なく、このフィルターを既存のすべてのクエリに追加します。

### <a name="example"></a>例

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate":::

`TextFilter` 関数では [IQueryable\<T>](xref:System.Linq.IQueryable%601) (<xref:System.Linq.IQueryable> だけでなく) を受け取って返すため、テキスト フィルターの後にコンパイル時に型指定されたクエリ要素をさらに追加できます。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate_usage":::

## <a name="add-method-call-nodes-to-the-xrefsystemlinqiqueryables-expression-tree"></a><xref:System.Linq.IQueryable> の式ツリーにメソッド呼び出しノードを追加する

[IQueryable\<T>](xref:System.Linq.IQueryable%601) の代わりに <xref:System.Linq.IQueryable> がある場合、汎用 LINQ メソッドを直接呼び出すことはできません。 代替手段の 1 つは、上記のように内部式ツリーをビルドし、リフレクションを使用して、式ツリーに渡すときに適切な LINQ メソッドを呼び出すことです。

LINQ メソッドの呼び出しを表す <xref:System.Linq.Expressions.MethodCallExpression> でツリー全体をラップすることにより、LINQ メソッドの機能を複製することもできます。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_lambdaexpression":::

この場合、コンパイル時の `T` 汎用プレースホルダーがないため、[Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) の代わりに、コンパイル時の型情報を必要としない、<xref:System.Linq.Expressions.LambdaExpression> を生成する <xref:System.Linq.Expressions.Expression.Lambda%2A> オーバーロードを使用することに注意してください。

## <a name="the-dynamic-linq-library"></a>動的 LINQ ライブラリ

ファクトリ メソッドを使用した式ツリーの構築は比較的複雑です。文字列を作成する方が簡単です。 [動的 LINQ ライブラリ](https://dynamic-linq.net/)では、<xref:System.Linq.Queryable>で標準 LINQ メソッドに対応する <xref:System.Linq.IQueryable> の拡張メソッドのセットを公開し、式ツリーではなく[特殊な構文](https://dynamic-linq.net/expression-language)で文字列を受け入れます。 ライブラリで文字列から適切な式ツリーが生成され、結果として変換された <xref:System.Linq.IQueryable> を返すことができます。

たとえば、前の例は次のように書き換えることができます。

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Dynamic_linq":::

## <a name="see-also"></a>関連項目

- [式ツリー (C#)](./index.md)
- [式ツリーを実行する方法 (C#)](./how-to-execute-expression-trees.md)
- [実行時における述語フィルターの動的指定](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
