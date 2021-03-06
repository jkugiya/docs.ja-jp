---
title: ASP.NET Identity と ASP.NET Core Id の比較
description: このセクションでは、ASP.NET Identity と ASP.NET Core Id の違いを調べます。これは、.NET Framework から .NET Core への移行を計画するときに特に重要です。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 184c0e7c872b7676530b917727f380d6735ba10a
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401378"
---
# <a name="compare-aspnet-identity-and-aspnet-core-identity"></a><span data-ttu-id="4569a-103">ASP.NET Identity と ASP.NET Core Id の比較</span><span class="sxs-lookup"><span data-stu-id="4569a-103">Compare ASP.NET Identity and ASP.NET Core Identity</span></span>

<span data-ttu-id="4569a-104">ASP.NET MVC では、通常、id 機能は、 *App_Start* フォルダーの *IdentityConfig.cs* で構成されます。</span><span class="sxs-lookup"><span data-stu-id="4569a-104">In ASP.NET MVC, identity features are typically configured in *IdentityConfig.cs* in the *App_Start* folder.</span></span> <span data-ttu-id="4569a-105">既存のアプリでこれがどのように構成されているかを確認し、 *Startup.cs* の [ASP.NET Core id に必要な構成](/aspnet/core/security/authentication/identity-configuration)と比較します。</span><span class="sxs-lookup"><span data-stu-id="4569a-105">Review how this is configured in the existing app, and compare it to the [configuration required for ASP.NET Core Identity](/aspnet/core/security/authentication/identity-configuration) in *Startup.cs*.</span></span>

<span data-ttu-id="4569a-106">ASP.NET Identity は、ユーザーインターフェイスのログイン機能をサポートし、ユーザー、パスワード、プロファイルデータ、ロール、要求、トークン、電子メールの確認などを管理する API です。</span><span class="sxs-lookup"><span data-stu-id="4569a-106">ASP.NET Identity is an API that supports user interface login functionality and manages users, passwords, profile data, roles, claims, tokens, email confirmations, and more.</span></span> <span data-ttu-id="4569a-107">Facebook、Google、Microsoft、Twitter などの外部ログインプロバイダーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4569a-107">It supports external login providers like Facebook, Google, Microsoft, and Twitter.</span></span>

<span data-ttu-id="4569a-108">ASP.NET MVC アプリで ASP.NET メンバーシップを使用している場合は、 [ASP.NET メンバーシップ認証から ASP.NET Core 2.0 id に移行](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)するためのガイドがあります。</span><span class="sxs-lookup"><span data-stu-id="4569a-108">If your ASP.NET MVC app is using ASP.NET Membership, you'll find a guide to [migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="4569a-109">これは主にデータ移行の演習です。この作業を完了すると、移行したユーザーレコードで ASP.NET Core Id を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4569a-109">This is mainly a data migration exercise, at the completion of which you should be able to use ASP.NET Core Identity with your migrated user records.</span></span>

<span data-ttu-id="4569a-110">ASP.NET Identity ユーザーを ASP.NET Core Id に移行する場合は、パスワードハッシュを更新したり、新しい ASP.NET Core Id アプローチまたは古い ASP.NET Identity アプローチでハッシュされるパスワードを追跡したりすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4569a-110">If you migrate your ASP.NET Identity users to ASP.NET Core Identity, you may need to update their password hashes, or track which passwords are hashed with the new ASP.NET Core Identity approach or the older ASP.NET Identity approach.</span></span> <span data-ttu-id="4569a-111">[Stack Overflow に記載されているこの方法](https://stackoverflow.com/a/57074910/13729) では、すべてのユーザーパスワードハッシュを一度に移行するのではなく、時間の経過と共に移行するオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="4569a-111">[This approach described on Stack Overflow](https://stackoverflow.com/a/57074910/13729) provides some options for migrating user password hashes over time, rather than all at once.</span></span>

<span data-ttu-id="4569a-112">ASP.NET Identity と比較して ASP.NET Core Id を使用する場合の最大の相違点の1つは、プロジェクトに含める必要があるコードの数が少ないことです。</span><span class="sxs-lookup"><span data-stu-id="4569a-112">One of the biggest differences when it comes to ASP.NET Core Identity compared to ASP.NET Identity is how little code you need to include in your project.</span></span> <span data-ttu-id="4569a-113">ASP.NET Core Id は Razor クラスライブラリとして出荷されるようになりました。つまり、UI とロジックはすべて NuGet パッケージから使用できます。</span><span class="sxs-lookup"><span data-stu-id="4569a-113">ASP.NET Core Identity now ships as a Razor Class Library, meaning its UI and logic are all available from a NuGet package.</span></span> <span data-ttu-id="4569a-114">[ASP.NET Core id ファイルをスキャフォールディング](/aspnet/core/security/authentication/scaffold-identity)することによって既存の UI とロジックをオーバーライドできますが、この場合でも、存在するページではなく、変更するページだけをスキャフォールディングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4569a-114">You can override the existing UI and logic by [scaffolding the ASP.NET Core Identity files](/aspnet/core/security/authentication/scaffold-identity) but even in this case you need only scaffold the pages you want to modify, not every one that exists.</span></span>

## <a name="migrate-from-owin--katana"></a><span data-ttu-id="4569a-115">OWIN/Katana からの移行</span><span class="sxs-lookup"><span data-stu-id="4569a-115">Migrate from OWIN / Katana</span></span>

<span data-ttu-id="4569a-116">次のリソースでは、OWIN/Katana からの移行に関するガイダンスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="4569a-116">The following resources offer some guidance for migrating from OWIN / Katana:</span></span>

- [<span data-ttu-id="4569a-117">移行</span><span class="sxs-lookup"><span data-stu-id="4569a-117">Migration</span></span>](/aspnet/core/migration/proper-to-2x/#globalasax-file-replacement)
- [<span data-ttu-id="4569a-118">Katana を ASPNET 5 に</span><span class="sxs-lookup"><span data-stu-id="4569a-118">Katana to ASPNET 5</span></span>](https://devblogs.microsoft.com/aspnet/katana-asp-net-5-and-bridging-the-gap/)

## <a name="references"></a><span data-ttu-id="4569a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4569a-119">References</span></span>

- [<span data-ttu-id="4569a-120">認証と Id を ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="4569a-120">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/core/migration/identity)
- [<span data-ttu-id="4569a-121">ASP.NET Core での Id の概要</span><span class="sxs-lookup"><span data-stu-id="4569a-121">Introduction to Identity on ASP.NET Core</span></span>](/aspnet/core/security/authorization/introduction)
- [<span data-ttu-id="4569a-122">ASP.NET Core Id の構成</span><span class="sxs-lookup"><span data-stu-id="4569a-122">Configure ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity-configuration)
- [<span data-ttu-id="4569a-123">ASP.NET Core プロジェクト内のスキャフォールディング Id</span><span class="sxs-lookup"><span data-stu-id="4569a-123">Scaffold Identity in ASP.NET Core projects</span></span>](/aspnet/core/security/authentication/scaffold-identity)

>[!div class="step-by-step"]
><span data-ttu-id="4569a-124">[前へ](authentication-differences.md)
>[次へ](controller-differences.md)</span><span class="sxs-lookup"><span data-stu-id="4569a-124">[Previous](authentication-differences.md)
[Next](controller-differences.md)</span></span>
