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
# <a name="compare-aspnet-signalr-and-aspnet-core-signalr"></a><span data-ttu-id="961bd-103">ASP.NET SignalR と ASP.NET Core SignalR を比較する</span><span class="sxs-lookup"><span data-stu-id="961bd-103">Compare ASP.NET SignalR and ASP.NET Core SignalR</span></span>

<span data-ttu-id="961bd-104">SignalR は、ASP.NET SignalR を使用しているクライアントまたはサーバーと互換性がありません。 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="961bd-104">ASP.NET Core SignalR is incompatible with clients or servers using ASP.NET SignalR.</span></span> <span data-ttu-id="961bd-105">ASP.NET Core SignalR を使用するには、クライアントとサーバーの両方を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="961bd-105">You'll need to update both clients and server to use ASP.NET Core SignalR.</span></span> <span data-ttu-id="961bd-106">このセクションでは、いくつかの違いについて説明しますが、完全な一覧については、 [ドキュメント](/aspnet/core/signalr/version-differences)を参照してください。ASP.NET Core SignalR には .NET Core 2.1 以上が必要です。</span><span class="sxs-lookup"><span data-stu-id="961bd-106">Some differences are described in this section, while the full list is available in the [docs](/aspnet/core/signalr/version-differences). ASP.NET Core SignalR requires .NET Core 2.1 or greater.</span></span>

## <a name="feature-differences"></a><span data-ttu-id="961bd-107">機能の違い</span><span class="sxs-lookup"><span data-stu-id="961bd-107">Feature differences</span></span>

- <span data-ttu-id="961bd-108">ASP.NET SignalR は、切断された接続の再接続を自動的に試みます。この動作は ASP.NET Core SignalR クライアントにオプトインされています。</span><span class="sxs-lookup"><span data-stu-id="961bd-108">ASP.NET SignalR automatically attempts to reconnect dropped connections; this behavior is opt-in for ASP.NET Core SignalR clients</span></span>
- <span data-ttu-id="961bd-109">どちらのフレームワークも JSON をサポートしています。また、ASP.NET Core SignalR は MessagePack に基づくバイナリプロトコルもサポートしており、カスタムプロトコルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="961bd-109">Both frameworks support JSON; ASP.NET Core SignalR also supports a binary protocol based on MessagePack, and custom protocols can be created.</span></span>
- <span data-ttu-id="961bd-110">ASP.NET SignalR でサポートされている無期限のフレームトランスポートは、ASP.NET Core SignalR ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="961bd-110">The Forever Frame transport, supported by ASP.NET SignalR, isn't supported in ASP.NET Core SignalR.</span></span>
- <span data-ttu-id="961bd-111">ASP.NET Core SignalR は、とにそれぞれとを追加することによって構成する必要があり `services.AddSignalR()` `app.UseEndpoints` `Startup.ConfigureServices` `Startup.Configure` ます。</span><span class="sxs-lookup"><span data-stu-id="961bd-111">ASP.NET Core SignalR must be configured by adding `services.AddSignalR()` and `app.UseEndpoints` in `Startup.ConfigureServices` and `Startup.Configure`, respectively.</span></span>
- <span data-ttu-id="961bd-112">ASP.NET Core SignalR には固定セッションが必要です。ASP.NET SignalR ません。</span><span class="sxs-lookup"><span data-stu-id="961bd-112">ASP.NET Core SignalR requires sticky sessions; ASP.NET SignalR doesn't.</span></span>
- <span data-ttu-id="961bd-113">ASP.NET Core により、接続モデルが単純化されます。接続は1つのハブに対してのみ行われます。</span><span class="sxs-lookup"><span data-stu-id="961bd-113">ASP.NET Core simplifies the connection model; connections are only made to a single hub.</span></span>
- <span data-ttu-id="961bd-114">ASP.NET Core SignalR は、ハブからクライアントへのデータのストリーミングをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="961bd-114">ASP.NET Core SignalR supports streaming data from the hub to the client.</span></span>
- <span data-ttu-id="961bd-115">ASP.NET Core SignalR は、クライアントとハブ間の状態の受け渡しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="961bd-115">ASP.NET Core SignalR doesn't support passing state between clients and the hub.</span></span>
- <span data-ttu-id="961bd-116">`PersistentConnection`クラスは ASP.NET Core SignalR に存在しません。</span><span class="sxs-lookup"><span data-stu-id="961bd-116">The `PersistentConnection` class doesn't exist in ASP.NET Core SignalR.</span></span>
- <span data-ttu-id="961bd-117">ASP.NET SignalR は SQL Server と Redis をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="961bd-117">ASP.NET SignalR supports SQL Server and Redis.</span></span> <span data-ttu-id="961bd-118">ASP.NET Core SignalR は、 [Azure SignalR](/azure/azure-signalr/) と Redis をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="961bd-118">ASP.NET Core SignalR supports [Azure SignalR](/azure/azure-signalr/) and Redis.</span></span>

## <a name="references"></a><span data-ttu-id="961bd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="961bd-119">References</span></span>

- [<span data-ttu-id="961bd-120">ASP.NET SignalR と ASP.NET Core SignalR の違い</span><span class="sxs-lookup"><span data-stu-id="961bd-120">Differences between ASP.NET SignalR and ASP.NET Core SignalR</span></span>](/aspnet/core/signalr/version-differences)
- [<span data-ttu-id="961bd-121">Azure SignalR Service</span><span class="sxs-lookup"><span data-stu-id="961bd-121">Azure SignalR Service</span></span>](/azure/azure-signalr/)

>[!div class="step-by-step"]
><span data-ttu-id="961bd-122">[前へ](razor-differences.md)
>[次へ](testing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="961bd-122">[Previous](razor-differences.md)
[Next](testing-differences.md)</span></span>
