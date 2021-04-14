---
title: ASP.NET Core への移行時の展開シナリオ
description: ASP.NET から ASP.NET Core への移行時に使用でき、サイドバイサイドの段階的な移行を可能にするさまざまな展開アプローチの概要。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 589acd8c66baacc3aef5833dfaa24e2dcc5c1ee5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401386"
---
# <a name="deployment-scenarios-when-migrating-to-aspnet-core"></a>ASP.NET Core への移行時の展開シナリオ

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

既存の ASP.NET MVC アプリと Web API アプリは、Windows と IIS 上で実行されます。 大規模なアプリでは、ASP.NET Core に移植するときに、段階的なアプローチまたはサイドバイサイドのアプローチが必要になる場合があります。 これまでの章で、大規模な .NET Framework アプリを ASP.NET Core に段階的に移行するためのさまざまな戦略について説明しました。 この章では、アプリを部分的に移行している間に元のアプリを運用環境で維持する必要がある場合に、さまざまな展開シナリオを実現する方法について説明します。

## <a name="split-a-large-web-app"></a>大規模な Web アプリを分割する

現在 1 つの Web サイト内で IIS 上でホストされている大規模な Web アプリの一般的なシナリオについて考えてみましょう。 大規模なアプリ内では、機能がさまざまなルートやディレクトリに分割されています。 アプリには MVC ビューと API エンドポイントが混在しています。 MVC ルートには機能に基づくさまざまなパスが含まれており、そのすべてが標準の `/{controller}/{action}/{id?}` ルート テンプレートを使用し、アプリのルートから始まっています。 API エンドポイントも同様のパターンに従っていますが、すべてが `/api` ルートの下にあります。

アプリを移植するタスクが、MVC 機能または API 機能のいずれかを最初に ASP.NET Core に移行するように分割されたと仮定した場合、元のサイトはどのようにして、他の場所で実行されている新しい ASP.NET Core アプリと引き続きシームレスに連携できるでしょうか? システムのユーザーには、移行前と同じ URL が (その変更が絶対に必要な場合を除き) 引き続き表示される必要があります。

幸いなことに、IIS は非常に機能豊富な Web サーバーであり、しばらく前から [URL 書き換えモジュールとアプリケーション要求ルーティング処理](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)という 2 つの機能を備えています。 これらの機能を使用すると、IIS は、クライアント要求を適切なバックエンド Web アプリにルーティングする[リバース プロキシ](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)の役割を果たすことができます。 IIS をリバース プロキシとして構成するには、アプリケーション要求ルーティング処理機能の **[プロキシを有効にする]** チェックボックスをオンにしてから、次のような URL 書き換え規則を追加します。

```xml
<rule name="NetCoreProxy">
  <match url="(.*)> />
  <action type="Rewrite" url="http://servername/{R:1}" />
</rule>
```

リバース プロキシとしての IIS は、特定のパターンに一致するトラフィックを (別のサーバー上に存在している可能性がある) まったく別のアプリにルーティングできます。

URL 書き換えモジュールのみを (おそらくホスト ヘッダーと組み合わせて) 使用することで、IIS は、(それぞれが異なるバージョンの .NET を実行している可能性がある) 複数の Web サイトを簡単にサポートできます。 大規模な Web アプリは、それぞれが異なる IP アドレスやホスト ヘッダーに対応している個別のサイトのコレクションとして、または特定の URL パスに応答する (URL 書き換えを必要としない) 1 つ以上のサブアプリケーションを含んだ 1 つの Web サイトとして展開できます。

> [!IMPORTANT]
> サブドメインとは、通常、ドメインの上位 2 レベルの前にある部分を指します。 たとえば、ドメイン `api.contoso.com` 内では、`api` が `contoso.com` ドメイン (それ自体が、ドメイン名 `contoso` と TLD、つまり最上位レベルのドメイン `.com` で構成されています) のサブドメインとなります。 URL パスとは、URL のドメイン名の後にある `/` で始まる部分を指します。 URL `https://contoso.com/api` のパスは `/api` です。

同じまたは異なるサブドメイン (およびドメイン) を使用して 1 つのアプリをホストすることには、長所と短所があります。 分散型アプリでは、[CORS](/aspnet/core/security/cors) などのメカニズムを使用する Cookies やアプリ内通信のような機能を正しく機能させるために、より多くの構成が必要になることがあります。 しかし、異なるサブドメインを使用するアプリのほうが、DNS を使用してまったく異なるネットワーク接続先に要求を簡単にルーティングできるため、IIS をリバース プロキシとして機能させなくても、(仮想またはそれ以外の) 多数の異なるサーバーにより簡単に展開できます。

上で説明した例で、API エンドポイントが、アプリの ASP.NET Core に移植する最初の部分として指定されたとします。 その場合、新しい ASP.NET Core アプリが作成され、既存の ASP.NET MVC Web "*サイト*" 内の別の Web "*アプリケーション*" として IIS でホストされます。 これは元の Web サイトの子として追加され、*api* という名前を付けられるため、その既定のルートが `api/` で始まらないようにしなければなりません。 これをそのまま維持すると、`/api/api/endpoint` という形式の URL と一致するようになります。

図 5-1 に、ASP.NET Core 2.1 の *api* アプリが IIS マネージャー内でどのように既存の *DotNetMvcApp* サイトの一部として表示されるかを示します。

![.NET Framework サイト内の api アプリが表示された IIS マネージャー](./media/Figure5-1.png)

**図 5-1**. IIS 内の .NET Core アプリが含まれている .NET Framework サイト

*DotNetMvcApp* サイトは、.NET Framework 4.7.2 上で実行されている MVC 5 アプリとしてホストされます。 これは、統合モードで構成され、.NET CLR バージョン 4.0.30319 を実行している独自の IIS アプリ プールを持ちます。 *api* アプリは、.NET Framework 4.6.1 (`net461`) 上で実行される ASP.NET Core アプリです。 これは *DotNetMvcApp* に新しい IIS アプリとして追加され、独自のアプリケーション プールを使用するように構成されています。 そのアプリケーション プールも統合モードで実行されていますが、[ASP.NET Core モジュール](/aspnet/core/host-and-deploy/aspnet-core-module?preserve-view=true&view=aspnetcore-2.1)を使用して実行されるため、**マネージド コードなし** の .NET CLR バージョンで構成されています。 ASP.NET Core アプリのバージョンは単なる例です。 これは .NET Core 3.1 または .NET 5.0 上で実行されるように構成することもできます。 ただし、その時点で、.NET Framework ライブラリをターゲットにすることが不可能になっている可能性があります (「[適切な .NET Core バージョンを選択する](choose-net-core-version.md)」を参照してください)。

このように構成した場合、ASP.NET Core アプリの API が正しくルーティングされるようにするために必要な変更は、その既定のルート テンプレートを `[Route("[api/controller]")]` から `[Route("[controller]")]` に変更することだけです。

また、ASP.NET Core アプリを IIS 内で別の最上位レベルの Web サイトにすることもできます。 その場合は、元のサイトを、パスが `/api` で始まる場合には他のアプリにリダイレクトするという書き換えルールを使用するように ([URL 書き換え](https://www.iis.net/downloads/microsoft/url-rewrite)によって) 構成できます。 ASP.NET Core アプリは、そのルートに対して別のホスト ヘッダーを使用して、メイン アプリと競合しないが、ルートベースのルートを使用した要求に引き続き応答するようにできます。

例として、図 5-1 で使用したのと同じ ASP.NET Core アプリを、IIS Web サイトとして構成された別のフォルダーに展開できます。 このサイトは、前と同じように、 **[マネージド コードなし]** で構成されたアプリ プールを使用する必要があります。 そのバインドを、サーバー上の一意のホスト名 (`api.contoso.com` など) に応答するように構成します。 `/api` に一致する要求を書き換える URL 書き換えを構成するには、IIS サーバー (または個別サイト) レベルで新しい受信規則を追加するだけです。 照合するパターン `^/api(.*)`、アクションの種類 `Rewrite`、書き換え URL `api.contoso.com/{R:1}` を指定します。 照合するパターン `(.*)`、書き換え URL `{R:1}` を組み合わせて使用することで、パスの残りの部分が新しい URL に使用されるようにできます。 これを設定すると、別のバージョンの .NET を実行している別のサイトを同じ IIS サーバー上で共存させ、それらをインターネットに対して 1 つの Web アプリのように見せることができます。 図 5-2 に、IIS 内で別の Web サイトを指定して構成された書き換え規則を示します。

![サブフォルダーの要求を別の Web サイトにルーティングする URL 書き換え規則が示された IIS マネージャー](./media/Figure5-2.png)

**図 5-2** サブフォルダーの要求を別の Web サイトに書き換えるための書き換え規則

アプリで、IIS 内の異なるサイトまたはアプリ間のシングル サインオンが必要な場合は、[ASP.NET アプリ間で認証 Cookie を共有する方法に関する記事](/aspnet/core/host-and-deploy/iis/)を参照して、このシナリオのサポートに関する詳細な手順を確認してください。

## <a name="summary"></a>まとめ

大規模なアプリを .NET Framework から ASP.NET Core に移植するための一般的なアプローチは、アプリの部分を選択して 1 つずつ移行することです。 アプリの各部分が移植されると、アプリ全体の実行を継続して使用可能な状態を保ちつつ、その一部は元の構成で、他の部分は何らかのバージョンの .NET Core 上で実行されているという状態にできます。 このアプローチに従うことで、大規模なアプリの移行を段階的に実行できます。 このアプローチを使用すると、より迅速なフィードバックを提供し、テストに関係する領域全体を縮小することができるため、リスクが軽減されます。 また、パフォーマンスの向上など、.NET Core のベネフィットをより迅速に実現できます。 ASP.NET Core アプリを IIS 上でホストする必要はなくなりましたが、IIS は依然として非常に柔軟で強力な Web サーバーであり、同じ IIS インスタンス上、または別のサーバー上で .NET Framework アプリと ASP.NET Core アプリの両方をホストするシナリオなど、幅広いホスティング シナリオをサポートするように構成できます。

## <a name="references"></a>リファレンス

- [IIS を使用した Windows での ASP.NET Core のホスト](/aspnet/core/host-and-deploy/iis/)
- [URL 書き換えモジュールとアプリケーション要求ルーティング処理](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)
- [URL 書き換え](https://www.iis.net/downloads/microsoft/url-rewrite)
- [ASP.NET Core モジュール](/aspnet/core/host-and-deploy/aspnet-core-module?preserve-view=true&view=aspnetcore-2.1)
- [ASP.NET アプリ間での認証 Cookie の共有](/aspnet/core/host-and-deploy/iis/)
- [このセクションで使用したサンプル](https://github.com/ardalis/MigrateDotNetWithIIS)

>[!div class="step-by-step"]
>[前へ](more-migration-scenarios.md)
>[次へ](summary.md)
