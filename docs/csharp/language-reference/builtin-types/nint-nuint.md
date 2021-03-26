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
# <a name="nint-and-nuint-types-c-reference"></a><span data-ttu-id="17072-103">`nint` 型と `nuint` 型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="17072-103">`nint` and `nuint` types (C# reference)</span></span>

<span data-ttu-id="17072-104">C# 9.0 以降、`nint` キーワードと `nuint` キーワードを使用して、*ネイティブサイズの整数* を定義できます。</span><span class="sxs-lookup"><span data-stu-id="17072-104">Starting in C# 9.0, you can use the `nint` and `nuint` keywords to define *native-sized integers*.</span></span> <span data-ttu-id="17072-105">これらは、32 ビット プロセスで実行される場合は 32 ビット整数、64 ビット プロセスで実行される場合は 64 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="17072-105">These are 32-bit integers when running in a 32-bit process, or 64-bit integers when running in a 64-bit process.</span></span> <span data-ttu-id="17072-106">これらは、相互運用シナリオ、低レベル ライブラリ、および整数演算が多用されるシナリオでパフォーマンスを最適化するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="17072-106">They can be used for interop scenarios, low-level libraries, and to optimize performance in scenarios where integer math is used extensively.</span></span>

<span data-ttu-id="17072-107">ネイティブサイズの整数型は、.NET 型 <xref:System.IntPtr?displayProperty=nameWithType> および <xref:System.UIntPtr?displayProperty=nameWithType> として内部で表現されます。</span><span class="sxs-lookup"><span data-stu-id="17072-107">The native-sized integer types are represented internally as the .NET types <xref:System.IntPtr?displayProperty=nameWithType> and <xref:System.UIntPtr?displayProperty=nameWithType>.</span></span> <span data-ttu-id="17072-108">他の数値型と異なり、キーワードは単純に型の別名ではありません。</span><span class="sxs-lookup"><span data-stu-id="17072-108">Unlike other numeric types, the keywords are not simply aliases for the types.</span></span> <span data-ttu-id="17072-109">次のステートメントは同等ではありません。</span><span class="sxs-lookup"><span data-stu-id="17072-109">The following statements are not equivalent:</span></span>

```csharp
nint a = 1;
System.IntPtr a = 1;
```

<span data-ttu-id="17072-110">コンパイラでは、`nint` と `nuint` に対して、整数型に適した演算と変換が提供されます。</span><span class="sxs-lookup"><span data-stu-id="17072-110">The compiler provides operations and conversions for `nint` and `nuint` that are appropriate for integer types.</span></span>

## <a name="run-time-native-integer-size"></a><span data-ttu-id="17072-111">実行時ネイティブ整数サイズ</span><span class="sxs-lookup"><span data-stu-id="17072-111">Run-time native integer size</span></span>

<span data-ttu-id="17072-112">実行時にネイティブサイズの整数のサイズを取得するには、`sizeof()` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="17072-112">To get the size of a native-sized integer at run time, you can use `sizeof()`.</span></span> <span data-ttu-id="17072-113">ただし、コードを安全でないコンテキストでコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="17072-113">However, the code must be compiled in an unsafe context.</span></span> <span data-ttu-id="17072-114">例:</span><span class="sxs-lookup"><span data-stu-id="17072-114">For example:</span></span>

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="SizeOf":::

<span data-ttu-id="17072-115">また、静的な <xref:System.IntPtr.Size?displayProperty=nameWithType> および <xref:System.UIntPtr.Size?displayProperty=nameWithType> プロパティから同等の値を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="17072-115">You can also get the equivalent value from the static <xref:System.IntPtr.Size?displayProperty=nameWithType> and <xref:System.UIntPtr.Size?displayProperty=nameWithType> properties.</span></span>

## <a name="minvalue-and-maxvalue"></a><span data-ttu-id="17072-116">MinValue と MaxValue</span><span class="sxs-lookup"><span data-stu-id="17072-116">MinValue and MaxValue</span></span>

<span data-ttu-id="17072-117">実行時にネイティブサイズの整数の最小値と最大値を取得するには、次の例のように、`nint` キーワードと `nuint` キーワードで、`MinValue` と `MaxValue` を静的プロパティとして使用します。</span><span class="sxs-lookup"><span data-stu-id="17072-117">To get the minimum and maximum values of native-sized integers at run time, use `MinValue` and `MaxValue` as static properties with the `nint` and `nuint` keywords, as in the following example:</span></span>

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="MinMax":::

## <a name="constants"></a><span data-ttu-id="17072-118">定数</span><span class="sxs-lookup"><span data-stu-id="17072-118">Constants</span></span>

<span data-ttu-id="17072-119">次の範囲の定数値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="17072-119">You can use constant values in the following ranges:</span></span>

* <span data-ttu-id="17072-120">`nint` の場合: <xref:System.Int32.MinValue?displayProperty=nameWithType> から <xref:System.Int32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="17072-120">For `nint`: <xref:System.Int32.MinValue?displayProperty=nameWithType> to <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="17072-121">`nuint` の場合: <xref:System.UInt32.MinValue?displayProperty=nameWithType> から <xref:System.UInt32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="17072-121">For `nuint`: <xref:System.UInt32.MinValue?displayProperty=nameWithType> to <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

## <a name="conversions"></a><span data-ttu-id="17072-122">コンバージョン</span><span class="sxs-lookup"><span data-stu-id="17072-122">Conversions</span></span>

<span data-ttu-id="17072-123">コンパイラによって、他の数値型への暗黙的と明示的な変換が提供されます。</span><span class="sxs-lookup"><span data-stu-id="17072-123">The compiler provides implicit and explicit conversions to other numeric types.</span></span> <span data-ttu-id="17072-124">詳細については、「[組み込みの数値変換](numeric-conversions.md)」に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="17072-124">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="literals"></a><span data-ttu-id="17072-125">リテラル</span><span class="sxs-lookup"><span data-stu-id="17072-125">Literals</span></span>

<span data-ttu-id="17072-126">ネイティブサイズの整数リテラルには、直接の構文がありません。</span><span class="sxs-lookup"><span data-stu-id="17072-126">There's no direct syntax for native-sized integer literals.</span></span> <span data-ttu-id="17072-127">`long` を示す `L` など、リテラルがネイティブサイズの整数であることを示すサフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="17072-127">There's no suffix to indicate that a literal is a native-sized integer, such as `L` to indicate a `long`.</span></span> <span data-ttu-id="17072-128">代わりに、他の整数値の暗黙的または明示的なキャストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="17072-128">You can use implicit or explicit casts of other integer values instead.</span></span> <span data-ttu-id="17072-129">例:</span><span class="sxs-lookup"><span data-stu-id="17072-129">For example:</span></span>

```csharp
nint a = 42
nint a = (nint)42;
```

## <a name="unsupported-intptruintptr-members"></a><span data-ttu-id="17072-130">サポートされていない IntPtr または UIntPtr メンバー</span><span class="sxs-lookup"><span data-stu-id="17072-130">Unsupported IntPtr/UIntPtr members</span></span>

<span data-ttu-id="17072-131"><xref:System.IntPtr> および <xref:System.UIntPtr> の次のメンバーは、`nint` 型および `nuint` 型ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="17072-131">The following members of <xref:System.IntPtr> and <xref:System.UIntPtr> aren't supported for `nint` and `nuint` types:</span></span>

* <span data-ttu-id="17072-132">パラメーター化されたコンストラクター</span><span class="sxs-lookup"><span data-stu-id="17072-132">Parameterized constructors</span></span>
* <xref:System.IntPtr.Add(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.CompareTo%2A>
* <span data-ttu-id="17072-133"><xref:System.IntPtr.Size> - 代わりに [sizeOf ()](#run-time-native-integer-size) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="17072-133"><xref:System.IntPtr.Size> - Use [sizeOf()](#run-time-native-integer-size) instead.</span></span> <span data-ttu-id="17072-134">`nint.Size` はサポートされていませんが、`IntPtr.Size` を使用して同等の値を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="17072-134">Although `nint.Size` isn't supported, you can use `IntPtr.Size` to get an equivalent value.</span></span>
* <xref:System.IntPtr.Subtract(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.ToInt32%2A>
* <xref:System.IntPtr.ToInt64%2A>
* <xref:System.IntPtr.ToPointer%2A>
* <span data-ttu-id="17072-135"><xref:System.IntPtr.Zero> - 代わりに 0 を使用してください。</span><span class="sxs-lookup"><span data-stu-id="17072-135"><xref:System.IntPtr.Zero> - Use 0 instead.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="17072-136">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="17072-136">C# language specification</span></span>

<span data-ttu-id="17072-137">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)と、C# 9.0 機能提案メモの「[ネイティブサイズの整数](~/_csharplang/proposals/csharp-9.0/native-integers.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="17072-137">For more information, see the [C# language specification](~/_csharplang/spec/introduction.md) and the [Native-sized integers](~/_csharplang/proposals/csharp-9.0/native-integers.md) section of the C# 9.0 feature proposal notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="17072-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="17072-138">See also</span></span>

- [<span data-ttu-id="17072-139">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="17072-139">C# reference</span></span>](../index.md)
- [<span data-ttu-id="17072-140">値型</span><span class="sxs-lookup"><span data-stu-id="17072-140">Value types</span></span>](value-types.md)
- [<span data-ttu-id="17072-141">整数数値型</span><span class="sxs-lookup"><span data-stu-id="17072-141">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="17072-142">組み込みの数値変換</span><span class="sxs-lookup"><span data-stu-id="17072-142">Built-in numeric conversions</span></span>](numeric-conversions.md)
