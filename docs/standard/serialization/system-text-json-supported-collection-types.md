---
title: System.Text.Json でサポートされているコレクション型
description: System.Text.Json 名前空間の API によるシリアル化がサポートされているコレクション型について説明します。
ms.date: 02/01/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5a5016c70e86124510a4778aafb9fb14b1890add
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99547656"
---
# <a name="supported-collection-types-in-systemtextjson"></a>System.Text.Json でサポートされているコレクション型

この記事では、どのコレクションでシリアル化および逆シリアル化がサポートされているかを概説します。 <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> では、次の場合にシリアル化用のコレクション型をサポートしています。

* <xref:System.Collections.IEnumerable>から派生します。
* シリアル化可能な要素が含まれている。

シリアライザーが <xref:System.Collections.IEnumerable.GetEnumerator> メソッドを呼び出し、その要素を書き込みます。

逆シリアル化はこれよりも複雑であり、一部のコレクション型ではサポートされていません。

次のセクションでは、名前空間ごとに、シリアル化と逆シリアル化がサポートされている型を示します。

## <a name="systemarray-namespace"></a>System.Array 名前空間

| 種類                                                                                            | シリアル化 | 逆シリアル化 |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| [1 次元配列](../../csharp/programming-guide/arrays/single-dimensional-arrays.md) | ✔️           | ✔️              |
| [多次元配列](../../csharp/programming-guide/arrays/multidimensional-arrays.md)    | ❌           | ❌              |
| [ジャグ配列](../../csharp/programming-guide/arrays/jagged-arrays.md)                         | ✔️           | ✔️              |

## <a name="systemcollections-namespace"></a>System.Collections 名前空間

| 種類                                      | シリアル化 | 逆シリアル化 |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | ✔️           | ✔️              |
| <xref:System.Collections.BitArray>        | ✔️           | ❌              |
| <xref:System.Collections.DictionaryEntry> | ✔️           | ✔️              |
| <xref:System.Collections.Hashtable>       | ✔️           | ✔️              |
| <xref:System.Collections.Queue>           | ✔️           | ✔️              |
| <xref:System.Collections.SortedList>      | ✔️           | ✔️              |
| <xref:System.Collections.Stack>           | ✔️           | ✔️              |
| <xref:System.Collections.ICollection>     | ✔️           | ✔️              |
| <xref:System.Collections.IDictionary>     | ✔️           | ✔️              |
| <xref:System.Collections.IEnumerable>     | ✔️           | ✔️              |
| <xref:System.Collections.IList>           | ✔️           | ✔️              |

## <a name="systemcollectionsgeneric-namespace"></a>System.Collections.Generic 名前空間

::: zone pivot="dotnet-5-0"

| 種類                                                      | シリアル化 | 逆シリアル化 |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Generic.Dictionary%602> \*       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.HashSet%601>             | ✔️           | ✔️              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedList%601>          | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | ✔️           | ❌              |
| <xref:System.Collections.Generic.List%601>                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Queue%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedDictionary%602> \* | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedList%602> \*       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedSet%601>           | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Stack%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IDictionary%602> \*      | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IEnumerable%601>         | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IList%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyDictionary%602> \* | ✔️        | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.ISet%601>                | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| 種類                                                                                            | シリアル化 | 逆シリアル化 |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| [Dictionary\<string, TValue>](xref:System.Collections.Generic.Dictionary%602) \*                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | ✔️           | ✔️              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | ✔️           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Queue%601>                                                     | ✔️           | ✔️              |
| [SortedDictionary\<string, TValue>](xref:System.Collections.Generic.SortedDictionary%602) \*    | ✔️           | ✔️              |
| [SortedList\<string, TValue>](xref:System.Collections.Generic.SortedList%602) \*                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Stack%601>                                                     | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | ✔️           | ✔️              |
| [IDictionary\<string, TValue> ](xref:System.Collections.Generic.IDictionary%602) \*              | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IList%601>                                                     | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | ✔️           | ✔️              |
| [IReadOnlyDictionary\<string, TValue>](xref:System.Collections.Generic.IReadOnlyDictionary%602) \* | ✔️        | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | ✔️           | ✔️              |
| <xref:System.Collections.Generic.ISet%601>                                                      | ✔️           | ✔️              |

::: zone-end

\* 「[サポートされているキーの種類](#supported-key-types)」を参照してください。

## <a name="systemcollectionsimmutable-namespace"></a>System.Collections.Immutable 名前空間

::: zone pivot="dotnet-5-0"

| 種類                                                              | シリアル化 | 逆シリアル化 |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*  | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\* | ✔️      | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableStack%601> \*         | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableDictionary%602> \*\* | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableStack%601> \*        | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| 種類                                                                                                          | シリアル化 | 逆シリアル化 |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | ✔️           | ✔️              |
| [ImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableDictionary%602) \*\*        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | ✔️           | ✔️              |
| [ImmutableSortedDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableSortedDictionary%602) \*\*| ✔️       | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableStack%601> \*                                                     | ✔️           | ✔️              |
| [IImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.IImmutableDictionary%602) \*\*      | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableStack%601> \*                                                    | ✔️           | ✔️              |

::: zone-end

\* 「[Stack\<T> のラウンド トリップをサポートする](system-text-json-converters-how-to.md#support-round-trip-for-stackt)」を参照してください。

\* 「\*サポートされているキーの種類[」を参照してください](#supported-key-types)。

## <a name="systemcollectionsspecialized-namespace"></a>System.Collections.Specialized 名前空間

| 種類                                                      | シリアル化 | 逆シリアル化 |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | ✔️           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | ✔️           | ✔️              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | ✔️           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | ✔️           | ✔️              |
| <xref:System.Collections.Specialized.StringCollection>    | ✔️           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | ✔️           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | ✔️           | ❌              |

\* <xref:System.Collections.Specialized.BitVector32> が逆シリアル化されると、パブリック セッターがないため、<xref:System.Collections.Specialized.BitVector32.Data> はスキップされます。 例外はスローされません。

## <a name="systemcollectionsconcurrent-namespace"></a>System.Collections.Concurrent 名前空間

::: zone pivot="dotnet-5-0"

| 種類                                                          | シリアル化 | 逆シリアル化 |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\* | ✔️      | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | ✔️           | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentStack%601> \*   | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| 種類                                                        | シリアル化 | 逆シリアル化 |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | ✔️           | ❌              |
| [ConcurrentDictionary\<string, TValue>](xref:System.Collections.Concurrent.ConcurrentDictionary%602) \*\* |✔️|✔️|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | ✔️           | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentStack%601> \* | ✔️           | ✔️              |

::: zone-end

\* 「[Stack\<T> のラウンド トリップをサポートする](system-text-json-converters-how-to.md#support-round-trip-for-stackt)」を参照してください。

\* 「\*サポートされているキーの種類[」を参照してください](#supported-key-types)。

## <a name="systemcollectionsobjectmodel-namespace"></a>System.Collections.ObjectModel 名前空間

::: zone pivot="dotnet-5-0"

| 種類                                                           | シリアル化 | 逆シリアル化 |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | ✔️            | ✔️             |
| [KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \* |✔️|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | ✔️            | ✔️             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | ✔️            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | ✔️            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | ✔️    | ❌             |

\* `string` ではないキーはサポートされていません。

::: zone-end

::: zone pivot="dotnet-core-3-1"

| 種類                                                           | シリアル化 | 逆シリアル化 |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | ✔️            | ✔️             |
| [KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \* |✔️|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | ✔️            | ✔️             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | ✔️            | ❌             |
| [ReadOnlyDictionary\<string, TValue>](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602) \* |✔️|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| ✔️     | ❌             |

\* 「[サポートされているキーの種類](#supported-key-types)」を参照してください。

::: zone-end

## <a name="custom-collections"></a>カスタム コレクション

上記のいずれの名前空間にも含まれないコレクション型は、カスタム コレクションと見なされます。 このような型には、ユーザー定義型と ASP.NET Core で定義されている型が含まれます。 たとえば、このグループには <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> があります。

すべてのカスタム コレクション (`IEnumerable` から派生するすべてのもの) は、その要素の型がサポートされている限り、シリアル化でサポートされます。

### <a name="custom-collections-with-deserialization-support"></a>逆シリアル化がサポートされているカスタム コレクション

次の場合、逆シリアル化にカスタム コレクションがサポートされます。

::: zone pivot="dotnet-5-0"

* インターフェイスでも抽象でもない場合。
* パラメーターのないコンストラクターがある場合。
* <xref:System.Text.Json.JsonSerializer> によってサポートされる要素型が含まれている場合。
* 次のインターフェイスまたはクラスを 1 つ以上実装または継承している場合。
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <xref:System.Collections.Concurrent.ConcurrentStack%601> \*
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <xref:System.Collections.Generic.IDictionary%602> \*\*
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <xref:System.Collections.Stack> \*
  * <xref:System.Collections.Generic.Stack%601> \*

::: zone-end

::: zone pivot="dotnet-core-3-1"

* インターフェイスでも抽象でもない場合。
* パラメーターのないコンストラクターがある場合。
* <xref:System.Text.Json.JsonSerializer> によってサポートされる要素型が含まれている場合。
* 次のインターフェイスまたはクラスを 1 つ以上実装または継承している場合。
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <xref:System.Collections.Concurrent.ConcurrentStack%601> \*
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * [IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \* \*
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <xref:System.Collections.Stack> \*
  * <xref:System.Collections.Generic.Stack%601> \*

::: zone-end

  \* 「[Stack\<T> のラウンド トリップをサポートする](system-text-json-converters-how-to.md#support-round-trip-for-stackt)」を参照してください。

  \* 「\*サポートされているキーの種類[」を参照してください](#supported-key-types)。

### <a name="custom-collections-with-known-issues"></a>既知の問題があるカスタム コレクション

次のカスタム コレクションには既知の問題があります。

- <xref:System.Dynamic.ExpandoObject>: [dotnet/runtime#29690](https://github.com/dotnet/runtime/issues/29690) に関するページを参照してください。
- <xref:System.Dynamic.DynamicObject>: [dotnet/runtime#1808](https://github.com/dotnet/runtime/issues/1808) に関するページを参照してください。
- <xref:System.Data.DataTable>: [dotnet/docs#21366](https://github.com/dotnet/docs/issues/21366) に関するページを参照してください。
- <xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559) に関するページを参照してください。
- <xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559) に関するページを参照してください。

既知の問題の詳細については、[System.Text.Json のオープンのイシュー](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)に関するページを参照してください。

## <a name="supported-key-types"></a>サポートされているキーの種類

::: zone pivot="dotnet-5-0"

`Dictionary` および `SortedList` 型のキーには、次の型がサポートされています。

* `Boolean`
* `Byte`
* `DateTime`
* `DateTimeOffset`
* `Decimal`
* `Double`
* `Enum`
* `Guid`
* `Int16`
* `Int32`
* `Int64`
* `Object` (シリアル化と、ランタイム型がこの一覧でサポートされている型のいずれかである場合のみ)。
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

\*\* .NET Core 3.1 では、`Dictionary` および `SortedList` 型に `string` ではないキーはサポートされていません。

::: zone-end

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JsonSerializerOptions インスタンスのインスタンスを作成する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [参照を保持する](system-text-json-preserve-references.md)
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [Newtonsoft.Json から System.Text.Json に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md)
* [文字エンコードをカスタマイズする](system-text-json-character-encoding.md)
* [カスタム シリアライザーと逆シリアライザーを作成する](write-custom-serializer-deserializer.md)
* [JSON シリアル化のためのカスタム コンバーターの作成](system-text-json-converters-how-to.md)
* [DateTime および DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)
