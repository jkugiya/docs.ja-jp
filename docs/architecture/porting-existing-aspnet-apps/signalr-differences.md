---
title: ASP.NET SignalR と ASP.NET Core SignalR を比較する
description: ASP.NET Core SignalR と先行する ASP.NET SignalR との違い
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 89236bd0272c8f20cf9838dddefeb9afee1f3d93
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401348"
---
# <a name="compare-aspnet-signalr-and-aspnet-core-signalr"></a>ASP.NET SignalR と ASP.NET Core SignalR を比較する

SignalR は、ASP.NET SignalR を使用しているクライアントまたはサーバーと互換性がありません。 ASP.NET Core ASP.NET Core SignalR を使用するには、クライアントとサーバーの両方を更新する必要があります。 このセクションでは、いくつかの違いについて説明しますが、完全な一覧については、 [ドキュメント](/aspnet/core/signalr/version-differences)を参照してください。ASP.NET Core SignalR には .NET Core 2.1 以上が必要です。

## <a name="feature-differences"></a>機能の違い

- ASP.NET SignalR は、切断された接続の再接続を自動的に試みます。この動作は ASP.NET Core SignalR クライアントにオプトインされています。
- どちらのフレームワークも JSON をサポートしています。また、ASP.NET Core SignalR は MessagePack に基づくバイナリプロトコルもサポートしており、カスタムプロトコルを作成することもできます。
- ASP.NET SignalR でサポートされている無期限のフレームトランスポートは、ASP.NET Core SignalR ではサポートされていません。
- ASP.NET Core SignalR は、とにそれぞれとを追加することによって構成する必要があり `services.AddSignalR()` `app.UseEndpoints` `Startup.ConfigureServices` `Startup.Configure` ます。
- ASP.NET Core SignalR には固定セッションが必要です。ASP.NET SignalR ません。
- ASP.NET Core により、接続モデルが単純化されます。接続は1つのハブに対してのみ行われます。
- ASP.NET Core SignalR は、ハブからクライアントへのデータのストリーミングをサポートしています。
- ASP.NET Core SignalR は、クライアントとハブ間の状態の受け渡しをサポートしていません。
- `PersistentConnection`クラスは ASP.NET Core SignalR に存在しません。
- ASP.NET SignalR は SQL Server と Redis をサポートしています。 ASP.NET Core SignalR は、 [Azure SignalR](/azure/azure-signalr/) と Redis をサポートしています。

## <a name="references"></a>関連項目

- [ASP.NET SignalR と ASP.NET Core SignalR の違い](/aspnet/core/signalr/version-differences)
- [Azure SignalR Service](/azure/azure-signalr/)

>[!div class="step-by-step"]
>[前へ](razor-differences.md)
>[次へ](testing-differences.md)
