---
title: 破壊的変更:Pubternal API が削除された
description: ASP.NET Core 5.0 の破壊的変更について学習します。この変更後、一部の Pubternal ローカライズ API が削除されました。
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 35b6f80569945e54367117446ea96107d6c5199c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497669"
---
# <a name="localization-pubternal-apis-removed"></a>ローカリゼーション:"Pubternal" API の削除

ASP.NET Core のパブリック API サーフェイスをより適切に維持するために、一部の :::no-loc text="\"pubternal\""::: ローカライズ API を削除しました。 :::no-loc text="\"pubternal\""::: API には、`public` のアクセス修飾子があり、[internal](../../../../csharp/language-reference/keywords/internal.md) インテントを意味する名前空間に定義されています。

ディスカッションについては、[dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 6

## <a name="old-behavior"></a>以前の動作

次の API が `public` でした。

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- 次のいずれかのパラメーター型を取る `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` コンストラクター オーバーロード。
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a>新しい動作

変更一覧の概要は次のとおりです。

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper` が `Microsoft.Extensions.Localization.AssemblyWrapper` となり、現在 `internal` になりました。
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` が `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` となり、現在 `internal` になりました。
- 次のいずれかのパラメーター型を取る `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` コンストラクター オーバーロードは、現在 `internal` になりました。
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a>変更理由

詳細は、[aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882) で説明していますが、:::no-loc text="\"pubternal\""::: 型が `public` API サーフェイスから削除されました。 これらの変更により、その設計判断により多くのクラスを順応させることができます。 問題のクラスは、チームの内部テストの拡張ポイントを意味していました。

## <a name="recommended-action"></a>推奨アクション

可能性は低いですが、一部のアプリが意図的にまたは誤って :::no-loc text="\"pubternal\""::: 型に依存するようになっている場合があります。 この型から移行する方法については、「[新しい動作](#new-behavior)」のセクションを参照してください。

この変更の前にはパブリックとして許可されていた API が、現在では許可されなくなったシナリオを特定した場合は、[dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) にイシューを立ててください。

## <a name="affected-apis"></a>影響を受ける API

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
