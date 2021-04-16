---
title: 参照セル
description: F# の参照セルが、どのように参照セマンティクスを持つ変更可能な値を作成できる格納場所となるかについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 2bca7797b272c0e7d5bf54df07041dc08e33709a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216771"
---
# <a name="reference-cells"></a>参照セル

*参照セル* は、参照セマンティクスを持つ変更可能な値を作成できる格納場所です。

## <a name="syntax"></a>構文

```fsharp
ref expression
```

## <a name="remarks"></a>解説

値をカプセル化する新しい参照セルを作成するには、値の前に `ref` 演算子を指定します。 基になる値は変更可能なので、後で変更できます。

参照セルは、単なるアドレスではなく、実際の値を保持します。 `ref` 演算子を使用して参照セルを作成すると、基の値のコピーが、カプセル化された変更可能な値として作成されます。

参照セルを逆参照するには、`!` (感嘆符) 演算子を使用します。

次のコード例は、参照セルの宣言と使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

出力は `50` になります。

参照セルは、次のように宣言される `Ref` ジェネリック レコード型のインスタンスです。

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

`'a ref` 型は、`Ref<'a>` のシノニムです。 コンパイラと IDE の IntelliSense では、この型について前者が表示されますが、基になる定義は後者です。

`ref` 演算子は、新しい参照セルを作成します。 次のコードは、`ref` 演算子の宣言です。

```fsharp
let ref x = { contents = x }
```

次の表に、参照セルで使用できる機能を示します。

|演算子、メンバー、またはフィールド|説明|Type|定義|
|--------------------------|-----------|----|----------|
|`!` (逆参照演算子)|基になる値を返します。|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (代入演算子)|基になる値を変更します。|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (演算子)|新しい参照セルに値をカプセル化します。|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (プロパティ)|基になる値を取得または設定します。|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (レコード フィールド)|基になる値を取得または設定します。|`'a`|`let ref x = { contents = x }`|

基になる値にアクセスする方法はいくつかあります。 逆参照演算子 (`!`) によって返される値は、代入可能な値ではありません。 したがって、基になる値を変更する場合は、代わりに代入演算子 (`:=`) を使用する必要があります。

`Value` プロパティと `contents` フィールドは、いずれも代入可能な値です。 したがって、次のコードに示すように、これらを使用して基になる値にアクセスしたり、基になる値を変更したりできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

出力は次のとおりです。

```console
10
10
11
12
```

`contents` フィールドは、他のバージョンの ML との互換性のために用意されており、コンパイル中に警告を生成します。 この警告を無効にするには、`--mlcompatibility` コンパイラ オプションを使用します。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。

C# プログラマは、C# の `ref` が F# の `ref` と同じものではないことを理解している必要があります。 F# の同等のコンストラクトは、参照セルとは異なる概念の [byref](byrefs.md) です。

`mutable` としてマークされた値は、クロージャによってキャプチャされた場合に自動的に `'a ref` に昇格される場合があります。「[値](./values/index.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [パラメーターと引数](parameters-and-arguments.md)
- [シンボルと演算子のリファレンス](./symbol-and-operator-reference/index.md)
- [値](./values/index.md)
