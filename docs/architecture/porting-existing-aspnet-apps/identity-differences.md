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
# <a name="compare-aspnet-identity-and-aspnet-core-identity"></a>ASP.NET Identity と ASP.NET Core Id の比較

ASP.NET MVC では、通常、id 機能は、 *App_Start* フォルダーの *IdentityConfig.cs* で構成されます。 既存のアプリでこれがどのように構成されているかを確認し、 *Startup.cs* の [ASP.NET Core id に必要な構成](/aspnet/core/security/authentication/identity-configuration)と比較します。

ASP.NET Identity は、ユーザーインターフェイスのログイン機能をサポートし、ユーザー、パスワード、プロファイルデータ、ロール、要求、トークン、電子メールの確認などを管理する API です。 Facebook、Google、Microsoft、Twitter などの外部ログインプロバイダーをサポートしています。

ASP.NET MVC アプリで ASP.NET メンバーシップを使用している場合は、 [ASP.NET メンバーシップ認証から ASP.NET Core 2.0 id に移行](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)するためのガイドがあります。 これは主にデータ移行の演習です。この作業を完了すると、移行したユーザーレコードで ASP.NET Core Id を使用できるようになります。

ASP.NET Identity ユーザーを ASP.NET Core Id に移行する場合は、パスワードハッシュを更新したり、新しい ASP.NET Core Id アプローチまたは古い ASP.NET Identity アプローチでハッシュされるパスワードを追跡したりすることが必要になる場合があります。 [Stack Overflow に記載されているこの方法](https://stackoverflow.com/a/57074910/13729) では、すべてのユーザーパスワードハッシュを一度に移行するのではなく、時間の経過と共に移行するオプションを提供します。

ASP.NET Identity と比較して ASP.NET Core Id を使用する場合の最大の相違点の1つは、プロジェクトに含める必要があるコードの数が少ないことです。 ASP.NET Core Id は Razor クラスライブラリとして出荷されるようになりました。つまり、UI とロジックはすべて NuGet パッケージから使用できます。 [ASP.NET Core id ファイルをスキャフォールディング](/aspnet/core/security/authentication/scaffold-identity)することによって既存の UI とロジックをオーバーライドできますが、この場合でも、存在するページではなく、変更するページだけをスキャフォールディングする必要があります。

## <a name="migrate-from-owin--katana"></a>OWIN/Katana からの移行

次のリソースでは、OWIN/Katana からの移行に関するガイダンスを提供しています。

- [移行](/aspnet/core/migration/proper-to-2x/#globalasax-file-replacement)
- [Katana を ASPNET 5 に](https://devblogs.microsoft.com/aspnet/katana-asp-net-5-and-bridging-the-gap/)

## <a name="references"></a>関連項目

- [認証と Id を ASP.NET Core に移行する](/aspnet/core/migration/identity)
- [ASP.NET Core での Id の概要](/aspnet/core/security/authorization/introduction)
- [ASP.NET Core Id の構成](/aspnet/core/security/authentication/identity-configuration)
- [ASP.NET Core プロジェクト内のスキャフォールディング Id](/aspnet/core/security/authentication/scaffold-identity)

>[!div class="step-by-step"]
>[前へ](authentication-differences.md)
>[次へ](controller-differences.md)
