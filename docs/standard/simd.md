---
title: .NET での SIMD アクセラレータの型
description: この記事では、.NET での SIMD が有効な型について説明し、C# および .NET でハードウェアの SIMD 操作を使用する方法について示します。
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.openlocfilehash: 9ac437fd78ed81cd4c2d786f52bac80c5cf22e8f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "103412172"
---
# <a name="use-simd-accelerated-numeric-types"></a><span data-ttu-id="eb2e8-103">SIMD アクセラレータの数値型を使用する</span><span class="sxs-lookup"><span data-stu-id="eb2e8-103">Use SIMD-accelerated numeric types</span></span>

<span data-ttu-id="eb2e8-104">SIMD (Single Instruction Multiple Data) を使用すると、1 つの命令を使用して、複数のデータに対して並列で操作を実行するためのハードウェア サポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-104">SIMD (Single instruction, multiple data) provides hardware support for performing an operation on multiple pieces of data, in parallel, using a single instruction.</span></span> <span data-ttu-id="eb2e8-105">.NET では、<xref:System.Numerics> 名前空間の下に SIMD アクセラレータの型のセットがあります。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-105">In .NET, there's set of SIMD-accelerated types under the <xref:System.Numerics> namespace.</span></span> <span data-ttu-id="eb2e8-106">SIMD 操作は、ハードウェア レベルで並列化できます。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-106">SIMD operations can be parallelized at the hardware level.</span></span> <span data-ttu-id="eb2e8-107">それにより、数学、科学、グラフィックス アプリで一般的な、ベクター化された計算のスループットが向上します。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-107">That increases the throughput of the vectorized computations, which are common in mathematical, scientific, and graphics apps.</span></span>

## <a name="net-simd-accelerated-types"></a><span data-ttu-id="eb2e8-108">.NET の SIMD アクセラレータの型</span><span class="sxs-lookup"><span data-stu-id="eb2e8-108">.NET SIMD-accelerated types</span></span>

<span data-ttu-id="eb2e8-109">.NET の SIMD アクセラレータの型には、次の型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-109">The .NET SIMD-accelerated types include the following types:</span></span>

- <span data-ttu-id="eb2e8-110">それぞれ 2、3、4 つの <xref:System.Single> 値を表す <xref:System.Numerics.Vector2> 型、<xref:System.Numerics.Vector3> 型、<xref:System.Numerics.Vector4> 型。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-110">The <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span>

- <span data-ttu-id="eb2e8-111">2 つのマトリックス型。3x2 行列を表す <xref:System.Numerics.Matrix3x2> と <xref:System.Single> 値の 4x4 行列を表す <xref:System.Numerics.Matrix4x4>。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-111">Two matrix types, <xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix of <xref:System.Single> values.</span></span>

- <span data-ttu-id="eb2e8-112"><xref:System.Single> 値を使用して 3 次元空間の平面を表す <xref:System.Numerics.Plane> 型。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-112">The <xref:System.Numerics.Plane> type, which represents a plane in three-dimensional space using <xref:System.Single> values.</span></span>

- <span data-ttu-id="eb2e8-113"><xref:System.Single> 値を使用して 3 次元物理回転をエンコードするために使用されるベクトルを表す <xref:System.Numerics.Quaternion> 型。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-113">The <xref:System.Numerics.Quaternion> type, which represents a vector that is used to encode three-dimensional physical rotations using <xref:System.Single> values.</span></span>

- <span data-ttu-id="eb2e8-114">指定の数値型のベクトルを表し、SIMD サポートが活かされる広範囲の演算子セットを提供する <xref:System.Numerics.Vector%601> 型。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-114">The <xref:System.Numerics.Vector%601> type, which represents a vector of a specified numeric type and provides a broad set of operators that benefit from SIMD support.</span></span> <span data-ttu-id="eb2e8-115"><xref:System.Numerics.Vector%601> インスタンスの数は、アプリケーションの有効期間にわたって固定されていますが、その値 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> は、コードを実行しているコンピューターの CPU によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-115">The count of a <xref:System.Numerics.Vector%601> instance is fixed for the lifetime of an application, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

  > [!NOTE]
  > <span data-ttu-id="eb2e8-116"><xref:System.Numerics.Vector%601> 型は .NET Framework に含まれません。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-116">The <xref:System.Numerics.Vector%601> type is not included in the .NET Framework.</span></span> <span data-ttu-id="eb2e8-117">この型にアクセスするには、[System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet パッケージをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-117">You must install the [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet package to get access to this type.</span></span>
  
<span data-ttu-id="eb2e8-118">SIMD アクセラレータの型は、非 SIMD アクセラレータのハードウェアや JIT コンパイラと共に使用できるように実装されています。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-118">The SIMD-accelerated types are implemented in such a way that they can be used with non-SIMD-accelerated hardware or JIT compilers.</span></span> <span data-ttu-id="eb2e8-119">SIMD 命令を活用するには、64 ビット アプリを **RyuJIT** コンパイラを使用するランタイムで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-119">To take advantage of SIMD instructions, your 64-bit apps must be run by the runtime that uses the **RyuJIT** compiler.</span></span> <span data-ttu-id="eb2e8-120">**RyuJIT** コンパイラは、.NET Core と .NET Framework 4.6 以降に含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-120">A **RyuJIT** compiler is included in .NET Core and in .NET Framework 4.6 and later.</span></span> <span data-ttu-id="eb2e8-121">SIMD のサポートは、64 ビット プロセッサを対象とする場合にのみ提供されます。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-121">SIMD support is only provided when targeting 64-bit processors.</span></span>

## <a name="how-to-use-simd"></a><span data-ttu-id="eb2e8-122">SIMD の使用方法</span><span class="sxs-lookup"><span data-stu-id="eb2e8-122">How to use SIMD?</span></span>

<span data-ttu-id="eb2e8-123">カスタム SIMD アルゴリズムを実行する前に、<xref:System.Boolean> を返す <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType> を使用して、ホスト コンピューターが SIMD をサポートするかどうかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-123">Before executing custom SIMD algorithms, it's possible to check if the host machine supports SIMD by using <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, which returns a <xref:System.Boolean>.</span></span> <span data-ttu-id="eb2e8-124">これにより、特定の型に対して SIMD アクセラレータが有効になることは保証されませんが、一部の型でサポートされていることを示すインジケーターになります。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-124">This doesn't guarantee that SIMD-acceleration is enabled for a specific type, but is an indicator that it's supported by some types.</span></span>

## <a name="simple-vectors"></a><span data-ttu-id="eb2e8-125">単純なベクター</span><span class="sxs-lookup"><span data-stu-id="eb2e8-125">Simple Vectors</span></span>

<span data-ttu-id="eb2e8-126">.NET で最もプリミティブな SIMD アクセラレータの型は <xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3>、<xref:System.Numerics.Vector4> 型です。これは、2、3、4 つの <xref:System.Single> 値を持つベクトルを表します。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-126">The most primitive SIMD-accelerated types in .NET are <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span> <span data-ttu-id="eb2e8-127">以下の例では、<xref:System.Numerics.Vector2> を使用して 2 つのベクトルを追加しています。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-127">The example below uses <xref:System.Numerics.Vector2> to add two vectors.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult = v1 + v2;
```

<span data-ttu-id="eb2e8-128">.NET ベクトルを使用して、`Dot product`、`Transform`、`Clamp` などのベクトルの他の数学的特性を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-128">It's also possible to use .NET vectors to calculate other mathematical properties of vectors such as `Dot product`, `Transform`, `Clamp` and so on.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult1 = Vector2.Dot(v1, v2);
var vResult2 = Vector2.Distance(v1, v2);
var vResult3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a><span data-ttu-id="eb2e8-129">Matrix</span><span class="sxs-lookup"><span data-stu-id="eb2e8-129">Matrix</span></span>

<span data-ttu-id="eb2e8-130">3x2 行列を表す <xref:System.Numerics.Matrix3x2> と 4x4 行列を表す <xref:System.Numerics.Matrix4x4>。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-130"><xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix.</span></span> <span data-ttu-id="eb2e8-131">行列関連の計算に使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-131">Can be used for matrix-related calculations.</span></span> <span data-ttu-id="eb2e8-132">以下の例は、SIMD を使用した対応する転置行列への行列の乗算を示しています。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-132">The example below demonstrates multiplication of a matrix to its correspondent transpose matrix using SIMD.</span></span>

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a><span data-ttu-id="eb2e8-133">ベクター\<T></span><span class="sxs-lookup"><span data-stu-id="eb2e8-133">Vector\<T></span></span>

<span data-ttu-id="eb2e8-134"><xref:System.Numerics.Vector%601> を使用すると、より長いベクトルを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-134">The <xref:System.Numerics.Vector%601> gives the ability to use longer vectors.</span></span> <span data-ttu-id="eb2e8-135"><xref:System.Numerics.Vector%601> インスタンスの数は固定ですが、その値 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> はコードが実行されるコンピューターの CPU によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-135">The count of a <xref:System.Numerics.Vector%601> instance is fixed, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

<span data-ttu-id="eb2e8-136">以下の例は、<xref:System.Numerics.Vector%601> を使用して、長い配列要素を追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-136">The example below demonstrates adding long arrays elements using <xref:System.Numerics.Vector%601>.</span></span>

```csharp
double[] SimdVectorProd(double[] left, double[] right)
{
    var offset = Vector<double>.Count;
    double[] result = new double[left.Length];
    int i = 0;
    for (i = 0; i < left.Length; i += offset)
    {
        var v1 = new Vector<double>(left, i);
        var v2 = new Vector<double>(right, i);
        (v1 * v2).CopyTo(result, i);
    }

    //remaining items
    for (; i < left.Length; ++i)
    {
        result[i] = left[i] * right[i];
    }

    return result;
}
```

## <a name="remarks"></a><span data-ttu-id="eb2e8-137">解説</span><span class="sxs-lookup"><span data-stu-id="eb2e8-137">Remarks</span></span>

<span data-ttu-id="eb2e8-138">SIMD は、メモリのスループットのように、1 つのボトルネックを取り除いても、次のものにさらされる可能性が高いです。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-138">SIMD is more likely to remove one bottleneck and expose the next, for example memory throughput.</span></span> <span data-ttu-id="eb2e8-139">一般に、SIMD を使用する場合のパフォーマンス上の利点は、具体的なシナリオによって異なります。場合によっては、より単純な SIMD 以外の同等のコードよりもパフォーマンスが悪くなることもあります。</span><span class="sxs-lookup"><span data-stu-id="eb2e8-139">In general the performance benefit of using SIMD varies depending on the specific scenario, and in some cases it can even perform worse than simpler non-SIMD equivalent code.</span></span>
