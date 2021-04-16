---
title: ビット処理演算子
description: F# プログラミング言語で使用できるビット処理演算子について説明します。
ms.date: 07/20/2018
ms.openlocfilehash: e4d61492ba94d26cfe8354c0ba89fbd732ed782e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645067"
---
# <a name="bitwise-operators"></a><span data-ttu-id="4709c-103">ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="4709c-103">Bitwise Operators</span></span>

<span data-ttu-id="4709c-104">このトピックでは、F# 言語で使用できるビット処理演算子について説明します。</span><span class="sxs-lookup"><span data-stu-id="4709c-104">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="4709c-105">ビット処理演算子の概要</span><span class="sxs-lookup"><span data-stu-id="4709c-105">Summary of Bitwise Operators</span></span>

<span data-ttu-id="4709c-106">次の表では、F# 言語のボックス化解除された整数型でサポートされるビット処理演算子について説明します。</span><span class="sxs-lookup"><span data-stu-id="4709c-106">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="4709c-107">演算子</span><span class="sxs-lookup"><span data-stu-id="4709c-107">Operator</span></span>|<span data-ttu-id="4709c-108">Notes</span><span class="sxs-lookup"><span data-stu-id="4709c-108">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="4709c-109">ビット処理 AND 演算子。</span><span class="sxs-lookup"><span data-stu-id="4709c-109">Bitwise AND operator.</span></span> <span data-ttu-id="4709c-110">結果のビットは、両方のソース オペランドの対応するビットが 1 の場合にのみ、値 1 を持ちます。</span><span class="sxs-lookup"><span data-stu-id="4709c-110">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="4709c-111">ビット処理 OR 演算子。</span><span class="sxs-lookup"><span data-stu-id="4709c-111">Bitwise OR operator.</span></span> <span data-ttu-id="4709c-112">結果のビットは、ソース オペランドの対応するビットのいずれかが 1 の場合にのみ、値 1 を持ちます。</span><span class="sxs-lookup"><span data-stu-id="4709c-112">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="4709c-113">ビット処理排他的 OR 演算子。</span><span class="sxs-lookup"><span data-stu-id="4709c-113">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="4709c-114">結果のビットは、ソース オペランドのビットの値が等しくない場合にのみ、値 1 を持ちます。</span><span class="sxs-lookup"><span data-stu-id="4709c-114">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="4709c-115">ビット処理否定演算子。</span><span class="sxs-lookup"><span data-stu-id="4709c-115">Bitwise negation operator.</span></span> <span data-ttu-id="4709c-116">これは単項演算子で、ソース オペランドのすべての 0 ビットが 1 ビットに変換され、すべての 1 ビットが 0 ビットに変換された結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="4709c-116">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="4709c-117">ビット処理左シフト演算子。</span><span class="sxs-lookup"><span data-stu-id="4709c-117">Bitwise left-shift operator.</span></span> <span data-ttu-id="4709c-118">結果は、ビットが 2 番目のオペランドのビット数だけ左にシフトされた最初のオペランドです。</span><span class="sxs-lookup"><span data-stu-id="4709c-118">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="4709c-119">最上位の位置からシフトされたビットは、最下位の位置に回転されません。</span><span class="sxs-lookup"><span data-stu-id="4709c-119">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="4709c-120">最下位ビットに 0 が埋め込まれています。</span><span class="sxs-lookup"><span data-stu-id="4709c-120">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="4709c-121">2 番目の引数の型が `int32` です。</span><span class="sxs-lookup"><span data-stu-id="4709c-121">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="4709c-122">ビット処理右シフト演算子。</span><span class="sxs-lookup"><span data-stu-id="4709c-122">Bitwise right-shift operator.</span></span> <span data-ttu-id="4709c-123">結果は、ビットが 2 番目のオペランドのビット数だけ右にシフトされた最初のオペランドです。</span><span class="sxs-lookup"><span data-stu-id="4709c-123">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="4709c-124">最下位の位置からシフトされたビットは、最上位の位置に回転されません。</span><span class="sxs-lookup"><span data-stu-id="4709c-124">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="4709c-125">符号なしの型では、最上位ビットに 0 が埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="4709c-125">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="4709c-126">負の値を持つ符号付きの型では、最上位ビットに 1 が埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="4709c-126">For signed types with negative values, the most significant bits are padded with ones.</span></span> <span data-ttu-id="4709c-127">2 番目の引数の型が `int32` です。</span><span class="sxs-lookup"><span data-stu-id="4709c-127">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="4709c-128">次の型は、ビット処理演算子と共に使用できます: `byte`、`sbyte`、`int16`、`uint16`、`int32 (int)`、`uint32`、`int64`、`uint64`、`nativeint`、`unativeint`。</span><span class="sxs-lookup"><span data-stu-id="4709c-128">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4709c-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="4709c-129">See also</span></span>

- [<span data-ttu-id="4709c-130">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="4709c-130">Symbol and Operator Reference</span></span>](index.md)
- [<span data-ttu-id="4709c-131">算術演算子</span><span class="sxs-lookup"><span data-stu-id="4709c-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="4709c-132">ブール演算子</span><span class="sxs-lookup"><span data-stu-id="4709c-132">Boolean Operators</span></span>](boolean-operators.md)
