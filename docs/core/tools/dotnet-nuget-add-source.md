---
title: dotnet nuget add source コマンド
description: dotnet nuget add source コマンドを使うと、NuGet 構成ファイルに新しいパッケージ ソースを追加できます。
ms.date: 03/20/2020
ms.openlocfilehash: df31a2eaba997d0e9fe4f4c2666052fd7c7c2f03
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105052"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**この記事の対象:** ✔️ .NET Core 3.1.200 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet nuget add source` - NuGet ソースを追加にします。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>説明

`dotnet nuget add source` コマンドを使うと、NuGet 構成ファイルに新しいパッケージ ソースを追加できます。

> [!WARNING]
> 複数のパッケージ ソースを追加するとき、[依存関係かく乱脆弱性](https://aka.ms/pkg-sec-wp)を持ち込まないようにご注意ください。

## <a name="arguments"></a>引数

- **`PACKAGE_SOURCE_PATH`**

  パッケージ ソースへのパス。

## <a name="options"></a>オプション

- **`--configfile <FILE>`**

  NuGet 構成ファイル。 指定した場合、このファイルの設定のみが使用されます。 指定しない場合、現在のディレクトリからの構成ファイルの階層が使用されます。 詳細については、「[一般的な NuGet 構成](/nuget/consume-packages/configuring-nuget-behavior)」をご覧ください。

- **`-n|--name <SOURCE_NAME>`**

  ソースの名前。

- **`-p|--password <PASSWORD>`**

  認証済みソースに接続するときに使用するパスワード。

- **`--store-password-in-clear-text`**

  パスワードの暗号化を無効にすることで、ポータブル パッケージ ソースの資格情報を保存できるようにします。

- **`-u|--username <USER>`**

  認証済みソースに接続するときに使用するユーザー名。

- **`--valid-authentication-types <TYPES>`**

  このソースに対して有効な認証の種類のコンマ区切りのリスト。 サーバーによって NTLM または Negotiate がアドバタイズされていて、基本メカニズムを使用して資格情報を送信する必要がある場合は、これを `basic` に設定します。たとえば、オンプレミスの Azure DevOps Server で PAT を使用する場合などです。 その他の有効な値には、`negotiate`、`kerberos`、`ntlm`、`digest` などがありますが、これらの値は役に立たない可能性があります。

## <a name="examples"></a>使用例

- `nuget.org` をソースとして追加します。

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- `c:\packages` をローカル ソースとして追加します。

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- 認証が必要なソースを追加します。

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- 認証が必要なソースを追加します (その後資格情報プロバイダーをインストールします)。

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>関連項目

- [NuGet.config ファイルのパッケージ ソース セクション](/nuget/reference/nuget-config-file#package-source-sections)

- [sources コマンド (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
