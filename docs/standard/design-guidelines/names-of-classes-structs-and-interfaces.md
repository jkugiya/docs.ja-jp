---
title: クラス、構造体、およびインターフェイスの名前
description: .NET ライブラリを拡張および操作するライブラリを設計するためのガイドラインの一部として、クラス、構造体およびインターフェイスの名前付けに関するこれらのガイドラインを使用します。
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 49bafda0d5c362fa02313c5304436069d054cfd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706516"
---
# <a name="names-of-classes-structs-and-interfaces"></a>クラス、構造体、およびインターフェイスの名前

次に示す名前付けのガイドラインは、一般的な型の名前付けに適用されます。

 ✔️ クラスと構造体には、Pascal 形式を使用して、名詞または名詞句で名前を付けてください。

 これにより、この型の名前が、動詞句を使用して名前が付けられたメソッドと区別されます。

 ✔️ インターフェイスには、形容詞句を使用するか、場合によっては名詞または名詞句を使用して名前を付けてください。

 名詞と名詞句を使用するのはまれで、型がインターフェイスではなく抽象クラスであることを示している可能性があります。

 ❌ クラス名にはプレフィックス (例: "C") を付けないでください。

 ✔️ 派生クラスの名前を基底クラスの名前で終了することを検討してください。

 これはとても読みやすく、関係が明確に説明されます。 コード内でのその例として、`Exception` の一種である `ArgumentOutOfRangeException` と、`Attribute` の一種である `SerializableAttribute` があります。 ただし、このガイドラインを適用する際には、合理的に判断することが重要です。たとえば、`Button` クラスは `Control` イベントの一種ですが、その名前に `Control` はありません。

 ✔️ インターフェイス名の前に I という文字を付けて、型がインターフェイスであることを示してください。

 たとえば、`IComponent` (わかりやすい名詞)、`ICustomAttributeProvider` (名詞句)、`IPersistable` (形容詞) は、適切なインターフェイス名です。 他の型名と同様に、省略形は避けてください。

 ✔️ クラスがインターフェイスの標準実装であるクラスとインターフェイスのペアを定義する場合は、名前の相違点がインターフェイス名の前の "I" プレフィックスだけとなるようにしてください。

## <a name="names-of-generic-type-parameters"></a>ジェネリック型パラメーターの名前

 .NET Framework 2.0 にはジェネリックが追加されました。 この機能により、"*型パラメーター*" と呼ばれる新しい種類の識別子が導入されました。

 ✔️ 1 文字の名前でも完全に説明され、説明的な名前を付けることに意味がない場合を除き、ジェネリック型パラメーターには説明的な名前を付けてください。

 ✔️ 1 文字の型パラメーターを持つ型の型パラメーター名として `T` を使用することを検討してください。

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ 型パラメーターの説明的な名前には `T` というプレフィックスを付けてください。

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ 型パラメーターに与えられた制約をパラメーターの名前で示唆することを検討してください。

 たとえば、`ISession` に制約されているパラメーターの名前を `TSession` にします。

## <a name="names-of-common-types"></a>一般的な型の名前

 ✔️ 特定の .NET Framework 型から派生した、またはそれを実装している型に名前を付ける場合は、次の表に記載されているガイドラインに従ってください。

|基本型|派生/実装型のガイドライン|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ カスタム属性クラスの名前にはサフィックス "Attribute" を追加してください。|
|`System.Delegate`|✔️ イベントで使用されるデリゲートの名前にはサフィックス "EventHandler" を追加してください。<br /><br /> ✔️ イベント ハンドラーとして使用されていないデリゲートの名前にはサフィックス "Callback" を追加してください。<br /><br /> ❌ デリゲートにはサフィックス "Delegate" を追加しないでください。|
|`System.EventArgs`|✔️ サフィックス "EventArgs" を追加してください。|
|`System.Enum`|❌ このクラスから派生させないでください。代わりに、お使いの言語でサポートされているキーワードを使用してください。たとえば、C# では `enum` キーワードを使用します。<br /><br /> ❌ サフィックス "Enum" または "Flag" は追加しないでください。|
|`System.Exception`|✔️ サフィックス "Exception" を追加してください。|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ サフィックス "Dictionary" を追加してください。 `IDictionary` は特定の型のコレクションですが、このガイドラインは、次に示す一般的なコレクションのガイドラインよりも優先されることに注意してください。|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ サフィックス "Collection" を追加してください。|
|`System.IO.Stream`|✔️ サフィックス "Stream" を追加してください。|
|`CodeAccessPermission IPermission`|✔️ サフィックス "Permission" を追加してください。|

## <a name="naming-enumerations"></a>列挙型に名前を付ける

 一般に、列挙型の名前は、標準的な型の名前付け規則 (Pascal 形式など) に従う必要があります。 ただし、列挙型にだけ適用される追加のガイドラインがあります。

 ✔️ 値がビット フィールドでない限り、列挙型には単数の型名を使用してください。

 ✔️ 値としてビット フィールドを持つ列挙型 (フラグ列挙型とも呼ばれます) には複数形の型名を使用してください。

 ❌ 列挙型の名前には "Enum" サフィックスを使用しないでください。

 ❌ 列挙型の名前には "Flag" または "Flags" サフィックスを使用しないでください。

 ❌ 列挙値の名前にはプレフィックスを使用しないでください (たとえば、ADO 列挙型に対する "ad"、リッチ テキスト列挙型に対する "rtf" など)。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [名前付けのガイドライン](naming-guidelines.md)
