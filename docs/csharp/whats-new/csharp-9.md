---
title: C# 9.0 の新機能 - C# ガイド
description: C# 9.0 で使用できる新しい機能の概要を説明します。
ms.date: 09/04/2020
ms.openlocfilehash: 49170b123f612c06f22b70e44b29ad7be5f382ea
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876046"
---
# <a name="whats-new-in-c-90"></a>C# 9.0 の新機能

C# 9.0 によって、C# 言語に次の機能と機能強化が追加されています。

- [レコード](#record-types)
- [init 専用セッター](#init-only-setters)
- [最上位レベルのステートメント](#top-level-statements)
- [パターン マッチングの拡張機能](#pattern-matching-enhancements)
- ネイティブ サイズの整数
- 関数ポインター
- localsinit フラグの出力を抑制する
- ターゲット型の新しい式
- 静的な匿名関数
- ターゲットにより型指定された条件式
- 共変の戻り値の型
- `foreach` ループの拡張機能 `GetEnumerator` サポート
- ラムダ ディスカード パラメーター
- ローカル関数の属性
- モジュールの初期化子
- 部分メソッドの新機能

C# 9.0 は **.NET 5** でサポートされています。 詳細については、「[C# 言語のバージョン管理](../language-reference/configure-language-version.md)」を参照してください。

最新の .NET SDK は [.NET のダウンロード ページ](https://dotnet.microsoft.com/download)でダウンロードできます。

## <a name="record-types"></a>レコードの種類

C# 9.0 には "***レコード型***" が導入されています。これは、等価性の値のセマンティクスを提供するための合成されたメソッドを提供する参照型です。 既定では、レコードは変更できません。

レコード型を使用すると、変更できない参照型を .NET で簡単に作成できます。 従来、.NET 型は、参照型 (クラス型と匿名型を含む) と値型 (構造体とタプルを含む) に大別されています。 変更できない値型が推奨されますが、変更可能な値型でエラーが頻繁に発生するわけではありません。 値型の変数には値が保持され、値型がメソッドに渡されるときは、元のデータのコピーが変更されます。

変更できない参照型にも多くの利点があります。 これらの利点は、共有データを使用する同時実行プログラムで、より顕著になります。 残念ながら、C# で変更できない参照型を作成するには、余分なコードをかなり記述する必要がありました。 レコードにより、等価性の値のセマンティクスを使用する、変更できない参照型の型宣言が提供されます。 等価コードとハッシュ コードの合成メソッドでは、プロパティがすべて等しい場合、2 つのレコードは等しいと見なされます。 次の定義を考慮してください。

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="RecordDefinition":::

レコード定義によって、`FirstName` と `LastName` の 2 つの読み取り専用プロパティを含む `Person` 型が作成されます。 `Person` 型は参照型です。 IL を見た場合は、それはクラスです。 どのプロパティも作成後に変更できないので、それは変更できません。 レコード型を定義すると、コンパイラによって他のいくつかのメソッドが自動的に合成されます。

- 値ベースの等価比較のためのメソッド
- <xref:System.Object.GetHashCode> のオーバーライド
- コピー メンバーとクローン メンバー
- `PrintMembers` および <xref:System.Object.ToString>

レコードによって、継承がサポートされます。 次のようにして、`Person` の新しい派生レコードを宣言できます。

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="InheritedRecord":::

また、レコードをシールして、さらに派生させることもできます。

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="SealedRecord":::

コンパイラにより、上記のメソッドの異なるバージョンが合成されます。 メソッドのシグネチャは、レコード型がシールされているかどうか、および直接基底クラスがオブジェクトであるかどうかによって異なります。 レコードには次の機能が必要です。

- 等価性は値に基づいており、型が一致するかどうかのチェックが含まれます。 たとえば、2 つのレコードが同じ名前を共有している場合でも、`Student` を `Person` と同じにすることはできません。
- レコードには、自動的に生成される一貫した文字列表現があります。
- レコードによって、コピーの構築がサポートされます。 正しいコピーの構築には、継承階層と、開発者によって追加されたプロパティが含まれる必要があります。
- レコードは、変更してコピーできます。 これらのコピー操作と変更操作では、非破壊的な変異がサポートされます。

使い慣れた `Equals` オーバーロード、`operator ==`、`operator !=` に加えて、コンパイラによって新しい `EqualityContract` プロパティが合成されます。 プロパティからは、レコードの型に一致する `Type` オブジェクトが返されます。 基本データ型が `object` の場合、プロパティは `virtual` になります。 基本データ型が別のレコード型である場合、プロパティは `override` になります。 レコード型が `sealed` の場合、プロパティは `sealed` になります。 合成された `GetHashCode` によって、基本データ型とレコード型で宣言されているすべてのプロパティとフィールドの `GetHashCode` が使用されます。 これらの合成メソッドにより、継承階層全体で値ベースの等価性が適用されます。 つまり、`Student` は、同じ名前の `Person` と等しいとは見なされません。 2 つのレコードの型が一致し、さらにレコード型の間で共有されているすべてのプロパティが等しい必要があります。

レコードには、合成されたコンストラクターと、コピーを作成するための "clone" メソッドもあります。 合成コンストラクターには、レコード型の引数が 1 つあります。 これにより、レコードのすべてのプロパティの値が同じ新しいレコードが生成されます。 レコードがシールされている場合、このコンストラクターは private です。それ以外の場合は、protected です。 合成された "clone" メソッドによって、レコード階層のコピーの構築がサポートされます。 "clone" という用語が引用符で囲まれているのは、実際の名前はコンパイラによって生成されるためです。 レコード型で `Clone` という名前のメソッドを作成することはできません。 合成された "clone" メソッドによって、仮想ディスパッチを使用してコピーされるレコードの型が返されます。 コンパイラにより、`record` のアクセス修飾子に応じて、異なる修飾子が "clone" メソッドに追加されます。

- レコード型が `abstract` の場合は、"clone" メソッドも `abstract` になります。 基本データ型が `object` でない場合は、メソッドも `override` になります。
- 基本データ型が `object` であるときの、`abstract` ではないレコード型の場合:
  - レコードが `sealed` の場合、追加の修飾子は "clone" メソッドに追加されません (つまり、`virtual` ではありません)。
  - レコードが `sealed` ではない場合、"clone" メソッドは `virtual` になります。
- 基本データ型が `object` ではないときの、`abstract` ではないレコード型の場合:
  - レコードが `sealed` の場合は、"clone" メソッドも `sealed` になります。
  - レコードが `sealed` ではない場合、"clone" メソッドは `override` になります。

これらすべてのルールの結果として、レコード型のすべての階層で等価性が一貫して実装されます。 次の例で示すように、プロパティが等しく、型が同じである場合、2 つのレコードは互いに等しくなります。

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="RecordsEquality":::

コンパイラにより、印刷出力をサポートする 2 つのメソッド <xref:System.Object.ToString> のオーバーライドと `PrintMembers` が合成されます。 `PrintMembers` は、引数として <xref:System.Text.StringBuilder?displayProperty=nameWithType> を受け取ります。 レコード型のすべてのプロパティに対し、プロパティ名と値のコンマ区切りリストが追加されます。 `PrintMembers` によって、他のレコードからのすべての派生レコードに対する基本実装が呼び出されます。 <xref:System.Object.ToString> のオーバーライドでは、`PrintMembers` によって生成され、`{` と `}` で囲まれた文字列が返されます。 たとえば、`Student` に対する <xref:System.Object.ToString> メソッドでは、次のコードのような `string` が返されます。

```csharp
"Student { LastName = Wagner, FirstName = Bill, Level = 11 }"
```

これまでに示した例では、従来の構文を使用してプロパティが宣言されています。 "***位置指定レコード***" と呼ばれる簡潔な形式があります。  次に示すのは、前に位置指定レコードとして定義されている 3 つのレコード型です。

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="PositionalRecords":::

これらの宣言によって、以前のバージョンと同じ機能が作成されます (次のセクションで説明する追加の機能がいくつかあります)。 これらのレコードには新しいメソッドが追加されていないため、これらの宣言は角かっこではなくセミコロンで終わっています。 本体を追加し、追加のメソッドを含めることもできます。

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="RecordsWithMethods":::

コンパイラによって、位置指定レコードに対して `Deconstruct` メソッドが生成されます。 `Deconstruct` メソッドには、レコード型のすべてのパブリック プロパティの名前と一致するパラメーターがあります。 `Deconstruct` メソッドを使用して、レコードをコンポーネント プロパティに分解できます。

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="DeconstructRecord":::

最後に、レコードは [`with` 式](../language-reference/operators/with-expression.md)をサポートしています。 "* **`with` 式** _" は、レコードのコピーを作成するが、_with* で指定されたプロパティは変更するようにコンパイラに指示します。

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="Wither":::

前の行では、`LastName` プロパティが `person` のコピーで、`FirstName` が `"Paul"` である、新しい `Person` レコードが作成されます。 `with` 式には、任意の数のプロパティを設定できます。 `with` 式を使用して、正確なコピーを作成することもできます。 変更するプロパティの空のセットを指定します。

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="WithCopy":::

"clone" メソッド以外のすべての合成メンバーは、開発者が自分で記述できます。 レコード型に、いずれかの合成メソッドのシグネチャと一致するメソッドがある場合、コンパイラでそのメソッドは合成されません。 前の `Dog` レコードの例には、手作業でコーディングされた <xref:System.String.ToString> メソッドが例として含まれます。

レコードの種類の詳細については、この[レコードの探索](../whats-new/tutorials/records.md)チュートリアルを参照してください。

## <a name="init-only-setters"></a>init 専用セッター

"***init 専用セッター***" によって、オブジェクトのメンバーを初期化するための一貫した構文が提供されます。 プロパティ初期化子を使用すると、どの値によってどのプロパティが設定されているかが明確にされます。 欠点は、それらのプロパティが設定可能である必要があることです。 C# 9.0 以降では、プロパティとインデクサーに対して `set` アクセサーの代わりに `init` アクセサーを作成できます。 呼び出し元により、プロパティ初期化子構文を使用して作成式でこれらの値を設定することができますが、構築が完了するとそれらのプロパティは読み取り専用になります。 init 専用セッターによって、状態を変更するためのウィンドウが提供されます。 構築フェーズが終了すると、そのウィンドウは閉じます。 プロパティ初期化子と with 式の完了を含め、すべての初期化の後で、構築フェーズは実質的に終了します。

`init` 専用セッターは、記述する任意の型で宣言できます。 たとえば、次の構造体では、気象監視構造体が定義されています。

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="DeclareWeatherObservation":::

呼び出し元は、プロパティ初期化子構文を使用して値を設定できますが、それでも不変性は維持されます。

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="UseWeatherObservation":::

ただし、初期化後に監視を変更することは、初期化の外側で init 専用プロパティに代入することによるエラーになります。

```csharp
// Error! CS8852.
now.TemperatureInCelsius = 18;
```

init 専用セッターは、派生クラスから基底クラスのプロパティを設定する場合に便利です。 また、基底クラスのヘルパーを使用して派生プロパティを設定することもできます。 位置指定レコードによって、init 専用セッターを使用してプロパティが宣言されます。 これらのセッターは、with 式で使用されます。 定義する任意の `class` または `struct` に対して、init 専用セッターを宣言できます。

## <a name="top-level-statements"></a>最上位レベルのステートメント

"***最上位レベル ステートメント***" により、多くのアプリケーションから不要な手続きが削除されます。 正規の "Hello World!" プログラムについて考えます。

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

何かを行うコード行は 1 つだけです。 最上位レベル ステートメントを使用すると、そのすべての定型句を、`using` ステートメントと処理を行う 1 行に置き換えることができます。

:::code language="csharp" source="snippets/whats-new-csharp9/Program.cs" ID="TopLevelStatements":::

1 行だけのプログラムが必要な場合は、`using` ディレクティブを削除し、完全修飾型名を使用することができます。

```csharp
System.Console.WriteLine("Hello World!");
```

最上位レベル ステートメントを使用できるのは、アプリケーション内の 1 つのファイルだけです。 コンパイラにより、複数のソース ファイルで最上位レベル ステートメントが検出されると、エラーになります。 また、最上位レベル ステートメントを、宣言されたプログラム エントリ ポイント メソッド (通常は `Main` メソッド) と組み合わせても、エラーになります。 ある程度まで、その 1 つのファイルに、通常は `Program` クラスの `Main` メソッドに含まれるステートメントが含まれているものと考えることができます。  

この機能の最も一般的な用途の 1 つは、教材の作成です。 C# の開発初心者は、正規の "Hello World!" を 1 行または 2 行のコードで作成できます。 余分な手続きは必要ありません。 一方、経験豊富な開発者は、この機能の多くの用途を見つけることができます。 最上位レベル ステートメントを使用すると、Jupyter Notebook で提供されるものと同様の実験用にスクリプトに似たエクスペリエンスを有効にできます。 最上位レベル ステートメントは、小規模なコンソール プログラムとユーティリティに最適です。 Azure Functions は、最上位レベル ステートメントに最適なユース ケースです。

最も重要なのは、最上位レベル ステートメントでアプリケーションのスコープや複雑さが制限されないことです。 それらのステートメントでは、任意の .NET クラスにアクセスしたり、使用したりできます。 また、コマンド ライン引数や戻り値の使用も制限されません。 最上位レベル ステートメントでは、args という名前の文字列の配列にアクセスできます。 最上位レベル ステートメントで整数値が返される場合、その値は、合成された `Main` メソッドからの整数のリターン コードになります。 最上位レベル ステートメントには、非同期式を含めることができます。 その場合、合成されたエントリ ポイントからは `Task` または `Task<int>` が返されます。

## <a name="pattern-matching-enhancements"></a>パターン マッチングの拡張機能

C# 9 には、新しいパターン マッチングの機能強化が含まれています。

- "***型パターン***" は、変数が型である場合に一致します
- "***かっこで囲まれたパターン***" では、パターンの組み合わせの優先順位が適用または強調されます
- "***接続的 `and` パターン***" では、両方のパターンが一致することが要求されます
- "***離接的 `or` パターン***" では、どちらかのパターンが一致することが要求されます
- "***否定的 `not` パターン***" では、パターンが一致しないことが要求されます
- "***関係パターン***" では、入力が定数より小さい、より大きい、以下、または以上であることが要求されます。

これらのパターンにより、パターンの構文が豊富になります。 次のような例を考えてみてください。

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterPattern":::

または、省略可能なかっこを使用して、`and` が `or` より優先順位が高いことを明確にします。

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterOrSeparatorPattern":::

最も一般的な使用方法の 1 つは、null チェックの新しい構文です。

```csharp
if (e is not null)
{
    // ...
}
```

これらのパターンのいずれも、パターンが許可される任意のコンテキスト (`is` パターン式、`switch` 式、入れ子になったパターン、`switch` ステートメントの `case` ラベルのパターン) で使用できます。

## <a name="performance-and-interop"></a>パフォーマンスと相互運用

3 つの新機能により、高パフォーマンスを必要とするネイティブ相互運用および低レベル ライブラリのサポートが向上します (ネイティブ サイズの整数、関数ポインター、`localsinit` フラグの省略)。

ネイティブ サイズの整数 `nint` と `nuint` は整数型です。 これらは、基になる型 <xref:System.IntPtr?displayProperty=nameWithType> および <xref:System.UIntPtr?displayProperty=nameWithType> によって表されます。 コンパイラによって、これらの型に対する追加の変換と操作がネイティブ int として公開されます。 ネイティブ サイズの整数では、`MaxValue` または `MinValue` のプロパティが定義されます。 これらの値は、ターゲット コンピューターでの整数のネイティブ サイズに依存するため、コンパイル時の定数として表すことはできません。 これらの値は実行時に読み取り専用になります。 `nint` に対する定数値は、[`int.MinValue` .. `int.MaxValue`]. `nuint` に対する定数値は、[`uint.MinValue` .. `uint.MaxValue`]. コンパイラによって、<xref:System.Int32?displayProperty=nameWithType> 型と <xref:System.UInt32?displayProperty=nameWithType> 型を使用するすべての単項演算子と二項演算子に対して、定数の折りたたみが実行されます。 結果が 32 ビットに収まらない場合、演算は実行時に実行され、定数とは見なされません。 ネイティブ サイズの整数を使用すると、整数演算が広く使用されており、最速のパフォーマンスを実現する必要があるシナリオで、パフォーマンスを向上させることができます。

関数ポインターでは、IL オペコード `ldftn` および `calli` にアクセスするための簡単な構文が提供されます。 関数ポインターは、新しい `delegate*` 構文を使用して宣言できます。 `delegate*` 型はポインター型です。 `Invoke()` メソッドで `callvirt` が使用されるデリゲートとは異なり、`delegate*` 型の呼び出しでは `calli` が使用されます。 構文的には、呼び出しは同じです。 関数ポインターの呼び出しでは、`managed` の呼び出し規約が使用されます。 `unmanaged` の呼び出し規約が必要であることを宣言するには、`delegate*` 構文の後に `unmanaged` キーワードを追加します。 その他の呼び出し規約は、`delegate*` 宣言の属性を使用して指定できます。

最後に、<xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute?displayProperty=nameWithType> を追加することで、`localsinit` フラグを生成しないようコンパイラに指示することができます。 このフラグは、すべてのローカル変数をゼロで初期化するように CLR に指示します。 1\.0 から、`localsinit` フラグが C# に対する既定の動作でした。 しかし、一部のシナリオでは、ゼロによる初期化を追加すると、パフォーマンスに大きく影響する可能性があります。 特に、`stackalloc` を使用する場合です。 そのような場合は、<xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute> を追加できます。 1 つのメソッドまたはプロパティに、または `class`、`struct`、`interface` に、さらにはモジュールに対してさえも、それを追加できます。 この属性は `abstract` メソッドに影響しません。実装用に生成されたコードに影響します。

これらの機能により、一部のシナリオでパフォーマンスを向上させることができます。 導入前と導入後の両方で慎重にベンチマークを行った後でのみ、使用する必要があります。 ネイティブ サイズの整数に関するコードは、複数のターゲット プラットフォームで、異なる整数サイズを使用して、テストする必要があります。 その他の機能には、アンセーフ コードが必要です。

## <a name="fit-and-finish-features"></a>適合性と完成度の機能

他の多くの機能は、コードをより効率的に記述するのに役立ちます。 C# 9.0 では、作成されるオブジェクトの型が既にわかっている場合、[`new` 式](../language-reference/operators/new-operator.md)で型を省略できます。 最も一般的な使用方法は、フィールドの宣言です。

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="WeatherStationField":::

ターゲット型の `new` は、メソッドへの引数として渡す新しいオブジェクトを作成する必要がある場合にも使用できます。 次のようなシグネチャを持つ `ForecastFor()` メソッドについて考えます。

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="ForecastSignature":::

これを、次のように呼び出すことができます。

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="TargetTypeNewArgument":::

この機能のもう 1 つの便利な用途は、init 専用プロパティと組み合わせて、新しいオブジェクトを初期化する場合です。

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="InitWeatherStation":::

`return new();` ステートメントを使用することで、既定のコンストラクターによって作成されたインスタンスを返すことができます。

同様の機能により、[条件式](../language-reference/operators/conditional-operator.md)の対象となる型の解決が向上します。 この変更により、2 つの式の間で暗黙的な変換を行う必要はありませんが、どちらもターゲット型への暗黙的な変換を行うことができます。 多くの場合、この変更に気付くことはありません。 気付くとすれば、以前はキャストを必要としたり、コンパイルされなかったりした一部の条件式が、機能するようになることです。

C# 9.0 以降では、`static` 修飾子を[ラムダ式](../language-reference/operators/lambda-expressions.md)または[匿名メソッド](../language-reference/operators/delegate-operator.md)に追加できます。 静的なラムダ式は、`static` ローカル関数に似ています。静的ラムダまたは匿名メソッドでは、ローカル変数またはインスタンスの状態をキャプチャできません。 `static` 修飾子により、誤って他の変数がキャプチャされることがなくなります。

共変の戻り値の型を使用すると、[override](../language-reference/keywords/override.md) メソッドの戻り値の型を柔軟に指定できます。 override メソッドは、オーバーライドされた基本メソッドの戻り値の型から派生した型を返すことができます。 これは、レコードや、仮想クローンまたはファクトリ メソッドをサポートするその他の型に役立ちます。

また、[`foreach` ループ](../language-reference/keywords/foreach-in.md)によって、それ以外の方法で `foreach` パターンを満たす拡張メソッド `GetEnumerator` が認識され、使用されます。 この変更は、非同期パターンやパターンベースの分解など、他のパターンベースのコンストラクションと `foreach` の間に整合性があることを意味します。 実際、この変更は、あらゆる型に `foreach` サポートを追加できることを意味します。 それの使用は、設計においてオブジェクトの列挙に意味があるときのみに限定してください。

次に、ラムダ式に対するパラメーターとして破棄を使用できます。 このようにすると、引数の名前付けを避けることができ、コンパイラではその使用を避けることができます。 任意の引数に対して `_` を使用します。 詳細については、[ラムダ式](../language-reference/operators/lambda-expressions.md)に関する記事の「[ラムダ式の入力パラメーター](../language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression)」セクションを参照してください。

ようやく、[ローカル関数](../programming-guide/classes-and-structs/local-functions.md)に属性を適用できるようになりました。 たとえば、[null 許容属性の注釈](../language-reference/attributes/nullable-analysis.md)をローカル関数に適用できます。

## <a name="support-for-code-generators"></a>コード ジェネレーターのサポート

2 つの最終機能では、C# コード ジェネレーターがサポートされています。 C# コード ジェネレーターは、roslyn アナライザーまたはコード修正と同じように記述できるコンポーネントです。 違いは、コード ジェネレーターでは、コードが分析され、コンパイル プロセスの一環として新しいソース コード ファイルが記述されることです。 一般的なコード ジェネレーターでは、属性またはその他の規則がコードで検索されます。

コード ジェネレーターにより、Roslyn 分析 API を使用して属性または他のコード要素が読み取られます。 その情報を基にして、コンパイルに新しいコードが追加されます。 ソース ジェネレーターではコードが追加されるだけで、コンパイル中の既存のコードの変更は許可されていません。

コード ジェネレーターに対して追加された 2 つの機能は、"***部分メソッド構文** _" の拡張機能と、"_*_モジュール初期化子_**" です。 1 つ目は、部分メソッドに対する変更です。 C# 9.0 より前の部分メソッドは `private` ですが、アクセス修飾子を指定することはできず、戻り値は `void` で、`out` パラメーターを持つことはできません。 これらの制限は、メソッドの実装を提供しないと、コンパイラによって部分メソッドのすべての呼び出しが削除されることを意味しました。 C# 9.0 ではこれらの制限はなくなりましたが、部分メソッドの宣言には実装が必要です。 コード ジェネレーターで、その実装を提供できます。 破壊的変更が発生しないよう、コンパイラでは、アクセス修飾子を持たないすべての部分メソッドは、古い規則に従うものと見なされます。 部分メソッドに `private` アクセス修飾子が含まれている場合、その部分メソッドは新しい規則によって制御されます。

コード ジェネレーターの 2 つ目の新機能は、"***モジュール初期化子***" です。 モジュール初期化子は、<xref:System.Runtime.CompilerServices.ModuleInitializerAttribute> 属性が関連付けられているメソッドです。 これらのメソッドは、全体モジュール内の他のフィールド アクセスまたはメソッド呼び出しの前にランタイムによって呼び出されます。 モジュール初期化子メソッドは次のようなものです。

- 静的でなければなりません
- パラメーターなしである必要があります
- void を返す必要があります
- ジェネリック メソッドであってはなりません
- ジェネリック クラスに含まれていてはなりません
- それを含むモジュールからアクセスできる必要があります

最後の項目は事実上、メソッドとそれを含んでいるクラスが internal または public である必要があることを意味します。 メソッドをローカル関数にすることはできません。
