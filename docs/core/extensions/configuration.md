---
title: .NET での構成
description: 構成 API を使用して、.NET アプリケーションを構成する方法を説明します。
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: overview
ms.openlocfilehash: 5955e46c2f5acb6776ada4e3fd6a65507d3faa1f
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "102402024"
---
# <a name="configuration-in-net"></a>.NET での構成

.NET での構成は、1 つまたは複数の[構成プロバイダー](#configuration-providers)を使用して実行されます。 構成プロバイダーは、以下のようなさまざまな構成ソースを使用して、キーと値のペアから構成データを読み取ります:

- *appsettings.json* などの設定ファイル
- 環境変数
- [Azure Key Vault](/azure/key-vault/general/overview)
- [Azure App Configuration](/azure/azure-app-configuration/overview)
- コマンド ライン引数
- インストール済みまたは作成済みのカスタム プロバイダー
- ディレクトリ ファイル
- メモリ内 .NET オブジェクト

## <a name="configure-console-apps"></a>コンソール アプリの構成

既定で [dotnet new](../tools/dotnet-new.md) または Visual Studio を使用して作成された新しい .NET コンソール アプリケーションでは、構成機能は公開 "*されません*"。 新しい .NET コンソール アプリケーションで構成を追加するには、`Microsoft.Extensions.Hosting` に[パッケージ参照を追加](../tools/dotnet-add-package.md)します。 *Program.cs* ファイルを次のコードに一致するように変更します。

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="18":::

<xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType> メソッドにより、次の順序でアプリの既定の構成が提供されます。

1. [ChainedConfigurationProvider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource): 既存の `IConfiguration` をソースとして追加します。
1. [JSON 構成プロバイダー](configuration-providers.md#file-configuration-provider)を使用する *appsettings.json*。
1. [JSON 構成プロバイダー](configuration-providers.md#file-configuration-provider)を使用する *appsettings.* `Environment`*json*。 たとえば、*appsettings*.***Production**_._json* および *appsettings*.***Development** _._json*。
1. `Development` 環境でアプリが実行される際の App シークレット。
1. [環境変数構成プロバイダー](configuration-providers.md#environment-variable-configuration-provider)を使用する環境変数。
1. [コマンドライン構成プロバイダー](configuration-providers.md#command-line-configuration-provider)を使用するコマンドライン引数。

後から追加される構成プロバイダーは、それ以前のキー設定をオーバーライドします。 たとえば、`SomeKey` が *appsettings.json* と環境の両方で設定されている場合、環境の値が使用されます。 既定の構成プロバイダーを使用すると、[コマンドライン構成プロバイダー](configuration-providers.md#command-line-configuration-provider)によって他のすべてのプロバイダーがオーバーライドされます。

### <a name="binding"></a>バインド

.NET での構成の主な利点の 1 つは、構成値を .NET オブジェクトのインスタンスにバインドする機能です。 たとえば、JSON 構成プロバイダーは、*appsettings.json* ファイルを .NET オブジェクトにマップするのに使用でき、依存関係の挿入で使用されます。 これによりオプション パターンが有効になります。オプション パターンは、クラスを使用して、関連する設定のグループに厳密に型指定されたアクセスを提供します。

## <a name="configuration-providers"></a>構成プロバイダー

.NET Core アプリで使用できる構成プロバイダーを次の表に示します。

| プロバイダー                                                                                                               | 以下から構成を提供します        |
|------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [Azure App Configuration プロバイダー](/azure/azure-app-configuration/quickstart-aspnet-core-app)                          | Azure App Configuration            |
| [Azure Key Vault 構成プロバイダー](/azure/key-vault/general/tutorial-net-virtual-machine)                        | Azure Key Vault                    |
| [コマンド ライン構成プロバイダー](configuration-providers.md#command-line-configuration-provider)                  | コマンド ライン パラメーター            |
| [カスタム構成プロバイダー](custom-configuration-provider.md)                                                      | カスタム ソース                      |
| [環境変数構成プロバイダー](configuration-providers.md#environment-variable-configuration-provider) | 環境変数              |
| [ファイル構成プロバイダー](configuration-providers.md#file-configuration-provider)                                  | JSON、XML、および INI ファイル           |
| [ファイルごとのキーの構成プロバイダー](configuration-providers.md#key-per-file-configuration-provider)                  | ディレクトリ ファイル                    |
| [メモリ構成プロバイダー](configuration-providers.md#memory-configuration-provider)                              | メモリ内コレクション              |
| [アプリのシークレット (Secret Manager)](/aspnet/core/security/app-secrets)                                                      | ユーザー プロファイル ディレクトリ内のファイル |

さまざまな構成プロバイダーの詳細については、「[.NET の構成プロバイダー](configuration-providers.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [.NET の構成プロバイダー](configuration-providers.md)
- [カスタム構成プロバイダーを実装する](custom-configuration-provider.md)
- 構成のバグは、[github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) リポジトリに作成する必要がある
