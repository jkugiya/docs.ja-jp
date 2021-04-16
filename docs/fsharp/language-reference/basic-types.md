---
title: 基本型
description: F# 言語で使用されている基礎となる基本型について説明します。
ms.date: 08/15/2020
ms.openlocfilehash: 2bfc9ba9370cb8ba1fcc1d42369c2551cbb57623
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456914"
---
# <a name="basic-types"></a>基本型

このトピックでは、F# 言語で定義されている基本型の一覧を示します。 これらの型は F# で最も基本的なものであり、ほぼすべての F# プログラムの基礎となります。 これらは、.NET プリミティブ型のスーパーセットです。

|Type|.NET の種類|説明|例|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|設定可能な値は `true` および `false` です。|`true`/`false`|
|`byte`|<xref:System.Byte>|0 から 255 までの値。|`1uy`|
|`sbyte`|<xref:System.SByte>|-128 から 127 までの値。|`1y`|
|`int16`|<xref:System.Int16>|-32768 から 32767 までの値。|`1s`|
|`uint16`|<xref:System.UInt16>|0 から 65535 までの値。|`1us`|
|`int`|<xref:System.Int32>|-2,147,483,648 から 2,147,483,647 までの値。|`1`|
|`uint`|<xref:System.UInt32>|0 から 4,294,967,295 までの値。|`1u`|
|`int64`|<xref:System.Int64>|-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807 までの値。|`1L`|
|`uint64`|<xref:System.UInt64>|0 から 18,446,744,073,709,551,615 までの値。|`1UL`|
|`nativeint`|<xref:System.IntPtr>|符号付き整数としてのネイティブ ポインター。|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|符号なし整数としてのネイティブ ポインター。|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|有効数字が 28 桁以上の浮動小数点データ型。|`1.0`|
|`float`, `double`|<xref:System.Double>|64 ビット浮動小数点型。|`1.0`|
|`float32`, `single`|<xref:System.Single>|32 ビット浮動小数点型。|`1.0f`|
|`char`|<xref:System.Char>|Unicode 文字値。|`'c'`|
|`string`|<xref:System.String>|Unicode テキスト。|`"str"`|
|`unit`|適用外|実際の値が存在しないことを示します。 この型には、`()` で示される仮値が 1 つだけあります。 単位値 `()` は、値が必要であるものの、実際の値を使用できない、または意味を持つ値がない場合のプレースホルダーとしてよく使用されます。|`()`|

> [!NOTE]
> 64 ビット整数型に対して大きすぎる整数の計算は、`bigint` 型を使用して実行できます。 `bigint` は基本型とは見なされません。これは、`System.Numerics.BigInteger` の省略形です。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
