---
title: Fedora に .NET をインストールする - .NET
description: Fedora に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 02/17/2021
ms.openlocfilehash: efaad4788db2200b1a47f9b4ae2414730588c6ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255759"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a>Fedora に .NET SDK または .NET ランタイムをインストールする

.NET は Fedora でサポートされており、この記事では Fedora に .NET をインストールする方法について説明します。 Fedora のバージョンがサポート対象外となった場合、.NET もそのバージョンでサポート対象外となります。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

パッケージ マネージャーを使用せずに .NET をインストールする方法の詳細については、次の記事のいずれかを参照してください。

- [Snap を使用して .NET SDK または .NET ランタイムをインストールする。](linux-snap.md)
- [スクリプトを使用して .NET SDK または .NET ランタイムをインストールする。](linux-scripted-manual.md#scripted-install)
- [手動で .NET SDK または .NET ランタイムをインストールする。](linux-scripted-manual.md#manual-install)

## <a name="install-net-50"></a>.NET 5.0 をインストールする

Fedora の既定のパッケージ リポジトリで利用可能な最新バージョンの .NET は、.NET 5.0 です。

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a>.NET Core 3.1 をインストールする

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a>サポートされているディストリビューション

現在サポートされている .NET リリースと、それらがサポートされている Fedora のバージョンの一覧は、次の表のとおりです。 これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Fedora のバージョンがサポート終了になる](https://fedoraproject.org/wiki/End_of_life)までサポートされます。

- ✔️ は、Fedora または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、Fedora または .NET のバージョンがその Fedora のリリースではサポートされていないことを示しています。
- Fedora のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| .NET のバージョン  | Fedora 33 ✔️ | 32 ✔️ | 31 ❌ | 30 ❌ | 29 ❌ | 28 ❌ | 27 ❌ |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| .NET 5.0      | ✔️        | ✔️ | ❌|❌ |❌ |❌  |❌ |
| .NET Core 3.1 | ✔️        | ✔️ | ✔️|✔️ |✔️ |❌  |❌ |
| .NET Core 2.1 | ✔️        | ✔️ | ✔️|✔️ |✔️ |✔️  |✔️ |

次のバージョンの .NET は、サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>プレビュー バージョンの削除

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a>依存関係

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a>古いディストリビューションにインストールする

古いバージョンの Fedora の既定のパッケージ リポジトリには、.NET Core が含まれていません。 [snap](linux-snap.md)、[_dotnet-install.sh_ スクリプト](linux-scripted-manual.md#scripted-install)、または Microsoft のリポジトリを使用して、.NET をインストールできます。

01. 最初に、Microsoft 署名キーを信頼されたキーのリストに追加します。

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. 次に、Microsoft パッケージ リポジトリを追加します。 リポジトリのソースは、お使いの Fedora のバージョンに基づいています。

    | Fedora のバージョン | パッケージ リポジトリ |
    | -------------- | ------- |
    | 31             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | 30             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | 29             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | 28             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | 27             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a>その他のバージョンをインストールする方法

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>パッケージ マネージャーのトラブルシューティング

このセクションでは、パッケージ マネージャーを使用して .NET または .NET Core をインストールするときに発生する可能性のある一般的なエラーについて説明します。

### <a name="unable-to-find-package"></a>パッケージが見つからない

パッケージ マネージャーを使用せずに .NET をインストールする方法の詳細については、次の記事のいずれかを参照してください。

- [Snap を使用して .NET SDK または .NET ランタイムをインストールする。](linux-snap.md)
- [スクリプトを使用して .NET SDK または .NET ランタイムをインストールする。](linux-scripted-manual.md#scripted-install)
- [手動で .NET SDK または .NET ランタイムをインストールする。](linux-scripted-manual.md#manual-install)

### <a name="failed-to-fetch"></a>フェッチできない

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a>次のステップ

- [.NET CLI のタブ補完を有効にする方法](../tools/enable-tab-autocomplete.md)
- [チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する](../tutorials/with-visual-studio-code.md)
