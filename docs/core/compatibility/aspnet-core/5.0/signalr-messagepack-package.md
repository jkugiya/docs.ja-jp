---
title: '破壊的変更: SignalR:MessagePack ハブ プロトコルが MessagePack 2.x パッケージに移動された'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: SignalR:MessagePack ハブ プロトコルが MessagePack 2.x パッケージに移動された'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 6851c4fdbaab61e7655dd71ba3c21b8835b2b855
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497113"
---
# <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="ea564-103">SignalR:MessagePack ハブ プロトコルが MessagePack 2.x パッケージに移動された</span><span class="sxs-lookup"><span data-stu-id="ea564-103">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="ea564-104">ASP.NET Core SignalR [MessagePack ハブ プロトコル](/aspnet/core/signalr/messagepackhubprotocol)では、MessagePack のシリアル化に [MessagePack NuGet パッケージ](https://www.nuget.org/packages/MessagePack)が使用されています。</span><span class="sxs-lookup"><span data-stu-id="ea564-104">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="ea564-105">ASP.NET Core 5.0 では、パッケージが 1.x から最新の 2.x パッケージ バージョンにアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="ea564-105">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="ea564-106">この問題に関するディスカッションについては、[dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea564-106">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ea564-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ea564-107">Version introduced</span></span>

<span data-ttu-id="ea564-108">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="ea564-108">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="ea564-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="ea564-109">Old behavior</span></span>

<span data-ttu-id="ea564-110">ASP.NET Core SignalR では、MessagePack 1.x パッケージを使用して、MessagePack メッセージのシリアル化と逆シリアル化が行われていました。</span><span class="sxs-lookup"><span data-stu-id="ea564-110">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="ea564-111">新しい動作</span><span class="sxs-lookup"><span data-stu-id="ea564-111">New behavior</span></span>

<span data-ttu-id="ea564-112">ASP.NET Core SignalR では、MessagePack 2.x パッケージを使用して、MessagePack メッセージのシリアル化と逆シリアル化が行われます。</span><span class="sxs-lookup"><span data-stu-id="ea564-112">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ea564-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="ea564-113">Reason for change</span></span>

<span data-ttu-id="ea564-114">MessagePack 2.x パッケージの最新の機能強化により、便利な機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="ea564-114">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ea564-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="ea564-115">Recommended action</span></span>

<span data-ttu-id="ea564-116">この破壊的変更は、次の場合に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ea564-116">This breaking change applies when:</span></span>

* <span data-ttu-id="ea564-117"><xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> での値の設定または構成。</span><span class="sxs-lookup"><span data-stu-id="ea564-117">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="ea564-118">MessagePack API の直接的な使用、および同じプロジェクトでの ASP.NET Core SignalR MessagePack ハブ プロトコルの使用。</span><span class="sxs-lookup"><span data-stu-id="ea564-118">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="ea564-119">以前のバージョンの代わりに、新しいバージョンが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ea564-119">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="ea564-120">パッケージ作成者からの移行ガイダンスについては、「[MessagePack v1 から MessagePack v2.x への移行](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea564-120">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="ea564-121">メッセージのシリアル化と逆シリアル化のいくつかの側面が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="ea564-121">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="ea564-122">具体的には、[DateTime 値をシリアル化する方法の動作が変わります](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)。</span><span class="sxs-lookup"><span data-stu-id="ea564-122">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ea564-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="ea564-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
