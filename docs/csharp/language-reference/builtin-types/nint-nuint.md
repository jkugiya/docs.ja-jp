---
description: C# の組み込みの nint 型と nuint 型について
title: nint 型と nuint 型 - C# リファレンス
ms.date: 03/15/2021
f1_keywords:
- nint_CSharpKeyword
- nuint_CSharpKeyword
helpviewer_keywords:
- nint data type [C#]
- nuint data type [C#]
ms.openlocfilehash: fc779731d7f67fd0239f095d1dd17217a56622f6
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760822"
---
# <a name="nint-and-nuint-types-c-reference"></a>`nint` 型と `nuint` 型 (C# リファレンス)

C# 9.0 以降、`nint` キーワードと `nuint` キーワードを使用して、*ネイティブサイズの整数* を定義できます。 これらは、32 ビット プロセスで実行される場合は 32 ビット整数、64 ビット プロセスで実行される場合は 64 ビット整数です。 これらは、相互運用シナリオ、低レベル ライブラリ、および整数演算が多用されるシナリオでパフォーマンスを最適化するために使用できます。

ネイティブサイズの整数型は、.NET 型 <xref:System.IntPtr?displayProperty=nameWithType> および <xref:System.UIntPtr?displayProperty=nameWithType> として内部で表現されます。 他の数値型と異なり、キーワードは単純に型の別名ではありません。 次のステートメントは同等ではありません。

```csharp
nint a = 1;
System.IntPtr a = 1;
```

コンパイラでは、`nint` と `nuint` に対して、整数型に適した演算と変換が提供されます。

## <a name="run-time-native-integer-size"></a>実行時ネイティブ整数サイズ

実行時にネイティブサイズの整数のサイズを取得するには、`sizeof()` を使用できます。 ただし、コードを安全でないコンテキストでコンパイルする必要があります。 例:

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="SizeOf":::

また、静的な <xref:System.IntPtr.Size?displayProperty=nameWithType> および <xref:System.UIntPtr.Size?displayProperty=nameWithType> プロパティから同等の値を取得することもできます。

## <a name="minvalue-and-maxvalue"></a>MinValue と MaxValue

実行時にネイティブサイズの整数の最小値と最大値を取得するには、次の例のように、`nint` キーワードと `nuint` キーワードで、`MinValue` と `MaxValue` を静的プロパティとして使用します。

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="MinMax":::

## <a name="constants"></a>定数

次の範囲の定数値を使用できます。

* `nint` の場合: <xref:System.Int32.MinValue?displayProperty=nameWithType> から <xref:System.Int32.MaxValue?displayProperty=nameWithType>。
* `nuint` の場合: <xref:System.UInt32.MinValue?displayProperty=nameWithType> から <xref:System.UInt32.MaxValue?displayProperty=nameWithType>。

## <a name="conversions"></a>コンバージョン

コンパイラによって、他の数値型への暗黙的と明示的な変換が提供されます。 詳細については、「[組み込みの数値変換](numeric-conversions.md)」に関するページを参照してください。

## <a name="literals"></a>リテラル

ネイティブサイズの整数リテラルには、直接の構文がありません。 `long` を示す `L` など、リテラルがネイティブサイズの整数であることを示すサフィックスはありません。 代わりに、他の整数値の暗黙的または明示的なキャストを使用できます。 例:

```csharp
nint a = 42
nint a = (nint)42;
```

## <a name="unsupported-intptruintptr-members"></a>サポートされていない IntPtr または UIntPtr メンバー

<xref:System.IntPtr> および <xref:System.UIntPtr> の次のメンバーは、`nint` 型および `nuint` 型ではサポートされていません。

* パラメーター化されたコンストラクター
* <xref:System.IntPtr.Add(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.CompareTo%2A>
* <xref:System.IntPtr.Size> - 代わりに [sizeOf ()](#run-time-native-integer-size) を使用してください。 `nint.Size` はサポートされていませんが、`IntPtr.Size` を使用して同等の値を取得することができます。
* <xref:System.IntPtr.Subtract(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.ToInt32%2A>
* <xref:System.IntPtr.ToInt64%2A>
* <xref:System.IntPtr.ToPointer%2A>
* <xref:System.IntPtr.Zero> - 代わりに 0 を使用してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)と、C# 9.0 機能提案メモの「[ネイティブサイズの整数](~/_csharplang/proposals/csharp-9.0/native-integers.md)」セクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [値型](value-types.md)
- [整数数値型](integral-numeric-types.md)
- [組み込みの数値変換](numeric-conversions.md)
