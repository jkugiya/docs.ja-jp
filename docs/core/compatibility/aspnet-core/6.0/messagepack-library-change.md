---
title: '破壊的変更: signalr-protocol-msgpack パッケージの MessagePack ライブラリが変更されました'
description: MessagePack ライブラリが変更され、@microsoft/signalr-protocol-msgpack パッケージで 2 つのオプションが削除された ASP.NET Core 6.0 の破壊的変更について説明します。
ms.date: 04/07/2021
ms.openlocfilehash: 62f853cbed0904e278e25f231528845baac9f71d
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107260029"
---
# <a name="changed-messagepack-library-in-microsoftsignalr-protocol-msgpack"></a>MessagePack: ライブラリが @microsoft/signalr-protocol-msgpack で変更されました

[@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack) npm パッケージが、`msgpack5` ではなく `@msgpack/msgpack` を参照するようになりました。 また、必要に応じて `MessagePackHubProtocol` に渡すことができるオプションも変更されています。 `MessagePackOptions.disableTimestampEncoding` と `MessagePackOptions.forceFloat64` のプロパティが削除され、いくつかの新しいオプションが追加されました。

ディスカッションについては、<https://github.com/dotnet/aspnetcore/issues/30471> を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

ASP.NET Core 6.0

## <a name="old-behavior"></a>以前の動作

以前のバージョンでは、ブラウザーで [MessagePack ハブ プロトコル](/aspnet/core/signalr/messagepackhubprotocol)を使用するために、次の 3 つのスクリプト参照を含める必要があります。

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/msgpack5/msgpack5.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

## <a name="new-behavior"></a>新しい動作

ASP.NET Core 6 以降では、ブラウザーで [MessagePack ハブ プロトコル](/aspnet/core/signalr/messagepackhubprotocol)を使用するために、次の 2 つのスクリプト参照のみが必要です。

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

アプリで直接使用する場合は、`msgpack5` パッケージではなく、`@msgpack/msgpack` パッケージが *node_modules* ディレクトリにダウンロードされます。

最後に、`MessagePackOptions` に新しいプロパティが追加され、`disableTimestampEncoding` と `forceFloat64` のプロパティが削除されます。

## <a name="reason-for-change"></a>変更理由

この変更により、資産サイズが削減され、パッケージを簡単に使用できるようになりました。カスタマイズもしやすくなっています。

## <a name="recommended-action"></a>推奨される操作

以前にアプリで `msgpack5` を使用していた場合は、*package.json* ファイルにライブラリへの直接参照を追加する必要があります。

## <a name="affected-apis"></a>影響を受ける API

次の API が削除されました。

- `MessagePackOptions.disableTimestampEncoding`
- `MessagePackOptions.forceFloat64`

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis.

-->
