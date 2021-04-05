---
title: dotnet nuget push コマンド
description: dotnet nuget push コマンドでは、パッケージをサーバーにプッシュして発行します。
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 71bc14fa729945b3d1e1508d014287cc5355f8cc
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637560"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet nuget push` - パッケージをサーバーにプッシュして発行します。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a>説明

`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。 プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。 構成ファイルの詳細については、「[Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。 NuGet の既定の構成は、 *%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。

このコマンドにより、既存のパッケージがプッシュされます。 パッケージは作成されません。 パッケージを作成するには、[`dotnet pack`](dotnet-pack.md) を使用します。

## <a name="arguments"></a>引数

- **`ROOT`**

  プッシュされるパッケージのファイル パスを指定します。

## <a name="options"></a>オプション

- **`-d|--disable-buffering`**

  メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。

- **`--force-english-output`**

  インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

- **`-h|--help`**

  コマンドの短いヘルプを印刷します。

- **`--interactive`**

  コマンドが認証などの操作をブロックして、手動アクションを要求することを許可します。 .NET Core 2.2 SDK 以降、使用できるオプションです。

- **`-k|--api-key <API_KEY>`**

  サーバーの API キーです。

- **`-n|--no-symbols`**

  シンボルをプッシュしません (存在する場合でも)。

- **`--no-service-endpoint`**

  ソース URL に "api/v2/package" を追加しません。 .NET Core 2.1 SDK 以降、使用できるオプションです。

- **`-s|--source <SOURCE>`**

  サーバー URL を指定します。 NuGet によって UNC またはローカル フォルダー ソースが識別され、HTTP を使用してファイルがプッシュされるのではなく、単にそこにファイルがコピーされます。
  > [!IMPORTANT]
  > NuGet 3.4.2 以降では、NuGet 構成ファイルで `DefaultPushSource` 値が指定されていない限り、これは必須パラメーターです。 詳しくは、「[NuGet の動作の構成](/nuget/consume-packages/configuring-nuget-behavior)」をご覧ください。

- **`--skip-duplicate`**

  複数のパッケージを HTTP(S) サーバーにプッシュする場合は、すべての 409 競合応答を警告として処理して、プッシュを続行できるようにします。 .NET Core 3.1 SDK 以降で利用できます。

- **`-sk|--symbol-api-key <API_KEY>`**

  シンボル サーバーの API キーです。

- **`-ss|--symbol-source <SOURCE>`**

  シンボル サーバーの URL を指定します。

- **`-t|--timeout <TIMEOUT>`**

  秒単位でサーバーにプッシュする場合のタイムアウトを指定します。 既定値は 300 秒 (5 分) です。 0 を指定すると、既定値が適用されます。

## <a name="examples"></a>使用例

- API キーを使用して、NuGet 構成ファイルで指定されている既定のプッシュ ソースに *foo.nupkg* をプッシュします。

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- API キーを指定して、公式 NuGet サーバーに *foo.nupkg* をプッシュします。

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * API キーを指定して、カスタム プッシュ ソース `https://customsource` に *foo.nupkg* をプッシュします。

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- NuGet 構成ファイルで指定されている既定のプッシュ ソースに *foo.nupkg* をプッシュします。

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- 既定のシンボル ソースに *foo.symbols.nupkg* をプッシュします。

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- NuGet 構成ファイルで指定されている既定のプッシュ ソースに *foo.nupkg* を 360 秒のタイムアウトでプッシュします。

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- NuGet 構成ファイルで指定されている既定のプッシュ ソースに、現在のディレクトリにあるすべての *.nupkg* ファイルをプッシュします。

  ```dotnetcli
  dotnet nuget push "*.nupkg"
  ```

  > [!NOTE]
  > このコマンドがうまくいかない場合は、古いバージョンの SDK (.NET Core 2.1 SDK 以前のバージョン) に存在したバグが原因である可能性があります。
  > これを解決するには、SDK のバージョンをアップグレードするか、代わりに次のコマンドを実行します: `dotnet nuget push "**/*.nupkg"`
  
  > [!NOTE]
  > ファイル グロビングを実行する bash など、シェルには引用符が必須です。 詳細については、[NuGet/Home#4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120) を参照してください。

- HTTP(S) サーバーによって競合応答 409 が返された場合でも、NuGet 構成ファイルで指定されている既定のプッシュ ソースにすべての *.nupkg* ファイルをプッシュします。

  ```dotnetcli
  dotnet nuget push "*.nupkg" --skip-duplicate
  ```

- ローカル フィード ディレクトリに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。

  ```dotnetcli
  dotnet nuget push "*.nupkg" -s c:\mydir
  ```

  このコマンドでは、パッケージが階層フォルダー構造に格納されないため、パフォーマンスを最適化することをお勧めします。 詳細については、[ローカル フィード](/nuget/hosting-packages/local-feeds)に関するページをご覧ください。  
