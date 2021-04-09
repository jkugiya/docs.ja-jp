---
title: '破壊的変更:Kestrel: 既定でサポートされている TLS プロトコル バージョンの変更'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Kestrel: 既定でサポートされている TLS プロトコル バージョンの変更'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1e3ebd700e5bb603f95a8b20ebdbd61379f1e508
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497646"
---
# <a name="kestrel-default-supported-tls-protocol-versions-changed"></a>Kestrel: 既定でサポートされている TLS プロトコル バージョンの変更

Kestrel では現在、以前のように TLS 1.1 プロトコルと TLS 1.2 プロトコルへの接続を制限するのではなく、システム既定の TLS プロトコル バージョンを使用します。

この変更で可能になること:

* それをサポートする環境で TLS 1.3 を既定で使用できます。
* TLS 1.0 を一部の環境 (既定の Windows Server 2016 など) で使用できます。通常、これは[望ましくありません](/security/engineering/solving-tls1-problem)。

ディスカッションについては、イシュー [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 6

## <a name="old-behavior"></a>以前の動作

Kestrel では既定で、TLS 1.1 または TLS 1.2 を接続に使用する必要がありました。

## <a name="new-behavior"></a>新しい動作

Kestrel では、使用に最適なプロトコルを選択し、セキュリティに保護されていないプロトコルをブロックすることがオペレーティング システムに許可されます。 <xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> は既定で `SslProtocols.Tls12 | SslProtocols.Tls11` ではなく `SslProtocols.None` になりました。

## <a name="reason-for-change"></a>変更理由

TLS 1.3 と、将来の TLS バージョンが利用できるようになったときにそれをサポートする目的で変更が行われました。

## <a name="recommended-action"></a>推奨アクション

アプリケーション側に特別な理由がある場合を除き、新しい既定値を使用してください。 セキュリティで保護されているプロトコルのみを許可するようにシステムが構成されていることを確認してください。

以前のプロトコルを無効にするには、次のいずれかのアクションを行います。

* [Windows の指示に従い](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry)、TLS 1.0 など、古いプロトコルをシステム全体で無効にします。 現在のところ、すべての Windows バージョンで既定で有効になっています。
* コードでサポートするプロトコルを次のように手動で選択します。

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

残念ながら、特定のプロトコルを除外する API はありません。

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
