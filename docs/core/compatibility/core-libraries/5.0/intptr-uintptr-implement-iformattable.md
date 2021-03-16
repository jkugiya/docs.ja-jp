---
title: 破壊的変更:IntPtr と UIntPtr の IFormattable 実装
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。IntPtr と UIntPtr で IFormattable が実装されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: adfb68807d5fa5f0c750fb41ef75951f63a4b2d5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257441"
---
# <a name="intptr-and-uintptr-implement-iformattable"></a>IntPtr と UIntPtr の IFormattable 実装

<xref:System.IntPtr> と <xref:System.UIntPtr> で <xref:System.IFormattable> が実装されるようになりました。 現在、<xref:System.IFormattable> サポートを確認する関数からは、これらの型に対して異なる結果が返されることがあります。書式指定子とカルチャで渡されることがあるためです。

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、<xref:System.IntPtr> と <xref:System.UIntPtr> では <xref:System.IFormattable> が実装されません。 <xref:System.IFormattable> を確認する関数はフォールバックし、<xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> または <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> を呼び出すことがあります。つまり、書式指定子とカルチャは無視されます。

.NET 5 以降のバージョンでは、<xref:System.IntPtr> と <xref:System.UIntPtr> で <xref:System.IFormattable> が実装されます。 現在、<xref:System.IFormattable> サポートを確認する関数からは、これらの型に対して異なる結果が返されることがあります。書式指定子とカルチャで渡されることがあるためです。

この変更は、補間された文字列や <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> などのシナリオに影響を与えます。

## <a name="reason-for-change"></a>変更理由

<xref:System.IntPtr> と <xref:System.UIntPtr> は、キーワードの `nint` と `nuint` を介して C# で言語サポートされます。 バッキング型は、<xref:System.Int32?displayProperty=nameWithType> など、他のプリミティブ型によって公開される機能により (可能であれば) ほぼ等しくなるように更新されました。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

これらの型の値を表示するとき、書式指定子またはカルチャを使用しない場合、`ToString()` のオーバーロードの <xref:System.IntPtr.ToString?displayProperty=nameWithType> と <xref:System.UIntPtr.ToString?displayProperty=nameWithType> を呼び出すことができます。

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Category

Core .NET libraries

### Affected APIs

Not detectable via API analysis.

-->
