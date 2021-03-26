---
description: C# の組み込みの数値型間での暗黙的および明示的な変換について
title: 組み込みの数値変換 - C# リファレンス
ms.date: 03/17/2021
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5ff0289f5365a7d3d334dd0130b3b0efcdf34c60
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759691"
---
# <a name="built-in-numeric-conversions-c-reference"></a><span data-ttu-id="26865-103">組み込みの数値変換 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="26865-103">Built-in numeric conversions (C# reference)</span></span>

<span data-ttu-id="26865-104">C# では、[整数](integral-numeric-types.md)数値型と[浮動小数点](floating-point-numeric-types.md)数値型のセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="26865-104">C# provides a set of [integral](integral-numeric-types.md) and [floating-point](floating-point-numeric-types.md) numeric types.</span></span> <span data-ttu-id="26865-105">任意の 2 つの数値型の間で、暗黙的または明示的のいずれかの変換が存在します。</span><span class="sxs-lookup"><span data-stu-id="26865-105">There exists a conversion between any two numeric types, either implicit or explicit.</span></span> <span data-ttu-id="26865-106">明示的な変換を実行するには、[キャスト式](../operators/type-testing-and-cast.md#cast-expression)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26865-106">You must use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span>

## <a name="implicit-numeric-conversions"></a><span data-ttu-id="26865-107">暗黙の数値変換</span><span class="sxs-lookup"><span data-stu-id="26865-107">Implicit numeric conversions</span></span>

<span data-ttu-id="26865-108">組み込みの数値型間の定義済みの暗黙的な変換を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="26865-108">The following table shows the predefined implicit conversions between the built-in numeric types:</span></span>

|<span data-ttu-id="26865-109">From</span><span class="sxs-lookup"><span data-stu-id="26865-109">From</span></span>|<span data-ttu-id="26865-110">終了</span><span class="sxs-lookup"><span data-stu-id="26865-110">To</span></span>|
|----------|--------|
|[<span data-ttu-id="26865-111">sbyte</span><span class="sxs-lookup"><span data-stu-id="26865-111">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-112">`short`、`int`、`long`、`float`、`double`、`decimal`、または `nint`</span><span class="sxs-lookup"><span data-stu-id="26865-112">`short`, `int`, `long`, `float`, `double`, `decimal`, or `nint`</span></span>|
|[<span data-ttu-id="26865-113">byte</span><span class="sxs-lookup"><span data-stu-id="26865-113">byte</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-114">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、`decimal`、`nint`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-114">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `nint`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-115">short</span><span class="sxs-lookup"><span data-stu-id="26865-115">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-116">`int`、`long`、`float`、`double`、または `decimal`、または `nint`</span><span class="sxs-lookup"><span data-stu-id="26865-116">`int`, `long`, `float`, `double`, or `decimal`, or `nint`</span></span>|
|[<span data-ttu-id="26865-117">ushort</span><span class="sxs-lookup"><span data-stu-id="26865-117">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-118">`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`、`nint`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-118">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`, `nint`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-119">int</span><span class="sxs-lookup"><span data-stu-id="26865-119">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-120">`long`、`float`、`double`、または `decimal`、`nint`</span><span class="sxs-lookup"><span data-stu-id="26865-120">`long`, `float`, `double`, or `decimal`, `nint`</span></span>|
|[<span data-ttu-id="26865-121">uint</span><span class="sxs-lookup"><span data-stu-id="26865-121">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-122">`long`、`ulong`、`float`、`double`、または `decimal`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-122">`long`, `ulong`, `float`, `double`, or `decimal`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-123">long</span><span class="sxs-lookup"><span data-stu-id="26865-123">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-124">`float`、 `double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="26865-124">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="26865-125">ulong</span><span class="sxs-lookup"><span data-stu-id="26865-125">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-126">`float`、 `double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="26865-126">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="26865-127">float</span><span class="sxs-lookup"><span data-stu-id="26865-127">float</span></span>](floating-point-numeric-types.md)|`double`|
|[<span data-ttu-id="26865-128">nint</span><span class="sxs-lookup"><span data-stu-id="26865-128">nint</span></span>](nint-nuint.md)|<span data-ttu-id="26865-129">`long`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="26865-129">`long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="26865-130">nuint</span><span class="sxs-lookup"><span data-stu-id="26865-130">nuint</span></span>](nint-nuint.md)|<span data-ttu-id="26865-131">`ulong`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="26865-131">`ulong`, `float`, `double`, or `decimal`</span></span>|

> [!NOTE]
> <span data-ttu-id="26865-132">`int`、`uint`、`long`、`ulong`、`nint`、または `nuint` から `float` へ、および `long`、`ulong`、`nint`、または `nuint` から `double` への暗黙的な変換では、精度が失われる可能性がありますが、桁違いに大きな損失が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="26865-132">The implicit conversions from `int`, `uint`, `long`, `ulong`, `nint`, or `nuint` to `float` and from `long`, `ulong`, `nint`, or `nuint` to `double` may cause a loss of precision, but never a loss of an order of magnitude.</span></span> <span data-ttu-id="26865-133">その他の暗黙的な数値変換では、情報が失われることはありません。</span><span class="sxs-lookup"><span data-stu-id="26865-133">The other implicit numeric conversions never lose any information.</span></span>

<span data-ttu-id="26865-134">次の点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="26865-134">Also note that</span></span>

- <span data-ttu-id="26865-135">[整数数値型](integral-numeric-types.md)はすべて、あらゆる[浮動小数点数値型](floating-point-numeric-types.md)に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="26865-135">Any [integral numeric type](integral-numeric-types.md) is implicitly convertible to any [floating-point numeric type](floating-point-numeric-types.md).</span></span>

- <span data-ttu-id="26865-136">`byte` および `sbyte` 型への暗黙的な変換はありません。</span><span class="sxs-lookup"><span data-stu-id="26865-136">There are no implicit conversions to the `byte` and `sbyte` types.</span></span> <span data-ttu-id="26865-137">`double` および `decimal` 型からの暗黙的な変換はありません。</span><span class="sxs-lookup"><span data-stu-id="26865-137">There are no implicit conversions from the `double` and `decimal` types.</span></span>

- <span data-ttu-id="26865-138">`decimal` 型と `float` 型または `double` 型の間に暗黙的な変換はありません。</span><span class="sxs-lookup"><span data-stu-id="26865-138">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>

- <span data-ttu-id="26865-139">型 `int` の定数式の値 (整数リテラルで表される値など) は、それが変換先の型の範囲内にある場合、`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong`、`nint`、または `nuint` に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="26865-139">A value of a constant expression of type `int` (for example, a value represented by an integer literal) can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, `nint`, or `nuint`, if it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  <span data-ttu-id="26865-140">前の例で示したように、定数値が変換先の型の範囲内にない場合、コンパイラ エラー [CS0031](../../misc/cs0031.md) が発生します。</span><span class="sxs-lookup"><span data-stu-id="26865-140">As the preceding example shows, if the constant value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

## <a name="explicit-numeric-conversions"></a><span data-ttu-id="26865-141">明示的な数値変換</span><span class="sxs-lookup"><span data-stu-id="26865-141">Explicit numeric conversions</span></span>

<span data-ttu-id="26865-142">次の表では、[暗黙的な変換](#implicit-numeric-conversions)がない組み込みの数値型間で事前定義されている明示的変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="26865-142">The following table shows the predefined explicit conversions between the built-in numeric types for which there is no [implicit conversion](#implicit-numeric-conversions):</span></span>

|<span data-ttu-id="26865-143">From</span><span class="sxs-lookup"><span data-stu-id="26865-143">From</span></span>|<span data-ttu-id="26865-144">終了</span><span class="sxs-lookup"><span data-stu-id="26865-144">To</span></span>|
|----------|--------|
|[<span data-ttu-id="26865-145">sbyte</span><span class="sxs-lookup"><span data-stu-id="26865-145">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-146">`byte`、`ushort`、`uint`、または `ulong`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-146">`byte`, `ushort`, `uint`, or `ulong`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-147">byte</span><span class="sxs-lookup"><span data-stu-id="26865-147">byte</span></span>](integral-numeric-types.md)|`sbyte`|
|[<span data-ttu-id="26865-148">short</span><span class="sxs-lookup"><span data-stu-id="26865-148">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-149">`sbyte`、`byte`、`ushort`、`uint`、`ulong`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-149">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-150">ushort</span><span class="sxs-lookup"><span data-stu-id="26865-150">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-151">`sbyte`、 `byte`、または `short`</span><span class="sxs-lookup"><span data-stu-id="26865-151">`sbyte`, `byte`, or `short`</span></span>|
|[<span data-ttu-id="26865-152">int</span><span class="sxs-lookup"><span data-stu-id="26865-152">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-153">`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-153">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-154">uint</span><span class="sxs-lookup"><span data-stu-id="26865-154">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-155">`sbyte`、`byte`、`short`、`ushort`、または `int`</span><span class="sxs-lookup"><span data-stu-id="26865-155">`sbyte`, `byte`, `short`, `ushort`, or `int`</span></span>|
|[<span data-ttu-id="26865-156">long</span><span class="sxs-lookup"><span data-stu-id="26865-156">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-157">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`ulong`、`nint`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-157">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, `nint`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-158">ulong</span><span class="sxs-lookup"><span data-stu-id="26865-158">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="26865-159">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`nint`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-159">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `nint`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-160">float</span><span class="sxs-lookup"><span data-stu-id="26865-160">float</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="26865-161">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`decimal`、`nint`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-161">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `decimal`, `nint`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-162">double</span><span class="sxs-lookup"><span data-stu-id="26865-162">double</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="26865-163">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`decimal`、`nint`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-163">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `decimal`, `nint`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-164">decimal</span><span class="sxs-lookup"><span data-stu-id="26865-164">decimal</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="26865-165">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、`nint`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-165">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `nint`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-166">nint</span><span class="sxs-lookup"><span data-stu-id="26865-166">nint</span></span>](nint-nuint.md)|<span data-ttu-id="26865-167">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`ulong`、または `nuint`</span><span class="sxs-lookup"><span data-stu-id="26865-167">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `nuint`</span></span>|
|[<span data-ttu-id="26865-168">nuint</span><span class="sxs-lookup"><span data-stu-id="26865-168">nuint</span></span>](nint-nuint.md)|<span data-ttu-id="26865-169">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、または `nint`</span><span class="sxs-lookup"><span data-stu-id="26865-169">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `nint`</span></span>|

> [!NOTE]
> <span data-ttu-id="26865-170">明示的な数値変換によって、データが失われたり、例外がスローされたりすることがあります (通常は <xref:System.OverflowException>)。</span><span class="sxs-lookup"><span data-stu-id="26865-170">An explicit numeric conversion might result in data loss or throw an exception, typically an <xref:System.OverflowException>.</span></span>

<span data-ttu-id="26865-171">次の点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="26865-171">Also note that</span></span>

- <span data-ttu-id="26865-172">ある整数型の値を別の整数型に変換するとき、その結果は、オーバーフロー [チェック コンテキスト](../keywords/checked-and-unchecked.md)によって変わります。</span><span class="sxs-lookup"><span data-stu-id="26865-172">When you convert a value of an integral type to another integral type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="26865-173">checked コンテキストでは、変換元の値が変換先の型の範囲内にあるとき、変換に成功します。</span><span class="sxs-lookup"><span data-stu-id="26865-173">In a checked context, the conversion succeeds if the source value is within the range of the destination type.</span></span> <span data-ttu-id="26865-174">それ以外の場合は、<xref:System.OverflowException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="26865-174">Otherwise, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="26865-175">unchecked コンテキストでは、変換は常に成功し、次のように続行されます。</span><span class="sxs-lookup"><span data-stu-id="26865-175">In an unchecked context, the conversion always succeeds, and proceeds as follows:</span></span>

  - <span data-ttu-id="26865-176">変換元の型が変換先の型より大きい場合、変換元の値はその "余分な" 最上位ビットを破棄することで切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="26865-176">If the source type is larger than the destination type, then the source value is truncated by discarding its "extra" most significant bits.</span></span> <span data-ttu-id="26865-177">結果は変換先の型の値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="26865-177">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="26865-178">変換元の型が変換先の型より小さい場合、変換元の値は変換先の型と同じサイズになるように、符号拡張またはゼロ拡張されます。</span><span class="sxs-lookup"><span data-stu-id="26865-178">If the source type is smaller than the destination type, then the source value is either sign-extended or zero-extended so that it's of the same size as the destination type.</span></span> <span data-ttu-id="26865-179">変換元の型に符号が付いている場合は符号拡張が利用され、符号が付いていない場合はゼロ拡張が利用されます。</span><span class="sxs-lookup"><span data-stu-id="26865-179">Sign-extension is used if the source type is signed; zero-extension is used if the source type is unsigned.</span></span> <span data-ttu-id="26865-180">結果は変換先の型の値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="26865-180">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="26865-181">変換元の型が変換先の型と同じサイズの場合、変換元の値は変換先の型の値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="26865-181">If the source type is the same size as the destination type, then the source value is treated as a value of the destination type.</span></span>

- <span data-ttu-id="26865-182">`decimal` 値を整数型に変換するとき、この値は 0 方向に最も近い整数値に丸められます。</span><span class="sxs-lookup"><span data-stu-id="26865-182">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="26865-183">結果的に生成される整数値が変換先の型の範囲外になった場合、<xref:System.OverflowException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="26865-183">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="26865-184">`double` または `float` 値を整数型に変換するとき、この値は 0 方向に最も近い整数値に丸められます。</span><span class="sxs-lookup"><span data-stu-id="26865-184">When you convert a `double` or `float` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="26865-185">結果的に生成される整数値が変換先の型の範囲外になる場合、結果はオーバーフロー [チェック コンテキスト](../keywords/checked-and-unchecked.md)によって変わります。</span><span class="sxs-lookup"><span data-stu-id="26865-185">If the resulting integral value is outside the range of the destination type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="26865-186">チェック済みコンテキストの場合、<xref:System.OverflowException> がスローされます。未チェック コンテキストの場合、結果は変換先の型の不特定な値になります。</span><span class="sxs-lookup"><span data-stu-id="26865-186">In a checked context, an <xref:System.OverflowException> is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>

- <span data-ttu-id="26865-187">`double` を `float` に変換すると、`double` 値は最も近い `float` 値に丸められます。</span><span class="sxs-lookup"><span data-stu-id="26865-187">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="26865-188">`double` 値が小さすぎるか、大きすぎて `float` 型に合わない場合、結果は 0 か無限になります。</span><span class="sxs-lookup"><span data-stu-id="26865-188">If the `double` value is too small or too large to fit into the `float` type, the result is zero or infinity.</span></span>

- <span data-ttu-id="26865-189">`float` または `double` を `decimal` に変換するとき、変換元の値は `decimal` 表現に変換され、必要であれば、28 番目の小数位の後に最も近い数字に丸められます。</span><span class="sxs-lookup"><span data-stu-id="26865-189">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="26865-190">変換元の値によっては、結果は次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="26865-190">Depending on the value of the source value, one of the following results may occur:</span></span>

  - <span data-ttu-id="26865-191">変換元の値が小さすぎて `decimal` として表現できない場合、結果は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="26865-191">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>

  - <span data-ttu-id="26865-192">変換元の値が NaN (Not a Number/数字ではない) か、無限か、大きすぎて `decimal` として表現できない場合、<xref:System.OverflowException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="26865-192">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="26865-193">`decimal` を `float` または `double` に変換すると、変換元の値はそれぞれ最も近い `float` または `double` 値に丸められます。</span><span class="sxs-lookup"><span data-stu-id="26865-193">When you convert `decimal` to `float` or `double`, the source value is rounded to the nearest `float` or `double` value, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="26865-194">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="26865-194">C# language specification</span></span>

<span data-ttu-id="26865-195">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="26865-195">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="26865-196">暗黙の数値変換</span><span class="sxs-lookup"><span data-stu-id="26865-196">Implicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [<span data-ttu-id="26865-197">明示的な数値変換</span><span class="sxs-lookup"><span data-stu-id="26865-197">Explicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a><span data-ttu-id="26865-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="26865-198">See also</span></span>

- [<span data-ttu-id="26865-199">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="26865-199">C# reference</span></span>](../index.md)
- [<span data-ttu-id="26865-200">キャストと型変換</span><span class="sxs-lookup"><span data-stu-id="26865-200">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
