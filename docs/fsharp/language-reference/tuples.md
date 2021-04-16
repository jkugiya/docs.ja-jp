---
title: タプル
description: F# のタプルについて説明します。これは、名前のない順序付けられた値のグループであり、型が異なる場合があります。
ms.date: 05/16/2016
ms.openlocfilehash: 6f4adf7e10e22d8b7a8cf697baee15962adf3630
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720362"
---
# <a name="tuples"></a>タプル

"*タプル*" は、名前のない順序付けられた値のグループであり、型が異なる場合があります。  タプルは、参照型または構造体にすることができます。

## <a name="syntax"></a>構文

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>解説

前の構文の各 "*要素*" は、任意の有効な F# 式にすることができます。

## <a name="examples"></a>例

タプルの例としては、同じまたは異なる型の 2 つ組や 3 つ組などがあります。 いくつかの例を次のコードに示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>個別の値の取得

次のコードに示すように、タプル要素にアクセスして名前を割り当てるためにパターン マッチングを使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

また、`let` バインディングを使用して、`match` 式の外側にあるパターン マッチングを使用してタプルを分解することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

または、関数への入力としてタプルのパターン マッチングを行うことができます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

タプルの要素が 1 つだけ必要な場合は、不要な値に新しい名前が作成されないよう、ワイルドカード文字 (アンダースコア) を使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

参照タプルから構造体タプルに要素をコピーすることも簡単です。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

関数 `fst` と `snd` (参照タプルのみ) では、タプルの 1 番目と 2 番目の要素がそれぞれ返されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

3 つ組の 3 番目の要素を返す組み込み関数はありませんが、次のように簡単に記述できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

通常、個々のタプル要素にアクセスするには、パターン マッチングを使用することをお勧めします。

## <a name="using-tuples"></a>タプルの使用

タプルでは、次の例に示すように、関数から複数の値を返す便利な方法が提供されます。 この例では整数除算が実行され、演算の丸めた結果がタプルの 2 つ組の最初のメンバーとして、剰余が 2 つ組の 2 番目のメンバーとして返されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

通常の関数構文によって暗黙的に指定される関数の引数の暗黙的なカリー化を回避する場合は、関数の引数としてタプルを使用することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

次のコードに示すように、この関数を定義するための通常の構文 `let sum a b = a + b` を使用すると、関数の最初の引数の部分適用である関数を定義できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

パラメーターとしてタプルを使用すると、カリー化が無効になります。 詳細については、「[関数](./functions/index.md)」の「引数の部分適用」を参照してください。

## <a name="names-of-tuple-types"></a>タプル型の名前

タプルである型の名前を記述する場合は、`*` 記号を使用して要素を区切ります。 `(10, 10.0, "ten")` のように、`int`、`float`、`string` で構成されるタプルの場合、型は次のように記述されます。

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>C# タプルとの相互運用

C# 7.0 で、この言語にタプルが導入されました。  C# のタプルは構造体であり、F# の構造体タプルと同等です。  C# と相互運用する必要がある場合は、構造体タプルを使用する必要があります。

これは簡単に行うことができます。  たとえば、タプルを C# クラスに渡して、その結果 (これも同様にタプル) を使用する必要があるとします。

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

F# コードでは、構造体タプルをパラメーターとして渡し、その結果を構造体タプルとして使用できるようになります。

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>参照タプルと構造体タプルの間の変換

参照タプルと構造体タプルの基になる表現はまったく異なるため、暗黙的に変換することはできません。  つまり、次のようなコードはコンパイルされません。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

1 つのタプルに対してパターン マッチングを行い、構成要素を使用してもう一方を構築する必要があります。  次に例を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>参照タプルのコンパイルされた形式

このセクションでは、タプルがコンパイルされている場合の形式について説明します。  こちらに記載されている情報は、.NET Framework 3.5 以下を対象としている場合を除き、読む必要はありません。

タプルはコンパイルされるといくつかのジェネリック型 (すべて `System.Tuple` という名前) の 1 つのオブジェクトになります。これは、アリティ、つまり型パラメーターの個数によってオーバーロードされます。 タプル型は、C# や Visual Basic などの別の言語から表示する場合や、F# コンストラクトを認識しないツールを使用する場合に、この形式で表示されます。 `Tuple` 型は .NET Framework 4 で導入されました。 以前のバージョンの .NET Framework を対象としている場合、コンパイラでは、F# コア ライブラリの 2.0 バージョンの `System.Tuple` のバージョンが使用されます。 このライブラリの型は、.NET Framework の 2.0、3.0、3.5 の各バージョンを対象とするアプリケーションにのみ使用されます。 型の転送は、.NET Framework 2.0 と .NET Framework 4 F# のコンポーネント間のバイナリ互換性を確保するために使用されます。

### <a name="compiled-form-of-struct-tuples"></a>構造体タプルのコンパイルされた形式

構造体タプル (たとえば、`struct (x, y)`) は、参照タプルとは基本的に異なります。  これらは <xref:System.ValueTuple> 型にコンパイルされます。これは、アリティ、つまり型パラメーターの個数によってオーバーロードされます。  これらは、[C# 7.0 タプル](../../csharp/language-reference/builtin-types/value-tuples.md)および[Visual Basic 2017 タプル](../../visual-basic/programming-guide/language-features/data-types/tuples.md)と同等のものであり、双方向の相互運用が可能です。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
