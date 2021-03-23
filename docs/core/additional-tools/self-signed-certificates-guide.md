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
# <a name="generate-self-signed-certificates-with-the-net-cli"></a><span data-ttu-id="1eed6-103">.NET CLI を使用して自己署名証明書を生成する</span><span class="sxs-lookup"><span data-stu-id="1eed6-103">Generate self-signed certificates with the .NET CLI</span></span>

<span data-ttu-id="1eed6-104">自己署名証明書を使用する場合、それらを作成し、開発やテストのシナリオに使用するには、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-104">When using self-signed certificates, there are different ways to create and use them for development and testing scenarios.</span></span>  <span data-ttu-id="1eed6-105">このガイドでは、`dotnet dev-certs`、および `PowerShell` や `OpenSSL` などのその他のオプションでの自己署名証明書の使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-105">In this guide, you'll cover using self-signed certificates with `dotnet dev-certs`, and other options like `PowerShell` and `OpenSSL`.</span></span>

<span data-ttu-id="1eed6-106">次に、コンテナーでホストされている [ ASP.NET Core アプリ](https://github.com/dotnet/dotnet-docker/blob/main/samples/run-aspnetcore-https-development.md)などの例を使用して、証明書が読み込まれることを検証できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-106">You can then validate that the certificate will load using an example such as an [ASP.NET Core app](https://github.com/dotnet/dotnet-docker/blob/main/samples/run-aspnetcore-https-development.md) hosted in a container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1eed6-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="1eed6-107">Prerequisites</span></span>

<span data-ttu-id="1eed6-108">サンプルでは、.NET Core 3.1 または .NET 5 のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-108">In the sample, you can utilize either .NET Core 3.1 or .NET 5.</span></span>

<span data-ttu-id="1eed6-109">`dotnet dev-certs` については、必ず適切なバージョンの .NET をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-109">For `dotnet dev-certs`, be sure to have the appropriate version of .NET installed:</span></span>

* [<span data-ttu-id="1eed6-110">Windows に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="1eed6-110">Install .NET on Windows</span></span>](../install/windows.md)
* [<span data-ttu-id="1eed6-111">Linux に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="1eed6-111">Install .NET on Linux</span></span>](../install/linux.md)
* [<span data-ttu-id="1eed6-112">macOS に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="1eed6-112">Install .NET on macOS</span></span>](../install/macos.md)

<span data-ttu-id="1eed6-113">このサンプルには、[Docker 17.06](https://docs.docker.com/release-notes/docker-ce) 以降の [Docker クライアント](https://www.docker.com/products/docker)が必要です。</span><span class="sxs-lookup"><span data-stu-id="1eed6-113">This sample requires [Docker 17.06](https://docs.docker.com/release-notes/docker-ce) or later of the [Docker client](https://www.docker.com/products/docker).</span></span>

## <a name="prepare-sample-app"></a><span data-ttu-id="1eed6-114">サンプル アプリを準備する</span><span class="sxs-lookup"><span data-stu-id="1eed6-114">Prepare sample app</span></span>

<span data-ttu-id="1eed6-115">テストに使用するランタイム ([.NET Core 3.1](#net-core-31-sample-app) または [.NET 5](#net-5-sample-app)) に応じてサンプル アプリを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-115">You'll need to prepare the sample app depending on which runtime you'd like to use for testing, either [.NET Core 3.1](#net-core-31-sample-app) or [.NET 5](#net-5-sample-app).</span></span>

<span data-ttu-id="1eed6-116">このガイドでは、[サンプル アプリ](https://hub.docker.com/_/microsoft-dotnet-samples)を使用し、必要に応じて変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-116">For this guide, you'll use a [sample app](https://hub.docker.com/_/microsoft-dotnet-samples) and make changes where appropriate.</span></span>

### <a name="net-core-31-sample-app"></a><span data-ttu-id="1eed6-117">.NET Core 3.1 サンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="1eed6-117">.NET Core 3.1 sample app</span></span>

<span data-ttu-id="1eed6-118">サンプル アプリを入手する。</span><span class="sxs-lookup"><span data-stu-id="1eed6-118">Get the sample app.</span></span>

```console
git clone https://github.com/dotnet/dotnet-docker/
```

<span data-ttu-id="1eed6-119">ローカルでリポジトリに移動し、エディターでワークスペースを開きます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-119">Navigate to the repository locally and open up the workspace in an editor.</span></span>

> [!NOTE]
> <span data-ttu-id="1eed6-120">dotnet publish パラメーターを使用して展開を "*トリミング*" する場合は、SSL 証明書をサポートするために適した依存関係が含まれていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-120">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="1eed6-121">[dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj) を更新して、適切なアセンブリがコンテナーに確実に含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="1eed6-121">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="1eed6-122">参考のために、自己完結型の展開にトリミングを使用する場合に [SSL 証明書をサポートする](../deploying/trim-self-contained.md#support-for-ssl-certificates)ための .csproj ファイルの更新方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-122">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="1eed6-123">`aspnetapp.csproj` に適切なターゲット フレームワークが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-123">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

<span data-ttu-id="1eed6-124">ランタイムで .NET Core 3.1 が指示されるように Dockerfile を変更します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-124">Modify the Dockerfile to make sure the runtime points to .NET Core 3.1:</span></span>

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

<span data-ttu-id="1eed6-125">サンプル アプリを指していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-125">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="1eed6-126">ローカルで、テスト用のコンテナーをビルドします。</span><span class="sxs-lookup"><span data-stu-id="1eed6-126">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="net-5-sample-app"></a><span data-ttu-id="1eed6-127">.NET 5 サンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="1eed6-127">.NET 5 sample app</span></span>

<span data-ttu-id="1eed6-128">このガイドでは、[サンプルの aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) で、.NET 5 を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-128">For this guide, the [sample aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) should be checked for .NET 5.</span></span>

<span data-ttu-id="1eed6-129">サンプル アプリ [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/Dockerfile) で .NET 5 が使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-129">Check sample app [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/Dockerfile) is using .NET 5.</span></span>

<span data-ttu-id="1eed6-130">ホスト OS によっては、ASP.NET ランタイムの更新が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-130">Depending on the host OS, the ASP.NET runtime may need to be updated.</span></span> <span data-ttu-id="1eed6-131">たとえば、Dockerfile で `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` から `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` に変更すると、適切な Windows ランタイムをターゲットにするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-131">For example, changing from `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` to `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` in the Dockerfile will help with targeting the appropriate Windows runtime.</span></span>

<span data-ttu-id="1eed6-132">たとえば、以下は、Windows で証明書をテストするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-132">For example, this will help with testing the certificates on Windows:</span></span>

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

<span data-ttu-id="1eed6-133">Linux で証明書をテストする場合は、既存の Dockerfile を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-133">If we're testing the certificates on Linux, you can use the existing Dockerfile.</span></span>

<span data-ttu-id="1eed6-134">`aspnetapp.csproj` に適切なターゲット フレームワークが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-134">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> <span data-ttu-id="1eed6-135">`dotnet publish` パラメーターを使用して展開を "*トリミング*" する場合は、SSL 証明書をサポートするために適した依存関係が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-135">If you want to use `dotnet publish` parameters to *trim* the deployment, make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="1eed6-136">[dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj) を更新して、適切なアセンブリがコンテナーに確実に含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="1eed6-136">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="1eed6-137">参考のために、自己完結型の展開にトリミングを使用する場合に [SSL 証明書をサポートする](../deploying/trim-self-contained.md#support-for-ssl-certificates)ための .csproj ファイルの更新方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-137">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="1eed6-138">サンプル アプリを指していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-138">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="1eed6-139">ローカルで、テスト用のコンテナーをビルドします。</span><span class="sxs-lookup"><span data-stu-id="1eed6-139">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="1eed6-140">自己署名証明書の作成</span><span class="sxs-lookup"><span data-stu-id="1eed6-140">Create a self-signed certificate</span></span>

<span data-ttu-id="1eed6-141">自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-141">You can create a self-signed certificate:</span></span>

- [<span data-ttu-id="1eed6-142">dotnet dev-certs を使用する</span><span class="sxs-lookup"><span data-stu-id="1eed6-142">With dotnet dev-certs</span></span>](#with-dotnet-dev-certs)
- [<span data-ttu-id="1eed6-143">PowerShell の場合</span><span class="sxs-lookup"><span data-stu-id="1eed6-143">With PowerShell</span></span>](#with-powershell)
- [<span data-ttu-id="1eed6-144">OpenSSL を使用する</span><span class="sxs-lookup"><span data-stu-id="1eed6-144">With OpenSSL</span></span>](#with-openssl)

### <a name="with-dotnet-dev-certs"></a><span data-ttu-id="1eed6-145">dotnet dev-certs を使用する</span><span class="sxs-lookup"><span data-stu-id="1eed6-145">With dotnet dev-certs</span></span>

<span data-ttu-id="1eed6-146">`dotnet dev-certs` を使用して、自己署名証明書を操作できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-146">You can use `dotnet dev-certs` to work with self-signed certificates.</span></span> <span data-ttu-id="1eed6-147">この例では、PowerShell コンソールを使用します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-147">This example uses a PowerShell console.</span></span>

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> <span data-ttu-id="1eed6-148">証明書名 (この場合は *aspnetapp*.pfx) は、プロジェクトのアセンブリ名と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-148">The certificate name, in this case *aspnetapp*.pfx must match the project assembly name.</span></span> <span data-ttu-id="1eed6-149">`crypticpassword` は、自身で選択したパスワードの代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-149">`crypticpassword` is used as a stand-in for a password of your own choosing.</span></span> <span data-ttu-id="1eed6-150">コンソールから "有効な HTTPS 証明書が既にあります。" が返された場合、信頼できる証明書がストア内に既に存在します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-150">If console returns "A valid HTTPS certificate is already present.", a trusted certificate already exists in your store.</span></span> <span data-ttu-id="1eed6-151">MMC コンソールを使用して、これをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-151">It can be exported using MMC Console.</span></span>

<span data-ttu-id="1eed6-152">証明書のアプリケーション シークレットを構成します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-152">Configure application secrets, for the certificate:</span></span>

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> <span data-ttu-id="1eed6-153">メモ:パスワードは、証明書に使用されているパスワードと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-153">Note: The password must match the password used for the certificate.</span></span>

<span data-ttu-id="1eed6-154">HTTPS 用に構成された ASP.NET Core を使用してコンテナー イメージを実行します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-154">Run the container image with ASP.NET Core configured for HTTPS:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="1eed6-155">アプリケーションが起動したら、Web ブラウザーで `https://localhost:8001` に移動します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-155">Once the application starts, navigate to `https://localhost:8001` in your web browser.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="1eed6-156">クリーンアップ</span><span class="sxs-lookup"><span data-stu-id="1eed6-156">Clean up</span></span>

<span data-ttu-id="1eed6-157">シークレットと証明書を使用しない場合は、それらを必ずクリーンアップしてください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-157">If the secrets and certificates are not in use, be sure to clean them up.</span></span>

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

### <a name="with-powershell"></a><span data-ttu-id="1eed6-158">PowerShell の場合</span><span class="sxs-lookup"><span data-stu-id="1eed6-158">With PowerShell</span></span>

<span data-ttu-id="1eed6-159">PowerShell を使用して自己署名証明書を生成できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-159">You can use PowerShell to generate self-signed certificates.</span></span> <span data-ttu-id="1eed6-160">自己署名証明書を生成するには、[PKI クライアント](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-160">The [PKI Client](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps) can be used to generate a self-signed certificate.</span></span>

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

<span data-ttu-id="1eed6-161">証明書は生成されますが、テストの目的で、ブラウザーでテストするために証明書ストアに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-161">The certificate will be generated, but for the purposes of testing, should be placed in a cert store for testing in a browser.</span></span>

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

<span data-ttu-id="1eed6-162">この時点で、証明書は、[MMC スナップイン](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)から表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-162">At this point, the certificates should be viewable from an [MMC snap-in](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

<span data-ttu-id="1eed6-163">サンプル コンテナーは、Linux 用 Windows サブシステム (WSL) で実行できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-163">You can run the sample container in Windows Subsystem for Linux (WSL):</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="1eed6-164">ボリューム マウントでは、ファイル パスの処理方法がホストによって異なる可能性があることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-164">Note that with the volume mount the file path could be handled differently based on host.</span></span>  <span data-ttu-id="1eed6-165">たとえば、WSL では、 */c/certs* を */mnt/c/certs* に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-165">For example, in WSL we may replace */c/certs* with */mnt/c/certs*.</span></span>

<span data-ttu-id="1eed6-166">以前に Windows 用に構築されたコンテナーを使用している場合、run コマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-166">If you're using the container built earlier for Windows, the run command would look like the following:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="1eed6-167">アプリケーションが起動したら、ブラウザーで contoso.com:8001 に移動します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-167">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="1eed6-168">適切な IP アドレス (たとえば、127.0.0.1) で応答するために、ホスト エントリが `contoso.com` 用に更新されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-168">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="1eed6-169">証明書が認識されない場合は、コンテナーと共に読み込まれる証明書もホストで信頼されていること、および `contoso.com` に適した SAN および DNS エントリがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-169">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="1eed6-170">クリーンアップ</span><span class="sxs-lookup"><span data-stu-id="1eed6-170">Clean up</span></span>

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

### <a name="with-openssl"></a><span data-ttu-id="1eed6-171">OpenSSL を使用する</span><span class="sxs-lookup"><span data-stu-id="1eed6-171">With OpenSSL</span></span>

<span data-ttu-id="1eed6-172">[OpenSSL](https://www.openssl.org/) を使用して自己署名証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-172">You can use [OpenSSL](https://www.openssl.org/) to create self-signed certificates.</span></span> <span data-ttu-id="1eed6-173">この例では、WSL および Ubuntu と、`OpenSSL`を使用する bash シェルを使用します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-173">This example will use WSL / Ubuntu and a bash shell with `OpenSSL`.</span></span>

<span data-ttu-id="1eed6-174">これにより、.crt と .key が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-174">This will generate a .crt and a .key.</span></span>

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

<span data-ttu-id="1eed6-175">.pfx を取得するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-175">To get a .pfx, use the following command:</span></span>

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> <span data-ttu-id="1eed6-176">.aspnetcore 3.1 の例では、`.pfx` とパスワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-176">The .aspnetcore 3.1 example will use `.pfx` and a password.</span></span> <span data-ttu-id="1eed6-177">`.net 5` ランタイム以降、Kestrel でも、`.crt` ファイルと PEM でエンコードされた `.key` ファイルを取得できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-177">Starting with the `.net 5` runtime, Kestrel can also take `.crt` and PEM-encoded `.key` files.</span></span>

<span data-ttu-id="1eed6-178">ホスト OS によっては、証明書が信頼されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eed6-178">Depending on the host os, the certificate will need to be trusted.</span></span> <span data-ttu-id="1eed6-179">Linux ホストでは、証明書を '信頼する' 方法が異なり、ディストリビューションに依存します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-179">On a Linux host, 'trusting' the certificate is different and distro dependent.</span></span>

<span data-ttu-id="1eed6-180">このガイドの目的のために、PowerShell を使用した Windows の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-180">For the purposes of this guide, here's an example in Windows using PowerShell:</span></span>

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

<span data-ttu-id="1eed6-181">.NET Core 3.1 の場合、WSL で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-181">For .NET Core 3.1, run the following command in WSL:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="1eed6-182">.NET 5 以降では、Kestrel により、`.crt` ファイルと PEM でエンコードされた `.key` ファイルを取得できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-182">Starting with .NET 5, Kestrel can take the `.crt` and PEM-encoded `.key` files.</span></span> <span data-ttu-id="1eed6-183">サンプルは、.NET 5 用の次のコマンドを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="1eed6-183">You can run the sample with the following command for .NET 5:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="1eed6-184">WSL では、ボリューム マウントのパスが構成によって変わる場合があることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-184">Note that in WSL, the volume mount path may change depending on the configuration.</span></span>

<span data-ttu-id="1eed6-185">Windows の .NET Core 3.1 の場合、`Powershell` で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-185">For .NET Core 3.1 in Windows, run the following command in `Powershell`:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="1eed6-186">Windows の .NET 5 の場合、PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-186">For .NET 5 in Windows, run the following command in PowerShell:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="1eed6-187">アプリケーションが起動したら、ブラウザーで contoso.com:8001 に移動します。</span><span class="sxs-lookup"><span data-stu-id="1eed6-187">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="1eed6-188">適切な IP アドレス (たとえば、127.0.0.1) で応答するために、ホスト エントリが `contoso.com` 用に更新されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-188">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="1eed6-189">証明書が認識されない場合は、コンテナーと共に読み込まれる証明書もホストで信頼されていること、および `contoso.com` に適した SAN および DNS エントリがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-189">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="1eed6-190">クリーンアップ</span><span class="sxs-lookup"><span data-stu-id="1eed6-190">Clean up</span></span>

<span data-ttu-id="1eed6-191">テストが完了したら、必ず自己署名証明書をクリーンアップしてください。</span><span class="sxs-lookup"><span data-stu-id="1eed6-191">Be sure to clean up the self-signed certificates once done testing.</span></span>

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
