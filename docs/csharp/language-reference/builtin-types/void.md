---
description: C# での void キーワードについて
title: void - C# リファレンス
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 4a6afbd88f9cabc6818cdc8ba34f14ae18b195a4
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497386"
---
# <a name="void-c-reference"></a>void (C# リファレンス)

[メソッド](../../programming-guide/classes-and-structs/methods.md) (または [ローカル関数](../../programming-guide/classes-and-structs/local-functions.md)) が値を返さないことを指定するには、メソッドの戻り値の型として `void` を使用します。

[!code-csharp[void method](snippets/shared/VoidType.cs#VoidExample)]

さらに、不明な型へのポインターを宣言するための参照型として `void` を使用できます。 詳しくは、「[ポインター型](../unsafe-code.md#pointer-types)」をご覧ください。

変数の型として `void` を使用することはできません。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
