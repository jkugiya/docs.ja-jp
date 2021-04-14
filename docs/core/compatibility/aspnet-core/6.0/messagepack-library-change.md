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
# <a name="changed-messagepack-library-in-microsoftsignalr-protocol-msgpack"></a><span data-ttu-id="45f9b-103">MessagePack: ライブラリが @microsoft/signalr-protocol-msgpack で変更されました</span><span class="sxs-lookup"><span data-stu-id="45f9b-103">Changed MessagePack library in @microsoft/signalr-protocol-msgpack</span></span>

<span data-ttu-id="45f9b-104">[@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack) npm パッケージが、`msgpack5` ではなく `@msgpack/msgpack` を参照するようになりました。</span><span class="sxs-lookup"><span data-stu-id="45f9b-104">The [@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack) npm package now references `@msgpack/msgpack` instead of `msgpack5`.</span></span> <span data-ttu-id="45f9b-105">また、必要に応じて `MessagePackHubProtocol` に渡すことができるオプションも変更されています。</span><span class="sxs-lookup"><span data-stu-id="45f9b-105">Additionally, the available options that can optionally be passed into the `MessagePackHubProtocol` have changed.</span></span> <span data-ttu-id="45f9b-106">`MessagePackOptions.disableTimestampEncoding` と `MessagePackOptions.forceFloat64` のプロパティが削除され、いくつかの新しいオプションが追加されました。</span><span class="sxs-lookup"><span data-stu-id="45f9b-106">The `MessagePackOptions.disableTimestampEncoding` and `MessagePackOptions.forceFloat64` properties were removed, and some new options were added.</span></span>

<span data-ttu-id="45f9b-107">ディスカッションについては、<https://github.com/dotnet/aspnetcore/issues/30471> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45f9b-107">For discussion, see <https://github.com/dotnet/aspnetcore/issues/30471>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="45f9b-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="45f9b-108">Version introduced</span></span>

<span data-ttu-id="45f9b-109">ASP.NET Core 6.0</span><span class="sxs-lookup"><span data-stu-id="45f9b-109">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="45f9b-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="45f9b-110">Old behavior</span></span>

<span data-ttu-id="45f9b-111">以前のバージョンでは、ブラウザーで [MessagePack ハブ プロトコル](/aspnet/core/signalr/messagepackhubprotocol)を使用するために、次の 3 つのスクリプト参照を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f9b-111">In previous versions, you must include three script references to use the [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) in the browser:</span></span>

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/msgpack5/msgpack5.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

## <a name="new-behavior"></a><span data-ttu-id="45f9b-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="45f9b-112">New behavior</span></span>

<span data-ttu-id="45f9b-113">ASP.NET Core 6 以降では、ブラウザーで [MessagePack ハブ プロトコル](/aspnet/core/signalr/messagepackhubprotocol)を使用するために、次の 2 つのスクリプト参照のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="45f9b-113">Starting in ASP.NET Core 6, you only need two script references to use the [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) in the browser:</span></span>

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

<span data-ttu-id="45f9b-114">アプリで直接使用する場合は、`msgpack5` パッケージではなく、`@msgpack/msgpack` パッケージが *node_modules* ディレクトリにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="45f9b-114">Instead of the `msgpack5` package, the `@msgpack/msgpack` package is downloaded to your *node_modules* directory if you want to use it directly in your app.</span></span>

<span data-ttu-id="45f9b-115">最後に、`MessagePackOptions` に新しいプロパティが追加され、`disableTimestampEncoding` と `forceFloat64` のプロパティが削除されます。</span><span class="sxs-lookup"><span data-stu-id="45f9b-115">Finally, `MessagePackOptions` has new, additional properties, and the `disableTimestampEncoding` and `forceFloat64` properties are removed.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="45f9b-116">変更理由</span><span class="sxs-lookup"><span data-stu-id="45f9b-116">Reason for change</span></span>

<span data-ttu-id="45f9b-117">この変更により、資産サイズが削減され、パッケージを簡単に使用できるようになりました。カスタマイズもしやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="45f9b-117">This change was made to reduce asset size, make it simpler to consume the package, and add more customizability.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="45f9b-118">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="45f9b-118">Recommended action</span></span>

<span data-ttu-id="45f9b-119">以前にアプリで `msgpack5` を使用していた場合は、*package.json* ファイルにライブラリへの直接参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f9b-119">If you were previously using `msgpack5` in your app, you'll need to add a direct reference to the library in your *package.json* file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="45f9b-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="45f9b-120">Affected APIs</span></span>

<span data-ttu-id="45f9b-121">次の API が削除されました。</span><span class="sxs-lookup"><span data-stu-id="45f9b-121">The following APIs were removed:</span></span>

- `MessagePackOptions.disableTimestampEncoding`
- `MessagePackOptions.forceFloat64`

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis.

-->
