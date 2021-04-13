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
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="cb198-103">クラス、構造体、およびインターフェイスの名前</span><span class="sxs-lookup"><span data-stu-id="cb198-103">Names of Classes, Structs, and Interfaces</span></span>

<span data-ttu-id="cb198-104">次に示す名前付けのガイドラインは、一般的な型の名前付けに適用されます。</span><span class="sxs-lookup"><span data-stu-id="cb198-104">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="cb198-105">✔️ クラスと構造体には、Pascal 形式を使用して、名詞または名詞句で名前を付けてください。</span><span class="sxs-lookup"><span data-stu-id="cb198-105">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="cb198-106">これにより、この型の名前が、動詞句を使用して名前が付けられたメソッドと区別されます。</span><span class="sxs-lookup"><span data-stu-id="cb198-106">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="cb198-107">✔️ インターフェイスには、形容詞句を使用するか、場合によっては名詞または名詞句を使用して名前を付けてください。</span><span class="sxs-lookup"><span data-stu-id="cb198-107">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="cb198-108">名詞と名詞句を使用するのはまれで、型がインターフェイスではなく抽象クラスであることを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cb198-108">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="cb198-109">❌ クラス名にはプレフィックス (例: "C") を付けないでください。</span><span class="sxs-lookup"><span data-stu-id="cb198-109">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="cb198-110">✔️ 派生クラスの名前を基底クラスの名前で終了することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-110">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="cb198-111">これはとても読みやすく、関係が明確に説明されます。</span><span class="sxs-lookup"><span data-stu-id="cb198-111">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="cb198-112">コード内でのその例として、`Exception` の一種である `ArgumentOutOfRangeException` と、`Attribute` の一種である `SerializableAttribute` があります。</span><span class="sxs-lookup"><span data-stu-id="cb198-112">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="cb198-113">ただし、このガイドラインを適用する際には、合理的に判断することが重要です。たとえば、`Button` クラスは `Control` イベントの一種ですが、その名前に `Control` はありません。</span><span class="sxs-lookup"><span data-stu-id="cb198-113">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="cb198-114">✔️ インターフェイス名の前に I という文字を付けて、型がインターフェイスであることを示してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-114">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="cb198-115">たとえば、`IComponent` (わかりやすい名詞)、`ICustomAttributeProvider` (名詞句)、`IPersistable` (形容詞) は、適切なインターフェイス名です。</span><span class="sxs-lookup"><span data-stu-id="cb198-115">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="cb198-116">他の型名と同様に、省略形は避けてください。</span><span class="sxs-lookup"><span data-stu-id="cb198-116">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="cb198-117">✔️ クラスがインターフェイスの標準実装であるクラスとインターフェイスのペアを定義する場合は、名前の相違点がインターフェイス名の前の "I" プレフィックスだけとなるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="cb198-117">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="cb198-118">ジェネリック型パラメーターの名前</span><span class="sxs-lookup"><span data-stu-id="cb198-118">Names of Generic Type Parameters</span></span>

 <span data-ttu-id="cb198-119">.NET Framework 2.0 にはジェネリックが追加されました。</span><span class="sxs-lookup"><span data-stu-id="cb198-119">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="cb198-120">この機能により、"*型パラメーター*" と呼ばれる新しい種類の識別子が導入されました。</span><span class="sxs-lookup"><span data-stu-id="cb198-120">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="cb198-121">✔️ 1 文字の名前でも完全に説明され、説明的な名前を付けることに意味がない場合を除き、ジェネリック型パラメーターには説明的な名前を付けてください。</span><span class="sxs-lookup"><span data-stu-id="cb198-121">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="cb198-122">✔️ 1 文字の型パラメーターを持つ型の型パラメーター名として `T` を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-122">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="cb198-123">✔️ 型パラメーターの説明的な名前には `T` というプレフィックスを付けてください。</span><span class="sxs-lookup"><span data-stu-id="cb198-123">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="cb198-124">✔️ 型パラメーターに与えられた制約をパラメーターの名前で示唆することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-124">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="cb198-125">たとえば、`ISession` に制約されているパラメーターの名前を `TSession` にします。</span><span class="sxs-lookup"><span data-stu-id="cb198-125">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="cb198-126">一般的な型の名前</span><span class="sxs-lookup"><span data-stu-id="cb198-126">Names of Common Types</span></span>

 <span data-ttu-id="cb198-127">✔️ 特定の .NET Framework 型から派生した、またはそれを実装している型に名前を付ける場合は、次の表に記載されているガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="cb198-127">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="cb198-128">基本型</span><span class="sxs-lookup"><span data-stu-id="cb198-128">Base Type</span></span>|<span data-ttu-id="cb198-129">派生/実装型のガイドライン</span><span class="sxs-lookup"><span data-stu-id="cb198-129">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="cb198-130">✔️ カスタム属性クラスの名前にはサフィックス "Attribute" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-130">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="cb198-131">✔️ イベントで使用されるデリゲートの名前にはサフィックス "EventHandler" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-131">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="cb198-132">✔️ イベント ハンドラーとして使用されていないデリゲートの名前にはサフィックス "Callback" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-132">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="cb198-133">❌ デリゲートにはサフィックス "Delegate" を追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="cb198-133">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="cb198-134">✔️ サフィックス "EventArgs" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-134">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="cb198-135">❌ このクラスから派生させないでください。代わりに、お使いの言語でサポートされているキーワードを使用してください。たとえば、C# では `enum` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb198-135">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="cb198-136">❌ サフィックス "Enum" または "Flag" は追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="cb198-136">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="cb198-137">✔️ サフィックス "Exception" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-137">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="cb198-138">✔️ サフィックス "Dictionary" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-138">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="cb198-139">`IDictionary` は特定の型のコレクションですが、このガイドラインは、次に示す一般的なコレクションのガイドラインよりも優先されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-139">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="cb198-140">✔️ サフィックス "Collection" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-140">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="cb198-141">✔️ サフィックス "Stream" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-141">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="cb198-142">✔️ サフィックス "Permission" を追加してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-142">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="cb198-143">列挙型に名前を付ける</span><span class="sxs-lookup"><span data-stu-id="cb198-143">Naming Enumerations</span></span>

 <span data-ttu-id="cb198-144">一般に、列挙型の名前は、標準的な型の名前付け規則 (Pascal 形式など) に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb198-144">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="cb198-145">ただし、列挙型にだけ適用される追加のガイドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="cb198-145">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="cb198-146">✔️ 値がビット フィールドでない限り、列挙型には単数の型名を使用してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-146">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="cb198-147">✔️ 値としてビット フィールドを持つ列挙型 (フラグ列挙型とも呼ばれます) には複数形の型名を使用してください。</span><span class="sxs-lookup"><span data-stu-id="cb198-147">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="cb198-148">❌ 列挙型の名前には "Enum" サフィックスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="cb198-148">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="cb198-149">❌ 列挙型の名前には "Flag" または "Flags" サフィックスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="cb198-149">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="cb198-150">❌ 列挙値の名前にはプレフィックスを使用しないでください (たとえば、ADO 列挙型に対する "ad"、リッチ テキスト列挙型に対する "rtf" など)。</span><span class="sxs-lookup"><span data-stu-id="cb198-150">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="cb198-151">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="cb198-151">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="cb198-152">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="cb198-152">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="cb198-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb198-153">See also</span></span>

- [<span data-ttu-id="cb198-154">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="cb198-154">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="cb198-155">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="cb198-155">Naming Guidelines</span></span>](naming-guidelines.md)
