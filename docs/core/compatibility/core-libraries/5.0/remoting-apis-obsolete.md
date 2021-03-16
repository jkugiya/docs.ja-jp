---
title: 破壊的変更:リモート API は旧型式
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。一部のリモート処理関連の API は古いものとしてマークされており、カスタム診断 ID を含む警告が生成されます。
ms.date: 11/01/2020
ms.openlocfilehash: 3c4f7cd200cadd11321da60f2b4a0d191497aae8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257170"
---
# <a name="remoting-apis-are-obsolete"></a>リモート API は旧型式

一部のリモート処理関連の API は古いものとしてマークされており、コンパイル時に `SYSLIB0010` 警告が生成されます。 これらの API は、将来のバージョンの .NET で削除される可能性があります。

## <a name="change-description"></a>変更内容

次のリモート API は、古いものとしてマークされています。

| API | 古いものとしてマークされる対象 |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | 5.0 RC1 |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | 5.0 RC1 |

.NET Framework 2.x から 4.x では、<xref:System.MarshalByRefObject.GetLifetimeService> および <xref:System.MarshalByRefObject.InitializeLifetimeService> メソッドによって、.NET リモート処理に関するインスタンスの有効期間が制御されます。 .NET Core 2.x から 3.x では、これらのメソッドによって常に、実行時に <xref:System.PlatformNotSupportedException> がスローされます。

.NET 5 以降のバージョンでは、<xref:System.MarshalByRefObject.GetLifetimeService> および <xref:System.MarshalByRefObject.InitializeLifetimeService> メソッドは古いものとしてマークされ、警告が示されますが、実行時には引き続き <xref:System.PlatformNotSupportedException> がスローされます。

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

これは、コンパイル時のみの変更です。 実行時については、以前のバージョンの .NET Core からの変更はありません。

## <a name="reason-for-change"></a>変更理由

[.NET リモート処理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))はレガシ テクノロジです。 これにより、(異なるコンピューター上にある可能性があっても) 別のプロセスでオブジェクトをインスタンス化し、通常のインプロセス .NET オブジェクト インスタンスの場合と同じように、そのオブジェクトとやりとりすることができます。 .NET リモート処理インフラストラクチャは .NET Framework 2.x から 4.x にのみ存在します。 .NET Core および .NET 5 以降のバージョンで .NET リモート処理はサポートされておらず、リモート API が存在しないか、常にこれらのランタイムで例外がスローされます。

開発者がこれらの API を使用しないようにするために、選択されたリモート処理関連の API を古いものと見なしています。 これらの API は、将来のバージョンの .NET で完全に削除される可能性があります。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨アクション

- 他のアプリケーションの、または複数のコンピューターのオブジェクトと通信する場合は、WCF または HTTP ベースの REST サービスの使用を検討してください。 詳細については、[.NET Core で使用できない .NET Framework テクノロジ](../../../porting/net-framework-tech-unavailable.md)に関するページを参照してください。

- 古い API を引き続き使用する必要がある場合は、コードで `SYSLIB0010` 警告を抑制することができます。

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  プロジェクト ファイルで警告を抑制することもできます。これにより、プロジェクト内のすべてのソース ファイルに対して警告が無効になります。

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  `SYSLIB0010` を抑制すると、リモート API が古いという警告のみが無効になります。 それ以外の警告は無効になりません。 また、常に <xref:System.PlatformNotSupportedException> をスローするハードコーディングされた実行時の動作は変更されません。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
