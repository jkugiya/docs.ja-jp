---
title: 破壊的変更:LastIndexOf では、空の検索文字列の処理が改善されています
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、LastIndexOf と関連 API により、長さ 0 の substring を検索するときに正しい値が返されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 9dc34300d867fe1bb9264494b3f2261bad2c1eea
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257428"
---
# <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a>LastIndexOf では、空の検索文字列の処理が改善されています

<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> と関連 API により、より大きな文字列内で長さ 0 の (または長さ 0 と同等の) サブ文字列を検索するときに、正しい値が返されるようになりました。

## <a name="change-description"></a>変更の説明

.NET Framework と .NET Core 1.0 から 3.1 では、呼び出し元が長さ 0 のサブ文字列を検索するときに、<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> と関連 API によって不正な値が返されることがありました。

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

.NET 5 以降では、これらの API によって `LastIndexOf` の正しい値が返されます。

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

これらの例では、`"Hello".Substring(5)` と `"Hello".AsSpan().Slice(5)` の両方で空の文字列が生成されるため、`5` は正しい答えです。これは、検索対象の空のサブ文字列と同等です。

## <a name="reason-for-change"></a>変更理由

この変更は、.NET 5 の文字列処理に関する全般的なバグ修正作業の一環として行われました。 またこれは、Windows の動作と Windows 以外のプラットフォームの動作を統合するのにも役立ちます。 詳細については、[dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) および [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

何らかのアクションをとる必要はありません。 .NET 5 ランタイムでは、新しい動作が自動的に提供されます。

以前の動作を復元するための互換性スイッチはありません。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
