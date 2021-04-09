---
description: sizeof 演算子 - C# リファレンス
title: sizeof 演算子 - C# リファレンス
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 6685cdb4fba2460ee4a47b004aa6911ab76235a4
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497373"
---
# <a name="sizeof-operator-c-reference"></a>sizeof 演算子 (C# リファレンス)

`sizeof` は、指定された型の変数が占有しているバイト数を返します。 `sizeof` 演算子への引数は、[アンマネージド型](../builtin-types/unmanaged-types.md)の名前、またはアンマネージド型に[制限される](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)型パラメーターである必要があります。

`sizeof` 演算子には [unsafe](../keywords/unsafe.md) コンテキストが必要です。 ただし、次の表に示す式は、コンパイル時に対応する定数値に評価され、unsafe コンテキストを必要としません。

|正規表現|定数値|
|---------|---------------|
|`sizeof(sbyte)`|1|
|`sizeof(byte)`|1|
|`sizeof(short)`|2|
|`sizeof(ushort)`|2|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|2|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16|
|`sizeof(bool)`|1|

`sizeof` 演算子のオペランドが[列挙](../builtin-types/enum.md)型の名前である場合も、unsafe コンテキストを使用する必要はありません。

`sizeof` 演算子の使用例を次に示します。

[!code-csharp[sizeof examples](snippets/shared/SizeOfOperator.cs)]

`sizeof` 演算子は、マネージド メモリ内の共通言語ランタイムによって割り当てられるバイト数を返します。 [構造体](../builtin-types/struct.md)型の場合、前の例のように、その値に埋め込みが含まれます。 `sizeof` 演算子の結果は、*アンマネージド* メモリの型のサイズを返す <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> メソッドの結果とは異なる場合があります。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の [sizeof 演算子](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator)に関するセクションを参照してください。

## <a name="see-also"></a>参照

- [C# リファレンス](../index.md)
- [C# の演算子と式](index.md)
- [ポインターに関連する演算子](pointer-related-operators.md)
- [ポインター型](../unsafe-code.md#pointer-types)
- [メモリおよびスパンに関連する型](../../../standard/memory-and-spans/index.md)
- [.NET のジェネリック](../../../standard/generics/index.md)
