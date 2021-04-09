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
# <a name="void-c-reference"></a><span data-ttu-id="25f9e-103">void (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="25f9e-103">void (C# reference)</span></span>

<span data-ttu-id="25f9e-104">[メソッド](../../programming-guide/classes-and-structs/methods.md) (または [ローカル関数](../../programming-guide/classes-and-structs/local-functions.md)) が値を返さないことを指定するには、メソッドの戻り値の型として `void` を使用します。</span><span class="sxs-lookup"><span data-stu-id="25f9e-104">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/shared/VoidType.cs#VoidExample)]

<span data-ttu-id="25f9e-105">さらに、不明な型へのポインターを宣言するための参照型として `void` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="25f9e-105">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="25f9e-106">詳しくは、「[ポインター型](../unsafe-code.md#pointer-types)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="25f9e-106">For more information, see [Pointer types](../unsafe-code.md#pointer-types).</span></span>

<span data-ttu-id="25f9e-107">変数の型として `void` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="25f9e-107">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="25f9e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="25f9e-108">See also</span></span>

- [<span data-ttu-id="25f9e-109">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="25f9e-109">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
