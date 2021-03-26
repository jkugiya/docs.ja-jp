---
title: 組み込み型 - C# リファレンス
description: C# の組み込みの値型と参照型を示します
ms.date: 03/15/2021
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.openlocfilehash: c2b1c736e17e55913ef1c593813717dd33efd6c3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759717"
---
# <a name="built-in-types-c-reference"></a>組み込み型 (C# リファレンス)

C# の組み込みの[値](value-types.md)型を次の表に一覧表示します。

|C# 型キーワード|.NET 型|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`nint`](nint-nuint.md)|<xref:System.IntPtr?displayProperty=nameWithType>|
|[`nuint`](nint-nuint.md)|<xref:System.UIntPtr?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

C# の組み込みの[参照](../keywords/reference-types.md)型を次の表に一覧表示します。

|C# 型キーワード|.NET 型|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|
|[`dynamic`](reference-types.md#the-dynamic-type)|<xref:System.Object?displayProperty=nameWithType>|

上の表の左の列にある各 C# 型キーワード ([nint と nuint](nint-nuint.md) を除く) は、対応する .NET 型の別名です。 これらは交換可能です。 たとえば、次の宣言では、同じ型の変数が宣言されています。

```csharp
int a = 123;
System.Int32 b = 123;
```

最初のテーブルの最後の 2 行の `nint` 型と `nuint` 型は、ネイティブサイズの整数です。 これらは、指定された .NET 型によって内部で表現されますが、いずれの場合もキーワードと .NET 型は交換できません。 コンパイラによって、`nint` と `nuint` に対して、整数型としての演算と変換が提供されます。ポインター型 `System.IntPtr` と `System.UIntPtr` に対しては提供されません。 詳細については、[`nint` 型と `nuint` 型](nint-nuint.md)に関するページを参照してください。

[`void`](void.md) キーワードで、値がないことが表されます。 値を返さないメソッドの戻り値の型として使用します。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# 型の既定値](default-values.md)
