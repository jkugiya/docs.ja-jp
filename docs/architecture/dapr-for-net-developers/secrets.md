---
title: Dapr のシークレット ビルディング ブロック
description: シークレット ビルディング ブロック、その機能、利点、適用方法の説明
author: edwinvw
ms.date: 02/17/2021
ms.openlocfilehash: 52b899b4d496aab6762f69bbee99faecfcd23d59
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623747"
---
# <a name="the-dapr-secrets-building-block"></a>Dapr のシークレット ビルディング ブロック

エンタープライズ アプリケーションにはシークレットが必要です。 たとえば、次のような場合です。

- ユーザー名とパスワードを含むデータベース接続文字列。
- 外部 Web API を呼び出すための API キー。
- 外部システムに対して認証を行うためのクライアント証明書。

シークレットは、アプリケーションの外部に公開されないように慎重に管理する必要があります。

最近までは、アプリケーションのシークレットをアプリケーション コードベース内の構成ファイルに格納するのが一般的でした。 .NET 開発者は、*web.config* ファイルを呼び戻すでしょう。 実装するのは簡単ですが、シークレットとコードの統合は決して安全なものではありませんでした。 よくある間違いは、パブリック Git リポジトリへのプッシュ時にファイルを追加し、世界中にシークレットを公開してしまうことでした。

最新の分散型アプリケーションの構築方法として広く受け入れられているのが [The Twelve-Factor App](https://12factor.net/) です。 これには一連の原則とベスト プラクティスが記述されています。 3 番目の要素では、"*構成とシークレットはコードベース外に外部化される*" と規定しています。

この問題に対処するために、.NET Core プラットフォームには、プロジェクト ツリーの外部にある物理フォルダーに機密データを格納する[シークレット マネージャー](/aspnet/core/security/app-secrets#secret-manager)機能が用意されています。 シークレットはソース管理の対象外ですが、この機能ではデータを暗号化しません。 **開発** のみを目的として設計されています。

より安全性に優れた最新の方法としては、**Hashicorp Vault** や **Azure Key Vault** などのシークレット管理ツールでシークレットを分離します。  これらのツールを使用すると、シークレットを外部に格納し、環境間で資格情報を変更して、アプリケーション コードから参照できます。 ただし、各ツールにはそれぞれ複雑な点と学習曲線があります。

Dapr は、シークレットの管理を簡略化するビルディング ブロックを提供します。

## <a name="what-it-solves"></a>解決される内容

Dapr の[シークレット ビルディング ブロック](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/)は、シークレットとシークレット管理ツールの操作の複雑さを解消します。

- 統合インターフェイスを使用して、基になるプラミングを非表示にします。
- 開発と運用の間で異なる可能性のある、"*プラグ可能な*" さまざまなシークレット ストア コンポーネントがサポートされます。
- アプリケーションには、シークレット ストア ライブラリへの直接的な依存関係は必要ありません。
- 開発者には、各シークレット ストアに関する詳細な知識は不要です。

Dapr は上記のすべての懸念事項に対処します。

シークレットへのアクセスは、認証と認可によって保護されます。 十分な権限を持つアプリケーションのみシークレットにアクセスできます。 Kubernetes で実行されているアプリケーションでは、組み込みのシークレット管理メカニズムを使用することもできます。

## <a name="how-it-works"></a>しくみ

アプリケーションでは、次の 2 つの方法でシークレット ビルディング ブロックを使用します。

- アプリケーション ブロックから直接シークレットを取得する。
- Dapr コンポーネント構成から間接的にシークレットを参照する。

直接シークレットを取得する方法について最初に説明します。 Dapr コンポーネント構成ファイルからシークレットを参照する方法については、後のセクションで説明します。

アプリケーションは、シークレット ビルディング ブロックの使用時に Dapr サイドカーと対話します。 サイドカーは、シークレット API を公開しています。 この API は、HTTP または gRPC を使用して呼び出すことができます。 次の URL を使用して HTTP API を呼び出します。

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/<name>?<metadata>
```

この URL に含まれるセグメントは次のとおりです。

- `<dapr-port>` は、Dapr サイドカーがリッスンするポート番号を指定します。
- `<store-name>` は、Dapr シークレット ストアの名前を指定します。
- `<name>` は、取得するシークレットの名前を指定します。
- `<metadata>` は、シークレットの追加情報を提供します。 このセグメントは省略可能であり、メタデータ プロパティはシークレット ストアごとに異なります。 メタデータ プロパティの詳細については、[シークレット API リファレンス]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/))を参照してください。

 > [!NOTE]
 > 上記の URL は、HTTP または gRPC をサポートするすべての開発プラットフォームで使用可能なネイティブの Dapr API 呼び出しを表します。 .NET、Java、Go などの一般的なプラットフォームには独自のカスタム API があります。

JSON 応答には、シークレットのキーと値が含まれています。

図 10-1 は、Dapr がシークレット API の要求を処理する方法を示しています。

![Dapr シークレット API を使用したシークレットの取得を示す図。](media/secrets/secrets-flow.png)

**図 10-1** Dapr シークレット API を使用したシークレットの取得。

1. サービスが、Dapr シークレット API、シークレット ストアの名前、取得するシークレットを呼び出します。
1. Dapr サイドカーが、指定されたシークレットをシークレット ストアから取得します。
1. Dapr サイドカーが、シークレット情報をサービスに返します。

一部のシークレット ストアでは、複数のキー/値のペアを 1 つのシークレットに格納できます。 これらのシナリオでは、次の例に示すように、1 つの JSON 応答に複数のキー/値のペアが含まれます。

```http
GET http://localhost:3500/v1.0/secrets/secret-store/interestRates?metadata.version_id=3
```

```json
{
  "tier1-percentage": "2.5",
  "tier2-percentage": "3.8",
  "tier3-percentage": "5.1"
}
```

Dapr シークレット API は、アプリケーションがアクセスできるすべてのシークレットを取得する操作も提供します。

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/bulk
```

## <a name="use-the-dapr-net-sdk"></a>Dapr .NET SDK を使用する

.NET 開発者が Dapr .NET SDK を使用すると、Dapr のシークレット管理が効率化されます。 たとえば、`DaprClient.GetSecretAsync` メソッドがあるとします。 これにより、最小限の作業で、任意の Dapr シークレット ストアから直接シークレットを取得できます。 SQL Server データベースの接続文字列シークレットを取り込む例を次に示します。

```csharp
var metadata = new Dictionary<string, string> { ["version_id"] = "3" };
Dictionary<string, string> secrets = await daprClient.GetSecretAsync("secret-store", "eshopsecrets", metadata);
string connectionString = secrets["customerdb"];
```

`GetSecretAsync` メソッドの引数は次のとおりです。

- Dapr シークレット ストア コンポーネントの名前 ("secret-store")
- 取得するシークレット ("eshopsecrets")
- (省略可能) メタデータのキーと値のペア ("version_id=3")

シークレットには複数のキーと値のペアを含めることができるため、このメソッドは辞書オブジェクトで応答します。 上の例では、`customerdb` という名前のシークレットがコレクションから参照され、接続文字列を返します。

Dapr .NET SDK には .NET 構成プロバイダーも用意されています。 これは、指定されたシークレットを、基になる [.NET Core 構成 API](../../core/extensions/configuration.md) に読み込みます。 これで、実行中のアプリケーションは、ASP.NET Core 依存関係の挿入で登録される `IConfiguration` 辞書からシークレットを参照できます。

シークレット構成プロバイダーは、[Dapr.Extensions.Configuration](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet パッケージから入手できます。 このプロバイダーは、ASP.NET Web API アプリケーションの `Program.cs` で登録できます。  

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureAppConfiguration(config =>
        {
            var daprClient = new DaprClientBuilder().Build();
            var secretDescriptors = new List<DaprSecretDescriptor>
            {
                new DaprSecretDescriptor("eshopsecrets")
            };
            config.AddDaprSecretStore("secret-store", secretDescriptors, daprClient);
        })
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

上の例では、起動時に `eshopsecrets` シークレット コレクションを .NET 構成システムに読み込みます。 プロバイダーを登録するには、Dapr サイドカーでシークレット API を呼び出すための `DaprClient` のインスタンスが必要です。 その他の引数には、シークレット ストアの名前、およびシークレットの名前を含む `DaprSecretDescriptor` オブジェクトがあります。

読み込みが完了すると、アプリケーション コードから直接シークレットを取得できます。

```csharp
public void GetCustomer(IConfiguration config)
{
    var connectionString = config["eshopsecrets"]["customerdb"];
}
```

## <a name="secret-store-components"></a>シークレット ストア コンポーネント

シークレット ビルディング ブロックでは、複数のシークレット ストア コンポーネントがサポートされます。 この記事の執筆時点では、次のシークレット ストアを使用できます。

- 環境変数
- ローカル ファイル
- Kubernetes シークレット
- AWS Secrets Manager
- Azure Key Vault
- GCP Secret Manager
- HashiCorp Vault

> [!IMPORTANT]
> 環境変数とローカル ファイル コンポーネントは、開発ワークロード専用に設計されています。

次のセクションでは、シークレット ストアを構成する方法について説明します。

### <a name="configuration"></a>構成

シークレット ストアは、Dapr コンポーネント構成ファイルを使用して構成します。 ファイルの一般的な構造を次に示します。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: [component name]
  namespace: [namespace]
spec:
  type: secretstores.[secret store type]
  version: [secret store version]
  metadata:
  - name: [property name]
    value: [property value]
```

すべての Dapr コンポーネント構成ファイルには、`name` とオプションの `namespace` 値が必要です。 また、`spec` セクションの `type` フィールドでは、シークレット ストア コンポーネントの種類を指定します。 `metadata` セクションのプロパティは、シークレット ストアごとに異なります。

### <a name="indirectly-consume-dapr-secrets"></a>Dapr シークレットを間接的に使用する

この章で既に説明したとおり、アプリケーションでシークレットを使用する方法として、コンポーネント構成ファイルでシークレットを参照することもできます。 Redis キャッシュを使用して状態を格納する[状態管理コンポーネント](state-management.md)について考えてみましょう。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: e$h0p0nD@pr
```

上の構成ファイルには、Redis サーバーに接続するための **クリア テキスト** のパスワードが含まれています。 **ハードコードされた** パスワードは常に不適切なアイデアです。 この構成ファイルをパブリック リポジトリにプッシュすると、パスワードが公開されます。 シークレット ストアにパスワードを格納すると、このシナリオが大幅に改善されます。

次の例では、異なるいくつかのシークレット ストアを使用してこのことを実証します。

### <a name="local-file"></a>ローカル ファイル

ローカル ファイル コンポーネントは、開発シナリオ用に設計されています。 これは、JSON ファイル内のローカル ファイル システムにシークレットを格納します。 `eshop-secrets.json` という名前のサンプルを次に示します。 これには、シークレットが 1 つ (Redis のパスワード) 含まれています。

```json
{
  "eShopRedisPassword": "e$h0p0nD@pr"
}
```

このファイルは、Dapr アプリケーションの実行時に指定する `components` フォルダーに配置します。

次のシークレット ストア構成ファイルでは、シークレット ストアとして JSON ファイルを使用します。 これは `components` フォルダーにも配置されます。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-local-secret-store
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secrets.json
  - name: nestedSeparator
    value: ":"
```

コンポーネントの種類は `secretstore.local.file` です。 `secretsFile` メタデータ要素は、シークレット ファイルへのパスを指定します。

> [!IMPORTANT]
> シークレット ファイルへのパスとして、絶対パスまたは相対パスを指定できます。 相対パスは、アプリケーションを起動するフォルダーを基準としています。 この例では、`components` フォルダーは、.NET アプリケーションが格納されているディレクトリのサブフォルダーです。

アプリケーション フォルダーから、コマンド ライン引数として `components` パスを指定して Dapr アプリケーションを起動します。

```console
dapr run --app-id basket-api --components-path ./components dotnet run
```

> [!NOTE]
> 上の例は、セルフホステッド モードでの Dapr の実行に適用されます。 Kubernetes ホスティングの場合は、ボリューム マウントの使用を検討してください。

Dapr 構成ファイルの `nestedSeparator` は、JSON 階層を "*フラット化*" する文字を指定します。 次のスニペットについて考えてみましょう。

```json
{
    "redisPassword": "some password",
    "connectionStrings": {
        "customerdb": "some connection string",
        "productdb": "some connection string"
    }
}
```

区切り記号としてコロンを使用すると、キー `connectionStrings:customerdb` を使用して `customerdb` 接続文字列を取得できます。

> [!NOTE]
> 既定の区切り記号値はコロン (`:`) です。

次の例では、状態管理構成ファイルがローカル シークレット ストア コンポーネントを参照し、Redis サーバーに接続するためのパスワードを取得します。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    secretKeyRef:
      name: eShopRedisPassword
      key: eShopRedisPassword
auth:
  secretStore: eshop-local-secret-store
```

`secretKeyRef` 要素は、パスワードを含むシークレットを参照します。 これにより、以前の "*クリア テキスト*" 値が置き換えられます。 シークレット名とキー名 (`eShopRedisPassword`) はシークレットを参照します。 シークレット管理コンポーネントの名前 (`eshop-local-secret-store`) は `auth` メタデータ要素にあります。

シークレット参照の名前とキーがなぜ両方とも `eShopRedisPassword` であるかを不思議に思うかもしれません。 ローカル ファイル シークレット ストアでは、複数のシークレットが個別の名前で識別されません。 このシナリオは、Kubernetes シークレットを使用する次の例では異なります。

### <a name="kubernetes-secret"></a>Kubernetes シークレット

この 2 番目の例では、Kubernetes で実行される Dapr アプリケーションに焦点を当てています。 この場合、Kubernetes が提供する標準のシークレット メカニズムが使用されます。 Kubernetes CLI (`kubectl`) を使用して、パスワードを含む `eshop-redis-secret` という名前のシークレットを作成します。

```console
kubectl create secret generic eshopsecrets --from-literal=redisPassword=e$h0p0nD@pr -n eshop
```

作成が完了すると、状態管理用のコンポーネント構成ファイルでシークレットを参照できます。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: eshopsecrets
      key: redisPassword
auth:
  secretStore: kubernetes
```

`secretKeyRef` 要素は、Kubernetes シークレットの名前 (`eshopsecrets`) とシークレットのキー (`redisPassword`) をそれぞれ指定します。 `auth` メタデータ セクションでは、Kubernetes シークレット管理コンポーネントを使用するように Dapr に指示します。

> [!NOTE]
> Kubernetes シークレットを使用する場合は、auth が既定値です。この値は省略できます。

運用環境の設定では、通常、シークレットは自動 CI/CD パイプラインの一部として作成されます。 これで、十分なアクセス許可を持つユーザーだけがシークレットにアクセスしたり、シークレットを変更したりできるようになります。 開発者は、シークレットの実際の値を把握せずに構成ファイルを作成します。

### <a name="azure-key-vault"></a>Azure Key Vault

次の例は、実際の運用環境のシナリオを対象としています。 シークレット ストアとして **Azure Key Vault** が使用されます。 Azure Key Vault は、シークレットを安全にクラウドに格納できるようにするマネージド Azure サービスです。

この例を使用するには、次の前提条件を満たしている必要があります。

- Azure サブスクリプションへの管理アクセスがセキュリティで保護されている。
- Redis サーバーに接続するためのパスワードを含むシークレット (`redisPassword`) を保持する Azure Key Vault (`eshopkv`) がプロビジョニングされている。
- Azure Active Directory で[サービス プリンシパル](/azure/active-directory/develop/howto-create-service-principal-portal)が作成されている。
- このサービス プリンシパルの X509 証明書 (公開キーと秘密キーの両方を含む) がローカル ファイル システムにインストールされている。

> [!NOTE]
> サービス プリンシパルは、アプリケーションが Azure サービスを認証するために使用できる ID です。 サービス プリンシパルでは X509 証明書を使用します。 アプリケーションでは、資格情報としてこの証明書を使用して自身を認証します。

[Dapr Azure Key Vault シークレット ストアのドキュメント](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/)では、Key Vault 環境を作成および構成するための詳細な手順について説明しています。

#### <a name="use-key-vault-when-running-in-self-hosted-mode"></a>セルフホステッド モードでの実行時に Key Vault を使用する

Dapr のセルフホステッド モードで Azure Key Vault を使用するには、次の構成ファイルが必要です。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: eshopkv
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificateFile
    value : "azurekv-spn-cert.pfx"
```

シークレット ストアの種類は `secretstores.azure.keyvault` です。 Key Vault へのアクセスを構成する `metadata` 要素には次のプロパティが必要です。

- `vaultName` には、Azure Key Vault の名前が含まれています。
- `spnTenantId` には、Key Vault に対する認証に使用されるサービス プリンシパルの "*テナント ID*" が含まれています。
- `spnClientId` には、Key Vault に対する認証に使用されるサービス プリンシパルの "*アプリ ID*" が含まれています。
- `spnCertificateFile` には、Key Vault に対する認証のためのサービス プリンシパルの証明書ファイル名へのパスが含まれています。

> [!TIP]
> サービス プリンシパル情報は、Azure portal または Azure CLI からコピーできます。

これで、アプリケーションが Azure Key Vault から Redis パスワードを取得できます。

#### <a name="use-key-vault-when-running-on-kubernetes"></a>Kubernetes での実行時に Key Vault を使用する

Azure Key Vault を Dapr と Kubernetes で使用するには、Azure Key Vault に対する認証のためのサービス プリンシパルも必要です。

最初に、kubectl CLI ツールを使用して証明書ファイルを含む "*Kubernetes シークレット*" を作成します。

```console
kubectl create secret generic [k8s_spn_secret_name] --from-file=[pfx_certificate_file_local_path] -n eshop
```

このコマンドには、次の 2 つのコマンド ライン引数が必要です。

- `[k8s_spn_secret_name]` は、Kubernetes シークレット ストア内のシークレット名です。
- `[pfx_certificate_file_local_path]` は、X509 証明書ファイルのパスです。

作成が完了すると、シークレット ストア コンポーネント構成ファイルで Kubernetes シークレットを参照できます。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: [your_keyvault_name]
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificate
    secretKeyRef:
      name: [k8s_spn_secret_name]
      key: [pfx_certificate_file_local_name]
auth:
    secretStore: kubernetes
```

この時点で、Kubernetes で実行されているアプリケーションは、Azure Key Vault から Redis パスワードを取得できます。

> [!IMPORTANT]
> サービス プリンシパルの X509 証明書ファイルを安全な場所に保管することが重要です。 ソース コード リポジトリの外部にある既知のフォルダーに配置することをお勧めします。 これで、構成ファイルがこの既知のフォルダーから証明書ファイルを参照できます。 ローカルの開発マシンでは、ユーザーが証明書をこのフォルダーにコピーする必要があります。 自動デプロイの場合は、パイプラインによって、アプリケーションがデプロイされているマシンに証明書がコピーされます。 環境ごとに異なるサービス プリンシパルを使用することをお勧めします。 これにより、開発環境のサービス プリンシパルが運用環境のシークレットにアクセスできなくなります。

Azure Kubernetes Service (AKS) での実行時には、[Azure マネージド ID](/azure/active-directory/managed-identities-azure-resources/overview) を使用して Azure Key Vault に対する認証を行うことをお勧めします。 マネージド ID については本書では説明しません。[Azure Key Vault でマネージド ID を使用する方法](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/)に関するドキュメントを参照してください。

### <a name="scope-secrets"></a>シークレットのスコープを指定する

シークレットのスコープを使用すると、アプリケーションがアクセスできるシークレットを制御できます。 スコープは、Dapr サイドカー構成ファイルで構成します。 [Dapr の構成に関するドキュメント](https://docs.dapr.io/operations/configuration/configuration-overview/)では、シークレットのスコープを指定する手順について説明しています。

シークレットのスコープを含む Dapr サイドカー構成ファイルの例を次に示します。

```yml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  secrets:
    scopes:
      - storeName: eshop-azurekv-secret-store
        defaultAccess: allow
        deniedSecrets: ["redisPassword", "apiKey"]
```

スコープはシークレット ストアごとに指定します。 上の例では、シークレット ストアに `eshop-azurekv-secret-store` という名前が付けられています。 シークレットへのアクセスを構成するには、次のプロパティを使用します。

| プロパティ         | 値               | 説明                                                                                                                       |
|------------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `defaultAccess`  | `allow` または `deny`   | 指定されたシークレット ストア内の "*すべて*" のシークレットへのアクセスを許可または拒否します。 このプロパティは省略可能であり、既定値は `allow` です。 |
| `allowedSecrets` | シークレット キーのリスト | 配列に指定されたシークレットにアクセスできます。 このプロパティは省略可能です。                                                     |
| `deniedSecrets`  | シークレット キーのリスト | 配列に指定されたシークレットにはアクセスできません。 このプロパティは省略可能です。                                                 |

`allowedSecrets` プロパティと `deniedSecrets` プロパティは `defaultAccess` プロパティよりも優先されます。 `defaultAccess: allowed` と `allowedSecrets` リストを指定すると想像してください。 この場合、アプリケーションからアクセスできるのは `allowedSecrets` リスト内のシークレットだけです。

## <a name="reference-application-eshopondapr"></a>参照アプリケーション: eShopOnDapr

eShopOnDapr 参照アプリケーションでは、次に示す 2 つのシークレットに対してシークレット ビルディング ブロックを使用します。

- Redis キャッシュに接続するためのパスワード。
- Twilio Sendgrid API を使用するための API キー。 このアプリケーションでは、Twilio を使用して、Dapr 出力バインディングによって電子メールを送信します ([バインディング ビルディング ブロックに関する章](bindings.md)を参照)。

Docker Compose を使用してアプリケーションを実行する場合は、**ローカル ファイル** シークレット ストアが使用されます。 コンポーネント構成ファイル `eshop-secretstore.yaml` は、eShopOnDapr リポジトリの `dapr/components` フォルダーにあります。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-secretstore
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secretstore.json
```

この構成ファイルは、同じフォルダーにあるローカル ストア ファイル `eshop-secretstore.json` を参照します。

```json
{
    "redisPassword": "**********",
    "sendgridAPIKey": "**********"
}
```

`components` フォルダーはコマンド ラインで指定され、Dapr サイドカー コンテナー内にローカル フォルダーとしてマウントされます。 ボリューム マウントを指定するリポジトリ ルート内の `docker-compose.override.yml` ファイルのスニペットを次に示します。

```yaml
  ordering-backgroundtasks-dapr:
    command: ["./daprd",
      "-app-id", "ordering-backgroundtasks",
      "-app-port", "80",
      "-dapr-grpc-port", "50004",
      "-components-path", "/components",
      "-config", "/configuration/eshop-config.yaml"
      ]
    volumes:
      - "./dapr/components/:/components"
      - "./dapr/configuration/:/configuration"
```

> [!NOTE]
> Docker Compose オーバーライド ファイルには、環境固有の構成値が含まれています。

`/components` ボリューム マウントと `--components-path` コマンド ライン引数は、`daprd` スタートアップ コマンドに渡されます。

構成が完了すると、他のコンポーネント構成ファイルでもシークレットを参照できます。 シークレットを使用するパブリッシュ/サブスクライブ コンポーネント構成の例を次に示します。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: eshop
spec:
  type: pubsub.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

上の例では、シークレットを参照するためにローカルの Redis ストアが使用されます。

## <a name="summary"></a>まとめ

Dapr シークレット ビルディング ブロックは、パスワードや接続文字列などの機密構成設定を格納および取得する機能を提供します。 シークレットは機密として扱われ、誤って公開されることはありません。

このビルディング ブロックでは、異なるいくつかのシークレット ストアがサポートされており、Dapr シークレット API によってその複雑さが隠されています。

Dapr .NET SDK には、シークレットを取得するための `DaprClient` オブジェクトが用意されています。 また、.NET Core 構成システムにシークレットを追加する .NET 構成プロバイダーも含まれています。 読み込みが完了すると、これらのシークレットを .NET コードで使用できます。

シークレットのスコープを使用すると、特定のシークレットへのアクセスを制御できます。

## <a name="references"></a>リファレンス

- [Beyond the Twelve-Factor Application (Beyond the Twelve-Factor App)](https://tanzu.vmware.com/content/blog/beyond-the-twelve-factor-app)

>[!div class="step-by-step"]
>[前へ](observability.md)
>[次へ](summary.md)
