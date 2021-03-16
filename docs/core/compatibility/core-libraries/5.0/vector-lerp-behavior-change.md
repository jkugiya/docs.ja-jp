---
title: 破壊的変更:Vector2.Lerp と Vector4.Lerp の動作の変更
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、Vector2.Lerp と Vector4.Lerp の実装が、浮動小数点丸め誤差を正しく考慮するように変更されています。
ms.date: 11/01/2020
ms.openlocfilehash: a7014c30f2b102dc9a19e9a58f97b7c0ed8cd648
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256999"
---
# <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a>Vector2.Lerp と Vector4.Lerp の動作の変更

浮動小数点の丸め誤差を正しく考慮するように <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> と <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> の実装が変更されました。

## <a name="change-description"></a>変更の説明

以前は、<xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> と <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> は `value1 + (value2 - value1) * amount` として実装されていました。 ただし、浮動小数点の丸め誤差のため、`amount` が `1.0f` のとき、このアルゴリズムから `value2` が返されないことがありました。

.NET 5 以降では、この実装では、<xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> と同じアルゴリズム、すなわち `(value1 * (1.0f - amount)) + (value2 * amount)` が使用されます。 このアルゴリズムでは、丸め誤差が正しく考慮されます。 これで、`amount` が `1.0f` のとき、結果は正確に `value2` となります。 更新後のアルゴリズムではまた、利用できるとき、<xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> を利用してアルゴリズムを自由に最適化できます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

必要なアクションはありません。 ただし、以前の動作を保持する場合、`value1 + (value2 - value1) * amount` の前のアルゴリズムを使用する独自の `Lerp` 関数を実装できます。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
