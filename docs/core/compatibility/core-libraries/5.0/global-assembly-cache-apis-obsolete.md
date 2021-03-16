---
title: '破壊的変更: グローバル アセンブリ キャッシュ API は旧型式'
description: Core .NET ライブラリでの .NET 5 に関する破壊的変更について学習します。この変更により、GAC を処理する API は、失敗するか、操作が実行されません。
ms.date: 11/01/2020
ms.openlocfilehash: 39c7b092b06754a28723693c0147b7ec3a0b705e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257480"
---
# <a name="global-assembly-cache-apis-are-obsolete"></a>グローバル アセンブリ キャッシュ API は旧型式

.NET Core および .NET 5 以降のバージョンでは、.NET Framework に存在していたグローバル アセンブリ キャッシュ (GAC) の概念がなくなりました。 そのため、GAC を処理するすべての .NET Core および .NET 5 以降の API は失敗するか、操作が実行されません。

開発者がこれらの API を使用しないようにするために、一部の GAC 関連の API は古いものとしてマークされており、コンパイル時に `SYSLIB0005` 警告が生成されます。 これらの API は、将来のバージョンの .NET で削除される可能性があります。

## <a name="change-description"></a>変更内容

次の API は古いものとしてマークされています。

| API | 古いものとしてマークされる対象 |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | 5.0 RC1 |

.NET Framework 2.x から 4.x では、クエリが実行されたアセンブリが GAC から読み込まれた場合は <xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティから `true` が返され、ディスク上の異なる場所から読み込まれた場合は `false` が返されます。 .NET Core 2.x から 3.x では、<xref:System.Reflection.Assembly.GlobalAssemblyCache> から常に `false` が返されます。これは、GAC が .NET Core に存在しないことを反映しています。

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

.NET 5 以降のバージョンでは、<xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティからは引き続き、常に `false` が返されます。 しかし、プロパティ getter も、プロパティへのアクセスを停止する必要があることを呼び出し元に示すために、古いものとしてマークされています。 ライブラリとアプリで実行時の動作を決定するために <xref:System.Reflection.Assembly.GlobalAssemblyCache> API を使用することはできません。これは、.NET Core および .NET 5 以降のバージョンでは常に `false` が返されるためです。

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

これは、コンパイル時のみの変更です。 実行時については、以前のバージョンの .NET Core からの変更はありません。

## <a name="reason-for-change"></a>変更理由

.NET Core および .NET 5 以降のバージョンでは、グローバル アセンブリ キャッシュ (GAC) は概念として存在しません。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨アクション

- アプリケーションによって <xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティのクエリが実行される場合は、呼び出しを削除することを検討してください。 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 値を使用して、実行時に "GAC のアセンブリ" フローと "GAC に存在しないアセンブリ" フローのどちらかを選択する場合は、フローが .NET Core または .NET 5.0 以降のアプリケーションで引き続き意味を持つかどうかを再検討してください。

- 古い API を引き続き使用する必要がある場合は、コードで `SYSLIB0005` 警告を抑制することができます。

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  プロジェクト ファイルで警告を抑制することもできます。これにより、プロジェクト内のすべてのソース ファイルに対して警告が無効になります。

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  `SYSLIB0005` を抑制すると、<xref:System.Reflection.Assembly.GlobalAssemblyCache> が旧型式であるという警告のみが無効になります。 それ以外の警告は無効になりません。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
