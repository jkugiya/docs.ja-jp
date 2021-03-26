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
# <a name="built-in-types-c-reference"></a><span data-ttu-id="5dba9-103">組み込み型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5dba9-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="5dba9-104">C# の組み込みの[値](value-types.md)型を次の表に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5dba9-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="5dba9-105">C# 型キーワード</span><span class="sxs-lookup"><span data-stu-id="5dba9-105">C# type keyword</span></span>|<span data-ttu-id="5dba9-106">.NET 型</span><span class="sxs-lookup"><span data-stu-id="5dba9-106">.NET type</span></span>|
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

<span data-ttu-id="5dba9-107">C# の組み込みの[参照](../keywords/reference-types.md)型を次の表に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5dba9-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="5dba9-108">C# 型キーワード</span><span class="sxs-lookup"><span data-stu-id="5dba9-108">C# type keyword</span></span>|<span data-ttu-id="5dba9-109">.NET 型</span><span class="sxs-lookup"><span data-stu-id="5dba9-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|
|[`dynamic`](reference-types.md#the-dynamic-type)|<xref:System.Object?displayProperty=nameWithType>|

<span data-ttu-id="5dba9-110">上の表の左の列にある各 C# 型キーワード ([nint と nuint](nint-nuint.md) を除く) は、対応する .NET 型の別名です。</span><span class="sxs-lookup"><span data-stu-id="5dba9-110">In the preceding tables, each C# type keyword from the left column (except [nint and nuint](nint-nuint.md)) is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="5dba9-111">これらは交換可能です。</span><span class="sxs-lookup"><span data-stu-id="5dba9-111">They are interchangeable.</span></span> <span data-ttu-id="5dba9-112">たとえば、次の宣言では、同じ型の変数が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="5dba9-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="5dba9-113">最初のテーブルの最後の 2 行の `nint` 型と `nuint` 型は、ネイティブサイズの整数です。</span><span class="sxs-lookup"><span data-stu-id="5dba9-113">The `nint` and `nuint` types in the last two rows of the first table are native-sized integers.</span></span> <span data-ttu-id="5dba9-114">これらは、指定された .NET 型によって内部で表現されますが、いずれの場合もキーワードと .NET 型は交換できません。</span><span class="sxs-lookup"><span data-stu-id="5dba9-114">They are represented internally by the indicated .NET types, but in each case the keyword and the .NET type are not interchangeable.</span></span> <span data-ttu-id="5dba9-115">コンパイラによって、`nint` と `nuint` に対して、整数型としての演算と変換が提供されます。ポインター型 `System.IntPtr` と `System.UIntPtr` に対しては提供されません。</span><span class="sxs-lookup"><span data-stu-id="5dba9-115">The compiler provides operations and conversions for `nint` and `nuint` as integer types that it doesn't provide for the pointer types `System.IntPtr` and `System.UIntPtr`.</span></span> <span data-ttu-id="5dba9-116">詳細については、[`nint` 型と `nuint` 型](nint-nuint.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dba9-116">For more information, see [`nint` and `nuint` types](nint-nuint.md).</span></span>

<span data-ttu-id="5dba9-117">[`void`](void.md) キーワードで、値がないことが表されます。</span><span class="sxs-lookup"><span data-stu-id="5dba9-117">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="5dba9-118">値を返さないメソッドの戻り値の型として使用します。</span><span class="sxs-lookup"><span data-stu-id="5dba9-118">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="5dba9-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dba9-119">See also</span></span>

- [<span data-ttu-id="5dba9-120">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="5dba9-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5dba9-121">C# 型の既定値</span><span class="sxs-lookup"><span data-stu-id="5dba9-121">Default values of C# types</span></span>](default-values.md)
