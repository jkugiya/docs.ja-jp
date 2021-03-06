---
title: ASP.NET Core に移行する場合の展開シナリオ
description: ASP.NET から ASP.NET Core に移植するときに使用できるさまざまな展開手法の概要について説明します。これにより、サイドバイサイドおよび段階的な移行が可能になります。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 589acd8c66baacc3aef5833dfaa24e2dcc5c1ee5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401386"
---
# <a name="deployment-scenarios-when-migrating-to-aspnet-core"></a>ASP.NET Core に移行する場合の展開シナリオ

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

既存の ASP.NET MVC および Web API アプリは、IIS と Windows 上で実行されます。 ASP.NET Core に移植するときは、大規模なアプリで段階的またはサイドバイサイドのアプローチが必要になる場合があります。 前の章では、大規模な .NET Framework アプリを段階的に ASP.NET Core に移行するためのいくつかの方法について学習しました。 この章では、その一部を移行するときに、元のアプリを運用環境で維持する必要がある場合に、さまざまな展開シナリオを実現する方法について説明します。

## <a name="split-a-large-web-app"></a>大規模な web アプリを分割する

現在、単一の web サイトの IIS でホストされている大規模な web アプリの一般的なシナリオを考えてみましょう。 大規模なアプリでは、機能は別のルートやディレクトリに分割されます。 アプリは、MVC ビューと API エンドポイントを組み合わせたものです。 MVC ルートには、機能に基づいたさまざまなパスが含まれており、そのすべてが標準ルートテンプレートを使用してアプリのルートから開始され `/{controller}/{action}/{id?}` ます。 API エンドポイントは同様のパターンに従いますが、すべてがルートの下にあり `/api` ます。

MVC 機能または API 機能が最初に ASP.NET Core に移行されるように、アプリを移植するタスクが分割されていると仮定した場合、元のサイトは、別の場所で実行されている新しい ASP.NET Core アプリとシームレスに連携して動作しますか。 システムのユーザーは、移行前と同じ Url を引き続き表示する必要があります。ただし、変更する必要がある場合は除きます。

幸いなことに、IIS は非常に機能豊富な web サーバーであり、しばらくの間、 [URL 書き換えモジュールとアプリケーション要求ルーティングと](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)いう2つの機能がありました。 これらの機能を使用して、IIS は [リバースプロキシ](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)として機能し、適切なバックエンド web アプリにクライアント要求をルーティングすることができます。 IIS をリバースプロキシとして構成するには、アプリケーション要求ルーティング機能の [ **プロキシを有効** にする] チェックボックスをオンにし、次のような URL 書き換え規則を追加します。

```xml
<rule name="NetCoreProxy">
  <match url="(.*)> />
  <action type="Rewrite" url="http://servername/{R:1}" />
</rule>
```

リバースプロキシとして、IIS では、特定のパターンに一致するトラフィックを、異なるサーバー上のすべてのアプリに分離することができます。

URL 書き換えモジュールだけを使用して (おそらくホストヘッダーと組み合わせて)、IIS では複数の web サイトを簡単にサポートでき、それぞれ異なるバージョンの .NET が実行される可能性があります。 大規模な web アプリは個々のサイトのコレクションとして、それぞれ異なる IP アドレスまたはホストヘッダーに対応している場合もあれば、特定の URL パスに応答する1つ以上のサブアプリケーションを含む単一の web サイトとして展開される場合もあります (URL の書き換えは必要ありません)。

> [!IMPORTANT]
> サブドメインは、通常、上位2つのレベルの前にあるドメインの部分を参照します。 たとえば、ドメインでは、 `api.contoso.com` `api` はドメインのサブドメインです `contoso.com` (それ自体がドメイン `contoso` 名と `.com` トップレベルドメインまたは TLD で構成されています)。 URL パスは、で始まるドメイン名の後の URL の部分を参照し `/` ます。 URL の `https://contoso.com/api` パスは `/api` です。

同じまたは異なるサブドメイン (およびドメイン) を使用して1つのアプリをホストすると、長所と短所があります。 Cookie や、 [CORS](/aspnet/core/security/cors) のようなメカニズムを使用したアプリ内通信などの機能では、分散アプリで適切に機能するためにより多くの構成が必要になる場合があります。 ただし、異なるサブドメインを使用するアプリでは、DNS を使用して要求を完全に異なるネットワーク宛先にルーティングできるため、IIS をリバースプロキシとして動作させることなく、さまざまなサーバー (仮想またはそれ以外) に簡単に展開できます。

前に説明した例では、API エンドポイントが ASP.NET Core に移植されるアプリの最初の部分として指定されているとします。 この場合、新しい ASP.NET Core アプリが作成され、既存の ASP.NET MVC web *サイト* 内の別の web *アプリケーション* として IIS でホストされます。 元の web サイトの子として追加され、 *api* という名前が付けられるため、既定のルートはで始まらなくなり `api/` ます。 これを維持すると、フォームの Url と一致するようになり `/api/api/endpoint` ます。

図5-1 は、既存の *DotNetMvcApp* サイトの一部として IIS マネージャーに ASP.NET Core 2.1 *api* アプリがどのように表示されるかを示しています。

![.NET Framework サイト内に api アプリを表示している IIS マネージャー](./media/Figure5-1.png)

**図 5-1**. IIS で .NET Core アプリを使用してサイトを .NET Framework します。

*DotNetMvcApp* サイトは、.NET Framework 4.7.2 で実行される MVC 5 アプリとしてホストされます。 独自の IIS アプリプールが統合モードで構成され、.NET CLR バージョン v4.0.30319 が実行されています。 *Api* アプリは、.NET Framework 4.6.1 () で実行される ASP.NET Core アプリです `net461` 。 新しい IIS アプリケーションとして *DotNetMvcApp* に追加され、独自のアプリケーションプールを使用するように構成されています。 このアプリケーションプールは統合モードでも実行されていますが、 [ASP.NET Core モジュール](/aspnet/core/host-and-deploy/aspnet-core-module?preserve-view=true&view=aspnetcore-2.1)を使用して実行されるため、**マネージコードのない**.net CLR バージョンで構成されています。 ASP.NET Core アプリのバージョンはほんの一例です。 また、.NET Core 3.1 または .NET 5.0 で実行されるように構成することもできます。 ただし、その時点では、.NET Framework ライブラリをターゲットにすることはできなくなります (「 [適切な .Net Core バージョンを選択](choose-net-core-version.md)する」を参照してください)。

このように構成した場合、ASP.NET Core アプリの Api を適切にルーティングするために必要な変更は、既定のルートテンプレートをからに変更することだけです `[Route("[api/controller]")]` `[Route("[controller]")]` 。

また、IIS の別のトップレベル web サイトに ASP.NET Core アプリを使用することもできます。 この場合、パスがで始まる場合に他のアプリにリダイレクトされる書き換え規則 ( [URL リライト](https://www.iis.net/downloads/microsoft/url-rewrite)) を使用するように、元のサイトを構成することができ `/api` ます。 ASP.NET Core アプリは、ルートに別のホストヘッダーを使用して、メインアプリと競合しないようにすることができますが、ルートベースのルートを使用して要求に応答できます。

例として、図5-1 で使用したのと同じ ASP.NET Core アプリを、IIS web サイトとして構成されている別のフォルダーに配置できます。 サイトでは、以前と同じように構成されたアプリプールを使用する必要があります。マネージコードは使用し **ません**。 など、サーバー上の一意のホスト名に応答するようにバインドを構成し `api.contoso.com` ます。 `/api`IIS サーバー (または個々のサイト) レベルで新しい受信規則を追加するだけで、一致する要求を再書き込みするように URL を書き換えることができます。 パターンに一致し、 `^/api(.*)` アクションの種類との書き換え URL を指定し `Rewrite` `api.contoso.com/{R:1}` ます。 照合パターンでを使用し、 `(.*)` `{R:1}` リライト URL でを組み合わせることにより、パスの残りの部分が新しい url で使用されるようになります。 これを使用すると、同じ IIS サーバー上の個別のサイトで別々のバージョンの .NET を共存させることができますが、インターネットには1つの web アプリとして表示されるようになります。 図5-2 は、IIS で構成されている、個別の web サイトと書き換え規則を示しています。

![サブフォルダーの要求を別の web サイトにルーティングするための URL 書き換えルールを示す IIS マネージャー](./media/Figure5-2.png)

**図 5-2** サブフォルダーの要求を別の web サイトに書き直す規則を書き換えます。

異なるサイトまたは IIS 内のアプリの間でシングルサインオンが必要なアプリの場合は、このシナリオをサポートするための詳細な手順について、 [ASP.NET アプリ間で認証 cookie を共有する方法](/aspnet/core/host-and-deploy/iis/) に関するドキュメントを参照してください。

## <a name="summary"></a>まとめ

大規模なアプリを .NET Framework から ASP.NET Core に移植する一般的な方法は、アプリの個々の部分を選択して1つずつ移行することです。 アプリの各部分が移植されると、アプリ全体が実行され、使用可能になります。元の構成で実行される部分と、.NET Core の一部のバージョンで実行されているその他の部分が実行されます。 このアプローチに従うことで、大規模なアプリの移行を段階的に実行できます。 このアプローチでは、より迅速なフィードバックを提供し、テストに関係する総領域を減らすことで、リスクを制限します。 また、パフォーマンスの向上など、.NET Core の利点をより迅速に実現できます。 ASP.NET Core のアプリは IIS でホストする必要がなくなりましたが、IIS は非常に柔軟で強力な web サーバーとして機能します。これは、.NET Framework と ASP.NET Core の両方のアプリを同じ IIS インスタンス上で、または異なるサーバー上でホストされているさまざまなホスティングシナリオをサポートするように構成できます。

## <a name="references"></a>関連項目

- [IIS を使用した Windows での ASP.NET Core のホスト](/aspnet/core/host-and-deploy/iis/)
- [URL 書き換えモジュールとアプリケーション要求ルーティング](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)
- [URL 書き換え](https://www.iis.net/downloads/microsoft/url-rewrite)
- [ASP.NET Core モジュール](/aspnet/core/host-and-deploy/aspnet-core-module?preserve-view=true&view=aspnetcore-2.1)
- [ASP.NET アプリ間で認証 cookie を共有する](/aspnet/core/host-and-deploy/iis/)
- [このセクションで使用するサンプル](https://github.com/ardalis/MigrateDotNetWithIIS)

>[!div class="step-by-step"]
>[前へ](more-migration-scenarios.md)
>[次へ](summary.md)
