---
title: .NET 5 以降の古い機能
description: SYSLIB コンパイラの警告を発生させる、.NET 5 以降のバージョンで古いものとしてマークされた API について説明します。
ms.date: 10/20/2020
ms.openlocfilehash: d6563f21624456d74801242268ecf72652fc4f88
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256284"
---
# <a name="obsolete-features-in-net-5"></a>.NET 5 の古い機能

.NET 5 以降、新たに、古いものとしてマークされた一部の API によって、<xref:System.ObsoleteAttribute> の 2 つの新しいプロパティが使用されます。

- <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> プロパティは、カスタム診断 ID を使用してビルド警告を生成するようにコンパイラに指示します。 カスタム ID を使用すると、旧型式であるという警告を明確に個別に分けて非表示にすることができます。 .NET 5 以降の旧型式の場合、カスタム診断 ID の形式は `SYSLIBxxxx` です。

- <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> プロパティは、旧型式の詳細について確認するために URL リンクを含めるようにコンパイラに指示します。

古い API の使用によってビルドの警告またはエラーが発生した場合は、「[リファレンス](#reference)」セクションに記載されている診断 ID に関する具体的なガイダンスに従ってください。 これらの古い警告またはエラーは、古い型またはメンバーに対して [標準診断 ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) を使用して非表示にすることは "*できません*"。代わりに、カスタム `SYSLIBxxxx` 診断 ID の値を使用してください。 詳細については、「[警告を表示しない](#suppress-warnings)」を参照してください。

## <a name="reference"></a>リファレンス

次の表は、.NET 5 以降の `SYSLIBxxxx` 旧型式のインデックスを示しています。

| 診断 ID | Description |
| - | - |
| [SYSLIB0001](syslib-warnings/syslib0001.md) | UTF-7 エンコードは安全ではないため、使用しないでください。 代わりに UTF-8 を使用することを検討してください。 |
| [SYSLIB0002](syslib-warnings/syslib0002.md) | <xref:System.Security.Permissions.PrincipalPermissionAttribute> はランタイムによって受け入れられず、使用することはできません。 |
| [SYSLIB0003](syslib-warnings/syslib0003.md) | コード アクセス セキュリティ (CAS) はサポートされていないか、ランタイムによって受け入れられていません。 |
| [SYSLIB0004](syslib-warnings/syslib0004.md) | 制約された実行領域 (CER) 機能はサポートされていません。 |
| [SYSLIB0005](syslib-warnings/syslib0005.md) | グローバル アセンブリ キャッシュ (GAC) はサポートされていません。 |
| [SYSLIB0006](syslib-warnings/syslib0006.md) | <xref:System.Threading.Thread.Abort?displayProperty=nameWithType> はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。 |
| [SYSLIB0007](syslib-warnings/syslib0007.md) | この暗号化アルゴリズムの既定の実装はサポートされていません。 |
| [SYSLIB0008](syslib-warnings/syslib0008.md) | <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。 |
| [SYSLIB0009](syslib-warnings/syslib0009.md) | <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> および <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> メソッドはサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。 |
| [SYSLIB0010](syslib-warnings/syslib0010.md) | 一部のリモート処理 API はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。 |
| [SYSLIB0011](syslib-warnings/syslib0011.md) | <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> シリアル化は古いので使用しないでください。 |
| [SYSLIB0012](syslib-warnings/syslib0012.md) | <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> と <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> は .NET Framework との互換性のためだけに含まれています。 代わりに、<xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> を使用してください。 |

## <a name="suppress-warnings"></a>警告を表示しない

古い API を使用する必要があり、`SYSLIBxxxx` 診断がエラーとして表示されない場合は、コードまたはプロジェクト ファイルで警告を非表示にすることができます。

コードは次のとおりです。

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

プロジェクト ファイル:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> このように警告を非表示にすると、指定した非推奨警告だけが無効になります。 診断 ID の異なる非推奨警告を含め、その他の警告は無効になりません。
