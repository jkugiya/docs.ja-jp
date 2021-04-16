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
# <a name="basic-types"></a><span data-ttu-id="4ed0b-103">基本型</span><span class="sxs-lookup"><span data-stu-id="4ed0b-103">Basic types</span></span>

<span data-ttu-id="4ed0b-104">このトピックでは、F# 言語で定義されている基本型の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="4ed0b-105">これらの型は F# で最も基本的なものであり、ほぼすべての F# プログラムの基礎となります。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="4ed0b-106">これらは、.NET プリミティブ型のスーパーセットです。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="4ed0b-107">Type</span><span class="sxs-lookup"><span data-stu-id="4ed0b-107">Type</span></span>|<span data-ttu-id="4ed0b-108">.NET の種類</span><span class="sxs-lookup"><span data-stu-id="4ed0b-108">.NET type</span></span>|<span data-ttu-id="4ed0b-109">説明</span><span class="sxs-lookup"><span data-stu-id="4ed0b-109">Description</span></span>|<span data-ttu-id="4ed0b-110">例</span><span class="sxs-lookup"><span data-stu-id="4ed0b-110">Example</span></span>|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="4ed0b-111">設定可能な値は `true` および `false` です。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-111">Possible values are `true` and `false`.</span></span>|`true`/`false`|
|`byte`|<xref:System.Byte>|<span data-ttu-id="4ed0b-112">0 から 255 までの値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-112">Values from 0 to 255.</span></span>|`1uy`|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="4ed0b-113">-128 から 127 までの値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-113">Values from -128 to 127.</span></span>|`1y`|
|`int16`|<xref:System.Int16>|<span data-ttu-id="4ed0b-114">-32768 から 32767 までの値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-114">Values from -32768 to 32767.</span></span>|`1s`|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="4ed0b-115">0 から 65535 までの値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-115">Values from 0 to 65535.</span></span>|`1us`|
|`int`|<xref:System.Int32>|<span data-ttu-id="4ed0b-116">-2,147,483,648 から 2,147,483,647 までの値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|`1`|
|`uint`|<xref:System.UInt32>|<span data-ttu-id="4ed0b-117">0 から 4,294,967,295 までの値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-117">Values from 0 to 4,294,967,295.</span></span>|`1u`|
|`int64`|<xref:System.Int64>|<span data-ttu-id="4ed0b-118">-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807 までの値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|`1L`|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="4ed0b-119">0 から 18,446,744,073,709,551,615 までの値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|`1UL`|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="4ed0b-120">符号付き整数としてのネイティブ ポインター。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-120">A native pointer as a signed integer.</span></span>|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="4ed0b-121">符号なし整数としてのネイティブ ポインター。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-121">A native pointer as an unsigned integer.</span></span>|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="4ed0b-122">有効数字が 28 桁以上の浮動小数点データ型。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-122">A floating point data type that has at least 28 significant digits.</span></span>|`1.0`|
|<span data-ttu-id="4ed0b-123">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="4ed0b-123">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="4ed0b-124">64 ビット浮動小数点型。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-124">A 64-bit floating point type.</span></span>|`1.0`|
|<span data-ttu-id="4ed0b-125">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="4ed0b-125">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="4ed0b-126">32 ビット浮動小数点型。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-126">A 32-bit floating point type.</span></span>|`1.0f`|
|`char`|<xref:System.Char>|<span data-ttu-id="4ed0b-127">Unicode 文字値。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-127">Unicode character values.</span></span>|`'c'`|
|`string`|<xref:System.String>|<span data-ttu-id="4ed0b-128">Unicode テキスト。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-128">Unicode text.</span></span>|`"str"`|
|`unit`|<span data-ttu-id="4ed0b-129">適用外</span><span class="sxs-lookup"><span data-stu-id="4ed0b-129">not applicable</span></span>|<span data-ttu-id="4ed0b-130">実際の値が存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-130">Indicates the absence of an actual value.</span></span> <span data-ttu-id="4ed0b-131">この型には、`()` で示される仮値が 1 つだけあります。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-131">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="4ed0b-132">単位値 `()` は、値が必要であるものの、実際の値を使用できない、または意味を持つ値がない場合のプレースホルダーとしてよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-132">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|`()`|

> [!NOTE]
> <span data-ttu-id="4ed0b-133">64 ビット整数型に対して大きすぎる整数の計算は、`bigint` 型を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-133">You can perform computations with integers too big for the 64-bit integer type by using the `bigint` type.</span></span> <span data-ttu-id="4ed0b-134">`bigint` は基本型とは見なされません。これは、`System.Numerics.BigInteger` の省略形です。</span><span class="sxs-lookup"><span data-stu-id="4ed0b-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ed0b-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ed0b-135">See also</span></span>

- [<span data-ttu-id="4ed0b-136">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="4ed0b-136">F# Language Reference</span></span>](index.md)
