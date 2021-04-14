---
title: 挿入文字列
description: 補間された文字列について説明します。これは、F# の式を直接埋め込むことができる特殊な形式の文字列です。
ms.date: 11/12/2020
ms.openlocfilehash: 8c552b44cea7d6c51ec333b6bdd4d407c6f10da7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829688"
---
# <a name="interpolated-strings"></a>挿入文字列

補間された文字列は、F# の式を埋め込むことができる[文字列](strings.md)です。 これは、値または式の結果に基づいて文字列の値が変わる可能性があるさまざまなシナリオで役立ちます。

## <a name="syntax"></a>構文

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a>解説

補間された文字列を使用すると、文字列リテラル内の "穴" にコードを記述できます。 基本的な例を次に示します。

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

各 `{}` 中かっこのペアで囲まれたコンテンツに、任意の F# 式を指定できます。

`{}` 中かっこのペアをエスケープするには、次のように 2 つのペアを記述します。

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a>型指定のある補間された文字列

補間された文字列に F# の書式指定子を使用して、タイプ セーフを適用することもできます。

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

上の例では、コードは `name` を渡す必要がある場所で誤って `age` 値を渡します (その逆も同様です)。 この補間された文字列では書式指定子が使用されているので、これは些細な実行時のバグではなくコンパイル エラーとなります。

補間された文字列内では、「[プレーンテキストの書式指定](plaintext-formatting.md)」で説明されているすべての書式指定子が有効となります。

## <a name="verbatim-interpolated-strings"></a>逐語的な補間された文字列

F# では、文字列リテラルを埋め込むことができるように、三重引用符を使用した逐語的な補間された文字列がサポートされています。

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a>補間された文字列内での式の配置

`|` を使用し、スペースの数を指定することで、補間された文字列内で式を左揃えまたは右揃えにできます。 次の補間された文字列では、それぞれスペース 7 つを使用して、式を左揃えおよび右揃えにします。

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a>補間された文字列と `FormattableString` 書式指定

<xref:System.FormattableString> の規則に従う書式指定を適用することもできます。

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

さらに、型の注釈によって、補間された文字列を <xref:System.FormattableString> として型チェックできます。

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

型の注釈は、補間された文字列式自体に対して指定する必要があります。 F# では、補間された文字列は暗黙的に <xref:System.FormattableString> に変換されません。

## <a name="see-also"></a>関連項目

* [文字列](strings.md)
