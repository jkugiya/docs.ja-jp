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
# <a name="use-simd-accelerated-numeric-types"></a>SIMD アクセラレータの数値型を使用する

SIMD (Single Instruction Multiple Data) を使用すると、1 つの命令を使用して、複数のデータに対して並列で操作を実行するためのハードウェア サポートが提供されます。 .NET では、<xref:System.Numerics> 名前空間の下に SIMD アクセラレータの型のセットがあります。 SIMD 操作は、ハードウェア レベルで並列化できます。 それにより、数学、科学、グラフィックス アプリで一般的な、ベクター化された計算のスループットが向上します。

## <a name="net-simd-accelerated-types"></a>.NET の SIMD アクセラレータの型

.NET の SIMD アクセラレータの型には、次の型が含まれます。

- それぞれ 2、3、4 つの <xref:System.Single> 値を表す <xref:System.Numerics.Vector2> 型、<xref:System.Numerics.Vector3> 型、<xref:System.Numerics.Vector4> 型。

- 2 つのマトリックス型。3x2 行列を表す <xref:System.Numerics.Matrix3x2> と <xref:System.Single> 値の 4x4 行列を表す <xref:System.Numerics.Matrix4x4>。

- <xref:System.Single> 値を使用して 3 次元空間の平面を表す <xref:System.Numerics.Plane> 型。

- <xref:System.Single> 値を使用して 3 次元物理回転をエンコードするために使用されるベクトルを表す <xref:System.Numerics.Quaternion> 型。

- 指定の数値型のベクトルを表し、SIMD サポートが活かされる広範囲の演算子セットを提供する <xref:System.Numerics.Vector%601> 型。 <xref:System.Numerics.Vector%601> インスタンスの数は、アプリケーションの有効期間にわたって固定されていますが、その値 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> は、コードを実行しているコンピューターの CPU によって異なります。

  > [!NOTE]
  > <xref:System.Numerics.Vector%601> 型は .NET Framework に含まれません。 この型にアクセスするには、[System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet パッケージをインストールする必要があります。
  
SIMD アクセラレータの型は、非 SIMD アクセラレータのハードウェアや JIT コンパイラと共に使用できるように実装されています。 SIMD 命令を活用するには、64 ビット アプリを **RyuJIT** コンパイラを使用するランタイムで実行する必要があります。 **RyuJIT** コンパイラは、.NET Core と .NET Framework 4.6 以降に含まれています。 SIMD のサポートは、64 ビット プロセッサを対象とする場合にのみ提供されます。

## <a name="how-to-use-simd"></a>SIMD の使用方法

カスタム SIMD アルゴリズムを実行する前に、<xref:System.Boolean> を返す <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType> を使用して、ホスト コンピューターが SIMD をサポートするかどうかを確認することができます。 これにより、特定の型に対して SIMD アクセラレータが有効になることは保証されませんが、一部の型でサポートされていることを示すインジケーターになります。

## <a name="simple-vectors"></a>単純なベクター

.NET で最もプリミティブな SIMD アクセラレータの型は <xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3>、<xref:System.Numerics.Vector4> 型です。これは、2、3、4 つの <xref:System.Single> 値を持つベクトルを表します。 以下の例では、<xref:System.Numerics.Vector2> を使用して 2 つのベクトルを追加しています。

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult = v1 + v2;
```

.NET ベクトルを使用して、`Dot product`、`Transform`、`Clamp` などのベクトルの他の数学的特性を計算することもできます。

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult1 = Vector2.Dot(v1, v2);
var vResult2 = Vector2.Distance(v1, v2);
var vResult3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a>Matrix

3x2 行列を表す <xref:System.Numerics.Matrix3x2> と 4x4 行列を表す <xref:System.Numerics.Matrix4x4>。 行列関連の計算に使用できます。 以下の例は、SIMD を使用した対応する転置行列への行列の乗算を示しています。

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a>ベクター\<T>

<xref:System.Numerics.Vector%601> を使用すると、より長いベクトルを使用することができます。 <xref:System.Numerics.Vector%601> インスタンスの数は固定ですが、その値 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> はコードが実行されるコンピューターの CPU によって異なります。

以下の例は、<xref:System.Numerics.Vector%601> を使用して、長い配列要素を追加する方法を示しています。

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

## <a name="remarks"></a>解説

SIMD は、メモリのスループットのように、1 つのボトルネックを取り除いても、次のものにさらされる可能性が高いです。 一般に、SIMD を使用する場合のパフォーマンス上の利点は、具体的なシナリオによって異なります。場合によっては、より単純な SIMD 以外の同等のコードよりもパフォーマンスが悪くなることもあります。
