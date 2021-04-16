---
title: 抽象クラス
description: 一部またはすべてのメンバーを実装しないままにして、さまざまなオブジェクト型のセットに共通の機能を表現するための F# の抽象クラスについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: d7fc87178cff7c5c824992c97198b49f87025f00
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082949"
---
# <a name="abstract-classes"></a>抽象クラス

"*抽象クラス*" は、一部またはすべてのメンバーを実装しないままにして、派生クラスによって実装できるようにするためのクラスです。

## <a name="syntax"></a>構文

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>解説

オブジェクト指向プログラミングでは、抽象クラスは、階層の基底クラスとして使用され、さまざまなオブジェクト型のセットに共通の機能を表します。 "抽象" という名前が示すとおり、多くの場合、抽象クラスは問題ドメインの具象エンティティに直接対応していません。 ただし、これらはさまざまな具象エンティティが共通して持つものを表しています。

抽象クラスには `AbstractClass` 属性が必要です。 メンバーは実装されているものと実装されていないものがあります。 クラスについて "*抽象*" という用語を使用する場合の意味は、他の .NET 言語の場合と同じです。ただし、メソッド (およびプロパティ) について "*抽象*" という用語を使用する場合の意味は、F# と他の .NET 言語とで少し異なります。 F# では、メソッドが `abstract` キーワードでマークされている場合は、メンバーが、その型の仮想関数の内部テーブルに "*仮想ディスパッチ スロット*" と呼ばれるエントリを持っていることを示します。 つまり、メソッドは仮想ですが、F# 言語では `virtual` キーワードは使用されません。 キーワード `abstract` は、そのメソッドが実装されているかどうかに関係なく、仮想メソッドに対して使用されます。 仮想ディスパッチ スロットの宣言は、そのディスパッチ スロットのメソッドの定義とは別個のものです。 したがって、別の .NET 言語の場合に相当する F# での仮想メソッドの宣言と定義は、`default` キーワードまたは `override` キーワードのいずれかを使用した抽象メソッド宣言と別個の定義の両方を組み合わせたものになります。 詳細と例については、「[メソッド](./members/methods.md)」をご覧ください。

クラスは、宣言されているが定義されていない抽象メソッドがある場合にのみ、抽象と見なされます。 したがって、抽象メソッドを持つクラスは、必ずしも抽象クラスではありません。 クラスに未定義の抽象メソッドがある場合を除き、**AbstractClass** 属性は使用しないでください。

上記の構文で、*accessibility-modifier* には `public`、`private`、または `internal` を指定できます。 詳しくは、「[アクセス制御](access-control.md)」をご覧ください。

他の型と同様に、抽象クラスは、1 つの基底クラスと 1 つ以上の基底インターフェイスを持つことができます。 各基底クラスまたはインターフェイスは、`inherit` キーワードと共に別個の行に指定します。

抽象クラスの型定義には、完全に定義されたメンバーを含めることができますが、抽象メンバーを含めることもできます。 抽象メンバーの構文は、上記の構文で別個に示されています。 この構文で、メンバーの "*型シグネチャ*" は、順番に並べたパラメーター型と戻り値の型を、カリー化およびタプル化パラメーターに応じて `->` トークンまたは `*` トークンで区切ったものを含むリストです。 抽象メンバーの型シグネチャの構文は、シグネチャ ファイルで使用されているもの、および Visual Studio Code エディターで IntelliSense によって示されるものと同じです。

次のコードは、抽象クラス Shape と、2 つの抽象ではない派生クラス Square と Circle の例を示しています。 この例は、抽象クラス、メソッド、プロパティの使用方法を示しています。 この例で、抽象クラス Shape は、具象エンティティである円と正方形に共通の要素を表しています。 すべての図形の (2 次元座標系における) 共通の特徴が、Shape クラスに抽象化されています。グリッド上の位置、回転角度、面積、外周の各プロパティです。 これらのうち位置だけは個々の図形で動作を変更することはできませんが、それ以外はオーバーライドできます。

rotation メソッドは、Circle クラスのように、オーバーライドすることができます。円は対称形であるため、回転させても変化しません。 そのため、Circle クラスでは、rotation メソッドは何も実行しないメソッドに置き換えられています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**出力:**

```console
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>関連項目

- [クラス](classes.md)
- [メンバー](./members/index.md)
- [メソッド](./members/methods.md)
- [プロパティ](./members/Properties.md)
