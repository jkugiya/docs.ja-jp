---
title: .NET ランタイムと SDK を削除する
description: この記事では、現在インストールされている .NET ランタイムと SDK のバージョンを確認する方法と、Windows、Mac、および Linux でそれらを削除する方法について説明します。
author: adegeo
ms.author: adegeo
ms.date: 03/02/2021
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 8ef6ab531d6c3eada5226b1682f19bfe5537bfe4
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255634"
---
# <a name="how-to-remove-the-net-runtime-and-sdk"></a>.NET ランタイムと SDK を削除する方法

時間の経過に伴い、.NET ランタイムと SDK の更新バージョンをインストールした場合は、ご利用のコンピューターから古いバージョンの .NET を削除することをお勧めします。 ランタイムの古いバージョンを削除すると、共有のフレームワーク アプリケーションを実行するように選択されているランタイムが変更される可能性があります。詳細については、[.NET バージョンの選択](../versions/selection.md)に関するページを参照してください。

## <a name="should-i-remove-a-version"></a>バージョンを削除する必要はあるか

[.NET バージョン選択](../versions/selection.md)動作および更新プログラム間での .NET のランタイム互換性により、以前のバージョンを安全に削除することができます。 1\.x や 2.x などのメジャー バージョン **バンド** 内で .NET ランタイム更新プログラムは互換性があります。 さらに、.NET SDK のより新しいリリースでは、通常、互換性を保ちながら、ランタイムの前バージョンを対象とするアプリケーションをビルドする機能が維持されます。

通常、必要なのは、ご自分のアプリケーションに必須である最新の SDK および最新のパッチ バージョンのランタイムのみです。 たとえば、*project.json* ベースのアプリケーションを管理するとき、以前のバージョンの SDK またはランタイムを保持することがあります。 ご利用のアプリケーションには以前の SDK やランタイムを維持する特別な理由がない場合、以前のバージョンを安全に削除することができます。

## <a name="determine-what-is-installed"></a>インストールされている内容を確認する

ご利用のコンピューターにインストールされている SDK とランタイムのバージョンを一覧表示するのに使用できるオプションが .NET CLI に用意されています。  ご利用のコンピューターにインストールされている SDK を一覧表示するには、[`dotnet --list-sdks`](../tools/dotnet.md#options) を使用します。 ご利用のコンピューターにインストールされているランタイムを一覧表示するには、[`dotnet --list-runtimes`](../tools/dotnet.md#options) を使用します。 詳細については、[.NET が既にインストールされていることを確認する方法](how-to-detect-installed-versions.md)に関するページを参照してください。

## <a name="uninstall-net"></a>.NET をアンインストールする

::: zone pivot="os-windows"

.NET では、Windows の **[アプリと機能]** ダイアログを使用して .NET ランタイムと SDK のバージョンを削除できます。 **[アプリと機能]** ダイアログ ボックスを次の図に示します。 .NET のインストールされているバージョンをフィルタリングしたり表示したりする目的で、**core sdk** または **.net sdk** を検索できます。

![.NET を削除するための [プログラムの追加と削除]](./media/remove-runtime-sdk-versions/programs-and-features.png)

ご利用のコンピューターから削除する任意のバージョンを選択して、 **[アンインストール]** をクリックします。

::: zone-end

::: zone pivot="os-linux"

さらに Linux 上で .NET (SDK またはランタイムのいずれか) をアンインストールするオプションもあります。 .NET をアンインストールするには、.NET をインストールするときに使用したアクションをミラー化することをお勧めします。 詳細は、選択した配布方法とインストール方法によって異なります。

> [!IMPORTANT]
> Red Hat のインストールについては、[.NET 用の Red Hat 製品ドキュメント](https://access.redhat.com/documentation/en-us/net/5.0/)を参照してください。

パッケージ マネージャーを使用して .NET SDK をアップグレードする場合、それをアンインストールする必要はありません。ただし、プレビュー バージョンからアップグレードする場合は除きます。 パッケージ マネージャーの `update` または `refresh` コマンドでは、新しいバージョンが正常にインストールされると、古いバージョンが自動的に削除されます。 プレビュー バージョンがインストールされている場合は、それをアンインストールします。

パッケージ マネージャーを使用して .NET をインストールした場合は、それと同じパッケージ マネージャーを使用して .NET SDK またはランタイムをアンインストールします。 .NET インストールでは、最も一般的なパッケージ マネージャーがサポートされています。 ご利用の環境内での正確な構文については、ご利用の配布のパッケージ マネージャーのドキュメントを参照してください。

- [apt-get(8)](https://linux.die.net/man/8/apt-get) は、Ubuntu などの Debian ベースのシステムによって使用されます。
- [yum(8)](https://linux.die.net/man/8/yum) は、Fedora、CentOS、Oracle Linux 上で使用されます。
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) は、openSUSE および SUSE Linux Enterprise System (SLES) 上で使用されます。
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) は、Fedora 上で使用されます。

ほとんどの場合、パッケージを削除するコマンドは `remove` となります。

ほとんどのパッケージ マネージャーの場合、.NET SDK インストールのパッケージ名は `dotnet-sdk` であり、その後にバージョン番号が続きます。 .NET SDK のバージョン 2.1.300 およびランタイムのバージョン `2.1` 以降は、メジャーおよびマイナーのバージョン番号のみ必要です。たとえば、.NET SDK バージョン 2.1.300 は、パッケージ `dotnet-sdk-2.1` として参照できます。 以前のバージョンでは、バージョン文字列全体が必須です。たとえば、.NET SDK のバージョン 2.1.200 の場合は `dotnet-sdk-2.1.200` が必須となります。

ランタイムのみがインストールされ、SDK はインストールされていないコンピューターの場合、.NET ランタイムのパッケージ名は `dotnet-runtime-<version>` となり、ランタイム スタック全体のパッケージ名は `aspnetcore-runtime-<version>` となります。

> [!TIP]
> 2\.0 より前の .NET Core インストールでは、パッケージ マネージャーを使用して SDK をアンインストールしたとき、ホスト アプリケーションはアンインストールされませんでした。 `apt-get` を使用する場合、コマンドは次のようになります。
>
> ```bash
> apt-get remove dotnet-host
> ```
>
> `dotnet-host` にはバージョンが添えられていません。

tarball を使用してインストールした場合、.NET の削除は手動で行う必要があります。

Linux では、バージョン管理されているディレクトリを削除し、SDK とランタイムを別々に削除する必要があります。 これらのディレクトリは、Linux ディストリビューションによって異なる場合があります。 これを削除すると、SDK とランタイムがディスクから削除されます。 たとえば、1.0.1 SDK とランタイムを削除するには、次の bash コマンドを使用します。

```bash
version="1.0.1"
sudo rm -rf /usr/share/dotnet/sdk/$version
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/share/dotnet/host/fxr/$version
```

上記の表に示したように、SDK とランタイムの親ディレクトリは、`dotnet --list-sdks` コマンドおよび `dotnet --list-runtimes` コマンドからの出力に一覧表示されます。

::: zone-end

::: zone pivot="os-macos"

Mac では、バージョン管理されているディレクトリを削除し、SDK とランタイムを別々に削除する必要があります。 これを削除すると、SDK とランタイムがディスクから削除されます。 たとえば、1.0.1 SDK とランタイムを削除するには、次の bash コマンドを使用します。

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

上記の表に示したように、SDK とランタイムの親ディレクトリは、`dotnet --list-sdks` コマンドおよび `dotnet --list-runtimes` コマンドからの出力に一覧表示されます。

::: zone-end

## <a name="net-uninstall-tool"></a>.NET アンインストール ツール

[.NET アンインストール ツール](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) を使用すると、.NET SDK とランタイムをシステムから削除できます。 一連のオプションを使用して、アンインストールするバージョンを指定できます。

::: zone pivot="os-windows"

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>.NET Core SDK バージョンに対する Visual Studio の依存関係

Visual Studio 2019 バージョン 16.3 より前では、Visual Studio インストーラーはスタンドアロンの .NET Core SDK インストーラーを呼び出しました。 その結果、Windows の **[アプリと機能]** ダイアログに SDK のバージョンが表示されます。 スタンドアロン インストーラーを使用して Visual Studio によってインストールされた .NET Core SDK を削除すると、Visual Studio が破損する可能性があります。 SDK をアンインストールした後に Visual Studio で問題が発生した場合は、その特定のバージョンの Visual Studio で [修復] を実行します。 次の表に、.NET Core SDK バージョンに対する Visual Studio の依存関係の一部を示します。

| Visual Studio のバージョン           | .NET Core SDK のバージョン          |
|---------------------------------|--------------------------------|
| Visual Studio 2019 バージョン 16.2 | .NET Core SDK 2.2.4xx、2.1.8xx |
| Visual Studio 2019 バージョン 16.1 | .NET Core SDK 2.2.3xx、2.1.7xx |
| Visual Studio 2019 バージョン 16.0 | .NET Core SDK 2.2.2xx、2.1.6xx |
| Visual Studio 2017 バージョン 15.9 | .NET Core SDK 2.2.1xx、2.1.5xx |
| Visual Studio 2017 バージョン 15.8 | .NET Core SDK 2.1.4xx          |

Visual Studio 2019 バージョン 16.3 以降では、Visual Studio によって .NET SDK の独自のコピーが管理されます。 そのため、 **[アプリと機能]** ダイアログにこれらの SDK バージョンが表示されなくなりました。

::: zone-end

## <a name="remove-the-nuget-fallback-folder"></a>NuGet フォールバック フォルダーの削除

.NET Core 3.0 SDK より前では、.NET Core SDK インストーラーでは *NuGetFallbackFolder* という名前のフォルダーを使用して NuGet パッケージのキャッシュを格納していました。 このキャッシュは、`dotnet restore` や `dotnet build /t:Restore` などの操作中に使用されました。 *NuGetFallbackFolder* は、Windows では *C:\Program Files\dotnet\sdk* に、macOS では */usr/local/share/dotnet/sdk* にあります。

次の場合は、このフォルダーを削除することができます。

- .NET Core 3.0 SDK または .NET 5.0 以降のバージョンのみを使用して開発している。
- 3\.0 より前の .NET Core SDK のバージョンを使用して開発しているが、オンラインで作業できる。

NuGet フォールバック フォルダーを削除する場合は、管理者特権が必要になります。

*dotnet* フォルダーの削除はお勧めしません。 これを行うと、以前にインストールしたグローバル ツールがすべて削除されます。 また、Windows の場合は、次のことが発生します。

- Visual Studio 2019 バージョン 16.3 以降のバージョンが破損します。 **[修復]** を実行して回復できます。
- **[アプリと機能]** ダイアログに .NET Core SDK エントリがある場合、それらは孤立状態になります。
