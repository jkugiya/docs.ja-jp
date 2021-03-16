---
title: 破壊的変更:NegotiateStream と SslStream によって連続した Begin 操作を許可する
description: .NET 5 での破壊的変更について学習します。セキュリティ ストリームのエラー ケースは異なる方法で処理され、BeginAuthenticateAsServer または BeginAuthenticateAsClient に対する連続した呼び出しが失敗しなくなりました。
ms.date: 10/18/2020
ms.openlocfilehash: 5c042be01873849cc154111a31fc007521508c7b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256440"
---
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="ac2b6-103">NegotiateStream と SslStream によって連続した Begin 操作を許可する</span><span class="sxs-lookup"><span data-stu-id="ac2b6-103">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="ac2b6-104">セキュリティ ストリームでのエラー ケースの処理は異なり、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` に対する連続した呼び出しが失敗しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ac2b6-104">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ac2b6-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ac2b6-105">Version introduced</span></span>

<span data-ttu-id="ac2b6-106">5.0</span><span class="sxs-lookup"><span data-stu-id="ac2b6-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="ac2b6-107">変更の説明</span><span class="sxs-lookup"><span data-stu-id="ac2b6-107">Change description</span></span>

<span data-ttu-id="ac2b6-108">以前のバージョンの .NET では、最初に `EndAuthenticateAsServer` または `EndAuthenticateAsClient` を呼び出さずに、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` を連続して呼び出すと、<xref:System.NotSupportedException> になります。</span><span class="sxs-lookup"><span data-stu-id="ac2b6-108">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="ac2b6-109">.NET 5 以降では、これらの API は <xref:System.Threading.Tasks.Task> ベースの実装によってサポートされるため、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` を連続して呼び出しても <xref:System.NotSupportedException> にはなりません。</span><span class="sxs-lookup"><span data-stu-id="ac2b6-109">Starting in .NET 5, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ac2b6-110">変更理由</span><span class="sxs-lookup"><span data-stu-id="ac2b6-110">Reason for change</span></span>

<span data-ttu-id="ac2b6-111">内部実装を非同期プログラミング モデル (APM) から <xref:System.Threading.Tasks.Task> ベースに切り替えると、パフォーマンスが向上し、コードの複雑さが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="ac2b6-111">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ac2b6-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="ac2b6-112">Recommended action</span></span>

<span data-ttu-id="ac2b6-113">開発者側では、何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ac2b6-113">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ac2b6-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="ac2b6-114">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

### Category

Networking

-->
