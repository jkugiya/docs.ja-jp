---
title: "NETSDK1045: 現在の .NET SDK では、ターゲットとして '新しいバージョン' がサポートされていません。"
description: .NET SDK エラー NETSDK1045 について説明します。これは、要求されたバージョンの .NET SDK をビルド ツールで見つけられない場合に発生します。
ms.topic: error-reference
ms.date: 02/12/2021
f1_keywords:
- NETSDK1045
ms.openlocfilehash: 7f21270fdc7c2db862a49302a302bf8121fc86a5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104103"
---
# <a name="netsdk1045-the-current-net-sdk-does-not-support-newer-version-as-a-target"></a>NETSDK1045: 現在の .NET SDK では、ターゲットとして '新しいバージョン' がサポートされていません。

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

このエラーは、プロジェクトのビルドに必要な .NET SDK のバージョンをビルド ツールで見つけられない場合に発生します。 これは通常、.NET Core SDK のインストールまたは構成の問題が原因です。 完全なエラー メッセージは、次の例のようになります。

> NETSDK1045: 現在の .NET SDK では、ターゲットとして '新しいバージョン' がサポートされていません。 '古いバージョン' 以下をターゲットにするか、'新しいバージョン' をサポートする .NET SDK バージョンを使用してください。

次のセクションでは、このエラーの考えられる原因についていくつか説明します。 それぞれを調べ、どれが自分に該当するかを確認します。 環境または構成ファイルに変更を加える際には、場合によってはコマンド ウィンドウを再起動するか、Visual Studio を再起動するか、コンピューターを再起動して変更を有効にする必要があることに注意してください。

## <a name="net-sdk-version"></a>.NET SDK バージョン

プロジェクト ファイル (.csproj、.vbproj、または .fsproj) を開き、ターゲット フレームワークを確認します。 これは、アプリで使用しようとしているフレームワークのバージョンです。

```xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

一覧表示されている .NET のバージョンがコンピューターにインストールされていることを確認してください。 次のコマンドを使用して、インストールされているバージョンを一覧表示できます (開発者コマンド プロンプトを開いて、このコマンドを実行する)。

```dotnetcli
dotnet --list-sdks
```

### <a name="x86-or-x64-architecture"></a>x86 または x64 のアーキテクチャ

.NET SDK の各バージョンは、x86 と x64 の両方のアーキテクチャで使用できます。 プロジェクトで間違ったアーキテクチャ用の .NET SDK を検索しようしているか、プロジェクトに必要なアーキテクチャ用の .NET SDK がインストールされていない可能性があります。 インストール フォルダーに必要なアーキテクチャがあるかどうかを確認してください。 たとえば、Windows では、.NET SDK の x86 バージョンが *C:\Program Files (x86)\dotnet* にインストールされ、x64 バージョンが *C:\Program Files\dotnet* にインストールされます。 「[.NET が既にインストールされていることを確認する方法](../../install/how-to-detect-installed-versions.md)」を参照し、ご利用のオペレーティング システムを選択して、コンピューターにインストールされているものを検出する方法を確認してください。

必要なバージョンがインストールされていない場合、[.NET ダウンロード](https://dotnet.microsoft.com/download/dotnet) ページで、必要なバージョンを見つけてください。

## <a name="preview-not-enabled"></a>プレビューが有効になっていない

要求された .NET SDK バージョンのプレビューがインストールされている場合は、Visual Studio でプレビューを有効にするオプションも設定する必要があります。 **[ツール]**  >  **[オプション]**  >  **[環境]**  >  **[プレビュー機能]** の順に移動し、 **[プレビューの .NET Core SDK を使用]** がオンになっていることを確認してください。

## <a name="visual-studio-version"></a>Visual Studio のバージョン

たとえば、.NET Core 3.0 以降では Visual Studio 2019 が必要です。 [Visual Studio 2019 バージョン 16.3](https://visualstudio.microsoft.com/downloads) 以降にアップグレードして、プロジェクトをビルドします。

## <a name="path-environment-variable"></a>PATH 環境変数

ビルド ツールでは、PATH 環境変数を使用して、適切なバージョンの .NET ビルド ツールを検索します。 PATH 環境変数に古いビルド ツールへの直接パスが含まれている場合、このエラー メッセージが表示されることがあります。 PATH 環境変数内の .NET ツールへの唯一のパスが、最上位の *dotnet* フォルダー (たとえば、*C:\Program Files\dotnet*) へのものであることを確認してください。 不適切な PATH の例としては、*C:\Program Files\dotnet\2.1.0\sdks* のようなものがあります。

## <a name="msbuildsdkpath-environment-variable"></a>MSBuildSDKPath 環境変数

MSBuildSDKPath 環境変数を確認します。 この省略可能な環境変数は MSBuild によって認識され、これが設定されている場合、既定値はオーバーライドされます。 これは、.NET SDK の特定の古いバージョンに設定されている可能性があります。 設定されている場合は、削除してプロジェクトをリビルドしてみてください。

## <a name="globaljson-file"></a>global.json file

フォルダー構造内の任意の場所に存在する可能性があるため、プロジェクトのルート フォルダーに *global.json* ファイルがあるかどうかを確認し、ボリュームのルートまでディレクトリ チェーンを上にたどっていきます。 SDK のバージョンが含まれている場合は、`sdk` ノードとそのすべての子を削除するか、必要な新しい .NET Core バージョンに更新します。

```json
{
  "sdk": {
    "version": "2.1.0"
  }
}
```

*global.json* ファイルは必須ではありません。したがって、`sdk` ノード以外のものが含まれていない場合は、ファイル全体を削除できます。

## <a name="directorybuildprops-file"></a>Directory.build.props ファイル

*Directory.build.prop* ファイルは、グローバル プロパティを設定できる省略可能な MSBuild ファイルです。 フォルダー構造内の任意の場所に存在する可能性があるため、ソリューション フォルダーにこれらのファイルがあるかどうかを確認し、ボリュームのルートまでディレクトリ チェーンを上にたどっていきます。 `TargetFramework` の要素、または目的の設定をオーバーライドできる `MSBuildSDKPath` の設定を探します。

## <a name="see-also"></a>関連項目

- [現在の .NET SDK は、.NET Core 3.0 のターゲットをサポートしていません – 修正](https://www.ryadel.com/current-net-sdk-not-support-net-core-3-0-fix/)
