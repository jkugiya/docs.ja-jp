---
title: C# のコーディング規則 - C# プログラミング ガイド
description: C# のコーディング規則について説明します。 コーディング規則によってコードの外観に一貫性がもたらされ、コードのコピー、変更、保守が容易になります。
ms.date: 03/31/2021
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.openlocfilehash: 019bf02ea3cdfec2c4ae0d73b5b375781c5fcd9a
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231324"
---
# <a name="c-coding-conventions-c-programming-guide"></a>C# のコーディング規則 (C# プログラミング ガイド)

コーディング規則には、次の目的があります。  
  
- コードの見た目が統一されるため、コードを読むときに、レイアウトではなく内容に重点を置くことができます。  
  
- これにより、経験に基づいて推測することで、コードをより迅速に理解することができます。  
  
- コードのコピー、変更、および保守が容易になります。  
  
- コーディング規約により、C# のベスト プラクティスがわかります。  

この記事のガイドラインは、サンプルおよびドキュメントを開発するために Microsoft によって使用されます。  
  
## <a name="naming-conventions"></a>名前付け規則  
  
- [using ディレクティブ](../../language-reference/keywords/using-directive.md)が含まれていない簡単な例では、名前空間の修飾を使用します。 プロジェクトに名前空間が既定でインポートされていることがわかっている場合は、その名前空間の各名前を完全修飾する必要はありません。 次の例に示すように、修飾名が長すぎて 1 行に収まらない場合は、ドット (.) の後で改行できます。

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet1":::

- 他のガイドラインに合わせて、Visual Studio デザイナーのツールを使用して作成されたオブジェクトの名前を変更する必要はありません。  
  
## <a name="layout-conventions"></a>レイアウト規則  

コードの構造を強調する書式が使用され、コードが読みやすくなっているのが、優れたレイアウトです。 マイクロソフトの例とサンプルは、次の規則に準拠しています。  
  
- コード エディターの既定の設定 (スマート インデント、4 文字インデント、タブを空白として保存) を使用します。 詳細については、「[[オプション]、[テキスト エディター]、[C#]、[書式設定]](/visualstudio/ide/reference/options-text-editor-csharp-formatting)」を参照してください。  
  
- 1 つの行には 1 つのステートメントのみを記述します。  
  
- 1 つの行には 1 つの宣言のみを記述します。  
  
- 継続行にインデントが自動的に設定されない場合は、1 タブ ストップ (4 つの空白) 分のインデントを設定します。  
  
- メソッド定義とプロパティ定義の間に少なくとも 1 行の空白行を追加します。  
  
- 次のコードに示すように、式に句を作成するときはかっこを使用します。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet2":::

## <a name="commenting-conventions"></a>コメント規則  
  
- コメントは、コード行の末尾ではなく別の行に記述します。  
  
- コメントのテキストは大文字で開始します。  
  
- コメントのテキストはピリオドで終了します。  
  
- 次の例に示すように、コメント デリミター (//) とコメント テキストの間に空白を 1 つ挿入します。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet3":::

- アスタリスクを整形したブロックでコメントを囲まないようにします。  
  
## <a name="language-guidelines"></a>言語ガイドライン  

以降のセクションでは、コード例とサンプルを準備する際に C# チームが従っている方法について説明します。  
  
### <a name="string-data-type"></a>文字列データ型  
  
- 次のコードに示すように、短い文字列を連結するときは[文字列補間](../../language-reference/tokens/interpolated.md)を使用します。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet6":::

- ループ内で文字列を追加する場合 (特に大量のテキストを処理する場合) は、<xref:System.Text.StringBuilder> オブジェクトを使用します。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

### <a name="implicitly-typed-local-variables"></a>暗黙的に型指定されたローカル変数  
  
- 変数の型が割り当ての右側から明らかである場合、または厳密な型が重要でない場合は、ローカル変数の[暗黙の型指定](../classes-and-structs/implicitly-typed-local-variables.md)を使用します。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet8":::
  
- 割り当ての右側から型が明らかではない場合、[var](../../language-reference/keywords/var.md) を使用しないでください。 メソッド名から型が明らかであると想定しないでください。 変数の型は、`new` 演算子または明示的なキャストの場合に明らかであると見なされます。
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet9":::

- 変数の型を指定するときに変数名に頼らないでください。 変数名が正しくない場合があります。 次の例で、変数名 `inputInt` は誤解を招きます。 文字列です。

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet10":::

- [dynamic](../../language-reference/builtin-types/reference-types.md) の代わりに `var` を使用しないようにしてください。 `dynamic` は、実行時の型の推定が必要な場合に使用します。 詳細については、「[dynamic 型の使用 (C# プログラミングガイド)](../types/using-type-dynamic.md)」を参照してください。
  
- [for](../../language-reference/keywords/for.md) ループでループ変数の型を決定するときは、暗黙の型指定が使用されます。  
  
  次の例では、`for` ステートメントで暗黙の型指定を使用しています。  

    :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

- [foreach](../../language-reference/keywords/foreach-in.md) ループでループ変数の型を決定するときは、暗黙の型指定は使用されません。

  次の例では、`foreach` ステートメントで暗黙の型指定が使用されています。

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet12":::

  > [!NOTE]
  > 反復可能コレクションの要素の型を誤って変更しないように注意してください。 たとえば、`foreach` ステートメントで <xref:System.Linq.IQueryable?displayProperty=nameWithType> から <xref:System.Collections.IEnumerable?displayProperty=nameWithType> に切り替えるのは簡単ですが、これを行うとクエリの結果が変更されます。

### <a name="unsigned-data-types"></a>unsigned データ型  
  
通常は、unsigned 型ではなく `int` を使用します。 C# では `int` を使用するのが一般的です。`int` を使用すると、他のライブラリと対話しやすくなります。  
  
### <a name="arrays"></a>配列  
  
宣言行で配列を初期化するときは簡潔な構文を使用します。 次の例では、`string[]` の代わりに `var` を使用できないことに注意してください。  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13a":::

明示的なインスタンス化を使用する場合は、`var` を使用できます。

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13b":::

配列のサイズを指定する場合は、1 つずつ要素を初期化する必要があります。
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13c":::
  
### <a name="delegates"></a>代理人  
  
デリゲート型を定義する代わりに [`Func<>` と `Action<>`](../../../standard/delegates-lambdas.md) を使用します。 クラスで、デリゲート メソッドを定義します。  

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14a":::

`Func<>` または `Action<>` デリゲートで定義されているシグネチャを使用してメソッドを呼び出します。

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15a":::

デリゲート型のインスタンスを作成する場合、簡潔な構文を使用します。 クラスで、デリゲート型および一致するシグネチャを持つメソッドを定義します。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14b":::

デリゲート型のインスタンスを作成し、それを呼び出します。 次の宣言は、短縮した構文を示しています。

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15b":::

次の宣言は、完全な構文を示しています。

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15c":::

### <a name="try-catch-and-using-statements-in-exception-handling"></a>例外処理での `try`-`catch` および `using` ステートメント  
  
- ほとんどの例外処理には、[try-catch](../../language-reference/keywords/try-catch.md) ステートメントを使用します。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet16":::

- C# の [using ステートメント](../../language-reference/keywords/using-statement.md)を使用して、コードを簡潔にします。 [try-finally](../../language-reference/keywords/try-finally.md) ステートメントを使用するときに `finally` ブロックのコードが <xref:System.IDisposable.Dispose%2A> メソッドの呼び出しだけである場合は、`using` ステートメントを代わりに使用します。

  次の例で、`try`-`finally` ステートメントは `finally` ブロックでのみ `Dispose` を呼び出します。
  
   :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17a":::

  `using` ステートメントを使用して同じことを行うことができます。

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17b":::

  C# 8 以降のバージョンでは、中かっこを必要としない新しい [`using` 構文](../../language-reference/keywords/using-statement.md)を使用します。

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17c":::

### <a name="-and--operators"></a>`&&` 演算子と `||` 演算子  
  
例外を回避し、不要な比較をスキップしてパフォーマンスを向上させるには、比較を実行する場合、次の例に示すように [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) の代わりに [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) を、[`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) の代わりに [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) を使用します。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet18":::

除数が 0 の場合、`if` ステートメント内の 2 番目の句によって実行時エラーが発生します。 ただし、最初の式が false の場合、&& 演算子はショートサーキットされます。 つまり、2 番目の式は評価されません。 & 演算子は両方を評価し、`divisor` が 0 の場合は実行時エラーが発生します。
  
### <a name="new-operator"></a>`new` 演算子  
  
- 次の宣言に示すように、オブジェクトのインスタンス化の簡潔な形式のいずれかを使用します。 2 番目の例は、C# 9 以降で使用できる構文を示しています。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet19":::
  
  ```csharp
  ExampleClass instance2 = new();
  ```
  
  上記の宣言は次の宣言と同等です。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet20":::

- 次の例に示すように、オブジェクト初期化子を使用してオブジェクトの作成を簡略化します。

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21a":::

  次の例では、前の例と同じプロパティを設定しますが、初期化子を使用しません。
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21b":::

### <a name="event-handling"></a>イベント処理  
  
後で削除する必要のないイベント ハンドラーを定義する場合は、ラムダ式を使用します。  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet22":::

ラムダ式では、次の従来の定義を短縮します。

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet23":::

### <a name="static-members"></a>静的メンバー  
  
[静的](../../language-reference/keywords/static.md)メンバーは、クラス名 *ClassName.StaticMember* を使用して呼び出します。 こうすることで、静的アクセスが明確になり、コードがよりわかりやすくなります。  派生クラスの名前を持つ基本クラスに定義された静的メンバーを指定しないでください。  このコードをコンパイルすると、コードが読みやすくなくなり、派生クラスに同じ名前の静的メンバーを追加すると、将来的にコードが中断する場合があります。  
  
### <a name="linq-queries"></a>LINQ クエリ  
  
- クエリ変数にはわかりやすい名前を使用します。 次の例では、シアトル在住の顧客に `seattleCustomers` を使用しています。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- エイリアスを使用して、匿名型のプロパティ名の大文字と小文字の使用が正しい Pascal 形式になるようにします。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet26":::

- 結果のプロパティ名があいまいになる場合は、プロパティ名を変更します。 たとえば、クエリで顧客名と販売店 ID を返す場合、クエリ結果で `Name` と `ID` をそのまま使用するのではなく、これらの名前を変更し、`Name` が顧客の名前であり、`ID` が販売店の ID であることを明確にします。  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet27":::

- クエリ変数と範囲変数の宣言で暗黙の型指定を使用します。  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- 前の例に示すように、クエリ句を [from](../../language-reference/keywords/from-clause.md) 句の下に配置します。  

- [where](../../language-reference/keywords/where-clause.md) 句を他のクエリ句より先に使用し、それ以降のクエリ句では、フィルター化されたデータセットが処理されるようにします。  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet29":::

- 内部コレクションにアクセスするには、[join](../../language-reference/keywords/join-clause.md) 句ではなく複数の `from` 句を使用します。 たとえば、`Student` オブジェクトのコレクションがあり、各オブジェクトに試験の点数のコレクションが含まれているとします。 次のクエリを実行すると、90 点より高い点数とその点数を取った学生の姓が返されます。  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet30":::

## <a name="security"></a>セキュリティ  

「[安全なコーディングのガイドライン](../../../standard/security/secure-coding-guidelines.md)」のガイドラインに従ってください。  
  
## <a name="see-also"></a>関連項目

- [.NET ランタイム コーディングのガイドライン](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
- [Visual Basic のコーディング規則](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [安全なコーディングのガイドライン](../../../standard/security/secure-coding-guidelines.md)
