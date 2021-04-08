---
title: ASP.NET Web API 2 と ASP.NET Core の比較
description: ASP.NET Web API 2 アプリと ASP.NET Core アプリとで、Web API はどのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 93aa917174bce24fdf924f6372312c3972473289
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401344"
---
# <a name="compare-aspnet-web-api-2-and-aspnet-core"></a>ASP.NET Web API 2 と ASP.NET Core の比較

ASP.NET Core では ASP.NET Web API 2 に対する反復的な機能強化が提供されますが、Web API 2 を使用してきた開発者にとっては馴染みやすいでしょう。 ASP.NET Web API 2 は ASP.NET MVC と共に開発され、出荷されました。 したがって、これらの 2 つのアプローチでは、属性ルーティングや依存関係の挿入などに対して似ているが異なるアプローチが採用されています。 ASP.NET Core では、MVC と Web API の区別がなくなりました。 存在するのは ASP.NET MVC のみで、これにはビューベースのシナリオ、API エンドポイント、Razor Pages (および正常性チェックや SignalR などのその他のバリエーション) のサポートが含まれます。

.NET Core に組み込まれている API は、ASP.NET Core 内で一貫していて統合されているのに加えて、ASP.NET Web API 2 上に構築されたものよりもはるかにテストが簡単です。 [テストの違い](testing-differences.md)については、後で詳しく説明します。 アプリに対してメモリ内の要求を行う `HttpClient` を作成できるテスト ホスト内の、ASP.NET Core アプリをホストするための組み込みのサポートは、自動テストに関して非常に大きなベネフィットとなります。

ASP.NET Web API 2 から ASP.NET Core に移行する場合、切り替えは簡単です。 大規模な、肥大化したコントローラーがある場合、それを分割するために検討できる 1 つのアプローチは、[Ardalis.ApiEndpoints](https://www.nuget.org/packages/Ardalis.ApiEndpoints/) NuGet パッケージを使用することです。 このパッケージは、各エンドポイントを、必要に応じて関連する要求および応答の種類と共に、独自の固有のクラスに分割します。 このアプローチでは、ビューベースのコード編成と比べたときに [Razor Pages で得られるのと同じベネフィット](comparing-razor-pages-aspnet-mvc.md)の多くが得られます。

## <a name="references"></a>リファレンス

- [ASP.NET Web API から ASP.NET Core への移行](/aspnet/core/migration/webapi)
- [Ardalis.ApiEndpoints NuGet パッケージ](https://www.nuget.org/packages/Ardalis.ApiEndpoints/)

>[!div class="step-by-step"]
>[前へ](comparing-razor-pages-aspnet-mvc.md)
>[次へ](authentication-differences.md)
