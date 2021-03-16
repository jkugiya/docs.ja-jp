---
title: 破壊的変更:.NET 5 を対象とする場合の NETCOREAPP3_1 プリプロセッサ シンボルが定義されていない
description: .NET 5 での破壊的変更について学習します。プロジェクトでのプリプロセッサ シンボルの定義は以前のバージョンに対しては行われなくなります。
ms.date: 09/17/2020
ms.openlocfilehash: 390c8f5af97510db4652f3f42db577e6de158020
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256531"
---
# <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a>.NET 5 を対象とする場合の NETCOREAPP3_1 プリプロセッサ シンボルが定義されていない

.NET 5 RC2 以降のバージョンでは、プロジェクトでのプリプロセッサ シンボルの定義は対象とするバージョンに対してのみ行われ、以前のバージョンでは行われなくなります。 これは、.NET Core 1.0 - 3.1 と同じ動作です。

## <a name="version-introduced"></a>導入されたバージョン

5.0 RC2

## <a name="change-description"></a>変更内容

.NET 5 Preview 7 から RC1 では、`net5.0` を対象とするプロジェクトで `NETCOREAPP3_1` と `NET5_0` の両方のプリプロセッサ シンボルが定義されます。 この動作変更は、.NET 5 以降で、条件付きコンパイルの[シンボルが累積になる](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols)ことを意図したものでした。

.NET 5 RC2 以降では、プロジェクトは、以前のバージョンではなく、対象となるターゲット フレームワーク モニカー (TFM) のみに対するシンボルを定義します。

## <a name="reason-for-change"></a>変更理由

Preview 7 からの変更は、お客様からのフィードバックにより元に戻されました。 以前のバージョンのシンボルの定義はお客様を驚かせ、混乱させました。C# のコンパイラにバグがあったと考えたお客様もいました。

## <a name="recommended-action"></a>推奨アクション

プロジェクトが `net5.0` 以上を対象とするときに `NETCOREAPP3_1` が定義されていることを `#if` ロジックで前提としていないことを確認してください。 代わりに、プロジェクトが `netcoreapp3.1` を明示的に対象としている場合は `NETCOREAPP3_1` のみが定義されることを前提としてください。

たとえば、プロジェクトが .NET Core 2.1 および .NET Core 3.1 のマルチターゲットで、.NET Core 3.1 で導入された API を呼び出す場合、`#if` ロジックは次のようになります。

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

## <a name="affected-apis"></a>影響を受ける API

N/A

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
