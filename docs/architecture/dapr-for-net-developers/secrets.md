---
title: Dapr シークレットの構成ブロック
description: シークレットの構成ブロックの説明、その機能、利点、適用方法
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 94942b396af947b2a3e49b918b2b082c15f4bb08
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401438"
---
# <a name="the-dapr-secrets-building-block"></a>Dapr シークレットの構成ブロック

エンタープライズアプリケーションにはシークレットが必要です。 たとえば、次のような場合です。

- ユーザー名とパスワードを含むデータベース接続文字列。
- 外部 web API を呼び出すための API キー。
- 外部システムに対して認証を行うためのクライアント証明書。

シークレットは、アプリケーションの外部に公開されないように、慎重に管理する必要があります。

アプリケーションのシークレットは、アプリケーションコードベース内の構成ファイルに保存するのが一般的です。 .NET 開発者は、 *web.config* ファイルを fondly に再呼び出します。 実装するのは簡単ですが、シークレットとコードを統合することは安全ではありませんでした。 一般的な誤った手順は、パブリック GIT リポジトリにプッシュするときにファイルを含めて、世界にシークレットを公開することでした。

最新の分散アプリケーションを構築するために広く受け入れられている方法として、 [Twelve-Factor アプリ](https://12factor.net/)があります。 ここでは、一連の原則とベストプラクティスについて説明します。 3番目の要素 *は、構成とシークレットがコードベースの外部で外部化さ* れることを規定します。

この問題に対処するために、.NET Core プラットフォームには、機密データをプロジェクトツリーの外部の物理的なフォルダーに格納する [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) 機能が含まれています。 シークレットはソース管理の対象外ですが、この機能はデータを暗号化しません。 **開発目的** のためだけに設計されています。

より新しい安全な方法は、 **Hashicorp Vault** や **Azure Key Vault** などのシークレット管理ツールでシークレットを分離することです。  これらのツールを使用すると、シークレットを外部に格納し、環境間で資格情報を変更して、アプリケーションコードから参照できます。 ただし、各ツールには複雑で学習曲線があります。

Dapr は、シークレットの管理を簡略化するビルディングブロックを提供します。

## <a name="what-it-solves"></a>解決方法

Dapr secret [ビルディングブロック](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) は、シークレットとシークレット管理ツールの操作の複雑さを解消します。

- これにより、基になるプラミングが統合インターフェイスで非表示になります。
- これは、開発と運用の間で異なる可能性がある、 *プラグ* 可能なさまざまなシークレットストアコンポーネントをサポートしています。
- アプリケーションでは、シークレットストアライブラリに直接依存する必要はありません。
- 開発者は、各シークレットストアに関する詳細な知識を必要としません。

Dapr は、上記のすべての懸念事項を処理します。

シークレットへのアクセスは、認証と承認によって保護されます。 十分な権限を持つアプリケーションのみがシークレットにアクセスできます。 Kubernetes で実行されているアプリケーションは、組み込みのシークレット管理メカニズムを使用することもできます。

## <a name="how-it-works"></a>しくみ

アプリケーションでは、次の2つの方法でシークレット構成ブロックを使用します。

- アプリケーションブロックからシークレットを直接取得します。
- Dapr コンポーネント構成から間接的にシークレットを参照します。

シークレットを直接取得する方法については、最初に説明します。 Dapr コンポーネント構成ファイルからシークレットを参照する方法については、後のセクションで説明します。

アプリケーションは、シークレットの構成ブロックを使用しているときに dapr サイドカーと対話します。 サイドカーは、シークレット API を公開しています。 API は、HTTP または gRPC を使用して呼び出すことができます。 次の URL を使用して HTTP API を呼び出します。

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/<name>?<metadata>
```

URL には、次のセグメントが含まれています。

- `<dapr-port>` dapr サイドカーがリッスンするポート番号を指定します。
- `<store-name>` Dapr シークレットストアの名前を指定します。
- `<name>` 取得するシークレットの名前を指定します。
- `<metadata>` シークレットに関する追加情報を提供します。 このセグメントは省略可能であり、メタデータのプロパティはシークレットストアごとに異なります。 メタデータプロパティの詳細については、「 [シークレット API リファレンス]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/))」を参照してください。

 > [!NOTE]
 > 上記の URL は、HTTP または gRPC をサポートするすべての開発プラットフォームで使用できるネイティブな Dapr API 呼び出しを表します。 .NET、Java、およびゴーなどの一般的なプラットフォームには、独自のカスタム Api があります。

JSON 応答には、シークレットのキーと値が含まれています。

図10-1 は、Dapr がシークレット API の要求を処理する方法を示しています。

![Dapr シークレット API を使用してシークレットを取得する方法の図。](media/secrets/secrets-flow.png)

**図 10-1**. Dapr secret API を使用してシークレットを取得する。

1. サービスは、Dapr シークレット API と、シークレットストアの名前、および取得するシークレットを呼び出します。
1. Dapr サイドカーは、指定されたシークレットをシークレットストアから取得します。
1. Dapr サイドカーは、秘密情報をサービスに返します。

一部のシークレットストアでは、複数のキー/値ペアを1つのシークレットに格納することがサポートされています。 これらのシナリオでは、次の例に示すように、応答には1つの JSON 応答に複数のキー/値ペアが含まれます。

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

.NET 開発者の場合、Dapr .NET SDK を使用すると、Dapr のシークレット管理が効率化されます。 メソッドについて考えてみましょう `DaprClient.GetSecretAsync` 。 これにより、最小限の労力で、任意の Dapr シークレットストアからシークレットを直接取得できます。 SQL Server データベースの接続文字列シークレットを取得する例を次に示します。

```csharp
var metadata = new Dictionary<string, string> { ["version_id"] = "3" };
Dictionary<string, string> secrets = await daprClient.GetSecretAsync("secret-store", "eshopsecrets", metadata);
string connectionString = secrets["customerdb"];
```

メソッドの引数 `GetSecretAsync` は次のとおりです。

- Dapr シークレットストアコンポーネント (' secret ストア ') の名前
- 取得するシークレット (' eshopsecrets ')
- 省略可能なメタデータのキーと値のペア (' version_id = 3 ')

シークレットには複数のキーと値のペアを含めることができるため、メソッドはディクショナリオブジェクトで応答します。 上の例では、という名前のシークレット `customerdb` がコレクションから参照され、接続文字列が返されます。

Dapr .NET SDK には、.NET 構成プロバイダーも用意されています。 指定されたシークレットを、基になる [.Net Core 構成 API](../../core/extensions/configuration.md)に読み込みます。 実行中のアプリケーションは、 `IConfiguration` ASP.NET Core 依存関係の挿入に登録されているディクショナリからシークレットを参照できます。

シークレット構成プロバイダーは、 [Dapr.Extensions.Configuration](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet パッケージから入手できます。 プロバイダーは、 `Program.cs` ASP.NET Web API アプリケーションのに登録できます。  

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

上の例では、 `eshopsecrets` 起動時に、.net 構成システムにシークレットコレクションを読み込みます。 プロバイダーを登録するには、 `DaprClient` Dapr sidecar でシークレット API を呼び出すために、のインスタンスが必要です。 その他の引数には、シークレットストアの名前、および `DaprSecretDescriptor` シークレットの名前を含むオブジェクトが含まれます。

読み込みが完了すると、アプリケーションコードから直接シークレットを取得できます。

```csharp
public void GetCustomer(IConfiguration config)
{
    var connectionString = config["eshopsecrets"]["customerdb"];
}
```

## <a name="secret-store-components"></a>シークレットストアのコンポーネント

シークレットの構成ブロックでは、複数のシークレットストアコンポーネントがサポートされています。 作成時には、次のシークレットストアを使用できます。

- 環境変数
- ローカル ファイル
- Kubernetes シークレット
- AWS シークレットマネージャー
- Azure Key Vault
- GCP シークレットマネージャー
- HashiCorp コンテナー

> [!IMPORTANT]
> 環境変数とローカルファイルコンポーネントは、開発ワークロード専用に設計されています。

次のセクションでは、シークレットストアを構成する方法について説明します。

### <a name="configuration"></a>構成

共有ストアは、Dapr コンポーネント構成ファイルを使用して構成します。 ファイルの一般的な構造を次に示します。

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

すべての Dapr コンポーネント構成ファイルは、 `name` オプションの値と共にを必要と `namespace` します。 また、セクションのフィールドは、 `type` `spec` シークレットストアコンポーネントの種類を指定します。 セクションのプロパティは、 `metadata` シークレットストアごとに異なります。

### <a name="indirectly-consume-dapr-secrets"></a>Dapr シークレットを間接的に使用する

この章で既に説明したように、アプリケーションでは、コンポーネント構成ファイルでシークレットを参照することによってシークレットを使用することもできます。 状態を格納するために Redis cache を使用する [状態管理コンポーネント](state-management.md) を考えてみましょう。

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

上記の構成ファイルには、Redis サーバーに接続するための **クリアテキスト** パスワードが含まれています。 **ハードコーディング** されたパスワードは、常に不適切なアイデアです。 この構成ファイルをパブリックリポジトリにプッシュすると、パスワードが公開されます。 シークレットストアにパスワードを格納すると、このシナリオが大幅に改善されます。

次の例では、いくつかの異なるシークレットストアを使用してこれを示します。

### <a name="local-file"></a>ローカル ファイル

ローカルファイルコンポーネントは、開発シナリオ向けに設計されています。 JSON ファイル内のローカルファイルシステムにシークレットを格納します。 という名前の例を次に示し `eshop-secrets.json` ます。 これには、Redis のパスワードという1つの秘密が含まれます。

```json
{
  "eShopRedisPassword": "e$h0p0nD@pr"
}
```

このファイルは、 `components` Dapr アプリケーションの実行時に指定したフォルダーに配置します。

次のシークレットストア構成ファイルは、シークレットストアとして JSON ファイルを使用します。 次のフォルダーにも配置され `components` ます。

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

コンポーネントの種類が `secretstore.local.file` です。 `secretsFile`メタデータ要素は、シークレットファイルへのパスを指定します。

> [!IMPORTANT]
> シークレットファイルへのパスには、絶対パスまたは相対パスを指定できます。 相対パスは、アプリケーションを起動するフォルダーに基づいています。 この例では、 `components` フォルダーは、.net アプリケーションが格納されているディレクトリのサブフォルダーです。

アプリケーションフォルダーから、 `components` コマンドライン引数としてパスを指定して Dapr アプリケーションを開始します。

```console
dapr run --app-id basket-api --components-path ./components dotnet run
```

> [!NOTE]
> 上記の例は、自己ホスト型モードでの Dapr の実行に適用されます。 Kubernetes をホストする場合は、ボリュームマウントの使用を検討してください。

`nestedSeparator`Dapr 構成ファイルのは、JSON 階層を *平坦* 化する文字を指定します。 次のスニペットを考えてみます。

```json
{
    "redisPassword": "some password",
    "connectionStrings": {
        "customerdb": "some connection string",
        "productdb": "some connection string"
    }
}
```

区切り記号としてコロンを使用すると、 `customerdb` キーを使用して接続文字列を取得でき `connectionStrings:customerdb` ます。

> [!NOTE]
> `:`既定の区切り記号の値は、コロンです。

次の例では、状態管理構成ファイルがローカルシークレットストアコンポーネントを参照し、Redis サーバーに接続するためのパスワードを取得します。

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

要素は、 `secretKeyRef` パスワードを含むシークレットを参照します。 これは、以前の *クリアテキスト* の値を置き換えます。 シークレット名とキー名は、 `eShopRedisPassword` シークレットを参照します。 シークレット管理コンポーネントの名前は、 `eshop-local-secret-store` `auth` メタデータ要素にあります。

`eShopRedisPassword`シークレット参照の名前とキーの両方でが同一であることが不思議に思われるかもしれません。 ローカルファイルシークレットストアでは、シークレットは別の名前で識別されません。 このシナリオは、Kubernetes シークレットを使用した次の例では異なります。

### <a name="kubernetes-secret"></a>Kubernetes シークレット

この2番目の例では、Kubernetes で実行されている Dapr アプリケーションに焦点を当てています。 Kubernetes が提供する標準のシークレット機構を使用します。 Kubernetes CLI ( `kubectl` ) を使用して、パスワードを含むという名前のシークレットを作成し `eshop-redis-secret` ます。

```console
kubectl create secret generic eshopsecrets --from-literal=redisPassword=e$h0p0nD@pr -n eshop
```

作成後は、状態管理のコンポーネント構成ファイルでシークレットを参照できます。

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

要素は、 `secretKeyRef` Kubernetes シークレットの名前とシークレットのキー、およびをそれぞれ指定し `eshopsecrets` `redisPassword` ます。 `auth`メタデータセクションは、Kubernetes シークレット管理コンポーネントを使用するように Dapr に指示します。

> [!NOTE]
> Kubernetes シークレットを使用する場合、Auth が既定値となります。これは省略できます。

運用環境の設定では、通常、シークレットは自動 CI/CD パイプラインの一部として作成されます。 これにより、十分なアクセス許可を持つ方だけがシークレットにアクセスして変更できるようになります。 開発者は、シークレットの実際の値を知らずに構成ファイルを作成します。

### <a name="azure-key-vault"></a>Azure Key Vault

次の例は、実稼働環境のシナリオを対象としています。 シークレットストアとして **Azure Key Vault** を使用します。 Azure Key Vault は、シークレットをクラウドに安全に格納できるようにする、管理された Azure サービスです。

この例を使用するには、次の前提条件を満たしている必要があります。

- Azure サブスクリプションへの管理アクセスをセキュリティで保護しました。
- `eshopkv` `redisPassword` Redis サーバーに接続するためのパスワードを含むという名前のシークレットを保持するという名前の Azure Key Vault をプロビジョニングしました。
- Azure Active Directory で [サービスプリンシパル](/azure/active-directory/develop/howto-create-service-principal-portal) が作成されました。
- このサービスプリンシパル (公開キーと秘密キーの両方を含む) の X509 証明書をローカルファイルシステムにインストールしました。

> [!NOTE]
> サービスプリンシパルは、アプリケーションが Azure サービスを認証するために使用できる id です。 サービスプリンシパルは、X509 証明書を使用します。 アプリケーションは、資格情報としてこの証明書を使用して自身を認証します。

[Dapr Azure Key Vault シークレットストアのドキュメント](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/)では、Key Vault 環境を作成および構成するための詳細な手順について説明しています。

#### <a name="use-key-vault-when-running-in-self-hosted-mode"></a>自己ホスト型モードで実行する場合は Key Vault を使用する

Dapr の自己ホスト型モードで Azure Key Vault を使用するには、次の構成ファイルが必要です。

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

シークレットストアの種類は `secretstores.azure.keyvault` です。 `metadata`Key Vault へのアクセスを構成する要素には、次のプロパティが必要です。

- には、 `vaultName` Azure Key Vault の名前が含まれています。
- には、 `spnTenantId` Key Vault に対する認証に使用されるサービスプリンシパルの *テナント ID* が含まれています。
- には、 `spnClientId` Key Vault に対する認証に使用されるサービスプリンシパルの *アプリ ID* が格納されます。
- には、 `spnCertificateFile` サービスプリンシパルが Key Vault に対して認証を行うための証明書ファイルへのパスが含まれています。

> [!TIP]
> サービスプリンシパル情報は、Azure portal または Azure CLI からコピーできます。

これで、アプリケーションは Azure Key Vault から Redis パスワードを取得できるようになります。

#### <a name="use-key-vault-when-running-on-kubernetes"></a>Kubernetes で実行する場合は Key Vault を使用する

Dapr と Kubernetes で Azure Key Vault を使用するには、Azure Key Vault に対して認証するためのサービスプリンシパルも必要です。

まず、kubectl CLI ツールを使用して証明書ファイルを含む *Kubernetes シークレット* を作成します。

```console
kubectl create secret generic [k8s_spn_secret_name] --from-file=[pfx_certificate_file_local_path] -n eshop
```

コマンドには、次の2つのコマンドライン引数が必要です。

- `[k8s_spn_secret_name]` Kubernetes secret ストアのシークレット名を指定します。
- `[pfx_certificate_file_local_path]` は、X509 証明書ファイルのパスです。

作成したら、シークレットストアのコンポーネント構成ファイルで Kubernetes シークレットを参照できます。

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
> サービスプリンシパルの X509 証明書ファイルを安全な場所に保管することが重要です。 ソースコードリポジトリの外部にあるよく知られたフォルダーに配置することをお勧めします。 構成ファイルは、この既知のフォルダーから証明書ファイルを参照できます。 ローカルの開発用コンピューターでは、証明書をフォルダーにコピーする必要があります。 自動デプロイの場合、パイプラインはアプリケーションが配置されているコンピューターに証明書をコピーします。 ベストプラクティスとして、環境ごとに異なるサービスプリンシパルを使用することをお勧めします。 これにより、開発環境のサービスプリンシパルが運用環境のシークレットにアクセスできなくなります。

Azure Kubernetes Service (AKS) で実行する場合は、Azure Key Vault に対して認証を行うために [Azure マネージ id](/azure/active-directory/managed-identities-azure-resources/overview) を使用することをお勧めします。 マネージド id はこの書籍の範囲外ですが、 [管理対象 id に](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) 関するドキュメントの Azure Key Vault で説明されています。

### <a name="scope-secrets"></a>シークレットのスコープを適用する

シークレットスコープを使用すると、アプリケーションがアクセスできるシークレットを制御できます。 スコープは、dapr サイドカー構成ファイルで構成します。 [Dapr 構成ドキュメント](https://docs.dapr.io/operations/configuration/configuration-overview/)では、シークレットのスコープを設定する方法を説明しています。

次に、秘密のスコープを含む dapr サイドカー構成ファイルの例を示します。

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

シークレットストアごとにスコープを指定します。 上の例では、シークレットストアにという名前が付けられて `eshop-azurekv-secret-store` います。 シークレットへのアクセスを構成するには、次のプロパティを使用します。

| プロパティ         | 値               | 説明                                                                                                                       |
|------------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `defaultAccess`  | `allow` または `deny`   | 指定したシークレットストア内の *すべて* のシークレットへのアクセスを許可または拒否します。 このプロパティは省略可能で、既定値は `allow` です。 |
| `allowedSecrets` | 秘密キーの一覧 | 配列に指定されたシークレットにアクセスできるようになります。 このプロパティは省略可能です。                                                     |
| `deniedSecrets`  | 秘密キーの一覧 | 配列に指定されたシークレットにアクセスできません。 このプロパティは省略可能です。                                                 |

`allowedSecrets`プロパティと `deniedSecrets` プロパティは、プロパティよりも優先され `defaultAccess` ます。 とリストを指定することを想像 `defaultAccess: allowed` `allowedSecrets` してください。 この場合、アプリケーションからアクセスできるのはリスト内のシークレットだけ `allowedSecrets` です。

## <a name="reference-application-eshopondapr"></a>参照アプリケーション: eShopOnDapr

EShopOnDapr 参照アプリケーションは、次の2つのシークレットに対してシークレットの構成ブロックを使用します。

- Redis cache に接続するためのパスワード。
- Twilio Sendgrid API を使用するための API キー。 アプリケーションは、Twillio を使用して、Dapr 出力バインドを使用して電子メールを送信します (「binding [ビルディングブロック](bindings.md)」の章を参照)。

Docker Compose を使用してアプリケーションを実行すると、 **ローカルファイル** シークレットストアが使用されます。 コンポーネント構成ファイル `eshop-secretstore.yaml` は、 `dapr/components` eShopOnDapr リポジトリのフォルダーにあります。

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

構成ファイルは、同じフォルダーにあるローカルストアファイルを参照し `eshop-secretstore.json` ます。

```json
{
    "redisPassword": "**********",
    "sendgridAPIKey": "**********"
}
```

この `components` フォルダーはコマンドラインで指定され、dapr サイドカーコンテナー内にローカルフォルダーとしてマウントされます。 `docker-compose.override.yml`ボリュームのマウントを指定するリポジトリルート内のファイルのスニペットを次に示します。

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
> Docker Compose 上書きファイルには、環境固有の構成値が含まれています。

`/components`ボリュームマウントと `--components-path` コマンドライン引数は、スタートアップコマンドに渡され `daprd` ます。

構成が完了すると、他のコンポーネント構成ファイルでもシークレットを参照できます。 次に、公開/サブスクライブコンポーネント構成でシークレットを使用する例を示します。

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

前の例では、シークレットを参照するためにローカル Redis ストアが使用されています。

## <a name="summary"></a>まとめ

Dapr シークレットの構成ブロックには、パスワードや接続文字列などの機密構成設定を格納および取得する機能が用意されています。 シークレットはプライベートに保持され、誤って開示されることはありません。

ビルディングブロックでは、いくつかの異なるシークレットストアがサポートされており、Dapr シークレット API での複雑さが隠蔽されています。

Dapr .NET SDK には、 `DaprClient` シークレットを取得するためのオブジェクトが用意されています。 また、.net Core 構成システムにシークレットを追加する .NET 構成プロバイダーも含まれています。 読み込んだ後は、これらのシークレットを .NET コードで使用できます。

シークレットスコープを使用して、特定のシークレットへのアクセスを制御することができます。

## <a name="references"></a>参照設定

- [Twelve-Factor アプリケーション以外](https://tanzu.vmware.com/content/blog/beyond-the-twelve-factor-app)

>[!div class="step-by-step"]
>[前へ](observability.md)
>[次へ](summary.md)
