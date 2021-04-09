---
title: '破壊的変更:Kestrel: 非推奨としてマークされている Libuv トランスポート'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Kestrel: 非推奨としてマークされている Libuv トランスポート'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7edec666df729edbffe60b6017a2b8ee5f46ae67
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497633"
---
# <a name="kestrel-libuv-transport-marked-as-obsolete"></a>Kestrel:非推奨としてマークされている Libuv トランスポート

早期バージョンの ASP.NET Core では、非同期出入力方法の実装詳細として Libuv が使用されていました。 ASP.NET Core 2.0 では、代替となる <xref:System.Net.Sockets.Socket> ベースのトランスポートが開発されました。 ASP.NET Core 2.1 では、Kestrel は既定で `Socket` ベースのトランスポートを使用するように切り替えられました。 Libuv サポートは、互換性の問題で維持されました。

この時点では、`Socket` ベースのトランスポートの使用は Libuv トランスポートよりもはるかに一般的です。 結果的に、Libuv サポートは .NET 5.0 で非推奨となり、.NET 6.0 では完全に削除されます。

この変更の一環として、新しいオペレーティング システム プラットフォーム (Windows ARM64 など) の Libuv サポートが .NET 5.0 の存続中に追加されることはありません。

Libuv トランスポートを使用する必要があるブロッキング問題については、GitHub イシューをご覧ください ([dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409))。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 8

## <a name="old-behavior"></a>以前の動作

Libuv API は非推奨ではありません。

## <a name="new-behavior"></a>新しい動作

Libuv API は非推奨です。

## <a name="reason-for-change"></a>変更理由

`Socket` ベースのトランスポートが既定です。 Libuv トランスポートの使用を続けることについて説得力のある理由がありません。

## <a name="recommended-action"></a>推奨アクション

[Libuv パッケージ](https://www.nuget.org/packages/Libuv)と拡張メソッドの使用を止める。

## <a name="affected-apis"></a>影響を受ける API

- [WebHostBuilderLibuvExtensions](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [WebHostBuilderLibuvExtensions.UseLibuv](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
