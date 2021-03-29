---
title: Alpine に .NET をインストールする - .NET
description: Alpine に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: ece9a253cc11195c67e79c89747efe462a71632d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873758"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="3ae15-103">Alpine に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="3ae15-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="3ae15-104">この記事では、Alpine に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ae15-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="3ae15-105">Alpine のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="3ae15-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="3ae15-106">ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="3ae15-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a><span data-ttu-id="3ae15-107">[インストール]</span><span class="sxs-lookup"><span data-stu-id="3ae15-107">Install</span></span>

<span data-ttu-id="3ae15-108">Alpine Linux 用に使用できるインストーラーはありません。</span><span class="sxs-lookup"><span data-stu-id="3ae15-108">Installers aren't available for Alpine Linux.</span></span> <span data-ttu-id="3ae15-109">次のいずれかの方法で .NET をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ae15-109">You must install .NET in one of the following ways:</span></span>

- [<span data-ttu-id="3ae15-110">Snap パッケージ</span><span class="sxs-lookup"><span data-stu-id="3ae15-110">Snap package</span></span>](linux-snap.md)
- [<span data-ttu-id="3ae15-111">_install-dotnet.sh_ でスクリプト化されたインストール</span><span class="sxs-lookup"><span data-stu-id="3ae15-111">Scripted install with _install-dotnet.sh_</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="3ae15-112">手動によるバイナリ抽出</span><span class="sxs-lookup"><span data-stu-id="3ae15-112">Manual binary extraction</span></span>](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a><span data-ttu-id="3ae15-113">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="3ae15-113">Supported distributions</span></span>

<span data-ttu-id="3ae15-114">次の表に、現在サポートされている .NET リリースと、それらがサポートされている Alpine のバージョンの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="3ae15-114">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="3ae15-115">これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Alpine のバージョンの有効期限が切れるまで](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)サポートされます。</span><span class="sxs-lookup"><span data-stu-id="3ae15-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="3ae15-116">✔️ は、Alpine または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="3ae15-116">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="3ae15-117">❌ は、Alpine または .NET のバージョンがその Alpine のリリースではサポートされないことを示します。</span><span class="sxs-lookup"><span data-stu-id="3ae15-117">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="3ae15-118">Alpine のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3ae15-118">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="3ae15-119">Alpine</span><span class="sxs-lookup"><span data-stu-id="3ae15-119">Alpine</span></span>  | <span data-ttu-id="3ae15-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-120">.NET Core 2.1</span></span> | <span data-ttu-id="3ae15-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-121">.NET Core 3.1</span></span> | <span data-ttu-id="3ae15-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-122">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="3ae15-123">✔️ 3.13</span><span class="sxs-lookup"><span data-stu-id="3ae15-123">✔️ 3.13</span></span> | <span data-ttu-id="3ae15-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-124">✔️ 2.1</span></span>        | <span data-ttu-id="3ae15-125">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-125">✔️ 3.1</span></span>        | <span data-ttu-id="3ae15-126">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-126">✔️ 5.0</span></span> |
| <span data-ttu-id="3ae15-127">✔️ 3.12</span><span class="sxs-lookup"><span data-stu-id="3ae15-127">✔️ 3.12</span></span> | <span data-ttu-id="3ae15-128">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-128">✔️ 2.1</span></span>        | <span data-ttu-id="3ae15-129">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-129">✔️ 3.1</span></span>        | <span data-ttu-id="3ae15-130">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-130">✔️ 5.0</span></span> |
| <span data-ttu-id="3ae15-131">✔️ 3.11</span><span class="sxs-lookup"><span data-stu-id="3ae15-131">✔️ 3.11</span></span> | <span data-ttu-id="3ae15-132">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-132">✔️ 2.1</span></span>        | <span data-ttu-id="3ae15-133">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-133">✔️ 3.1</span></span>        | <span data-ttu-id="3ae15-134">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-134">✔️ 5.0</span></span> |
| <span data-ttu-id="3ae15-135">✔️ 3.10</span><span class="sxs-lookup"><span data-stu-id="3ae15-135">✔️ 3.10</span></span> | <span data-ttu-id="3ae15-136">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-136">✔️ 2.1</span></span>        | <span data-ttu-id="3ae15-137">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-137">✔️ 3.1</span></span>        | <span data-ttu-id="3ae15-138">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-138">❌ 5.0</span></span> |
| <span data-ttu-id="3ae15-139">❌ 3.9</span><span class="sxs-lookup"><span data-stu-id="3ae15-139">❌ 3.9</span></span>  | <span data-ttu-id="3ae15-140">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-140">✔️ 2.1</span></span>        | <span data-ttu-id="3ae15-141">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-141">✔️ 3.1</span></span>        | <span data-ttu-id="3ae15-142">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-142">❌ 5.0</span></span> |
| <span data-ttu-id="3ae15-143">❌ 3.8</span><span class="sxs-lookup"><span data-stu-id="3ae15-143">❌ 3.8</span></span>  | <span data-ttu-id="3ae15-144">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-144">✔️ 2.1</span></span>        | <span data-ttu-id="3ae15-145">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="3ae15-145">✔️ 3.1</span></span>        | <span data-ttu-id="3ae15-146">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-146">❌ 5.0</span></span> |

<span data-ttu-id="3ae15-147">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="3ae15-147">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="3ae15-148">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="3ae15-148">The downloads for these still remain published:</span></span>

- <span data-ttu-id="3ae15-149">3.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-149">3.0</span></span>
- <span data-ttu-id="3ae15-150">2.2</span><span class="sxs-lookup"><span data-stu-id="3ae15-150">2.2</span></span>
- <span data-ttu-id="3ae15-151">2.0</span><span class="sxs-lookup"><span data-stu-id="3ae15-151">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="3ae15-152">依存関係</span><span class="sxs-lookup"><span data-stu-id="3ae15-152">Dependencies</span></span>

<span data-ttu-id="3ae15-153">Alpine Linux 上の .NET には、次の依存関係がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ae15-153">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="3ae15-154">Bash</span><span class="sxs-lookup"><span data-stu-id="3ae15-154">bash</span></span>
- <span data-ttu-id="3ae15-155">icu-libs</span><span class="sxs-lookup"><span data-stu-id="3ae15-155">icu-libs</span></span>
- <span data-ttu-id="3ae15-156">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="3ae15-156">krb5-libs</span></span>
- <span data-ttu-id="3ae15-157">libgcc</span><span class="sxs-lookup"><span data-stu-id="3ae15-157">libgcc</span></span>
- <span data-ttu-id="3ae15-158">libgdiplus (.NET アプリで *System.Drawing.Common* アセンブリが必要な場合)</span><span class="sxs-lookup"><span data-stu-id="3ae15-158">libgdiplus (if the .NET app requires the *System.Drawing.Common* assembly)</span></span>
- <span data-ttu-id="3ae15-159">libintl</span><span class="sxs-lookup"><span data-stu-id="3ae15-159">libintl</span></span>
- <span data-ttu-id="3ae15-160">libssl1.1 (Alpine v3.9 以上)</span><span class="sxs-lookup"><span data-stu-id="3ae15-160">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="3ae15-161">libssl1.0 (Alpine v3.8 以下)</span><span class="sxs-lookup"><span data-stu-id="3ae15-161">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="3ae15-162">libstdc++</span><span class="sxs-lookup"><span data-stu-id="3ae15-162">libstdc++</span></span>
- <span data-ttu-id="3ae15-163">zlib</span><span class="sxs-lookup"><span data-stu-id="3ae15-163">zlib</span></span>

<span data-ttu-id="3ae15-164">必要な要件をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3ae15-164">To install the needed requirements, run the following command:</span></span>

```bash
apk add bash icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib
```

<span data-ttu-id="3ae15-165">**libgdiplus** をインストールするには、次のようにリポジトリを指定する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="3ae15-165">To install **libgdiplus**, you may need to specify a repository:</span></span>

```bash
apk add libgdiplus --repository https://dl-3.alpinelinux.org/alpine/edge/testing/
```

## <a name="next-steps"></a><span data-ttu-id="3ae15-166">次のステップ</span><span class="sxs-lookup"><span data-stu-id="3ae15-166">Next steps</span></span>

- [<span data-ttu-id="3ae15-167">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="3ae15-167">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="3ae15-168">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="3ae15-168">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
