---
title: ASP.NET SignalR と ASP.NET Core SignalR の比較
description: ASP.NET Core SignalR は、その前身である ASP.NET SignalR とどのように異なるのでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 89236bd0272c8f20cf9838dddefeb9afee1f3d93
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401348"
---
# <a name="compare-aspnet-signalr-and-aspnet-core-signalr"></a>ASP.NET SignalR と ASP.NET Core SignalR の比較

ASP.NET Core SignalR は、ASP.NET SignalR を使用しているクライアントまたはサーバーとの互換性がありません。 ASP.NET Core SignalR を使用するには、クライアントとサーバーの両方を更新する必要があります。 このセクションでは相違点の一部について説明しますが、完全な一覧については[ドキュメント](/aspnet/core/signalr/version-differences)を参照してください。ASP.NET Core SignalR には .NET Core 2.1 以降が必要です。

## <a name="feature-differences"></a>機能の違い

- ASP.NET SignalR は、切断された接続の再接続を自動的に試みます。この動作は、ASP.NET Core SignalR クライアントに対するオプトインです。
- どちらのフレームワークでも、JSON がサポートされています。ASP.NET Core SignalR では MessagePack に基づくバイナリ プロトコルもサポートされており、カスタム プロトコルを作成することもできます。
- ASP.NET SignalR でサポートされている Forever Frame トランスポートは、ASP.NET Core SignalR ではサポートされていません。
- ASP.NET Core SignalR は、`Startup.ConfigureServices` と `Startup.Configure` 内に `services.AddSignalR()` と `app.UseEndpoints` をそれぞれ追加することで構成する必要があります。
- ASP.NET Core SignalR にはスティッキー セッションが必要ですが、ASP.NET SignalR には必要ありません。
- ASP.NET Core では接続モデルが単純化され、接続は 1 つのハブに対してのみ行われます。
- ASP.NET Core SignalR では、ハブからクライアントへのデータのストリーミングがサポートされています。
- ASP.NET Core SignalR では、クライアントとハブ間の状態の受け渡しがサポートされていません。
- ASP.NET Core SignalR には `PersistentConnection` クラスが存在しません。
- ASP.NET SignalR では SQL Server と Redis がサポートされています。 ASP.NET Core SignalR では [Azure SignalR](/azure/azure-signalr/) と Redis がサポートされています。

## <a name="references"></a>リファレンス

- [ASP.NET SignalR と ASP.NET Core SignalR の相違点](/aspnet/core/signalr/version-differences)
- [Azure SignalR Service](/azure/azure-signalr/)

>[!div class="step-by-step"]
>[前へ](razor-differences.md)
>[次へ](testing-differences.md)
