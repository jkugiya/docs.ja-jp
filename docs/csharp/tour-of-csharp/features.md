---
title: C# のツアー - 主要な言語分野
description: C# を始めてお使いの方のために、 この言語の基本を説明します。 この記事には、主な言語機能の概説が含まれています。
ms.date: 08/06/2020
ms.openlocfilehash: e62ed4e360fdf3b30142474494ff4f038c77a772
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111336"
---
# <a name="major-language-areas"></a>主な言語の領域

## <a name="arrays-collections-and-linq"></a>配列、コレクション、および LINQ

C# と .NET には、さまざまなコレクション型が用意されています。 配列には、言語によって定義された構文があります。 ジェネリック コレクション型は、<xref:System.Collections.Generic?displayProperty=fullName> 名前空間に一覧表示されます。 特化されたコレクションには、スタック フレーム上の連続メモリにアクセスするための <xref:System.Span%601?displayProperty=nameWithType>、およびマネージド ヒープ上の連続メモリにアクセスするための <xref:System.Memory%601?displayProperty=nameWithType> が含まれます。 配列、<xref:System.Span%601>、<xref:System.Memory%601> を含むコレクションはすべて、反復の統一原則を共有します。 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> インターフェイスを使用します。 この統合原則は、LINQ クエリまたはその他のアルゴリズムで任意のコレクション型を使用できることを意味します。 <xref:System.Collections.Generic.IEnumerable%601> を使用してメソッドを記述します。それらのアルゴリズムは任意のコレクションで動作します。

### <a name="arrays"></a>配列

"[***配列** _](../programming-guide/arrays/index.md)" とは、算出されたインデックスを介してアクセスされる多くの変数を含むデータ構造です。 配列に含まれる変数は配列の "_*_要素_*_" とも呼ばれ、すべて同じ型です。 この型は配列の "*_要素型_*" と呼ばれます。

配列型は参照型で、配列変数の宣言は、配列インスタンスへの参照の領域を確保します。 実際の配列インスタンスは、`new` 演算子を使用して実行時に動的に作成されます。 `new` 操作によって、新しい配列インスタンスの ***長さ*** が指定され、それはインスタンスの有効期間中は固定です。 配列の要素のインデックスは、`0` から `Length - 1` までです。 `new` 演算子は配列の要素を自動的に既定値に初期化します。たとえば、すべての数値型はゼロ、すべての参照型は `null` です。

次の例では、`int` 要素の配列を作成し、その配列を初期化し、配列の内容を出力します。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArraysSample":::

この例では、"**1 次元配列**" を作成し、操作対象とします。 C# では、"_*_多次元配列_*_" もサポートされます。 配列型の次元数は、配列型の "*_ランク_*" とも呼ばれ、配列型の角かっこ内のコンマの数に 1 を加えたものです。 次の例では、1 次元、2 次元、および 3 次元の配列をそれぞれ割り当てます。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DeclareArrays":::

`a1` 配列は 10 の要素、`a2` 配列は 50 (10 × 5) の要素、`a3` 配列は 100 (10 × 5 × 2) の要素を含みます。
配列の要素型には、配列型を含む任意の型を指定できます。 配列型の要素を持つ配列は、***ジャグ配列*** と呼ばれることがあります。要素の配列の長さがすべて同じである必要がないからです。 次の例では、`int` の配列の配列を割り当てます。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArrayOfArrays":::

最初の行で 3 つの要素を持つ配列を作成しますが、各々は `int[]` 型で `null` 初期値を持ちます。 次の行では、3 つの要素を、それぞれ異なる長さの配列インスタンスへの参照で初期化します。

`new` 演算子では、配列要素の初期値を、区切り記号 `{` および `}` のあいだに記述された式の一覧である ***配列初期化子*** を使用して指定することができます。 次の例は、`int[]` を割り当て 3 つの要素で初期化します。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeArray":::

配列の長さは、`{` と `}` の間にある式の数から推論されます。 配列の初期化をさらに短縮して、配列型の記述を省略することができます。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeShortened":::

前述の例はどちらも、次のコードと同等です。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeGenerated":::

`foreach` ステートメントを使用すると、任意のコレクションの要素を列挙できます。 次のコードは、前の例の配列を列挙するものです。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="EnumerateArray":::

`foreach` ステートメントは <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを使用しているので、任意のコレクションに対して機能します。

## <a name="string-interpolation"></a>文字列補間

C# [***文字列補間***](../language-reference/tokens/interpolated.md) を使用すると、書式文字列内に結果が配置される式を定義することで、文字列の書式を設定できます。 たとえば、次の例では、特定の日の気温を気象データのセットから出力しています。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="StringInterpolation":::

補間文字列は `$` トークンを使用して宣言されます。 文字列補間では、`{` と `}` の間の式が評価され、結果が `string` に変換され、角かっこ内のテキストが式の文字列の結果に置き換えられます。 最初の式 `{weatherData.Date:MM-DD-YYYY}` 内にある `:` は、"*書式文字列*" を指定するものです。 前の例では、それによって、日付を "MM-DD-YYYY" 形式で出力するように指定されています。

## <a name="pattern-matching"></a>パターン マッチング

C# 言語には、オブジェクトの状態を照会し、その状態に基づいてコードを実行するための [***パターン マッチング***](../pattern-matching.md)式が用意されています。 型と、プロパティおよびフィールドの値を調べれば、実行されるアクションを特定することができます。 `switch` 式は、パターン マッチングの主な式です。

## <a name="delegates-and-lambda-expressions"></a>デリゲートおよびラムダ式

[***デリゲート型***](../delegates-overview.md)は、特定のパラメーター リストおよび戻り値の型を持つメソッドへの参照を表します。 デリゲートを使用すると、変数に割り当ててパラメーターとして渡すことのできるエンティティとして、メソッドを処理できます。 デリゲートは、他の言語で検出された関数ポインターの概念に似ています。 ただし、関数ポインターとは異なり、デリゲートはオブジェクト指向で、タイプ セーフです。

次の例では、`Function` という名前のデリゲート型を宣言して使用します。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DelegateExample":::

`Function` デリゲート型のインスタンスは、`double` 引数を取得して `double` 値を返す任意のメソッドを参照できます。 `Apply` メソッドは、指定された `Function` を `double[]` の要素に適用し、`double[]` を結果とともに返します。 `Main` メソッドでは、`Apply` は `double[]` に 3 つの異なる関数を適用するために使用されます。

デリゲートは、静的メソッド (前述の例の `Square` や `Math.Sin` など) またはインスタンス メソッド (前述の例の `m.Multiply` など) のいずれかを参照できます。 インスタンス メソッドを参照するデリゲートはまた、特定のオブジェクトを参照し、インスタンス メソッドがデリゲートから呼び出されると、そのオブジェクトは呼び出しで `this` になります。

宣言時に作成される "インライン メソッド" である匿名関数を使用してデリゲートを作成することもできます。 匿名関数では、周囲のメソッドのローカル変数を確認できます。 次の例では、クラスは作成されません。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseDelegate":::

デリゲートでは、自身が参照するメソッドのクラスについては認識も考慮もしません。 重要なのは、参照されるメソッドがデリゲートと同じパラメーターと戻り値の型を持つことです。

## <a name="async--await"></a>async / await

C# では、`async` と `await` の 2 つのキーワードを使用した非同期プログラムがサポートされます。 メソッドが非同期であることを宣言するには、メソッド宣言に `async` 修飾子を追加します。 `await` 演算子からは、結果が完了するまで非同期に待機するようにコンパイラに対して指示が出されます。 制御が呼び出し元に返されます。そして、メソッドから、非同期処理の状態を管理する構造体が返されます。 構造体は通常は <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> ですが、awaiter パターンをサポートする任意の型とすることができます。 これらの機能を使用すると、その同期相手として読み取られるが非同期で実行されるコードを記述できます。 たとえば、次のコードでは [Microsoft Docs](/) のホームページがダウンロードされます。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="AsyncExample":::

この小さなサンプルは、非同期プログラミングの主な機能を示しています。

- メソッドの宣言には、`async` 修飾子が含まれています。
- メソッドの本体では、`GetByteArrayAsync` メソッドの戻り値に対して `await` が適用されます。
- `return` ステートメント内で指定された型は、メソッドの `Task<T>` 宣言の型引数と一致しています (`Task` を返すメソッドの場合は、引数なしで `return` ステートメントが使用されます)。

## <a name="attributes"></a>属性

C# プログラムにおける型、メンバー、およびその他のエンティティは、動作の特定の側面を制御する修飾子をサポートします。 たとえばメソッドのアクセシビリティは、`public`、`protected`、`internal`、および `private` 修飾子を使用して制御されます。 C# はこの機能を一般化し、宣言情報のユーザー定義型をプログラム エンティティに追加して実行時に取得できるようにします。 プログラムでは、[***属性***](../programming-guide/concepts/attributes/index.md)を定義して使用することにより、この追加の宣言情報を指定します。

次の例では、プログラムのエンティティに配置して関連するドキュメントへのリンクを提供することができる `HelpAttribute` 属性を宣言しています。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DefineAttribute":::

すべての属性クラスは、.NET ライブラリによって提供される <xref:System.Attribute> 基底クラスから派生します。 属性は、関連付けられた宣言の直前に、名前を任意の変数とともに角かっこで囲んで与えることにより、適用できます。 属性の名前が `Attribute` 内で終わる場合、属性の参照時に、名前のその部分は省略可能です。 たとえば、`HelpAttribute` は次のように使用できます。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseAttributes":::

この例では `HelpAttribute` を `Widget` クラスにアタッチしています。 別の `HelpAttribute` をクラス内の `Display` メソッドに追加しています。 属性クラスのパブリック コンストラクターは、属性がプログラム エンティティにアタッチされたときに提供する必要がある情報を制御します。 その属性クラスのパブリックの読み取り/書き込みプロパティを参照することにより (`Topic` プロパティへの参照のような)、追加情報を提供することができます。

属性によって定義されるメタデータは、実行時にリフレクションを使用して読み取り、操作することができます。 この手法を使用して特定の属性が要求されると、プログラム ソースで提供される情報で属性クラスのコンストラクターが呼び出されます。 結果として得られる属性インスタンスが返されます。 追加情報がプロパティを通じて提供された場合、属性インスタンスが返される前に、これらのプロパティは指定された値に設定されます。

`Widget` クラスとその `Display` メソッドに関連付けられた `HelpAttribute` インスタンスを取得する方法を、次のコード サンプルに示します。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ReadAttributes":::

## <a name="learn-more"></a>詳細情報

C# の詳細については、[チュートリアル](../tutorials/intro-to-csharp/introduction-to-classes.md)のいずれかをお試しください。

>[!div class="step-by-step"]
>[[戻る]](program-building-blocks.md)
