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
# <a name="compare-aspnet-identity-and-aspnet-core-identity"></a>Compare ASP.NET Identity と ASP.NET Core Identity の比較

ASP.NET MVC では、通常、ID 機能は *App_Start* フォルダーにある *IdentityConfig.cs* 内で構成されます。 既存のアプリでこの構成を確認し、*Startup.cs* での [ASP.NET Core Identity に必要な構成](/aspnet/core/security/authentication/identity-configuration)と比較します。

ASP.NET Identity は、ユーザー インターフェイスのログイン機能をサポートし、ユーザー、パスワード、プロファイル データ、ロール、クレーム、トークン、電子メールの確認などを管理する API です。 Facebook、Google、Microsoft、Twitter などの外部ログイン プロバイダーをサポートしています。

ASP.NET MVC アプリで ASP.NET メンバーシップを使用している場合は、[ASP.NET メンバーシップ認証から ASP.NET Core 2.0 Identity への移行](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)に関するガイドがあります。 これは主にデータ移行の演習であり、完了すると、移行したユーザー レコードで ASP.NET Core Identity を使用できるようになります。

ASP.NET Identity ユーザーを ASP.NET Core Identity に移行する場合は、そのパスワード ハッシュを更新したり、新しい ASP.NET Core Identity アプローチまたは以前の ASP.NET Identity アプローチでハッシュされるパスワードを追跡したりすることが必要になる場合があります。 [Stack Overflow で説明されているこのアプローチ](https://stackoverflow.com/a/57074910/13729)には、ユーザーのパスワード ハッシュをすべて一度に移行するのではなく時間をかけて移行するためのオプションがいくつか用意されています。

ASP.NET Core Identity を ASP.NET Identity と比較したときの最大の違いの 1 つは、プロジェクトに含める必要があるコードの少なさです。 ASP.NET Core Identity は、Razor クラス ライブラリとして出荷されるようになりました。これはつまり、その UI とロジックをすべて NuGet パッケージから利用できるということです。 [ASP.NET Core Identity のファイルをスキャフォールディングする](/aspnet/core/security/authentication/scaffold-identity)ことによって既存の UI とロジックをオーバーライドできますが、その場合でも、存在するすべてのページではなく、変更したいページのみをスキャフォールディングするだけで済みます。

## <a name="migrate-from-owin--katana"></a>OWIN / Katana からの移行

OWIN / Katana からの移行に関しては、以下のリソースをガイダンスとして利用できます。

- [移行](/aspnet/core/migration/proper-to-2x/#globalasax-file-replacement)
- [Katana から ASPNET 5 へ](https://devblogs.microsoft.com/aspnet/katana-asp-net-5-and-bridging-the-gap/)

## <a name="references"></a>リファレンス

- [ASP.NET Core への認証と ID の移行](/aspnet/core/migration/identity)
- [ASP.NET Core の ID の概要](/aspnet/core/security/authorization/introduction)
- [ASP.NET Core Identity を構成する](/aspnet/core/security/authentication/identity-configuration)
- [ASP.NET Core プロジェクトでの ID のスキャフォールディング](/aspnet/core/security/authentication/scaffold-identity)

>[!div class="step-by-step"]
>[前へ](authentication-differences.md)
>[次へ](controller-differences.md)
