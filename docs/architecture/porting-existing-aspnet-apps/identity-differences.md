---
title: Compare ASP.NET Identity と ASP.NET Core Identity の比較
description: このセクションでは、ASP.NET Identity と ASP.NET Core Identity の相違点について説明します。これは、.NET Framework から .NET Core への移行を計画するときに特に重要です。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 184c0e7c872b7676530b917727f380d6735ba10a
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401378"
---
# <a name="compare-aspnet-identity-and-aspnet-core-identity"></a><span data-ttu-id="305b1-103">Compare ASP.NET Identity と ASP.NET Core Identity の比較</span><span class="sxs-lookup"><span data-stu-id="305b1-103">Compare ASP.NET Identity and ASP.NET Core Identity</span></span>

<span data-ttu-id="305b1-104">ASP.NET MVC では、通常、ID 機能は *App_Start* フォルダーにある *IdentityConfig.cs* 内で構成されます。</span><span class="sxs-lookup"><span data-stu-id="305b1-104">In ASP.NET MVC, identity features are typically configured in *IdentityConfig.cs* in the *App_Start* folder.</span></span> <span data-ttu-id="305b1-105">既存のアプリでこの構成を確認し、*Startup.cs* での [ASP.NET Core Identity に必要な構成](/aspnet/core/security/authentication/identity-configuration)と比較します。</span><span class="sxs-lookup"><span data-stu-id="305b1-105">Review how this is configured in the existing app, and compare it to the [configuration required for ASP.NET Core Identity](/aspnet/core/security/authentication/identity-configuration) in *Startup.cs*.</span></span>

<span data-ttu-id="305b1-106">ASP.NET Identity は、ユーザー インターフェイスのログイン機能をサポートし、ユーザー、パスワード、プロファイル データ、ロール、クレーム、トークン、電子メールの確認などを管理する API です。</span><span class="sxs-lookup"><span data-stu-id="305b1-106">ASP.NET Identity is an API that supports user interface login functionality and manages users, passwords, profile data, roles, claims, tokens, email confirmations, and more.</span></span> <span data-ttu-id="305b1-107">Facebook、Google、Microsoft、Twitter などの外部ログイン プロバイダーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="305b1-107">It supports external login providers like Facebook, Google, Microsoft, and Twitter.</span></span>

<span data-ttu-id="305b1-108">ASP.NET MVC アプリで ASP.NET メンバーシップを使用している場合は、[ASP.NET メンバーシップ認証から ASP.NET Core 2.0 Identity への移行](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)に関するガイドがあります。</span><span class="sxs-lookup"><span data-stu-id="305b1-108">If your ASP.NET MVC app is using ASP.NET Membership, you'll find a guide to [migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="305b1-109">これは主にデータ移行の演習であり、完了すると、移行したユーザー レコードで ASP.NET Core Identity を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="305b1-109">This is mainly a data migration exercise, at the completion of which you should be able to use ASP.NET Core Identity with your migrated user records.</span></span>

<span data-ttu-id="305b1-110">ASP.NET Identity ユーザーを ASP.NET Core Identity に移行する場合は、そのパスワード ハッシュを更新したり、新しい ASP.NET Core Identity アプローチまたは以前の ASP.NET Identity アプローチでハッシュされるパスワードを追跡したりすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="305b1-110">If you migrate your ASP.NET Identity users to ASP.NET Core Identity, you may need to update their password hashes, or track which passwords are hashed with the new ASP.NET Core Identity approach or the older ASP.NET Identity approach.</span></span> <span data-ttu-id="305b1-111">[Stack Overflow で説明されているこのアプローチ](https://stackoverflow.com/a/57074910/13729)には、ユーザーのパスワード ハッシュをすべて一度に移行するのではなく時間をかけて移行するためのオプションがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="305b1-111">[This approach described on Stack Overflow](https://stackoverflow.com/a/57074910/13729) provides some options for migrating user password hashes over time, rather than all at once.</span></span>

<span data-ttu-id="305b1-112">ASP.NET Core Identity を ASP.NET Identity と比較したときの最大の違いの 1 つは、プロジェクトに含める必要があるコードの少なさです。</span><span class="sxs-lookup"><span data-stu-id="305b1-112">One of the biggest differences when it comes to ASP.NET Core Identity compared to ASP.NET Identity is how little code you need to include in your project.</span></span> <span data-ttu-id="305b1-113">ASP.NET Core Identity は、Razor クラス ライブラリとして出荷されるようになりました。これはつまり、その UI とロジックをすべて NuGet パッケージから利用できるということです。</span><span class="sxs-lookup"><span data-stu-id="305b1-113">ASP.NET Core Identity now ships as a Razor Class Library, meaning its UI and logic are all available from a NuGet package.</span></span> <span data-ttu-id="305b1-114">[ASP.NET Core Identity のファイルをスキャフォールディングする](/aspnet/core/security/authentication/scaffold-identity)ことによって既存の UI とロジックをオーバーライドできますが、その場合でも、存在するすべてのページではなく、変更したいページのみをスキャフォールディングするだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="305b1-114">You can override the existing UI and logic by [scaffolding the ASP.NET Core Identity files](/aspnet/core/security/authentication/scaffold-identity) but even in this case you need only scaffold the pages you want to modify, not every one that exists.</span></span>

## <a name="migrate-from-owin--katana"></a><span data-ttu-id="305b1-115">OWIN / Katana からの移行</span><span class="sxs-lookup"><span data-stu-id="305b1-115">Migrate from OWIN / Katana</span></span>

<span data-ttu-id="305b1-116">OWIN / Katana からの移行に関しては、以下のリソースをガイダンスとして利用できます。</span><span class="sxs-lookup"><span data-stu-id="305b1-116">The following resources offer some guidance for migrating from OWIN / Katana:</span></span>

- [<span data-ttu-id="305b1-117">移行</span><span class="sxs-lookup"><span data-stu-id="305b1-117">Migration</span></span>](/aspnet/core/migration/proper-to-2x/#globalasax-file-replacement)
- [<span data-ttu-id="305b1-118">Katana から ASPNET 5 へ</span><span class="sxs-lookup"><span data-stu-id="305b1-118">Katana to ASPNET 5</span></span>](https://devblogs.microsoft.com/aspnet/katana-asp-net-5-and-bridging-the-gap/)

## <a name="references"></a><span data-ttu-id="305b1-119">リファレンス</span><span class="sxs-lookup"><span data-stu-id="305b1-119">References</span></span>

- [<span data-ttu-id="305b1-120">ASP.NET Core への認証と ID の移行</span><span class="sxs-lookup"><span data-stu-id="305b1-120">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/core/migration/identity)
- [<span data-ttu-id="305b1-121">ASP.NET Core の ID の概要</span><span class="sxs-lookup"><span data-stu-id="305b1-121">Introduction to Identity on ASP.NET Core</span></span>](/aspnet/core/security/authorization/introduction)
- [<span data-ttu-id="305b1-122">ASP.NET Core Identity を構成する</span><span class="sxs-lookup"><span data-stu-id="305b1-122">Configure ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity-configuration)
- [<span data-ttu-id="305b1-123">ASP.NET Core プロジェクトでの ID のスキャフォールディング</span><span class="sxs-lookup"><span data-stu-id="305b1-123">Scaffold Identity in ASP.NET Core projects</span></span>](/aspnet/core/security/authentication/scaffold-identity)

>[!div class="step-by-step"]
><span data-ttu-id="305b1-124">[前へ](authentication-differences.md)
>[次へ](controller-differences.md)</span><span class="sxs-lookup"><span data-stu-id="305b1-124">[Previous](authentication-differences.md)
[Next](controller-differences.md)</span></span>
