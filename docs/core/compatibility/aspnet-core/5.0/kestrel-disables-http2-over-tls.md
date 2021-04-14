---
title: '破壊的変更: Kestrel: 互換性のない Windows バージョンでの TLS 経由の HTTP/2 の無効化'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Kestrel: 互換性のない Windows バージョンでの TLS 経由の HTTP/2 の無効化'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b8bbe113b3357508b6af29fa9a4d1431f6a6acea
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498114"
---
# <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="f0fba-103">Kestrel: 互換性のない Windows バージョンでの TLS 経由の HTTP/2 の無効化</span><span class="sxs-lookup"><span data-stu-id="f0fba-103">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="f0fba-104">Windows で HTTP/2 over TLS (トランスポート層セキュリティ) を有効にするには、次の 2 つの要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0fba-104">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="f0fba-105">アプリケーション層プロトコル ネゴシエーション (ALPN) のサポート。これは、Windows 8.1 および Windows Server 2012 R2 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0fba-105">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="f0fba-106">HTTP/2 と互換性のある暗号のセット。これは、Windows 10 および Windows Server 2016 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0fba-106">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="f0fba-107">そのため、HTTP/2 over TLS が構成されている場合の Kestrel の動作は、次のように変更されました。</span><span class="sxs-lookup"><span data-stu-id="f0fba-107">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="f0fba-108">`Http1` にダウングレードし、[ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) が `Http1AndHttp2` に設定されている場合は、`Information` レベルでメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="f0fba-108">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="f0fba-109">`ListenOptions.HttpProtocols` の既定値は `Http1AndHttp2` です。</span><span class="sxs-lookup"><span data-stu-id="f0fba-109">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="f0fba-110">`ListenOptions.HttpProtocols` が `Http2` に設定されている場合は、`NotSupportedException` をスローします。</span><span class="sxs-lookup"><span data-stu-id="f0fba-110">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="f0fba-111">ディスカッションについては、イシュー [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0fba-111">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f0fba-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f0fba-112">Version introduced</span></span>

<span data-ttu-id="f0fba-113">ASP.NET Core 5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="f0fba-113">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="f0fba-114">以前の動作</span><span class="sxs-lookup"><span data-stu-id="f0fba-114">Old behavior</span></span>

<span data-ttu-id="f0fba-115">次の表には、HTTP/2 over TLS が構成されている場合の動作の概要が示されています。</span><span class="sxs-lookup"><span data-stu-id="f0fba-115">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="f0fba-116">プロトコル</span><span class="sxs-lookup"><span data-stu-id="f0fba-116">Protocols</span></span> | <span data-ttu-id="f0fba-117">Windows 7、</span><span class="sxs-lookup"><span data-stu-id="f0fba-117">Windows 7,</span></span><br /><span data-ttu-id="f0fba-118">Windows Server 2008 R2、</span><span class="sxs-lookup"><span data-stu-id="f0fba-118">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="f0fba-119">またはそれ以前</span><span class="sxs-lookup"><span data-stu-id="f0fba-119">or earlier</span></span> | <span data-ttu-id="f0fba-120">Windows 8、</span><span class="sxs-lookup"><span data-stu-id="f0fba-120">Windows 8,</span></span><br /><span data-ttu-id="f0fba-121">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f0fba-121">Windows Server 2012</span></span> | <span data-ttu-id="f0fba-122">Windows 8.1、</span><span class="sxs-lookup"><span data-stu-id="f0fba-122">Windows 8.1,</span></span><br /><span data-ttu-id="f0fba-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f0fba-123">Windows Server 2012 R2</span></span> | <span data-ttu-id="f0fba-124">Windows 10、</span><span class="sxs-lookup"><span data-stu-id="f0fba-124">Windows 10,</span></span><br /><span data-ttu-id="f0fba-125">Windows Server 2016、</span><span class="sxs-lookup"><span data-stu-id="f0fba-125">Windows Server 2016,</span></span><br /><span data-ttu-id="f0fba-126">またはそれ以降</span><span class="sxs-lookup"><span data-stu-id="f0fba-126">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="f0fba-127">`NotSupportedException` をスローする</span><span class="sxs-lookup"><span data-stu-id="f0fba-127">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="f0fba-128">TLS ハンドシェイク中にエラーが発生する</span><span class="sxs-lookup"><span data-stu-id="f0fba-128">Error during TLS handshake</span></span>     | <span data-ttu-id="f0fba-129">TLS ハンドシェイク中にエラーが発生する &ast;</span><span class="sxs-lookup"><span data-stu-id="f0fba-129">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="f0fba-130">エラーなし</span><span class="sxs-lookup"><span data-stu-id="f0fba-130">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="f0fba-131">`Http1` にダウングレードする</span><span class="sxs-lookup"><span data-stu-id="f0fba-131">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="f0fba-132">`Http1` にダウングレードする</span><span class="sxs-lookup"><span data-stu-id="f0fba-132">Downgrade to `Http1`</span></span>     | <span data-ttu-id="f0fba-133">TLS ハンドシェイク中にエラーが発生する &ast;</span><span class="sxs-lookup"><span data-stu-id="f0fba-133">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="f0fba-134">エラーなし</span><span class="sxs-lookup"><span data-stu-id="f0fba-134">No error</span></span> |

<span data-ttu-id="f0fba-135">&ast; 互換性のある暗号スイートを構成して、これらのシナリオを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f0fba-135">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="f0fba-136">新しい動作</span><span class="sxs-lookup"><span data-stu-id="f0fba-136">New behavior</span></span>

<span data-ttu-id="f0fba-137">次の表には、HTTP/2 over TLS が構成されている場合の動作の概要が示されています。</span><span class="sxs-lookup"><span data-stu-id="f0fba-137">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="f0fba-138">プロトコル</span><span class="sxs-lookup"><span data-stu-id="f0fba-138">Protocols</span></span> | <span data-ttu-id="f0fba-139">Windows 7、</span><span class="sxs-lookup"><span data-stu-id="f0fba-139">Windows 7,</span></span><br /><span data-ttu-id="f0fba-140">Windows Server 2008 R2、</span><span class="sxs-lookup"><span data-stu-id="f0fba-140">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="f0fba-141">またはそれ以前</span><span class="sxs-lookup"><span data-stu-id="f0fba-141">or earlier</span></span> | <span data-ttu-id="f0fba-142">Windows 8、</span><span class="sxs-lookup"><span data-stu-id="f0fba-142">Windows 8,</span></span><br /><span data-ttu-id="f0fba-143">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f0fba-143">Windows Server 2012</span></span> | <span data-ttu-id="f0fba-144">Windows 8.1、</span><span class="sxs-lookup"><span data-stu-id="f0fba-144">Windows 8.1,</span></span><br /><span data-ttu-id="f0fba-145">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f0fba-145">Windows Server 2012 R2</span></span> | <span data-ttu-id="f0fba-146">Windows 10、</span><span class="sxs-lookup"><span data-stu-id="f0fba-146">Windows 10,</span></span><br /><span data-ttu-id="f0fba-147">Windows Server 2016、</span><span class="sxs-lookup"><span data-stu-id="f0fba-147">Windows Server 2016,</span></span><br /><span data-ttu-id="f0fba-148">またはそれ以降</span><span class="sxs-lookup"><span data-stu-id="f0fba-148">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="f0fba-149">`NotSupportedException` をスローする</span><span class="sxs-lookup"><span data-stu-id="f0fba-149">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="f0fba-150">`NotSupportedException` をスローする</span><span class="sxs-lookup"><span data-stu-id="f0fba-150">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="f0fba-151">`NotSupportedException` をスローする &ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="f0fba-151">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="f0fba-152">エラーなし</span><span class="sxs-lookup"><span data-stu-id="f0fba-152">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="f0fba-153">`Http1` にダウングレードする</span><span class="sxs-lookup"><span data-stu-id="f0fba-153">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="f0fba-154">`Http1` にダウングレードする</span><span class="sxs-lookup"><span data-stu-id="f0fba-154">Downgrade to `Http1`</span></span>     | <span data-ttu-id="f0fba-155">`Http1` にダウングレードする &ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="f0fba-155">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="f0fba-156">エラーなし</span><span class="sxs-lookup"><span data-stu-id="f0fba-156">No error</span></span> |

<span data-ttu-id="f0fba-157">&ast;&ast; 互換性のある暗号スイートを構成し、アプリ コンテキスト スイッチ `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` を `true` に設定して、これらのシナリオを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f0fba-157">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f0fba-158">変更理由</span><span class="sxs-lookup"><span data-stu-id="f0fba-158">Reason for change</span></span>

<span data-ttu-id="f0fba-159">この変更によって、以前の Windows バージョンでの HTTP/2 TLS over TLS の互換性エラーができるだけ早い段階で明確に示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="f0fba-159">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f0fba-160">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f0fba-160">Recommended action</span></span>

<span data-ttu-id="f0fba-161">互換性のない Windows バージョンで HTTP/2 over TLS が無効になるようにします。</span><span class="sxs-lookup"><span data-stu-id="f0fba-161">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="f0fba-162">Windows 8.1 および Windows Server 2012 R2 は、既定で必要な暗号がないため、互換性はありません。</span><span class="sxs-lookup"><span data-stu-id="f0fba-162">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="f0fba-163">しかし、HTTP/2 と互換性のある暗号を使用するように、コンピューターの構成設定を更新することは可能です。</span><span class="sxs-lookup"><span data-stu-id="f0fba-163">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="f0fba-164">詳細については、「[Windows 8.1 の TLS 暗号スイート](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0fba-164">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="f0fba-165">構成が完了したら、アプリ コンテキスト スイッチ `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` を設定し、Kestrel で HTTP/2 over TLS を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0fba-165">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="f0fba-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f0fba-166">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="f0fba-167">基になるサポートは変更されていません。</span><span class="sxs-lookup"><span data-stu-id="f0fba-167">No underlying support has changed.</span></span> <span data-ttu-id="f0fba-168">たとえば、Windows 8 や Windows Server 2012 で HTTP/2 over TLS が動作したことはありません。</span><span class="sxs-lookup"><span data-stu-id="f0fba-168">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="f0fba-169">この変更により、これらのサポートされていないシナリオでのエラーの表示方法が変わります。</span><span class="sxs-lookup"><span data-stu-id="f0fba-169">This change modifies how errors in these unsupported scenarios are presented.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f0fba-170">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f0fba-170">Affected APIs</span></span>

<span data-ttu-id="f0fba-171">なし</span><span class="sxs-lookup"><span data-stu-id="f0fba-171">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
