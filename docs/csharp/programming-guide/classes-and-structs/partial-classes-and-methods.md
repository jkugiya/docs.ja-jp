---
title: 部分クラスと部分メソッド - C# プログラミング ガイド
description: C# の部分クラスと部分メソッドでは、クラス、構造体、インターフェイス、またはメソッドの定義を、2 つ以上のソース ファイルに分割できます。
ms.date: 03/23/2021
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 2132dd8e729725f0dd9bcb4477a3a604aa7065a0
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111050"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>部分クラスと部分メソッド (C# プログラミング ガイド)

[クラス](../../language-reference/keywords/class.md)、[構造体](../../language-reference/builtin-types/struct.md)、[インターフェイス](../../language-reference/keywords/interface.md)やメソッドの定義を複数のソース ファイルに分割できます。 各ソース ファイルには型やメソッドの定義のセクションが含まれ、分割されたすべての部分はアプリケーションのコンパイル時に結合されます。

## <a name="partial-classes"></a>部分クラス

クラス定義を分割するのが望ましいのは、次のような場合です。

- 大型プロジェクトを開発する際にクラスを別個のファイルに分割すると、複数のプログラマーが同時にそのクラスの作業を行うことができます。

- 自動的に生成されたソースを使用する場合、ソース ファイルを再作成することなく、コードをクラスに追加できます。 Visual Studio では、Windows フォームや Web サービス ラッパー コードなどを作成するときにこのアプローチを使用します。 Visual Studio によって作成されたファイルを変更せずに、これらのクラスを使用するコードを作成できます。

- クラス定義を分割するには、次のように [partial](../../language-reference/keywords/partial-type.md) キーワード修飾子を使用します。

  [!code-csharp[EmployeeExample#1](snippets/partial-classes-and-methods/Program.cs#1)]

`partial` キーワードは、クラス、構造体、またはインターフェイスの他の部分を名前空間内で定義できることを示します。 `partial` キーワードは、すべての部分で使用する必要があります。 最終的な型を形成するためには、コンパイル時にすべての部分が利用可能である必要があります。 また、すべての部分で同じアクセシビリティ (`public` や `private` など) を使用する必要があります。

abstract と宣言された部分がある場合、型全体が抽象と見なされます。 sealed と宣言された部分がある場合、型全体が sealed と見なされます。 また、基本データ型を宣言する部分がある場合は、型全体が該当するクラスを継承します。

基底クラスを指定する部分はすべて一致する必要がありますが、基底クラスを省略する部分も基本データ型を継承します。 部分は別の基本インターフェイスを指定でき、すべての部分宣言で示されたすべてのインターフェイスが最終的な型によって実装されます。 部分定義で宣言されたクラス、構造体、インターフェイスの各メンバーは、他のすべての部分で利用できます。 最終的な型は、コンパイル時にすべての部分を結合して形成されます。

> [!NOTE]
> `partial` 識別子は、デリゲートや列挙宣言では使用できません。

次の例は、入れ子にされた型は、それを包含する型自体が partial でない場合でも、partial にできることを示しています。

[!code-csharp[NestedPartialTypes#2](snippets/partial-classes-and-methods/Program.cs#2)]

部分型定義の属性は、コンパイル時に結合されます。 たとえば、次のような宣言があるとします。

[!code-csharp[PartialMoonDeclarations#3](snippets/partial-classes-and-methods/Program.cs#3)]

これらは、次の宣言と等価です。

[!code-csharp[SingleMoonDeclaration#4](snippets/partial-classes-and-methods/Program.cs#4)]

各部分型定義に含まれる次の要素は、すべて結合されます。

- XML コメント

- インターフェイス

- ジェネリック型パラメーター属性

- クラス属性

- メンバー

たとえば、次のような宣言があるとします。

[!code-csharp[PartialEarthDeclarations#5](snippets/partial-classes-and-methods/Program.cs#5)]

これらは、次の宣言と等価です。

[!code-csharp[SingleEarthDeclaration#6](snippets/partial-classes-and-methods/Program.cs#6)]

### <a name="restrictions"></a>制約

部分クラス定義を使用する場合は、いくつかの規則に従う必要があります。

- 同じ型の部分である部分型定義はすべて `partial` で修飾する必要があります。 たとえば、次のクラス宣言はエラーになります。

  [!code-csharp[AllDefinitionsMustBePartials#7](snippets/partial-classes-and-methods/Program.cs#7)]

- `partial` 修飾子は、`class`、`struct`、または `interface` キーワードの直前にのみ配置できます。

- 入れ子にされた部分型は、次の例に示すように、部分型定義で宣言できます。

  [!code-csharp[NestedPartialTypes#8](snippets/partial-classes-and-methods/Program.cs#8)]

- 同じ型の部分である部分型定義は、すべて同じアセンブリおよび同じモジュール (.exe ファイルまたは .dll ファイル) 内で定義する必要があります。 部分定義は、複数のモジュールにまたがることができません。

- クラス名とジェネリック型パラメーターはすべての部分型定義で一致する必要があります。 ジェネリック型は partial にできます。 それぞれの部分宣言では、同じパラメーター名を同じ順序で使用する必要があります。

- 以下のキーワードは、部分型定義では省略できますが、ある 1 つの部分型定義に存在する場合は、同じ型の別の部分定義で指定されているキーワードと競合できません。

  - [public](../../language-reference/keywords/public.md)

  - [private](../../language-reference/keywords/private.md)

  - [protected](../../language-reference/keywords/protected.md)

  - [internal](../../language-reference/keywords/internal.md)

  - [abstract](../../language-reference/keywords/abstract.md)

  - [sealed](../../language-reference/keywords/sealed.md)

  - 基本クラス

  - [new](../../language-reference/keywords/new-modifier.md) 修飾子 (入れ子にされた部分)

  - ジェネリック制約

詳細については、「[型パラメーターの制約](../generics/constraints-on-type-parameters.md)」を参照してください。

## <a name="example-1"></a>例 1

### <a name="description"></a>説明

次の例では、クラス `Coords` のフィールドとコンストラクターを 1 つの部分クラス定義で宣言し、メンバー `PrintCoords` を別の部分クラス定義で宣言しています。

### <a name="code"></a>コード

[!code-csharp[CoordsExample#9](snippets/partial-classes-and-methods/Program.cs#9)]

## <a name="example-2"></a>例 2

### <a name="description"></a>説明

次の例は、部分構造体と部分インターフェイスも開発できることを示しています。

### <a name="code"></a>コード

[!code-csharp[PartialStructsAndInterfaces#10](snippets/partial-classes-and-methods/Program.cs#10)]

## <a name="partial-methods"></a>部分メソッド

部分クラスまたは構造体には部分メソッドを含めることができます。 クラスのある部分に、メソッドのシグネチャが含まれます。 実装は、同じ部分でも別の部分でも定義できます。 実装が指定されていない場合、メソッドとメソッドに対するすべての呼び出しは、コンパイル時に削除されます。 メソッド シグネチャによっては、実装が必要になる場合があります。

部分メソッドを使用すると、イベントと同様に、クラスのある部分の実装者がメソッドを定義できます。 クラスの別の部分の実装者は、メソッドを実装するかどうかを決定できます。 メソッドが実装されない場合、コンパイラは、メソッド シグネチャとメソッドに対するすべての呼び出しを削除します。 このメソッドの呼び出しは、呼び出しの引数の評価から発生するすべての結果を含め、実行時に影響を及ぼしません。 そのため、実装が指定されていない場合でも、部分クラス内のすべてのコードで部分メソッドを自由に使用できます。 実装されていないメソッドが呼び出された場合、コンパイル時エラーまたは実行時エラーにはなりません。

部分メソッドは、生成されるコードをカスタマイズする方法として特に便利です。 メソッドの名前とシグネチャを予約できるため、生成されるコードでメソッドを呼び出すことができます。ただし、メソッドを実装するかどうかは開発者が決定できます。 部分クラスと同様に、部分メソッドでも、コード ジェネレーターによって作成されたコードと人間である開発者によって作成されたコードを実行時コストなしで連携させることができます。

部分メソッドの宣言は、定義と実装の 2 つの部分から成ります。 これらは部分クラスの別々の部分にあっても同じ部分にあってもかまいません。 実装宣言がない場合は、定義宣言とメソッドに対するすべての呼び出しの両方が、コンパイラによる最適化によって除外されます。

```csharp
// Definition in file1.cs
partial void OnNameChanged();

// Implementation in file2.cs
partial void OnNameChanged()
{
  // method body
}
```

- 部分メソッドの宣言は、コンテキスト キーワード [partial](../../language-reference/keywords/partial-type.md) で始まる必要があります。

- 部分型の両方の部分で部分メソッド シグネチャが一致する必要があります。

- 部分メソッドには [static](../../language-reference/keywords/static.md) 修飾子と [unsafe](../../language-reference/keywords/unsafe.md) 修飾子を使用できます。

- 部分メソッドはジェネリックにできます。 制約は部分メソッドの定義宣言に置き、必要に応じて実装宣言で繰り返すことができます。 パラメーター名と型パラメーター名は、定義宣言と実装宣言で同じである必要はありません。

- [delegate](../../language-reference/builtin-types/reference-types.md) は、定義および実装されている部分メソッドには使用できますが、定義されているのみの部分メソッドには使用できません。

次の場合には、部分メソッドを実装する必要はありません。

- アクセシビリティ修飾子 (既定の [private](../../language-reference/keywords/private.md) を含む) はありません。

- [void](../../language-reference/builtin-types/void.md) を返します。

- [out](../../language-reference/keywords/out-parameter-modifier.md) パラメーターはありません。

- [virtual](../../language-reference/keywords/virtual.md)、[override](../../language-reference/keywords/override.md)、[sealed](../../language-reference/keywords/sealed.md)、[new](../../language-reference/keywords/new-modifier.md)、[extern](../../language-reference/keywords/extern.md) のいずれの修飾子もありません。

これらのすべての制限に準拠していないメソッド (`public virtual partial void` メソッドなど) は、実装を提供する必要があります。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[部分型](~/_csharplang/spec/classes.md#partial-types)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [クラス](./classes.md)
- [構造体型](../../language-reference/builtin-types/struct.md)
- [インターフェイス](../interfaces/index.md)
- [partial (型)](../../language-reference/keywords/partial-type.md)
