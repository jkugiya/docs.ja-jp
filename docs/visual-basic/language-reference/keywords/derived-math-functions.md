---
description: '詳細情報: 数値演算関数の導出 (Visual Basic)'
title: 数値演算関数の導出
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: daaed1312f08cecc0c68af0e36d574424fc526a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730773"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="66250-103">数値演算関数の導出 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66250-103">Derived Math Functions (Visual Basic)</span></span>

<span data-ttu-id="66250-104">次の表に、<xref:System.Math?displayProperty=nameWithType> オブジェクトの組み込み数学関数から導出できる非組み込み数学関数を示します。</span><span class="sxs-lookup"><span data-stu-id="66250-104">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="66250-105">組み込み数学関数にアクセスするには、ファイルまたはプロジェクトに `Imports System.Math` を追加します。</span><span class="sxs-lookup"><span data-stu-id="66250-105">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="66250-106">関数</span><span class="sxs-lookup"><span data-stu-id="66250-106">Function</span></span>|<span data-ttu-id="66250-107">導出した同等物</span><span class="sxs-lookup"><span data-stu-id="66250-107">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="66250-108">Secant (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="66250-108">Secant (Sec(x))</span></span>|<span data-ttu-id="66250-109">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="66250-109">1 / Cos(x)</span></span>|  
|<span data-ttu-id="66250-110">Cosecant (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="66250-110">Cosecant (Csc(x))</span></span>|<span data-ttu-id="66250-111">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="66250-111">1 / Sin(x)</span></span>|  
|<span data-ttu-id="66250-112">Cotangent (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="66250-112">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="66250-113">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="66250-113">1 / Tan(x)</span></span>|  
|<span data-ttu-id="66250-114">Inverse sine (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="66250-114">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="66250-115">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="66250-115">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="66250-116">Inverse cosine (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="66250-116">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="66250-117">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="66250-117">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="66250-118">Inverse secant (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="66250-118">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="66250-119">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="66250-119">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="66250-120">Inverse cosecant (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="66250-120">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="66250-121">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="66250-121">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="66250-122">Inverse cotangent (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="66250-122">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="66250-123">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="66250-123">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="66250-124">Hyperbolic sine (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="66250-124">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="66250-125">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="66250-125">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="66250-126">Hyperbolic cosine (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="66250-126">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="66250-127">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="66250-127">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="66250-128">Hyperbolic tangent (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="66250-128">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="66250-129">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="66250-129">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="66250-130">Hyperbolic secant (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="66250-130">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="66250-131">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="66250-131">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="66250-132">Hyperbolic cosecant (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="66250-132">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="66250-133">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="66250-133">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="66250-134">Hyperbolic cotangent (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="66250-134">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="66250-135">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="66250-135">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="66250-136">Inverse hyperbolic sine (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="66250-136">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="66250-137">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="66250-137">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="66250-138">Inverse hyperbolic cosine (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="66250-138">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="66250-139">Log(x + Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="66250-139">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="66250-140">Inverse hyperbolic tangent (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="66250-140">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="66250-141">Log((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="66250-141">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="66250-142">Inverse hyperbolic secant (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="66250-142">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="66250-143">Log((Sqrt(-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="66250-143">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="66250-144">Inverse hyperbolic cosecant (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="66250-144">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="66250-145">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="66250-145">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="66250-146">Inverse hyperbolic cotangent (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="66250-146">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="66250-147">Log((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="66250-147">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66250-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="66250-148">See also</span></span>

- [<span data-ttu-id="66250-149">数値演算関数</span><span class="sxs-lookup"><span data-stu-id="66250-149">Math Functions</span></span>](../functions/math-functions.md)
