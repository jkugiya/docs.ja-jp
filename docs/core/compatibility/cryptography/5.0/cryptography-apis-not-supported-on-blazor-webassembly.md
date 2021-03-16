---
title: 破壊的変更:Blazor WebAssembly で System.Security.Cryptography API がサポートされない
description: .NET 5 の破壊的変更について学習します。この変更後、暗号化 API は、ブラウザーで実行されると例外をスローするようになりました。
ms.date: 09/16/2020
ms.openlocfilehash: ecbdda4c04642af6b1737e888491eb6565ba7479
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256882"
---
# <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a>Blazor WebAssembly で System.Security.Cryptography API がサポートされない

<xref:System.Security.Cryptography> API は、ブラウザーで実行されると、実行時に <xref:System.PlatformNotSupportedException> をスローします。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、ほとんどの <xref:System.Security.Cryptography> API が Blazor WebAssembly で使用できません。 .NET 5 以降、Blazor WebAssembly アプリでは .NET 5 API の全アクセス領域が対象になりますが、ブラウザー サンドボックスの制約によりすべての .NET 5 API がサポートされているわけではありません。 .NET 5 以降のバージョンでは、サポートされていない <xref:System.Security.Cryptography> API を WebAssembly で実行すると <xref:System.PlatformNotSupportedException> がスローされます。

> [!TIP]
> ブラウザー プラットフォームをサポートするプロジェクトをビルドすると、[プラットフォーム互換性アナライザー](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md)によって、影響を受ける API の呼び出しにフラグが設定されます。 このアナライザーは、.NET 5 以降のアプリでは既定で実行されます。

## <a name="reason-for-change"></a>変更理由

Microsoft では、Blazor WebAssembly 構成の依存関係として OpenSSL を公開することができません。 私たちは、ブラウザーの `SubtleCrypto` API と統合することでこれを回避しようとしました。 残念ながら、それには大幅な API の変更が必要であり、統合は困難でした。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

現時点では、推奨される回避策はありません。

## <a name="affected-apis"></a>影響を受ける API

次を除くすべての <xref:System.Security.Cryptography?displayProperty=fullName> API:

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

### Affected APIs

- `T:System.Security.Cryptography`

### Category

- ASP.NET Core
- Cryptography

-->
