---
title: 破壊的変更:Socket.LocalEndPoint が SendToAsync を呼び出した後に更新される
description: .NET 5 での破壊的変更について学習します。SendToAsync によって、ローカル エンドポイント プロパティの値がソケットのローカル アドレスに更新されます。
ms.date: 10/18/2020
ms.openlocfilehash: 4be62f8bf6596cc3531d59f3e65eda005bff778a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256427"
---
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a>Socket.LocalEndPoint が SendToAsync を呼び出した後に更新される

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> によって、<xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> プロパティの値がソケットのローカル アドレスに更新されます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> によって、ソケット インスタンスの <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> プロパティの値が変更されることはありません。 .NET 5 以降では、<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> が正常に完了した場合、<xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> の値は暗黙的にバインドされたソケットのローカル アドレスになります。 この新しい動作は、<xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> および <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> の動作と同じです。

## <a name="reason-for-change"></a>変更理由

この変更によって、[バグが修正](https://github.com/dotnet/runtime/issues/915)され、`SendTo` バリアントとの間で動作に一貫性を持たせます。

## <a name="recommended-action"></a>推奨される操作

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> によって <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> の値が変更されないことを前提とするコードを変更します。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
