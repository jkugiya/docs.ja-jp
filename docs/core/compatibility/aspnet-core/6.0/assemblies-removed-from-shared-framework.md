---
title: '破壊的変更: Microsoft.AspNetCore.App 共有フレームワークから削除されたアセンブリ'
description: ASP.NET Core 6.0 の破壊的変更について説明します。Microsoft.AspNetCore.App 共有フレームワークから一部のアセンブリが削除されました。
ms.date: 04/02/2021
ms.openlocfilehash: e6a0aa97dd97eae2cdc5aa8ae64e277840d6a083
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255260"
---
# <a name="assemblies-removed-from-microsoftaspnetcoreapp-shared-framework"></a>Microsoft.AspNetCore.App 共有フレームワークから削除されたアセンブリ

次の 2 つのアセンブリが ASP.NET Core ターゲット パックから削除されました。

- System.Security.Permissions
- System.Windows.Extensions

さらに、次のアセンブリが ASP.NET Core ランタイム パックから削除されました。

- Microsoft.Win32.SystemEvents
- System.Drawing.Common
- System.Security.Permissions
- System.Windows.Extensions

## <a name="version-introduced"></a>導入されたバージョン

ASP.NET Core 6.0

## <a name="old-behavior"></a>以前の動作

アプリケーションでは、[Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) 共有フレームワークを参照して、これらのライブラリによって提供される API を使用できました。

## <a name="new-behavior"></a>新しい動作

プロジェクト ファイルに [PackageReference](../../../project-sdk/msbuild-props.md#packagereference) を指定せずに、影響を受けるアセンブリから API を使用すると、実行時エラーが発生することがあります。 たとえば、パッケージへの明示的な参照を追加せずに、リフレクションを使用して、これらのいずれかのアセンブリから API にアクセスするアプリケーションでは、実行時エラーが発生します。 `PackageReference` により、アプリケーションの出力の一部として、アセンブリが確実に存在します。

ディスカッションについては、<https://github.com/dotnet/aspnetcore/issues/31007> を参照してください。

## <a name="reason-for-change"></a>変更理由

この変更は、ASP.NET Core 共有フレームワークのサイズを小さくするために導入されました。

## <a name="recommended-action"></a>推奨される操作

引き続きプロジェクトでこれらの API を使用するには、[PackageReference](../../../project-sdk/msbuild-props.md#packagereference) を追加します。 次に例を示します。

```xml
<PackageReference Include="System.Security.Permissions" Version="6.0.0" />
```

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Security.Permissions?displayProperty=fullName>
- <xref:System.Media?displayProperty=fullName>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2UI?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlAccessLevel?displayProperty=fullName>

<!--

## Category

ASP.NET Core

## Affected APIs

- `N:System.Security.Permissions`
- `N:System.Media`
- `N:System.Security.Cryptography.X509Certificates.X509Certificate2UI`
- `N:System.Xaml.Permissions.XamlAccessLevel`

-->
