---
title: Alpine に .NET をインストールする - .NET
description: Alpine に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6cd36fa6329d3c1a5835d4c202ac0024ffa41892
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079506"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>Alpine に .NET SDK または .NET ランタイムをインストールする

この記事では、Alpine に .NET をインストールする方法について説明します。 Alpine のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。 ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a>[インストール]

Alpine Linux 用に使用できるインストーラーはありません。 次のいずれかの方法で .NET をインストールする必要があります。

- [Snap パッケージ](linux-snap.md)
- [_install-dotnet.sh_ でスクリプト化されたインストール](linux-scripted-manual.md#scripted-install)
- [手動によるバイナリ抽出](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a>サポートされているディストリビューション

次の表に、現在サポートされている .NET リリースと、それらがサポートされている Alpine のバージョンの一覧を示します。 これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Alpine のバージョンの有効期限が切れるまで](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)サポートされます。

- ✔️ は、Alpine または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、Alpine または .NET のバージョンがその Alpine のリリースではサポートされないことを示します。
- Alpine のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Alpine  | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|-------- |---------------|---------------|----------------|
| ✔️ 3.13 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.12 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.11 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.10 | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ 3.9  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ 3.8  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |

次のバージョンの .NET は、サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>依存関係

Alpine Linux 上の .NET には、次の依存関係がインストールされている必要があります。

- icu-libs
- krb5-libs
- libgcc
- libgdiplus (.NET アプリで *System.Drawing.Common* アセンブリが必要な場合)
- libintl
- libssl1.1 (Alpine v3.9 以上)
- libssl1.0 (Alpine v3.8 以下)
- libstdc++
- zlib

必要な要件をインストールするには、次のコマンドを実行します。

```bash
apk add bash icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib
```

**libgdiplus** をインストールするには、次のようにリポジトリを指定する必要がある場合があります。

```bash
apk add libgdiplus --repository https://dl-3.alpinelinux.org/alpine/edge/testing/
```

## <a name="next-steps"></a>次のステップ

- [.NET CLI のタブ補完を有効にする方法](../tools/enable-tab-autocomplete.md)
- [チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する](../tutorials/with-visual-studio-code.md)
