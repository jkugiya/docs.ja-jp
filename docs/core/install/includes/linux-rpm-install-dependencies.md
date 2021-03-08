---
ms.openlocfilehash: 5a027054024d8429831d73525ab3748c51ae850e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255758"
---

パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。 ただし、手動で .NET Core をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。

- krb5-libs
- libicu
- openssl-libs
- zlib

ターゲット ランタイム環境の OpenSSL バージョンが 1.1 以降である場合は、**compat-openssl10** をインストールする必要があります。

依存関係の詳細については、「[Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」(自己完結型 Linux アプリケーション) をご覧ください。

*System.Drawing.Common* アセンブリを使用する .NET Core アプリの場合は、次の依存関係も必要です。

- [libgdiplus (バージョン 6.0.1 以降)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > 最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。 詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。
