---
title: 自己署名証明書の生成の概要
description: .NET Core および ASP.NET Core プロジェクトの機能を追加する Microsoft dotnet dev-certs ツール、および自己署名証明書を使用するためのその他のオプションの概要。
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: 738af3fc091e415399a53015a40748ad6116a2b4
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873017"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a>.NET CLI を使用して自己署名証明書を生成する

自己署名証明書を使用する場合、それらを作成し、開発やテストのシナリオに使用するには、さまざまな方法があります。  このガイドでは、`dotnet dev-certs`、および `PowerShell` や `OpenSSL` などのその他のオプションでの自己署名証明書の使用について説明します。

次に、コンテナーでホストされている [ ASP.NET Core アプリ](https://github.com/dotnet/dotnet-docker/blob/main/samples/run-aspnetcore-https-development.md)などの例を使用して、証明書が読み込まれることを検証できます。

## <a name="prerequisites"></a>前提条件

サンプルでは、.NET Core 3.1 または .NET 5 のいずれかを使用できます。

`dotnet dev-certs` については、必ず適切なバージョンの .NET をインストールしてください。

* [Windows に .NET をインストールする](../install/windows.md)
* [Linux に .NET をインストールする](../install/linux.md)
* [macOS に .NET をインストールする](../install/macos.md)

このサンプルには、[Docker 17.06](https://docs.docker.com/release-notes/docker-ce) 以降の [Docker クライアント](https://www.docker.com/products/docker)が必要です。

## <a name="prepare-sample-app"></a>サンプル アプリを準備する

テストに使用するランタイム ([.NET Core 3.1](#net-core-31-sample-app) または [.NET 5](#net-5-sample-app)) に応じてサンプル アプリを準備する必要があります。

このガイドでは、[サンプル アプリ](https://hub.docker.com/_/microsoft-dotnet-samples)を使用し、必要に応じて変更を加えます。

### <a name="net-core-31-sample-app"></a>.NET Core 3.1 サンプル アプリ

サンプル アプリを入手する。

```console
git clone https://github.com/dotnet/dotnet-docker/
```

ローカルでリポジトリに移動し、エディターでワークスペースを開きます。

> [!NOTE]
> dotnet publish パラメーターを使用して展開を "*トリミング*" する場合は、SSL 証明書をサポートするために適した依存関係が含まれていることを確認する必要があります。
[dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj) を更新して、適切なアセンブリがコンテナーに確実に含まれるようにします。 参考のために、自己完結型の展開にトリミングを使用する場合に [SSL 証明書をサポートする](../deploying/trim-self-contained.md#support-for-ssl-certificates)ための .csproj ファイルの更新方法を確認してください。

`aspnetapp.csproj` に適切なターゲット フレームワークが含まれていることを確認します。

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

ランタイムで .NET Core 3.1 が指示されるように Dockerfile を変更します。

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet-core
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app --no-restore

# final stage/image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "aspnetapp.dll"]
```

サンプル アプリを指していることを確認します。

```console
cd .\dotnet-docker\samples\aspnetapp
```

ローカルで、テスト用のコンテナーをビルドします。

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="net-5-sample-app"></a>.NET 5 サンプル アプリ

このガイドでは、[サンプルの aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) で、.NET 5 を確認する必要があります。

サンプル アプリ [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/Dockerfile) で .NET 5 が使用されていることを確認します。

ホスト OS によっては、ASP.NET ランタイムの更新が必要になる場合があります。 たとえば、Dockerfile で `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` から `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` に変更すると、適切な Windows ランタイムをターゲットにするのに役立ちます。

たとえば、以下は、Windows で証明書をテストするのに役立ちます。

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore -r win-x64

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app -r win-x64 --self-contained false --no-restore

# final stage/image
# Uses the 2009 release; 2004, 1909, and 1809 are other choices
FROM mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["aspnetapp"]

```

Linux で証明書をテストする場合は、既存の Dockerfile を使用できます。

`aspnetapp.csproj` に適切なターゲット フレームワークが含まれていることを確認します。

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> `dotnet publish` パラメーターを使用して展開を "*トリミング*" する場合は、SSL 証明書をサポートするために適した依存関係が含まれていることを確認します。
[dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj) を更新して、適切なアセンブリがコンテナーに確実に含まれるようにします。 参考のために、自己完結型の展開にトリミングを使用する場合に [SSL 証明書をサポートする](../deploying/trim-self-contained.md#support-for-ssl-certificates)ための .csproj ファイルの更新方法を確認してください。

サンプル アプリを指していることを確認します。

```console
cd .\dotnet-docker\samples\aspnetapp
```

ローカルで、テスト用のコンテナーをビルドします。

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate"></a>自己署名証明書の作成

自己署名証明書を作成できます。

- [dotnet dev-certs を使用する](#with-dotnet-dev-certs)
- [PowerShell の場合](#with-powershell)
- [OpenSSL を使用する](#with-openssl)

### <a name="with-dotnet-dev-certs"></a>dotnet dev-certs を使用する

`dotnet dev-certs` を使用して、自己署名証明書を操作できます。 この例では、PowerShell コンソールを使用します。

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> 証明書名 (この場合は *aspnetapp*.pfx) は、プロジェクトのアセンブリ名と一致する必要があります。 `crypticpassword` は、自身で選択したパスワードの代わりに使用されます。 コンソールから "有効な HTTPS 証明書が既にあります。" が返された場合、信頼できる証明書がストア内に既に存在します。 MMC コンソールを使用して、これをエクスポートできます。

証明書のアプリケーション シークレットを構成します。

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> メモ:パスワードは、証明書に使用されているパスワードと一致する必要があります。

HTTPS 用に構成された ASP.NET Core を使用してコンテナー イメージを実行します。

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

アプリケーションが起動したら、Web ブラウザーで `https://localhost:8001` に移動します。

#### <a name="clean-up"></a>クリーンアップ

シークレットと証明書を使用しない場合は、それらを必ずクリーンアップしてください。

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

### <a name="with-powershell"></a>PowerShell の場合

PowerShell を使用して自己署名証明書を生成できます。 自己署名証明書を生成するには、[PKI クライアント](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps)を使用できます。

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

証明書は生成されますが、テストの目的で、ブラウザーでテストするために証明書ストアに配置する必要があります。

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

この時点で、証明書は、[MMC スナップイン](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)から表示できるようになります。

サンプル コンテナーは、Linux 用 Windows サブシステム (WSL) で実行できます。

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> ボリューム マウントでは、ファイル パスの処理方法がホストによって異なる可能性があることにご注意ください。  たとえば、WSL では、 */c/certs* を */mnt/c/certs* に置き換えることができます。

以前に Windows 用に構築されたコンテナーを使用している場合、run コマンドは次のようになります。

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

アプリケーションが起動したら、ブラウザーで contoso.com:8001 に移動します。

適切な IP アドレス (たとえば、127.0.0.1) で応答するために、ホスト エントリが `contoso.com` 用に更新されていることを確認してください。 証明書が認識されない場合は、コンテナーと共に読み込まれる証明書もホストで信頼されていること、および `contoso.com` に適した SAN および DNS エントリがあることを確認してください。

#### <a name="clean-up"></a>クリーンアップ

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

### <a name="with-openssl"></a>OpenSSL を使用する

[OpenSSL](https://www.openssl.org/) を使用して自己署名証明書を作成できます。 この例では、WSL および Ubuntu と、`OpenSSL`を使用する bash シェルを使用します。

これにより、.crt と .key が生成されます。

```bash
PARENT="contoso.com"
openssl req \
-x509 \
-newkey rsa:4096 \
-sha256 \
-days 365 \
-nodes \
-keyout $PARENT.key \
-out $PARENT.crt \
-subj "/CN=${PARENT}" \
-extensions v3_ca \
-extensions v3_req \
-config <( \
  echo '[req]'; \
  echo 'default_bits= 4096'; \
  echo 'distinguished_name=req'; \
  echo 'x509_extension = v3_ca'; \
  echo 'req_extensions = v3_req'; \
  echo '[v3_req]'; \
  echo 'basicConstraints = CA:FALSE'; \
  echo 'keyUsage = nonRepudiation, digitalSignature, keyEncipherment'; \
  echo 'subjectAltName = @alt_names'; \
  echo '[ alt_names ]'; \
  echo "DNS.1 = www.${PARENT}"; \
  echo "DNS.2 = ${PARENT}"; \
  echo '[ v3_ca ]'; \
  echo 'subjectKeyIdentifier=hash'; \
  echo 'authorityKeyIdentifier=keyid:always,issuer'; \
  echo 'basicConstraints = critical, CA:TRUE, pathlen:0'; \
  echo 'keyUsage = critical, cRLSign, keyCertSign'; \
  echo 'extendedKeyUsage = serverAuth, clientAuth')

openssl x509 -noout -text -in $PARENT.crt
```

.pfx を取得するには、次のコマンドを使用します。

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> .aspnetcore 3.1 の例では、`.pfx` とパスワードを使用します。 `.net 5` ランタイム以降、Kestrel でも、`.crt` ファイルと PEM でエンコードされた `.key` ファイルを取得できます。

ホスト OS によっては、証明書が信頼されている必要があります。 Linux ホストでは、証明書を '信頼する' 方法が異なり、ディストリビューションに依存します。

このガイドの目的のために、PowerShell を使用した Windows の例を次に示します。

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

.NET Core 3.1 の場合、WSL で次のコマンドを実行します。

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

.NET 5 以降では、Kestrel により、`.crt` ファイルと PEM でエンコードされた `.key` ファイルを取得できます。 サンプルは、.NET 5 用の次のコマンドを使用して実行できます。

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> WSL では、ボリューム マウントのパスが構成によって変わる場合があることにご注意ください。

Windows の .NET Core 3.1 の場合、`Powershell` で次のコマンドを実行します。

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

Windows の .NET 5 の場合、PowerShell で次のコマンドを実行します。

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

アプリケーションが起動したら、ブラウザーで contoso.com:8001 に移動します。

適切な IP アドレス (たとえば、127.0.0.1) で応答するために、ホスト エントリが `contoso.com` 用に更新されていることを確認してください。 証明書が認識されない場合は、コンテナーと共に読み込まれる証明書もホストで信頼されていること、および `contoso.com` に適した SAN および DNS エントリがあることを確認してください。

#### <a name="clean-up"></a>クリーンアップ

テストが完了したら、必ず自己署名証明書をクリーンアップしてください。

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
