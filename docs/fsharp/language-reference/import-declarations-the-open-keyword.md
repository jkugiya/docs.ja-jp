/---
title: 'インポート宣言: open キーワード'
description: 'F # インポート宣言と、完全修飾名を使用せずに参照できる要素を持つモジュールまたは名前空間を指定する方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 4d3fd159aa4b334e9db0d7f756047470ad9c0829
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739686"
---
# <a name="import-declarations-the-open-keyword"></a>インポート宣言: `open` キーワード

*インポート宣言* は、完全修飾名を使用せずに参照できる要素を持つモジュールまたは名前空間を指定します。

## <a name="syntax"></a>構文

```fsharp
open module-or-namespace-name
open type type-name
```

## <a name="remarks"></a>Remarks

常に完全修飾名前空間またはモジュールパスを使用してコードを参照すると、書き込み、読み取り、および保守が困難なコードを作成できます。 代わりに、 `open` 頻繁に使用されるモジュールと名前空間にキーワードを使用して、そのモジュールまたは名前空間のメンバーを参照するときに、完全修飾名の代わりに短い形式の名前を使用できます。 このキーワードは、C# の `using` キーワード、 `using namespace` Visual C++、Visual Basic に似てい `Imports` ます。

指定されたモジュールまたは名前空間は、同じプロジェクトまたは参照されるプロジェクトまたはアセンブリ内に存在する必要があります。 そうでない場合は、プロジェクトへの参照を追加するか、 `-reference` コマンドラインオプション (またはその省略形) を使用することができ `-r` ます。 詳細については、「 [コンパイラオプション](compiler-options.md)」を参照してください。

インポート宣言は、外側の名前空間、モジュール、またはファイルの末尾まで、宣言の後のコードで名前を使用できるようにします。

複数のインポート宣言を使用する場合は、別々の行に表示する必要があります。

次のコードは、キーワードを使用して `open` コードを簡略化する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F # コンパイラは、同じ名前が複数の開いているモジュールまたは名前空間で発生した場合に、あいまいさが発生した場合にエラーまたは警告を生成しません。 あいまいさが発生すると、F # は、最近開いたモジュールまたは名前空間を優先します。 たとえば、次のコードでは、 `empty` `Seq.empty` との `empty` 両方のモジュールにがある場合でも、はを意味し `List` `Seq` ます。

```fsharp
open List
open Seq
printfn %"{empty}"
```

したがって、同じ名前を持つメンバーが含まれているモジュールまたは名前空間を開く場合は注意が必要です。 `List` `Seq` 代わりに、修飾名の使用を検討してください。 コードがインポート宣言の順序に依存している状況を避ける必要があります。

## <a name="open-type-declarations"></a>オープン型の宣言

F # `open` は、次のような型でサポートされます。

```fsharp
open type System.Math
PI
```

これにより、型のアクセス可能なすべての静的フィールドとメンバーが公開されます。

また、 `open` F # で定義された [レコード](records.md) と [判別共用体](discriminated-unions.md) の型を使用して、静的メンバーを公開することもできます。 判別共用体の場合は、共用体ケースを公開することもできます。 これは、次のように、モジュール内で宣言された型の共用体ケースにアクセスする場合に役立ちます。

```fsharp
module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

## <a name="namespaces-that-are-open-by-default"></a>既定で開かれている名前空間

一部の名前空間は、明示的なインポート宣言がなくても暗黙的に開かれる F # コードでよく使用されます。 次の表は、既定で開かれている名前空間を示しています。

|名前空間|説明|
|---------|-----------|
|`FSharp.Core`|やなどの組み込み型の基本的な F # 型定義が含まれてい `int` `float` ます。|
|`FSharp.Core.Operators`|やなどの基本的な算術演算が含まれてい `+` `*` ます。|
|`FSharp.Collections`|やなどの変更できないコレクションクラスが含まれてい `List` `Array` ます。|
|`FSharp.Control`|レイジー評価や非同期ワークフローなどのコントロール構成要素の型が含まれています。|
|`FSharp.Text`|関数など、書式設定された IO 用の関数が含まれてい `printf` ます。|

## <a name="autoopen-attribute"></a>AutoOpen 属性

`AutoOpen`アセンブリが参照されたときに名前空間またはモジュールを自動的に開く場合は、アセンブリに属性を適用できます。 また、属性をモジュールに適用して、 `AutoOpen` 親モジュールまたは名前空間を開いたときに自動的にそのモジュールを開くようにすることもできます。 詳細については、「 [Autoopenattribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html)」を参照してください。

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 属性

モジュール、レコード、共用体の中には `RequireQualifiedAccess` 属性を指定できるものがあります。 この属性を指定したモジュール、レコード、共用体の要素を参照する場合は、コードがインポート宣言を含んでいたとしても完全修飾名を使用しなければいけません。 この属性を一般的に使用される名前で定義されている型に対して戦略的に使用することで、名前の競合を避けることができるため、ライブラリの変更に対するコードの回復性を高められます。 詳細については、「 [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [名前空間](namespaces.md)
- [モジュール](modules.md)
