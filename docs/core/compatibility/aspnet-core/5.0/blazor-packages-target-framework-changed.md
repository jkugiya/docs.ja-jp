---
title: '破壊的変更:Blazor: NuGet パッケージのターゲット フレームワークを変更'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:NuGet パッケージのターゲット フレームワークを変更'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 02945c223410860c9336b6046afe54cacce878dd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498192"
---
# <a name="blazor-target-framework-of-nuget-packages-changed"></a>Blazor: NuGet パッケージのターゲット フレームワークを変更

Blazor 3.2 WebAssembly プロジェクトは、.NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`) をターゲットにするようコンパイルされていました。 ASP.NET Core 5.0 では、Blazor Server と Blazor WebAssembly プロジェクトの両方で .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`) がターゲットとされます。 ターゲット フレームワークの変更に対応するため、次の Blazor パッケージで .NET Standard 2.1 がターゲットとされることはなくなりました。

* [Microsoft.AspNetCore.Components](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [Microsoft.AspNetCore.Components.Authorization](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [Microsoft.AspNetCore.Components.Forms](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [Microsoft.AspNetCore.Components.Web](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [Microsoft.AspNetCore.Components.WebAssembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [Microsoft.AspNetCore.Components.WebAssembly.Authentication](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSInterop](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop.WebAssembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [Microsoft.Authentication.WebAssembly.Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 7

## <a name="old-behavior"></a>以前の動作

Blazor 3.1 および 3.2 では、.NET Standard 2.1 and .NET Core 3.1 がパッケージによりターゲットとされます。

## <a name="new-behavior"></a>新しい動作

ASP.NET Core 5.0 では、.NET 5.0 がパッケージによりターゲットとされます。

## <a name="reason-for-change"></a>変更理由

.NET ターゲット フレームワークの要件に対応するために変更が行われました。

## <a name="recommended-action"></a>推奨アクション

Blazor 3.2 WebAssembly のプロジェクトは、パッケージ参照の 5.x.x への更新の一環として、.NET 5.0 をターゲットとする必要があります。 これらのパッケージのいずれかを参照するライブラリでは、要件に応じて、.NET 5.0 をターゲットとするか、またはマルチターゲットとすることができます。

## <a name="affected-apis"></a>影響を受ける API

なし

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
