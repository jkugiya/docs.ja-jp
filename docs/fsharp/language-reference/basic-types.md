---
title: 基本型
description: 'F # 言語で使用される基本的な基本型について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 2bfc9ba9370cb8ba1fcc1d42369c2551cbb57623
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456914"
---
# <a name="basic-types"></a><span data-ttu-id="75b57-103">基本型</span><span class="sxs-lookup"><span data-stu-id="75b57-103">Basic types</span></span>

<span data-ttu-id="75b57-104">このトピックでは、F # 言語で定義されている基本型の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="75b57-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="75b57-105">これらの型は F # で最も基本的なものであり、ほぼすべての F # プログラムの基礎となります。</span><span class="sxs-lookup"><span data-stu-id="75b57-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="75b57-106">これらは、.NET プリミティブ型のスーパーセットです。</span><span class="sxs-lookup"><span data-stu-id="75b57-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="75b57-107">Type</span><span class="sxs-lookup"><span data-stu-id="75b57-107">Type</span></span>|<span data-ttu-id="75b57-108">.NET の種類</span><span class="sxs-lookup"><span data-stu-id="75b57-108">.NET type</span></span>|<span data-ttu-id="75b57-109">[説明]</span><span class="sxs-lookup"><span data-stu-id="75b57-109">Description</span></span>|<span data-ttu-id="75b57-110">例</span><span class="sxs-lookup"><span data-stu-id="75b57-110">Example</span></span>|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="75b57-111">設定可能な値は `true` および `false` です。</span><span class="sxs-lookup"><span data-stu-id="75b57-111">Possible values are `true` and `false`.</span></span>|`true`/`false`|
|`byte`|<xref:System.Byte>|<span data-ttu-id="75b57-112">0 ~ 255 の値。</span><span class="sxs-lookup"><span data-stu-id="75b57-112">Values from 0 to 255.</span></span>|`1uy`|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="75b57-113">-128 から127までの値。</span><span class="sxs-lookup"><span data-stu-id="75b57-113">Values from -128 to 127.</span></span>|`1y`|
|`int16`|<xref:System.Int16>|<span data-ttu-id="75b57-114">-32768 から32767までの値。</span><span class="sxs-lookup"><span data-stu-id="75b57-114">Values from -32768 to 32767.</span></span>|`1s`|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="75b57-115">0 ~ 65535 の値。</span><span class="sxs-lookup"><span data-stu-id="75b57-115">Values from 0 to 65535.</span></span>|`1us`|
|`int`|<xref:System.Int32>|<span data-ttu-id="75b57-116">-2147483648 から2147483647までの値。</span><span class="sxs-lookup"><span data-stu-id="75b57-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|`1`|
|`uint`|<xref:System.UInt32>|<span data-ttu-id="75b57-117">0 ~ 4294967295 の値。</span><span class="sxs-lookup"><span data-stu-id="75b57-117">Values from 0 to 4,294,967,295.</span></span>|`1u`|
|`int64`|<xref:System.Int64>|<span data-ttu-id="75b57-118">-9223372036854775808 ~ 9223372036854775807 の値。</span><span class="sxs-lookup"><span data-stu-id="75b57-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|`1L`|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="75b57-119">0 ~ 18446744073709551615 の値。</span><span class="sxs-lookup"><span data-stu-id="75b57-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|`1UL`|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="75b57-120">符号付き整数としてのネイティブポインター。</span><span class="sxs-lookup"><span data-stu-id="75b57-120">A native pointer as a signed integer.</span></span>|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="75b57-121">符号なし整数としてのネイティブポインター。</span><span class="sxs-lookup"><span data-stu-id="75b57-121">A native pointer as an unsigned integer.</span></span>|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="75b57-122">有効桁数が28以上の浮動小数点データ型。</span><span class="sxs-lookup"><span data-stu-id="75b57-122">A floating point data type that has at least 28 significant digits.</span></span>|`1.0`|
|<span data-ttu-id="75b57-123">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="75b57-123">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="75b57-124">64ビットの浮動小数点型。</span><span class="sxs-lookup"><span data-stu-id="75b57-124">A 64-bit floating point type.</span></span>|`1.0`|
|<span data-ttu-id="75b57-125">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="75b57-125">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="75b57-126">32ビットの浮動小数点型。</span><span class="sxs-lookup"><span data-stu-id="75b57-126">A 32-bit floating point type.</span></span>|`1.0f`|
|`char`|<xref:System.Char>|<span data-ttu-id="75b57-127">Unicode 文字の値。</span><span class="sxs-lookup"><span data-stu-id="75b57-127">Unicode character values.</span></span>|`'c'`|
|`string`|<xref:System.String>|<span data-ttu-id="75b57-128">Unicode テキスト。</span><span class="sxs-lookup"><span data-stu-id="75b57-128">Unicode text.</span></span>|`"str"`|
|`unit`|<span data-ttu-id="75b57-129">適用外</span><span class="sxs-lookup"><span data-stu-id="75b57-129">not applicable</span></span>|<span data-ttu-id="75b57-130">実際の値が存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="75b57-130">Indicates the absence of an actual value.</span></span> <span data-ttu-id="75b57-131">型には、示されている仮値が1つだけあり `()` ます。</span><span class="sxs-lookup"><span data-stu-id="75b57-131">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="75b57-132">単位値は、 `()` 値が必要であるものの、実際の値を使用できない、または意味を持つプレースホルダーとしてよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="75b57-132">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|`()`|

> [!NOTE]
> <span data-ttu-id="75b57-133">型を使用して、整数値が64ビット整数型に対して大きすぎる計算を実行でき `bigint` ます。</span><span class="sxs-lookup"><span data-stu-id="75b57-133">You can perform computations with integers too big for the 64-bit integer type by using the `bigint` type.</span></span> <span data-ttu-id="75b57-134">`bigint` は基本的な型とは見なされません。これは、の省略形です `System.Numerics.BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="75b57-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="75b57-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="75b57-135">See also</span></span>

- [<span data-ttu-id="75b57-136">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="75b57-136">F# Language Reference</span></span>](index.md)
