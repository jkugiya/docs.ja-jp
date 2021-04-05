---
ms.openlocfilehash: b75f9ce8e878c935dcc5fd9dc292369720b895e9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105152725"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="f270f-101">HTTP:ブラウザー SameSite の変更による認証への影響</span><span class="sxs-lookup"><span data-stu-id="f270f-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="f270f-102">Chrome や Firefox などの一部のブラウザーでは、Cookie の `SameSite` の実装に破壊的変更が加えられました。</span><span class="sxs-lookup"><span data-stu-id="f270f-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="f270f-103">この変更は、OpenID Connect や WS-Federation などのリモート認証シナリオに影響します。これをオプトアウトするには、`SameSite=None` を送信します。</span><span class="sxs-lookup"><span data-stu-id="f270f-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="f270f-104">ただし、iOS 12 および一部の古いバージョンの他のブラウザーでは `SameSite=None` は中断します。</span><span class="sxs-lookup"><span data-stu-id="f270f-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="f270f-105">アプリはこれらのバージョンをスニッフィングし、`SameSite` を省略する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f270f-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="f270f-106">この問題に関するディスカッションについては、[dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f270f-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f270f-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f270f-107">Version introduced</span></span>

<span data-ttu-id="f270f-108">3.1 Preview 1</span><span class="sxs-lookup"><span data-stu-id="f270f-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f270f-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="f270f-109">Old behavior</span></span>

<span data-ttu-id="f270f-110">`SameSite` は、HTTP Cookie の 2016 ドラフト標準の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="f270f-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="f270f-111">これは、クロスサイト リクエスト フォージェリ (CSRF) を軽減することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="f270f-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="f270f-112">もともと、これは、新しいパラメーターを追加することでサーバーでオプトインされる機能として設計されました。</span><span class="sxs-lookup"><span data-stu-id="f270f-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="f270f-113">ASP.NET Core 2.0 で `SameSite` の初期サポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="f270f-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f270f-114">新しい動作</span><span class="sxs-lookup"><span data-stu-id="f270f-114">New behavior</span></span>

<span data-ttu-id="f270f-115">Google から、は下位互換性のない新しいドラフト標準が提案されました</span><span class="sxs-lookup"><span data-stu-id="f270f-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="f270f-116">この標準では、既定のモードが `Lax` に変更され、オプトアウト対象の新しいエントリ `None` が追加されています。`Lax` はほとんどのアプリの Cookie に十分です。ただし、OpenID Connect や WS-Federation ログインなどのクロスサイト シナリオは中断されます。</span><span class="sxs-lookup"><span data-stu-id="f270f-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="f270f-117">ほとんどの OAuth ログインは、要求フローの違いによって影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="f270f-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="f270f-118">新しい `None` パラメーターを使うと、以前のドラフト標準 (iOS 12 など) を実装したクライアントとの互換性の問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="f270f-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="f270f-119">Chrome 80 にこの変更が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f270f-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="f270f-120">Chrome 製品の発売タイムラインについては、「[SameSite Updates](https://www.chromium.org/updates/same-site)」(SameSite の更新) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f270f-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="f270f-121">ASP.NET Core 3.1 は、新しい `SameSite` 動作を実装するように更新されました。</span><span class="sxs-lookup"><span data-stu-id="f270f-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="f270f-122">この更新により、`SameSite=None` が出力され、`SameSite` 属性を省略する新しい値 `SameSiteMode.Unspecified` が追加されるように `SameSiteMode.None` の動作が再定義されました。</span><span class="sxs-lookup"><span data-stu-id="f270f-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="f270f-123">すべての Cookie API の既定は `Unspecified` になりましたが、Cookie を使用する一部のコンポーネントでは、OpenID Connect の相関関係や nonce Cookie など、シナリオに固有の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f270f-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="f270f-124">この分野の最近の変更については、「[HTTP:SameSite の cookie オプションの既定値が一部、None に変更されました](../../../../docs/core/compatibility/3.0.md#http-some-cookie-samesite-defaults-changed-to-none)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f270f-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](../../../../docs/core/compatibility/3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="f270f-125">ASP.NET Core 3.0 では、ほとんどの既定値が <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> から <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> に変更されました (ただし、以前の標準を使用しています)。</span><span class="sxs-lookup"><span data-stu-id="f270f-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f270f-126">変更理由</span><span class="sxs-lookup"><span data-stu-id="f270f-126">Reason for change</span></span>

<span data-ttu-id="f270f-127">既に概要を説明したように、ブラウザーと仕様が変わっています。</span><span class="sxs-lookup"><span data-stu-id="f270f-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f270f-128">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="f270f-128">Recommended action</span></span>

<span data-ttu-id="f270f-129">サードパーティ ログインなどを介してリモート サイトとやり取りするアプリは、以下を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f270f-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="f270f-130">複数のブラウザー上でこのようなシナリオをテストする。</span><span class="sxs-lookup"><span data-stu-id="f270f-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="f270f-131">「[以前のブラウザーをサポートする](#support-older-browsers)」で説明されている Cookie ポリシー ブラウザー スニッフィングの軽減策を適用します。</span><span class="sxs-lookup"><span data-stu-id="f270f-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="f270f-132">テストとブラウザー スニッフィングの手順については、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f270f-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="f270f-133">影響を受けているかどうかを判断する</span><span class="sxs-lookup"><span data-stu-id="f270f-133">Determine if you're affected</span></span>

<span data-ttu-id="f270f-134">新しい動作をオプトインできるクライアント バージョンを使用して、Web アプリをテストします。</span><span class="sxs-lookup"><span data-stu-id="f270f-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="f270f-135">Chrome、Firefox、Microsoft Edge Chromium のいずれにも、テストに使用できる新しいオプトイン機能フラグがあります。</span><span class="sxs-lookup"><span data-stu-id="f270f-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="f270f-136">パッチを適用した後、アプリが古いクライアント バージョンと互換性があることを確認します (特に Safari)。</span><span class="sxs-lookup"><span data-stu-id="f270f-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="f270f-137">詳細については、「[以前のブラウザーをサポートする](#support-older-browsers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f270f-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="f270f-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="f270f-138">Chrome</span></span>

<span data-ttu-id="f270f-139">Chrome 78 以降では、誤解を招くテスト結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f270f-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="f270f-140">これらのバージョンには一時的な軽減策が適用されており、2 分前よりも短い Cookie が許可されます。</span><span class="sxs-lookup"><span data-stu-id="f270f-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="f270f-141">適切なテスト フラグを有効にすると、Chrome 76 および 77 からはより正確な結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f270f-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="f270f-142">新しい動作をテストするには、`chrome://flags/#same-site-by-default-cookies` を有効に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="f270f-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="f270f-143">Chrome 75 以前は、新しい `None` 設定を使うと失敗すると報告されています。</span><span class="sxs-lookup"><span data-stu-id="f270f-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="f270f-144">詳細については、「[以前のブラウザーをサポートする](#support-older-browsers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f270f-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="f270f-145">Google は、以前のバージョンの Chrome を提供していません。</span><span class="sxs-lookup"><span data-stu-id="f270f-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="f270f-146">ただし、以前のバージョンの Chromium をダウンロードすることはできますが、テスト目的には十分です。</span><span class="sxs-lookup"><span data-stu-id="f270f-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="f270f-147">[Chromium のダウンロード](https://www.chromium.org/getting-involved/download-chromium)に関する記事の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="f270f-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="f270f-148">Chromium 76 Win64</span><span class="sxs-lookup"><span data-stu-id="f270f-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="f270f-149">Chromium 74 Win64</span><span class="sxs-lookup"><span data-stu-id="f270f-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="f270f-150">Safari</span><span class="sxs-lookup"><span data-stu-id="f270f-150">Safari</span></span>

<span data-ttu-id="f270f-151">Safari 12 では以前のドラフトが厳密に実装されており、Cookie に新しい `None` 値が存在すると失敗します。</span><span class="sxs-lookup"><span data-stu-id="f270f-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="f270f-152">これは、「[以前のブラウザーをサポートする](#support-older-browsers)」に示されているブラウザー スニッフィング コードを使って防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="f270f-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="f270f-153">Microsoft Authentication Library (MSAL)、Active Directory 認証ライブラリ (ADAL)、または使用している任意のライブラリを使って、Safari 12 および 13 と WebKit ベースの OS スタイルのログインをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="f270f-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="f270f-154">この問題は、基盤の OS バージョンによって変わります。</span><span class="sxs-lookup"><span data-stu-id="f270f-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="f270f-155">OSX Mojave 10.14 および iOS 12 には、新しい動作との互換性の問題があることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="f270f-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="f270f-156">OSX Catalina 10.15 または iOS 13 にアップグレードすると、問題が解決します。</span><span class="sxs-lookup"><span data-stu-id="f270f-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="f270f-157">現在、Safari には新しい仕様の動作をテストするためのオプトイン フラグがありません。</span><span class="sxs-lookup"><span data-stu-id="f270f-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="f270f-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="f270f-158">Firefox</span></span>

<span data-ttu-id="f270f-159">Firefox の新しい標準のサポートは、バージョン 68 以降で、機能フラグ `network.cookie.sameSite.laxByDefault` を指定して `about:config` ページで選択することでオプトインできます。</span><span class="sxs-lookup"><span data-stu-id="f270f-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="f270f-160">以前のバージョンの Firefox では、互換性の問題は報告されていません。</span><span class="sxs-lookup"><span data-stu-id="f270f-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="f270f-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f270f-161">Microsoft Edge</span></span>

<span data-ttu-id="f270f-162">Microsoft Edge では古い `SameSite` 標準がサポートされていますが、バージョン 44 の時点では、新しい標準との互換性の問題はありませんでした。</span><span class="sxs-lookup"><span data-stu-id="f270f-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="f270f-163">Microsoft Edge Chromium</span><span class="sxs-lookup"><span data-stu-id="f270f-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="f270f-164">機能フラグは `edge://flags/#same-site-by-default-cookies` です。</span><span class="sxs-lookup"><span data-stu-id="f270f-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="f270f-165">Microsoft Edge Chromium 78 を使ってテストした際には、互換性の問題は検出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="f270f-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="f270f-166">Electron</span><span class="sxs-lookup"><span data-stu-id="f270f-166">Electron</span></span>

<span data-ttu-id="f270f-167">Electron の複数のバージョンには、Chromium の古いバージョンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f270f-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="f270f-168">たとえば、Microsoft Teams で使用されている Electron のバージョンは Chromium 66 であり、以前の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="f270f-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="f270f-169">お使いの製品に使用されている Electron のバージョンを使って、ご自分で互換性テストを実行してください。</span><span class="sxs-lookup"><span data-stu-id="f270f-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="f270f-170">詳細については、「[以前のブラウザーをサポートする](#support-older-browsers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f270f-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="f270f-171">以前のブラウザーをサポートする</span><span class="sxs-lookup"><span data-stu-id="f270f-171">Support older browsers</span></span>

<span data-ttu-id="f270f-172">2016 `SameSite` 標準では、不明な値を `SameSite=Strict` 値として扱うことが義務付けられていました。</span><span class="sxs-lookup"><span data-stu-id="f270f-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="f270f-173">そのため、元の標準をサポートする以前のブラウザーがある場合、値が `None` の `SameSite` プロパティが表示されたときに、中断される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f270f-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="f270f-174">このような以前のブラウザーをサポートする場合、Web アプリではブラウザー スニッフィングを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f270f-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="f270f-175">`User-Agent` 要求ヘッダー値は非常に不安定であり、週単位で変わるため、ASP.NET Core ではブラウザー スニッフィングを実装していません。</span><span class="sxs-lookup"><span data-stu-id="f270f-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="f270f-176">代わりに、Cookie ポリシーの拡張ポイントを使って、`User-Agent` 固有のロジックを追加できます。</span><span class="sxs-lookup"><span data-stu-id="f270f-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="f270f-177">*Startup.cs* で、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f270f-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None)
    {
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here.
        if (/* UserAgent doesn't support new behavior */)
        {
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services)
{
    services.Configure<CookiePolicyOptions>(options =>
    {
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    });
}

public void Configure(IApplicationBuilder app)
{
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication();
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="f270f-178">オプトアウト スイッチ</span><span class="sxs-lookup"><span data-stu-id="f270f-178">Opt-out switches</span></span>

<span data-ttu-id="f270f-179">`Microsoft.AspNetCore.SuppressSameSiteNone` 互換性スイッチを使用すると、新しい ASP.NET Core Cookie の動作を一時的にオプトアウトできます。</span><span class="sxs-lookup"><span data-stu-id="f270f-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="f270f-180">プロジェクトの *runtimeconfig.template.json* ファイルに次の JSON を追加します。</span><span class="sxs-lookup"><span data-stu-id="f270f-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="f270f-181">その他のバージョン</span><span class="sxs-lookup"><span data-stu-id="f270f-181">Other Versions</span></span>

<span data-ttu-id="f270f-182">関連する `SameSite` パッチは以下に対して適用されます。</span><span class="sxs-lookup"><span data-stu-id="f270f-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="f270f-183">ASP.NET Core 2.1、2.2、および 3.0</span><span class="sxs-lookup"><span data-stu-id="f270f-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="f270f-184">`Microsoft.Owin` 4.1</span><span class="sxs-lookup"><span data-stu-id="f270f-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="f270f-185">`System.Web` (.NET Framework 4.7.2 以降の場合)</span><span class="sxs-lookup"><span data-stu-id="f270f-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="f270f-186">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="f270f-186">Category</span></span>

<span data-ttu-id="f270f-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f270f-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f270f-188">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f270f-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
