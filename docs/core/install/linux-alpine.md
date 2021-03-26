---
title: Alpine に .NET をインストールする - .NET
description: Alpine に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 19cae3c6237dc9f1a23087ec654e8f24ca13cd66
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653440"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="1b362-103">Alpine に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="1b362-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="1b362-104">この記事では、Alpine に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b362-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="1b362-105">Alpine のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="1b362-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="1b362-106">ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="1b362-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a><span data-ttu-id="1b362-107">[インストール]</span><span class="sxs-lookup"><span data-stu-id="1b362-107">Install</span></span>

<span data-ttu-id="1b362-108">Alpine Linux 用に使用できるインストーラーはありません。</span><span class="sxs-lookup"><span data-stu-id="1b362-108">Installers aren't available for Alpine Linux.</span></span> <span data-ttu-id="1b362-109">次のいずれかの方法で .NET をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b362-109">You must install .NET in one of the following ways:</span></span>

- [<span data-ttu-id="1b362-110">Snap パッケージ</span><span class="sxs-lookup"><span data-stu-id="1b362-110">Snap package</span></span>](linux-snap.md)
- [<span data-ttu-id="1b362-111">_install-dotnet.sh_ でスクリプト化されたインストール</span><span class="sxs-lookup"><span data-stu-id="1b362-111">Scripted install with _install-dotnet.sh_</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="1b362-112">手動によるバイナリ抽出</span><span class="sxs-lookup"><span data-stu-id="1b362-112">Manual binary extraction</span></span>](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a><span data-ttu-id="1b362-113">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="1b362-113">Supported distributions</span></span>

<span data-ttu-id="1b362-114">次の表に、現在サポートされている .NET リリースと、それらがサポートされている Alpine のバージョンの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="1b362-114">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="1b362-115">これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Alpine のバージョンの有効期限が切れるまで](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)サポートされます。</span><span class="sxs-lookup"><span data-stu-id="1b362-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="1b362-116">✔️ は、Alpine または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="1b362-116">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="1b362-117">❌ は、Alpine または .NET のバージョンがその Alpine のリリースではサポートされないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1b362-117">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="1b362-118">Alpine のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1b362-118">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="1b362-119">Alpine</span><span class="sxs-lookup"><span data-stu-id="1b362-119">Alpine</span></span>  | <span data-ttu-id="1b362-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1b362-120">.NET Core 2.1</span></span> | <span data-ttu-id="1b362-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1b362-121">.NET Core 3.1</span></span> | <span data-ttu-id="1b362-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1b362-122">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="1b362-123">✔️ 3.12</span><span class="sxs-lookup"><span data-stu-id="1b362-123">✔️ 3.12</span></span> | <span data-ttu-id="1b362-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="1b362-124">✔️ 2.1</span></span>        | <span data-ttu-id="1b362-125">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="1b362-125">✔️ 3.1</span></span>        | <span data-ttu-id="1b362-126">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="1b362-126">✔️ 5.0</span></span> |
| <span data-ttu-id="1b362-127">✔️ 3.11</span><span class="sxs-lookup"><span data-stu-id="1b362-127">✔️ 3.11</span></span> | <span data-ttu-id="1b362-128">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="1b362-128">✔️ 2.1</span></span>        | <span data-ttu-id="1b362-129">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="1b362-129">✔️ 3.1</span></span>        | <span data-ttu-id="1b362-130">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="1b362-130">✔️ 5.0</span></span> |
| <span data-ttu-id="1b362-131">✔️ 3.10</span><span class="sxs-lookup"><span data-stu-id="1b362-131">✔️ 3.10</span></span> | <span data-ttu-id="1b362-132">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="1b362-132">✔️ 2.1</span></span>        | <span data-ttu-id="1b362-133">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="1b362-133">✔️ 3.1</span></span>        | <span data-ttu-id="1b362-134">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="1b362-134">❌ 5.0</span></span> |
| <span data-ttu-id="1b362-135">❌ 3.9</span><span class="sxs-lookup"><span data-stu-id="1b362-135">❌ 3.9</span></span>  | <span data-ttu-id="1b362-136">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="1b362-136">✔️ 2.1</span></span>        | <span data-ttu-id="1b362-137">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="1b362-137">✔️ 3.1</span></span>        | <span data-ttu-id="1b362-138">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="1b362-138">❌ 5.0</span></span> |
| <span data-ttu-id="1b362-139">❌ 3.8</span><span class="sxs-lookup"><span data-stu-id="1b362-139">❌ 3.8</span></span>  | <span data-ttu-id="1b362-140">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="1b362-140">✔️ 2.1</span></span>        | <span data-ttu-id="1b362-141">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="1b362-141">✔️ 3.1</span></span>        | <span data-ttu-id="1b362-142">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="1b362-142">❌ 5.0</span></span> |

<span data-ttu-id="1b362-143">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="1b362-143">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="1b362-144">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="1b362-144">The downloads for these still remain published:</span></span>

- <span data-ttu-id="1b362-145">3.0</span><span class="sxs-lookup"><span data-stu-id="1b362-145">3.0</span></span>
- <span data-ttu-id="1b362-146">2.2</span><span class="sxs-lookup"><span data-stu-id="1b362-146">2.2</span></span>
- <span data-ttu-id="1b362-147">2.0</span><span class="sxs-lookup"><span data-stu-id="1b362-147">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="1b362-148">依存関係</span><span class="sxs-lookup"><span data-stu-id="1b362-148">Dependencies</span></span>

<span data-ttu-id="1b362-149">Alpine Linux 上の .NET には、次の依存関係がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b362-149">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="1b362-150">Bash</span><span class="sxs-lookup"><span data-stu-id="1b362-150">bash</span></span>
- <span data-ttu-id="1b362-151">icu-libs</span><span class="sxs-lookup"><span data-stu-id="1b362-151">icu-libs</span></span>
- <span data-ttu-id="1b362-152">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="1b362-152">krb5-libs</span></span>
- <span data-ttu-id="1b362-153">libgcc</span><span class="sxs-lookup"><span data-stu-id="1b362-153">libgcc</span></span>
- <span data-ttu-id="1b362-154">libgdiplus (.NET アプリで *System.Drawing.Common* アセンブリが必要な場合)</span><span class="sxs-lookup"><span data-stu-id="1b362-154">libgdiplus (if the .NET app requires the *System.Drawing.Common* assembly)</span></span>
- <span data-ttu-id="1b362-155">libintl</span><span class="sxs-lookup"><span data-stu-id="1b362-155">libintl</span></span>
- <span data-ttu-id="1b362-156">libssl1.1 (Alpine v3.9 以上)</span><span class="sxs-lookup"><span data-stu-id="1b362-156">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="1b362-157">libssl1.0 (Alpine v3.8 以下)</span><span class="sxs-lookup"><span data-stu-id="1b362-157">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="1b362-158">libstdc++</span><span class="sxs-lookup"><span data-stu-id="1b362-158">libstdc++</span></span>
- <span data-ttu-id="1b362-159">zlib</span><span class="sxs-lookup"><span data-stu-id="1b362-159">zlib</span></span>

<span data-ttu-id="1b362-160">必要な要件をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b362-160">To install the needed requirements, run the following command:</span></span>

```bash
apk add bash icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib
```

<span data-ttu-id="1b362-161">**libgdiplus** をインストールするには、次のようにリポジトリを指定する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="1b362-161">To install **libgdiplus**, you may need to specify a repository:</span></span>

```bash
apk add libgdiplus --repository https://dl-3.alpinelinux.org/alpine/edge/testing/
```

## <a name="next-steps"></a><span data-ttu-id="1b362-162">次の手順</span><span class="sxs-lookup"><span data-stu-id="1b362-162">Next steps</span></span>

- [<span data-ttu-id="1b362-163">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="1b362-163">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="1b362-164">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="1b362-164">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
