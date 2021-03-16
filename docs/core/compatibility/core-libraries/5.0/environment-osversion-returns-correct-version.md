---
title: 破壊的変更:Environment.OSVersion で正しいオペレーティング システム バージョンが返される
description: Environment.OSVersion から、たとえば、アプリケーションの互換性にために選択されている OS ではなく、オペレーティング システムの実際のバージョンが返されるという、コア .NET ライブラリの .NET 5 破壊的変更について学習します。
ms.date: 11/01/2020
ms.openlocfilehash: 05ec886061263ea43a2d956b8ce0ecc06e2bf3ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257532"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment.OSVersion で正しいオペレーティング システム バージョンが返される

<xref:System.Environment.OSVersion?displayProperty=nameWithType> で、アプリケーションの互換性のために選択される OS などではなく、オペレーティング システム (OS) の実際のバージョンが返されます。

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、アプリケーションが Windows 互換モードで実行されている場合、<xref:System.Environment.OSVersion?displayProperty=nameWithType> によって、正しくない可能性がある OS バージョンが返されます。 詳細については、[GetVersionExA 関数の解説](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)に関する記述を参照してください。 macOS では、基になる Darwin カーネルのバージョンが <xref:System.Environment.OSVersion?displayProperty=nameWithType> によって返されます。

.NET 5 以降では、Windows と macOS のオペレーティング システムの実際のバージョンが <xref:System.Environment.OSVersion?displayProperty=nameWithType> によって返されます。

次の表に、動作の違いを示します。

|  | 以前の .NET バージョン | .NET 5+ |
|--|------------------------|---------|
| Windows | 6.2.9200.0 | 10.0.19042.0 |
| macOS | 19.6.0.0 | 10.15.7 |

## <a name="reason-for-change"></a>変更理由

このプロパティのユーザーは、オペレーティング システムの実際のバージョンが返されることを期待しています。 ほとんどの .NET アプリにより、アプリケーション マニフェストでサポートされているバージョンが指定されないため、dotnet ホストから既定でサポートされているバージョンが取得されます。 その結果、実行されているアプリでは互換性 shim はほとんど意味がなくなります。 Windows で新しいバージョンがリリースされており、古い dotnet ホストがまだ使用されている場合は、これらのアプリの OS バージョンが正しくない可能性があります。 実際のバージョンを返すことが、この API に対する開発者の期待により沿うことになります。

.NET 5 での <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>、<xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>、および <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> の導入により、Windows および macOS で <xref:System.Environment.OSVersion?displayProperty=nameWithType> が整合するように変更されました。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

<xref:System.Environment.OSVersion?displayProperty=nameWithType> を使用するコードを確認してテストし、確実に期待どおりに動作するようにします。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
